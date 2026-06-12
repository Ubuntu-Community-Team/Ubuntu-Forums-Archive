---
title: "RT2870STA and RT3070STA wireless, easy fix."
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by Dangerouge on 2010-08-06
I've fought with this RaLink 3070 WLAN card on multiple installations, doing practically everything possible, finally ending up with one installation with it working. However, in my latest attempt I finally got to the core of it, and realized it is really simple, so I thought I'd share. You can get away with just four commands, no downloading drivers or anything, just open your terminal and type.

```

sudo su
echo "rt2870sta" >> /etc/modules
modprobe rt2870sta
exit

```et voilá, restart and you have your stick working. This worked for my Netwjork W311U, probably will work with most of the RTxx70 chipset WLAN cards. Reply to this if this helped or you didn't manage to get it work, and we'll have a look at it.

Oh, and after kernel update it probably doesn't work anymore, so just do

sudo modprobe rt2870sta

EDIT: as of 10.10, aforementioned drivers SHOULD work out of the box, but if they don't, here's what you can do:
1. Check that your WLAN is on (especially if on a laptop), usually there's either a switch or a button with the appropriate icon (computer sending signals or the typical WLAN icon). Please make sure of this, because some devices are disabled by default on Linux. If this was the case, either restart network-manager (just "$sudo kill-all network-manager" should do the trick).
2. If that didn't work for you, tough luck, post here and we'll have a look at it together!

---

### Post by gbestrada on 2010-09-06
thanks for the tip it,  works perfectly on my desktop.

---

### Post by pcarreon on 2010-09-10
Also worked for my Intel Atom based desktop. I had been working on this for days now until I came across this post. 

I needed to reboot, though for this to work on my setup.

Thanks!

---

### Post by lukenuckley on 2010-10-08
Hi, thanks for this.

Unfortunately this hasn't worked for me.

I have a Novatech X10, which I have determined contains a Ralink 3070. I've tried the suggested fix but still cannot see my wireless network.

The below is what my terminal looked like before I restarted;

luke@luke-netbook:~$ sudo su
[sudo] password for luke:
root@luke-netbook:/home/luke# echo "rt2870sta" >> /etc/modules
root@luke-netbook:/home/luke# modprobe rt2870sta
root@luke-netbook:/home/luke# exit
exit


I have been discussing this at [https://answers.launchpad.net/ubuntu/+question/128344](https://answers.launchpad.net/ubuntu/+question/128344) - where Francois kindly provided a link to this topic. If you're able to help, then please either reply here or on my Launchpad question.


Thanks,
Luke

---

### Post by RalphP on 2010-10-13
When I installed Ubuntu 10.10 my RT3070STA worked out-of-the-box, asking only for my WPA2 pass-phrase the first time, unlike 10.04, where I had to blacklist conflicting modules. For some reason it did not work with Kubuntu 10.10.

---

### Post by edco76 on 2010-10-13
This also worked for my RT2860

Just changed the command lines to rt2860sta.

Thanks. Been workin on this all day.

---

### Post by Dangerouge on 2010-11-02
Hello Luke,

Try this in the console:
$sudo gedit /etc/modules

then remove the all the lines containing rt2870sta

$sudo modprobe rt2870sta

and restart, which happens most efficiently with
$sudo init 6

Then post your results back here. Please provide us with the output of your

$lsmod |*grep rt28 rt30

You might also want to update to Maverick Meerkat, like mentioned in the previous post.

Great to see that this post was of use! :)

You haven't tried to install any other drivers for this, have you? It might get messy if you have, but let's try.

> **lukenuckley said:**
> Hi, thanks for this.

Unfortunately this hasn't worked for me.

I have a Novatech X10, which I have determined contains a Ralink 3070. I've tried the suggested fix but still cannot see my wireless network.

The below is what my terminal looked like before I restarted;

luke@luke-netbook:~$ sudo su
[sudo] password for luke:
root@luke-netbook:/home/luke# echo "rt2870sta" >> /etc/modules
root@luke-netbook:/home/luke# modprobe rt2870sta
root@luke-netbook:/home/luke# exit
exit


I have been discussing this at [https://answers.launchpad.net/ubuntu/+question/128344](https://answers.launchpad.net/ubuntu/+question/128344) - where Francois kindly provided a link to this topic. If you're able to help, then please either reply here or on my Launchpad question.


Thanks,
Luke

---

### Post by clarett on 2010-12-06
I have this same problem - I've tried numerous combinations of blacklisting different modules, I've tried Ubuntu 10.04 and 10.10 what Dangerouge posted at the top but got the same as Luke in how it looked - tried Luke's solution that he found on Launchpad.
Nothing!
Driving me nuts!
Desperately want this to work as it is really hard to find linux netbooks in UK with similar spec - thought I was safe buying a -no OS- one as they knew who the market was for.
Incredibly frustrated!

Anyone got anymore ideas?
I'm very new to linux so bit by bit please!

---

### Post by fhd on 2011-01-10
A bit late, but I just so other people find this faster than I did, I'll spread the news:

I had the exact same issue and figured out that it works if you activate WLAN (it's disabled per default on the x10, press Fn+F2 to change that) and then restart network-manager. See [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/602213").

---

