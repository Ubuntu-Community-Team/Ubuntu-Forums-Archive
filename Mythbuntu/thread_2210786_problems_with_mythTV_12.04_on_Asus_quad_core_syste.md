---
title: "problems with mythTV 12.04 on Asus quad core system, Hauppauge pvr usb2"
date: 2014-03-12
forum: Mythbuntu
---

### Post by Johnathon_Galtman on 2014-03-12
Hello folks,

I'm an experienced Linux user going way back to the 90s, SW / dev by trade. But I'm new to MythTV (not to Ubuntu in it's many variants; Mint is my fav tho).

My video tears like it looses sync occasionally, enough to make it unusable. I suspect an issue with the harddisk but I'm not sure.

Using the exact same hardware I get clear video without any issues whatsoever, under a Windoze XP guest OS (VirtualBox) on a Windoze 7 host.

The HW specs of my system are: Asus Ma785M mobo w/8GB of ddr2 RAM, AMD quad core CPU at 2.4Ghz, sda: 500GB Segate SATA, sdb: 1TB SATA refurb. drive (unknown manufacturer), a Pioneer BluRay SATA drive, a Hauppauge PVR USB 2 video capture (old school 4:3 aspect ratio, newer H/W version 24000 not 29000), Actisys IR200L IR blaster (not setup yet, but hoping this will work with MythTV).

This machine is a real MULTIboot system (OpenSuSE 12.2, Ubuntu 12.10, Mint 13, Mint 16, Bhodi Linux 2.2, Windows 7, Windows XP), plus several operating systems run guest OSs under virtualBox.

I suspect the harddisk since when I run the Hauppauge software under the Windows XP Virtual Machine I am not recording the data to disk, just viewing it. If it were going to disk behind the scenes, it would be to the SATA 1 (Seagate drive sda) disk, while under MythTV it's going to the 1TB SATA 2 drive on stb. Aside from that and the obvious differences in software I see no differences in hardware.

As a test I may reconfigure mythTV to save video to the Seagate drive and see if it works better. But frankly, my disk benchmarks show the 1 TB drive to perform as good if not slightly better than the Seagate drive so I am a bit skeptical it's the disk.

Oh, I forgot a really important point: I installed Myth from the Mythbunu 12.04 ISO, and (since I failed to see the selection for boot disk) clobbered my nice multiboot  GUI created with OpenSuSE. So I booted OpenSuSE and ran grub2-install to fix it, which added the Mythbuntu installation via os_prober. 

So if any of you gurus care to comment on what I should do to resolve my (intermittent) loss of video sync I'm all ears. Barring any progress on this problem I will try to find a better capture device, which means waiting for several months (at least) to come up with the funds.

PS: Myth doesn't seem to play either DVDs or BluRay disks from the Optical menu selection, although I elected to load the codecs during installation. I know getting BuRay working is a bit of a pain. I did it under OpenSuSE and Windoze 7 using VLC but it took some research and effort to accomplish. Has anyone done it under MythV? Does MythTV use an internal player or external, like VLC or mPlayer?

PS2: I forgot to mention, that the pvrusb linux driver seems to detect my Hauppauge just fine, but do I need to load different firmware for it or does the driver take care of that automatically? I don't see any errors in dmesg, tho I do see the driver go through what seems to be initialization twice, with the first time ending with something like "unloading device video0" and "the same for radio0. Second time thru is fine, otherwise MythTV wouldn't display the video feed at all.

Thanks!

---

### Post by Johnathon_Galtman on 2014-03-15
I see my post has plenty of views, but nobody has any thoughts? I tried changing the recording location to the other disk but that didn't help.

With an ISO built for the sole purpose of installing mythTV, I would hope there would be more help (man pages, info or html) installed, but can't seem to find much. In fact I had some difficulty figuring out how to change the recording location. The backend setup allows for ADDing new locations but no facility I could figure out on how to remove any. I also used find to locate where in the filesystem those settings were, but I'm betting the answer is they're in the DB NOT in an XML file or other config.

---

### Post by blm-ubunet on 2014-03-15
The video tearing (horizontal discontinuity/offset) is caused by screen/display buffer redrawing being to slow or incorrectly timed w.r.t. screen refresh rate.
The setting sync to vertical blank should be set (somewhere in graphics driver settings).
Never used AMD GPU or radeon so can't help..
The solution can depend on what video h/w & driver..You are probably better using FOSS radeon & VDPAU decode/rendering in MythTV (if possible).

Other snags can be related to composite effects manager:
- redirecting full screen (compiz)
- incorrect refresh rate reporting (compiz)
Can completely disable composite effects but this should not be necessary with any modern h/w.

Mythtv has a OSD jitterometer to help check playback performance.
Check decoder is not emptying buffer, check frame timing jitter mean & std-dev.

Storage groups..
Hit <d> or <m> ...you can delete them..
I mount recording HDDs in to /mnt/storageN & the storage group are /mnt/storageN/recordings/..
Don't write recording files into root of mounted HDDs.

BD (bluray) playback in mythtv uses internal player or mythavtest.
Neither support menus..XBMC does.
To play BDs with AACS MKB > version28 you need to use 3rd party tools, none are free.
MakeMKV alternative system library (symlinks) approach works well.
Check the mythtv wiki..

---

### Post by Johnathon_Galtman on 2014-03-15
Hey thanks [**[COLOR=#000000]blm-ubunet[/COLOR]**]("http://ubuntuforums.org/member.php?u=1899844") for your input. Some of what you said I understand, other parts not so much. But I hadn't yet visited the wiki so thanks for that too. Surprised about the BD as I had it working under OpenSuSE & Windows, but if the version 28 you're referring to is for recent BDs I think I know what you mean; I had to load a memory resident (tho free) tool before playing the BD which required being connected to Internet to work.

---

### Post by blm-ubunet on 2014-03-15
Concentrating on the video tearing problem..
I read that the radeon driver (FOSS) has vsync set by default..

```
glxinfo | grep -i opengl
```

Believe that you can use "driconf" GUI tool to control the radeon driver settings.

What playback profile are you using in mythtv?
Have you tried the video playback test in myth FE setup?
Have you tried to debug video playback with mplayer? It allows you to set vcodec & voverlay method.

Mythbuntu follows LTS release so the xorg/radeon code is old. You could try xorg-edgers ppa or just wait for 14.04-LTS.
There has been a lot of good progress with the FOSS driver including VDPAU decode (h/w dependent).

---

### Post by Johnathon_Galtman on 2014-03-16
Thanks again blm-ubunet for your reply and assistance. I am online today to do further research and get up to speed on mythtv.

Although the mobo has Radeon video built in, I'm using an Nvidia Geforce 520 card and the mobo video is disabled. I believe I elected the third party (no free) driver at install time but I actually don't recall for sure, truth be told.

The playback profile is "normal" (probably whatever the default is as I didn't spend much time in the frontend setup). I tried several others, primarily VDPAU settings, all with the same result. 

In both frontend and backend if I didn't understand what a setting was for and couldn't find info about it easily I left it alone. I did read about card selection on the pvrusb2 driver website and the need to set the type to an mpeg decoder rather than the default raw video frame grabber. Had I not found that I probably would have been quite lost.

I didn't try the playback test, b/c I currently only have a 500MB limit on my cell phone, which is the only Interne connection I have and I didn't want to use it up for a test. That should be built in and not online. I haven't tried mplayer yet, but I did try vlc. However I didn't have the info on the Hauppauge commands (to turn it on, set input source etc) so video was available. 

There are alot of details that I need to come up to speed on. 

FYI, not spending much time on this but I noticed it as I was reading. According to this page ([http://www.mythtv.org/wiki/High_Definition_Disk_Formats](http://www.mythtv.org/wiki/High_Definition_Disk_Formats)), BD playback should be possible with .25 out of the box.

BTW, is the .25 release of mythbuntu capable [as installed from the ISO] of compiling mythTV from a tarball or source package or do I need to "jump through some hoops" to get prerequisite tools etc? What is the easiest way to upgrade to .27?

---

### Post by blm-ubunet on 2014-03-16
If you are using GT520 & using the proprietary driver then you can run nvidia-settings GUI tool & find & set openGL "sync to vertical blank".

Are you using unity/ubuntu or mythbuntu Xfce?
If you are using VDPAU on mythbuntu then there should not be tearing.
Mythbuntu desktop manager behaves correctly. (reports refresh rate & does not redirect full screen).
With Unity DE/effects manager you have to install use "ccsm" & config full screen redirection etc etc.

You could be using openGL without vsync set..but I would recommend VDPAU.
The painter engine should be set to "auto" or "openGL".

The video playback test downloads a trailer of a FOSS Blender film/movie.

Mythtv Version:
mythbuntu ppa has 0.25 & 0.27+fixes branches for 12.04-LTS
I believe these packages allow you to install source packages & dependencies.

To build from source the best way is to get source directly from github.

---

### Post by Johnathon_Galtman on 2014-03-16
I tried using mplayer but can't figure out the options, it's rather confusing. For example in the manpage, the pvr option (listed as: -pvr <option1:option2:...> (PVR only)) shows nothing for selecting the composite input source. It's just very confusing. I tried several pvr & tv command lines but no luck with mplayer.

I looked at isely's pvrusb2 docs and tried to just "turn on" the hauppauge device using his sysfs interface but can't figure that out either. His commands.txt file is admittedly old. Looking at the files under /sys/class/pvrusb2/sn-xxxxxx/ I see ctl_master_state, power and many others, but those seem the most logical to turn on device. There's just too many to try them all, and that doesn't make much sense anyway.

I'm using mythbuntu / xfce. The "Sync to VBlank" option in nvidia driver is checked under OpenGL Settings. [COLOR=#000000]The painter engine option is Qt, not OpenGL so I'll try changing that.

If you can tell me what the command line should be for mplayer I can try that too. My capture device is the std /dev/video0. When I select "Watch TV" in mythTV the Hauppauge LED turns on, and goes off when I exit the frontend (or possibly when I stop watching).

----------- UPDATE -----------

I decided to boot another Linux version and try it on a different OS (do recall my system is a mutltiboot). I thought I noticed the /dev/video0 before, which is how I decided to check into mythTV in the first place.

I booted Linux Mint 13 and sure enough there it was, right outa the box (/dev/video0). I fired up vlc, chose the pvr capture device on /dev/video0 and wella ... nice clear green screen. Then I just did an echo "composite" > /sys/class/usbpvr2/snxxxxx/ctl_input/cur_val and the vlc came to life with perfect video, no tearing.

So I'm gonna backup the mythTV partition and reinstall from mythbuntu from the same ISO image and before I do any configuration or setup of mythTV I will try the vlc test. If it fails I'd say it's a bug in the .25 release code. In that case I'll just wait till I get a DSL Internet connection (coming next week I hope) and get my .25 updated and upgraded to .27 and proceed from there.

[/COLOR]

---

### Post by blm-ubunet on 2014-03-17
mplayer is less confusing than vlc cmdline interface or echo'ing text into filesystem nodes...!

This could be useful for analogue input encoder card control "v4l-ctl"

I wouldn't try to debug video tearing with liveTV input..
Just use an existing recording video file of known resolution/refresh rate/bitrate/codecs.

---

### Post by Johnathon_Galtman on 2014-03-17
> **blm-ubunet said:**
> mplayer is less confusing than vlc cmdline  interface or echo'ing text into filesystem nodes...!
I'm  afraid I can't agree with you on that (I used the VLC gui). The mplayer  man page is  e x t r e m e l y  long, inconsistent and I couldn't figure  it out after numerous trials. I had no trouble following Isely's info  on using his sysfs interface.

> **blm-ubunet said:**
> This could be useful for analogue input encoder card control "v4l-ctl"

I wouldn't try to debug video tearing with liveTV input..
Just use an existing recording video file of known resolution/refresh rate/bitrate/codecs.

That  might be a better approach than mplayer or vlc against the liveTV feed,  but since I have now vindicated the linux drivers & OS (having  already done the same for windoze) it's either how I configured mythTV  or the mythbunto's ISO. I followed a pictorial step-by-step guide to  install & configure both the FE & BE of mythTV, and it resulted  in this problem. Plus, if I used a video of known pedigree, how does  that tell me what to tweak / adjust / change in mythTV?

Now that  I've backed up the mythbuntu partition I'll reinstall from the same ISO  as I originally did (which I have on a USB hard drive so it installs  pretty fast), and see if I have the same problem, using vlc. I may have  overlooked or chose to ignore doing an "update" after installation since  the box isn't online quite yet (tho I did get DSL installed today,  hurray!), and if the quickstart guide I used says to do so that may be  what the issue is (some bug was identified & fixed since the ISO was  released).

Whatever I find I'll post the results here as it may help others.  And speaking of help, thanks again for your help blm-ubunet, it's  greatly appreciated!

---------- UPDATE ------------

I reinstalled mythbuntu from the same ISO, and immediately upon first boot I started vlc, selected open capture device, used pvr device type and /dev/video0 as the file location and saw a nice stable green screen. Using the pvrusb2 driver interface in the sysfs I switched the input source to composite and presto live TV!

Next I'll use the quickstart guide I used before to setup the BE & FE and see what happens.

One thing I noticed that's different is the fonts are much larger & smoother than my previous installation. Although the nvidia driver config says I'm in 1280 x 800 display resolution (the default for my projector), I selected 720p at install time.

Anyway, I'll see if the quickstart config process leads me to select options that cause the video tearing or not tomorrow.

---------- UPDATE # 2 ------------

OK - so now that I've got an Internet connection, and after doing the package updates for the system and running through the BE & FE setup / configuration (by memory only, didn't use the quickstart guide), I ran the std & high def tests in the FE setup wizard, all worked just fine. But for some unknown reason when I click on Watch TV I get a brief flash and then back to FE menu, no errors or other info. I need to look in the logs I guess to see whats going on. There's no reason it shouldn't be working now.

---

### Post by blm-ubunet on 2014-03-18
mplayer (cmd line) just used to experiment with video playback options (using a file) is quite straight forward & provides good stdout.

MythTV is a PVR.
IMHO
You debug video playback by doing just that..expt with known good video recording (from the filesystem & not liveTV) & try different video drivers/settings/OS/etc.

You debug video capture/tuner cards by capturing that output into the filesystem (i.e. a file).
You then analyze that same file with different programs/OS/etc.

LiveTV in mythtv is good for debugging "livetv in mythtv" & partial checking of your tuner/HLS recorder configuration.
LiveTV (mythtv) demands that the filesystem can write & read the stream & CPU can parse stream & filesystem can update database elements.

Note: that VLC does not support VDPAU directly (latest builds might), it can use VA-API only if you have a particular VDPAU-backend-for-VAAPI library. By default it probably uses XVideo or openGL rendering & CPU decode.

VDPAU (on nVidia driver) is guaranteed tear-free when composite redirection is disabled. This happens with correctly functioning composite effects manager & running mythtv full screen.
Mythbuntu should have been okay.

Maybe your tearing is just a playback glitch or refreshrate mismatch or following "live" to closely for weak CPU? Try pausing LiveTV for 5 seconds..

---

