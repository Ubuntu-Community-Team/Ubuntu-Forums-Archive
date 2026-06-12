---
title: "Not detected onboard soundcard - ASUS k8n-vm"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by antubis on 2006-08-25
Hello,

I have a problem with my onboard sound card. The motherboard is K8N-VM. The sound device si not detected during the installation. How can I run the soundcard? Its enabled from BIOS. My colegue has the same PC but he installed Ubuntu 6.06 and he has no problems, but I installed the older ( 5.X ).

Thanks to all!

---

### Post by wjp.reg on 2006-08-25
"Sounds" like you should upgrade to 6.06 ;)

---

### Post by antubis on 2006-08-26
When I run Kubuntu Live CD 6.06 everythink is fine:

lspci: nVidia Corporation MCP51 High Definition Audio

Any suggestions?

---

### Post by alucinado on 2006-10-16
Hi Antubis,

I have a similar problem with Ubuntu 6.06. When I start with the Live CD, the audio is properly configured and everything works perfectly (different volume controls for the different outputs/inputs and even front headphones works).
But the installation did not configure the front headphones properly (they don't play any sound, just static) and a single PCM volume control is shown :-k I compared the /etc/modprobe.d/alsa-base and they are the same! :confused:

Good luck,
Alucinado

---

