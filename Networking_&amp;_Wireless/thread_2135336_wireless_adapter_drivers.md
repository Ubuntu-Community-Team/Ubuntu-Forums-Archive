---
title: "wireless adapter drivers"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by Roxbury on 2013-04-13
I'm trying to get my wireless DLink adapter to connect. 

I'm trying to install the drivers for the adapter. When I download the drivers, I'm left with a tar.gz. How do I run the tar.gz in order to install the drivers onto the machine? 

I'd really love to connect to the internet sometime soon. :)

---

### Post by ahallubuntu on 2013-04-14
~

---

### Post by Roxbury on 2013-04-14
The adapter is a Dlink DWA-140 B2.

I went to the uncompressed files and found a readme. I'm stuck on the part where it wants me to compile a certain directory. How do I compile?

---

### Post by ahallubuntu on 2013-04-14
~

---

### Post by Roxbury on 2013-04-14
Thank you for your answers.

Unfortunately, I tried all of that and everything went smooth, but on reboot I still couldn't get a connection.. 

By the way, unrelated.. everytime I reboot I have to do this:

apt-get install

startx

I have to do that in order to continue booting. Is that normal?

---

### Post by Roxbury on 2013-04-14
I went through every step that you linked, and when I reboot I still can't connect. :(

When I go to wicd network manager and try to log into my network, I get the bad password error.

Also, how do I confirm the drivers I installed are there? I still have the DPO file but I wonder if whatever I did before reboot is having any effect or if the driver isn't being recognized when I reboot..

I greatly appreciate anyones help.

---

### Post by ahallubuntu on 2013-04-14
You can type this in a terminal:

lsmod | grep ^rt 

to see if any ralink modules (drivers) are loaded.

You might also need to type (just copying-pasting from the link from above):

sudo modprobe -rf rt5370sta rt2800usb rt2800lib rt2x00usb rt2x00lib
sudo modprobe rt5370sta

so you get only the new rt5370sta driver.   I'm making some assumptions that the page I linked to is referring to the same card you have.

---

### Post by Roxbury on 2013-04-14
how do I know which RT number I need?

---

### Post by Roxbury on 2013-04-14
btw, when I do [COLOR=#000000]lsmod | grep ^rt I get

[/COLOR]rt5370sta             734575  0 
rt2800usb              22176  0 
rt2800lib              50886  1 rt2800usb
rt2x00usb              19162  1 rt2800usb
rt2x00lib              46110  3 rt2800usb,rt2800lib,rt2x00usb

---

### Post by ahallubuntu on 2013-04-14
Can you simply try the two commands above?  If they work, you can create a file like this, in terminal:

gksu gedit /etc/modprobe.d/ralink_blacklist.conf

and put these lines in it:

blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

You may also need to add the module name "rt5370sta" to the end of the file /etc/modules so that you won't need to do the modprobe at each reboot - again, wait until you try those two modprobe lines and see if they work before doing any of this.

---

### Post by Roxbury on 2013-04-14
I did the two sudo commands, and then I made the file with the blacklists. I also put rt5370sta in the modules file. On reboot, still can't connect but the difference is that I don't see any networks to even attempt to connect to through wicd network manager. Before, I could see my network, I just couldn't connect to it. Now it just says no wireless networks found when I go into network manager.

---

### Post by Roxbury on 2013-04-15
Thank you everyone for trying to help but I decided to just do the extra work of getting myself wired up directly.

---

### Post by kurt18947 on 2013-04-15
> **Roxbury said:**
> I did the two sudo commands, and then I made the file with the blacklists. I also put rt5370sta in the modules file. On reboot, still can't connect but the difference is that I don't see any networks to even attempt to connect to through wicd network manager. Before, I could see my network, I just couldn't connect to it. Now it just says no wireless networks found when I go into network manager.

In your post you mention both wicd and network manager.  You don't have both wicd and Network Manager running, do you?  They conflict and you won't get a connection.  If you are referring to wicd, a network manager then disregard please.

---

