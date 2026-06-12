---
title: "No Audio settings!"
date: 2011-07-19
forum: Multimedia Software
---

### Post by cubanjinx on 2011-07-19
Long story short. I was trying to fix my audio, I had it coming out of my headphones and speakers at the same time. I was told to run [this script]("http://www.stchman.com/alsa_update.html") to try to fix the problem but it only made it worse. I've attached screen shots showing that I now have no hardware showing. 

Any info on resolving this would be greatly appreciated!

Thanks in advance.

---

### Post by An Sanct on 2011-07-19
EDIT: previous attempt to help was ... well, wrong ;)

Try typing this command
```
alsa
```in the terminal, you should get output like this

```

an@an-VirtualBox:~$ alsa
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}

```Then try to reload or resume it ... 

Alsa keeps changing :}

---

### Post by cubanjinx on 2011-07-19
No, there isn't anything there. But to be fair this is what it also looked like before this problem came about.


And yes, I know it's on mute right now. :-P

---

### Post by An Sanct on 2011-07-19
note: I edited out the misleading attempt to help from post #2...

> **An Sanct said:**
> EDIT: previous attempt to help was ... well, wrong ;)

Try typing this command
```
alsa
```in the terminal, you should get output like this

```

an@an-VirtualBox:~$ alsa
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}

```Then try to reload or resume it ... 

Alsa keeps changing :}

---

### Post by cubanjinx on 2011-07-19
Yes, that's what I got.

```
cubanjinx@cubanjinx-Aspire-5253:~$ alsa
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
cubanjinx@cubanjinx-Aspire-5253:~$ reload
reload: missing job name
Try `reload --help' for more information.
cubanjinx@cubanjinx-Aspire-5253:~$ resume
resume: command not found
cubanjinx@cubanjinx-Aspire-5253:~$ 

```

This is what "reload --help" gives me.
```
 cubanjinx@cubanjinx-Aspire-5253:~$ reload --help
Usage: reload [OPTION]... JOB [KEY=VALUE]...
Send HUP signal to job.

Options:
      --session               use D-Bus session bus to connect to init daemon
                                (for testing)
      --system                use D-Bus system bus to connect to init daemon
      --dest=NAME             destination well-known name on D-Bus bus
  -q, --quiet                 reduce output to errors only
  -v, --verbose               increase output to include informational messages
      --help                  display this help and exit
      --version               output version information and exit

JOB is the name of the job that is to be sent the signal, this may be followed
by zero or more environment variables to distinguish between job instances.


Report bugs to <upstart-devel@lists.ubuntu.com>
cubanjinx@cubanjinx-Aspire-5253:~$ 

```

---

### Post by marin123 on 2011-07-19
you are supposed to type:
```
alsa reload
```

---

### Post by cubanjinx on 2011-07-19
```
cubanjinx@cubanjinx-Aspire-5253:~$ alsa
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
cubanjinx@cubanjinx-Aspire-5253:~$ alsa reload
mkdir: cannot create directory `/var/run/alsa': Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 219: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-hda-codec-conexant snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
mkdir: cannot create directory `/var/run/alsa': Permission denied
Loading ALSA sound driver modules: (none to reload).
cubanjinx@cubanjinx-Aspire-5253:~$ 

```

hmmm...

---

### Post by marin123 on 2011-07-19
it seems you need sudo permissions for that:

```
sudo alsa reload
```

and then type your password.

---

### Post by cubanjinx on 2011-07-19
```
cubanjinx@cubanjinx-Aspire-5253:~$ sudo alsa
[sudo] password for cubanjinx: 
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
cubanjinx@cubanjinx-Aspire-5253:~$ sudo alsa reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/cubanjinx/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-codec-conexant snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-conexant snd-hda-codec-hdmi snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-conexant snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
cubanjinx@cubanjinx-Aspire-5253:~$ 
```

---

### Post by marin123 on 2011-07-19
there you have it, you reloaded alsa. is there any change in sound settings?

---

### Post by cubanjinx on 2011-07-19
Sorry, I should have added that part in. No, no changes at all. Still only have dummy output with no sound at all.

---

### Post by Kalavere on 2011-07-19
I have roughly the same problem as you cubanjinx, I was trying to get HDMI sound to work on my GT 520M and in the process I have managed to get 'Dummy Output' and even seemed to wipe off ALSA, which I can't seem to get to reload back on. :(

---

### Post by cubanjinx on 2011-07-19
I'm at a complete standstill with this. If there is a cmd that will reset Ubuntu without me having to rerun my .iso burn I will run it.

Anyone know of such a thing?

---

### Post by Kalavere on 2011-07-19
> **cubanjinx said:**
> I'm at a complete standstill with this. If there is a cmd that will reset Ubuntu without me having to rerun my .iso burn I will run it.

Anyone know of such a thing?

Tell me about it, I've spent the most of the day on and off setting up Ubuntu on my new laptop, now I am looking at doing the same thing. I have tried installing;

[LIST]
[*] [alsa-driver-1.0.24]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.24.tar.bz2")
[*] [alsa-lib-1.0.24.1]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.24.1.tar.bz2")
[*] [alsa-utils-1.0.24.2]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.24.2.tar.bz2")
[*] [alsa-tools-1.0.24.1]("ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.24.1.tar.bz2")
[*] [alsa-firmware-1.0.24.1]("ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.24.1.tar.bz2")
[*] [alsa-plugins-1.0.24]("ftp://ftp.alsa-project.org/pub/plugins/alsa-plugins-1.0.24.tar.bz2")
[*] [alsa-oss-1.0.17]("ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.17.tar.bz2")
[*] [pyalsa-1.0.24]("ftp://ftp.alsa-project.org/pub/pyalsa/pyalsa-1.0.24.tar.bz2")
[/LIST]
Still nothing!

---

