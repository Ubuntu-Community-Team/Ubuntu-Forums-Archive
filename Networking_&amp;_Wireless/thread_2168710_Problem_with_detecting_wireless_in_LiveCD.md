---
title: "Problem with detecting wireless in LiveCD"
date: 2013-08-19
forum: Networking &amp; Wireless
---

### Post by jechadwell99 on 2013-08-19
I am a total linux noob so please do not post complicated answers.

I am running an old(ish) HP laptop that came pre-installed with Windows Vista. I hate Windows Vista so I started searching for an alternate OS. I discovered Ubuntu. I prepared a LiveCD (with Ubuntu 12.04 32-bit) and put it into the computer. It worked fine as far as I can tell. I like Ubuntu so much I decide to install it. It's then that I discover I am not connected to the internet. I spent the next hour or so trying to connect to the internet. I can't. Even the little light on the bottom of my laptop that shows that my Wireless thing is on is off. I shut down Ubuntu, go back to Vista and I can access the internet as much as I like from there. The Wireless light comes back on. It just won't work from Ubuntu. I have tried lots of things from different forums (including this one) but none of them seem to work.

Somebody please help me out!!! :(

---

### Post by carl4926 on 2013-08-19
Please open a terminal and post for us the result of

```
lspci -nnk
```

---

### Post by jechadwell99 on 2013-08-19
I have attached a picture of what it did. Is that what you wanted?

PS. Sorry about the picure quality, I had to take with my iPod because I have no Internet connection from my laptop.

---

### Post by jechadwell99 on 2013-08-19
Sorry about sending the picture, I found a way to get it from Ubuntu LiveCD to Vista where I have a connection. Here is what I got:

ubuntu@ubuntu:~$ lspci -nmk
00:00.0 "0500" "10de" "0547" -ra2 "103c" "30cf"
00:01.0 "0601" "10de" "0548" -ra2 "103c" "30cf"
00:01.1 "0c05" "10de" "0542" -ra2 "103c" "30cf"
00:01.2 "0500" "10de" "0541" -ra2 "" ""
00:01.3 "0b40" "10de" "0543" -ra2 "103c" "30cf"
00:02.0 "0c03" "10de" "055e" -ra2 -p10 "103c" "30cf"
00:02.1 "0c03" "10de" "055f" -ra2 -p20 "103c" "30cf"
00:04.0 "0c03" "10de" "055e" -ra2 -p10 "103c" "30cf"
00:04.1 "0c03" "10de" "055f" -ra2 -p20 "103c" "30cf"
00:06.0 "0101" "10de" "0560" -ra1 -p8a "103c" "30cf"
00:07.0 "0403" "10de" "055c" -ra1 "103c" "30cf"
00:08.0 "0604" "10de" "0561" -ra2 -p01 "" ""
00:09.0 "0101" "10de" "0550" -ra2 -p85 "103c" "30cf"
00:0a.0 "0200" "10de" "054c" -ra2 "103c" "30cf"
00:0c.0 "0604" "10de" "0563" -ra2 "" ""
00:0d.0 "0604" "10de" "0563" -ra2 "" ""
00:12.0 "0300" "10de" "0531" -ra2 "103c" "30cf"
00:18.0 "0600" "1022" "1100" "" ""
00:18.1 "0600" "1022" "1101" "" ""
00:18.2 "0600" "1022" "1102" "" ""
00:18.3 "0600" "1022" "1103" "" ""
02:05.0 "0c00" "1180" "0832" -r05 -p10 "103c" "30cf"
02:05.1 "0805" "1180" "0822" -r22 "103c" "30cf"
02:05.2 "0880" "1180" "0592" -r12 "103c" "30cf"
02:05.3 "0880" "1180" "0852" -r12 "103c" "30cf"
03:00.0 "0280" "14e4" "4311" -r02 "103c" "1375"

Does this help?

---

### Post by carl4926 on 2013-08-19
No
Because you did it wrong

lspci -nnk

not : lspci -nmk

---

### Post by chili555 on 2013-08-19
Carl-

I think this is the thing you need:> 03:00.0 "0280" "[COLOR="#FF0000"]14e4[/COLOR]" "[COLOR="#FF0000"]4311[/COLOR]" -r02 "103c" "1375"That's a Broadcom 4311 wireless card and he wants firmware. It's pretty bad when a guy can read PCI identifiers and see the card! I can't help it.

---

### Post by carl4926 on 2013-08-19
> **chili555 said:**
> Carl-

I think this is the thing you need:That's a Broadcom 4311 wireless card and he wants firmware. It's pretty bad when a guy can read PCI identifiers and see the card! I can't help it.

You are correct
I just didn't have time to sit and wade thru all that garbage

@[COLOR=#000000]jechadwell99
This wireless will work post install
To make it work in a live session you can copy this folder to /lib/firmware
[/COLOR]https://dl.dropboxusercontent.com/u/10573557/b43_firmware/2013_b43/b43.zip
You need to extract the folder and copy it over
You may need to modprobe it, I usually have to

Or, if you have a wired connection
I think it's
```
[COLOR=#000000][FONT=courier]sudo apt-get install firmware-b43-installer[/FONT][/COLOR]
```

---

### Post by jechadwell99 on 2013-08-20
OK thank you. The Broadcom 4311 wireless card will not interfere with a wired connection will it?

---

### Post by carl4926 on 2013-08-20
> **jechadwell99 said:**
> OK thank you. The Broadcom 4311 wireless card will not interfere with a wired connection will it?
No

---

