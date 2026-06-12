---
title: "No DHCPOFFERS after Upgrade to 8.04"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by mpref on 2008-12-21
Hi,

I had my WLAN USB-Stick running under 7.10 perfectly well -- and used it recently to upgrade to 8.04. That was the last time it worked, now **iwlist scanning** gives: 

```

wlan0 Scan completed:
      Dell 01 - Address: 00:1a:2a:29:58:19
                ESSID:"CasaMama"
                Protocol:IEEE 902.11g
                ...
                IE: IEEE 802.11i/WPA2 Version 1
                    Group Cipher: TKIP
                    Pairwise Ciphers (2): TKIP CCMP
                    Authentication Suites (1): PSK
                ...

```

So, everything looks fine just like under 7.10, but I can't connect to the internet. Calling **sudo dhclient wlan0** outputs

```

DHCPISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.

```

Anybody got an idea -- besides going back to 7.10. (That is not really an option, since I need the more recent kernel for the latest version of truecrypt.)

I'd gladly provide more information, but at the moment I have to type them with other computer, in the next room.

Thanks in advance.

---

### Post by gnusci on 2008-12-21
I will recommend you to change the encryption method, since for some reason the new driver doesn't support the actual encryption method for your network interface. Once you have the connection working you can try to get an appropriate driver.

Could you please post the output of the following commands:

[B]$ lsusb
$ lsmod[/B]

BTW, give a look to the following post to get more useful information from your interface, so help you will be easier.

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by mpref on 2008-12-21
Hi gnusci,

thanks for your quick reply. For **lsusb** I get the following reply:

```

Bus 005 Device 003: ID 0572:2002 Conexant System (Rockwell), Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 0572:2002 Dell Computer Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

I tried to extract the useful information from **lsmod** by applying

```

$ lsmod | grep "wlan_module_name"

```

according to your post at [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)
But unfortunately I faild with "wlan0", "ndiswrapper" and "Conexant" for the "wlan_module_name". I guess, I missed something pretty obvious.

Ah, there is something interesting. Reading on in your post, tried **iwconfig wlan0** and received

```

wlan0	No such device

```

Checking with **iwconfig** I found only

```

lo	no wireless extensions.
eth0	no wireless extensions.

```

Isn't that strange, now **iwlist scanning** also yields

```

lo	Interface doesn't support scanning
eth0 	Interface doesn't support scanning

```

I guess, that's worse than before -- but I am quite sure about the output I posted first?!:P:P

---

### Post by mpref on 2008-12-21
OK, it seems like I can at least get a handle on the last problem.

After

```

sudo wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -B

```

the **iwlist scanning** returns what I described in the first post.

So, now back to your proposal: You proposed to change the encryption to get a connection to look for a driver which would support the WPA2 encryption that I want to use. But couldn't I download the appropriate driver with another machine and transfer it via USB-Stick?! The only problem I see is, that I do not know of any alternative driver. I used the one for Windows and included it via the ndiswrapper. I don't see any alternatives here?!

---

