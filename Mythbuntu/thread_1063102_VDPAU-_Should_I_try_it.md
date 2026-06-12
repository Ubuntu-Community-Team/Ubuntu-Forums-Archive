---
title: "VDPAU- Should I try it?"
date: 2009-02-07
forum: Mythbuntu
---

### Post by itlarson on 2009-02-07
I have read about the new VDPAU support, and am wondering if I should try it.  [http://zacgarrett.com/software/installing-mplayer-vdpau/index.html](http://zacgarrett.com/software/installing-mplayer-vdpau/index.html) gives a fairly involved way to do this.  [http://www.avenard.org/files/mythtv-vdpau/](http://www.avenard.org/files/mythtv-vdpau/) says I can simply install a new repository, then upgrade the system.  Have other mythbuntu users tried either of these?  I am interested in peoples experiences and opinions.

---

### Post by ian dobson on 2009-02-07
Hi,

I'm interested in the answers as well.

Regards
Ian Dobson

---

### Post by gr8nash on 2009-02-07
Yeah me too, i would love to upgrade my mythbuntu to try out vdapu

---

### Post by itlarson on 2009-02-07
If I did try this and it didn't work, how would I recover?

---

### Post by nicoloks on 2009-02-07
If you have a card supporting VDPAU and you wish to watch 1080p conent, I would say it is a must. I'm building a AMD X2 5600+ (dual core 2.9Ghz) HTPC for a mate with a Asus M3N78-VM motherboard which has the Nvidia 8200 IGP. Watching a high quality 1080p/DTS bluray rip used to consume 90%+ of the CPU and result in servere video stutter and audio sync issues. After installing the 180.22 drivers and compiling the VDPAU enabled Mplayer CPU usage dropped to around 15%, and the related stutter and sync issues disappeared. Some people say that if you have a fast enough CPU then VDPAU doesn't matter, however I haven't found that to always be the case.   

If you follow the first guide at the top of this thread, then there is nothing to recover as you run the VDPAU enabled Mplayer in parrallel with the standard version.

---

### Post by ian dobson on 2009-02-08
> **itlarson said:**
> If I did try this and it didn't work, how would I recover?

As always backup before you do any major changes.

My frontend boots from a small (8Gb) CF card in a CF-SATA adapter. Before I make any major changes I boot up in rescue mode, go to the command prompt and then copy the Boot CF to a backup CF card (Plugged into an USB card reader). The command I use to copy the entire CF is:-

dd if=/dev/sda of=/dev/sdb bs=4k

A backup takes about 15-20minutes, but thats alot less than reinstalling everything if an update goes wrong :D

Regards
Ian Dobson

---

### Post by itlarson on 2009-02-08
The flash memory thing sounds complicated.  I recall hearing about a way to back up the mythtv database-  which would probably be enough.  
   Also I would be interested hearing which method people used for installing vduap and what problems they ran into.

---

### Post by ian dobson on 2009-02-08
Hi,

I imagine that I'll try out the [http://www.avenard.org/files/mythtv-vdpau/](http://www.avenard.org/files/mythtv-vdpau/) depository sometime this week. I just need to steal a vdpau compatible vga card from another PC and install it in the frontend.

Regards
Ian Dobson

---

### Post by ian dobson on 2009-02-13
Hi,

Finally got a 9400gt from the childrens box :)

I'll be trying it out this evening/tomorrow. Is it really as easy as adding the [http://www.avenard.org/files/mythtv-vdpau/](http://www.avenard.org/files/mythtv-vdpau/) repositries and doing an apt-get update/upgrade?

I'll post my findings here in the next few days.

Regards
Ian Dobson

---

### Post by phismith on 2009-02-13
I'm also curiosu to know the results. I'm lookign at building a mythbuntu box around the gigabyte GA-E7AUM-DS2H.

This makes it sound like all you'd have to do is install the latest nvida driver and add the repositries!

---

### Post by nickrout on 2009-02-13
> **phismith said:**
> I'm also curiosu to know the results. I'm lookign at building a mythbuntu box around the gigabyte GA-E7AUM-DS2H.

This makes it sound like all you'd have to do is install the latest nvida driver and add the repositries!

The results have been good, but you'll get more info on the mythtv-user mailing list, or mythtvnz. Archives are at [http://www.gossamer-threads.com/lists/mythtv](http://www.gossamer-threads.com/lists/mythtv)

---

### Post by ian dobson on 2009-02-15
Hi All,

1) Backedup my dediated backend to another CF card.
2) Booted from it and enabled the [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/ repo.
3) Did a apt-get update/upgrade
4) Enabled the nvidia driver in the ubuntu "Hardware drivers tool"
5) Rebooted and started watching a recording, saw about 20% CPU load
6) Went into the mythfrontend playback profiles screen and changed all profiles to use vdpau.
7) Rebooted and watched the same recording again and saw about 5-6% CPU load.

Note: Both recordings watched are SD. I'll try HD sometime today.

The only problem I'm having is some tearing in the video, I think I know what the solution is.

The upgrade isn't just an apt update/upgrade and everythings OK. Unless your willing to spend sometime debugging/setting up vdpau I'd recommend waiting for an official release.

Oh and do a full backup of the system before you start playing. It took me three attempts before I got a working/stable system.

EDIT: Just tried HD (BBC HD/Torchwood) and the CPU load is 5-10%. Without vdpau it was about 80-95%. VDPAU makes a huge difference for me. 

My frontend is:
Intel Core2DUO E5200@2.5GHz
2Gb DDR2 Memory
1Gb network connection to my Mythtv backend
8Gb CF-SATA adapter
NVidia 9400GT graphic card with 512Mb ram 

Regards
Ian Dobson

---

### Post by nickrout on 2009-02-15
Read this post from Yeechang Lee and make sure you have everything set right.

[http://www.gossamer-threads.com/lists/mythtv/users/370435#370435](http://www.gossamer-threads.com/lists/mythtv/users/370435#370435)

---

### Post by jyavenard on 2009-02-16
> **ian dobson said:**
> Hi All,

1) Backedup my dediated backend to another CF card.
2) Booted from it and enabled the [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/ repo.
3) Did a apt-get update/upgrade
4) Enabled the nvidia driver in the ubuntu "Hardware drivers tool"
5) Rebooted and started watching a recording, saw about 20% CPU load
6) Went into the mythfrontend playback profiles screen and changed all profiles to use vdpau.
7) Rebooted and watched the same recording again and saw about 5-6% CPU load.

Note: Both recordings watched are SD. I'll try HD sometime today.

The only problem I'm having is some tearing in the video, I think I know what the solution is.

The upgrade isn't just an apt update/upgrade and everythings OK. Unless your willing to spend sometime debugging/setting up vdpau I'd recommend waiting for an official release.

Oh and do a full backup of the system before you start playing. It took me three attempts before I got a working/stable system.

EDIT: Just tried HD (BBC HD/Torchwood) and the CPU load is 5-10%. Without vdpau it was about 80-95%. VDPAU makes a huge difference for me. 


I posted a quick FAQ answering most of the questions asked here:
[http://www.avenard.org/files/mythtv-vdpau/](http://www.avenard.org/files/mythtv-vdpau/)

Q: Video is tearing
A: Tearing when composite is enabled is the norm (checkout the driver readme for more details). Add to your xorg.conf:
Section "Extensions"
    Option         "Composite" "Disable"
EndSection

Q: When I start playing a Video/LiveTV I get a blank screen:
A: To prevent blank screens when running without composite, try running with:
USE_VDPAU_COLORKEY=1 mythfrontend.
Amended Answer: Use patch > 19970, it fixes many bugs related to colorkey

Q: I get stuttering  every few seconds with errors like "NVP: Video is 3.12705 frames behind audio (too slow), dropping frame to catch up."
A: Check your settings: In General: make sure "Aggressive sound card buffering" is unckecked
In TV -> Playback "Extra audio buffering" is checked.

Q: I installed your latest patch, and it makes my machine crash
A: You must run nvidia drivers >= 180.25 with the latest patches

Now, for the people asking if adding my repository is enough to get VDPAU working, then the answer is yes.
My packages are made from the mythbuntu original packages ; as such they are 100% compatible.

Warning, do not activate the mythbuntu weekly build repository. The weekly repository is updated every week, and due to the nature of SVN ; each week the version number will increase ; even if there has been no changes in Mythtv 0.21-fixes.
If you activate the mythbuntu weekly build, it is likely that at some stage the weekly repository will update mythtv and will remove the VDPAU mods.

To use VDPAU, all you need to do is add to your /etc/apt/sources.list:
deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/
deb-src [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/

You can also enable the testing repository which is updated more often ..
deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) testing/
deb-src [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) testing/

This repository also includes the Nvidia drivers. One thing to know, the nvidia drivers are also 100% compatible with the nvidia drivers found in 9.04.. However, since 180.11 the structure of the package has changed. The vdpau libraries are now found in a separate package (libvdpau-180).
As such, you can't upgrade easily from 180.11 to 180.22 or later.

You must de-install any previous nvidia drivers (<180.22) then install the new one. If you attempt a simple upgrade, you will get an error about vdpau.

BTW, you will never get an "official" 0.21 release with VDPAU

> The upgrade isn't just an apt update/upgrade and everythings OK. Unless your willing to spend sometime debugging/setting up vdpau 

I disagree, it is precisely that: it's an update/upgrade and everything is okay.
There are no modification required to the backend or the database. You can always revert back to the official build of mythtv.

And the only setup required is creating a VDPAU video profile in the TV Settings -> Playback

Installing my mythtv packages with VDPAU will not mess your system in any way .. It doesn't touch the structure of the database *ever*.

I can't imagine why it would have taken you 3 attempts to get it working.

If it doesn't work for you; uninstall mythtv, disable my repository. Re-install mythtv.
That is it.

Cheers
Jean-Yves

---

### Post by ian dobson on 2009-02-16
Hi Jean-Yves,

Your the guy that backported the vdpau code to 0.21. 

Firstly I'd like to say thankyou very much for all the work you put in at getting vdpau working in 0.21.

The biggest problem for me to get the NVidia drivers running correctly. My first attempt went wrong as I didn't remove the old NVidia drivers before installing the new ones which left me low resolution mode in X and alot of errors about conflicting versions.

My second attempt should have worked as I deinstalled the old drivers and installed the 180. but they wern't activated in the Hardware Drivers programm (Where you can chose which version of the NVidia drivers to use).

The third attempt worked. 

I actually gave up each time quite quickly as I have a "dd" backup of the frontend harddisk which only takes afew minutes to load and I got myself into such a mess that I started again from new rather than trying to sortout the mess.

All I can say now, is thankyou very much. Less than 10% CPU load when playing HD (1080p h264) video is wonderful. I can now use cpufreqd to slowdown the CPU to 1200MHz (Core2Duo) without any side effects.

Regards
Ian Dobson

---

### Post by Lido on 2009-02-17
Can I use this upgrade if I'm just running Ubuntu 8.10 with MythTV installed (i.e. I'm not running Mythbuntu)?

---

### Post by jyavenard on 2009-02-17
> **ian dobson said:**
> 
My second attempt should have worked as I deinstalled the old drivers and installed the 180. but they wern't activated in the Hardware Drivers programm (Where you can chose which version of the NVidia drivers to use).


You don't need to activate the hardware drivers program if you manually install the 180.x drivers ...

it should automatically be recognised.

the only manual change you need to do is modify xorg.conf so it uses the nvidia driver

---

### Post by jyavenard on 2009-02-17
> **Lido said:**
> Can I use this upgrade if I'm just running Ubuntu 8.10 with MythTV installed (i.e. I'm not running Mythbuntu)?

Yes you can ...

---

### Post by ian dobson on 2009-02-17
> **jyavenard said:**
> You don't need to activate the hardware drivers program if you manually install the 180.x drivers ...

it should automatically be recognised.

the only manual change you need to do is modify xorg.conf so it uses the nvidia driver

I installed the 180.29? drivers from your repo. But it works now and I'm a happy man :p

Regards
Ian Dobson

---

### Post by xinix on 2009-02-18
If I had a VDPAU compatible card it would be great.  I installed from the Avenard repo and it works great, even the nvidia driver.  This version runs really well for me and it may just be my imagination, but, I've been happier with the playback even without the VDPAU enabled in the playback settings.  Enabling it crashes myth, like I said before I don't have a compatible card.  Oddly the mobile version of the card is listed in the compatible list.  If it doesn't work I'd make a backup of our database (actually, Id do this first), then uninstall myth, and reinstall it from the standard repo.  This worked for me when I downgraded from this version temporarily.  I'm back to using it again.  one thing I can think of is that this repo is for 8.10, 8.4 doesn't have the right version of some things to meet the required dependencies.

---

### Post by jyavenard on 2009-02-18
> **xinix said:**
> If I had a VDPAU compatible card it would be great.  I installed from the Avenard repo and it works great, even the nvidia driver.  This version runs really well for me and it may just be my imagination, but, I've been happier with the playback even without the VDPAU enabled in the playback settings.  Enabling it crashes myth, like I said before I don't have a compatible card.  Oddly the mobile version of the card is listed in the compatible list.  If it doesn't work I'd make a backup of our database (actually, Id do this first), then uninstall myth, and reinstall it from the standard repo.  This worked for me when I downgraded from this version temporarily.  I'm back to using it again.  one thing I can think of is that this repo is for 8.10, 8.4 doesn't have the right version of some things to meet the required dependencies.

The mythtv package contains a lot of fixes ; including OpenGL fixes which can be very useful even if you do not use VDPAU.

If you do set a video profile with VDPAU and your card isn't VDPAU compatible ; it shouldn't crash. It will default to ffmpeg/Xv instead

To use the new opengl mods; set opengl or opengl2 as renderer and try the new hardware accelerated deinterlacer ; I had great result with Yadif HW,2X for SD and Kernel HW,2X / or MotionGreedy for HD.

Yes, this repo is for 8.10...

---

### Post by covert on 2009-02-19
I did this upgrade and it was relatively painless except for a issue I had with the nVidia drivers not loading properly. Loading nvida-new from apt-get then installing the new nvida drivers again solved the problem. I would recommend only upgrading mythtv and not doing a full upgrade. The new mysql also caused me issues with the new config file being loaded and only accepting local connections.

Very impressed with the results of the VDAPU.

---

### Post by jyavenard on 2009-02-19
> **covert said:**
> I did this upgrade and it was relatively painless except for a issue I had with the nVidia drivers not loading properly. Loading nvida-new from apt-get then installing the new nvida drivers again solved the problem. I would recommend only upgrading mythtv and not doing a full upgrade. The new mysql also caused me issues with the new config file being loaded and only accepting local connections.

Very impressed with the results of the VDAPU.

VDPAU won't work well with the stock nvidia drivers that comes with Ubuntu

> The new mysql also caused me issues with the new config file being loaded and only accepting local connections.

??? there is no change to the database whatsoever with my package ; and for the backend/database it's just the mythbuntu package compiled ...
So any issues you have there you would have had it with the standard mythbuntu package

---

### Post by Monsieur Gonzalez on 2009-02-19
Just wanted to say thanks to JYA for making the patches and repository available. It's working even better than before, many small improvements, and of course, with VDPAU reducing CPU use.

8.10 + mythtv + Nvidia 8400GS.

---

### Post by covert on 2009-02-19
> **jyavenard said:**
> VDPAU won't work well with the stock nvidia drivers that comes with Ubuntu


Should of been more clear. I had to load (install) the ubuntu nvidia driver then loaded (installed) the new nvidia driver from nvidia site a second time because the first attempt to install the nvidia drivers from the nvidia site failed the first time with API version error messaged in dmesg.

> **jyavenard said:**
> 
??? there is no change to the database whatsoever with my package ; and for the backend/database it's just the mythbuntu package compiled ...
So any issues you have there you would have had it with the standard mythbuntu package

When I did a apt-get upgrade a new MySQL config file was loaded with settings for allow localhost only.


Thanks for your work on the upgrades.

---

### Post by mathog on 2009-02-22
> **Monsieur Gonzalez said:**
> Just wanted to say thanks to JYA for making the patches and repository available. It's working even better than before, many small improvements, and of course, with VDPAU reducing CPU use.

8.10 + mythtv + Nvidia 8400GS.

Same config and graphics card (256MB model for me) and same good result.  Excellent work.  Much praise to jyavenard.

With vdpau enabled the pauses I used to see when using the program guide while TV was running went away.  On the other hand, so did the live TV that used to be visible at the same time the guide was up.  

The only glitch I have seen so far concerns PIP, where sometimes it comes up with H = 2W (stretched vertically), instead of H = W.  Oddly the stretched one uses much less CPU time than the rectangular one, which tends to push to 50-60% CPU, where regular TV (one stream) is <=10%.  Also the front end hung up for a longish time once when trying to switch PIP streams.

VDPAU + mythtv is definitely a big win.

THANKS!

---

### Post by itlarson on 2009-02-22
Boy- this thread really has legs!  I am still interested in trying VDPAU, but I will need things to be to be a bit more step-by-step before I am confident enough to try it.  So here are my questions:

-first, I need a good way to recover if this fails, and am wondering if I can adapt Ian Dobson's system to my hardware by simply backing up my root directory to a usb flash drive.  Would something like this work:
dd if=/dev/sda1 of=/dev/sdb bs=4k -to back up.  (or of=/dev/sdb1 ?)
dd if=/dev/sdb1 of=/dev/sda1 bs=4k -to restore. (or if=/dev/sdb  ?)
(what does the bs=4k do?)
sda1 is my root directory, and sdb would be the flash drive. 
     I assume I would boot from a rescue disk to restore, but would I have to do this when making the backup, so the drive wouldn't be active?

-next, do I remove nvidia drivers first?  Do I just run sudo apt-get remove nvidia-* ?  If I do this from X will things work untill I reboot?

-then to install the repository do I (per Jean-Yves Avenard's site) just run:
echo "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/" | sudo tee /etc/apt/sources.list.d/avenard.list   ?

-and then is just running updates enough to install VDPAU?  Will I need to re-install nvidia drivers? Is that just apt-get install nvidia-something, or will I be able to run the mythbuntu setup tool?

-once the drivers are installed, is enabling them simply a matter of going into the Mythtv playback settings or profiles and choosing VDPAU as the playback engine?

I am hoping you experts can answerer some of these questions, and perhaps it will act as a guide for us less expert users.

---

### Post by nickrout on 2009-02-22
> **itlarson said:**
> Boy- this thread really has legs!  I am still interested in trying VDPAU, but I will need things to be to be a bit more step-by-step before I am confident enough to try it.  So here are my questions:

-first, I need a good way to recover if this fails, and am wondering if I can adapt Ian Dobson's system to my hardware by simply backing up my root directory to a usb flash drive.  Would something like this work:
dd if=/dev/sda1 of=/dev/sdb bs=4k -to back up.  (or of=/dev/sdb1 ?)
dd if=/dev/sdb1 of=/dev/sda1 bs=4k -to restore. (or if=/dev/sdb  ?)
(what does the bs=4k do?)
sda1 is my root directory, and sdb would be the flash drive. 
     I assume I would boot from a rescue disk to restore, but would I have to do this when making the backup, so the drive wouldn't be active?

-next, do I remove nvidia drivers first?  Do I just run sudo apt-get remove nvidia-* ?  If I do this from X will things work untill I reboot?

no

> 

-then to install the repository do I (per Jean-Yves Avenard's site) just run:
echo "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/" | sudo tee /etc/apt/sources.list.d/avenard.list   ?

-and then is just running updates enough to install VDPAU?  Will I need to re-install nvidia drivers? Is that just apt-get install nvidia-something, or will I be able to run the mythbuntu setup tool?

Yes.

> 

-once the drivers are installed, is enabling them simply a matter of going into the Mythtv playback settings or profiles and choosing VDPAU as the playback engine?



you need to set up vdpau as your playback method in setup. 

[http://mythtv.org/wiki/Playback_profiles](http://mythtv.org/wiki/Playback_profiles)

---

### Post by itlarson on 2009-02-22
Thanks for the help.  Probably I should post the backup question in the general forums.  So here's how it would work, as I currently understand it:

-install the repository as per JYA.
-do a system update.
-re-install the nvidia drivers from mythbuntu setup(?)
-choose vdpau in mythtv's setup menu.

Is it really that simple?

---

### Post by nickrout on 2009-02-22
JYA's repository has the latest nvidia drivers so your third step should not be necessary.

Also make sure you disable "composite" in xorg.conf

```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection

```

This post has some good information.

[http://www.gossamer-threads.com/lists/mythtv/users/370435#370435]("http://www.gossamer-threads.com/lists/mythtv/users/370435#370435")

---

### Post by itlarson on 2009-02-22
Thanks- Think I got it!

---

### Post by mathog on 2009-02-23
> **itlarson said:**
> Thanks for the help.  Probably I should post the backup question in the general forums.  So here's how it would work, as I currently understand it:

-install the repository as per JYA.
-do a system update.
-re-install the nvidia drivers from mythbuntu setup(?)
-choose vdpau in mythtv's setup menu.

Is it really that simple?

Pretty much.

Before you do anything else:

cd ~
. /etc/mythtv/mysql.txt
mysqldump -u$DBUserName -p$DBPassword $DBName -c >mythtv_backup.sql
cp /etc/X11/xorg.conf ./xorg.conf.save

With any luck you will never need to use the mythtv_backup, you will need a safe copy of xorg.conf.  One should remain in /etc/X11 but it will end up with a name like "xorg.conf.fglrx-12" and you may not know which was the last good one. 

On my system after I added the repository and did:

sudo apt-get update
sudo apt-get upgrade

it did NOT pick up the new nvidia driver.  To do that it was necessary to do a manual:

sudo apt-get install nvidia-glx-180
sudo apt-get install nvidia-180-modaliases

After that 

mythbuntu control center -> restricted drivers -> select 180 (should now be on the list), quit.

Reboot to single user (root)

sudo cp -f xorg.conf.save /etc/X11/xorg.conf
#test it
startx 
# should start up X11 as before the upgrade
# use ctrl-alt-backspace to shutdown X11
exit
(select resume)
#system should come up normally, starting X11 like before the upgrade
#myth should also start up as it did before.

Then all you have to do is in mythfrontend (already running)

Utilities/Setup -> Setup -> TV settings -> playback -> step through to Playback Profiles (3/9).  Edit the profiles, change the decoder to "Nvidia VDPAU acceleration", that should also change Video Renderer and OSD Renderer to "vdpau".  And voila, much (much) lower CPU usage.

---

### Post by Lido on 2009-02-24
I'm using 8.10 with MythTV installed (not mythbuntu). I followed the instructions to get the patched version running and it seemed to work for the most part. I had some trouble getting the 180 nvidia drivers installed but in the end I think I did get them. The trouble is that I'm not using mythbuntu control center so I'm not sure which nvidia drivers I'm using. I used synaptic to get them, here's the window that shows all the nvidia files I installed:

[[IMG]http://img27.imageshack.us/img27/9089/nvidiar.th.jpg[/IMG]](http://img27.imageshack.us/my.php?image=nvidiar.jpg)

When I look at the Hardware Devices control panel, it no longer has the two nvidia 17x drivers listed, it just has "nvidia" with a green dot and no version numbers.

VPDAU is visible in my playback profiles setup page but when I select it and then try to watch either live tv or any recording I get an error. The preview videos play in the recordings menu, but when I select one to watch, I get one of two errors. I'm assuming this onboard video card is compatible with vdpau, but I'm not sure.

```
$lspci
...
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200 (rev a2)

```

One other issue is that even without vdpau selected I get a black screen unless I use the composite disabled flag in xorg.conf. Then compiz fusion effects don't work. I can live without them, but is there a way I can have both?

So to boil it down, I need some help getting vdpau to work. Any suggestions?

---

### Post by TMcC on 2009-02-24
Way I got it to work was by using Jean-Yves Avenard's patches.

Steps I followed were:

*Download Mythbuntu 8.10
*Install... but DO NOT select the 177 drivers when you go through the Mythbuntu control centre
*After installation, add the repositories shown by: [http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)
*Do a "sudo apt-get update"
*Do a "sudo apt-get install nvidia-glx-180" 
*Reboot, and check that you're using the nvidia driver by running "nvidia-settings".
*Do a "sudo aptitude safe-upgrade"
*Grab mplayer_vdpau.sh from [http://www.knoppmythwiki.org/index.php?page=HardwareAcceleratedVideo](http://www.knoppmythwiki.org/index.php?page=HardwareAcceleratedVideo)
*Stick in /usr/local/bin and alter myth to use that script instead of mplayer
*Try using myth to play a 1080p video, checking cpu usage.

Note, you may need to alter the amount of shared memory assigned to your 8200. 128MB isn't enough, 256 might be.

And don't use compiz...

Also check post #14 of this thread.

---

### Post by Lido on 2009-02-25
Thanks. That helped. It's working fairly well now. Some occasional stuttering, but no more tearing and the cpu load is way down.

---

### Post by geoffp on 2009-02-26
Thanks, Jean-Yves, for the backports and the repos.  Great stuff!

The only major problem I have consistently now is that changing from one channel to another on the same tuner using the live TV guide will produce two errors and crap out to the main menu.  "Failed to reinit video", I think.

VDPAU is impressive.  I'm able to get 1080i MPEG2 / Temporal 2x to play back perfectly with my lowly integrated 8200.  I did have to give it 512MB of RAM to play with in BIOS, since it would error out with just 128.  I didn't try 256.

---

### Post by jdeslip on 2009-02-26
geoffp,  I have the exact same problem and reported it to jean-yves on the nvidia forum.  I don't think he can reproduce the problem though :(

See comment 143 (and subsequent conversation) at this thead: [http://www.nvnews.net/vbulletin/showthread.php?t=123865&page=10](http://www.nvnews.net/vbulletin/showthread.php?t=123865&page=10)

---

### Post by joshoekstra on 2009-04-14
I like to try just mplayer with vdpau enabled, could I use these packages  for that as well?
I got the the nvidia 180.11 driver installed from the 'normal' repo.

---

### Post by jyavenard on 2009-04-14
you will want to upgrade your nvidia drivers if you want to try VdPAU

current stable version is 180.44

If you are upgrading from 180.11 to 180.44 ; you must uninstall the nvidia drivers first before you can install 180.44

doing a simple upgrade will fail..

---

### Post by joshoekstra on 2009-04-14
Just did, went to the 185 drivers and got update packages for mplayer and made a config in my homedir for mplayer to start trying with the VDPAU-assisted codecs first and ith works pretty much ok. Some overlay problem with after restarting mplayer seems to be over and significantly dropped CPU-hogging. I like it :)
Later on I'll take the plunge to using your repo or waiting for .22 of mythtv, but sofar I'm happy.

---

### Post by utar on 2009-04-15
Hi


I have just started using jyavenard's vdpau build of Myth and I'm impressed.  My CPU usage with 1920x1080 video is now under 10%.

I think however I have found a bug.  Basically I want to use the standard software decoding for everything except HD video (as the deinterlacing seems to be much better with software).  So I modified the "high quality" playback filter to use vdpau with 1920x1080 video, however this doesn't work and myth always uses the software decoding.  Not sure if this is because when I start watching TV Myth (correctly) starts playback with software and does not recheck the playback rules when I change to a HD channel.

Has anyone else experienced this, and have any suggestions?

---

### Post by utar on 2009-04-15
Just for the record, there isn't a bug.  It seems that BBC-HD transmits in 1440x1080 and as such I had my playback rule wrong as this was set for 1980x1080.


Utar

---

### Post by mshannon on 2009-04-24
I'm trying to update to 180 as per avenard's instructions, when I try to remove lthe old versions with packet manager I get the following error.

E: /var/cache/apt/archives/nvidia-180-libvdpau_180.44-0ubuntu1_amd64.deb: trying to overwrite `/usr/lib/libvdpau.so.1', which is also in package nvidia-glx-177

It also tells me I have a broken package "libmyth-0.21-0" if I try and re-install this I get the same error again. 

Any clues as to my next move?

---

### Post by jyavenard on 2009-04-24
The error is rather clear.

Uninstall nvidia-glx-177

once you're done, install nvidia-glx-180 and mythtv.

You can't install both at the same time

BTW: Latest nvidia drivers are 180.51

---

### Post by m0bilitee on 2009-05-03
Let me chime in here with my attempts at this.

Wow, it's amazing. I'm using an ASUS 9300 based board with a Dual Core Pentium e5200, and I went from spikes near 100% to running around 5-7% CPU utilization in MythTV.  I'm doing HDMI output to 1080i (older TV), and this works great.  Note my video card is allocated 256 megs, if anyone has questions about that.  Occasionally I have video hiccups (quick freeze and then all the missed frames get played back at lightning speed), but considering the level this stuff is at in development, it's awesome.  I'm on 8.10 64 bit.

In mplayer, 1080p mkv container files would frequently drift out of sync badly, and with the vpdau enabled mplayer and the latest everything (as of May 2nd), it's just amazing.  Very very impressed.

Thanks for all your efforts JYA!  

- m0b

---

### Post by Familienvater on 2009-05-19
Jean-Yves,

HD playback is just great using your repository in Mythbuntu 9.04, thank you very much.

I have only one minor issue.

Before, mplayer disabled the Gnome Screensaver when playing a movie. Now ater installing the mplayer from your repository this is not longer the case. After 10 minutes the screen gets blank.

It does not matter if I replace or keep the mplayer.conf during installation.

Do you (or anybody else) have an idea, what goes wrong?

Thank you!

Regards,

Familienvater

---

### Post by utar on 2009-05-19
I had this problem and I fixed it by adding a command line option to mplayer.  From memory I think it was "-stop-xscreensaver", however I'm not in front of my Myth box at the moment.  I'll check later.



Utar

---

### Post by Familienvater on 2009-05-19
Thank you for your quick answer, utar!

But actually this doesn't seem to work for me. I added -stop-xscreensaver to the command line, but this is ignored by mplayer. I also tried to add 

```

stop-xscreensaver = "yes"

```

to mplayer.conf. This does not disable the Screensaver. What's worse, Mplayer even crashes when playing some videos (I don't know what's so special about these files)

What I do not understand: How is the screensaver disabled in the standard configuration? There is neither an entry in mplayer.conf nor a command line option!

Regards,

Familienvater

---

### Post by nickrout on 2009-05-19
from man mplayer:

> &#8722;heartbeat&#8722;cmd
	

Command that is executed every 30 seconds during playback via system() - i.e. using the shell.

NOTE: MPlayer uses this command without any checking, it is your responsibility to ensure it does not cause security problems (e.g. make sure to use full paths if "." is in your path like on Windows). It also only works when playing video (i.e. not with &#8722;novideo but works with &#8722;vo null).

This can be "misused" to disable screensavers that do not support the proper X API (also see &#8722;stop&#8722;xscreensaver). If you think this is too complicated, ask the author of the screensaver program to support the proper X APIs.

EXAMPLE for xscreensaver: mplayer &#8722;heartbeat&#8722;cmd "xscreensaver&#8722;command &#8722;deactivate" file

EXAMPLE for GNOME screensaver: mplayer &#8722;heartbeat&#8722;cmd "gnome&#8722;screensaver&#8722;command &#8722;p" file

---

### Post by jyavenard on 2009-05-19
> **Familienvater said:**
> 
Before, mplayer disabled the Gnome Screensaver when playing a movie. Now ater installing the mplayer from your repository this is not longer the case. After 10 minutes the screen gets blank.

It does not matter if I replace or keep the mplayer.conf during installation.

Do you (or anybody else) have an idea, what goes wrong?


I just had a look.

The original mplayer found in ubuntu comes with extra code for handling the gnome screen-saver.

The one I build is straight from the SVN code.

I added the patches found in debian/patches which is the usual location for all patches ; but the original ubuntu package directly patched the source code. So I had missed that.

I will rework on my mplayer package to include the gnome screen saver support.

I never noticed because the screen saver on my box, which is exclusively used for mythtv, is disabled by default

Edit/Update: I re-added the old KDE screensaver support... I'm rebuilding packages, they will be in the release directory as I've tested them to be working as intended...

Jean-Yves

---

### Post by nickrout on 2009-05-19
That would be great Jean-Yves. I never could figure out why my vdpau machine worked different to the other frontend!

---

### Post by jyavenard on 2009-05-20
Hi

Allright, I ported the gnome-screensaver support and updated mplayer to revision #29317

I'm uploading the packages in the testing repository.

Something to note:
the old mplayer 1.0rc2 had native support for the KDE screensaver and the ubuntu package add supports for the gnome screensaver.

The latest version in trunk has support for neither of them... I added support for gnome.

That means there's no support for the kde one.

I will be looking at adding support for the KDE screensaver next.

---

### Post by nickrout on 2009-05-20
I believe the mplayer devs got sick of gnome and kde not using the X API's for disabling screensaver, and ripped out the hacks for gnome and kde. The comments in the man page that I quoted above bear this out. Whether they should be patched back in, or whether you should use the -heartbeat-cmd, or whether you should be hassling the gnome/kde devs to get it right is a moot point I guess.

---

### Post by jyavenard on 2009-05-20
I uploaded the mplayer changes with gnome and KDE screen saver support.

Did you get the chance to try them? do they work as expected?

---

### Post by birdie101 on 2009-05-23
May I please ask for help?

I am running mythbuntu 8.10 and am having trouble upgrading my system.  What is the correct process?  My understanding of it is:

1. uninstall old nvidia driver (sudo apt-get remove nvidia-glx-new)
2. Add Jean-Yves' repository, then update and upgrade.
3. Install new nvidia driver (sudo apt-get install nvidia-glx-180)
4. Install "modaliases" (sudo apt-get install nvidia-180-modaliases)
5. Reboot and the new driver should be loaded and the upgrade will install the VPDAU patches and VPDAU will be available as an option in Mythtv.

When I follow this process though, upon rebooting I get a message saying that I am loading low-graphics mode, and I can't seem to avoid that message even after reinstalling the nvidia driver.

Can anyone please point out what I am doing wrong?

Thanks,
Luke

---

### Post by epi 1:10,000 on 2009-05-23
Sorry for my noobness but Did you run 

sudo nvidia-xconfig --no-composite

in the console?

---

### Post by jyavenard on 2009-05-23
> **birdie101 said:**
> May I please ask for help?

I am running mythbuntu 8.10 and am having trouble upgrading my system.  What is the correct process?  My understanding of it is:

1. uninstall old nvidia driver (sudo apt-get remove nvidia-glx-new)
2. Add Jean-Yves' repository, then update and upgrade.
3. Install new nvidia driver (sudo apt-get install nvidia-glx-180)
4. Install "modaliases" (sudo apt-get install nvidia-180-modaliases)
5. Reboot and the new driver should be loaded and the upgrade will install the VPDAU patches and VPDAU will be available as an option in Mythtv.

When I follow this process though, upon rebooting I get a message saying that I am loading low-graphics mode, and I can't seem to avoid that message even after reinstalling the nvidia driver.

Can anyone please point out what I am doing wrong?

Thanks,
Luke

What do the X11 logs say ? (/var/log/Xorg.0.log)

---

### Post by AlecJ on 2009-05-23
> **birdie101 said:**
> May I please ask for help?

I am running mythbuntu 8.10 and am having trouble upgrading my system.  What is the correct process?  My understanding of it is:

1. uninstall old nvidia driver (sudo apt-get remove nvidia-glx-new)
2. Add Jean-Yves' repository, then update and upgrade.
3. Install new nvidia driver (sudo apt-get install nvidia-glx-180)
4. Install "modaliases" (sudo apt-get install nvidia-180-modaliases)
5. Reboot and the new driver should be loaded and the upgrade will install the VPDAU patches and VPDAU will be available as an option in Mythtv.

When I follow this process though, upon rebooting I get a message saying that I am loading low-graphics mode, and I can't seem to avoid that message even after reinstalling the nvidia driver.

Can anyone please point out what I am doing wrong?

Thanks,
Luke
I had this look here
[http://ubuntuforums.org/showthread.php?t=1142976](http://ubuntuforums.org/showthread.php?t=1142976)

---

### Post by jyavenard on 2009-05-23
> **AlecJ said:**
> I had this look here
[http://ubuntuforums.org/showthread.php?t=1142976](http://ubuntuforums.org/showthread.php?t=1142976)

Very dirty way of doing things, especially as the package install the exact same files...

Re-run nvidia-xconfig or make sure xorg.conf correctly use the nvidia drivers is all you need to worry about.

No need to run the nvidia installer

---

### Post by AboveTheLogic on 2009-05-23
I've had issues updating the nvidia driver in any way other than using the built-in package manager with mythbuntu.

i've done it through the package manager a few times with good luck.

---

### Post by utar on 2009-06-10
I've been using jya's ubuntu 8.10 repository for a while and have been very happy.

However recently something seems to be going funny with the dependencies.  Earlier in the week there was an Myth update that wouldn't fully install without me removing nvidia-180-libvdpau and installing nvidia-185-libvdpau.  Anyway after some trouble I got 185 install and everything was good.

Anyway today I notice that there is another myth update which now wants to uninstall 185 and install 180.  I would prefer to stick with 185 now I have it installed.

Is this just me missing something and can anyone give me any suggestions?


Thanks.


Utar


[Edit: just noticed on Jya's website that he has reverted back to 180 so please ignore the above!]

---

### Post by bcg30506 on 2009-06-11
I've noticed this too.  I'm not doing this update as I'm happy and working with 185.  I'd like to hear why they are downgrading it.

---

### Post by nickrout on 2009-06-11
read the mailing list archive:

[http://www.gossamer-threads.com/lists/mythtv/users/383877](http://www.gossamer-threads.com/lists/mythtv/users/383877)

---

### Post by dano1 on 2009-06-16
having problems with 185. using update manager rolled back to 180 drivers, unfortunately went ahead with a partial upgrade using updated manager and am stuck with 158 drivers. I've tried jya's method using synaptic but this removes myth and mplayer to no avail.

 Been working on this for days trying to roll back drivers without success. anyone got any tips, tricks, etcfor rolling back the drivers i.e. synaptic or other i may be missing ?

tia, danny

---

### Post by jbman on 2009-06-16
Have you tried remove ALL nvidia, kernel and all then reinstall?

---

### Post by dano1 on 2009-06-16
using synaptic wants to remove dependencies, mythtv mplayer, gecko.

don't where to go from here.

---

### Post by jyavenard on 2009-06-16
> **dano1 said:**
> having problems with 185. using update manager rolled back to 180 drivers, unfortunately went ahead with a partial upgrade using updated manager and am stuck with 158 drivers. I've tried jya's method using synaptic but this removes myth and mplayer to no avail.

 Been working on this for days trying to roll back drivers without success. anyone got any tips, tricks, etcfor rolling back the drivers i.e. synaptic or other i may be missing ?

tia, danny

Disable the testing repository.

In the testing repository you have newer packages linked against 185.xx ; so it won't let you go down to 180.xx

---

### Post by dano1 on 2009-06-16
already tried that, same thing happens. Can not downgrade drivers without removing myth. cannot upgrade myth either, installed versions shows as latest version. Will try a previous backup and see if i can downgrade from that.

Any more help is greatly appreciated. Thanks jya,

danny

---

### Post by nickrout on 2009-06-16
Whats wrong with removing myth? You can reinstall it again after the downgrade. All your settings will still be there.

---

### Post by dano1 on 2009-06-18
rolled back to 180.60 drivers, and system is stable. unfortunately have better visual with 185 drivers, except for lockups :(. any word on upgraded 185 drivers? Wish they were "stable" 

tia, danny

---

### Post by grytpype on 2009-06-19
The -vdpau builds have been very crashy for me, mythfrontend has been crashing when trying to play certain recordings.  I reverted to -fixes.

---

### Post by utar on 2009-06-20
I installed the latest vdpau build today and now seem to have a problem with lcdproc.  Basically 2 "screens" are being opended on my lcd and the display switches between the mythtv screen and a blank one every few seconds.

If I kill mythlcdserver then the switching stops.

Is anyone else seeing this, or is it just me?



Utar

---

### Post by epi 1:10,000 on 2009-06-23
Does anyone else have a problem w/ the most recent stable release breaking their HVR-2250?  For some reason my backend is not able to determine the type of tuner and information in the frontend list the tuners as unavailable.

---

### Post by jyavenard on 2009-06-29
> **utar said:**
> I installed the latest vdpau build today and now seem to have a problem with lcdproc.  Basically 2 "screens" are being opended on my lcd and the display switches between the mythtv screen and a blank one every few seconds.

If I kill mythlcdserver then the switching stops.

Is anyone else seeing this, or is it just me?


An update to lcdproc was done in 0.21-fixes SVN #20697
[http://svn.mythtv.org/trac/changeset/20697](http://svn.mythtv.org/trac/changeset/20697)

The VDPAU built doesn't modify anything there, so any issues seen must come from upstream unfortunately

---

### Post by jyavenard on 2009-06-29
> **epi 1:10,000 said:**
> Does anyone else have a problem w/ the most recent stable release breaking their HVR-2250?  For some reason my backend is not able to determine the type of tuner and information in the frontend list the tuners as unavailable.

The VDPAU built stay very far from anything touching mythbackend ..

Is your 2250 seen by the system properly ?
You can always try one of the latest mythbuntu weekly built and see if it's any better.

If it works there, but not with my build, I'd be happy to investigate

---

### Post by jyavenard on 2009-06-29
> **grytpype said:**
> The -vdpau builds have been very crashy for me, mythfrontend has been crashing when trying to play certain recordings.  I reverted to -fixes.

What do you mean by "crashing" ? an actual crash, or the frontend exits with an error (that's not a crash).

Try to switch to a video playback profile not using VDPAU and see if it plays any better.
if it does, but not with VDPAU I'd like to get a sample of your recording if possible to have a look at it.

Any issues seen in the backport is likely in trunk, so any fixes made here would be for the better good :P

---

### Post by utar on 2009-06-30
> **jyavenard said:**
> An update to lcdproc was done in 0.21-fixes SVN #20697
[http://svn.mythtv.org/trac/changeset/20697](http://svn.mythtv.org/trac/changeset/20697)

The VDPAU built doesn't modify anything there, so any issues seen must come from upstream unfortunately

Thanks for the reply.

This has been driving me mad!  But just for the record in case anyone else has the same problem I found a solution here:

[http://www.gossamer-threads.com/lists/mythtv/users/384973](http://www.gossamer-threads.com/lists/mythtv/users/384973)

Basically adding "ServerScreen=no" to LCDd.conf fixes the problem.



Utar

---

### Post by epi 1:10,000 on 2009-06-30
Problem solved:
 
On the last symantic update it mush have updated the kernel and messed up the HVR-2250 drivers.
 
Fix:
 
Delete all the previous HVR-2250 install folders then download and reinstall the driver. (LowSky's install tutorial worked)

---

### Post by uncle hammy on 2009-07-13
OK, I tried doing this yesterday, and ended up with a horror show on my hands.  I am running Mythbuntu 9.04 which currently uses the 180.44 NVidia drivers.  THe steps I followed were....

1.  Deactivated the NVidia Drivers
2.  Added the vdpau repository release and testing
3.  Disabled weekly builds
3.  update / upgrade...here's where I think my torubles began, because it said it could only do a partial upgrade

After all this, I never did get any updates to the nvidia drivers.  I also couldn't re-activate the ubuntu nvidia drivers, kept getting an error about "held broken packages".  I downloaded the 185 drivers from NVidia and managed to install them manually, however the playback was horrible (with and without vdpau enabled) and my CPU usage was holding around 90% (with and without vdpau enabled), compared to the normal 55% with the CPU++ profile.  Entirley frustrated and dejected :), ended up doing a fresh install of the system...this is just a frontend, so it's relatively painless.

So now, I have a nice clean machine with all updates and the most current weekly build on it and the standard 180.44 drivers from ubuntu, and ready to try again.  My plan this time is....

1. Disable weekly builds
2. add vdpau repository release ONLY this time
3. update / upgrade

Now, other than actually creating a vdpau playback profile, is there anything else I need to do?  I am not planning on uninstalling or deactivating the NVidia drivers this time...is this required if I am already running the 180.x series of drivers?  Will the update / upgrade automatically update the 180.44 drivers to the 180.60 drivers?

---

### Post by jyavenard on 2009-07-13
> **uncle hammy said:**
> OK, I tried doing this yesterday, and ended up with a horror show on my hands.  I am running Mythbuntu 9.04 which currently uses the 180.44 NVidia drivers.  THe steps I followed were....

1.  Deactivated the NVidia Drivers
2.  Added the vdpau repository release and testing


Wrong steps.

testing repository uses drivers 185.xx ; which IMHO aren't usable despite being tagged as official stable by nvidia.

only activate [release]

There was no need to de-activate the nvidia drivers if you were running ubuntu 9.04.

Uninstalling the nvidia drivers was only required on 8.04 when you had 180.11 drivers.

> 
3.  Disabled weekly builds
3.  update / upgrade...here's where I think my torubles began, because it said it could only do a partial upgrade


After all this, I never did get any updates to the nvidia drivers.  I also couldn't re-activate the ubuntu nvidia drivers, kept getting an error about "held broken packages".  I downloaded the 185 drivers from NVidia and managed to install them manually, however the playback was horrible.  Ended up doing a fresh install of the system...this is just a frontend, so it's relatively painless.

So now, I am have a nice clean machine with the most current weekly build on it and the standard 180.44 drivers from ubuntu, and ready to try again.  My plan this time is....

1. Disable weekly builds
2. add vdpau repository release ONLY this time
3. update / upgrade

Now, other than actually creating a vdpau playback profile, is there anything else I need to do?  I am not planning on uninstalling or deactivating the NVidia drivers this time...is this required if I am already running the 180.x series of drivers?  Will the update / upgrade automatically update the 180.44 drivers to the 180.60 drivers?

This last plan is the good one.

Adding a VDPAU playback profile is all you need to do. And let it upgrade to 180.60, reboot or restart X after doing so...

lots of fixes in 180.60.

---

### Post by uncle hammy on 2009-07-13
Thanks for the reply...and FAST at that!  I will try it out tonight when I get home.

---

### Post by tombongo on 2009-07-13
First off, I would like to thank jyavenard for the ubuntu repositories.  It has made this build doable for me.  Mostly everything seems to be working great so far in my MythTV frontend.  I am still testing.

Zotac IONITX-C-U
1GB RAM
4GB USB flash drive
HDMI with audio
Mythbuntu 8.10

The one problem that I do know of is related to the nvidia-settings dialog.  I made my normal adjustments to gamma and saturation from that dialog.  These adjustments carry over to the MythTV menus, but playback seems to ignore them.  I also have a Zotac GeForce 8200 frontend and playback respects the settings.  The systems are similar except that I am not using VDPAU acceleration on the 8200.  I am not sure what to do.  Any suggestions?

---

### Post by uncle hammy on 2009-07-13
OK, this time it went well!  I don't seem to have any ill effects of using vdpau (stuttering with or without the OSD, etc), and my CPU usage has gone froma steady 55% to 3%.  

one thing...

With the new builds, the preview screen of the Program Guide doesn't display anything.  I happen to use the MePo theme, which displays the channel logos when the guide is viewed  when not watching something or the live preview if viewed while watching something.  With the new builds, it always displays channel logos only, regardless.  I checked other themes, and there simply is no preview window.  It appears that calling the guide while in "viewing mode" is loading the same guide that gets displayed in "Manage Recordings".

Other than that, I am very impressed.  Nice work!

---

### Post by uncle hammy on 2009-07-13
I am discovering one more thing.  There appears to be some instability with LiveTV.  I have had several instances where the frontend exits to the desktop when trying to change channels, and one instance where LiveTV locked up completely unresponsive (couldn't even ssh in) requiring a hard shutdown.

---

### Post by frigginacky on 2009-07-19
I'm having a bit of trouble with VDPAU.  Here's what I've done so far:
1. make sure my card is VDPAU-compatible (onboard 8200)
2. add jyavenard's repos (release only), update & upgrade
3. create a vdpau profile in mythtv
4. disable composite in xorg.conf
If I understand what I've read in this thread correctly, this should be all I need to do to experience the magic of VDPAU.  Problem is, it's not working. Playback is jerky, and CPU usage is around 60-90%. Am I missing something?

---

### Post by jyavenard on 2009-07-19
> **uncle hammy said:**
> I am discovering one more thing.  There appears to be some instability with LiveTV.  I have had several instances where the frontend exits to the desktop when trying to change channels, and one instance where LiveTV locked up completely unresponsive (couldn't even ssh in) requiring a hard shutdown.

Using 185.18.14 drivers by any chance?
it's typically what occurs when using VDPAU on my mythtv frontend.
180.60 has proven to be much more reliable

---

### Post by jyavenard on 2009-07-19
> **frigginacky said:**
> I'm having a bit of trouble with VDPAU.  Here's what I've done so far:
1. make sure my card is VDPAU-compatible (onboard 8200)
2. add jyavenard's repos (release only), update & upgrade
3. create a vdpau profile in mythtv
4. disable composite in xorg.conf
If I understand what I've read in this thread correctly, this should be all I need to do to experience the magic of VDPAU.  Problem is, it's not working. Playback is jerky, and CPU usage is around 60-90%. Am I missing something?

If your CPU is around 60-90% , you're certainly not using VDPAU

The 8200 is very low end, and it won't allow you to use most of the nice vdpau deinterlacers. Bob 2X seems to be one reported to work almost reliably with a 8200.

In any case, you'll have to provide a log to see what's going on.
Start mythfrontend with:
mythfrontend.real -v playback
and post back the results.

---

### Post by frigginacky on 2009-07-19
> **jyavenard said:**
> If your CPU is around 60-90% , you're certainly not using VDPAU

The 8200 is very low end, and it won't allow you to use most of the nice vdpau deinterlacers. Bob 2X seems to be one reported to work almost reliably with a 8200.

In any case, you'll have to provide a log to see what's going on.
Start mythfrontend with:
mythfrontend.real -v playback
and post back the results.

Thanks for the fast reply! Here's the output of that command (I watched a few seconds of OTA SDTV before exiting):

```
2009-07-19 11:04:02.901 Using runtime prefix = /usr
2009-07-19 11:04:03.439 XScreenSaver support enabled
2009-07-19 11:04:03.439 DPMS is disabled.
2009-07-19 11:04:03.440 Empty LocalHostName.
2009-07-19 11:04:03.440 Using localhost value of FrigTPC
2009-07-19 11:04:03.454 New DB connection, total: 1
2009-07-19 11:04:03.469 Connected to database 'mythconverg' at host: localhost
2009-07-19 11:04:03.472 Closing DB connection named 'DBManager0'
2009-07-19 11:04:03.474 Primary screen 0.
2009-07-19 11:04:03.474 Connected to database 'mythconverg' at host: localhost
2009-07-19 11:04:03.476 Running in a window
2009-07-19 11:04:03.476 Using screen 0, 1920x1032 at 0,24
2009-07-19 11:04:03.514 user: 1000 effective user: 1000 before privileged thread
2009-07-19 11:04:03.515 user: 1000 effective user: 1000 run_priv_thread
2009-07-19 11:04:03.515 user: 1000 effective user: 1000 after privileged thread
2009-07-19 11:04:03.517 New DB connection, total: 2
2009-07-19 11:04:03.518 Connected to database 'mythconverg' at host: localhost
2009-07-19 11:04:03.520 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-07-19 11:04:03.520 Enabled verbose msgs:  important general playback
2009-07-19 11:04:04.235 max_width: 1920 max_height: 1080
2009-07-19 11:04:04.338 No theme dir: /home/frigginacky/.mythtv/themes/Mythbuntu-8.04-wide
2009-07-19 11:04:04.340 Primary screen 0.
2009-07-19 11:04:04.340 Running in a window
2009-07-19 11:04:04.340 Using screen 0, 1920x1032 at 0,24
2009-07-19 11:04:04.341 No theme dir: /home/frigginacky/.mythtv/themes/Mythbuntu-8.04-wide
2009-07-19 11:04:04.342 Switching to wide mode (Mythbuntu-8.04-wide)
2009-07-19 11:04:04.384 Using the Qt painter
2009-07-19 11:04:04.385 JoystickMenuClient Error: Joystick disabled - Failed to read /home/frigginacky/.mythtv/joystickmenurc
2009-07-19 11:04:04.386 lirc_init failed for mythtv, see preceding messages
2009-07-19 11:04:06.933 Specified base font 'medium' does not exist for font clock
2009-07-19 11:04:06.933 Specified base font 'medium' does not exist for font small
2009-07-19 11:04:06.934 Specified base font 'medium' does not exist for font medium
2009-07-19 11:04:06.934 Specified base font 'medium' does not exist for font large
2009-07-19 11:04:06.934 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04-wide/base.xml
2009-07-19 11:04:06.994 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-07-19 11:04:07.015 Registering Internal as a media playback plugin.
2009-07-19 11:04:07.063 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-07-19 11:04:07.095 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-07-19 11:04:07.125 No theme dir: /home/frigginacky/.mythtv/themes/Mythbuntu-8.04-wide
2009-07-19 11:04:20.330 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-07-19 11:04:20.332 Using protocol version 40
2009-07-19 11:04:20.358 TV: Attempting to change from None to WatchingLiveTV
2009-07-19 11:04:20.359 Using protocol version 40
2009-07-19 11:04:21.451 LiveTVChain(live-FrigTPC-2009-07-19T11:04:20): ReloadAll(): Added new recording
2009-07-19 11:04:21.461 TV: StartRecorder(): took 1 ms to start recorder.
2009-07-19 11:04:21.480 New DB connection, total: 3
2009-07-19 11:04:21.481 Connected to database 'mythconverg' at host: localhost
2009-07-19 11:04:21.506 detectInterlace(Ignore Scan, Interlaced Scan, 25, 576) ->Interlaced Scan
2009-07-19 11:04:21.510 NVP: Disabling Audio, params(-1,2,44100)
2009-07-19 11:04:21.643 VDPAU: Version 0
2009-07-19 11:04:21.644 VDPAU: Information Unknown
2009-07-19 11:04:22.151 VideoOutput: Allowed renderers: directfb,xv-blit,xshm,opengl,vdpau,xlib
2009-07-19 11:04:22.151 VideoOutput: Allowed renderers (filt: dummy): xlib,xshm,directfb,xv-blit,opengl
2009-07-19 11:04:22.154 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubobdeint,none) filt()
2009-07-19 11:04:22.154 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-07-19 11:04:22.154 VDP: LoadBestPreferences(2048x2048, 0)
2009-07-19 11:04:22.155 VDP: LoadBestPreferences(2048x2048, 60)
2009-07-19 11:04:22.155 VDP: LoadBestPreferences(720x576, 60)
2009-07-19 11:04:22.155 VideoOutput: Trying video renderer: xv-blit
2009-07-19 11:04:22.156 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubobdeint,none) filt()
2009-07-19 11:04:22.156 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-07-19 11:04:22.156 VDP: LoadBestPreferences(2048x2048, 0)
2009-07-19 11:04:22.156 VDP: LoadBestPreferences(2048x2048, 60)
2009-07-19 11:04:22.182 VideoOutputXv: ctor
2009-07-19 11:04:22.215 XOff: 0, YOff: 0
2009-07-19 11:04:22.216 VDP: LoadBestPreferences(720x576, 60)
2009-07-19 11:04:22.216 Display Rect  left: 0, top: 0, width: 1920, height: 1032, aspect: 1.33333
2009-07-19 11:04:22.216 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-07-19 11:04:22.218 VideoOutputXv: Pixel dimensions: Screen 1920x1032, window 1920x1032
2009-07-19 11:04:22.220 VideoOutputXv: Estimated display dimensions: 488x274 mm  Aspect: 1.78102
2009-07-19 11:04:22.220 VideoOutputXv: Estimated window dimensions: 488x274 mm  Aspect: 1.78102
2009-07-19 11:04:22.396 VideoOutputXv: InitSetupBuffers() render: vdpau, allowed: xv-blit,xshm,opengl,vdpau,xlib
2009-07-19 11:04:22.557 Created data @0x21eac20->0x2282a22
2009-07-19 11:04:22.557 Created data @0x2282a70->0x231a872
2009-07-19 11:04:22.557 Created data @0x231a8c0->0x23b26c2
2009-07-19 11:04:22.557 Created data @0x23b2710->0x244a512
2009-07-19 11:04:22.558 Created data @0x244a560->0x24e2362
2009-07-19 11:04:22.558 Created data @0x24e23b0->0x257a1b2
2009-07-19 11:04:22.558 Created data @0x257a200->0x2612002
2009-07-19 11:04:22.558 Created data @0x2612050->0x26a9e52
2009-07-19 11:04:22.558 Created data @0x26a9ea0->0x2741ca2
2009-07-19 11:04:22.558 Created data @0x2741cf0->0x27d9af2
2009-07-19 11:04:22.558 Created data @0x27d9b40->0x2871942
2009-07-19 11:04:22.558 Created data @0x2871990->0x2909792
2009-07-19 11:04:22.558 Created data @0x29097e0->0x29a15e2
2009-07-19 11:04:22.559 Created data @0x29a1630->0x2a39432
2009-07-19 11:04:22.559 Created data @0x2a39480->0x2ad1282
2009-07-19 11:04:22.559 Created data @0x2ad12d0->0x2b690d2
2009-07-19 11:04:22.559 Created data @0x2b69120->0x2c00f22
2009-07-19 11:04:22.589 VideoOutputXv: Created VDPAU context (software decode)
2009-07-19 11:04:22.589 VDP: SetVideoRenderer(vdpau)
2009-07-19 11:04:22.589 VDP: SetVideoRender(vdpau) == GetVideoRenderer()
2009-07-19 11:04:22.591 VDPAU: Created OSD (1920x1032)
2009-07-19 11:04:22.591 VideoOutputXv: VDPAU Colorkey: 0x20202 (depth 24)
2009-07-19 11:04:22.591 Display Rect  left: 240, top: 0, width: 1440, height: 1032, aspect: 1.77778
2009-07-19 11:04:22.591 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-07-19 11:04:22.593 Over/underscan. V: 0, H: 0
2009-07-19 11:04:22.593 Display Rect  left: 240, top: 0, width: 1440, height: 1032, aspect: 1.77778
2009-07-19 11:04:22.594 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-07-19 11:04:22.594 VDP: LoadBestPreferences(720x576, 25)
2009-07-19 11:04:22.595 NVP: LoadFilters(''..) -> 0
2009-07-19 11:04:22.597 OSD Theme Dimensions W: 640 H: 480
2009-07-19 11:04:23.121 NVP: ClearAfterSeek(1)
2009-07-19 11:04:23.121 VideoOutputXv: ClearAfterSeek()
2009-07-19 11:04:23.121 VideoOutputXv: DiscardFrames(0)
2009-07-19 11:04:23.121 TV: StartPlayer(): took 1612 ms to start player.
2009-07-19 11:04:23.121 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA
2009-07-19 11:04:23.122 TV: Changing from None to WatchingLiveTV
2009-07-19 11:04:23.122 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA -- done
2009-07-19 11:04:23.122 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-07-19 11:04:23.124 Realtime priority would require SUID as root.
2009-07-19 11:04:23.127 rate: 25 speed: 1 skip: 1 = interval 40000
2009-07-19 11:04:23.146 VDP: GetFilteredDeint() : vdpau -> 'vdpaubobdeint'
2009-07-19 11:04:23.248 nVidiaVideoSync: VBlank ioctl did not work, unimplemented in this driver?
2009-07-19 11:04:23.248 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2009-07-19 11:04:23.248 OpenGLVideoSync()
2009-07-19 11:04:23.253 OpenGLVideoSync: x,y -> 956, 540
2009-07-19 11:04:23.300 Using OpenGLVideoSync
2009-07-19 11:04:23.300 Set video sync frame interval to 40000
2009-07-19 11:04:23.306 Using audio as timebase
2009-07-19 11:04:23.306 Video timing method: SGI OpenGL
2009-07-19 11:04:23.306 Refresh rate: 16666, frame interval: 40000
2009-07-19 11:04:23.363 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-07-19 11:04:23.398 LiveTVChain(live-FrigTPC-2009-07-19T11:04:20): ReloadAll(): Added new recording
2009-07-19 11:04:23.400 LiveTVChain(live-FrigTPC-2009-07-19T11:04:20): SwitchTo(1)
2009-07-19 11:04:23.400 LiveTVChain(live-FrigTPC-2009-07-19T11:04:20): Entry@1: '2261_20090719110422'
2009-07-19 11:04:23.400 JumpToProgram(void)
2009-07-19 11:04:23.413 RingBuf(/htpc/recordings/2261_20090719110420.mpg): OpenFile(/htpc/recordings/2261_20090719110422.mpg, 12)
2009-07-19 11:04:23.499 RingBuf(/htpc/recordings/2261_20090719110422.mpg): CalcReadAheadThresh(6500 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-07-19 11:04:23.523 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAA
2009-07-19 11:04:23.733 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-07-19 11:04:23.756 NVP: Waiting for prebuffer..  1 AAAAAAAAAAAAAAAAA
2009-07-19 11:04:23.985 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-07-19 11:04:24.006 NVP: Waiting for prebuffer..  2 AAAAAAAAAAAAAAAAA
2009-07-19 11:04:24.213 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-07-19 11:04:24.239 NVP: Waiting for prebuffer..  3 AAAAAAAAAAAAAAAAA
2009-07-19 11:04:24.447 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-07-19 11:04:24.457 NVP: Waiting for prebuffer..  4 AAAAAAAAAAAAAAAAA
2009-07-19 11:04:24.663 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-07-19 11:04:24.673 NVP: Waiting for prebuffer..  5 AAAAAAAAAAAAAAAAA
2009-07-19 11:04:24.891 AFD: Stream #0, has id 0x49 codec id MPEG2VIDEO, type Video, bitrate 65000000 at 0x0x7f08880f44d0
2009-07-19 11:04:24.893 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubobdeint,none) filt()
2009-07-19 11:04:24.893 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-07-19 11:04:24.893 VDP: LoadBestPreferences(2048x2048, 0)
2009-07-19 11:04:24.893 VDP: LoadBestPreferences(2048x2048, 60)
2009-07-19 11:04:24.893 VDP: LoadBestPreferences(1920x1080, 60)
2009-07-19 11:04:24.896 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-07-19 11:04:25.055 VDPAU: Using 4 output surfaces (max 4)
2009-07-19 11:04:25.128 NVP: Waiting for prebuffer..  6 AAAAAAAAAAAAAAAAA
2009-07-19 11:04:25.283 VDPAU Error: Error at util-vdpau.cpp:870 (#23, The system does not have enough resources to complete the requested operation at this time.)
2009-07-19 11:04:25.283 VDPAU Error: Failed to create output surface.
2009-07-19 11:04:25.326 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubobdeint,none) filt()
2009-07-19 11:04:25.326 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-07-19 11:04:25.326 VDP: LoadBestPreferences(2048x2048, 0)
2009-07-19 11:04:25.327 VDP: LoadBestPreferences(2048x2048, 60)
2009-07-19 11:04:25.327 VDP: LoadBestPreferences(1920x1080, 60)
2009-07-19 11:04:25.327 Using 0 CPUs for decoding
2009-07-19 11:04:25.327 AFD: InitVideoCodec() 0x7f0888147b80 id(MPEG2VIDEO) type (Video).
2009-07-19 11:04:25.327 VideoOutputXv: InputChanged(1920,1080,1.77778) 'None'->'MPEG2'
2009-07-19 11:04:25.327 VDP: LoadBestPreferences(1920x1088, 25)
2009-07-19 11:04:25.327 VDP: GetFilteredDeint() : vdpau -> 'vdpaubobdeint'
2009-07-19 11:04:25.327 VDP: GetFilteredDeint() : vdpau -> 'vdpaubobdeint'
2009-07-19 11:04:25.327 VideoOutputXv: DiscardFrames(1)
2009-07-19 11:04:25.327 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA
2009-07-19 11:04:25.328 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2009-07-19 11:04:25.328 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2009-07-19 11:04:25.328 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-07-19 11:04:25.328 VideoOutputXv: DiscardFrames(1)
2009-07-19 11:04:25.328 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA
2009-07-19 11:04:25.328 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2009-07-19 11:04:25.328 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2009-07-19 11:04:25.328 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-07-19 11:04:25.378 VideoOutputXv: DiscardFrames(1)
2009-07-19 11:04:25.379 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA
2009-07-19 11:04:25.379 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2009-07-19 11:04:25.379 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2009-07-19 11:04:25.379 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-07-19 11:04:25.563 VideoOutputXv: InitSetupBuffers() render: vdpau, allowed: xv-blit,xshm,opengl,vdpau,xlib
2009-07-19 11:04:25.737 Created data @0x7f088b9ffec0->0x7f088bcfcec2
2009-07-19 11:04:25.738 Created data @0x7f087c000030->0x7f087c2fd032
2009-07-19 11:04:25.738 Created data @0x7f087c2fd080->0x7f087c5fa082
2009-07-19 11:04:25.738 Created data @0x7f087c5fa0d0->0x7f087c8f70d2
2009-07-19 11:04:25.738 Created data @0x7f087c8f7120->0x7f087cbf4122
2009-07-19 11:04:25.738 Created data @0x7f087cbf4170->0x7f087cef1172
2009-07-19 11:04:25.739 Created data @0x7f087cef11c0->0x7f087d1ee1c2
2009-07-19 11:04:25.739 Created data @0x7f087d1ee210->0x7f087d4eb212
2009-07-19 11:04:25.739 Created data @0x7f087d4eb260->0x7f087d7e8262
2009-07-19 11:04:25.739 Created data @0x7f087d7e82b0->0x7f087dae52b2
2009-07-19 11:04:25.739 Created data @0x7f087dae5300->0x7f087dde2302
2009-07-19 11:04:25.739 Created data @0x7f087dde2350->0x7f087e0df352
2009-07-19 11:04:25.739 Created data @0x7f087e0df3a0->0x7f087e3dc3a2
2009-07-19 11:04:25.739 Created data @0x7f087e3dc3f0->0x7f087e6d93f2
2009-07-19 11:04:25.739 Created data @0x7f087e6d9440->0x7f087e9d6442
2009-07-19 11:04:25.739 Created data @0x7f087e9d6490->0x7f087ecd3492
2009-07-19 11:04:25.739 Created data @0x7f087ecd34e0->0x7f087efd04e2
2009-07-19 11:04:25.864 VideoOutputXv: Created VDPAU context (software decode)
2009-07-19 11:04:25.864 VDP: SetVideoRenderer(vdpau)
2009-07-19 11:04:25.864 VDP: SetVideoRender(vdpau) == GetVideoRenderer()
2009-07-19 11:04:25.866 VDPAU: Created OSD (1920x1032)
2009-07-19 11:04:25.866 VideoOutputXv: VDPAU Colorkey: 0x20202 (depth 24)
2009-07-19 11:04:25.866 Snapping height to avoid scaling: height: 1080, top: -24
2009-07-19 11:04:25.866 Snapping width to avoid scaling: width: 1920, left: 0
2009-07-19 11:04:25.866 Display Rect  left: 0, top: -24, width: 1920, height: 1080, aspect: 1.77778
2009-07-19 11:04:25.866 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-07-19 11:04:25.866 VDP: GetFilteredDeint() : vdpau -> 'vdpaubobdeint'
2009-07-19 11:04:25.866 VDP: GetFilteredDeint() : vdpau -> 'vdpaubobdeint'
2009-07-19 11:04:25.866 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-07-19 11:04:25.866 VDP: LoadBestPreferences(1920x1088, 29.97)
2009-07-19 11:04:26.091 NVP: ClearAfterSeek(1)
2009-07-19 11:04:26.091 VideoOutputXv: ClearAfterSeek()
2009-07-19 11:04:26.091 VideoOutputXv: DiscardFrames(0)
2009-07-19 11:04:26.091 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA
2009-07-19 11:04:26.091 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA -- done
2009-07-19 11:04:26.091 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-07-19 11:04:26.092 NVP: LoadFilters(''..) -> 0
2009-07-19 11:04:26.092 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
2009-07-19 11:04:26.092 AFD: EIA-708 caption service #1 is in the English language.
2009-07-19 11:04:26.092 AFD: Using ffmpeg for video decoding
2009-07-19 11:04:26.092 AFD: Looking for decoder for MPEG2VIDEO
2009-07-19 11:04:26.092 AFD: Opened codec 0x7f0888147b80, id(MPEG2VIDEO) type(Video)
2009-07-19 11:04:26.092 AFD: Stream #1, has id 0x52 codec id AC3, type Audio, bitrate 448000 at 0x0x7f0888147f90
2009-07-19 11:04:26.092 AFD: codec AC3 has 2 channels
2009-07-19 11:04:26.093 AFD: Looking for decoder for AC3
2009-07-19 11:04:26.094 AFD: Opened codec 0x7f08881216a0, id(AC3) type(Audio)
2009-07-19 11:04:26.094 RingBuf(/htpc/recordings/2261_20090719110422.mpg): CalcReadAheadThresh(2233016608 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-07-19 11:04:26.101 Opening audio device 'hdmi_complete'. ch 2(2) sr 48000
2009-07-19 11:04:26.101 Opening ALSA audio device 'hdmi_complete'.
2009-07-19 11:04:26.106 NVP: Waiting for prebuffer..  7 AAAAAAAAAAAAAAAAA
2009-07-19 11:04:26.300 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-07-19 11:04:26.398 NVP: Waiting for prebuffer..  8 AAAAAAAAAAAAAAAAA
2009-07-19 11:04:26.515 Mixer unable to find control Master
2009-07-19 11:04:26.516 Mixer unable to find control Master
2009-07-19 11:04:26.518 NVP: Enabling Audio
2009-07-19 11:04:26.518 Dec: Trying to select track (w/lang)
2009-07-19 11:04:26.518 Dec: Selecting first track
2009-07-19 11:04:26.518 Dec: Selected track #1 in the Unknown language(0)
2009-07-19 11:04:26.518 Dec: Selected track #1 in the English language(6647399)
2009-07-19 11:04:26.519 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(1)
2009-07-19 11:04:26.520 Position map filled from DB to: 75
2009-07-19 11:04:26.520 SyncPositionMap watchingrecording, from DB: 6 entries
2009-07-19 11:04:26.521 Filling position map from 76 to 80
2009-07-19 11:04:26.521 Position map filled from Encoder to: 75
2009-07-19 11:04:26.521 SyncPositionMap watchingrecording total: 6 entries
2009-07-19 11:04:26.521 SyncPositionMap, new totframes: 75, new length: 2, posMap size: 6
2009-07-19 11:04:26.521 AFD: Partial position map found
2009-07-19 11:04:26.521 AFD: Successfully opened decoder for file: "/htpc/recordings/2261_20090719110422.mpg". novideo(0)
2009-07-19 11:04:26.525 NVP: DoPlay: rate: 29.97 speed: 1 skip: 1 => new interval 33366
2009-07-19 11:04:26.525 Set video sync frame interval to 33366
2009-07-19 11:04:26.525 NVP: Stretch Factor 1, allow passthru 
2009-07-19 11:04:26.525 RingBuf(/htpc/recordings/2261_20090719110422.mpg): CalcReadAheadThresh(2233089824 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-07-19 11:04:26.526 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(1)
2009-07-19 11:04:26.527 Position map filled from DB to: 75
2009-07-19 11:04:26.527 SyncPositionMap watchingrecording, from DB: 6 entries
2009-07-19 11:04:26.527 Filling position map from 76 to 80
2009-07-19 11:04:26.527 Position map filled from Encoder to: 75
2009-07-19 11:04:26.527 SyncPositionMap watchingrecording total: 6 entries
2009-07-19 11:04:26.539 NVP: Waiting for prebuffer..  9 LAAAAAAAAAAAAAAAA
2009-07-19 11:04:26.886 VDPAU: Using 4 output surfaces (max 4)
2009-07-19 11:04:27.218 NVP: Video is 4.62785 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.219 NVP: Video is 5.34403 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.219 NVP: Video is 5.63391 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.219 NVP: Video is 5.59657 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.219 NVP: Video is 5.32132 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.219 NVP: Video is 4.86762 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.219 NVP: Video is 4.27258 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.419 NVP: Video is 4.01936 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.420 NVP: Video is 4.1459 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.517 NVP: Video is 4.35132 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.518 NVP: Video is 4.37988 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.518 NVP: Video is 4.14656 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.703 NVP: Video is 4.38953 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.703 NVP: Video is 4.5434 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.704 NVP: Video is 4.41905 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.704 NVP: Video is 4.07103 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.883 NVP: Video is 4.01019 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.883 NVP: Video is 4.10906 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.973 NVP: Video is 4.22757 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:27.973 NVP: Video is 4.20464 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:28.182 NVP: Video is 4.01519 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:28.393 NVP: Video is 4.16028 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:28.393 NVP: Video is 4.04181 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:28.760 NVP: Video is 4.14892 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:28.760 NVP: Video is 4.03327 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.162 NVP: Video is 4.17119 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.166 NVP: Video is 4.08745 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.539 NVP: Video is 4.13376 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.569 NVP: Video is 4.35159 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.598 NVP: Video is 4.49997 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.624 NVP: Video is 4.58128 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.656 NVP: Video is 4.58982 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.690 NVP: Video is 4.57376 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.715 NVP: Video is 4.5692 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.741 NVP: Video is 4.51334 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.776 NVP: Video is 4.404 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.810 NVP: Video is 4.34448 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.836 NVP: Video is 4.30732 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.868 NVP: Video is 4.21201 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.898 NVP: Video is 4.13304 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:29.924 NVP: Video is 4.04385 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.012 NVP: Video is 4.05041 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.037 NVP: Video is 4.08676 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.071 NVP: Video is 4.0541 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.110 NVP: Video is 4.04457 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.137 NVP: Video is 4.0674 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.171 NVP: Video is 4.03956 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.200 NVP: Video is 4.0187 frames behind audio (too slow), dropping frame to catch up.
'video_output' mean = '35153.32', std. dev. = '28924.22', fps = '28.45'
2009-07-19 11:04:30.298 NVP: Video is 4.17113 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.325 NVP: Video is 4.31967 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.362 NVP: Video is 4.38611 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.400 NVP: Video is 4.46592 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.427 NVP: Video is 4.55575 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.463 NVP: Video is 4.58566 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.494 NVP: Video is 4.62306 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.520 NVP: Video is 4.63613 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.522 NVP: Video is 4.59348 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:30.522 NVP: Video is 4.32173 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:31.058 NVP: Video is 4.06495 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:31.216 NVP: Video is 4.0012 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:31.420 NVP: Video is 4.04579 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:31.686 NVP: Video is 4.08817 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:31.813 NVP: Video is 4.17008 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:31.813 NVP: Video is 4.17653 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:32.224 NVP: Video is 4.08805 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:32.387 NVP: Video is 4.07921 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:32.684 NVP: Video is 4.06606 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:33.018 NVP: Video is 4.04403 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:33.351 NVP: Video is 4.04921 frames behind audio (too slow), dropping frame to catch up.
'video_output' mean = '33427.53', std. dev. = '14554.06', fps = '29.92'
2009-07-19 11:04:33.622 NVP: Video is 4.07673 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:33.820 NVP: Video is 4.04855 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:34.057 NVP: Video is 4.05365 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:34.318 NVP: Video is 4.03366 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:34.556 NVP: Video is 4.03033 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:34.784 NVP: Video is 4.00291 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:35.085 NVP: Video is 4.00779 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:35.368 NVP: Video is 4.06333 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:35.556 NVP: Video is 4.03878 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:35.856 NVP: Video is 4.01136 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:36.256 NVP: Video is 4.07774 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:36.521 NVP: Video is 4.05536 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:36.824 NVP: Video is 4.09153 frames behind audio (too slow), dropping frame to catch up.
'video_output' mean = '33214.96', std. dev. = '13394.42', fps = '30.11'
2009-07-19 11:04:37.091 NVP: Video is 4.06773 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:37.372 NVP: Video is 4.15453 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:37.372 NVP: Video is 4.05997 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:38.064 NVP: Video is 4.0544 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:38.323 NVP: Video is 4.0704 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:38.458 NVP: Video is 4.03357 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:38.657 NVP: Video is 4.00204 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:38.995 NVP: Video is 4.07646 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:39.190 NVP: Video is 4.00551 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:39.428 NVP: Video is 4.08569 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:39.662 NVP: Video is 4.07559 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:39.924 NVP: Video is 4.04271 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:40.195 NVP: Video is 4.08035 frames behind audio (too slow), dropping frame to catch up.
'video_output' mean = '33305.12', std. dev. = '13690.82', fps = '30.03'
2009-07-19 11:04:40.460 NVP: Video is 4.02137 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:40.785 NVP: Video is 4.15762 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:40.785 NVP: Video is 4.13721 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:41.064 NVP: Video is 4.08221 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:41.263 NVP: Video is 4.05134 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:41.427 NVP: Video is 4.04804 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:41.637 NVP: Video is 4.10259 frames behind audio (too slow), dropping frame to catch up.
2009-07-19 11:04:41.673 TV: Attempting to change from WatchingLiveTV to None
2009-07-19 11:04:41.673 TV: StopStuff() -- begin
2009-07-19 11:04:41.673 TV: StopStuff(): stopping ring buffer[s]
2009-07-19 11:04:41.703 TV: StopStuff(): stopping player[s] (1/2)
2009-07-19 11:04:41.703 TV: StopStuff(): stopping recorder[s]
2009-07-19 11:04:41.704 NVP: Exited decoder loop.
2009-07-19 11:04:41.711 ~OpenGLVideoSync() -- begin
2009-07-19 11:04:41.711 ~OpenGLVideoSync() -- middle
2009-07-19 11:04:41.712 ~OpenGLVideoSync() -- end
2009-07-19 11:04:41.712 VideoOutputXv: dtor
2009-07-19 11:04:41.712 VideoOutputXv: DiscardFrames(1)
2009-07-19 11:04:41.712 VideoBuffers::DiscardFrames(1): LAAAUUUUUUUUUUuAA
2009-07-19 11:04:41.712 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2009-07-19 11:04:41.712 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2009-07-19 11:04:41.712 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-07-19 11:04:41.743 VDPAU Error: DISPLAY PRE-EMPTED. Aborting playback.
2009-07-19 11:04:41.743 VDPAU Error: Error at util-vdpau.cpp:582 (#2, The display was pre-empted, or a fatal error occurred.)
2009-07-19 11:04:41.743 VDPAU Error: Error at util-vdpau.cpp:590 (#3, An invalid handle value was provided.)
2009-07-19 11:04:41.743 VideoOutputXv: DiscardFrames(1)
2009-07-19 11:04:41.743 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA
2009-07-19 11:04:41.743 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2009-07-19 11:04:41.743 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2009-07-19 11:04:41.743 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-07-19 11:04:42.153 TV: StopStuff(): stopping player[s] (2/2)
2009-07-19 11:04:42.174 TV: StopStuff() -- end
2009-07-19 11:04:42.174 TV: Changing from WatchingLiveTV to None
2009-07-19 11:04:46.862 Deleting UPnP client...
```

BTW, Bob2X is the deinterlacer I'm using.

---

### Post by jyavenard on 2009-07-19
you aren't using VDPAU for decoding here but software decoding, and vdpaubasicdoublerate which your 8200 will never handle properly.

edit your video playback profile so it only uses vdpau, never the default decoder...
like create one with one entry only:
>      W: 0 H: 0, decoder: VDPAU, renderer: VDPAU, Deinterlacer: Bob 2X

To prevent errors like "Error at util-vdpau.cpp:870 (#23, The system does not have enough resources to complete the requested operation at this time"

try to increase the amount of RAM shared by the GPU.

And finally, make sure you follow my FAQ:
[http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html](http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html)

in particular, the audio settings...

---

### Post by uncle hammy on 2009-07-19
> **jyavenard said:**
> Using 185.18.14 drivers by any chance?
it's typically what occurs when using VDPAU on my mythtv frontend.
180.60 has proven to be much more reliable
No, 180.60 drivers.

---

### Post by frigginacky on 2009-07-19
> **jyavenard said:**
> you aren't using VDPAU for decoding here but software decoding, and vdpaubasicdoublerate which your 8200 will never handle properly.

edit your video playback profile so it only uses vdpau, never the default decoder...
like create one with one entry only:
>      W: 0 H: 0, decoder: VDPAU, renderer: VDPAU, Deinterlacer: Bob 2X

To prevent errors like "Error at util-vdpau.cpp:870 (#23, The system does not have enough resources to complete the requested operation at this time"

try to increase the amount of RAM shared by the GPU.

And finally, make sure you follow my FAQ:
[http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html](http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html)

in particular, the audio settings...

All suggestions followed, and it appears to be mostly working - playback looks better, and CPU usage has dropped to ~25%. :D  I'm still getting masses of "video ahead of/behind audio" errors, though. Aggressive sound card buffering is unchecked & extra audio buffering is checked, as you instructed.

---

### Post by jyavenard on 2009-07-19
> **frigginacky said:**
> All suggestions followed, and it appears to be mostly working - playback looks better, and CPU usage has dropped to ~25%. :D  I'm still getting masses of "video ahead of/behind audio" errors, though. Aggressive sound card buffering is unchecked & extra audio buffering is checked, as you instructed.

Despite those errors, does it play okay ?

Disable the AC3 upmixer if you have it enabled and change the upmixer settings to "Passive" this will lower your CPU usage even more, and may help playback

---

### Post by frigginacky on 2009-07-19
> **jyavenard said:**
> Despite those errors, does it play okay ?

Disable the AC3 upmixer if you have it enabled and change the upmixer settings to "Passive" this will lower your CPU usage even more, and may help playback


Both of those options were already set that way.  

It plays better than before, but you can see it stuttering sometimes when it hits an audio/video sync error.  I just checked playback with the default CPU+ playback profile, and I'm getting the same errors, so it's not strictly a VDPAU thing.

---

### Post by emillan on 2009-07-29
Just wanted to publicly thank Jean-Yves for all his initiative and good work getting VDPAU-enabled Myth on our systems and then teaching us how to make it work.  I am a very happy user!

---

### Post by frigginacky on 2009-07-29
> **emillan said:**
> Just wanted to publicly thank Jean-Yves for all his initiative and good work getting VDPAU-enabled Myth on our systems and then teaching us how to make it work.  I am a very happy user!

Seconded.  Thanks for all your help!

---

### Post by laffinet on 2009-08-14
I'm currently running 9.04 and am planning to install a new graphics card ([Gainward 9400]("http://www.gainward.net/main/vgapro.php?id=128")) to my box and try VDPAU. Couple of questions:

1. As far as I understand, these are the steps I have to perform to get things working
a) enable jyavenard's repos (release only, not test)
b) update & upgrade
c) create a vdpau playback profile
d) a few other tweaks (as per FAQ) if required
Is this it, anything I've forgotten ?

2. Any backups required ?

3. If for whatever reason things go wrong, how can I revert back to the original situation ?

Thanks for any help.

---

### Post by jyavenard on 2009-08-14
> **laffinet said:**
> I'm currently running 9.04 and am planning to install a new graphics card ([Gainward 9400]("http://www.gainward.net/main/vgapro.php?id=128")) to my box and try VDPAU. Couple of questions:

1. As far as I understand, these are the steps I have to perform to get things working
a) enable jyavenard's repos (release only, not test)

If you want to use drivers nvidia drivers 180.60 yes.
To use 190.18 you need the testing repository.
But even those drivers are still a tad unstable and crash on a daily basis (though not as much as 185.xx)

> 
b) update & upgrade
c) create a vdpau playback profile
d) a few other tweaks (as per FAQ) if required


some of the tweaks mentioned in the FAQ aren't even necessary anymore as if using the vdpau profile it will automatically set things up automatically such disabling the aggressive audio profile.

> 
Is this it, anything I've forgotten ?

2. Any backups required ?

You may want to backup your database for the sake of it... though no modification to the database is made.

> 
3. If for whatever reason things go wrong, how can I revert back to the original situation ?


Yes, simply disable my repository. Uninstall all mythtv packages and re-install mythtv.
It's the easiest way and nothing will be lost.

My vdpau packages are based on the mythbuntu packages so many things are in common, in particular it uses the same file location and configuration, so they are compatible with one another.

Could keep mythbuntu packages on your backend for example, and only use mine for the frontend.

Though, my packages do add fixes for h264 recordings so the time is properly recorded...
0.21-fixes is buggy for those, and I backported some fixed from trunk.

---

### Post by laffinet on 2009-08-14
> **jyavenard said:**
> 
Yes, simply disable my repository. Uninstall all mythtv packages and re-install mythtv.
It's the easiest way and nothing will be lost.


Will all my settings be kept should I have to do this ?

---

### Post by jyavenard on 2009-08-15
> **laffinet said:**
> Will all my settings be kept should I have to do this ?

Yes. Settings will be fine. All settings are stored on a mysql database which survive everything. 

BTW, you're better off getting a nvidia 9500GT video card instead of a 9400. The 9400 isn't fast enough for using the advanced deinterlacers on HD content.

---

### Post by dano1 on 2009-08-15
jya,

am having no probs with the 190 drivers from testing everything is great. noticed that there an updte for the 180 drivers in release, any updates for testing soon? or are u pretty much done?
 btw, thanks for all ur work, made my linux/myth experience very enjoyable now.

danny

---

### Post by jyavenard on 2009-08-15
> **dano1 said:**
> jya,

am having no probs with the 190 drivers from testing everything is great. noticed that there an updte for the 180 drivers in release, any updates for testing soon? or are u pretty much done?
 btw, thanks for all ur work, made my linux/myth experience very enjoyable now.

danny

I automated the build for the release repository. I need to do the same for the testing one. 

I stopped using testing because having to power cycle my pc every few days isn't something my wife enjoyed when watching tv.

---

### Post by laffinet on 2009-08-15
> **jyavenard said:**
> 
BTW, you're better off getting a nvidia 9500GT video card 

Thanks for the tip.
The passively cooled 9500 is a lot bigger than the 9400 and I don't have a lot of room in my case, so I had to go with the 9400.

I'm about to plug the thing in and update with your repos. Fingers crossed :P

---

### Post by jyavenard on 2009-08-15
> **laffinet said:**
> Thanks for the tip.
The passively cooled 9500 is a lot bigger than the 9400 and I don't have a lot of room in my case, so I had to go with the 9400.



Weird, my 9400GT passively cool is already quite big, takes two slots.

---

### Post by laffinet on 2009-08-15
Okay, installed the card, did the changes, not quite working as it should.

Live TV is showing "random blocks" throughout the picture. Any idea ?

Which driver should be installed ? nvidia control panel is telling me 180.60. Is this the right version ?

Also, on the desktop (or in applications like firefox right now) tiny white specs appear and disappear in black areas (like the letters of this post).

---

### Post by jyavenard on 2009-08-15
Make sure your cable is properly connected and not bent.
I see random white dots when I the cable is too bend on my system.

There's an issue seen with 185.x drivers where random points appear everywhere, but I haven't heard about this issue with 180.60.

For VDPAU, after intalling the drivers, did you reboot? when you start nvidia-settings, does it see the proper driver: it's the only way for testing if you are running the proper driver.

As for random block in playback, this can only occurs if your TV stream is corrupted.

---

### Post by laffinet on 2009-08-15
Cable seems okay, same position as before.

As for random blocks during playback: I doubt it's a corrupted stream (I assume you mean some kind of reception issue). This hasn't happened before.

I hate to say it, but these two issues (random blocks and white dots) haven't happened before, starting when putting in the new card and updating.

I did reboot. What do you mean with "does it see the proper driver"? How do I check ?

---

### Post by jyavenard on 2009-08-15
> **laffinet said:**
> Cable seems okay, same position as before.

As for random blocks during playback: I doubt it's a corrupted stream (I assume you mean some kind of reception issue). This hasn't happened before.

I hate to say it, but these two issues (random blocks and white dots) haven't happened before, starting when putting in the new card and updating.

I did reboot. What do you mean with "does it see the proper driver"? How do I check ?

start nvidia-settings and see which drivers it states you have. did you have an nividia card before? which driver did you use?

there's no way vdpau or mythtv would have anything to do with corrupted display and firefox.. Could be a faulty video card ...

I still would check the cable...

---

### Post by laffinet on 2009-08-15
Used an onboard nvidia 7 card chip before. 

Can I use your packages with the old card ? If so, I'd take the new card out, see how things look then ?

---

### Post by laffinet on 2009-08-15
nvidia-settings says 180.60

---

### Post by jyavenard on 2009-08-15
> **laffinet said:**
> Used an onboard nvidia 7 card chip before. 

Can I use your packages with the old card ? If so, I'd take the new card out, see how things look then ?

Check if the 180.x drivers support your video card first.
But yes, you can use my packages. They aren't specific to using VDPAU only.
they contain a lot of fixes and extra features not even found in MythTV trunk yet (though many of them are being comitted)

---

### Post by laffinet on 2009-08-15
I think I'm narrowing the problem down. 

These problems only occur when I use the playback profile I set up for vdpau.
When I revert back to teh standard CPU+ profile everything is fine. So it's not a faulty card or a dodgy cable connection.

Interestingly enough, the white dots on the desktop are also gone when I'm not using the vdpau profile. I suppose that's because I was still running mythfrontend with live tv, just switched to firefox. So the vdpau problems somehow affected the desktop, if that makes sense.

---

### Post by laffinet on 2009-08-15
Question is, what's wrong with "my vdpau".

I've attached some screenshots of my settings, anything wrong with that ?

---

### Post by ian dobson on 2009-08-15
Hi laffinet,

Can you provide abit more information:-

1) What graphic card are you using?
2) Post the end of your mythrontend.log from /var/log/mythtv

Regards
Ian Dobson

---

### Post by laffinet on 2009-08-15
It's a Gainward 9400GT

end of log:

```
2009-08-15 19:30:35.552 Received a remote 'Clear Cache' request
2009-08-15 19:30:40.561 TV: Attempting to change from None to WatchingLiveTV
2009-08-15 19:30:40.562 Using protocol version 40
2009-08-15 19:30:41.665 DPMS Deactivated 
2009-08-15 19:30:41.809 NVP: Disabling Audio, params(-1,2,44100)
2009-08-15 19:30:42.298 OSD Theme Dimensions W: 1280 H: 720
2009-08-15 19:30:42.576 TV: Changing from None to WatchingLiveTV
2009-08-15 19:30:42.579 Realtime priority would require SUID as root.
2009-08-15 19:30:42.680 Video timing method: USleep with busy wait
2009-08-15 19:30:45.528 AFD: Opened codec 0xa89ffa60, id(MPEGVIDEO_VDPAU) type(Video)
2009-08-15 19:30:45.528 AFD: codec AC3 has 6 channels
2009-08-15 19:30:45.528 AFD: Opened codec 0xaa1d7520, id(AC3) type(Audio)
2009-08-15 19:30:45.597 Opening audio device 'default'. ch 2(2) sr 48000
2009-08-15 19:30:45.597 Opening ALSA audio device 'default'.
2009-08-15 19:30:45.660 Mixer unable to find control Master
2009-08-15 19:30:45.660 Mixer unable to find control Master
2009-08-15 19:30:45.662 NVP: Enabling Audio
```

I tried different deinterlacers, some are the same, some are worse, none eliminate the problem.

I do notice a drop in CPU usage when using the vdpau profile, but that's obviously no good if it comes at the price of the other problems :)

---

### Post by jyavenard on 2009-08-15
> **laffinet said:**
> Question is, what's wrong with "my vdpau".

I've attached some screenshots of my settings, anything wrong with that ?

My mythtv settings can even explain why it would cause a corrupt display outside of mythtv.

It's either a driver issue, or a graphic card issue.

Now, I've never heard of such issue with the 180.xx drivers ; some people did report white dots everywhere with 190.xx drivers...

Try rebooting the PC completely, see if it still does it ...

Try using the "testing "repository with the 190.18 drivers...
Here is how to upgrade
[http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/6/6_How_to_upgrade_to_nVidia_drivers_185.18.14_part_2.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/6/6_How_to_upgrade_to_nVidia_drivers_185.18.14_part_2.html)

Try using a different video card.

---

### Post by laffinet on 2009-08-15
> **jyavenard said:**
> My mythtv settings can even explain why it would cause a corrupt display outside of mythtv.

Remember that this is while mythtv is still open with livetv playing and me opening firefox on top of this. Isn't it possible that whatever is going wrong with vdpau has an effect on the desktop as well when mythtv is still running?

> **jyavenard said:**
> 
Try rebooting the PC completely, see if it still does it ...

Done that, doesn't change a thing.

> **jyavenard said:**
> 

Try using a different video card.

Only other video card I have is the onboard GF7, which doesn't support vdpau. Works fine with your repos though and doesn't show any of the issues I described.

> **jyavenard said:**
> Try using the "testing "repository with the 190.18 drivers...
Here is how to upgrade
[http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/6/6_How_to_upgrade_to_nVidia_drivers_185.18.14_part_2.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/6/6_How_to_upgrade_to_nVidia_drivers_185.18.14_part_2.html)

How easy (or difficult) is it to revert back to your release repos and the old (180.60) driver ?

---

### Post by laffinet on 2009-08-15
I also just noticed another thing: when starting to watch a video (which calls up mplayer) the volume is ridiculously loud. Previously the volume had to be around 50% in player to be alright, now it's got to be at the lowest possible setting. Live TV and music are still the same as before, so I guess it's something to do with mplayer. Any setting I can change somewhere to rectify this.

Note: mplayer also doesn't seem to keep the volume setting, ie everytime I start to watch a video it starts at full volume.

---

### Post by jyavenard on 2009-08-15
> **laffinet said:**
> 
How easy (or difficult) is it to revert back to your release repos and the old (180.60) driver ?

Quite easy. Pretty much the same process as going back to the original mythbuntu packages.

For the nvidia drivers: [http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/6/10_How_to_downgrade_to_nVidia_drivers_180.xx.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/6/10_How_to_downgrade_to_nVidia_drivers_180.xx.html)

For the rest, pretty much: remove the repository testing, uninstall mythtv, apt-get update, re-install mythtv.

I do it each time nivida release a new driver: test if they fixed their crashes (I supplied them heaps of kernel backtrace), see that they didn't, go back to 180.60.

---

### Post by jyavenard on 2009-08-15
> **laffinet said:**
> I also just noticed another thing: when starting to watch a video (which calls up mplayer) the volume is ridiculously loud. Previously the volume had to be around 50% in player to be alright

mplayer has been updated to a much more recent version of mplayer (as of yesterday in fact)

but you don't have to use mplayer to play a video.
Change it to use the internal player.

In the settings, go to edit the file type, and change the various type to use "Internal" (uppercase I is important) instead of the default player.

my 0.21-fixes contains patches that makes it play much more content than the stock 0.21-fixes

---

### Post by laffinet on 2009-08-15
First of all, thanks for all your help. Much appreciated.

So, what options do I have at the moment ?

Try upgading to nvidia 185.xx, see if that fixes my problems

If it doesn't:
a) revert back to 180.xx, your release repos and don't run the vdpau profile
b) revert back all the way to the original repos 

Both of which make the new graphics card kind of obsolete :(

Another question: does the internal player make use of vdpau at all ?

---

### Post by laffinet on 2009-08-15
I'm a bit confused about how exactly to upgrade to 185.xx

Please confirm:

1. add "testing" to the repo

2. Start synaptic

3. Click on “Reload”

4.Click on “Mark All Upgrades”

5. This will prompt you that nvidia-glx-180 and nvidia-libvdpau-180 will be uninstalled. That’s okay. Do not click Apply yet.

What do I do here, cancel ?

6. Mark to install nvidia-glx-185

Where ? Can you explain ?

Thanks.

---

### Post by jyavenard on 2009-08-15
> **laffinet said:**
> 
If it doesn't:
a) revert back to 180.xx, your release repos and don't run the vdpau profile
b) revert back all the way to the original repos 

Both of which make the new graphics card kind of obsolete :(


Not really... Mythtv in my repo add other playback options not available on stock 0.21-fixes. in particular the new opengl accelerated video renderer. A 9400GT is going to be much faster than what you had before when it comes top OpenGL.

Try the new Yadif OpenGL HW accelerated.

But frankly, with a 9400GT, VDPAU is much better.

> Another question: does the internal player make use of vdpau at all ?
Of course, even mplayer can you vdpau

If you're using an AMD processor with frequency scaling, when using VDPAU make sure the minimum CPU speed is set at 1.8GHz, not anything slower. When using frequency scaling, AMD (unlike intel processor) also slows down the external databus, below 1.8GHz it's not fast enough to feed the graphic card with the video stream.

---

### Post by jyavenard on 2009-08-15
> **laffinet said:**
> I'm a bit confused about how exactly to upgrade to 185.xx

Please confirm:

1. add "testing" to the repo

2. Start synaptic

3. Click on “Reload”

4.Click on “Mark All Upgrades”

5. This will prompt you that nvidia-glx-180 and nvidia-libvdpau-180 will be uninstalled. That’s okay. Do not click Apply yet.

What do I do here, cancel ?

6. Mark to install nvidia-glx-185

Where ? Can you explain ?

Thanks.

Those instructions were for 185.xx drivers, latest ones are 190.18, use the same instructions but replace anything with 185 with 190

So click on Upgrade All.
Then go and install the nvidia-glx-190.

Then apply the changes

---

### Post by laffinet on 2009-08-15
> **jyavenard said:**
> 
So click on Upgrade All.
Then go and install the nvidia-glx-190.

Then apply the changes

Sorry, I might be a bit slow, but I'm not sure what you mean here.

I click on "Mark all upgrades", this is what I get:
lists a whole lot of packages
Some to be removed (2x 180 packages)
1 to be installed (nvidia 190 libvdpau)
Several other to be upgraded (myth related stuff, mplayer etc.)

What do I do here ? 

And how and where do I install nvidia-glx-190?

---

### Post by jyavenard on 2009-08-15
You've never installed packages with ubuntu ?
Same place you do it for all other packages, either synaptic or from the command line with apt-get

Just do a search on nvidia-glx-190 and install that !

I can't help you if you do not know at least the basics, it's not that complicated.

---

### Post by laffinet on 2009-08-15
> **jyavenard said:**
> You've never installed packages with ubuntu ?
Same place you do it for all other packages, either synaptic or from the command line with apt-get

Just do a search on nvidia-glx-190 and install that !

I can't help you if you do not know at least the basics, it's not that complicated.

No no, I have installed packages many times, synaptic and command line.

And I just noticed where I got confused. I should read what's on the screen...

Click mark all upgrades, click mark (this is what I confused with apply earlier), search for new nvidia driver, mark for installation, click apply. All clear now.

---

### Post by laffinet on 2009-08-15
Okay, installed the new driver, no difference. Still random blocks in livetv (seem to be more frequent during pictures with lots of black),
Still white pixels on desktop with myth running on vdpau in background.

No problems at all when running standard CPU+ profile.

I'm not frequency scaling my processor.

Not quite sure where to from here.

BTW: Don't discard me as a complete noob, just got confused with that one instruction for the driver installation...;-)

---

### Post by jyavenard on 2009-08-16
> **laffinet said:**
> Okay, installed the new driver, no difference. Still random blocks in livetv (seem to be more frequent during pictures with lots of black),
Still white pixels on desktop with myth running on vdpau in background.

No problems at all when running standard CPU+ profile.

I'm not frequency scaling my processor.

Not quite sure where to from here.


I would post your issue in the nvidia linux forum..
At that stage it looks to me that either your card is faulty, or you've uncovered a driver bug..
I just never seen any reports like you earlier.

---

### Post by laffinet on 2009-08-16
This thread [here]("http://www.nvnews.net/vbulletin/showthread.php?t=136817&highlight=myth") is describing the same problem I have. Will put a comment on there.

---

### Post by laffinet on 2009-08-16
Found some more threads (I think you posted in them too, JY) which seem to describe the same problem
[VDAPU and artifacts]("http://www.gossamer-threads.com/lists/mythtv/users/369072?search_string=vdpau;#369072")
[VDPAU terrible with 9400]("http://www.gossamer-threads.com/lists/mythtv/users/383823?search_string=vdpau;#383823")

The problem is obviously not restricted to a 9400 card or a single manufacturer.

Unfortunately none of the threads offer a solution yet :(

---

### Post by jyavenard on 2009-08-17
> **laffinet said:**
> Found some more threads (I think you posted in them too, JY) which seem to describe the same problem
[VDAPU and artifacts]("http://www.gossamer-threads.com/lists/mythtv/users/369072?search_string=vdpau;#369072")
[VDPAU terrible with 9400]("http://www.gossamer-threads.com/lists/mythtv/users/383823?search_string=vdpau;#383823")

The problem is obviously not restricted to a 9400 card or a single manufacturer.

Unfortunately none of the threads offer a solution yet :(

What happens when you play a video with mplayer and vdpau ?
do you see the same artefacts ?

to play with mplayer using vdpau, start it with:
mplayer -fs -vo vdpau -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, file.ext

I'll be interested with your results.
Jean-Yves

---

### Post by epi 1:10,000 on 2009-08-18
I'm using a 
**[GIGABYTE GV-N95TD3-512I GeForce 9500 GT 512MB 128-bit GDDR3]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814125260")**

without any problems.  I notice that allot of the 9400 and 1 GB 9500's are using gDDR2.  I alway tought using gDDR2 on a second gen DX10 card was a little shady.  Maybe manufacturers are pawning off low bin gDDR2???

---

### Post by laffinet on 2009-08-18
> **jyavenard said:**
> What happens when you play a video with mplayer and vdpau ?
do you see the same artefacts ?


Just tried playing a recording with mplayer and vdpau: same artefacts as with live tv.

Also tried a h264 and xvid encoded file with mplayer and vdpau: no problems, no artefacts. I guess the artefact problems only happen with mpeg2 files, similar to what others have reported.

---

### Post by novellahub on 2009-08-18
I have a question about adding the VDPAU repository for Mythtv 0.21.  Does adding this break the transcoding / commercial flagging abilities of Mythtv in Mythbuntu?  

There are several reports in LinHES (Knoppmyth) R6 of adding the VDPAU patch and this affecting both.

[http://knoppmyth.net/phpBB2/viewtopic.php?t=19635http://knoppmyth.net/phpBB2/viewtopic.php?t=19635](http://knoppmyth.net/phpBB2/viewtopic.php?t=19635http://knoppmyth.net/phpBB2/viewtopic.php?t=19635)

---

### Post by geekyhawkes on 2009-08-18
Potential daft question coming up now, but this is a monster thread and I just want to check i understand the details fully.

I am running 9.04 Mythbuntu 64bit with 180.60 Nvidia drivers enabled and running the myth box via HDMI.  (Using an onboard 8300 GPU)

I have taken from this thread all i need to do is add the followin repos;

To use VDPAU, all you need to do is add to your /etc/apt/sources.list:
deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/
deb-src [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/

And then sudo apt-get update
sudo apt-get upgrade

The bit i am unsure of is creating the vdpau display profile mentioned here, where and how do i do this?  Is there anything else i need to do to get VDPAU working on my install?

Thanks

---

### Post by ian dobson on 2009-08-18
> **laffinet said:**
> Just tried playing a recording with mplayer and vdpau: same artefacts as with live tv.

Also tried a h264 and xvid encoded file with mplayer and vdpau: no problems, no artefacts. I guess the artefact problems only happen with mpeg2 files, similar to what others have reported.

Hi laffinet,

Maybe can you try underclocking your card. You can patch/flash the bios using nibitor and nvflash (only under windows).

I had afew problems with my pasive cooled NV9400 until I underclocked it abit. I think the problem was caused by heat and underclocking the card reduced the temperature by a good 20°c.

EDIT: You might be able to adjust the GPU/MEM frequency using nvclock from the repos.

Regards 
Ian Dobson

---

### Post by laffinet on 2009-08-18
> **ian dobson said:**
> Hi laffinet,

Maybe can you try underclocking your card. You can patch/flash the bios using nibitor and nvflash (only under windows).

That is a problem, I don't have windows. Any other way this can be done ?

> **ian dobson said:**
> EDIT: You might be able to adjust the GPU/MEM frequency using nvclock from the repos.


Ah, that might answer my question above. Will have a look at this and report back.

---

### Post by laffinet on 2009-08-18
> **geekyhawkes said:**
> 
The bit i am unsure of is creating the vdpau display profile mentioned here, where and how do i do this?

This is done in the frontend setup. In the frontend go to Setup, TV settings, Playback settings. Select next a few times until you get to the "playback profiles" screen. 

You need to create a new profile called vdpau, then edit that profile and create a few entries. Going by JY's FAQ ([here]("http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html")) you need to create these entries:
> <      W: 1920 H: 720, decoder: VDPAU, renderer: VDPAU, Deinterlacer: Advanced 2X

>=    W: 0 H: 720, decoder: VDPAU, renderer: VDPAU, Deinterlacer: Temporal 2X


Hope this helps.

---

### Post by laffinet on 2009-08-18
> **jyavenard said:**
> Quite easy. Pretty much the same process as going back to the original mythbuntu packages.

For the nvidia drivers: [http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/6/10_How_to_downgrade_to_nVidia_drivers_180.xx.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/6/10_How_to_downgrade_to_nVidia_drivers_180.xx.html)

For the rest, pretty much: remove the repository testing, uninstall mythtv, apt-get update, re-install mythtv.

I do it each time nivida release a new driver: test if they fixed their crashes (I supplied them heaps of kernel backtrace), see that they didn't, go back to 180.60.

Hi JY,

I'm having a few stability issues with the testing repos and the 190.xx driver, so I tried reverting back to "release" and the 180.60 drivers. I must be doing something wrong though, because it's not working as planned.

Here's what happened:
- deleted "testing" from the repos
- opened synaptic, reloaded, selected "mark all upgrade" 

This is where I expected a message coming up saying 190 will be uninstalled, 180 will be installed, but that never happened. So I manually selected for 190 to be uninstalled and 180 to be installed

- selected uninstall myth
- applied
- apt-get update again (probably unnecessary)
- apt-get install mythtv

This is where I really ran into trouble, as apt was telling me there are unmet dependencies. From what I can tell it was about installing some 190 components which should really be 180 components.

Because it was getting late and I needed a working myth installation I ended up adding the testing repo again and installing the 190 driver and mythtv and everything worked fine, but I'd really like to go back to the "release" version. 
What am I doing wrong ?

Do I need to uninstall mythtv with the "testing" repo still active ?

---

### Post by geekyhawkes on 2009-08-19
Not just as simple as adding the repos.  I have just restarted and got an error window stating;
Ubuntu is running in low graphics mode;

Failed to load module type1 (module does not exist)
Failed to load module freetype )module does not exist)
EE NVIDIA 0 failed to intialize the nvidia kernel module
please ensure that there is a supported nvidia gpu in this system
and that the nvidia device files have been created properly.

***Aborting***
Screen found but none have a useable configuration!

Some how it seems to have confused my system which drivers to use.  I dont think i am running the nvidia drivers anymore and cannot get into the nivida settings from within the menu, however if i go into hardware drivers it shows 180 as active and in use!  

How do i recover my system?  It was nice and stable with 180.60 installed and active before this update repos was used.

Its now all messed up with various X windows failing and default settings being used by mythbuntu at the desktop.  HELP!

I have just downloaded and installed 185.18.31 driver and sadly have the same error.  Plus i now have API mismatch errors between 15 and 180.  I have tried editing nano /etc/default/linux-restricted-modules-common 
 to exclude "nv nvidia_new"

but the api mismatch is still there!

Pretty frustrating as i cannot get into my mythbuntu machine now other than terminal (which scores low with WAF!)


EDIT::::: 

I am trying to go back to 180.60 as we speak.  I am hoping this will get around the api mismatch errors so i can get back to x normally.  Still in need of help though.


Right, with 180.60 installed and a fresh build/install of X I am back into my system with the nvidia drivers loaded. 


I am noticing a fair few more artifacts watching live tv than i had before enabling vdpau.  I am going to  look into under clocking my card but without windows this seems like it might be tricky. nvclock doesnt fully recognise my 8300 card so i am not sure i can do anything.  

How can i disable vdpau until i can sort these artifacts?  (Can i just remove the display profile and go back to cpu++?)

---

### Post by laffinet on 2009-08-19
> **geekyhawkes said:**
> 
How can i disable vdpau until i can sort these artifacts?  (Can i just remove the display profile and go back to cpu++?)

Yes, just choose a different playback profile (without hardware acceleration) and you should be fine again. 

I'll be looking into underclocking my card as well and report back.

Somebody also suggested compiling my own driver, will have a look at that too.

---

### Post by jyavenard on 2009-08-20
> **laffinet said:**
> Hi JY,

I'm having a few stability issues with the testing repos and the 190.xx driver, so I tried reverting back to "release" and the 180.60 drivers. I must be doing something wrong though, because it's not working as planned.

Here's what happened:
- deleted "testing" from the repos
- opened synaptic, reloaded, selected "mark all upgrade" 

This is where I expected a message coming up saying 190 will be uninstalled, 180 will be installed, but that never happened. So I manually selected for 190 to be uninstalled and 180 to be installed

- selected uninstall myth
- applied
- apt-get update again (probably unnecessary)
- apt-get install mythtv

This is where I really ran into trouble, as apt was telling me there are unmet dependencies. From what I can tell it was about installing some 190 components which should really be 180 components.

Because it was getting late and I needed a working myth installation I ended up adding the testing repo again and installing the 190 driver and mythtv and everything worked fine, but I'd really like to go back to the "release" version. 
What am I doing wrong ?

Do I need to uninstall mythtv with the "testing" repo still active ?

Your process looks okay to me..

The way I do it is:
-Remove testing repository
-Reload (that's important)
-Uninstall all mythtv packages
-Apply
-Install mythtv packages, this will prompt to remove libvdpau-190 and use libvdpau-180 instead
-Install nvidia-glx-180 ; this will automatically uninstall nvidia-glx-190 and nvidia-190-kernel-source
-Apply

Either reboot, or do (in a text console):
/etc/init.d/gdm stop
rmmod nvidia
modprobe nvidia
/etc/init.d/gdm start

You can tell which nvidia drivers mythtv is linked against by looking at the version number.
0.21.0+fixes-21349-openglvdpau2-nv180-0ubuntu2

nv180 indicates that it is using nvidia drivers 180.xx
ubuntu0 is jaunty
ubuntu1 is hardy
ubuntu2 is intrepid

---

### Post by geekyhawkes on 2009-08-20
laffinet Thanks for the reply. I will be very interested to hear how you get on underclocking the card / sorting your own driver.

---

### Post by laffinet on 2009-08-20
> **geekyhawkes said:**
> laffinet Thanks for the reply. I will be very interested to hear how you get on underclocking the card / sorting your own driver.

No worries. Underclocking is a bit of a now-go at the moment. nvclock doesn't support my card yet. There seem to be ways to override that and force underclocking regardless, but I'm reluctant to do that.

So unless I find some other suggestions on how to solve this artefacts issue I'm at a dead end...:(

---

### Post by laffinet on 2009-08-21
> **jyavenard said:**
> 
You can tell which nvidia drivers mythtv is linked against by looking at the version number.
0.21.0+fixes-21349-openglvdpau2-nv180-0ubuntu2


Okay, I managed to revert back to the release version (had to select a lot of the packages separately though, as dependencies weren't met automatically. Not sure if that's normal).

One thing I noticed, though: 

mencoder version installed is this one:
1.0-svn29519-nv190-0ubunut0

which says requires >=190.xx for vdpau.
Is this correct ? I can't see another mencoder version in synaptic.
mplayer seems fine (1.0-svn29501-x264-vdpau-0ubunut0)

---

### Post by laffinet on 2009-08-21
Hm, I encountered another problem. Looks like I can't use xvmc anymore. When selecting the standard CPU+ profile I get a blank screen with some channels (I guess depending on the resolution). 
The frontend log tells me that xvmc-blit is not available and my display doesn't support xvmc:
> 2009-08-22 10:15:54.902 TV: Changing from None to WatchingLiveTV
2009-08-22 10:15:54.907 Realtime priority would require SUID as root.
2009-08-22 10:15:55.006 OpenGLVideoSync()
2009-08-22 10:15:55.058 Video timing method: SGI OpenGL
2009-08-22 10:15:56.737 VideoOutputXv Error: XvMC output requested, but is not supported by display.
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
/usr/lib/libXvMC.so.1: undefined symbol: XvMCCreateContext
2009-08-22 10:15:56.929 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,vdpau,xlib,' available, using 'xv-blit' instead.
2009-08-22 10:15:56.934 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-08-22 10:15:57.586 AFD: Opened codec 0xa049e50, id(MPEG2VIDEO) type(Video)

This is the playback profile I've been using all along with no problems, why is it all of a sudden not working anymore ?

---

### Post by novellahub on 2009-08-22
> **laffinet said:**
> Hm, I encountered another problem. Looks like I can't use xvmc anymore. When selecting the standard CPU+ profile I get a blank screen with some channels (I guess depending on the resolution). 
The frontend log tells me that xvmc-blit is not available and my display doesn't support xvmc:


This is the playback profile I've been using all along with no problems, why is it all of a sudden not working anymore ?

xvmc is no longer present in newer Nvidia cards.  I believe the last generation was Geforce 6 or 7.

---

### Post by jyavenard on 2009-08-22
> **laffinet said:**
> Hm, I encountered another problem. Looks like I can't use xvmc anymore. When selecting the standard CPU+ profile I get a blank screen with some channels (I guess depending on the resolution). 
The frontend log tells me that xvmc-blit is not available and my display doesn't support xvmc:


This is the playback profile I've been using all along with no problems, why is it all of a sudden not working anymore ?

VDPAU and XvMC are mutually exclusive with nvidia card.

So if your card supports VDPAU, it won't support XvMC and vice-versa.

If you want XvMC back, you will want to put back your old nvidia cards...

BTW, you should submit a bug to nvidia regarding the issue you're experiencing...

---

### Post by laffinet on 2009-08-23
Thanks for the info.

Was planning to submit a bug, just need to find the time to document it.

Do you have any suggestions on how to set up my playback profile so that I still make good use of the card until the vdpau issue is sorted ? I've been experimenting a bit but haven't really found the combination of settings that work well.

Thanks for you help.

---

### Post by jyavenard on 2009-08-23
> **laffinet said:**
> 
Do you have any suggestions on how to set up my playback profile so that I still make good use of the card until the vdpau issue is sorted ? I've been experimenting a bit but haven't really found the combination of settings that work well.


If you use my repository, it includes extra playback option using OpenGL hardware-accelerated deinterlacer.

With a 9400GT, I had excellent result (2nd best after VDPAU) using the following profile:

W <= 1920 ; H < 720: OpenGL / Kernel (2X, HW) or OpenGL / Greedy Highmotion (2x)

W > 0 ; H >= 720 : OpenGL / Kernel (2X, HW)

Greedy HighMotion 2X requires quite a fair bit a processor, if you have less than a C2D @ 2.66GHz, better of using Kernel 2X,HW

---

### Post by laffinet on 2009-08-23
What decoder where you using ? Standard (ffmpeg) ? libmpeg2 ?

---

### Post by jyavenard on 2009-08-23
ffmpeg

---

### Post by laffinet on 2009-08-24
> **jyavenard said:**
> If you use my repository, it includes extra playback option using OpenGL hardware-accelerated deinterlacer.

With a 9400GT, I had excellent result (2nd best after VDPAU) using the following profile:

W <= 1920 ; H < 720: OpenGL / Kernel (2X, HW) or OpenGL / Greedy Highmotion (2x)

W > 0 ; H >= 720 : OpenGL / Kernel (2X, HW)

Greedy HighMotion 2X requires quite a fair bit a processor, if you have less than a C2D @ 2.66GHz, better of using Kernel 2X,HW

Wow, that isn't working with my machine at all.
Greedy Highmotion produces choppy picture fullstop.

Kernel 2x,Hw works, but the CPU (AMD AM2X2 5000+) is sitting around 150% (doesn't really make sense but I guess top is looking at both cores). 
Shouldn't opengl transfer some of the load to the graphics card ? Is there a way to check if opengl is working ? Anything I need to change anywhere else ? xorg.conf ?

---

### Post by jyavenard on 2009-08-24
What is taking 150% of the CPU ?

X or mythtv?

kernel 2X takes about 65% of the CPU when watching mpeg2 1080i on my box ; it's a E8200 Intel 2.66GHz dual core.

Here is the post I made with my review of all the various deinterlacers available (that was before VDPAU time)

[http://www.nvnews.net/vbulletin/showthread.php?p=1814111#post1814111](http://www.nvnews.net/vbulletin/showthread.php?p=1814111#post1814111)

---

### Post by geekyhawkes on 2009-08-24
Slight aside, how are you guys measuring cpu loading with the front end up and running?

---

### Post by laffinet on 2009-08-24
> **jyavenard said:**
> What is taking 150% of the CPU ?

X or mythtv?


mythfrontend sits around 150% when watching TV with your settings. Opengl seems to be the issue. Any deinterlacer combined with opengl is producing this kind of CPU load on my machine.

I've also tried the vdpau renderers (combined with ffmpeg decoding), but didn't have much luck there either. 

I'm pretty much back to ffmpeg&xv-blit, which brings my CPU to 80-90%. Not ideal and I guess it doesn't really use my graphics card very well. Almost at the point of taking the card out and going back to the onboard gforce7 and xvmc. 
But I'm willing to try other options if there are any.

---

### Post by laffinet on 2009-08-24
> **geekyhawkes said:**
> Slight aside, how are you guys measuring cpu loading with the front end up and running?

I just have a terminal window open in the background and run "top" in it. Then switch to the terminal window with ALT+tab while watching TV to see the loads.

---

### Post by ktmom on 2009-08-29
Firstly - jyavenard,  Thank you so much for the time you have put into this.  

I installed a HVR-2250 using Steven Toth's drivers with no problems.  Then I installed VDPAU support. I'm appreciative of how easy it was for a relative newb to get this all running.

One question, I have had the 185.18.29 NVIDIA drivers since they came out (EV3A GeForce 8600GT).  I skipped the steps to install video drivers since I currently meet the requirement on the [Add VDPAU support to MythTV 0.21]("http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html") page.  I've read through this thread carefully though, and it appears that these may not be the best option?  I've not yet experienced and problems and under the theory of don't fix what ain't broke, I was planning to leave things be.  Any reason that I should reconsider this approach?

---

### Post by jyavenard on 2009-08-29
> **ktmom said:**
> 
One question, I have had the 185.18.29 NVIDIA drivers since they came out (EV3A GeForce 8600GT).  I skipped the steps to install video drivers since I currently meet the requirement on the [Add VDPAU support to MythTV 0.21]("http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html") page.  I've read through this thread carefully though, and it appears that these may not be the best option?  I've not yet experienced and problems and under the theory of don't fix what ain't broke, I was planning to leave things be.  Any reason that I should reconsider this approach?

If you are using my repository, you will have to use either 180.60 (release repo, recommended) or 190.25 (testing repo, unstable with vdpau).
I've only had problems with 185.18.29. They work fine as video drivers, but start using vdpau and you will get your computer crashing.

Mind you, there are issues in all those drivers.
In 180.60, the OpenGL library sometimes segfault (especially noticeable in mythmusic with the fancy libvisual based animated screen) ; but on the vdpau side of things it's very stable.

190.25 still has some known issue:
First, you must disable UseEvents : this is a problem on non-vdpau playback like Xv, without UseEvents X will take 100% of the CPU time.
You also need to disable opengl v-sync, otherwise libGL segfault
The other libGL segfault with 180.60 are gone ; but every once in a while , about once a day, two of my computers running 190.25 hang and require a power cycle.

So I still recommend you stay with 180.60, for a 8600GT card , it would make very little difference, if any

---

### Post by laffinet on 2009-08-29
> **laffinet said:**
> 
Note: mplayer also doesn't seem to keep the volume setting, ie everytime I start to watch a video it starts at full volume.

Just in case somebody is experiencing similar problems, I managed to overcome this issue (mplayer starting at a ridiculously high volume) by adding
```
-ao alsa
```
to the video player line in mythfrontend setup.

---

### Post by laffinet on 2009-08-30
Hi JY,

I'm currently running your "testing" repos (190.25 driver), with standard decoding and vdpau rendering. Since the latest update came through (this morning I think) I now have this "white dots" issue I mentioned earlier even without vdpau decoding.

However, I've got a bit more information: it's not actually white dots, it's the TV picture "showing through" in black areas.

Have a look at the attached photo. It's a photo of the TV screen while displaying a wikipedia page in firefox with mythtv running in the background. The original photo is [here]("http://en.wikipedia.org/wiki/Black")
That red and white stuff is the actual TV picture showing through.
Interestingly enough, the black square at the top of that wikipedia article displays fine, plain black, nothing showing through.

Hope this somehow helps finding the problem.

---

### Post by jyavenard on 2009-08-30
The update yesterday was about fixing a possible segfault when some custom modelines were defined with particular characters in the name.

Other than that there's been no difference...

So I believe this is purely a coincidence.

You can try reverting to the previous version if you want...

Do you have Compiz installed and running? try disabling it to see if it makes a difference.

---

### Post by laffinet on 2009-08-30
No I don't have compiz installed.

BTW, here's a snippet from my frontend log
> 2009-08-30 20:07:32.435 TV: Attempting to change from None to WatchingLiveTV
2009-08-30 20:07:32.436 Using protocol version 40
2009-08-30 20:07:33.539 DPMS Deactivated 
2009-08-30 20:07:33.549 NVP: Disabling Audio, params(-1,2,44100)
2009-08-30 20:07:33.745 OSD Theme Dimensions W: 1280 H: 720
2009-08-30 20:07:34.032 TV: Changing from None to WatchingLiveTV
2009-08-30 20:07:34.034 Realtime priority would require SUID as root.
2009-08-30 20:07:34.149 Video timing method: USleep with busy wait
2009-08-30 20:07:36.679 AFD: Opened codec 0xaae05c40, id(MPEG2VIDEO) type(Video)
2009-08-30 20:07:36.679 AFD: codec AC3 has 6 channels
2009-08-30 20:07:36.680 AFD: Opened codec 0xaae09770, id(AC3) type(Audio)
2009-08-30 20:07:36.711 Opening audio device 'default'. ch 2(2) sr 48000
2009-08-30 20:07:36.711 Opening ALSA audio device 'default'.
2009-08-30 20:07:36.777 Mixer unable to find control Master
2009-08-30 20:07:36.777 Mixer unable to find control Master
2009-08-30 20:07:36.778 NVP: Enabling Audio
2009-08-30 20:07:36.915 NVP: prebuffering pause
2009-08-30 20:07:48.774 TV: Attempting to change from WatchingLiveTV to None
2009-08-30 20:07:49.185 TV: Changing from WatchingLiveTV to None
2009-08-30 20:07:49.281 DPMS Reactivated.

---

### Post by jyavenard on 2009-08-30
You'll have to see if going back to the earlier version fix it for you...

But I can't think of any reasons why it should ...

---

### Post by geekyhawkes on 2009-08-30
I am slightly confused as to why my vdpau comes up with so many "artifacts" during playback.  I am running 180.60nvidia drivers and have setup the playback settings as described here.  If i use cpu++ my average cpu loading during live tv playback is around 18%. If i use high quality i get around 48-50%cpu loading. With vdpau selected i get lots of artifacts on all channels (that are no there without vdpau) but reduced cpu loading down to around 6% average. 

My GPU (8300) is onboard my motherboard but isnt supported by the underclocking util so Im guessing i am kind of stuck as to getting vdpau working.

Is there any problem with running 50%cpu loading during livetv playback?  Using highquality does seem to have solved the audio "clicking" i was getting during live tv in cpu++, but obviously does have a higher cpu loading to boot.

Incase it matters im using 9.04 64bit on an AMD 64 5050e (dual core 2.6GHz) with 2gbram so should be up to the job of a media center combined front/back end.

---

### Post by jyavenard on 2009-08-30
what do you mean by "artifacts" ?

---

### Post by geekyhawkes on 2009-08-30
like very large pixcels appearing on the screen (similar to those displayed during very bad reception), except they are only present with vdpau selected and not with high quality or cpu++.  They are worse when the picture is high speed (such as the f1) but present around all moving objects as very large square over sized pixcels.

---

### Post by laffinet on 2009-08-30
Do these "large pixels" disappear during almost static pictures (eg a newsreader in front of a static background) ? 
And reappear once the scene changes (eg the news cut to a report)?

---

### Post by jyavenard on 2009-08-30
> **geekyhawkes said:**
> like very large pixcels appearing on the screen (similar to those displayed during very bad reception), except they are only present with vdpau selected and not with high quality or cpu++.  They are worse when the picture is high speed (such as the f1) but present around all moving objects as very large square over sized pixcels.

Which version of MythTV are you using?

From my 0.21-fixes repository or something else ?

---

### Post by geekyhawkes on 2009-08-31
Exactly as decribed by laffinet above.  I am using myth from your repos as listed earlier in this thread.  I then ran apt-get update / upgrade and created a vdpau display profile for live tv.

---

### Post by williammanda on 2009-09-02
My thanks for the ease of the setup and changeover. I have a C2Q 9300 and 1 of the cpus was at 100% and now is at the 5% range. I have one piece of information. It seems that you would need to stop mythtvbackend before the change. I got a message that it couldn't install mythbackend but things seems to work anyway.
Thanks

---

### Post by hackmeister on 2009-09-02
VDPAU is simply amazing. HD playback of h264 and mpeg2 files with 5% CPU usage! I recently built a small form factor frontend based on a Zotac Ionix AU motherboard and have been very happy with it using VDPAU. I was so happy I unloaded my Popcorn Hour box since the Zotac box replaced it.

---

### Post by novellahub on 2009-09-04
VDPAU has been working great for me as well.  Yesterday I set up a Frontend using the ECS GF8200A motherboard and Phenom X4 9150e processor.  I am getting 5% to 7% CPU usage using Temporal 2X or Bob 2X.

---

### Post by bcg30506 on 2009-09-06
> **mathog said:**
> Same config and graphics card (256MB model for me) and same good result.  Excellent work.  Much praise to jyavenard.

With vdpau enabled the pauses I used to see when using the program guide while TV was running went away.  On the other hand, so did the live TV that used to be visible at the same time the guide was up.  

The only glitch I have seen so far concerns PIP, where sometimes it comes up with H = 2W (stretched vertically), instead of H = W.  Oddly the stretched one uses much less CPU time than the rectangular one, which tends to push to 50-60% CPU, where regular TV (one stream) is <=10%.  Also the front end hung up for a longish time once when trying to switch PIP streams.

VDPAU + mythtv is definitely a big win.

THANKS!
PIP does not really work for me with VDPAU.  It technically does show the other tuner in a window, but the window is almost in the middle of the screen and is no larger than a dime.  I run at 1920x1080 res.  When I change my profile to Slim instead, PIP works great.  The window is just under 1/4 the size of the screen and is in the bottom left position where I have it setup to be.

---

### Post by nickrout on 2009-09-06
> **bcg30506 said:**
> PIP does not really work for me with VDPAU.  It technically does show the other tuner in a window, but the window is almost in the middle of the screen and is no larger than a dime.  I run at 1920x1080 res.  When I change my profile to Slim instead, PIP works great.  The window is just under 1/4 the size of the screen and is in the bottom left position where I have it setup to be.

My understanding is that vdpau can only open one video 'surface' at a time, so PIP is not going to work as expected.

---

### Post by bcg30506 on 2009-09-06
> **nickrout said:**
> My understanding is that cdpau can only open one video 'surface' at a time, so PIP is not going to work as expected.
Okay.  Thanks for the explanation.  I'll just keep using the Slim profile for TV and switch it back to VDPAU for watching my HD videos.  Any chance there is a one key shortcut for getting to the setup screen?

---

### Post by nickrout on 2009-09-06
> **bcg30506 said:**
> Okay.  Thanks for the explanation.  I'll just keep using the Slim profile for TV and switch it back to VDPAU for watching my HD videos.  Any chance there is a one key shortcut for getting to the setup screen?

you could set up a button on your main menu like:

<button>
	      <type>TV_SETTINGS_PLAYBACK</type>
	      <text>Playback</text>
	      <action>SETTINGS PLAYBACK</action>
</button>

Which would take you straight to the Playback settings menu.

---

### Post by bcg30506 on 2009-09-07
> **nickrout said:**
> you could set up a button on your main menu like:

<button>
	      <type>TV_SETTINGS_PLAYBACK</type>
	      <text>Playback</text>
	      <action>SETTINGS PLAYBACK</action>
</button>

Which would take you straight to the Playback settings menu.

Awesome. You rock. Thanks!
(Wouldn't be possible to map this to a remote key to jump from anywhere would it?  Just checking.)

---

### Post by trevs.bronco on 2009-09-08
I want to try VDPAU as HD playback isn't working too well on my new Zotac ION based frontend. the first and hopefully only issue I need to solve is how to enable the Nvidia 185.18.31 driver that I have installed, it does not show up in System > Hardware Drivers, but it is listed in Settings > Nvidia X Server Settings.

Can someone please show me the way.
Thanks,
Trev

---

### Post by dano1 on 2009-09-08
> **trevs.bronco said:**
> I want to try VDPAU as HD playback isn't working too well on my new Zotac ION based frontend. the first and hopefully only issue I need to solve is how to enable the Nvidia 185.18.31 driver that I have installed, it does not show up in System > Hardware Drivers, but it is listed in Settings > Nvidia X Server Settings.

Can someone please show me the way.
Thanks,
Trev

download nvidia modaliases through synaptic. How did you install? sounds like the drivers are in use.

---

### Post by trevs.bronco on 2009-09-08
there is not a nvidia modaliases package available for my driver version. So what is the next step. I was unable to install the drivers automatically or through the instructions on Nvidia's website so I had to do it following [this]("http://ubuntuforums.org/showthread.php?t=1125400&highlight=install+nvidia+proprietary%2C+drivers") how to I found in the forums.

Trev.

---

### Post by dano1 on 2009-09-09
you don't show 185modaliases in synaptic? do you have proprietary drivers checked in software sources ?

---

### Post by bcg30506 on 2009-09-09
> **nickrout said:**
> My understanding is that vdpau can only open one video 'surface' at a time, so PIP is not going to work as expected.

I think I know the answer to this, but will this also impact the live TV window in the Program Guide?  It does not seem to work with VDPAU but does with CPU+ or Slim.  Based upon all this, do you think it will ever be possible so we don't lose features to get HW acceleration, or is this a technological limitation we just are stuck living with forever?

---

### Post by williammanda on 2009-09-09
I'm not sure if the the VDPAU upgrade did this but mythwweather no longer displays any info. See my detailed post here:

[http://ubuntuforums.org/showthread.php?t=1260567]("http://ubuntuforums.org/showthread.php?t=1260567")

I saw in another post on mythweather problems that the author of this VDPAU upgrade conceded that it did cause a problem but I'm not sure about the fix.
Any ideas?
Thanks

---

### Post by trevs.bronco on 2009-09-11
Ok, I upgraded mplayer with Jean-Yves repository using ```
apt-get update
apt-get upgrade
```and then configured myth frontend for play back using VDPAU as per [http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html](http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html) It did not work for some reason, the error messages said i needed to recompile it so I did using [this]("http://blog.avirtualhome.com/2009/05/29/how-to-compile-mplayer-with-vdpau-support-on-ubuntu/") tutorial. I tried it and it gave me a blank scren and I could not exit it or even kill it from top. so I recompiled it again and then it would not even start up at all. so I removed it, reinstalled it from Jean-Yves repository, still can not get it to run. I tried it from a terminal and recieved a message that it could not connect to a socket and that the file I was trying to play did not exist. i triple checked that it was correct and tried another file and same result.
Anyone else have this happen and/or know how to correct it?

Trev

---

### Post by trevs.bronco on 2009-09-11
some other peculiar behavior is that Mplayer still works in myth but will not playback HD content only SD, but there is no sound. I do get sound when watching live TV or outside of myth. all my settings are the same as they were before.

Trev

---

### Post by laffinet on 2009-09-11
Can you post the command you were using to play the video file ?

Plus the line in mythfrontend setup for video playback.

---

### Post by trevs.bronco on 2009-09-11
the command was just mplayer /file/path/file_name
the line from Myth is the default of mplayer -fs -zoom -quiet -vo xv %s

Trev

---

### Post by laffinet on 2009-09-12
This will probably have nothing to do with your problems but you're not using vdpau with mplayer. To do that your command line will have to look like this

```
mplayer -fs -vo vdpau -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, file.ext

```

For myth:

```
mplayer -fs -zoom -quiet -vo vdpau -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,

```

---

### Post by dano1 on 2009-09-12
i wouldn't apply patches, just recompile using his repos. am using 190 beta drivers from jeans repos(testing) and found them to be much more stable than the 185 drivers fwiw. as said you must create a vdpau playback profile to utilize it. 

Also if your drivers are showing in your xserver settings  it sounds like your using them, even though they aren't showing under hardware drivers. happened to me and i was missing the modaliases, but still using the new/upgraded drivers iirc.

---

### Post by korgman on 2009-09-12
I just did a fresh mythbuntu 9.04 install and immediately upgraded to VDPAU using jyavenard's repo.  Most of the time it works fine, but sometime the frontend gets into trouble.  I have a plethora of errors and crashes when watching LiveTV or recordings.  Here's some:

Watching Live TV mythfronend.log
```
2009-09-12 08:47:28.868 NVP: Error condition detected in videoOutput after Show(), aborting playback.
2009-09-12 08:47:28.868 VideoOutputXv Error: IsErrored() in ProcessFrame()
2009-09-12 08:47:28.868 NVP, Error: AVSync: Unknown error in videoOutput, aborting playback.
2009-09-12 08:47:28.868 ~OpenGLVideoSync() -- begin
2009-09-12 08:47:28.868 ~OpenGLVideoSync() -- middle
2009-09-12 08:47:28.868 TV: Attempting to change from WatchingLiveTV to None
2009-09-12 08:47:28.918 ~OpenGLVideoSync() -- end
2009-09-12 08:47:28.937 VDPAU Error: DISPLAY PRE-EMPTED. Aborting playback.

```
Blue screen "Return to Menu"


Or this while watching prerecorded programs:
```
2009-09-12 08:49:44.823 TV: Changing from None to WatchingPreRecorded
2009-09-12 08:49:44.823 The realtime priority setting is not enabled.
2009-09-12 08:49:44.897 VDPAU Error: Picture format has changed.
2009-09-12 08:49:44.923 OpenGLVideoSync()
2009-09-12 08:49:44.949 Video timing method: SGI OpenGL
2009-09-12 08:49:45.016 VDPAU Error: Picture format has changed.
2009-09-12 08:49:45.018 VDPAU Error: Picture format has changed.
2009-09-12 08:49:45.024 VDPAU Error: Picture format has changed.
2009-09-12 08:49:45.037 VDPAU Error: DISPLAY PRE-EMPTED. Aborting playback.
2009-09-12 08:49:45.066 VideoOutputXv Error: IsErrored() in ProcessFrame()
2009-09-12 08:49:45.066 NVP, Error: AVSync: Unknown error in videoOutput, aborting playback.
2009-09-12 08:49:45.066 VideoOutputXv Error: IsErrored() in ProcessFrame()
2009-09-12 08:49:45.066 NVP, Error: AVSync: Unknown error in videoOutput, aborting playback.
2009-09-12 08:49:45.066 ~OpenGLVideoSync() -- begin
2009-09-12 08:49:45.066 ~OpenGLVideoSync() -- middle
2009-09-12 08:49:45.066 TV: Attempting to change from WatchingPreRecorded to None
2009-09-12 08:49:45.066 ~OpenGLVideoSync() -- end
```
Blue screen - "Return to Main Menu"


Or sometimes I get this and the frontend crashes:
```
2009-09-09 22:38:15.457 NVP: Prebuffer wait timed out 20 times.
mythfrontend.real: ../../src/xcb_io.c:176: process_responses: Assertion `!(req && current_request && !(((long) (req->sequence) - (lon
g) (current_request)) <= 0))' failed.
Starting mythfrontend.real..

```

Any ideas?  My xorg is barely touched from the installation, but I'll post it:
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"UseEvents"	"1"
	Option	"DPI"	"100x100"
	Option	"NoLogo"	"1"
        Option  "TripleBuffer" "True"
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

-Matt

---

### Post by Cuppa-Chino on 2009-09-19
Hi,

i totally don't want to hijack this but have a questin. I had a manual installation of 185.18 drivers with which vdpau worked. it made a mess of every kernel upgrade etc, so I decided to go back to 180.60 package and try the trunk repo by the esteemed JYA.

Now vdpau no longer initialises - not sure if this is the right word but that is what it feels like:

```
mplayer -fs -vo vdpau -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, a.ts
MPlayer UNKNOWN-4.3.3 (C) 2000-2009 MPlayer Team
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick

Playing a.ts.
TS file format detected.
VIDEO H264(pid=720) AUDIO MPA(pid=730) NO SUBS (yet)!  PROGRAM N. 1031
FPS seems to be: 25.000000
**[vdpau] Error when calling vdp_device_create_x11: 1**
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:55542.0 (15:25:41.9) of 1074.8 (17:54.7)  1.1% 

MPlayer interrupted by signal 2 in module: play_audio
A:55542.0 (15:25:41.9) of 1074.8 (17:54.7)  1.2% 
Exiting... (Quit)

```

same thing also appears with myth

when I run the vdpau info tool, or rather try and autogen the latest version 0.0.6:
```
checking for VDPAU... configure: error: Package requirements (x11 vdpau >= 0.2) were not met:

No package 'vdpau' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables VDPAU_CFLAGS
and VDPAU_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I have tried to see how to find what to do but am at a bit of a loss (and yes I have reinstalled libvdpau and all 180.60 files a couple of times)

any help very welcome

---

### Post by Cuppa-Chino on 2009-09-19
half between a note to self and a help for anyone else who might run into to this (yes I managed to fix it!)

first all my libvdpau symlinks were busted, I just manually started hunting for all the old versions and then replaced them with the links to 180.60 version:

check this in /usr/lib/ (and lib32 and lib64 if needed) ```
ls -l | grep vdpau
```
that spat out wrong links, which I delete with sudo rm xyz and rebuilt with sudo ln -s libvdpau_xyz.180.60 libvdpau_xyz (of course xyz stands for a numer of different libs)

then I ran into the problem that I could not open the nvidiactl 
```
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
```

check that /lib/udev/rules.d/50-udev-default.rules has an Nvidia block that contains that nvidiactl and points to video group

mine looks like this:
```
# graphics
KERNEL=="agpgart",		MODE="0600", GROUP="video"
KERNEL=="card[0-9]*",		NAME="dri/%k"
KERNEL=="pmu",			GROUP="video"
KERNEL=="nvidia*|nvidiactl*",	GROUP="video"
SUBSYSTEM=="graphics",		GROUP="video"
SUBSYSTEM=="drm",		GROUP="video"
```

after I checked that access to the video device was fixed by adding the required user to the video group

```
sudo usermod -a -G video YOURUSERNAME
```
check with
```
grep video /etc/group
```

reboot

---

### Post by korgman on 2009-10-03
I just downloaded the deb package mythbuntu-repos_2-0ubuntu0+mythbuntu5_all.deb and installed that, selected "weekly builds", and did an update. It looked like it updated some nvidia and vdpau stuff.

Now when I try to start mythfrontend all I get is:
Code:

```
/usr/bin/mythfronend.real: error while loading shared libraries: 
libvdpau.so.1: cannot open shared object file: No such file or directory
```

myth will no launch. Any ideas?

---

### Post by Bachstelze on 2009-10-03
> **korgman said:**
> I just downloaded the deb package mythbuntu-repos_2-0ubuntu0+mythbuntu5_all.deb and installed that, selected "weekly builds", and did an update. It looked like it updated some nvidia and vdpau stuff.

Now when I try to start mythfrontend all I get is:
Code:

```
/usr/bin/mythfronend.real: error while loading shared libraries: 
libvdpau.so.1: cannot open shared object file: No such file or directory
```

myth will no launch. Any ideas?

You need nvidia-180-libvdpau.

---

### Post by korgman on 2009-10-03
OK, this is what I get

```
sudo apt-get install nvidia-180-libvdpau
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-180-libvdpau is already the newest version.
The following packages were automatically installed and are no longer required:
  update-inetd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mythtv-backend (2:0.21.0+fixes-21583-openglvdpau2-nv180-0ubuntu2) ...
 * Starting MythTV server: mythbackend                                                                                                    /usr/bin/mythbackend: error while loading shared libraries: libvdpau.so.1: cannot open shared object file: No such file or directory
invoke-rc.d: initscript mythtv-backend, action "start" failed.
dpkg: error processing mythtv-backend (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-backend (= 2:0.21.0+fixes-21583-openglvdpau2-nv180-0ubuntu2); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-backend (= 2:0.21.0+fixes-21583-openglvdpau2-nv180-0ubuntu2); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                          Errors were encountered while processing:
 mythtv-backend
 mythtv
 mythtv-backend-master
E: Sub-process /usr/bin/dpkg returned an error code (1)
matt@mythtv:~$ 

```

Now I see that earlier, jyavenard warned :
> Warning, do not activate the mythbuntu weekly build repository. The weekly repository is updated every week, and due to the nature of SVN ; each week the version number will increase ; even if there has been no changes in Mythtv 0.21-fixes.
If you activate the mythbuntu weekly build, it is likely that at some stage the weekly repository will update mythtv and will remove the VDPAU mods.

Well this is exactly what I did, and its turned my libraries into a hodgepodge mess of I don't know what.  I didn't realize that enabling weekly builds would mess up the vdpau stuff, so how do I just get back to a working system?

---

### Post by nickrout on 2009-10-03
> **korgman said:**
> OK, this is what I get

```
sudo apt-get install nvidia-180-libvdpau
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-180-libvdpau is already the newest version.
The following packages were automatically installed and are no longer required:
  update-inetd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mythtv-backend (2:0.21.0+fixes-21583-openglvdpau2-nv180-0ubuntu2) ...
 * Starting MythTV server: mythbackend                                                                                                    /usr/bin/mythbackend: error while loading shared libraries: libvdpau.so.1: cannot open shared object file: No such file or directory
invoke-rc.d: initscript mythtv-backend, action "start" failed.
dpkg: error processing mythtv-backend (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-backend (= 2:0.21.0+fixes-21583-openglvdpau2-nv180-0ubuntu2); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-backend (= 2:0.21.0+fixes-21583-openglvdpau2-nv180-0ubuntu2); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                          Errors were encountered while processing:
 mythtv-backend
 mythtv
 mythtv-backend-master
E: Sub-process /usr/bin/dpkg returned an error code (1)
matt@mythtv:~$ 

```

Now I see that earlier, jyavenard warned :


Well this is exactly what I did, and its turned my libraries into a hodgepodge mess of I don't know what.  I didn't realize that enabling weekly builds would mess up the vdpau stuff, so how do I just get back to a working system?

Take the weekly repo out of your list of sources. Remove all mythtv packages and reinstall it.

---

### Post by jyavenard on 2009-10-03
> **nickrout said:**
> Take the weekly repo out of your list of sources. Remove all mythtv packages and reinstall it.

If you are using my nvidia driver packages ; to be able to use mythbuntu default packages you need to install the libvdpau0 package.

I explained why here:
[http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/10/4_VDPAU_packages.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/10/4_VDPAU_packages.html)

All the vdpau related packages on my repository are currently being rebuilt, there's a few of them so it takes a while...

Installing libvdpau0 + nvidia-xxx-libvdpau on my repo is all you need to keep compatibility with mythbuntu packages.
If using my repository it's all automatic

---

### Post by mars76 on 2009-12-05
Hi,

  I had the VDPAU working till i updated my Drivers..

 My avenard packages are update date i am using the version 22952. After the update my CPU usage for mythbackend is now showing as 100%

Here are the versions of various drivers/modules i have

libvdpau1                    0.3-0ubuntu3
libvdpau0                    0.2-0ubuntu11
libvdpau-dev               0.3-0ubuntu3
vdpau-driver-all           0.3-0ubuntu3
nvidia-195-libvdpau    195.22-0ubuntu3

i checked the logs and i see the following error:

```

AFD: Opened codec 0x8e24750, id(H264) type(Video)
2009-12-05 21:00:13.038 AFD: codec AAC has 2 channels
2009-12-05 21:00:13.072 AFD: Opened codec 0x8e26790, id(AAC) type(Audio)
2009-12-05 21:00:13.278 AFD Error: Unknown decoding error
2009-12-05 21:00:13.365 [h264 @ 0x3bf8620]illegal short term buffer state detected
2009-12-05 21:00:13.406 AFD Error: Unknown decoding error

```

thanks
mars

---

### Post by laffinet on 2010-02-24
Time to celebrate: there finally seems to be a solution for those of us that suffer from "random blocks" or artefacts when playing mpeg2 with vdpau:

See [this ]("http://www.nvnews.net/vbulletin/showpost.php?p=2181650&postcount=41")post at the nvidia forums.

Basically involves using the lates beta driver 195.36.03 and using a modified library.

I applied the change yesterday and so far everything seems to be working well :D

---

### Post by newlinux on 2010-06-12
> **laffinet said:**
> Time to celebrate: there finally seems to be a solution for those of us that suffer from "random blocks" or artefacts when playing mpeg2 with vdpau:

See [this ]("http://www.nvnews.net/vbulletin/showpost.php?p=2181650&postcount=41")post at the nvidia forums.

Basically involves using the lates beta driver 195.36.03 and using a modified library.

I applied the change yesterday and so far everything seems to be working well :D

I know this thread is old but I found it when googling. I'm using 195.36.15 and I still have the artifact problem with mpeg-2 recordings. Is the fix in that driver or is a patch available for that driver?

---

### Post by rulet on 2010-06-12
To not have artifacts some people say to write vdpaubuffersize=50 in Custom filters of TV Setting. So I've tried to do that... but when I check if this setting is saved there(and I saved) but there is nothing there, so what I have wrote(vdpaubuffersize=50) it is not saving there...
Why is that? I cannot find answers anywhere.

---

### Post by newlinux on 2010-06-12
> **rulet said:**
> To not have artifacts some people say to write vdpaubuffersize=50 in Custom filters of TV Setting. So I've tried to do that... but when I check if this setting is saved there(and I saved) but there is nothing there, so what I have wrote(vdpaubuffersize=50) it is not saving there...
Why is that? I cannot find answers anywhere.

I was able to put in the vdpaubuffersize=50 (and it saved) but it didn't help me. I don't think buffer or memory is the issue I'm running into. 

Did you save it there, and then next all the way through the settings to finish?

---

### Post by rulet on 2010-06-12
Yes of course I saved it to finish, but it is not saving -- cannot even imagine why is that.
I searched everywhere -- some tells it is something with permissions to database, but how to get that permissions?, if this a problem of course.
I see you don't use nvidia card(or onboard like ION with 9400M) -- so you will not be able to use vdpau hardware acceleration.

---

### Post by newlinux on 2010-06-12
> **rulet said:**
> Yes of course I saved it to finish, but it is not saving -- cannot even imagine why is that.
I searched everywhere -- some tells it is something with permissions to database, but how to get that permissions?, if this a problem of course.
I see you don't use nvidia card(or onboard like ION with 9400M) -- so you will not be able to use vdpau hardware acceleration.

where do you see that? Of course I'm talking about VDPAU capable nvidia cards. (8400GS and ION and G210) I've been using it, that's how I know about the problem with it.

check your frontend logs - that will tell you if there is a permissions problem with saving settings to the DB.

---

### Post by rulet on 2010-06-13
This what shows terminal when I saving that setting:
```
2010-06-13 11:21:33.841 mythfrontend version: branches/release-0-23-fixes [25073] www.mythtv.org
2010-06-13 11:21:33.842 Using runtime prefix = /usr
2010-06-13 11:21:33.842 Using configuration directory = /home/r/.mythtv
2010-06-13 11:21:34.276 Empty LocalHostName.
2010-06-13 11:21:34.276 Using localhost value of NGF
2010-06-13 11:21:34.284 New DB connection, total: 1
2010-06-13 11:21:34.287 Connected to database 'mythconverg' at host: localhost
2010-06-13 11:21:34.289 Closing DB connection named 'DBManager0'
2010-06-13 11:21:34.308 ScreenSaverX11Private: Gnome screen saver support enabled
2010-06-13 11:21:34.309 DPMS is disabled.
2010-06-13 11:21:34.311 Primary screen: 0.
2010-06-13 11:21:34.312 Connected to database 'mythconverg' at host: localhost
2010-06-13 11:21:34.313 Using screen 0, 1440x900 at 0,0
2010-06-13 11:21:34.336 Desktop video mode: 1440x900 59.891 Hz
2010-06-13 11:21:34.366 MythUI Image Cache size set to 20971520 bytes
2010-06-13 11:21:34.400 AudioPulseUtil: Suspend Success
2010-06-13 11:21:34.401 Enabled verbose msgs:  important general
2010-06-13 11:21:34.408 Primary screen: 0.
2010-06-13 11:21:34.409 Using screen 0, 1440x900 at 0,0
2010-06-13 11:21:34.410 Using theme base resolution of 1280x720
2010-06-13 11:21:34.417 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: ÐÐµÑ&#130; Ñ&#130;Ð°ÐºÐ¾Ð³Ð¾ Ñ&#132;Ð°Ð¹Ð»Ð° Ð¸Ð»Ð¸ ÐºÐ°Ñ&#130;Ð°Ð»Ð¾Ð³Ð° (2)
2010-06-13 11:21:34.417 JoystickMenuThread Error: Joystick disabled - Failed to read /home/r/.mythtv/joystickmenurc
2010-06-13 11:21:34.459 Using Frameless Window
2010-06-13 11:21:34.460 Using Full Screen Window
2010-06-13 11:21:34.649 Using the Qt painter
2010-06-13 11:21:34.866 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-06-13 11:21:34.886 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-06-13 11:21:34.904 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-06-13 11:21:34.904 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-06-13 11:21:34.916 Current MythTV Schema Version (DBSchemaVer): 1254
2010-06-13 11:21:35.413 Registering Internal as a media playback plugin.
2010-06-13 11:21:35.450 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-13 11:21:35.450 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-13 11:21:35.450 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-13 11:21:35.451 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-06-13 11:21:35.475 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-06-13 11:21:35.527 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-06-13 11:21:35.537 Cannot load language ru for module mythmusic
2010-06-13 11:21:35.547 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-06-13 11:21:35.582 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-06-13 11:21:35.677 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-06-13 11:21:35.681 Found mainmenu.xml for theme 'Mythbuntu'
2010-06-13 11:21:36.452 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-06-13 11:21:36.453 Using protocol version 56
2010-06-13 11:21:39.149 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-06-13 11:21:40.208 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-06-13 11:21:41.471 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//tv_settings.xml
2010-06-13 11:22:34.789 New DB connection, total: 2
2010-06-13 11:22:34.790 Connected to database 'mythconverg' at host: localhost
2010-06-13 11:22:34.790 New DB connection, total: 3
2010-06-13 11:22:34.791 Connected to database 'mythconverg' at host: localhost
2010-06-13 11:22:34.992 Received a remote 'Clear Cache' request
2010-06-13 11:22:39.288 AudioPulseUtil: Resume Success
2010-06-13 11:22:39.288 Deleting UPnP client...
r@NGF:~$ 

```

---

### Post by rulet on 2010-06-14
It'is o'key now, I just was confusused with mythtv interface...
In my case vdpaubuffersize=50 works...

---

### Post by newlinux on 2010-06-14
> **rulet said:**
> It'is o'key now, I just was confusused with mythtv interface...
In my case vdpaubuffersize=50 works...

I didn't see anything in that log that indicated it couldn't access the DB, so I'm glad it is working. It might help others if you explain what you were doing wrong...

---

### Post by rulet on 2010-06-15
:???: The thing is I just was adding "New Entry" in vdpau profile of "TV settings" and every time I pressed on "New Entry" iterface button I thought
that I editing current Entry. I was just to CHANGE current entry and to write in Custom filter vdpaubuffersize=50 and save it. And because I was adding every time new entry of course in Custom filter was nothing...

---

### Post by rulet on 2010-06-15
And I have a question to you -- does subtitles shows when you are playing mkv in mythvideo with internal player? I mean not external subtitles but that which is inside mkv. Or in mythvideo it is impossible for now in current 0.23 realise of mythtv?
I can't find any information about it.

---

### Post by newlinux on 2010-06-15
I think I used to have problems with internal subtitles in mkvs in myth .21, and thus I always used mplayer for those... Not sure about .23. Googling tells me it is hit and miss.

---

