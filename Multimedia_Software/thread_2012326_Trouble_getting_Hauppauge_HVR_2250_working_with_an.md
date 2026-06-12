---
title: "Trouble getting Hauppauge HVR 2250 working with any tv viewer"
date: 2012-06-28
forum: Multimedia Software
---

### Post by Colonel Forbin on 2012-06-28
I am just trying to return to ubuntu and can not get my tv tuner working. I have read through the forums and tried several fixes, including setting up the firmware, drivers, mythtv, zapping, me tv and several others. I can not get any program to recognize my card, although a dmesg | grep shows it as card 7 at dev/video1. I'm a noob, so any help would be much appreciated.

Thanks
Forbin

---

### Post by MartyBuntu on 2012-06-29
How is your card set up?

What is your video source (cable, antenna...etc..)

---

### Post by Colonel Forbin on 2012-06-29
My video source is cable. I'm not sure exactly what you mean by how is it set up. It is a Hauppauge HVR 2250. I have installed the firmware and drivers already. But none of the tv viewers will even recognize it's there.

---

### Post by MartyBuntu on 2012-06-30
Which TV viewers have you tried?

---

### Post by fixitdude on 2012-06-30
Some of the other ones you might try are Kaffeine and Mplayer, also xawtv works on NTSC video pretty well and is easy to use, I've even used xine but it's not very friendly for TV tuning.

I've also got a pretty cool little TV recording program you might want to try:
[http://ubuntuforums.org/showthread.php?t=2009778](http://ubuntuforums.org/showthread.php?t=2009778)

You could use it to schedule and record shows at certain times / days. Just change the mencoder line a little so it works for your device. If you ever get a DVB tuner instead this will work great.

---

### Post by Colonel Forbin on 2012-07-01
I have tried mythtv, xawtv, zapping, me tv, tvtime. xawtv recognizes my camera as a video source, but not my card. Mythtv seems to recognize the card, but not show video from it.

---

### Post by Colonel Forbin on 2012-07-04
bump

---

### Post by fixitdude on 2012-07-14
All of this ATSC stuff is sort of new and you want to be on Ubuntu 12.04, which is a pain to upgrade to, it's better to do a new install.

I had to do that to get my USB tuner to work, I tried compiling the latest drivers and that didn't make it so I had to bite the bullet and "upgrade" which ended up being a new install, but I left my home folder intact.

My method of figuring out what is wrong would be to look at dmesg and see where it shows your card is being detected. You just read the lines, people always freak out but there's a lot of info there, take it slow and actually read what it says, people's eyes glaze over and they try to take the whole screen in at once like it's a batman TV show but it makes better sense one line at a time.

You can post the lines here and maybe someone will see something.

A ATSC tuner will show up as /dev/dvb/adapter0/ or something like that then there will be a "frontend", if you don't see something like that then a driver isn't loading for it and you might visit this site to see if it's supported and also read around and see what's up etc...

[http://linuxtv.org/wiki/index.php/Hardware_Device_Information](http://linuxtv.org/wiki/index.php/Hardware_Device_Information)

Did you find this page with google? It shows that it's been supported since 2008 and there's an example of the dmesg output you can compare.

[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250)

See this

"DVB: registering adapter 0 frontend 0"

And kaffeine should pick that up and start using it.

I also upgraded to the 3.3.6 kernel, check my other posts. It works better but did work with the old kernel (sometimes).

You also want to make sure you have a strong TV signal for testing, it helps to have a TV box to compare against, I didn't but it would have been nice.

And you also want to know a little about what type of TV broadcasts are in your area and if this is even going to work at all.

And I hate to say this, try it on windows and see if it works there.

And while I am editing this, kaffeine is the best thing for ATSC I found, so you really want to use that. And you have to do a SCAN of your channels so it will know where to tune, if you can't scan you are sort of screwed without a channels.conf file.

Read some of my posts about all that.

---

### Post by jessicasix on 2012-08-19
I would love to get this working too.
I've tried going through the documentation, from a few sources, but I get lost and can't get it to work the way it should.
My card is:

02:00.0 Multimedia controller: Philips Semiconductors SAA7164 (rev 81)
    Subsystem: Hauppauge computer works Inc. WinTV HVR-2250
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at df400000 (64-bit, non-prefetchable) [size=4M]
    Memory at df000000 (64-bit, non-prefetchable) [size=4M]
    Capabilities: <access denied>
    Kernel driver in use: saa7164
    Kernel modules: saa7164

Is there a good straight forward document somewhere describing how to make it work, or will it maybe 'just work by itself' with a future version of Ubuntu, like my old TV card did?  :)

---

### Post by dlparker on 2012-11-30
> **jessicasix said:**
> I would love to get this working too.
I've tried going through the documentation, from a few sources, but I get lost and can't get it to work the way it should.
My card is:

02:00.0 Multimedia controller: Philips Semiconductors SAA7164 (rev 81)
    Subsystem: Hauppauge computer works Inc. WinTV HVR-2250
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at df400000 (64-bit, non-prefetchable) [size=4M]
    Memory at df000000 (64-bit, non-prefetchable) [size=4M]
    Capabilities: <access denied>
    Kernel driver in use: saa7164
    Kernel modules: saa7164

Is there a good straight forward document somewhere describing how to make it work, or will it maybe 'just work by itself' with a future version of Ubuntu, like my old TV card did?  :)

I got my 2250 on Thursday and I've been scouring the net for advice, too. I've got mine recognized and the /dev/dvb/adapter[0-1] nodes loaded, but I'm not picking up any program material. Surewest KC says I should be able to pick up clear QAM, and we have two other tvs in the house plugged right into cable with no set top box and they're working fine. I've tried it on both kernel 3.6.7-4 and 3.6.8-2 with the same results.

Anyone had any luck with the 3.6.x kernels?

---

