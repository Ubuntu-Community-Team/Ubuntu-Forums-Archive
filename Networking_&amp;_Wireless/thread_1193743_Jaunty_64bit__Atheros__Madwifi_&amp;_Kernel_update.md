---
title: "Jaunty 64bit / Atheros / Madwifi &amp; Kernel updates..."
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by dBuster on 2009-06-21
I have been a Jaunty user since Alpha 3 release since I couldn't get another version to load on my laptop.  In doing so in order back then to get my Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) card to work I resorted to the Mad-Wifi drivers to get my wireless going.  The only draw back I have seen is that any kernel update I have to do the following:

```
cd ~/madwifi-hal-0.10.5.6
sudo make clean
sudo make install
```

That was taken from the post:  [How To:MadWifi Support for AR2425 (AR5007EG) on 64bit Ubuntu !!!]("http://ubuntuforums.org/showthread.php?t=816780")

Since I have not done a clean install since the final release...

1.  Is there anyone out there who is not using the madwifi for their Atheros card?  

2.  Also are there any issues with kernel updates?

3.  Does anyone know of a painless method to, if there is another way to get it working, to get the Atheros card up and running smoothly without Madwifi???  

Any input is accepted & Appreciated!

---

### Post by Bachstelze on 2009-06-21
Since you are compiling the madwifi driver, you have to recompile it every time you install a new kernel. There's no way around it. However, now that Jaunty is released, you shouldn't have to do that anymore since the kernel version won't change (there wil only be minor upgrades, which shouldn't require you to recompile the madwifi module.

---

### Post by dBuster on 2009-06-22
> **HymnToLife said:**
> Since you are compiling the madwifi driver, you have to recompile it every time you install a new kernel. There's no way around it. However, now that Jaunty is released, you shouldn't have to do that anymore since the kernel version won't change (there wil only be minor upgrades, which shouldn't require you to recompile the madwifi module.

Okay I have only known the madwifi driver...  

What is the kernel version that I should be using?  Are there any how to's to get the kernel version working?  I have removed the madwifi and lost all wifi all together so how do you get the released kernel version working?

Actually there was a Kernel update just recently to Jaunty, it went from Kernel 2.6.28-12 to 2.6.28-13....

---

### Post by dBuster on 2009-07-02
> **HymnToLife said:**
> Since you are compiling the madwifi driver, you have to recompile it every time you install a new kernel. There's no way around it. However, now that Jaunty is released, you shouldn't have to do that anymore since the kernel version won't change (there wil only be minor upgrades, which shouldn't require you to recompile the madwifi module.

Yep minor kernel update and I had to recompile the driver again!  hmmm

---

