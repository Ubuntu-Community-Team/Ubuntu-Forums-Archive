---
title: "downgrade ASUS bios for ati video drivers"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by bittergourd on 2006-09-22
i don't know if this is already posted or not. if not, it might be helpful.

my hardware:
ASUS K8N
radeon 9600pro

i tried to install fglrx drivers on my computer but failed again and again and again (and agian...). fglrxinfo and glxinfo always tell me it is using mesa driver instead of fglrx. despairing...

...until i see someone acutally has a solution to this. as the title suggests, they downgrade the bios to 1006. i sort of know that k8n board has compatability issues and sometimes lower version bios actually works better. so i tried, and it worked...

i don't know how wide this problem is, maybe k8ne, a8n boards all have the same issue? just hope my ](*,)  experience is helpful to someone else.

---

### Post by JackCorbae on 2007-03-22
I searched the net for hours trying to find any solution other than downgrading my Asus K8N-E Deluxe BIOS to 1006. I was running 1011.

It appeared I had no choice. fglrxinfo would constantly default to Mesa.

I went to the Asus site to download the 1006 BIOS and noticed there was a 1012 beta driver.

I don't know if the beta status will cause any other strange problems but after flashing my BIOS and rebooting ... my Radeon x1950 Pro AGP is running 1680x1050 FAST! ::KS

---

