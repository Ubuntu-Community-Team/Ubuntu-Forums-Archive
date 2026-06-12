---
title: "Asus F5RL"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by rock_fredde on 2008-12-09
[B]SOLUTION FOR ASUS F5RL (AND MAYBE OTHERS) USERS - HOW TO GET WIFI RUNNING:

[/B]

I, like many F5RL users, have been struggling to get wifi working. Getting to the point of installing the packages but never actually getting the LED to turn on nor actually find any wireless networks to connect to.

The solution, however, is REALLY SIMPLE.

**You simply need to UNLOAD the asus laptop module!!!!**

sudo modprobe -r asus-laptop

in terminal. This will enable you to flip the wireless switch on AND connect to networks.


I do not know whether this will work on a fresh install. I did this after installing fresh 8.10, updating it and then following this guide: [http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

It should be known that I am not to credit for this. I am simply passing on information found here on the forum and on this website: [http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/#comment-355](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/#comment-355)

I am new to the Ubuntu community and I dont know how to pass this on to people in charge of the ubuntu wikis and FAQs. It is imperative however that this is published in all appropriate forums and wikis so that Asus owners can enjoy Ubuntu, and so that this bug is fixed, enabling out of the box or at least easier use of Ubuntu on Asus computers.

---

### Post by RezoApio on 2008-12-27
Just a note from my own experience with the asus F5RL.

Removing this module has not changed anything for me. 
I have the wifi working following the same post and with or without the asus-laptop module, I need to switch off/on the wifi at login screen so it works.

Still trying to understand the link between the acpid daemon and maybe the stopping of the wifi led.

Merry christmas.

---

### Post by sabour86 on 2009-04-23
Hey. Thanks loads. I dont know how it happened. But it worked. 

```
sudo modprobe -r asus-laptop
```

FYI I'm using an updated version of Ubuntu Intrepid with ndiswrapper installed with XP32 bit drivers for Atheros 5007EG!!!

---

### Post by Sand &amp; Mercury on 2009-04-26
I can't believe it was really that simple! 

This has plagued me for so long, now it's working like a charm. Wireless working flawlessly, LED light going good, switch works properly. Using 9.04. Thank you very much for passing this along, OP!

---

### Post by aalhamer on 2009-04-28
still nothing on my end, I'm running an Asus F5RL, and have been trying to get my wireless working, i have followed the instruction to the word, amending the source file wget -c [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2009-02-24.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2009-02-24.tar.bz2)
to its latest version, wget -c [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2009-04-20.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2009-04-20.tar.bz2), that didn't help.

i waited until ubuntu 9.04, HUH!! it recognized my wireless cards Atheros as a restricted device but still no dice..
y 
i did all the previous instruction in 9.04, NOTHING...

either i'm doing something wrong or i'm missing a command.

i did the sudo modprobe -r asus-laptop, that only helped turning my wireless LED light on... i love ubuntu, but WTF. just once i'd like to buy system install ubuntu and have it work without me messing with it...

in desperate need of help, vista really really sucks in comparison, but i have no other solution.....

Also, i'm facing the same problem with an Acer Inspire One Netbook, Guess what wireless card it has... F***ing Atheros.. same model too... 
Someone Please contact this shitty company and ask them to develop a driver for ubuntu..

---

### Post by alexrb on 2009-05-25
it worked for me with LED. Thanks for the tip.

as to wifi on intrepid:
i did these steps:
removed ath5k module
enabled madwifi module
added 1 to /proc/sys/dev/wifi0/softled
unloaded madwifi
loaded ath5k

bingo! it worked.

ANOTHER QUESTION from me is Sound.
I've upgraded to latest ALSA but still my notebook is silent. any ideas?

---

