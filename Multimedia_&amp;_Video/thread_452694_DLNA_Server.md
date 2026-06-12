---
title: "DLNA Server"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by binarymelon on 2007-05-23
I wasn't sure if I should post this here or in networking, but I'm feeling very alphabetical this afternoon.  Mods can move it if necessary.

With the news that the PS3 will be DLNA enabled with the next big update which may drop as early as this week, I was just wondering if anyone knew of any quick and easy ways of serving up media on my Ubuntu box with a DLNA able server.

---

### Post by Reapman on 2007-05-23
I'd love to know as well, I just read about this, and right now use an Ubuntu server to stream media to my XBox Media Centre PC.  I'd love to use my PS3 for this role since the XBox is gettin old and sometimes having trouble booting up right.

Anyways anyone know details on this?  From googling I see Buffalo has built a Linux based NAS device that supports DLNA, and Intel apparently has some sort of proof of concept on their site, but i don't yet know the details.  Anyone know?

---

### Post by Reapman on 2007-05-24
Well I installed the new firmware, and am trying out the media server made by these guys:
[http://www.twonkyvision.com/](http://www.twonkyvision.com/)  Note this product is a 30 day trial, so not free.  

So far it's far from perfect, however I'm not sure if it's because I'm doing something wrong, PS3, or the software doesn't properly mesh with the PS3.  Photos seem OK,  I could watch a music video in MPG format (not sure exact codec right now), but none of my music seemed to work and 90% of my videos didn't work either.  Curious if anyone else had any luck?  or a different product that worked just fine for them?

:popcorn:

---

### Post by Ciego on 2007-05-24
I hope that the PS3 update doesn't leave us exclusive Linux users out in the cold when it comes to streaming.  I will be watching this topic closely.

---

### Post by binarymelon on 2007-05-24
Hopefully there's a solution that will allow for on-the-fly transcoding as well so we can view divx files and other not supported file types.

---

### Post by Reapman on 2007-05-24
Twonky + VLC apparently allows on the fly Transcoding, I'm going to give it a go tonight.  if I get this going I'll try and fire off a quick howto.

FYI, apparently they released a beta of version 4.4  for Twonky that speciifcally addresses the PS3 (that was fast!)
[http://www.twonkyvision.com/Download/TwonkyMedia/index-4-4.html](http://www.twonkyvision.com/Download/TwonkyMedia/index-4-4.html)

Thread I found this in:
[http://www.twonkyvision.de/forum/viewtopic.php?t=3064](http://www.twonkyvision.de/forum/viewtopic.php?t=3064)

Thread on PS3 and Twonky in general:
[http://www.twonkyvision.de/forum/viewtopic.php?p=11606#11606](http://www.twonkyvision.de/forum/viewtopic.php?p=11606#11606)

Ok so apparently VLC Transcoding on the fly works by streaming a specific video, you can't choose it "on the fly" with the PS3, or pause/ff/rr.  Which to me is kinda useless.  Going to keep looking but if I have to stick with XBMC then so be it.  I can't see Sony ever supporting stuff like DivX or Xvid :/

---

### Post by c0reyf on 2007-05-25
> **Ciego said:**
> I hope that the PS3 update doesn't leave us exclusive Linux users out in the cold when it comes to streaming.  I will be watching this topic closely.

Unfortunately I believe they are going to cater to M$ customers as they are going to be the majority up front. Eventually someone will make one for us penguins. Just to try it I did use WMP11 on a dual boot and it was sweet to watch the videos and browse my netowrk on TV from a laptop.

---

### Post by Reapman on 2007-05-25
Try TwonkyVision, I know that works on Linux I've done it and there's posts on their forums of other users using it.  It's possible other products like uShare that are free would work, hopefully anything uPNP would work.  

Your just limited with video codecs, but that's a PS3 limitation (hopefully just for now)

---

### Post by lando786 on 2007-05-25
in windows u can use nero home because it has on the fly transcoding, im wondering if there is anything like that in linux i cant seem to configure twonky shares. Is there a program with on the fly transcoding for linux?

---

### Post by Reapman on 2007-05-26
TVersity apparently does transcoding on the fly, but right now it doesn't support the PS3 1.80 firmware, they'll probably fix that I'm sure.  TVersity is free but windows only (googling it should be the first link)  so not what we're looking for :/  I don't know how well it would run under VMWare, guessing not good for transcoding.

FWIW - listening to some MP3's streaming via Twonky right now, the 4.4 beta version seems to work good for audio and photo at least.  Going to try a free product like uShare this weekend.

I imagine in a month or more from now there should be a good solid option to make the PS3 workable as a complete media system. :)

---

### Post by crane on 2007-05-26
Twonkyvision is working great so far.

---

### Post by Crosbie on 2007-05-26
Will [GeeXbox Ushare]("http://ushare.geexbox.org/") work?

---

### Post by NobodySpecial on 2007-05-26
Check out this thread for the answer:
[http://boardsus.playstation.com/playstation/board/message?board.id=ps3&message.id=1547529]("http://boardsus.playstation.com/playstation/board/message?board.id=ps3&message.id=1547529")

> UPnP AV MediaServer software

    * XBMC (Xbox Media Center), a free, open-source software media-player/media-center for Microsoft's Xbox game-console.
          o XBMC built-in UPnP client and UPnP server code are from Platinum UPnP C++ SDK (open source under GPL).
    * Windows Media Connect from Microsoft - free UPnP AV MediaServer and Control Point (server and client) for Microsoft Windows
          o Windows Media Connect (WMC) version 2.0 can be installed for usage with Windows Media Player 10 for Windows XP
          o Windows Media Connect (WMC) version 3.0 can be installed for usage with Windows Media Player 11 for Windows XP
          o Windows Media Connect (WMC) version 4.0 already comes pre-installed on Windows Vista with its WMP version 11
    * AwoX mediaCTRL, a commercial DLNA 1.5 Controller, Renderer and Server for Microsoft Windows.
    * MythTV, an open source HTPC and PVR software for Linux, with a built-in UPnP AV MediaServer.
    * SnapStream Beyond TV (BTV), a commercial Media Control/Renderer/Server and PVR software for Windows.
    * Musicmatch Jukebox, a commercial MediaServer UPnP MediaServer and music-player for Windows, (also features media organizing functionality).
    * Rhapsody, by RealNetworks, a commercial UPnP MediaServer (with a online music service) for Win/Mac, (Rhapsody requires an WMDRM-ND encrypted DRM connection).
    * GeeXboX, an opensource lightweight Media center has uShare for Linux.
    * MediaTomb - free, open source (GPL) UPnP AV MediaServer for Linux, Mac OS X, FreeBSD and Cygwin which also runs on NAS devices. Allows users to define a custom container layout by the means of JavaScript, has a nice AJAX based UI.
    * TwonkyMedia - Commercial and light-weight UPnP AV Server for Windows, Linux and embedded systems. Can be installed for instance on an NSLU2.
    * Nero MediaHome - Commercial media-player/media-center software for Windows which is shipped as part of the Nero product suite, it includes a UPnP AV Server (and a UPnP AV Client). The latest version is able to capture and stream live TV and transcodes all common source file formats in real-time to other UPnP AV Clients via the UPnP AV Server.
    * Fuppes - free open source UPnP MediaServer, supports transcoding of diverse audio formats to mp3. Only directory browsing supported.
    * TVersity - free closed source UPnP MediaServer, currently in beta, which allows on-the-fly transcoding to wmv.
    * SimpleCenter is a Java-based UPnP AV MediaServer
    * Philips Media Manager is a free closed source UPnP AV MediaServer for Windows and Macintosh that is based on Streamium


So it looks like there are many potential options for DLNA service to the PS3.

Would appreciate the first person to stream to PS3 from Ubuntu please post feedback here.

---

### Post by lando786 on 2007-05-26
i could not get twonkyvision to work it detected it but all the folders were empty i read they made a patch for the ps3 1.8 FW any1 try it out i didnt get how to config twonky shares

---

### Post by NobodySpecial on 2007-05-26
Just got [GeeXboX uShare]("http://ushare.geexbox.org/") working!  Pictures work fine.  The PS3 is finicky about what music and videos it will play.

Problem is, I installed it under Arch Linux.  Now will have to figure out how to get it going under Ubuntu.  If anybody beats me to it, please post here.

---

### Post by ralyon on 2007-05-30
Just compiled svn mythtv from a couple days ago and it popped up on the ps3. I haven't tried audio as my collection is completely ogg and I don't expect it to work but I was able to get a recording from my pvr150 to play fine. Recordings from my pcHDTV with an OTA signal would play video but not audio.

Issues so far:

1. If you browse away from the mythtv menu it becomes locked out until you restart the backend (and possible the ps3) I noticed that it also locks out the web status on port 6544 so it is most likely a mythtv problem.

2. There is no pause/ff/rw available. There is a patch that I will try in the next couple days at [http://pastebin.ca/510453](http://pastebin.ca/510453). I will update when I've tested that.

3. the PS3 does not play nupple vids so anything thats been transcoded is listed as an unrecognized format. I would like to find a way to change the transcoding from nupple to mp4, x264 which should work. The only info I've found so far relates to exporting which I would prefer to keep it in the recordings.

Its not a myth frontend, but if it plays the videos I would hope I could do anything else from mythweb with the browser. I hope to be able to get that midtower out of the living room soon. :D

---

### Post by icedfusion on 2007-05-30
Hi,
I have ushare working in ubuntu, however I still can only see pictures - no films/tv/music - I have tried a variety of the formats listed by the PS3 manual and I can only view jpeg pics.

I had the same problem with gmediaserver as well.

I also tried gnump3d and tried to use the browser to access audio files, but again it says the files do not exist. Not sure if its because of a network issue of the PS3 just does not like 'other' DLNA servers apart from Windows Media Player 11....ffs!!

followed a howto which basically said:

add the following line to your /etc/apt/sources.list file :

```
deb http://www.geexbox.org/debian/ unstable main
```

and install ushare with :
```

apt-get update && apt-get install ushare
```

add a directory to share with:

```
ushare -c /shares
```

All instructions found here:
[http://ushare.geexbox.org/](http://ushare.geexbox.org/)

ice.

---

### Post by NobodySpecial on 2007-05-30
icedfusion - I had the same problem with GeeXBox under Linux.  Its a problem with the program itself - will have to be updated to work with the PS3.

Mediatomb has already done so on their SVN version.  I haven't got it going yet, but further details here:
[http://sourceforge.net/forum/forum.php?thread_id=1742633&forum_id=440751]("http://sourceforge.net/forum/forum.php?thread_id=1742633&forum_id=440751")

---

### Post by NobodySpecial on 2007-05-30
Here's the deal on Mediatomb.  The SVN version is reported to work with the PS3.  We just need some smart people to help get it going on Ubuntu!

Here is a start to get the ball rolling:
```
sudo apt-get install build-essential subversion libsqlite3-dev zlib1g-dev libmagic-dev libtagc0-dev libexif-dev autoconf automake
cd mediatomb
autoreconf -i
./configure --prefix=/my/test/install
make
make install

```
Obviously, change "/my/test/install" to wherever you want to install.

The make step stops with various errors which I can't decipher.  The configure step says that the spidermonkey dev files are missing.  I don't think that will prevent compiling, as the README says its optional.  If required, its a huge problem on Ubuntu, because you can't install the spidermonkey dev files without un-installing most of your system.

So I would appreciate if somebody smarter than me would lend a hand in compiling this.

Addendum: The make step crashes when compiling of UPNP.

---

### Post by icedfusion on 2007-05-31
[oops - looks like i have just re-iterated 'nobodyspecial's post]

I have found the following install instructions for Mediatomb in Ubuntu which has been updated to work with the PS3.


Reports indicate that this works for mp3, mp4, mpv, mp3g2 etc.....

[http://mediatomb.cc/pages/download](http://mediatomb.cc/pages/download)

I will be installing this when I get home later today!!


Cheers.

ice.

---

### Post by icedfusion on 2007-05-31
Whey hey....it works...finally, the guys over at MediaTomb have it sorted.

I just installed the program via apt-get as instructed from the link I gave above.

Once installed I just ran it by typing:
mediatomb

and it auto-generated alot of stuff - I then selected my  directory that mediatomb should be using via the web interface.

NOTE:
You MUST add the following line to the /home/<username>/.mediatomb/config.xml:

<protocolInfo extend="yes"/>

in between the <server> </server> section of the xml config script!

I can now view the supported PS3 formats.

In fact, I was doing all my testing by sitting at my linux machine and 'remote playing' the ps3 via my psp. Then when the streaming started, it came straight to my PSP!! Quality!!! Really cant wait to see if I can access it from an outside wifi network and when they sort out the real time transcoding!!!

ice.

---

### Post by crane on 2007-05-31
Pictures work OK for me and some videos. But the MP3's come up as unsupported Format?
I will look into it further. This is running on Edgy. I may try it on Fiesty to see if that makes a difference.

---

### Post by NobodySpecial on 2007-06-01
icedfusion - Thanks for clarifying how to do this.  I didn't realize the package was already updated.  No compiling is necessary.

It works great!  I'm transcoding my videos into mp4 files - they stream flawlessly.  Now I might need to get a PSP . . . .

---

### Post by icedfusion on 2007-06-01
> **crane said:**
> Pictures work OK for me and some videos. But the MP3's come up as unsupported Format?
I will look into it further. This is running on Edgy. I may try it on Fiesty to see if that makes a difference.


Have you added the following line to your config.xml?

<protocolInfo extend="yes"/>

I think what you see will happen if you dont have the following line added.


Cheers.

ice.

---

### Post by jgc on 2007-06-01
I have this running nicely on Edgy! :D

Is there a maximum number of folders viewable?... I have around 100 folders (basically a folder per artist), but can only view the first 23?

---

### Post by crane on 2007-06-01
> **icedfusion said:**
> Have you added the following line to your config.xml?

<protocolInfo extend="yes"/>

I think what you see will happen if you dont have the following line added.


Cheers.

ice.
I say I did. It seems I had protocolinfo instead of protocolInfo so I will give it a try tonight.
I added the line towards the end of the server section. It shouldn't make a difference as the where it is as long as it's between <server. and </server> right?

---

### Post by jgc on 2007-06-01
> **jgc said:**
> I have this running nicely on Edgy! :D

Is there a maximum number of folders viewable?... I have around 100 folders (basically a folder per artist), but can only view the first 23?

It's fine, just a little slower than I was expecting! Great stuff, works a treat! :D

---

### Post by crane on 2007-06-01
Now am am ready to leave work and go mess with this some more!:popcorn:

---

### Post by crane on 2007-06-02
Well that seemed to fix the mp3 problem. Mediatomb has issues playing many of the videos I have. Twonkymedia played everything the first time I ran it, now I keep getting Connection errors when I try to play videos.
Twonky was a good bit faster and smoother than mediaomb was as well.

---

### Post by Reapman on 2007-06-02
Another Thumbs Up for Mediatomb.  Only issue I have now is that AVI files are not "hidden" from view in the PS3, and show up as unsupported.  RemotePlay also works great on the PSP, trying to Convert a few AVI's over to MPG and see if the quality suffers much.  Anyone have advice on some Conversion tools that are a good mix of quality / speed?

---

### Post by hanexar on 2007-06-04
> **NobodySpecial said:**
> 
  I'm transcoding my videos into mp4 files - they stream flawlessly.  Now I might need to get a PSP . . .

Oh please, tell me how you are doing it. I've tried so many different way without success so far... except from booting windows...

---

### Post by boarderpatrol on 2007-06-04
I configured ushare to stream jpegs to my ps3 but reading in the forums here ushare is not working with mp3 yet.  I came across this thread and decided to give it a shot.  

I am trying to use Mediatomb to stream some mp3 from my fiesty box to my ps3.  I am not sure how to install mediatomb using the directions on the  given page. Instructions from their site are at bottom of my post.  Here is what i have tried an not sure of.

from termiinal:

sudo wget [http://apt.mediatomb.cc/key.asc](http://apt.mediatomb.cc/key.asc) -O- -q | sudo apt-key add -
(key id: A2DCDB57; fingerprint: F1A6 C581 6BC1 AD55 80E9 EEFE 48AD 7164 A2DC DB57)

  I added sudo command. I have tried pasting in just wget portion and different key id parts as well as the entire statement.  I am getting a enter passphrase in terminal which i"m confident is not my root password.  What do i place there?  It must be the key id or fingerprint.  I have tried entering the key id and fingerprint key  but only recieve a  fingerprint: command not found.  Can some help break this down for me.   This seems simple but I cant seem to figure out how to understand these instructions.   Thank you for any help.


> Debian and Ubuntu

The best way to install Debian or Ubuntu packages is via our APT repository. To use it properly, you will need our GPG key (for all distributions except “sarge”). To install it, issue the following command as root:
wget [http://apt.mediatomb.cc/key.asc](http://apt.mediatomb.cc/key.asc) -O- -q | sudo apt-key add -
(key id: A2DCDB57; fingerprint: F1A6 C581 6BC1 AD55 80E9 EEFE 48AD 7164 A2DC DB57)

Below you will find the appropriate “deb” line to add to your /etc/apt/sources.list for all supported distributions and a direct download to the ”.deb” file in case you don’t want to use the APT repository. We also provide source packages for these distributions (add the same line, but with “deb-src” instead of “deb” at the beginning), so you should be able to build MediaTomb for platforms other than i386, AMD64 and ARM.

If you want APT to automatically install all dependencies on Ubuntu, you have to enable the “universe” component. (Spidermonkey isn’t part of the “main” component there.) This doesn’t apply to Debian.

There are basically two ways of starting MediaTomb: you can either start it directly as a normal user or run it as a deamon. For the latter a “mediatomb” user and group will be added automatically and you’ll find the configuration under /etc/mediatomb/config.xml, the logfile under /var/log/mediatomb and the database under /var/lib/mediatomb/. If you want MediaTomb to be started at boot time, change the NO_START option from "yes" to "" in the file /etc/default/mediatomb. To access the UI of the MediaTomb daemon open the file /var/lib/mediatomb/mediatomb.html in your browser.

---

### Post by hanexar on 2007-06-04
> **boarderpatrol said:**
> 
sudo wget [http://apt.mediatomb.cc/key.asc](http://apt.mediatomb.cc/key.asc) -O- -q | sudo apt-key add -
(key id: A2DCDB57; fingerprint: F1A6 C581 6BC1 AD55 80E9 EEFE 48AD 7164 A2DC DB57)


Just copy and past the first line, then go add the repositories in your /etc/apt/sources.list as stated in the download page:

for feisty
```
deb http://apt.mediatomb.cc/ feisty main  
```
for edgy
```
deb http://apt.mediatomb.cc/ edgy main 
```

then you: 

```
sudo apt-get upgrade 
sudo apt-get install mediatomb
```


That being said, I have a problem with mediatomb myself. When reading stuff from my PS3, the reading stop after a few second (10 seconds to 1 minutes). I can restart the process right away, but it always do the same. I even get kick out of the menu when browsing for too long. Any idea what's going on? There's no error on the console on the PC...

---

### Post by boarderpatrol on 2007-06-04
:popcorn:
thank you Hanexar.

  Installed like a charm. I am currently setting it up so I cannot attest to any speed issues.

Update:  Mediatomb works well for streaming mp3 from fiesty to mp3.  I didnt see any issues with slow speed.

               However:   only 4 or 5 subfolders are being displayed on the ps3 out of perhaps 75.  It may take a while for mediatomb to complete the scan of directory  
                                   and build database.   I used the web configurator btw.  pretty nifty tool imho

---

### Post by hanexar on 2007-06-04
I'm glad I could help. It took me a very long time to build the database, so don't worry about that. For my problem, I just shut down some of the millions of processes running on my poor old PC... Seems like I was over working it. Works like a charm now.

Just need an easy way to convert my divx to h.264 (with ubuntu) and I'll have the perfect media center!

---

### Post by icedfusion on 2007-06-05
Well, glad people have got it sorted.
The downsides i see is the very limited amount of file types it can play and the way it lists files.

ahh well - looks like i will have to build that linux media centre after all!

ice.

---

### Post by Zeikcied on 2007-06-06
> **icedfusion said:**
> Have you added the following line to your config.xml?

<protocolInfo extend="yes"/>

I think what you see will happen if you dont have the following line added.


Cheers.

ice.
I just set up MediaTomb, with that line in the config.xml file, in the correct spot, and my PS3 says that all the audio files are an unknown format.

I found that a lot of the audio files, as listed in the MediaTomb database, don't have their proper file extensions.

I did get a lot of errors regarding invalid characters, likely in the file names or the ID3 tags.  But not even the files that have the proper extension are recognized by my PS3.

What is the problem?

---

### Post by NobodySpecial on 2007-06-06
hanexar - there is a way to convert video to PS3-compliant h.264 in Linux, but it certainly isn't easy.  There is a [long thread]("http://ubuntuforums.org/showthread.php?t=273635") on how to make h.264 files in general, and I posted [here]("http://ubuntuforums.org/showthread.php?p=2795870#post2795870") how to make PS3 compliant ones.

---

### Post by crane on 2007-06-06
> **Zeikcied said:**
> I just set up MediaTomb, with that line in the config.xml file, in the correct spot, and my PS3 says that all the audio files are an unknown format.

I found that a lot of the audio files, as listed in the MediaTomb database, don't have their proper file extensions.

I did get a lot of errors regarding invalid characters, likely in the file names or the ID3 tags.  But not even the files that have the proper extension are recognized by my PS3.

What is the problem?

I had the same issue, turned out a had entered the text wrong. Had a lower case i where I should have had an Upper case I. Be sure to check the format and how you typed it. Even copy and paste can give problems if it was posted wrong.
Here is a copy of my server section:

-<server>
&#8722;
	<ui enabled="yes">
<accounts enabled="no" session-timeout="30"/>
</ui>
<name>MediaTomb</name>
<udn>uuid:6d02b8ec-bd17-4156-b3d3-5369904c5fba</udn>
<home>/home/jason/.mediatomb</home>
<webroot>/usr/share/mediatomb/web</webroot>
&#8722;<storage driver="sqlite3">
<database-file>mediatomb.db</database-file>
</storage>
<protocolInfo extend="yes"/>
</server>

---

### Post by Zeikcied on 2007-06-08
> **crane said:**
> I had the same issue, turned out a had entered the text wrong. Had a lower case i where I should have had an Upper case I. Be sure to check the format and how you typed it. Even copy and paste can give problems if it was posted wrong.
Here is a copy of my server section:

-<server>
&#8722;
	<ui enabled="yes">
<accounts enabled="no" session-timeout="30"/>
</ui>
<name>MediaTomb</name>
<udn>uuid:6d02b8ec-bd17-4156-b3d3-5369904c5fba</udn>
<home>/home/jason/.mediatomb</home>
<webroot>/usr/share/mediatomb/web</webroot>
&#8722;<storage driver="sqlite3">
<database-file>mediatomb.db</database-file>
</storage>
<protocolInfo extend="yes"/>
</server>
The instructions on the download page are confusing.  As they seem to be quite outdated.

It says that the config files and mediatomb.html are in /var/lib/mediatomb, but they aren't.  It also mentioned a config file in /etc/mediatomb, and that's the one I edited.  Now I figure out myself that the proper config and html files are in ~/.mediatomb.  This is ridiculous.  But hopefully now I have it set properly.  I just hope I don't have to rescan the stuff in the database.  But I probably will...

Thanks anyway.

---

### Post by crane on 2007-06-08
> **Zeikcied said:**
> The instructions on the download page are confusing.  As they seem to be quite outdated.

It says that the config files and mediatomb.html are in /var/lib/mediatomb, but they aren't.  It also mentioned a config file in /etc/mediatomb, and that's the one I edited.  Now I figure out myself that the proper config and html files are in ~/.mediatomb.  This is ridiculous.  But hopefully now I have it set properly.  I just hope I don't have to rescan the stuff in the database.  But I probably will...

Thanks anyway.

I not sure about rescanning. But if it works it should be worth it. I have made a habit of looking in my home directory for config's first. No matter if I read where the config file is. Many programs have a file in the home directory.
 Did that seem to work for you?

---

### Post by balthamaisteri on 2007-06-13
Oh noes, i think that i need to buy me a psp :<

hope they add support to something else than mp4.

---

### Post by JOWIROMA on 2007-06-27
I have tried MediaTomb and the ps3 found the server but I could not play any file and now I tried to run MediaTomb again and it wont start so I tried TwonkyVision and it work, with my ps3 and xbox360 the only problem that I found is that it wont play my AAC audio files that I have in my Ipod library.
Does anyone has a solution to play those AAC files through TwonkyVision?

---

### Post by Spyplane on 2007-07-17
Has anyone been able to install this recently.   I followed the directions to the tee, but I still can't get apt to find mediatomb.

E:  Couldn't find package mediatomb


Was there something else you had to do to get this to work?    I added the server to sources.list and I did the wget for the key.

---

### Post by solracarevir on 2007-07-19
I compiled mediatomb from source and it's working great for Mp3's and pictures in jpeg format,:KS you just have to add the following line after your  <server> line
```
<protocolInfo extend="yes"/>
```

The only issue i have is that most of my  music is Mp4. :( videos plays fine as well but in my case only .MOV format.:( I think we should find a way to do Transcoding with mediatomb.....:mad:

---

### Post by meanmrmustard on 2007-08-19
> **Spyplane said:**
> Has anyone been able to install this recently.   I followed the directions to the tee, but I still can't get apt to find mediatomb.

E:  Couldn't find package mediatomb


Was there something else you had to do to get this to work?    I added the server to sources.list and I did the wget for the key.

Did you apt-get update and upgrade?

---

### Post by koenbeek on 2008-01-03
I've set up mediatomb on my gutsy AMD 64 PC (with the mediatomb feisty repositories as they don't seem to have gutsy reps yet)

I had to add the <interface>eth0</interface> to the server section in ~/.mediatomb/mediatomb.xml to get my PS3 to find the mediatomb media server

I had to add the <protocolInfo extend="yes"/> in the ~/.mediatomb/mediatomb.xml file in the server section to get my PS3 support my mp3 files.

And I still need to change the media type for my avi file to video/divx for them to be recognised by the PS3 as supported divx formats

Some AVIs still don't play (maybe some type of divxs are not supported ?) but I'm reasonable happy, everything that works, works fine and fast.

still need to get all my AVIs to work and to get them to work without having to change the media type !

---

### Post by Craig Caldwell on 2008-01-03
I just wanted to mention that there is an issue with linksys routers. I've switched away from my WRT54G linksys and back to an old wired dlink to avoid the ps3 disconnect from server messages.
I hope mentioning this will help others avoid wasting time.

craig

---

### Post by koenbeek on 2008-01-03
I got rid of the avi problem (having to manually update the filetype to video/divx to get them to work on the PS3) by adding the avi -> divx translation in the configuration file in ~/.mediatomb/config.xml

all the changes I did :

1. to get the PS3 to see the media server : specified the network interface (mine is eth0, use ifconfig to check what yours is)

<server>
    <interface>eth0</interface>

2. to get the mp3 to be a supported type by PS3 

<protocolInfo extend="yes"/>

(just after the <interface> line)

3. to get the avi files to be recognised as divx formats)

        <map from="avi" to="video/divx"/>

 just before the  </extension-mimetype> line

hope this helpes someone

---

### Post by crane on 2008-01-03
A problem with Linksys routers? Is the problem hardware or software? I have a Linksys running different firmware and so far I have not had disconnect problems in game or from media server.

---

### Post by uschxc on 2008-04-28
for those who have used twonkyvision and mediatomb, how much faster/better is twonkyvision?  20 bucks isn't horrible if its a much better server.  will both work on ps3 AND 360?  how has ushare's compatibility and performance come along?  it seems to be working via this thread: [http://www.ps3forums.com/showthread.php?t=74506](http://www.ps3forums.com/showthread.php?t=74506)

also, anyone have a clue as to how i could stream .mkv to the ps3?

---

### Post by ruffneck on 2008-05-04
I second this. Anyone?

---

### Post by crane on 2008-05-04
I haven't messed with either in a while. I have recently installed Fuppes i believe it is called. I plan ot mess with it over the next few days.

---

### Post by KillaB7 on 2008-05-08
Any idea why a file encoded with XviD, shows up as XviD in MediaTomb when viewed from the PS3 but then turns into MPEG-4 when copied to the PS3 hard drive?

It doesn't happen when I move files with a memory stick and I don't recall it happening when I tested with TVersity.

I'm pretty sure it's not being transcoding since it's not enabled in /etc/mediatomb/config.xml and there's very little CPU usage during the copy.  Is it an AVI wrapper mix-up.  The files play fine, I just don't get why there's a change?

---

### Post by inportb on 2008-05-08
If you play it in VLC, you can discover what format the A/V streams are in.

---

### Post by KillaB7 on 2008-05-08
> **inportb said:**
> If you play it in VLC, you can discover what format the A/V streams are in.

They are unquestionably XviD encoded.

---

