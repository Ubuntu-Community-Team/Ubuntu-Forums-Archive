---
title: "Why install ATI video cards the &quot;Ubuntu&quot; way ?"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by MaximB on 2008-01-29
I don't understand why those long guides and "how to's" about ATI drivers installation.
Why not just download the latest driver from AMD/ATI make it executable and "sudo" run it without creating any packages ?
It works for me every time.
The "Ubuntu" ways are longer, and doesn't always work.
The ATI way is much easier and faster.

I just don't get it...

---

### Post by eye208 on 2008-01-29
> **MaximB said:**
> The "Ubuntu" ways are longer, and doesn't always work.
The ATI way is much easier and faster.
The tutorials and HOWTOs circulating here are _NOT_ the Ubuntu way.

The Ubuntu way is: Open the "Restricted Drivers Manager", mark a checkbox, then reboot. It's even easier than the ATI (or Nvidia) way because it handles future kernel updates automatically.

---

### Post by erfahren on 2008-01-29
> **MaximB said:**
> I don't understand why those long guides and "how to's" about ATI drivers installation.
Why not just download the latest driver from AMD/ATI make it executable and "sudo" run it without creating any packages ?
It works for me every time.
The "Ubuntu" ways are longer, and doesn't always work.
The ATI way is much easier and faster.

I just don't get it...
easier to revert the changes

---

### Post by MaximB on 2008-01-29
> **eye208 said:**
> The tutorials and HOWTOs circulating here are _NOT_ the Ubuntu way.

The Ubuntu way is: Open the "Restricted Drivers Manager", mark a checkbox, then reboot. It's even easier than the ATI (or Nvidia) way because it handles future kernel updates automatically.

The problem with this way is that the ATI drivers don't update in the repro's.

---

### Post by eye208 on 2008-01-29
> **MaximB said:**
> The problem with this way is that the ATI drivers don't update in the repro's.
If you consider the lack of frequent updates a problem, you should use Debian instead of Ubuntu. Debian's "testing" and "unstable" repos always have the latest packages. Otherwise it's the same distro.

---

### Post by Adam_S on 2008-01-29
"make it executable and "sudo" run it without creating any packages"

I am pretty much a noob at this, can you please explain on how to do this?

---

### Post by MaximB on 2008-01-29
> **Adam_S said:**
> "make it executable and "sudo" run it without creating any packages"

I am pretty much a noob at this, can you please explain on how to do this?

1. Download the newest driver for your video card from amd/ati website.
2. in order to be able to run it as a program you must make it executable, by the command (in cli ofc) sudo chmod +x filename. 
You can also use the GUI , right click on the file>properties>check the execute box at the permission tab.
3. You must have root privileges to install those drivers so you type : sudo ./filename to run it.
4. Then just click install , restart the xserver and you are done.


P.S
If I'm not mistaken you no longer need to reinstall the ATI drivers after each kernel update.

---

### Post by terminal on 2008-01-29
^ Yes the new dkms system used by ati installer handles and compiles modules again for newly added kernels .  The ATI driver in ubuntu repository is very old and doesnt support newer cards , for eg. i can't get my radeon hd2600 pro to start with ubuntu's driver .

---

### Post by Adam_S on 2008-01-29
> **MaximB said:**
> 1. Download the newest driver for your video card from amd/ati website.
2. in order to be able to run it as a program you must make it executable, by the command (in cli ofc) sudo chmod +x filename. 
You can also use the GUI , right click on the file>properties>check the execute box at the permission tab.
3. You must have root privileges to install those drivers so you type : sudo ./filename to run it.
4. Then just click install , restart the xserver and you are done.


P.S
If I'm not mistaken you no longer need to reinstall the ATI drivers after each kernel update.

Thank you very much, it is greatly appreciated... but will this work with the ATI HD 3800 series? as i have been trying to get all the eye candy effects of Beryl+ Compiz fusion but have failed because apparently there is no driver support for this. But would it work if i grabbed the vista drivers and used this way to install the drivers? Or would that hurt my system? Sorry lot of questions, but we all have to start some where ><

---

### Post by MaximB on 2008-01-29
You can't use the windows's drivers for GNU/Linux.
I don't own ATI HD video card so I can't tell you for 100% but I don't see why the ATI drivers won't work, their newer drivers are much better then the older ones (about 4 months ago).
The compiz effects are a different story, first off course you need to install your video card drivers but after that you got loads of How-to's on the compiz fusion issue.

---

