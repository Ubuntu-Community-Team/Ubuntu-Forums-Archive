---
title: "Getting Oxygen8 MIDI USB Keyboard working."
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by TechSupportNoob on 2007-05-27
Hey Guys,

I'm relatively new to all of this, but a fairly fast learner when it comes to CLI type things.  

Anyway I just picked up Ubuntu Studio Audio from the repos and I'm eager to try my hand at making tunes with my new USB Oxygen8.

I've followed the instructions here so far.

> hi
just used the info in metasymbol's post to get an Oxygen 8 (v1) running with a laptop (compaq R4000) Very Happy Very Happy Very Happy
figured i would post the altered instructions that i used (very much similar), because the locations were different. I am using suse101 with jacklab repos.

first i installed FXload from SMART gui, then:

# mkdir /usr/share/midisport
# cd /usr/share/midisport/
# wget [http://homepage3.nifty.com/StudioBreeze/software/bin/usbmidi-20040829.tar.gz](http://homepage3.nifty.com/StudioBreeze/software/bin/usbmidi-20040829.tar.gz)
# tar -xzf usbmidi-20040829.tar.gz
# mv usbmidi-20040829/testing/MidiSport/*.ihx ./
# rm -R usbmidi-20040829
# lsusb
[now something like this appears - it can be various - your values will be different]
Bus 006 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
--my list says :
Bus 002 Device 002: ID 0763:1110 Midiman

[Here is what i put in for the fxload command:
# fxload -D /dev/bus/usb/002/002 -I ezusbmidi1x1.ihx

notice that oxygen 8 is a 1x1 device, not a 2x2 like metasymbol's, so i changed just that part, and the address of the device.
and now it shows up where it should, in jack and stuff.

[http://forum.jacklab.net/viewtopic.php?p=807&sid=29d364cdc6b15c283edc125267b79576](http://forum.jacklab.net/viewtopic.php?p=807&sid=29d364cdc6b15c283edc125267b79576)

When when I get to the last command to try to...I believe it's loading the firmware to the keyboard...correct me if I'm wrong...but yeah, now my keyboard showed up as being on Bus 003 and device 002 Example:

> thomas@thomas-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0763:0195 Midiman 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


...so I changed that accordingly.  And here is where I run into a brick wall:

thomas@thomas-desktop:/usr/share/midisport$ sudo fxload -D /dev/bus/usb/003/002 -I ezusbmidi1x1.ihx
can't modify CPUCS: Broken pipe

Okay...so where do I go from here?  I spent the $150.00 on the Oxygen8 and I sure don't want to have to take it back.  This is doable right?  It seems that the other guy got this going on his *nix box.

So any suggestions?  If you need any more info/clarification please ask.

-Tom

---

### Post by TechSupportNoob on 2007-05-27
Hello?  Anybody?

---

### Post by pneaveill on 2007-11-07
> **TechSupportNoob said:**
> Hey Guys,

I'm relatively new to all of this, but a fairly fast learner when it comes to CLI type things.  

Anyway I just picked up Ubuntu Studio Audio from the repos and I'm eager to try my hand at making tunes with my new USB Oxygen8.

I've followed the instructions here so far.


[http://forum.jacklab.net/viewtopic.php?p=807&sid=29d364cdc6b15c283edc125267b79576](http://forum.jacklab.net/viewtopic.php?p=807&sid=29d364cdc6b15c283edc125267b79576)

When when I get to the last command to try to...I believe it's loading the firmware to the keyboard...correct me if I'm wrong...but yeah, now my keyboard showed up as being on Bus 003 and device 002 Example:



...so I changed that accordingly.  And here is where I run into a brick wall:

thomas@thomas-desktop:/usr/share/midisport$ sudo fxload -D /dev/bus/usb/003/002 -I ezusbmidi1x1.ihx
can't modify CPUCS: Broken pipe

Okay...so where do I go from here?  I spent the $150.00 on the Oxygen8 and I sure don't want to have to take it back.  This is doable right?  It seems that the other guy got this going on his *nix box.

So any suggestions?  If you need any more info/clarification please ask.

-Tom

Let me be honest and upfront that I do not own one of these devices and the only reason that I even found you post here is that I am considering the purchase of this product also. That not withstanding, I hope that I can offer some more general info in the hopes of helping. [edit] Also, just because they told you to do this and that for one distro, does not always mean it will be automatic for ubuntu, as there are some minor differences -- and no, I am not a super linux geek that can part the *nix differences.[/edit]

As far as I am aware, the lsusb will give your settings on your computer. Translated, this means that yours will be different than mine, even if similar machines and setups.  Hence, trying to get your lsusb to match someone else's is a lesson in futility.  With all that said, your equipment should work with your lsusb, not try to live up to someone else's. What I would suggest is uninstalling all the stuff and starting over, letting the computer set itself up and posting that info here.

---

### Post by newsun on 2007-11-18
I just want to say that I have this same keyboard and I am very interested in getting it running, if OP or anyone else has the success info for ubuntu/kubuntu, I will be one giddy person.

So far I have done this...installed the midisport-firmware in the repos and I can get the device to show on with lsusb 

I will try the fxload option, which you may want to try again only with MidiSportKS.ihx file which is the one for the keystations including oxygen included in the midsport-firmware AFAIK

okay, so here is what I did, some before, some while I was in the middle of this response...

-first install midisport-firmware, this is in the repos and can be gotten via apt-get install midisport-firmware I believe(I used adept personally)

-next lsusb determine which bus/port your device is on
```
Bus 006 Device 001: ID 0000:0000
Bus 007 Device 008: ID 0763:1014 Midiman

```

-fxload - this was already installed on my machine install if you don't have it, it is in the repos(apt-get install fxload) below is the command I used basically
```
sudo fxload -D /dev/bus/usb/007/008 -I PATH-TO-IHX-FILE/MidiSportKS.ihx (I believe this is the PATH /lib/firmware/maudio/ I tried this one and one I downloaded and extracted to my home dir)

```

-loaded jack, qsynth, a soundfont for it and voila sounds coming out of my system via my oxygen

:guitar:

sweet, now I just need to get my presonus firebox up and running via the firewire so I can use the mic(currently just hard cabled in via headphone jack to get sound out)

P.S. I am running Kubuntu 7.10 Gutsy but should basically be the same for other ubuntu installs but I cannot say for sure.

---

