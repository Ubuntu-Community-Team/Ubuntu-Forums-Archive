---
title: "Can't rip CD in .mp3"
date: 2009-06-17
forum: Multimedia Software
---

### Post by Uziel126 on 2009-06-17
Hi, 
I've tried using rhythmbox, sound juicer, grip and asunder to try and rip my CDs in an mp3 format , but so far this has failed. I did a few searches for a fix, tried using "sudo apt-get install lame" to install the codec but it doesn't resolve my problem. What am I doing wrong?

Also, the error messages I get when trying to rip,

Rhythmbox: (none, I just can't rip in mp3)
Sound Juicer: (none, I can't enable an mp3 format from the drop down menu in preferenes)
Asunder: "There was an error creating *x* files"
Grip: Invalid encoder executable. Check your encoder config, and ensure it specifies the full path to the encoder executable

Thanks in advance

---

### Post by CatKiller on 2009-06-18
[https://help.ubuntu.com/community/CDRipping#MP3 Encoding]("https://help.ubuntu.com/community/CDRipping#MP3 Encoding")

---

### Post by shine jo on 2009-06-18
how can i install vlc player in ubuntu > **Uziel126 said:**
> Hi, 
I've tried using rhythmbox, sound juicer, grip and asunder to try and rip my CDs in an mp3 format , but so far this has failed. I did a few searches for a fix, tried using "sudo apt-get install lame" to install the codec but it doesn't resolve my problem. What am I doing wrong?
 
Also, the error messages I get when trying to rip,
 
Rhythmbox: (none, I just can't rip in mp3)
Sound Juicer: (none, I can't enable an mp3 format from the drop down menu in preferenes)
Asunder: "There was an error creating *x* files"
Grip: Invalid encoder executable. Check your encoder config, and ensure it specifies the full path to the encoder executable
 
Thanks in advance

---

### Post by zenbachry on 2009-06-18
Or, you could rip them in OGG format (or whatever format you so choose) and get SoundConverter from the add/remove. I'm not too familiar with the terminal, so I don't know the package that you want to get. When you open up the Add/remove software dealy, type in SoundConver, and there should only be 1. I use SoundConverter to go from OGG to MP3, and use SoundKonverter to go from MP3 to OGG.

Oh, reason I said to type in SoundConver instead of the full name is 'cause I think I might have misspelled it. Not sure if its an or or er. But I'm almost positive its er

---

### Post by zenbachry on 2009-06-18
> **shine jo said:**
> how can i install vlc player in ubuntu

Applications->Add/Remove type in VLC and search for the VLC player. Install that way.

---

### Post by Uziel126 on 2009-06-18
> **CatKiller said:**
> [https://help.ubuntu.com/community/CDRipping#MP3 Encoding]("https://help.ubuntu.com/community/CDRipping#MP3%20Encoding")

I'm hesitant to install yet another application, isn't it possible for me to just get the job done with one of the other apps? I do after all have grip. soundjuicer, asunder, rhythmbox, and now soundconverter shouldn't one of them work?

I'm thinking my problem is with the codec, after installing soundconverter and still not getting results. I'm pretty sure i did get the lame codec though. Any way I can check this?

---

### Post by CatKiller on 2009-06-18
> **Uziel126 said:**
> I'm thinking my problem is with the codec, after installing soundconverter and still not getting results. I'm pretty sure i did get the lame codec though. Any way I can check this?

Installing the ubuntu-restricted-extras package, as indicated on that page, will install the codecs that you need. They should then be available in many of the applications that you already have.

Personally, I rip to FLAC. But then, I don't have to deal with a portable player, I have plenty of hard drive space, and I prefer things to sound as good as they can.

---

### Post by Bölvaður on 2009-06-18
> **Uziel126 said:**
> I'm thinking my problem is with the codec, after installing soundconverter and still not getting results. I'm pretty sure i did get the lame codec though. Any way I can check this?

I think the you will get the proper error messages either from the terminal or synaptic.

Terminal (applications &#8594; accessories &#8594; terminal)
```
[sudo apt-get install ubuntu-restricted-extras]("apt:ubuntu-restricted-extras")
```


in synaptic you can also try to see if ubuntu-restricted-extras is installed.
also check if all gstreamer plugins are insatlled (not all are needed.. some are for programs that you might not use)

---

### Post by vambo on 2009-06-18
Looks like a problem with lame.
Asunder uses this as it's mp3 backend.
See if you have lame installed NB NOT the gstreamer plugin thing

```
aptitude show lame
```

If it's not installed install it

```
sudo aptitude install lame
```

Should be able to do this via Synaptic and apt-get too

Also note you need this installed as well

libmp3lame0

Pulling in lame should do it, but in case it doesn't.

---

### Post by Uziel126 on 2009-06-18
Ok, I definitely have the LAME encoder, but the problem is still there. Do I need to configure something within the ripper/converter? The error I get when I run soundconverter in terminal is

> #lame' element not found, disabling MP3.
  'faac' element not found, disabling AAC.

But when running lame in terminal

> LAME 32bits version 3.98 ([http://www.mp3dev.org/](http://www.mp3dev.org/))

usage: lame [options] <infile> [outfile]

    <infile> and/or <outfile> can be "-", which means stdin/stdout.

Try:
     "lame --help"           for general usage information
 or:
     "lame --preset help"    for information on suggested predefined settings
 or:
     "lame --longhelp
  or "lame -?"              for a complete options listI'm guessing this means I do have lame somewhere? Also downloading the ubuntu restricted extras package, not done yet though. will update when it completes... It's a little irritating though, that I have to go through this entire process to rip CDs to mp3 files, shouldn't the codec be enough? Well, will see how it goes, thanks for the replies :)

/edit

Ok, I couldn't download the whole package, I managed to get all but these
> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/f/freepats/freepats_20060219-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/f/freepats/freepats_20060219-1_all.deb)
  Could not connect to archive.ubuntu.com:80 (91.189.88.31). - connect (113 No route to host) [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-pitfdll/gstreamer0.10-pitfdll_0.9.1.1+cvs20080215-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-pitfdll/gstreamer0.10-pitfdll_0.9.1.1+cvs20080215-1ubuntu1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (91.189.88.31). - connect (113 No route to host) [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394-22/libdc1394-22_2.0.2-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394-22/libdc1394-22_2.0.2-1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (113 No route to host) [IP: 91.189.88.46 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdca/libdca0_0.0.5-0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdca/libdca0_0.0.5-0.1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (113 No route to host) [IP: 91.189.88.46 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/f/faad2/libfaad0_2.6.1-3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/f/faad2/libfaad0_2.6.1-3.1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (113 No route to host) [IP: 91.189.88.46 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.1.30really5.0.75-0ubuntu10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.1.30really5.0.75-0ubuntu10_all.deb)
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (113 No route to host) [IP: 91.189.88.46 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.75-0ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.75-0ubuntu10_i386.deb)
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (113 No route to host) [IP: 91.189.88.46 80]



i don't know if these files are all that important to warrant me trying again, its kinda frustrating having to download these things :/

---

### Post by mc4man on 2009-06-18
As far as mp3 you should be ok.
While using "ubuntu-resticted-extras" is the 'easy' way it installs a lot of stuff, some of which you might not need or want, or in the case of a flash player there is a better version from adobe (IMO)

If you search gstreamer in synaptic you'll see all the available plugins

Ubuntu makes it a bit confusing by breaking the bad and ugly into 2 versions with 4  or 5 listing's for bad and ugly 
The more useful are 
bad (1st listed
bad multiverse (4th listed
ugly (1st
ugly multiverse (4th
the ffmpeg one
pitfdll (allows use of w32codecs

If you only wanted mp3 support it's probably one of the 2 ugly or just using the fluendo one

---

### Post by Uziel126 on 2009-06-18
> **mc4man said:**
> As far as mp3 you should be ok.
While using "ubuntu-resticted-extras" is the 'easy' way it installs a lot of stuff, some of which you might not need or want, or in the case of a flash player there is a better version from adobe (IMO)

If you search gstreamer in synaptic you'll see all the available plugins

Ubuntu makes it a bit confusing by breaking the bad and ugly into 2 versions with 4  or 5 listing's for bad and ugly 
The more useful are 
bad (1st listed
bad multiverse (4th listed
ugly (1st
ugly multiverse (4th
the ffmpeg one
pitfdll (allows use of w32codecs

If you only wanted mp3 support it's probably one of the 2 ugly or just using the fluendo one

Installed the fluendo package, I already had the ugly packages... didn't help, unfortunately.

---

### Post by mc4man on 2009-06-18
> nstalled the fluendo package, I already had the ugly packages... didn't help, unfortunately. 

I don't use gstreamer apps very much, but you should have everything you need to play and encode mp3.

Personally I think it's better to use non gstreamer apps for ripping/encoding [B]particularly with mp3's.
[/B]
While they all take a little time and effort to setup and learn you'll get a superior job from abcde, rubyripper, soundKonverter to name a few. 

Even grip still works ok and is the easiest of the lot to get going

Just to ck. on gstreamer in jaunty (I still use hardy mainly

From a jaunty live cd, nothing installed, using rhythmbox to test

min for playback of mp3

the fluendo mp3 plugin or the ugly-multiverse and ffmpeg plugins (installed just the fluendo, got mp3 playback in rhythmbox

min for encoding an mp3  ripped from an audio cd

installed just the ugly-multiverse, rhythmbox was able to rip and encode to mp3.

I've seen people say grip doesn't work in jaunty which wouldn't of been that surprising considering it's development ended quite some time ago.

Installed it and lame, worked fine ripping and encoding an mp3
first time thru no tags showed up on the grip mp3 in rhythmbox, added id3v2 and all was good.

---

### Post by Uziel126 on 2009-06-18
> **mc4man said:**
> I don't use gstreamer apps very much, but you should have everything you need to play and encode mp3.

Personally I think it's better to use non gstreamer apps for ripping/encoding [B]particularly with mp3's.
[/B]
While they all take a little time and effort to setup and learn you'll get a superior job from abcde, rubyripper, soundKonverter to name a few. 

Even grip still works ok and is the easiest of the lot to get going

Just to ck. on gstreamer in jaunty (I still use hardy mainly

From a jaunty live cd, nothing installed, using rhythmbox to test

min for playback of mp3

the fluendo mp3 plugin or the ugly-multiverse and ffmpeg plugins (installed just the fluendo, got mp3 playback in rhythmbox

min for encoding an mp3  ripped from an audio cd

installed just the ugly-multiverse, rhythmbox was able to rip and encode to mp3.

I've seen people say grip doesn't work in jaunty which wouldn't of been that surprising considering it's development ended quite some time ago.

Installed it and lame, worked fine ripping and encoding an mp3
first time thru no tags showed up on the grip mp3 in rhythmbox, added id3v2 and all was good.

I don't get it, are you saying it works for you? In any case either I'm missing out a few steps when I use the apps to rip or convert, or my codec isn't installed correctly. Assuming I've installed the codec (because I'm now absolutely certain I have it) what do I need to do with the apps to ensure I rip correctly? Are there any other things which could be the problem?

---

### Post by Uziel126 on 2009-06-19
update: Fixed the problem, sort of. Managed to get grip going with a howto on the forum here: [http://ubuntuforums.org/archive/index.php/t-183125.html](http://ubuntuforums.org/archive/index.php/t-183125.html)

The other apps still aren't working though, but since grip's fine I guess I'll go along with it. Thanks for all the help :)

---

### Post by ewan86 on 2009-07-11
I found that ripperX was by far the easiest to use after having the same problem and it has an easy to use GUI.

---

### Post by infinitelink on 2009-07-23
Just asking to be thorough, but did you really run the aptitude command as given above to check for lame? Then read the WHOLE output, it says on one line whether it is installed or not. If so, did you re-start Asunder? 

I had the issue and was getting this when trying to select MP3, 
> 'lame' was not found in your path. Asunder requires it to create MP3 files. All MP3 functionality is disabled.

Using 'sudo aptitude install lame' and re-starting Asunder worked for me. If that doesnt' work you might want to uninstall Asunder with a complete purge, 'sudo aptitude purge Asunder" of both that program and all its config files, and ensuring you have lame installed (or upgrading to the latest release, or if neither works once you're re-installed Asunder, 'sudo aptitude purge lame' followed by repurging Asunder, followed by 'sudo aptitude install lame') then re-install Asunder 'sudo aptitude install Asunder'.

If none of that works, I may ask you to check-out the configuration files and have a look-see.

---

### Post by WhatsIt4 on 2010-05-21
Hey, running that sudo command uninstalled a bunch of stuff.  Sure I have the encoder working now, thank you very much, but it was nice to have Flash player, Java 6, w32 codecs, and just a few other things, so was it something I did?

$ sudo aptitude install lame
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  lame 
The following packages will be REMOVED:
  bsh{u} bsh-gcj{u} flashplugin-installer{u} flashplugin-nonfree{u} 
  gcj-4.3-base{u} gecko-mediaplayer{u} gstreamer0.10-pitfdll{u} 
   libjline-java{u} mint-meta-gnome{u} moonlight-plugin-core{u} 
  moonlight-plugin-mozilla{u} sun-java6-plugin{u} unrar{u} unshield{u} 
  w32codecs{u} 
0 packages upgraded, 1 newly installed, 20 to remove and 361 not upgraded.
Need to get 219kB of archives. After unpacking 84.0MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse lame 3.98-0.0 [219kB]
Fetched 219kB in 13s (16.5kB/s)                                                 
(Reading database ... 189616 files and directories currently installed.)
Removing bsh-gcj ...
Removing mint-meta-gnome ...
Removing bsh ...
Removing flashplugin-nonfree ...
Removing flashplugin-installer ...
Removing libgcj9-jar ...
Removing libgcj-bc ...
Removing libgcj9-0 ...
rmdir: failed to remove `/var/lib/gcj-4.3': No such file or directory
Removing gcj-4.3-base ...
Removing gecko-mediaplayer ...
Removing gstreamer0.10-pitfdll ...
Removing libjline-java ...
Removing moonlight-plugin-mozilla ...
Removing moonlight-plugin-core ...
Removing sun-java6-plugin ...
Removing unrar ...
Removing unshield ...
Removing w32codecs ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package lame.
(Reading database ... 189281 files and directories currently installed.)
Unpacking lame (from .../lame_3.98-0.0_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up lame (3.98-0.0) ...

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done


Just thought everyone should know this is a possibility.

Linux Mint 7.04
Gnome 2.26.1
Kernel 2.6.28.11

---

### Post by CatKiller on 2010-05-23
> **WhatsIt4 said:**
> Hey, running that sudo command uninstalled a bunch of stuff.  Sure I have the encoder working now, thank you very much, but it was nice to have Flash player, Java 6, w32 codecs, and just a few other things, so was it something I did?

I don't think it was installing lame that did it, so much as using aptitude. When it comes to orphaned packages (those packages that were installed automatically as a dependency, but the package that depended on them has been removed again) aptitude automatically removes them, whereas apt-get just complains that **you** should remove them.

I'd imagine that you've installed some kind of restricted-extras package which has pulled all of those in as dependencies and then removed that package but left the dependencies behind. Aptitude then tidied those up for you, exactly as you requested. But I know nothing about Mint packages, so it could have come about some other way.

Installing whatever package that was, or installing those dependent packages that you want, manually will install the packages that you wanted to keep.

> Just thought everyone should know this is a possibility.```
The following packages will be REMOVED:

...

Do you want to continue? [Y/n/?] y
```

---

