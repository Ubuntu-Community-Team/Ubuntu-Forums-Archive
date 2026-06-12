---
title: "HELP! with ALFA USB wireless adapter"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by risk2thefactor on 2010-08-01
I cant get my ALFA USB wireless network adapter to work in Ubuntu 10.04 on my ASUS EEE PC.  It comes up as Ralink 802.11 n WLAN in the network connection window but all I can connect with is the internal wireless of the Netbook.  How do I use the USB card instead? why is this not working????

---

### Post by risk2thefactor on 2010-08-01
btw i downloaded the tar driver file from Ralink so Its on my HD. I just dont know enought about the command line to get this to work!!!

---

### Post by Maverick87 on 2011-01-30
It's an old post, but i don't see the answer.
Unfortunately I don't have the alfa adapter and I'm not sure you can solve your problem.
As you can see in the official ( [QUI]("http://www.alfa.com.tw/in/front/bin/ptdetail.phtml?Part=AWUS036NH&Category=105463#Download") )site you need only to put one default driver in blacklist to get alfa work, without installing from .tar any driver. ( i don't know how!) 

     disable default driver that ubuntu try to use with this adapter:
     open terminal, and type: sudo gedit /etc/modprobe.d/blacklist.conf
     in the text editor ( gedit ) add at the end the line: blacklist rt2800usb
     save the file and close the editor.

now you can restart your system and re-plugin your usb adapter and look if it's work!
( I don't have this adapter, I found this topic because I want to buy it! )

---

### Post by naja on 2011-01-30
hi
i really dont know the premalink, here is a copy past of it:

t problems in 10.10 64 bit
Hi everyone

I have an HP DV6 3143se which has a Ralink 3090 wifi card in it.the only thing that doesn't work at the moment is the Wifi. I tried installing the Linux backports module, but the trouble is that sometimes, my home wifi network is shown on the list of available networks and most often, it's not.

when the network does show up, and i click on it and enter my WPA2 password, it takes ages to handshake and then it tells me that my password is wrong. the same password works in windows 7 so something's not working.

when i try to disable and re enable wireless network on the network manager applet, i get a Wireless device not ready or Network manager not running message.

Any suggestions would be most welcome as i hate having to depend on my wired ethernet to stay connected.


EDIT
Thanks all  Please follow the method outlined below. Much thanks to Rtomakov for guiding me. 

Download new driver from ralink support page (version 2.4.1) and unpack it somewhere (I did it in my Download folder). 
Read README_STA_PCI file - find file config.mk in os/linux folder, open it with gedit and edit lines: - 
HAS_ATE=y (originally was n) - 
HAS_WPA_SUPPLICANT=y (originally was n) - 
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y (originally was n) and - 
HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n) 

Now, before compile, install via synaptic these packages: build-essential, devscripts and cdbs. * Note : I didn't have to do this, but perhaps you can try it out if you have your wired internet working. Edit is mine, not Rtomakov's. * 

Enter DPO_... folder from terminal and do sudo make, and after make finishes (without errors, ignore warnings) do sudo make install. That is it, but it is not over yet. Now open /etc/modprobe.d/blacklist.conf (as root) and add at the end: blacklist rt2800pci. Also open (as root) file /etc/modules and add: rt3390sta. 

* to do the above, i used the command - gksudo gedit /etc/modprobe.d/blacklist.conf and - gksudo gedit /etc/modules. Make your edits in gedit, Save them and CLOSE the file to return to the terminal.* 

Now, reboot. That should work.
Last edited by archithcr; November 3rd, 2010 at 03:08 AM.. Reason: Solution posted

this worked for me, though i didnt add rt3370 (my chipset i think it is the same as yours) but u have to blacklist rt2870sta .

but I have a wierd problem:
network-manager or any other gui program cant find it unless i choose to connect to hidden network AND it connects succesfully, otherthan that if i got it to connect through iwconfig ra0 essid xxxxx network manager can scan with it again.
this happens in kubuntu too but it was enough to run iwlist ra0 scan to make it appear in plasma network manager.
hope it helps you

---

