---
title: "Wireless wpa2 with RT2790 on ubuntu 10.04 Can't connect"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by aatkco on 2010-05-23
Hi,
[COLOR=Red]**update** : It's confirmed , changing the encryption to "**AES**" instead of "**TKIP or AES**" solves the problem without any other modifications .[/COLOR]
I have RT2790 Wireless Adapter and My Wireless Network is protected  using wpa2 , When I try to connect T keep getting password prompt  screen, Is there anyway to solve this ?
My Modem is Linksys WAG160Nv2 And My ubuntu is 10.04 Final, No updates  Available

Thanks
Note : if this is a known bug please provide temp. solution, I need this to work
Note 2 : When I use My old Modem ( TP-Link ) it works with the same password and encryption ! But I can't use this modem for some family stuff , also the Linksys modem is much newer .
Note 3 : there are official 3 different drivers for linux for my card [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) , but how to use them ?

---

### Post by Drunkpunk on 2010-05-23
Same problem here. The wireless NIC worked fine with karmic and will work if all security is reset on the router.  Any help much appreciated.

---

### Post by aatkco on 2010-05-24
Heeeeeeeeeeeeeeeeeeeeeeelp

---

### Post by Drunkpunk on 2010-05-24
Bump!

---

### Post by chili555 on 2010-05-24
I have read on this forum of an issue where the router is set to mixed WPA ***and*** WPA2 mode. There is a problem with some drivers connecting. When the router is reset to WPA2 only (as mine is), it connects immediately. You all might check that setting in the router's administration pages.

---

### Post by ilomo on 2010-05-24
Hi,

I'm getting crazy trying to resolve the stuff; a week ago I installed Lucid on an Asus with iwl 3945 inside; everything worked fine but because of another problem I have recently installed it again two days ago and I can't connect via wireless.
Wifi signal is WPA-TKIP at home and at work and the interface tells me that PASSWORD IS INCORRECT.

I remember that the last week I installed a guys hand-made scrypt which included several functions, a wifi monitor included but: I dont remember WHERE did I download it from and neither remember the utilities name.

I have tried Wicd, Wifi-Radar... and can't get acces to MY internet wifi line!!!!!

---

### Post by Drunkpunk on 2010-05-25
> **chili555 said:**
> I have read on this forum of an issue where the router is set to mixed WPA ***and*** WPA2 mode. There is a problem with some drivers connecting. When the router is reset to WPA2 only (as mine is), it connects immediately. You all might check that setting in the router's administration pages.

Cheers for the input but AFAIK my router is set only to WPA2 Personal.  For u guys who are waiting on this desperately; I got some help on the Ultimate Edition forums that I'll be checking out in the next coupla hours.  The linkage is here: [http://forumubuntusoftware.info/viewtopic.php?f=68&t=4817](http://forumubuntusoftware.info/viewtopic.php?f=68&t=4817)

edit: when the "Wireless Authentication Required" dialogue comes up, it *is* set to WPA & WPA2 Personal with an arrow for a dropdown but no other options to choose.

---

### Post by aatkco on 2010-05-25
I'm gonna bump this until I got an answer, A big community like this one and nobody have a damn @^#%$#^ solution :( !!!!!

---

### Post by Drunkpunk on 2010-05-25
Aatkco: no joy on implementing the fix supplied in the link?

edit: Well here's weird - mine's fixed.  All I did was change the settings on the router to AES encryption only and after 3 reboots just to make SURE I'm getting online automatically every time.  Hope something works out for you guys who are still trying.

---

### Post by ilomo on 2010-05-25
Ive had to reinstall Lucid Lynx on my laptop and, strangely, I'm connected via wireless!!!!!!

Haven't done anything!!!!

I've used W7 enterprise edition with no problem till last week and because of my work, need stability; guess that Lucid isn't...

---

### Post by aatkco on 2010-05-27
It's already AES and I rebooted +30 times with no results

---

### Post by ilomo on 2010-05-27
Try to reinstall Ubuntu.
Mine's still workin fine...

---

### Post by aatkco on 2010-05-29
I have three different OS's , I can't reinstall it easily. Heeeeeeeeelp

---

### Post by seagullplayer77 on 2010-05-29
I can confirm this issue, and I can also confirm that it was *never* an issue in 9.10. So much for Lucid being a nice, stable LTS release. I've been sorely disappointed with it as a stable platfrom and I'm seriously considering switching back to Jaunty. At least everything worked.

Anyway, I'm using Wicd and my ability to connect to the WPA2 network I'm dealing with right now is spotty, at best. I'll get in maybe one time out of ten. The other nine, Wicd tells me that the password is bad, which is wrong. I've tried switching the router exclusively to AES encryption, but I'm hesitant to disconnect because I'm afraid that reconnecting will be a PITA.

And FWIW, I don't remember having this issue when I first installed 10.04. Perhaps a recent update broke the ability to easily connect to WPA/WPA2 networks?

I suppose it's worth mentioning that reinstalling Wicd solves the problem *sometimes.* Which leads me to believe that I'm just getting lucky, and that the reinstall has nothing to do with fixing the problem. But that's just a guess.

EDIT: I ditched Wicd for the standard Ubuntu network-manager package, and all seems well. It doesn't connect quickly, but it *does* connect reliably.

---

### Post by seagullplayer77 on 2010-06-01
I'd like to bump the thread, and I'd also like to report that I've been having issues connecting again.

After switching back to network-manager, I didn't have any issues for a while, but they've resurfaced. Sometimes, I'll be able to connect in an instant. Other times, it'll take several minutes of timing out and retrying before I get in. With network-manager, it's hard to tell, but with Wicd, it would always hang at "Authenticating password." It seems like this is a WPA issue.

---

### Post by Talon2 on 2010-06-01
> **seagullplayer77 said:**
>  It seems like this is a WPA issue.

This problem seems very familiar.  I posted the following bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

In my case with the rt2870, there were 3 problems:

- Won't connect.  This was solved by blacklisting 3 conflicting drivers.

- Won't do WiFi N.  This was solved by downloading and compiling the latest version of the driver.

- Won't do WPA2.  This was also solved by downloading and compiling the latest version of the driver.

If you go to MSG# 28 in the bug I providing the link to above, you will see a link to a thread where the person spells out how to do all of the steps I'm talking about.

In case anyone is wondering, support in Ubuntu for modern Ralink chipsets is BAD!

Good luck.

---

### Post by seagullplayer77 on 2010-06-01
I suppose I probably should've mentioned that I don't have the same wireless card as the OP. According to lspci, I have an Intel 3945ABG chip installed. I just spent twenty minutes trying to connect with no success, but reinstalling network-manager did the trick.

I'm not sure if it'll work again though, and in any case, that's far from a permanent fix. I'll nose around in Synaptic and see if there's any driver files that are worth reinstalling.

---

### Post by panderson on 2010-06-03
I concur with the above behavior.  I must admit that I first encountered this behavior in Karmic Koala, but after fooling around with multiple attempts, the problem went away.  Then, just the other day I upgraded to 10.04 and I have NOT BEEN ABLE TO CONNECT YET with my previous WPA2/PSK settings.  I am using a linksys router with mixed AES/TKIP.  I will switch to AES only, and if that doesn't work, I will attempt to switch from the default (Wcid?) by uninstalling it and installing network-manager instead.  I'll post my test results.

---

### Post by panderson on 2010-06-03
[COLOR=DarkOrange][B]I concur - changing WPA2/PSK encryption on my linksys  router to "AES" fixes problem.

I also re-installed network-manager, but I'm not sure this affected the situation any.  I also noticed that the wireless did connect WHILE connected with the hard line - e.g. two active connections.  While both connections were active - when I disconnected the hard line, the wireless stayed connected and I was able to ping google.com.

So here is what I did:
1. connect to router with hard line
2. change router wireless security to WPA2/PSK "AES" only.
3. re-install network-manager:

# sudo apt-get remove network-manager
# sudo apt-get install network-manager

4. connect with both wireless AND hard line, then disconnect hard line (pull cable out).
5. ping test:

# ping google.com

6. restart computer, see that it automatically logs on to wireless.
7. ping test (successful)

[/B][/COLOR]> **aatkco said:**
> Hi,
[COLOR=Red]**update** : It's confirmed , changing the encryption to "**AES**" instead of "**TKIP or AES**" solves the problem without any other modifications .[/COLOR]
I have RT2790 Wireless Adapter and My Wireless Network is protected  using wpa2 , When I try to connect T keep getting password prompt  screen, Is there anyway to solve this ?
My Modem is Linksys WAG160Nv2 And My ubuntu is 10.04 Final, No updates  Available

Thanks
Note : if this is a known bug please provide temp. solution, I need this to work
Note 2 : When I use My old Modem ( TP-Link ) it works with the same password and encryption ! But I can't use this modem for some family stuff , also the Linksys modem is much newer .
Note 3 : there are official 3 different drivers for linux for my card [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) , but how to use them ?

---

### Post by lnicks on 2010-06-16
I'd been having almost the same problem (I say almost because I never quite got my wireless to work in 9.10 before I upgraded) and likewise, this solution almost works.  =)

I switched the setting on the router to AES only and now my laptop does establish a connection...but it's terribly flaky (disconnects/reconnects almost constantly) and nearly unbearably slow (slow as in, I feel like it's 1998 again and I'm using dial-up.  It's pretty noticeable.)

Any thoughts why that behavior might occur?  Thanks!

---

### Post by johnmay on 2010-06-20
I was actually surprised when the  wireless usb adapter began to work. I was running 9.1, and after a first  (fatal) install of 10.04 I am running ubuntu again. 



The currently  trouble with the wireless devices seems to be purely related to WPA and  WPA2. I was already broadcasting AES only, and am still receiving the  authentication prompt instead of being logged onto the network.


 I am able to post, because I am also able to authenticate to a  network which uses WEP.
My wireless info: lsusb | grep rt
Bus 002 Device 002: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter  [ralink rt73]
 

Which suggests that the bug is not only related to the rt2870  chipset.


 I would like to find a workaround, and see the issue solved soon,  since so far the rest of the release is pretty cool.

---

### Post by dybet on 2010-07-29
i have problems as well with pci-e wifi and the rt2790 chipset.

can only connect with G, and throughput is horrible.:(

---

