---
title: "ATI TV Wonder Elite"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by leroy_30 on 2007-04-17
HELP! LOL. I am a huge noob when it comes to hardware config in linux. 

I am having trouble configuring my ATI TV Wonder Elite internal PCI-X card that came w/ my Dell E310. I have installed Ubuntu 6.10. 

Ubuntu Recognizes the card & Shows it as an ATI card but says Unknown.

I have searched high & low for idiot proof instructions on how to config this and am really getting frustrated. 

From what I gather this card should be supported under video4linux but I don't know how to config. I also noticed that there were no /dev/videoX files in the /dev directory.  I found a sh script that created these but every program keeps saying unable to open device. 

I'm into day 3 on trying to get this working and will probably fresh install today and start trying again. I would just like some guidance before I get too far into screwing up a fresh install.

If you need more info I would be happy to provide what I can...

Thanx in advance.

---

### Post by garlik42 on 2007-04-17
[https://help.ubuntu.com/community/MythTV_Dapper_hardware#head-83dbca2c20a36470fee58f582d0f9c274c1da43d](https://help.ubuntu.com/community/MythTV_Dapper_hardware#head-83dbca2c20a36470fee58f582d0f9c274c1da43d)

This is a set of instructions for getting a TV wonder to work with Mythtv, but it should bet you started.
At least to get a /dev/video0 device.

---

### Post by leroy_30 on 2007-04-17
I tried that exactly. the command 

```
sudo modprobe cx88-dvb
```

did nothing. As far as I can tell?

---

### Post by leroy_30 on 2007-04-17
I ran lspci -v and here is the output:


02:00.0 Multimedia controller: ATI Technologies Inc Unknown device 4d53
        Subsystem: Dell Unknown device a503
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at dfd00000 (32-bit, non-prefetchable) [size=1M]
        Memory at d0000000 (32-bit, prefetchable) [size=32M]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Express Endpoint IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable

Whatever that means?

---

### Post by leroy_30 on 2007-04-18
OK. THIS SUCKS!

I've fresh installed Edgy & updates.

followed the above intructions. nothing.

installed almost every video / tv prog i can find. nothing.

tvtime did setup the /dev but put them in /dev/.static/dev didn't work.

created symbolic link in /dev to /dev/.static/dev/video0 just to see. nothing.

everything keeps saying can't open or dosen't exist.

Is this just an issue w/ Edgy.

I have read a few old posts that says the Capture stuff will be supported in Dapper. Is it? did it break in Edgy.


GOING ON A RANT! Just ignore it I need to vent.

I'm thinking about switching to some other distro. It amazes me that as wonderful as ubuntu & linux in general is that noone has put together "Simple" instructions on how to get video capture and several other things to work. You just have to try to piece it together from a bunch of miscellaneous bits & pieces and hope you can make it work. I mean come on almost half a week to get something as simple as video capture to work if friggin retarded. Especially when EVERYWHERE I search someone is having this problem and some say they've got it to work so it's definately possible.

---

### Post by newlinux on 2007-05-19
You can rant, but I don't think your card is supported in Linux:

[http://linuxtv.org/v4lwiki/index.php/ATI/AMD](http://linuxtv.org/v4lwiki/index.php/ATI/AMD)

I don't know of any PCI express cards that are, yet.

---

