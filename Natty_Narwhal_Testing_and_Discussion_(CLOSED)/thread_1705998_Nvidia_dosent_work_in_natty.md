---
title: "Nvidia dosent work in natty"
date: 2011-03-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sda123 on 2011-03-13
I upgraded to 11.04 natty narwhal alpha 3 thinking the nvidia drivers i had installed would work but when i rebooted my laptop it didn't have any use of 3d acceleration at all in fact it was up-scaling 640 x 480 to 1280 x 800. When i try to install the right drivers it says it successfully installed but then i reboot and nothing happens to 3d acceleration. Please help i an looking forward to compiz based unity!:?#-o

---

### Post by cariboo on 2011-03-13
You may have to open a terminal and run:

```
sudo nvidia-xconfig
```

the above command will create a new /etc/X11/xorg.conf file, in most cases you shouldn't need one, but in your case you might.

---

### Post by sda123 on 2011-03-13
> **cariboo907 said:**
> You may have to open a terminal and run:

```
sudo nvidia-xconfig
```the above command will create a new /etc/X11/xorg.conf file, in most cases you shouldn't need one, but in your case you might.
Tried that, just says ubuntu is running in low graphics mode. I switch the drivers to nv and it works perfectly but i would rather prefer 3d acceleration!

---

### Post by Harry33 on 2011-03-13
> **sda123 said:**
> Tried that, just says ubuntu is running in low graphics mode. I switch the drivers to nv and it works perfectly but i would rather prefer 3d acceleration!

How did you install the nvidia proprietary drivers?
What driver version are you using?
What xserver version do you have installed?
What is your graphics card model?

---

### Post by sda123 on 2011-03-14
> **Harry33 said:**
> How did you install the nvidia proprietary drivers?
What driver version are you using?
What xserver version do you have installed?
What is your graphics card model?

Installed by running the .run file
I an using Nvidia geforce FX 5200 173.14.28
dont know what xserver version
Nvidia geforce Fx 5200

---

### Post by Harry33 on 2011-03-14
> **sda123 said:**
> Installed by running the .run file
I an using Nvidia geforce FX 5200 173.14.28
dont know what xserver version
Nvidia geforce Fx 5200

When did you do that .run file installation?
If it was before you "upgraded" to Natty,
the driver will not work with Natty's xserver 1.10 rc2.

You need to uninstall the .run file completely.
Then delete the file /etc/X11/xorg.conf.
Then install xserver-xorg-video-nouveau.

I think you can only use the open source nouveau driver in Natty.
You see nvidia-current does not anymore support series 5 GeForce cards.
And the older drivers (96 and 173) do not support new xserver (video ABI 9).

Perhaps the best solution for the time being is to reinstall (a clean installation) Maverick (10.10).
Natty is in heavy development and by no means ready for every day stable use.

---

### Post by cariboo on 2011-03-14
The driver you installed, doesn't support the Xorg-xserver version used in Natty. Have you tried the driver from the repositories?

---

### Post by sda123 on 2011-03-17
> The driver you installed, doesn't support the Xorg-xserver version used in Natty. Have you tried the driver from the repositories?
Where do I get them from?

---

### Post by beew on 2011-03-17
Does jockey (additional drivers) work anymore in Natty?

The nouveau driver in Natty is no good either, installed the libgl1-mesa-dri-experimental package but 3d effects are sluggish, rotating cube has a lot of tearing (in both classical desktop and Unity). In the classical desktop the Cairo Dock actually freezes. Whereas the nouveau driver works reasonably well in Maverick. I install Natty in an external drive to do tests. The Maverick installed with the nouveau driver is also in the same drive, I use Nvidia's graphic driver for the "real" Maverick installation in the internal drive.

Why are people in such a rush to upgrade? I don't get it.

---

### Post by cariboo on 2011-03-17
Some people may be confused, as Hardware Drivers is now called Additional Drivers.

sda123, just click the Applicaion icon in the panel and type **add** in the search box

---

### Post by t.rei on 2011-03-19
[http://phoronix.com/forums/showthread.php?35420-New-Nvidia-drivers-with-Xserver-1.10-support-270.30](http://phoronix.com/forums/showthread.php?35420-New-Nvidia-drivers-with-Xserver-1.10-support-270.30)

the 270.30 is the first driver to actually support the server 1.10.

Unfortunately I am having a really crash-prone compiz right now, and not shure where this is coming from. I can't complain, though: running beta drivers on an alpha state os is bound to get "interesting".

---

### Post by dino99 on 2011-03-19
have no trouble with nvidia 270.30 without compiz

---

### Post by rburkartjo on 2011-03-19
dino same on my end

---

### Post by insaini on 2011-03-19
try adding xorg-edgers ppa and x-swat ppa .. update and upgrade

---

### Post by VinDSL on 2011-03-19
> **t.rei said:**
> Unfortunately I am having a really crash-prone compiz right now, and not shure where this is coming from.
Compiz has been crashing on me too, since the 270.30 update.

I can easily reproduce it by opening an "Extra Window" in Nautilus.

But, it happens in other proggies too...

When this happens, the Unity Dashboard & Launcher disappears... plus the title bar in any open windows disappears -- forcing a restart.

> **t.rei said:**
> I can't complain, though: running beta drivers on an alpha state os is bound to get "interesting".
Heh!  For sure!  :D

---

### Post by rburkartjo on 2011-03-19
in, didnt work for me got this error

W:Failed to fetch [http://ppa.launchpad.net/x-swat/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/x-swat/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/x-swat/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/x-swat/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by kuvanito on 2011-03-19
Intel based desktop with Nvidia Card working beautiful here.
I don't do upgrades,rather full installs.So far so good...:P

---

### Post by thiebaude on 2011-03-19
No problem with jockey, after I installed 11.04, I was notified that graphic card drivers were available, and the i installed the recommended driver for my Nvidia 8400 gs card.I still have to problem of not being able to do updates, but thats not a big deal, i'll wait til they get that sorted out.And also im using the classic desktop.I have to say when I started the computer this morning I got a purple screen and nothing else, I was worried at first, but then I did a reboot, and everything was fine after that.Just the hiccups that can be expected from testing a developement OS, but I think i'll stick with it.
:)

---

### Post by thiebaude on 2011-03-19
I just noticed my spelling errors,lol:D

---

### Post by dino99 on 2011-03-19
> **rburkartjo said:**
> in, didnt work for me got this error

W:Failed to fetch [http://ppa.launchpad.net/x-swat/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/x-swat/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/x-swat/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/x-swat/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

x-swat ?????? not very updated, so dont use it (and uncheck "source" if missed)

---

### Post by Harry33 on 2011-03-19
> **rburkartjo said:**
> in, didnt work for me got this error

W:Failed to fetch [http://ppa.launchpad.net/x-swat/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/x-swat/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/x-swat/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/x-swat/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

You got a wrong link.
Get the right one from here (X Updates PPA):
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

However, there is nothing for Natty right now.

---

### Post by t.rei on 2011-03-20
> **VinDSL said:**
> ...
When this happens, the Unity Dashboard & Launcher disappears... plus the title bar in any open windows disappears -- forcing a restart.
...

Just a friendly hint: you don't have to restart the whole system.

Just create a desktop launcher for "compiz --restart" and click that, after it crashed. Panel and docks will become visible again.

---

### Post by VinDSL on 2011-03-22
> **VinDSL said:**
> Compiz has been crashing on me too, since the 270.30 update.[...]
w00t!

Today's update(s) cured the Compiz crashes, for me, when opening an "Extra Pane" in Nautilus.

Actually, I traced this down to opening an extra pane, **and** SFTP'ing into my web server in Atlanta.

The main culprit was gvfsd-sftp

Put another way, gvfsd-sftp has been crashing Compiz, since I installed 270.30

Nautilus was just a "person of interest" in the Compiz Murder Case!

LoL!  Oh, what a tangled web we weave...  :D

---

### Post by VinDSL on 2011-03-22
> **t.rei said:**
> Just a friendly hint: you don't have to restart the whole system.

Just create a desktop launcher for "compiz --restart" and click that, after it crashed. Panel and docks will become visible again.
Thanks!

Yeah, I tried all the usual tricks, but...

When Compiz crashed, it was like throwing a hand grenade into a crowded room!

It fragged any programs that were running, the mouse, the display, blah, blah, blah.

Restarting was the only way to fully recover...  ;)

---

