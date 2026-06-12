---
title: "2915ABG Wireless Nightmare"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by ToadJamb on 2010-10-25
I cannot for the life of me get my wireless card to work correctly.  

I am quite new to Ubuntu and this is my first try at a non-Windows OS, so I ask that you forgive any ignorance on my part.

lspci reveals that my card is an Intel 2915ABG in an IBM Lenovo Thinkpad z60m.  I have it set up to dual boot with Windows XP (where the wireless card has had no problems).  I have looked high and low and tried a number of solutions, including building the ipw2200 driver, which I have since read should be included in the kernel, but I am clueless on how to find it and none of the howtos, faqs, or guides detailed that part of the process.  I installed the ndiswrapper and installed the windows driver, which appeared to work initially, but once I shut down and rebooted, it now locks up my laptop within 30 seconds of connecting to a wireless network.

I am running 10.04 LTS.

Any help is greatly appreciated.

---

### Post by conradin on 2010-10-25
Thats an Intel card right? Intel tends to have decent Linux support, you might try their site:
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=10138&ProdId=1847&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=10138&ProdId=1847&lang=eng)

---

### Post by chili555 on 2010-10-25
The driver is included in the kernel; it's called ipw2200.

I suspect ndiswrapper is causing the lock-up because it is conflicting and fighting with ipw2200. Let's do some diagnostics. Open a terminal and do:```
dmesg | grep -e ndis -e ipw
```Post the result and we'll get it sorted out.

FYI, here is my wireless card:```
*-network:1
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 99:16:6f:9a:5f:88
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=ipw2200[/COLOR] driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007)
etc.
```

---

### Post by ToadJamb on 2010-10-25
That link is where I got the source to build the driver, which results in a message saying I need to install the ieee80211 subsystem, which subsequently appeared to need to be built and installed and it gave me build errors:

```
/ieee80211-1.2.18/ieee80211_module.c: In function ‘alloc_ieee80211’:
/ieee80211-1.2.18/ieee80211_module.c:148: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/ieee80211-1.2.18/ieee80211_module.c:149: error: ‘struct net_device’ has no member named ‘change_mtu’
/ieee80211-1.2.18/ieee80211_module.c:153: error: ‘struct net_device’ has no member named ‘get_stats’
/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)

```

But [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel") sure makes it look as though I shouldn't have to do all that to get my wireless card to work.  Of course there's always the chance that in my newbness I've undone something vital.

If, on the other hand, you were suggesting that I peruse and/or post in the Intel forums, a search there for "Ubuntu 2915abg" turns up 1 result, "Linux 2915abg" returns 0, while "Ubuntu 2915abg" returns 184 here (a number of which I have already been through).

---

### Post by ToadJamb on 2010-10-25
ndiswrapper is still installed with the windows driver installed.  I was inclined to think that I should be able to get by without ndiswrapper.  If I need to remove/uninstall stuff and do this again to clarify anything, I'll be happy to.  Here are the results of dmesg | grep -e:

```
toadjamb@ubuntu:~/Build/ieee80211-1.2.18$ dmesg | grep -e ndis -e ipw
[   21.381945] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   22.036984] usbcore: registered new interface driver ndiswrapper
[  126.638820] usbcore: deregistering interface driver ndiswrapper
[  126.655206] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  126.667195] ndiswrapper: driver w29n51 (Intel,12/19/2007,9.0.4.39) loaded
[  126.667642] ndiswrapper 0000:14:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[  126.674991] ndiswrapper: using IRQ 21
[  126.997472] usbcore: registered new interface driver ndiswrapper
toadjamb@ubuntu:~/Build/ieee80211-1.2.18$ 

```

---

### Post by chili555 on 2010-10-25
Let's try a temporary approach:```
sudo rmmod -f ndiswrapper
sudo modprobe ipw2200
```Now let's see if the kernel has any complaints:```
dmesg | grep -e ndis -e ipw
```We are looking for errors or warnings *after* here: [  126.997472] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2010-10-25
Do you have the wired ethernet attached all this time?

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for themAre you being "managed?"

---

### Post by ToadJamb on 2010-10-25
Ok, here are the commands and the output:

```
toadjamb@ubuntu:~$ sudo rmmod -f ndiswrapper
[sudo] password for toadjamb: 
toadjamb@ubuntu:~$ sudo modprobe ipw2200
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
toadjamb@ubuntu:~$ dmesg | grep -e ndis -e ipw
[   22.275451] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   22.963609] usbcore: registered new interface driver ndiswrapper
[  171.268170] usbcore: deregistering interface driver ndiswrapper
[  185.291463] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[  185.291471] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  185.291585] ipw2200 0000:14:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[  185.291702] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[  185.291802] ipw2200 0000:14:02.0: firmware: requesting ipw2200-bss.fw
[  185.464303] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
toadjamb@ubuntu:~$ 

```

After a reboot, I get:

```
toadjamb@ubuntu:~$ dmesg | grep -e ndis -e ipw
[   21.321959] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   22.140029] usbcore: registered new interface driver ndiswrapper
toadjamb@ubuntu:~$ 

```

Even after a reboot, a couple ndiswrapper-related items appear to be installed:

Windows Wireless Drivers (Ndiswrapper driver installation tool)
Userspace utilities for the ndiswrapper Linux kernel module (ndiswrapper-utils-1.9)

I have not had the ethernet attached for the duration of my troubles.  I do right now since I am working from the laptop, though.  It certainly makes it a lot easier to copy and paste things.  There is a good chance I installed the ndiswrapper stuff before I fully explored getting the ipw2200 driver to work, though.  I would much prefer the ipw2200 driver over ndiswrapper, if I can get it to work.  As for the Network Manager bit, as it stands, when I unplug my cable, I get nothing in the way of wireless (I don't even see the checkbox to enable/disable wireless networking like I did before and no wireless networks are detected).  And the wireless indicator at the top of the screen shows nothing (greyed out with the exclamation point).

---

### Post by chili555 on 2010-10-25
Ahem. The meaning of temporary is that, upon reboot, it's gone. The behavior you experienced is entirely normal. After you (temporarily) remove ndiswrapper and load ipw2200, is an interface created, perhaps eth1?```
sudo rmmod -f ndiswrapper
sudo modprobe ipw2200
iwconfig
sudo iwlist eth1 scan
```

---

### Post by ToadJamb on 2010-10-25
Touché.  Here is the output (no reboots this time round):


```
toadjamb@ubuntu:~$ sudo rmmod -f ndiswrapper
[sudo] password for toadjamb: 


toadjamb@ubuntu:~$ sudo modprobe ipw2200
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.


toadjamb@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

pan0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


toadjamb@ubuntu:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:1B:11:5E:65:E3
                    ESSID:"dlink"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-73 dBm  
                    Extra: Last beacon: 13096ms ago
          Cell 02 - Address: 00:24:B2:1A:97:68
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=93/100  Signal level=-35 dBm  
                    Extra: Last beacon: 12924ms ago

toadjamb@ubuntu:~$ 

```

---

### Post by chili555 on 2010-10-25
It looks like it works perfectly! I am troubled by this:> Cell 02 - Address: 00:24:B2:1A:97:68
                    ESSID:"[COLOR="Red"]\x00\x00\x00\x00\x00\x00\x00\x00\x00[/COLOR]"
                    Protocol:IEEE 802.11bg
                    Mode:Master
Is this your network? Is it a hidden SSID? Do networks now appear in Network Manager?

---

### Post by ToadJamb on 2010-10-25
I have no idea what Cell 02 is, but I have no idea what most of this stuff is.  I'm still learning my way round.  My network is hidden, but I can see wireless networks.

---

### Post by ToadJamb on 2010-10-25
Ok, so it seems to be working.  I am on wireless now with no lock ups, but these were "temporary" changes, right?  How do I make them permanent?

---

### Post by chili555 on 2010-10-25
I am off to bed. I suggest you remove ndiswrapper:```
sudo ndiswrapper -e  w29n51
sudo apt-get remove --purge ndiswrapper*
```Now let's be sure ipw2200 loads explicitly:```
sudo su
echo ipw2200 >> /etc/modules
exit
```Now click the Network Manager icon and select Connect to Hidden Wireless Network; fill in your details and connect.

Our fix is permanent and will survive many reboots.

---

### Post by ToadJamb on 2010-10-25
Awesome!  I cannot possibly thank you enough.  I owe you a beer (or six) or Mt. Dew or whatever it is Ubuntu gurus drink.

---

### Post by chili555 on 2010-10-26
Awesome! Glad it's working. Have fun!

---

