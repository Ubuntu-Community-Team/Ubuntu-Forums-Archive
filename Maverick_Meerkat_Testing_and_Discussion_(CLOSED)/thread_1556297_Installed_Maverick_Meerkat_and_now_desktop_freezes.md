---
title: "Installed Maverick Meerkat and now desktop freezes at boot"
date: 2010-08-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by MadMikeyB on 2010-08-19
Hi all, I'm posting here in the vain hopes that someone could help me out :)

Right, I probably shouldn't have done it, but I did the distribution upgrade from Ubuntu 10.04 from the desktop edition to 10.10 - everything in the upgrade went swimmingly, except the reboot part. It seems to hang on the 'splash screen' - by this I mean the Ubuntu screen which comes up, with 4 little dots under it which go from white to red as a loading indicator, it fills all the dots up, and then continues to do nothing. It's not the computer being slow as I left it for a considerable amount of time before CTRL+ALT+DEL which worked fine to reboot.

I do have an NVidia GPU, but as I can't get into the system [SIZE="1"]*(I'm relatively new to ubuntu, not sure if there is an equivalent of windows "safe mode")*[/SIZE] I don't think there is anything I can do.

I can't remember exact specs offhand, but I think it's a Pentium 4 3GHz, 2GB RAM, NVidia 9x Series (was having trouble with this anyway, stupid graphics).. and that's it, I think.

Hopefully I've given enough info, and I hope that someone can come through with a solution.

Thanks!

---

### Post by nbkr on 2010-08-19
> **MadMikeyB said:**
> 
Right, I probably shouldn't have done it


No offense meant, but yes, you shouldn't have done this. Ubuntu 10.10 is not yet for productive usage - it is out for testing. Everything on such releases is probably unstable and can ruin your files. 

However, if you press "ESC" while the bootloader shows the dots, you should be able to see what the machine is doing and what step freezes the system.

---

### Post by MadMikeyB on 2010-08-19
No offense taken, don't worry. I only reinstalled ubuntu 10.04 a few days ago as stuff wasnt working properly, so I figured "What's to lose" - I'd rather fix this than do a reinstall of ubuntu 10.04 again, but if that's what it takes, that's what it takes.

I've already tried ESC on the bootloader, and it didn't do anything I'm afraid.

---

### Post by nbkr on 2010-08-19
If you have Grub installed you can get into the grub menu by pressing shift after powering on the computer. There should be a item in the menu labled "rescue mode". That will - hopefully - get you into the single user mode. There you can have look at the boot logs and try to figure out what the problem is.

---

### Post by MadMikeyB on 2010-08-19
I got GRUB once saying "loading GRUB" then it continued its merry way through the boot procedure. Can't get it to try to load GRUB again, even holding shift through the boot process.

Is that the only way to get into a user state where I can see where things go wrong?

---

### Post by MadMikeyB on 2010-08-19
Alright, I'm in a user shell now, not sure what I should be doing next.

Edit, tried sudo apt-get update and it doesnt have internet access by the looks of it.

---

### Post by nbkr on 2010-08-19
> **MadMikeyB said:**
> 
Edit, tried sudo apt-get update and it doesnt have internet access by the looks of it.

Yeah - no network, no gui - no nothing :-)

Try to open the file /var/log/messages and see what the system said while trying to boot.

---

### Post by mc4man on 2010-08-19
you could fix this several ways - if you read the sticky at top of this forum you'll see the issue with nvidia drivers.
Not knowing which drivers you had previously or what the upgrade does in that regard the simplest may be to return to nouveau and then square up from there.

From the recovery mode - user prompt

```
sudo update-alternatives --config gl_conf
```
 select the alternative provided by mesa, then these 3 commands and reboot
```
sudo ldconfig
sudo update-initramfs -u
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old
```

I believe that once at the desktop if you use 'Hardware Drivers' (jockey) to install nvidia-current then you'll get a working xorg.conf, otherwise the sticky will show you how to edit to work

(you could also try the low graphics from recovery menu - i'd just return to nouveau as above

---

### Post by glasen on 2010-08-19
The freeze is caused by a kernel bug introduced in version 2.6.35.2 to fix a security issue. The latest Maverick kernel is based on this version.
There is already a patch for this bug, but you have to wait for kernel version 2.6.35.3 to get it officially.

There a two solutions for this bug

[LIST=1]
[*]Downgrade to an older kernel package and wait for a fixed package (e.g package version [2.6.35-15.22]("https://launchpad.net/ubuntu/+source/linux/2.6.35-15.21") which is based on kernel version 2.6.35.1)
[*]Compile your own kernel with the patch mentioned above (See attachment of this post)
[/LIST]

---

### Post by marcio.mutti on 2010-08-19
I had that problem yesterday. For a simple solution, I booted in safe-mode, removed the Nvidia proprietary drivers (I guess the system resumed to Nouveau). Today, I updated the system again and reinstalled the Nvidia drivers. So far, the gdm-not-showing issue didn't come back.

---

### Post by MadMikeyB on 2010-08-20
> **nbkr said:**
> Yeah - no network, no gui - no nothing :-)

Try to open the file /var/log/messages and see what the system said while trying to boot.

It didnt exist, no file.

> **mc4man said:**
> you could fix this several ways - if you read the sticky at top of this forum you'll see the issue with nvidia drivers.
Not knowing which drivers you had previously or what the upgrade does in that regard the simplest may be to return to nouveau and then square up from there.

From the recovery mode - user prompt

```
sudo update-alternatives --config gl_conf
```
 select the alternative provided by mesa, then these 3 commands and reboot
```
sudo ldconfig
sudo update-initramfs -u
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old
```

I believe that once at the desktop if you use 'Hardware Drivers' (jockey) to install nvidia-current then you'll get a working xorg.conf, otherwise the sticky will show you how to edit to work

(you could also try the low graphics from recovery menu - i'd just return to nouveau as above

I did all you said in your post, the comp is currently working on low graphics mode, gonna keep it up for as long as I need to back things up :p

> **glasen said:**
> The freeze is caused by a kernel bug introduced in version 2.6.35.2 to fix a security issue. The latest Maverick kernel is based on this version.
There is already a patch for this bug, but you have to wait for kernel version 2.6.35.3 to get it officially.

There a two solutions for this bug

[LIST=1]
[*]Downgrade to an older kernel package and wait for a fixed package (e.g package version [2.6.35-15.22]("https://launchpad.net/ubuntu/+source/linux/2.6.35-15.21") which is based on kernel version 2.6.35.1)
[*]Compile your own kernel with the patch mentioned above (See attachment of this post)
[/LIST]

How long do you think before a kernel update will released? Could I, in theory, keep the computer online until the update is rolled out and then sudo aptitude update ?

---

### Post by cariboo on 2010-08-20
The kernel was upgraded to 2.6.35-17 today, but your problem is more than likely the same as the xserver sticky at the top of the page. I did a fresh install today, with nvidia-current from the repositories, I still had to add the ignoreABI section to /etc/X11/xorg.conf. This was on a system with a 9400GT graphics card.

To create an /etc/X11/xorg.conf file, open a terminal and type:

```
sudo nvidia-xconfig
```

you can then edit the file using nano:

```
sudo nano /etc/X11/xorg.conf
```

and add the section quoted in the Xserver sticky.

---

### Post by MadMikeyB on 2010-08-21
To clarify, you mean the fix in [this post](http://ubuntuforums.org/showpost.php?p=9702585&postcount=25)? Just applied that. Done sudo aptitude upgrade sudo aptitude update and it updated everything. Now to reboot (waiting for confirmation that that is the right fix..)

---

### Post by linux18 on 2010-08-21
this could be a plymouth bug, at the prompt type " xinit " if you get a terminal and mouse support after a few seconds then it's plymouth, if you get a blank screen then it's your video driver/xorg/kernel/so many things

---

### Post by shantiq on 2010-09-04
> **glasen said:**
> The freeze is caused by a kernel bug introduced in version 2.6.35.2 to fix a security issue. The latest Maverick kernel is based on this version.
There is already a patch for this bug, but you have to wait for kernel version 2.6.35.3 to get it officially.

There a two solutions for this bug

[LIST=1]
[*]Downgrade to an older kernel package and wait for a fixed package (e.g package version [2.6.35-15.22]("https://launchpad.net/ubuntu/+source/linux/2.6.35-15.21") which is based on kernel version 2.6.35.1)
[*]Compile your own kernel with the patch mentioned above (See attachment of this post)
[/LIST]



yes and this really works   on maverick i got all of those freezes i used to get with 2.6.32 on lucid before i chose 2.6.34

the default kernel on maverick is 2.6.35 and THE CURRENT version gives me the freezes again so i moved down to 2.6.34 again and hey presto no freezes


as you say will have to wait for a 2.6.35 which does not do that


but maverick seems happy with 2.6.34 for the time being


[here ]("http://ubuntuforums.org/showthread.php?p=9805341#post9805341")i wrote a few tips about moving up and down the kernels

---

### Post by Orpheon on 2010-09-04
The problem is that I cannot acces the grub menu to go in single-user mode. The computer first does does the part where you can change the bios, then immediatly jumps to the white "ubuntu" with five red dots, and then stays like that for atleast 2 hours( I pulled the cable and booted with the live cd at that point.). I tried repeatingly pressing shift during boot but nothing happened. The commands to get rid of the nvidia drivers don't work on a live cd and the sticky you all refer to is missing. I know nvidia is the problem, but how do get rid of it through a live cd? Thanks in advance.

---

### Post by cariboo on 2010-09-04
Did you try the esc key? Doesn't the reset button work on your system? I always find pulling the power cord dangerous.

---

### Post by Orpheon on 2010-09-04
> **cariboo907 said:**
> Did you try the esc key? Doesn't the reset button work on your system? I always find pulling the power cord dangerous.

Thank you, esc worked! Though I still haven't seen the grub menu, it complained about an error -16 and gave me xterm, which I used as was described in thread. Mabye that's useful......... probably not. My problem is solved.
ps: No, the reset button does not work.

---

### Post by cariboo on 2010-09-04
It's probably plugged into the wrong place on the motherboard, :) I'd suggest you fix it, as I've seen a problem with a power supply after the plug had been pulled from it. The owner said he saw an arc from the power cord to the power supply, and it this case it meant a toasted power supply.

---

### Post by Rasa1111 on 2010-09-04
> The owner said he saw an arc from the power cord to the power supply, and it this case it meant a toasted power supply.

Yup.
 My brother did the same thing. 
and it was after I repeatedly told him not to do that. lol
needless to say...
he listens better these days.. :p

---

