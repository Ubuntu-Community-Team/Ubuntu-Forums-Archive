---
title: "ALSA: how to save default sound volume across reboots"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by garymansell on 2007-10-22
Hi,

I have a HP ZD8000 laptop with an Intel ICH6 sound card.

I find the login sound annoyingly loud if I have shut the laptop down, after perhaps watching a movie or listening to music with the volume turned up - ie I forget to turn the volume down before shutting down.

Is there some way that I can set/store a reasonable level volume that gets set upon boot time. This way if I shut the laptop down with it being set on full volume, I don't get blasted by the login sound.

I have tried setting the volume and the doing:

sudo alsactl store 0 

but this does not seem to work - the laptop persists in remembering the settings of the volume mixer at shutdown time.

Any help gladly received

Gary

---

### Post by katsuma on 2008-06-08
LOL man i am haveing EXACTLY the opposite what you have, when i reboot it always puts the volume settings to default i dont know why :(

---

### Post by exodus_ on 2008-06-08
> **garymansell said:**
> Hi,

I have a HP ZD8000 laptop with an Intel ICH6 sound card.

I find the login sound annoyingly loud if I have shut the laptop down, after perhaps watching a movie or listening to music with the volume turned up - ie I forget to turn the volume down before shutting down.

Is there some way that I can set/store a reasonable level volume that gets set upon boot time. This way if I shut the laptop down with it being set on full volume, I don't get blasted by the login sound.

I have tried setting the volume and the doing:

sudo alsactl store 0 

but this does not seem to work - the laptop persists in remembering the settings of the volume mixer at shutdown time.

Any help gladly received

Gary

Hey there,

The current mixer settings are actually stored by your system on shutdown so this is why it defaults back to what it was when you shut down.

From reading the README file in /etc/rcS.d and /etc/rc6.d it appears if you REMOVE /etc/rc6.d/K50alsa-utils then it should no longer store your mixer settings.  Here is the header to /etc/rcS.d/k50alsa-utils:

```
#
# alsa-utils initscript
#
### BEGIN INIT INFO
# Provides:          alsa-utils
# Required-Start:    $local_fs
# Required-Stop:     $local_fs
# Should-Start:
# Should-Stop:
# Default-Start:     S
# Default-Stop:      0 6
# Short-Description: Restore and store ALSA driver settings
# Description:       This script stores and restores mixer levels on
#                    shutdown and bootup.On sysv-rc systems: to
#                    disable storing of mixer levels on shutdown,
#                    remove /etc/rc[06].d/K50alsa-utils.  To disable
#                    restoring of mixer levels on bootup, rename the
#                    "S50alsa-utils" symbolic link in /etc/rcS.d/ to
#                    "K50alsa-utils".

```

I hope this is able to help!

ETA:  Once this is done when you use alsactl store it should store your current settings and then restore them on bootup.  I could be wrong though again I hipe this is able to help you

---

### Post by Neovos on 2008-06-25
The removal didn't work for me. I ended up just changing the percentages to my liking in /etc/rcS.d/k50alsa-utils itself. After a restart it worked for me. My problem was that I wanted some volumes to be muted by default and others to be turned up. I'd have to change it every bootup manually. Now it does it itself.

---

