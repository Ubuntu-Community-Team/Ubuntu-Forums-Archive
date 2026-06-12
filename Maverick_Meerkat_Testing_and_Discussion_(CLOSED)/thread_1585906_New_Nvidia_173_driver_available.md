---
title: "New Nvidia 173 driver available"
date: 2010-10-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kumaryu on 2010-10-01
For those trying out Maverick with legacy cards dependent on Nvidia 173 drivers. 

There was an issue with the new Xorg Xserver 1.9 preventing Xorg/GUI use. 

A new driver (173.14.28 ) is now available from Nvidia at:
[http://www.nvnews.net/vbulletin/showthread.php?p=2326225](http://www.nvnews.net/vbulletin/showthread.php?p=2326225)

I now have Geforce FX5700 Ultra running Maverick's Xserver 1.9 using this driver. Experience using this driver with other cards would be useful.

Notes:
* I understand that there was a similar issue with Nvidia- 96 drivers but am not aware of any update/fixes for this.
** For those with similar issues not fixed by the new driver, booting without xorg.conf works as a stop-gap.
***A downgrade workaround (ie short-term, not fix) from Voynix also worked for me: 
[http://ubuntuforums.org/showthread.php?t=1569736&highlight=maverick+xorg+173&page=2](http://ubuntuforums.org/showthread.php?t=1569736&highlight=maverick+xorg+173&page=2)

---

### Post by kumaryu on 2010-10-04
As reported in:

Ubuntu “nvidia-graphics-drivers-173” package Bugs Bug #626918
"Nvidia 173 driver does not work with xserver 1.9 "

and

Ubuntu “xorg-server” package Bugs Bug #626974
"ABI change in xorg 1.9 breaks legacy nvidia-96 and nvidia-173 drivers in Maverick"


nvidia-graphics-drivers-173 (173.14.28-0ubuntu1) Maverick

has now been released. I can confirm that it is now included in the most recent set of updates for Maverick.

---

### Post by auxbuss on 2010-10-04
The new drivers have killed my machine. Black screen when gdm login expected. Xorg.0.log shows all okay.

Ideas? I have a brick here right now.

Maverick/GeForce GT 330M/Sony Vaio f-series

---

### Post by ktp on 2010-10-04
> **auxbuss said:**
> Maverick/GeForce GT 330M/Sony Vaio f-series

your card should be using 260 driver not 173.  what version do you have installed?

Also might be better to start new thread for your specific issue.

---

### Post by theanswriz42 on 2010-10-04
> **ktp said:**
> your card should be using 260 driver not 173.  what version do you have installed?

Also might be better to start new thread for your specific issue.

The 260 driver kills the 330. I too have a Sony Vaio F12 and when I saw that downloading, I quickly stopped it. I was really hoping the devs wouldn't sneak that in, but they did.

---

### Post by ktp on 2010-10-04
if you are sure this is caused by 260, then you should report it to upstream:

[http://www.nvnews.net/vbulletin/showthread.php?p=2314331](http://www.nvnews.net/vbulletin/showthread.php?p=2314331)

---

### Post by theanswriz42 on 2010-10-04
> **ktp said:**
> if you are sure this is caused by 260, then you should report it to upstream:

[http://www.nvnews.net/vbulletin/showthread.php?p=2314331](http://www.nvnews.net/vbulletin/showthread.php?p=2314331)

I'll do that. I was actually using the PPA for nvidia drivers with 10.04 and it also killed the card when they went to 260 :(

---

### Post by theanswriz42 on 2010-10-04
[http://www.nvnews.net/vbulletin/showthread.php?t=155238](http://www.nvnews.net/vbulletin/showthread.php?t=155238) was already there so I appended to it.

---

### Post by kumaryu on 2010-10-05
Just to clarify...

As far as I know, Nvidia 173 driver should only be used for the following cards:
GeForce 5 FX series:
FX 5900 Ultra, FX 5200 Ultra, FX 5100, FX 5900XT, FX 5900, FX 5950 Ultra, FX 5200LE, FX 5900ZT, FX 5700 Ultra, FX 5600XT, FX 5800 Ultra, FX 5700, FX 5700LE, FX 5200, PCX 5900, PCX 5750, FX 5600, FX 5600 Ultra, PCX 5300, FX 5700VE, FX 5800, FX 5500

Although other cards are listed by Nvidia as being supported (not 300M series), more recent cards are supported by later driver versions and they should be tried first.

One significant omission at the moment appears to be for those using Nvidia-96 drivers (currently 96.43.18 ). I understand that we are still waiting for an update to -96 drivers for compatibility with Xorg Xserver 1.9. The cards affected are:
  GeForce 4 MX series:
  Quadro NVS series:
  Quadro 4 Go series:
  Quadro 2 Go series:
  GeForce 4 Ti series:
  GeForce 2 series:
  Quadro 2 MXR series:

As noted by KTP above, 300M are "supposed" to be supported with Nvidia-260 driver and any bugs should be reported upstream.

---

### Post by auxbuss on 2010-10-05
I don't know a lot about this are. Ubuntu packages installed indicate
that 173 is being used: from package nvidia-173-modlaiases. But Xorg.0.log
shows that it is loading 260.19.06. I don't know how the packages relate
to what is used, I'm afraid.  

From that, 260 is the issue, so I posted in the wrong place.

I'll move over to the thread noted above.

---

### Post by kumaryu on 2010-10-05
Have you tried booting without xorg.conf file?
In many cases, Xserver can start without xorg.conf file.

 1. At Grub, Cntrl_alt+F1 to enter the terminal.
 2. Log in and goto /etc/X11/: cd /etc/X11/
 3. Rename xorg.conf: mv xorg.conf oldexorg.conf
 4. Restart: sudo shutdown -r now

If it works, it should at least give you a working GUI.

If there are no working drivers suitable for your GeForce GT 330M, you could try a temporary workaround suggested by Voynix here:
[http://ubuntuforums.org/showthread.php?t=1569736&highlight=maverick+xorg+173&page=2](http://ubuntuforums.org/showthread.php?t=1569736&highlight=maverick+xorg+173&page=2)

It downgrades your Xserver to the Lucid version and allows the use of the old Nvidia drivers. Its not pretty but it worked for me until Nvidia released their new driver.

---

### Post by kumaryu on 2010-10-05
This may also be of some interest to you...

[http://ubuntuforums.org/showthread.php?t=1577779](http://ubuntuforums.org/showthread.php?t=1577779)

---

### Post by theanswriz42 on 2010-10-05
> **kumaryu said:**
> This may also be of some interest to you...

[http://ubuntuforums.org/showthread.php?t=1577779](http://ubuntuforums.org/showthread.php?t=1577779)

Thanks!

---

