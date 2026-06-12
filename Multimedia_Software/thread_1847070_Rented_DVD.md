---
title: "Rented DVD"
date: 2011-09-20
forum: Multimedia Software
---

### Post by Robbie80 on 2011-09-20
I can't seem to play rented DVDs (from Netflix) with Ubuntu 11.04. I can play DVDs that I have purchased with no problems, haven't tried with a brand new dvd, other than rentals, (with the newest encryption) yet. Is there a problem with libdvdcss2 in breaking newer encryption schemes or is the rental encryption different? 

I have installed all of the restricted codecs and medibuntu repos of course and also looked around for similar problems, but I can't find any which leads me to believe I have made an error somewhere.

Thanks all.

---

### Post by Grenage on 2011-09-20
As far as I am aware, the encryption can't be any different; if it was, it wouldn't play on anyone's DVD player.

---

### Post by Robbie80 on 2011-09-20
> **Grenage said:**
> As far as I am aware, the encryption can't be any different; if it was, it wouldn't play on anyone's DVD player.

That's what I thought, but I found a post talking about Disney and Sony DVDs doing something similar. And then similar posts from 2006. 

When I put in a movie, say Alpha Dog or Dogma, the DVD drive grinds for 10 seconds or so and then the icon pops up. When I put in The Adjustment Bureau, the drive just grinds and grinds for about 20 minutes and falls silent. Trying to mount manually shows the "nothings in the drive stupid" message. Pretty sure its not a region issue either, I live in US and only really have access to region 1 dvds and the drive of course is set to region 1. 

Anyone had a similar problem and found resolution? Can I purchase the Fluendo player and play these newer disks?

---

### Post by BicyclerBoy on 2011-09-20
It is probably not libdvdcss that's causing the problems.

The most common DVD playback issues relate to 'file system' navigation obfuscation.

Some people have optical drive problems.

Your best DVD playback will be had from latest builds of mplayer/VLC or HandBrake.

I suggest using HandBrake on a fast PC & transcode to H264 in mkv file. Small files/no loss with very good seeking.

---

### Post by Robbie80 on 2011-09-20
File system obfuscation. Yes, from what I have read, that seems to be the case. Disks with intentional bad sectors and impossible file sizes cause the drive to read the disk forever or until it gives up.

 I am using the latest VLC, and I have tried mplayer as well. The problem with trying to use handbrake to rip it to a hard disk (which is of course the ultimate goal) is that the drive doesn't ever recognize the disk. After it stops grinding it acts as if there were no disk in the drive. 

 Is there a way or a command to tell my drive to ignore the bad sectors and files, or a command to tell the drive not to try to read the disk just to rip it to the hard drive, even as an image?

---

### Post by BicyclerBoy on 2011-09-21
One problem is that a DVD does not have a real file system in the computer sense. One wonders how many other traps were designed into the DVD standard. 

Some problems can be eased by using RPC1 or RPC none firmware.
The heavy disk access is the attempt to break the CSS by raw block reads. Some drive firmware tries to stop this unless region is set.

All you can do it get the latest copies from nightly or weekly builds. Or compile from source.
The private copies of the libdvdread/nav have all the patches.

I get HB from 
[https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)
If this fails I give up & use the DVD player.

---

### Post by Robbie80 on 2011-09-21
Thanks all for the help. I don't know if this is going to be a deal breaker or not, I am trying to build two LinuxMCE systems as Christmas presents. It would not be good if they couldn't play DVDs and Blu-Ray. Of course, I would still have telecom, security and Netflix streaming via a roku box and VLC. Not to mention my collection of about 200 movies. Right now I am testing on an old Dell Studio (which could be part of the problem, as much as Dell claims to be pro open source, their consumer products are not at all out-of-the-box Linux compatible) so the newer hardware (better, possibly region free drive) and faster processor might help. If all else fails, I guess I could just apply the roku netflix workaround to a  black box bluray/dvd player.

What do ya think?

---

### Post by nothingspecial on 2011-09-21
> **Robbie80 said:**
> I can't seem to play rented DVDs (from Netflix) with Ubuntu 11.04. I can play DVDs that I have purchased with no problems, haven't tried with a brand new dvd, other than rentals, (with the newest encryption) yet. Is there a problem with libdvdcss2 in breaking newer encryption schemes or is the rental encryption different? 


> **Robbie80 said:**
>  The problem with trying to use handbrake to rip it to a hard disk (which is of course the ultimate goal) is that the drive doesn't ever recognize the disk. 

We do not support illegal activity here.

Closed.

---

