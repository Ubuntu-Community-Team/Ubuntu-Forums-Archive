---
title: "wxdial -- no dialtone"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by Dr Small on 2009-06-09
I just reinstalled Ubuntu to 9.04 (it was 7.04), and I had previously got this annoying little modem working on it before. It would connect fine, with gnome-ppp, and I was able to browse the web with it. No problem.

I reinstall, install the "alsa-driver-linuxant" deb, and the "hsfmodem_7.80.02.04full_k2.6.28_11_generic_ubuntu_i386" deb. I still couldn't get it to work after those, so I installed the "sl-modem-daemon" package.

This created the symlinks to /dev/modem and /dev/ttySL0 devices. Ok, all fine and dandy. I run:
```
sudo wvdialconf /etc/wvdial.conf
```

And got,
> Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

That told me that it found a modem. I proceeded to edit /etc/wvdial.conf, so it looks like this:
```


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = 0000000
Modem = /dev/ttySL0
Username = user@host
Password = password
Baud = 460800
```

I then run:
```
sudo wvdial
```

And get:
> --> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT0000000
--> Waiting for carrier.
ATDT0223001
NO DIALTONE
--> No dial tone.
--> Disconnecting at Tue Jun  9 12:28:58 2009

So, there you have it. I have no dialtone. Yet, I plug the line back into the phone, pick up on it, and there is a tone. Plug it back into the modem, try to connect, no tone. I am just stumped at what the problem could possibly be. I've been using this modem in the past, and it seemed to work fine, and even wvdial detects the modem drivers.

I'm sorta out of thought at what to do. I've been working on this for several hours now, and finally decided to just give it a whirl to the community.

Any help would be most appreciated,
Dr Small

---

### Post by GeorgeVita on 2009-06-09
Hi **Dr Small**,
insert the parameter **X3** within init2 line:

Init2 = ATQ0 V1 E1 **X1** S0=0 &C1 &D2 +FCLASS=0

This will force the modem to Dial without checking the dial tone.

Also there is a possibility to need an extra line:
**Stupid mode = Yes**
which will try to use ppp connect and then negotiate for user/password.

Regards,
George

---

### Post by Dr Small on 2009-06-10
Thanks for the response, George.
I have tried what you said, and now my wvdial.conf file looks like thus:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 X3 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = Yes
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = 000000000
Modem = /dev/ttySL0
Username = user@host
Password = password
Baud = 460800
```

And then, when running 'wvdial' I don't get anymore "NO DIALTONE" errors. It just sits there and never connects:
> --> Modem initialized
--> Sending: ATDT000000000
--> Waiting for carrier.
ATDT000000000
NO ANSWER

(I have actually reinstalled ubuntu several times now, trying to get this to work, and this time around, I never used scanModem, nor installed the alsa-driver-linuxant or hsfmodem. I only installed gnome-ppp, and sl-modem-daemon, configured wvdial and this is where I am now.

Thanks for all your help. I am really struggling with all of this (as I'm not telephone technition) and I need to get this thing up and running before I go on vacation (where dialup is an only option).

Dr Small

---

### Post by GeorgeVita on 2009-06-10
OK, till we or another reader of this thread give any idea, you should check basic electrical connections.

The problem could be:
a. Audio connection tone generation of the soft modem (driver and setup required)
>>> usually modem cards have a small buzzer/speaker. Do you here the dial tone or DTMF tones while trying to dial?

b. A physical cable connection problem
>>> Hooking up a parallel connected telephone. You must hear a small "click" while starting/ending dial. Best will be to hear the DTMF tones.

c. An external modem is always a better solution!

G

---

### Post by Dr Small on 2009-06-10
Thanks for your help George,
Due to frustration and a recommendation from someone on Identi.ca, I've ordered an external Zoom USB Modem, which had a good review for Ubuntu 9.04. So, hopefully that will help.

As for the audio while dialing, there never was any noise, and as for the cable connection, I don't think it is that, as it works perfect for the telephone, and this is the same line that I used to plug into and it worked before on this laptop. It could very well be a driver problem, or it could be that the modem has finally bit the dust.

Whatever it is, I've got a new modem on the way and I am hoping that it will work right out of the box without any complications. I hate to leave this thread as a dead-end for someone else who may run into the same problem, but I can't for the life of me solve the problem... Oh well.

Thanks again for your help!
(After I get the modem, I'll keep this thread posted as to how it went.)

Dr Small

---

### Post by Dr Small on 2009-06-14
My modem arrived in the mail. I ordered this one from Amazon:
[http://www.amazon.com/gp/product/B0013FDLM0/ref=s9_simz_gw_s4_p23_i1?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=1NVHPZA26MESNPYSRKXV&pf_rd_t=101&pf_rd_p=470938631&pf_rd_i=507846](http://www.amazon.com/gp/product/B0013FDLM0/ref=s9_simz_gw_s4_p23_i1?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=1NVHPZA26MESNPYSRKXV&pf_rd_t=101&pf_rd_p=470938631&pf_rd_i=507846)

It supports Windows/Mac/Linux. I plugged it in, the little green PWR light came on. Plugged in the Phone line, opened gnome-ppp, went to settings, clicked the "Detect" button for the modem device, it found it, saved the settings, and clicked dial. It dialed right away and connected!

The modem may have been 50$, but it was sure worth it to me, so I can have dialup when I go away to my grandparent's house. :)

This thread, although the strange problem unresolved, has been resolved by purchasing a new modem... and I recommend this modem to anyone else who is having modem problems with connecting, or is seeking to buy a modem for a laptop/desktop. This thing works like a champ. Zero configuration! :)

Dr Small

---

