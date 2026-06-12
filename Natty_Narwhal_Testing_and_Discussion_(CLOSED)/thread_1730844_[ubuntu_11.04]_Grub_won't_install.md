---
title: "[ubuntu 11.04] Grub won't install"
date: 2011-04-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by evilnone on 2011-04-16
Ok let me start off by saying that I am dual booting windows 7 and ubuntu.  I use 7 for work and ubuntu for everything else.

I installed windows 7 first and have it set up fine.  I then installed 11.04b2 because I wanted to test it out. The problem I am having is that I no matter how I install it, I can not get a grub menu to show.  I have tried the automated install of putting 7 and ubuntu side by side.  nothin.  I tried doing it manually and still no boot loader.  I have tried installing the boot loader on both drives and still nothing.  

Linux shows windows 7 on sdb and ubuntu on sda. I have tried the recovering grub from the help thread here:[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

after running this command
sudo grub-install --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sda

I get this:
Installation finished. No error reported.

But not the other lines that are after it (in the help article it says it should have some more lines).  

Anyone have any thoughts on what I need to do?

---

### Post by drs305 on 2011-04-16
> Installation finished. No error reported.]
That's all you normally see with the 'grub-install' command.

You probably aren't seeing the menu because Grub2 has not yet detected Windows. By default, if G2 doesn't detect another OS it boots directly into Ubuntu.

During boot, you should be able to display the menu by holding down the SHIFT key. However, what you really need to do is to run the following command after Ubuntu boots:
```
sudo update-grub
```
This should run the proper scripts to locate Windows and include it in your Grub2 menu. Once that is done, the menu should display on boot and allow you to select the desired OS.

---

### Post by evilnone on 2011-04-16
the problem is that it doesnt load grub at all... it goes into windows every time.  the only way I have a command line is from the live USB i am using.  

Any other suggestions?


EDIT: solved by putting it on the other hdd... should be on sdd instead of sda for my setup.  Thanks or the help

---

### Post by drs305 on 2011-04-16
> **evilnone said:**
> the problem is that it doesnt load grub at all... it goes into windows every time.  the only way I have a command line is from the live USB i am using.  

Any other suggestions?

Have you tried changing the boot order in BIOS? It's possible your system is booting the Windows drive - on which the MBR points to the Windows bootloader. Make sure BIOS is instructing the system to boot your Ubuntu drive first.

If that is not the issue, please boot the LiveCD, go to the following site to download and run the boot info script. Post the contents of RESULTS.txt, which will give us a pretty good idea of what is happening.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

