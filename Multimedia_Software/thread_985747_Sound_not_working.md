---
title: "Sound not working"
date: 2008-11-17
forum: Multimedia Software
---

### Post by talasthenoob on 2008-11-17
Hello,
I have just installed Ubuntu 8.10 onto my brand new hard drive, and I am not getting any sound out of anything.  I have an onboard sound card, a PCI sound card (soundblaster, brand new), and a Logitech 950 USB headset.  None of my sound devices are working.  I went through all the steps on this post: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and nothing has come of it.  If someone could help that would be greatly appreciated.

Thanks,
TalasTheLinuxNoob

---

### Post by alwayshere on 2008-11-17
This might sort ya sound

sudo killall pulseaudio

then


sudo alsa force-reload

and then go to System>Preferences>Sound and change everything to ALSA

if ya get no sound try a restart and see how that goes

---

### Post by psyke83 on 2008-11-17
You're looking at the wrong guide. Intrepid uses PulseAudio by default - so it's highly likely that you're experiencing a configuration problem with PulseAudio and not ALSA. I hope you didn't take any drastic steps (such as removing packages or installing ALSA from source).

This is the guide you should follow: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

After following the guide, make an effort to ensure:
[LIST]
[*]your sound card's PCM volume is not muted or low (it seems to be a common problem for Intrepid users) - check via:```
$ alsamixer -Dhw
```
[*]that you have selected the right default playback in the PulseAudio Volume Control application (it's explained in the guide).
[/LIST]

Please also read the FAQ and refer to the troubleshooting section if you still have problems.

---

### Post by talasthenoob on 2008-11-17
I do the sudo commands from alwayshere's post and here is what I get:

> zach@zach-linuxdesktop:~$ sudo killall pulseaudio
pulseaudio: no process killed
zach@zach-linuxdesktop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zach/.gvfs
      Output information may be incomplete.
Terminating processes: 11190lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zach/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zach/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zach/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-usb-audio snd-usb-lib snd-hwdep snd-via82xx-modem snd-via82xx snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
Loading ALSA sound driver modules: snd-usb-audio snd-usb-lib snd-hwdep snd-via82xx-modem snd-via82xx snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.

---

### Post by psyke83 on 2008-11-17
> **alwayshere said:**
> This might sort ya sound

sudo killall pulseaudio

then


sudo alsa force-reload

and then go to System>Preferences>Sound and change everything to ALSA

if ya get no sound try a restart and see how that goes

I've seen this "technique" before, and it's silly. All it does is kill the PulseAudio server and reload the ALSA kernel modules (which are already loaded correctly). By killing PulseAudio you are forcing applications to use standard ALSA output - it works, but it fixes absolutely nothing in reality. You will also have to do this each time you log in (as PulseAudio launches upon startup via gnome-settings-daemon).

Take the time to configure & troubleshoot PulseAudio rather than using band-aid workarounds such as this.

---

### Post by talasthenoob on 2008-11-17
> **psyke83 said:**
> I've seen this "technique" before, and it's silly. All it does is kill the PulseAudio server and reload the ALSA kernel modules. By killing PulseAudio you are forcing applications to use standard ALSA output - it works, but it fixes absolutely nothing in reality. You will also have to do this each time you log in (as PulseAudio launches upon startup via gnome-settings-daemon).

Take the time to configure & troubleshoot PulseAudio rather than using band-aid workarounds such as this.

Going through the guide now.

---

### Post by talasthenoob on 2008-11-17
Ok, I get to step 5 (opening pavucontrol) and I get a connection refused error. I am going to restart and see if that helps

---

### Post by talasthenoob on 2008-11-17
Awesome! Thank you for the help, it is working properly now, or so I think.  I hear sound but have yet to test the mic.

Thanks again!

---

### Post by psyke83 on 2008-11-17
> **talasthenoob said:**
> Awesome! Thank you for the help, it is working properly now, or so I think.  I hear sound but have yet to test the mic.

Thanks again!

That's good. FYI, Appendix A of the guide can verify if it's working correctly (it also explains the "connection refused" error). Some applications need custom configuration to work properly with PulseAudio, so refer Appendix B of the guide if you have issues.

---

