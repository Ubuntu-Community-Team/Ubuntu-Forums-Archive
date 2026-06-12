---
title: "Nvidia / dual monitor help please"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by StrangeRanger on 2007-12-07
I'm trying to get my lappy to work w/ an external monitor. Card is a GForce Go 7800. I believe I've got the Nvidia drivers installed properly. But when I go into the Nvidia control panel and select X Server Display Configuration it recognizes the monitors correctly, but I can't configure the external monitor.

When I "select" the external monitor and adjust its resolution etc. then hit Apply I get an error msg listing various reasons it won't / can't apply the settings. The last lines of the msg tell me I must save the settings to the x configuration file. 

So then I click the "Save to X configuration file" button and I'm prompted for the file to write to: 'etc/X11/xorg.conf'  - I click save and get:
Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.

I've tried checking file permissions, renaming the backup file, moving it etc but nothing I do seems to work. Any ideas? Thanks,
j

---

### Post by macele on 2007-12-07
try:

sudo nvidia-settings

with root you can move the old xorg.conf

---

### Post by StrangeRanger on 2007-12-11
Cool, thanks for the idea.
j

---

