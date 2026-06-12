---
title: "Nvidia Geforce 9600 GT (512mb) problem"
date: 2008-07-18
forum: Multimedia Software
---

### Post by Bonez56 on 2008-07-18
Hi,

I built myself a new PC this afternoon with a Nvidia GeForce 9600 GT (512mb) PCIe card.

I installed Ubuntu from the alternative CD and all went fine. When I first logged in it was using a generic VESA driver, so I tried to enable the one from System > Administration > Hardware drivers.

After downloading and installing I rebooted, but X did not start any more, it was just a black screen.

I went into Recovery mode and defaulted back to the VESA driver.

Next I tried EnvyNG and it could not automatically detect my card, but said if I wanted to, I could try to manually install anyway, so I did.

This time after installing the driver, I reboot and get a prompt saying that Ubuntu is running in low graphics mode, blah blah. Basically that failed.

The last thing I tried was to go to the Nvidia.com website and download their Linux driver package. I tried to install that with guides from other posts on the forum (eg, stopped GDM, ran the .bin and compiled the module). This also fails, with the low-graphics mode warning coming up when I start Ubuntu.

I am stuck! Here's some info that may help.

```

blake@horizon:~$ lspci |grep VGA
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 084d (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)

```

Can anyone shed some light on this?

Thank you:)

---

### Post by Bonez56 on 2008-07-18
I solved this problem, thank you

I removed everything and tried the nvidia.com installer again, which worked.

---

### Post by w116tjb on 2008-07-21
Does everything work fine? Compiz and whatnot? Have you tried running any games on it? I'm torn between this card and an 8800 GT because of compatibility issues.

---

### Post by keelon72 on 2008-08-08
Hi,

I have trouble with my newly bought Sparkle nvidia 9600 GT (512 mb) card. I thought it best to do a fresh install of Hardy with the new card. It works fine in 2D, but glxinfo displays that there is no GL support.

Armed with this information I searched on Google and found that there was a new driver for EnvyNG 173.14.12 in the proposed repositoriy that supposedly should support my card. 

I added the proposed repository and installed EnvyNG. When I tried to install the new driver with EnvyNG, Envy threw an error that my card couldn't be detected as a supported card for that driver. I went ahead and tried to install the driver manually, but this resulted in a distorted screen. From what I could see I think it was the screen for low resolution mode.

I copied my backup of my xorg.conf file with the NV driver back to /etc/X11 and rebooted, no problems, but still no GL mode available. 

I also read a bunch of tutorials, but I can&#8217;t remember any of them addressing a working Direct Rendering mode. 

The only reason I bought this card was so I could play WoW through Wine with higher resolution and better performance.

I also saw that there was a beta driver from nvidia (177.13), does this help my case in anyway?

Please, any solutions?! Don&#8217;t find it pleasing to wait for Inrepid to get it to work.

// Kim

---

### Post by keelon72 on 2008-08-11
Solved it. 

Wasn't a software issue (I think). I changed my 350W PSU to a 450W PSU.

Reinstalled Hardy 8.04.1, updated, installed EnvyNG (BTW: the 173.14.12 driver is in the hardy-updates now, no need to activate hardy-proposed) and choose the manual install. And that was that.

glxinfo | grep direct
direct rendering: Yes

---

### Post by Roasted on 2008-10-20
But does Compiz work? I have the same graphics card and I can't get my compiz setting to stay on custom. Whatever I select, it goes back to "normal." I'm not sure if it's compiz-dependent or related to my graphics card.

I'm running Hardy 64 bit and I have the Nvidia 64 bit driver installed.

---

