---
title: "PulseAudio EQ enabled on startup"
date: 2016-01-12
forum: Multimedia Software
---

### Post by stefanospecia on 2016-01-12
Hello everybody! How can I set PulseAudio's EQ to be enabled on startup? It's kinda annoying me to set it manually after every startup. 
Thank you for your help! :KS

---

### Post by QDR06VV9 on 2016-01-12
Hi stefanospecia
I was seeing the same so i reported to Launchpad.
I received an email (reply) from Launchpad that describes a similar bug and advice to fix it:
```
gksudo gedit /etc/pulse/daemon.conf
```


and change:
> flat-volumes = yes


to


flat-volumes = no
But it worked for me, some still report that it did not fix it.

---

### Post by stefanospecia on 2016-01-12
Thank you for your reply runrickus. Actually I just entered the config file, and my flat-volumes setting is on "no" by default. I did not make any changes on the GUI since startup.

---

### Post by Yellow Pasque on 2016-01-14
What do you normally do to start the EQ? It looks like this app has a "Keep Settings" checkbox to accomplish what you want. [http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html](http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html)

EDIT: I also think this will work if you prefer to edit the file yourself: [https://wiki.archlinux.org/index.php/PulseAudio#Load_equalizer_sink_and_dbus-protocol_module](https://wiki.archlinux.org/index.php/PulseAudio#Load_equalizer_sink_and_dbus-protocol_module)

---

### Post by stefanospecia on 2016-01-16
Incredible, didn't notice it so far, thank you! :lolflag:

---

