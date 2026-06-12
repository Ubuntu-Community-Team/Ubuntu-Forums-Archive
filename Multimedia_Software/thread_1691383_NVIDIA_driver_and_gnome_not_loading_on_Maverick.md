---
title: "NVIDIA driver and gnome not loading on Maverick"
date: 2011-02-19
forum: Multimedia Software
---

### Post by Valir on 2011-02-19
Hi, 

I had some serious problems getting the NVIDIA driver to work for a GeForce 7300 card. The problem was that the Desktop failed to load. After cleaning out old kernels, re-installing the Nvidia drivers, and Gnome Desktop dependies in Synaptic, I succeded getting everything to work. 

But only for me. Other users on the computer have the same problem, or the desktop loads but everything is unresponsive except the mouse pointer. 

This leads me to guess that the solution must be quite ease, some config file in the home folder which can simply be copied to other users. 

But which? 

Does anyone understand the dynamics of this problem?

Cheers,

---

### Post by bgarrett@fatcatsfun.com on 2011-02-19
I too spent a day and a half getting this problem taken care of I finally found a solution to my problem.

You will need to get rid of all nvidia drivers, I did so in the packet manager and unchecked all drivers associated with nvidia that have a number by them like nvidia-96 and nvidia-173...and so on.

Next open terminal and code
sudo nano /etc/modprob.d/blacklist.conf

Enter the following on the last part of the file:
blacklist vga16fb
blacklist nouveau
blacklist nvidia-173
blacklist nvidia-96

Save file, you will need to edit your menu.lst:

Code
sudo nano /boot/grub/menu.lst

Add at the end of all Kernel lines "vmalloc=256M" with out quotations. This gives extra virtual memory while loading necessary drivers. 

Install nvidia drivers as you would normally. Hope this helps.

---

### Post by BicyclerBoy on 2011-02-20
@fatcats.
Your problem is completely different. You blacklisted the nouveau kernel module & other framebuffer kernel modules that stop the nvidia driver loading.

I think the memory issue only arises with 32bit & 2 video cards.
I don't think you are meant to edit that grub file directly any more (not with grub2)
There are other files to edit & then run update-grub.

@Valir
I think you are on the right track but don't know what the fix is..could be a gnome display resolution setting.

Could make one new user & see if this works.
Could then copy over some of the old user files to the new user .

---

### Post by Valir on 2011-02-20
Yes, this is quite mysterious. First of all the blacklist did nothing, even while reinstalling drivers (which it theoretically shouldn't do either). 

When I created a new user the same problem persisted. So there must be a template somewhere which generates a faulty configuration file for the desktop. I tried to copy all of the .folders related to graphics from the working user space, plus a nvidia settings file, to the new user. But no luck. Which is strange. There must be a newly generated configuration file which is user-specific but not situated in the home folder. 

best, 

:confused:

---

### Post by drdos2006 on 2011-02-20
I had the same problem. Eventually unloaded the latest Nvidia and went back to 173.
This worked for me. Display is G73 [GeForce 7600 GT]

regards

---

### Post by Valir on 2011-02-20
](*,) Silly me. I forgot to check that the permissions were ascribed to the user to whom I copied the home folder files which made the Nvidia-Current driver work. 

Good thing, because then it is easier trying to pinpoint who is the troublemaker. At least it is a problem with Compiz (which is loaded as the default window manager now, I guess). The working model uses Metacity. 

So either it is a conflict between driver/compiz, or a config file related to compiz which points in the wrong direction. Not sure which. 

In the meantime those who want to use the Nvida-current and experience this problem, can install the driver from the console(press Ctrl+alt 1); cd to the folder where your Nvidia.run file is; &sudo ./Nvidia-?.run; follow the instructions; then enter $sudo service gdm restart; login; right-click screen and choose Change Desktop Background; choose Visual Effects tab; select None; reboot.

Cheers

---

### Post by bgarrett@fatcatsfun.com on 2011-02-22
> **BicyclerBoy said:**
> @fatcats.
Your problem is completely different. You blacklisted the nouveau kernel module & other framebuffer kernel modules that stop the nvidia driver loading.

I think the memory issue only arises with 32bit & 2 video cards.
I don't think you are meant to edit that grub file directly any more (not with grub2)
There are other files to edit & then run update-grub.

@Valir
I think you are on the right track but don't know what the fix is..could be a gnome display resolution setting.

Could make one new user & see if this works.
Could then copy over some of the old user files to the new user .

yes you are right about the 32bit. I should have asked what version they were running. If any one is running a 32bit version they can edit the grub2 and add the vmalloc function at the end of the BOOT line to ensure that the drivers have enough virtual memory to load, or else it will crash. I did this and it worked for me on a 32bit mythbuntu disro.

---

