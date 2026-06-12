---
title: "Mythbackend &quot;Forgetting&quot; input on boot"
date: 2010-06-30
forum: Mythbuntu
---

### Post by Furry_Fighter_20x66 on 2010-06-30
Hi All:

     I'm having some strange issues here since my upgrade to mythbuntu 10.04. After all reboots and even on one occasion for no reason at all as far as I can deduce, I have had issues with the backend "forgetting" its settings. The fix is simple: launch mythtv-setup and then exit again immediately. This seems to "remind" the backend that I have a pvr-150 plugged into it. 
     Fortunately for me I rarely reboot the backend anyway but this new issue where it just seemingly forgot its settings has me a little more concerned and I want to fix this so it doesn't happen when I am away from home or something. Anyone know what's causing this erratic behavior?

---

### Post by ian dobson on 2010-06-30
Hi,

Could it be that the backend is starting before the ivtv drivers are finished with loading?

Ubuntu/mythbuntu have gone over to using upstart to start most processes so, when you boot the system and it "forgets" you tuner card what do you see in the backend log file (/var/log/mythbackend.log). If you just restart the backend process with
restart mythtv-backend 

does it find the card? One solution would be to just add a delay to the startup script for your mythtv-backend. The configuration script is in /etc/init/mythtv-backend.conf.

I had a similar problem. I'm using external IPTV tuners and myth-backend tries to read the configuration (m3u file) from the webserver but as apache and myth started at the same time myth didn't always find the m3u file. My solution was to add a loop to the myth-backend startup script that waited until port 80 was open on the server before starting the backend.

Regards
Ian Dobson

---

### Post by Furry_Fighter_20x66 on 2010-06-30
Thanks Ian. I threw in a sleep command ahead of the starting of the backend to make it wait an additional minute and that cleared up the problem. \\:D/ I don't know why I never thought of that... :-k

---

