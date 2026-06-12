---
title: "How to connect to wireless network via terminal?"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by tranduyhung on 2010-12-28
Hi!

I wonder how we can to connect a wireless network via terminal if we use a minimal *buntu in command line, without network manager. I've found some old threads in ubuntuforums but I still can't figure out.

Would you please explain to me?

Thank you :).

Best regards,
Hung

---

### Post by spiky001 on 2010-12-28
Hi to start you can scan from Terminal with the command ```
sudo iwlist wlan0 scan
```   Then try ```
iwconfig wlan0 essid NETWORK_ID key s:WIRELESS_KEY
``` Where NETWORK_ID is name of network, And WIRELESS_KEY is the key. Then ```
sudo dhclient wlan0
``` Wlan0 is your wireless device

---

### Post by kevdog on 2010-12-28
I wrote a tutorial on this a ways back -- yes it is old if using computer standards, however the information contained in it still works and is truly a low level way of connecting that shouldn't change unless the wireless tools package is dropped from the linux kernel (which would be rather an outstanding event!!)

---

### Post by tranduyhung on 2011-01-03
When I tried "iwconfig wlan0 essid network_name key s:network_password", I got this error:
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.

And then I used sudo, but there was something wrong:
$ sudo iwconfig wlan0 essid network_name key s:network_password
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

What did I do wrong? How could I fix?

Thank you!

---

### Post by tranduyhung on 2011-01-07
Help please :).

---

### Post by aflyingturtle on 2011-01-22
Don't suppose you ever figured it out? I'm trying to figure it out too.

---

### Post by dennis1200 on 2011-06-16
I've gotten that error as well, but only when trying to pass hexadecimal keys with the s: prefix. You may not need the s: prefix at all. It may also be related to trying to enter a WPA/WPA2 passphrase, which is described here:
[http://www.cyberciti.biz/tips/howto-debian-ubuntu-linux-wlan-wpa2-configuration.html]("http://www.cyberciti.biz/tips/howto-debian-ubuntu-linux-wlan-wpa2-configuration.html"), which suggests using iwpriv as well (not familiar with it).

---

### Post by tliimfee on 2013-04-24
Hey,

I don't know if it's still relevant but I was having the same problem and read in the manual that with iwconfig(8) ""Passphrase is currently not supported.", which was why I was getting the error.

This tread shows you have to connect via terminal with a passphrase:
[http://askubuntu.com/questions/16584/how-to-connect-and-disconnect-to-a-network-manually-in-terminal](http://askubuntu.com/questions/16584/how-to-connect-and-disconnect-to-a-network-manually-in-terminal)

---

### Post by wildmanne39 on 2013-04-24
Thread closed. Please do not post in old threads.

---

