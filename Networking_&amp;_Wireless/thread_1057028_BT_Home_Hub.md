---
title: "BT Home Hub"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by spanglefox on 2009-02-01
Hi all,

Seem to have a real odd problem.

Firstly the hardware: I am having problems connecting an Asus EEE PC 901 to a BT Home Hub (b/g version). The problem seems related to the WEP key.

The version of Ubuntu is 8.04 32-bit.

Using the default key which is in the format of xxxxxxxxxx (where x = is a character. There should be 10 characters there). I am unable to connect to the hub. (ie a 40-bit WEP key) Should I add and extra 2 characters to the password/passphrase (xxxxxxxxxxYY where Y = the new characters) the machine simply hooks up and works fine. In addition when I remove the WEP key the computer hooks up fine.

Unfortunately I cannot run an 8 character key nor a 12 character key as the hub is used to connect devices such as Nintendo DS & wiis. Which only seem to work with a 10 character WEP key.

I have tried Network Manager shipped with Ubuntu and Wicd.

For Network Manager I manage to get one green light before the connection dumps out & in Wicd it sticks at obtaining IP address.

Any help would be greatly appreciated! :D

---

### Post by spanglefox on 2009-02-08
this has been solved by installing 8.10 with its new option of 40/128 bit key; however, I have not tested using a 64 bit key on the new system.

From what I have seen from other posts I suspect that 64 bit will fail.If this is the case what is the technical obstacle that prevents linux using a purely variable length WEP key? The "other" operating system out there seems to deal with any length WEP keys perfectly fine, which begs the questions as to why Linux, unfortunately, cannot?

On a personal rant: I would love to see Linux being able to cope with such a demand. Not only to simply answer a purely selfish wish of having my equipment work, but if, like me, you wish to see Linux one day being a mainstream operating system then this is a stumbling block that should be overcome.

Many thanks to those who have read my post.

---

