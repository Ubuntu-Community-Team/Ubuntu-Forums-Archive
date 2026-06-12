---
title: "56k modem install help"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by spaceboy909 on 2009-02-13
Modem:  **[SIZE=1]Rosewill RNX-56USB Conexant Hardware Based[/SIZE]**

Distro: Latest Xubuntu 8.10 CD install.  (Have not been online yet for updates)

Box: AthlonXP 1800, 512Mb Corsair, Shuttle mainboard

I have been to linmodems and downloaded and ran 'scanmodem'.  It pointed me to the 'dgc' drivers, which I installed, but I still can't find any sort of properties panel for the modem.  Normally, IIRC, it is in the networking properties box with everything else, but it's not there this time.

So, how do I access the modem properties so I can begin testing of the modem?

---

### Post by ModelM on 2009-02-13
Your modem is at

/dev/ttyACM0

This is a hardware modem. No driver is required.

The instructions in [_this thread](http://ubuntuforums.org/showthread.php?t=1056659)_ should get you up & running. Your modem is different, but it won't matter, just follow the instructions.

---

### Post by spaceboy909 on 2009-02-13
Ok, thanks.  I won't be able to work on it again until monday or tuesday.  I'll post again with the results.

---

### Post by Snort44 on 2009-03-16
I have almost succeeded in getting this modem online. Both lights are showing activity for a while and then go off.

In Kubuntu 8.10 I did the following:
1-  sudo wvdialconf
2-  sudo kate /etc/wvdial.conf
2.5-  in kate I updated the Phone, Password, and Username and saved the file and closed kate.
3-  alt-f2 and enter wvdial Defaults
the modem started responding with the lights.  I waited about a minute and opened the browser which is the stock one in Kubuntu and not Firefox.  Efforts to open a web page gave an error and then the modem lights went out.

I feel I'm almost there but don't know what to do next.  Help please and thanks.

---

### Post by Snort44 on 2009-03-16
I forgot to include my wvdial.conf

```


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = 1234567890
Password = ********
Username = emailaddy
; Stupid mode = 1


```

---

### Post by ModelM on 2009-03-16
For the dial command, try

gksu wvdial

or, in a terminal the command would be

sudo wvdial

---

