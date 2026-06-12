---
title: "Audio configuration not working (possible bug with pulseaudio) Kubuntu 17.10"
date: 2018-03-02
forum: Multimedia Software
---

### Post by joshua-m-salazar on 2018-03-02
I usually connect my laptop to an HDMI additional screen, so I am used to changing the audio output. But now, I cannot select any of the available outputs, even I cannot change the volume. The taskbar icon now its shown as this, with no options.

[IMG]https://i.stack.imgur.com/yNSxk.png[/IMG]


*

**UPDATE** Considering the answers in [this askubuntu question]("https://askubuntu.com/questions/976375/kubuntu-17-10-no-audio-devices-found-no-settings-no-sound/1011279#101279")
------------------------------------------------------------------

*

I managed to get the audio again, but the volume controls do not work any more neither the icon in tray appears. 

I reinstalled completely the `pulseaudio`, and in the same way `alsa`, as in @ChristophS' answer:

> ```
apt-get remove --purge pulseaudio
rm -rf /etc/pulse
apt-get install pulseaudio
reboot
```

Also edited the lines as in @Carla sousa's answer:

> So I opened `/etc/pulse/default.pa` and edited it using `#` to disable
3 lines:
 
```
#.ifexists module-switch-on-connect.so
#load-module module-switch-on-connect
#.endif
```

Then, I went to the system configuration as follows:

[IMG]https://i.stack.imgur.com/rBtZu.png[/IMG]

After that, to the Hardware > Multimedia section:

[IMG]https://i.stack.imgur.com/2F79Z.png[/IMG]
 
And finally, I chose the build-in driver:

[IMG]https://i.stack.imgur.com/CLFYg.png[/IMG]

As I said before, I got the sound again, but I cannot control it. Some idea?

It looks like it is a [Kubuntu 17.10 bug]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1720519"), but I freshly installed it, not upgraded.

---

