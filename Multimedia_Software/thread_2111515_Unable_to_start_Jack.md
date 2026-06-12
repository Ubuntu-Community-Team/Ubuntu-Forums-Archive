---
title: "Unable to start Jack"
date: 2013-02-02
forum: Multimedia Software
---

### Post by curiousapprentice on 2013-02-02
If try to start jack immediate after login, it works, but if I try starting jack after opening any audio video file it gives me error -

 p, li { white-space: pre-wrap; }  [COLOR=#999999]15:34:22.174 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]15:34:22.177 Statistics reset.[/COLOR]
 [COLOR=#cccc99]15:34:22.184 ALSA connection change.[/COLOR]
 [COLOR=#999999]15:34:22.207 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Registered event listener change listener:  true 
 [COLOR=#66cc99]15:34:22.226 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]15:34:25.009 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0xbfda4130) "" 
 FIXME: handle dialog start. 
 Sat Feb  2 15:34:24 2013: Starting jack server...
 Sat Feb  2 15:34:24 2013: JACK server starting in realtime mode with priority 10
 Sat Feb  2 15:34:24 2013: [1m[31mERROR: Cannot lock down 82241434 byte memory area (Cannot allocate memory)[0m
 Sat Feb  2 15:34:24 2013: control device hw:0
 Sat Feb  2 15:34:24 2013: control device hw:0
 Sat Feb  2 15:34:24 2013: [1m[31mERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory[0m
 Sat Feb  2 15:34:24 2013: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
 Sat Feb  2 15:34:24 2013: [1m[31mERROR: Cannot initialize driver[0m
 Sat Feb  2 15:34:24 2013: [1m[31mERROR: JackServer::Open() failed with -1[0m
 Sat Feb  2 15:34:25 2013: [1m[31mERROR: Failed to open server[0m
 FIXME: handle dialog end. 
 Sat Feb  2 15:34:26 2013: Saving settings to "/home/soham/.config/jack/conf.xml" ...
 [COLOR=#ff0000]15:34:28.912 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0xbfda49c0) "" 
 FIXME: handle dialog start. 
 FIXME: handle dialog end. 
 [COLOR=#999999]QSpiAccessible::accessibleEvent not handled:  "6"  obj:  QMenu(0x9c8bfd0) "" [/COLOR]


If I delete "jack" directory from /home/soham/.config/ then jack starts working again but meanwhile I could not hear any sound from any audio/video apps.

Please help.

---

