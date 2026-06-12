---
title: "Setting up Wifi"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by 97nrpwng on 2012-02-08
Hi All,

This is my first post so please be gentle.

I am trying to set up wifi on my Dell D610 and am having no ends of problems. I believe this article will solve the issue [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) for the internal card.

I know this because I had it working before. However I was using 10.04 and then upgraded to 11.10 which was unusable for me as the device is very old and it seems the new version makes everything run slow. So I have reverted back to 10.04 with a clean install (I had load of junk I wanted to remove anyway).

The problem is that without Wifi I only have limited wired internet access so I can not install using the internet access version on the above post. When I do the non internet access version it simply does not work. I think I got as far as step 3 on the 2nd part where it states to run ~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2. When I did this it came up with something about old and expression needed.

As I recall last time I had to install an external card a NWU275 and then when I had full internet access with that (it has a better range and can access a network point without any filters in place) I was able to run the fix in the post above.

Now the NWU275 ADDON card comes with Linux drivers on it apparently but there seems to be no way to install them.

I am rather new to linux so please give me basic instructions.

Thanks
Gary

---

### Post by chili555 on 2012-02-08
There are at least four ways to get Broadcom cards working. Some cards can be driven with two different methods and some work better than others. Before we can decide what works best for your card, we need more data. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.> This is my first post so please be gentle.That's my middle name!

---

### Post by 97nrpwng on 2012-02-08
Hi thanks for the quick reply. This is what I get when I type the above:

03:03.0 Network Controller [0280]: Broadcom Corporation BCM4311 [Airforce 54g] 802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)

So I assume the model is a BCM4311 and the PCI-ID 14e4:4319

---

### Post by 97nrpwng on 2012-02-08
Also I use a UK keyboard and it may be handy for people using the same to mention it is the same key as the \ which is on the left side of UK keyboards.

On my Dell laptop I had to press the ¦ button instead but on a normal keyboard it did show as |.

---

### Post by chili555 on 2012-02-08
Your Broadcom card simply needs firmware. Please get some limited wired access and in the terminal, do:```
sudo apt-get install b43-fwcutter firmware-b43-installer
```After its done, reboot and enjoy your wireless.

Post back, of course, if it doesn't go perfectly.

---

### Post by 97nrpwng on 2012-02-08
Thanks,

I tried and it comes up with the error:

Couldn't find package b43-fwcutter

---

### Post by chili555 on 2012-02-08
How about this?```
sudo apt-get install firmware-b43-installer
```I don't have a 10.04 machine to verify; sorry.

---

### Post by 97nrpwng on 2012-02-08
Nope I get the error below now:

Couldn't find package firmware-b43-installer

Thanks
Gary

---

### Post by chili555 on 2012-02-08
You are connected to ye olde internet, right?

I will be away for a few hours.

---

