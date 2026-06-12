---
title: "Internet Woes"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by jpzrfreek on 2008-12-15
Hi Everyone,

I am a **brand new **user (7 Days) of Linux (Ubuntu 8.10) and whilst I am finding the use of the menu's pretty easy, I am having hassles with the Internet connection.
I have an Asus VX2 Laptop and an Iprimus Speedster (3G)mobile broadband internet connection, unfortunately the Speedster is designed for the use of Bill Gates software and anyone I have contacted including Iprimus....well quite frankly, as soon as I mentioned Linux I may as well have been talking a foreign language and do not want to know.
Please accept my apologises if this has been asked before but I am hoping that someone will be able to help me get my combination of hardware working so I can away from time restricted public domain internet usage.

Thanks

Phil

---

### Post by lensman3 on 2008-12-15
At a text window enter: "lspci -nn".  The program will dump all your pci devices.  In the output is a number that looks like "xxxx:yyyy".  Now go to google and google that number, your hardware name, linux, and install.  Chances are that someone else has had trouble and has already figured it out.

The xxxx:yyyy number is a unique number that is assigned your hardware by the pci "gods".  The number is unique to your hardware.

Good luck.

---

### Post by jpzrfreek on 2008-12-16
Hi Lensman,

Thanks for your responce, please forgive my ignorance but I have not yet worked out all the terminologies between the dreaded Microsoft and Ubuntu.

You say in your reply to go to a text page and type in something, but I am unsure of what you mean by text page, is this start a new document (sorry for speaking Microsoft) or a command somewhere in the menu's.

Thanks again for your help

P

---

### Post by Iowan on 2008-12-16
(I call it a terminal) On my Gutsy Ubuntu, it's under Appllications>Accessories... or CTRL-ALT-F1 through CTRL-ALT-F6.  CTRL-ALT-F7 will get you back to GUI.

---

### Post by jpzrfreek on 2008-12-19
Thanks Iowan but I think I have lost the plot (and am blaming it on my age) but I eventually found the text window and I opened terminal and got the Ubuntu equivalent of MS Notepad where I logged on (as it asked) then it came up with *username* @ *username* "$ and after typing in "ispci-nn" I got just a flashing cursor. The exact same thing happened when I did the Alt/Ctrl/F1, with the only difference being the screen looked more like DOS (sorry about the MS terminologies but after over 15 years of MS software I am not offay with Ubuntu terms).

Is it possible that there is some "debris" left over from Vista which was originally installed on the laptop when I got it and is causing these problems??

As I do not have much on the computer yet would it be worthwhile reformatting the drive?? 

Could I type in format C: at the $ prompt???

Could there be some problem with the Ubuntu copy that I have...I got a mate to download it for me, as it is giving me the impression that something is missing.

Thank you for your help

P

---

