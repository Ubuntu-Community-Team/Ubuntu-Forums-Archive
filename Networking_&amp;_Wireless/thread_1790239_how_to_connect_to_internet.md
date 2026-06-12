---
title: "how to connect to internet"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by NoBody0420 on 2011-06-24
i have internet in my nokia mobile phone
i can use it through nokia pc suite in windows but i cant install it in ubuntu
so is there a way to my ubuntu to my phone without installing nokia pc suite

---

### Post by dineshs on 2011-06-25
Connect your phone in PC suite mode.
Click on Network manager icon on top right of the panel-edit connections-mobile broadband..... and proceed

---

### Post by Maisun on 2011-06-25
if your phone has a bluetooth and so does your PC, then you can connect to internet through bluetooth. there are several methods and tutorials on the net. try googling the term 'connecting to internet through bluetooth'. however, i find this method not suitable for my need. the connection is not very stable and strong. myself i'm looking for alternative means. let us know if mr. dineshs's method works out.

---

### Post by NoBody0420 on 2011-06-25
but i dont have pc suite installed
how can i connect in pc suite mode

---

### Post by dineshs on 2011-06-27
> but i dont have pc suite installed I mean your phone not the operating system.Your mobile phone will have an option to connect in PC suite mode or mass storage mode.Also please post what you get for ```
lsusb
dmesg | grep tty
```when your phone is connected.

---

### Post by NoBody0420 on 2011-06-29
i don't think my phone has those options because when i connect my phone to my computer i get a small icon in my phone which means it is connected to my computer

we get the option of mass storage mode or nokia pc suite in nokia n97 but i don't we can get it in n70

---

### Post by dineshs on 2011-06-29
What about the command results?

---

### Post by NoBody0420 on 2011-06-30
here's the output

lsusb
Bus 
005 Device 002: ID 1267:0201 Logic3 / SpectraVideo plc A4Tech SWOP-3 Mouse
Bus 
005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 
004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 
003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 
003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 
002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 
001 Device 004: ID 0781:5567 SanDisk Corp. Cruszer Blade
Bus 001 Device 
001: ID 1d6b:0002 Linux Foundation 2.0 root hub


dmesg | grep tty

[    0.000000] console [tty0] enabled

[    3.169989] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[    3.240883] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

---

### Post by dineshs on 2011-07-01
Was the device plugged in when you run the command?

---

### Post by pjd99 on 2011-07-01
To get into PC suite mode you may need to set it on the phone first (if it doesn't ask when you connect it).

e.g. on my E51:
Menu->Connectivity->USB->USB mode
Select PC Suite.

Then when you click the network icon and select "Edit Connections" you should be able to select your device when setting up a mobile broadband connection.

and you should see similar if you perform the following```

pjd99@pjd99-work:~$ lsusb | grep Nokia
Bus 003 Device 002: ID 0421:0042 Nokia Mobile Phones E51 (PC Suite mode)

pjd99@pjd99-work:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[26527.182601] cdc_acm 3-1:1.10: ttyACM0: USB ACM device
[26527.185232] cdc_acm 3-1:1.12: ttyACM1: USB ACM device

```

---

### Post by NoBody0420 on 2011-07-02
@dineshs
no my phone wasn't plugged in
sorry didn't know i had to do that

@pjd99
i will try that
i hope it works with n79

---

### Post by NoBody0420 on 2011-07-06
@dineshs
thanks for your time
i figured it out
my internet is working now

---

