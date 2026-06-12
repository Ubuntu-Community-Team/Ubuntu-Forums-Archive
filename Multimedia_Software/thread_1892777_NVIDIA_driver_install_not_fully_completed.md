---
title: "NVIDIA driver install not fully completed"
date: 2011-12-08
forum: Multimedia Software
---

### Post by Albury_Boy on 2011-12-08
Ok... I know, this was dumb. I upgraded from 11.04 to 11.10 and had to reinstall the nvidia-current drivers from the repository. Unfortunately I didn't finalise the install before a reboot. I now don't have any display set, and I'm getting a black screen on boot. In the shell xhost reports 'display not set'. Can't even get gedit to run, and I can't use the ed text editor.

Under 11.04 you could use a xconsole to get a fall-back video driver from the recovery menu, but this doesn't seem to be available with 11.10. I'm running ubuntu from a USB stick to post this.

Is there a way to boot with the reduced gfx with 11.10, or am I going to have to edit the grub or something similar??? I can usually fix most of my screw ups, but this one has me pulling my hair out!!

Any advice or suggestions are appreciated.

Cheers

---

### Post by siddharth_univ on 2011-12-08
the way i installed nvidia proprietary drivers was was to do a ctrl+alt+f1, then do sudo service lightdm stop, run the nvidia drivers setup, then do a sudo service lightdm start, and then reboot

---

### Post by Albury_Boy on 2011-12-08
Thanks for the reply.

As I said, I've screwed the install. I can only use the command prompt with networking, or run from a livecd or usb.

'sudo service lightdm stop' returns 'stop: Unknown instance:'

I'd really like to know a way to run a xconsole with reduced gfx.

---

### Post by Albury_Boy on 2011-12-08
I've run 'sudo apt-get remove --purge nvidia-current' and 'sudo apt-get install nvidia-current' 

It seems to install ok, but still nothing happening for me....

---

### Post by BicyclerBoy on 2011-12-08
I have not upgraded to 11.10 but made a new temp install, no drama with nVidia driver but the video card is supported by old drivers..

Do you mean you can login at console screen only or are you using a terminal in a X server window ?

I assume you are at a console login..because service lightdm stop reports no X server running..

What happens if you:
sudo service lightdm restart

then copy/look/post the /var/log/Xorg.0.log file for clues &/or run dmesg.

---

### Post by Albury_Boy on 2011-12-08
Thanks for the response BicyclerBoy

I used to consider myself a poweruser, but I feel like a total n00b with Linux. I've used many other platforms before (C64 -> Amiga -> Win has been my progression), but I've only been using Ubuntu for about 6mths, so you might have to bear with me a little.

Normal boot results in a black screen, purple screen, a weird combination of both, or sometimes hangs at the splash screen. Depending on what I've tried last.

I've only just upgraded to 11.10 from 11.04 and it's a bit different to what I'm used to. There is no 'run with reduced gfx support' option in the recovery console anymore...

I've been going to the recovery console, mounting the drives, then dropping to the command line with networking. 

As far as I can see, lightdm doesn't seem to be running.

Do you how to revert back to the nouveau drivers from the command line?? 
Or get a reduced gfx session running??

I'm pretty sure that if I can get a gui running then I can fix it.

---

### Post by siddharth_univ on 2011-12-08
Hi, im just starting to use ubuntu , but to what i have read, lightdm is the default desktop manager for 11.10, and gdm was for 11.04(not sure)? if not lightdm service, could you try gdm? Since you said that the install was incomplete, i was wondering if it could be the case that lightdm wasnt set as default if it wasnt already default for 11.04..

---

### Post by Albury_Boy on 2011-12-08
'sudo service lightdm restart' = 'restart: Unknown instance'

'sudo service gdm restart' = 'restart: Unknown instance'

I've got two laptops going side-by-side, but I can't copy'n'paste results

---

### Post by BicyclerBoy on 2011-12-08
My first bought computer was an Amiga 2000..a 'friend' formatted the HDD on day 2..good learning experience.

Could try
sudo apt-get install xserver-xorg-core

sudo dpkg-reconfigure xserver-xorg
Xorg -configure
sudo nvidia-xconfig

look in the log file /var/log/Xorg.0.log...

If you edit /etc/X11/xorg.conf & change driver "nvidia" to "nv" you should be able to restart X server with nouveau driver..check for blacklisting..

Last resort:
The nVidia driver will have blacklisted nouveau kernel module in a file in
/etc/modprobe.d/*.conf  blacklist.conf or nvidia-blaklist.conf

AFAIK Will need to
sudo update-initramfs -u 
if you edit any modprobe.d/*.conf files.

The nVidia driver has a kernel space component that will still be 'dkms'ed into the boot image.
With the nouveau blacklisted & nVidia purged (& update-initramfs -u) & a reboot you should get VESA driver.

---

### Post by Albury_Boy on 2011-12-09
Appreciate all the advice BicyclerBoy. I'm still not getting anywhere. I may end up re-installing Natty. The new distro is really stripped back, and it kind of feels like Mac OSX. It's missing some of the 'poweruser' GUI functions that I've got used to. I see that you're still using the Lucid distro. So I probably won't be missing out on too much. I was just seduced by some of the 'pretty' gui features in 11.10. 

My laptop is dual booted with Win7, and I'm so over it. It's good for games, and that's about it. I've been using a liveUSB stick to try to rescue my ubuntu boot, but I want my software back again. I can always back up my files and start again...

Cheers.

---

### Post by josephmills on 2011-12-09
Hello there you could boot a live cd of ubuntu then mount your harddrive that nvidia is messed up. 

boot live 
enter TRY 
open terminal 
```
sudo fdisk -l 
```
^^ locate drive for ubuntu ^^
mount it 
```
sudo mount /dev/sdXXXXX  /mnt/
```
cd to the mount point 
```
cd /mnt/
```
chroot the mounted harddrive 
```
sudo chroot /mnt/
```
remove all nvidia stuff 
```
sudo apt-get --purge remove nvidia-current 
```
drop out of chroot with "exit command"
reboot computer hope that this helps 
Joseph

---

### Post by inkrypted on 2011-12-09
I had something similar happen to me once and I thought all was lost so I used a live CD and went in and deleted my xorg.conf file from /etc/X11 and to my surprise i was able to log in again. I don't know if you situation is exactly like mine but it might be something to try before you reinstall.

---

### Post by Albury_Boy on 2011-12-09
Thanks to everyone for the support. It's great to know that there's a community like this. I really appreciate all the suggestions.

I have a suspicion that I didn't generate a new xorg.conf after installing the nvidia-current drivers. 

In any case, I've reinstalled natty 11.04. I feel much more comfortable with it. I think I'll give the 11.10 distro a miss. It burnt me :-(

---

