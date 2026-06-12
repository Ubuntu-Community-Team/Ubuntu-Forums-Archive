---
title: "wvdial and ppp options file"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by David J Bush on 2009-05-10
I am trying to get wvdial to work on my Kubuntu 9.04 amd64 system. Attached is the console output of a session. It tells me of a problem with ppp options. Also attached is the /etc/ppp/options file which I renamed options.txt for uploading. I tried auth, I tried noauth, both ways gave me the same error code 2, indicating an options problem. The options which are not commented out are:

asyncmap 0
auth
lock
hide-password
modem
lcp-echo-interval 30
lcp-echo-failure 4

I do not have a ~/.ppprc file nor an /etc/ppp/options.ttyUSB0 file.

What is the problem with my ppp options? Or could there be a problem with wvdial?

Thanks!

---

### Post by GeorgeVita on 2009-05-10
Hi **David J Bush**,

I had some problems to connect via Puppy-Linux with Huawei modems (E220, E170, E169) resulting to **error code 2**.

I solved this by creating the file: **/etc/ppp/peers/wvdial**
containing:
[B]noauth
name wvdial
usepeerdns
[/B]
I don't know the differences between Puppy & Ubuntu.

My /etc/wvdial.conf was:

[B][Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = user
Password = password
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","internet"
Dial Attempts = 1
Phone = *99#
Stupid Mode = 1
[/B]

Hope something of the above will help you,
George

---

