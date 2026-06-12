---
title: "Is it my video card?"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by keno on 2006-09-22
please bear with me.

I believe that my video card is on the fritz. You be the judge.

I recently switched to Ubuntu because Windows kicked it. It would freeze with increasing frequency and on its death bed i was greeted with a display of pixelated goodness. 

So I install Ubuntu and everything is fine, runs smoother than silk. I am new to linux, and i wanted to play some of my mp3s and try and run a higher resolution (i can't stand 1024X786). so i installed Automatix, yess booo boo i know, with the Nvidia driver in order to hopefully get a higher res. well after i reboot some weird things happen, then the Nvidia logo pops up, then it logs on and works for a second, and then starts to pixelate like it did when it died on Windows. 

Is this because i installed some shitty nvidia drivers via Automatix? If so how can i correct this?

Do you think my old NV25, GeForce4 Ti 4600, has had it after 4+ years? If so, what video card would you recommend with Ubuntu?

I appreciate your help, as i am new and have seen the promise that that is linux and ubuntu, and only want to continue through it.

---

### Post by Paul41 on 2006-09-22
It is normal to get the nvidia splash screen at start up.  Unfortunately that is the only thing I know the answer to on this.

---

### Post by kaptainlange on 2006-09-22
If the effect you describe as pixelated is what I think it is, it happens when your display is set out of range of your montior's capabilities.

I can't provide a detailed description of how to remedy it as each monitor is different, but taking a look at the file:

/etc/X11/xorg.conf

You should see something about HorizSync and VertRefresh in there.  Sometimes you can get by with removing those lines from the config file and restarting the xserver.  I'd recommend you comment them out instead so you can put them back later if need be.

You could also try messing around with the ranges yourself if you know what your monitor is capable of.

Also I don't know if you were complaining of the Nvidia splash screen or not, but its easily turned off by placing:

```
Option       "NoLogo" "True"
```

In the section "Device".

---

### Post by keno on 2006-09-23
when it goes pixelated, it also freezes up. i can move my mouse, but nothing else budges.

---

### Post by Paul41 on 2006-09-23
You could use nano from the command line to get to the xorg.conf file and try the changes kaptainlange suggested.  Pressing Ctrl + Alt + F1 will take you to the command prompt with no GUI so hopefully you would have the problem there.  If you can't even get there you could try to boot in recovery mode.  To do that you choose recovery mode from the GRUB menu at startup.  It will be the option right under the kernel that you normally use.  Recovery mode is command line only so you might be able to get your problem fixed there.

Edit:
Get to the file with nano like this
```
sudo nano /etc/X11/xorg.conf
```

If you go to recovery mode you will be root so you don't need the sudo.
```
nano /etc/X11/xorg.conf
```

---

