---
title: "previously working wireless stopped working"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by satipera on 2009-02-01
Running 8.10 Intepid. When I installed ubuntu my wireless networking worked fine and continued to do so until recently. I was at a friends house and plugged my laptop into the net with a wired connection it worked straight away. However when i returned home the wireless would not work, the "enable wireless" is greyed out in the menu and I have no idea how to get it working again.


This my second computer proves wireless network itself is still working.

3 days and 33 people do not have a clue? Am I asking a stupid question or is this really too difficult? and  I will have to do without internet on my laptop in ubuntu?

---

### Post by satipera on 2009-02-05
bump

---

### Post by xannaxprozaxx on 2009-02-05
Hello! I have exactly the same problem. I tried everything in the help center but it still did not work. Maybe it has to do with the updates. I'm gonna try re-installing Ubuntu, and will tell you if it worked...:)

---

### Post by kbutcher5 on 2009-02-05
Do this, and post the output here:
```

sudo iwconfig

```

---

### Post by xannaxprozaxx on 2009-02-05
I typed this in the terminal and it said:

lo      no wireless extensions.


ethO    no wireless extensions.


panO    no wireless extensions.



but I have XP on the same computer and the wireless works just fine. What can I do??

---

### Post by kbutcher5 on 2009-02-05
Did you by any chance run an update at your friends place? Because the driver seems to nonexsistant or broken.
What is the pan0 interface?

---

### Post by mohitchawla on 2009-02-05
Which wireless card/adapter are you using ?

---

### Post by satipera on 2009-02-05
Hello, thanks for the replies the network card is PRO/Wireless 3945ABG Intel and here is the print out asked for, I would caution you that this is not the original settings as I have been floundering around trying to get it going myself.

mac@mac-laptop:~$ sudo iwconfig
[sudo] password for mac: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

mac@mac-laptop:~$ 
mac@mac-laptop:~$

Btw it is me who had the problem since connecting with a wired connection around my friends house the other person whose name I can't remember (appologies to person concerned) has a simmilar problem and has said he is reinstalling. I do not think I updated the laptop around my friends house but can't be sure.

---

### Post by kbutcher5 on 2009-02-05
It seems to show up now?
I use the exact same controller, try:
```

ifconfig wlan0 up

```
Then see if your wlan doesn't pop back into place in the network manager?

---

### Post by satipera on 2009-02-05
When I enter that I get " SIOCSIFFLAGS: No such device"

---

### Post by kbutcher5 on 2009-02-05
What i feared, apparently, it seems to be some sort of mismatch of kernel and ndiswrapper, that makes ndiswrapper freak out.
I have the same problem, I will post a solution here if i find one!

---

### Post by satipera on 2009-02-05
Okay kbutcher5 I will look forward to it :-)

---

### Post by kbutcher5 on 2009-02-05
Try doing a [COLOR="Red"]lshw -C network[/COLOR], scroll down to your wireless card, my bet is it says:
  *-network DISABLED
right above the wireless interface?

---

### Post by satipera on 2009-02-05
Yes it does say network disabled above wireless interface and above ethernet interface.

---

### Post by satipera on 2009-02-07
Problem solved, this is embarassing, during transport the slider switch which enables and disables the wireless connection was moved over. I never touch it as a rule and never thought of it.

---

