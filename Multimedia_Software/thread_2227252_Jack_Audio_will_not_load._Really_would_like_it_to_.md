---
title: "Jack Audio will not load. Really would like it to work"
date: 2014-05-31
forum: Multimedia Software
---

### Post by 777funk on 2014-05-31
Here's what it says when opened. 

```
[COLOR=#999999]17:15:40.418 Patchbay deactivated.[/COLOR]
[COLOR=#999999]17:15:40.433 Statistics reset.[/COLOR]
[COLOR=#cccc99]17:15:40.447 ALSA connection change.[/COLOR]
[COLOR=#999999]17:15:40.472 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Registered event listener change listener:  true 
[COLOR=#66cc99]17:15:40.486 ALSA connection graph change.[/COLOR]

```

Then if I start a session I get:
D-Bus JACK Server could not be started 

and this message:
```
[COLOR=#999999]FIXME: handle dialog start.[/COLOR][COLOR=#999999]FIXME: handle dialog end. [/COLOR]
[COLOR=#ff0000]17:16:46.779 D-BUS: JACK server could not be started. Sorry[/COLOR]
[COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
[COLOR=#999999]Cannot connect to server request channel[/COLOR]
[COLOR=#999999]jack server is not running or cannot be started[/COLOR]
[COLOR=#999999]QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0xbf8da640) "" [/COLOR]
[COLOR=#999999]FIXME: handle dialog start. [/COLOR]
[COLOR=#999999]Sat May 31 17:16:46 2014: Starting jack server...[/COLOR]
[COLOR=#999999]Sat May 31 17:16:46 2014: JACK server starting in realtime mode with priority 10[/COLOR]
[COLOR=#999999]Sat May 31 17:16:46 2014: ERROR: can't load "/usr/lib/i386-linux-gnu/jack/jack_alsa.so": /usr/lib/i386-linux-gnu/jack/jack_alsa.so: undefined symbol: _ZN4Jack10JackDriver15SaveConnectionsEi[/COLOR]
[COLOR=#999999]Sat May 31 17:16:46 2014: ERROR: Cannot initialize driver[/COLOR]
[COLOR=#999999]Sat May 31 17:16:46 2014: ERROR: JackServer::Open() failed with -1[/COLOR]
[COLOR=#999999]Sat May 31 17:16:46 2014: ERROR: Failed to open server[/COLOR]
[COLOR=#999999]Sat May 31 17:16:47 2014: Saving settings to "/home/nick/.config/jack/conf.xml" ...[/COLOR]
[COLOR=#999999]FIXME: handle dialog end. [/COLOR]
[COLOR=#999999]FIXME: handle dialog start. [/COLOR]
[COLOR=#ff0000]17:16:51.283 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
[COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
[COLOR=#999999]Cannot connect to server request channel[/COLOR]
[COLOR=#999999]jack server is not running or cannot be started[/COLOR]
[COLOR=#999999]QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0xbf8d9f60) "" [/COLOR]
[COLOR=#999999]FIXME: handle dialog start. [/COLOR]
[COLOR=#999999]FIXME: handle dialog end. [/COLOR]
[COLOR=#999999]QSpiAccessible::accessibleEvent not handled:  "6"  obj:  QMenu(0xbf8d98f4) "" [/COLOR]
[COLOR=#999999]QSpiAccessible::accessibleEvent not handled:  "7"  obj:  QMenu(0xbf8d98f4) "" [/COLOR]
[COLOR=#999999]QSpiAccessible::accessibleEvent not handled:  "6"  obj:  QMenu(0xbf8d98f4) "" [/COLOR]
[COLOR=#999999]QSpiAccessible::accessibleEvent not handled:  "7"  obj:  QMenu(0xbf8d98f4) "" [/COLOR]
[COLOR=#999999]QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QComboBoxListView(0x8b8ada0) "" [/COLOR]
[COLOR=#999999]FIXME: handle dialog end. [/COLOR]
[COLOR=#ff0000]17:17:18.608 D-BUS: JACK server could not be started. Sorry[/COLOR]
[COLOR=#999999]Sat May 31 17:17:18 2014: Starting jack server...[/COLOR]
[COLOR=#999999]Sat May 31 17:17:18 2014: JACK server starting in realtime mode with priority 10[/COLOR]
[COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
[COLOR=#999999]Cannot connect to server request channel[/COLOR]
[COLOR=#999999]jack server is not running or cannot be started[/COLOR]
[COLOR=#999999]QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0xbf8da640) "" [/COLOR]
[COLOR=#999999]FIXME: handle dialog start. [/COLOR]
[COLOR=#999999]Sat May 31 17:17:18 2014: ERROR: can't load "/usr/lib/i386-linux-gnu/jack/jack_alsa.so": /usr/lib/i386-linux-gnu/jack/jack_alsa.so: undefined symbol: _ZN4Jack10JackDriver15SaveConnectionsEi[/COLOR]
[COLOR=#999999]Sat May 31 17:17:18 2014: ERROR: Cannot initialize driver[/COLOR]
[COLOR=#999999]Sat May 31 17:17:18 2014: ERROR: JackServer::Open() failed with -1[/COLOR]
[COLOR=#999999]Sat May 31 17:17:18 2014: ERROR: Failed to open server[/COLOR]
[COLOR=#999999]Sat May 31 17:17:19 2014: Saving settings to "/home/nick/.config/jack/conf.xml" ...[/COLOR]
[COLOR=#999999]FIXME: handle dialog end. [/COLOR]
[COLOR=#999999]FIXME: handle dialog start. [/COLOR]
[COLOR=#ff0000]17:17:51.287 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
[COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
[COLOR=#999999]Cannot connect to server request channel[/COLOR]
[COLOR=#999999]jack server is not running or cannot be started[/COLOR]
[COLOR=#999999]QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0xbf8d9f60) "" [/COLOR]
[COLOR=#999999]FIXME: handle dialog start. [/COLOR]
[COLOR=#999999]FIXME: handle dialog end. [/COLOR]
[COLOR=#999999]FIXME: handle dialog end. [/COLOR]
[COLOR=#ff0000]17:18:07.496 D-BUS: SetParameterValue('driver:inchannels', '2'): Parameter value type mismatch: was expecting 'i', got 'u'. (org.jackaudio.Error.InvalidArgs)[/COLOR]
[COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
[COLOR=#999999]Cannot connect to server request channel[/COLOR]
[COLOR=#999999]jack server is not running or cannot be started[/COLOR]
[COLOR=#999999]QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0xbf8da1c0) "" [/COLOR]
[COLOR=#999999]FIXME: handle dialog start. [/COLOR]
[COLOR=#999999]Sat May 31 17:18:07 2014: ERROR: Parameter value type mismatch: was expecting 'i', got 'u'[/COLOR]
[COLOR=#999999]Sat May 31 17:18:08 2014: Saving settings to "/home/nick/.config/jack/conf.xml" ...[/COLOR]
[COLOR=#ff0000]17:18:10.300 D-BUS: SetParameterValue('driver:outchannels', '2'): Parameter value type mismatch: was expecting 'i', got 'u'. (org.jackaudio.Error.InvalidArgs)[/COLOR]
[COLOR=#999999]FIXME: handle dialog end. [/COLOR]
[COLOR=#999999]QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0xbf8da1c0) "" [/COLOR]
[COLOR=#999999]FIXME: handle dialog start. [/COLOR]
[COLOR=#999999]Sat May 31 17:18:10 2014: ERROR: Parameter value type mismatch: was expecting 'i', got 'u'[/COLOR]
[COLOR=#ff0000]17:18:11.706 D-BUS: JACK server could not be started. Sorry[/COLOR]
[COLOR=#999999]FIXME: handle dialog end. [/COLOR]
[COLOR=#999999]QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0xbf8da640) "" [/COLOR]
[COLOR=#999999]FIXME: handle dialog start. [/COLOR]
[COLOR=#999999]FIXME: handle dialog end. [/COLOR]
[COLOR=#999999]Sat May 31 17:18:11 2014: Starting jack server...[/COLOR]
[COLOR=#999999]Sat May 31 17:18:11 2014: JACK server starting in realtime mode with priority 10[/COLOR]
[COLOR=#999999]Sat May 31 17:18:11 2014: ERROR: can't load "/usr/lib/i386-linux-gnu/jack/jack_alsa.so": /usr/lib/i386-linux-gnu/jack/jack_alsa.so: undefined symbol: _ZN4Jack10JackDriver15SaveConnectionsEi[/COLOR]
[COLOR=#999999]Sat May 31 17:18:11 2014: ERROR: Cannot initialize driver[/COLOR]
[COLOR=#999999]Sat May 31 17:18:11 2014: ERROR: JackServer::Open() failed with -1[/COLOR]
[COLOR=#999999]Sat May 31 17:18:11 2014: ERROR: Failed to open server[/COLOR]
[COLOR=#999999]FIXME: handle dialog start. [/COLOR]
[COLOR=#999999]Sat May 31 17:18:12 2014: Saving settings to "/home/nick/.config/jack/conf.xml" ...[/COLOR]
[COLOR=#ff0000]17:18:14.569 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
[COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
[COLOR=#999999]Cannot connect to server request channel[/COLOR]
[COLOR=#999999]jack server is not running or cannot be started[/COLOR]
[COLOR=#999999]QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0xbf8d9f60) "" [/COLOR]
[COLOR=#999999]FIXME: handle dialog start. [/COLOR]
[COLOR=#999999]FIXME: handle dialog end. [/COLOR]
[COLOR=#999999]FIXME: handle dialog end. [/COLOR]
```


However Ardour works just fine (does it's own Jack controls). 

Where do I look?

I have an MAudio 192 Audiophile PCI card interface

---

### Post by 777funk on 2014-05-31
Got it to work somehow. I followed these steps:
[COLOR=#000000][FONT=sans-serif]Please delete [/FONT][/COLOR]~/.jackdrc[COLOR=#000000][FONT=sans-serif], [/FONT][/COLOR]~/.config/jack/conf.xml[COLOR=#000000][FONT=sans-serif], [/FONT][/COLOR]~/.config/rncbc.org/QjackCtl.conf[COLOR=#000000][FONT=sans-serif]. Kill [/FONT][/COLOR][I]jackdbus and restart from scratch :) (Thanks to nedko)

and killed it by:
[/I][COLOR=#000000][FONT=Verdana]jack_control exit

in the terminal

So I guess it's solved (hopefully still solved after a reboot).

But I'm getting a lot of xruns at 256 samples. I don't get this in Ardour or in Reaper running in windows.

[/FONT][/COLOR]

---

