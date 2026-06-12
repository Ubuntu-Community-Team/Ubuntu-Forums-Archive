---
title: "Sound not working after suspend."
date: 2008-05-05
forum: Multimedia Software
---

### Post by artir on 2008-05-05
I have a custom made PC
-Q6600 quad core
-8600 GT
ASUS P5K3SE
-Integrated Intel Realtek soundcard(works 100% perfect with ubuntu)

Today i suspended my pc(a desktop pc) and all was OK, except the sound, which not work after the suspend. **It works when i reboot.**

Version Ubuntu 8.04 LTS. 32 bits. clean install.

Cannot hear audio after suspend.

Edit: data added.

---

### Post by Zorael on 2008-05-05
Does it work if you manually stop and restart the module (driver) for the soundcard?
```
$ lshw -C multimedia
```
Should say "module=*<something>*" down at the bottom. Make note of what something is and apply it to the below commands.
```
$ sudo rmmod something
$ sudo modprobe something
$ sudo /etc/init.d/alsa-utils restart
```


For instance, mine says:
```
zorael@sunspire:~$ lshw -C multimedia
WARNING: you should run this program as super-user.
  *-multimedia
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```
Which'd make it:
```
$ sudo rmmod snd_hda_intel
$ sudo modprobe snd_hda_intel
$ sudo /etc/init.d/alsa-utils restart
```

---

### Post by artir on 2008-05-05
lshw -C multimedia:> ARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

Im going to try to unload and load it

---

### Post by artir on 2008-05-05
(After a reboot and with audio working, any sound-application with sound-using ability closed, i get this) > sudo rmmod snd_hda_intel
ERROR: Module snd_hda_intel is in use



---

### Post by artir on 2008-05-05
After a suspend, sudo rmmod snd_hda_intel says ERROR: Module snd_hda_intel is in use. But still no sound. WTF.
I filled a bug in launchpad here: [https://bugs.launchpad.net/ubuntu/+bug/227007](https://bugs.launchpad.net/ubuntu/+bug/227007)

---

### Post by Zorael on 2008-05-05
Perhaps stopping sound first would help, with **sudo /etc/init.d/alsa-utils stop**.

You could also try forcing an unload with **rmmod -f snd_hda_intel**, but likely your system will lock up.

edit: You beat me to it.
[quote=me]Unless someone else viewing this thread has better ideas, you may want to check [http://launchpad.net/ubuntu](http://launchpad.net/ubuntu) for similar bugs, and/or post your own. Searching it real quick, I see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/78257](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/78257) which seems at least somewhat similar to what you're describing.[/quote]

---

### Post by artir on 2008-05-05
If i do the /etc/init.d/alsa-utils stop before rmmod, I still get the error.
Thanks anyway. I will try to get help from launchpad.

---

### Post by animeshaga on 2008-11-10
sudo /etc/init.d/alsa-utils stop
sudo /etc/init.d/alsa-utils start
and it worked
some permanent solution would be better

---

