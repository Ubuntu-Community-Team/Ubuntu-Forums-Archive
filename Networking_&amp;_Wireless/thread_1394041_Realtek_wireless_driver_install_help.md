---
title: "Realtek wireless driver install help?"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by JoJerome on 2010-01-30
Installing Kubuntu (though tempted to try Ubuntu Satanic!) on a Vaio. Wireless card is a rtl8101. Naturally it has been a challenge to find.

Found a couple of promising websites:

[https://bugs.launchpad.net/ubuntu/+bug/342898](https://bugs.launchpad.net/ubuntu/+bug/342898)
[http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)

But I'm quite rusty on just how to install the drivers. On that second website, it freezes up when I get to the bit about "Check the sources out of the subversion directory." It looks like it's assuming I know how to do that from the shell?

I have a feeling the information is there - I'm just horribly rusty on how to get that info onto my drive.

Thanks in advance!

---

### Post by chili555 on 2010-01-30
Please let us see the following terminal commands:```
lspci -nn | grep Ethernet
dmesg | grep r8
```Thanks.

The files you wanted to get at Sourceforge are far too old to work here.

---

### Post by JoJerome on 2010-01-30
```
~$ lspci -nn | grep Ethernet
06:00.0 Ethernet controller [0200] Realtek Semiconductor Co., Ltd. RTL8101E/RTL
8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)


~$ dmesg | grep r8
[         1.382220]  r8169 Gigabit Ethernet Driver 2.3LK-NAPI loaded
[         1.382245]  r8169 0000:06:00.0: PCI INT A -> GSI 18 (level, low) ->IRQ 18
[         1.382300]  r8169 0000:06:00.0: setting latency timer to 64
[         1.382395]  r8169 0000:06:00.0: irq 27 for MSI/MSI-X
[        16.398275]  r8169 eth0: link down

```

Sorry for the delay - limited access to a wired connection this weekend. Thanks for the help! I would naturally happen to have a wireless card that isn't an easy snap in the front of the wiki to install. :-?

Thanks again!

---

### Post by chili555 on 2010-01-30
You have a driver, but it simply doesn't work. Googling finds several bugs about this, however they were supposed to be solved by this latest kernel version.

Are you ready to try the Realtek driver r8101?

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false)

If you want to try it, you will need to do:```
sudo apt-get install linux-headers-`uname -r` build-essential
```After you extract the file, read the readme and all the instructions are in there. Also, Dr. Chili, your humble servant, is at your service.

---

### Post by JoJerome on 2010-01-30
>  Also, Dr. Chili, your humble servant, is at your service.

A thousand thank yous Dr. Chilli! Given my aforementioned limited wired access this weekend, it'll probably be 24 hours or so before I can give it a go. But I'll let you know how it works and if I need further help.

It seems I was stumbling upon the right driver here and there, just not the how-to on installing it. 

The next laptop he wants me to convert has a Dell 13xx wireless card. I think I've done that one before and as I recall it also took some poking around but was a snap once I found it.

Next of course is to dual boot my Mac to Ubuntu. Which I understand does indeed require some poking under the hood. But in a fun way I hope. I learn lots on these forums!

---

### Post by JoJerome on 2010-02-01
Ok, downloaded the drivers from Realtek.com. Everything seemed to install great, even did what it told me to activate it. Yet tragically ... no wireless.

Rebooted, no wireless. 

```

~$ ifconfig -a
eth0        Link encap:Ethernet    HWaddr   00:1a:80:ee:el:50
                UP BROADCAST MULTICAST MTU:1500 Metric:1
                RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0  txqueuelen:1000
                RX bytes:0 (0,0 B)     TX bytes:0 (0,0 B)
                Interrupt:28 Base address:0xe000

```

I take this to mean it's installed ok. The wireless light on the machine itself is confirming it's on. But no access. I go to system settings -> Network Settings (the only place I can find that has anything to do with connectivity) and nothing.

I'm sure there's something painfully simple I'm missing here?

---

### Post by chili555 on 2010-02-01
Let's see if there is any change in things:```
dmesg | grep r8
lspci -nn | grep Network
```Thanks.

---

### Post by JoJerome on 2010-02-01
```

~$ dmesg | grep r8
[             1.561534] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[             1.561560] r8169 0000:06:00.0: PCI INIT A -> GSI 18 (level, low) -> IRQ 18
[             1.595248] r8169 0000:06:00.0: setting latency timer to 64
[             1.595346] r8169 0000:06:00.0: irq 28 for MSI/MSI-X
[            16.886620] r8169 eth0: link down


~$ lspci -nn | grep network
02:00.0 Network controler [0280: Intel Corporation PRO Wireless 4965 AG or AGN (Kedron) Network Connection [8086:4229] (rev61)

```


Taking an educated guess here, but does this mean the r8169 drivers need removing?

---

### Post by chili555 on 2010-02-01
> Wireless card is a rtl8101.> Intel Corporation PRO Wireless 4965It means your wirless card is *not* an rtl8101, it's an Intel 4965! Let's see why it's driver is not loading up and driving the card. Please post:```
dmesg | grep iwl
rfkill list
```Thanks.

---

### Post by JoJerome on 2010-02-02
```

james@Illuzionz-Vaio:~$ dmesg |grep iwl
[   15.589075] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   15.589079] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   15.599485] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.599516] iwlagn 0000:02:00.0: setting latency timer to 64
[   15.599573] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   15.649949] iwlagn 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   15.650085] iwlagn 0000:02:00.0: irq 29 for MSI/MSI-X
[   15.677633] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.631574] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   17.021924] iwlagn 0000:02:00.0: loaded firmware version 228.61.2.24
[   17.248719] Registered led device: iwl-phy0::radio
[   17.248760] Registered led device: iwl-phy0::assoc
[   17.248782] Registered led device: iwl-phy0::RX
[   17.248799] Registered led device: iwl-phy0::TX

james@Illuzionz-Vaio:~$ rfkill list
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
james@Illuzionz-Vaio:~$

```

So for future reference, when I do lspci, I'm looking for Network controller, not Ethernet controller?

---

### Post by chili555 on 2010-02-02
> when I do lspci, I'm looking for Network controller, not Ethernet controller?Ethernet is for wired ethernet and Network is for wireless. I was hoping you wouldn't catch my little error along about post #2.

Your wireless gives every sign of being healthy! Let's take a look at:```
iwconfig
dmesg | grep wlan
```Thanks.

---

### Post by JoJerome on 2010-02-02
```

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=14 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

~$ dmesg | grep wlan
[   16.980631] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

Here's a question then if it's healthy; Last laptop I set up Linux on, the drivers I installed came with a handy, pretty, GUI wifi finder. In the absence of that, am I just going to System Settings -> Network Settings? Once wireless is active will available networks show up there?

---

### Post by chili555 on 2010-02-02
> Once wireless is active will available networks show up there?The wireless is all ready to be commanded to connect. The best way is to click the Network Manager icon at the upper right and see if you see networks. See attached. 

Click your network, supply any WEP or WPA details and connect.

---

### Post by JoJerome on 2010-02-10
Hi Chilli - sorry it took me a while. Frustrating intermittent access to 'Net connections...

The only thing called 'Network Manager" is "KNetwork Manager" In the Kmenu->system. When I click on it nothing happens. Kmenu goes away as if it's opening something, but nothing opens.

There is no network manager on the desktop or in the start panel. No app that looks anything remotely like the photo you attached.

When I go to Kmenu->Settings->System Settings->Network Settings it's a whole lot of blank pages. I go to the "Wireless" tab on the menu and my 4 options on the left hand side: Network Connections, Proxy, Connection Preferences, Service Discovery, all give me blank screens and/or blank forms. Nothing indicating that it's finding or even looking for a wifi connection. 

And I've made sure to test this in spots where I should be seeing a half dozen or more routers.


Edit: Isn't there a shell command that will also look for available wireless networks?

---

### Post by chili555 on 2010-02-10
Well, that's a bit odd. I don't know why it won't work correctly. You could try to run it in a terminal so that you get some feedback as to what's going wrong.```
network-manager
``` There are several bugs about knetwork manager and complaints on this forum. Many suggest Wicd as a better alternative. Please see attached. 

Should you wish to try Wicd, you can simply:```
sudo apt-get install wicd
```

---

### Post by JoJerome on 2010-02-10
**THANK YOU!**

WiCd - that looks like the program I used to put on Kubuntu way back when I was using it more often. Will make life way easier. Now that I've got my friend, his cousin, his cousin's cousin, his other friends... all wanting to ditch Windows for Linux. 

Tomorrow I'll try and get the wireless working on that Dell. Thanks again Dr. Chilli!

---

