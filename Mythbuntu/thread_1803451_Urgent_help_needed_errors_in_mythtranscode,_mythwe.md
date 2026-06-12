---
title: "Urgent help needed: errors in mythtranscode, mythwelcome and alsa"
date: 2011-07-13
forum: Mythbuntu
---

### Post by matthias.rieber on 2011-07-13
Hi everybody,
 
I'm running myth 0.24.1 (latest fixes) on a Mythbuntu 11.04.
It was a new Install, but with DB restore from Mythbuntu 10.10 Version (to keep the recordings (copied back from external disk) and all the channels).
Finally it took 4 months to get the 10.10 running - and another 2 weeks to get most of the 11.04 running (including remote, reciever....very tricky, because remote worked BEFORE installing s2liplianin - but not afterwards....etc...needed to change the .config of v4l.....).
First of all: all the time spent (up to now) on this system was worth it ! Really great software !
 
No my Problems (in order of their impact):
 
1. Mythtranscode: 
This one is solved - wrong rights in /var/lib/mythtv/recordings.... problem description still here - maybe it helps s.o.
 
*worked in 10.10 - now I always get "error 255" - transcoding fails nearly every time.*
*I checked all the settings, removed RTjpeg... use losless transcoding, implemented a user Job with following:*
```

*mythtranscode --honorcutlist --showprogress -c $CHANID -s $STARTTIME -o $VIDEODIR/$FILENAME.tmp*

```*the transcode startet and failed the same way as the internal transcoding job.*
*I tried the "remove commercials" like described here: [http://www.mythtv.org/wiki/Removing_Commercials](http://www.mythtv.org/wiki/Removing_Commercials)*
*too....*
*Checked recording and transcoding profiles.... saw an error like "error writing file: permisson denied" (log files will be delivered) and changed (for testing) the rights on the recording folder to "777". I get the "preview error" like described in this thread too: "**Transcode Jobs Failing"***
*I've no further idea where to look.....:(:(*
 
2. Mythwelcome: works in the same way than in 10.10....
I did everything like described here: [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)
starting, stopping and "setwakealarm" works - nearly....
But: the shutdown command is "sudo shutdown -P now" - If I test this in console (the visudo entry is there and works, so I need no pwd for user mythtv) - the system shuts down (as expected) and powers off (as expected) including the USB-ports. That means: the USB-Reciever (TT-S2-3600) will power off, too.
If mythwelcome shuts down the system, the console says "going down for power off now" - but USB stays on - that means, the reciever is running all the time and gets really, really hot (within the cupboard !) - and yes: Mythtv will release the reciever if not used - but most times at shutdown the reciever is on......
Tests i did:
Entry in Mythbackend: instead of "mythshutdown --shutdown" I tried with "shutdown -P" - and shutdown works including power off of USB - but no wakeup-time set :-(
Entry in Mythwelcome (command to shutdown): "echo 'hallo' > /home/mythtv/tmp" - nothing happens
Entry in Mythwelcome (command to shutdown): "/home/mythtv/shutdown.sh" with following (changing per test) entries:
```

# 1
echo 'hallo' > /home/mythtv/tmp
#2
sudo shutdown -P now
#3
sudo reboot

```With active commands one and two: no tmp file created, system shuts down (with power on USB)
With active commands one and three: no tmp file created, system reboots
Only command 1 active: nothing happens - timer goes back to 180 sec (like the configured idle time before shutdown) and counts back again to 0 and so on.....
 
Any suggestions welcome how to shutdown completly ! Otherwise I have to keep the cupboard door open - and there is no waf (woman acceptance factor) for that....
 
3. alsa: I found a workaround here... 
Using Pulseaudio I was able to put audio output to HDMI and S/Pdif simultanously. With alsa: no chance !
Digital passthrough is not working at all (tried with alsa and pulseaudio). I use vlc to play Videos with direct digital audio output - I hope VDPAU (or sth. like this) will be working sometime - at the moment HD-Videos are shuttering :-(
Original Problem see here:
*very strange, too. With some work, configuration, testing and so on I was able to use hdmi and/or s/pdif.... but never both....*
*I tried this: [FONT=Helv][SIZE=2][FONT=Helv][SIZE=2][http://alsa.opensrc.org/TwoCardsAsOne](http://alsa.opensrc.org/TwoCardsAsOne) and that: [http://www.gossamer-threads.com/lists/mythtv/dev/416607](http://www.gossamer-threads.com/lists/mythtv/dev/416607) and [http://www.mythtv.org/wiki/Digital_Audio_Tutorial](http://www.mythtv.org/wiki/Digital_Audio_Tutorial) and some more..... and nothing worked.....[/SIZE][/FONT][/SIZE][/FONT]*
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]*Using ALSA:hw or ALSA:plughw or ALSA:default (works only wirthout asound-file) works (for hdmi or s/pdif). But no digital passthrough - and never both ! (no waf here, too....) for music I don't want tv running, HD-Films like 2012, Avatar... should be with DTS (7.1 reciever over s/pdif) - and TV-shows, most Videos etc we want just watch it with sound on TV (not with suround) over hdmi....*[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]*so, digital passthrough will be OK for most of the purposes (exept of music) - but it doesn't work.....*[/SIZE][/FONT][/SIZE][/FONT]
 
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]And last and least: since the change to 11.04 I have poor/instable Wlan performance (changing between 260 mbit/s and 11mbit/s) and in special very, very poor smb performance (between 1 Mb/s and 2,5 Mb/s - even if there ist 260mbit on Wlan).[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]My NAS (where films and music resides) has no nfs - so there is no way round smb)[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]I tried: cifs mount (700K-1,5MB - depends on settings like directio, tcp_buffer, maxbuffersize .......), network neighborhood (thunar) (1Mb-2Mb) and fusesmb (1Mb-2,5Mb) - with cable direct on network switch (100Mbit) I'll get around 8 MB/s..... [/SIZE][/FONT][/SIZE][/FONT]
[FONT=Helv][SIZE=2]Checked WLan performance with iperfmon: round 35 MB/s (!!!!) I don't understand this.....[/SIZE][/FONT]
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]Any suggestions here are welcome, too[/SIZE][/FONT][/SIZE][/FONT]
 
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]Hopefully someone has enough patience to read all this stuff - because I'm really in desperation............ After months of work - these things should start working now - so I (and my wife) can just sit down, watch videos or recordings, cut commercials, move good films to nas.... just enjoy the myth-box.....[/SIZE][/FONT][/SIZE][/FONT]
 
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]If any logfiles, outputs or sth else needed: pls post it and I'll get them....[/SIZE][/FONT][/SIZE][/FONT]
 
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]thanx all [/SIZE][/FONT]
[/SIZE][/FONT]

---

