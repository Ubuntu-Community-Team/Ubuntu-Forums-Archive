---
title: "tryign to get my nvidia card working"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by Linux&amp;Lizards on 2007-02-13
Ok,
I have an nvidia card that seems to be puzzling all the folks at the lug.
I'm about 4-5 months into linux so there is much that I still need to learn.

here is all I know 
lspci | grep VGA

01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

Can someone give me some step by step instructions on hwo to set it up with beryl?
I know there are other threads but I hate to hijack them..
anyhow any help would be greatly excepted.

---

### Post by highneko on 2007-02-13
The best beryl tutorials in my opinion are on the following page. [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)
Well.. It used to be good until all the automated scripts came.

Follow this if you don't have the nvidia drivers installed:
```
sudo cp /etc/apt/sources.list /etc/apt/_sources.list.backup
# Add the following line to the bottom of you /etc/apt/sources.list file if you're using edgy nvidia:
deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
# Then enter the commands:
wget [http://nvidia.limitless.lupine.me.uk/ubuntu/root@lupine.me.uk.gpg](http://nvidia.limitless.lupine.me.uk/ubuntu/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get update && sudo apt-get install linux-restricted-modules-$(uname -r) nvidia-glx
# For more information:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia)
```

---

### Post by Titus A Duxass on 2007-02-13
If you don't have the drivers installed use Automatix2, it's painless.

---

### Post by Linux&amp;Lizards on 2007-02-13
I made it this far    wget [http://nvidia.limitless.lupine.me.uk...pine.me.uk.gpg](http://nvidia.limitless.lupine.me.uk...pine.me.uk.gpg) -O- | sudo apt-key add -

and I got this

mcmahon@mcmahon-desktop:~$ wget [http://nvidia.limitless.lupine.me.uk...pine.me.uk.gpg](http://nvidia.limitless.lupine.me.uk...pine.me.uk.gpg) -O- | sudo apt-key add -
--21:21:58--  [http://nvidia.limitless.lupine.me.uk...pine.me.uk.gpg/](http://nvidia.limitless.lupine.me.uk...pine.me.uk.gpg/)
           => `-'
Resolving nvidia.limitless.lupine.me.uk...pine.me.uk.gpg... failed: Name or service not known.
gpg: no valid OpenPGP data found.


what should I do now?

---

### Post by highneko on 2007-02-13
That's because the forum changed the url. Try this:
```
wget http://nvidia.limitless.lupine.me.uk/ubuntu/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

---

### Post by Linux&amp;Lizards on 2007-02-13
Ok, so Iev followed all the steps now what?

---

### Post by Linux&amp;Lizards on 2007-02-13
by the way cool youtube vid.

---

### Post by highneko on 2007-02-13
> **Linux&Lizards said:**
> Ok, so Iev followed all the steps now what?
Hopefully you can restart and have it work. I just noticed that it says feisty testing user by your name. That little quide I made was for edgy but might work for feisty too. Here's a tutorial for feisty: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia) I don't know anything about feisty. I read parts of the guide and you should be ok, but you should read the whole thing if you're a feisty user. :!: 
> **Linux&Lizards said:**
> by the way cool youtube vid.
Thanks. That was a long time ago too, beryl has become even better.

---

### Post by Linux&amp;Lizards on 2007-02-13
KK ill restart my computer and see what happens.

I use edgy but I have feist on a seperate hard drive.

---

### Post by fenian on 2007-02-13
I believe the Riva TNT2 uses the legacy driver and therefore is not supported in beryl.

---

### Post by Linux&amp;Lizards on 2007-02-13
That would explain many of my problems.

Where did you here this I'll qoute it at the lug

---

### Post by Pollywoggy on 2007-02-13
I just installed Edgy and this is how I got things to work.  I have a Geforce 7600 GS (PNY Verto).

First, I did 'sudo apt-get install nvidia-glx' and that got all the packages needed.  Certainly easier than it was in Debian.

Once that was done, I had to do 'cd /etc/X11' and I edited the xorg.conf and did two things with it:

 1.  In Section "Module" I removed the "Load dri" line

 2.  In Section "Device" I found the line 
        Driver          "nv"
      and changed the "nv" to "nvidia"

I saved the file and then I added "nvidia" without the quotes to /etc/modules

Next I did "sudo modprobe nvidia" and then 'sudo lsmod | grep nvidia' to confirm the nvidia module had loaded.  I then restarted kdm:

sudo /etc/init.d/kdm restart

If after an upgrade, nvidia refuses to start, try 'sudo depmod' and then try to load the nvidia module.  If it loads, restart your session manager (kdm, gdm, or xdm) as above.

---

### Post by fenian on 2007-02-14
Look under hardware requirements [here]("http://gentoo-wiki.com/HOWTO_nVidia_GL_Desktop_Effects").

---

### Post by Linux&amp;Lizards on 2007-02-17
My dear friends,
I was able to beryl up and running on MY FRIEND'S computer.
I am now under the impression that there is no way to get it running with my nvidia card :(
I guess I'll have to live in a beryless world for now.

---

