---
title: "Heaphone jacks not working in Natty."
date: 2011-05-06
forum: Multimedia Software
---

### Post by mdrew93 on 2011-05-06
Hey all. When I start up my pc, occasionally the headphone jack works fine, but not usually. But it's really starting to get on my nerves. I am using Ubuntu 11.04 (fully updated) on an HP G-60 120 US. The results of sudo lshw -C multimedia are posted below if that will help.


  *-multimedia            
       description: Audio device
       product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:19 memory:c0000000-c0003fff


I know its an nvidia mcp77 HDMI audio driver. But it might just be a solder problem. I'll open it up soon and take a look. Hopefully I don't screw anything in there up too badly. I am experienced with soldering, so it shouldn't be a problem.

Thanks for all help.

EDIT: I restarted, and it seems to be completely arbitrary. Sometimes it works, sometimes it doesn't. Any help is appreciated.

---

### Post by lidex on 2011-05-06
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by mdrew93 on 2011-05-07
[http://www.alsa-project.org/db/?f=70d6910cd2b52344580586f145938e09f753780e](http://www.alsa-project.org/db/?f=70d6910cd2b52344580586f145938e09f753780e)

---

### Post by lidex on 2011-05-08
Try this:

```
echo "options snd-hda-intel model=laptop position_fix=1 enable=yes" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

I didn't see any real issues other than no mixer controls for headphone. If the fix above doesn't work, I would suspect your soldering issue.

---

### Post by mdrew93 on 2011-05-08
Thanks. It hasn't happened in a while. It just goes on and off. Some times it works, and sometimes it doesn't. Just random. But I did this and I hope the problem stops. I'll let you know if it keeps up.

Thanks again.

---

