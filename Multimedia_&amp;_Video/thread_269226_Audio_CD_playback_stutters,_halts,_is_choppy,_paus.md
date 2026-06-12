---
title: "Audio CD playback stutters, halts, is choppy, pauses every few seconds"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by rwinter on 2006-10-01
Hi, Help a newbie to Ubuntu. I have loaded Dapper Drake (6.06.1 LTS) onto an IBM 300GL Celeron 333Mhz (P2/PII generation) desktop with 256 Mb of ram. It has an Opti ISA bus sound card which is driven by the opti93x module. Audio CD playback halts for two or three seconds every 10-15 seconds. I've spent several days doing google searches with no direct hits on a solution (or anyone having this specific problem).

I installed the direct CD to soundcard audio cable suspecting processor speed and DMA problems, but it had no effect. I also could not find a Gnome GUI for manipulating the sound card settings (Master, line in, mic, CD, aux, etc.) Is there such a thing? I suspect that the sound card is not configured to use the cable at all.

I next used sysv-rc-conf to disable twelve unneeded services: bluez brltty festival hotkey-setup hplip laptop-mo? lvm mdadm mdadm-raid nvidia-ker pcmcia pcmcia-util

This improved the situation - the pauses were less than 1 second every 10-15 seconds.

Here are the 'ps -ef', dmesg, lspci listings - hopefully something in there will be a clue. Please let me know if there's anything else that can be improved.



Thank you,
-Robert

---

### Post by rwinter on 2006-10-02
bump

---

