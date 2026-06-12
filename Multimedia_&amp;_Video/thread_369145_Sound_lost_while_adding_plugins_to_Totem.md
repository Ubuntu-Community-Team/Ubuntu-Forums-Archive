---
title: "Sound lost while adding plugins to Totem"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by gewitty on 2007-02-24
I'm new to Linux and have recently installed Ubuntu 6.1/Gnome. I've been getting on pretty well and had already managed to get Rhythmbox playing my existing MP3 collection. However, I was unable to open any WMV files in Totem. I discovered the instructions for resolving this in the Ubuntu documentation ([https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)) and followed the directions to run the following in terminal:

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

Having done that, I now find that not only do WMV files NOT play in Totem, but I seem to have lost all sound from both Totem and Rhythmbox. One thing that has changed is that if I click on a WMV file, Totem loads and appears to be playing something (the progress bar moves along), but there is no video or audio.

Can anyone tell me what has happened and how I can either fix the problem or reverse whatever the gstreamer installations have done.

Bear in mind that I'm new to this, so keep any instructions at idiot level please.

---

### Post by louis_nichols on 2007-02-24
Isn't it just a matter of muted sound? You should check the sound settings by right clicking the sound icon in the tray, selecting sound settings and checking that the sliders for PCM and Master are not at minimum and/or muted.

Next thing is to go to System>Preferences>Sound settings and make sure everything is set to ALSA, for both source and sink.

Now, with wmv, the situation might be even more complicated> You might need the w32 codecs. You can get them [here]("http://medibuntu.sos-sts.com/repository.php")

---

### Post by gewitty on 2007-02-24
Thanks for the help, but having tried all your suggestions, I'm still getting silence. Something seems to have got broken during the gstreamer updates. I notice that when I try to play an MP3 in Rhythmbox, it behaves like Totem and appears to be playing the track, but no sound. I also found that radio streams, which were working before, are coming up with an error message saying, 'Unknown Playback Error".

---

### Post by gewitty on 2007-02-24
Things are improving. I noticed that a couple of other apps weren't working and did a re-boot. After this, sound was restored in both Rhythmbox and Totem. However, I'm still not getting the video for WMV files, only sound.

---

### Post by louis_nichols on 2007-02-24
aha. good. for wmv, as I said, you will most likely need the w32 codecs package.

---

### Post by gewitty on 2007-02-24
I ran the download from Medibuntu, but it just appeared to download something called medibuntu.list. Not sure where to go from there.

---

### Post by louis_nichols on 2007-02-24
Well, if all that went fine, you just need to:

```
sudo apt-get update && sudo apt-get install w32codecs
```

---

### Post by gewitty on 2007-02-24
I'd already found and installed W32 codecs via Synaptic, but with no improvement (still sound but no video).

I tried going the terminal route as you suggested, but it looks as if there might have been problems with that, or it spotted that I already had the latest version. Here's what happened:

dave@dave-desktop:~$ sudo apt-get update && sudo apt-get install w32codecs
Get:1 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release.gpg [191B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US                
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Translation-en_US                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Translation-en_US   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Translation-en_US     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Translation-en_US   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Translation-en_US               
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release.gpg [191B]   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Translation-en_US 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                     
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                     
  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Get:6 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release [739B]                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Packages          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Sources     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Packages    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Packages      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Translation-en_US
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Translation-en_US
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release
  
Get:7 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release [4421B]
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Sources
Fetched 5545B in 5s (988B/s)
Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
w32codecs is already the newest version.
The following packages were automatically installed and are no longer required:
  python-crypto libopenexr2c2a libarts1c2a kdelibs4c2a cracklib2 libdc1394-13
  gnome-bin libgnome32 kdelibs-data libjack0.100.0-0 gnome-libs-data
  liblualib50 libpcre3 libart2 libgnorbagtk0 gdk-imlib1 mencoder libavformat0d
  dvdauthor libavahi-qt3-1 libgnomeui32 vamps libdb3 libfluidsynth1 imlib-base
  liborbit0 gdk-imlib11 libavcodec0d libgnomesupport0 liblua50 ladcca2 scummvm
  libgnorba27 libungif4g
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Just out of interest, and in case it's related, I'm also having problems with gxine. Every time I try to access a TV or Radio site, I get an error message saying that the xine engine has a problem. I've tried un-installing and re-installing, but with no success. This may be completely unrelated to the Totem problem, but I thought it was worth mentioning as they are similar apps.

---

### Post by gewitty on 2007-02-27
All sound and most video problems are now resolved, thanks to the EasyUbuntu download - [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/). This installs a whole raft of codecs and apps that sort out pretty much everything you'll need.

---

