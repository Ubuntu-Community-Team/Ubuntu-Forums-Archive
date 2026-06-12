---
title: "Somebody or something is hijacking my password...."
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by red3rh on 2009-09-05
I have installed a used wireless card and can see all nearby network connections.  I select my personal wireless network, enter the WPA password but Ubuntu 9.04 cannot connect.  In about 2 minutes the OS tells me that an authentication password is required for this connection.  I choose "Show Password" and what appears looks nothing like what I typed in Network Manager.  Is there a hidden file somewhere that is automatically changing my password and preventing the connection?  Any ideas?

---

### Post by wojox on 2009-09-05
What type of wireless router do you have?

---

### Post by red3rh on 2009-09-05
LinkSys WMP 110

---

### Post by wojox on 2009-09-05
Log on to your router and check the password again.
It should be 192.168.1.1 for LinkSys.
Or reset it. You may want to configure wpa-psk.

---

### Post by imbjr on 2009-09-05
> **red3rh said:**
> and what appears looks nothing like what I typed in Network Manager

I've seen this happen. I bet it looks like a load of letters and numbers.

I cannot confirm this, but I suspect it's the hashed version of the password, so that it is not stored in plain text. Google indicates others have seen a similar thing, but I'm not finding a clearer explanation with only a quick search.

---

### Post by red3rh on 2009-09-05
Just re-checked the WPA password in the router and I am typing the right number and letter combination in Network Manager.  The router is a LinkSys Wireless G WRT54G.  The router says "WPA Algorithms TKIP".  Apparently, when I finish typing the correct password and select "Connect" something is changing the password to a completely different number and letter combination.  Is it possible that the wireless card has some type of imbedded file or does Ubuntu have a secret file that may be overriding what I type?

---

### Post by wojox on 2009-09-05
No it's just encrypting it like imbjr stated. Still can't get online?

---

### Post by red3rh on 2009-09-05
No.  I am in the forum at another machine.

---

### Post by wojox on 2009-09-05
The fact that your able to boot up and see networks is a plus. I have the same wireless router, but I'm connected via Ethernet cord and my wife and daughter use wireless and Vista. 

Here's a little help page.

[https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html](https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html)

Just type in the search box for wireless if that doesn't help.

---

