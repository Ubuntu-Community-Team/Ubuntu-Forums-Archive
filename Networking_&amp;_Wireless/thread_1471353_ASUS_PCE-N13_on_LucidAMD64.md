---
title: "ASUS PCE-N13 on Lucid/AMD64"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by dpneal on 2010-05-03
Hi all,

I just installed the Ubuntu-10.04-Alternate-AMD64 version of Lucid on a new system build.  The installation went swimmingly, and everything seems to be working with a single exception:

My wireless network card is an ASUS PCE-N13.  While I can see the wireless network to which I wish to connect, I am unable to connect to it.  I am prompted for my WPA2 PSK, but the computer is unable to connect successfully to the network.

The card successfully connects to my network when I boot into Win7.  I've verified that I typed the PSK correctly.

Is this a 64-bit/32-bit driver issue?  I can reinstall the 32-bit version of Lucid, but would prefer not to if there's an easy fix.

Thanks,

Dan

---

### Post by Vampyree on 2010-05-06
Hey Everyone

Im a new hopefully Ubuntu user

I have the exact same question, My internet tries to connect but the little connector thing just goes up and down and keeps asking for the wpa2 password. It connects the first time no worries then never again :(

Is there a solution to this??

Thanks 
Vampyree

---

### Post by Vampyree on 2010-05-06
I have been doing a bit of googling as we do. I came across this post from a review on Newegg. This is exactly what happened to me. It connects to the internet the first time then I install Ati drivers that Ubuntu picks up restart and then the internet doesnt work.

How would I fix this???

Turns out, AMD Catalyst Control Center was detecting this wireless card as TWO HD4770s, causing some kind of software error, which caused the card to be incredibly slow, and would also explain why it worked so well under Ubuntu 10.04 (no CCC running).
Now that I've gotten this problem sorted out, performance is great, and I am (so far) very pleased. I hope it lasts :s

---

### Post by dpneal on 2010-05-06
Weird, I can't connect at all with the card.  Haven't been able to update my video card drivers, so my issue may be different.

As a common thread, we're both using WPA2 -- maybe this is it?  Searching the forums, I found that someone was able to connect successfully onto his or her wireless network by disabling encryption.  Not a possibility for me.

---

### Post by kramzero on 2010-05-08
i'm using ubuntu 10.04 64-bit. this card works only on 802.11b and g mode. can't connect to my network everytime i set my router to n-only mode. i uninstalled ati ccc, same problem persists. i have wpa2 encryption on my network. can somebody please help?

---

### Post by pdc on 2010-05-08
this is a very useful diagnostic script that analyses your wireless setup; it is used on the OpenSuse forum; it diagnoses; suggests solutions; 

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

post the results back here if you need further help

---

### Post by dpneal on 2010-05-15
The wireless network connection works perfectly if I disable WPA/WPA2 on my router.

This isn't a good solution, for obvious reasons.

I'm updating Lucid now; hopefully something has been pushed that fixes the issue.

---

### Post by dpneal on 2010-05-15
... and everything is working after allowing Ubuntu to update over the temporarily unsecured network.

---

### Post by pdc on 2010-05-15
> .. *and everything is working after allowing Ubuntu to update over the temporarily unsecured network*. 

... I understand that to mean you can now protect using WPA ....

---

### Post by dpneal on 2010-05-15
Correct.  I was able to tell the router to start using WPA2 personal again after patching.

---

