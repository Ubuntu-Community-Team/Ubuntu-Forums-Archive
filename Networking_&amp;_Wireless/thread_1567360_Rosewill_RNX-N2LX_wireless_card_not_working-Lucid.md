---
title: "Rosewill RNX-N2LX wireless card not working-Lucid"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by Harri_s on 2010-09-03
Hello,

I cannot get my wireless card to work.  I have been using Ubuntu for over a year, relying on an old, cheap ASUS adapter that gets poor signal strength, but has out of the box Ubuntu support.

I decided to upgrade to the Rosewill RNX-N2LX because it also claimed out of the box support. Chipset Realtek 819su.

However, when I plug it in, its blue light flashes for a split second and then goes dead.  It is not recognized by Ubuntu as a wireless card, it shows up as:  "Realtek Semiconductor Corp." when I type lsusb and nothing shows up when I type iwconfig.  I don't have a wired connection, so I am using my old wireless adapter if there are specific terminal commands I should post, let me know and I can disconnect and then post them later.

I have not found any support as to how to make this card linux compatible (I am using Lucid 64 bit).

There is a linux driver on the website, I tried to follow instructions, but I could not get it to "make-" my computer would freeze up.  I also tried ndiswrapper to no avail. 
  
I also tried adding these 2 commands to the blacklist per a newegg review:

blacklist rt2800usb
blacklist rt2870usb

[http://www.newegg.com/Product/Product.aspx?Item=33-166-027&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=ubuntu&Page=2#scrollFullInfo]("http://www.newegg.com/Product/Product.aspx?Item=33-166-027&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=ubuntu&Page=2#scrollFullInfo")


These reviews are for an older version of the card, but I thought that they would still apply, or more naively, that rosewill has cleared up any compatibility issues with Ubuntu.

 Any help would be greatly appreciated.

Edit: The card itself is not defective, it works fine under XP.

---

### Post by Harri_s on 2010-09-03
Here is the dmesg output:

```
[ 2339.018832] wlan0: associated
[ 2339.042381] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2346.959889] bridge-wlan0: disabling the bridge
[ 2347.001295] bridge-wlan0: down
[ 2347.001303] bridge-wlan0: detached
[ 2347.001354] /dev/vmnet: open called by PID 1181 (vmnet-bridge)
[ 2347.001364] /dev/vmnet: hub 0 does not exist, allocating memory.
[ 2347.001388] /dev/vmnet: port on hub 0 successfully opened
[ 2347.001398] bridge-wlan0: is a Wireless Adapter
[ 2347.001402] bridge-wlan0: up
[ 2347.001406] bridge-wlan0: attached
[ 2349.561378] wlan0: no IPv6 routers present
[ 2686.453089] usb 1-1: USB disconnect, address 8

```

---

### Post by shoeheight on 2011-01-16
Same problem here, I am still searching for an answer. But so far no luck.
EDITED:
According to the documentation:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
there is no help....so....
This was my lsusb
	
ID 0bda:8174 Realtek Semiconductor Corp

So, after googling around, there appears to be an answer here:
wiki.debian.org/rtl819x#r8192susb

But after:
sudo modprobe r8192s_usb

There was no change, the wireless adapter still does nothing. What am I missing?

---

### Post by shoeheight on 2011-01-16
ok, I tried something new.

I found the Ralink driver:
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
aka - "RT2870USB(RT2870/RT2770)"

I installed it, no luck.
So after searching some more, I found this link:
[http://ubuntuforums.org/showthread.php?t=960642](http://ubuntuforums.org/showthread.php?t=960642)
It appears that by changing a few "n"'s to "y"'s as directed (in directions#9) it makes all the difference. After fretting for a while if I needed to "rmmod" the prior install before modifying it for a second time, I decided against it and simply followed the directions in the link posted above. It appeared to install with no errors. Unfortunately it made no difference.

I assumed that after installing this there would be a change to my "proprietary drivers", but there is none.

dmseg gave me this response:
```
[  429.349298] usb 1-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[  581.255907] usb 2-7: USB disconnect, address 3
[  600.474460] usb 2-7: new high speed USB device using ehci_hcd and address 4
[  600.629147] usb 2-7: configuration #1 chosen from 1 choice
[  707.058389] usb 2-7: USB disconnect, address 4
[  723.564515] usb 2-1: new high speed USB device using ehci_hcd and address 5
[  723.718005] usb 2-1: configuration #1 chosen from 1 choice

```

Obviously other than having two USB's with this Network interface, there isn't too much info here....

---

### Post by shoeheight on 2011-01-24
FYI....
I have given up. It doesn't work, I am using an older one I had lying around.

---

### Post by shoeheight on 2011-05-13
Card now works on 11.04 install

---

### Post by jacobie on 2012-01-03
Hi Shoeheight,
Were you able to install successfully out of box with 11.04?

---

