---
title: "Using JACK and FFADO with Lucid Lynx"
date: 2010-07-25
forum: Multimedia Software
---

### Post by seanlano on 2010-07-25
Previously I have used Ubuntu with a Presonus FP10 via JACK and FFADO (and FREEBoB before that) with few problems - it's a pain to set it up initially and needs to be done again every six months with the distribution updates - but once it goes it works like magic. I haven't used the FP10 for a while, not since last year I think, so I knew when I got it out last week that it might take a bit of fiddling around to get it working with Lucid. 
However, I did not anticipate it to be as difficult as it turned out to be. After following the guides [here]("https://help.ubuntu.com/community/UbuntuStudioPreparation") and [here]("https://help.ubuntu.com/community/FireWire") like I normally would, I still couldn't get it to work. 
So I looked around, and [found this]("http://ffado.org/?q=node/1316"). So then I installed libraw1394 v2.0.5 and compiled JACK and FFADO from SVN source, and installed kernel 2.6.33 realtime from [this ppa]("https://launchpad.net/~abogani/+archive/ppa"). Individually it seems that all the installations went well, but then when I try to start the JACK server, I get "*firewire ERR: Error creating FFADO streaming device. cannot load driver module firewire*". No matter what I did I could not get it to go. I've tried running jackd with gksudo, so I'm sure it's not a permissions problem. There was actually once when the server started for about a second, but then it pumped a load of error messages and crashed - and the red light on the FP10 didn't turn blue as it should when it is connected. 

What the hell do I need to do to get Ubuntu to talk to my FP10? Why doesn't FFADO just work, like it used to? It was fine in 9.04 and 9.10. Any ideas or suggestions at all would be appreciated.

---

### Post by cchhrriiss121212 on 2010-07-25
> What the hell do I need to do to get Ubuntu to talk to my FP10? Why  doesn't FFADO just work, like it used to? It was fine in 9.04 and 9.10.  Any ideas or suggestions at all would be appreciated.
To anyone using audio work I would recommend skipping 10.04 due to the lack of rt-kernel and the default kernels not supporting firewire (even in Ubuntu Studio). 
After you installed the rt kernel did you make sure you booted with it at GRUB? If so I would switch back to 9.10.

---

### Post by seanlano on 2010-07-26
Yeah, I was definitely using the Abogani realtime kernel. It didn't work. 


Is there really nothing that I can do to get it to work? What if I install an older kernel? (Although surely this can't be a good idea). What was changed? This is a huge backwards step for Ubuntu.

---

### Post by cchhrriiss121212 on 2010-07-26
AFAIK you have completed everything you need to do in order to get this going, so it's possible you may have made a mistake somewhere. 10.04 is not like this by design.
Does the jack message window show anything else?

---

### Post by seanlano on 2010-08-06
OK, I've tried it again. This is the message that JACK gives: 
```
20:15:10.431 Startup script...
20:15:10.432 artsshell -q terminate
sh: artsshell: not found
20:15:10.836 Startup script terminated with exit status=32512.
20:15:10.836 JACK is starting...
20:15:10.837 /usr/bin/jackd -P89 -dfirewire -r44100 -p512 -n2
jackd 0.119.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1535469
no message buffer overruns
JACK compiled with System V SHM support.
20:15:10.885 JACK was started with PID=2807.
loading driver ..
00515048102:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0-1871 built Jul 24 2010 10:30:16
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
20:15:11.283 JACK was stopped successfully.
20:15:11.284 Post-shutdown script...
20:15:11.285 killall jackd
jackd: no process found
20:15:11.701 Post-shutdown script terminated with exit status=256.
```

And I have attached a screenshot of the settings in qjackctl. 


What does this mean? Is there anything I'm missing in the ffado output?

I'll try getting the very latest FFADO and JACK from SVN again now, and see if that helps.

---

### Post by seanlano on 2010-08-06
Well, I've tried installing the most recent versions of FFADO, JACK and libraw1394 from their various SVN or GIT repositories. Then I rebooted. The error message I get now seems exactly the same, except for the listed compile date of the FFADO installation. 

```
21:04:57.936 Startup script...
21:04:57.937 artsshell -q terminate
sh: artsshell: not found
21:04:58.341 Startup script terminated with exit status=32512.
21:04:58.341 JACK is starting...
21:04:58.342 /usr/bin/jackd -P89 -dfirewire -r44100 -p512 -n2
jackd 0.119.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1535469
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
21:04:58.418 JACK was started with PID=2472.
00282551934:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0-1878 built Aug  6 2010 20:23:02
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
21:04:58.762 JACK was stopped successfully.
21:04:58.763 Post-shutdown script...
21:04:58.763 killall jackd
jackd: no process found
21:04:59.178 Post-shutdown script terminated with exit status=256.
```

What else is there to install? I read on the FFADO site that with the latest versions of these things my audio should work! :( What about compiling a RT kernel from source? I don't really want to do this though, and I can't see why it would help.

---

### Post by seanlano on 2010-08-06
Okay, I've done it! It works!!!!! :D

The FP10 has two firewire ports on the back of it, for daisy-chaining multiple units. I normally use port 1, just because it seems standard. However, I thought that after all my cursing of the software, I should double- and triple-check the hardware was working... and when I unplugged the cable from port 1 it felt a little wobbly. So I tried port 2, which felt much more solid. I then ran qjackctl just like normal, and it works! Amazing! 
So I guess someone else who uses this FP10 wasn't gentle enough with it (or it could have been me, hard to tell) and broke the internal connection. No wonder FFADO couldn't connect to it. 

Anyway, thanks for the help, and apologies if I annoyed anyone with my complaints about Ubuntu being crap. I love Ubuntu! ;)


So the moral of the story is: Install the Abogani RT kernel, compile FFADO and JACK from source ([described here]("http://subversion.ffado.org/wiki/Dependencies/Ubuntu")) and then install libraw1394 from the [Maverick archive]("https://launchpad.net/ubuntu/maverick/amd64/libraw1394-11/2.0.5-2ubuntu1") or from source. Then, make sure your hardware works, then it should run.

---

