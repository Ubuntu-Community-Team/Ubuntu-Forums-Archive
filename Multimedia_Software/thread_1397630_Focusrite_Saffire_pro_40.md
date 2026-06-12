---
title: "Focusrite Saffire pro 40"
date: 2010-02-03
forum: Multimedia Software
---

### Post by brucioamaphone on 2010-02-03
Hi all,
         Im trying to setup my Focusrite Saffire pro 40 firewire interface and i am having issues loading the drivers up. Im not sure if its with my jackd config, or if its system related. when i try to start Jackd i get the following

 p, li { white-space: pre-wrap; }  [COLOR=#999999]14:40:55.017 Startup script...[/COLOR]
 [COLOR=#990099]14:40:55.018 artsshell -q terminate[/COLOR]
 [COLOR=#66CC99]14:40:55.023 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]14:40:55.436 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]14:40:55.436 JACK is starting...[/COLOR]
 [COLOR=#990099]14:40:55.437 /usr/bin/jackd -R -dfirewire -d/dev/audio -r44100 -p1024 -n3 -i8 -o8[/COLOR]
 [COLOR=#999999]14:40:55.450 JACK was started with PID=3674.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 04134152394:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:03:51
 firewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 no message buffer overruns
 [COLOR=#999999]14:40:55.555 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]14:40:55.558 Post-shutdown script...[/COLOR]
 [COLOR=#990099]14:40:55.559 killall jackd[/COLOR]
 [COLOR=#CCCC99]14:40:55.640 ALSA connection change.[/COLOR]
 jackd: no process found
 [COLOR=#999999]14:40:55.972 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]14:40:57.647 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


Any help would be greatly appreciated.  
[COLOR=#FF0000][/COLOR]
[COLOR=#FF0000]
[/COLOR]

---

### Post by danielfernando on 2010-02-20
Hi  brucioamaphone ,

You'll need to get the subversion ffado driver to make it work. The card will be supported on the 2.1 version.
Instructions here: [http://subversion.ffado.org/wiki/DownloadFfadoSource](http://subversion.ffado.org/wiki/DownloadFfadoSource)

See Ya

Deedos

---

