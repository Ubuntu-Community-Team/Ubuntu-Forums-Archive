---
title: "iwconfig w/ wpa_supplicant guide request?"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by dragos240 on 2009-05-23
I have a wpa/wpa2 connection (I don't know which :() and I was never able to get an open connection working, so nm-applet is the only way right now >.<. Help?

---

### Post by dragos240 on 2009-05-24
BuMp.

---

### Post by kevdog on 2009-05-24
I have no idea what you are asking about.  NWM is never the only way!

---

### Post by dragos240 on 2009-05-24
> **kevdog said:**
> I have no idea what you are asking about.  NWM is never the only way!

I can't get a connection to the internet using iwconfig. I don't know how. And I want to know how. And how to use it with a wpa connection.

---

### Post by Icehuck on 2009-05-24
I'm actually looking for help on this as well. Tried following your guide here [http://ubuntuforums.org/showthread.php?t=571188&highlight=manually+connect+wifi]("http://ubuntuforums.org/showthread.php?t=571188&highlight=manually+connect+wifi") with no success. Network Manager works just fine, but I rather just use the command line to connect to my wifi since I'm switching to DWM.

---

### Post by dragos240 on 2009-05-25
> **Icehuck said:**
> I'm actually looking for help on this as well. Tried following your guide here [http://ubuntuforums.org/showthread.php?t=571188&highlight=manually+connect+wifi](http://ubuntuforums.org/showthread.php?t=571188&highlight=manually+connect+wifi) with no success. Network Manager works just fine, but I rather just use the command line to connect to my wifi since I'm switching to DWM.

Yeah, I need to connect to wireless using iwconfig because I don't have an ethernet connection and I want to install arch. By the way, chakra isn't working either.

---

### Post by kevdog on 2009-05-25
Try this:
[http://ubuntuforums.org/showthread.php?t=571188&highlight=manually+connect+wifi](http://ubuntuforums.org/showthread.php?t=571188&highlight=manually+connect+wifi)

---

### Post by dragos240 on 2009-05-25
Okay, I followed the guide, and when I did "wpa_supplicant$ sudo wpa_supplicant -Dwext -iwlan0 -cwpa_supplicant.conf" (without quotes of course)

I got "CTRL-EVENT-SCAN-RESULTS"

And just so you know I used a compiled from source version of wpa_supplicant, it was actually a perfectly clean one too, no errors or warnings.

---

