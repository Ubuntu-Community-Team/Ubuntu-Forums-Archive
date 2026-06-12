---
title: "Cannot play DVDs (yes another one of those...)"
date: 2008-05-21
forum: Multimedia Software
---

### Post by masonfoley on 2008-05-21
I followed the instructions posted [here]("https://help.ubuntu.com/community/RestrictedFormats") for 8.04 and the packages installed without any noticeable errors. Although I did not see it load/install libdvdcss2.  So I added the following repository:

> [http://packages.medibuntu.org/](http://packages.medibuntu.org/)

From there I was able to browse and install libdvdcss2.  Again, no apparent errors so I'm assuming no errors.  Also, the package is indicating it is installed. 

However, when I attempt to play DVDs in Kaffeine, Kaffeine proceeds to attempt to install a codec.  Here is the message:

> 
Codec not found

LibDVDCSS ([http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html)) is about to be installed, it allows you to watch encrypted DVD videos.  This is illegal in some countries which require decryption to be authorised by the copyright holder. Do you want to install this package?

So I click on Yes to this prompt and then my browser will load with the following address:  > [http://kubuntu.org/packages/libdvdcss-i386.deb](http://kubuntu.org/packages/libdvdcss-i386.deb)

Which is a bogus address apparently as the page reads:
> Object not found!
 The requested URL was not found on this server. If you entered the URL manually please check your spelling and try again. 
 If you think this is a server error, please contact the webmaster. 
Error 404
www-master.kubuntu.org
 Thu May 22 03:35:21 2008
 Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a

What's the deal?  Quite a frustrating experience to say the least and after 2 hours of browsing here and there, running into countless dead-ends, I'm giving up for the evening.

What's supposed to be a 15 minute install has turned into, now, 4 days of troubleshooting, trying various how-to's, tweaking and guessing my way through various configurations.  Surely it shouldn't be this hard no?

---

### Post by cor2y on 2008-05-21
Completely remove the libdvdcss2 package.
And follow the guide for adding the medibuntu repos for your specific version of ubuntu.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Update, then via synaptic or the terminal install libdvdcss2 libdvdread3 and libdvdnav4
And then try again with kaffine.

---

### Post by masonfoley on 2008-05-21
> **cor2y said:**
> Completely remove the libdvdcss2 package.
And follow the guide for adding the medibuntu repos for your specific version of ubuntu.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Update, then via synaptic or the terminal install libdvdcss2 libdvdread3 and libdvdnav4
And then try again with kaffine.

Booyah!

Caveat, I did not install libdvdread3 and libdvdnav4 as they were already there.  Would you suggest I remove/resinstall those as well?

Thanks a ton.  Wished I would have posted this question 4 hours ago.  ;)

---

### Post by cor2y on 2008-05-21
Couldn't hurt and then install the version thats tied to your version of kubuntu.
Just remember to bookmark that page for the next upgrade of ubuntu so you get the correct package for your version of (k)ubuntu.

---

### Post by masonfoley on 2008-05-24
Ok, now after a recent update from Adept (as prompted by the update icon in the task bar), I can no longer play DVDs.  What the heck is going on with this version of libdvdcss that my media players can't work with?

---

### Post by mc4man on 2008-05-24
the default behavior of kaffeine when it can't access your dvd device is to try to prompt you to install libdvdcss (even when it's installed)
run sudo lshw -C disk to see what your dvd drive is linked to and then check in kaffeine -> settings -> xine engine parameters -> media and see what the default dvd device is.

---

### Post by masonfoley on 2008-05-24
Thanks mc4man for the quick response.  In spite of re-running cor2y's suggested steps again (which before had worked), I am still unable to play DVDs.  Interestingly, when I uninstalled libdvdread and libdvdnav, it also removed my MythTV backend.  That was a bit of an "aha!" moment as now I suspect that the MythTV package is introducing a libdvdcss2 that isn't compatible for lack of a better term.  But let's put that on the back burner for now and I will post the information acquired from your suggestion.

Here is the output of **sudo lshw -C disk**. *I clipped only info relevant to the cd-rom drive.  Other references were to my hard drive and removeable hard drive so I didn't think it was relevant.  Let me know if you think it would be useful to post that too.*

```
 *-cdrom
       description: DVD writer
       product: DVD RW DW-D26A
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: JYS3
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
```

Now, navigating to the xine engine configuration dialog as you suggest, I see the following (as it pertains to "dvd"):

dvd.language = en
dvd.region = 1
dvd.device = /dev/dvd

So, looking at the output from the hardware list and the settings in the xine engine, it would appear this is correct?  If you agree, do you have any further suggestions for troubleshooting?

---

### Post by masonfoley on 2008-05-24
Thought this was interesting.  I took a closer look at the "OK" dialog that suggested I run a script, which I did.  Here's the output:

```
sudo /usr/share/doc/kaffeine/install-css.sh
--15:16:10--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
           => `/tmp/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to [www.dtek.chalmers.se|129.16.30.198|:80](www.dtek.chalmers.se|129.16.30.198|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178        87.41K/s

15:16:11 (87.24 KB/s) - `/tmp/libdvdcss.deb' saved [25178/25178]

dpkg - warning: downgrading libdvdcss2 from 1.2.9-2medibuntu4 to 1.2.5-1.
(Reading database ... 123236 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-2medibuntu4 (using /tmp/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

I thought it was interesting that the libdvdcss2 library was "downgraded".  In any event, DVD playback is still not functioning.

So, it would appear that there are various versions of libdvdcss2 floating about that do not play nicely with various media players.  Any suggestions?

---

### Post by masonfoley on 2008-05-24
More info.  Monitoring the console when running Kaffeine and attempting to play back a DVD, I noticed it is pointing to /dev/sda1.  Is this correct?  Shouldn't the reference be /dvd/dvd?

```
mason@myth:/var/log/apt$ kaffeine
mason@myth:/var/log/apt$ ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (376)
ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (376)
ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (376)
ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (376)
libdvdnav: Using dvdnav version 1.1.11.1 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/sda1 mounted on / for CSS authentication
libdvdread: Could not open /dev/sda1 with libdvdcss.
libdvdread: Can't open /dev/sda1 for reading
libdvdread: Device /dev/sda1 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/mason/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdnav: Using dvdnav version 1.1.11.1 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: vm: faild to open/read the DVD
```

---

### Post by mc4man on 2008-05-24
navigate to /etc/udev/rules.d and post the contents of 70-persistent-cd.rules
It's possible you have something related to this, or variation of (easily fixed)
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)

Edit; In your case look at and post /etc/fstab and ck. the properties of the dvd, dvdrw, cdrom links in /dev for the targets
once your done looking and comparing those 3 things (cd rules, fstab, links in /dev you'll probably see the solution, any doubts then post those files and we can get this squared up in a few minutes.

---

### Post by masonfoley on 2008-05-24
70-persistant-cd.rules

```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DVD_RW_DW-D26A (pci-0000:00:11.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
```

/etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=9b23fb0d-76e3-4910-88af-327e1075f3e1 / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=7be394c2-6cb8-4304-aded-4523bcd3a259 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdb1 /media/external ext2 rw
/dev/sdb1 /media/external ext3 nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
```

---

### Post by mc4man on 2008-05-25
everything looks right, did you ck. in /dev and right click on the dvd link -> properties -> target device and see if any of them are wrong. While in /dev see if a device scd1 exists 

edit: you didn't post fstab
i just pointed kaffeine to wrong device here and it's looking for /dev/dvd1 at /dev/sda6 
What version are you using 7.10 or 8.04

re edit; after getting near to same errors as you (wanting to install libdvdcss, looking to wrong device) _i just switched the device in settings to /dev/scd0 and it works fine._ (d. ck. that you do have libdvdcss2, use the medibuntu ver.)

 Ot.  haven't spent much time in kubuntu (8.04) but there seems to be odd behavior with autoplay and or r.click open wth when you have 2 dvd drives with both kaffeine and amarok - it seems the default device should be dynamically set to last device to call those apps which isn't happening

re re edit something changed in kubuntu since i did an install last week, going to start from fresh again and see, vlc works great from the r. click open with, even with 2 drives, _auto switches_ to device with mounted dvd (media/cdrom, media/cdrom1) 
see here [https://bugs.launchpad.net/ubuntu/+source/kaffeine/+bug/213274](https://bugs.launchpad.net/ubuntu/+source/kaffeine/+bug/213274)

---

### Post by mc4man on 2008-05-25
Last post was getting jumbled.
from a freah kubuntu install regarding kaffeine (no updates yet)
install libdcdcss2 - no playback
install vlc (with related libs) - no playback (vlc works great as mentioned above, no need to set either device)
install libxine-all-plugins  - no playback
switch default device to /dev/scd0 - playback with scd0 drive (none with 2nd drive unless default is manually switched)
disk is not auto mounted, must mount before playback (green light)

Note: in the updated install I just removed, (normal+some proposed) could not get green light 'mount', kaffeine would not play unless set to scd0 and opened from gui,  vlc would play (device specific)

---

### Post by stinger30au on 2008-05-25
i had this same dram this afternoon when i wanted to watch a dvd

i foloowed these steps for 8.04 and it works just fine now

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

hope this helps

---

### Post by miciurin on 2008-05-25
I had the same problem. After correctly adding medibuntu to your repositories and installing libdvdcss2 I opened Kaffeine, and under xine settings I set the device to dev/scd0. No more problems after that. If in doubt after mounting the DVD right click to properties and see the actual mount point of your DVD device.

---

### Post by masonfoley on 2008-05-25
I updated my fstab to the right text.

---

### Post by masonfoley on 2008-05-26
If I insert a DVD, shouldn't it mount?  (i.e. shouldn't I see an icon for it on the desktop)?  I'm not seeing this happen.  Is this a symptom of fstab, peresistent-cd.rules, etc) not configured properly?

---

### Post by masonfoley on 2008-05-26
Any other ideas?  Or is there something requested I post which I forgot to post?

---

### Post by mc4man on 2008-05-26
Are you getting an icon for dvd but no 'green light'
Based on what you posted everything is fine. (based on what I've seen of kubuntu anythings possible in terms of _un_useability)

---

### Post by masonfoley on 2008-05-26
I'm about at my wits end as far as Kubuntu goes.  For kicks, I decided to install 7.10, just to see if that would allow me to play DVDs.

So I installed 7.10  (check)
Added medibuntu repository entry (check)
Added medibuntu group key (check)
Installed in one step, libdvdnav, libdvdread, libdvdcss2  (check)

Play dvds?

Nope

So, continuing:  
sudo apt-get install ubuntu-restricted-extras  (check)

Not necessary but I rebooted anyway.  Put in Sweeny Todd DVD, launched Kaffeine.  Won't play the DVD.  Tells me I don't have the required plugins.

Then I install MPlayer, attempt to play the DVD, says it can't find /dev/dvd:1 or something like that.

I've checked the links in /dev, it's pointing to hdc0 which according to fstab, this is correct, that's my CD-Rom drive.

Seriously, am I that unlucky that I haven't dialed up the right combination to get this working?  Excuse me if I sound rude or biting the hand that feeds.  That's not it at all.  MC4Man, et. al., you all have been of great help even though a particular set of advice doesn't lead to the end goal, there is much to be gained by simply digging in and trying things out.

But one must understand the seeming countless number of users that have attempted to join the revolution, only to run into these inexplicable errors and we do our best to ignore the the self-elevated egos that pull out their trump cards and say, "Linux simply isn't for you, buy a Mac or install Windows."  That hasn't happened to me personally but I've seen plenty of people in my situation, trying to get some basic features of their system implemented, get dogged.

Again, baffling, simply baffling.  I've installed RedHat before, installed a Websphere server, managed a MySQL database, set-up countless php sites and have been a QA Engineer for over 10 years.  I've managed to setup Samba and successfully have CUPS manage our printer so that both Windows and Linxu can print to it.  I've setup MythTV (no easy feat), MythWeb to schedule recordings remotely, setup a LIRC configuration for my Snapstream remote, managed to overcome countless Grub hiccups...and I can't get two different Kubuntu distros to play DVDs?

---

### Post by mc4man on 2008-05-26
As I mentioned A bit back i did a fresh install of kubuntu, got dvd playback but in terms of kaffeine it still s....s. Now I've only used kubuntu for a few hours total but the idea that 'default' installed apps don't work right (if at all) is silly. So in any event while the fresh install has vlc working good (from the app menu or from open with) kaffeine was  only autoplaying from 1 (scd0) drive till I rebooted. Now it's back to the same poor behavior of only playing from app menu (with karreine set to /dev/scd0). The biggest problem I see is when you insert a dvd movie (dvd video disk last time I checked) it shows up as an unmounted dvd, ie. it's not seen for what it is and it doesn't automount. Now maybe there's a setting for that, who knows and to some extent who cares. I do know that the _last beta or rc did work_ somewhat ok.(couldn't deal with 2 dvd drives, but one was ok) The current release doesn't.
I really think if multimedia is a _very_important concern gutsy is the best. Otherwise you could install ubuntu hardy and spend your time enjoying your setup rather than this.
It would be great to hear from some kubuntu users that have perfect working setups (with 2 drives in particular) and how they managed to get kaffeine and amarok to autoplay or play and disks to automount blah, blah

edit : seeing that 7.10 gives you the hcdx for your drive (vs. scdx0 have you triedthe all generic ide boot parameter [http://ubuntuforums.org/showthread.php?t=767449&page=8](http://ubuntuforums.org/showthread.php?t=767449&page=8)  post 80

If you ck. out the bug report i linked before you'll see your not the only one.

---

### Post by masonfoley on 2008-05-26
I don't want to speak too soon, but through brute force methods, something I did worked.  I believe it was installing the xine-ffmpeg packages as suggested by [this thread]("http://ubuntuforums.org/showthread.php?t=462910&highlight=couldn%27t+find+demux").

I found that thread by searching on Kaffeine complaining about 'demux'.


After applying those items, Kaffeine and Ogle are playing DVDs (Ogle has a bit of interlace problem but that's something I'll deal with another time.)

But I didn't get to that step until I dealt [with this nonsense]("https://bugs.launchpad.net/ubuntu/+source/adept/+bug/54450").  I went for broke and divided the list into thirds, focusing on the kernel update first.  That seemed to do the trick although it bitched about qtc3 being updated so I answered the prompt "N" which means to keep the previous install.


If I find out exactly what made it work, I'll update this thread.

Again, can't thank you folks enough, shout out to MC4Man, for your persistence and commentary.

---

### Post by mc4man on 2008-05-26
Is this 7.10 or 8.04 your on now?

---

### Post by masonfoley on 2008-05-26
> **mc4man said:**
> Is this 7.10 or 8.04 your on now?

This would be 7.10 but I believe I have suffered a false-positive.

The DVD I threw into the player on the 7.10 side was National Geographic's "Human Footprint".  

So, I thought, what the heck, let me test my xine all-plugins theory.  I booted over to 8.04, the DVD was already in the drive so I proceeded to launch Human Footprint.

It played.

That just didn't make any sense so I then removed that DVD and put in Sweeny Todd.  Same behavior as before.  It complained about libdvdcss2.

I took Sweeny Todd back out and put Human Footprint back in, thinking maybe something is awry with the Auto-play feature.

The system accepted the DVD and prompted me with an open-dialog.  I cancelled out of that, right clicked on the DVD icon on the desktop and selected "Play with Kaffeine...".  

It played.

Maybe Human Footprint doesn't have encryption?

So I put in Prozac Nation.  It didn't appear to automount (no DVD icon on Desktop and no Open dialog) and it doesn't play.

So after all is said and done, I'm beginning to suspect that the version of libdvdcss2 does have issues.  The version I have is 1.2.9-2medibuntu4.

It does appear to be a false positive and it may very well boil down to encrypted versus non-encrypted DVDs (I've run into National Geographic DVDs that didn't have encryption before on the Windows side of the house).  Nothing definitive there and I can verify with tools that I have there.

So, I think I'm back to square one but perhaps armed with a better idea of what the problem is.  But I've been with this issue for over a week now attempting all of the steps that I have encountered as it relates to restricted packages, medibuntu, libdvdcss, etc. etc.  So, I'm not terribly certain that I'll be taking any steps forward any time soon.

---

### Post by mc4man on 2008-05-26
> So after all is said and done, I'm beginning to suspect that the version of libdvdcss2 does have issues. The version I have is 1.2.9-2medibuntu4. i'm sure your sick of the whole deal, you could try an eariler ver. [http://download.videolan.org/pub/libdvdcss/1.2.5/deb/](http://download.videolan.org/pub/libdvdcss/1.2.5/deb/)
i see it fail on unencrypted disks (prompting the codec install) also when kaffeine is approached from the wrong direction. It always works from the gui, not too likely from the open with (as long as you manually mount the disk)
You really should try vlc just to see (again disk must be mounted, will never autoplay but should work with open with)

Kaffeine in kubuntu 8.04 takes this approach in regards to dvd video disks
Well it sorta looks like a duck, sorta walks like a duck, let's throw some codecs at it and we'll see if it quacks like a duck.

---

### Post by masonfoley on 2008-05-26
> **mc4man said:**
> i'm sure your sick of the whole deal, you could try an eariler ver. [http://download.videolan.org/pub/libdvdcss/1.2.5/deb/](http://download.videolan.org/pub/libdvdcss/1.2.5/deb/)

Hmmmm...before I proceed with that, wanted to get someone's opinion on this error message upon opening the DEB file:

> Error:  Dependency is not satisfiable:  libdvdcss2

I remember from a previous experience in RedHat a couple of years ago that I should avoid "dependency hell" at all costs.  My tentativeness stems from the notion that once this gets on the system, all dependency checks going forward will be out of whack.

Yes?  No?

---

### Post by masonfoley on 2008-05-26
Upon further review, it wouldn't appear that I have any choice in the matter as the "Install" button in the DEB gui isn't enabled.  Perhaps for good reason.

I will add that I have had 1.2.5.? on the system previously.  Earlier in the thread, I had mentioned running a script,  /usr/share/doc/kaffeine/install-css.sh, and this installed  the following package:  ```
http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb
```

Perhaps not the same exact flavor since it's coming from a different location but in any event, it wouldn't appear that I can install the deb package you linked to.  Unless there is an alternative method to force it onto the system where the deb gui wouldn't allow it.  If so, please see my previous concern regarding the error message.

---

### Post by masonfoley on 2008-05-26
Ah nevermind, I had donwloaded the -dev version.  The regular version reported that a later version was installed, so I removed the medibuntu version of libdvdcss2 via Adept, then launched the correct debian package from the folder I downloaded it to  It "warned" me that a later version was available in a software channel and suggested I stick with that.  I ignored this message and installed it.

Still am not able to play DVDs.  Inserting the DVD does not "mount" the disc (as suggested by no open dialog and no DVD icon on the desktop).

---

### Post by masonfoley on 2008-05-26
> **mc4man said:**
> 

edit : seeing that 7.10 gives you the hcdx for your drive (vs. scdx0 have you triedthe all generic ide boot parameter [http://ubuntuforums.org/showthread.php?t=767449&page=8](http://ubuntuforums.org/showthread.php?t=767449&page=8)  post 80

I did try the all_generic_ide switch at the end of  my kernel line in menu.lst and confirmed in dmesg and syslog that it executed with that parameter.  

No noticeable difference that I can see, namely, DVDs are still not playing.

---

### Post by mc4man on 2008-05-27
Some how I was under impression your disks were showing up (unmounted but still showing up)
If you can't see the disk on the desktop or in dolphin - storage manager then i don't know, you can't playback what's not there. You'd have to fix it or do fresh install.
I did a fresh install with only 1 drive (2 drives was messing me up, is messed up)
update fully (no backports, did the proposed, shouldn't matter
Added medibuntu to source
installed libdvdcss2 from medibuntu
installed vlc (adds lib support - you can uninstall vlc right after if you want
installed libxine-all-plugins
_opened kaffeine, xine ... parameters changed dvd device to /dev/scd0  (or whatever is shown in fstab)_

_From the command line_ there are 5 commands that all work fine whether disk is mounted or not (some other possible commands send kaffeine into endless codecs installed loop or black screen)
_kaffeine dvd:///_ dev/cdrom (cdrom0,scd0) 0r media/cdrom (cdrom0) change any 0 to 1 if your scd1 (command should start with underlined)
[U]
From the r. click open with[/U] - umounted - opens kaffeine, clicking play dvd works fine. 
mounted  - opens movie, hangs or blank (2 titles tried, may be caused by empty VIDEO_TS.VOB)

_From gui_ - works fine mounted or umounted
_from the disk insert popup_ - no kaffeine initially,  after adding kaffeine in notifications kaffeine opens, click on dvd works fine.  

Obviously the most important thing is to set kaffeine to your dvd device.  (vs. /dev link or mountpoint)
edit
This was only on commercial disks, a backup on dvdr media never 'mounts' but plays back as above for unmounted. (for the most part, can't remember)

---

### Post by masonfoley on 2008-05-27
Yep.  When I insert a DVD that can't be read, it does not show up on the Desktop nor does it show up in the "Storage Media" perspective in Dolphin.

Is there some logging that would capture the system's attempt to read the DVD after it is inserted?

---

### Post by mc4man on 2008-05-28
> Is there some logging that would capture the system's attempt to read the DVD after it is inserted? if you haven't squared things away yet after inserting disk and drive settles down run
dmesg | tail
If you see something like
[ 4236.284598] Buffer I/O error on device sr1, logical block 405586
 there's hope, What you'd want to see is
[ 4284.036047] UDF-fs: Partition marked readonly; forcing readonly mount
[ 4284.154109] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume '300', timestamp 2007/05/03 02:35 (1f10)

---

### Post by masonfoley on 2008-05-28
> **mc4man said:**
> if you haven't squared things away yet after inserting disk and drive settles down run
dmesg | tail
If you see something like
[ 4236.284598] Buffer I/O error on device sr1, logical block 405586
 there's hope, What you'd want to see is
[ 4284.036047] UDF-fs: Partition marked readonly; forcing readonly mount
[ 4284.154109] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume '300', timestamp 2007/05/03 02:35 (1f10)

Hmmm...nothin'.  And I verified that the log is written to with the Read-Only mount message by putting in Human Footprint, which I believe is an unencrypted DVD but putting in Prozac Nation, simply nothing occurs.

---

### Post by wedesoft on 2008-05-28
Maybe deleting the directory $HOME/.dvdcss to force restoring the keys helps?

---

### Post by masonfoley on 2008-05-28
> mason@myth:~$ ls .dvdcss
CACHEDIR.TAG  HUMAN_FOOTPRINT-2008021812185600-2b36e4e9d7  INCONVENIENTTRUTH-2006101219004500-6acb11d3bf

This is what I currently have in there.  I deleted as you suggested.  Attempted to insert DVD that had not worked previously *Prozac Nation*, and nothing happens.  Interestingly, the .dvdcss directory is not recreated when inserting the DVD.  

So it would seem, it's not even getting to that point with these DVDs.

Putting the DVD that I know has mounted and played before National Geographic's *Human Footprint*, creates the /.dvdcss directory and creates what I would call a key file.

It just seems so odd that these DVDs won't even mount.  So, again, it's almost as if it isn't even getting to the point of accessing libdvdcss.  Something else is precluding these DVDs from loading.

Thanks for the suggestion though.  I wasn't even aware that this .dvdcss directory existed.  Now I do.  :)

Cheers

---

### Post by wedesoft on 2008-05-29
So you watched "An inconvenient truth"? :lolflag:

Maybe just try to put a softlink from */dev/scd0* (or wherever your DVD drive appears) to */dev/dvd*.

```
cd /dev
sudo ln -s scd0 dvd
```

---

### Post by masonfoley on 2008-06-04
This is bordering on the ridiculous...if it hasn't breached the edge.  :)

I have a new system...that's right, I am building a new media server from scratch.

To recap, in my previous system, DVDs wouldn't mount at all if they were encrypted.

Now, with the new system, the DVDs are mounting...but Kaffeine is throwing the silly, tired error that the DVD is encrypted.

To recap again, I have done the requisite usual stuff by installing the restricted package, including libdvdcss2 and libdvdnav4.

Here is the output from the console when attempting to play a "commercial" DVD:

> ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (376)
ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (376)
ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (376)
ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (376)
ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (376)
libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/sda1 mounted on / for CSS authentication
libdvdread: Could not open /dev/sda1 with libdvdcss.
libdvdread: Can't open /dev/sda1 for reading
libdvdread: Device /dev/sda1 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/mason/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: Devil_On_Horseback
libdvdnav: DVD Serial Number: ca61d1ee
libdvdnav: DVD Title (Alternative): Devil_On_Horseback
libdvdnav: Unable to find map file '/home/mason/.dvdnav/Devil_On_Horseback.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000137
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000019e
libdvdread: Elapsed time 7
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000410d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001cd63d
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x001cd63d)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001cd641
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x001cd641)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001cdf16
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001cdf1a
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 8
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

Any ideas?

---

### Post by mc4man on 2008-06-04
How many dvd drives in this system?
Did you set a region on the drive?

---

### Post by masonfoley on 2008-06-04
> **mc4man said:**
> How many dvd drives in this system?
Did you set a region on the drive?

Howdy my MC4MAN!  :)

There is one DVD drive.

Based on a post I saw somewhere out there, I downloaded and installed and ran "regionset" at the console.  I set it to "1".  I don't know, however, if the region wasn't set at all.  Perhaps it wasn't, it was a new DVD drive, purchased OEM style from NewEgg.

Anyhow, it confirmed as successfully set to Region 1.

Kaffeine still pukes on it.

So, I installed VLC.  Damn thing works.

So...in conclusion (crosses fingsers)...I'm thinking Kaffeine has some work to do.  I seem to recall that you prefer VLC.  Perhaps this is an example as to why.  Installing VLC from Adept brings quite a few things along with it.  Perhaps something in that list of components allowed for the DVD to play.  Then again, Kaffeine still doesn't like my DVDs...VLC does.

Sure would like to know why Kaffeine still refuses to play the DVDs but I'm confident now that my hardware and libdvdcss2 / libdvdnav4 components do not appear to be the problem.  There is at least one media player out there that is cooperating.  Additionally, K3b successfully opened the disc and I was able to proceed with a copy operation with that app.  Again, pointing the accusative finger at Kaffeine.

Dunno what to say except that I can't say I care much if I'm able to play DVDs at this point whereas with my older system, I wasn't.  I'll simply accept it.  :)

Cheers

---

### Post by mc4man on 2008-06-05
> libdvdread: Attempting to use device /dev/sda1 mounted on / for CSS authentication
Probably because kaffeine is looking to wrong device
 if your inclined run ```
sudo lshw -C disk
``` and we'll see what is what
With one drive it should be scd0

---

### Post by masonfoley on 2008-06-05
Perhaps...in the back of my mind, I was thinking the same thing based on your earlier posts.  Here is the output:

>  *-disk
       description: ATA Disk
       product: ST3250410AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 6RY39B8Z
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00019416
  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW SH-S203B
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: SB03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom


---

### Post by mc4man on 2008-06-05
That's all good! I got rid of my kubuntu install but there is probably somewhere in kaffeine to set default device. _Set it to /dev/scd0 _!!
(refer to post 30 for other possibilities, cli, ect.)

It's in settings -> xine engine parameters -> media

---

### Post by Manelpt on 2008-06-07
> **stinger30au said:**
> i had this same dram this afternoon when i wanted to watch a dvd

i foloowed these steps for 8.04 and it works just fine now

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

hope this helps

This one helped me. It was driving me crazy, thanks!

---

### Post by quadCoreBrainWithNoMemory on 2008-06-25
> **masonfoley said:**
> 
However, when I attempt to play DVDs in Kaffeine, Kaffeine proceeds to attempt to install a codec.  Here is the message:


I have sometimes had kaffeine complain about missing codecs when they were installed.
Have you had other media players fail to play dvds too?  Perhaps try using vlc, xine, mplayer, or totem.

Kaffeine is a bit dumb in dealing with iso images, if that's what you're doing.  Instead of:
kaffeine /my/media/files/movie.iso
I have to do:
kaffeine dvd://my/media/files/movie.iso
and to play a dvd in the drive I type
kaffeine dvd://

Kaffeine's auto-installer for codecs has come up on me with the first command line where it doesn't on the second or third.  I have no idea why.  Perhaps this should be filed as a bug.

Your mileage may vary.

---

### Post by MoeNeigh on 2008-06-28
I am using Kubuntu 8.04, and kaffeine stopped playing my DVDs also. However, in my case, despite kaffeine asking to install libdvdcss2, which was already installed, I finally got the DVD to play.

I could not select "play DVD with Kaffeine" when the DVD was first mounted.
I could not right click and select "play DVD with Kaffeine".

HOWEVER,

If I opened Dolphin file management, and went to Storage Media, and right clicked on the DVD icon there, I selected "open with". No options were given, but I was able to type in the word "kaffeine" as the application I wanted the DVD to be opened with. Voilà! It played. Right now, this is the only way I can get DVDs to play with Kaffeine. I must manually type in "kaffeine" as the application to open the DVD with.

Any ideas why this works this way? Anyway, I'm happy that it DOES work! Hope this helps someone even though it's not a very technical solution.

Oh, also, Adept keeps telling me libdvdcss2 is upgradable, but it never gives me the option to "request install".

---

### Post by Monster_user on 2008-06-29
Funny. That only half works for me. 

To add my issues to this thread, Can anybody link me to the page that explains why Kaffeine keeps giving me "Source Cannot be Read" errors?

It works fine when I run "sudo kaffeine".

---

### Post by mc4man on 2008-06-30
I haven't used kaffeine/Kubuntu for a month but at least back then the most important thing was to set the default device in xine parameters to what is shown in fstab, usually /dev/scd0 or /dev/scd1.
All the possible ways I saw to run kaffeine and results are in post 30. Maybe it's the same now, maybe not.

---

### Post by Craftycorner on 2009-08-12
I have had the same problem with css. sh. being dodgy.  I installed a program called Ogle to bite that problem.  Ogle is new so there are few bugs, but you can get the DVD to at least play with it.  It's good for testing home made DVD's I make using DeVeDe.

Now if I could just get past DeVeDe's lame menues, I will be a happy burner.
:guitar:

---

