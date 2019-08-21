Improved XBMC Wiimote Gateway
=============================

A Kodi event client that receives input from a Wii remote via bluetooth
and feeds them to Kodi.

While Kodi comes with a Wii remote event client already (`xbmc-wiiremote`),
this project aims to improve upon it by adding some additional features
such as automatic disconnect, by having better error handling and to be
more hackable by using the Python bindings.

Features
--------

* Automatic disconnect after a period of disuse
* On connect…
  * notifications in Kodi,
  * rumble, and
  * battery status report
* Supports key repeating when holding a button down
* Rudimentary error handling
* Usage of a specific Wii remote to be able to pair quickly
* Uses the official Kodi [EventServer API](http://wiki.xbmc.org/?title=EventServer#Event_Clients_and_the_EventServer)
* Uses the [custom controller keymap](https://kodi.wiki/view/Keymap) with Kodi (>= 17.0)

Requirements
------------

XBMC Wiimote Gateway is an Kodi event client, so it needs:

* Kodi (>= 17), with
  * Kodi Event Client Python bindings
* Python (>= 2.6), with
  * Python CWIID bindings (>= 0.6)
* Bluez (>= 4.96)

and of course a working bluetooth controller.

Installation & Use
------------------

First, install a keymap file `WiiRemote.xml` in `$HOME/.kodi/userdata/keymaps`:

```xml
<keymap>
  <global>
    <customcontroller name="WiiRemote">
      <button id="1">Up</button>
      <button id="2">Down</button>
      <button id="3">Left</button>
      <button id="4">Right</button>
      <button id="5">Select</button>
      <button id="6">Back</button>
      <button id="7">VolumeDown</button>
      <button id="8">ActivateWindow(Home)</button>
      <button id="9">VolumeUp</button>
      <button id="10">ContextMenu</button>
      <button id="11">ActivateWindow(PlayerControls)</button>
    </customcontroller>
  </global>
  <Home>
    <customcontroller name="WiiRemote">
      <button id="8">Fullscreen</button>
      <button id="10">ActivateWindow(Favourites)</button>
      <button id="11">ActivateWindow(ShutdownMenu)</button>
    </customcontroller>
  </Home>
  <FullscreenVideo>
    <customcontroller name="WiiRemote">
      <button id="1">Pause</button>
      <button id="2">Stop</button>
      <button id="3">StepBack</button>
      <button id="4">StepForward</button>
      <button id="5">OSD</button>
      <button id="6">Info</button>
      <button id="7">VolumeDown</button>
      <button id="8">ActivateWindow(Home)</button>
      <button id="9">VolumeUp</button>
      <button id="10">CodecInfo</button>
      <button id="11">AspectRatio</button>
    </customcontroller>
  </FullscreenVideo>
</keymap>
```

(Feel free to modify it to your liking.)

Then install the script itself, xbmc-wiimote, can be put anywhere.  Preferably,
put it somewhere that is in the system's/in your path.

Run:

    $ xbmc-wiimote -b <Wii remote bluetooth address>

You should see a notification pop up in Kodi that tells you that the
XBMC Wiimote Gateway has connected.

If you don't know the bluetooth address of your Wii remote, run

    $ hcitool scan

and quickly press 1+2 on the Wii remote to find the address

License
-------

XBMC Wiimote Gateway free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by the
Free Software Foundation, either version 3 of the License, or (at your
option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT
ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for
more details.

You should have received a copy of the GNU General Public License along
with this program.  If not, see <http://www.gnu.org/licenses/>.

*N.B.* The source code of this program includes code from
http://code.activestate.com/recipes/577407/ which is licensed under the
Apache License 2.0, see also: http://www.apache.org/licenses/LICENSE-2.0.html
