---
title: "Horrible, just... Horrible."
date: 2011-03-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by bejayel on 2011-03-24
Severely unimpressed here.

Everything constantly crashes.
I can't actually click on anything half the time. My mouse moves. Clicks are detected, but just throw errors. 
A window can never keep / take focus.
it completely ****** my boot loader

There is way way way too much wrong with this. It's basically unusable. 

I guess it's a small step forward since 8 doesn't even work. 9/10 is the same as this except it goes a step further and crashes my network card till I hard boot.

edit***********

I am running 11.04 daily from march 23.

I am not sure what it is that keeps crashing. All I know is that every time it comes up, I can't click anything any more.

The video is not from 11.04, but it displays exactly what's happening in 11.04 - Unity.

[http://www.youtube.com/watch?v=Pfy453fbK88](http://www.youtube.com/watch?v=Pfy453fbK88)

Here you are. This exact same thing happens to me in every ubuntu 9 and up.

Ubuntu 8 wont even install.

Gigabyte 890FXA-ud5
AMD Phenom 2 x6 1055t
XFX radeon 5850 Crossfire
8 gig gskill ddr3
3 WD black in raid 0 (Windows 7, grub goes here and works fine)
1 WD green (where ubuntu should go)

What's worse is it's seemingly random. I'll start typing and then all keyboard input freezes and all mouse input is completely ignored. Except it's not the mouse / keyboard. There is some GLObject error popping up int he console for every single click. I can't give any information beyond that cause I simply can't do anything.

Also, it no longer detects and set up your boot manager for dual booting windows. The installer just sets it up for ubuntu and that's it. I was unable to find menu.lst.

---

### Post by PaulW2U on 2011-03-24
> **bejayel said:**
> 
Everything constantly crashes.

But you haven't told us what you're running. I've now got Xubuntu, Kubuntu and Ubuntu Classic/Unity installed on seperate partitions. Not one crash this evening. A re-install and a clear out of my settings folders did wonders for stability.

---

### Post by VMC on 2011-03-24
Yes, what are you referring to: "9" would be Jaunty, and "10" Lucid. Maybe you posted in the wrong forum.

If you want natty, what ISO did you install? Try the latest, found [_**here**_]("http://cdimage.ubuntu.com/daily-live/current/"). Many updates since alpha.

---

### Post by bejayel on 2011-03-24
> **VMC said:**
> Yes, what are you referring to: "9" would be Jaunty, and "10" Lucid. Maybe you posted in the wrong forum.

If you want natty, what ISO did you install? Try the latest, found [_**here**_]("http://cdimage.ubuntu.com/daily-live/current/"). Many updates since alpha.

I was waiting till I got a video uploaded. Here we go.

I am running 11.04 daily from march 23.

I am not sure what it is that keeps crashing. All I know is that every time it comes up, I can't click anything any more.

The video is not from 11.04, but it displays exactly what's happening in 11.04 - Unity.

[http://www.youtube.com/watch?v=Pfy453fbK88](http://www.youtube.com/watch?v=Pfy453fbK88)

Here you are. This exact same thing happens to me in every ubuntu 9 and up.

Ubuntu 8 wont even install.

Gigabyte 890FXA-ud5
AMD Phenom 2 x6 1055t
XFX radeon 5850 Crossfire
8 gig gskill ddr3
3 WD black in raid 0 (Windows 7, grub goes here and works fine)
1 WD green (where ubuntu should go)

I will update my upper post.

What's worse is it's seemingly random. I'll start typing and then all keyboard input freezes and all mouse input is completely ignored. Except it's not the mouse / keyboard. There is some GLObject error popping up int he console for every single click. I can't give any information beyond that cause I simply can't do anything.

Also, it no longer detects and set up your boot manager for dual booting windows. The installer just sets it up for ubuntu and that's it. I was unable to find menu.lst.

---

### Post by lucazade on 2011-03-24
Try to isolate the problem..

Does another desktop manager work well (i.e. kde - kubuntu)?
How about other distribution (Fedora, Debian..)?
Have you tried both opensource and closed drivers for ATI?
Is the problem present with/without a compositor enabled (compiz, metacity..)?
Did you look at logs (/var/log/dmesg and /var/log/Xorg.0.log)?

---

### Post by bejayel on 2011-03-24
> **lucazade said:**
> Try to isolate the problem..

Does another desktop manager work well (i.e. kde - kubuntu)?
How about other distribution (Fedora, Debian..)?
Have you tried both opensource and closed drivers for ATI?
Is the problem present with/without a compositor enabled (compiz, metacity..)?
Did you look at logs (/var/log/dmesg and /var/log/Xorg.0.log)?

I'll try kubuntu 11.04 daily from today. It's just downloading right now. 

As I mentioned, I can't check anything else. All input is being frozen by some globject error. If kubuntu is better for usage, I will try to grab some logs in the livecd.

Also, this is the AMD64 version.

This is my first attempt to do any linux installs on this PC. I gave up on linux when I started working as I got home and was burnt out of computer work. Now I want to get some dev stuff back up, but I'd like to keep it out of windows.

I try to stay far away from fedora. Every single time I use it, it causes nothing but problem after problem. There was this one time that it kept resetting all the listen ports on every single one of my servers, obviously royally screwing everything up. I had to have a script that would run to make sure the ports were right because it would just randomly switch them all for absolutely no reason.

brb kubuntu is ready to go.

---

### Post by Cam! on 2011-03-24
Crashing, and bugs on an alpha build of an operating system? Unheard of! :p

---

### Post by lucazade on 2011-03-24
> **bejayel said:**
> I'll try kubuntu.

As I mentioned, I can't check anything else. All input is being frozen by some globject error.

Also, this is the AMD64 version.

ok.. try also to add some kernel parameters at boot:
acpi=off

and/or

nomodeset=1

---

### Post by bejayel on 2011-03-24
> **Cam! said:**
> Crashing, and bugs on an alpha build of an operating system? Unheard of! :p

Except that the stable previous versions are even worse off. Thanks for the contribution. Note that the video is of ubuntu 9.10 I believe.

Xorg.0.log is normal.
dmesg has nothing

kubuntu seems to be ok, but dammit I hate KDE. I am going to book back in to the 11.04 unity and try to get as much errors as possible.

---

### Post by beew on 2011-03-24
> **bejayel said:**
> Except that the stable previous versions are even worse off. Thanks for the contribution. Note that the video is of ubuntu 9.10 I believe.


So you upgraded from  9.10 to an alpha bug test release while skipping two stable releases (10.04 and 10.10) Am I missing something?

---

### Post by kuvanito on 2011-03-24
sorry bejayel that this is happening to you.
i have two Desktop one is an Intel P4 with a Nvidia video card and it runs beautiful.
I also have an AMD Phenom Quad-Core with 4GB of Ram and ATI internal Video Card running great! except for the HDMI Audio Output.
I don't run Windows anymore,so Natty is the only OS in both Desktops,all is good for me.
I had some problems before but that was with the first Alpha 1.
So Far So Good! :popcorn:
Try Clean installs by downloading the ISO and use a 1GB USB Flash Drive
also you can install the 32 Bit OS you don't have to install the 64,since your CPU is a 64 Bit you can do either 32 or 64.
use a single OS,do not dual boot Ubuntu and Windows.
hell,i quit windose over ubuntu anytime...:)

---

### Post by VMC on 2011-03-24
> **bejayel said:**
> ...I am running 11.04 daily from march 23.

I am not sure what it is that keeps crashing. All I know is that every time it comes up, I can't click anything any more.

The video is not from 11.04, but it displays exactly what's happening in 11.04 - Unity.
...
Gigabyte 890FXA-ud5
AMD Phenom 2 x6 1055t
XFX radeon 5850 Crossfire
8 gig gskill ddr3
3 WD black in raid 0 (Windows 7, grub goes here and works fine)
1 WD green (where ubuntu should go)

...
What's worse is it's seemingly random. I'll start typing and then all keyboard input freezes and all mouse input is completely ignored. Except it's not the mouse / keyboard. There is some GLObject error popping up int he console for every single click. I can't give any information beyond that cause I simply can't do anything.

Also, it no longer detects and set up your boot manager for dual booting windows. The installer just sets it up for ubuntu and that's it. I was unable to find menu.lst.

Do you have a USB drive that you can load the ISO image into. If so run the livecd - Try Ubuntu without installing. See if you can navigate around a bit and open firefox and open close nautilus. Things like that for a while see if you have the same experience.  If not then something with your hardware that Ubuntu doesn't like.

---

### Post by bejayel on 2011-03-24
> **VMC said:**
> Do you have a USB drive that you can load the ISO image into. If so run the livecd - Try Ubuntu without installing. See if you can navigate around a bit and open firefox and open close nautilus. Things like that for a while see if you have the same experience.  If not then something with your hardware that Ubuntu doesn't like.

There is a bug in this motherboard that doesn't allow booting from USB for whatever reason.

GSettings
Compiz

The two things that constant crash. I know what compiz is (it's probably going as a result of lack of fglrx?). Why is GSettings always crashing?

11.04 is unfortunately my only option. I guess I will have to wait a little while till I get it going.

when is actual release date?

It's definitely compiz causing all of the clicking errors.

Also, where the crap is menu.lst? I have no way of adding my windows system to dual boot...

Apparently it doesn't currently detect my RAID unfortunately. 10.10 was able to and so does the livecd...

---

### Post by VMC on 2011-03-24
> **bejayel said:**
> ...
Also, where the crap is menu.lst? I have no way of adding my windows system to dual boot...

Apparently it doesn't currently detect my RAID unfortunately. 10.10 was able to and so does the livecd...

menu.lst has been replace in grub2 with grub.cfg found at /boot/grub.

Maybe you can check into you BIOS to fix USB booting. Also check into upgrading your BIOS firmware.

Edit:  The purest will tell you not to edit the grub.cfg file...enuf said.

---

### Post by epicoder on 2011-03-24
Also note that grub2 has some slightly different syntax and commands. Here's how you would boot a typical installation of windows on /dev/sda3:
```
menuentry "Windows 7 Home" {
    set root="(hd0,msdos3)"
    insmod ntfs
    chainloader +1
}
```

---

### Post by cariboo on 2011-03-24
If grub senses that you windows partition was shut down uncleanly, it may not be detected, so it may help to run:

```
sudo update-grub
```

in a terminal.

---

### Post by Quackers on 2011-03-25
So you have Crossfire graphics and a raid0 setup and you're running an alpha as a main system?
Wow, why don't you throw yourself in at the deep end? Oh, you did :-)

---

### Post by coffeecat on 2011-03-25
Since you get these problems with every stable release (if I read you correctly) since Jaunty, I'd put money on a hardware fault somewhere. How about RAM? If Windows has been happy that doesn't necessarily discount bad RAM. Windows and Linux utilise RAM differently and Linux is more likely to encounter bad registers.

If not faulty hardware, perhaps a buggy BIOS, so some of the kernel parameters suggested may help. A few more listed here:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by macroshaft on 2011-03-25
> **coffeecat said:**
> Since you get these problems with every stable release (if I read you correctly) since Jaunty, I'd put money on a hardware fault somewhere. How about RAM? If Windows has been happy that doesn't necessarily discount bad RAM. Windows and Linux utilise RAM differently and Linux is more likely to encounter bad registers.

If not faulty hardware, perhaps a buggy BIOS, so some of the kernel parameters suggested may help. A few more listed here:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

He has already stated a bug in the motherboard prevents booting from USB. Sounds like a buggy BIOS to me!

---

### Post by coffeecat on 2011-03-25
> **macroshaft said:**
> He has already stated a bug in the motherboard prevents booting from USB. Sounds like a buggy BIOS to me!

Agreed. I noticed that. :) A bug in a motherboard designed to allow booting from USB that doesn't allow booting from USB would be a serious bug. There are probably more. This sounds like one Linux-hostile BIOS.

---

### Post by rbrick49 on 2011-03-25
I had a similar problem after getting a new box the bios was altered for some reason the boot sequences were all wrong try looking at the boot sequence in your bios first boot floppy 2nd cd/dvd 3rd hard drive

---

