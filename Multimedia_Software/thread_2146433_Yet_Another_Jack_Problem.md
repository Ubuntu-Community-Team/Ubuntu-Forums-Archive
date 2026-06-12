---
title: "Yet Another Jack Problem"
date: 2013-05-18
forum: Multimedia Software
---

### Post by ajukilibodin on 2013-05-18
I am trying to connect my guitar to my laptop through a USB interface but it's failing, this is what qjackctl tells me 

```
 [COLOR=#999999]17:33:02.840 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]17:33:02.841 Statistics reset.[/COLOR]
 [COLOR=#cccc99]17:33:02.890 ALSA connection change.[/COLOR]
 [COLOR=#999999]17:33:02.900 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#66cc99]17:33:02.906 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]17:33:09.166 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Sat May 18 17:33:09 2013: Starting jack server...
 Sat May 18 17:33:09 2013: JACK server starting in realtime mode with priority 10
 Sat May 18 17:33:09 2013: [1m[31mERROR: Cannot lock down 82246176 byte memory area (Cannot allocate memory)[0m
 Sat May 18 17:33:09 2013: [1m[31mERROR: can't load "/usr/lib/x86_64-linux-gnu/jack/jack_alsa.so": /usr/lib/x86_64-linux-gnu/jack/jack_alsa.so: undefined symbol: jack_driver_nt_init[0m
 Sat May 18 17:33:09 2013: [1m[31mERROR: Cannot initialize driver[0m
 Sat May 18 17:33:09 2013: [1m[31mERROR: JackServer::Open() failed with -1[0m
 Sat May 18 17:33:09 2013: [1m[31mERROR: Failed to open server[0m
 Sat May 18 17:33:11 2013: Saving settings to "/home/ajuk/.config/jack/conf.xml" ...
 [COLOR=#ff0000]17:33:19.256 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


```

Some blog said to uninstall jackd2 and install jackd1. That didn't help either

```
ajuk@Monster:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```
```
ajuk@Monster:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 045e:077b Microsoft Corp. 
Bus 002 Device 004: ID 04f2:b249 Chicony Electronics Co., Ltd 
Bus 002 Device 005: ID 08bb:2902 Texas Instruments Japan PCM2902 Audio Codec


```

Sensei, what do I do?

---

### Post by ajukilibodin on 2013-05-18
Good news, got it working (somehow??) but I am unable to connect the USB to output. Whenever I run rakarrack and qjackctl together, system has no sound. Tried to connect them together, but it detects my laptops mic, not the USB guitar interface :/

---

### Post by jukingeo on 2013-05-18
I have the same exact problem with Jack in Ubuntu Studio 12.04...I get that darn D-bus error.   The strange thing is that I CAN use the connections panel and set up a soft synth or sampler to work with Jack and a midi keyboard (Virtual Keyboard).  But if I try to use a sequencer and push the play button?  Wham!  D-bus error.   Anyway, I did make a post about it here, but I find it curious that you went back to the old version of Jack.   I thought the old version was buggy too, yet there were times I did get it to work fine.   I had hoped that by going with 12.04 and having a new version of Jack that things were going to be better with it.   Apparently, it seems Jack still has problems.

Really, I think since there were so many problems with Jack for so long that I think it would be best to nix the Jack project and just come up with something better that actually works.

Geo

---

### Post by ajukilibodin on 2013-05-18
It works if I run qjackctl AND rakarrack. But then jack doesn't detect my guitar input :/ Sigh

---

### Post by ajukilibodin on 2013-05-19
*bump*

---

