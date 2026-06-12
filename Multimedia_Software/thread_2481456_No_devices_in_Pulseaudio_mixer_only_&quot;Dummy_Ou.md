---
title: "No devices in Pulseaudio mixer only &quot;Dummy Output&quot;"
date: 2022-11-30
forum: Multimedia Software
---

### Post by Jonners59 on 2022-11-30
Out of the blue, I lost all audio.  This seemed to follow a kernel upgrade, but that could be misleading as I have a couple of updates a day.  Nonetheless, everything was working and then suddenly stopped.  When I open the Pulseaudio Mixer in the "Configuration" tab there are no devices.  I have searched Google and everything I have seen I have tried, and TBH that's made it even worse, as now the mixer is empty!  No tabs.  Now, small caveate to all this.  I seem to have got audio working on some apps, BUT still Pulseaudio is not working.  All entries are blank and there is only a "dummy".

Linux BaroniPC 5.19.0-23-generic #24-Ubuntu SMP PREEMPT_DYNAMIC Fri Oct 14 15:39:57 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```
alsamixer -c 0
```  All devices are listed and levels are up  It gives me this information if any value.
Advanced Linux Sound Architecture Driver Version k5.19.0-23-generic.

Interestingly, most threads state to try removing the config and restarting, but I get this error:
```
rm -r ~/.pulse ~/.pulse-cookie ~/.config/pulse
```
[HTML]rm: cannot remove '/home/baroni/.pulse': No such file or directory
rm: cannot remove '/home/baroni/.pulse-cookie': No such file or directory[/HTML]

```
pulseaudio -k; pulseaudio --start
```
[HTML]E: [pulseaudio] main.c: Failed to kill daemon: No such process[/HTML]

```
aplay -l
```
[HTML]**** List of PLAYBACK Hardware Devices ****
card 0: DX [Xonar DX], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: DX [Xonar DX], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia [HDA NVidia], device 7: HDMI 1 [LG SIGNAGE   ]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia [HDA NVidia], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia [HDA NVidia], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/HTML]

```
ls -l /dev/snd
```
[HTML]total 0
drwxr-xr-x  2 root root       60 Nov 30 08:28 by-id
drwxr-xr-x  2 root root      120 Nov 30 08:28 by-path
crw-rw----+ 1 root audio 116, 22 Nov 30 08:28 controlC0
crw-rw----+ 1 root audio 116, 17 Nov 30 08:28 controlC1
crw-rw----+ 1 root audio 116, 15 Nov 30 08:28 controlC2
crw-rw----+ 1 root audio 116,  9 Nov 30 08:28 controlC3
crw-rw----+ 1 root audio 116, 14 Nov 30 08:28 hwC2D0
crw-rw----+ 1 root audio 116,  8 Nov 30 08:28 hwC3D0
crw-rw----+ 1 root audio 116, 19 Nov 30 08:28 pcmC0D0c
crw-rw----+ 1 root audio 116, 18 Nov 30 08:28 pcmC0D0p
crw-rw----+ 1 root audio 116, 21 Nov 30 08:28 pcmC0D1c
crw-rw----+ 1 root audio 116, 20 Nov 30 08:28 pcmC0D1p
crw-rw----+ 1 root audio 116, 16 Nov 30 08:28 pcmC1D0c
crw-rw----+ 1 root audio 116, 11 Nov 30 08:28 pcmC2D0c
crw-rw----+ 1 root audio 116, 10 Nov 30 08:28 pcmC2D0p
crw-rw----+ 1 root audio 116, 12 Nov 30 08:28 pcmC2D1p
crw-rw----+ 1 root audio 116, 13 Nov 30 08:28 pcmC2D2c
crw-rw----+ 1 root audio 116,  6 Nov 30 08:28 pcmC3D10p
crw-rw----+ 1 root audio 116,  7 Nov 30 08:28 pcmC3D11p
crw-rw----+ 1 root audio 116,  2 Nov 30 08:28 pcmC3D3p
crw-rw----+ 1 root audio 116,  3 Nov 30 08:28 pcmC3D7p
crw-rw----+ 1 root audio 116,  4 Nov 30 08:28 pcmC3D8p
crw-rw----+ 1 root audio 116,  5 Nov 30 08:28 pcmC3D9p
crw-rw----+ 1 root audio 116,  1 Nov 30 08:28 seq
crw-rw----+ 1 root audio 116, 33 Nov 30 08:28 timer
[/HTML]

---

### Post by Jonners59 on 2022-12-02
FIXED:
                                   []("https://askubuntu.com/posts/1430326/timeline")  
          
                       [No sound output devices listed after upgrade from 21.10 to 22.04]("https://askubuntu.com/questions/1403665/no-sound-output-devices-listed-after-upgrade-from-21-10-to-22-04")

 

 ```
sudo touch /usr/share/pipewire/media-session.d/with-pulseaudio
systemctl --user restart pipewire-session-manager

``` (credits go to [https://askubuntu.com/users/1156299/adam](https://askubuntu.com/users/1156299/adam))

     
[https://askubuntu.com/questions/1406646/ubuntu-22-04-audio-output-not-working-dummy-audio](https://askubuntu.com/questions/1406646/ubuntu-22-04-audio-output-not-working-dummy-audio)

---

### Post by Claus7 on 2022-12-02
Hello,

glad you found it. I had faced exactly the same problem when upgrading back then from ubuntu 22.04 to 22.10. I do not remember coming across this solution though, so re-installation in the end took place. In the meantime I had created a thread and now I will add your directions in case someone checks it out, for additional information. 

Regards!

---

### Post by cigtoxdoc on 2022-12-06
Thank you for your solution.

It only solved part of the sound problem with my Dell Precision 7720 laptop.  The built-in speakers still will not work; however, my Logitech USB headphones will work.

To make sure it was not a hardware problem, I rebooted into Win 11 Pro (insider) and tried the same things.  With Win 11, the built-in speakers work.

So, there is still something missing.  The same thing happened on a PC with dual-boot to Win 10 Pro.  The USB headphones work, but not the normal audio out.

John

---

### Post by cigtoxdoc on 2022-12-09
The problem here as reported by others is that audio on the internal speakers sometimes works, but most of the time it does not.  For example, it came on suddenly last night, but then stopped.  I have another PC that has the same problem.  However, when USB headphones are plugged in, sound works all the time.  On both PCs, the sound works 100% of the time when booted into Windows. 10 or 11.  Various responses on this and other Ubuntu related forums discuss changes related to pipewire and alsa.  What is the real answer to the problem?  John

---

### Post by michaelangelus on 2023-01-22
I also ran into this problem and, after a long search, found that entering the following brings back the devices in the options immediately:

```
systemctl --user enable pulseaudio

systemctl --user start pulseaudio
```

Supposedly that simply starts the PulseAudio service.

HOWEVER, in my case it also resets again after rebooting the system (but retains it when merely suspending the system). Also, when I click the PulseEffects-icon, it will show up in the top bar for a split second but then immediately go away, like something is preventing it from launching or staying active.
So, for some reason, I need to do this manually every time, or find some way of preventing it from messing up or get it to launch with the OS. Though, it already shows in Startup Applications, so I guess something's broken when it comes to that service and launching it.

Other than that, it does work like it used to, except that it won't launch with the system.

---

### Post by cigtoxdoc on 2023-02-20
On a restart of a desktop PC that had been shut down for a week, I got the "Dummy Output" problem when it had not occurred previously.  I have shown below the terminal output when I tried to correct the problem.

john@john-ThinkCentre-M83:~$ sudo touch /usr/share/pipewire/media-session.d/with-pulseaudio
systemctl --user restart pipewire-session-manager
[sudo] password for john: 
Failed to restart pipewire-session-manager.service: Unit pipewire-session-manager.service not found.
john@john-ThinkCentre-M83:~$ systemctl --user enable pulseaudio
Created symlink /home/john/.config/systemd/user/default.target.wants/pulseaudio.service &#8594; /usr/lib/systemd/user/pulseaudio.service.
Created symlink /home/john/.config/systemd/user/sockets.target.wants/pulseaudio.socket &#8594; /usr/lib/systemd/user/pulseaudio.socket.
john@john-ThinkCentre-M83:~$ systemctl --user start pulseaudio
john@john-ThinkCentre-M83:~$ 

So, how does one create the symlinks so that they are executed each time this PC boots into Ubuntu 22.10?

Thank you,

John

---

