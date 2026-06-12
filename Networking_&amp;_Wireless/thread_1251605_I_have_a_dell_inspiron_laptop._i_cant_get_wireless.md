---
title: "I have a dell inspiron laptop. i cant get wireless internet setup. please help!"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by Ilovecomputers on 2009-08-27
what do i do to get my wireless card to get internet access via my router at home and through any wifi. the card in the laptop is a dell bcm4306 802.11b/g. i called my local cable company where i get dsl wireless and they dont know anything about ubuntu to help me. what do i do? how to i set up wireless?? please help.

---

### Post by benmoran on 2009-08-28
> **Ilovecomputers said:**
> what do i do to get my wireless card to get internet access via my router at home and through any wifi. the card in the laptop is a dell bcm4306 802.11b/g. i called my local cable company where i get dsl wireless and they dont know anything about ubuntu to help me. what do i do? how to i set up wireless?? please help.

Hello I also have an Inspiron (1501). The best thing for you to do is either plug it in using a network cable (or temporarily a spare USB network adapter like I do), and then on the menu go to:
System, Administration, Hardware Drivers
This will automatically download and install the binary drivers for your card. You may have to do a system update first, but going to:
System, Administration, Update Manager

Also read [www.ubuntu1501.com](www.ubuntu1501.com) for more in-depth guides. It's really quite easy.

---

### Post by Ilovecomputers on 2009-09-02
> **benmoran said:**
> Hello I also have an Inspiron (1501). The best thing for you to do is either plug it in using a network cable (or temporarily a spare USB network adapter like I do), and then on the menu go to:
System, Administration, Hardware Drivers
This will automatically download and install the binary drivers for your card. You may have to do a system update first, but going to:
System, Administration, Update Manager

Also read [www.ubuntu1501.com](www.ubuntu1501.com) for more in-depth guides. It's really quite easy.

Hey i wanted to write back becuase i fixed the problem. I really appreciate what ubuntu has to offer so i wanted to share how i resolved this problem so it may help others. After i installed the ubuntu OS 9.04 i created the wireless network. Ubuntu always asks you to download about 175mb of software after you install the OS. After i installed all the software updated, rebooted the wireless networks and all wifi networks were recognized! So it must have been that the updated included the drivers to the wireless card. 
I do have another issue now. Everytime i boot the computer it asks me to enter an encryption key for the wireless network. It it many numbers and letters. I would wondering how i can just boot and get to my desktop without having to enter the key anytime. can anyone tell me what to do?
thanks.

---

### Post by Bucky Ball on 2009-09-02
It's a catch 22 situation. The wireless drivers are restricted so not part of the install. But to get wireless to happen you have to get online via ethernet cable and agree to install the restricted drivers!

By the way, you will find that your card is actually a Broadcom chipset and, as you have found, these cards are now pretty well supported (not always the case!). Interesting to note that Dell don't actually make anything! They assemble the bits and sell them as Dell computers.

Open a terminal:

Applications->Accessories->Terminal

and paste this in:

```
lspci
```Down near the bottom of the output from that command you will find the details of your wireless card.

Also, in:

System->Administration->Hardware Drivers

... you will probably find you are using the b43 driver, specifically for Broadcom cards. :)

Welcome and good luck with it all.

---

