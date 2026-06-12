---
title: "Corrupted Graphics after Grub on Lucid"
date: 2010-05-04
forum: Multimedia Software
---

### Post by lechip on 2010-05-04
[LIST]
[/LIST]Hey guys!

So here's the deal:
Upgraded to Lucid from Karmic last week or so, everything was fine.
Today i needed to log into windows to set up some stuff, closed everything the ormal way, went to windows, came back and after Grub: Disaster! black screen, then corrupted graphics on top of the screen. Rebooted, same thing. Rebooted, went to recovery mode... same thing!
No freaking idea whats going on, 9.10LiveCD works fine, but i have no idea whats going on.

My machine: ASUS N81V with ATI HD4670 graphics

Guess ill have to use windows for the time being... :S

Terrible Quality photo provided:p:
[http://dl.dropbox.com/u/2666536/Pic0504001.jpg](http://dl.dropbox.com/u/2666536/Pic0504001.jpg)

---

### Post by quixote on 2010-05-05
What happens when you're booted into Windows should have zero effect on your ubuntu partition.  Are you using wubi, perhaps?  Even then, I don't think it should be able to do that, but I don't know.

I would think that somehow your graphics driver became corrupted, but you say that even recovery mode doesn't work...???  Since that's text-only, it shouldn't be affected.  Try booting into recovery again.  Is it really hosed?  If yes, I'm not sure what to suggest (aside from reinstall :().  

If no, then the thing to do is find out which driver lucid uses for your ATI, and reinstall it in recovery mode. First is a matter of searching the forums, second is "apt-get --reinstall install *driver-package-name*".  (You're already root in the recovery console, so no need for "sudo".)  We can go into more detail if that's what you want to do.

---

### Post by lechip on 2010-05-17
Well, i had to reinstall, actually i get the same screen but once the login menu loads, i´m able to see everything normal again.
It´s totally weird.

---

### Post by evilsectoid on 2010-05-22
This same thing happens to me after grub. Boot to windows all good. Boot to Ubuntu 10.04, black screen, then corrupted graphics on top, then freezes. If I ctrl+alt+Del it continues to the login screen. No problems after that everything work perfect.

Any help?

-Computer-
Processor		: 2x AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
Memory		        : 4057MB
Operating System	: Ubuntu 10.04 LTS
OpenGL Renderer		: GeForce 8800 GTS 512/PCI/SSE2
Audio Adapter		: Audigy2 - SB Audigy 2 ZS [SB0350]

---

### Post by lechip on 2010-06-07
The problem reappeared today, if i ctrl+alt+del, computer restarts and same problem appears.
I really need help, i dont want to reinstall all my SO just because of this.

---

### Post by lavinog on 2010-06-07
Just to be safe, try dusting out your computer, and reseating the memory.
How old is the computer?  Could the power supply be failing?

---

### Post by quixote on 2010-06-07
I'd second lavinog's advice.  Do whatever hardware checks you can, in Windows if need be.  Hardware is hardware.  Weird, random fails like that are often a sign of a failing component, and it's better to find out before it takes everything with it.

---

### Post by wilee-nilee on 2010-06-07
Boot a live cd run this command and post it.
```
lspci | grep VGA
```
If your hardware is working this will identify the graphics card and probably where the issue is as far as drivers go. I suspect you have a ati card that isn't supported with other then the generic diver but your computer is trying to use a ati version driver.

---

### Post by lechip on 2010-06-18
> **lavinog said:**
> Just to be safe, try dusting out your computer, and reseating the memory.
How old is the computer?  Could the power supply be failing?

Will do, dont thnik the supply fails since i am able to play hih end games on windows and the problem randomly occurs so often (has happened 3 times now, only thing i can do is to reinstall the OS)
> **quixote said:**
> I'd second lavinog's advice.  Do whatever hardware checks you can, in Windows if need be.  Hardware is hardware.  Weird, random fails like that are often a sign of a failing component, and it's better to find out before it takes everything with it.

Unlikely since i can play al kind of crazy stuff in windows and there everything works a breeze.

> **wilee-nilee said:**
> Boot a live cd run this command and post it.
```
lspci | grep VGA
```
If your hardware is working this will identify the graphics card and probably where the issue is as far as drivers go. I suspect you have a ati card that isn't supported with other then the generic diver but your computer is trying to use a ati version driver.

This will do inmediatly, im pretty sure it's some kind of wierd driver problem.

---

### Post by lavinog on 2010-06-19
Ok it looks like it could be that you are using the old proprietary driver.
I got a similar issue when I updated the kernel.
The way I fixed it was to boot into the recovery shell
and uninstall fgrlx.  After uninstalling, I was able to reboot using the open source drivers (which work great despite the lack of power saving features)
From there you can re-enable the proprietary drivers if you wish.

uninstall fglrx with the following commands:
```

cd /usr/share/ati
ls

```
You should see a list of files.  If not, this won't work.
In that list should be something like fglrx-uninstall.sh
```

sudo bash ./fglrx-uninstall.sh

```
sudo isn't needed if you are root already, but the new recovery shell can let you login as a user too.

if everything worked properly you can reboot with:
```

sudo reboot

```

---

### Post by lechip on 2010-06-19
The thing is even recovery mode has corrupted graphics :confused:
Live CD works though.
The in run from live cd:
```
lspci | grep VGA
```
I get
```

01:00.0 VGA compatible controller: ATI Technologies Inc Device 9488

```

BTW, from live CD i searched for the path
```

/usr/share/ati

```
But is nowhere to be found

Ive read some stuff bout plymouth, is it possbile it is causing the problem?

---

### Post by lechip on 2010-07-04
OK, is definetly driver related, i've reinstaled lucid and havent installed any drivers yet and everything works just fine.
Since i'm now pretty sure is a propietary driver problem, how do i install open-source drivers?
I'll look into it but until then i'll just leave th message here.

---

### Post by quixote on 2010-07-04
I believe the default drivers are open source, and if it's working well after a reinstall, you're done.  The drivers are installed.

---

### Post by lechip on 2010-07-05
Then the question is: why do i still have this: 
[IMG]http://dl.dropbox.com/u/2666536/drivers.png[/IMG]

Is that the restricted driver icon?
Still confused, sry.

---

### Post by quixote on 2010-07-05
I've never studied that little icon.  It is the restricted driver icon, but I don't remember whether it always has that lock on it or not.  If not, maybe it's just telling you that there's a problem with your proprietary drivers... which you already know :S

I'm just guessing, obviously.  You could click on the icon and see what it says.  It won't install anything until you tell it to in the popup window that comes up.

---

