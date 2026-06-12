---
title: "seeking upgrade to 9.10 reports, please"
date: 2009-10-31
forum: Mythbuntu
---

### Post by wayover13 on 2009-10-31
I would like to ask that those who have upgraded their mythbuntu from 9.04 to 9.10 would post to this thread reporting on how the process went. E.g., was it hassle free? Did you encounter problems? If you can list basic hardware that would be helpful too. I'd like to upgrade my own system (P4 2.6 1 GB RAM, Hauppage 150 capture, NVidia GeForce MX400 AGP video card) from 9.04 to 9.10 but am leery of doing so too quickly. I'd like to first find out whether the process has gone smoothly for others. As you might guess, I'm running older hardware. My experience to date has been that older hardware support tends to get dropped with updated versions of GNU/Linux/Ubuntu.

Input will be appreciated.

Thanks,
James

---

### Post by alexyz on 2009-10-31
Did the distro upgrade yesterday and overall very few problems - some issues with myth though.  This is an all-purpose machine I use as both workstation and dvr - two displays (one is a TV).  To watch TV I fire up mythfrontend on the TV and turn off the monitor.

* Live TV, recording, playback worked out of the box.  Some issues/questions about changes to the UI...

* My previous theme (blootube) was gone, so I switched to another.  

* [FIXED] Problems with video playback (using vlc) - either crashes, or no sound if it works.

The new storage groups feature is probably the cause of the vlc problem - a known issue.  See [MythTV .22 Transition Guide]("http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide") - wish I'd read this first.  But I can't for the life of me understand how you're supposed to disable this feature (as described [here]("http://ubuntuforums.org/showthread.php?t=1304386&highlight=storage+groups") and elsewhere).  There's a "default" storage group and no way to delete it that I can figure out.  Maybe that means I'm not using storage groups?  I'm not sure.

:arrow: Anyhow I recommend looking into the storage groups feature so you know what to expect.

edit:  FIXED but I stand by that recommendation.  For how to fix see chipppy's post below and [my reply]("http://ubuntuforums.org/showpost.php?p=8225586&postcount=17").

A minor but extremely annoying related issue - in the recordings list there's a new storage groups popup menu and I have to redefine my remote somehow so I can pull up the other "info" popup.  Annoying because that's the menu with all the options I need (notably the delete function).  In general the new UI model seems to use more iPod-like rotating navigation, which I find doesn't work very well with my remote and is somehow aggravating to boot.

But overall these are minor - need to reprogram the remote, and probably another few days and I'll find a good explanation of storage groups that will fix the vlc problem.

Hardware not exactly cutting-edge:  P4 3GHz, 2GB RAM, Nvidia Geforce 6800GS/XT, Hauppauge PVR-350, using Sony RM-VL600 universal remote instead of the Hauppauge.

---

### Post by shocksafe on 2009-10-31
_**Hardware**_
gfx card : gforce mx400 64mb
Tuners : DBT airstar2, bt878p (capture)
remote : Hauppauge MCE
cpu : P4 2.4
Mobo : MSI 848p neo


Upgrade was smooth as silk. Only issue was with a theme I installed and had active, deleted the theme directory, restarted front end and it defaulted to MCE Blue (Going from memory here so name could be wrong).

Everything just worked. Didn't have to reconfigure anything.

---

### Post by SFromley on 2009-10-31
Hi

I upgraded just fine (I think) - took an age and a half, but hey it's all free right?

I don't have a tuner yet so really my mythbuntu machine is just a media player at the moment.

One problem I have since upgrading is that the file browser in myth isn't updating the contents of the videos folder - indeed, judging by what it tells me is in there it's using an old snapshot of that dir. I have not yet worked out why it's doing this or where it's getting that information.

Other than that, running through the auto-upgrade from the updates manager from 9.04 to 9.10 went smoothly. It only asked me a couple of questions at the start, and a couple at the end. You really can set it going and then bog off and find something more interesting to do for a couple of hours, once you've got through the first couple of (IIRC - machine role) questions.

Hardware: AMD64 3200, 1gig RAM, nv7900 gfx and nforce4 chipset mobo.

---

### Post by twyt88 on 2009-11-01
H/W: Core 2 duo with 2GB RAM previously running JJ.

Upgraded to KK without a problem. However:

- Gnome was replaced. Which I'm fine with.
- HD viewing and LiveTV on HD channel suddenly have choppy sound. Extra audio buffer needed to be set to resolve this problem
- Could not view my videos under mplayer anymore. That was expected because of the Video SD

Spending (lots of) time with metadata now so I can get Graphite going.

BTW, there aren't a lot of documentation on Graphite, for example, getting fan arts on TV recordings. Coud anyone point me to the right direction?

TT

---

### Post by agamotto on 2009-11-01
**Hardware**
Asus nforce 7 series gfx mobo w/hdmi on board
2gb Corsair ddr2 ram
160Gb WD Caviar SATA hd
LiteOn DVD burner
Hauppauge pvr-150 and hvr-1800 tuner cards

I did a clean install just to make sure previous stuff wouldn't interfere, and as a whole, I will be skipping this one for the next LTS, I think.  Install went well, save for forgetting to set the 'login automatically' box during the install.  I loaded the codecs and nvidia drivers through Mythbuntu Center.

I did the backend setup, with no errors reported.  The newer channel scanner interface for the digital channels was nice, but still doesn't report signal strength.  Nothing major.  Brought everything up in the frontend and no video, period.  I tried all three inputs for Live TV, and nothing.  I went back into the backend, deleted the cards, started over, this time, some success with the video.  The analog input on the 1800 is still useless - I managed to get blue/purple striped video.  The output from the 150 was jittery as hell on any channel with an 'overlay' on the screen.  Digital video oddly, was pretty much perfect.

I say video, because like the last few iterations, Mythbuntu didn't find or didn't set up my audio.  I went into the mixer, made switches for Master Front and PCM, put them at 90%, problem solved.  Myth now had audio for everything but the analog on the 1800.

The main reason I put 8.04 back on is the jittery video on the analog 150 input, which made watching cable near useless.  The Watch TV portion also seems to have caused the system to hang/crash randomly, as there were at least nine occasions where trying to watch the analog from the 150 blacked out the screen, with no response to reset/escape commands.

Other than that, I can't say much, as I didn't bother to explore the rest of it after six hours of these annoyances.

I liked the look of what I saw, but without video/audio that 'just works,' I doubt I will try it again.

Not a bitchfest, just my experience with this iteration.  Oddly enough, 9.10 Ubuntu installed and is working fine so far on this laptop!

---

### Post by blueeyesmike on 2009-11-01
Mostly worked well but I've realised now that mythvideo and mythgame don't work. Basically while mythtv is running it seems to freeze out other programs, so if I try run a video or rom it will fail if mythtv frontend is running, if I close the frontend the video will immediately start playing as if unpaused and I can run roms as well. Still haven't fixed this so if anyone knows what is going on...

---

### Post by AKADAP on 2009-11-01
Unmitigated disaster.

Motherboard: P6T Deluxe with 6 GB memory.
Video: ATI 4850 HD
Optical drive: LG Blue-ray reader DVD burner.

I use this machine as a desktop, myth front end & myth back end.
I had installed Ubuntu first then added Mythbuntu as a package to it. previous updated had left the window manager defaulting to Gnome. 9.10 changed the default to something else which left me without many of the menus I had added, and with much of the functionality using different applications that I was not familiar with. I just figured out today that I can select the window manager at the login screen. This fixed the most irritating of the issues.

I (foolishly) "upgraded" to the ATI 9.10 driver. This seems to actually be a downgrade. Now 16x9 content is squeezed into a 4x3 window, and 4x3 content is stretched to fill a 16x9 screen. no amount of tweaking fixed this. 
I tried uninstalling the ATI 9.10 driver to go back to the one that came with Ubuntu 9.10. I was left with the screen off and a dead keyboard. I had to SSH into the machine to re-install the ATI 9.10 driver. So, I'm stuck with a broken driver and can't revert.

I wanted to test a clean install on another machine. I downloaded the i386 release, and tried to burn it, the burn failed with error code 0 "no error" (this error is repeatable even when simulating a burn). I tried the disk anyway, it crashed when I attempted to verify the disk. I transfered the file to a windows machine and burned it there. The disk verify would spin up the disk for a moment then spin it back down without ever leaving the main menu. I created an ISO from the disk and used cygwin to run diff on the original and read back ISOs, they were the same. I downloaded the ISO again and ran diff against this and found that they were different (How is it with all of the checksums in network connections that it is still possible to get a corrupt file, and why is there no checksum in an ISO?). I burned a new disk and was able to verify this disk and install ubuntu on the old computer. This is where I learned that there was an option to select window managers, and that the default install is still Gnome.

I tried to use mythweb, I get: 
Error at /var/www/includes/mythbackend.php, line 172:
Incompatible protocol version (mythweb=40, backend=50)

So if there is a new version out, it did not get installed.

In summary, 9.10 changed my default window manager, broke mythweb, and broke my ability to burn CDs. ATIs 9.10 drive broke my ability to watch TV.

On top of all of this, pulse audio will still not pass dolby digital or AC3 to my receiver through SPDIF.

On the plus side though recordings are still happening correctly, and the computer is still turning on at the correct times for recordings. Also using the PS3 to play back recordings still works.

Update:
It seems most of my problems were caused by the window manager.
With Gnome, I was able to burn a CD.
The other window manager was not telling me that the flash drive was still busy, and allowed me to unmount the drive anyway. This accounts for the corrupted files, the files on the linux disk were actually good.
Samba is still broken, I can not access the windows shares using Ubuntu.
I reported a bug about the mythweb not working. All I got was a snide remark that I should take it up with the guy who puts my packages together and the bug was closed. Not very helpful.
Both 16x9 and 4x3 streams are being zoomed to fill my 16x10 monitor, so neither is correct.

---

### Post by Babstar on 2009-11-01
Dedicated FE/BE: Core2 Duo,E7400, Gigabyte EP45-UD3P, nVidia 9400GT 4Gb Memory

[s]Fresh install[/s] / Upgrade
Upgraded via ssh, all went smoothly.

New things that worked:
[VDPAU]("http://www.mythtv.org/wiki/VDPAU")

What Didn't work:
[LIST]
[*]Auto-Login [[SOLVED]]("http://ubuntuforums.org/showthread.php?p=8210982#post8210982")
[*]Retro Theme
[*] [s]EIT scan failed.[/s]  Deleted all cards & new channel scan and it works.
[/LIST]

---

### Post by garry.thorpe on 2009-11-01
Big problems.

Been running 8.04 for about a year, no major issues.  Disk died, decided to rebuild with new disk and 9.10 and same hardware (Dell Dimension 1100, 2GB).  Biggest problem is the video is jerky, can't work out why.  Same hardware which worked perfectly before.

Video card is Intel Corporation 82865G Integrated Graphics Controller (rev 02).  Any help or suggestions appreciated.

---

### Post by nickrout on 2009-11-01
> **garry.thorpe said:**
> Big problems.

Been running 8.04 for about a year, no major issues.  Disk died, decided to rebuild with new disk and 9.10 and same hardware (Dell Dimension 1100, 2GB).  Biggest problem is the video is jerky, can't work out why.  Same hardware which worked perfectly before.

Video card is Intel Corporation 82865G Integrated Graphics Controller (rev 02).  Any help or suggestions appreciated.

frontend log???

---

### Post by garry.thorpe on 2009-11-01
> **nickrout said:**
> frontend log???

Good point...  :- )  Thanks

2009-11-02 12:34:13.061 VideoOutputXv Error: Could not find suitable XVideo surface.
2009-11-02 12:34:13.061 VideoOutputXv: Falling back to X11 video output over a network socket.
                              *** May be very slow ***
2009-11-02 12:34:13.061 VideoOutputXv Error: XCreateImage failed: XJ_disp(0xa22eef8) visual(0xa22a5c0)
                        depth(24) WxH(1360x768) bpl(4080)
2009-11-02 12:34:13.064 VideoOutputXv Error: Could not find suitable XVideo surface.
2009-11-02 12:34:13.064 VideoOutputXv: Falling back to X shared memory video output.
                              *** May be slow ***

---

### Post by nickrout on 2009-11-02
xvinfo?

Looks like xv extension is not working in X, its not a myth problem, its an X problem.

---

### Post by chipppy on 2009-11-02
Hey alexyz

A quick fix for the storage groups problem that worked for me was to just modify the default group.  some I just replaced the default location with what I wanted and other I wanted to use the default and my extra harddrive so I just added in the extra locations.  
eg /var/lib/mythtv/hdd2/videos replaced the original for videos, and /var/lib/mythtv/recording; /var/lib/mythtv/hdd4/recordings for my tv recording.  NOTE I have all extra harddrives mounted at /var/lib/mythtv/hdd* (*=number of drive)

Anyway hope that helps a little.

Cheers
chipppy

---

### Post by DominicF on 2009-11-02
Hi,

I started with a fresh install of Mythbuntu 9.10 64-bit version.  I had two problems and decided to switch to the 32-bit version which seemed to have fixed my issues.

The first issue with the 64-bit version was that my system wasn't shutting down/powering down correctly, I could still hear the fans in my PC case still whizzing away.

The second issue was when using the Mythbuntu Control Centre to add plugins e.g. Mythbrowser, I was getting a pop message on screen when trying download the files saying something like to I can not download files from this unauthenticated location.

After changing to the 32-bit version I didn't see these issues.  I still have a few more things to try.

---

### Post by sstakes1 on 2009-11-02
Upgrading from Mythbuntu 8.10.
1. Automatic upgrade of database failed. I'm not sure what the expectation is. Should I upgrade (at least database schemas )to 9.04 and then on to 9.10?

2. As usual missing firmware for Kworld ATSC-110/120 card. Had to copy the file in manually 

3. OSD and picture issues. Text and picture not as sharp as in 8.10. Using Nvidia

---

### Post by alexyz on 2009-11-02
> **chipppy said:**
> Hey alexyz
A quick fix for the storage groups problem ...
chipppy

Thanks chipppy, I figured out the same thing.  My default group was broken because it was pointing to directories that didn't exist (maybe the upgrade is supposed to create them?)  They also need to be writable by the myth process.  After that vlc works fine for playing videos.

AFAICT this IS the proper way to disable storage groups.  You only define the default group.  Way too magical if you ask me, a checkbox somewhere would be a lot more obvious.

Somewhat related, my video listings weren't updating.  To fix:  go to videos list, hit menu (or key M) and choose refresh, rescan, something like that.

One other thing:  the upgrade changed a bunch of file extensions to use the Internal player.  Deleted these and it uses vlc for everything.

---

### Post by sk8er3810 on 2009-11-02
Foxconn motherboard
Athlon 64 2.4Ghz
Nvidia 7300GT
512MB DDR
1x pcHDTV 5500
1x Hauppuage PVR-150
hooked up to a 40" 1080p display DVI to HDMI

Upgraded from Mythbuntu 9.04 to 9.10 using Ubuntu alternate disc

First machine
Frontend/Backend
Install went fine.  Upon reboot auto-login no longer worked. and the mythbuntu-gdm-theme did not show. I got the generic log-in screen
Logging in the window fonts were messed up in Xfce4 but Mythfrontend automatically ran and asked me about upgrading the database schema.  For each of the tables, I just said yes to all.

Frontend only machine
Auto-login didn't work and no more mythbuntu-gdm-theme.  However unlike the Backend the window fonts looked fine after logging in.

I did a clean install on the frontend because I didn't feel like fighting with it and everything works fine on it.

I'm still fussing with the backend because it requires more initial configuration post clean-install.

---

### Post by the_pod on 2009-11-02
One thing I haven't seen mention of but am curious about.  Is the volume level on playback fixed?  

My biggest complaint to-date with the Mythbuntu distro has been that the sound levels are seriously depressed. I've heard this is specific to the Mythbuntu distro and that Knoppmyth doesn't experience this.  Would prefer to upgrade inside the Ubuntu family since I'm most familiar with that but am holding off a bit until I'm really comfortable.

Thanks for any info.

---

### Post by sk8er3810 on 2009-11-02
Good question.  It might still be broken seeing as last night I tried to change the volume on my frontend but didn't notice a difference in volume.  I was watching live tv streaming from backend to dedicated frontend.  Didn't pay much attention to it at that point but I'll check it when I get home in a few hours.

:(
I may end up doing a clean install on my backend if I can't fix the large window title font problem.

---

### Post by kja999 on 2009-11-02
> **DominicF said:**
> Hi,

I started with a fresh install of Mythbuntu 9.10 64-bit version.  I had two problems and decided to switch to the 32-bit version which seemed to have fixed my issues.

The first issue with the 64-bit version was that my system wasn't shutting down/powering down correctly, I could still hear the fans in my PC case still whizzing away.

The second issue was when using the Mythbuntu Control Centre to add plugins e.g. Mythbrowser, I was getting a pop message on screen when trying download the files saying something like to I can not download files from this unauthenticated location.

After changing to the 32-bit version I didn't see these issues.  I still have a few more things to try.

Interesting you say this. I'm having the power off issues on the 32bit version .maybe I should upgrade to 64 :-)

---

### Post by nickrout on 2009-11-02
> **the_pod said:**
> One thing I haven't seen mention of but am curious about.  Is the volume level on playback fixed?  

My biggest complaint to-date with the Mythbuntu distro has been that the sound levels are seriously depressed. I've heard this is specific to the Mythbuntu distro and that Knoppmyth doesn't experience this.  Would prefer to upgrade inside the Ubuntu family since I'm most familiar with that but am holding off a bit until I'm really comfortable.

Thanks for any info.

What TV source are you using?

Are you playing back to digital (spdif or hdmi) or analogue?

---

### Post by NTolerance on 2009-11-02
1.  The upgrade app gave me a prompt towards the end about removing obsolete packages.   I naturally chose to accept to remove these packages.  Unfortunately, both mythtv and mythvideo are considered obsolete, so they were removed.  I discovered this when I started the frontend and it couldn't connect to the database.  A simple apt-get of mythtv and mythvideo fixed this.

2.  mplayer no longer works in mythvideo.  No fix for this at this time, can only use the internal player for now.  I am not using storage groups for mythvideo.  

3.  My apache config was overwritten and my index.html is no longer loaded.  Instead, my webserver goes directly to mythweb.  Need to fix this.

---

### Post by stans on 2009-11-02
I had no new problems - just the old one did not go away as I hoped it would (usb mouse lockup).

---

### Post by shocksafe on 2009-11-02
I replied on page one about my upgrade going smoothly.

However, I since did a fresh install of 9.10 and can no longer get nvidia drivers to work.
Did not have this problem with the upgrade though.

Just thought I'd mention it seeing you (OP) have the same graphics card.

---

### Post by the_pod on 2009-11-03
> **nickrout said:**
> What TV source are you using?

Are you playing back to digital (spdif or hdmi) or analogue?

Re: TV Source - not sure I understand the question.  It is QAM 256 via cable (Comcast), however if that's what you meant.

For audio I'm running analog out via a dangler that splits the sound into 2 channels and inputs into the amp/receiver via RCA cables.  Video is run via HDMI but haven't girded up the loins to mess with the sound via HDMI after initial efforts (slack efforts on my part to be fair) were unsuccessful.  

When playing video out (DVD or TV / recording) I need the Myth audio cranked to roughly 90% (with full volume enabled in the system) and the amp/rcvr volume at roughly 80%.  When playing audio files through the same system this volume level is pretty deafening, so there's obviously a disconnect.  

Don't have links handy but did a bunch of searching several months ago and came to the conclusion that that was just the way it was going to be.  If you think getting my HDMI audio working will help I may do that.

Not trying to steal the thunder of the original post, but thought I'd provide some context.

---

### Post by SpotTheWonderDog on 2009-11-03
My upgrade was a disaster.  I got the 'general error mounting filesystems'

I followed a bunch of instructions which only messed up my other non-Ubuntu hard disks.  One hard disk I wasn't able to recover.  Fortunately I had made backups of my MBRs for the Windows RAID disks otherwise I would have lost Windows.

It's best to unplug your other hard disks before upgrading or installing Ubuntu.

Somehow, after many hours I finally got Koala working.  Sound still doesn't work.  Auto-login doesn't work.  I got used the Jaunty icons but now they've changed so I have to think about which icon I should press for a second or so.  Yeah, I'll get accustomed to them but why did they have to change?  Change for the sheer sake of change?  Bored programmers?

I hate the new background.  I haven't found a single reason for the upgrade.  I not upgrading any other Jaunty computers.

If you can, clone your hard disk to another before installing.  It'll save you many hours of grief if you run into an upgrade problem.

For some people, the upgrade went smoothly but for  a lot of others where the upgrade was a total nightmare.

For me, it was lots of work and zero value add.

---

### Post by bph663 on 2009-11-14
Upgraded from 9.04.
Using asrock 330 ion, spdif for audio, hdmi for video, xbmc, boxee, (and mythtv), usb-uirt irblaster, snapstream firefly remote. Already had the .21 to .22 fixes from avenard installed for the vdpau.

Had to uninstall the avenard patches for the myth update to take.

So far, only broken things not resolved (still looking for solution after a few weeks) that used to work:
1. usb-uirt no longer transmits (only used for transmit, not not receive)
2. boxee videos (hulu,etc.) play with no audio over spdif (analog out not being used). 
3. VLC and mplayer have no audio over spdif (just trying to play mp3's). However, local mp3's play from boxee.
using ALSA, pulseaudio not installed

update: boxee audio over spdif is ok now. Changed Passthrough output device in boxee audio settings from "iec958" to "iec958 D" (as named in my alsamixer). Audio then played for hulu videos. Looking at audio settings after this shows passthrough output device is now "default". (go figure, I know I tried default before.) 
Other audio settings are: Audio output=Digital; DD and DTS capable receiver boxes are checked; Audio output device=iec958; Downmix multichannel to stereo is unchecked.

---

### Post by argonsloth on 2009-12-25
I decided X-mas was the perfect time to upgrade my mythTV network because I had a 48 hour period without any scheduled recordings. It's a pretty ambitious setup composed of 2 standalone frontends, one combo back/frontend. All outputting to TVs. The signal comes via ExpressVu so the backend needs an IR transmitter to control the STB. I'm using a serial IR blaster purchased from irblaster.info. It's using a Hauppauge PVR 350 for recording and IR receiving. 

One of the Frontends uses a serial homebrew IR receiver and an orphaned DVD remote, the other uses an Xbox DVD kit, with the receiver grafted onto a USB cable.

Before the upgrade everything was based on Mythbuntu 8.04. Upgrading to 9.10 wasn't too bad, had to do it incrementally to 8.10 -> 9.04 -> 9.10. But the machines were able to do it concurrently via ssh. So the whole upgrade process took about two hours.

Unfortunately things didn't go smoothly. lirc problems on the two machines that rely on lirc_serial.

The backend uses lirc_serial to drive the IR transmitter, and lirc_i2c to drive the IR receiver. No matter what I try, I cannot manage to both working at the same time. Seems to depend on which of lirc_serial or lirc_i2c gets loaded first. My lircd configuration files haven't changed, and two lircd processes start, so I'm pretty confused over what's going here. 

On the upside, the backend is rarely ever used as a frontend. As a temporary fix, I've disabled the receiver and enabled the transmitter. Which allows the backend to control the STB.

The other frontend was not so lucky. It relies on lirc_serial for IR reception, and that just doesn't work at all. mode2 doesn't recognize signals from any remotes. So far I've tried reverting lirc to the version installed with 8.04, but no dice. 

About all that's left is to try compiling lirc from source on either machine. The really weird thing is that there's nothing in the logs/dmesg suggesting that anything is going wrong.

---

### Post by SiHa on 2009-12-26
> the other frontend was not so lucky. It relies on lirc_serial for ir reception, and that just doesn't work at all. Mode2 doesn't recognize signals from any remotes. So far i've tried reverting lirc to the version installed with 8.04, but no dice. 
If it helps,```
sudo dpgk-reconfigure lirc
```...was all I needed to do to get my homebrew serial receiver working (ie, mode2 working)with 9.10, then I just copied the relevant files (hardware.conf, lircd.conf, lircrc, and ~/.lirc/*) over from my old 8.04.1 install.

---

### Post by DataTracer on 2010-01-14
I've been having a terrible time with my "upgrade" to 9.10 karmic. I use MythBuntu, and I had a perfectly working 9.04 box that served as my MythTV front/backend. I'm using a single Hauppauge HVR-1600 with IR Blaster/Receiver. Before the update, the blaster and remote both worked fine using the lirc_pvr150 module. Currently using the lirc_zilog module as a workaround since pvr150 is either broken or no longer being maintained. I can't get it to work no matter what I try, and it doesn't seem to be giving any errors on start up...

$ dmesg | grep lirc
[   19.064312] lirc_dev: IR Remote Control driver registered, major 61 
[  284.912937] lirc_zilog: Zilog/Hauppauge IR driver initializing
[  284.916982] lirc_zilog: initialization complete

From /var/log/syslog
--- On lirc restart

Jan 14 17:46:50 mythion lircd-0.8.6[4616]: caught signal
Jan 14 17:46:50 mythion lircd-0.8.6[4609]: removed client
Jan 14 17:46:50 mythion lircd-0.8.6[4609]: caught signal
Jan 14 17:46:50 mythion lircd-0.8.6[4673]: lircd(default) ready, using /var/run/lirc/lircd
Jan 14 17:46:50 mythion lircd-0.8.6[4680]: lircd(default) ready, using /var/run/lirc/lircd1
Jan 14 17:46:50 mythion lircd-0.8.6[4680]: connected to localhost
Jan 14 17:46:50 mythion lircd-0.8.6[4673]: accepted new client from 127.0.0.1
Jan 14 17:46:50 mythion lircd-0.8.6[4673]: accepted new client on /var/run/lirc/lircd

--- After running an irsend command

Jan 14 17:47:05 mythion lircd-0.8.6[4673]: accepted new client on /var/run/lirc/lircd
Jan 14 17:47:05 mythion lircd-0.8.6[4673]: bad send packet: "p#027"
Jan 14 17:47:05 mythion lircd-0.8.6[4673]: removed client
Jan 14 17:47:05 mythion lircd-0.8.6[4673]: error reading from /dev/lircd
Jan 14 17:47:05 mythion lircd-0.8.6[4673]: Success
Jan 14 17:47:05 mythion lircd-0.8.6[4673]: removed client
Jan 14 17:47:05 mythion lircd-0.8.6[4673]: accepted new client on /var/run/lirc/lircd

The bad packet error might be because my codes are incorrect, but I can't use irrecord to get new remote codes! I have tried to get input from my remotes using irw, and I've also tried running irrecord and neither of them work.

I should note I am using the 64-bit version of 9.10 . I may roll back to 9.04 32-bit, or even try the 32-bit version of 9.10 . I didn't really want to do that since my machine is a new Atom 330 and I wanted to use MythTV .22 VDPAU support for the nvidia chip that is already built in.

Option number 2 is just to research IR blasters that are confirmed to work with 9.10 and just buy a new one! Ugg.

---

### Post by bcg30506 on 2010-01-14
DataTracer, I'm using VDPAU with my NVIDIA system just fine on 0.21-fixes (mythbuntu 9.04) with the avenard packages added.  This system has been good and stable and your story is exactly why I don't upgrade.

I'd suggest going back to 9.04+avenard and you'll get VDPAU.

---

### Post by azmyth on 2010-01-15
Ah, the joys of lirc. The toughest thing about mythtv. One issue on this will give a ton of headaches. I noticed in the latest hardware.conf when I did the upgrade is they made some changes to the file so I'd compare as if I recall they added some extra options to remote and transmitter. Don't know if this could be your issue assuming you used the one from the previous rev of MB.

---

