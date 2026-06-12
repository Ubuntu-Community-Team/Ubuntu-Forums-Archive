---
title: "tenda mini 11n wireless usb adapter   w311u"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by XxDARKXx on 2010-02-21
Hi all 
i have buy tenda mini 11n wireless usb adapter   w311u
to me computer and in my computer the usb port for dsl is broken
i cant use the internet except using the usb except using usb Wireless
i cant use the internet  in ubuntu 9.10 i cant see our modem in Wireless in ubuntu 
can you help me 
lsusb

> 
Bus 002 Device 003: ID 148f:3070 Ralink Technology, Corp.
Bus 002 Device 002: ID 0644:0200 TEAC Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ifconfig
> 
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)

wlan0 Link encap:Ethernet HWaddr 00:b0:8c:0a:d6:52
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wmaster0 Link encap:UNSPEC HWaddr 00-B0-8C-0A-D6-52-00-00-00-00-00-00-00-00-00-00
UP RUNNING MTU:0 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)


iwconfig

> 
ubuntu:~$ iwconfig
lo no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11bgn ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=7 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:on
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


sudo ifup wlan0


sudo iwconfig wlan0 mode managed

sudo iwconfig wlan0 channel 11

sudo iwconfig wlan0 essid networkname



ifconfig wlan0

sudo iwconfig wlan0 key FEFEFEFEFE 

> 


iwlist wlan0 scan
[QUOTE]
wlan0 no scan results


---

### Post by XxDARKXx on 2010-02-22
I want help

---

### Post by XxDARKXx on 2010-02-22
Anyone

---

### Post by XxDARKXx on 2010-02-22
:confused::confused::confused::confused::confused::confused:

---

### Post by Everybody Loves Hypnotoad on 2010-02-22
Stop bumbing your thread every hour :(

Maybe this can be of interest: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323)

I think your usb stick might be using the RT73 chipset. Google or these forums should be able to help you. Next time you might want to not buy the cheapest chinese stuff and look for something you know will work. (Just some friendly but maybe kinda harsh advice).

---

### Post by eeBus on 2010-04-05
I have the Tenda W311U working fine under Ubuntu 10.04 beta 1 on my netbook.

The Tenda is cheap but works.

All I did was to add rt2870sta to the end of /etc/modules.

I disabled the built in wireless. (There's a switch on the netbook). Plugged in the Tenda USB. Rebooted, and it worked!

Hope this helps

---

### Post by Everybody Loves Hypnotoad on 2010-10-21
I might add to this that sometimes the switch for enabling/disabling the internal wireless also does the same for any other wireless cards that are connected.

---

### Post by IBNubei on 2010-10-28
> **eeBus said:**
> 
All I did was to add rt2870sta to the end of /etc/modules.


Hello,

I too have the Tenda W311U in my Ubuntu 10.04 LTS (vanilla install).  The Network Selector app can see it and make it active, but still, I can't connect!

I tried but I can't edit the file "/etc/modules" - How did you add the line, what was the exact code?

Some Info:
------------------------------------|
Me@UbuntuSys:~$ **ifconfig** [for the Wireless]:

wlan0     Link encap:Ethernet  HWaddr a8:35:a5:d8:33:d1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
------------------------------------|
Me@UbuntuSys:~$ **iwconfig**
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on


Me@UbuntuSys:~$ **lsusb**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


------------------------------------|

Thanks for your help.

------------------------------------|
**[COLOR="DarkRed"]Updated Info:[/COLOR]**
------------------------------------|

[COLOR="DarkRed"]Since my last post, I have found the following links from the Manufacturer:[/COLOR]

**[Linux support Page - go down to: [(RT2870USB(RT2870/RT2770) - 07/09/2010 - 2.4.0.1)]:]("http://www.ralinktech.com/support.php?s=2")**

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

**[Linux driver source Page [just click the Accept button to get the source download dialog box]:]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekEzTHpBNUwyUnZkMjVzYjJGa05ETTVOalU0TXpVeU5pNWllakk5UFQweU1ERXdYekEzTURsZlVsUXlPRGN3WDB4cGJuVjRYMU5VUVY5Mk1pNDBMakF1TVM1MFlYST1D")**

[http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekEzTHpBNUwyUnZkMjVzYjJGa05ETTVOalU0TXpVeU5pNWllakk5UFQweU1ERXdYekEzTURsZlVsUXlPRGN3WDB4cGJuVjRYMU5VUVY5Mk1pNDBMakF1TVM1MFlYST1D](http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekEzTHpBNUwyUnZkMjVzYjJGa05ETTVOalU0TXpVeU5pNWllakk5UFQweU1ERXdYekEzTURsZlVsUXlPRGN3WDB4cGJuVjRYMU5VUVY5Mk1pNDBMakF1TVM1MFlYST1D)

Now, since I am not a programmer nor an advanced Linux user, could someone explain, in simple terms:

**[COLOR="DarkRed"]1.[/COLOR]** If it is the right driver for the "Tenda mini 11n wireless usb adapter w311u"?

**[COLOR="DarkRed"]2.[/COLOR]** How, in simple terms, to compile and install this driver.

I certainly hope that Ubuntu adds native support for this adapter.  It's cheep and very popular.

Thanks in advance.

---

### Post by eeBus on 2010-11-10
You need to open a terminal window and enter

sudo gedit /etc/modules

You will then be able to edit the file and add

rt2870sta

as the last line.

Save the file, and again in the terminal window type 

cat /etc/modules

to confirm that the changes have been made.
That's all I did!

---

