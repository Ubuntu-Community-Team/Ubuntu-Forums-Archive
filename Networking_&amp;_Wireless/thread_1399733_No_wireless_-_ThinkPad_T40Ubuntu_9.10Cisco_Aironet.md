---
title: "No wireless - ThinkPad T40/Ubuntu 9.10/Cisco Aironet Wireless /ThinkPad 802 11a/b/g"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by 50GreenDodge on 2010-02-06
No wireless - ThinkPad T40/Ubuntu 9.10/Cisco Aironet Wireless /ThinkPad 802 11a/b/g Wireless LAN Mini PCI Adapter

I just installed 9.10 yesterday, after having several months of bliss with 9.04 (and the previous distro, I think, 8.10.)

The wireless connection was so easy the first time that I forgot what I even did. So i figure there is something off with 9.10.  What, I don't know.

I'm also trying to get a Verizon MiFi 2200 access point working, but that's another story.  

First things first. 

I selected the "Network Connections" and added a wireless connection.  

I filled in the SSID:  (Name of my Network)
Mode: Choice of Infrastructure / Ad Hoc.  I chose Infrastructure 
I left BSSID blank
MAC address: I entered the MAC address of the ThinkPad
MTU: I left it as 'automatic'

I didn't touch the IPv4 or IPv6 tabs

Wireless Security:
WEP 40/128 bit key
I entered the key from my router pages (Netgear N router)
WEP Index: 1 (default)
Authentication: Open system/shared key I chose Open System.

I'm hoping I've got these settings ALL wrong, and a helpful hint or 2 will get me back to where I once belonged.  

The only reason I wiped my drive and installed 9.10 is I was trying to install Windoz XP in a dual boot so I might have better luck using the MiFi 2200. But the Product Number I had was for some reason not valid.

All in all, a rotten Friday. 

Thanks to all for assistance.

50GreenDodge (aka Jack in Phoenix)

---

### Post by northd_tech on 2010-02-06
Hi 50GD (I used to live in PHX myself).

Can you post the results here when you run the following commands in a terminal?

```
lspci 

lsmod

uname -a

sudo lshw -C network

ifconfig

iwconfig
```

---

### Post by chili555 on 2010-02-06
> MAC address: I entered the MAC address of the ThinkPadI think it wants the MAC address of the router, but it's only really useful if you have several routers/access points all with the same ESSID and you want to force an association with one particular device, such as in a business. It has no real purpose in a home network. You can safely leave it blank.

If you click on the Network Manager icon, isn't all this taken care of for you automagically?

---

### Post by 50GreenDodge on 2010-02-06
Network Manager.  Is that the correct name?  I only have an item in the popup 'Preferences' menu that lets me select 'Network Connections' 

What I'm getting at is: am I missing an applet that would make life easier?

Thanks.

---

### Post by chili555 on 2010-02-06
Evidently you are. It's at the top right of your desktop and looks like two little computer monitors with a red **[SIZE="3"][COLOR="Red"]X[/COLOR][/SIZE]** when it's not connected. When you click it, it will show available networks and you can click one and, if you have the WEP or WPA details, connect.

Here is mine, which I have relocated to the bottom because it suits my old eyes better. As you can see, I am connected to GBR1. The little yellow padlock tells us that it's encrypted.

If it's missing altogether, please see:  [http://ubuntuforums.org/showthread.php?t=1311790](http://ubuntuforums.org/showthread.php?t=1311790)

---

### Post by Sylvain Prévost on 2010-02-06
I am having the same problem:
I installed this evening Ubuntu 9.10 32bits on my IBM Thinkpad T40p (2373-G1G)
I am using the Wireless network icon to choose the network (the SSID is not hidden) and give my password. There is no other option (the wireless security list only contains one entry: "WPA & WPA2 Personal).

I am not making a mistake with the password (checked) and the wireless is OK (currently 2 other computers seeing and using it).

I am normally using WPA-TKIP (pre-shared key). My router can also use WPA2 (AES), but selecting this option on the router did not help for my laptop.

I believe that previously I had to install a proprietary driver to have it working. With this 9.10 version I am not getting any suggestion for proprietary driver (even not the ATI card, but I think open source drivers for these are now essentially OK? even though I do have the feeling that the display responsiveness is slower that it used to be, and connecting a full HD screen on hte VGA port does not work so far, but this I should try again before to report).

The commands suggested earlier produce a lot of information; what we should we look at?
Among many other things, "sudo lshw -C network" gives that:
       product: AR5211 802.11ab NIC
       vendor: Atheros Communications Inc.
       physical id: 2

Thanks in advance for the help!

---

### Post by chili555 on 2010-02-06
@Sylvain

Please start a new thread referencing T40 and Atheros. You are likely to get a better response than buried in a Cisco thread. I'll jump in as soon as I see it. I may even answer it on my T40/IPW2915!

---

### Post by 50GreenDodge on 2010-02-08
Thanks for your help. I took a break for a day and a night and after the Super Bowl, I found the network stuff with your advice and now I'm hooked up.  A-gain.

Hope your team won.  I didn't have a dog in the fight. I'm a Giants fan.

---

