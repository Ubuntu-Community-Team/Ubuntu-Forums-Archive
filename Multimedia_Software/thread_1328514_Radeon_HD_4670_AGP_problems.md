---
title: "Radeon HD 4670 AGP problems"
date: 2009-11-16
forum: Multimedia Software
---

### Post by Sea Bisquick on 2009-11-16
Ubuntu appears to highly dislike this video card.

I was running 9.04 fine with nVidia 7800 GS card, and upgraded successfully to 9.10. I replaced the video card with an HIS Radeon HD4670 AGP, and Ubuntu will not boot. I have tried 9.04 and 9.10 from live CD, no luck. I tried xfix with my 9.10 installation, no luck. I booted to recovery mode and installed the proprietary ATI driver successfully (from all appearances). Still no luck. Once the boot-up splash screen gets close to the end, the colors go all wonky, and then the screen just alternates slowly from black to a bunch of small, strangely colored Ubuntu logos. Any ideas?

---

### Post by markbuntu on 2009-11-16
remove the ati card and boot with the nvidia. Remove the nvidia driver and the ati driver. reboot again into the recovery kernel and use the fix x option. This should get you working with the generic VESA driver. Shut off the machine, install the ati card and in the bios disable the nvidia card and enable the ati card. continue the boot into the recovery kernel again and again use the fix x option so x can set up the VESA driver for the new card. Continue the boot and then you can get the ati driver with hardware manager. Make sure you have run update manager before installing the driver. Once the new driver is installer open a terminal and

sudo aticonfig --initial

This will initialize the new driver. reboot again and everything should work. Make any adjustments in the catalyst control center which you will find in your menus.

I know this sounds like a lot of work but really it is the only way.

---

### Post by Sea Bisquick on 2009-11-19
I haven't tried putting the nVidia card back in yet to revert to a VESA driver, but I plan to do that.

Am I correct in my understanding that 9.10 incorporates the latest driver and Catalyst Control Center from ATI? If so, wouldn't I just run into the same problems once I install the ATI driver package?

---

### Post by markbuntu on 2009-11-19
Your problem is not the ati driver, it is the nvidia driver which needs to be removed before the ati driver can work properly.

---

### Post by Sea Bisquick on 2009-11-20
I thought that I had removed the nVidia driver, but perhaps not. What's the right way to remove the nVidia and ATI drivers - ie the package manager?

---

### Post by jeantasse on 2009-11-20
Tell me markbuntu, are you saying that my ati radeon hd 4670 will finaly work with ubuntu?

---

### Post by Akita on 2009-11-21
Mine works perfectly and seems as fast or faster than my 8800GT and 9600GT with everything I've thrown at it (with fglrx). Can't wait for full support from the FOSS driver ;)

---

### Post by Sea Bisquick on 2009-11-27
OK - I got the card to work with the VESA drivers. After trying both the fglrx and proprietary drivers (both on fresh installs), still no luck. After the initial Ubuntu boot logo, the screen shuts off. (The Ubuntu start-up music plays, which makes me think the OS is running fine.) It's not the same as when there's no signal - the monitor does not show the 'no-signal' alert. It's similar to when windows shuts the monitor off after a long period to save power. By the way, I'm using the VGA output, as I have an old CRT. (The card also has DVI and HDMI out.) Is the VGA output somehow disabled by default in Linux? It works fine in Windows.

---

### Post by clhsharky on 2009-11-27
HI

Check out [ man radeon ]

The man pages says your card is supported.

I have read AGP can causes some hardware problems, but cant remember at the moment where I saw that. Sounds like your card is not identified properly.

Adding [CODE]AGP    -- AGP bus/CODE] to Device Identifier in xorg.conf file and turn off AGPFastWrite in BIOs should help.

If you do not know how, please ask for help.


[QUOTE]       Option "AGPMode" "integer"
              Set AGP data transfer rate.  (used only when DRI is enabled)
              1      -- 1x (before AGP v3 only)
              2      -- 2x (before AGP v3 only)
              4      -- 4x
              8      -- 8x (AGP v3 only)
              others -- invalid
              The default is to leave it unchanged.

       Option "AGPFastWrite" "boolean"
              Enable AGP fast writes.  Enabling this is frequently  the  cause
              of instability. Used only when the DRI is enabled. If you enable
              this option you will get *NO* support from developers.
              The default is off.

       Option "BusType" "string"
              Used to replace previous ForcePCIMode option.   Should  only  be
              used  when  driver's  bus  detection is incorrect or you want to
              force a AGP card to PCI mode. Should NEVER force a PCI  card  to
              AGP bus.
              PCI    -- PCI bus
              AGP    -- AGP bus
              PCIE   -- PCI Express bus
              (used only when DRI is enabled)
              The default is auto detect.
/QUOTE]

Sharky

---

### Post by Nilladar on 2011-08-19
I understand that this post is old, but I'm actually having this issue trying to install Ubuntu 11.04. The Livecd sorta boots, the unity bar on the side is a mass of graphical glitches and same with the top bar. The icons show up fine and I'm able to install the OS just fine as well. But like stated above on boot it defaults to a blank screen.

The card I'm using is ATI Radeon HD 4670 AGP version

---

### Post by taoh780 on 2011-08-31
> **Nilladar said:**
> I understand that this post is old, but I'm actually having this issue trying to install Ubuntu 11.04. The Livecd sorta boots, the unity bar on the side is a mass of graphical glitches and same with the top bar. The icons show up fine and I'm able to install the OS just fine as well. But like stated above on boot it defaults to a blank screen.

The card I'm using is ATI Radeon HD 4670 AGP version

If you have a login screen before Ubuntu loads your desktop:
At the bottom of the screen there is a menu that will let you choose your session. Pick 'Ubuntu Classic (No effects)' and you should now get a usable interface.

If you disabled your login screen and Ubuntu loads your desktop without a login:
Look for the menu that will let you log out. By default, it should be the last icon in the upper right corner along the panel. Just click once and wait several seconds until the menu appears and choose logout. You should then be able to choose your session.

If you want desktop effects to be usable, you can install the FGLRX proprietary drivers. On my system, it causes the playback of anything with audio to freeze the computer and I have to use the reset button to reboot. Removing the drivers will stop the freezing, but when playing youtube videos, the playback isn't smooth and it's like watching a slideshow.

Troubleshooting still in progress.

---

### Post by taoh780 on 2011-08-31
I pulled my sound card and used the on-board sound on my motherboard to see if that would change anything when I used the FGLRX drivers. The system would freeze when playing videos through youtube but for some reason, it didn't freeze while playing local audio/video files.

I ended up finding this and it looks like youtube videos are playing smoothly now nor has the system froze on me: [http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

As of this post, kernel 3.0.4 is the latest version available.

Instructions for installing the PPA are included on the xorg-edgers page given in the first post.

---

### Post by janagn on 2011-09-25
Hello,

I am getting also troubles with HD Radeon AGP 4670. My system boots up fine and may work with no problems for hours but then the desktop will freeze with no mouse or keyboard input. I can still access the system with SSH or I can reboot it with REISUB. I have noticed that freezes usually take place when resizing/moving windows and even more often if "the window" is any browser. Have been using the latest catalyst drivers following the wiki instructions as I need the 3D acceleration that is not available (I think) on the open source ATI driver. My system is an old Athlon 3200 build around the Gigabyte ga-7n400 pro2 mobo. It had been working fine with its old NVidia gpu but as it gave up spirit I got this HIS Radeon. Drivers from previous installation have been successfully removed (naturally as I reinstalled everything after running out of ideas).

Thanks in advance
Yiannis

---

### Post by sherwindm on 2011-11-27
I also have a 4670HD AGP and tried to install the FGLRX drivers it gives me an error saying failed to install drivers. Right now whenever I move a window it's all jittery with the VESA standard driver. Is there an optional driver which I can install or is this a 11.10 problem.

specs:

Intel Core2 Extreme QX6700
4 GiG RAM
120GB SSD

P.S    I just found out that there are NO LINUX DRIVERS for the 4670 AGP version on the ATI website. We are all screwed!!

---

