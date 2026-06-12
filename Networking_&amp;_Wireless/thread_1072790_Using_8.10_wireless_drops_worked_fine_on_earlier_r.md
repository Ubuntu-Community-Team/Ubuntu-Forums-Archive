---
title: "Using 8.10 wireless drops worked fine on earlier releases"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by tinski on 2009-02-17
Have been using Ubuntu on IBM Thinkpad X31 for many years.  However, my battery died and corrupted my 8.04 release.  Rather than fixing I just made a 8.10 CD and reinstalled from scratch.  Everything installed great.  However, after connecting to wireless it dropped after a short time.  Just will not stay up very long.  I have looked through many posts and there seems to be many issues with 8.10 and wireless.  Seems security may be causing my issues.  My wireless router wants WEP 64 bit.  I did plug in directly to lan and installed all the latest patches (256 of them).  Was hoping that would solve issue.  This is the 1st time I'm actually disappointed with Ubuntu. :( 

Can someone simply explain why wireless connections work differently (poorly) in 8.10 and easily explain how to fix it back like it used to work on earlier releases.

---

### Post by MarkAfterDark on 2009-02-17
You're not alone.  I've been browsing the forum for _two days now_ in a futile attempt to remedy the issue.  
Let me guess... You connect to your access point and it works fine varying for either a few seconds or perhaps even a couple of minutes... Then it just drops and keeps reconnecting right?

Edit:  What wireless card are you using?

lspci  

Look for network controller.

---

### Post by haddog on 2009-02-17
I had the same issue. I hate to say it... I gave up and went back to 8.04.2.

---

### Post by MarkAfterDark on 2009-02-17
You know... I've been considering doing just that.  Everything worked fine with 8.04.  

This is the second bug (with me) to appear with wireless since updating to 8.10.  

The first was the inability to connect to access points with WEP/WPA2E security.  That problem was obvious the moment I booted 8.10 for the first time.  That was in mid December(2008 ) and it already had a solution by the time I updated and it only effected a couple types of cards.    

This new issue is not just limited to intel cards or axxom cards or (name here cards).  This problem is popping up all over the forum.  (Yes... I've read every one of them).  It's effecting a LOT of 8.10 users.  

The strangest thing to note about this problem:  It didn't happen as a result of an update or modification, to anything.  From other threads, I've read that "it just started happening" and no one knows why.  This is true with mine as well.  It was fine for weeks... Now I'm back to tethered.

I've even started thinking a virus may be the culprit.  Yea... I said it!  Start the flaming!

---

### Post by tinski on 2009-02-17
I think there has to be some logical reason.  Maybe the new 8.10 has some different security settings from 8.04.  I also got this strange keyring that would pop-up after reboot saying network manager needed access.

Can anyone please explain the differences between 8.04 and 8.10?  Maybe we can then work our way back to the answer.

---

### Post by Depressed Man on 2009-02-17
I have an Intel integrated iwl3945, and I have this issue too.. The thing is it use to work just fine so I think it had to do with the kernel update.

---

### Post by haddog on 2009-02-18
Depressed Man. I think you make a good point. I'm going to setup another linux box this weekend. I'll see what happens with my wifi card before applying any updates.

---

### Post by tinski on 2009-02-20
Installed 8.10 on a Dell Latitude D600 and wireless never dropped out.  It has a PRO/Wireless LAN 2100 3B Mini PCI Adapter by Intel.  The IBM Thinkpad X31 has a AR5211 802.11ab NIC by Atheros Communications Inc.

I used terminal and ran the following to find out which cards they used;
   sudo lshw -C network

Since the IBM Thinkpad worked fine on earlier releases of Unbuntu there may be a wireless driver change in 8.10 that is causing our heartburn.  Anyone know how to fix this issue?

---

### Post by izizzle on 2009-02-20
I am having the exact same problem as the rest of you all. Actually, previous releases picked up my COMPAQ IPAQ 11 MBPS Wireless Adapter perfectly- but 8.10 doesn't even pick it up! So, I have to use my backup 11 mbps usb adapter. However, with my backup, I get the same problem as you guys. Connects, then drops the connection! They better fix this in 9.04!

---

### Post by tinski on 2009-02-20
I think I fixed it!!! :) Did some searching on the web.  This worked on my Thinkpad X31

1. sudo apt-get install linux-backports-modules-intrepid-generic

2. reboot

3. Go into System->Administration->Hardware Drivers
   and Deactivate "Support for Atheros 802.11 wireless Lan cards
   and leave "Support for 5xxx series of Atheros 802.11 wireless LAN cards" activated.

4. reboot again.  Your done and wireless now happy!!

Original post where I found the answer:

[http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/](http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/)

---

### Post by tinski on 2009-02-22
Wireless has been working great for over a day now.  I consider this thread solved.  Not sure how you change thread to solved.

---

### Post by Julian_Satran on 2009-02-22
> **tinski said:**
> Installed 8.10 on a Dell Latitude D600 and wireless never dropped out.  It has a PRO/Wireless LAN 2100 3B Mini PCI Adapter by Intel.  The IBM Thinkpad X31 has a AR5211 802.11ab NIC by Atheros Communications Inc.

I used terminal and ran the following to find out which cards they used;
   sudo lshw -C network

Since the IBM Thinkpad worked fine on earlier releases of Unbuntu there may be a wireless driver change in 8.10 that is causing our heartburn.  Anyone know how to fix this issue?

----- 

I am not sure it is related to the ilw2100 driver. I have an old T41 with an Intel2100 Mini PCI adapter and I have the same issues as others have reported (link dropped, WPA - PSK doesn't work etc.

---

### Post by rxex on 2009-02-22
I'm having a problem with my wireless connection also. Its an Intel Pro wireless 2915ABG on a Dell Inspiron 600m.

Wireless worked great on 8.04, since upgrading to 8.10 I'm getting frequent connection drops. Every 5-10 minutes sometimes shorter sometimes longer the connection drops and reconnects in a matter of seconds. It is very frustrating.

---

### Post by Mortus Pryde on 2009-04-14
Will have to try this when I get home, granted I am almost certainly going to clean install my T42 when 9.4 releases.

Point of irony, my internal Intel 2100 Wireless B aside from the drops gets better reception in the basement then my wireless N PCMCIA adapter.

---

