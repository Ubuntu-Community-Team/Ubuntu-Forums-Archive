---
title: "8800GT Issues"
date: 2008-02-01
forum: Multimedia &amp; Video
---

### Post by CaesarLike on 2008-02-01
Hi All,

I have just installed a EVGA 8800GT graphics card in my pc.  Now, I want to install Ubuntu onto the pc, but Ubuntu does not recognise the card, and either wants to run in very low graphics mode, or wont install at all.  So, as I am new to linux, does anyone know a simple solution to this problem?

As well, I tried installing a few other linux distros, and some like Zenwalk Linux had no problems with the card, where as others like Linux Mint did as it is derived from Ubuntu.

---

### Post by renzokuken on 2008-02-01
install ubuntu as normal in the low grafix mode.

then when fully installed, simply run the **Restricted Drivers Manager** from the menu and install the official nVidia linux driver to use your 8800gt to the max

---

### Post by CaesarLike on 2008-02-01
Hi renzokuken,

Thanks for the help.  Unfortunately, I cannot get Ubuntu to install past the point of it bringing up the message of using low graphics.

---

### Post by 123456 on 2008-02-01
Hi

I'm exactly the same problem :S
When I boot from the CD in low graphics mode shows a warning about the low resolution..after that it's just black screen.
I've searched other forums.. other ppl seem to bypass this problem using the onboard graphics card. I can't though :P

---

### Post by 123456 on 2008-02-01
Just found another way to install ubuntu :)
[http://ubuntuforums.org/showthread.php?t=641839]("http://ubuntuforums.org/showthread.php?t=641839")

---

### Post by CaesarLike on 2008-02-02
Ok, I have successfully installed the Nvidia drives for the 8800GT, and now Ubuntu appears to be working, and displaying, properly.

Below are the steps I took to do this.  Please note: I am a Linux newbie, and the procedure below is based on what I worked out from the post given below.

First to prepare, go to the post as provided by 123456 above. (Thanks 123456)
[http://ubuntuforums.org/showthread.php?t=641839]("http://ubuntuforums.org/showthread.php?t=641839")

Read the 9th post, by owlgorithm.  Note the requirement to install Ubuntu via the text based installer using the Alternate Desktop CD.  This avoids the problem of the installation stopping when it has problems with the graphics card.  Note also the requirement to download and install the libc6-dev libraries.

Read the 4th post, by Orlon.  This is the procedure I used to to do the installation.

The Procedure I used:

1). Install Ubuntu using the Alternate CD. When installed, make absolutely no changes at all to anything in Ubuntu, especially to do with the screen or graphics driver.  This can kill the Xserver setup and you can loose the GUI.
( [COLOR="Blue"]After completing the drivers installation I discovered that if you install the Nvidia drivers before you update a new installation it breaks the drivers and they no longer boot up.  I had to re-install the drivers.  It may be better to update the new installation **before** installing the drivers. This would include Automatix too I would assume. As well, updates to the kernel break the drivers installation it seems, and so have to re-install the drivers when-ever this happens.[/COLOR] )

2). When Ubuntu starts, go to the Nvidia website and download the drivers.
[http://www.nvidia.com/object/linux_display_ia32_169.09.html]("http://www.nvidia.com/object/linux_display_ia32_169.09.html")

Best to put this file in the root of your Home directory - easier to find later.
I also downloaded the X Config utility from the same page.  I unzipped it, but did nothing more with it. This was also put in the Home directory with the drivers installation file.  I have no idea if its actually needed, but have included it here as it was one of the things I did.

3). Use Synaptic to find and install the libc6-dev libraries.  I could not install the Nvidia drivers without these.

4). Hit CRTL + ALT + F1 to go to command prompt.

5). Close down the Xserver to kill the GUI - "sudo /etc/init.d/gdm stop".

6). Verify the GUI has been shut down using CRTL + ALT + F7.  If you see a blank black screen then the GUI has been successfully shut down.  Use CRTL + ALT + F1 to return to the command prompt.

7). Log in as root user - "sudo -i".  You need to be root user to install the Nvidia drivers.

8. Change directory to root - "cd /". I don't know why, but I had to do this to get to my home directory.

9). Change directory to where you have downloaded the Nvidia drivers install file eg "cd home/username"

10). Install the Nvidia drivers by typing - "sh NVIDIA-Linux-x86-169.09-pkg1.run"
The install program should then start.  Just say Yes to everything, including at the end when it asks if you would like the installer to configure the Xserver for you to allow the Nvidia drivers to be loaded at bootup.

11). When the installation was completed, I then followed Orlon's advice to type in "sudo modprobe nvidia".  This did not appear to actually do anything.  At least not that I noticed.

12). Next, type "startx" to start up the GUI again.  If the installation was successful, you should see a Nvidia logo appear as the GUI is starting.

13). Finally, reboot the PC, and hopefully everything should be fine.

After installation you should find NVIDIA X Server Settings in Applications > System Tools, where you can change the settings for the graphics card drivers.

And for those who might find such info interesting, here are my PC's specs:

Core 2 Duo E6420 CPU
Gigabyte 965P-DS3 Motherboard
2 Gigs, Crucial Balistix PC2-6400 DDR-800 Memory
EVGA GeForce 8800GT Superclocked (650MHz) 512Mb Graphics Card

---

### Post by RainKap on 2008-02-15
Very useful post - thanks very much for the step by step instructions!

One point I would like to add: bearing in mind that whenever you do a kernel upgrade it trashes the nVidia driver installation, I have found it to be useful to download the nVidia driver installers (I use both the 64-bit and the 32-bit, 'cos I dual boot my box into the 32-bit and 64-bit flavours of Gutsy) and burn them to a rewritable CD, which I keep in the second optical drive. I put the 32-bit driver installer in a directory called IA32 and the 64-bit driver installer in a directory called AMD64

After you've upgraded the kernel and find you're stuck with a text login, do

mount /dev/hdb
#my HDDs are SATA, so the optical drives show as had and hdb
cd /media/cdrom1/AMD64
# or cd /mediacdrom1/IA32
sudo sh N<tab>

and away you go!

HTH

Ian

---

