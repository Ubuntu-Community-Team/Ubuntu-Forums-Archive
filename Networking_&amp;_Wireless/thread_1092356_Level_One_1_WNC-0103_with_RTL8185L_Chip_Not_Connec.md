---
title: "Level One 1 WNC-0103 with RTL8185L Chip Not Connecting to Access Point"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by physeetcosmo on 2009-03-10
Anyone who can help,

I have searched the web and cannot determine a fix. Before I go out and purchase a new card to replace this WNC-0301 with a Realtek RTL8185L wifi chip.

I am on a Dell Inspiron Tower, using this card in one of the 32 bit PCI slots. When I run the card in Windows it is somewhat temperamental as only the 'magic' software interface will make this card work (although just letting Windows try and run the card and failing doesn't surprise me :]).

I am running Ubuntu Intrepid, and upon running:
```
$ lspci
```
I get a line at the very bottom listing this PCI card and recognizing it as an RTL8185L chipset. 

In the GUI (I am running Gnome), I can scan for Wifi access points (and being in Downtown Denver, there are a ton!) but the signal strength isn't right. The reason I know is I am running Ubuntu Intrepid as well on an Asus Netbook right next to my tower surfing the web on it. The signal strength for the router is 100% at ~15dBm. Thus I know the WNC-0301 isn't decoding something right, and needs a proper driver.

There is no listing in: /etc/modprobe.d/blacklist for a current driver that I can find, but I have tried entering the line:
```
blacklist rtl8185
```
with no avail.
Just to cover all bases, I have checked my router and turned off all security features (MAC Filtering, IP DHCP Pool Limit, WPA, WEP...etc) for when I was testing the card.

I have read that a ton of people have had issues with this card before, but that was at least a year ago and they didn't have the same chipset.

NDISWrapper won't work as the 'Driver' from [_Level1_]("http://download.level1.com/level1/driver/WNC-0301(XP-U2.4.16.314_XP-D5.1097.201.2007_Vista-U1.15.108.60_Vista-D6.1099.312.2007_HW-6)_2007-12-11.zip"), is only a .exe and NDISWrapper wants a ton of .inf and .bin (if I remember right).

Any other thoughts? Guess I could right my own driver....oh wait, Realtek doesn't have an opensource program... :]

---

### Post by Brain-free on 2009-03-20
Hi physeetcosmo.

I've been having exactly the same problem as you in Intrepid. The signal strength was never above 15% and my IP - the 192.1****** one - would randomly change. I do not have anything to suggest as far as the native driver is concerned, but maybe I can help you with getting the necessary files for the ndiswrapper process.

There are two easy ways to get them:

1) The first and safest one is, if you're dual-booting with Ubuntu and Windows XP on the same machine, you can copy the "Driver" folder from "Program Files" - which includes the necessary .inf to make ndiswrapper work - and paste it in your Ubuntu partition. 

2) The second one is to download the files from [Realtek's site]("http://www.realtek.com./downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L") and from there use the ndiswrapper.

Instructions on how to use ndiswrapper can be found [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

(Hopefully, I've posted this too late and you have already bought a new card cause this one, is a f*%@$ nightmare man...)

---

