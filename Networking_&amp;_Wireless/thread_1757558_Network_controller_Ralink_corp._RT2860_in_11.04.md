---
title: "Network controller: Ralink corp. RT2860 in 11.04"
date: 2011-05-13
forum: Networking &amp; Wireless
---

### Post by farsight on 2011-05-13
Hey folks, 

I am not entirely sure if this is the best place for this post, however I thought I would highlight an issue I have recently encountered in Ubuntu 11.04 (Kernel: Linux 2.6.38-8-generic (i686)), when running in WUBI.

_Details:_

Laptop brand: Acer
Laptop model: 5735Z
Wireless network card info: Ralink corp. RT2860

Okay, so I am connected to a netgear router (that works fine in Windows Vista - I am running a dual boot machine), and am posting from within Ubuntu 11.04 to report this. 

The issue relates to the fact that the wireless is unbearably slow (unable to even load basic pages such as Google or BBC news) when the laptop is not connected to the power mains. Upon reconnecting the power cable, the wireless returns to a functional speed and works nicely. I don't know if this has something to do with some sort of power saver option....however this would make a complete lack of sense to me.

Effectively, I just wanted to report this quirk and put it out there to see if anyone else had had a similar experience.

---

### Post by chili555 on 2011-05-13
> I don't know if this has something to do with some sort of power saver option....however this would make a complete lack of sense to me.It probably does have to do with power saving but I suspect it's a bit faulty. With the mains disconnected, please run:```
iwconfig
```Does it report Power Management:On? If so, please do:```
sudo iwconfig wlan0 power off
```Is your speed improved?

---

### Post by farsight on 2011-05-13
Thank you for your reply :)

I followed the instruction provided and power save was already off. Either way, the problem seems to have cleared (for now). I'll report back if this persists. 

As an aside: commendations to the Ubuntu 11.04 team....after a few weeks on 11.04, I'm pleased to report that Unity rocks :D 

Kind regards
Farsight

---

### Post by ohan_g9 on 2011-05-30
Thanks for this!

I'm running

Xubunto 11.04 on a
Asus eee pc 901

and have similar problems with the wifi;
it goes slow and the connections dies when running on battery.

Turning of Power Management on the wlan0 helps,
(using "sudo iwconfig wlan0 power off" ).

However, the Power Management automatically turns on again when I plug in and re-dismount the power adapter.

Now I wounder:
How do I permanently turn of the Power Management for the wifi?

---

### Post by chili555 on 2011-05-30
I'm not totally sure. You might look around in System > Preferences > Power Management.

In my system, there is a file called /etc/laptop-mode/conf.d/wireless-[COLOR="Red"]iwl[/COLOR]-power.conf. I have an Intel iwl3945 wireless card. You might do:```
ls /etc/laptop-mode/conf.d
```See if you have a conf file that relates to your Ralink card. In my case, the file says, in part:> # Control Intel IWL wireless power?
CONTROL_IWL_POWER=0I'm guessing the 0 means no. Indeed, my iwconfig says:> wlan0     IEEE 802.11abg  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:24:56:2A:99:99   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          [COLOR="Red"]Power Management:off[/COLOR]
          Link Quality=69/70  Signal level=-41 dBm  
I can only guess if the two are related. See if you have a similar file. You can sudo gedit it to change to =0. Reboot and tell us the result.

---

### Post by ohan_g9 on 2011-05-30
[Partly SOLVED, see also post #8]

I don't have a /etc/laptop-mode/conf.d, not even a /etc/laptop-mode .

But I found the answer at:

[ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/]("http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/")

Create or edit:
/etc/pm/power.d/wireless
```
sudo nano /etc/pm/power.d/wireless

```
In this file add:
```
#!/bin/sh
/sbin/iwconfig wlan0 power off
```
Now the Power Management stays off when I plug in and re-dismount the power adapter. And my wifi is now working, also without the power adapter mounted.

---

### Post by chili555 on 2011-05-31
Super! You have helped a few searchers, too. Thanks.

---

### Post by ohan_g9 on 2011-06-01
Just as chris wrote on 2011-01-05, in post #8 at
["EEPC 901: rt2x00pci WLAN will not work after suspend if aspm was active during suspend"]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/689004")

The problem still persists, with reconecting after suspended, also for me.

The solution, that woks for me as well as for chris was to
Turn of PCIe bus power saving:

```
sudo touch /etc/pm/power.d/pcie_aspm
```

> (There is man pm-powersave for the curious, btw.)
Thanks to Wolfgang Kufner!

---

### Post by Xvani on 2011-06-06
Power saving fix worked for me too! Thanks!!

Hopefully someone reported this bug?

---

### Post by N4RPS on 2011-08-25
Hello, all!

I have been interested in Linux for a long time, but I've had to wait for a version of Linux that would install without all those driver issues to have to resolve. Many thanks to those who have worked hard to get Linux to the point where it can finally be installed and used sucessfully by a typical user, such as myself.

I'm using Lubuntu 11.04 on an Asus EEE netbook that has a built-in RT2860-based WiFi adapter. The installation onto a 4GB thumb drive was effortless. Again, my complements to the chefs.

My question is: Is there a driver available for this card that will allow master mode. If so, where do I find it, and how do I go about installing it, keeping in mind that I am a total idiot about all things Linux? :confused:

Thanks for your help in advance.

73 DE N4RPS

Rob

---

