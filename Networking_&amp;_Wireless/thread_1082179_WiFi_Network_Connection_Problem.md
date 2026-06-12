---
title: "WiFi Network Connection Problem"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by Fulviobru on 2009-02-27
I just installed ubuntu on a laptop and was trying to set up WiFi connection to my home router a US Robotics 9106. 
I select the automatic roaming mode for wireless. 
The laptop finds the broadcast SSID.
It then asks for the passphrase, which I input and it seems the connection to the wireless router is ok. But there is no Internet connectivity (tried everything including ping a website) and keeps asking for the passphrase.
Any suggestions?

ps: I just did the same procedure for the new Windows Vista based laptop of my wife and it worked on the first attempt. Don't tell me Windows is easier and more robust than Linux :confused:

---

### Post by superprash2003 on 2009-02-27
is this a WEP key?? if so try all various combinations, 64bit,128 bit ( passphrase)

---

### Post by Fulviobru on 2009-02-27
Yes is a WEP key 128 bits. Already tried with the other possibilitis but they are clearly wrong since the number of allowed char for the password are different from mine (13 char).

---

### Post by sgosnell on 2009-02-27
Is the router using MAC filtering?  If so, you'll have to give it the MAC address of the laptop and have it allow that connection.  Are you 100% certain you're using the correct password, with correct capitalization?

---

### Post by Fulviobru on 2009-02-27
Don't think so, since it uses DHCP which assigns IP addresses automatically. In addition on other machines running Windows did not need to do anything else than input the passkey (which is correct including capitalisation always for the same reason: it works) 
I see a lot of threads on Wireless connectivity problems: isn't there a problem with release 8.10 on the matter?

---

