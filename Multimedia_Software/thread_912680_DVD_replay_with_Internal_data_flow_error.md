---
title: "DVD replay with Internal data flow error"
date: 2008-09-07
forum: Multimedia Software
---

### Post by steffenklug on 2008-09-07
Hi 
I am a Windows admin who wants to give Ubuntu a try, well here I go.
I try to play a DVD and it does not work right. 
I see the opening screen screen, but thats it.
I can seem to slide to another position in the movie but then I get a 
strange output almost like the frequency is off.
==
I installed VLC with the same result
==
I ran sudo /sin/hdparm -d1 /dev/hdc and the DMA mode was off and is on now.

No change
I have two DVD drives and I try to figure out which one is /dev/hdc

Why can I not go into properties in the file manager and see this information on what is actually refering to?

I also received a Internal data flow error after I did the -d1 thing
I did not receive this error before.
---
The DVD works fine in XP and Vista.
---
I tried other DVD's same result.
---
Any ideas?

---

### Post by mc4man on 2008-09-07
What you can and or should do is dependent on what version of ubuntu your using. (edgy, feisty, gutsy, hardy. 6.10, 7.04, 7,10, 8.04 respectively

try running ```
sudo lshw -C disk
``` to get some idea of device nodes ect.
If you have a dvd in the drive when running the above some other useful info may appear ( depends on ubuntu ver., not so much on hdx setups

Also starting vlc from the terminal and then going file -> open disk is helpful

Generally speaking  hardware for **most** setups in gutsy and hardy is now sdx and scdx vs. hdx

It never hurts to provide a little basic hardware info either

---

### Post by steffenklug on 2008-09-07
The above results in:
##################
  *-cdrom:0
       description: DVD-RAM writer
       product: HP DVD Writer 840b
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: ED56
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: mode=udma2 status=nodisc
  *-cdrom:1
       description: DVD reader
       product: IDE-DVD DROM6216
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       logical name: /media/cdrom0
       version: HD08
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio dvd
       configuration: mode=udma2 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,noexec state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/hdd
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,noexec state=mounted
##############
so I added the -d1 to /dev/hdd and /dev/hdc
##############
and still the same problem

---

### Post by steffenklug on 2008-09-09
I ran a second install of Kubuntu and it's kaffeine did not work either. I received an error saying its decoded and even after installing the codecs I received the same error.
very frustrating.
But then I downloaded VLC and that worked like a charm
I did not need to do any of the -d1 
I guess it is Kubuntu for me

---

