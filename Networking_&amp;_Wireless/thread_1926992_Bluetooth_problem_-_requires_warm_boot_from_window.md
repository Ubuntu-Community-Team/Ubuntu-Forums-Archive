---
title: "Bluetooth problem - requires warm boot from windows to work"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by dixoncx on 2012-02-17
OS: Ubuntu 11.10 x64
Device: Sony VAIO VPCEH15

My laptop has a hardware switch for wireless.

My problem is that,
If i boot to ubuntu, while wireless switch is turned OFF, then there is no way to use bluetooth..
If i turn ON wireless switch, then my wifi works but still bluetooth didn't works..

And i get "rfkill list" output as 
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```The only way i left to turn on my bluetooth is,
first boot into windows, turn on wireless hardware switch, then warm boot to Ubutnu...

Is there any way to fix this problem ?

---

### Post by dixoncx on 2012-02-17
Anyone...?

---

### Post by dixoncx on 2012-02-19
Anyone here......?

---

### Post by dixoncx on 2012-03-12
Anybody please guide me... :-(

---

### Post by puppywhacker on 2012-04-15
For me, I have to enable hci0 to use bluetooth since it is down by default.

So I get it to work with 
sudo hciconfig hci0 up

```

$hciconfig 
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
	DOWN 
	RX bytes:0 acl:0 sco:0 events:0 errors:0
	TX bytes:6 acl:0 sco:0 commands:2 errors:0

$ sudo hciconfig hci0 up

$ hciconfig 
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:07:61:F9:0D:05  ACL MTU: 1017:8  SCO MTU: 64:0
	UP RUNNING PSCAN ISCAN 
	RX bytes:783 acl:0 sco:0 events:28 errors:0
	TX bytes:382 acl:0 sco:0 commands:29 errors:0

```

---

### Post by willunicamp on 2012-05-04
HI,

I'm having the same problem. My bluetooth works fine after if I first boot in Windows.

When my bluetooth doesn't work, I tried the command below, but I received a timeout message:

```
sudo hciconfig hci0 up
```

I've been trying some things. I've already installed a lot of softwares, tried to reinstall the bluez packages, but nothing worked.

If someone have a solution, please share. :confused:

---

### Post by dixoncx on 2012-05-27
No hope..:(
hciconfig gives "Connection timed out" 

```

dixon@dixon-vaio:~$ sudo hciconfig 
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
    DOWN 
    RX bytes:0 acl:0 sco:0 events:0 errors:0
    TX bytes:9 acl:0 sco:0 commands:3 errors:0

dixon@dixon-vaio:~$ sudo hciconfig hci0 up
Can't init device hci0: Connection timed out (110)

dixon@dixon-vaio:~$ sudo hciconfig hci0 reset
Can't init device hci0: Connection timed out (110)

```

---

### Post by dixoncx on 2012-05-30
bump :(

---

### Post by CaptainPasty on 2012-07-12
Yeah, I can confirm the same problem on the same model of machine.  

sudo hciconfig hci0 up's also giving me a connection time out...

First one of us to figure this one out, post here.  :)

---

