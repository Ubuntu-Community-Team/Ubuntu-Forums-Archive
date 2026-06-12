---
title: "Jack (through QjackCtl) not working"
date: 2011-12-29
forum: Multimedia Software
---

### Post by helasraizam on 2011-12-29
I am new at using ardour, which requires Jack.  It didn't work the first few times I loaded it; Ardour had two input options (aquire 1 and 2), both of which seemed to correspond to how much memory I used in my computer:confused:.  Regardless, I got my usb logitech mic to work when I started jack, put as input the microphone itself, set channel to 1, and started a new recording session on ardour with 1 channel max under the options--you can imagine how much trial and error went into this achievement.  Now, I'd like to learn it properly from you gurus.
As you guessed, it's not that simple.  Now that I've restarted my computer, jack will start the first time by whatever options I ask it to, but ardour will not hear the usb microphone (it lists again "acquire 1" and "acquire 2" to my dismay).  When I go to restart jack, however, it gives me the following error message in the message window:
```

[COLOR=#999999] 18:47:00.213 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]18:47:00.214 Statistics reset.[/COLOR]
 [COLOR=#cccc99]18:47:00.226 ALSA connection change.[/COLOR]
 [COLOR=#999999]18:47:00.245 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]18:47:00.254 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]18:47:03.535 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: driver "alsa" selected
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Saving settings to "/home/helasraizam/.config/jack/conf.xml" ...
 Thu Dec 29 18:47:03 2011: Starting jack server...
 Thu Dec 29 18:47:03 2011: JACK server starting in non-realtime mode
 Thu Dec 29 18:47:03 2011: [1m[31mERROR: Cannot lock down memory area (Cannot allocate memory)[0m
 Thu Dec 29 18:47:03 2011: control device hw:0
 Thu Dec 29 18:47:03 2011: control device hw:0
 Thu Dec 29 18:47:03 2011: [1m[31mERROR: Failed to acquire device name : Audio0 error : Input/output error[0m
 Thu Dec 29 18:47:03 2011: [1m[31mERROR: Audio device hw:0 cannot be acquired, trying to open it anyway...[0m
 Thu Dec 29 18:47:03 2011: creating alsa driver ... hw:0|hw:0|1024|3|44100|1|0|nomon|swmeter|-|32bit
 Thu Dec 29 18:47:03 2011: control device hw:0
 Thu Dec 29 18:47:03 2011: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
 Thu Dec 29 18:47:03 2011: ALSA: final selected sample format for capture: 32bit integer little-endian
 Thu Dec 29 18:47:03 2011: [1m[31mERROR: ALSA: cannot set channel count to 1 for capture[0m
 Thu Dec 29 18:47:03 2011: [1m[31mERROR: ALSA: cannot configure capture channel[0m
 Thu Dec 29 18:47:03 2011: [1m[31mERROR: Cannot initialize driver[0m
 Thu Dec 29 18:47:03 2011: [1m[31mERROR: JackServer::Open() failed with -1[0m
 Thu Dec 29 18:47:03 2011: [1m[31mERROR: Failed to open server[0m
 [COLOR=#ff0000]18:47:06.577 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started


```All options are default (and I've tried 1 channel, setting input to mic, etc.) except realtime, which is turned off (of course, I've also tried it with realtime on).  When I restart the x server (ctl+alt+bkspc), jack will start once more, but not again thereafter, and the one time it does work, Ardour does not recognize the mic.

Thanks for your help!  (Quick note: the data you see is the data I got, , , were also displayed as symbols in the message window).

EDIT: More good news, my sound isn't working atm.  This is after logging in, turning jack on, turning ardour on, turning jack and ardour off.  I know that restarting (x-server) will fix it.

---

### Post by helasraizam on 2011-12-29
Hi guys!  So after checking the forums I realized quickly that this topic is not among the oft answered.  I did find [http://ubuntuforums.org/showthread.php?t=1423874](http://ubuntuforums.org/showthread.php?t=1423874) helpful in telling me that the default ubuntu package is jackd1, not jackd2.  I therefore uninstalled jackd1 and jackd2 and jackd and all firewires with "complete uninstall" to remove any faulty settings I created.  This also removed ardour.  I then rebooted and installed jackd1-firewire, then jackd1, which automatically installed jackd.  Finally, I installed Ardour.  At this point, QjackCtl was either already installed, or I installed it.

In any case, it I was able to open and run QjackCtl without a problem.  When I ran Ardour, it still did not recognize my microphone.  So I closed it and set the input in QjackCtl to be my microphone, closed Ardour, restarted Jack through QjackCtl, and reopened Ardour.  Now I had only one input (the microphone).

Now I know what this emote is for..
:guitar:

---

### Post by stuartcnz on 2012-01-01
The one input only thing, maybe hardware related. I use a Lexicon Omega as my audio interface. When I use it on a mackbook, running Ubuntu 10.04 Lucid, I can only get I think two inputs, recognised by Jack. When I use it on my desktop, which has a ton of horsepower and also running Lucid, it recognises all of the Lexicon's inputs and outputs.

---

