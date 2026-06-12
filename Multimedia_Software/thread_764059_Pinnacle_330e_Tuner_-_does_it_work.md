---
title: "Pinnacle 330e Tuner - does it work?"
date: 2008-04-23
forum: Multimedia Software
---

### Post by crossy on 2008-04-23
Is there anyone out there that's got a working install of this USB hardware (Pinnacle Dazzle Hybrid Stick) with Ubuntu 7.10 (especially 64bit!)?

The card's lsusb identity looks like:
```
Bus 002 Device 006: ID 2304:0226 Pinnacle Systems, Inc. [hex]
```

I've followed as many of the relevant links that I could Google for, but mainly:

[http://mcentral.de/wiki/index.php5/Main_Page#Pinnacle_PCTV_Hybrid_Pro_Stick_330e](http://mcentral.de/wiki/index.php5/Main_Page#Pinnacle_PCTV_Hybrid_Pro_Stick_330e)

I got nothing initially, but when I added the firmware (v3) for the analog part, then I got picture (no sound) in tvtime. xawtv fails because it's looking for an analog device that isn't there, (*I'll put in some links for it at some point*). That said I'm not that bothered for analog - it's the digital service I want.

Anyway, the problem with the digital side of this appears to be that's it's not firing up the DVB tuner, (I think), so there's no /dev/dvb/... tree. The stick is being recognised correctly, as in:
```
[ 1307.383661] em28xx #0: Found Pinnacle Hybrid Pro (2)
```

Any/all help most greatfully received, because I really don't fancy going back to the Hauppauge Nova-TD that I got the Pinnacle to replace, (because the tuner stage doesn't work that well for Linux - so the Nova-TD will be going onto a WindowsXP box - heresy I know) ](*,)

Thanks, crossy.

---

### Post by ulixes1983 on 2008-04-24
Hi,

analog mode with tvtime was working for me under 7.10.

For the sound issue you have to use a sox command.

There is a script named usbaudio_setup.sh in the v4l directory. Use this and the sound will work, not perfectly, but it works!

---

### Post by crossy on 2008-04-25
> **ulixes1983 said:**
> Hi,

analog mode with tvtime was working for me under 7.10.

For the sound issue you have to use a sox command.

There is a script named usbaudio_setup.sh in the v4l directory. Use this and the sound will work, not perfectly, but it works!

Thanks for that ulixes1983 :cool:

Now if I can find someone equally helpful with the digital part of this hardware, then I'll be a happy penguin herder!

I might just say "what the heck", back off my files and put a new install of Hardy on here.

---

### Post by krauli on 2008-09-09
I cant get my 330e to work.. can someone plz help me :s 
i got 8.04 64 bit.. :s
I tried to understand this but with no success-.- 
[http://mcentral.de/wiki/index.php5/Installation_Guide](http://mcentral.de/wiki/index.php5/Installation_Guide)

---

### Post by alexelprogramador on 2010-07-03
Hi again!

I have the same device: **pinnacle pctv hYBRID PRO STICK 330E**

Is a small usb tv sintonizer.

Its small and really usefull, but only under windows

Under linux I cant start it

pleasse, any help would be greatfully received

thanks

[IMG]http://img815.imageshack.us/img815/2179/pinnaclepctvhybridprost.jpg[/IMG]

---

### Post by PCNetSpec on 2011-03-14
See here:
[http://linuxforums.org.uk/linux-tips-tricks/pinnacle-hybrid-tv-tuner-pctv-330e-in-ubuntu-10-10-maverick/](http://linuxforums.org.uk/linux-tips-tricks/pinnacle-hybrid-tv-tuner-pctv-330e-in-ubuntu-10-10-maverick/)

---

