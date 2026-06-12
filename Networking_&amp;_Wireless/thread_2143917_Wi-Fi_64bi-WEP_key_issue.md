---
title: "Wi-Fi 64bi-WEP key issue"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by Thyber on 2013-05-10
Hi,

I've been using the same wep-key since long, and after switching from Windows 7 to Ubuntu, I'm encountering a strange problem, one which google doesn't seem to help with.

I've got a belkin router and a broadcom wireless built-in adapter which works fine when I turn off my wep-encryption.

But when I turn it on, it doesn't seem to connect, and I'm using the correct wep-hex-phrase.

Is this a known issue (google and forum search shows no info)???

I don't want to be stuck with an open network...

using 12.04lts version

---

### Post by Hadaka on 2013-05-10
Hi, try this..
click the wireless icon...(upper right next to envelope)
click Edit Connections
click Wireless
click (your ssid)
click Edit
click Wireless Security
at Security setting..click the down arrow and choose
    WEP 40/128-BIT Key (Hex or ASCII)
Enter You hex-phrase
click Connect Automatically
click available to others
click SAVE
close
boot.

---

### Post by Thyber on 2013-05-10
Hadaka,

I've tried all "menu's" and even tried doing it via WICD as I read it solves alot, I still don't manage to connect to my secured network.

---

### Post by Hadaka on 2013-05-10
Hi, you might try letting the router generate it's own
26 character key for your wifi configuration so that
once its working.......change it to the key you like.
It has to be something simple thats being over looked
if it worked before and if it works with other devices
there is usually a small error being overlooked.
good luck !

---

### Post by Thyber on 2013-05-10
I'm using a simple 10 digit key taken from my parents first router, it kinda stuck for me the last 10 years. 
I tried WPA with the same password... and that's no success either at first sight? Strange how it worked  with every other device and OS ranging from Xbox, Android, Ipod Touch, Iphone, MacMini... yet ubuntu is the first one to do difficult...

---

### Post by pqwoerituytrueiwoq on 2013-05-10
when it prompts for a wep key you have to use the hex key (eg: D0B17F91EC ), not the passphrase like you could back in 10.04
to use the passphase you have to go into the net connections editor and under security change it from key to passphrase

---

### Post by Thyber on 2013-05-10
They key I use is also generated, C5DDBD92E3...

---

### Post by varunendra on 2013-05-11
Thyber,

Let's take a look at all current settings. Please follow the Wireless Script link in my signature, download the script, and run it while you are trying to connect wirelessly (and failing).

Just to make sure everything else is fine. :)

---

### Post by Thyber on 2013-05-13
I forgot to mention this is my first experience with ubuntu.

I realized I'm only using my laptop for "casual" stuff and wanted to experiment with Ubuntu, which should be able to offer a perfectly good "daily use" experience.

It does give me a perfectly usable interface...

But since I want to keep my wifi protected... and don't want to use a cabled connection with my router... I'm kinda-stuck right now. 

I installed drivers and wicd in the software center. 

fiddled for hours, googled, tried solutions ...

did a clean-install of ubuntu. retried all of the above...

read things about wpa-supplicant today (at work) might be trying that out... but still if WEP didn't work, and WPA doesn't work either...

Can anybody give me the terminal codes to connect to my wifi with wifi pass? I wouldn't mind uninstalling the network manager since I'll only be connecting to this specific wifi at home.

ESSID name = Cavia4Belgium

---

### Post by varunendra on 2013-05-13
Please download and run the script I suggested in my previous post. It will generate a diagnostics report regarding your wireless settings (without including any sensitive data). Post back the report (netinfo.txt file or its contents), or its pastebin link as asked in the linked post.

Without relevant info on the issue, we can't offer any precise help. The script is perfectly safe, be assured on that :).

---

