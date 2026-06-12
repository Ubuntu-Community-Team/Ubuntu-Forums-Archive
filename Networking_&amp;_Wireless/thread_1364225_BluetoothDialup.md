---
title: "BluetoothDialup"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by atheistrical on 2009-12-25
This is a followup from the following useful post/wiki

[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)

I was in fact successfully connected to my laptop using my nokia E51 internet over bluetooth. The speed was great (3G)!! Was very grateful to the above post/wiki until I turned my laptop off!!!

When I turned my laptop back on, things started to appear weird

**My Configuration**

```

HP-Pavilion DV4 Laptop
Ubuntu 9.04 (Jaunty Jackalope)
2.6.28-11-generic Kernel

```**The error**

```

atheistrical@atheistic:~$ sudo pon ab
atheistrical@atheistic:~$ plog
Dec 26 01:04:24 atheistic pppd[3791]: pppd 2.4.5 started by root, uid 0
Dec 26 01:04:27 atheistic pppd[3791]: Failed to open /dev/rfcomm0: Connection refused
Dec 26 01:04:27 atheistic pppd[3791]: Exit.
Dec 26 01:05:05 atheistic pppd[3800]: pppd 2.4.5 started by root, uid 0

```I started to troubleshoot, I tried search engines which led me to

```

atheistrical@atheistic:~$ sudo service bluetooth restart
[sudo] password for atheistrical: 
 * Stopping bluetooth                                                    [ OK ] 
 * Starting bluetooth                                                    [ OK ] 
atheistrical@atheistic:~$ sudo rfcomm release 0
atheistrical@atheistic:~$ sudo rfcomm
atheistrical@atheistic:~$ sudo rfcomm bind 0
atheistrical@atheistic:~$ sudo rfcomm
rfcomm0: 00:1D:FD:F5:01:7D channel 4 clean 
atheistrical@atheistic:~$ sudo pon ab
atheistrical@atheistic:~$ plog
Dec 26 01:18:25 atheistic pppd[4455]: pppd 2.4.5 started by root, uid 0
Dec 26 01:18:28 atheistic pppd[4455]: Failed to open /dev/rfcomm0: Connection refused
Dec 26 01:18:28 atheistic pppd[4455]: Exit.

```Here are my file contents of

**/etc/bluetooth/rfcomm.conf**

```

#
# RFCOMM configuration file.
#

rfcomm0 {
#    # Automatically bind the device at startup
bind yes;
#
#    # Bluetooth address of the device
device 00:1D:FD:F5:01:7D;
#
#    # RFCOMM channel for the connection
channel    4;
#
#    # Description of the connection
comment "Atheist's Bluetooth";
}

```
I shall post the contents of other relevant files if required.

However, my big question is:

When the connection worked for the first time, why does it refuse to connect upon restart? My phone is already paired and authorized to accept connection without prompting for the pin. Out of curiosity, I tried:-

```

atheistrical@atheistic:~$ sudo aptitude install bluez-pin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "bluez-pin"
Couldn't find any package whose name or description matched "bluez-pin"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 276 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```This error seems to be a very notorious one from what I discovered over different internet forum postings. No clean resolution found anywhere!!

I believe that you guys definitely will crack this one. Thanks for the slightest help, or even reading this through.

---

### Post by chewearn on 2009-12-25
I'm not sure if my suggestion would help, just want to throw out a suggestion.

I have a similar bluetooth dial-up set-up on a Nokia N95.  Sometimes, the phone crashed for unknown reasons, which caused the[FONT=monospace] [/FONT]RFCOMM channel is changed to another.

You could edit the rfcomm.conf file to reflect the new channel, or you could reset the phone to bring it back to it original channel.

---

### Post by atheistrical on 2009-12-25
> **chewearn said:**
> I'm not sure if my suggestion would help, just want to throw out a suggestion.

I have a similar bluetooth dial-up set-up on a Nokia N95.  Sometimes, the phone crashed for unknown reasons, which caused theRFCOMM channel is changed to another.

You could edit the rfcomm.conf file to reflect the new channel, or you could reset the phone to bring it back to it original channel.

Well, I have always monitored the change in channel number (DUN in my case)

```

sdptool search DUN

```

I am using the correct channel number, I'm sure! Thanks for the response.

---

