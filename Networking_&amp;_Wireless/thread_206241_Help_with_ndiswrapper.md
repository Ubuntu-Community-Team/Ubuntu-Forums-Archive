---
title: "Help with ndiswrapper"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by cerpin_taxt on 2006-06-29
I recently installed Ubuntu on one of my machines.  The only way for me to currently connect to the internet is through a wireless usb adapter (DWL-G122, hardware version A1).  Knowing that the software that came with device will not work with Ubuntu, I looked around and found the source code for ndiswrapper, which would allow me to run the driver for my adapter.  I downloaded the tar.gz on one of my computers with internet access, and burnt it to a CD-RW.

After putting the cd into my disk drive and extracting the file into a directory on the desktop, I opened up the terminal and made my way to the directory.  Once in the directory I followed the directions for installing programs from source code (found here: [http://monkeyblog.org/ubuntu/installing/#source)](http://monkeyblog.org/ubuntu/installing/#source)).  I typed 'make' after typing in './configure' (which yielded no results), and to my suprise, I was given the message: "bash: make: command not found".  I'm obvoiusly doing something wrong, and would greatly appreciate it if someone could help me.

I am not sure if there are compiler tools installed on my computer, and if anyone could link me to them so I could burn them to a CD and transfer it to my Ubuntu computer, I would be forever greatful.  The version of ndiswrapper I downloaded can be found here: [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

---

### Post by pontius_lake on 2006-06-29
Hi ive been in the same position as you have,

First off it would be easier to install Ndiswrapper by using the Synaptic Packet Manager.( System > Administration > Synaptic Package Manager ) Seach for ndiswrapper you should get a few results. Mark ndisgtk for install and ndiswrapper-utils and click apply. 

The problem with make not working is simply its not installed, use the Synaptic Packet Manager and seach for MAKE. Install it, and your problem would be solved. Personally i find that using the Synaptic Packet Manager is much easier :P for installing ndiswrapper.

I just read that you havnt got an internet connection so Synaptic Packet Manager isnt going to work to well. Right, You need 'Make' , see if it works then,  you may run into a few errors post them back here. I hope all this info is correct :D Good luck

---

### Post by cerpin_taxt on 2006-06-29
*I just read that you havnt got an internet connection so Synaptic Packet Manager isnt going to work to well. Right, You need 'Make' , see if it works then, you may run into a few errors post them back here. I hope all this info is correct  Good luck*

Sorry, but I'm having a little trouble understanding what you're saying I should do.  I know that I need make, but where can I get it?

---

### Post by cerpin_taxt on 2006-06-29
Well, I finally got ndiswrapper working by using my CD in Synaptic, but now I'm not sure how to get the drivers for my Wireless USB Adapter.  It uses the Prism2/2.5/3 chipset, so I'm figuring on taking a gamble with the drivers for the DWL-G122 A2 chipset, because they're both made by the same people.

Here's the link to  the page where I THINK the drivers can be found:[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D)

Once again, I'd appreciate any feedback or help from you guys on how to find, download, or install the appropriate drivers.

---

### Post by stupidkid on 2006-06-29
Do a iwconfig and make sure you don't have a wireless interface already. If you do, you'll have you remove the pre-loaded drivers. You have your windows driver cd right? Use that and find and copy the .inf (or .INF) and the .sys (.SYS) files to your home directory. Then run sudo ndiswrapper -i driver.inf (replace this with that .inf file). Then run sudo ndiswrapper -l (that's a lowercase L) and you should see "driver present hardware present". Finally sudo modprobe ndiswrapper and you should connect now.

---

### Post by pontius_lake on 2006-06-30
Ndiswrapper Basic Commands
---------------------------
Put the inf file on the desktop and CD to it, ( cd Desktop )
sudo ndiswrapper -i DRIVERNAMEHERE.inf - Installs driver

ndiswrapper -l       <--- This will list the driver installed, it should say something like yourdrivername Present.

If not remove the driver by typing sudo ndiswrapper -e DRIVERNAMEListedbyNdiswrapper.

---

