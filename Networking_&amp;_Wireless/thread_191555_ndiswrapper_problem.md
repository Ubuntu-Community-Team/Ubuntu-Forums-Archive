---
title: "ndiswrapper problem"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by beniwtv on 2006-06-07
Hi.

I've installed a Conceptronic USB 54Mbit wireless adaptor USB2. I have tried to compile the native driver rtx00, but it doesn't work as it throws segmentation faults in the kernel. ](*,) .

So, I've decided to try ndiswrapper. And it works, at least for kernel 2.6.16-20. Now, with the new 2.6.16-23 kernel, it works too but when I am connected to the network, sometimes internet goes away. Gnome still displays the green 100% coverage icon. But I can't send or recive data. Router and AP are OK, as my collegue connects well, and in wind***s it works, too. Then, I have to disconnect and connect the wireless adaptor again to make it work again.

I get this mesage in the kernel log:

usb 1-2: new high speed USB device using ehci_hcd and address 4
[4296310.203000] ndiswrapper: driver rt73 (Ralink,11/03/2005, 1.00.01.0000) load ed
[4296311.540000] wlan0: vendor: 'IEEE 802.11g Wireless Card.'
[4296311.540000] wlan0: ndiswrapper ethernet device 00:80:5a:38:67:aa using driver rt73, 14B2:3C22.F.conf
[4296311.542000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WP A2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[4296322.739000] wlan0: no IPv6 routers present
[4296436.426000] ndiswrapper (wrap_reset_pipe:789): resetting pipe 2 failed: -71

What could be wrong? I wouldn't like to compile another kernel as this one works just amazing (despite of the wlan)! Nor I wouldn't like to downgrade it.

Thanks for your help.

---

### Post by pelle.k on 2006-06-08
Wait for an update i guess. My belkin make my computer freeze completely ATM, so you're lucky you can make it work again that easiely...
Or better yet, let them finish the rt2x00.

---

### Post by beniwtv on 2006-06-08
Yeah,

That's what I will do. 8) And problably I'll try to compile a new ndiswrapper version and/or rtx200 driver.

---

### Post by ComplexNumber on 2006-06-08
> **beniwtv]Hi.

I've installed a Conceptronic USB 54Mbit wireless adaptor USB2. I have tried to compile the native driver rtx00, but it doesn't work as it throws segmentation faults in the kernel. ](*,) .

So, I've decided to try ndiswrapper. And it works, at least for kernel 2.6.16-20. Now, with the new 2.6.16-23 kernel, it works too but when I am connected to the network, sometimes internet goes away. Gnome still displays the green 100% coverage icon. But I can't send or recive data. Router and AP are OK, as my collegue connects well, and in wind***s it works, too. Then, I have to disconnect and connect the wireless adaptor again to make it work again.

I get this mesage in the kernel log:

usb 1-2: new high speed USB device using ehci_hcd and address 4
[4296310.203000] ndiswrapper: driver rt73 (Ralink,11/03/2005, 1.00.01.0000) load ed
[4296311.540000] wlan0: vendor: 'IEEE 802.11g Wireless Card.'
[4296311.540000] wlan0: ndiswrapper ethernet device 00:80:5a:38:67:aa using driver rt73, 14B2:3C22.F.conf
[4296311.542000] wlan0: encryption modes supported: WEP said:**
>  wlan0: no IPv6 routers present
[4296436.426000] ndiswrapper (wrap_reset_pipe:789): resetting pipe 2 failed: -71

What could be wrong? I wouldn't like to compile another kernel as this one works just amazing (despite of the wlan)! Nor I wouldn't like to downgrade it.

Thanks for your help. i don't think you need the update. perhaps you just need to go into firefox and type 'about:config' in the address bar, do a search for v6, then set it to true. try it and let me know if you can successfully use the internet.

---

### Post by beniwtv on 2006-06-08
The problem isn't firefox. I can't even do a ping to google or something. Other programs also connect. In fact, it's a ndiswrapper problem. :-({|=

---

### Post by ComplexNumber on 2006-06-08
[quote=beniwtv]The problem isn't firefox. I can't even do a ping to google or something. Other programs also connect. In fact, it's a ndiswrapper problem. :-({|=[/quote] in that case, you're right. but you will need to do that in firefox anyway when you reach that stage. i thought that you were more advanced in the process than you actually are.
what happens when you type in sudo modprobe ndiswrapper', then 'ndiswrapper ra0 scan'?
also, what is the output of typing 'dmesg'?

---

### Post by beniwtv on 2006-06-08
The output of dmesg is:


```
usb 1-2: new high speed USB device using ehci_hcd and address 4
[4296310.203000] ndiswrapper: driver rt73 (Ralink,11/03/2005, 1.00.01.0000) load ed
[4296311.540000] wlan0: vendor: 'IEEE 802.11g Wireless Card.'
[4296311.540000] wlan0: ndiswrapper ethernet device 00:80:5a:38:67:aa using driver rt73, 14B2:3C22.F.conf
[4296311.542000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WP A2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[4296322.739000] wlan0: no IPv6 routers present
[4296436.426000] ndiswrapper (wrap_reset_pipe:789): resetting pipe 2 failed: -71
```

My interface is recognized as wlan0. When I type 'modprobe ndiswrapper' I get:

```
[4296310.203000] ndiswrapper: driver rt73 (Ralink,11/03/2005, 1.00.01.0000) load ed
[4296311.540000] wlan0: vendor: 'IEEE 802.11g Wireless Card.'
[4296311.540000] wlan0: ndiswrapper ethernet device 00:80:5a:38:67:aa using driver rt73, 14B2:3C22.F.conf
[4296311.542000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WP A2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[4296322.739000] wlan0: no IPv6 routers present
```

When I type 'ndiswrapper wlan0 scan(ning)' I get a list of networks, 2 in my case: My own (100% signal) and another with about 10%.

Hope that this helps to find out what's wrong.

---

### Post by ComplexNumber on 2006-06-08
they seem ok (AFAIK). how long does it stay connected for, usually?

btw bear in mind that i'm a total noob when it comes to this. its just that i, too, have recently gone through the pain of trying to get my wireless card up and running by reading forums etc. so its still quite fresh in my mind.

---

### Post by beniwtv on 2006-06-08
Normally I stay connected for 5 to 10 minutes. Sometimes up to one hour. Or, sometimes (very low chance) I stay connected as long as I want.

---

### Post by ComplexNumber on 2006-06-08
[quote=beniwtv]Normally I stay connected for 5 to 10 minutes. Sometimes up to one hour. Or, sometimes (very low chance) I stay connected as long as I want.[/quote] so is the problem just that you can't ping? also, what happens when you fire up firefox?

---

### Post by beniwtv on 2006-06-08
When I fire up firefox, it just stays at looking up [www.google.com](www.google.com) (or any other page). All other programs as well. 

Thought something with DNS, but entering the IP doesn't help neither. I can't even ping the AP or router.


Note that this doesn't happens in wind***s, so no hardware/router/ap config issue.

---

### Post by ComplexNumber on 2006-06-08
whats the contents of /etc/resolv.conf? it should have your routers IP.

---

### Post by beniwtv on 2006-06-08
Yes, it shows the router's IP. Additionally, I'm not using DHCP. I assigned the IP and DNS (router) myself. However, I don't think this is related.

---

### Post by pelle.k on 2006-06-08
I just installed ndiswrapper 1.17 from source. So far so good, but, knock on wood....
I'll get back to ya in a few hours...

---

### Post by beniwtv on 2006-06-09
pelle.k: Did you have success? Works the wifi connection now?


I'll try to install ndiswrapper from source, too. But I won't have time to do it until next week. I'll report back...

---

### Post by pelle.k on 2006-06-09
I can happily report that i've been online since i wrote that post, while downloading stuff with bittorrent, and so far everything is A-OK! :)
So i must conclude it really is working....

Just to clarify. My usb dongle is a Belkin F5D7050 v3000.
I use the driver which came on the driver CD (version 1.00.00.0000 - 08/02/2005).

```
pelle@pelle1:~$ lsusb | grep Belkin
Bus 005 Device 005: ID 050d:705a Belkin Components

```
So this is a 705a id = rt73 chipset

---

### Post by beniwtv on 2006-06-09
Great! Good work!

I'll try to compile ndiswrapper next week. Maybe I'll able to stay connected then....

Your belkin is an rt73? hm. like mine too. So maybe the upgrade helps...

---

### Post by beniwtv on 2006-06-21
Quick update here

I've updated the kernel. Now is kernel 2.6.15-25. And it seems to work all ok now.

---

