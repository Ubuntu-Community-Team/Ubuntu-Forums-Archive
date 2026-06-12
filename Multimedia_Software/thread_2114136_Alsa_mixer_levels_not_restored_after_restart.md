---
title: "Alsa mixer levels not restored after restart"
date: 2013-02-09
forum: Multimedia Software
---

### Post by satnelav on 2013-02-09
On Ubuntu Lucid (10.10), alsa mixer levels are not restored after reboot.
I think the "Master" level is restored, but I need to store different default level for "headphones". 

alsactl store/restore

works if I manually call them.

But if I add "alsactl restore" into /etc/rc.local, it makes no effect.

I suspect there is some level above alsa in Ubuntu - any ideas where to look for the configuration? I cannot find a way to control mixer levels through the "Sound" GUI dialog from the main menu.

Thanks.

---

### Post by tgalati4 on 2013-02-09
```
man alsactl
```

FILES
       /var/lib/alsa/asound.state  (or  whatever  file  you specify with the -f flag) is used to store current settings for your soundcards. The settings
       include all the usual soundcard mixer settings.  More importantly, alsactl is capable of controlling other card-specific features that mixer  apps
       usually don't know about.

       The  configuration  file  is  generated  automatically  by running alsactl store. Editing the configuration file by hand may be necessary for some
       soundcard features (e.g. enabling/disabling automatic mic gain, digital output, joystick/game ports, some future MIDI routing options, etc).

------

So, you can add a line to poke values into that file.  I would put it into your login script .bashrc.  You can probably save a copy of it locally and it will get read as well, but you will have to research that.

---

### Post by satnelav on 2013-02-10
Thanks tgalati, but I have already said that alsactl store and alsactl restore works correctly and at the time of calling them, they set the mixer to correct levels. However, after my 'alsactl restore' line in rc.local is called there is something else that sets different mixer levels in Ubuntu startup - and I cannot figure out what. 

Does anybody know what other parts/scripts of ubuntu (pulseaudio, gnome-control-center, etc?) can change the sound?

---

### Post by tgalati4 on 2013-02-10
Well a crude search:

tgalati4@Mint14-Extensa ~ $ locate asound.state
/var/lib/alsa/asound.state

***So there is only one copy of asound.state on my system.

tgalati4@Mint14-Extensa /usr/sbin $ grep asound *
Binary file alsactl matches

***Only alsactl touches asound in /usr/sbin.

tgalati4@Mint14-Extensa /usr/bin $ grep asound *
Binary file aconnect matches
Binary file alsaloop matches
Binary file alsamixer matches
Binary file alsaucm matches
Binary file amidi matches
Binary file amixer matches
Binary file aplay matches
Binary file aplaymidi matches
Binary file arecord matches
Binary file arecordmidi matches
Binary file aseqdump matches
Binary file aseqnet matches
Binary file audacity matches
Binary file brltty-ctb matches
Binary file brltty-trtxt matches
Binary file brltty-ttb matches
Binary file gnome-mplayer matches
Binary file iecset matches
inxi:FILE_ASOUND_DEVICE='/proc/asound/cards'
inxi:FILE_ASOUND_MODULES='/proc/asound/modules' # not used but maybe for -A?
inxi:FILE_ASOUND_VERSION='/proc/asound/version'
inxi:		cat $FILE_ASOUND_DEVICE &> $debug_data_dir/proc-asound-device.txt
inxi:		cat $FILE_ASOUND_VERSION &> $debug_data_dir/proc-asound-version.txt
inxi:## create array of sound cards installed on system, and if found, use asound data as well
inxi:				# only one card and it was null, from the first test of asound/cards
inxi:		# for every sound card symlink in /proc/asound - display information about it
inxi:		for usb_proc_file in /proc/asound/*
inxi:	# for every sound card symlink in /proc/asound - display information about it
Binary file mate-services-admin matches
Binary file mate-shares-admin matches
Binary file mate-time-admin matches
Binary file mplayer matches
Binary file speaker-test matches

***Many suspects in /usr/bin touch asound.

Possibly gnome-mplayer loads or modifies asound.state as it possibly loads with nautilus to play media by hovering over icons?

mate-volume-control-applet runs in my system tray.  If running gnome it's probably called gnome-volume-control-applet.  Try killing that application and see if your settings stick.  Or run that application and compare its settings to your desired settings.

---

### Post by satnelav on 2013-03-24
> **tgalati4 said:**
> 
mate-volume-control-applet runs in my system tray.  If running gnome it's probably called gnome-volume-control-applet.  Try killing that application and see if your settings stick.  Or run that application and compare its settings to your desired settings.

Every time I put on my headphones and forget to adjust the alsamixer before, it makes me almost deaf :).  I don't understand the gnome-volume-control-applet at all. It doesn't have the alsamixer-style bars (although if I remember correctly there used to be a usable GUI mixer earlier). The current one has a horizontar slider for the master volume and tabs "Sound Effects", "Devices", "Input", "Output", "Programs". I can select, for example, the "Analog headphones / No Amplifier" in the "Output" tab and slide the "Balance" slider,
 which again seems to affect only the master output regardless what I select in the drop-down list.

---

