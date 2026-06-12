---
title: "WEP key not working?"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by Sternfan on 2006-06-06
Hi all,

New to k/ubuntu.  

Problem - I have an old laptop that I used to run fedora 4 on.  Thought I would try kubuntu 6.  The wireless used to work, but now is giving me fits.  I can verify that wireless is working on my other laptops.

One the Kubuntu laptop, I can see SSIDs, so I know the card is working and getting signal.  I go to put in my WEP encryption key, and it will not connect.  Tried it with both the Network settings and the Wireless assistant.  Tried it in Hex and in ascii.

Is there something I am missing with the WEP key?  I put it in this format 0x12345F8 etc.  Should there be dashes?  Should it be in CAPS?  Should I be using the Network Settings or the Wireless Assistant?

Any and all help appreciated,
Rob

---

### Post by rbalfour on 2006-06-06
the format is 12345F8
you don't put the 0x in front. just make sure you select, hex and not plain ascii.

---

### Post by ness0216 on 2006-06-06
I have the same problem. I can see the AP but when I try to set the wep key it never takes. Let me know if you find a solution.

---

### Post by M.a.d on 2006-06-11
Yes, me too. My wireless connection works perfect but when I enable WEP it won't connect. The key is valid Im sure, as it is used by other (Windows) machines on the network.

I am, WE are I guess, really interested in hearing from somebody who might know what the problem is..!

Until then I'll just keep searching and searching and trying and trying... :)

---

### Post by ex-guru on 2006-06-11
M.a.d., have you found a solution for the problem? If you have, please let me know.
I have the same problem with Ubuntu 6.06: without WEP encryption I have perfect access, which vanishes when I enable the encryption.
Thanks a lot for any help!

---

### Post by rbalfour on 2006-06-11
[QUOTE=M.a.d]Yes, me too. My wireless connection works perfect but when I enable WEP it won't connect. The key is valid Im sure, as it is used by other (Windows) machines on the network.

I am, WE are I guess, really interested in hearing from somebody who might know what the problem is..!

Until then I'll just keep searching and searching and trying and trying... :)[/QUOTE]

Post a screen shot of your current setup.

This is what my /etc/network/interfaces looks like

iface eth1 inet dhcp
wireless-essid tokyomod
wireless-key 52A7608B1B

---

### Post by ex-guru on 2006-06-11
Editing /etc/network/interfaces seems to have worked in my system! I'm connecting nicely with encryption activated. Thanks rbalfour!

---

### Post by fredbro on 2006-07-19
A followup question?

Should the aphabetical characters all be capitalized even if the
is a combination of upper and lower case letters?

Thank you, fred bro

---

### Post by tturrisi on 2006-07-19
try this format of a hyphen after every 4 CASE SENSITIVE characters:

abcd-efgh-ij

---

