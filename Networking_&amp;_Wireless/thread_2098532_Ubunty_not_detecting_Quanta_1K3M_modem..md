---
title: "Ubunty not detecting Quanta 1K3M modem."
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by fzlunx on 2012-12-26
Hi I am using Ubuntu 12.10 & My 4G Modem (Quanta 1K3M) is not getting detected. What to do?

---

### Post by rrnbtter on 2012-12-27
Greetings,
Open a terminal and type lsusb and see if your modem is listed. you can also copy the resulting readout and put in your post.

---

### Post by fzlunx on 2012-12-28
This is what I get when I type lsusb

Bus 001 Device 002: ID 04f2:b026 Chicony Electronics Co., Ltd 
Bus 002 Device 007: ID 0408:ea25 Quanta Computer, Inc. 
Bus 006 Device 002: ID 04d9:1133 Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So what shall I do next?

---

### Post by rrnbtter on 2012-12-29
Greetings,
Just to verify your device, unplug your modem and do another lsusb and see if this line is gone "Bus 002 Device 007: ID 0408:ea25 Quanta Computer, Inc.".

If the line is gone it would indicate that your modem is being detected. So the only thing you would need to do is let your system know that it is a serial communications device.

Open a terminal and give this command.  sudo modprobe usbserial vendor=0x0408 product=0xea25
Then wait plug your modem back into the usb port.  In about five seconds you should have a new network connection listed with a setup wizard.

---

### Post by fzlunx on 2012-12-29
Did it but still not connecting. is there anything else I can do?

---

### Post by rrnbtter on 2012-12-29
Greetings,
When you say that it isn't connecting, do you mean that it is showing up in the network manager but not connecting?

also from a terminal enter ifconfig then iwconfig and post the results.

---

### Post by rrnbtter on 2012-12-29
Greetings,
In addition did you copy the line "sudo modprobe usbserial vendor=0x0408 product=0xea25" into your terminal or type it? I suggest you copy and paste it into the terminal. Without the quote marks of course.

---

### Post by fzlunx on 2012-12-29
It's not showing up in network manager.

I copied that to terminal.

when i typed "ifconfig" result is
  	 	 	 	 	
  	 	 	 	 	 	   eth0      Link encap:Ethernet  HWaddr 00:1d:72:20:fa:ba   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
           Interrupt:16  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:23066 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:23066 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:1814750 (1.8 MB)  TX bytes:1814750 (1.8 MB) 
  
 wlan0     Link encap:Ethernet  HWaddr 00:17:c4:1b:d1:79   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
  


when I typed "iwconfig" result is

  	 	 	 	 	 	   wlan0     IEEE 802.11bg  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off 
           Power Management:off 
            
 lo        no wireless extensions. 
  
 eth0      no wireless extensions.

---

### Post by rrich1974 on 2012-12-29
you also can try wvdial

---

### Post by rrnbtter on 2012-12-29
Greetings,

> **rrich1974 said:**
> you also can try wvdial

I agree with the above in this case. Looks like the network manager isn't recognizing your dialup device.

---

### Post by rrich1974 on 2012-12-29
you also maybe must to do a "setserial"....i don't know!

---

### Post by fzlunx on 2012-12-29
When I type wvdial in terminal this is what I am getting

fazl@fazl-Aspire-4315:~$ wvdial
--> Can't open '/etc/wvdial.conf' for reading: Permission denied
--> ...starting with blank configuration.
--> WvDial: Internet dialer version 1.61
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

So I typed "sudo wvdial" then I got this.

fazl@fazl-Aspire-4315:~$ sudo wvdial
--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/ttyUSB4: No such file or directory
--> Cannot open /dev/ttyUSB4: No such file or directory
--> Cannot open /dev/ttyUSB4: No such file or directory


Thank You very much for your great help.
what can I do now?

---

### Post by rrnbtter on 2012-12-29
Greetings,
In a terminal type
sudo wvdialconf /etc/wvdial.conf

post results

---

### Post by rrich1974 on 2012-12-29
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

look at alternative way 1

---

### Post by fzlunx on 2012-12-29
This is what I get when I type "sudo wvdialconf /etc/wvdial.conf"

fazl@fazl-Aspire-4315:~$  sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://alumnit.ca/wiki/?WvDial](http://alumnit.ca/wiki/?WvDial)

---

### Post by rrich1974 on 2012-12-30
i was afraid of this, maybe we can solve it!
you must set the setserial. plug the modem.
 
"modprobe usbserial vendor=0x16d5 product=0x6502" (that is an exemple)

the parameter vendor and product will be taken from lsusb output. 
now, you will run wvdial conf again and it should see the modem.

> This is what I get when I type lsusb

Bus 001 Device 002: ID 04f2:b026 Chicony Electronics Co., Ltd 
_Bus 002 Device 007: ID 0408:ea25 Quanta Computer, Inc._ 
Bus 006 Device 002: ID 04d9:1133 Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


"modprobe usbserial vendor=0x0408 product=0xea25"  seems to be the command for you.

---

