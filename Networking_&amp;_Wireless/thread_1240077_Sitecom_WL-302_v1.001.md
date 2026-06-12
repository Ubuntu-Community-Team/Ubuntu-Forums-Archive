---
title: "Sitecom WL-302 v1.001"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by nyarnon on 2009-08-14
Has anybody been able to get this running in N mode? Currently mine only will do 54 Mb/s.

---

### Post by Hobbiter on 2009-09-18
how did you get it to work? and do you have ubuntu 9.04?

---

### Post by Tomatosoup on 2009-10-28
I have a WL-302 and a 300N-XR wireless USB, which indeed should support 802.11n.

Under Ubuntu 9.04 it does connect with ease!
But when I transfer files in my local network (LAN) it goes rather slowly. Maybe 2,6 MB/sec, which would be 20,8 Mbit/s...

So it does not use the N-standard...

I would like it to do so too!!

AND:
I've tried a Beta version a few days ago, a beta version of 9.10 (Karmic Koala), and then I couldn't even establish a link between my 300N-XR wireless USB and my WL-302 router!!!

In Ubuntu 9.04 the driver has 'Sitecom' in its name. In Ubuntu 9.10 it is a 'Ralink' driver.................WTF?

I can't even get it to work in 9.10. Not in the beta version at least. I hope it will work in the final version of Karmic Koala, tomorrow....

---

### Post by iaga84 on 2009-10-31
Same issue with my WL-302 and Ubuntu 9.10,
any news? I can't connect to router.

Thanks

---

### Post by kboarder on 2009-11-01
I had the same problem, hope this solution works for you.

You have to blacklist rt2800usb driver. It seems the wrong one is loaded cause it should be the rt2870sta. 

These steps should do the trick!

 1: gksudo nautilus

2: go to: /etc/modprobe.d/

3: gedit the: blacklist.conf

4: Add this line in it:  

blacklist rt2800usb

5: Safe the file, and restart system. 


Hopefully it connects to your router.

---

### Post by iaga84 on 2009-11-02
Perfect!
Thanks [kboarder]("http://swiss.ubuntuforums.org/member.php?u=943675") :)

Problem solved.

---

### Post by kboarder on 2009-11-02
> **iaga84 said:**
> Perfect!
Thanks [kboarder]("http://swiss.ubuntuforums.org/member.php?u=943675") :)

Problem solved.

you're welcome!

---

### Post by cathyra on 2009-11-04
> **kboarder said:**
> I had the same problem, hope this solution works for you.

You have to blacklist rt2800usb driver. It seems the wrong one is loaded cause it should be the rt2870sta. 

These steps should do the trick!

 1: gksudo nautilus

2: go to: /etc/modprobe.d/

3: gedit the: blacklist.conf

4: Add this line in it:  

blacklist rt2800usb

5: Safe the file, and restart system. 


Hopefully it connects to your router.



Hi,

I just registered myself to thank you for this solution.
I installed karmic this morning on an old windows pc, with the sitecom WL-302.
Been reading and trying all day to get it to work, and this simple solution finally did the trick! 

So thanks again very very much:-)

Cathyra

---

### Post by kboarder on 2009-11-04
Glad i could help you!

But don't thank me to much! Or i get emotional.. ;):D

---

### Post by nyarnon on 2010-04-23
Well this solution doesn't seem to work anymore under Lucid

---

### Post by tkn1955 on 2010-05-04
> **kboarder said:**
> I had the same problem, hope this solution works for you.
 
You have to blacklist rt2800usb driver. It seems the wrong one is loaded cause it should be the rt2870sta. 
 
These steps should do the trick!
 
1: gksudo nautilus
 
2: go to: /etc/modprobe.d/
 
3: gedit the: blacklist.conf
 
4: Add this line in it: 
 
blacklist rt2800usb
 
5: Safe the file, and restart system. 
 
 
Hopefully it connects to your router.
 
Hi there.
 
I used this sollution on the 9.10 version of ubuntu and it worked fine. Thanks for that. But... I upgraded to 10.04, same problem but the solution doesn't seem to work. In both versions after installing the wireless adapter (sitecom wl-302) didn't detect my wireless network. After modification of the blacklist.conf file as indicated under 9.10 it worked fine. However under 10.04 it detects the network but it fails to connect. It doesn't seem to recognize the WPA password. As it worked fine before a hardware problem seems not plausible. Do you or somebody else know a solution for this new problem??
 
Thanks in advance

---

### Post by purno on 2010-05-04
I have the same problem, however there is a workaround. By changing the authentication type of your router in wpa tkip, instead of wpa2. This is not a perfect solution, but I find it better for the time being than a wire through my apartment ;)

---

### Post by tkn1955 on 2010-05-05
> **purno said:**
> I have the same problem, however there is a workaround. By changing the authentication type of your router in wpa tkip, instead of wpa2. This is not a perfect solution, but I find it better for the time being than a wire through my apartment ;)
 
This worked immediately, thanks Purno!
 
I wonder if somebody comes up with a better solution because WPA TKIP is supposedly a less secure encryption.
 
Greets, tkn1955

---

