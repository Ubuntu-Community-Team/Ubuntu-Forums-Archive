---
title: "no commercial DVD playback - did 'how to'"
date: 2008-08-27
forum: Multimedia Software
---

### Post by tparker on 2008-08-27
It has been about four months since I could play commercial DVDs and it's about to drive me away from Ubuntu, any help is appreciated.

Computer is an AMD 64 athlon chip running 32 bit Heron, was a fresh install not an upgrade, DVD player is HP internal 840. Player works fine in other machines, all DVDs play fine in other machines. Same DVDs played fine on this machine, this install, until an update about four months ago. 

I have gone through and reinstalled the libs, dcss, etc according to instructions in the sticky at the top of this section and the instructions in the 'help' section. Nothing changed - it was all there already. I deleted it all and reinstalled - no change. 

DVD player shows up in Places->Computer but says it can't mount.

If a commercial DVD is in the drive when I boot the machine the start up will hang just before 'loading grub' and stay there until I pop the DVD drive open.

If I play a DVD in Xine it tells me there is no disk in the drive and/or can't mount it.

If I play a DVD in Kaffeine it tells me: 
"This DVD Video is encrypted. To be able to watch it you will need to install libdvdcss by running from a console: sudo /usr/share/doc/kaffeine/install-css.sh." Which I have done and verified is there but I still get the message. 

If I put in a homemade video DVD it plays just fine, no errors; video, sound, and menus all work perfectly.

I am completely lost as to how to fix this and very disheartened about linux because of it. Watching the DVDs I buy is over half of my computer use and I've stopped even buying new DVDs since I can't watch them.

I am happy to post any other information that can help but will need to be told how to find whatever you need, I'm very much an 'end user' computer wise. :)

---

### Post by mc4man on 2008-08-27
Are you running Kubuntu or Ubuntu?
Put a comm. disk in your drive, let it settle and then run 
```
sudo lshw -C disk
``` and post *cdrom listings

edit; forgot to mention, kaffeine shows that message for just about all problems. It also needs the default dvd device to be /dev/scd[COLOR="Red"]x[/COLOR] (in settings -> xine engine parameters -> media. (change x to match from above comm

---

### Post by tparker on 2008-08-27
Here is the response to sudo lshw -C disk:

*-cdrom
       description: DVD-RAM writer
       product: DVD Writer 840x
       vendor: HP
       physical id: 1
       bus info: scsi@9:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: S632
       serial: [HP      DVD Writer 840x S63206/01/12CNN92277
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready

I checked to be sure the xine engine parameters were scd0 and they were already.

---

### Post by mc4man on 2008-08-27
> configuration: ansiversion=5 status=ready
Was there a disk (preferably a comm. dvd) in the drive when you ran sudo lshw.....,?
Above is indicating nothing (no file system found) in the drive.

Edit; just tried comm. dvd playback in kubuntu and something is borked. Have got players opening a comm. dvd (didn't initially), but no decryption is being done. (added medibuntu and installed libdvdcss2
Will post back when I get it working

---

### Post by mc4man on 2008-08-27
What a pita kubuntu can be. Installed vlc because it's easier to trouble shoot. First it didn't want to access /dev/scd0 and then when it did playback was decrypted still. Showed encrypted dvd support unavailable.(libdvdcss2 is installed
Did a reboot, went into home dir. and opened the **.dvdcss folder**, deleted the contents, and now can playback dvd's with vlc and kaffeine

So I'd add the medibuntu repo, install libdvdcss2 and try kaffeine.
If that doesn't work, find and empty the .dvdcss folder. ( and maybe reboot
If that doesn't work install vlc and try all again

---

### Post by tparker on 2008-08-28
Had medibuntu added, reinstalled libdvdcss2 through them (it had already been there so I deleted and reinstalled) - no change, same error messages.

I emptied the .dvdcss folder, rebooted and tried both xine and kaffeine again, still no change. 

I installed vlc through synaptic, tried to play a commercial dvd in it and got the error: Unable to open 'dvd:///dev/scd0'

Retried vlc through command line to see if it gave more info and got this:

VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/scd0 with libdvdcss.
libdvdread: Can't open /dev/scd0 for reading
libdvdnav: vm: faild to open/read the DVD
[00000287] dvdread demuxer error: DVDRead cannot open source: /dev/scd0
[00000288] vcd access error: could not read TOCHDR
[00000288] vcd access error: no movie tracks found
[00000288] access_file access error: file /dev/scd0 is empty, aborting
[00000288] cdda access error: could not read TOCHDR
[00000288] cdda access error: no audio tracks found
[00000285] main input error: no suitable access module for `dvd:///dev/scd0'
[00000280] main playlist: nothing to play

---

### Post by djRobbieF on 2008-08-28
Have you tried multiple DVDs?  Try a different one.

---

### Post by djRobbieF on 2008-08-28
> **tparker said:**
> If I put in a homemade video DVD it plays just fine, no errors; video, sound, and menus all work perfectly.

Just looked at your first post and saw that.  Did you install the decoders?

sudo apt-get install libdvdread3

You need that to read encrypted DVDs.

---

### Post by tparker on 2008-08-28
<quote> Did you install the decoders? </quote>

Thank you but yes, I have, over and over. :)

Deleted it all and reinstalled then re-reinstalled. Have added them through apt-get, synaptic, medibuntu. Followed all the steps in the media stickies and the ubuntu help page for restricted formats. It all worked fine until it magically didn't so the main thing I have tried is reinstalls and attempts to update hoping it was just something corrupt somewhere and that that would fix it.

---

### Post by tparker on 2008-08-28
In the command line errors for vlc I noticed the line:

[00000288] access_file access error: file /dev/scd0 is empty, aborting

I checked that file and it really is empty. Is it supposed to be or is there supposed to be something in the file?

---

### Post by mc4man on 2008-08-28
Is a dvd icon showing up on the desktop? If so right click on it -> open with dolphin. Then right click on the VIDEO_TS folder -> open with kaffeine.
That's what I had to do **once** to get the filesystem recognized and kaffeine, vlc working. Took over a min. for kaffeine to respond, after that all is back to 'normal', as far as normal is in kubuntu.

---

### Post by tparker on 2008-08-28
No, the dvd icon is not showing up on the desktop. When I put a commercial dvd in the drive and close the drive I get a very quick flash on the desktop that looks like it might be the icon, but it goes away before I can even see it clearly. After that nothing else shows up on the desktop and the light on the dvd drive flashes slowly and doesn't stop until I pop the drive open again. I let it flash for over 5 minutes the first time, tried again and let it flash for 10 minutes. 

If I put in a no-drm disk (homemade video dvd) I get the desktop icon and the it plays fine.

---

### Post by chip616 on 2008-08-28
mc4man:

I have similar issues on my Dell vostro 1700 and 1710 with Kubuntu 8.04.  I do get a desktop icon, and I tried to open the file from Dolphin with Kaffeine.  I get the same error message that I need libdvdcss.  Libdvdcss is installed.

I tried reinstalling, and tried the medibuntu repository that you pointed us to as well.  No dice.

I tried removing Kaffeine (I've yet to find a version of it that really worked) and installed xine and the xine-ui, which I have used for years with Xandros and Fedora.  Then I get a 'source can't be read' message suggesting that I don't have enough rights, or that there is no disc in the drive.  Interestingly, I get one of those error messages for every file on the DVD (stacked one on top of the other), proving that Xine IS seeing the files, and therefore it is seeing the disk.

Now, before I removed Kaffeine, I did try another commercial DVD in my Vostro.  It played that one.  The DVD I am trying to play now works in my home DVD player, so the disk is not bad.  But nothing I can do makes it work in this machine with Kubuntu 8.04.

However:

I tried this same DVD on my desktop machine downstairs.  'White box' AMD 2800 with generic DVD reader/writer and also running Kubuntu 8.04.  First time I dropped the DVD in, it complained about the lack of libdvdcss, and gave me the script to run to load it, which I did.  DVD ran just fine on that machine.

So what in blazes is going on here?

Frank.

---

### Post by mc4man on 2008-08-28
> So what in blazes is going on here? i truly don't know.

Everything works fine now, really can't explain it, i had all the symptoms both of you described (except icon not showing up)
lshw..... showed no filesystem, the players couldn't connect ect.,ect.

when I hover over the icon now it shows DVD Video Disk, Device node /dev/scd0 and plays back fine. D. clicking adds a mount point at /media/cdrom but isn't necessary for playback

I'm going to remove this install and start over with a livecd from april and pay closer attention.

Edit; just did a fresh, un-updated  install - atm kaffeine will not playback - keeps wanting to install libdvdcss2 - getting 404 error on the site. Installed libdvdcss2 from medibuntu, still won't work even though the decryption keys are being added to .dvdcss.
Installed vlc, it works fine, kaffeine doesn't.

Edit: a full update and kaffeine doesn't play. The libdvdcss error now shows a script to run. (worthless if libdvdcss2 is already installed.
Kaffeine actually creates a valid folder in .dvdcss.

What's missing is libxine-ffmpeg and maybe a few other libxine1* (libxine1-x, libxine-misc-plugins.

Trying to open the disk from any open with... -> multimedia -> kaffeine should get prompt to install these libs, or manually install.

After that kaffeine works fine from the initial popup, autoplay, and r.clicking on the dvd icon -> play dvd with kaffeine'

Atm any of the 'open with....ect' plays the disk but doesn't decrypt.      (such nonsense)

---

### Post by HousieMousie2 on 2008-08-29
> **mc4man said:**
> Is a dvd icon showing up on the desktop? If so right click on it -> open with dolphin. Then right click on the VIDEO_TS folder -> open with kaffeine.
That's what I had to do **once** to get the filesystem recognized and kaffeine, vlc working. Took over a min. for kaffeine to respond, after that all is back to 'normal', as far as normal is in kubuntu.

Didn't fix it for me... but at least I am one step closer to it being fixed... it is no longer giving me the Encryption BS.  It just gets stuck on a single screen and will not change.  Time for a shut down/power up I think, see if that changes it's tune.  :)

---

### Post by mc4man on 2008-08-29
> Didn't fix it for me... but at least I am one step closer to it being fixed... it is no longer giving me the Encryption BS. It just gets stuck on a single screen and will not change.
If you got the libxine1 libs installed, (maybe d.check in adept for 3 mentioned above) then try going into home dir. (show hidden files), find the .dvdcss folder and delete the contents inside. See edit in above post for some ways kaffeine is successfully opening atm.

If still no good install vlc (will install add. libs
Vlc works good and maybe the add. libs are useful

---

### Post by tparker on 2008-08-29
New attempt, I deleted everything I could find that looked related to playing videos/dvds, made sure I had the libs, dcss, etc per the tutorial/stickies and reinstalled vlc through synaptic, then rebooted.

It looked like it almost worked. In the control window for vlc I got zeros in the place were it tracks how far into the disk you are and it opened a window to show the video in - it had not been seeing the disk enough to get that far before. It stopped at that point with an error window that said: Unable to open 'dvdsimple:///dev/scd0'    That is a different error than I was getting before. 

I had started it in command line and the info that gave at the error is: 

VLC media player 0.8.6e Janus
[00000294] dvdread demuxer error: DVDRead cannot open source: /dev/scd0
[00000296] vcd access error: could not read TOCHDR
[00000296] vcd access error: no movie tracks found
[00000296] access_file access error: file /dev/scd0 is empty, aborting
[00000296] cdda access error: could not read TOCHDR
[00000296] cdda access error: no audio tracks found
[00000292] main input error: no suitable access module for `dvdsimple:///dev/scd0'
[00000283] main playlist: nothing to play

Any ideas?

Forgot to include - still no DVD icon on desktop this time other than the quick flash of one, same as before. Also tried data cd and a non-comm. video dvd again, both worked fine.

---

### Post by soch on 2010-06-04
Even when there is a disk in the drive lshw says no disk!!!

I have installed libdvdread4 & run the install-css.sh

Any help will be appreciated.


-laptop:/usr/share/doc/libdvdread4$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: Hitachi HTS54108
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MB4O
       serial: MPB4PAXKK7KWAM
       size: 74GiB (80GB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=8d08c9b1-775d-41e3-a0a9-57163c4edfcd
  *-cdrom
       description: DVD reader
       product: UJDA755yDVD/CDRW
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.72
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc


/dev$ ls -l /dev/cdrom*
lrwxrwxrwx 1 root root 3 2010-06-04 02:25 /dev/cdrom -> sr0
a@a-laptop:/dev$ ls -l /dev/dvd*
lrwxrwxrwx 1 root root 3 2010-06-04 02:25 /dev/dvd -> sr0

---

