---
title: "I am booting in EFI mode without efibootmgr and with no /etc/default/grub file?"
date: 2015-08-22
forum: Mac OSX
---

### Post by imattux on 2015-08-22
How is that possible? Here's the link to my Boot Repair report: 

[http://paste.ubuntu.com/12152662/](http://paste.ubuntu.com/12152662/)

**PRIMARY OBJECTIVE: (ACHIEVED)** Learn about Linux by installing and running a relatively recent distro on my aging but solid 2007 MacPro 1,1 
Relevant System Info: 
**32b EFI** with **64b Intel Xeon** Quad Core processor; 
Somewhat wonky **Radeon XT1900** 512MB card (details below);
**Four drive bays** (I think that is a key factor); 
**MacOS 10.7.5** was my primary OS. It is installed on a **separate physical 1TB drive**; 
**Ubuntu** **14.04 LTS** is installed on its own **separate, physical 160GB drive** (with a hacked/manually created ESP); 
Other 2 drive bays are physically empty for now, but one is the Time Machine BU drive for the Lion drive and I'd like the last one to be shared and accessible to both Linux and Lion.

*It was a nightmare.* For the sake of anyone else who's had all the trouble I had, I'll post all the details below or in another thread, but for now I'll start with where I am currently and what I want to do. If you want any or all of the gory details, ask.

**CURRENT OBJECTIVE: **Clean everything up from more failed attempts and re installs than I can count and have a better understanding of exactly what is happening when I boot into Ubuntu. Right now, it's "magically' working but nothing seems to be where it's supposed to be to make that happen. To wit:
[B]
CURRENT CONFIGURATION AND ISSUES:[/B]
If I don't do anything from a cold boot or reboot, the box boots into OSX Lion, as desired. 
If I hold the option key, I get the Apple boot manager screen with:

[LIST]
[*=1]the OSX Lion drive,
[*=1]a phantom Windows drive from a Boot Camp installation/logical partition that has been deleted and zero'd (?),
[*=1]the Lion recovery partition on the 1 TB Lion drive,
[*=1]and the 160GB Ubuntu 14.04 LTS Drive.
[/LIST]

I'd love to get rid of the phantom Windows drive, but more importantly, now that I know I have to pass the "nomodeset" argument before loading the kernel 

**(NEW OBJECTIVE) I need to add "nomodeset" and make the 3.16.0.46 kernel the default (from 4 other choices) so that all I have to do is choose the Ubuntu disk to boot from and I'll get to my Ubuntu password prompt with no further intervention.**

I've read all the documentation on Grub2 (remember, Grub2 is ia32, Ubuntu is x64). **I went to edit the /etc/default/grub file and there was none.** [B]I looked for my efibootmgr and there was none.

[/B]Terminal Output:
imattux@UB-MacPro-DT:~$ sudo efibootmgr
[sudo] password for imattux: 
imattux@UB-MacPro-DT:~$ sudo efibootmgr -v
imattux@UB-MacPro-DT:~$ [ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"
Installed in UEFI mode
imattux@UB-MacPro-DT:~$ 

I read some more documentation and decided that I should not edit /EFI/BOOT/grub.cfg manually because it would be overwritten every time I ran sudo apt-get update*. I copied and pasted a generic version of /etc/default/grub and added the "nomodeset" argument and ran sudo apt-get update-grub. Next reboot, the Grub screen changed from blue bg to black bg and the "nomodeset" argument had been added to all the entries. So (I'm 99% certain) I was using different, new grub.cfg generated from sudo update-grub.

Okay, it's working. Kind of. But I want to KNOW why and how. The whole point of this exercise is to learn how things work so I can eventually write code. I don't want to be the guy that follows some instructions blindly, trusts that they'll work, crosses his fingers and pastes "sudo *whatever*" and then has not idea how to fix what just broke.

The linked boot repair report say's I'm using Grub legacy... Huh? There are multiple boot files on sda1 including refind*, grub i32 and x64, shimx64, etc. That's the OSX Lion drive. Nothing else needs to be there but the apple boot files. I can fix that on the OSX side, but I'm pretty sure that will break Grub/Ubuntu

There are several warnings at the bottom of the report and it talks about BIOS in the recommended repairs section. There is not need for BIOS. I know that that thanks to Rod Smith and several others.

Rather than blindly letting Boot Repair do it's thing, I think I can:

Physically remove the OSX Lion (1TB) drive,
Reboot and see what happens - if necessary, I can boot from the grub command line,
Blow away the entire EFI partition - zero it out
Run [COLOR=#586E75][FONT=Menlo]$ sudo grub-install --target i386-efi --boot-directory=/boot --efi-directory=/boot/efi --bootloader-id="$(lsb_release -ds)"
[/FONT][/COLOR]Run sudo apt-get update-grub
Edit /etc/default/grub
Reboot and achieve desired result. 

Am I at least on the right track?
Please do not point me to the UEFI booting pages on the forums. I've read them and bookmarked them and read them again. Rod Smith is a saint and he has educated me enormously. I'm read all that to get myself where I am. It's working but as I said, all the things that are supposed to be there to make it work are not there.

TIA

---

### Post by oldfred on 2015-08-22
Moving you to the Apple Mac sub-forum.
I do not know Mac, nor 32 bit UEFI, nor rEFInd. Although rEFInd is on my short list of things to try.
I only have a UEFI PC, but have booted from sdb drives.

I would think a Mac would also boot similarly as it seems to be UEFI standard, but Mac has mixed UEFI old versions & new versions of UEFI.

With a PC, an external drive (like installer) only boots from the ESP - efi system partition and /EFI/Boot/bootx64.efi. And if you copy an installed grub, it seems to be hard codes to find the grub.cfg in /EFI/ubuntu. That grub.cfg is just a small configfile entry to find full grub.cfg in your actual install.
But you are not showing an ESP on your sdb drive?
I have had to copy /EFI/ubuntu folder to sdb & create /EFI/Boot folder. And copy grub or shim into that folder and rename to bootx64.efi. 
If using rEFInd it may be that file(s) that you need to copy.

You normally add a boot parameter in /etc/default/grub
 sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
      
 gksudo gedit /etc/default/grub
After any change to grub's configuration:
sudo update-grub

The sudo update-grub will not change the tiny grub.cfg in the ESP.

[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel. 
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only. 
[/LIST]
        o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

---

