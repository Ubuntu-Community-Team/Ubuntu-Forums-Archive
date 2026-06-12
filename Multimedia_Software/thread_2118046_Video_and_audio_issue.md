---
title: "Video and audio issue"
date: 2013-02-20
forum: Multimedia Software
---

### Post by kholburn on 2013-02-20
I have a system with and Asutek P8H61 M'board, with onboard audio and a Radeon HD 6450 with DVI, VGA and HDMI out which includes HDMI audio. I installed ubuntu (64bit) 12.04

I believe when I installed ubuntu I tried the restricted driver but it failed dismally and it was quite difficult to set it back to the opensource driver.  I had to use the terminal but I forget what I had to do.

Since then it has been working perfectly. I have two monitors and I have them working side-by-side, one connected by DVI cable and one by VGA.

All worked perfectly until the kernel update 3.2.0-33-generic #50-Ubuntu SMP.

The video stopped allowing two monitors.  The VGA monitor would flash with random noise.  Sometimes parts of a possible screen would be visible, mostly in the top half of the monitor usually flashing and distorted.

The Monitor connected by DVI cable worked fine.  With each successive kernel upgrade the situation stayed the same.  I discovered that if I booted into 3.2.0-31-generic #50-Ubuntu SMP I could get my two monitors back and everything was OK.

Then when the last kernel upgrade came, Linux 3.2.0-37-generic I have two issues: 
1. Now when I try to boot into any kernel later than 3.2.0.31 I get text mode with no graphics at all.  

2.The other issue is much more of a hassle.  When I play a movie, say an avi or youtube I get sound but no voice.  I assume that the headphones are connected to the rear streams of 4, 4.1, 5, 5.1 audio with the front possibly going to the HDMI output which I'm not using.  It is very frustrating.  No amount of using sound configuring utilities seems to help.  All the forum posts seem to be about people who want 5.1 audio but I want the opposite, just normal stereo and just normal headphones or speakers.

 I hope someone may be able to help me.

---

### Post by kholburn on 2013-02-21
I tried the restricted drivers both when I installed ubuntu and recently.  I tried recently using the gui and again following directions in another post using

```
sudo apt-get install fglrx fglrx-amdcccle
sudo aticonfig --initial
(reboot)

```
On rebooting my vga monitor shows a message that it can't display the resolution the card is outputing.  The DVI monitor shows nothing.  Then I use text mode to:
```

sudo apt-get remove --purge fglrx fglrx-amdcccle

```
And everything returns to the way it was (ie working OK in kernel 3.2.0.31).

---

### Post by kholburn on 2013-02-22
I tried a solution from another post: 
```

sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade

```
and rebooting.

This made no change what so ever.
3.2.0.38 boots straight into text mode
most of the other kernels show fine graphics on my DVI monitor, rubbush on the vga.
3.2.0.31 still works fine.

I should mention too that I use gnome, unity and KDE.  Different family users have different window managers.

---

### Post by kholburn on 2013-02-22
I really, really don't want to install the proprietary drivers direct from intel but I don't think I have any other options at the moment.

---

### Post by kholburn on 2013-02-22
I just tried installing the latest proprietary driver from AMD/ATI.  It gave me exactly the same results as the ubuntu one.  My monitor tells me it can display at that resolution.  fglrxinfo says display is null.

I removed the drivers with the script and went back to 3.2.0.31: video OK but with no audio when playing video.

It's very annoying.  There doesn't seem to be any way to use this video card properly under ubuntu, possibly linux.  Do I have to get another video card to make my system work?

---

### Post by kholburn on 2013-02-22
Is there some way to change the resolution in a text config file before I start x.  Maybe it's working but outputting the wrong resolution?

Why is getting graphics and sound so hard?  Even for someone who's been using computers for a very long time?  How can I recommend linux, which I do, when I can't even get a desktop machine working properly under linux?

I deliberately chose ATI because I thought that there were open source drivers.  Wrong, clearly!

---

