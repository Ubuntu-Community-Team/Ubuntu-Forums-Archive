---
title: "PCI wifi card temporarily works"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by silvergoat on 2011-09-18
I was at work a little while ago with one of my computers that I was setting up a PCI wireless card for.  It was a no go because I need a new wireless router, but I was still able to install the Netgear card which uses a Marvell 88w8335 chip.  It wasn't in the listing I was given a link to, but I searched and found a method to use it.  I followed instructions on using something called ndiswrapper at this link: [http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/](http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/)

but when I got to the section where I was supposed to append the supplicant file with my network settings, I stopped because the network was down and I didn't have the settings.

I brought the computer home and I tried to proceed where I left off, but the iwconfig command no longer identified a wifi card.

I went back to step 4 and reinstalled the supplicant and a few other steps and finally got back to where I left off....but I got an error/warning message.

```
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.

```

The card is now working, but I was not able to get past step 5 where I modify the supplicant file.  I don't even know where to find it, and the command does nothing.  Maybe it's the version I'm running that doesn't have the text editor or file install location that the command is designed to retrieve.

Regardless, I would like to find a way to make this card permanently installed on the PC.

here is the WLAN info in case it's needed:

```
wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by chili555 on 2011-09-19
> The card is now working, but I was not able to get past step 5 If the card is working, I'm not sure you need to edit a .conf file. Network Manager is supposed to take care of all that for you. When you boot up the computer, can you click the NM icon, see your network and connect? If so, you ought to be able to click Edit Connections, mark Connect Automatically and be all set.

Please see attached.

---

### Post by silvergoat on 2011-09-19
I will be at the computer tomorrow, but this morning I was able to complete the instructions that included loading the driver at login and I found the config and was able to edit it.  Next time I start the computer I should know if the driver will load itself automatically and, if so, all should be good.

Edit:

I did enter the settings in the NetworkManager at least once, but the driver itself wasn't present to even show my wireless networks available so I was unable to even select a network.

---

### Post by chili555 on 2011-09-19
> Next time I start the computer I should know if the driver will load itself automatically and, if so, all should be good.Let us know if we can help you further.

---

### Post by silvergoat on 2011-09-19
will do

---

### Post by silvergoat on 2011-09-20
No good news.   When I restarted the PC today, the wireless failed again.  The drivers can be loaded, but they will not remain installed/available.  They're there, but Lubuntu doesn't pull them on start up.

---

### Post by chili555 on 2011-09-20
> The drivers can be loaded, but they will not remain installed/available.What do you have to do to load them? We can likely fix it.

---

### Post by silvergoat on 2011-09-20
First I run this command-

ndiswrapper -l

and it returns this

```
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
wg311v3 : driver installed
device (11AB:1FAA) present
```

I then run this command-  

sudo modprobe ndiswrapper

this comes up

```
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
```

BUT......the wifi card becomes active and scans for and connects to my network.

---

### Post by chili555 on 2011-09-20
Let's have a look at:```
cat /etc/modprobe.conf
```This might be pretty easy...

---

### Post by silvergoat on 2011-09-20
returns:

```
alias rausb0 rt73
```

---

### Post by chili555 on 2011-09-20
> **silvergoat said:**
> returns:

```
alias rausb0 rt73
```:confused: :confused: :confused:

Do you have an interface using rt73? There is no rt73 module; it is actually rt73usb. If you are *very sure* you don't have such a device, I'd do:```
sudo su
rm /etc/modprobe.conf
echo ndiswrapper >> /etc/modules
exit
```Reboot and I think you'll be all set.

---

### Post by silvergoat on 2011-09-20
I don't know what rt73 is..... This PC is a frankenstein so it has a few different parts from a few PCs.

The wifi card is not USB, if that's what the rt73usb refers to....it's a netgear pci card with the antenna on the back.

EDIT:  AH- HA!  Just looked it up-  I had one of those connected before, but I chose to use the USB adapter in another computer.  The netgear PCI card took its place.

---

### Post by silvergoat on 2011-09-20
Yep, it worked.

What was happening?  I will be playing a lot more with Linux and I'm trying to pick up some know-how.

---

### Post by chili555 on 2011-09-20
I think ndiswrapper was stumbling over the improper .conf file and not loading as expected. We removed the .conf file altogether and asked /etc/modules to load ndiswrapper no matter what. 

Would you please use Thread Tools at the top and Mark Solved?

---

### Post by silvergoat on 2011-09-20
Thanks for your help with this-

---

