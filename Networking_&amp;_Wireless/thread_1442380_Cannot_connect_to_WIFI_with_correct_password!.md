---
title: "Cannot connect to WIFI with correct password!"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by tyling81 on 2010-03-29
Hi, I'm using Ubuntu 9.04 on my eee pc 901, as mentioned above, I been trying to connect to my home WIFI(WPA enable) yet it keep asking for password, any idea?

---

### Post by 2hot6ft2 on 2010-03-29
> **tyling81 said:**
> Hi, I'm using Ubuntu 9.04 on my eee pc 901, as mentioned above, I been trying to connect to my home WIFI(WPA enable) yet it keep asking for password, any idea?
Click on Cancel then

Right click on the network manager applet in the top panel and select Edit Connections
Select Wireless then your connection, then Edit
Enter your password
Click on Wireless Security
Put in your passkey and click Ok.

Wait to see if it connects
If it does click Close
If it doesn't put it in again.

No guarantee, but sometimes it works.

---

### Post by tyling81 on 2010-03-30
It kinda weird, that I could connect with other WIFI but not my home WIFI, any assistant would be appreciate, as My Home WIFI is WPA2 TSK enable.

---

### Post by pauldast on 2010-03-31
I ma having the same issue here.  There are 2 home wireless networks that I use regularly that I can't connect to as of late but I have never had any trouble connecting to my school network.

---

### Post by Grez on 2010-03-31
Same here.

It's been fine, but isn't playing ball anymore.

Any ideas anyone?

(BTW same USB dongle works fine on same network with my Ubuntu Hardy Box!)

---

### Post by fredthomke on 2010-04-12
Same here.  Xubuntu 9.10, on a Dell laptop with a PCMCIA card.  If I set my home router so it is NOT secure (no encryption) then I can connect just fine.  If I secure my router in ANY manner (WEP, WPA, WPA-PSK) with any appropriate key, then my Xubuntu laptop cannot connect to it.  

The laptop "sees" the router just fine.  When I try to connect to it by left-clicking the Network-Manager icon and choosing my SSID from the list, it asks for a password key, which I dutifully type in.  But no joy.  I've tried short keys, long keys, all-number keys (like 1234567890) all to no avail.  But as soon as I disable the router's Wifi security, I connect IMMEDIATELY!

What's up??  This is also the same if I use "wicd" instead of "network-manager".

Any one ever get this to work with WPA security?

---

### Post by diogenes_3 on 2010-04-13
My Netbook, at this time running 10.04 UNR Beta 2, is currently unable to connect to my home network using WPA2 encryption. When I reluctantly downgraded it to WPA, it worked. Needless to say it has worked before and works on the alternate Windows partition... Network out-of-the-boxness, I am sorry to say, seems to be a gamble with every new Ubuntu release.

For me as a barely-not-complete-fool type of user that means lots of toying with settings. OK, so I asked for it, installing a Beta and so...

---

### Post by whistl3r on 2010-04-24
I have got the same problem. Both on my netbook and my laptop.

---

### Post by Txakurra on 2010-05-30
> **whistl3r said:**
> I have got the same problem. Both on my netbook and my laptop.

Hi there,

Had a similar problem and solved it by following these instructions:

[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

Good luck.
Didier

---

