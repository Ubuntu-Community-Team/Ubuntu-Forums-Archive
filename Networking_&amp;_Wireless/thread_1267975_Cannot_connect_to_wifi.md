---
title: "Cannot connect to wifi"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by PinkZeppelin on 2009-09-16
Hey

I just installed Ubuntu netbook remix on my Eeepc 901. I cannot connect to my wireless internet.

Two computers are connected that the wireless internet access, and they run on vista.

When I connect, ubuntu prompts me a passphrase, i enter the exact same one that the other computers connect with. The little animation on the top left corner then just goes on and on. Only one green light is lit, the other one is grey.

Any help would be very welcome :)
Thanks,

RP

---

### Post by CoolHand on 2009-09-16
There are a bunch of things I would check.  First open a terminal and type iwconfig and see what info that gives you.  Try to determine if you are connecting to the AP at all.  I've had similar issues in the past and found I was connecting but not getting a DHCP address.  You can configure a static address to check that.  It's also possible your key isn't translating right.  Try entering the HEX version of the key.  If you don't know it you can convert it here in the custom section:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

Good luck

---

### Post by PinkZeppelin on 2009-09-16
Thanks for your reply,

Here's what iwconfig says:

> lo        no wireless extensions.



eth0      no wireless extensions.



ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"

          Mode:Auto  Frequency=2.442 GHz  Access Point: Not-Associated   

          Bit Rate:1 Mb/s   

          RTS thr: off   Fragment thr: off

          Link Quality=10/100  Signal level:-84 dBm  Noise level:-97 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



pan0      no wireless extensions.


Im, sorry Im not very good at this, but I dont know how to figure out if Im connectin gto the AP or how to configure a static address to check if im getting a DHCP address.

Thanks again,
RP

ps Thanks for the link
I tried it out, it didnt work, but i may have done something wrong.

---

