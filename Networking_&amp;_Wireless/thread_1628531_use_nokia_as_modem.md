---
title: "use nokia as modem"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by cold0zero on 2010-11-22
how i can use my nokia E52 as a modem in ubuntu 10.10 to surf net

in windows i use nokia pc suite and connect my phone by usb cable and connect

---

### Post by cold0zero on 2010-11-22
plz help i can't use internet only by my mobile and my 3G sim card and i don't have a 3G modem

---

### Post by cold0zero on 2010-11-23
no one answer me ?

---

### Post by SecretCode on 2010-11-23
DOes the E52 have a setting to enable internet sharing / modem?

When I connect my HTC Android phone to Ubuntu 10.10 and select "Internet sharing" in the **phone's** USB menu, it pops up as "Auto eth0" in Ubuntu (no settings required).

by the way, you should wait 24 hours before bumping your thread

---

### Post by dethorpe on 2010-11-23
I use an N95 in 9.10 and was basically plug and play. 

Might be same for you if E52 is supported same way in Network Manager. These are the steps i used:

1 ) Connect Phone with USB, select PC Suite Mode on phone (even though you are not using PC suite as that is windows only).
2) Open Network Manager on Ubuntu,  should show entry for mobile broadband.
3) Select Mobile broadband entry and use wizard to select details for network (i used vodafone)
4) Should now be able to select entry and connect to internet from network manager.

Hope that helps

---

### Post by cold0zero on 2010-11-24
not work with me

---

### Post by quadra on 2010-12-11
Hi. On my Ubuntu 10.04, it worked, but I had to actively add the connection.
1) Connect Nokia E52 via usb cable. Select PC Suite mode(!)
2) **Right-click** network manager icon, **Edit connections** (or System - Preferences - Network connections)
3) Tab "Mobile Broadband" - Add. "Nokia E52" is shown in the list. Go through the wizard
4) Now, I could connect smoothly by enabling this broadband connection.

---

### Post by mosaic2s on 2010-12-12
using 10.04.
Today I tried MTNL 3G Sim card. Worked without any issues.

Plugged in nokia E52 using pc suite mode. Network connections - mobile broadband. Selected operator. Thats it.
Tried Idea Cellular - non 3G - works ok.

---

### Post by Rikoos on 2010-12-13
Same problem here BUT on my netbook the problem started after upgrading to 10.10

Connection works thru windows but on 10.10 it will not recognize my Nokia E60 while usb-devices shows it is connected thru USB.

Some how the network assistent will not use my Nokia 3G connection.

---

### Post by mosaic2s on 2010-12-13
Use 10.04. It works. Will not trade it for fancy features for 10.10.

---

### Post by prat22 on 2010-12-15
[B]I am strugling with samsung c3010. 10.04 doesnt eneble mobile broadband, every time I click to eneble, it disables automatically. I tried with kppp, but it hangs up after showing connecting to network. 
Any ideas?
I am using Airtel 2g.
[/B]

---

### Post by seydou on 2010-12-18
> **cold0zero said:**
> not work with me

Well, Network manager does not work for me either, as I do not have it installed :-). Nonetheless, there is a sort of bullet-proof way how to connect, but you need to go down to the terminal window and fiddle in the terminal window. All you need is wvdial, so make sure you have it installed.

```
sudo apt-get install wvdial
```

1/ Connect the phone and switch to PC Suite
2/ Fire up terminal, and do

```
sudo su -
```

3/This brings you to root console. Now, check out what is going on with the kernel:

```
dmesg
```

Look for following lines

```

[  331.939066] usb 2-2: new high speed USB device using ehci_hcd and address 7
[  332.055474] cdc_acm 2-2:1.1: ttyACM0: USB ACM device
[  332.056465] cdc_acm 2-2:1.3: ttyACM1: USB ACM device

```

This is to say our modem has created a device /dev/ttyACM0. Alternative way to find it out is

```
ls /dev|grep ACM
```

4/ Open up /etc/wvdial.conf (if you do not know vim editor, learn it, it is a great tool)

```
vi /etc/wvdial.conf
```

and make sure it contains something like this:

```

[Modem1]
Modem = /dev/ttyACM0
Baud = 460800
SetVolume = 0
Dial ***mand = ATDT
Init1 = ATZ
Init3 = ATM0
FlowControl = NOFLOW

[Dialer nokia]
Username = user
Password = password
Phone = *99#
Stupid Mode = 1
Init1 = ATZ
Inherits = Modem1

```

Check the username, password and phone number with your operator. Note that even if they do not require username and password, you can not leave those two items blank, so having it like this is just fine. Save the file and go connected.

4/ Configuration is persistent, the only thing you need to do (in root console) is

```
wvdial nokia
```

You should be live in a few secs, check out the console output, wvdial is pretty eloquent. The console is blocked by wvdial, so do not close it or you loose the connection. Open up firefox and check if you are online.

When you finished, just type Ctrl+C in the root console and the connection ends. Alternatively, you can fire up wvdial like this

```
wvdial nokia &
```

This puts it to the background and you can exit the console. Terminate the connection with

```
sudo killall wvdial
```

This way has many advantages to Network Manager, as you would have plenty of debugging info from either dmesg or wvdial.

If for example vwdial says no dial tone, change dial ***mand to ATXDT. The dial number might differ as well (could be #777 for example), so check with your operator for correct format.

Hope it helps.

---

### Post by waldherrvonbirnbaum on 2012-04-18
with nokia 6600 fold it works great. i had to restart my nokia and everything was ok. i use ubuntu 11.10.
with bluetooth it also worked but it interrupted the co connection frequently. for checking mail and searching for a solution it was enough.

---

