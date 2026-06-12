---
title: "Problem with ATI 1650"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by swartz on 2007-04-23
Hi!

Im a newbie at Linux.

I built a new computer, a very nice cube by the way! :) 

Now for the question. Ive got a Asus motherboard with an integrated nvidia 6150 card. And I also got a Asus Extreme PCIe  ATI 1650.

All hardware works fine on Windows XP...and works fine on Ubuntu 7.04 but only in Vesa mode and no ATI drivers installed...if I install ATI drivers my system freezes and the monitor gets black.

Does someone know what to do with this problem?

Full Hardware spec:
Asus M2NPV-VM GeForce 6150 Socket AM2
AMD Athlon 64 X2 4200+ (2,2GHz) Socket AM2 65W Box
2 GB DDR 2
Asus X1650 512MB PCI-E Silent

---

### Post by dannymichel on 2007-04-29
> **swartz said:**
> Hi!

Im a newbie at Linux.

I built a new computer, a very nice cube by the way! :) 

Now for the question. Ive got a Asus motherboard with an integrated nvidia 6150 card. And I also got a Asus Extreme PCIe  ATI 1650.

All hardware works fine on Windows XP...and works fine on Ubuntu 7.04 but only in Vesa mode and no ATI drivers installed...if I install ATI drivers my system freezes and the monitor gets black.

Does someone know what to do with this problem?

Full Hardware spec:
Asus M2NPV-VM GeForce 6150 Socket AM2
AMD Athlon 64 X2 4200+ (2,2GHz) Socket AM2 65W Box
2 GB DDR 2
Asus X1650 512MB PCI-E Silent

Same question, same hardware...
BUMP

---

### Post by cumbo87 on 2007-05-07
> **swartz said:**
> Hi!

Im a newbie at Linux.

I built a new computer, a very nice cube by the way! :) 

Now for the question. Ive got a Asus motherboard with an integrated nvidia 6150 card. And I also got a Asus Extreme PCIe  ATI 1650.

All hardware works fine on Windows XP...and works fine on Ubuntu 7.04 but only in Vesa mode and no ATI drivers installed...if I install ATI drivers my system freezes and the monitor gets black.

Does someone know what to do with this problem?

Full Hardware spec:
Asus M2NPV-VM GeForce 6150 Socket AM2
AMD Athlon 64 X2 4200+ (2,2GHz) Socket AM2 65W Box
2 GB DDR 2
Asus X1650 512MB PCI-E Silent
Same Question.

Appriciate it if someone knows how to fix this.

---

### Post by bender5788 on 2007-05-07
Yeah ive got a mate with the same problem same hardware (well mostly replace the x2 with a normal AMD64)

---

### Post by Golyadkin on 2007-05-12
Same problem, almost same hardware. I have an AMD X2 4200+ (EE 65W) with an X1650XT 256M PCI-e

---

### Post by cdemi on 2007-06-04
yea me 2 but AGP X1650

---

### Post by Dragonshadow on 2007-06-12
Wouldn't it be as simple as disabling it either on the motherboard or in the bios?

No I don't know how, jsut a thought.

---

### Post by Neodymion on 2007-10-08
Hardware:
ASUS X1650 AGP 256MB
Athlon 1900Mhz

I had a somewhat similar problem, monitor gave an out of scan range error until I deleted the stuff the FAQ said to add about modelines etc. in xorg.conf. I guess I did the calculation wrong or something. Don't know if that helps anyone...

---

### Post by crag277 on 2007-10-18
Hmmm, seems this is a widespread known issue without a solution!  That's a real bummer.  I have exactly the same problem with an AGP ATI 1650.  I need to install the driver because that's the only way to get my monitor's resolution (1680x1050).

I have tried using Ubuntu's Restricted Drivers Manager AND manually installing the ATI drivers.  I have also tried Fedora 7, PCLinuxOS 2007, and Mepis 6.5.  They ALL have the exact same problem.  Once the ATI driver is installed the system never makes it to the desktop.  Immediately before you would expect to see the login screen the screen goes black and does not respond to anything but the reset button.

Here are my system specs:
Asus P5PE-VM mobo
Intel 3.2 GHz P4
2 GB DDR RAM
ATI Radeon X1650 AGP 512 MB
On-board sound

Any help with this matter is much appreciated!

---

### Post by LinuxNewb_22 on 2007-10-18
I have a Sapphire Radeon X1650PRO PCIE and this is how I got it to work on a fresh install of Feisty.

BTW... these are the instructions from: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

However, I will post the exact list of commands that I used just to make it simple.

**1. System > Administration > Software Sources. Check "Proprietary Drivers for Devices (Restricted)" box.**

**2. In terminal, type:**
```
gksu gedit /etc/X11/xorg.conf
```

**3. Add the following to the file that pops up and SAVE the file immediately after and close:**
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```

**4. Download the ATI Linux fglrx driver version 8.40.4 to the desktop from here and save to Desktop:**
[http://www2.ati.com/drivers/linux/ati-driver-installer-8.40.4-x86.x86_64.run]("http://www2.ati.com/drivers/linux/ati-driver-installer-8.40.4-x86.x86_64.run")

**5. In terminal, change directory to Desktop:**
```
cd Desktop
```

**6. In terminal, type:**
```
sudo apt-get update
```

**7. In terminal, type:**
```
sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic
```

**8. In terminal, type:**
```
sudo bash ati-driver-installer-8.40.4-x86.x86_64.run --buildpkg Ubuntu/feisty
```

**9. In terminal, type:**
```
gksu gedit /etc/default/linux-restricted-modules-common
```

**10. Add "fglrx" to the line "DISABLED_MODULES" and SAVE the file immediately after and close:**
```
DISABLED_MODULES="fglrx"
```

**11. In terminal, type:**
```
sudo dpkg -i xorg-driver-fglrx_8.40.4-1*.deb fglrx-kernel-source_8.40.4-1*.deb fglrx-amdcccle_8.40.4-1*.deb
```

**12. In terminal, type the following (obviously hit Enter after every line and wait for terminal to get back to "$" before entering next line):**
```
sudo apt-get install -f
sudo rm /usr/src/fglrx-kernel*.deb
sudo apt-get -f install
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
sudo mkdir /lib/modules/$(uname -r)/volatile
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx -f
sudo module-assistant install fglrx -f
sudo depmod -a
```

**13. REBOOT!!**

**14. In terminal, type:**
```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo shutdown -r now
```

**15. Upon logging in, go to System>Administration>Restricted Drivers Manger and click "Enable your ATI driver"**
(The Restricted Drivers Manager should show as a green icon when you reboot and log in from "sudo shutdown -r now" anyway, but the above merely shows how to get there in case you quickly close that pop-up.)

I hope this helps. Let me know if you want to know how to add Compiz once you have your graphics card working.

---

### Post by starbase1 on 2007-10-18
My ATI Radeon X1650 worked fine directly from the live CD with Feisty, but now I am trying it with the brand new Gutsy CD, and it won't come up at all...

It goes through the usual text then Ubuntu graphic at startup, with the logo and the orange progress bar. After a minute or two the orange bar completes, and the screen flashes some mess briefly before showing a few messages about the deferred execution scheduler (?), checking battery state, and running local boot scripts.

Then I get a message on a screen that looks like it is tring to use the wrong font to draw a frame about the display server shutting down six times in 90 seconds, and "something bad is going on"

When I try safe graphics mode, exactly the same.

Nick

---

### Post by LinuxNewb_22 on 2007-10-18
Ah, ok. I guess that's something that would prevent you from following the instructions that I posted!

Have you tried installing using the Alternate ISO?

As a last resort... I would install Feisty, run the instructions that I posted and wait a while before going to Gusty.

BTW... if you install using the alternate iso for Gutsy and it works (you manage to "get in") then you will have to change this line...
```
sudo bash ati-driver-installer-8.40.4-x86.x86_64.run --buildpkg Ubuntu/feisty
```

to...
```
sudo bash ati-driver-installer-8.40.4-x86.x86_64.run --buildpkg Ubuntu/gutsy
```

Hopefully something works for you... I know how frustrating it can be. (I've reinstalled my entire system over a DOZEN times since I bought my new desktop 3 weeks ago! - deciding between Gutsy and Feisty, I stuck with Feisty because I managed to get Compiz to work)

---

### Post by starbase1 on 2007-10-18
Alternate ISO?!?! Am I missing something obvious here?

---

### Post by LinuxNewb_22 on 2007-10-18
> Alternate ISO?!?! Am I missing something obvious here? 

Go to the download page:
[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

Choose the Desktop Edition, the type of computer (x86, 64bit, or UltraSPARC), the download location and then BEFORE clicking download, check the box next to "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

This is the Alternate ISO. It is the text-based installer. In order to install with this, you will have to set your boot order to read from the CD/DVD drive before the hard drive. You've probably already done this for the Live CD.

Once the installer boots, make sure the first option is highlighted ("Use text-based installer" or "Install Ubuntu" .... or something like that... basically the first option installs the OS)...press Enter and go through the rest of the install process to get a fresh install.

BTW... I just read in the Gutsy Release Notes that this is a problem with ATI hardware:
[http://www.ubuntu.com/getubuntu/releasenotes/710]("http://www.ubuntu.com/getubuntu/releasenotes/710")

Now where it says, "In the meantime, add 'Option "LVDSBiosNativeMode" "false"' to the driver section of xorg.conf." ... I believe it means to do the following...
In terminal, type:
```
gksu gedit /etc/X11/xorg.conf
```

Then add to the bottom of the file (don't forget to save the file before closing)...
```
Section "driver"
Option "LVDSBiosNativeMode" "false"
EndSection
```

....again... hope that helps... if not, stick to Feisty for now! ;)

---

### Post by starbase1 on 2007-10-19
Thanks for that - though I must admit I understand very little of it! I may just hold off on Gutsy for a while. Is there any history of how long I might expect to wait for a fix for this sort of thing?

(And why do you call yourself newb when you seem to jhave pretty deep knowledge from what I can see?!?!)
:lolflag:

---

### Post by landcross on 2007-10-19
Also on a ATI 1650 with problems now writing this post from Windows XP as cannot reconfigure X. I tried this posting advice after no solutions to my own posting.

But regretably it did not work for me. Probably due to my own config files being already messed up.

---

### Post by LinuxNewb_22 on 2007-10-19
> **starbase1 said:**
> Thanks for that - though I must admit I understand very little of it! I may just hold off on Gutsy for a while. Is there any history of how long I might expect to wait for a fix for this sort of thing?

Yes, I would suggest holding off on Gutsy until about the new year. By then I'm sure that some of the kinks with the ATI cards will be worked out with Gutsy (personally I'm waiting until the next long term support release 8.04 Hardy Heron).

Also by the new year ATI will have come out with version8.44/8.45 of their open fglrx driver which will make it much easier for the ATI hardware to play nice with Ubuntu.

I can't really tell you on what, if any, timeline there is for bug fixes. I suggest checking the bug fix # that was posted in the Release Notes that I linked you to earlier:
[http://www.ubuntu.com/getubuntu/releasenotes/710]("http://www.ubuntu.com/getubuntu/releasenotes/710")

In the meantime, have you got Compiz up and running in Feisty? The effects from that should hold off the impatience for a while! I know it's tempering my craving to have the latest and greatest!

> **starbase1 said:**
> (And why do you call yourself newb when you seem to jhave pretty deep knowledge from what I can see?!?!)
:lolflag:

As I wrote earlier, having to install this thing over a dozen times in 3 weeks has forced me to remember the steps that I've taken to get 4 major things to work for me:
1. RAID 0 configuration (makes things so much faster!)
2. ATI working
3. Compiz
4. Sound

I've merely been following instructions posted by the very helpful people on this forum. Until I start to understand some of it... still a newbie! :)

---

### Post by LinuxNewb_22 on 2007-10-19
> **landcross said:**
> Also on a ATI 1650 with problems now writing this post from Windows XP as cannot reconfigure X. I tried this posting advice after no solutions to my own posting.

But regretably it did not work for me. Probably due to my own config files being already messed up.

Did you try a fresh install of Feisty using the Alternate ISO? I'm sure if, after backing up, you completely wipe your HDD and install Feisty you could get it working.

---

### Post by crag277 on 2007-10-19
I like your method!  I will try it on Gusty sometime this weekend when I have more time and will post my results.

Also, if you have time and don't mind posting how you got Compiz and all that fancy stuff working I would greatly appreciate it.

---

### Post by LinuxNewb_22 on 2007-10-19
The instructions for Compiz are taken from both:
["How To : Compiz Fusion for ATI cards + Xgl in Feisty"]("http://ubuntuforums.org/showthread.php?t=488385") ;and,
[Forlong's Blog]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty").

As you may notice, in all of the instructions I have posted, I do NOT provide any explanations as to why each step must be done. If you'd like them, please see the websites that I have linked to.

**Make sure, after installing the fglrx driver for your ATI card you enable the restricted driver:**
```
System > Administration > Restricted Drivers Manger
...check the box.
```

**REBOOT!**

**Make sure your system is up to date:**
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

(You will likely have to reboot each time after the "upgrade" and "dist-upgrade" commands)

**In terminal, type:**
```
sudo apt-get install xserver-xgl
```

**Then type:**
```
sudo gedit /usr/local/bin/startxgl.sh
```

**Copy and paste the following into the window that pops up:**
```
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

**Save the file. Close it.**

**In terminal, type:**
```
sudo chmod a+x /usr/local/bin/startxgl.sh
```

**Then type:**
```
sudo gedit /usr/share/xsessions/xgl.desktop
```

**Copy and paste the following into the window that pops up:**
```
[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

**Save the file. Close it.**

**In terminal, type:**
```
sudo chmod a+x /usr/share/xsessions/xgl.desktop
```

**Logout.**

**At the Login screen ... Sessions (bottom left) > Change Session > GNOME with XGL.**

Enter your Login username and password.

**Choose "Make this the Default Session" when prompted.**

Sometimes the XGL session goes all screwy - warped/deformed/blurry. Not to worry. Just reboot the computer... I know you can't exactly see it but click the blurred button on the top right of the screen, then on the window that pops up, the "Shutdown" option will be on the bottom right - which you know you are hovering over because the already screwy screen will blur differently over the area.

[If you keep rebooting and you get the same blurry screen, then simply log back in with the normal Gnome session and try reinstalling the ATI driver using the instructions that I posted earlier in this thread. THEN follow this post's instructions again. If it STILL does not work, try reinstalling Feisty (fresh install) and follow the (1) ATI driver install instructions and (2) the instructions in this post.]

**Upon successful login, go to:**
```
System > Administration > Synaptic Package Manager
```

Click the "**Search**" button. Type ***compiz*** (if it's not set by default, choose, "Look in: Description and Name").

Then **click on the box** next to all the installed packages we found and **choose "Mark for Removal"**. Afterwards, **click "Apply"**.

**Click "Settings"** and **choose "Repositories"** - that will start the "Software Sources" application where you **click "Third Party Software"** tab and **click "Add"**...

**For the APT line, type:**
```
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
```

**Close the "Software Sources" window**. A prompt will likely appear saying that you need to reload the repositories. So in Synaptic, **click "Reload"** to do so. 

Search for ***compiz*** again.

**Click on the empty boxes and choose "Mark for Installation" for the following:**
```
compiz
```
```
compizconfig-settings-manager
```

**Click Apply.**

Due to a bug, the version number of compiz-core doesn't get updated and therefore Synaptic wants to upgrade the package all the time, although it's already the latest available. So **go back to Settings > Repositories > Third Party Software**. **Uncheck the box** next to the source that you added a couple of steps before.

Close the "Software Sources". **Click Reload**. Close Synaptic.

**Before we launch Compiz for the first time, Go to:**
```
System > Preferences > CompizConfig Settings Manager
```
 
**Click "Preferences"**, in the "Backend" section **choose "Flat-file Configuration Backend"**.

**Create a new profile**, so that you can easily switch back to default and back. To do so, **click [+] in the "Profile" section**. 

**Click "Back"** and look for the **"Window Decoration" button**. Click it.

Right next to **"Command"**, **type *gtk-window-decorator***.

Close CompizConfig Settings Manager.

**Press [Alt]+[F2] to start "Run Application" and type:**
```
compiz --replace
```

This should start Compiz with your standard window boarder. 

**In order to load Compiz on startup, go to:**
```
System > Preferences > Sessions > Startup Programs
```

**Click "Add", type "Compiz" in "Name" and "compiz --replace" in the "Command" area. Apply that change.**

**Reboot.**

---

### Post by LinuxNewb_22 on 2007-10-19
In order to configure all of the cool Compiz stuff, see this blog entry:

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

Have fun with it!

---

### Post by crag277 on 2007-10-19
OK, I gave it a shot, but still no go.  I will try with Feisty later just to make sure, but I'm not going to be holding my breath.

The installation went fine with no errors, and after the first reboot everything seemed to be in order, but the resolution was way too low.  I ran the two aticonfig commands and rebooted, and then I got the dreaded black screen.

There must be something written to the xorg.conf file during the ATI initial setup that breaks the X server for X1650s, but what?!

---

### Post by LinuxNewb_22 on 2007-10-19
Hmmm, so you tried it with Gutsy and a no go... I assume that in following the instructions that I posted (post #10 in this thread) that you changed the line:
```
sudo bash ati-driver-installer-8.40.4-x86.x86_64.run --buildpkg Ubuntu/feisty
```

to...
```
sudo bash ati-driver-installer-8.40.4-x86.x86_64.run --buildpkg Ubuntu/gutsy
```

Did you take note of the problem with ATI hardware in Gutsy posted in the Release Notes?
```
http://www.ubuntu.com/getubuntu/releasenotes/710
```

Apparently, the temporary fix is to add
```
Option "LVDSBiosNativeMode" "false"
```
to the drvier section of /etc/X11/xorg.conf file.

However, as I wrote earlier, I would stick with Feisty for the time being and wait for the next update(s) to the ATI fglrx driver and the bug fixes for Gutsy.

---

### Post by crag277 on 2007-10-19
Correct, I did change "feisty" to "gusty", but the ATI driver does not have a package for gusty yet, so I build and installed the feisty one.  That's probably the biggest problem right there.

I had not seen teh release notes until now.  I will try adding that line to my xorg.conf, but I agree that a fresh feisty install is probably the best way to go.

---

### Post by crag277 on 2007-10-20
I tried it again with feisty and still had the same problem.

Maybe the next version of fglrx...

---

