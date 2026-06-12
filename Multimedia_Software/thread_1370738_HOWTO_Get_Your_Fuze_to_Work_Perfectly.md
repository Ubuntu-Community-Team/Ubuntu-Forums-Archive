---
title: "HOWTO: Get Your Fuze to Work Perfectly"
date: 2010-01-02
forum: Multimedia Software
---

### Post by N00b-un-2 on 2010-01-02
**HOWTO: Get your Sansa Fuze to Work Perfectly**

Hello everyone! This is my first tutorial I've written for this forum. Please let me know if this helps anyone out there. It's always nice to give something back to the community.
This tutorial pertains mainly to the Sansa Fuze V2 released late in 2009, but most of the information here can be applied to other mp3 players as well as other devices that can play music or videos but do not show up by default in your music player, such as Cellphones, PDAs, or even your PSP. This will help you enjoy the same kind of functionality with your Sansa Fuze (which --IS-- officially supported on linux) that owners of iPods have enjoyed for a while now on Linux. The iPod is --NOT-- officially supported on Linux, and merely syncing your iPod with ANYTHING but iTunes is in direct violation of the Apple EULA. Not only that, but it becomes a hassle, especially with later models of iPods due to the ever changing database hash checking method that Apple comes up with as a deterrent to you using THEIR hardware with anything but THEIR software. I got sick of syncing my iPod and having it work fine, but the next time I added music to my iPod one of two things would INVARIABLY happen: A) all of my album artwork would disappear, or all of my music would disappear and the iPod would just say "0 songs". But that is a discussion for another thread and another time... We will cover the following in this tutorial:


* updating your Fuze's firmware (to support free music formats Ogg and FLAC) 
* Getting your music player to recognize/sync with your Fuze (may also work for other devices) 
* Getting videos to work on your Sansa Fuze 
* Syncing Photos to your Fuze 
* Making your computer recognize and mount your Fuze the way it does with an iPod instead of a generic USB drive (once again, this will work with other devices as well)

Step 1: Update your firmware

This step may or may not be necessary for you depending on the date of manufacture for you Fuze. Also note that there are two version of the Fuze, the V1 and the V2. As I mentioned before, this tutorial mainly pertains to the Fuze V2. If you have a Fuze V1 I would highly recommend that you check out Rockbox. There are two methods for updating your Sansa Fuze firmware. With the firmware update comes the long anticipated Ogg and FLAC compatiblity.

Method 1: Automated Firmware Update (for Windows only)
And no... you can't run this in Wine. It doesn't work. Don't ask. Just follow the instructions.

1)	Set your Sansa Fuze to MTP (media transfer protocol) mode by navigating to:
```
SETTINGS>>SYSTEM SETTINGS>>USB MODE>>MTP
```
2)	Boot into your Windows partition
3)	Download the [Sansa Firmware Updater]("http://mp3support.sandisk.com/sansa/Application/SansaUpdaterInstall.exe") and install it.
4)	Connect the Fuze to your computer, run the Sansa Firmware Updater, select the 'Firmware' checkbox and click 'Download Now'
5)	Once the download is complete you will be prompted to disconnect your Fuze. Your Fuze will then update itself and then it will shut off. Turn the Fuze back on, and your done. It's pretty straightforward.
[IMG]http://kb.sandisk.com/euf/assets/images/faqs/id278_13_clickfw.gif[/IMG]
Method 2: Manual Firmware Update (for Linux)

1)	Set your Sansa Fuze to MSC (mass storage controller) mode by navigating to:
```
SETTINGS>>SYSTEM SETTINGS>>USB MODE>>MSC
```
2)	Boot into your Linux partition
3)	Download the firmware zip file [here]("http://mp3support.sandisk.com/firmware/fuze/fuze02.02.28.zip") and extract it.
4)	Connect the Fuze to your computer and copy the file 'fuzpA.bin' to the root of your Fuze
5)	After you've copied the file to your Fuze, unmount and disconnect it from your computer. The update will beging automatically and when it's done it will shut off. Turn your Fuze back on, follow the instructions and you're done.
[[IMG]http://img403.imageshack.us/img403/4998/updatea.th.png[/IMG]](http://img403.imageshack.us/i/updatea.png/)
Verify that your Fuze updated navigating to -
```
SETTINGS>>SYSTEM SETTINGS>>INFO>>VERSION
```
And your screen should look like this:
[[IMG]http://img3.imageshack.us/img3/7615/versioninfo.th.jpg[/IMG]](http://img3.imageshack.us/i/versioninfo.jpg/)
As you can see from the screenshot, my Fuze is running Firmware Ver. 02.02.28A (and yes, it plays OGG and FLAC just fine)
Step 2: Syncing Your Fuze

In order to get your Fuze or any otherwise unrecognized device to be recognized by your Music Player, you have to add a hidden file called .is_audio_player to the root of the device. Simply adding this file will enable "basic" functionality with various music players, ie; your device will show up on your Music Player you'll be able to add music (.mp3 only) to it.

[[IMG]http://img689.imageshack.us/img689/388/fuzehidden.th.jpg[/IMG]](http://img689.imageshack.us/i/fuzehidden.jpg/)
I have tested this with several music players and I've had mixed results. Here is the 'compatibility' list:
Banshee - Works great! Syncs music and video without any issues. Screenshot below.
**Rhythmbox** - works just as well as Banshee, but doesn't have video support, no support for ID3 tagged art tho.
**Exaile** - Works (sort of) after you've enabled the MSC driver, and force mount your Fuze. No album art though
**Songbird** - Doesn't work. There is an MSC plugin but it only works on Windows. Whats the point? If you're using Windows you have MTP. Maybe soon...
**Amarok** - Doesn't work
**Audacious!** - Doesn't work either
[[IMG]http://img526.imageshack.us/img526/6656/bansheeq.th.png[/IMG]](http://img526.imageshack.us/i/bansheeq.png/)
The main reason I wanted a Fuze was specifically for its free format support (ogg, FLAC), which SUPPOSEDLY worked out of the box. In order to enable the other audio formats you player can handle you will need to add a few instructions to .is_audio_player. Here is a sample .is_audio_player file and some explainations of a few instructions you can add to your .is_audio_player file
```

name=Sansa\ Fuze
audio_folders=MUSIC/,VIDEO/ folder_depth=2
output_formats=audio/ogg,audio/flac,audio/x-ms-wma,audio/mpeg,audio/aac,audio/x-wav

```

**name=Sansa\ Fuze**	
This is the name that will show up in your music player, NOT the device label or AYTHING that your system sees. This is only for naming your device in a music player like Rhythmbox. In case you're wondering why there is a backslash after "Sansa", it is because the name of your device is in UNICODE, and spaces are not supported, so the space is 'escaped' by the backslash. Thus, your device will be seen in your music player as "Sansa Fuze".

**audio_folders=MUSIC/,VIDEO/**	
This simply tells the music player where to put music (or video) files that you sync to your device. Like I said, this works for more devices than just the Fuze, so the absolute location of where to put the files may vary. In my experience though, music players will always default to the same folder (typically "MUSIC/"), but the Fuze seems to be able to read video files as videos even if they're placed in the Music folder and vice versa. The same does NOT apply to a PSP though, so you'll have to play around with it to figure out what workes for you.

**output_formats=audio/ogg...**	
This instructs the Music Player what types of files the device can handle (without transcoding). If you do not add a file type here, you will not be able to transfer it to the device. You may want to try out some other variables to make more files transfer, for example, try adding audio/avi to the list to enable video sync with Banshee (the only music player I know of that supports this)

There are a few extra arguments that you can add, but most of them don't do much. Just google ".is_audio_player" to find out more.


**Step 3: Video for Fuze**

I quickly figured out that while the Fuze has a wide range of audio formats it can handle, there is only ONE type of video it can play. It plays AVI files that are encoded with the DIVX5 video codec and standard MP3 audio at 128kbps 16bit stereo 44.1khz. The Video MUST be 224x176 at 20fps exactly, between 500-700kbps, and the avi file has to be remuxed. Ridiculous.
The Sansa Media Converter application for Windows is absolute garbage and does NOT run under Wine, so forget about that.

The solution I've found is an awesome little application (well, actually its a collection of scripts and applications wrapped up in a neat little gui built with QT so it's cross platform) called Video4Fuze, which you can download [here]("http://video4fuze.googlecode.com/files/video4fuze-0.4.1_all.deb")
[[IMG]http://img36.imageshack.us/img36/2946/video4fuze.th.jpg[/IMG]](http://img36.imageshack.us/i/video4fuze.jpg/)
Here's a picture of Video4fuze in action. My only complaint about Video4fuze is the lack of drag and drop, but whatever. It works. Once you've converted a file, you can easily sync it with Banshee, or you can simply drag and drop it to your Fuze's '/VIDEO' folder. Also, you could just use Video4fuze and just set the output file to '/path-to/your-fuze/VIDEO'. The additional .thm file that is generated is just a renamed .jpg at 224x176, which acts as the cover art for the file provided it is named exactly the same as the video file.

**Step 4: Photos and your Fuze**

Well... for the most part, you're going to be limited to drag and drop. You can go through photo management programs like F-SPot and export your photos but there is no 'sync' functionality for pictures just yet. I hear that they're working on making an F-Spot plugin for Banshee which should be available in the near future, but til then things will be a bit more manual.
Just like video, you'll need the images to be 224x176 saved as jpeg, and you can actually use Video4fuze to convert and sync photos.
Your best option is probably going to be using F-Spot or Picasa if you want to quickly add a few photos to your Fuze. All you have to do is export the files you want to add to your Fuze's /PHOTO folder, making sure to set the size to 224 pixels. On F-Spot, It will probably throw a few error messages at you, but in the end the files will be veiwable on your Fuze after you disconnect, but it seems to work just fine on Picasa.
[[IMG]http://img17.imageshack.us/img17/480/export1.th.jpg[/IMG]](http://img17.imageshack.us/i/export1.jpg/)[[IMG]http://img22.imageshack.us/img22/6683/export2.th.jpg[/IMG]](http://img22.imageshack.us/i/export2.jpg/)
Step 5: Labeling Your Fuze

This is best broken down into two parts, setting the mount point and changing the drive label

1) Setting Your Mount Point
The first thing we need to do is change the Fuze's mount point so that when it loads it's easier to find, particularly if you have multiple devices plugged in at the same time. To do this, open the "Computer" icon and right click the icon for your Fuze. Then right click it, and select 'Properties'. Then go to the 'Volume' tab, the furthest one to the right. Expand the 'Settings' arrow and under "Mount Point:" type in
```
Fuze
```
or something to that effect. Keep in mind that you CAN NOT use either the absolute path to the mount point, eg; /media/Fuze, and you can't use spaces for the mount point either.
Unmount your Fuze, disconnect it and then reconnect. It should have mounted at '/media/Fuze'. This will make the device easier to locate for the next step.

2) Change Your Drive Label
There are three main steps to labeling a device on Linux. First you need to identify where the device is mounted, then you determine what it's label is, then you relabel it. By default when you plug in your Fuze it will be automounted to /media/disk-1 or something to that effect and it will show up as a generic USB volume called "7.9 GB Media" (or something similar if you have another size Fuze). We just changed the mount point to /media/Fuze, but it still shows up as a generic USB drive called "7.9 GB Media".
You may need to install a few packages to continue. In the Terminal, type in:
```
sudo apt-get install gparted mtools
```
Then open the Gnome Partition Editor
```
sudo gparted
```
In gparted, determine which drive is your Fuze. it will typically be /dev/sdb or /dev/sdb-1. Then exit out of gparted without making any changes. DO NOT PARTITION YOUR FUZE!!!
Then in the terminal unmount your Fuze,
```
sudo umount /media/Fuze
```
then enter the following command to rename your Fuze
```
sudo mlabel -i /dev/sdb ::'Sansa Fuze 8GB'
```
make sure to substitute '/dev/sdb' with wherever your Fuze is actually located. Then disconnect it from your computer, and then reconnect. It should now be showing up in your computer as "Sansa Fuze 8GB". More in depth info on how to label drives can be found at [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive).
From here you can manually change the icon for the Fuze by right clicking it and just changing the icon to whatever you wish. In order to change the icon from showing an iPod in Banshee however, you'll need to save the Fuze icon over the icon called '/devices/multimedia-player.png' in most icon sets.
[http://img685.imageshack.us/img685/9966/multimediaplayer.png](http://img685.imageshack.us/img685/9966/multimediaplayer.png)

Thank you for reading, and I hope this helps some of you out! let me know how it goes.

---

### Post by spydeyrch on 2010-01-08
Nice tutortial. Well put together and clear. Thanks!
 
-Spydey:guitar:

---

### Post by cprofitt on 2010-01-08
ALERT: For v2 - do not download 2.02.28 of the firmware if you use gain - there is a known bug that has not been resolved that affects gain. Stay or upgrade to 2.02.26 [[link to firmware warning]("http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=33874")]

---

### Post by mathias j sagartz on 2010-04-01
Is there any trick to installing video4fuze?

Yesterday I downloaded the .deb packages video4fuze and fuzemux.  I clicked on the downloaded files and used the package installer that came up.  That seemed to work OK and the synaptic package manager says they are both the fuzemux and video4fuze packages are installed.  Under the Applications 
menu in Other there is a video4fuze icon but when I click it I just get a
busy clock for a while and then nothing.  Any ideas?

---

### Post by 0e8h on 2010-06-25
Wine does work with Media Converter!!!

Using;
video4fuze-0.6
Wine 1.2r4

---

### Post by nemoinis on 2010-06-26
your "output_formats" line includes "audio/aac", but that's wrong: the Fuze does not support the aac format (unless you're using Rockbox :D)

Also, on my Fuze 8GB with the latest FW (and using Lucid's Rhythmbox), "audio/ogg" is not recognized properly. After changing it to "application/ogg", files in formats that the Fuze does not support are properly converted to ogg by Rhythmbox.
Note: the first entry in the "output_formats" line is the format that unsupported files will be converted to.

---

### Post by Objekt on 2010-07-04
Neat.  I usually don't have a strong desire to watch a video on the tiny screen, but it is nice to know there is a native Linux app to do the conversion.

I bought a refurbished 4 GB Sansa Fuze v2 late last year, and have been very happy with it.  I added an 8 GB micro SDHC card soon after, and have yet to manage to fill all the storage.

When people ask, "What's a Fuze?" I tell them, "it's like an iPod, only way better and cheaper."

---

### Post by TheDebianGuy on 2010-08-18
Thanks alot, i was looking for a program to do that!!!
Great job!!! 
=D
:popcorn:

---

### Post by gmaximogomez on 2010-11-14
Hello All.  I have a Sansa Fuze 8gb and am using ubuntu 10.04 Lucid Lynx.  I have Rhythmbox 0.12.8  

The problem I am having is rhythmbox will load and display the songs on my fuze, but when i click to play them, I get the red icon with a white line thru it next to the title of the song and the error message " No file name specified for reading".  (note: the songs i have loaded on this fuze were loaded thru windows before i switched to linux, could this have something to do with it? even when i load a song i ripped using rhythmbox and try to play it from the fuze, i get the same message)  I have mtpfs and mtp-tools installed and I've tried the fuze in MTP mode and Auto select.  I dont know what else to do, any help is appreciated! 
Thanks.

---

### Post by nardis_Miles1 on 2010-12-23
That is a very nice tutorial. My fuze is working very well through Banshee. However, I just bought a fuzePlus for my wife, and I can't get lucid to recognize it as a music source. Has anyone had any success with this?

---

### Post by alan404 on 2011-01-05
Hello. I have recently bought a Fuzeplus. I defaults to MSC mode, and it appeared in Rhythmbox, but what I did is not use Rhythmbox but simply drag all the albums I wanted into the Music folder using the file manager and this worked well. This is on Maverick.

However I had a bit of trouble getting album cover art working. I use the Flac format (Bad quality mp3s aren't progress in my book), and I think the player only supports embedded tag art in mp3. But the solution is incredibly simple. Simply provide a jpg named folder.jpg in the album folder and it will display it. I only wish this important bit of information was in the manual. 

Also be careful with tagging programs which "helpfully" add musicbrainz id tags as these will confuse the player. It plays mp4 video too, so video is much easier, although I haven't tried this. 

I tried it with Amarok and I was very impressed. There is an album cover script for Amarok called copycover2 which will store Amarok's retrieved album cover as a file in the folder of the album. It defaults to "cover.jpg" for this but you can change it to "folder" in the Settings menu. Amarok also handled the Fuzeplus very well as a device in either MSC or MTP modes. You simply right click on the track or album in your library you want to copy and you can copy it to the Fuzeplus. A lovely window appears where you can rename everything based on tags.

So all in all the Fuzeplus is a hit with Ubuntu and it works well, once you've worked out the "secrets". There is a forum on the SanDisk website which has a lot of people moaning (!) but it can be useful for undocumented features.

Alan

---

### Post by silvabone on 2011-11-23
Thank you very much! It is working perfectly well. 
May God bless you.
All the best!

---

