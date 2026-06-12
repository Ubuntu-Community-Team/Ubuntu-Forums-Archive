---
title: "Get DVD operating in Myth frontend ?"
date: 2013-03-31
forum: Mythbuntu
---

### Post by gga96 on 2013-03-31
One frontend machine has two DVD installed. I cant get them working in the myth frontend.

I thought the drive should be mounted ...

glen@glen-mythtv:~$ wodim --devices
wodim: Overview of accessible drives (2 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'    rwrw-- : 'LITE-ON' 'DVDRW SHM-165P6S'
 1  dev='/dev/sg2'    rwrw-- : 'HL-DT-ST' 'CD-RW GCE-8527B'
-------------------------------------------------------------------------
glen@glen-mythtv:~$ sudo mkdir /media/cdrom
glen@glen-mythtv:~$ sudo mount -t iso9660 /dev/sg1 /media/cdrom
[sudo] password for glen: 
mount: /dev/sg1 is not a block device

Googling suggested ...
glen@glen-mythtv:~$ dmesg | grep dvd
[    2.235590] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray.

Any help is appreciated.

---

### Post by AlecJ on 2013-03-31
you need a disk in the drive, so there is something to mount, then it will appear in /media/
the device is not cdrom but sr0 and sr1, you may have to add the path to the cdrom in the frontend setup as /dev/sr0:/dev/sr1

---

### Post by gga96 on 2013-04-01
Thank you again Alec.
Some progress has been achieved.
Frontend "Utilities/Setup>Setup>Video Settings>Player Settings" as:
    Default Player    Internal
    DVD Player    /dev/sr0
    DVD Drive    default
    Blu-Ray Mount    /media/cdrom
    ...    
The result is I now get a menu to choose between the two drives. Having chosen the DVD drive I am returned to the menu without seeing any video. 
I suspected the DVD drive and tested the desktop VLC with "Media>Open Disk": 
    Disk devise /dev/sr0
    Play
Nothing happened.

I have stuffed up somewhere along the way!
Glen

---

### Post by AlecJ on 2013-04-01
With a DVD in the drive check out the new folder at /media/
to see it it is mounting properly.

a manual mount everything is
sudo mount -a

if there are any errors, there normally displayed after this command

---

### Post by gga96 on 2013-04-01
Drive with new DVD inserted and door closed,  /media/cdrom/ is empty. File Manager lists DVD label.
In File Manager when I right click Mount Volume, /media/MASH_SEASON_DISK_1/VIDEO_TS.
When I open then close DVD drive...
   sudo mount &#8211;a
does nothing. Nothing errors or otherwise.

The failure with VLC has prompted my memory.
Prior to posting this thread seeking help the following took place.

Googling several sites referred to libdvdread as necessary and that led to 
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs).

So I followed instruction...
Install the libdvdread4 package:
   sudo apt-get install libdvdread4
Then open a terminal window and execute: 
   sudo /usr/share/doc/libdvdread4/install-css.sh

During the process I approved for some files to be removed, then later the 
process failed. So some files may be missing from the system.

---

### Post by AlecJ on 2013-04-01
the folder you created /media/cdrom won't do anything as nothing is telling it to mount in fstab , I would delete this folder it will only confuse things.

the dvd's should mount automatic and appear as the title of the dvd at /media/   this is correct and may also appear on the desk top.
Myth frontend should be able to play the dvd.

The libdvdread4 package's are for reading the copy protected dvd's but Myth normally has these or similar installed.

I take it this is your vanilla myth install?
first go to Thunar settings (file manager) and ensure it is set to auto mount CD's etc you may need to start it with privileges so in a terminal

```
sudo thunar
``` 

I would also in Myth Control Centre enable the update repository, I guess your using 0.25 without the fixes.
so

---

### Post by gga96 on 2013-04-01
Thank you, did all the above.

During the Update Manager Check and Update procedures two questions arose.
1. "Could not install 'samba4'...not in working state...subprocess installed post-installation script...returned exit status 126.
2. I answered No to using MythWeb exclusively by mythtv.

Still cant play desktop VLC. Have not tried anything with samba4.

---

### Post by klc5555 on 2013-04-01
> **gga96 said:**
> One frontend machine has two DVD installed. I cant get them working in the myth frontend.

I thought the drive should be mounted ...

glen@glen-mythtv:~$ wodim --devices
wodim: Overview of accessible drives (2 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'    rwrw-- : 'LITE-ON' 'DVDRW SHM-165P6S'
 1  dev='/dev/sg2'    rwrw-- : 'HL-DT-ST' 'CD-RW GCE-8527B'
-------------------------------------------------------------------------
glen@glen-mythtv:~$ sudo mkdir /media/cdrom
glen@glen-mythtv:~$ sudo mount -t iso9660 /dev/sg1 /media/cdrom
[sudo] password for glen: 
mount: /dev/sg1 is not a block device

Googling suggested ...
glen@glen-mythtv:~$ dmesg | grep dvd
[    2.235590] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray.

Any help is appreciated.

At this point I have to return to the beginning: why are you trying to manually mount this DVD to your filesystem from a terminal in the first place? One normally manually mounts a data DVD or CD prior to manipulating files, but one doesn't mount a video/music DVD/CD prior to simple Video/Music playback with any standard video/music player.

Without manually mounting /dev/sr0 (or /dev/sr1) to your filesystem, run VLC (or Xine) from a terminal (regular user not sudo). Put a media DVD in /dev/sr0. Tell the player to playback from /dev/sr0 (or in Xine's case, from "DVD" if it's running one of its usual skins) If there is an error in the playback, some useful error message is likely to be displayed in the terminal window.  Including errors with libdvd, libdvdcss2, inability to find /dev/sr0, etc.

libdvdnav  and libdvdread should have been installed with your plain-vanilla mythbuntu installation. Most commercial DVDs will also require the restricted library libdvdcss2, normally gotten from [http://www.medibuntu.org/](http://www.medibuntu.org/) and easily installed with the gdebi installer. Depending on your version of mythbuntu some few recent DVDs (post late 2011 Paramount and Lionsgate releases) may have a copy-protection scheme that older versions of libdvdnav, libdvdread, and libdvdcss2 can't handle.

---

### Post by gga96 on 2013-04-01
[FONT=courier new]Thank you klc5555 for your interest.

Yes this is my vanilla system with local and remote frontends connected but [/FONT]the DVD was not recognized.  
This lack of DVD led to an attemp to install libdvdread4 but the system was currupted during this process (refer prev posts).

The results of VLC...
> 
glen@glen-mythtv:~$ vlc /dev/sr0
VLC media player 2.0.5 Twoflower (revision 2.0.5-0-g1661b7d)
[0x82758f0] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QGtkStyle was unable to detect the current GTK+ theme.
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.css     **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: MASH_SEASON_1_DISC_1
libdvdnav: DVD Serial Number: 2D5689D1
libdvdnav: DVD Title (Alternative): MASH_SEASON_1_DISC_1
libdvdnav: Unable to find map file '/home/glen/.dvdnav/MASH_SEASON_1_DISC_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
[0xb7400618] main input error: ES_OUT_RESET_PCR called
[0xb7400618] main input error: ES_OUT_RESET_PCR called
[0xb7400618] main input error: ES_OUT_RESET_PCR called
[0xb7400618] main input error: ES_OUT_RESET_PCR called

This looks to indicate some errors with VLC.

One thing at a time but the samba4 problem still exists and the remote frontend will no longer connect.

---

### Post by gga96 on 2013-04-02
OK i have got the DVD working at last and remote frontends connecting. Slight picture distortion at times. I think the problem was with samba4.

Could you please advise if better results can be achieved with changes to "Player Settings" ?
Currently the vanilla set is ...

Default Player: Internal
DVD Player: Internal
DVD Drive: default
Blu-ray Mount: /media/cdrom

My up coming agender items are
1. get WiFi working
2. frontend sleep/wake on AsRock ION 3D 
3. network boot frontend (no HDD)
4. auto re-boot after power failure

Any good reference material tips will be greatfully received.

Thank you both once again.
Glen

---

### Post by klc5555 on 2013-04-02
One problem indicated by the VLC messaging is that you haven't installed libdvdcss2. Therefore encrypted discs (i.e. 95% of all commercial  DVDs) can't be played. Install libdvdcss2, either from the control centre or via the link posted earlier.

Also the DVD you played was region-masked to regions 2, 4. Normal of course for UK/Europe, but, if new, check which region your DVD drive is set for --if the drive was intended for the US market it may have been set to region 1. Mythtv can't (nor can VLC any longer) automatically compensate in software for the region setting of the DVD drive, since really modern DVD drives like Matshita's check the region of the DVD from firmware before allowing the software to access the block device.

As for your other desiderata, items 3 and 4 are handled by settings in the bios setup of the machine that you wish to be network booted or that you wish to automatically reboot after power outages. Note that a dirty shutdown from a power outage may frequently leave some peripherals in a state where (after the machine auto-reboots) the peripheral simply won't function until the machine is shut down again --cleanly this time-- and restarted. I've had several TV tuners and USB IR blasters that were like this. So where power glitches of a few seconds or even 10-15 minutes are common, in addition to auto-rebooting I've preferred  to put the most massive UPS unit I could afford on the backends I don't want to crash. That way, if the backends go down, at least it was due not to a glitch, but to a serious power interruption (like a day or so off after a hurricane, as happened last fall). 

Items 1 and 2 will be topics for other threads, but expect WIFI on frontends to be functional (even for HD), but certainly not as reliable as ethernet.

---

### Post by AlecJ on 2013-04-02
Just a point
but have you installed the Restricted extra's from Myth control centre, on the last menu?

These problems should not have not happened.

---

### Post by gga96 on 2013-04-02
Good morning from under down under.

Thank you for your advice klc555 it was helpful and along with AlecJ eventually led to a happy ending.

The result of running **vlc /dev/sr0 **indicated that no css library was available. So after &#8220;Activate MythTV Update Repository&#8221; to 0.26 I retried &#8220;Proprietary Codecs&#8221; again and it worked this time.

Regards
Glen

---

