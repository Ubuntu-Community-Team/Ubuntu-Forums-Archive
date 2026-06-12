---
title: "Very low 2D performance after NVidia driver reinstall"
date: 2005-11-23
forum: Multimedia &amp; Video
---

### Post by 23meg on 2005-11-23
I'm having severe 2D performance problems after reinstalling the 7667 driver in Breezy. I had direct rendering reported as disabled in glxinfo and was having minor graphics corruption in 3D apps, thus decided to reinstall the driver. After reinstall, direct rendering did become enabled and 3D problems went away, but 2D performance took a great hit. Desktop icons take about a second to get repainted while switching workspaces (which itself is sluggish), minimizing a window takes two seconds and freezes all other 2D operations, etc. When I enable the composite extension, windows take FIVE seconds to get minimized and redrawn. It's as if all 2D acceleration suddenly went away.

I had this exact problem upon first install of the drivers after installing Breezy but it "magically" went away while I was tweaking away randomly. The only thing I recall doing that may have caused the magic improvement was dpkg-reconfiguring the kernel image.

My chip is a Geforce Go6200 with TurboCache (64MB), and it runs on a PCI-E bus. I suspect this is a kernel module related problem. I've tried blacklisting the intel_agp module but it didn't help. I don't know if it's at all possible to keep the agpgart module from loading, but I haven't managed to do so.

I should underline the fact that this problem only reoccured after a driver reinstall and this has not been the case in my six weeks of normal usage with the same configuration. I've had the problem on first install, somehow remedied it, things went well for about six weeks, and now the problem is back after a reinstall of the drivers. In other words, I'm 100% sure that the problem is fixable. I've tried the 7676 driver as well, which is what I have installed at the moment, but it doesn't seem to fix anything.

Below are links to the relevant sections of my xorg.conf (I've tried removing every option one by one; it doesn't seem to be an xorg.conf related problem) and my X, installer and bug report logs. Any help appreciated.

[Xorg.0.log]("http://sh.nu/p/728")
[nvidia-installer.log]("http://sh.nu/p/727")
[nvidia-bug-report.log]("http://sh.nu/p/729")
[]("http://sh.nu/p/729")

---

### Post by Teroedni on 2005-11-24
Try to completely remove the glx -package  and revert to nv in xorg.
Then reconfigure your xorg and see if its get better. 


If its get better Install nvidia-glx, and hopefully everything will work


Yust remeber to completely remove nvidia-glx so no trace are left;)

---

### Post by 23meg on 2005-11-24
I did this countless times; unfortunately no luck.

---

### Post by 23meg on 2005-11-29
I've made a clean install of Breezy and upon first install of the drivers, bot via apt and with the official package, and I have the same problem. The only difference is that nvidia-settings shows a temperature of around 82 degrees this time.

---

### Post by Teroedni on 2005-11-29
You sure it is not the card failing?

---

### Post by oofnik on 2005-11-29
[QUOTE=23meg]nvidia-settings shows a temperature of around 82 degrees this time.[/QUOTE]
Celsius or Fahrenheit? If it's C that is pretty damn high, check the fan, see if it's still spinning. :???:

---

### Post by 23meg on 2005-11-29
[quote=Teroedni]You sure it is not the card failing?[/quote]I'm sure, because it worked fine until driver reinstall and it still works as supposed with Windows.

---

### Post by 23meg on 2005-11-29
[quote=oofnik]Celsius or Fahrenheit? If it's C that is pretty damn high, check the fan, see if it's still spinning. :???:[/quote]It's Celcius. The fan is spinning, and Nvidia settings shows a "slowdown threshold" of 104C so I thought 82 was acceptable. It's on the border of the red zone in the graphical display though.

---

### Post by 23meg on 2005-12-08
I reinstalled Breezy and the drivers, and the GPU temperature was back up to 82-85C, but no change in performance. I enabled ASPM for PCI-E in my bios and now the average temperature is around 70C, still no noticeable improvement in performance.

---

