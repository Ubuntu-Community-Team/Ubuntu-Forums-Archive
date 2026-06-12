---
title: "Help!!!"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by mscout2004 on 2008-12-30
I have tried many different things to get my wireless card to work in ubuntu on my toshiba a215-s6804. Still cant get it to work. If someone can tell me what model the atheros card is I can create an inf file for it and use ndiswrapper to get it to work.

---

### Post by cdtech on 2008-12-30
Using the command "lspci" will list the card's model your using:
```
lspci
```

---

### Post by mscout2004 on 2008-12-30
ok I ran that command and it said AR242x. I cant even find that card on atheros website. What am I doing wrong??? Why wont it work???

---

### Post by melojo on 2008-12-30
Here is a post, read through it and others have got it working.

[http://ubuntuforums.org/showthread.php?t=940048](http://ubuntuforums.org/showthread.php?t=940048)

---

### Post by mscout2004 on 2008-12-30
still wont work after trying the suggestions in that post.

---

### Post by mscout2004 on 2008-12-30
this is annoying as hell I had this same card when I was running 8.04 before my hard drive went bad, and I just installed an inf file to get it to work. I havent been able to get the same file again. Any suggestions?????

---

### Post by balloooza on 2008-12-30
Wait, you are in the absolute beginner talk and you know how to use vi??!! I think that you just didn't folow the instructions. The guide should work, but so this instead
```
sudo gedit /etc/modprobe.d/blacklist
```
and then add:
```
blacklist ath_pci
blacklist ath_hal

```
to the end of the file

then run
```
sudo modprobe -r ndiswrapper
```
then run
```
sudo modprobe ath_pci
```
then reboot and then try the wireless network

---

### Post by mscout2004 on 2008-12-30
did that and got the same results...nothing...darn machine.

---

### Post by cdtech on 2008-12-30
Check out this site for the driver:
[http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/)

---

### Post by mscout2004 on 2008-12-30
i downloaded this driver and did the make and sudo make install commands. Still no wireless card in ubuntu

---

### Post by Shannon_VanWagner on 2008-12-31
I'm seeing quite a few hits with the google search term "AR242x".

Perhaps you could try the steps here:
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

Looks promising...

Also, if you could double check that your wireless hardware button (if you have one) on your notebook is in the enabled position and then run sudo lspci -v |grep Atheros and post the result in this forum, that might help.

Dugg up

Congrats on your Freedom!

Shannon VanWagner

---

### Post by mscout2004 on 2008-12-31
got an 404 error when trying to download the modules in that how-to could not get an of the links to work. I will post in the postbin

---

### Post by mscout2004 on 2008-12-31
results of dmesg

[http://pastebin.ubuntu.com/96924/](http://pastebin.ubuntu.com/96924/)

---

### Post by albinootje on 2008-12-31
> **mscout2004 said:**
> i downloaded this driver and did the make and sudo make install commands. Still no wireless card in ubuntu

Can you please post the output of the following :
```

sudo lshw -c network
dpkg -l|grep ndis
lsmod|grep ath
sudo iwlist scan
ifconfig -a

```

Thanks in advance.

---

### Post by mscout2004 on 2008-12-31
**sudo lshw -c network**
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:a0:d1:95:9d:60
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.101 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:98:26:4b:dc:06
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

**dpkg -l|grep ath**
ii  iputils-tracepath                         3:20071127-1                            Tools to trace the network path to a remote 
ii  libgweather-common                        2.24.1-0ubuntu1                         GWeather common files
ii  libgweather1                              2.24.1-0ubuntu1                         GWeather shared library
ii  libkpathsea4                              2007.dfsg.2-3ubuntu1                    TeX Live: path search library for TeX (runti
ii  libxml-xpath-perl                         1.13-6                                  Perl module for processing XPath
ii  openoffice.org-math                       1:2.4.1-11ubuntu2.1                     OpenOffice.org office suite - equation edito
ii  perl-base                                 5.10.0-11.1ubuntu2.2                    The Pathologically Eclectic Rubbish Lister
ii  python-numeric                            24.2-9                                  Numerical (matrix-oriented) Mathematics for 


**lsmod|grep ath**
did nothing


**sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


**ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:95:9d:60  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe95:9d60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6761554 (6.7 MB)  TX bytes:1065790 (1.0 MB)
          Interrupt:220 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

pan0      Link encap:Ethernet  HWaddr 6a:98:26:4b:dc:06  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by mscout2004 on 2008-12-31
hopefully you can make something out of that. I have no clue what that stuff says...?????

---

### Post by albinootje on 2008-12-31
Thanks.
So you have internet through your network-card, but your wifi-card is not showing anything yet.
Can you also post the output of :
```

ndiswrapper -l
lsmod|grep ndis
dmesg|tail -n30

```
Thanks.

---

### Post by mscout2004 on 2008-12-31
**ndiswrapper -l**
netathw : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

**lsmod|grep ndis**
ndiswrapper           196380  0 
usbcore               148848  5 uvcvideo,ndiswrapper,ehci_hcd,ohci_hcd


**dmesg|tail -n30**
[  105.196161]  domain 0: span 0-1 level MC
[  105.196169]   groups: 0 1
[  105.196181]   domain 1: span 0-1 level CPU
[  105.196188]    groups: 0-1
[  105.196198] CPU1 attaching sched-domain:
[  105.196203]  domain 0: span 0-1 level MC
[  105.196209]   groups: 1 0
[  105.196218]   domain 1: span 0-1 level CPU
[  105.196224]    groups: 0-1
[  323.729226] CPU0 attaching NULL sched-domain.
[  323.729259] CPU1 attaching NULL sched-domain.
[  323.736132] CPU0 attaching sched-domain:
[  323.736146]  domain 0: span 0-1 level CPU
[  323.736158]   groups: 0 1
[  323.736171] CPU1 attaching sched-domain:
[  323.736176]  domain 0: span 0-1 level CPU
[  323.736182]   groups: 1 0
[  341.184096] r8169: eth0: link up
[  341.584224] NET: Registered protocol family 17
[  357.616019] APIC error on CPU0: 00(40)
[  357.616036] APIC error on CPU1: 00(40)
[  362.351541] NET: Registered protocol family 10
[  362.352763] lo: Disabled Privacy Extensions
[  372.669034] eth0: no IPv6 routers present
[  454.717023] APIC error on CPU0: 40(40)
[  454.717051] APIC error on CPU1: 40(40)
[ 1434.829981] APIC error on CPU0: 40(40)
[ 1434.830010] APIC error on CPU1: 40(40)
[ 1630.136020] APIC error on CPU1: 40(40)
[ 1630.136039] APIC error on CPU0: 40(40)

---

### Post by albinootje on 2008-12-31
> **mscout2004 said:**
> **ndiswrapper -l**
netathw : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

**lsmod|grep ndis**
ndiswrapper           196380  0 
usbcore               148848  5 uvcvideo,ndiswrapper,ehci_hcd,ohci_hcd


Looks all pretty good.
Except that "sudo iwlist scan" should have showed something.

Can you also show the output of :
```

sudo update-usbids
lsusb

```

---

### Post by mscout2004 on 2008-12-31
**sudo update-usbids**
--2008-12-31 10:22:07--  [http://linux-usb.sourceforge.net/usb.ids](http://linux-usb.sourceforge.net/usb.ids)
Resolving linux-usb.sourceforge.net... 216.34.181.96
Connecting to linux-usb.sourceforge.net|216.34.181.96|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357258 (349K) [text/plain]
Saving to: `/var/lib/misc/usb.ids.new'

100%[======================================>] 357,258      171K/s   in 2.0s    

2008-12-31 10:22:10 (171 KB/s) - `/var/lib/misc/usb.ids.new' saved [357258/357258]

Done.

**lsusb**
Bus 006 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by mscout2004 on 2008-12-31
tried the  "sudo iwlist scan" again still same result

---

### Post by mscout2004 on 2008-12-31
when i go into ndiswrapper, it says the driver is installed and the hardware is present but, it will not let me configure the network. says no network configuration tool found. 

 dont know if this info will help or not???

---

### Post by albinootje on 2008-12-31
> **albinootje said:**
> Looks all pretty good.

Hmm, I think I was wrong there :(
Ndiswrapper sees the other module "as in use".
You should blacklist the ath_pci module I think.

Can you post the link to the howto you've followed ?

---

### Post by mscout2004 on 2008-12-31
when i try to blacklist the module it will not let me save the file..do I have to use sudo nautilus???

---

### Post by Shannon_VanWagner on 2008-12-31
Yes.. I see that I can get to [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/) in the web browser, but I am not able to download the file:
[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

I've sent an email to the Admins for kernel.org, I'll let you know when they replied. Actually looking at the suggestion on [http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex) , I've used it before and it worked for me.

Should they make the download available and it still doesn't work, would you be willing to go as far as to reinstall your Ubuntu system completely(all 7 steps, lol) and try from fresh? Just a question for later.

The ubuntuforums will get you patched up and working one way or the other. So long as you're willing to keep trying stuff, right?

Again, congratulations on your Freedom.

---

### Post by albinootje on 2008-12-31
> **mscout2004 said:**
> when i try to blacklist the module it will not let me save the file..do I have to use sudo nautilus???

Please read this :
[https://lists.ubuntu.com/archives/ubuntu-users/2008-June/151117.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-June/151117.html)
> 
sudo echo "blacklist ath_pci" >> /etc/modprobe.d/blacklist

sudo ndiswrapper -i yourdriver.inf

Add ndiswrapper to the autoloading list

sudo modprobe ndiswrapper
sudo echo "ndiswrapper" >> /etc/modules


---

### Post by mscout2004 on 2008-12-31
when i did the ```
sudo echo "blacklist ath_pci">>/etc/modprobe.d/blacklist
```it said permission denied.

---

### Post by albinootje on 2008-12-31
> **mscout2004 said:**
> when i did the ```
sudo echo "blacklist ath_pci">>/etc/modprobe.d/blacklist
```it said permission denied.

Can you try this instead :
```

sudo su -
echo "blacklist ath_pci" >>/etc/modprobe.d/blacklist
echo "ndiswrapper" >> /etc/modules
exit

```
And reboot.

---

### Post by mscout2004 on 2008-12-31
did the code no problems rebooted still no wireless card in ubuntu.

---

### Post by albinootje on 2008-12-31
> **mscout2004 said:**
> did the code no problems rebooted still no wireless card in ubuntu.

Okay, can you post the output of the following, after your reboot :
```

lsmod|grep ath
lsmod|grep ndis
ndiswrapper -l

```

---

### Post by mscout2004 on 2008-12-31
**lsmod|grep ath**
nothing

**lsmod|grep ndis**
ndiswrapper           196380  0 
usbcore               148848  5 uvcvideo,ndiswrapper,ehci_hcd,ohci_hcd


**ndiswrapper -l**
netathw : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

---

### Post by albinootje on 2008-12-31
> **mscout2004 said:**
> 

**ndiswrapper -l**
netathw : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

Did you install the Windows driver for XP or Vista ?

---

### Post by mscout2004 on 2008-12-31
i would have no idea which how-to i used. i followed about 5 different ones off the ubuntu forums.

---

### Post by albinootje on 2008-12-31
> **mscout2004 said:**
> i would have no idea which how-to i used. i followed about 5 different ones off the ubuntu forums.

Can you try this one :

[http://ubuntu-snippets.blogspot.com/2008/12/making-atheros-ar242x-wireless-chipset.html](http://ubuntu-snippets.blogspot.com/2008/12/making-atheros-ar242x-wireless-chipset.html)

---

### Post by mscout2004 on 2008-12-31
i uninstalled the driver and then tried reinstalling the driver, but i think it locked up on me. just the ndiswrapper, the kernel is still functioning.

---

### Post by mscout2004 on 2008-12-31
that one worked thanks for all the help.

---

### Post by mscout2004 on 2008-12-31
dang it!!!  It worked for about an hr. Now it will say it connects to the network but nothing can get access to the internet. Firefox and synaptic pakage manager cant even get access.  What happened to it????

---

### Post by albinootje on 2008-12-31
> **mscout2004 said:**
> dang it!!!  It worked for about an hr. Now it will say it connects to the network but nothing can get access to the internet. Firefox and synaptic pakage manager cant even get access.  What happened to it????

Can you post the output of :
```

ifconfig -a
route -n
cat /etc/resolv.conf
dmesg|tail -n30

```
To see whether it's DNS issue.

---

### Post by mscout2004 on 2009-01-01
I went in this morning to ubuntu and went down to plug in to a wired network and had the same problem. I think there is something wrong with the network settings in ubuntu. I tried pinging my gateway and got no response from it.

**ifconfig -a**
ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:95:9d:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:792 (792.0 B)  TX bytes:1152 (1.1 KB)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:157145 (157.1 KB)  TX bytes:157145 (157.1 KB)

pan0      Link encap:Ethernet  HWaddr 9a:bb:3c:3b:d9:7d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:42:b8:96  
          inet addr:169.254.7.75  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21e:4cff:fe42:b896/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3140 (3.1 KB)  TX bytes:3144 (3.1 KB)
          Interrupt:18 Memory:f8200000-f8210000 


That is the one one I could remember to get when I got into ubuntu this moprning.  

I will be on most of the day, let me know when you get on today, it will be hard to do cause I will have to go back and forth trying things, but I can copy the output to a txt file into my windows partion so it would be okay.

---

### Post by albinootje on 2009-01-01
> **mscout2004 said:**
> 
ifconfig -a
-- cut --
wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:42:b8:96  
          inet addr:169.254.7.75  Bcast:169.254.255.255  Mask:255.255.0.0


Okay, thanks for the output.
The 169.254.x.x addresses are not real ip-addresses.
If you have the chance can you try the *wired* connection with the command :
```

sudo dhclient

```

---

### Post by mscout2004 on 2009-01-02
I plugged in the wired connection and ran the code, but it did nothing. Still same output and no response from the internet throught the browser.

---

