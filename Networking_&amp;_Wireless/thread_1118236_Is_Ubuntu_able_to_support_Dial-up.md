---
title: "Is Ubuntu able to support Dial-up?"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by billfreeboy on 2009-04-06
Hi, I'm Jacob Freer-Balko who got a very first look at Ubuntu on a school computer,:popcorn: they now have Fedora Computers.
This is my one question in this thread, is Ubuntu able to support a Dial-Up Connection?

---

### Post by kreggz on 2009-04-06
yes, in Add/Remove programs do a search for dialup and a program called Gnome PPP will appear, try that

---

### Post by billfreeboy on 2009-04-06
Thanks for the info.
It's since some people in my life use Dial-Up instead of Broadband.:grin:
EDIT: I actually use broadband, it's just for people who are stuck with Dial-Up.

---

### Post by chili555 on 2009-04-06
Of course, the real question is whether your *modem* is supported. Here is a starting place: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by j d on 2009-04-09
in ubuntu 8.04 yes in ubuntu 8.10 no

---

### Post by chili555 on 2009-04-10
> **j d said:**
> in ubuntu 8.04 yes in ubuntu 8.10 no[COLOR="Blue"][Citation Needed][/COLOR]

---

### Post by ModelM on 2009-04-11
> **j d said:**
> in ubuntu 8.04 yes in ubuntu 8.10 no

This is not true and it is quite irresponsible to make such a statement here as some people may believe it.

I use a dialup modem with Ubuntu 8.10 every day.

There is a little more info in [_this thread](http://ubuntuforums.org/showthread.php?t=1110137)_.

---

### Post by djrakun on 2009-04-18
not only does it depend on your modem but also your carrier.  it appears that sbcglobal.net does not have good/any linux support, which is strange because it is straight AT commands for the most part so I'm surprised that the handshake would have an OS bias.  

here's a great how-to to get you started.  There is one error however:  you will want to edit /etc/wvdial.conf  ( howto says /etc/wvdial

[http://ubuntuforums.org/showthread.php?t=843973&highlight=usb+modem](http://ubuntuforums.org/showthread.php?t=843973&highlight=usb+modem)

the instructions here detected my serial modem no problem, but the USB modem that I borrowed from work for the test was not detected, however I don't know if it even works because it was in our junk pile.

I was setting up a pII with feisty for my in-laws so they could get their email over dialup, and I was sorry to experience login problem with their sbcglobal.net account.  Looks like I'm not the only one

[http://ubuntuforums.org/showthread.php?t=465045](http://ubuntuforums.org/showthread.php?t=465045)

I've read some non ubuntu forums of users complaining about loss of service after their accounts were acquired from Prodigy to SBCGlobal.net.  I'll reply to this thread if I make any headway on this problem but from what I read so far ( only 15 minutes into the issue) it looks pretty hopeless.  Of course I graciously accept any advice from the community members reading this.

Cheers

---

### Post by djrakun on 2009-04-18
my prob was resolved with by this thread

[http://www.murga-linux.com/puppy/viewtopic.php?p=280161](http://www.murga-linux.com/puppy/viewtopic.php?p=280161)

i added the following lines to my wvdial.conf file and all is working now

Carrier Check = no 
Dial Command = ATDT  
Stupid Mode = yes

---

