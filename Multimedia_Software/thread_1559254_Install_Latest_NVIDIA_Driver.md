---
title: "Install Latest NVIDIA Driver"
date: 2010-08-23
forum: Multimedia Software
---

### Post by rykel on 2010-08-23
Hi, I want to install the official NVIDIA driver instead of using the outdated one provided by "Hardware Driver".

Do I need to remove all "nvidia-*", "nouveau" and "nv" drivers first?

Also, there used to be Envy, which easily installs the latest NVIDIA driver. Does anyone know if it is still available?

---

### Post by Linuxforall on 2010-08-23
> **rykel said:**
> Hi, I want to install the official NVIDIA driver instead of using the outdated one provided by "Hardware Driver".

Do I need to remove all "nvidia-*", "nouveau" and "nv" drivers first?

Also, there used to be Envy, which easily installs the latest NVIDIA driver. Does anyone know if it is still available?

Easiest and safest least hassle way, add x-swat ppa.

In terminal paste sudo add-apt-repository  ppa:ubuntu-x-swat/x-updates 

sudo apt-get update
sudo apt-get upgrade

Go and enable hardware driver for latest 256.xx drivers.

---

### Post by rykel on 2010-08-23
Hi, with regards to x-swat ppa, it was easy alright, but safest, no.

After installing, my system cannot go into any GUI. I have removed all traces of nvidia, nv and nouveau as well from Synaptic Package Manager.

What can I do now to restore my system?

---

### Post by hsoulen on 2010-08-24
> **rykel said:**
> Hi, with regards to x-swat ppa, it was easy alright, but safest, no.

After installing, my system cannot go into any GUI. I have removed all traces of nvidia, nv and nouveau as well from Synaptic Package Manager.

What can I do now to restore my system?

Hey there,

I just download the latest binaries from Nvidia: [http://www.nvidia.com]("http://www.nvidia.com/")


[LIST=1]
[*]Select the driver for your card and either Linux 32/64 bit.
[*]Save the file to a folder other than desktop (your home folder is fine)
[*]Exit your window manager (for gnome it's gdm-stop)
[*]Login at the text only prompt
[*]Sudo su
[*]Run the installer: ./NVIDIA-Linux-x86-256.44.run
[*]Answer the questions and reboot
[/LIST]
If you do it this way you will have to re-install every time you install a new kernel.

Alternatively you can always just select "nvidia-current" in synaptic, this is not always the newest driver but at least you will know it has been tested. 

Since you have no GUI you can just run "sudo apt-get nvidia-current".

Cheers,

Hank

---

### Post by rykel on 2010-08-24
Well, I installed the x-swat nvidia driver, and now I have a BIGGER problem.

Not only is the GUI gone, even the ability to see the commandline is GONE!

Now what remains is only a few random stripes of white and blue near the top of my screen, and black screen.

I believe the system is still running, but the black screen is hiding its activity from my view.

---

### Post by rykel on 2010-08-24
Hi all, I managed to get my GUI back.

Actually, the system was indeed running, except that the GUI was not loading properly. So I literally issued the following commands blindly - as if somebody blindfolded me, and it worked!

I am able to do it because I used the terminal enough and remembered the behaviour of Ubuntu!

[INDENT][B]<my username>
<Enter>
<my user password>
<Enter>
sudo dhclient3 eth0 <-- to activate my LAN internet
<Enter>
sudo apt-get remove --purge nvidia-current nvidia-current-modaliases nvidia-settings
<Enter> <-- wait for a minute for apt-get to remove all traces of NVIDIA
sudo reboot
<Enter>
[/B][/INDENT]
Hope this helps anyone in my shoes!

---

### Post by Linuxforall on 2010-08-24
> **rykel said:**
> Hi, with regards to x-swat ppa, it was easy alright, but safest, no.

After installing, my system cannot go into any GUI. I have removed all traces of nvidia, nv and nouveau as well from Synaptic Package Manager.

What can I do now to restore my system?

xswat is the safest, don't know what you had done previously, this is the method that works best with Ubuntu and is developed by Ubuntu devs. Also it integrates with hardware drivers. Now its too late as you have removed essential files needed for nvidia drivers to install properly. Are you sure you selected the right drivers in hardware applet?

---

### Post by rykel on 2010-08-25
> **Linuxforall said:**
> xswat is the safest, don't know what you had done previously, this is the method that works best with Ubuntu and is developed by Ubuntu devs. Also it integrates with hardware drivers. Now its too late as you have removed essential files needed for nvidia drivers to install properly. Are you sure you selected the right drivers in hardware applet?

Yes, it was "nvidia-current" that I selected.

btw, I did a "sudo apt-get install ubuntu-desktop" to ensure that my system is a pristine setup again, tried x-swat once more and still, I get the black screen.

Maybe my card is not supported by the latest driver? (in which case x-swat should use the next highest version driver that does support it)

---

### Post by squidpotion on 2010-08-25
I'm having somewhat of a similar problem.

I've tried nearly everything. Installing from terminal, installing from Synaptic, installing with the GUI off, installing the official drivers off the nvidia site... Every time I try to install this thing, my resolution is HUGE and I can't change it through ubuntu or through nvidia. It also puts my taskbar icons all out of order, so then I have to completely uninstall everything nvidia and run in low graphics mode, which makes Docky lag, but my resolution doesn't rape my eyes. Not to mention that I can't run Compiz, because it'll automatically install the driver and I can't use compositing. 

Anyone have a solution? Maybe install the earlier driver? I have a GeForce 8200, if that helps.

---

### Post by Linuxforall on 2010-08-25
> **rykel said:**
> Yes, it was "nvidia-current" that I selected.

btw, I did a "sudo apt-get install ubuntu-desktop" to ensure that my system is a pristine setup again, tried x-swat once more and still, I get the black screen.

Maybe my card is not supported by the latest driver? (in which case x-swat should use the next highest version driver that does support it)

For Go6600 use the older 173xx series driver, not nvidia-current.

---

### Post by squidpotion on 2010-08-25
Now Ubuntu stalls at the splash screen and it won't even boot up. Great.

Any suggestions on how to get Ubuntu up and running again?

---

### Post by realzippy on 2010-08-25
@ squidpotion

Had some,but suggest to open your "own" thread.
Threadnapping confuses a thread....

---

### Post by squidpotion on 2010-08-25
> **realzippy said:**
> @ squidpotion

Had some,but suggest to open your "own" thread.
Threadnapping confuses a thread....

Thanks, I did. I thought about that but didn't want to start a whole new thread and add clutter to the board.

---

### Post by rykel on 2010-08-26
> **Linuxforall said:**
> For Go6600 use the older 173xx series driver, not nvidia-current.

Right... I guess my card is indeed very OLD and apparently abandoned by NVIDIA already.   :(

Anyway, I purged ubuntu-desktop, jockey-gtk, jockey-common and all nvidia/nouveau* from my system, reinstalled ubuntu-desktop and have gone back to letting Ubuntu choose the driver for my card.

Thank you!

---

### Post by Linuxforall on 2010-08-26
> **rykel said:**
> Right... I guess my card is indeed very OLD and apparently abandoned by NVIDIA already.   :(

Anyway, I purged ubuntu-desktop, jockey-gtk, jockey-common and all nvidia/nouveau* from my system, reinstalled ubuntu-desktop and have gone back to letting Ubuntu choose the driver for my card.

Thank you!

No in fact nvidia updated their 173 series drivers for your card so you can install that version without any hitch.

---

