---
title: "Wireless interface missing"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by davinamarie on 2010-03-06
Hi there, I bought my fiance a dell laptop.  It used to work on our wifi but now it doesn't.  When I look at the Network Settings there is only "Wired connection" and "Point to point connection".
 
I have looked through lots of help subjects and it seems the wireless interface is missing?  I really don't know how this has happened, I've tried for hours to try and get it to work but to be honest it's just like a foreign language... I have never used this kind of OS before.
 
Please can someone help?

---

### Post by avguy on 2010-03-06
well, if it is a adapter, i know your problem. I just solved it myself. What you have to do is get the package ndisgtk. It can be obtained through synapatic. If not, got to packages.ubuntu.org. or whatever the packages site for ubuntu is. Anyway, if you get it off the site, you need to get ndiswrapper commons and 1.9. Then use archive manager to install these stuff. It should install something called Wireless Drivers, or something like that. It can be found under systems-administration. Then get your adapter installer disk and google the files you need to install for it to recognize, find, and use your adapter.

---

### Post by davinamarie on 2010-03-06
Sounds great! Wish I understood what you were telling me lol.  Any chance you could go through that step by step?

---

### Post by bkratz on 2010-03-06
Ndiswrapper should not be necessary with Dell laptop because they usually relabel Broadcom devices. If you go to the terminal ( applications>>Accessories>>Terminal)
and enter:

lspci | grep Wireless

(that is LSPCI in lowercase, W is uppercase)

What does it say?

---

### Post by davinamarie on 2010-03-06
It doesn't say anything!
 
This is what it says:
 
[EMAIL="ashley@ashley:~$"]ashley@ashley:~$[/EMAIL] lspci | grep Wireless
[EMAIL="ashley@ashley:~$"]ashley@ashley:~$[/EMAIL] 
 
It doesnt do anything....?

---

### Post by bkratz on 2010-03-06
> **davinamarie said:**
> It doesn't say anything!
 
This is what it says:
 
[EMAIL="ashley@ashley:~$"]ashley@ashley:~$[/EMAIL] lspci | grep Wireless
[EMAIL="ashley@ashley:~$"]ashley@ashley:~$[/EMAIL] 
 
It doesnt do anything....?

how about just

lspci

? You will have to read the output or copy/paste it back here for decoding.


Oh! I just noticed you used a \ instead of a pipe |

---

### Post by davinamarie on 2010-03-06
Ok, that worked... this is a long one and I will have to type it so just bare with me

---

### Post by bkratz on 2010-03-06
> **davinamarie said:**
> Ok, that worked... this is a long one and I will have to type it so just bare with me

Well do this or reread the end of my last post edited


```

lspci >> ~/Desktop/lspci.txt
```

attatch the lspci.txt file (its on your desktop) to your post

---

### Post by davinamarie on 2010-03-06
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corp. 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corp. 82801G (ICH7 Fam.)  PCI Express Port 1
00:1c.1 " Express Port 2
00:1c.2 " Port 3
.......
 
blah blah blah, loads more...
 
On the bottom is 04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
 
?

---

### Post by bkratz on 2010-03-06
Is there an entry that says network controller?

---

### Post by davinamarie on 2010-03-06
No, I used... ----> | <---- this symbol and not ----> / <---- this one.... is that correct?

---

### Post by davinamarie on 2010-03-06
Network controller says: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

