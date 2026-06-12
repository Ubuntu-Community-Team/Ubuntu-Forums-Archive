---
title: "Bridging Network Connections Issue"
date: 2012-09-24
forum: Networking &amp; Wireless
---

### Post by DaGeek247 on 2012-09-24
Alright, Here's the setup:

Server<eth0>Desktop<wlan0>Router-Internet

What I want to do on my personal 12.04 desktop is allow the server to connect to to the internet and have its own internal ip address on the router so i can use it for minecraft and assaultcube server stuff.

Sharing the internet via the network manager is not suitable because I need to be able to ssh to my machine. I have also done various googling exercises, and none of them have offered a solution.

In windows (dont hate, it worked) I would just bridge my ethernet and wireless devices and my server would have its own internal network ip. How would i bridge network connections like that on ubuntu?

Here is what I have tried (as sudo):
```

apt-get install bridge-utils
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 wlan0

```
but when i do the last line i get this error:
```

can't add wlan0 to bridge br0: Operation not supported

```

Is there something wrong? do I need to set something else up? I am assuming it is something to do with my usb wireless adapter but I have no idea how to fix it. any and all help would be appreciated.

---

### Post by DaGeek247 on 2012-09-26
bump?

---

### Post by DaGeek247 on 2012-09-28
I have also tried a completely different wireless usb device and it has also come up with the same error. what am I doing wrong? Does USB not support bridges? are my commands wrong?

---

### Post by DaGeek247 on 2012-09-29
bump.

---

### Post by uncaspi on 2012-09-29
It seems to me on the fly that wireless cannot be bridging. Maybe you should use another logical name i.e eth2. This just a guess and probably not much help.

---

### Post by DaGeek247 on 2012-09-29
> **uncaspi said:**
> It seems to me on the fly that wireless cannot be bridging. Maybe you should use another logical name i.e eth2. This just a guess and probably not much help.
so you are suggesting i go into something like **/etc/udev/rules.d/70-persistent-net.rules** and change wlan0 to eth2. then try bridging it again?

---

### Post by uncaspi on 2012-09-29
Yes something like this.
Before you do this you could google the forums with the keywords bridging wireless linux

---

### Post by DaGeek247 on 2012-09-29
So I edited **/etc/udev/rules.d/70-persistent-net.rules** and changed my wireless (wlan0) to eth2. (just the device name)

Then I restarted the network with **sudo /etc/init.d/networking restart**.

output of **iwconfig** is
```

dageek247@dageek247-pc:~$ iwconfig
lo        no wireless extensions.

br0       no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"10FX08136693"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 0C:D5:02:12:48:3F   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:54  Invalid misc:128   Missed beacon:0

eth0      no wireless extensions.

```

I still tried adding wlan0 the bridge; i got the same error.

---

### Post by uncaspi on 2012-09-29
Ok. I think I read somewhere that bridging cannot be performed wireless in Linux. Try google. That is the last idea I have. Sorry.

---

