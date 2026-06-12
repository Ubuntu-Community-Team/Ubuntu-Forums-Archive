---
title: "Unable to get Jack to produce sound through alsa"
date: 2011-03-20
forum: Multimedia Software
---

### Post by xaegis on 2011-03-20
I am using Ubuntu 10.10 x64 on a Dell Studio XPS

I am unable to get JACK to make any sound from any of the applications which plug into it.
Can someone please check over my setup and let me know if I'm doing something wrong.

```

lspci:
me@TheComputer:~/Desktop$ lspci
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)



me@TheComputer:~/Desktop$ cat /proc/asound/cards
 0 [Intel             ]: HDA-Intel - HDA Intel
                             HDA Intel at 0xf1000000 irq 53
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                             HD-Audio Generic at 0xcfedc000 irq 54
  
me@TheComputer:~/Desktop$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel


me@TheComputer:~/Desktop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

me@TheComputer:~/Desktop$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

```


and here is the output from the jack server:

```

22:44:09.383 Patchbay deactivated.
22:44:09.389 Statistics reset.
22:44:09.413 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
22:44:09.490 Startup script...
22:44:09.491 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
22:44:09.493 ALSA connection graph change.
sh: artsshell: not found
22:44:09.892 Startup script terminated with exit status=32512.
22:44:10.135 D-BUS: JACK server is starting...
22:44:10.147 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).
22:44:10.337 ALSA connection change.
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: driver "alsa" selected
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Saving settings to "/home/me/.config/jack/conf.xml" ...
Sun Mar 20 22:44:09 2011: Starting jack server...
Sun Mar 20 22:44:09 2011: JACK server starting in realtime mode with priority 1
Sun Mar 20 22:44:09 2011: Acquired audio card Audio0
Sun Mar 20 22:44:09 2011: Acquired audio card Audio1
Sun Mar 20 22:44:09 2011: creating alsa driver ... hw:1,3|hw:0,0|1024|3|48000|0|0|nomon|swmeter|-|32bit
Sun Mar 20 22:44:09 2011: Using ALSA driver HDA-Intel running on card 1 - HD-Audio Generic at 0xcfedc000 irq 54
Sun Mar 20 22:44:09 2011: configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 3 periods
Sun Mar 20 22:44:09 2011: ALSA: final selected sample format for capture: 32bit integer little-endian
Sun Mar 20 22:44:09 2011: ALSA: use 3 periods for capture
Sun Mar 20 22:44:10 2011: ALSA: final selected sample format for playback: 16bit little-endian
Sun Mar 20 22:44:10 2011: ALSA: use 3 periods for playback
Sun Mar 20 22:44:10 2011: graph reorder: new port 'system:capture_1'
Sun Mar 20 22:44:10 2011: New client 'system' with PID 0
Sun Mar 20 22:44:10 2011: graph reorder: new port 'system:capture_2'
Sun Mar 20 22:44:10 2011: graph reorder: new port 'system:playback_1'
Sun Mar 20 22:44:10 2011: graph reorder: new port 'system:playback_2'

```


What am I doing wrong?
I tried the youtube tutorials and some ubuntu forum tutorials from 2008 to no avail.
Thanks in advance

---

### Post by lidex on 2011-03-21
Have a look here:
[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

---

### Post by xaegis on 2011-03-26
> **lidex said:**
> Have a look here:
[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

I couldn't find any configuration onformation or links in the wikipedia site. Most of the tutorials are very old. (ubuntu 8-9) and the underlying infrastructure seems to have changed a bit. I don't want to just install a bunch of stuff from depreciated packages just to see if it works. Does anyone have a source of "current" configuration troubleshooting help?

Thanks,

  :D

---

### Post by xaegis on 2011-03-26
ok i ran the command :cat /proc/asound/cards


and got:
```

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf1000000 irq 52
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xcfedc000 irq 54

```

but what does it mean. Which sound card SHOULD I be using for jack and what does the HD-Audio generic card Do anyway? Is it the HDMI external audio port?

Thanks in advance.

---

### Post by xaegis on 2011-03-26
Well, I should mark this thread as solved because sound is now working through alsa, but I don't understand why. Should my input device and output device be the same device?
What is this doing?

---

### Post by cchhrriiss121212 on 2011-03-26
You have 2 sound devices, the first is your on board audio (hw:0), the second is your HDMI output (hw:1). 
> 
Should my input device and output device be the same device?
Yes, jack does not handle multiple sound cards. Select hw:0 as your interface, then leave input/output selection as default, the rest of your settings are fine.

---

### Post by xaegis on 2011-03-26
> **cchhrriiss121212 said:**
> You have 2 sound devices, the first is your on board audio (hw:0), the second is your HDMI output (hw:1). 

Yes, jack does not handle multiple sound cards. Select hw:0 as your interface, then leave input/output selection as default, the rest of your settings are fine.

AWESOME! Thanks for enlightening me!:D

---

### Post by Amicum on 2011-10-16
Hi, I have some problems whit JACK on Ubuntu 11.10 x64. 
 p, li { white-space: pre-wrap; }  [COLOR=#FF0000]
[/COLOR]
[COLOR=#ff0000]11:44:02.793 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: driver "alsa" selected
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Saving settings to "/home/rok/.config/jack/conf.xml" ...
 Sun Oct 16 11:44:02 2011: Starting jack server...
 Sun Oct 16 11:44:02 2011: JACK server starting in realtime mode with priority 1
 Sun Oct 16 11:44:02 2011: control device hw:1
 Sun Oct 16 11:44:02 2011: control device hw:1
 Sun Oct 16 11:44:02 2011: [1m[31mERROR: Failed to acquire device name : Audio1 error : Input/output error[0m
 Sun Oct 16 11:44:02 2011: [1m[31mERROR: Audio device hw:1 cannot be acquired, trying to open it anyway...[0m
 Sun Oct 16 11:44:02 2011: creating alsa driver ... hw:1|hw:1|32|2|48000|1|1|nomon|hwmeter|soft-mode|32bit
 Sun Oct 16 11:44:02 2011: control device hw:1
 Sun Oct 16 11:44:02 2011: configuring for 48000Hz, period = 32 frames (0.7 ms), buffer = 2 periods
 Sun Oct 16 11:44:02 2011: ALSA: final selected sample format for capture: 24bit little-endian
 Sun Oct 16 11:44:02 2011: [1m[31mERROR: ALSA: cannot set channel count to 1 for capture[0m
 Sun Oct 16 11:44:02 2011: [1m[31mERROR: ALSA: cannot configure capture channel[0m
 Sun Oct 16 11:44:02 2011: [1m[31mERROR: Cannot initialize driver[0m
 Sun Oct 16 11:44:02 2011: [1m[31mERROR: JackServer::Open() failed with -1[0m
 Sun Oct 16 11:44:02 2011: [1m[31mERROR: Failed to open server[0m
 [COLOR=#ff0000]11:44:04.095 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started


I tray to reconfigure JACK for several times and it doesn't work. I need some help, please!

---

