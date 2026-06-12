---
title: "Aircrack-ng"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by tpacyga2 on 2009-07-28
I am trying to test out my networks security using aircrack, but am having some trouble.  I have a Macbook Pro and am using the restricted driver that comes with ubuntu for the wireless card.  I use

sudo airmon-ng start eth1

to put into monitor mode (I don't know what channel means, can anyone help me out with that), and it says monitor mode enabled, but when I check the status using

sudo airmon-ng

it doesn't say it is enabled, and when I use airodump (sudo airodump-ng --write test eth1) I get this output:

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

I am kind of new to using Ubuntu, so if someone could help me out that would be much appreciated.

---

### Post by tpacyga2 on 2009-07-28
Can anyone help me out, or point me in the right direction?  Is this in the right section?

---

### Post by lswb on 2009-07-28
According to the error messages you've posted, eth1 on your system is an ethernet (wired) interface, not wireless. In a terminal try the command "sudo iwconfig" and look for an interface that doesn't have "No wireless extensions" in the description.

---

### Post by Crafty Kisses on 2009-07-29
Depending on what kind of card you have you may need the injection patch. What are the results of the following command?
```
lspci
```
I know there are problems with the b43 cards that require the injection patch. You need to grab the injection patch and apply the patch if you do indeed have the b43 card, you can apply the patch by running:
```
patch -p1 -i b43-injection-<kernel version>.patch
```
Then of course once you have patched, check and see if the newly patched module is in use, run the following:
```
modinfo b43
```
That will give you details about the module, and from there you can check if you're currently running the patch.

---

### Post by tpacyga2 on 2009-07-29
After typing the command sudo iwconfig, the only interface that doesn't have "No wireless extensions" is eth1, so I think that that is the wireless interface.

After typing lspci I get:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 05)
0c:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
0d:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02)


So I am guessing that I do have a b43 card?  Since it is BCM4328 right?

---

### Post by Crafty Kisses on 2009-07-29
Yes, now from what I remember, this patch is for older kernels, but I could be wrong. Now depending on what kernel you have, you need different patches. What are the results of the following?
```
uname -r
```
I need to know that first, but let's just say for the sake of time your using the 2.6.25 kernel. Then you need to grab the patch:
```
wget http://patches.aircrack-ng.org/b43-injection-2.6.25-wl.patch
```
Then you need to apply the patch:
```
patch -p1 < b43-injection-2.6.25-wl.patch
```
Now in same cases you need the fragmentation patch, you can grab that as well by running:
```
wget http://www.latinsud.com/bcm/mac80211_2.6.24.4_frag.patch
```
Then apply the frag patch:
```
patch -p1 < mac80211_2.6.24.4_frag.patch
```
That's the basics, but there's is a way more in depth look right **[here.]("http://www.aircrack-ng.org/doku.php?id=b43")** Read that, that should get you going.

---

### Post by tpacyga2 on 2009-08-01
The output of uname -r is:

2.6.28-14-generic

That page says that I just need the basic mac80211 frag+ack patch, im not really sure what that is.

---

### Post by tpacyga2 on 2009-08-03
I found the patch I need to apply, but I am not sure how to apply it:

[http://aircrack-ng.org/doku.php?id=mac80211&DokuWiki=6bbb39eb0ac23ea9d06108a33ac5c5fb](http://aircrack-ng.org/doku.php?id=mac80211&DokuWiki=6bbb39eb0ac23ea9d06108a33ac5c5fb)

I need the 2.6.28+ one, but it just opens a text file.  Am I supposed to save this somewhere or type it in somewhere?

---

### Post by tpacyga2 on 2009-08-05
No one has responded in a while, I still haven't gotten this to work.  I tried patching the mac80211 stack but ended up messing up my system and having to reinstall.  I think what I am really having problems with is getting mon0 to show up as one of the interfaces?

---

### Post by Crafty Kisses on 2009-08-05
> **tpacyga2 said:**
> I found the patch I need to apply, but I am not sure how to apply it:

[http://aircrack-ng.org/doku.php?id=mac80211&DokuWiki=6bbb39eb0ac23ea9d06108a33ac5c5fb](http://aircrack-ng.org/doku.php?id=mac80211&DokuWiki=6bbb39eb0ac23ea9d06108a33ac5c5fb)

I need the 2.6.28+ one, but it just opens a text file.  Am I supposed to save this somewhere or type it in somewhere?

You can apply the injection patch by running:
```
patch -p1 < patchname
```

---

### Post by tpacyga2 on 2009-08-05
ted@ted-laptop:~$ sudo patch -p1 < [http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch](http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch)
bash: [http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch:](http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch:) No such file or directory

that is what happens when I did that and I have kernel 2.6.28:

ted@ted-laptop:~$ uname -r
2.6.28-14-generic

---

### Post by Crafty Kisses on 2009-08-05
> **tpacyga2 said:**
> ted@ted-laptop:~$ sudo patch -p1 < [http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch](http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch)
bash: [http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch:](http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch:) No such file or directory

that is what happens when I did that and I have kernel 2.6.28:

ted@ted-laptop:~$ uname -r
2.6.28-14-generic

Hey there my friend! You need to direct the patch to actually where to apply the patch. So for example, you would run:
```
patch -p1 < (/path/to/patch/file)
```
So in essence, if the injection patch is called "injection-patch" and you saved the patch to your desktop, you would run: 
```
patch -p1 < /home/username/Desktop/injection-patch
```
Then in theory, that should apply the patch.

---

### Post by tpacyga2 on 2009-08-06
Im sorry if I am making dumb mistakes, I am kind of new at this, but it is asking me to enter a file name, and I tried searching for mac80211, and different variations and I don't know what file I am supposed to patch?

ted@ted-laptop:~$ patch -p1 < /home/ted/Desktop/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/net/mac80211/tx.c b/net/mac80211/tx.c
|index 0855cac..221bed6 100644
|--- a/net/mac80211/tx.c
|+++ b/net/mac80211/tx.c
--------------------------
File to patch: 



This is line 5 of the patch which I think it is talking about:

@@ -611,11 +611,19 @@ ieee80211_tx_h_sequence(struct ieee80211_tx_data *tx)

which I have no idea what it means.

---

### Post by guerramacina on 2009-08-17
i am having this EXACT same problem...any help would be appreciated

---

### Post by guerramacina on 2009-08-17
Can anyone help with this problem? I have been beating my brains out googling this problem and can't seem to figure it out.

---

### Post by tpacyga2 on 2009-08-17
OK, I really need help with this.  I have tried everything and nothing is working, this is what I am using:

-Macbook pro 4.1 with linux kernel 2.6.28-14-generic with ubuntu 9.04
-The network controller I have is BCM 4328 (14e4:4328)
-I am using the Broadcom STA wireless driver that came with Ubuntu 9.04

When I run ifconfig my wireless interface is eth1 not wan0, I don't no if this is a problem, if it is what can I do about it?

I run sudo airmon-ng check kill, then sudo airmon-ng start eth1

When I do ifconfig again I thought I am supposed to see a mon0 interface, but it isn't there, is that a problem, if so how can I fix it?

When I run sudo airodump-ng eth1 i get:

ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

what is rfmon and how do i enable it, if it is running the command airmon-ng start eth1, I have done that, I have also patched the mac80211 stack, someone please help me out.

---

### Post by guerramacina on 2009-08-18
how did you manage to patch the file?

---

### Post by guerramacina on 2009-08-18
I guess this is a lost cause. I will continue googling anyways!

---

### Post by lswb on 2009-08-18
This page referring to the b43 driver says [http://www.aircrack-ng.org/doku.php?id=broadcom&DokuWiki=19d0755190f766a12d2860f63e0c807c](http://www.aircrack-ng.org/doku.php?id=broadcom&DokuWiki=19d0755190f766a12d2860f63e0c807c)

says:
Most broadcom cards are supported EXCEPT the following:

    *      PCI ID 14e4:4315
    *      Wireless-N

Are you sure your card is NOT in this category?

And I would suggest foregoing the patching until you get monitor mode working, it is just confusing the issue (to me anyway)

---

### Post by tpacyga2 on 2009-08-19
when i run lspci -nn i get this for the network card:

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 05)

so its: PCI ID is 14e4:4328 not      PCI ID 14e4:4315
and i dont no what wireless-n is but i don't think i have that

So when you run start airmon-ng eth1 are you supposed to get another interface in ifconfig called mon0?  Or does it change the eth1 interface to monitor mode?  Any suggestions on getting monitor mode working or mon0 to show up in ifconfig?

---

### Post by sqvelasquez on 2010-07-20
Your card is not supported by the b43 driver so u cannot run aircrack-ng cuz it will not enter monitor mode. Sorry man

---

