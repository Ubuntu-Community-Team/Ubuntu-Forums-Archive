---
title: "Nvidia ION for remote frontend?"
date: 2009-05-24
forum: Mythbuntu
---

### Post by epi 1:10,000 on 2009-05-24
Is anyone planing on trying this?

---

### Post by nickrout on 2009-05-24
I think almost anyone who uses myth is thinking its going to be a great option.

---

### Post by bernied on 2009-10-14
Not sure if the OP of this thread is still watching ?
Did you get an ION machine?

I'm about to try this, but haven't decided on the details. 

I have found the Acer Revo systems available in the UK, and a few more options available from the US. Generally they are marketed as a 'nettop' or mini itx systems. I don't really want to build it myself, as I'll have enough to do sorting out the software.

But I haven't decided between the single and dual core options. I want a fanless system, but I also want it to be a bit future proof (HD). Most of the dual core (Atom 330) systems seem to ship with a fan, but this is sometimes described as 'optional', so it sounds like operating without a fan is marginal.

Google tells me that the Revo has a fan, and some find it annoying, so I think that's out.

I plan to use flash memory with an adapter as a boot device (no disk), and would consider underclocking as well, if it would keep the thing silent.

I would love to see a mythtv-frontend centric review on these options.

Also see this thread:
[http://ubuntuforums.org/showthread.php?t=1235837](http://ubuntuforums.org/showthread.php?t=1235837)

Bernie

---

### Post by Marky Mark on 2009-10-28
THe Revo does have a fan, but we sleep with it turned on (same room) and cannot hear anything, and I'm a light sleeper.  It makes a whoosh when it starts, but after that settles down to almost silent.  I am a middle aged heavy metal fan, but my hearing is still pretty good;)

Good luck MyM

---

### Post by bernied on 2009-11-01
> **Marky Mark said:**
> THe Revo does have a fan, but we sleep with it turned on (same room) and cannot hear anything, and I'm a light sleeper.  It makes a whoosh when it starts, but after that settles down to almost silent.  I am a middle aged heavy metal fan, but my hearing is still pretty good;)

Good luck MyM
Thanks for your review of the Revo. But can you clarify which one you have? There seem to be models with either single or dual core (at least in the UK0, and the dual cores probably need a bit more cooling.

I don't plan to sleep in the same room, just don't like a background hum when reading or chatting.

So it might be a good'n.

If I get it, and it's noisy, I'll let you know that the 'music' wasn't so good for you.

---

### Post by DominicF on 2009-11-02
Hi,

I also have a Revo and recently installed mythfrontend which works very nicely for watching recording and liveTV from a backend machine.  My Revo is the single core version.

---

### Post by fatmonk on 2009-11-03
DominicF,

Do you know if the VGA output on the Revo is S-video capable?

I've been looking at the Revo as a front-end, but the TV it will initially be connected to doesn't have any digital (HDMI/DVI etc) or VGA inputs, just SCART and S-Video.

Cheers,

FM

---

### Post by nickrout on 2009-11-03
> **fatmonk said:**
> DominicF,

Do you know if the VGA output on the Revo is S-video capable?

I've been looking at the Revo as a front-end, but the TV it will initially be connected to doesn't have any digital (HDMI/DVI etc) or VGA inputs, just SCART and S-Video.

Cheers,

FM

Is the TV's SCART connector RGB or not? There are VGA-SCART adaptors available. See google.

The last thing you want to do is downgrade to s-video. Yuk.

---

### Post by hackmeister on 2009-11-04
I have an Nvidia Ion MythTV frontend:
[http://pdavila.homelinux.org:8080/blog/?p=347](http://pdavila.homelinux.org:8080/blog/?p=347)
[http://pdavila.homelinux.org:8080/blog/?p=348](http://pdavila.homelinux.org:8080/blog/?p=348)
[http://pdavila.homelinux.org:8080/blog/?p=349](http://pdavila.homelinux.org:8080/blog/?p=349)

To hook up the my Ion box to a SDTV I had to pickup a vga to s-video converter for about $35:
[http://sewelldirect.com/PC-to-TV-Converter.asp](http://sewelldirect.com/PC-to-TV-Converter.asp)

The Zotac board only has hdmi, dvi or vga connections.

---

### Post by perlLlama on 2009-11-04
Hi all

I just built a frontend based on the Nvidia ION chip and Atom processor it is sweet.  Mini ITX board, 2.5" harddrive and and dinky little case. The board has HDMI out, which makes my life so much easer, no more jerking around with the xorg.conf to set the right modes for VGA.

Almost silent, I have a small case fan. 

Using nvpdau the processor hits a max of 3% with video playback. With Myth running, this jumps up to around 15%.

Sound through HDMI was not working until I set the correct setting in 'setup -> general'. 

It's the future..........

---

### Post by ZedThou on 2009-11-04
MIght as well jump in here as well. I have an IONITX-A with a couple of laptop hard drives and an HDHomeRun serving as a complete silent low-power HTPC. It's completely up to the task.

---

### Post by byronmyth on 2009-12-03
Can I ask which VDPAU interlace setting you are using with your ION?

---

### Post by stefangr1 on 2009-12-03
Yet another question...

I know the ethernet chip works with Ubuntu, but are gbit speeds supported with the default driver? I'm considering buying an ION motherboard to make a home server.

---

### Post by nickrout on 2009-12-03
you are wasting the nvidia video chip if using it as a server. There are cheaper atom boards with lesser graphics.

---

### Post by ZedThou on 2009-12-03
I use "VDPAU Normal" which is Temporal 2x deinterlacing for 1080i and Advanced 2x for 480i. Haven't tried 1g ethernet as I have an HDHomeRun hooked up directly and I believe it's 100 Mbps.

---

### Post by stefangr1 on 2009-12-03
> **nickrout said:**
> you are wasting the nvidia video chip if using it as a server. There are cheaper atom boards with lesser graphics.

Those cheaper atom boards have a very inefficient i945GC chipset, which results in an overall system energy usage of about 40W when idle. The ION system consumes only 25W. This results in a 30 euro lower annual energy consumption. The ION motherboard is 40 euro's more expensive than cheap motherboards with atom 330 processor, so I imagine that can be easily earned back within the expected live time of at least 3 years.

EDIT: But your right about wasting the graphics as I'm going to turn them off :)

---

