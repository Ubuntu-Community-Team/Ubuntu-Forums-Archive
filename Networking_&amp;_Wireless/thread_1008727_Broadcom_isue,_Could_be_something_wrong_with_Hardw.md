---
title: "Broadcom isue, Could be something wrong with Hardware??"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by chamus on 2008-12-11
Hi to all, I am running Ubuntu 8.10. in my notebook it is a Compaq f-500,everything is working fine except from my wireless. My card is a broadcom mini pci 94311 (rev 01). I know we have lot of post of Broadcoms problems, but I had really look for one in the same position to my and I have not find that, so here it goes..... 

 Ones I installed Ubuntu it asked to install drivers, so I did that, but from that on the light start to get orange casually; so I started my notebook and sometimes it work and some others times i t does not. When it work, it function perfectly, but when it doesnt....I have check that drivers were correct, so I run:

chamu@compaq:~$ sudo lsmod | grep b43
b43                   131356  0 
ssb                    40580  1 b43
rfkill                 17176  1 b43
mac80211              216820  1 b43

led_class              12164  1 b43
input_polldev          11912  1 b43

chamu@compaq:~$ sudo lsmod | grep wl
wl                   1076372  0 
ieee80211_crypt        13572  1 wl

As I now, this means that drivers are running fine, I had already tried running only wl or only b43, but it is the same.
What really call my atention is this:

chamu@compaq:~$ lspci | grep Broadcom
chamu@compaq:~$ 


So when I type that command nothing happened!! So I think that it must by a hardware problem and not a problem of drivers. Also when I go to System > Administration > restricted hardware. There I have only drivers from my video card, it is an NVIDIA and its working really fine whit that. It really seem that Ubuntu has not notice about that card!!

So what may I do?'
 Thanks to all answers!

---

### Post by Ayuthia on 2008-12-11
> **chamus said:**
> Hi to all, I am running Ubuntu 8.10. in my notebook it is a Compaq f-500,everything is working fine except from my wireless. My card is a broadcom mini pci 94311 (rev 01). I know we have lot of post of Broadcoms problems, but I had really look for one in the same position to my and I have not find that, so here it goes..... 

 Ones I installed Ubuntu it asked to install drivers, so I did that, but from that on the light start to get orange casually; so I started my notebook and sometimes it work and some others times i t does not. When it work, it function perfectly, but when it doesnt....I have check that drivers were correct, so I run:

chamu@compaq:~$ sudo lsmod | grep b43
b43                   131356  0 
ssb                    40580  1 b43
rfkill                 17176  1 b43
mac80211              216820  1 b43

led_class              12164  1 b43
input_polldev          11912  1 b43

chamu@compaq:~$ sudo lsmod | grep wl
wl                   1076372  0 
ieee80211_crypt        13572  1 wl

As I now, this means that drivers are running fine, I had already tried running only wl or only b43, but it is the same.
What really call my atention is this:

chamu@compaq:~$ lspci | grep Broadcom
chamu@compaq:~$ 


So when I type that command nothing happened!! So I think that it must by a hardware problem and not a problem of drivers. Also when I go to System > Administration > restricted hardware. There I have only drivers from my video card, it is an NVIDIA and its working really fine whit that. It really seem that Ubuntu has not notice about that card!!

So what may I do?'
 Thanks to all answers!

For starters, the b43 driver and the wl driver should not be used at the same time.  They could cause conflicts.  You should use one of them and blacklist the other.

As for your current issue, the missing lspci card could be a hardware problem.  Does the card show up when the light is not orange?  You might want to check and see if that is the case.  If it is there when the light is not orange but missing when it is, it probably is a hardware issue.  If you are dual booting with Windows, you might check and see if you have similar problems there.  That will help confirm that you have a hardware problem.

You should also check dmesg (from the Terminal) to see if any error messages show up when the light turns orange.  It might provide some clues.

Just to play it safe, you might check the following to see if you can find your card:
```
lspci
lsusb
lshw -C network
```

---

### Post by chamus on 2008-12-11
Well, first, thaks for that answer.

I had blacklist b43, so now its only running wl. I shuted down my system 6 times and ligth did not put blue anytime.

I check the four commands tha you provide and no one show my card. 
I can be pretty sure that when ligth is blue the card apears with lspci. 

If it is a hardware problem is there anyway to see if it is the motherboard or the card ?

I dont have mocosofts in my computer.

Thanl again for the help !!

---

### Post by Ayuthia on 2008-12-11
I am not for sure about how to test for this.  My laptop (HP Pavilion dv6338se) had a similiar issue and it was the motherboard that needed to be replaced.  Fortunately, my laptop was given a special warranty that covered it (basically it was a recall).  But the symptoms that you are having were the same as mine.  They said that the BIOS was not handling the fan speed well enough so the motherboard somehow lost contact with my wireless.  I just checked one document that I had from a while back and it looked like it only covered the 6000 series of the Pavilion and Compaq.

---

### Post by chamus on 2008-12-11
Well, thanks, I had read something about bios problems so I go hp web page and there you have the software to update your Bios, but all that information is only for mocosoft Vista, so.....
I have a Sempron, in this web you have the update for mocosoft only!.

Do you think I should update my bios? How can i run that in Ubuntu??

---

### Post by Ayuthia on 2008-12-11
I am not for sure if updating your BIOS will fix the problem or not, but even if it did, I am not for sure about if/how to do it through Linux.  That is the only reason why I have kept Vista on my laptop.  Sorry I can't help you too much further.

---

