---
title: "Broadcom Wireless issues AGAIN"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by underdog512 on 2009-12-07
I have had this issue with broadcom wireless card for I don't how many versions.  

Heres what happens.  I get all the broadcom drivers installed and I am connecting to wireless networks and life is good. Until one day out of the blue Ubuntu just decides it does not want to connect to any network at all anymore.

On secured networks, the authentication window keep popping up over and over again like my password isn't right (and i know it is!).  On unsecured networks,  it will just keep trying to connect for a few minutes and then finally give up.  

I have a dell studio 15 running 32-bit Ubuntu 9.10

Here is my lspci output for my broadcom card.

09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by mikey.duhhh on 2009-12-07
I installed 9.10 on a Presario 2100 laptop with a Broadcom 4306 wireless.  First boot asked me for a password for the wireless (Seahorse - passwords and keyring under Applications>Accessories) and then, nothing.  

     So I found some info about downloading b43 and b43legacy drivers in a tar file and moving the contents to /lib/firmware/, which I did and still nothing.  

     Then I plugged it into a lan and updated all 147 updates and it worked.... on an open network.  


     When I took it to the coffee shop today and booted, it would not connect to the WPA network there.  Seahorse asked me for the password, then the wireless network asked me for its password, and after about one minute or so the wireless network asked me for its password again, and again, and again. 

I used gksudo seahorse so I could delete all the passwords under it and tried again.  No, it wanted a password to use the wireless again.  Could Seahorse be interfering with the wireless?

And how can I fix something with so little explanatory documentation?

---

### Post by underdog512 on 2009-12-08
I have found several forum posts and bug reports related to Broadcom wireless issues. most of them have to do with initial setup and driver issues so I just wanted to clarify.  This was working beautifully for a few months and then maybe 2 weeks ago it just stop for no apparent reason.

---

### Post by underdog512 on 2009-12-08
bump

---

### Post by teward on 2009-12-08
> **underdog512 said:**
> I have had this issue with broadcom wireless card for I don't how many versions.  

Heres what happens.  I get all the broadcom drivers installed and I am connecting to wireless networks and life is good. Until one day out of the blue Ubuntu just decides it does not want to connect to any network at all anymore.

On secured networks, the authentication window keep popping up over and over again like my password isn't right (and i know it is!).  On unsecured networks,  it will just keep trying to connect for a few minutes and then finally give up.  

I have a dell studio 15 running 32-bit Ubuntu 9.10

Here is my lspci output for my broadcom card.

09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

I know there's a bug with WPA and stuff, and also that there were issues with Broadcom cards after the most recent kernel update (note: this is what I found by watching the forums.  I don't use 9.10).



> **mikey.duhhh said:**
> I installed 9.10 on a Presario 2100 laptop with a Broadcom 4306 wireless.  First boot asked me for a password for the wireless (Seahorse - passwords and keyring under Applications>Accessories) and then, nothing.  

     So I found some info about downloading b43 and b43legacy drivers in a tar file and moving the contents to /lib/firmware/, which I did and still nothing.  

     Then I plugged it into a lan and updated all 147 updates and it worked.... on an open network.  


     When I took it to the coffee shop today and booted, it would not connect to the WPA network there.  Seahorse asked me for the password, then the wireless network asked me for its password, and after about one minute or so the wireless network asked me for its password again, and again, and again. 

I used gksudo seahorse so I could delete all the passwords under it and tried again.  No, it wanted a password to use the wireless again.  Could Seahorse be interfering with the wireless?

And how can I fix something with so little explanatory documentation?

As for this issue, again, there were problems with WPA and the most recent kernel update.  There hasn't yet been a fix (as far as I can find), so keep checking the forums.



For both of you, I'm sorry I can't be of more help.  There's bound to be more experienced users around eventually, so you don't need to keep bumping your threads.

Also, the second poster I quoted: Consider in future taking your problems and posting them into a new thread rather than piggyback off of someone else's thread.

---

### Post by underdog512 on 2009-12-14
> **TrekCaptainUSA said:**
> 
As for this issue, again, there were problems with WPA and the most recent kernel update.  There hasn't yet been a fix (as far as I can find), so keep checking the forums.


Confirmed. The latest kernel update is the issue.  I booted to the previous kernel from the grub menu and my wifi worked like a charm.  

So for those out there having issues with broadcom wireless, access the grub menu and select the previous kernel version to boot with.

---

