---
title: "Unstable Wireless connection - Intel WiFi Link 5100/Ubuntu 11.04/Acer 5739g"
date: 2011-05-13
forum: Networking &amp; Wireless
---

### Post by bradumd on 2011-05-13
I have had this issue since 10.10 and the same issue still exists in version 11.04. My wireless connection is extremely unstable and it drops constantly. I have my computer set to dual boot with Windows 7 and the issue is non-existent on the windows side. Here is some background info.

**1) Machine Brand and Model (PC/Laptop):** Acer Aspire 5739g

**2) Wireless Brand, Model and Wireless Chipset:**
Network controller: Intel Corporation WiFi Link 5100

**3 ) check interface:**
wlan0     Link encap:Ethernet  HWaddr 00:22:fa:27:54:2a  
          inet addr:10.108.201.93  Bcast:10.108.207.255  Mask:255.255.240.0
          inet6 addr: fe80::222:faff:fe27:542a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46669 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:97221101 (97.2 MB)  TX bytes:5971058 (5.9 MB)


wlan0     IEEE 802.11abgn  ESSID:"umd-secure"  
          Mode:Managed  Frequency:5.24 GHz  Access Point: 00:27:0D:98:8A:DD   
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:365  Invalid misc:4   Missed beacon:0

---

### Post by obriente on 2011-05-27
I'm having the same exact issue on a ThinkPad X200 with the Intel 5300 chip. Connection drops and seems like the only way to get it back is to reboot. It's also unpredictable -- some days it'll drop 10 times, some days it won't drop at all. But it's definitely something on the Ubuntu side, it happens regardless of Wi-Fi network and I'm not having the same issue when booted into Windows 7.

---

### Post by Hippytaff on 2011-05-27
If you run the wireless script found in the link below and choose continual wireless connectivity checking, when the connection drops it will return all relevant info and log details which might point to the problem.
 
Some instructions on how to use the script can be found [here]("http://www.bodhilinux.com/wiki/doku.php?id=wireless_script#how_do_i_run_the_script")

---

### Post by silex89 on 2011-05-27
Maybe you need some privative drivers. Did you check out jockey if there's something available ?

---

### Post by obriente on 2011-06-09
So I finally found a possible solution:
[http://ubuntuforums.org/showthread.php?t=1756096&page=2](http://ubuntuforums.org/showthread.php?t=1756096&page=2)

Followed the directions to install compat-wireless drivers... so far, so good, but it's too early to tell if it actually solved the problem yet.

---

### Post by obriente on 2011-06-15
Nope... still dropping the connection constantly. Back to Windows it is.

---

### Post by chili555 on 2011-06-15
Is the behavior improved if you disable N speeds? I believe it's a known issue in iwlagn.```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up
```If it works, we can write a simple conf file to make it persistent.

---

### Post by obriente on 2011-06-20
I'm trying out turning of 'N' I'll let you know how it goes... though this is not really an ideal solution.

---

### Post by garvinrick4 on 2011-06-20
Chili555 is correct there is an issue with the iwlagn driver it is unstable in "N"
Set your router in 2.4 Ghz to mixed g and n at 20 Mhz for first choice and "N" works
in second choice with 3.0 kernel:
You have two choices either make the config file:
```
sudo gedit /etc/modprobe.d/iwlagn.conf
```and insert this line save and reboot.
                                 [COLOR=#000000][FONT=Times New Roman][SIZE=3]options iwlagn 11n_disable50=1 11n_disable=1[/SIZE][/FONT][/COLOR]


[COLOR=#000000][FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][SIZE=3]or you can use the 3.0 kernel and "N" will be stable with iwlagn driver:[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT][/COLOR]
 [Index of /~kernel-ppa/mainline/v3.0-rc2-oneiric]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0-rc2-oneiric/")

Need headers, all deb and kernel image generic of the 3 packages of whatever you use 32 or 64 bit
Download and install in 11.04 and 11.10 already has 3.0 kernel.

---

### Post by obriente on 2011-06-21
Sad to say disabling N didn't solve the issue. Still dropping the connection.

---

### Post by garvinrick4 on 2011-06-21
> **obriente said:**
> Sad to say disabling N didn't solve the issue. Still dropping the connection.
when you run:
```
iwconfig
```What does it say 802.11abgn or 802.11abg card?

##I have that same driver and have used maybe 50 or more different installs over time
and it has always worked with iwlagn driver.
Did you make the config file and then insert the line of code and hit save and reboot?

---

### Post by obriente on 2011-06-30
I made the config file and it only reads "abg," no "n."

The connection is *more* stable, but it still drops. Now it's just every 6 hours instead of every 2.

---

### Post by obriente on 2011-07-05
Okay, I take it back -- it's just as unstable, I just had a brief run of good luck. But, I'm beginning to think the issue is hardware based now.  Last week started having a similar issue under Windows -- not nearly as frequent, but once a day or ever other day the connection would drop and I'd have to reboot. Then, this morning, Windows simply stopped recognizing the WiFi all together. The two problems may not be connected, but seems a little odd that I'm now having issues with the WiFi regardless of OS.

---

### Post by in-dust-rial on 2011-07-11
hi there,

did you actually validate how 'stable' the connection in wiondows is?

have very similar problems wirh intel wifi card.
the windows connection has still several time outs.
i usually watch:
[HTML]ping URL /n 9999[/HTML]

in the same location a different wireless machine never loses any package.
so if you find your windows losing packages too, consider it to be a hardware problem. 

good luck.

---

### Post by lotus49 on 2011-10-06
I have the same Intel 5100 in a Dell E6400 and it does exactly the same thing in Ubuntu but never in Windows 7.

It did used to work well enough for me not to have noticed a problem in 10.10 (all wifi devices seem to drop the connection every now and then) but in 11.04 it is frustratingly flaky.  Although this machine dual boots, I hardly ever used to boot into Windows but since upgrading to 11.04 I find myself using 7 more and more (indeed I posted this from Windows) :(.

---

### Post by egemenaydin on 2011-10-09
I was experiencing similar problem with Intel Centrino Advanced-N 6200 wireless card in Ubuntu 11.10. Disabling N speed as suggested by chili555 solved the issue. Even tough I have 3.0 kernel, I couldn't have stable internet connection with a wireless card having N speed capability in my case.  
However, creating a conf file as suggested by garvinrick4 caused disabling my wireless card. Therefore, I created /etc/modprobe.d/iwlagn.conf and inserted this: 
```
options iwlagn 11n_disable=1
```

For now it seems working. The strange thing is while using Ubuntu 11.04, I hadn't experienced such problems with the same configuration.

---

