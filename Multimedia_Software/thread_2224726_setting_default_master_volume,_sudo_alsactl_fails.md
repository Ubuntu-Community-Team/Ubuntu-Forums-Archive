---
title: "setting default master volume, sudo alsactl fails"
date: 2014-05-17
forum: Multimedia Software
---

### Post by scholz-thispla on 2014-05-17
I changed the master volume in alsamixer and want to set this new value as default.  But ```
sudo alsactl store
``` does not work: On next system start, the volume has the old default.  

What would be the right command? As workaround: where's the configuration file such that I can change the value by hand?

Ubuntu 14.04 LTS, i686

---

### Post by ronb19495 on 2014-05-18
I was having the same problem as you but with the latest updates on 64 bit system alsamixer is working like it should

---

### Post by scholz-thispla on 2014-05-18
I usually use the provided versions, i.e., I only install the official Ubuntu updates. Where/how did you get your updates?

---

### Post by ronb19495 on 2014-05-18
just type in a terminal sudo apt-get update when that finishes sudo apt-get upgrade if you have updates it will tell you then ask you to type  n/y if you want o update type y hit enter. is yousystem 14.04 64 bit
and reboot after updating

---

### Post by scholz-thispla on 2014-05-19
well, it's a 64 bit processor and I have all updates (update + upgrade = 0 changes).  And "sudo alsactl store" does not work

---

### Post by steeldriver on 2014-05-19
iirc **store** is only half the procedure (save current config to file) - you need to **restore** that saved config **from** the file on restart (usually done from /etc/rc.local)

---

### Post by Yellow Pasque on 2014-05-19
restore should be automatically called during the alsa upstart process. 

Maybe you should try editing /var/lib/alsa/asound.state manually if 'store' isn't working.

---

### Post by scholz-thispla on 2014-05-23
Executing [FONT=courier new]sudo alsactrl restore[/FONT] sets the new value.  So that seems not to be called during startup.  Should I just add [FONT=courier new]alsactrl restore[/FONT] to [FONT=courier new]/etc/rc.local[/FONT] ?

---

### Post by Yellow Pasque on 2014-05-23
No harm in trying that, but I'm not sure if rc.local works under upstart like it did in older sysvinit days.
Also, I've seen some references to pulseaudio overriding alsactl...

---

### Post by scholz-thispla on 2014-06-15
I have still no luck in setting the default volume.  But I notified the following: Just after logging in (and before autostart of applications has finished), the stored volume is correctly set (I tried it with two different values, so it's actually the latest stored value). Then, suddenly, the value jumps back to the incorrect value. So, the value is set twice: Once, at the beginning, to the correct value and then later to another, wrong default value.

---

### Post by Yellow Pasque on 2014-06-15
Seems like pulseaudio is overriding ALSA volumes:
[https://wiki.archlinux.org/index.php/PulseAudio#Pulse_overwrites_ALSA_settings](https://wiki.archlinux.org/index.php/PulseAudio#Pulse_overwrites_ALSA_settings)

---

