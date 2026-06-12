---
title: "&quot;Venetian blinds&quot; screen with nVidia cards"
date: 2011-03-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quaxo76 on 2011-03-14
This is a problem I've had since Lucid Lynx, but it's still unresolved and now it makes the system impossible to use for me. The short description of the symptom: the screen, after Natty has booted, looks sort of like looking through venetian blinds. This is both using the live cd AND after installing to HD, using the "standard" (non-restricted) drivers, on nVidia hardware (this is the output of lspci: 00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
)

I had this problem on 4 different computers, all using (different) nVIdia cards.

To better describe the effect: the whole screen is divided in horizontal bands, more or less 20 pixels high; and in each band, the topmost row of pixels is OK, while the bottom row of pixels is a "clone" of the top row of the whole screen (so usually a solid gray, because there's the menu panel up there); and all the pixel rows inbetween are a smooth "gradient" between the two. 
And, on the left part of the screen, on a column maybe 40 pixels wide, I can see what should be on the right edge of the page (for example the shutdown button is on the top left, not top right).

This problem has been there since Lucid, but it only made installation difficult, because after I could just install the restricted drivers and the problem would go away. In natty, if I install the nvidia drivers, the computer just hangs - it displays a black screen and I have to manually reboot. So I can't use the system.
It would also be nice if the live CDs didn't show this problem - once I was installing Maverick on a friend's computer (she has a nVidia card too), and while I was installing, she looked at the screen and asked why her pc was looking like venetian blinds... She didn't have a good first impression, needless to say!

So, is this a known problem? I tried searching around but didn't find anything. A temporary fix to be able to get it running would be OK, but it'd be great if the liveCD would just work out of the box...

Thank you,
Cristian

PS - I can't post a screenshot of the problem, because screenshots come out OK. If needed I can physically take a photo of the screen...

---

### Post by Quaxo76 on 2011-03-15
Hm... Anybody? Right now I can't use the system at all - when I try to boot, it ends up with a black page with a purple-ish band at the top, and I can only reboot (not even Ctrl-Alt-F1 works). If I boot in "safe mode" and uninstall the nVidia drivers, then I get the "venetian blinds" screen again, and though that doesn't crash, it's just unusable - and by the way, I forgot to mention that when I get the venetian blinds effect, the screen resolution is lower than optimal, and Unity does not load.

What really surprises me is that I get that behavior on several different computers - and not with some hacked/modified system, but with just a plain vanilla live Natty (or Maverick or Lucid) USB key - which makes me think it's a common problem... yet I can find nothing online about it. 

Cristian

---

### Post by VMC on 2011-03-15
From a terminal run nvidia-settings - or from dash type nvidia and select it that way. 
What does it show from your driver? Here's mine. I had a similar issue but that was back a couple of weeks.

---

### Post by Quaxo76 on 2011-03-15
VMC, thanks for your reply.
- If I boot the liveCD and run "nvidia-settings" from the terminal, I get a message saying that the program is not installed. (the liveCD doesn't use the 3D drivers by default).
- If I boot the installed system in "low graphics mode", I only get a desktop background and a mouse pointer - no launchers, no menu bar, no nothing. I can just reboot. Even alt+F2 doesn't work.
- If I boot the installed system in "normal mode", I get a black screen and nothing else.

I attached a screenshot of what I get after booting the liveCD. Sorry for the bad quality but I only have my cell phone with me now.

Cristian

---

### Post by prettl on 2011-03-15
I don't know on which way you installed the Nvidia driver (I meant if you installed that through additional drivers window the problem probably is not I'm thinking of) you could try to start the system with nouveau.modeset=0 kernel option which will disable nouveau driver. For this all you have to do to press the shift button, while the grub is loading press b and type it at the end of the penultimate line after start the system with ctrl-x.

---

### Post by Quaxo76 on 2011-03-15
Hi prettl,
When I installed natty on the HD, I also installed the restricted drivers. So I currently don't have the free 3D drivers, but the official nVidia ones.
BUT - what you see on the screenshot above is *without* any 3D driver. It's what comes out when I boot the live CD, without modifications. And it's been like that for 3 releases now, since Lucid. That doesn't give a good first impression to someone who tries the liveCD just to see if they like Ubuntu...

Cristian

---

### Post by cariboo on 2011-03-15
It looks like your driver didn't install properly, as nvidia-settings didn't get installed, it's a dependency of nvidia-current.

---

### Post by Quaxo76 on 2011-03-15
Hm... What do you mean the driver didn't install properly... It's a LiveCD, it should be the same thing everyone else has!! :(

---

### Post by Harry33 on 2011-03-15
> **Quaxo76 said:**
> Hm... What do you mean the driver didn't install properly... It's a LiveCD, it should be the same thing everyone else has!! :(

Surely you do not have nvidia-current nor nvidia-settings in live-CD.
The proprietary drivers and applications cannot be delivered via live-CD.
With live-CD and with NVidia graphics card, your system boots up with nouveau driver
(xserver-xorg-video-nouveau).

The black screen in your installed system and with nvidia-current may be due to the fact, that you have not run nvidia-xconfig after first installation
or it may be due to the fact that Natty's nvidia-current does not support your graphics card.
It should provide support for GPUs such as GeForce series 6 or newer and acceleration support for GeForce 8 and later series cards for h264 video.

---

### Post by Quaxo76 on 2011-03-15
OK, let's try to fix the first things first! :)
For now, let's forget about the installed system and the 3D drivers.
I just downloaded (just to try) the latest daily. I installed it to a USB pendrive, and ran it. It booted - but the desktop had the stripes (see screenshot above).
I tried to boot the old Maverick live-CD, and it booted - BUT *with the stripes*. I don't have a Lucid CD anymore so I can't try that. Sometimes in the last few releases, something went wrong and the standard drivers don't work anymore on my system (I didn't report this for the previous releases, because with those, I was able to install the restricted drivers, and those worked OK).
I thought that before choosing the restricted drivers, the system would use the nv driver? Anyway, besides making a mess with those stripes, it also gets the resolution wrong - it upscales to full screen, but from a lower resolution.

So: for now I would be happy to have an usable desktop (even if 2D with no acceleration) out of the box, and start working from there. Booting into a venetian blinds screen (from a fully standard, plain vanilla live CD) is frustrating to say the least.

---

### Post by cariboo on 2011-03-15
Have you tried setting nomodeset from the main menu screen? When you see the little man & keyboard, press the any key, select your language, and press F6. select nomodeset from the menu, press esc, then return, and wait for the cd to boot to the desktop.

I've had strange results when booting from the Live CD using the on-board nVidia chipsets, 6150SE, so I've always had to use failsafe, or nomodeset to get to the desktop.

Most of the problems were solved by using PCI-E graphics cards.

---

### Post by Quaxo76 on 2011-03-16
What do you mean "the main menu screen"? I can't see any little man and keyboard... When I boot the liveCD, I get a sort of text-based menu with choices like "Install Ubuntu", "try Ubuntu", "Boot from HD" or something like that... I just choose the default option. And after a while I get to the desktop, without any other menus. Are you talking about that text-based menu at boot?

---

### Post by coffeecat on 2011-03-16
> **Quaxo76 said:**
> What do you mean "the main menu screen"? I can't see any little man and keyboard... When I boot the liveCD, I get a sort of text-based menu with choices like "Install Ubuntu", "try Ubuntu", "Boot from HD" or something like that... I just choose the default option. And after a while I get to the desktop, without any other menus. Are you talking about that text-based menu at boot?

The little man and the keyboard icons appear at the bottom of a purple screen before the text menu that you describe. In fact you have to tap a key when the two icons appear to get the text menu. If you don't, the live system will boot to two graphical options inviting you to 'try Ubuntu' or 'install Ubuntu'. If you are not getting the two icons and are going straight to the text menu then something is wrong with your CD. [s]Either that, or you are booting from a magazine cover disc. Some of the magazines re-engineer the ISO.[/s] **EDIT**: Sorry, silly comment that last.  You're using the Natty CD, aren't you? :oops:

---

### Post by Quaxo76 on 2011-03-17
I just checked again, and this is what happens here.
As soon as the LiveCD boots, I get a DOS-style text-only menu. It's a black screen with a blue window, at the top there's the title "Unetbootin", and below there are the options:
- Default
- Help
- Try Ubuntu
- Install Ubuntu
- Check disc for errors
- Test memory
- Boot first HD

The wording may be a little different, but this is the general meaning.
When I choose "Default" or "Try Ubuntu", it boots the system and I few seconds I'm at the (ugly) desktop, without having seen any other menu.

I don't think it's a corrupted image because I've had exactly the same behavior with 3 different Natty images, two Maverick images, and (at least) one Lucid image.

Cristian

---

### Post by VMC on 2011-03-17
> **Quaxo76 said:**
> I just checked again, and this is what happens here.
As soon as the LiveCD boots, I get a DOS-style text-only menu. It's a black screen with a blue window, at the top there's the title "Unetbootin", and below there are the options:
- Default
- Help
- Try Ubuntu
- Install Ubuntu
- Check disc for errors
- Test memory
- Boot first HD

The wording may be a little different, but this is the general meaning.
When I choose "Default" or "Try Ubuntu", it boots the system and I few seconds I'm at the (ugly) desktop, without having seen any other menu.

I don't think it's a corrupted image because I've had exactly the same behavior with 3 different Natty images, two Maverick images, and (at least) one Lucid image.

Cristian
Did you create this using unetbootin or usb-creator?

---

### Post by Quaxo76 on 2011-03-17
I used Unetbootin. I've always used it in the past and it's always worked ok. Is there a possibility that Unetbootin is what's causing these graphic problems?

---

### Post by VMC on 2011-03-17
> **Quaxo76 said:**
> I used Unetbootin. I've always used it in the past and it's always worked ok. Is there a possibility that Unetbootin is what's causing these graphic problems?
I've had problems using unetbootin in the past. Especially with hybridiso's. Just create your image using usb-creator. I now only use a usd hard drive and never use cd disks.

---

### Post by Quaxo76 on 2011-03-17
OK, I'll try what you say when I get home (I'm at work now and I don't have the iso file here).
One thing I like about Unetbootin is that it preserves my personal data on the USB pendrive. Will the usb-creator do the same? Or will it destroy the data in the pendrive?

Cristian

---

### Post by coffeecat on 2011-03-17
Bit of a contradiction here:

> **Quaxo76 said:**
> As soon as the LiveCD boots

> **Quaxo76 said:**
> I used Unetbootin.

Which are you using, a live CD or a live USB created with unetbootin?

Whatever, Unetbootin certainly bypasses the two little icons stage and what  you describe sounds more like the unetbootin menu rather than the Ubuntu  text menu. I don't know whether unetbootin could be responsible for  your graphics problems, but I agree with VMC. If you want a live USB, try using Ubuntu's startup  disk creator.

---

### Post by Quaxo76 on 2011-03-17
@ Coffeecat (et al.): sorry for the contradiction! Maybe bad wording on my part.
I never use "actual" CDs, too clunky to use IMO. I always use an USB pendrive. I used the word "LiveCD" because that's what it originally is - an iso of a LiveCD. I thought that wouldn't matter.
Anyway, I'll report as soon as I can try that, later today.

Cristian

---

### Post by coffeecat on 2011-03-17
@Quaxo76, may I just warn you about a rather irritating bug in the Lucid and Maverick versions of startup disk creator? If you use Maverick's disk creator with a Lucid ISO you get an unbootable USB drive. It errors out immediately you try to boot it. I'm fairly sure that's also true if you use the Lucid disk creator to create a Maverick USB. With Maverick and Lucid you need like for like. Whether that's true for Natty, I don't know. If it's true that you need Natty's startup disk creator to create a Natty USB and you don't have a Natty installation, that going to be a bit of a catch22! :-k :|

---

### Post by VMC on 2011-03-17
> **Quaxo76 said:**
> OK, I'll try what you say when I get home (I'm at work now and I don't have the iso file here).
One thing I like about Unetbootin is that it preserves my personal data on the USB pendrive. Will the usb-creator do the same? Or will it destroy the data in the pendrive?

Cristian

Not sure where your personal data is, but with my usb drive I have two partitions. One I use for other things and the other one is a 2gig partition that I only use for usb-creator. Just make sure you don't erase the disk just delete the files/folders on the boot partition.

---

### Post by Quaxo76 on 2011-03-17
> **VMC said:**
> Not sure where your personal data is, but with my usb drive I have two partitions. One I use for other things and the other one is a 2gig partition that I only use for usb-creator. Just make sure you don't erase the disk just delete the files/folders on the boot partition.

I have a folder called /Data where I keep all my personal data. Unetbootin leaves it alone, it just creates some more folders which I just ignore. I may as well resize the pendrive and create a new partition, but I hate when I have too many auto-mounted partitions... And having *two* partitions mounted everytime I plug my USB pendrive isn't optimal for me. Well, I guess one can't have everything! :)

Cristian

---

### Post by Quaxo76 on 2011-03-17
Update: I tried using usb-creator to make a bootable usb pendrive. It didn't work: the newly created pendrive hung immediately after boot with a message saying "Syslinux" and something else that I forgot.
The Maverick version of usb-creator doesn't like natty iso's (btw, I think this is something that has to be fixed... if I need a natty pendrive, usually I don't already HAVE a natty system).
Anyway: I was able to launch a natty system from the hd, using the recovery console, I forgot exactly how I did but I managed to get a very lo-res desktop running (with black background and no Unity) and ran usb-creator from there. And it worked. Now I have a working natty pendrive, with the latest daily iso. And I got the graphical icons (keyboard and little man). But using the default options gave me the same graphic corruption.
Enabling the nomodeset option gives me a working desktop, but again in lo-res and without Unity. Right now I'm using that to install the system to HD, hoping that I can then install the restricted drivers and have a working system.

Is there no hope to fix the iso's so that even my graphic card (which isn't all that old, and has a decent power for a laptop) works out-of-the-box even for who doesn't even know what "nomodeset" is? What component is to blame here?
Or failing that, maybe blacklisting that video card so that it loads, by default, the failsafe driver? Anything that gives a workable desktop out of the box would be preferable, IMO...

Thanks,
Cristian

---

### Post by VMC on 2011-03-17
Its been a while since I used mavericks iso-creator, but as I recall you need to alter the file "/isolinux/isolinux.cfg" and replace the line "ui gfxboot bootlogo" with "gfxboot bootlogo".

Also there was a time when you got the boot: prompt all was need was to type help return.

---

### Post by Quaxo76 on 2011-03-17
The latest daily iso doesn't complete the install. I tried twice, and twice it stopped about at the end of the installation process (I think just before the GRUB installation) with the message "Installer crashed". I'll try again with Alpha 3 - I suppose if I let it download updates during installation, the system will be current anyway.

---

### Post by Quaxo76 on 2011-03-17
Hm. Problem. The failed install attempts destroyed the grub on the HD. So now I can't boot my laptop at all.
I tried to put the Alpha 3 on the USB stick using the Maverick usb-creator, and modifying the file like VMC sayd (by the way it wasn't /isolinux/isolinux.cfg but /syslinux/syslinux.cfg) but it still doesn't work. Which now put me in a difficult position: I can't boot the old system anymore because grub is destroyed, and I can't boot the Natty alpha 3 from the USB stick because I can only use the Maverick usb-creator to make it, and it doesn't work.
Any ideas? :)

Cristian

---

### Post by VMC on 2011-03-17
> **Quaxo76 said:**
> Hm. Problem. The failed install attempts destroyed the grub on the HD. So now I can't boot my laptop at all.
I tried to put the Alpha 3 on the USB stick using the Maverick usb-creator, and modifying the file like VMC sayd (by the way it wasn't /isolinux/isolinux.cfg but /syslinux/syslinux.cfg) but it still doesn't work. Which now put me in a difficult position: I can't boot the old system anymore because grub is destroyed, and I can't boot the Natty alpha 3 from the USB stick because I can only use the Maverick usb-creator to make it, and it doesn't work.
Any ideas? :)

Cristian

Booting from old livecd, do the following[Replace sdaX with your Maverick partition number]:
s```
udo mount /dev/sdaX /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount -o bind /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt/ /bin/bash
```

Then re-install grub:

```
sudo grub-install /dev/sda
```

---

### Post by Quaxo76 on 2011-03-19
Status update:
I was able to reinstall the system. I used a recent (March 17) daily build. After installing it, when booted it showed the striped (corrupted) desktop. I made a complete update today, and after I activated the restricted nVidia driver (the recommended one). Now Natty doesn't boot anymore. It just shows a black screen, and I can't do anything - not even Ctrl+Alt+F1-7 work. I can only reboot using Ctrl+Alt+Del.
So, if I don't enable the restricted driver, I get an unusable, corrupt screen - and with no Unity; if I enable it, the system just stops working. How can I test this system if I can't boot it? :(

Cristian

---

### Post by cariboo on 2011-03-19
Your system is actually booting, it's just that X isn't starting. I'd suggest you start in recovery mode, and once at the Menu, select failsafeX, then when the desktop loads, check /var/log/Xorg.0.log.

---

### Post by Quaxo76 on 2011-03-19
OK, with "failsafe X" the system boots fine, and I'm presented a desktop. There is no "venetian blind" corruption, but there is no menu bar or anything. Just the background and an icon for the DVD. Even Alt+F2 doesn't work. But if I press Ctrl+Alt+F2 I get another desktop, with a different theme and a black background, and there I can see NO DVD icon but there's a menu bar. Very weird...
Anyway, the log file you told me, shows some errors, but I don't know how to proceed. I'm attaching it here so you can have a look at it (renamed to .txt to make the forum happy).

What's frustrating is that both video drivers are buggy with my card: the standard driver and the restricted driver...
How can I be sure that the standard driver developers are aware of this problem? What package exactly is the "culprit"?

Cristian

---

### Post by cariboo on 2011-03-19
From your attached file, it looks like your video chipset is running out of ram, how much ram do you have allocated in the bios? I always found when I used integrated graphics chipsets that 64Mb ram seemed to work the best for me.

---

### Post by Quaxo76 on 2011-03-20
I had 128MB allocated in the BIOS. I need as much Video Ram as possible because I run a very complex flight simulator on this laptop.
Anyway, I changed it to 64 MB and, wonder, now the restricted driver works.
(On a side note, for now I really can't say that I like Unity - I can't find anything. How do I even tell what applications are installed on the computer? I want my "System" and "Applications" menus back!!)

But now, read this: I changed it back to 128MB to use my Maverick system, and tried (just out of curiosity) booting Natty again... AND it still works!
So: 128MB -> didn't work;
changed to 64MB -> it worked;
changed back to 128MB -> Still works.

I give up trying to understand this whole video drivers thing... 

Thanks,
Cristian

---

### Post by cariboo on 2011-03-20
You still have an Applications menu and the system menu is avaliable when you click the Applications menu button. See screenshot

---

### Post by Quaxo76 on 2011-03-20
Hm, yes but the Applications menu only shows a few applications, not all; and the three "installed/most used/available for download" panels are distracting for me. And I like to see my apps organized in categories (and the menu button you pointed out doesn't fork for me - if I click on any line, it launches the application underneath, as if the menu wasn't there).

I'll try to learn it, but for how I use the computer (I don't only use 2-3 applications, but I use many application not so often; so putting them in the sidebar doesn't make sense, and they wouldn't end up in the "most used" menu) I think for me it will be slower and take more clicks... Anyway, we'll see. I intend to give it a fair try!

Cristian

---

