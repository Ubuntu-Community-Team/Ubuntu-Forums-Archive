---
title: "Change primary network interface &amp; set up static IP"
date: 2011-03-07
forum: Networking &amp; Wireless
---

### Post by Jonathan B on 2011-03-07
Hi,

I am new to running a server and I am having great difficulty in changing the primary network interface from an ethernet connection that uses DHCP to get it's IP address to my wireless network card and assign my own static IP instead (I just want to set up a simple FTP server for home use).

I've done a lot of searching but the problem is I'm not familiar with a lot of the terminology which limits my ability to narrow down my searches in Google and here.

I've tried editing /etc/network/interfaces and changing the eth0 to wlan0 and restarting network but doesn't work and the guides I've found online don't fix my issue.

If anyone can point me in the right direction I would appreciate it. You don't need to explain step by step as I'd prefer to learn as I go along but at this point I'm getting a little frustrated :\

---

### Post by matt_symes on 2011-03-07
Hi

Edit your /etc/network/interfaces file to look some thing like

```
auto eth0
iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1
```

You might want to add a broadcast address as well. Then restart neworking

```
sudo /etc/init.d/networking restart
```

Kind regards

---

### Post by Jonathan B on 2011-03-07
Yeah, that's what I've done but no go.

I have also just realised that that's probably because I'm not associated with my wireless router. 

Can I trouble you to give me a heads up on that one as well?

---

### Post by matt_symes on 2011-03-07
Hi

Something like this in your /etc/network/interfaces file. Using WPA encryption

auto wlan0
iface wlan0 inet static
        address 192.168.1.99
        gateway 192.168.1.1
        dns-nameservers 192.168.1.1
        netmask 255.255.255.0
        wpa-ssid dd-wrt
        wpa-key-mgmt WPA-PSK
        wpa-psk Key_goes_here

Change as required.

Kind regards

---

### Post by Jonathan B on 2011-03-07
I appreciate the help matt_symes but I'm still no closer to getting it connected to the router and online.

This is what I have and I've double checked it for typos and am still stuck :\ Sorry to trouble you further with something I'm guessing is simple for most people.

```

auto wlan0
iface wlan0 inet static
address 192.168.1.99
gateway 192.168.1.1
dns-nameservers 192.168.1.1
netmask 255.255.255.0
wpa-ssid jonsinternet
wpa-key-mgmt WPA-PSK
wpa-psk thisismywifipassword

```

---

### Post by matt_symes on 2011-03-07
Hi

> **Jonathan B said:**
> I appreciate the help matt_symes but I'm still no closer to getting it connected to the router and online.

This is what I have and I've double checked it for typos and am still stuck :\ Sorry to trouble you further with something I'm guessing is simple for most people.

```

auto wlan0
iface wlan0 inet static
address 192.168.1.99
gateway 192.168.1.1
dns-nameservers 192.168.1.1
netmask 255.255.255.0
wpa-ssid jonsinternet
wpa-key-mgmt WPA-PSK
wpa-psk thisismywifipassword

```

That looks alright to me. It's pretty much the same setup as i have on my server.

Open a terminal and type

```
ifconfig
```

Do you have a valid IP address ?

Can you see the router with

```
nm-tool
sudo iwlist scan
```

Can you ping your router ?

```
ping -c 4 192.168.1.1
```

What is the output of

```
iwconfig
```

Is the interface up ?

```
sudo ifconfig wlan0 up
```

Have you configured the router correctly and can you access it in a browser ?

Is networking up and running

```
sudo /etc/init.d/networking restart
```

Here is a how to

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

Kind regards

---

### Post by Jonathan B on 2011-03-07
> **matt_symes said:**
> Hi

```
ifconfig
```Do you have a valid IP address ?


Yes, I do


> **matt_symes said:**
> 
Can you see the router with

```
nm-tool
sudo iwlist scan
```Can you ping your router ?

Yes, I can see mine including other ones.
> **matt_symes said:**
> 
```
ping -c 4 192.168.1.1
```What is the output of

Destination Host Unreachable

> **matt_symes said:**
> 
```
iwconfig
```Is the interface up ?

```
sudo ifconfig wlan0 up
```Have you configured the router correctly and can you access it in a browser ?


Yes to both. 

> **matt_symes said:**
> 
Is networking up and running

```
sudo /etc/init.d/networking restart
```

Yes.

I've included a couple screenshots in case I'm missing something.

Thanks for the guide as well, I'll try starting from scratch and see what I come up with.

---

### Post by dforthman on 2011-03-07
Are you sure your router's IP address 192.168.1.1? Do you have another PC on your network that successfully connects that you can verify this with?

Edit:
After looking at your screenshots it looks like you're not connected to the AP. Be sure to follow the guide here:
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

Let us know how it goes.

---

### Post by matt_symes on 2011-03-07
Hi 

Remove all encryption and try to connect again. I had a usb dongle that would not connect with wpa encryption in 10.04.

What make is the card ?

Kind regards

---

### Post by Jonathan B on 2011-03-07
> **dforthman said:**
> Are you sure your router's IP address 192.168.1.1? Do you have another PC on your network that successfully connects that you can verify this with?

Let us know how it goes.

Yeah, I have a laptop and the router IP is definitely 192.168.1.1 I've tried following the guide but it later on it uses the GUI and I'm only running from the terminal.

> **matt_symes said:**
> Hi 

Remove all encryption and try to connect again. I had a usb dongle that would not connect with wpa encryption in 10.04.

What make is the card ?

Kind regards

Removed it so that the router is open but still having the same issue. I see it when I scan but can't connect.

lsppci | grep Network returns
```
RaLink RT2561/RT61 rev B 802.11g

```nm-tool returns
```
State: unknown
** (process: 3954): WARNING ***: error: could not connect to NetworkManager

```

---

### Post by matt_symes on 2011-03-07
Hi

> State: unknown
** (process: 3954): WARNING ***: error: could not connect to NetworkManager

What version of Ubuntu are you using ?

Are you running a desktop edition as a server or have you actually installed the server version ? 

What wifi driver are you using ?

Kind regards

---

### Post by Jonathan B on 2011-03-07
> **matt_symes said:**
> Hi

What version of Ubuntu are you using ?

Are you running a desktop edition as a server or have you actually installed the server version ? 

What wifi driver are you using ?

Kind regards

I'm using 10.10. I have installed the server version as I want to setup LAMP and host a test website to learn a little more about how it all works and why.

I'm not sure which wifi driver I'm using. dmesg | grep -i wlan0 returns the following information in the attached image. Not sure if that's relevant, it's just what I've managed to pull from Google so far regarding commands.

---

### Post by Jonathan B on 2011-03-07
I have a USB Alfa AWUS036H here as well, do you think I would be better off using that instead?

---

### Post by matt_symes on 2011-03-07
Hi

If you open a terminal and type

```
lspci -k | grep -i network -A3
```

that will tell us your driver for your RaLink (assuming it's PCI)

> I have a USB Alfa AWUS036H here as well, do you think I would be better off using that instead?

Could be worth a go.

Kind regards

---

### Post by Jonathan B on 2011-03-07
> **matt_symes said:**
> Hi

If you open a terminal and type

```
lspci -k | grep -i network -A3
```that will tell us your driver for your RaLink (assuming it's PCI)



Could be worth a go.

Kind regards

```

Network controller: RaLink RT2561/RT61 rev B 802.11g
Subsystem: D-Link System Inc AirPlus G DWL-G510 Wireless Network Adapter (Rev.C)
Kernel driver in use: rt61pci
Kernal modules: rt61pci

```

---

### Post by matt_symes on 2011-03-07
Hi

Have you considered the RaLink drivers and blacklisting rt61pci

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Kind regards

---

### Post by Jonathan B on 2011-03-07
I can't really give consideration to it as I just don't understand how the drivers work, are compiled and installed. I think I'll have to give the wifi a miss and come back to it a bit later when I've learned a bit more about Linux.

I do appreciate your help matt_symes, so, thank you for your help so far :)

---

### Post by Jonathan B on 2011-03-07
Don't know if it's related but running the desktop live CD allows the wireless card to run out of the box.

---

### Post by matt_symes on 2011-03-08
Hi

There have been reports of this happening before

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992)

You could always post your syslog file here. That might shed more light on what is happening. It's at /var/log/syslog.

The fact that it's working from the liveCD sheds hope. I assume from the LiveCD you are using DHCP ? Does DHCP work on your main install ?

Kind regards

---

