---
title: "Ralink 5390 not working"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by EvanEjk on 2011-02-01
I've followed these instructions exactly but when I get here:
> Reboot and you should see an ra0 interface when you run the command 'ifconfig'

All I see if this
```
eth0      Link encap:Ethernet  HWaddr 78:ac:c0:52:a0:2f  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7aac:c0ff:fe52:a02f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3084644 (3.0 MB)  TX bytes:260285 (260.2 KB)
          Interrupt:42 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

Even after I use "/etc/init.d/network-manager restart".

lspci gives me this
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: RaLink Device 5390
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

This laptop has a built in wireless kill key (f12), and the wireless turns off when I start the computer. Maybe this has something to do with it?

I would be very thankful if somebody could help me.

---

### Post by EvanEjk on 2011-02-02
I found that if I enable the wireless with that kill switch thing during the early startup then ubuntu does recognize the wireless card and is able to get the name of avaliable networks. But it still can't connect to them.

---

### Post by rebeltaz on 2011-02-04
I have the same problem on a Compaq CQ56 with the RaLink 5390 as well.... SOME ONE PLEASE HELP!!!

---

### Post by roxdub on 2011-04-03
Same here. This is the fourth or fifth laptop with zero wireless functionality in Ubuntu. It's getting embarrassing, and I'm tempted to move to Fedora or another distro.

Can anyone help out here? I'm also only getting eth0 and lo appearing as connections. the ralink 5390 appears in lshw, but as "unclaimed", and with no logical name. I suspect that, as with most wireless issues in Ubuntu, this has something to do with blacklisted models, but I have no idea what to do with that info. Any help is appreciated.

---

### Post by lngndvs on 2011-07-03
On an HP Pavilion G6, Ubuntu 11.04 has been installed.  It has not been able to connect wirelessly.   Following some instructions on the Inet, the driver was compiled and installed.  I have also tried several suggestions I have found: nothing works.  The driver has obviously loaded ok.  Something isn't working.  Perhaps the "hardware" switch on fn key f12.  The key requires to push "fn" together with "f12" even when the BIOS is set up to not need it.  THere is also an f5 switch with a globe on it, I'm not sure what it means.

I have noted the following:


  - The module is loaded on startup.  
  - iwconfig shows wlan0 as device rt5390sta.
  - rfkill list all does not list wlan0; but an hp wireless lan.
  - After rmmod hp_wmi, rfkill doesn't show any connection anymore.
  - After rmmod rt5390sta, network manager (on the toolbar) posts a message that the wireless connection has been lost, and the "wireless enabled" line is shadowed.
  - After modprobe rt5390sta --- network manager again shows the wireless enabled line checked.
  - still, rfkill list all shows nothing for rt5390sta
  - I have changed a line in config.mk of the driver, to enable rfkill to block / unblock in hardware.  Still doesn't work, since rfkill shows nothing.  

If any of the above presents a clue, I would be grateful.  I should mention that when I first installed the driver, rfkill did show this device, but somehow it doesn't do it anymore.

I think this laptop has a crippled bios, by HP, as it was quite difficult to boot from a cd, and there are few parameters to tweak.  

I would be pretty happy if I were able to use wireless networking with this, using GNU/Linux.  Should I return this to the vendor where I bought it?

AD

---

### Post by chili555 on 2011-07-03
May I see the exact wording of:```
rfkill list all
```Also, see post #8-10 here: [http://ubuntuforums.org/showthread.php?t=1793994&highlight=hp-wmi](http://ubuntuforums.org/showthread.php?t=1793994&highlight=hp-wmi)

---

### Post by lngndvs on 2011-07-04
After booting/logging in:

$ sudo rfkill list all
  0: hp-wifi: Wireless LAN
	  Soft blocked: no
	  Hard blocked: yes

After this,

$ sudo rmmod hp_wmi
$ sudo modprobe hp_wmi


Now the message is

$ sudo rfkill list all
  1: hp-wifi: Wireless LAN
         Soft blocked: no
         Hard blocked: no

Alan

---

### Post by chili555 on 2011-07-04
And, as the link I gave you suggests, did you investigate the likelyhood that hp-wmi maps to the wrong keys? Run:```
rfkill list all
```Try Alt+F12 instead of Fn+F12. Use the up arrow key to recall the last command on the terminal, rfkill list all. Are you still hard-blocked?

Repeat the procedure using Ctrl+F12. Alt+F11, Fn+F3, etc., etc. Keep looking and trying rfkill list all. I strongly suspect you will find a combination that works. If you do, please post back and report it here so the searchers will learn.

---

### Post by lngndvs on 2011-07-04
I have tried them all.  ALT and CTRL modifiers with Fn keys do nothing other than insert a two character string (~X, where X is some digit) in the console, except for a couple of keys.  

The only changes in rfkill list all are the toggling of hard blocking, for f12 combos.

Never do I see the rt5390sta interface in rfkill.  

What is strange about this is that earlier on, I DID see rt5390sta, so I have to backtrack and follow the compiling instructions again, and check the files in /etc/ 

I noted a post somewhere that indicated that after installing a newer kernel (2.6.38.10?) (or 2.6.38-10) this same problem was solved for a broadcom adaptor.  I saw some new kernels, and thought it might also be worth trying.  THat will have to wait until I have an ethernet connection.

Thanks,

Alan

---

### Post by chili555 on 2011-07-04
> The only changes in rfkill list all are the toggling of hard blocking,I thought your main issue was that the wireless button didn't remove hard-blocked and therefore the wireless wouldn't work. I suspect you have another issue and a misunderstanding. rfkill is not going to show wlan0 or rt5390sta; it is going to show that the system is or is not working because the wireless is turned on or off in software or hardware.

If the driver has been installed correctly, you will see a wireless interface, probably wlan0 here:```
iwconfig
```If the module has been loaded correctly, you will see it here:```
lsmod
```If it is not loaded, please do so:```
sudo modprobe rt5390sta
```Now is there a wireless interface?```
iwconfig
```If so, and rfkill is not blocked, can you click the Network Manager icon and connect?> After modprobe rt5390sta --- network manager again shows the wireless enabled line checked.And then do you see a network you can click and connect? Network Manager is not going to automatically connect to any old possibly insecure network.

---

### Post by lngndvs on 2011-07-04
iwconfig:

I do see the interface wlan0, hooked up to rt5390sta.  However, clicking on the network manager interface does not do anything.  

sudo rmmod rt5390sla results in the loss of the wlan0 connection to rt5390sla

I have to reboot to windows to post to the Inet.

There are some mentions I have seen, suggesting to downgrade to 10.10.  I think there are some people who have been able to make this work, however, on 11.04.  Still hoping that an upgrade of the kernel may help, or there may be patches to the driver.

Alan

---

### Post by chili555 on 2011-07-04
> I do see the interface wlan0, hooked up to rt5390sta. However, clicking on the network manager interface does not do anything.

sudo rmmod rt5390sla results in the loss of the wlan0 connection to rt5390slaYou do not have to downgrade; you do not have to return the laptop to the vendor; and, most of all, in order to get your wireless working, you do *NOT* need to rmmod the driver. When you click on the icon, do you see networks? Please see attached. In the attached example, I am attached to GBR1, my neighbors are Dynex and WEST5214. If you do not see networks, let's see if the interface scans. Please be sure the Fn+F12 buttons are pressed so that hard- and soft-blocked is No. Then do:```
sudo iwlist wlan0 scan
```If there are no scan results, let's see if there are any interesting kernel messages:```
dmesg | grep -e rt5 -e wlan
```You can copy and paste from the terminal to a text editor and save it and then put it on a USB key or similar to post it here.

---

### Post by lngndvs on 2011-07-05
Thank you for your assistance.  I discovered a problem in my installation of the driver: I had copied the wrong file over to /etc/Wireless .   Now I am responding from the linux partition of this laptop, which, after all this, seems just fine now.

Alan

---

### Post by chili555 on 2011-07-05
Awesome! Glad it's working. Have fun!

---

### Post by MadBillyGoat on 2012-12-30
> **lngndvs said:**
> Thank you for your assistance.  I discovered a problem in my installation of the driver: I had copied the wrong file over to /etc/Wireless .   Now I am responding from the linux partition of this laptop, which, after all this, seems just fine now.

Alan


Hello I have been unable to find this driver.. I have been looking for days..
Does anyone have a link to the driver.  
Thanks.

---

### Post by chili555 on 2012-12-30
> **MadBillyGoat said:**
> Hello I have been unable to find this driver.. I have been looking for days..
Does anyone have a link to the driver.  
Thanks.Please post:```
lspci -nn | grep 0280
arch
```I probably have them.

---

### Post by laeeq2 on 2013-09-15
this is output of fisrt line:

01:00.0 Network controller [0280]: Ralink corp. Device [1814:539a]

this is of second

i686

---

### Post by Elfy on 2013-09-16
Please start your own support thread rather than bumping someone else's old one.

Closed.

---

