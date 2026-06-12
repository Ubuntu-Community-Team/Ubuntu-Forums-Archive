---
title: "Airlink101 Driver Help!"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by brain_stergeon on 2010-06-10
Hello,
I recently purchased a Airlink 101 AWLH6075 Wireless N Pci card but I can't seem to find any way to get it to work in 10.04. I know somewhere someone has gotten this card to work but I can't. Any ideas or advice?

---

### Post by SlidingHorn on 2010-06-10
Not currently listed under ndiswrapper's db of working cards.  This is the closest I could find: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Airlink_AWLH3026T](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Airlink_AWLH3026T)

---

### Post by brain_stergeon on 2010-06-10
I did see that one, I did find one site where it says the card is ralink based, could I use one of their drivers to install it?

---

### Post by brain_stergeon on 2010-06-10
Anyone have any way to fix this problem?

---

### Post by SlidingHorn on 2010-06-10
try not to bump threads so early...usually recommended to give it 24 hours

Check out the link in my signature about wireless issues & post the results of the commands it advises

**Edit**:  are you dual-booting?  if so, mount your windows partition, and copy the drivers from there...then use ndiswrapper to try to get them to work.  like I said, it's not listed as supported, but that doesn't necessarily mean it won't.

Either way, check out the link mentioned earlier

---

### Post by brain_stergeon on 2010-06-10
Sorry, didn't realize it was to early it is just really frustrating when things dont work. Also I am not dual booting I was going to try that on a different pc but I couldn't find the installed drivers. I will check out that link you mentioned. I tried to run the included cd with wine but it crashes every time.

---

### Post by SlidingHorn on 2010-06-10
It happens :)  Some cards end up just not being compatible at the time...however, we'll try to get it working for you.

---

### Post by M!K3_$ on 2010-06-23
SOLVED.

I made him bring his PC over and I did it myself. :)

I used the drivers off Ralink's site and it worked like a charm.
[http://www.ralinktech.com/]("http://www.ralinktech.com/")

I haven't ran into a situation, with wireless devices. where you can't bypass the device vendor and go right to the chip vendor for drivers.

---

### Post by brain_stergeon on 2010-06-23
Its best to be a n00b when you have someone you can drag everything over to and say "Fix it" :P

---

### Post by ANew on 2010-08-22
> **M!K3_$ said:**
> 
I used the drivers off Ralink's site and it worked like a charm.
[http://www.ralinktech.com/]("http://www.ralinktech.com/")



What Ralink adapter is equavalent to this Airlink? There are
number of drivers on this website - which one to use?

---

### Post by LaJuan on 2011-01-20
Hi,

I'm new to Ubuntu as well, BUT love how it runs and the look!!!!!!! I can install Ubuntu but, adding new hardware is confusing. I'm having the same issue using the same PCI irlink 101 card and is some what confused on the process of installing a window's driver or installing it using terminal. Is there a user's guide to this process? Also, my wireless network is completely gone.

Thanks,

LaJuan

---

### Post by LaJuan on 2011-01-20
Hi,

I new to Ubuntu and Linux as well. I'm having the same issue and would like to know, is there a user guide that shows how to install a windows driver or Linux driver? This process is very confusing and I'm sure it will get better once I play with Ubuntu more and more. Running 10.10 on a AMD Presario.

Thanks,

LaJuan

---

### Post by LaJuan on 2011-01-20
Hi,

I new to Ubuntu and Linux as well. I'm having the same issue and would like to know, is there a user guide that shows how to install a windows driver or Linux driver? This process is very confusing and I'm sure it will get better once I play with Ubuntu more and more. Running 10.10 on a AMD Presario.

Thanks,

LaJuan

---

### Post by LaJuan on 2011-01-20
Hi,

I new to Ubuntu and Linux as well. I'm having the same issue and would like to know, is there a user guide that shows how to install a windows driver or Linux driver? This process is very confusing and I'm sure it will get better once I play with Ubuntu more and more. Running 10.10 on a AMD Presario.

Thanks,

LaJuan

---

