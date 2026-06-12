---
title: "Jaunty - Nvidia driver says it installs, but Ubuntu will not start with it"
date: 2009-05-02
forum: Multimedia Software
---

### Post by gohanssjn on 2009-05-02
Whenever I activate the restricted driver (1.80, or 1.73), Ubuntu fails to boot all the way in.  I get dumped to a screen asking if if I want a "Low Video" mode or to try and fix it.  Neither of these options works.  I have to go into recovery mode from GRUB and tell it to try and fix xorg.conf to get into Ubuntu again.  Any ideas?:confused:

If it helps:
Intel Q6600 @ 3.2GHz
4GB Ram
NVIDIA 8800GTX (BFG)(2 monitors run off this card)
X-Fi Fatal1ty
Hauppauge 1600

Thanks for any help.

---

### Post by chaser.nl on 2009-05-02
Manual driver install

Select the option low video to get a desktop and be able to grab the latest driver from nvidia.

This is a dirty workaround i am using for some time now. Be sure to first download the latest linux driver from the nvidia website: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Save the driver to the desktop.

[size=3][color=red]Use this at own risk, it worked for me but maybe will not for you. Read & Understand what you do.[/size]
[size=2]Maybe even print the instuctions or write them down.[/size][/color]

**First switch to a other tty by pressing ctrl+alt+F3**

Now you will get a black screen where you are asked for your login name, login here to get a command line.

**Stop the current grafical session**
```
sudo /etc/init.d/gdm stop
```

**Remove any nvidia stuff installed**
```
sudo apt-get remove --purge nvidia*
```

**Change to the folder where the driver is**
```
cd ~/Desktop
```

**Run the driver downloaded from nvidia**
```
sudo ./NVIDIA-Linux-x86-180.51.pkg1.run
```

The installer will  ask to create a new configuration for you, if you have a custom xorg.conf it will make a back-up. I do let it create a new xorg.conf and it never let me down before.

**After driver installation start gdm again**
```
sudo /etc/init.d/gdm start
```

Maybe its not the way to go because it breaks automated installation of nvidia drivers but it takes me far less time to setup.

I hope this helps you and maybe more people :)

---

### Post by gohanssjn on 2009-05-02
> **chaser.nl said:**
> Manual driver install

**Run the driver downloaded from nvidia**
```
sudo NVIDIA-Linux-x86-180.51.pkg1.run
```



Ok, whenever I get to this step, it tells me the command cannot be found...

I even changed the downloaded file name to driver.run to make sure I typed it in right the first few times, same error.

This is so weird, I cannot get this package to run for the life of me :(

Redownloaded, no help at all.

---

### Post by punzada on 2009-05-02
you have to do: 

sudo ./driver.run

the ./ is needed to let the shell know the file you are looking for is in your current directory.

---

### Post by ed-koala on 2009-05-02
Also double check your xorg.conf file.  I've had issues with X not doing its job configuring it correctly, tho that may be due to having dual graphic cards.  Never hurts to check it tho.

---

### Post by rob444 on 2009-05-08
I tried to follow your guide chaser and I get the same error as the thread starter, it simply says "./NVIDIA-blaha.run: command not found".

Doesn't matter if I rename it a.run and try sudo ./a.run , same error. However if I just type ./NVIDIA-blaha.run it'll say "Permission denied".

Any clue on why it's acting up like this :O?

I found out that I didn't have permission to run it as an executable file so I just right clicked it on my desktop, went into properties and made sure I had permission. That worked and your guide is great Chaser.

Now the moment of truth to see if it'll actually use those drivers >_<

EDIT: Worked like a charm, thanks :).

---

