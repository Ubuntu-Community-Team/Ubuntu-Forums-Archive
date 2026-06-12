---
title: "wireless network card not working after suspend"
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by Quazze on 2012-02-28
After I suspend Ubuntu (or after is suspends itself) half of the times the wireless card isn't working anymore. Even the little light, marking whether the WLAN is on, is off although the switch is on. Flipping the switch off and on again doesn't have any effect. I have to reboot to make my wireless card work again.

I have a Sony Vaio PCG 392M and my Wireless Network Card is a Intel PRO/Wireless 3945ABG (rev 02) 
(or full out: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)). 
I have Ubuntu 11.04 installed.

I don't understand why this is, because it really seems completely random: sometimes it is still working, sometimes it isn't

I don't know if it is really half of the times, might be even more, but it seems that there is larger chance of it not working anymore after a long time of being suspended.

This is really annoying because so often I have to reboot when I thought I could just quickly check something online (often I don't have the time to reboot). Certainly during the exams it is very inefficient when I often have to quickly look up little things on the internet. Could someone please help me?

---

### Post by chili555 on 2012-02-28
You might try this:```
sudo gedit /etc/pm/config.d/config
```A new, empty file will open. Add one line:```
SUSPEND_MODULES="iwl3945"
```Proofread, save and close gedit. Reboot, suspend and let us have your report.

---

### Post by Quazze on 2012-02-29
thanks for the quick response and sorry for my own tardy reaction (had a lot to do today).

I'm not quite sure what you mean. Is this a possible solution? If so I'll have to try it out for a little while, since the "not working" happens randomly, but is more likely to occur after a long time of my laptop being suspended.

But so I have done what you suggested and I'll see what happens...
thanks

---

### Post by chili555 on 2012-02-29
> Is this a possible solution?That's why I suggested it, so, yes!

We will be interested in your report.

---

### Post by Quazze on 2012-03-03
I'm afraid it still happens... :S

---

### Post by chili555 on 2012-03-03
> **Quazze said:**
> I'm afraid it still happens... :SIf you've proofread your work and it's all correct, then I have no further suggestions/mojo/talent. Sorry.

---

### Post by Contsa on 2012-05-17
Hi,

I have exactly the same problem on my Sony FZ11M. My card is also reported as "Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)"

Following this thread [https://bugzilla.redhat.com/show_bug.cgi?id=682514](https://bugzilla.redhat.com/show_bug.cgi?id=682514) it seems that there is a kernel issue resolved in kernels newer than 3.2.7. As I understand Ubuntu has the 3.2.0 (and I guess our bug is not back fixed). So I will try to use the 3.3.6 kernel of ppa based on the instructions found here: [http://www.upubuntu.com/2012/05/how-to-install-linux-kernel-336-via-ppa.html](http://www.upubuntu.com/2012/05/how-to-install-linux-kernel-336-via-ppa.html)

Wish me good luck!

---

### Post by Contsa on 2012-05-18
It did not work.....

---

### Post by m7redp on 2013-02-12
Did anyone ever find a solution for this problem?  I am having the same issue with a Dell laptop running a similar Intel wireless card. Only the card is not turning on after reboot.  When this use to happen I would just boot into my windows partition and then the wireless card would turn back on. but I am running this on a dedicated server so I can't just boot into another OS to turn the thing back on.  If anyone has a solution to this is I would be very interested!

---

### Post by chili555 on 2013-02-12
> **m7redp said:**
> Did anyone ever find a solution for this problem?  I am having the same issue with a Dell laptop running a similar Intel wireless card. Only the card is not turning on after reboot.  When this use to happen I would just boot into my windows partition and then the wireless card would turn back on. but I am running this on a dedicated server so I can't just boot into another OS to turn the thing back on.  If anyone has a solution to this is I would be very interested!Did you try the suggested solution, substituting your wireless driver if not iwl3945? It works for some, maybe most, and not for others.

Your Dell laptop is a dedicated server? Does the server really need to suspend?

---

### Post by m7redp on 2013-02-12
> **chili555 said:**
> 
Your Dell laptop is a dedicated server? Does the server really need to suspend?

No it does not need to suspend. The problem is I threw Gnome on there because I am not entire a ninja at the command line yet, so I wanted to be able to set up vnc or something for remote management. It is the default setting in Gnome to suspend when the lid closes and it's on battery. I had picked it up to transfer some files from a flash drive because they were too big to send over the network. When I this I closed the lid not thinking it would suspend. After waking it up the wifi card is not powered on and won't power on through multiple reboots.  So the short answer would be no I don't need to suspend, but it happened once and I can't seem to get the wifi card to turn back on.

---

### Post by chili555 on 2013-02-13
> After waking it up the wifi card is not powered on and won't power on through multiple reboots. So the short answer would be no I don't need to suspend, but it happened once and I can't seem to get the wifi card to turn back on.I think I see. The problem isn't really that the wireless needs a push to come back up after suspend; it is , rather, that you suspended once and it won't come back at all ever. If that is correct, let's try to find out what it is and where it is. Let's also set Power Management to *NOT* suspend on lid closing.

First the wireless. Let's find out what you have:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

I suggest you go into System Settings, select Power and set as I've attached.

---

### Post by ThatNewGuy on 2013-08-22
Heres the solution, works for me. HP dv6 Pav

[http://www.webupd8.org/2013/01/fix-wireless-or-wired-network-not.html](http://www.webupd8.org/2013/01/fix-wireless-or-wired-network-not.html)

ThatNewGuy

---

