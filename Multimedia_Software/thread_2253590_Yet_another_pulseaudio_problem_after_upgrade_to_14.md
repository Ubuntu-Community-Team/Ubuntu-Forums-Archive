---
title: "Yet another pulseaudio problem after upgrade to 14.04"
date: 2014-11-20
forum: Multimedia Software
---

### Post by wkuhns on 2014-11-20
I have a server that was running 12.04. I have a web based application that plays music using the server's sound card HDMI output. I added www-data to the audio group and added this line to default.pa and it worked perfectly: 

[FONT=courier new]load-module module-alsa-sink device=hw:0,3[/FONT]

I recently upgraded to 14.04 and have entered a pulseaudio nightmare. I get sound only rarely, generally after deleting /var/www/.config/pulse/* and restarting the web server. That doesn't always work, either. The log file sometimes complains about the alsa-sink module:

[FONT=courier new]module.c: Failed to load module "module-alsa-sink" (argument: "device=hw:0,3"): initialization failed.[/FONT]

Other time, there's no alsa-sink error and it works, or sometimes there's no alsa-sink error and it doesn't work.

I sometimes have a user logged into a graphical session on the server. That user sometimes gets sound and sometimes doesn't, with no discernable pattern.

I've purged and reinstalled pulseaudio, and the only change to default.pa is the line mentioned above.

What next?

---

