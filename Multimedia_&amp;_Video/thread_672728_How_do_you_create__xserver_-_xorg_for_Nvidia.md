---
title: "How do you create  xserver - xorg for Nvidia"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by russ1960 on 2008-01-19
I have an older Dell - early 00 - 01 with a Celeron  2.0 -  my Nvidia card is in the pci slot - I cannot disable the on board video from the bios (older bios set on auto detect).   The install went fine but no xorg file created because  Ubuntu couldn't detect my video card.

I tried to edit xorg with nano but no file is there to edit because was not created.

How do I put this file in place to get xorg working?  My card is a PNY Nvidia FX5200 PCI  256mb in PCI slot 1.  I will have to edit from the command line unless there is something i can do on a re-install.

I am a total newbie at this but willing to learn.

Thanks

Russ

---

### Post by EXCiD3 on 2008-01-19
Try installing the nvidia graphics driver using Envy. It will install the drivers AND configure /etc/X11/xorg.conf for you. [http://www.[SIZE=-1]albertomilone.com/nvidia_scripts1.html[/SIZE]]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by russ1960 on 2008-01-19
How do I do this from a command line?   I cannot boot up at all?

Thanks

---

### Post by EXCiD3 on 2008-01-19
If you can get to a terminal:
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu6_all.deb
sudo dpkg -i envy_0.9.9-0ubuntu6_all.deb
sudo apt-get install -f
sudo dpkg -i envy_0.9.9-0ubuntu6_all.deb
sudo envy -t
```This should install it correctly for you. 

Quick overview of what is going on:
If the first dpkg command returns errors then you have unmet dependencies. sudo apt-get install -f will download and install these dependencies. try to install the package again using dpkg again. envy -t runs the terminal mode of envy!

Good luck!

**NOTE: **This will probably only help if you have an xorg.conf that exists. "sudo nano /etc/X11/xorg.conf" shoud bring up a file with text in it. Remember that Linux IS case sensitive. Envy will only configure the graphics portion of xorg.conf.

I forgot to mention, if you want to redo your xorg.conf, ```

 dpkg-reconfigure -phigh xserver-xorg
```
will bring up a wizard to reset your xorg.conf file. After this is done you will still need to install your graphics driver and configure the xorg using Envy.

---

### Post by russ1960 on 2008-01-20
How do I get terminal to come up from the command line?

Thanks

Russ

---

### Post by ginnie6 on 2008-01-20
at grub go into recovery. that will get you to a command line.

---

### Post by russ1960 on 2008-01-20
ok-I have that - what do I do next?  I have no xorg file at all - it is blank because couldn't detect the card. So I have to create from scratch.   Do you have a sample?

Thanks

Total Newbie on command line editing

---

### Post by EXCiD3 on 2008-01-20
Terminal and the command line are the exact same thing. ;)

Lets make sure your video card is being detected for sure. Run ```
lspci
``` in terminal/command line. In the output you should see your video card listed among other things. If it is not detected we have a problem. Post the output of the lspci command for us just to be sure.

If it **is** detected, you will need to reconfigure the xserver using the dpkg-reconfigure command. ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This will rewrite your xorg.conf file for you allowing you to then install Envy as i mentioned before.

---

### Post by russ1960 on 2008-01-20
The video card does show at address:   0000: 01: 04.0 so it was picked up - I tried run the sudo dpkg - reconfugre and it failed.  It asked me for various command extensions.

Let me know what I need to do next.

Thanks

Russ

---

