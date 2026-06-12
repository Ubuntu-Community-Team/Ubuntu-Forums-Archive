---
title: "Jack not starting in kxstudio"
date: 2011-04-24
forum: Multimedia Software
---

### Post by poodoopealeoaph on 2011-04-24
I just installed KXstudio and I got everything else working on my system but I can't seem to get jack to start. When I check the message screen it doesn't plainly tell me where things are going wrong. So I was hoping that someone could help me to figure this out. The message box reads... ```
22:10:53.564 Patchbay deactivated.
22:10:53.568 Statistics reset.
22:10:53.607 ALSA connection change.
22:10:53.614 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
22:10:53.652 ALSA connection graph change.
22:10:56.172 Startup script...
22:10:56.173 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
22:10:56.575 Startup script terminated with exit status=32512.
22:10:56.710 D-BUS: JACK server could not be started. Sorry
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: driver "alsa" selected
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Saving settings to "/home/adam/.config/jack/conf.xml" ...
Sun Apr 24 22:10:56 2011: Starting jack server...
Sun Apr 24 22:10:56 2011: JACK server starting in realtime mode with priority 10
Sun Apr 24 22:10:56 2011: control device hw:0
Sun Apr 24 22:10:56 2011: control device hw:0
Sun Apr 24 22:10:56 2011: [1m[31mERROR: Failed to acquire device name : Audio0 error : Input/output error[0m
Sun Apr 24 22:10:56 2011: [1m[31mERROR: Audio device hw:0 cannot be acquired, trying to open it anyway...[0m
Sun Apr 24 22:10:56 2011: creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
Sun Apr 24 22:10:56 2011: control device hw:0
Sun Apr 24 22:10:56 2011: Using ALSA driver HDA-Intel running on card 0 - HDA NVidia at 0xded78000 irq 22
Sun Apr 24 22:10:56 2011: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
Sun Apr 24 22:10:56 2011: ALSA: final selected sample format for capture: 32bit integer little-endian
Sun Apr 24 22:10:56 2011: ALSA: use 3 periods for capture
Sun Apr 24 22:10:56 2011: ALSA: final selected sample format for playback: 32bit integer little-endian
Sun Apr 24 22:10:56 2011: [1m[31mERROR: ALSA: got smaller periods 2 than 3 for playback[0m
Sun Apr 24 22:10:56 2011: [1m[31mERROR: ALSA: cannot configure playback channel[0m
Sun Apr 24 22:10:56 2011: [1m[31mERROR: Cannot initialize driver[0m
Sun Apr 24 22:10:56 2011: [1m[31mERROR: JackServer::Open() failed with -1[0m
Sun Apr 24 22:10:56 2011: [1m[31mERROR: Failed to start server[0m
22:10:58.968 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

---

### Post by poodoopealeoaph on 2011-04-29
I just wanted to add that KXstudio was not that impressive from the experience I had last week. It had trouble running streaming video, it couldn't start jack, and it only installs on systems with very specific settings. If you really want a good recording system I would highly recommend getting regular Ubuntu and just typing: ```
sudo apt-get install ubuntustudio-audio
``` and ```
sudo apt-get install ubuntustudio-audio-plugins
```... then just add yourself to the audio group and you are good to go...

the whole reason why I don't recommend ubuntu studio is because it only works good if you never want updates and you never want to be able to use the internet. I know you can get it to work right but unless you really want to mess around with your computer for like four hours, you should probably just get regular ubuntu and install the packages...

---

### Post by falkTX on 2011-05-03
Well, as I can see from your jack log, you didn't configured JACK properly (just a minor detail):
```
Sun Apr 24 22:10:56 2011: ERROR: ALSA: got smaller periods 2 than 3 for playback
```

Just change the [buffer] periods from 3 to 2, and it JACK should start fine again.

---

