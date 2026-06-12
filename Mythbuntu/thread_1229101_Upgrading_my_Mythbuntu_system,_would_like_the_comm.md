---
title: "Upgrading my Mythbuntu system, would like the community's thoughts"
date: 2009-08-01
forum: Mythbuntu
---

### Post by NTolerance on 2009-08-01
Right now I'm running a Mythbuntu Hardy system with these basic specs:
```
Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
2GB RAM
500GB SATA drive used for / and /var/lib/mythtv
400GB IDE drive used for /home
750GB IDE drive used for backups
Hauppauge PVR-150
```


I have a few reasons for upgrading:

1.  I'm running out of disk space on /home
2.  I'd like to record programs in HD
3.  Hardy is getting long in the tooth, I'd like the newer packages in Jaunty


So as a result, I'm planning on addressing those issues in this fashion:

1.  I've got a spare 400GB SATA drive that I can add to the system for more storage space
2.  I'm looking at purchasing a Hauppauge HVR-1250 for HD recording
3.  I can do a clean install of Jaunty during the hardware upgrade process


Questions moving forward:

1.  I back up my mythconverg mySQL database on a regular basis.  It's my understanding that this stores program data and mythTV settings among other things.  I need to restore my program data to the new system, but I'd like to start fresh with all other mythTV settings.  Is there a way to backup/restore with this goal in mind? 
2.  Is XFS still the way to go for the /var/lib/mythtv/ directory?  Is ext2 or ext3 recommended for USB drives?
3.  Here's my planned partition scheme.  Let me know if this seems like a good plan or not. 
```
400GB SATA formatted as ext3, 
mounted as / and /home

400GB IDE formatted as ext3, 
mounted in /media and used for videos and other things that won't fit on the 400GB SATA drive that contains /home

500GB SATA formatted as XFS, 
mounted as /mythtv (symlink to /var/lib/mythtv)

750GB IDE formatted as ext3, 
mounted in /media and connected via USB for backups and quick removal
```

4.  Are the mythbuntu packages in the repository still dependent on XFCE?  I plan on installing mainline Jaunty with GNOME and adding Mythbuntu afterwards through Synaptic.  Is there a way to control the installation of Mythbuntu GDM themes, usplash, etc?  

5.  What's the fastest VNC server for remote administration?

6.  Does anyone know if Time-Warner cable in the southeast US provides clearQAM channels?  Should I go with that option or with rabbit ears for HD content? 

10.  What's a well-supported wireless keyboard with integrated pointer?  Bluetooth seems completely hosed in Jaunty so I suppose RF with a USB dongle is the way to go.   


I know this is a lot of info, so I'm grateful to the community for any input.  I'm sure I can think of more questions later.  :D

---

### Post by NTolerance on 2009-08-03
bump

---

### Post by newlinux on 2009-08-03
1. [http://www.mythtv.org/wiki/Database_Backup_and_Restore#Partial_restore_of_a_backup](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Partial_restore_of_a_backup)

2. I still prefer XFS for all my recording partitions (for speed). I prefer ext3 where data integrity and recovery are most important. If all your recordings are from a PVR-150, filesystem speed probably won't be an issue anyway. If you are going to start going HD, I'd use XFS. Remember to defrag it periodically.

3. Seems okay. is the XFS partition/drive for recordings? why not call it something other than mythtv and/or link it in /var/lib/mythtv as something other than mythtv (like recordings) - It could be a little confusing? I typically mount my recordings storage drive as /storage, and I don't symlink it to anything - I just add that directory to the storage groups. But honestly, i don't see a problem with what you are doing, just a personal preference difference for me.

4. i think when I installed mythbuntu in jaunty it did take over and install XFCE and my splash screens with mythbuntu themes. I just changed them back though, and changed my default session back to gnome. So yes, you can control the themes/splash/etc.

5. LAN or WAN? Over WAN, I don't recommend VNC at all. I use freeNX with NXclient. Very fast with great compression over the WAN even with my slow upstream connection at home. otherwise. It creates its own session though - not sure if it can connect to the existing desktop session. But it can connect and disconnect to the same session, however.

6. Check your local content provider AVSforum thread or try [http://www.silicondust.com/hdhomerun/channels_us](http://www.silicondust.com/hdhomerun/channels_us)

7-9. What happened to these questions?

10. Check my hardware link. 2 different models I use with integrated mice that worked pretty much out of the box.

---

### Post by NTolerance on 2009-08-03
Thanks for the info about the partial backup, I should have had a look at the MythTV wiki.  HD is one of the reasons for this upgrade, so I'll definitely go XFS.  I suppose defragging is done by a simple cron job? 

I wasn't aware of MythTV's storage groups.  That will definitely be useful with my mass of assorted hard drives.  Maybe I will mount all storage drives under /media as it seems that's the standard place Ubuntu likes to put them.  

Puzzling that the Mythbuntu packages in the standard repo depend on XFCE.  I can understand the Mythbuntu distro being packaged with the preferred DE, but it's just a bit odd.  

I'll probably start using Nomachine NX for remote access.  I generally want to control display 0, so I can use the "shadow" option when connecting.  Only downside of Nomachine is the excessive time it takes to connect and log in.

Questions 7-9 never existed, my head just jumped directly to 10 as a nice round number to end with.  :D

Thanks again for all your help.

---

### Post by newlinux on 2009-08-03
> **NTolerance said:**
>   I suppose defragging is done by a simple cron job? 
...
Questions 7-9 never existed, my head just jumped directly to 10 as a nice round number to end with.  :D

Yep, in fact mythbuntu-control-center can set up the cron job for you. It can be down while the filesystem is mounted, even when it is in use.

Yeah, I was just messing with you about 7-9. Good luck with the your myth build...

---

### Post by NTolerance on 2009-08-08
**Beware of the wall of text.  The main purpose for this is to remind myself of what I did to get things working and maybe to help others doing similar things.**

So I've completed my upgrade.  It was a long and twisted road with more problems than I anticipated.  

The install was a pain because Ubuntu insists on making all IDE drives sda1+ regardless of whether the actual OS is installed on them or not.  I tried to avoid this by only plugging in my SATA drive where the bootloader and / resides during the install.  It naturally became sda1, but when I subsequently plugged in my IDE bulk storage drive, it became sda1 and my SATA drive became something else.  Ugh.  I just have to deal with this; I don't think it can be fixed.  

Turns out the hardware revision of my HVR-1250 is [not yet supported](http://ubuntuforums.org/showthread.php?t=1234274) in the kernel.  In that link you can see how I resolved that issue.  

The "partial restore" method in the MythTV wiki does not work for Ubuntu Jaunty.  The mc.sql script contained in Ubuntu's /usr/share/mythtv/sql directory doesn't jive with the MythTV documentation and wipes out the mythtv MySQL password.  It gets reset to something unknown; definitely not the random password generated during install.  The only way I know to fix this is to run dpkg-reconfigure on the myth backend package.  Did that to re-create the default mythtv database and reset the password to the known random-generated one.  I did some searching and found [this document](http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.7) that uses some SQL commands to extract the program data from the full SQL dump.  I used the second method involving backticks.  I was able to successfully restore this backup and confirmed that it only brought back program data, not MythTV settings.

I was able to install lirc and bring back my ~/.lircrc file easily.  MCE remote works as expected in all apps.

Next, I installed XBMC from their repository and restored my ~/.xbmc directory with success.  Everything works except ATSC recordings from MythTV.  ATSC playback works except fast forward and seek are completely broken.  This seems to be a problem with XBMC and I'll have to wait for an update.  Found a few posts on their forums where others are having the same problem.  

To stream music to my XBox 360 and PS3, I installed Twonkymedia per [this guide](http://www.twonkyforum.com/viewtopic.php?f=6&t=5065).  Twonky is my only option as I've yet to see a Linux uPNP server that can stream music to both the 360 and PS3.  MythTV has it's own uPNP server, but I don't want it showing up in my server list, so I edited the /etc/default/mythtv-backend file to turn it off.

Next, I installed ampache from the repository and subsequently updated it to the latest version from a PPA from the developer.  Getting it integrated with mpd was a pain.  Turns out you can't use "localhost" as your mpd player in ampache, you must use 127.0.0.1.  Also, mpd must be set to run as the "mpd" user; it can't be run as your own user account because it can't write to it's log files.  This presents serious problems for pulseaudio.  I ran these commands to give mpd access to pulseaudio and added a pulseaudio section to the mpd.conf file:

```
  $ sudo usermod -a -G pulse-access mpd
  $ sudo usermod -a -G pulse mpd
  $ sudo usermod -a -G pulse-rt mpd

```

I tried uninstalling the pulseaudio X11 bell packages, but that had no effect.  If I restart mpd and try to play music through it from ampache, I get nasty X11 permissions errors in my terminal session.  I have found no way to fix this other than to not restart mpd.  So long as mpd is not manually restarted it won't spam these messages and generally works.  The [mpd wiki](http://mpd.wikia.com/wiki/PulseAudio) was somewhat useful in working on this.

Finally, as is widely known, Intel graphics are still hosed in Jaunty.  My mobo has the integrated X3100 chip.  Worked great in Hardy.  I didn't run into the normal things people run into with Jaunty, such as bad framerate and stuttering in video playback.  My playback speed is fine, but all video players have horrible non-vsynced tearing issues.  For mplayer, I use this command line option to make the player use the Intel Overlay as described [here](http://smplayer.berlios.de/forums/viewtopic.php?id=944):

```
vo=xv:port=87
```

This will fix mplayer, but not the MythTV internal player nor XBMC.  In XBMC there is a vsync setting in system options that gets things working there.  For gstreamer apps, gstreamer-properties can be used to set the Overlay as default through the GUI.  I spent a long time tryin to get the MythTV internal player working.  I finally set up a TV playback profile with XvMC.  I had stayed away from this originally because lots of talk seems to suggest that XvMC is broken and/or not implemented in the sketchy Jaunty Intel drivers.  But for some reason it gives me pretty smooth playback without tearing.  

So yeah, that's it.

---

