---
title: "A General Multimedia Guide"
date: 2009-07-15
forum: Multimedia Software
---

### Post by oronte on 2009-07-15
This guide is the culmination of years of work and research into finding the best, most interoperable solution for my own music collection. When I switched from Windows to Ubuntu 7 months ago I found that I couldn't do a lot of things that I could so on Windows. It turns about everything done on Windows can be done on Ubuntu but some of it will require a little extra work.

First here's the easiest solution to working with your music collection and music devices:
1.Rip your CD's with Sound Juicer in MP3 format or purchase them from legal online sites.
2.Plug in your device, if it's recognised as a music player you're set to go.
3.In Rhythmbox drag and drop your music tracks from your collection to your device and you're set.
Of course this solution has limited flexibility and there are certainly other advanced things you might want to do or you might have a few problems. If so read on!

Step One: Your Music Collection
So to start from the beginning. You either want to listen to music on your PC or you have a music player/phone and you want to listen to your music collection there. You have two basic options.

Option A: Rip your physical CD's
Legal Issues: Please check local copyright law in your region as this may now be illegal in some places, but it falls under 'fair use' legislation in most countries as long as you always keep the physical CD. If you later give away or sell the CD you should delete it from your music collection.

Format
FLAC: The absolute best solution here is to rip your music in FLAC format with maximum compression. FLAC is a lossless format so you can re-encode from it as many times as you like and you'll never have to worry about quality, this is not true of any lossy format (MP3/AAC/Ogg) you do not want to re-encode from ne of those formats to another as you'll lose a lot of audio quality. If you rip your collection in FLAC to begin with you can move to any other format with no qualtity issues whatsoever. Think of FLAC as a way of zipping up the original file on your CD. You can decompress a FLAC file and you'll have a file that will match a ripped wav (the original format that music on CD's is presented in) 100%. You could also just rip your music to wav format but the files will be much larger and yor ability to tag the file will be severely limited. Bear in mind that ripping to FLAC creates files that are typically around 50% the size of the original wav files. Typically expect about 7 CD's to take about 2gb of disk space (less if you've mostly got classical music and more if you have heavy metal) so you might need a larger hard-drive for this solution. Note that you generally won't be using the FLAC files on your removable music players (unless oyu have lots of space and it supports FLAC), you'll be encoding to another format. You can find more information on the FLAC format a [http://flac.sourceforge.net/](http://flac.sourceforge.net/)

MP3: Still the easiest format to rip to and the most compatible of any music format you can think of. Bear in mind that it is not open source and if you wish to use it you'll have to install the Ubuntu restricted extras. For more information on the restricted extras read the first section of this thread: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683). Typically you'll want to record your MP3's at 128 kbps in variable bit rate (vbr) and you can expect the resultant files to take up about 1meg/1 minute of playing time of the song. You might choose a higher bit rate if you have particularly well-tuned ears, but there are very few people who notice the difference in quality above 192 kpbs. Never choose a bit rate lower than 128kbps as you'll defintiely notice the loss in quality.

Ogg: I'm sorry to say that this is only a good choice if you plan on listening to your music on your PC. There are very few music players that natively support Ogg, but there are 3rd party programs you can purchase that might allow you to listen to Ogg music. Generally I can't recommend using Ogg at the present moment, unless you enjoy making your life difficult or you refuse to use closed source formats.

How to Rip:
Sound Juicer is the easiest program to rip your music collection with but it offers very few options for customisation and error correction new users might want to use Sound Juicer and leave it at that. A far better option is GRIP. Here are a few option I've found useful when using GRIP, all under the configuration tab: If you're having trouble ripping CD's, GRIP starts ripping but doesn't produce a useable file then tick the 'delay before ripping' option under Config – Rip. Don't tick any of the options to disable paranoia, etc unless you're having trouble ripping an old disc, in that case disabling some of these options might help the process along. If you're using FLAC then under encoder type the following:
Encoder Executable: /usr/bin/flac
Encoder Command-Line: --best -V -o %m %w -T "ARTIST=%A" -T "TRACKNUMBER=%t" -T "ALBUM=%d" -T "TITLE=%n" -T "GENRE=%G" -T "DATE=%y"
Encoder File Extension: flac
Encoder File Format: ~/Music/%a/%d/%a - %n.%x (this will create a directory in your Music folder for the disc's artists and a folder within that for the album, change this to whatever suits you best). If you're using MP3 use the LAME encoder (which you'll have to download from Synaptic first). Here's a site with more suggestions for MP3: [http://thismightbehelpful.blogspot.com/2007/05/grip-settings.html](http://thismightbehelpful.blogspot.com/2007/05/grip-settings.html) There isn't a single best solution with MP3 encoding, see above for a few guidelines.
You'll also want to tick 'delete .wav after encoding' and enter the number of CPU's you have if you're using a multi-core PC. Under ID3 tick 'only tag files ending in MP3' as the command line above will create the tag for your FLAC file. Under DiscDB select 'perform disc lookups automatically'. 
Now insert your disc, give GRIP a minute or two to find the disc information (requires an internet connection) or else type in the information yourself (generally not tagging files at this stage will become a nightmare later on). Click on the Rip tab and click on 'Rip & Encode'. Depending on the speed of your system and disc drive this may take several minutes. More information about GRIP here: [http://www.nostatic.org/grip/](http://www.nostatic.org/grip/) 
Finally if your CD has multimedia content (you'll know it does if under GRIP the last track of the CD is listed as a 'data track) then in the terminal type: sudo mount /dev/cdrom which will allow you access to the content. Note you may need to install Wine to access some of these files as many of them are programs that will only work on Windows. 

Option B: Download your music
Legal: Please only download your music from legal sources and not free file-sharing sites (unless the artist has made their music availabel for free). It might seem easier and cheaper to download yor music from file-sharing sites but the long term effects on the industry will he  large. You're not just hurting the artist or the record company but the engineers, lyricists, and musicians. If we all just download our music from these sites then no one will get paid for their music and ultimately all we'll have is poor quality music.
If you're downloading your music be aware of DRM you generally do not want to use websites that make use of this as the files you download will be severely limited in how they can be transferred, etc. Also stay away from the wma format (windows media format) which typically cannot be played on Linux and is generally the worst offender in the DRM area.

Music Players
After trying every player these is for Linux, Gnome users will want to stick with Rhythmbox. It's simply the best most intutivie solution. Although Songbird will eventually give Rhythmbox a run for it's money: [http://www.getsongbird.com/](http://www.getsongbird.com/) Songbird is the most Winamp like player for Windows users looking for a replacement. If you want advanced syncing and cover art features then you have ot install Amarok, a KDE application that works quite well in Gnome. Possibly you might prefer it's system for playing music and then it can be a full replacement for you (as it has many advanced features) but personally I found it takes me longer to select my music for playing on my PC than on Rhythmbox.

Amarok Settings: If you install Amarok and you want to sync and use cover art on your removable device (and there is no better program for this) you'll have to tweak a few settings. You'll have to install and use MySQL or else Amarok will be too slow, here's a guide: [http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html](http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html)
Although the setting for Amarok didn't work for me (might be a Gnome thing), instead I typed in 'localhost' under host name and 'root' under user name.

Your removable Music Player
I'm not going to deal with Ipods as there is more than enough information about them available. I'm specifically dealing with cell-phones and other devices with removeable memory. Plug-in your device, if Ubuntu recognises it then continue on from here, if it is not recognised at all then check the hardware forums or google for more help. If your phone is recognised as a music player (when you open Rhythmbox your device is listed on the left side) then you can skip the next step.
If Ubuntu recognises your device but you can't access it, format your memory card (back-up your information before you do) via your phone (see your phone manual for more).
If your device is recognised by Ubuntu as a mass storage device but you don't see it in Rhythmbox do the following: Go to the root directory of your removable device (the top most directory) and create a new file with the name “.is_audio_player” note the dot before the words is_audio_player. Open this file in a text editor and type the following:
audio_folders=music/
folder_depth=2
Now Rhythmbox, Banshee and other players should recognise your memory card as a music player. It is possible to configure Amarok to recognise your device with creating this file, but doing so make it much easier to work with. 

The easiest solution now is to use Rhythmbox and drag and drop your music into your music player. If you're using FLAC Rhythmbox can automatically convert it to any format. If you want to convert your files to MP3, for example, go to Edit – Preferences – Music – Preferred Format – and choose CD Quality MP3, these settings can be editing as you like. Bear in mind that Rhythmbox does not always convert FLAC files as it should and this is where Amarok can be helpful. Additionally it's possible 

Note this guide was compiled with Hardy and the new version of Amarok can't do most of the things mentioned above. Hope this helps someone.

---

