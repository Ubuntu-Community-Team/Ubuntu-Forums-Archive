---
title: "ATI 9.4 Released"
date: 2009-04-17
forum: Multimedia Software
---

### Post by keypox on 2009-04-17
Anyone try it yet with 4800 series?  Fix any issues?  

Im installing 9.04 now and gonna try it out :)

---

### Post by keypox on 2009-04-17
still has issues, with xorg using 100% cpu (known bug) and tearing in videos/compiz. This is using 9.04 gonna try 8.10.

---

### Post by zivagolee on 2009-04-18
strange.. it locks up X on startup.  Logging back in as root, the logfile says no devices found.  I have an X300... is it not supported any longer (I thought it read R300 -- not sure if its the same thing)?

Back to 9.3 for me.

---

### Post by Crandom on 2009-04-18
Should I use it instead of xf86-video-ati on a mobility radeon x1300 (r500)? Is it stable enough?

---

### Post by spoons on 2009-04-18
> **Crandom said:**
> Should I use it instead of xf86-video-ati on a mobility radeon x1300 (r500)? Is it stable enough?

I believe starting with this release they have dropped support for cards older than the R600 generation. It won't work.

---

### Post by caustic386 on 2009-04-18
Has anyone had any luck with this at all in Jaunty?  I can get it to "install", but nothing I do will allow me to set up dual monitors.  Xinerama is greyed out, and when I add a 2nd display via display manager, it tells me to log out.  Seems normal, but when I log in, displays are still mirrored and display manager is back to defaults, as if I never changed anything?

---

### Post by naveensn on 2009-04-18
I installed it and it seems to work fine so far.

AMD64
Radeon HD3200

---

### Post by redenex on 2009-04-18
> **naveensn said:**
> I installed it and it seems to work fine so far.

AMD64
Radeon HD3200

I am on the same, can you guide how to set this up please?

---

### Post by naveensn on 2009-04-18
Browse to the link below

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Select the parameters that apply to your system and press Go.

Download the driver and see the installer instructions.

---

### Post by Melcar on 2009-04-18
```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms ia32-libs

sudo sh ati-driver-installer-9-4-x86.x86_64.run

#Follow the automatic installation and when dropped back into the terminal...

sudo aticonfig --initial

#reboot
```

Works every time for me.


Only thing that's bugging me about the driver is not being able to accelerate video playback under Compiz.  Xv pegs the CPU at 100% and causes X to crash if you attempt to run fullscreen or manually resize your windowed video, and opengl causes my video players to segfault.  Turning composite effects solves all of this however.  Oh well, they were bound to break something when they started optimizing their composite support.

---

### Post by redenex on 2009-04-18
> **naveensn said:**
> Browse to the link below

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Select the parameters that apply to your system and press Go.

Download the driver and see the installer instructions.

Oh! thank you!

---

### Post by caustic386 on 2009-04-18
> **naveensn said:**
> I installed it and it seems to work fine so far.

AMD64
Radeon HD3200

Using dual monitors?  That seems to be the tricky part - as soon as I install fglrx, display manager detects my monitors as "unknown" and doesn't accept any changes.  If I had a single monitor, would be gravy!

Oh, it's a HD2400XT.  Seems to be on the supported list.

---

### Post by 00arthuryu on 2009-04-22
I have a 4850 and video playback is beyond terrible on 9.04/ATICC 9.4
I too have dual monitors, it just comes up as unknown :(
Its also quite broken for 9.3 as well...

---

### Post by caustic386 on 2009-04-22
> **00arthuryu said:**
> I have a 4850 and video playback is beyond terrible on 9.04/ATICC 9.4
I too have dual monitors, it just comes up as unknown :(
Its also quite broken for 9.3 as well...

Much as I hate to say it, glad to know I'm not the only one.  I thought video playback problem was because of crappy wireless, glad you pointed that out!

---

### Post by keypox on 2009-04-22
> **00arthuryu said:**
> I have a 4850 and video playback is beyond terrible on 9.04/ATICC 9.4
I too have dual monitors, it just comes up as unknown :(
Its also quite broken for 9.3 as well...

yeah ATIs CCC is not working to well with dual monitor support. But the built in tool in ubuntu works fine. In both 8.10 and 9.04 

but video playback is pretty much crap... though its not as bad as it was with 9.2 and earlier.  

I really thought 9.4 along with 9.04 would fix some issues but not really.

---

### Post by PCZahra on 2009-04-22
I updated to the Jaunty RC, and it was unable to reboot. I think that may have interfered with the update, but I'm stuck in low graphics mode with the only Radeon driver, Fglrx is "unable to allocate memory" (when it is installed) and Ati is nowhere to be found. I have a 9200SE that was working fine in 8.10. I even tried that trick of uninstalling fglrx and reinstalling radeon, but that knocked me back to console. I'm back up to low graphics now, and according to the log it also doesn't seem to recognise that I have a keyboard or mouse plugged in (yet it's using them just fine).
What happened?

---

### Post by PCZahra on 2009-04-28
OK, so it's still not working. I tried another ATI card, and even a different brand, but it didn't make any difference. Also the clock is running fast, and music and video is running that tiny bit faster. Is it possible unexpected power cuts (from storms) may have fried something in the motherboard? and if so is there a way around it?

---

