---
title: "HP DeskJet 610C"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by Zanthador on 2008-01-29
[SIZE="4"]I have an HP DeskJet 610C, and the system detects it just fine. However, with the stock installer, I cannot do any maintenance operations such as printing a self-test page or cleaning the printing heads. When I launch the printing configuration from the Administration menu, those features are simply disabled.

I also tried using HPLIP. I installed it first from Synaptic, but the same features were not available either. After that, I tried downloading the latest version from their site and using that to configure my printer. It did not detect it. I really want to know how I can perform mantenance operations on my printer, it wouldn't be nice buying a new one just because I can't maintain this one...

Any advices?[/SIZE]

---

### Post by linuxwizard on 2008-01-29
Are you using the HP Toolbox/HP Device Manager ? Also I have seen some models the maintenance feature are not available for certain models.

---

### Post by Zanthador on 2008-01-29
Yes, I'm using those. If you say maintenance are not available for some models, then how should I still do it? The big problem is, that it doesn't print straight, despite how I position the paper. It always tilts it to the side for some reason.

---

### Post by linuxwizard on 2008-02-02
I just noticed that no one else answered you or offered any other suggestions. Your printer [COLOR="Red"]does not[/COLOR] have Services and Status. > [http://hplip.sourceforge.net/supported_devices/inkjet.html](http://hplip.sourceforge.net/supported_devices/inkjet.html)

"Services and status" means that ink/toner levels, error reporting, and services such as alignment, and color calibration are available (via the HP Device Manager aka Toolbox)


I tried searching around to see what I could find to help. This is no guarantee this will work but in terminal type > hp-align >> for cartridge alignment 
in terminal type > hp-clean >> for cartridge cleaning

Let me know how it goes if you decide to use it.

---

### Post by Zanthador on 2008-02-02
Thank you for your answer, linuxwizard. Unfortunately, cleaning and alignment cannot be initiated from the command line either. See below:

---

zanth@master:~$ hp-align

HP Linux Imaging and Printing System (ver. 2.7.7)
Printer Cartridge Alignment Utility ver. 4.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hp:/par/DESKJET_610C?device=/dev/parport0
warning: No status available for device.
error: Alignment not supported or required by device.
zanth@master:~$ hp-clean

HP Linux Imaging and Printing System (ver. 2.7.7)
Printer Cartridge Cleaning Utility ver. 3.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hp:/par/DESKJET_610C?device=/dev/parport0
warning: No status available for device.
error: Cleaning not needed or supported on this device.

Done.
zanth@master:~$ 

---

Well, I guess that all sums it up. I know my printer isn't supported when it comes to supplies, but I was hoping there would be an alternate way of maintaining it. I guess the only solution is to either get over it or start gathering up for a new, better supported printer.... :lolflag:

But hey, thanks for taking the time to help me. Really appreciated. :)

---

### Post by linuxwizard on 2008-02-02
I am out of ideas for you not sure where else to search. That printer is a older model. Best thing to do is buy a new one. I would suggest buying another HP though. Good Luck

---

### Post by Zanthador on 2008-02-02
Thank you very much. :)

---

