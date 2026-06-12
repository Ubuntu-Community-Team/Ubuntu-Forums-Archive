---
title: "Two Providers, Two Modems, one PCI, one USB"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by Malac on 2006-06-19
Hi,
I have a USB ADSL Modem (currently showing up as ppp0) which is on all the time and I use as my normal internet connection and picking up e-mail which is through new ISP.

I have a slow PCI 56K linmodem which I need to use to connect to my old ISP when I send e-mails from my old e-mail addresses as these are specific addresses I'd rather not change.

I can use just the PCI 56K linmodem if I uninstall/swap all the modules and reconfigure the dialup files and reboot.
OR
I can use just the USB ASDL modem if I reconfigure and reboot for that.

Is there anyway that I can set the PCI modem to not use ppp0 (maybe set it to ppp1 or something) and just dial that when I need to send an e-mail, then hang up when finished.

This used to be what I did on Windows and would like this ability if possible.

Thanks in advance.

---

### Post by mips on 2006-06-19
The majority of ISP will allow you to access their mail servers via a web browser from any isp in the world to read & send mail. Would this not be a easier option ?

If you don't like the above you could always configure your email client with a new account reflecting the dial-up isp pop3 & smtp server details + username/password and u should be able to download your mail from the old isp without physically dialing into their network.

---

### Post by Malac on 2006-06-19
Downloading is not the problem, sorry should have been clearer, that works fine it's the sending(uploading) that's the problem.

---

### Post by mips on 2006-06-19
Please elaborate more, who is your ISP ?

---

### Post by Malac on 2006-06-20
I have a current 512K ADSL USB connection with SupaNet (Always On)
I have an old dial-up account with Tiscali which has the e-mail addresses I need to use.

I use SupaNet now on the USB Modem as my main connection.
Normal web access and access to the POP3 servers of (Tiscali) to collect e-mail from my old @tiscali.co.uk accounts work through this connection.

I have an old dial-up account with Tiscali which is a "pay-as-you-go"  i.e. they charge me for the call time.

I cannot connect to the Tiscali SMTP server to send mail through the SupaNet connection.
I have to be dialed in on the Tiscali number on my 56k modem, as they check the connection type at their end somehow.

At the moment I can have *either* the ADSL USB Modem *or* the PCI 56K Modem connected as they are both "mapped" to ppp0. This involves re-writing some files e.g. interfaces and options and resolv.conf removing references to the USB modem and then completely rebooting everytime I need to send one e-mail or return receipt or reply to someone.

In Windows the connections were handled differently as the modems were seen as different things and I could tell Windows to use a specific modem for a specific provider and both connections could run at the same time.
To elaborate;
------
I could pick-up all my e-mails connected via ADSL USB Modem.
                      Sift through, sort, compose replies, etc.
                      Dial the Tiscali connection on the 56k Modem.
                      Hit send and it would do the "handshake" stuff over that connection
                      Thus allowing me to connect to the Tiscali SMTP server, sending my mail.
                      Then just hang-up the Tiscali connection. Costing me minimum pennies in connection fees.
-----

1/. How do I do this in Ubuntu, as both are currently "mapped" to ppp0?
2/. Can I create a ppp1 for the 56K Modem or move the ADSL USB Modem to another adapter name (eth1 for example)?
3/. How does Ubuntu handle the different "options" files needed for each connection?

I have several e-mail addresses for various things and would like not to have to change them and inform multiple contacts as people have put these e-mail addresses in there allow/friends/trust list in spam filters etc.

Thanks for your time and patience.

---

### Post by Malac on 2006-06-23
Anybody?????

---

### Post by mips on 2006-06-23
Malac, it must be possible but unfortunately I don't know how. Maybe google or search these forums.

---

### Post by bishop1641 on 2007-02-23
An excellent place to start

[http://www.lartc.org/](http://www.lartc.org/)

---

### Post by Malac on 2007-02-24
> **bishop1641 said:**
> An excellent place to start

[http://www.lartc.org/](http://www.lartc.org/)
I thought this thread was dead. I 'd almost given up. :)
Thanks for the link it should prove useful. I am still having trouble finding out how to get both modems to appear as ppp0 and ppp1 but I'll get there.
Thanks for the response.

---

