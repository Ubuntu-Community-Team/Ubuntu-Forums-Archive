---
title: "Yet another DVD playback problem"
date: 2008-07-19
forum: Multimedia Software
---

### Post by JRPettus on 2008-07-19
It's been a long couple of days.  Two days ago I attempted to upgrade my Ubuntu 7.10 desktop (Dell XPS 410) to Hardy.  The upgrade hung at locales and after finally finishing it I got a message that it was in an unstable state.  

I reinstalled without formatting so that I could try to ensure that I didn't lose anything.  I could watch and rip DVD's at that time but the ripped .avi's were unwatchable and the DVD playback was jerky and difficult.  The rest of the operations ran painfully slow as well.

So, I opted for a clean install hoping that would resolve everything.  I saved all my files, backed up and moved my evolution settings and mail and then wiped the partition and reinstalled clean.

Now I have no DVD playback, can't rip and when I attempt to put a DVD in the drive I get a message stating "An error occurred.  Could not read from resource."

I installed mplayer and the libdvdcss2 and W32codecs using instructions from this site:
[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html)

No luck.  I still can't play from any player, including VLC and Totem and movie player and mplayer.  

I've been spending the better part of non-work hours getting the install done, the updates done, installing the applications I want and regularly use and getting those updated and working on this problem.

Right now I think I'm pretty close, since fixing this multimedia problem (I hope) will resolve my DVD ripping issues.  (I'm in Afghanistan and I rip the movies so I can send the disks home to the wife and I can watch them here on the computer.)

Also, it's getting late here in Afghanistan so I'm off to bed in a few minutes but I will getting up in the morning to look at any notes or suggestions that anyone might be able to offer so I can try to get this running.

I've read some other posts all over the net and seen all kinds of things suggested, such as changing the regionset (not necessary, my region is showing itself already set to the region that the DVD comes from) or perhaps DMA issues.  I'm pretty tired so I will be hitting this again tomorrow.  Hopefully either some rest or assistance from the community will help me resolve.

Oh, I'm mostly a n00b on command line but I'm picking it up as quickly as I can.

Thanks!

---

### Post by JRPettus on 2008-07-19
Oops, to make matters worse, I just discovered I've lost my audio tracks entirely.

---

### Post by JRPettus on 2008-07-19
No one has any suggestions for me to try or a direction in which to point me?

---

### Post by mc4man on 2008-07-19
run ```
sudo lshw -C disk 
```to see some of the logical names for your drive
most dvd players default to /dev/dvd to access
Maybe also start vlc from the terminal, then try to open a disk and ck. terminal output

---

### Post by JRPettus on 2008-07-20
> **mc4man said:**
> run ```
sudo lshw -C disk 
```to see some of the logical names for your drive
most dvd players default to /dev/dvd to access
Maybe also start vlc from the terminal, then try to open a disk and ck. terminal output

When I first installed acidrip, I could access the drive at /dev/dvd but also I could browse to it from /media/cdrom0, and acid could read the files on the disk at either one.

I also believe the problem is codecs related as I can't even play sound files now that worked before.  No audio on anything other than a flash video I downloaded from jibjab.

I think I'm going to just wipe and re-load again and take it slowly one step at a time and make sure that I can get everything running.

---

### Post by JRPettus on 2008-07-20
Ok, more news.  I reinstalled.  When I finished the install process, totem went out after I clicked on an .avi file and found the correct gstreamer codec and installed it.

I installed acidrip and amarok and then installed the libdvdcss2 and w32codecs from the medibuntu site using the same instructions from ubuntugeek.

At this point I was working.  I could get DVD playback.  I could rip movies and the movies were again watchable.

Then, Ubuntu prompted me to install updates to the acidrip, amarok and codec files I had installed.  I accepted the updates and now I can't read from resource yet again.

I'm back to where I started, this time because of the updates to the programs that WERE working.

On edit:  new information. The problem appears to be certain DVD's that don't playback.  The playback, since the new install, is mplayer.  It will play some DVD's but not others.  I downloaded and installed VLC Player, and it will play the movies without a problem.

Still attempting to run acidrip on the disk, but it's not looking good.  It at first found the files but couldn't rip them, just crashed and closed, and now when I re-open it, it can't read the disk at all.

---

### Post by JRPettus on 2008-07-21
Consider this one resolved.  Right now I'm doing everything I need to.  I will install the Kubuntu desktop tonight and make sure that it works and then will pronounce myself mostly done.

Thanks!

---

