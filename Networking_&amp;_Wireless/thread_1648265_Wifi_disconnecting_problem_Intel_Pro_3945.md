---
title: "Wifi disconnecting problem Intel Pro 3945"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by tha_chriz on 2010-12-18
Hi all,
I'm new here on forum but also on Ubuntu platform.
After upgrade to Ubuntu 10.10, but also before, I had a wifi connection problems. After few minutes connection is lost and I cannot connect again. I need to restart Laptop.

I've tried many solutions from different sources but none of them is working.

My laptop is HP 530, I've decided to install Ubuntu because Win Vista was very slow on it, Ubuntu is much faster but this disconnecting is annoying. Wifi probably is Intel Pro 3945.

Please help with this issue, I will provide all logs, but I need to know how to get them :)

Thanks a lot for any suggestions.

Chris

---

### Post by hakermania on 2010-12-18
Please, tell me, is your laptop near to the modem?

---

### Post by tha_chriz on 2010-12-18
yes, if there is connection there is around 80%, after disconnecting it can be again 80% but it won't to connect and I need to reboot it. :(

---

### Post by hakermania on 2010-12-18
Did you try Right Click on the Signal Strength icon -> Edit Connections -> Wireless -> Select your Modem's name -> delete and then try to reconnect to the modem?
On the other hand this seems to be a temporary solution.

---

### Post by tha_chriz on 2010-12-18
I will try to force Ubuntu to disconnect, because if I will do that there are no problems with connecting again. When it will be done by system, there is no possibility to reconnect.

But it will be as you said, temporary solution but maybe restart will not be needed ;)

Thanks for suggestions

---

### Post by hakermania on 2010-12-18
Glad to help you. Hope to find something more effective! :)

---

### Post by tha_chriz on 2011-01-03
Still disconnecting :( 
Few weeks of normal work today again I need to reboot to connect again.

---

### Post by PatchesTheCaveman on 2011-01-03
Hi tha_chriz.  Happy New Year!

Go to Applications > Accessories > Terminal, type the following, and press Enter:
```
sudo iwconfig
```

Then, copy/paste what appears into a reply to this thread.  We'll see what we can do.

---

### Post by tha_chriz on 2011-01-03
Happy New Year !!! :)

I think that I can suspend alert for a while.

I was a bit frustrated so I was digging and trying, last thing what I found was conflict between Network Manager and WICD. 
I did it using wire because network was not working.

Problem was that I wasn't able to remove Network Manager thru Ubuntu Software Center (it was removing but probably not all components), when I did it in Terminal using:

sudo apt-get remove network-manager

after that

sudo /etc/init.d/wicd restart

it start to works perfectly.

Everything is here
[http://ubuntuforums.org/showthread.php?t=1498035&page=3]("http://ubuntuforums.org/showthread.php?t=1498035&page=3") 


So, because I'm a rookie with Ubuntu I was not able to find a source of problem, now it works. I will test it for a while and in couple of days I will give some feedback if it is solution for similar problems or I will need help from experts.

Thanks a lot for responding,
Chris

---

