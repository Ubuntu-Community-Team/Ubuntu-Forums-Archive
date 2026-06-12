---
title: "Wireless not Working - Intel Centrino Advanced-N WiMax AGN 6250"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by jseabold on 2010-07-13
This is a crosspost of [thread=1529245]a thread in the hardware and laptop forum.[/thread] 

Haven't been able to get my wireless card working in Ubuntu 10.04.

$ uname -r
2.6.32-23-generic

It's an Intel Centrino AGN 6250.

I've installed the Intel 6050 microcode from here
[http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads)
and rebooted

$ rfkill list
 0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: yes
$ rfkill unblock all
$ rfkill list
 0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: yes

$ sudo ifconfig wlan0 up
 SIOCSIFFLAGS: Unknown error 132

Seems odd. Any other info I can provide? Any help would be appreciated.

PS.

Wondering if all of these should be there?

$ ls -la /lib/firmware/ | grep ucode
-rw-r--r-- 1 root root 335056 2010-05-26 12:10 iwlwifi-1000-3.ucode
-rw-r--r-- 1 root root 150100 2010-05-26 12:10 iwlwifi-3945-2.ucode
-rw-r--r-- 1 root root 187972 2010-05-26 12:10 iwlwifi-4965-2.ucode
-rw-r--r-- 1 root root 345008 2010-05-26 12:10 iwlwifi-5000-1.ucode
-rw-r--r-- 1 root root 353240 2010-05-26 12:10 iwlwifi-5000-2.ucode
-rw-r--r-- 1 root root 337400 2010-05-26 12:10 iwlwifi-5150-2.ucode
-rw-r--r-- 1 root root 462280 2010-05-26 12:10 iwlwifi-6000-4.ucode
-rw-r--r-- 1 root root 463692 2010-07-11 22:35 iwlwifi-6050-4.ucode

---

### Post by iponeverything on 2010-07-13
No idea where this stands, poke the lp bug with a question asking if someone has it working.

[https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/537814](https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/537814)

edit:

Just found another lp for it:

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451)

From this report, try installing backports:

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

---

### Post by jseabold on 2010-07-13
Thanks for finding the bug report.  I neglected to mention that I had installed the backports already.

When I click on the NetworkManager applet under wireless it says wireless is disabled and it's greyed out.

It's that hard block that I find to be odd.  Like my wireless is toggled off and won't turn back on, but it looked like the wireless toggle key is working.

---

### Post by jseabold on 2010-07-13
As an update, I have reinstalled Ubuntu 10.04 to start from scratch and installed the wireless modules backports.

I have done

```

sudo modprob iwlang

```

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

```

$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied
$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132

```

I also noticed that it's not the wireless switch providing the hard block

```

$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

Toggle wireless key.

```

$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

```

Anyone have any thoughts on the workaround in the last reply to [post=8244101]this post[/post]

---

### Post by jseabold on 2010-07-13
Solved the problem.  I have a dual boot system.  I logged into Windows 7.  Toggled wireless off then back on.  Reboot into Ubuntu and all is good.

---

### Post by iponeverything on 2010-07-14
> **jseabold said:**
> Solved the problem.  I have a dual boot system.  I logged into Windows 7.  Toggled wireless off then back on.  Reboot into Ubuntu and all is good.

Maybe the card got a bad firmware load..

Interesting. I wonder if it could have been done without the dual boot option by removing all power and letting the system sit for while. What is your hardware?

---

### Post by jseabold on 2010-07-14
> 
Interesting. I wonder if it could have been done without the dual boot option by removing all power and letting the system sit for while. What is your hardware? 


Maybe, but I installed and uninstalled Ubuntu several times with the same result.  I also had problems with Win 7 overwriting the MBR through retail vendor software, and I don't think the bluetooth was working in Ubuntu until I also toggled it in Windows.

I saw this fix mentioned on another site for the hard block problem.  The machine is a brand new Dell Studio.  I don't know the motherboard, but the wireless is an Intel Centrino WiFi/WiMax 6240 AGN.

---

### Post by iponeverything on 2010-07-14
I have heard of cases where power had to removed from the device for a period of time to clear an inconsistent register state caused by a bad firmware.

---

### Post by fitzjj on 2010-10-02
> **iponeverything said:**
> 

From this report, try installing backports:

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```


Thanks iponeverything, I've been searching for a solution to this for a while and that one line solved everything. For reference that was on a Lenovo Thinkpad with an Intel wireless card:

description: Wireless interface
product: PRO/Wireless 3945ABG [Golan] Network Connection
vendor: Intel Corporation

---

### Post by syats on 2010-11-20
Another solution is to use rfkill

1. rmod your wifi module
2. rfkill block all
3. rfkill unblock all
4. modprobe your wifi module
5. rfkill unblock all

in my case

```
rmmod ath5k
rfkill block all
rfkill unblock all
modprobe ath5k
rfkill unblock all
```

did it (works also on debian)

---

