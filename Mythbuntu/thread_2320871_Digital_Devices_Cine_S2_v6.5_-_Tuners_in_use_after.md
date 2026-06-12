---
title: "Digital Devices Cine S2 v6.5 - Tuners in use after resume"
date: 2016-04-18
forum: Mythbuntu
---

### Post by proton23 on 2016-04-18
Hello!

I've read about resume issues with this card when using mythtv or tvheaded

I found a script for tvheaded and tried to modify it for mythtv but with no luck.
```
[Unit]
Description=Restart mythtv-backend and ddbridge
Before=sleep.target
StopWhenUnneeded=yes

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=/bin/systemctl stop mythtv-backend.service ; /sbin/modprobe -r ddbridge cxd2099 dvb_core
ExecStop=/sbin/modprobe ddbridge cxd2099 dvb_core ; /bin/systemctl start mythtv-backend.service

[Install]
WantedBy=sleep.target
```

Has anybody a solution for a tv-card occupying the tuner after resume, that I can adopt?

Best regards
Proton

---

### Post by proton23 on 2016-04-20
Can at least tell me somebody in which forum I can find some help with this problem, please?

Regards
Proton

---

### Post by proton23 on 2016-05-01
Now I know, that the backend couldn't start on boot because of the wrong password in ~mythtv/.mythtv/config.xml
Mythtv-backend starts now on boot and I can start and stop it with "systemctl"
but the script still wont't work, channels are still unavailable after resume.

Anybody an idea what wrong is with my script?

Best regards
Proton

---

