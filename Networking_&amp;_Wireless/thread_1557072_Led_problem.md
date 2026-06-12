---
title: "Led problem"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by hakermania on 2010-08-20
So, annoyed by the blinking of the wireless led I decided to disable it, following some tutorials in the foroum...
Well, I realized that led blinking was actually useful for me, but now every time I open the PC the LED is disabled (the WiFi works fine), but I really need it. I deleted a file I created at /etc/network/if-up.d/ and after a reboot nothing seemed to happen...Can you help me a bit?

---

### Post by Iowan on 2010-08-20
Which tutorial did you follow? 
Is the current problem the blinking LED - or has the deleted file killed networking?

---

### Post by hakermania on 2010-08-20
I followed this one :[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=949642&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=949642&page=2)
(the one at the pre-last answer)
and now my wifi is constantly off (red)
I want it to make it blink normally as previously..

---

### Post by hakermania on 2010-08-23
Any help?

---

### Post by Iowan on 2010-08-23
This is out of my league - so I have NO idea if it will work. The script looks a bit odd in the last line. I see no definition for "TX" in the */etc/udev/rules.d/90-led.rules* file - only "radio" and "brightness". You might re-create /usr/local/bin/led - but change the "TX" in the last line to "radio".

---

### Post by hakermania on 2010-08-25
You mean simply change iwl-pyth0::radio/brightness text to 255?
This turns on the led but it still doesn't blink while network packets come and leave the PC... :/

---

### Post by Iowan on 2010-08-25
No, the "50" seems more appropriate.

---

