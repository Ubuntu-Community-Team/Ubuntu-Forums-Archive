---
title: "RTL8188CE Destination Host Unreachable"
date: 2012-12-27
forum: Networking &amp; Wireless
---

### Post by mvmacd on 2012-12-27
Ubuntu 12.10, RTL8188CE chipset, using rtl8192ce driver. 

My wifi works when I first connect, but then after about 5-7 minutes, it all of a sudden stops working. 

I try to load pages, they will just sit there loading, or eventually error out. 

I tried a different network also [with different encryption] and it did the same thing.

after it stops working, **iwconfig** still says I'm connected and associated, and all that, **ip route** still shows my route, but if I, say, try to ping a server:

```

$ ping 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
From 192.168.1.14 icmp_seq=1 Destination Host Unreachable
From 192.168.1.14 icmp_seq=2 Destination Host Unreachable
From 192.168.1.14 icmp_seq=3 Destination Host Unreachable
From 192.168.1.14 icmp_seq=4 Destination Host Unreachable

```

So when this happens I just reconnect with NetworkManager and it usually reconnects and is up and working again.. but it's killing me, so much I started to use a external wifi.  But the wifi is clunky [alfa] and that's a pain too.  


I tried to compile compat-wireless but then when I went to insmod rtl8192ce.ko, it said invalid parameters.  
[Asked ubuntu here: [http://askubuntu.com/questions/232793/compat-wireless-inserting-ko-1-invalid-parameters](http://askubuntu.com/questions/232793/compat-wireless-inserting-ko-1-invalid-parameters) ]

And here is iwconfig and ip route, while it is working:

```

$ iwconfig wlan3
wlan3     IEEE 802.11bgn  ESSID:"Digital"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:7F:28:86:DE:13   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry limit:30   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:51   Missed beacon:0

$ ip route
default via 192.168.1.1 dev wlan3  proto static 
169.254.0.0/16 dev wlan3  scope link  metric 1000 
192.168.1.0/24 dev wlan3  proto kernel  scope link  src 192.168.1.14  metric 9 


```

---

### Post by TOMBSTONEV2 on 2012-12-27
I have the exact same wireless network adapter in my HP Mini 110-3700 netbook. The driver I am using quite successfully I might add is rtl8192c. I use this driver for both ubuntu 12.04 LTS and Back Track 5 R3. This card/driver supports packet monitoring and even packet injection. I installed 12.04 about 2 months ago and the drivers were just there for me.

Did you have to install the drivers yourself or were they just there when you installed ubuntu 12.10? I have taken interest in this and would like to see what I can do to help.

---

### Post by mvmacd on 2012-12-27
First, rtl8192c or rtl8192ce? 

No I didn't have to install them they came with Ubuntu.

---

### Post by TOMBSTONEV2 on 2012-12-27
My apologies; driver=rtl8192ce driverversion=3.2.0-35-generic-pae this is what my network card is using as its drivers.

```
sudo su
```

then

```
lshw -C network
```

This determines which drivers are in use.

---

### Post by mvmacd on 2012-12-27
It seems mine is slightly older:

```

driver=rtl8192ce driverversion=3.5.0-21-generic firmware=N/A 

```

also is firmware supposed to be N/A?

---

### Post by TOMBSTONEV2 on 2012-12-28
Well my firmware says N/A as well.

It stands to reason that since quite a few are using this driver successfully (including me) try:

```
sudo modprobe rtl8192ce 3.2.0-35-generic-pae
```

---

### Post by mvmacd on 2012-12-30
> **TOMBSTONEV2 said:**
> Well my firmware says N/A as well.

It stands to reason that since quite a few are using this driver successfully (including me) try:

```
sudo modprobe rtl8192ce 3.2.0-35-generic-pae
```

```


# modprobe rtl8192ce 3.2.0-35-generic-pae
FATAL: Error inserting rtl8192ce (/lib/modules/3.5.0-21-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko): Invalid argument

```

also all my packages are up to date. how do you have kernel 3.5.0-35?

---

### Post by ahallubuntu on 2012-12-30
> **mvmacd said:**
> [code]also all my packages are up to date. how do you have kernel 3.5.0-35?

You mean 3.2.0-35 ?  That's the latest kernel I have in Ubuntu 12.04 LTS, too.

Ubuntu 12.04 LTS and 12.10 both seem to have issues with some of the Realtek chipsets.  For my little mini WiFi dongles with the Realtek 8188/8192CU chipset, even though I can sort of get WiFi to work (sometimes) with the built-in drivers, they are almost unsable.  Instead, I have had great luck download the latest drivers from Realtek - they have worked flawlessly for me.

I get them from here:

http://www.realtek.com.tw/downloads/

But I don't have any experience installing the driver for your particular chipset, so I don't know how well the downloaded driver may work for you.  (These Realtek chipsets have very similar names but may have different drivers.)

---

### Post by mvmacd on 2013-01-01
> **ahallubuntu said:**
> You mean 3.2.0-35 ?  That's the latest kernel I have in Ubuntu 12.04 LTS, too.

Ubuntu 12.04 LTS and 12.10 both seem to have issues with some of the Realtek chipsets.  For my little mini WiFi dongles with the Realtek 8188/8192CU chipset, even though I can sort of get WiFi to work (sometimes) with the built-in drivers, they are almost unsable.  Instead, I have had great luck download the latest drivers from Realtek - they have worked flawlessly for me.

I get them from here:

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

But I don't have any experience installing the driver for your particular chipset, so I don't know how well the downloaded driver may work for you.  (These Realtek chipsets have very similar names but may have different drivers.)

Oh I just realized that you have an **OLDER** kernel, not a newer one. [I was just paying attention to the last part]  Yes I have downloaded the drivers from Realtek but when I try to insert the driver I get an error.

I downloaded the rtl8192ce driver and typed `$ make` then `# make install` 
It had no errors.  So then I `# modprobe rtl8192ce` and I get "Invalid argument"

And from syslog, I get this long error message
[http://paste.ubuntu.com/1485784/](http://paste.ubuntu.com/1485784/)

edit:  I just realized on the downloads page it says the driver is for 2.6.something to 3.2.x.  I guess that explains why it works for you [3.2 kernel] but not for me [3.5 kernel].  :( I guess I'm stuck now.

---

### Post by TOMBSTONEV2 on 2013-01-02
So from what I understand here, I had better not update my kernal or I may have issues with my wireless? Thats scary O.o Tomorrow I am going to dedicate a significant amount of time to this to figure it out.

Nevermind it seems I miss-read the post. For some reason my computer bonded with the t virus.. Er umm I mean 3.2.0-35 drivers quite nicely.

---

### Post by mvmacd on 2013-01-02
> **TOMBSTONEV2 said:**
> So from what I understand here, I had better not update my kernal or I may have issues with my wireless? Thats scary O.o Tomorrow I am going to dedicate a significant amount of time to this to figure it out.

Nevermind it seems I miss-read the post. For some reason my computer bonded with the t virus.. Er umm I mean 3.2.0-35 drivers quite nicely.

actually, it's weird, sometimes my wifi works for a long time. like now, I haven't had an issue for probably half an hour.  

but do you use rtl8192ce?  What kernel version? [uname -r]
Also, if you do update your kernel you should have your old kernel too and with some GRUB configuration [or none, depending on your grub settings] you can boot your old kernel.

---

### Post by TOMBSTONEV2 on 2013-01-02
My kernal is 3.2.0-35-generic-pae
rtl8192ce is the driver I use for my wlan

One thing to check is to make sure ubuntu cannot shut the device off to save power. Sometimes this causes these kinds of issues

```
iwconfig
```

Then look where it says power management, it should say "off"

---

### Post by mvmacd on 2013-01-02
Right, I have already done that. :)

---

### Post by TOMBSTONEV2 on 2013-01-02
Maybe blacklist the driver and choose an earlier version? If thats the route you want to go, it may produce results

---

