---
title: "nVidia 7600 GS - Will not even boot Ubuntu"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by djRobbieF on 2006-09-04
Hey all.  Thanks in advance for any help you can provide.

* Using Ubuntu 6.06 *

I have been using an ATI card for the longest time, and just FINALLY was able to get myself what I thought would be a good nVidia card; the 7600 GS AGP.  Yes, I know it's not spectacular; but I was on a budget (birthday money)  :)

So my problem is this; now that I've installed the card, I cannot even BOOT Ubuntu's (or any other distro, it seems) live CDs.

My first guess is that the card is newer than the drivers that are being shipped with the build, but I can't be sure - any time I've used my ATI cards, it is always picked up "out of the box" - so this is a new experience for me.

Essentially, Kororaa simply says "failed to boot" or something along those lines, whereas Ubuntu fails after trying to decompress the kernel.

If I boot Ubuntu live disc with the noapic option, I at least get past the kernel and it looks like it's going to boot, but as soon as X should be loaded, I get a bunch of text on the screen and get the Linux prompt.  I type X, and it repeats (screen goes black, looks like X will load, but then sits back at the prompt saying that there are no displays).

I *really* want to get Ubuntu installed, and the first thing I want to do is get XGL and Compiz going (hence the upgrade in video card).

Thanks !!!

Robbie

---

### Post by djRobbieF on 2006-09-04
BTW (Quick amendment):

I had considered trying to install Ubuntu first with my ATI card, and then while booted in with my ATI card, download and install the latest nVidia drivers.  Then, shut off my computer, install the nVidia card, and try booting.

BUT - that still doesn't help me for all the times I want to use the live disc (I use this often for recovery ... when I screw things up ... LOL)

Any thoughts or help you can provide is much appreciated!!

BTW - I am new to the Ubuntu community.  I got my 6.06 discs about a month ago and since trying the live disc (with my ATI card) I've been waiting for this nVidia card to come before I installed... so now I'm kinda down about it  :)

---

### Post by The Pinny Parlour on 2006-09-04
Firstly, don't be to bummed by this, I'm certain it can be resolved.
I have a 7600GS and experienced a truck load of issues when installing ubuntu.  Unfortunately for yourself though, I COULD boot the live CD.

Make sure your BIOS is set to boot from CD
If you have a Samsung optical drive, remove it and try another.  Try another anyway.

Hope fully you will get somewhere with that.

I had to use the second option on the ubuntu CD to get my install working.  

All the best with it.

---

### Post by tseliot on 2006-09-04
Try booting the livecd in Safe Mode

---

### Post by djRobbieF on 2006-09-04
The Pinny Parlour >> Thanks.  Sorry, I should clarify:  I am an IT specialist, and have been using linux (Linspire - also Debian-based, like Ubuntu) for about 2 years as my main OS.  I build computers as part of my job, and I most definitely know how to configure my bios  ;)  So in otherwords, I'm not a newbie, even though I'm "new" to the Ubuntu community; you can rule out all the obvious stuff.

To clarify:  When using my ATI card, I can boot Ubuntu live disc without problems, and that's what sold me on Ubuntu.  But I wanted to get an nVidia card BEFORE making the switch, so that I could install the OS with all the hardware I wanted (rather than having to patch it after the fact).  But I cannot boot to Ubuntu while using the nVidia card.  I can still boot Linspire, although it uses the Vesa drivers (gulp)... but at least I can get in to my desktop.

So my GUESS is that it's a driver issue with the newer nVidia chipset; but because I have not encountered this before, I could really use some advice.  You're right; sucks that YOU could boot the live disc, and I cannot  :)  Figures eh?  You got my hopes up until I read that you were able to boot out-of-the-box  LOL

tseliot >> Yes, I tried that, thanks.  Unfortunately I get the same thing.  I even tried booting using noapic, as per my first post.

---

### Post by The Pinny Parlour on 2006-09-04
You may have a DOA (Dead On Arrival) video card mate.  Has that crossed your mind yet?

---

### Post by djRobbieF on 2006-09-04
The Pinny Parlour >> Yeah that was my first thought; but I installed the drivers in Windows XP (I have it on one of my partitions and dual-boot with GRUB), and it was SCREAMING.  No issues at all.

---

### Post by tseliot on 2006-09-04
> **djRobbieF said:**
> The Pinny Parlour >> Thanks.  Sorry, I should clarify:  I am an IT specialist, and have been using linux (Linspire - also Debian-based, like Ubuntu) for about 2 years as my main OS.  I build computers as part of my job, and I most definitely know how to configure my bios  ;)  So in otherwords, I'm not a newbie, even though I'm "new" to the Ubuntu community; you can rule out all the obvious stuff.

To clarify:  When using my ATI card, I can boot Ubuntu live disc without problems, and that's what sold me on Ubuntu.  But I wanted to get an nVidia card BEFORE making the switch, so that I could install the OS with all the hardware I wanted (rather than having to patch it after the fact).  But I cannot boot to Ubuntu while using the nVidia card.  I can still boot Linspire, although it uses the Vesa drivers (gulp)... but at least I can get in to my desktop.

So my GUESS is that it's a driver issue with the newer nVidia chipset; but because I have not encountered this before, I could really use some advice.  You're right; sucks that YOU could boot the live disc, and I cannot  :)  Figures eh?  You got my hopes up until I read that you were able to boot out-of-the-box  LOL

tseliot >> Yes, I tried that, thanks.  Unfortunately I get the same thing.  I even tried booting using noapic, as per my first post.
The nv driver is the problem.

Try the alternate installer
After the installation the xserver will crash
Boot in Recovery Mode and type:
```
dpkg-reconfigure xserver-xorg
```

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then reboot:
```
reboot
```

and boot as usual

Note: you will need to install the nvidia driver in order to make the most of your card

---

### Post by djRobbieF on 2006-09-04
>> Try the alternate installer

How do I do that, if I cannot even boot the disc?  Should I do the installation first using my ATI card?

Thanks!!

---

### Post by tseliot on 2006-09-04
> **djRobbieF said:**
> >> Try the alternate installer

How do I do that, if I cannot even boot the disc?  Should I do the installation first using my ATI card?

Thanks!!
The Alternate installer is another (and separate) CD (which is not a livecd) which  will enable you to use the textual installer.


Of course you can also use your ATI card to install Ubuntu.
Then you will swap the cards.
Boot in Recovery mode and type:
```
dpkg-reconfigure xserver-xorg
```
and select the "vesa" driver.
Then reboot.


The choice is down to you.

---

### Post by djRobbieF on 2006-09-04
Oh ok awesome.  I think I'll do the ATI test first, because if the Alternate Installer is a separate disc, I will have to download that (Shipit only sent me a single disc version of Ubuntu, and it's a live disc).

So I'll give this a go first and see what happens, and will let you know.

Thanks!
Robbie

---

### Post by GreatSunJester on 2006-09-17
Anyone find out why this GPU has a Linux issue?  I just installed an AGP 7600gs (radeon 9800 fan just seized up and the card fried itself).  This card sure breathed some life into my computer and has extended my system replacement by a year or longer ... I don't play bleeding edge anything!

I have on the other hand been looking forward to an nVidia card and functional 3D drivers (damn you ATI!)

Downloading the alternate install iso right now.

---

### Post by tseliot on 2006-09-17
> **GreatSunJester said:**
> Anyone find out why this GPU has a Linux issue?  

It's just that the open source driver ("nv") doesn't support it and you need to install the nvidia driver. That's all

---

### Post by GreatSunJester on 2006-09-17
Odd -- booted the alternate install CD and get hung at exactly the same screen as the normal CD.  Tried booting to my original 6.06 install in recovery mode.. boot progresses and hangs at "ACPI:  Looking for DSDT .. not found!"

Does Edgy have the same open source NV driver problem?

---

### Post by reedatschool on 2006-09-24
Same problem here with a 7600 AGP Card.  

Solution?  Use the Alternate Install Cd to install 6.06.1 and then when Xserver crashes out login and type

sudo apt-get install nvidia-glx

This installs the driver from Nvidia (Non-free version)

sudo nano /etc/X11/xorg.conf

Once you got it open find where it says

"nv" 

and change it to 

"nvidia"

Reboot or type startx and it works like a charm!

It would be great if this could get sorted out though, it would be a real bummer for someone who isn't familiar with the command line.

---

