---
title: "Catalyst 9.6 on Ubuntu 9.04 64bit = Extremely slow??"
date: 2009-07-18
forum: Multimedia Software
---

### Post by brandysnap on 2009-07-18
...Im talking 1fps on desktop, extremely slow here....

Installed ubuntu 9.04 from a live cd this afternoon onto the free remaining space on my hard drive (about 50gb free space there was)

Everything went fine until after the first round of updates.
First of all Ubuntu pops up a hardware driver box (dont know what its actually called) saying there are new fglrx(sp?) drivers for my ati radeon card and that they are proprietary etc. I clicked on the activate button and it downloaded and installed it.
During this another box from update manager appeared saying there were about 173 updates to stuff, so i did all those aswell.

After restarting with all those updates the machine has been a nightmare in terms of sluggishness (i dont exaggerate when i say 1fps.. eg. it took 30-40 seconds for the 'download complete' popup from firefox to scroll up and back down again.... 1.... pixel.... at....a.....time.....zzzz.

I immediately suspected video drivers as being out of date or incorrect so i downloaded the latest x86 64 linux drivers from Ati's own website (9.6) and, after some fiddling and much cursing trying to work out how you actually use '.run' files, i got them to install...... but they havent improved things much if at all.

whats going on here? what am i doing wrong?
i just want a nice 1680x1050@60hz display where i can turn on all those fancy and superfluous compiz fusion effects ive seen on youtube.

Other side things to note/ask are :-
- Cant set 1680x1050 as my desktop resolution even though my monitor supports it. infact at one point it was listed for one of the monitors. now it isnt at all for either!!

- I have 2 monitors listed. one as analog (thats my tv which i sometimes output the signal to so i can play pc games on my widescreen tv) and one as digital/dvi (thats my monitor which is connected via VGA even though ubuntu says its dvi - its always said its dvi even without ati drivers updated/installed) how do i get rid of the analog one because i aint using it for linux but i also dont want to physically disconnect it either.
 
specs:
ubuntu 9.04 - amd x86 64bit
amd x2 64 4400
4gb ddr2 666mhz
radeon 3870 - 9.6 linux x86 64bit drivers.
audigy 2zs


Linux newbie so give me a break.. or three.

---

### Post by UncertainGod on 2009-07-18
I'm having the exact same problem on a very similar machine also with ubunutu 64bit. I've noticed that fedora 11 doesn't even have ati drivers available so I'm guessing there are some pretty major issues with them. Do we have to stick with VESA for now or is there another option?

---

### Post by igorzwx on 2009-07-18
It may have something to do with pulse.

---

### Post by brandysnap on 2009-07-18
> **igorzwx said:**
> It may have something to do with pulse.

Care to elaborate on that?

Being a newbie to linux ive got no idea what Pulse is, what it does or how to fix it. :/

---

### Post by igorzwx on 2009-07-18
Perhaps, I cannot hepl much.
I do not use such things.

I solved my problems by OSS4

read this:
[http://ubuntuforums.org/showthread.php?t=1216484](http://ubuntuforums.org/showthread.php?t=1216484)

---

### Post by igorzwx on 2009-07-18
Install skype from Medibuntu repositories.
And tell how it works.
If noise, delay, and such things,
you are in trouble.

---

### Post by UncertainGod on 2009-07-18
There is no issue with the audio at all, it is the graphics driver that is screwed on modern ATi cards.

---

### Post by igorzwx on 2009-07-18
and old too

---

### Post by brandysnap on 2009-07-18
im going to install EnvyNG ( [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A) ) and see if that does anything.

i didnt uninstall the previous ati drivers before manually installing 9.6 (i didnt think linux would have the same problems as windows in that department.) so ill uninstall them using synpatic and then use envy to install 9.6.

---

### Post by markbuntu on 2009-07-18
No no !! don;t use envy with ati drivers. They have never worked for me.

The most likely problem is that the driver is misinstalled and the kernel modules were not loaded so the driver has fallen back to indirect rendering. The most probable cause for this is because the driver from the Hardware Manager was not removed before the driver from the ati site was installed. 

What you need to do is remove all the fglrx drivers and reinstall the 9.6 driver.

sudo apt-get remove fglrx fglrx-kernel-source fglrx-amdccle

Then go here and follow the manual install directions.

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

You could try creating the debs and then installing just the kernel modules. That may work.

What you should have done is get all the updates before installing the driver but that is not your fault. If you want to gain control over your two monitors and use the Catalyst Control Center to configure them then you should read this

[http://ubuntuforums.org/showthread.php?t=1152121](http://ubuntuforums.org/showthread.php?t=1152121)

---

### Post by UncertainGod on 2009-07-19
Thanks for the reply but that doesn't solve the issue at all.

---

### Post by igorzwx on 2009-07-19
there was a discussion about pulse and games
try to google it

---

### Post by igorzwx on 2009-07-19
[http://www.google.com/search?q=pulseaudio%20games&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=pulseaudio%20games&ie=UTF-8&oe=UTF-8)

---

