---
title: "Convert mp3 to AAC"
date: 2009-05-06
forum: Multimedia Software
---

### Post by jordey24 on 2009-05-06
HI,
i want to convert my music library to AAC so i can copy it on the SD card for my Nintendo DSi.I  tried stuff on the forum and installed lots of programs,but nothing worked.If possible,how can i convert  about 3 gb of mp3's to aac with a user friendly interface?

---

### Post by DerHesse on 2009-05-06
Hi Geordy, how's your German?
[http://wiki.ubuntuusers.de/Audiodateien_umwandeln](http://wiki.ubuntuusers.de/Audiodateien_umwandeln)
 
This is a Nautilus integratable solution. In short words:
 
```
sudo apt-get install wavpack mppenc libmpcdec3 faac flac vorbis-tools faad lame nautilus-script-audio-convert 
```

then: 
```
nautilus-script-manager enable ConvertAudioFile 

```
and
```
nautilus --restart 
```
 
That's it.
[I]Right-click the file to convert and choose: "Scripts -> ConvertAudioFile"

With DSi you still have to rename the output file to either .3gp or .m4a. Othewise DSi will not recognise the files. 




[/I]

---

### Post by jordey24 on 2009-05-06
Thanks!I can now enjoy my music on DSi =D
And the sound quality still is great! thanks again

---

### Post by dgoosens on 2010-03-26
nice !
thanks a lot...

---

### Post by Rubicon421 on 2010-08-01
Just tried this out and it works perfectly! I did still have to rename the files and add .M4A for the DS to recognize them though. Anyone know of a good script to batch rename files by adding .M4A to the end while preserving each files current name? 

Also, I started trying to use WinFF because it worked well in Windows to convert MP3s to M4A but it doesn't have the right preset in Linux. Anyone know how to set it up?

---

### Post by ron999 on 2010-08-01
> **Rubicon421 said:**
> ... but it doesn't have the right preset in Linux. Anyone know how to set it up?

Convert to... Audio
Device Preset... MPEG4 Audio

---

### Post by Rubicon421 on 2010-08-01
> **ron999 said:**
> Convert to... Audio
Device Preset... MPEG4 Audio


That preset is not available in mine. I probably just need to install the codec or something. I'm running Linux Mint 32 Bit and have Ubuntu-Tweak installed with all the extra media codecs installed so I'm not sure what I am missing.

---

### Post by ron999 on 2010-08-01
The current version of WinFF is 1.2
If you need to upgrade then use the ppa from the website here:-[http://code.google.com/p/winff/wiki/UbuntuInstallation]("http://code.google.com/p/winff/wiki/UbuntuInstallation")

---

### Post by Rubicon421 on 2010-08-01
I just checked and I do have the newest version of Winff, version 1.2. I'm searching the package manager now for another codec to install.

---

### Post by andrew.46 on 2010-10-14
Hi,

Newest version is now 1.3.1, it is actually labeled 1.3 but I took it upon myself to modify the source to reflect the point upgrade :). Linux version (deb) not out for this so you will need to break out a Pascal compiler...

Andrew

---

### Post by ron999 on 2010-10-14
Hi Andrew
I know that Winff v1.3 is available for Windows, but so far the Ubuntu version isn't available from the Winff PPA.

The source code is available from the Winff website.
Do you have instructions how to compile Winff to make a deb?

---

### Post by andrew.46 on 2010-10-14
Hi ron,

> **ron999 said:**
> The source code is available from the Winff website.
Do you have instructions how to compile Winff to make a deb?

Well, interestingly enough the source code contains nothing debian at all, I suspect that the debian package is made by Mr Gevers. I actually built WinFF on my *other* distro but it should be just as easy to do on Ubuntu, which is where I found [the instructions]("http://ubuntuforums.org/archive/index.php/t-826622.html") :). It is written in Pascal so you will need fpc, fpc-source and lazarus. Download the WinFF source and extract it. Then start lazarus and open the file winff.lpi and select 'build all' from the lazarus run menu. This will build the executable.

On my own setup I only use this executable and a presets.xml file in $HOME/.winff/, placing the executable in $HOME/bin which is in my path. With no shame I discard the icons, desktop menu, man pages etc :). It is a little bare bones but it works well enough for me. If you have any trouble I can install it on Ubuntu and help you troubleshoot?

Andrew

---

### Post by mc4man on 2010-10-14
> but so far the Ubuntu version isn't available from the Winff PPA.
There seems to be a .deb for maverick/lucid, as far as karmic (ron), doing what Andrew suggests may be better

(though you could try installing the lucid .deb and see what transpires - the dep.'s
Depends: ffmpeg, xterm | x-terminal-emulator, libatk1.0-0 (>= 1.29.3), libc6 (>= 2.3.6-6~), libcairo2 (>= 1.2.4), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.8.0), libpango1.0-0 (>= 1.14.0), libx11-6

[https://launchpad.net/~paul-climbing/+archive/ppa/+packages](https://launchpad.net/~paul-climbing/+archive/ppa/+packages)

---

### Post by ron999 on 2010-10-14
OK
That was easy enough to compile with Lazarus.:)
Then replaced winff in /usr/bin folder with the new version.
I keep my own modified presets file.

Synaptic still shows v1.2 installed so when v1.3 is available through PPA I suppose it will update automatically.
This new Winff has additional crop options.

[IMG]http://img831.imageshack.us/img831/5998/winff2.png[/IMG]

---

### Post by andrew.46 on 2010-10-14
Hi ron,

> **ron999 said:**
> That was easy enough to compile with Lazarus.:)

D'oh!! I wrestled with a very raw Lazarus / Free Pascal installation under Slackware for hours :(.

> This new Winff has additional crop options.

But users of the svn FFmpeg will note that it uses *-croptop* etc rather than the very swish video filter system now available to the latest svn. But I guess the commandline svn FFmpeg and WinFF have different purposes.

Andrew

---

### Post by henrodon on 2010-12-09
[QUOTE=DerHesse;7224251]Hi Geordy, how's your German?
[http://wiki.ubuntuusers.de/Audiodateien_umwandeln](http://wiki.ubuntuusers.de/Audiodateien_umwandeln)
 
This is a Nautilus integratable solution. In short words:
 
```
sudo apt-get install wavpack mppenc libmpcdec3 faac flac vorbis-tools faad lame nautilus-script-audio-convert 
```

I'm trying to do the same thing and found this old thread. I wonder if somebody who understands these things could update it. It tried the above and got:

Unable to locate package libmpcdec3

Henro

---

### Post by mc4man on 2010-12-10
s```
sudo apt-get install wavpack mppenc \
faac flac vorbis-tools faad lame \
nautilus-script-audio-convert libmpcdec6
```

It's now 6

---

### Post by jfmessier on 2012-09-23
Cool. Although I had all the tools to convert the files from other discussions and sources, I coul dnot get them to work, and I was actually looking for something to put on my son's DSi XL. Although all my music is in MP3 format, his game console only plays those AAC-encoded files, and those never worked, until I found *YOUR* message about this file extension change. My son will be very happy !!!!!!

> **DerHesse said:**
> Hi Geordy, how's your German?
[http://wiki.ubuntuusers.de/Audiodateien_umwandeln](http://wiki.ubuntuusers.de/Audiodateien_umwandeln)
 
This is a Nautilus integratable solution. In short words:
 
[I]Right-click the file to convert and choose: "Scripts -> ConvertAudioFile"

With DSi you still have to rename the output file to either .3gp or .m4a. Othewise DSi will not recognise the files. 

[/I]

---

