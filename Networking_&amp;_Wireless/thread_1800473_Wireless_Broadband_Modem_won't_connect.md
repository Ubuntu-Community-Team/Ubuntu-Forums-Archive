---
title: "Wireless Broadband Modem won't connect"
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by fantab on 2011-07-09
I am unable to connect to the Internet with my **ZTE-AC2726 Reliance Netconnect Wireless Broadband Modem** on my Lucid. My present Kernel is _vmlinuz-2.6.32-32-generic._

I have installed **usbmodeswitch**- my modem is recognized (I think) as <*lsusb> *identifies it. I have also configured the network connection to the best of my knowledge. Yet the connection is elusive. 

Fedora Lovelock on my desktop connects it to to internet, all I had to do here was to do the basic configuration.

I have searched these forums for the solution but I could not find the definitive solution... 

I request the forum to help me resolve this.

Thank you.

---

### Post by fantab on 2011-07-09
Kindly Assist with the above... I have to get the wireless broadband working.

---

### Post by fantab on 2011-07-10
Still no help?

I have also tried the above device on my Bro's LMDE amd64 and the said device connects without any problems immediately after the basic configuration.

How do I get it to work with Lucid Lynx amd64?

---

### Post by AlexDudko on 2011-07-10
Is it a fresh install? As far as I remember, there was an issue with 64-bit version of Lucid Lynx. The 32-bit one worked without a hitch. But I was able to use my broadband wireless stick after all updates were installed. Is your system up to date?

---

### Post by fantab on 2011-07-11
> **AlexDudko said:**
> Is it a fresh install? As far as I remember, there was an issue with 64-bit version of Lucid Lynx. The 32-bit one worked without a hitch. But I was able to use my broadband wireless stick after all updates were installed. Is your system up to date?
  
Thank you AlexDudko for your reply. Yes, my Lucid Lynx system is up-to-date with all latest updates.

---

### Post by AlexDudko on 2011-07-11
What configuration have you done? What errors do you receive? Can you post the logs?

---

### Post by fantab on 2011-07-11
> **AlexDudko said:**
> What configuration have you done? What errors do you receive? Can you post the logs?

I have only done the basic config in the Network Connections... I added my usb broadband connection settings (like number, username, password) to the network connections.... (and I did the same in Fedora and LMDE). I don't get any error messages... device just won't connect to the internet. What logs do you want me to post? 

Thanks.

---

### Post by AlexDudko on 2011-07-11
See > /var/log/messages
And find there the messages about your broadband connection.
As an example here is my log:

> Jul 11 17:53:12 alex modem-manager: In mm_modem_enable
Jul 11 17:53:12 alex modem-manager: In mm_modem_get_state
Jul 11 17:53:12 alex modem-manager: (ttyUSB0) opening serial device...
Jul 11 17:53:12 alex modem-manager: In mm_modem_set_state
Jul 11 17:53:12 alex modem-manager: In mm_modem_get_state
Jul 11 17:53:12 alex modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Jul 11 17:53:12 alex modem-manager: (ttyUSB2) opening serial device...
Jul 11 17:53:12 alex modem-manager: In mm_modem_get_state
Jul 11 17:53:12 alex modem-manager: In mm_modem_get_supported_charsets
Jul 11 17:53:12 alex modem-manager: In mm_modem_set_charset
Jul 11 17:53:12 alex modem-manager: In mm_modem_set_charset
Jul 11 17:53:12 alex modem-manager: In mm_modem_set_state
Jul 11 17:53:12 alex modem-manager: In mm_modem_get_state
Jul 11 17:53:12 alex modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)
Jul 11 17:53:12 alex modem-manager: Registration state changed: 1
Jul 11 17:53:12 alex modem-manager: In mm_modem_get_state
Jul 11 17:53:12 alex modem-manager: In mm_modem_set_state
Jul 11 17:53:12 alex modem-manager: In mm_modem_get_state
Jul 11 17:53:12 alex modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> registered)
Jul 11 17:53:12 alex modem-manager: In mm_modem_get_state
Jul 11 17:53:12 alex modem-manager: In mm_modem_get_state
Jul 11 17:53:12 alex modem-manager: In mm_modem_connect
Jul 11 17:53:12 alex modem-manager: In mm_modem_get_state
Jul 11 17:53:12 alex modem-manager: In mm_modem_set_state
Jul 11 17:53:12 alex modem-manager: In mm_modem_get_state
Jul 11 17:53:12 alex modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
Jul 11 17:53:12 alex modem-manager: In mm_modem_set_state
Jul 11 17:53:12 alex modem-manager: In mm_modem_get_state
Jul 11 17:53:12 alex modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> connected)
Jul 11 17:53:12 alex pppd[5159]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Jul 11 17:53:13 alex kernel: [   89.312510] PPP generic driver version 2.4.2
Jul 11 17:53:13 alex pppd[5159]: pppd 2.4.5 started by root, uid 0
Jul 11 17:53:13 alex pppd[5159]: Using interface ppp0
Jul 11 17:53:13 alex pppd[5159]: Connect: ppp0 <--> /dev/ttyUSB0
Jul 11 17:53:13 alex pppd[5159]: CHAP authentication succeeded
Jul 11 17:53:13 alex pppd[5159]: CHAP authentication succeeded
Jul 11 17:53:13 alex modem-manager: (net/ppp0): could not get port's parent device
Jul 11 17:53:13 alex kernel: [   89.580321] PPP BSD Compression module registered
Jul 11 17:53:13 alex kernel: [   89.612382] PPP Deflate Compression module registered
Jul 11 17:53:15 alex pppd[5159]: Could not determine remote IP address: defaulting to xx.xx.xx.xx
Jul 11 17:53:15 alex pppd[5159]: local  IP address xx.xxx.xxx.xx
Jul 11 17:53:15 alex pppd[5159]: remote IP address xx.xx.xx.xx
Jul 11 17:53:15 alex pppd[5159]: primary   DNS address xx.xxx.xxx.xx
Jul 11 17:53:15 alex pppd[5159]: secondary DNS address xx.xxx.xxx.xx


---

