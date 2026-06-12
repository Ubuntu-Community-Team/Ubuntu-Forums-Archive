---
title: "Intellinet 150N USB cannot connect"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by tomlagrinch on 2010-09-11
Hello, I'm a total newb (and i can already see everyone ignoring this thread :) oh well), heres my problem, I can only connect via wire beacuse ubuntu doesn't appear to have drivers for my adapter (the 150n) which uses the RaLink RT2870 (or 3070 this part I'm not totally clear on). Thats all fine and dandy, Intellinet supply the driver, but heres the clincher, 
I downloaded the driver, and realised with a grand "ahhh crap", I really had no idea where to go from there
(if you find yourself needing to back away from this thread now, i understand)

(I had the full instructions here but if you look at the next post you'll see why they were unnecessary)

now, if anybody has infinite patience and a divine hatred for newbs getting away with not knowing anything, please can you help me?

oh and if you're wondering why i got ubuntu without knowing how to do something as simple (I'm sure this is all very basic stuff) as this, its because everything elsse (EVERYTHING) is working perfectly, including my dvd drive which claimed (under windows rule) that it was broken, its just the damn internet, and im getting a wee bit tired of hunching over a computer arranged on the floor, inconveniently placed so i can use the wire-

---

### Post by tomlagrinch on 2010-09-15
Alright, its ok, solved it! turns out the drivers were installed already, its just that they were conflicting with another driver, if anybody else has such a problem this is what i did.

(In the terminal)
sudo ifconfig wlan0 down ***(wlan0 is the name for my wireless device where the ethernet is called eth0, I'm sure this would be the same on all machines but if your not sure go to Network Tools in System/Administration, the Network Devices dropdown menu should list wireless-wlan0, ethernet-eth0 and loopback interface-l0)***
sudo modprobe -r rt2800usb  ***(not sure but i think this the line that disabled the conflicting driver, if anybody could confirm this it would be appreciated because for some reason, as you'll see in the next line, its necessary to disable the driver i want to use too)***
sudo modprobe -r rt2870sta
sudo modprobe rt2870sta  ***(presumably if the above two commands disabled the drivers, this one re-enabled the correct one, again not sure about this, I am after all a beginner)***
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan  ***This last command should bring up a string of lines detailing an available network, if not connection shouldn't work still, in this case I'm stumped and my most sincere apologies for wasting precious time***

Then I went to network manager (or in my case Wicd Network manager) scanned for networks and hey presto! my house network (finally) showed! I am finally on the ol' interweb via wireless! 

Hope this info can help you:D

---

### Post by celsius57 on 2010-12-28
I want to thank you for solving this problem, that it was exactly the same I had (with Ubuntu 10.04 -wubi).
I found you may block forever the bad driver this way:

sudo gedit  /etc/modprobe.d/blacklist.conf
(of course, you may use vi  or whatever editor you like) 

add this line:
blacklist rt2800usb

save, reset the PC and voila! :p

Thanks again.

---

