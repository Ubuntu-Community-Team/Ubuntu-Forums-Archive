---
title: "LIRC is not configured message on boot -HELP!"
date: 2008-01-18
forum: Mythbuntu
---

### Post by Peterg707 on 2008-01-18
When I try to boot from the CD I get the message, "LIRC is not configured".  Then it hangs

I've tried to install ubuntu and mythbuntu both amd64 and i386 and I get the same results.

My hardware is
Mobo: abit AN-M2HD
Processor: AMD 4800 
HD1: Sata western digital 250
HD2: Sata Westerd digital 750
Opt drive: Toshiba s203
Case: Ahanix 303
Vid card: xfx Geforce 7200 GS
Tuner card: (not yet installed) divco hdtv5 rt
I'm at my wits end and about to jump to vista mce!

:confused:

---

### Post by racmar on 2008-01-18
Well, you could always try installing the server version of ubuntu.  Then add mythbuntu repository to /etc/apt/sources.list.  That's what I did last time I installed it.

you might also have to install the generic kernel.

the repo install directions are here: [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by superm1 on 2008-01-19
> **Peterg707 said:**
> When I try to boot from the CD I get the message, "LIRC is not configured".  Then it hangs

I've tried to install ubuntu and mythbuntu both amd64 and i386 and I get the same results.

My hardware is
Mobo: abit AN-M2HD
Processor: AMD 4800 
HD1: Sata western digital 250
HD2: Sata Westerd digital 750
Opt drive: Toshiba s203
Case: Ahanix 303
Vid card: xfx Geforce 7200 GS
Tuner card: (not yet installed) divco hdtv5 rt
I'm at my wits end and about to jump to vista mce!

:confused:
This means that the graphical interface (X server) did not finish self configuring.  If you are hooked up to a TV, try doing it with a monitor, or in safe graphics mode.

---

### Post by racmar on 2008-01-19
@superm1 - good catch.  I didn't even think of that problem.
anyway, here are a couple links to help setup your TV out /w nvidia: 
[http://ubuntuforums.org/showthread.php?t=663636&highlight=nvidia+svideo](http://ubuntuforums.org/showthread.php?t=663636&highlight=nvidia+svideo)
[http://ubuntuforums.org/showthread.php?t=595363&highlight=nvidia+tvout](http://ubuntuforums.org/showthread.php?t=595363&highlight=nvidia+tvout)

---

### Post by Peterg707 on 2008-01-19
Racmar and Superm1,
THanks for responding.  I'm going to try that when I get home from work and I'l let you know how it goes.  I've been really frustrated because I couldn't find any information on that message. I've been thinking it had to do with the IR receiver.

I'm not hooked up to a TV just yet.  I'm using and analog monitor while I'm installing.

---

### Post by Peterg707 on 2008-01-19
Well, I've tried mutliple things and nothing seems to be working. I even tried mythdora and knoppmyth.  I have a feeling it's either my. Ubuntu server will load, but cannot find my network. Mythdora  and knoppmyth can't find my hard drives.  ubuntu hangs.

One of the reasons I bought the motherboard was a positive linux review on newegg. 

I'm thinking there might be SATA problems and graphic card problems.

If anyone has any clues let me know.

---

### Post by superm1 on 2008-01-20
> **Peterg707 said:**
> Well, I've tried mutliple things and nothing seems to be working. I even tried mythdora and knoppmyth.  I have a feeling it's either my. Ubuntu server will load, but cannot find my network. Mythdora  and knoppmyth can't find my hard drives.  ubuntu hangs.

One of the reasons I bought the motherboard was a positive linux review on newegg. 

I'm thinking there might be SATA problems and graphic card problems.

If anyone has any clues let me know.
Well so in safe graphics mode, what does /var/log/Xorg.0.log say?

---

### Post by Peterg707 on 2008-01-20
It still comes up with the LIRC not configured message.

I thought LIRC was specific to Linux Infnrared Remote Control, not the graphics card.  

THe odd thing is I'm geting that message when trying to install regular Ubuntu also

I'm going to try adjusting some of my bios settings today and see what happens.  I'm just flabbergasted that I'm getting this message and haven't been able to track down the cause.

---

### Post by superm1 on 2008-01-20
> **Peterg707 said:**
> It still comes up with the LIRC not configured message.

I thought LIRC was specific to Linux Infnrared Remote Control, not the graphics card.  

THe odd thing is I'm geting that message when trying to install regular Ubuntu also

I'm going to try adjusting some of my bios settings today and see what happens.  I'm just flabbergasted that I'm getting this message and haven't been able to track down the cause.
As i've been trying to get the message across, that is the last thing that happens upon boot before the graphics comes up.  The problem is the graphics coming up, **not** the remote.

Hit ctrl-alt-f1 and you will get a virtual terminal that you can log into and look at logs etc.

---

### Post by racmar on 2008-01-20
Are you sure it is hung?  Like superm1 is saying, the graphical portion of linux is not starting.  It is called Xserver, commonly refereed to as X.  Specifically, gutsy is using xserver-xorg and the configuration file for xorg is /etc/X11/xorg.conf . 

Your computer is probably not locked up, but X is not starting.  Try holding control+alt then press F1 or F2, etc.  Then logon with your username.  

Make a copy of xorg.conf before you edit the file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Next, edit
 ```
sudo nano /etc/X11/xorg.conf
```

find the line that looks like this:
```

Section "Device"
        Identifier      "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

```

in your case, the identifier will be different ( like xfx geforce, yada, yada ).  Then change the driver from nvidia ( or nv ) to vesa.

Then save the files with control+O then enter.
Then exit with control+X

Now, you can reboot and see if the graphics come up at all.  This is just a test, since using vesa is a very simple dirve, ie. no 3d or 2d acceleration.  But if it works, we can move on to other tests.



Also, when you boot from the live CD do you see the desktop?  If so, you could always copy the auto-generated /etc/X11/xorg.conf file from the live cd envrionment.  I usually do this from a different machine, after installing ssh ( sudo apt-get install openssh-server )

---

### Post by Peterg707 on 2008-01-20
This is great information to know.  Many thanks again.
Unfortunately, the live CD won't even come up - can't even get to the live desktop.

I boot from the CD, the menu comes up for what do I want to do (install, safe graphics mode, etc.)  
It gives me the LIRC error before I even get to the live cd desktop.
If I try a direct install, it gives me the same.  So, unfortunately at this point I am unable to change xorg.conf

I think there might be a combination of things with my choice of hardware that is creating this problem.  When I load the live desktop to my p4 pc it loads beautifully.

On this AMD 4800+ with the abit board it's not happy. I've tested with mythbuntu (both versions), Ubuntu (all versions and server), mythdora (get driver error message) and knoppmyth (error message I can't remember at this time)

This is really unusual for me as I've had excellent experience with various linux distros in the past.

---

### Post by superm1 on 2008-01-20
> **Peterg707 said:**
> This is great information to know.  Many thanks again.
Unfortunately, the live CD won't even come up - can't even get to the live desktop.

I boot from the CD, the menu comes up for what do I want to do (install, safe graphics mode, etc.)  
It gives me the LIRC error before I even get to the live cd desktop.
If I try a direct install, it gives me the same.  So, unfortunately at this point I am unable to change xorg.conf

I think there might be a combination of things with my choice of hardware that is creating this problem.  When I load the live desktop to my p4 pc it loads beautifully.

On this AMD 4800+ with the abit board it's not happy. I've tested with mythbuntu (both versions), Ubuntu (all versions and server), mythdora (get driver error message) and knoppmyth (error message I can't remember at this time)

This is really unusual for me as I've had excellent experience with various linux distros in the past.
As mentioned before: that is not a lirc error.  It is **not **configured on live boot.  **After **install it is configured.

Please switch to a virtual terminal as described above and look at /var/log/Xorg.0.log in both normal boot and safe graphics mode.  These logs will tell you what the problem is.

---

