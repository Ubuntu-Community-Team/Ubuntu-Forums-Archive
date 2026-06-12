---
title: "Cannot connect after changing MAC address"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by orangecakez on 2009-03-14
I have an Atheros chip based wireless card, so I have wifi0 and ath0 in my ifconfig.

It connects to my wireless network fine, but when I do:

```
sudo /etc/init.d/networking stop
sudo ifconfig wifi0 down
sudo ifconfig ath0 down
sudo macchanger -r wifi0
sudo macchanger -r ath0
sudo ifconfig wifi0 up
sudo ifconfig ath0 up
sudo /etc/init.d/networking start
```

It does not connect to my wireless network anymore, no matter how long I wait or try.
Even if I change the MAC address *back to the original* again with the same process as above, it still does not connect!

But if I reboot, it goes back to the original MAC and it connects fine again.

If it makes any difference, on Windows if I change the MAC, I still connect fine.

---

### Post by fixitdude on 2009-03-14
I'm thinking you could find out where the networking starts at boot and do that before it boots the first time.

It's possible that the macchanger program is messed up, have you confirmed with ifconfig that it actually changes the mac? And why do you change the mac on both interfaces? Is it possible that it tries to change the mac on both to the same one?

---

### Post by orangecakez on 2009-03-15
Yea, ifconfig after shows that the MACs have changed.

I change both because I'm not sure which one it uses, so just in case I do both. If I only change one, the other stays the same (verified with ifconfig/iwconfig) so I just change both in case

---

### Post by fixitdude on 2009-03-15
The wireless side is going to use the wireless MAC. Try it with just one changed and see what happens.

---

### Post by lisati on 2009-03-15
Maybe something has changed at the router end - the Thomson router I currently use has an option that lets me choose whether to allow new Wifi MAC addresses automatically or only when I tell it to scan for new hardware.

---

### Post by fixitdude on 2009-03-15
But you said you can do it in windows.

Guess you could turn the router off and back on after switching.

And windows probably doesn't change both interface's MAC.

---

### Post by orangecakez on 2009-03-15
> **fixitdude said:**
> The wireless side is going to use the wireless MAC. Try it with just one changed and see what happens.

Both wifi0 and ath0 are wireless, so which one do I change?

> **fixitdude said:**
> But you said you can do it in windows.

Guess you could turn the router off and back on after switching.

And windows probably doesn't change both interface's MAC.

Rebooting the router doesn't do anything. I still can't connect :(

---

### Post by Sente on 2009-05-01
I'm having the same issue that you are. I'm using a Broadcom 4311. I 've tried connecting via wpa_supplicant and gnome's network manager, but fail to connect either way. I did not have this trouble under 8.10...but did have the same issue under 8.10 with a ralink card.

I hope someone can shed light on this. Kind if a nice feature that we're out of here!

---

### Post by Pax_Harmonica on 2011-02-14
I experience the same problem. I usually change my MAC through ifconfig

sudo ifconfig INTERFACE down
sudo ifconfig INTERFACE hw ether XX:XX:XX:XX:XX:XX
sudo ifconfig INTERFACE up

I am consistently dropped from the network and unable to reconnect unless I reboot. I have changed my MAC *before* making the initial connection to a network and got it to work (most of the time, anyway). I know that I am overlooking something important here. I assume there is still something that expects your computer to have the old MAC.

for reference I'm using:
ASUS EEE PC
AR9285 Wifi card, Ath9K drivers
Ubuntu 10.04

---

### Post by aaronp1990 on 2011-07-11
Very interesting.
I observed this problem in my computer.
I changed mac address in terminal successfully then try to connect wireless router and failed. After notification of failed connection I wrote ifconfig in terminal I see mac address was reset to original. Why Network Manager changed it back?

Here detailed screenshots on website. Website is very slow loading.
[http://problemwithmacaddressinubuntu.yolasite.com/](http://problemwithmacaddressinubuntu.yolasite.com/)

---

### Post by Objekt on 2011-08-20
I have a similar problem to the OP's.  Atheros AR5700EG wireless NIC in a netbook running Ubuntu 10.04, and it will not connect to my router (Netgear WNR3500) with anything but the original MAC.

Interestingly, it has no trouble making an ad-hoc connection to another computer's wireless device, which is also using a non-default MAC address.

I have the same issue in Windows XP: the Atheros wireless driver has a field for changing the MAC address, but if I do, it cannot connect to my wireless LAN, no matter how many times I reboot or power cycle either the netbook or the router.

This is very frustrating.  I wanted to do some wireless security testing, but it's sort of impossible when I can't pose one of my computers as a wireless "threat."

---

### Post by vst0rm on 2011-09-17
hey I had the same problem I change my MAC and after this nothing works anymore. Have to reload the kernel module =(   Then I realized when a sniffer is running everything starts working. Sniffer == Promiscuous mode =)  ```
 sudo ifconfig eth0 promisc 
```I know this is not a good solution but at least it works.Tested under debian squeeze running on virtualbox.
Hope this helps someone and sorry for my english ...

---

### Post by Objekt on 2011-09-17
Not really sure WHY it started working, but now it does.  I can change the netbook's MAC address at will, using the proper ifconfig commands in Terminal.  And then connect with the new MAC.

It could be that the difference consists in doing things via Terminal, vs. trying to use the NetworkManager GUI.

So now that changing MACs works, I tried changing the netbook's MAC address to that of a wireless NIC belonging to another computer on the network.  The results were quite educational.

---

