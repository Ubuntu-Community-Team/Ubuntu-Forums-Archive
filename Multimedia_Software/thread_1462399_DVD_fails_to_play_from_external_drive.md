---
title: "DVD fails to play from external drive"
date: 2010-04-25
forum: Multimedia Software
---

### Post by Maximus559 on 2010-04-25
I have an external LG DVD drive that I'm trying to use to play DVD video. Ubuntu recognizes the drive perfectly, and even will play CD audio from it. However, it will not play DVDs. When I insert a DVD and attempt to play it with Movie Player, it comes up with this: 

"An error occured / could not read from resource." 

I've tried it with VLC media player as well - in that one, it just doesn't work. It just briefly flashes a new window like it's going to start playback, then nothing. If I check the message log, it shows four instances of

[COLOR=#00008b]*main*[/COLOR][COLOR=#ff0000]* error: *[/COLOR][COLOR=#000000]ES_OUT_RESET_PCR called[/COLOR]

I know that this external drive works for playing DVDs, as it does so perfectly on my Vista machine. Also, I am able to navigate to the drive and view the files on the DVD under Ubuntu... they just won't play. Any ideas as to what's going on here? Note: I've also got the Ubuntu restricted extras pack installed, so that's not the problem...

---

### Post by mc4man on 2010-04-25
Find out the device or dev link to the drive and point vlc to it.

With the drive connected this should show (anything I've highlighted in blue will do - in this case a dvd was in the drive
```
sudo lshw -C disk 
```

Ex. (clipped
> *-cdrom
       description: DVD reader
       product: DVD/HD  X807616
       vendor: TOSHIBA
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom3
       logical name: [COLOR="Blue"]/dev/dvd3[/COLOR]
       logical name: /dev/scd2
       logical name: [COLOR="Blue"]/dev/sr2[/COLOR]
       logical name: /media/DVD_VIDEO
       version: MC08
       capabilities: removable audio dvd
       configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready

Then vlc -> media -> open disc and adjust Disc Device box or as an example from cli
>  vlc dvd:///dev/sr2
> vlc dvd:///dev/dvd3

or insert a dvd and hold down the shift button - pick vlc from the pop up

( totem (gstreamer) is and remains a crappy dvd video player

Edit : it some of this doesn't seem applicatable then post what ubuntu release and vlc version you have..

---

### Post by Maximus559 on 2010-04-25
Never mind... turned out I needed the libdvdcss2 package. Beats me why that can't be included in the restricted extras pack...

---

