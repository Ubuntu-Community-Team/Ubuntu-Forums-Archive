---
title: "Wicd RTL8187SE eeepc701SD 9.10NBR problem"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by coupedeluxe on 2010-02-12
Hi,

I have installed Wicd after not being able to connect wired/wireless with my computer. I removed the network manager/gnome of 9.10.

I had followed several threads including the Wifi Docs/Troubleshoot all to no avail.

After installing Wicd and doing a reboot I plugged in my ethernet cable. Wicd say's it's connected to a wired network and gives an IP address.

I try to load Firefox and it tell's me I am not connected to the net.

I have run out of options and have been sourcing the net and this forum trying to get it to work. I think I have probably spent 30-40hrs just trying to get on the net.

I welcome any help or suggestions.
Cheers

---

### Post by chili555 on 2010-02-13
Your post is just a bit unclear as to which, wired or wireless, you want to get going first. Since the title references rtl8187se, let's start the wireless first. Please detach the ethernet cable. First, let's check to see what device you have to be sure rtl8187se is the correct driver. Is it a USB device? If so, please open a terminal and do:```
lsusb
```Post the results. If it's a built-in device, please post:```
lspci -nn | grep Network
```Now, let's see if the driver has grabbed your device and created an interface:```
iwconfig
```Do you see an interface with lots of details following it, like this example?> wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 99:24:56:2A:99:29   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=69/70
--- snip ---If so, we're mostly done. Next, try to get to the outside world. Ask Wicd to connect to your network. Success? If so, please try:```
ping -c3 74.125.65.99
```Did you get ping returns, like this?> 64 bytes from 74.125.65.99: icmp_seq=1 ttl=48 time=27.7 msIf so, we're getting very close. Now try:```
ping -c3 www.google.com
```Success or fail? If it fails, please post:```
route -n
cat /etc/resolv.conf
```Thanks.

---

### Post by coupedeluxe on 2010-02-13
Hi Chili,

It's a built in device.

brendon@brendon-eeepc:~$ lspci -nn | grep Network
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
brendon@brendon-eeepc:~$ 


brendon@brendon-eeepc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  link  ESSID:"Brendon Fraser's MacBook"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:1E:52:7E:FE:E6   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=93/100  Signal level=-30 dBm  Noise level=-117 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

brendon@brendon-eeepc:~$


Wicd shows me the wireless signal and say's it's trying to obtain an IP address but fails to connect.

Thanks for your help. Took a while to respond as due to the time difference with me in Australia.

---

### Post by chili555 on 2010-02-13
> it's trying to obtain an IP address but fails to connect.Does it ask for your WEP or WPA encryption details? Did you add them under 'Properties?'

---

### Post by coupedeluxe on 2010-02-13
Hi,

There is no encryption as I am sharing my wireless through my macbooks connection.

---

### Post by 2hot6ft2 on 2010-02-13
I feel your pain. Network manager has been giving me problems lately. Not remembering my wifi key and disconnecting. That together with every browser I tried being slow. So since wicd works fine in backtrack I decided to give it a try in ubuntu.

Wired worked fine that's how I ended up getting network-manager back.

wicd only very briefly saw 1 wifi network the rest of the time it wouldn't see any networks.

Only wlan0 showed up with ifconfig although I tried 2 wifi adapters aside from the built in card.

AR928x showed up as wlan0 but no networks even if I was right next to the AP.

RTL8187B and RTL8187L neither of which would even show up with wicd.

I reinstalled network-manager and they showed right up and connected although it has disconnected 4 times already while typing this.

I tried putting the adapters down and up and they did show up with lsusb.

---

