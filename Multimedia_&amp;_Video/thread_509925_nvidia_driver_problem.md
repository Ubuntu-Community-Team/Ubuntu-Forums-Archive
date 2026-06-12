---
title: "nvidia driver problem"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by tesseract36 on 2007-07-26
im trying to install an nvidia driver and i cant, the error it gives me is something about not having libc but i went to a site to download an libc and it says mine is more up to date then theres.... and help. the driver is NVIDIA-Linux-x86-1.0-9639-pkg1.run and its on a dell inspiron 8200

---

### Post by wolfen69 on 2007-07-26
did you try installing through the restricted drivers manager?

---

### Post by tesseract36 on 2007-07-26
> **wolfen69 said:**
> did you try installing through the restricted drivers manager?

Yeah, When i do that the next time ubuntu starts my screen turns off...

The only way i know how to fix that problem is reinstalling ubuntu witch takes forever

---

### Post by dabl on 2007-07-26
If the -9631 version is the right driver for your Dell, I THINK that is the driver that is in the *nvidia-glx* package (not *nvidia-glx-new*).  So probably the packaged driver will be just as functional as the downloaded driver, plus it won't break when there is a kernel upgrade, which the downloaded one will.

However, you will first have to remove the Nvidia bits that you already have installed, and I'm not totally sure how to tell you to do that.  In general, I would first convert it to a VESA display system, using ```
sudo dpkg-reconfigure xserver-xorg
``` and on the first screen say "NO" to autodetecting, and on the next screen choose "VESA" as the display type.  Then finish the script, get dumped back to the command line, and enter ```
startx
``` to get a GUI login.

Then you'll need to search for "remove proprietary Nvidia driver" and do whatever it takes to remove that stuff, and then you should be able to open Synaptic and simply choose the nvidia-glx package for installation.

I hope this helps!  :)


EDIT: AHA -- here's the rest of the story -- see next to last post for the rest of the solution. [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217)

:)

---

### Post by tesseract36 on 2007-07-26
i tryed to followed you instruction but after reconfiguring xserver my screen resolution is 1024x768 and wont go and bigger (should be 1600x1200) and i still cant install the nvidia driver the errors i get are

```
no precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site...
```

then it says it could find on from the site...

then i get this

```
ERROR: you do not appear to have libc header files installed on your system. Please install your distribution's libc development package.
```

---

### Post by dabl on 2007-07-26
OK, well you're not exactly following my instructions, but what you need is the package "linux-headers" for your kernel version.

So, in a console window, do ```
sudo apt-get install linux-headers-`uname -r`
```

Better cut it from here and paste it in -- those marks around uname -r have to be the one under the tilde (left of number 1 on the top row).

Then try again with your install of the downloaded driver. :)

---

### Post by tesseract36 on 2007-07-27
yes i copyed the code and pasted it into a konsole and this is what it output :

```
steven@inspiron:~$ sudo apt-get install linux-headers-`uname -r`<br>
Reading package lists... Done<br>
Building dependency tree<br>
Reading state information... Done<br>
linux-headers-2.6.20-16-generic is already the newest version.<br>
The following packages were automatically installed and are no longer required:<br>
  libneon26 libapr1 libsvn1 kdesvn-kio-plugins libsvnqt3 libpq5 libaprutil1<br>
Use 'apt-get autoremove' to remove them.<br>
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.<br>

```

and my screen is still way smaller then it should be. sorry for all the trouble but st this point i would just like my screen back, i can wate to be able to use desktop effects.

i checked my xorg.conf and all the settings in there say my screen can do 1900x1440 so i have no idea what im doing.

---

### Post by fcigoi on 2007-08-03
Hi,

I have the same problem...installation of Nvidia drivers and, following the same path to try solve it, came across the same errors, i.e. no kernel interface, and no libc.
Now when i try to apt-get install the system tells me that both are there and up-to-date. What can I do to progress ?

---

### Post by dannyboy79 on 2007-08-03
we need to see the output of
lspci -v
to see exactly which driver you need. Also, here's a great guide for getting rid of lingering nvidia stuff which screws stuff up.

Follow the steps in post number 78 here ([http://ubuntuforums.org/showthread.php?t=432056&page=8](http://ubuntuforums.org/showthread.php?t=432056&page=8)) for your specific card and driver

To the guy who want 1600x1200, you won't get that until you install the correct Nvidia driver so no sense in even trying with the vesa driver.

---

### Post by fcigoi on 2007-08-03
Here's the output from lspci -v :

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0407 (rev a1) (prog-if 00 [VGA])

Subsystem: Sony Corporation Unknown device 9016
Flags: bus master, fast devsel, latency 0, IRQ 5
Memory at ce000000 (32-bit, non prefetchable) [size=16M]
Memory at d0000000 (64-bit, prefetchable) [size=256M]
Memory at cc000000 (64-bit, prefetchable) [size=32M]
I/O ports at 2000 [size=128]
Capabilities: <access denied>


Hope this section is sufficient as I have no other way of copying it here than typing

---

### Post by dannyboy79 on 2007-08-03
well what's the laptop brand because as you saw the nvidia info was incomplete. I need to know which nvidia chipset you have.

Also, didn't you check out the link I pasted? That should tell you what to do thoroughly enough to get you going.

---

### Post by fcigoi on 2007-08-04
Hi Dannyboy,

I fumble around with it all evening yesterday and managed somehow to install the proprietary nvidia driver and all the stuff it wanted to install itself, but the problem is still the same...xserver doesn't start.
The laptop is a Sony Vaio Ar41S, with and 8600GT video card on board.
Does this ring a bell ?

---

### Post by fcigoi on 2007-08-04
Oh, and YES I tried to follow your other post and set the driver to vesa, but then all i got was a black screen and no way to open a console

---

### Post by dannyboy79 on 2007-08-05
i would suggest trying out Envy, it's compatible with the newest 8600gt and it's text based and gui based. It's a 3rd party software which allows you to install either ATI or Nvidia proprietary drivers. give that a shot. I find it very weird that vesa wouldnt give you a screen, evern if the x server failed to start you should still be in text mode so you could download envy using wget and run it from the command line, good luck

---

