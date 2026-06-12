---
title: "Wireless Network Connection"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by YMS_1975 on 2009-04-03
Hi,

I just purchased an MSI GX-720 laptop. I'm trying to connect wirelessly but just can't seem to connect to the internet.

I've read a few articles on the forum, but I'm not sure what my starting point should be. Here's what I've picked up from what I've read in these forums : 

I opened up a terminal and typed in "**sudo lshw -C network**" and it generated the following response : 

[B]*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:df:02:ec
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 52:4a:e7:6b:cd:c4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/B]

That's a direct copy & paste, so there won't be any typos.  :p

Now I don't know if it'll help any but I have the following information for my router :

- Password /WPE/WPA Key
- SSID
- Key 1

Can somebody please help?

---

### Post by chili555 on 2009-04-03
This may help: [http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

---

### Post by Tobi-fp on 2009-04-03
You have just found your ethernet card (not your wireless card), anyways, can you find out the exact card you are using? i believe your machine has a broadcom card, and you therefore need to go into hardware drivers to enable it..

---

### Post by YMS_1975 on 2009-04-03
> **chili555 said:**
> This may help: [http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)


Read this article, but isn't that specifically for an Acer?

---

### Post by YMS_1975 on 2009-04-03
> **Tobi-fp said:**
> You have just found your ethernet card (not your wireless card), anyways, can you find out the exact card you are using? i believe your machine has a broadcom card, and you therefore need to go into hardware drivers to enable it..

Please excuse my ignorance, but how would I find out the exact type of wireless card it has? This is the laptop's spec page : 
[http://www.msimobile.com/level3_productpage.aspx?cid=10&id=13](http://www.msimobile.com/level3_productpage.aspx?cid=10&id=13)

Does that help any?     :confused:

OH....I did go into the hardware drivers section, and it says it's enabled (it has a green light/icon next to it indicating it's enabled).

---

### Post by chili555 on 2009-04-03
> **product: AR242x 802.11abg Wireless PCI Express Adapter**You have, indeed, found your wireless adapter. The key element here is *AR242x*.> Read this article, but isn't that specifically for an Acer? As William Shakespeare is reputed to have said, "An AR242x is an AR242x, bye any othre name." The key here is the specific wireless chipset, not the chassis it's bolted into. I suggest you proceed with the tutorial I linked.

---

### Post by YMS_1975 on 2009-04-03
> **chili555 said:**
> You have, indeed, found your wireless adapter. The key element here is *AR242x*.As William Shakespeare is reputed to have said, "An AR242x is an AR242x, bye any othre name." The key here is the specific wireless chipset, not the chassis it's bolted into. I suggest you proceed with the tutorial I linked.

OK...

So I followed your directions very carefully, and here's the verdict. When I rebooted, at first nothing seemed to change but then I went into the Hardware Drivers section where I noticed something had changed.

- Support for 5xxx series of Atheros 802.11 wireless LAN cards. (THIS one is new, it wasn't there before I followed your steps and it's ACTIVATED).
- NVIDIA accelerated graphics driver (Version 173) (deactivated)
- Support for Atheros 802.11 wireless LAN cards (activated).
- NVIDIA accelerated graphics driver (Version 177)(Recommended)(Activated)

But when I try to connect to the internet, it doesn't see a connection there.

---

### Post by chili555 on 2009-04-03
Let's take a look at:```
sudo lshw -C network
```Is your wireless card still showing UNCLAIMED? Does it have a logical name, ath0, perhaps? Let's also see:```
sudo iwlist ath0 scan
```Thanks.

---

### Post by YMS_1975 on 2009-04-04
> **chili555 said:**
> Let's take a look at:```
sudo lshw -C network
```Is your wireless card still showing UNCLAIMED? Does it have a logical name, ath0, perhaps? Let's also see:```
sudo iwlist ath0 scan
```Thanks.

Well,

I ran the two commands and here's what I got.

sudo lshw -C network generated : 

  [B]*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:df:02:ec
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: c6:b1:f0:cf:81:52
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/B]



sudo iwlist ath0 scan generated : 

**atho0     Interface doesn't support scanning.**

Keep in mind that for this scan, I was NOT wired to the internet, as I needed my ethernet cable plugged into my desktop PC to log onto here via my desktop. I don't know if that makes a difference or not, but just didn't want to overlook any detail(s).

So, what do you make of these results?


ON A SIDE NOTE : I don't know if this will make any difference or not, so I think you should know that my router has security measures enabled such as : 

- Disable SSID broadcast
- WEP
- Authentication Type = Open with Cipher = 128 bits - Hex

---

### Post by chili555 on 2009-04-04
Generally, when a device shows as UNCLAIMED, it means that no driver module has attached to it. Let's try to kick-start it:```
sudo modprobe ath5k
```Now let's check to see if it loaded with:```
lsmod | grep ath
```Now, let's see if an interface was created:```
iwconfig
```Please let us know.

---

### Post by polkadotteapot on 2009-04-04
If you've got an atheros card this should work [http://www.aspireonekernel.com/#Downloads](http://www.aspireonekernel.com/#Downloads)

I'm really untecnical and I managed it, just.

---

### Post by YMS_1975 on 2009-04-04
> **chili555 said:**
> Generally, when a device shows as UNCLAIMED, it means that no driver module has attached to it. Let's try to kick-start it:```
sudo modprobe ath5k
```Now let's check to see if it loaded with:```
lsmod | grep ath
```Now, let's see if an interface was created:```
iwconfig
```Please let us know.

Ok, here are the results. I'm starting to worry that it might be a hardware problem. As I type this I'm installing a copy of Vista Ultimate just to make sure this is working as it should.

What do you think of the results?

[B]sudo modprobe ath5k
lsmod |grep ath
ath5k                 126596  0 
lbm_cw_mac80211       247744  1 ath5k
lbm_cw_cfg80211        52912  2 ath5k,lbm_cw_mac80211
led_class              13192  1 ath5k
yousaf@yousaf-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


[/B]

---

### Post by chili555 on 2009-04-04
> wlan0 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=27 dBm etc.Looks like you have it now, although I'd be happier if your interface were ath0 instead of wlan0. Can you click the Network Manager icon (upper right), see your network, tell it to connect and give your WEP 26-character key and connect?

---

### Post by YMS_1975 on 2009-04-05
> **chili555 said:**
> Looks like you have it now, although I'd be happier if your interface were ath0 instead of wlan0. Can you click the Network Manager icon (upper right), see your network, tell it to connect and give your WEP 26-character key and connect?

Well,

The whole re-installing Vista concept failed (miserably). I have a legit OEM copy but for the sake of this install (on my laptop) I tried installing a not-so legit copy and let's just say it made a good mess of everything (serves me well for trying that). Anyways, I did a format and re-installed Ubuntu on my laptop.

I re-followed the steps as outlined and when I did another "**sudo lshw -C network**" here are the results :

  [B]*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:df:02:ec
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:43:07:c8:9d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 76:29:e1:6d:f5:bd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



[/B]

So....in a nutshell, I'm still SOL with the whole wifi experience. It works fine when I'm hard-wired into the network. When I **right-click** on the network icon, here are my options : 

- Enable Networking (checked)
- Enable Wireless (checked)
- Connection Information (grayed out)
- Edit Connections...
- About

When I **left-click** on the network icon, here are my options : 

- Wired Network (grayed out)
- Auto eth0 (grayed out) [this option has a circle preceding the option itself indicating it's selected]
- Wireless Networks (grayed out)
- VPN Connections > (has a sub menu)
                    - Sub menu # 1 : Configure VPN...
                    - Sub menu # 2 : Disconnect VPN... (grayed out)
- Connect to Hidden Wireless Network...
- Create New Wireless Network...

At this point I select "Connect to Hidden Wirless Network..." and am prompted to enter in the Network Name (which is my SSID as outlined in the router settings), I select "WEP 40/128-bit Key" security and enter in the 26 digit encryption key ACCURATELY. My WEP Index is untouched at the default of 1 and my Authentication is "Open System" as is outlined in the router settings.

When I click "Connect" (once the above parameters are met) the network icon at the top changes to 2 little green lights/icons and a little blue wave circles around the 2 lights/icons indicating it's attempting to authenticate the connection. After about.....45 seconds to 1 minute it fails and gives the error message : DISCONNECTED. The network connection has been disconnected.

*Deep Sigh* This is (what's the word I'm looking for?) challenging. I know I've spewed a lot of information in this thread. I've only done so because I'm afraid that I might overlook something and not realize that it may be reason for all my connectivity woes. In that spirit, the router I'm using is [D-Link's VWR]("http://www.vonage.ca/help.php?article=1164&category=128&nav="), as I'm a Vonage Canada subscriber. Do you think that might be the problem? The router? Also I was looking over the [Atheros]("http://www.atheros.com") website and couldn't find my AR242x 802.11abg Wireless PCI Express Adapter card. Does that mean the card that's in my laptop is outdated? Sorry if my questions seem off-base. I'm just trying to figure out WHY this is not working.

So....what do you think?

---

### Post by AdamShumpisxXx on 2009-04-05
This may sound stupid but have you tried disconnecting the wire, LEFT clicking the NetworkManager Applet, and then seeing if it now displays your wireless networks? A friend of mine who I just switched over to Ubuntu on his laptop had a similar problem and this suggestion helped him. This is only applicable if your "UNCLAIMED" problem no longer persists which by looking at your most recent "sudo lshw -C network" terminal read-out it seems to have been solved. Good luck!

---

### Post by YMS_1975 on 2009-04-05
> **AdamShumpisxXx said:**
> This may sound stupid but have you tried disconnecting the wire, LEFT clicking the NetworkManager Applet, and then seeing if it now displays your wireless networks? A friend of mine who I just switched over to Ubuntu on his laptop had a similar problem and this suggestion helped him. This is only applicable if your "UNCLAIMED" problem no longer persists which by looking at your most recent "sudo lshw -C network" terminal read-out it seems to have been solved. Good luck!

I don't think your ideology is stupid; a new perspective might be what I need. But, to answer your question : the network cable is in fact disconnected.

I just wanted to see if it would work if it was hard wired (which it does). Then I disconnected it, and tried the wireless option and that failed. :confused:

---

### Post by YMS_1975 on 2009-04-05
> **polkadotteapot said:**
> If you've got an atheros card this should work [http://www.aspireonekernel.com/#Downloads](http://www.aspireonekernel.com/#Downloads)

I'm really untecnical and I managed it, just.


Before I download anything and/or make any changes, I'd like a little bit more clarification. The link you provided has 4 possible downloads.

Do I need to download & install all 4 files or just the MadWiFi modules?

---

### Post by AdamShumpisxXx on 2009-04-05
OK, just wanted to cover the easy bases. Some people are so used to RIGHT clicking icons they never check to LEFT click them. I noticed that since your reinstall of Ubuntu your wireless card seems to be properly detected without the previous "UNCLAIMED" error. I bet if you did a "iwconfig" now in terminal it would post a read-out that you indeed have a wireless device. Problem is perhaps the default driver installed with Ubuntu seems to not "speak" with your wireless card's chipset properly in which case you should first search the internet to find your exact chipset for that card and see if there is a native linux driver available. If not, you'll have to use ndiswrapper to install the Windows driver for your wireless card. Basically what I suggest is:

1) Uninstall current wireless driver (may or may not be necessary).
2) Check for native Linux driver (wireless chipset).
2A) If a proper native linux driver is available then install that.
2B) If no proper native Linux driver is available...
3) Install ndiswrapper.
4) Use ndiswrapper to install the Windows based driver.

These steps are your best option as they have led me to have a perfectly working wireless configuration every time. I cannot however give you a step by step myself because every time I have gone to do such a thing I have had to look up specific tutorials for each wireless card. These steps though are exactly what I go through every time so keeping them in mind will help you solve your problem.

Here is some documentation on ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Here is also a tutorial I BELIEVE to be pertinent to your situation and may very well be an exact tutorial to install your wireless card properly (this solution does not require ndiswrapper and I believe it is a native Linux driver install):
[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

Best of luck. I hope you succeed.

---

### Post by AdamShumpisxXx on 2009-04-05
I almost forgot to mention...The reason I believe the tutorial I linked you to is exactly what you need is because it describes installing a "AR242x" wireless card which is exactly what you have judging from your "sudo lshw -C network" terminal read-out. Again...good luck!

:KS

---

### Post by YMS_1975 on 2009-04-07
Unfortunately,

None of the above seems to be working for me which really sucks. :mad:  I would like to take this opportunity to thank you all (especially my good friend "chili555") for your valiant efforts in trying to fix this problem.

After hours (and trust me, it's been hours) of fudging around with Ubuntu and system settings, I've decided to buy a PCMCIA wireless adapter card. Now I know there have been other **Which PCMCIA card is Ubuntu/Linux friendly?** threads, so I won't go there.

I have however, decided to go with the "[Ubiquiti Networks Inc. - SR71]("http://ubnt.com/products/sr71c.php")" PCMCIA cards.  :guitar:

---

