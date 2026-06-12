---
title: "hardware detected but does not connects to wireless"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by wolfmaniac on 2006-06-28
well i manached to connect to my router usins the bcm4306 by a howto in the forums.
now the problem is that whenever i reboot my system i m not able to find the router.
i have even tried to ping it but no response.

please can nebody help.

NB: i m not using nsdripper

instead i used bcmxx cutter

---

### Post by Eversmann on 2006-06-28
I had lots of problems with the opensource drivers for the bradcom drivers. Using ndiswrapper resolved all of them and made my life easier.

Try them (if you haven't done). It's worth the try.

Is the wifi radio enabled?

---

### Post by wolfmaniac on 2006-06-28
yes wifi is enabled.
also i tried using  ndiswrapper  but it said that driver found but no hardware present!!!!:confused:

---

### Post by Eversmann on 2006-06-28
Can you put your dmesg here?

---

