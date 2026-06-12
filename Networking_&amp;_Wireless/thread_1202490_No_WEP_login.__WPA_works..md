---
title: "No WEP login.  WPA works."
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by chip616 on 2009-07-02
I'm using Kubuntu 8.04 on all my machines, and no matter what I do, I cannot get any of my laptops to log in to a WEP network.  They all work fine with WPA encryption or an unlocked network.  This includes two Dells and an Acer eeepc 901 with the array kernel, so this is not a hardware or driver issue.  I've tried them on two different WEP protected networks.  They see the network, begin the login process, but ultimately fail.

What am I doing wrong?

Frank.

---

### Post by chip616 on 2009-07-02
OK, figured it out.  Now I feel stupid.  :(

For the benefit of others that might be as stupid as me, here is how it works.

WEP on my router allows a 40 bit hex key, or a 128 bit hex key, or a passphrase that the router will convert to a hex key.

40 bits is 5 bytes (at 8 bits to the byte).  This translates as 5 ASCII characters, or 10 hex digits.  this could be, for example ABCDE, which, as hex, would be 41:42:43:44:45.  However, both the router and KNetworkManager don't use the colons.  Therefore, the hex key equivalent of ABCDE is 4142434445 plain and simple.

KNetworkManager has three options for inputting the WEP key.  The first is WEP Passphrase.  This is expecting a 5 character (40 bit) UPPER CASE key, like ABCDE.  If you type in abcde it will convert it to ABCDE.  This really messed me up until I found out that this conversion was taking place.  :)

The next is 40/104-bit hex.  If you choose this, then the above passphrase has to be keyed in as 4142434445 in order to work, as this is the hexadecimal equivalent of ABCDE.

The final option is 40/104 bit ASCII.  This too is expecting a 5 character passphrase, but it will accept it as you type it in without any conversion.  Here you can enter lower case ascii characters, and they will NOT be converted to upper case.  For instance, if the passphrase set on your router is abcde, option 1 in KnetworkManager WILL NOT WORK as it gets converted to ABCDE.  However, in option 3, you can type in abcde and it will remain in lower case.

Now why the boys at KDE set it up this way is beyond me.

In any case, the issue I was having with the networks that I was trying to connect to is that I was providing the correct password, but in the wrong format.

Hope this is of some help to others.

Frank.

---

