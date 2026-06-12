---
title: "Can't connect to internet, please help"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by raac on 2011-03-14
I have a dell with a broadcom chipset
 
Hello guys, please I need your help. This is what happened, I was able to connect to internet before, then I installed kismet from the repositories and I changed the source line to
 
source=bcm43xx, wlan0, wlan0source
 
I ran kismet again and it worked. Ok, so then I did 'Q' to quit. I exited kismet but the terminal was frozen it said
 
"Reading client manufacturer data and defaults from //etc/kismet/client_manuf.
 
It hang in there for a while until I did Ctrl-C...then this appeared
 
^C
"
Select failed: Bad file descriptor
Didn't see any weak encryption packets, unlinking weak file
WARNING: Sometimes cards don't always come out of monitor mode"
 
Then I uninstalled kismet and downloaded the latest release, just to see if there was anything new with it, After I did ./configure
it said that I needed 
 
"libncurses", So I downloaded "ncurses 5.8", then I did ./configure again on kismet, and it said that i needed libpcap. I couldn't install libpcap library and I gave up. I installed the repository kismet again.
 
Anyways, ubuntu detects all the network routers, but when it comes to connect to it, it keeps trying for a while, then ask for password, then it keeps trying, and it never connects. I know it is that a hardware problem because I'm able to connect in Windows(I have it dual boot)
 
Please guys, did anything that i need caused this problem???
 
Thanks a lot

---

### Post by raac on 2011-03-15
Hi guys I posted my problems yesterday and nobody responded. I guess what I have left to do is deleting my wlan0 and created again (don't know if that would help). Although I noticed something, if I do "ifconfig", on my wlan0 

Link encap:Ethernet
is that normal???

How can I delete the wlan0 and created again??


yesterday's post:
[http://ubuntuforums.org/showthread.php?t=1707032](http://ubuntuforums.org/showthread.php?t=1707032)

---

### Post by raac on 2011-03-15
Also, what I noticed is that it does not even check if the password is correct when I'm trying to connect. I typed a wrong password on purpose and it does not say anything, it just hang in there. I've never seen this before...

---

### Post by wojox on 2011-03-15
Are you positive your trying to connect to your router and not one you scanned?

Click the nm-applet and be sure.

---

### Post by raac on 2011-03-15
I'm actually trying to connect through the network manager.

---

