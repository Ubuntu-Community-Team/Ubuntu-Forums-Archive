---
title: "RTL8111DL not detected"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by stefano.fraccaro on 2009-03-25
Hi,
   I have a asrock g31m-gs motherboard with rtl8111dl integrated Gigabit PCI-Express Ethernet... I have tried with Intrepid e Jaunty alpha6 but the kernel is unable to detect the nic. I can't see the nic in the output of lspci command   :-(
What can I do for this ethernet card??

The bios option "Enable OnBoard Lan" is active and the nic works fine in Windows...  ideas??

---

### Post by threetimes on 2009-04-25
I have the same mobo with the same chip and the same problem. But it get's better: Windows XP has the same problem as Ubuntu. So it's not ubuntu's fault (stupid conclusion, i know...). Any idea? I'll check the Realtek site for drivers/info for both platforms.

---

### Post by narween on 2009-04-27
Hi,

I got the same problem, G31M-GS motherboard and the network card, a RTL8111DL , is not shown with lspci

Any idea?

Regards,
Narween

---

### Post by K-Spaz on 2009-04-29
I downloaded a driver from Realtek.com but the instructions fail under 9.04

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

I didn't even look to see what I might be missing yet.  The make caused many errors.

---

### Post by Enav on 2010-08-21
Well the cause of this crazy problem is  some kind of bad driver support for WinXP, the simpthom is that you network card is unable to use autonegotiation feature for some unkow reason... to temporally fix this problem under windows you need to set NIC speed to 10Mps fullduplex... is the only way to make this NIC work under Win...  but for some crazy reason that change is save in some kind of FLASH memory inside the NIC... Wooops  that is not good...  because that setting is not compatible with Ubuntu, then your network card is not going to be detectec under ubuntu....  to use your NIC under ubuntu you need to load windows and change the NIC speed to 100Mps Fullduplex....  next reboot and load ubuntu... check your mail or something just to verify the network connection....

Conclucion:
-----------------------
This stupid problem only happens when you switch beetwen WinXP and Ubuntu, the only way to fix this problem is delete WinXp and install Win Vista or 7... this way you are not going to have this crazy issue when swap from Win To Ubuntu.

I dont consider this a solution but... there is no solutions...  WinXP is not well suported and the NIC driver is corrupting NIC settings or something like that

I use Win for gamming
and Ubuntu for everything else

---

