---
title: "Problems with JACK"
date: 2009-07-29
forum: Multimedia Software
---

### Post by pianoman91210 on 2009-07-29
[COLOR=Red][SIZE=3][FONT=Comic Sans MS]Ok, so I'm a bit new to Ubuntu 8.10, and I realized some programs have to be run with JACK (Ex. Ardour, Rack Jack, Rakarrack, etc.) but for some reason, I keep getting this message after it starts, then I stop it: :confused:

[/FONT][/SIZE][/COLOR]  p, li { white-space: pre-wrap; }  [COLOR=#cc0000]jackd 0.109.2[/COLOR]
 [COLOR=#cc0000]Copyright 2001-2005 Paul Davis and others.[/COLOR]
 [COLOR=#cc0000]jackd comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=#cc0000]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=#cc0000]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=#cc0000]JACK compiled with System V SHM support.[/COLOR]
 [COLOR=#cc0000]loading driver ..[/COLOR]
 [COLOR=#cc0000]SSE2 detected[/COLOR]
 [COLOR=#cc0000]apparent rate = 44100[/COLOR]
 [COLOR=#cc0000]creating alsa driver ... hw:0,0|hw:0,0|64|2|44100|0|0|nomon|swmeter|-|32bit[/COLOR]
 [COLOR=#cc0000]control device hw:0[/COLOR]
 [COLOR=#cc0000]configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 2 periods[/COLOR]
 [COLOR=#cc0000]ALSA: final selected sample format for capture: 16bit little-endian[/COLOR]
 [COLOR=#cc0000]ALSA: use 2 periods for capture[/COLOR]
 [COLOR=#cc0000]ALSA: final selected sample format for playback: 16bit little-endian[/COLOR]
 [COLOR=#cc0000]ALSA: use 2 periods for playback[/COLOR]
 [COLOR=#cc0000]**** alsa_pcm: xrun of at least 1248882268831.744 msecs[/COLOR]
 [COLOR=#cc0000]**** alsa_pcm: xrun of at least 1248882268831.744 msecs[/COLOR]
 [COLOR=#cc0000]**** alsa_pcm: xrun of at least 1248882268831.744 msecs[/COLOR]
 [COLOR=#cc0000]**** alsa_pcm: xrun of at least 1248882268831.744 msecs[/COLOR]
 [COLOR=#cc0000][COLOR=#999933]12:14:00.715 Server configuration saved to "/home/mark/.jackdrc".[/COLOR][/COLOR]
 [COLOR=#cc0000][COLOR=#999999]12:14:00.717 Statistics reset.[/COLOR][/COLOR]
 [COLOR=#cc0000][COLOR=#999999]12:14:00.718 Client activated.[/COLOR][/COLOR]
 [COLOR=#cc0000][COLOR=#9999cc]12:14:00.722 JACK connection change.[/COLOR][/COLOR]
 [COLOR=#cc0000][COLOR=#cc9966]12:14:00.738 JACK connection graph change.[/COLOR][/COLOR]
 [COLOR=#cc0000]**** alsa_pcm: xrun of at least 1248882268831.744 msecs[/COLOR]
 [COLOR=#cc0000]SSE2 detected[/COLOR]
 [COLOR=#cc0000]**** alsa_pcm: xrun of at least 1248882268831.744 msecs[/COLOR]
 [COLOR=#cc0000]**** alsa_pcm: xrun of at least 1248882268831.744 msecs[/COLOR]
 [COLOR=#cc0000][COLOR=#cc66cc]12:14:00.750 XRUN callback (1).[/COLOR][/COLOR]
 [COLOR=#cc0000]**** alsa_pcm: xrun of at least 1248882268831.744 msecs[/COLOR]
 [COLOR=#cc0000][COLOR=#6699cc]12:14:00.927 Audio active patchbay scan...[/COLOR][/COLOR]
 [COLOR=#cc0000]**** alsa_pcm: xrun of at least 1248882268831.744 msecs[/COLOR]
 [COLOR=#cc0000][COLOR=#cc99cc]12:14:02.752 XRUN callback (3 skipped).[/COLOR][/COLOR]
 [COLOR=#cc0000][COLOR=#cc66cc]12:14:02.784 XRUN callback (5).[/COLOR][/COLOR]
 [COLOR=#cc0000]**** alsa_pcm: xrun of at least 1248882268831.744 msecs[/COLOR]
 [COLOR=#cc0000]**** alsa_pcm: xrun of at least 1248882268831.744 msecs[/COLOR]
 [COLOR=#cc0000][COLOR=#cc99cc]12:14:04.778 XRUN callback (1 skipped).[/COLOR][/COLOR]
 [COLOR=#cc0000][COLOR=#999999]12:14:05.460 Client deactivated.[/COLOR][/COLOR]
 [COLOR=#cc0000][COLOR=#999999]12:14:05.462 JACK is stopping...[/COLOR][/COLOR]
 [COLOR=#cc0000]jack main caught signal 15[/COLOR]
 [COLOR=#cc0000]**** alsa_pcm: xrun of at least 1248882268831.744 msecs[/COLOR]
 [COLOR=#cc0000]no message buffer overruns[/COLOR]
 [COLOR=#cc0000][COLOR=#999999]12:14:05.478 JACK was stopped successfully.[/COLOR][/COLOR]
 [COLOR=#cc0000][COLOR=#999999]12:14:05.479 Post-shutdown script...[/COLOR][/COLOR]
 [COLOR=#cc0000][COLOR=#990099]12:14:05.479 killall jackd[/COLOR][/COLOR]
 [COLOR=#cc0000]jackd: no process killed[/COLOR]
 [COLOR=#cc0000][COLOR=#999999]12:14:05.893 Post-shutdown script terminated with exit status=256.[/COLOR][/COLOR]
[COLOR=#cc0000]
[/COLOR]
[COLOR=#cc0000][SIZE=3][FONT=Comic Sans MS]Now JACK runs fine with other programs on, but does anyone have an idea what that could be, and how I can fix it & maybe find the information for setup JACK (Ex. Interface, Rates) ? Also, my line-in just randomly stopped working a while back and now only the microphone works with some digital noise - why is that? Please help![/FONT][/SIZE] :(
[/COLOR]

---

### Post by markbuntu on 2009-07-30
You should really run jack with the rt kernel and the one in intrepid has problems. That said, you can try changing the buffers higher and the buffer size higher. 

Here are some links to help with setting up jack


[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

---

