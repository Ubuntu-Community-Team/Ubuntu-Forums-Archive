---
title: "Problems with watching HD video"
date: 2011-09-06
forum: Multimedia Software
---

### Post by CJJones829 on 2011-09-06
Hi!

I got this laptop brand new yesterday and installed Ubuntu that same day.  I'm an EXTREME novice user, so bare with me.

I seem to be having difficulty viewing YouTube videos in HD.  They load and look fine, but are extremely sluggish and laggy.  Same with livestreams in HD.  I didn't have this problem when I was testing everything out on Windows before switching to Ubuntu.

I was also having issues with just ANY YouTube video (or video file in general), but then yesterday I went to the "available drivers" (I believe it was called) and upgraded to the 3D graphics card thingy that it recommended.  This seems to have fixed just watching regular YouTube videos.  Hopefully there's an actual connection there, because I have no idea!  But it seemed to make it better.

So my question is, what can I download or do to help make viewing HD videos better?  What do you recommend?  And please remember, I'm an EXTREME novice with this, but I'm eager to listen and learn.  So thank you for the help and bare with me!  :)

---

### Post by Stigmata13 on 2011-09-06
Linux has always had notoriously worse flash performance than the windows counterpart, either due to an un-optimized flash plugin or sub-par graphics drivers.

I myself have these problems myself, I have an Acer Aspire 5515 that has an outdated 1.6Ghz single-core athlon, so sometimes I even have trouble with 480p flash, but I can play 720p video fine through mplayer or VLC. If you have a decent modern CPU (and since you're having problems, I'm guessing you have a low-end one too...) you probably wouldn't have these problems. Of course, you will have better video playback but your CPU usage will probably still be rather high.

There is a program I use called Minitube, it's a standalone app that lets you view and search for youtube videos, and since it uses mplayer to play them, you would notice better performance using it. [http://flavio.tordini.org/minitube]("http://flavio.tordini.org/minitube")
If you decide to go this route be sure to read the setup instructions as there are some packages you will probably need for the program to work correctly.

If you absolutely want to watch them in the browser, I would recommend a CPU upgrade, but that isn't cheap and definitely isn't easy for a novice to do.

---

### Post by CJJones829 on 2011-09-06
> **Stigmata13 said:**
> Linux has always had notoriously worse flash performance than the windows counterpart, either due to an un-optimized flash plugin or sub-par graphics drivers.

I myself have these problems myself, I have an Acer Aspire 5515 that has an outdated 1.6Ghz single-core athlon, so sometimes I even have trouble with 480p flash, but I can play 720p video fine through mplayer or VLC. If you have a decent modern CPU (and since you're having problems, I'm guessing you have a low-end one too...) you probably wouldn't have these problems. Of course, you will have better video playback but your CPU usage will probably still be rather high.

There is a program I use called Minitube, it's a standalone app that lets you view and search for youtube videos, and since it uses mplayer to play them, you would notice better performance using it. [http://flavio.tordini.org/minitube]("http://flavio.tordini.org/minitube")
If you decide to go this route be sure to read the setup instructions as there are some packages you will probably need for the program to work correctly.

If you absolutely want to watch them in the browser, I would recommend a CPU upgrade, but that isn't cheap and definitely isn't easy for a novice to do.

Yeah.. I don't plan on doing any type of upgrade.  I just purchased this laptop.. and I don't do many complicated things.  I keep it simple!  No real need to upgrade.

I'll try that program out.  Thanks for the help.

---

### Post by papibe on 2011-09-06
Which graphic card do you have?

If you have a fairly recent Nvidia card, Firefox, and the proprietary driver, you can setup the Adobe flashplugin to use video hardware acceleration (VDPAU).

Regards.

---

### Post by CJJones829 on 2011-09-06
> **papibe said:**
> Which graphic card do you have?

If you have a fairly recent Nvidia card, Firefox, and the proprietary driver, you can setup the Adobe flashplugin to use video hardware acceleration (VDPAU).

Regards.

Honestly, I have no idea!  How do I find out which graphic card I have?

Also, I'm using Chromium as my web browser.

---

### Post by papibe on 2011-09-06
Could you post the result of this command?
```
$ sudo lshw -C display
```

---

### Post by CJJones829 on 2011-09-06
```
^Ccorey@CJ-Satellite-C655D:~$ sudo lshw -C display
PCI (sysfs) 

```

---

### Post by CJJones829 on 2011-09-06
```
^Ccorey@CJ-Satellite-C655D:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:41 memory:c0000000-cfffffff ioport:4000(size=256) memory:d0300000-d033ffff
corey@CJ-Satellite-C655D:~$ 

```

this popped up too.. all randomly, like 5 mins later.  is this info relevant or helpful at all?

---

### Post by papibe on 2011-09-07
It looks like motherboard integrated graphics. My guess is that it doesn't support video hardware acceleration.

Regards.

---

### Post by CJJones829 on 2011-09-07
> **papibe said:**
> It looks like motherboard integrated graphics. My guess is that it doesn't support video hardware acceleration.

Regards.

So.. what does that mean? :confused:

---

