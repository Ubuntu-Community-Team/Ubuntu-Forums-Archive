---
title: "Alsa capture settings won't save"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by miatawnt2b on 2008-02-04
I am trying to save my mixer settings so they are the same after a reboot.  I have tried to run alsamixer in a terminal, set the settings, then run 'sudo alsactl store' but after a reboot, the capture is again unmuted.  If I open the gnome mixer applet, mute the capture, close the applet then re-open the applet, the capture is again unmuted.

I believe that the gnome applet is stomping on my settings, but i can't figure out why.  Can someone help?

I have tried to delete the /var/lib/alsa/asound.state file and re-create it with 'sudo alsactl store' but that didn't help either.

thanks,
-J

---

### Post by linuxwizard on 2008-02-04
First make sure you have your settings just the way you want them in alsamixer.
Than try this > sudo alsactl store 0

---

