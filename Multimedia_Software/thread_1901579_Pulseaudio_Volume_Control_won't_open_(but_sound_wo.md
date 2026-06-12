---
title: "Pulseaudio Volume Control won't open (but sound works fine)"
date: 2011-12-28
forum: Multimedia Software
---

### Post by Amurko on 2011-12-28
So sound works fine on my system but I can't adjust any of the settings.

So I try to open the Pulseaudio Volume Control app and an error message pops up:

"Fatal Error: Unable to Connect to Pulseaudio: OK"

I recently reinstalled.. this problem was present before AND after reinstalling.  Reinstalling did not help at all.

Running Ubuntu 11.10

Where to I begin the troubleshooting?

---

### Post by lidex on 2011-12-31
Try purging pulse config files. ```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*
No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by icemn on 2012-06-14
If you didn't get this working, have you tried ```
**pulseaudio -D**
``` if that works, this should help [URL="http://shuffleos.com/3496/how-to-enable-all-applications-in-startup-applications-ubuntu-11-10/"]http://shuffleos.com/3496/how-to-enable-all-applications-in-startup-applications-ubuntu-11-10/
[/URL]

---

