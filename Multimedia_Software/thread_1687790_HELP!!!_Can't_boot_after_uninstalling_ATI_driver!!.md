---
title: "HELP!!! Can't boot after uninstalling ATI driver!!!"
date: 2011-02-14
forum: Multimedia Software
---

### Post by insecure hyena on 2011-02-14
Hello folks here's what I've done.
I've installed proprietary drivers from ATI (downloaded from the site of AMD) and then I uninstalled them simply by launching the script *fglrx*-*uninstall*.*sh* located in */usr/share/ati/*.
After reboot the system hang at the loading stage!!!
What I'm supposed to do now!!!
I'm really scared right now...I can't imagine to reinstall all my system from the start!!!
Help me please!

---

### Post by insecure hyena on 2011-02-14
Up! :cry:

---

### Post by fsleeman on 2011-02-14
I had the same problem and had to boot in safe graphics mode to undo my configuration. I tried to use the restricted drivers from Ubuntu but the right one didn't show up as I mentioned here ([http://ubuntuforums.org/showthread.php?t=1687295](http://ubuntuforums.org/showthread.php?t=1687295)).

What card are you using?

---

### Post by insecure hyena on 2011-02-15
Oh thanks someone responded me!
I'm using an ATI Radeon HD2400XT. But let me ask you one thing...how can i boot in safe graphic mode?
I tried to press Ctrl-alt-f1 when the pseudo black screen appeared but nothing happened!

P.S: again thank you very much.

---

### Post by Yellow Pasque on 2011-02-15
Hold shift after BIOS screen. Boot to recovery mode and choose root prompt with networking. Use the 6 commands in this section to fix your graphics: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

EDIT: Oh, and you may need to delete your /etc/X11/xorg.conf if dpkg-reconfigure command doesn't do it

---

### Post by rcuswalk on 2011-02-15
> **Temüjin said:**
> Hold shift after BIOS screen. Boot to recovery mode and choose root prompt with networking. Use the 6 commands in this section to fix your graphics: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

EDIT: Oh, and you may need to delete your /etc/X11/xorg.conf if dpkg-reconfigure command doesn't do it

I'm having the same problem as the OP, but I can't get the link for your six commands to work. Can you write the commands out for us? Thanks.

---

### Post by jocko on 2011-02-16
The link works just fine. I guess these are the commands you're looking for:```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```But the last command probably doesn't do anything anymore, so use this instead:
```
sudo rm /etc/X11/xorg.conf
```

---

### Post by rcuswalk on 2011-02-16
> **jocko said:**
> The link works just fine. I guess these are the commands you're looking for:```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```But the last command probably doesn't do anything anymore, so use this instead:
```
sudo rm /etc/X11/xorg.conf
```

Thanks. The commands worked perfectly. Also the link does work now; before it would take me to "about:blank" even though other websites worked right.

---

### Post by insecure hyena on 2011-02-18
I'm sorry for having abandoned this discussion but at the same time I fell pleased that it helped solving the problem.
Personally I haven't tried the over mentioned commands cause at the end I decided to format my hard drive and install the LTS Lucid.
However I appreciate all the interventions and so let me said thanks to everyone.
And if there's nothing to add let's mark this thread as [SOLVED]!

P.S: again thanks to everyone!!!\\:D/

---

