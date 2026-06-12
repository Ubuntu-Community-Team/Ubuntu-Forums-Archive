---
title: "PDANet (v2.45) - Desire HD - Bluetooth DUN - HowTo?"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by ghost_zero on 2011-02-03
Hi,

I want to get my Desire HD to connect to the Internet over Bluetooth DUN by using my Desire HD and PDANet v2.45.
I don't want to use Wireless because of the power requirements.

I am using Ubuntu 10.10 64Bit

I tried to enable the DUN option after adding the phone to my Bluetooth devices but it fails with an error like "cannot retrieve configuration" (or however that one is called).

So I decided to try to get this to work manually by using sdptool to find the DUN channel, rfcomm to bind it to /dev/rfcomm0
and then I tried using wvdial to connect.

And here I run into problems:
1.) Most of the time it doesn't connect and is stuck after starting pppd
2.) In the unlikely case that it indeed does connect, it takes way longer than e.g. under Windows to do so.
3.) Also if it works, the speed is terrible slow. My old ISDN connection was way faster. 
However, under Windows - also using Bluetooth - this is not an issue.

I also tried to connect through pppd and chat script only.
However, there I have the problem that I either don't get a reply (I do so by using wvdial and also tested it with cutecom) 
or that the chat script doesn't send the commands correctly or the reply is a bit different or something like this
because it is stuck at the first "Expecting (OK)".

Regarding wvdial.conf I tried some variations but I think the issue is either resolved by changing the modem tty settings by using stty or by changing the pppd settings.
Nevertheless this would be my current wvdial.conf (after looking at what modem commands Windows is calling when connecting over PDANet):
```

[Dialer Defaults]
Phone = #777
Init1 = AT
Init2 = ATE0V1&D2
Init3 = AT
Init4 = ATS0=0
Init5 = AT
Init6 = ATE0V1&D2
Init7 = AT
Modem Type = Analog Modem
Stupid Mode = on
New PPPD = yes
SetVolume = 0
Dial Command = ATDT
Baud = 115200
Username = blank
Password = blank
Dial Attempts = 0
Modem = /dev/rfcomm0

```

Regarding pppd settings I tried to change them by using the /etc/ppp/peers/wvdial and /etc/ppp/options but I don't really know to what, so it has been kinda fruitless.

Maybe there is some other way to get this to work or somebody knows how to configure everything?

---

### Post by SwarfEye on 2011-02-10
I am having the exact same problem, except that I am trying to use bluetooth DUN with PDAnet and a HTC Incredible.


Clearly this is an Ubuntu issue, not a PDAnet or Android issue.  I have seen instructions for how to do this that make it appear that this worked just fine in Ubuntu 9.04.  I have never heard of anyone getting this to work in 10.10.

Perhaps I will try a 9.04 installation and see if I can get it going there?

B

---

