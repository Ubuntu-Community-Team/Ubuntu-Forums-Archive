---
title: "Sound Working &quot;Partially&quot;"
date: 2010-05-07
forum: Multimedia Software
---

### Post by medusa~ on 2010-05-07
Yes it's weird. Last night I finished watching movie, tested gtk-recordmydesktop, transmaggedon(vid file transcoder) a few files and played around with audacious settings. Then after all these, I played tracks on audacious and there was no sound. It playing and when it starts, it give a kinda vocal jolt to the speaker, then nothing. I found out that interface sounds are working. Even aMsn sounds are working. I think it has to do with multimedia specifically!


system status output:

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu lucid (development branch)"

```
$ uname -a
Linux medusa 2.6.32-19-generic #28-Ubuntu SMP Wed Mar 31 17:46:20 UTC 2010 i686 GNU/Linux
```

```
$sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/caprica/.gvfs
      Output information may be incomplete.
Terminating processes: 2264lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/caprica/.gvfs
      Output information may be incomplete.
 2458lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/caprica/.gvfs
      Output information may be incomplete.
 2476lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/caprica/.gvfs
      Output information may be incomplete.
 2493lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/caprica/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 2510lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/caprica/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 2527(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/caprica/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 2527(pulseaudio). 
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-intel8x0 snd-ac97-codec snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-intel8x0 snd-ac97-codec snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-intel8x0 snd-ac97-codec snd-pcm snd-timer snd-page-alloc.

```
```
$cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

```
```
$ head -n 1 /proc/asound/card0/codec97#0/ac97#0-0
0-0/0: Analog Devices AD1981B
```

---

### Post by medusa~ on 2010-05-07
I just created a new accout and loggin, sound is playing all the way. means,  1. Card is properly installed(I knew that!) 2. Problem is specifically account dependent. that is my first user account.  now, what I was thinking is what are the .xxx user config directories that has to do with sound? I thought if I could identify them. I will just copy default config or the new account and overwrite those. Kinda, return it to default.  Please let me know, what you think! I dont wanna be a coward and run away from first account and start reconfig second one 'cos of sound.

---

### Post by medusa~ on 2010-05-07
Don't know if this might help anyone, just to make this solved kinda. 

```
apt-get --purge remove audacious
```
and
```
apt-get install remove audacious
```

same thing to alsa
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```
and
```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

Reboot and that solved it for me. I must confess, I didn't really figure out what really happened but I am happy I solved it.[FONT=monospace][U]
[/U][/FONT]

---

