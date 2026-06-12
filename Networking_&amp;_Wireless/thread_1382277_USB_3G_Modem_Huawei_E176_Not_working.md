---
title: "USB 3G Modem: Huawei E176 Not working"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by KaiserG on 2010-01-15
This is really weird, and I would like just this question answered:
I've spent like 2 hours by plugging, unplugging, rebooting, and doing everything I could, but the modem wasn't working.
When I did **ls /dev/ttyU*** it was showing up a list of 6 usb devices.
```
[B]/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2
/dev/ttyUSB3  /dev/ttyUSB4  /dev/ttyUSB5[/B]
```
And when I sent the command **wvdialconf** after looking into all the devices, it didn't recognize any modem.

The thing is, that by the time I was writing here for a solution, I disconnected the modem, and when I reconnected it I did a **ls /dev/ttyU*** just to copypaste the info, and Voilá! there were just 2 devices, and **wvdialconf** worked out just fine!
I would like to know what I was doing wrong, so I make sure it won't happen again.

Oh, and I forgot to say: I use Ubuntu 8.04

Thanks in advance for this great community. I'm quite new to Ubuntu and to Linux but I really love it!

---

### Post by pdc on 2010-01-15
so when you send us this message, are you connected to the internet from your Huawei E176 modem?

---

### Post by KaiserG on 2010-01-15
No, the modem is from another person, and I was just testing the hardware under Ubuntu. My connection is from an ethernet device. However, I have to wait 2 days until the SIM is activated so Internet connection is not tested yet.
I've already dowloaded the Wvdial debian package and all of its dependencies for installing it on the Ubuntu machine that is going to be used.
The modem communicates with the computer very well, no errors at all so it should work just fine.

---

### Post by pdc on 2010-01-15
well in a couple of days let everyone know how it goes; i have found wvdial very good

---

### Post by KaiserG on 2010-01-17
It's doing the same thing again!!! I can't believe it!
[B]ls /dev/ttyU*
/dev/ttyUSB0  /dev/ttyUSB2  /dev/ttyUSB4
/dev/ttyUSB1  /dev/ttyUSB3  /dev/ttyUSB5
[/B]

What am I doing wrong???

Thanks in advance.

---

### Post by pdc on 2010-01-17
If I understand you correctly,  you think it is wrong to see multiple ttyUSB* devices; to the contrary, I don't think it is wrong:

main thing surely is: can you dial with wvdial? If so, enjoy

---

### Post by KaiserG on 2010-01-17
No, when I run **wvdialconf** it shows up some Exec errors on devices ttyUSB1,3 and 4. And after that no modems are found.
I've found a solution, it seems not to detect correctly the usb device. If it shows up 6 devices, I only disconnect, wait 10 seconds and reconnect. Then it shows up only 2 devices and works as a normal modem.

But that's not all. The new problem I have now is that when I wvdial it shows up:
[B]$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
[/B]

I've called for support and the login/password is OK. It just doesnt work. Any ideas?
Thanks for your support.

EDIT: I'm so stupid, forgot to remove the quotemarks ';' from the wvdial.conf.

Now I have a message that says NO CARRIER. But I'm looking into that.

---

### Post by KaiserG on 2010-01-17
Ok, got it finnally to work. The 'No Carrier' message was just because the modem had not signal.

The only problem that bothers me is that the first time i connect the modem it shows up 6 different devices and doesnt work. I have to unplug and plug again to get it to work. (shows up 2 devices).
If anyone can help me on that i would appreciate it.

Thanks to everyone for your help.

---

### Post by pdc on 2010-01-17
I thought one had to run wvdial command as root or sudo; so in Ubuntu I thought one had to go

> sudo wvdial to do the dialling bit;

when I installed wvdial, I just pinched a wvdial.conf script from a George Vitas posting; changed the IP details, and all was good;

I understand if after you have installed wvdial and you move on to let it configure, and type

> wvdialconf

that it creates /etc/wvdial.conf but you may need to edit that

so then in Ubuntu you go

> sudo gedit /etc/wvdial.conf

and add what you may need to add

eg what currently works for me is:

> [Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = user
Password = pass
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","*xxx.yyy.co.zz*"
Phone = *99#
Stupid Mode = 1

---

### Post by GeorgeVita on 2010-01-18
Hi **KaiserG** and **pdc**.

Use the following procedure to see system activity when the modem is attached:
- Boot without modem, **wait** for the system to load
- open a terminal window (Applications>Accessories>Terminal) and execute: **sudo dmesg -c**
(this will show all system activity till then and will 'clear' this log. Next simple **dmesg** will show only 'new' activity)
- attach modem, **wait** 30 seconds
- from terminal: **dmesg**
- from terminal: **lsusb**
- copy all output from THE LAST **dmesg** (not from the previous 'sudo dmesg -c') and lsusb, post it here.

Regards,
George

---

### Post by KaiserG on 2010-02-07
Sorry for the late Response vita. Im afraid I have the modem no more. My sister (who bought the modem) saw ubuntu too hard for her, although she liked it. And moved onto MS where the modem is an auto-install thing. (damn MS) Though, I have seen reports that those modems work great in 9.04 and later versions of Ubuntu.
I appreciate all your help, and Im sorry as I can't get further with this thing. I hope anyone out there that is having the same problem as me can solve it with no issues at all. However the modem connected the 2nd time I plugged it so I can mark this thread as SOLVED. Thanks a lot George! You helped a lot!

---

