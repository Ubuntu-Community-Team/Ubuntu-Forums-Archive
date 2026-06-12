---
title: "[SOLVED] Using Ubuntu as a DLNA Media Server for Samsung TV"
date: 2009-06-27
forum: Multimedia Software
---

### Post by sobrien on 2009-06-27
I have a Samsung UN46B8000 LCD television set to which I wanted to feed .jpg, .mp3, and other files from my computer which is running Ubuntu 9.04.  Samsung televisions have included an Ethernet port and the ability to connect to a DLNA server for quite a long time.

I used Synaptic (or apt-get) and installed MediaTomb, which is a UPnP (DLNA) server, but it didn't work as it was installed.  It would show thumbnails of my .jpg files, but it said "Unsupported File Type" or something when I tried to start a slideshow, so I did the following:  

1)  Enter mediatomb into a command line just so it creates a directory under my user ID.  Then I exited mediatomb and edited the ~/.mediatomb/config.xml file and made the following changes:

2)  Remove the comment tags <!-- and --> that were around the <custom-http-headers> section.

3)  Add the following two lines to the <custom-http-headers> section:

<add header="transferMode.dlna.org: Streaming"/>
<add header="contentFeatures.dlna.org: DLNA.ORG_OP=01;DLNA.ORG_CI=0;DLNA.ORG_FLAGS=01700000000000000000000000000000"/>

4)  Change <protocolInfo extend="yes"/> to say "yes"; it says "no" when it is installed.

That's it; when I started mediatomb by entering: mediatomb into a command line and then used Firefox to add some pictures and audio files to the mediatomb database, and finally used the TV remote control to go to MEDIA.P, up popped my pictures and .mp3 files.  Very neat - .jpg files look great on a 46 inch High-Def monitor, and it is very cool to add or remove files on my desktop and make them available or remove them from my TV set over my home network.

There is a good discussion at:  [http://forums.tversity.com/viewtopic.php?f=2&t=10992&st=0&sk=t&sd=a&start=45](http://forums.tversity.com/viewtopic.php?f=2&t=10992&st=0&sk=t&sd=a&start=45) - a tip o' the hat to "crappylogin" for providing the custom header lines that fixed the problem!

---

### Post by dillzz on 2009-07-16
Sobrien,

Thank you for this information.  I can finally get Music + Pictures streamed to my TV.  I am however having problems with the video, i have tried endless encodings and no supported format :(.  It however works fine on the PS3 and their dlna implementation...Any ideas?

---

### Post by Rafiek on 2009-10-16
To be honest. This did not solve my problem. I have a Samsung LN40B650.
As a test I installed Mediatomb on my laptop and followed these instructions. The problem remained. I can see all the content (music, pictures, movies) but I always get "Unsupported File format"
I have no Idea that to do next.

---

### Post by redbeardmcg on 2009-11-24
Add this to your <extension-mimetype> node:

<map from="avi" to="video/mpeg"/>

That along with the custom http-header and you should be able to do... everything :)

-Ryan

---

### Post by ydo on 2009-12-08
Got my new Samsung TV from 6-series (40" 650) to work with the custom HTTP headers, however I CAN NOT PAUSE or fwd VIDEO, just pause MP3. This makes it kind of unusable for watching video.. :-/
Does it work for you? On a 6-series TV? Any other tweaks floating around?

I found that some people got pause to work using the development version of mediatomb 0.12.0, I run that too but it doesn't work for me.
[http://forums.cnet.com/5208-13973_102-0.html?threadID=333752](http://forums.cnet.com/5208-13973_102-0.html?threadID=333752)

---

### Post by ydo on 2009-12-09
Installing SamyGO which can mount samba, nfs and upnp/dlna as virtual usb drives gives access to these features which are disabled over normal dlna. 
AND it is way cool to be able to ssh the TV ;-)

---

### Post by dbcal on 2009-12-15
Kinda rehashing what some others already said here, but this is what worked for me, and pics, mp3s and videos (DivX included) now work (including ability to pause video).
Setup: MediaTomb 0.11, Samsung LN46A750 TV, Ubuntu 9.10.

1) installed MediaTomb via Ubuntu's Software Center

2) open /etc/mediatomb/config.xml in your text editor of choice

3) remove the comment tags around the <custom-http-headers> section and make that section look like this:

    <custom-http-headers>
      <add header="transferMode.dlna.org: Streaming"/>
      <add header="contentFeatures.dlna.org: DLNA.ORG_OP=01;DLNA.ORG_CI=0;DLNA.ORG_FLAGS=017000 00000000000000000000000000"/>
    </custom-http-headers>

4) Under <mappings>, add <map from="avi" to="video/mpeg"/>

5) save and close config.xml and restart mediatomb (`sudo service mediatomb restart` from command line)

6) load MediaTomb web interface and tell it where to start looking for files.  If you already had it scanning for files, they're likely to have the wrong mimetype associated with them (divx/avi videos, anyways).  If so, just use the web interface to remove all the video content it had discovered (click a folder and click the red 'X' on the right-hand side), then tell it to rescan/rediscover those folders....the vids should now have video/mpeg associated with them (check by clicking the 'edit' icon for a given folder).

Hope that helps!  I only got this to work thanks to the posts here, so thanks!

---

### Post by tomazo on 2009-12-21
I just brought my SAMSUNG UE40B7000 from shop and can't get .mkv's play over DLNA and Mediatomb :/ It says unsupported format..but plays just fine from USB key.
How do I fix it?

EDIT: Alright, I got it to work with MiniDLNA. It plays subtitles too when they are named same as mkv file. It appears tho that TV won't play mkv with multiple audio streams. Any ideas on that?

---

### Post by Redsandro on 2010-02-03
I've got it working, too. Full .avi and .mkv support.

**Except for some important stuff.**

[s]I'd really like to know how to **get fast-forward and rewind to work**. It doesn't. It only does pause.[/s] The buttons on my remote were programmed incorrectly :tongue:

Also, Samsung **does not play DTS audio**. Does anyone know how to transcode just DTS audio? My server is not strong enough to transcode HD video too. The video is not the problem anyway. ;)

When I play back a DTS containing MKV on the tv, it plays without audio. I tried adding the profile
```
      <profile name="vid-dts" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="ffmpeg" arguments="-y -threads 2 -i %in -acodec ac3 -ab 192000 -vcodec copy -f matroska %out"/>
        <buffer size="14400000" chunk-size="512000" fill-size="120000"/>
      </profile>
```But now the entire file will not play anymore.

[s]Finally, is there a way to **change the audio stream**? It always plays the first one, and that is usually not the English one.[/s] MediaTomb handles this fine. It's the television that might not. I can choose the audiostream just fine in XBMC. Subtitles also. :D

So anyone with the knowledge, please help! :)



[SIZE="4"]How to do it.[/SIZE]

Two people mentioned it before. Here's my version.

**MediaTomb 0.12**
**Samsung 32b650**

[list]
[*]Edit config, for example, alt+f2 enter:
```
gksudo geany /etc/mediatomb/config.xml
```
[*]No need to remove comments, just add:
```
    <custom-http-headers>
      <add header="transferMode.dlna.org: Streaming"/>
      <add header="contentFeatures.dlna.org: DLNA.ORG_OP=01;DLNA.ORG_CI=0;DLNA.ORG_FLAGS=017000 00000000000000000000000000"/>
    </custom-http-headers>
```
[*]Under **<mappings>**, add:
```
<map from="avi" to="video/mpeg"/>
```
and change mkv into:
```
<map from="mkv" to="video/mpeg"/>
```
[SIZE="1"](Because Samsung wants everything it secretly supports just to be called mpeg.)[/SIZE]
[*]Restart *MediaTomb*:
```
sudo /etc/init.d/mediatomb restart
```
[*]Remove and re-add all your video's (updates mime-types)
[*]Voilá!
[/list]

---

### Post by Redsandro on 2010-02-04
> **tomazo said:**
> It appears tho that TV won't play mkv with multiple audio streams. Any ideas on that?
The TV only plays the default audio stream, even if your DLNA server offers both. you can manually get rid of those other streams you don't need by remuxing the media files.

---

### Post by GoodP123 on 2010-02-18
> **sobrien said:**
> I have a Samsung UN46B8000 LCD television set to which I wanted to feed .jpg, .mp3, and other files from my computer which is running Ubuntu 9.04.  Samsung televisions have included an Ethernet port and the ability to connect to a DLNA server for quite a long time.

I used Synaptic (or apt-get) and installed MediaTomb, which is a UPnP (DLNA) server, but it didn't work as it was installed.  It would show thumbnails of my .jpg files, but it said "Unsupported File Type" or something when I tried to start a slideshow, so I did the following:  

1)  Enter mediatomb into a command line just so it creates a directory under my user ID.  Then I exited mediatomb and edited the ~/.mediatomb/config.xml file and made the following changes:

2)  Remove the comment tags <!-- and --> that were around the <custom-http-headers> section.

3)  Add the following two lines to the <custom-http-headers> section:

<add header="transferMode.dlna.org: Streaming"/>
<add header="contentFeatures.dlna.org: DLNA.ORG_OP=01;DLNA.ORG_CI=0;DLNA.ORG_FLAGS=01700000000000000000000000000000"/>

4)  Change <protocolInfo extend="yes"/> to say "yes"; it says "no" when it is installed.

That's it; when I started mediatomb by entering: mediatomb into a command line and then used Firefox to add some pictures and audio files to the mediatomb database, and finally used the TV remote control to go to MEDIA.P, up popped my pictures and .mp3 files.  Very neat - .jpg files look great on a 46 inch High-Def monitor, and it is very cool to add or remove files on my desktop and make them available or remove them from my TV set over my home network.

There is a good discussion at:  [http://forums.tversity.com/viewtopic.php?f=2&t=10992&st=0&sk=t&sd=a&start=45](http://forums.tversity.com/viewtopic.php?f=2&t=10992&st=0&sk=t&sd=a&start=45) - a tip o' the hat to "crappylogin" for providing the custom header lines that fixed the problem!

Sobrien - I have created an account on here for one thing. To say THANK YOU for posting this all those years ago!!  I have read several config guides on MediaTomb (and hundres more on DNLA generally) but it's through your post that I am watching media on my DNLA tv, streamed from my laptop via a wireless link.

You are wonderful!

Hooray!

(Can you tell it's taken me months?!)

Much love

GP  :popcorn:

---

### Post by thekat on 2010-02-28
I also wanted to say thank you..!!!

I just updated the firmware to 1017 and now
**I can pause / Stop / FF RW  !!! **

I have SAMSUNG LN40B650T1FXZA 
with firmware (2010/01/05_001017)
MediaTomb 0.12.0~svn2018-4ubuntu1

tk

---

### Post by thekat on 2010-03-27
> **thekat said:**
> I also wanted to say thank you..!!!

I just updated the firmware to 1017 and now
**I can pause / Stop / FF RW  !!! **

I have SAMSUNG LN40B650T1FXZA 
with firmware (2010/01/05_001017)
MediaTomb 0.12.0~svn2018-4ubuntu1

tk

Well not all shows have ff and rew but all do pause.

---

### Post by Feridun on 2010-03-31
> **Redsandro said:**
> I've got it working, too. Full .avi and .mkv support.


[s]I'd really like to know how to **get fast-forward and rewind to work**. It doesn't. It only does pause.[/s] The buttons on my remote were programmed incorrectly :tongue:



I belive I have the same problem with the fast-forward and rewind on my Samsung 7-series TV. I use mediatomb and it works great except for this part. How did you solve the problem?

//Feridun

---

### Post by p2ranger on 2010-04-10
I've followed this thread and appreciate the effort that has gone into it. Mediatomb is installed, but I don't understand how to get my TV to see it.  When I go to media share, it says there are no devices connected. The TV is connected to the network.

All the samsung instructions point towards using their windows software. I'm using the samsung pn50c590 tv. Any help would be great.

Thanks

Jason

---

### Post by p2ranger on 2010-04-13
I wound up installing minidlna and got that to work for me.

[http://sourceforge.net/projects/minidlna](http://sourceforge.net/projects/minidlna)
[http://www.audiodude.nl/?p=84](http://www.audiodude.nl/?p=84)

---

### Post by Cay on 2010-04-28
I run a recent subversion build of mediatomb (v0.12) together with a Samsung LE40B655T and had the regular pause, fast forward and rewind problems. None of the suggestions I read worked but:

I installed Samsung PC Share and WireShark on a Windows machine and tried sharing the same file there. I started the packet capture before selecting the media file on my tv and among all the other packets I found this:

```

HTTP/1.1 200 OK                                            
Server: Samsung HTTP streaming server    
Content-Type: video/x-avi                            
Content-Length: 364435456                    
Cache-Control: no-cache                            
contentFeatures.dlna.org:DLNA.ORG_OP=01;DLNA.ORG_CI=0;DLNA.ORG_FLAGS=01500000000000000000000000000000  
MediaInfo.sec: SEC_Duration=2555856;    

```



So I remapped avi to present itself as video/x-avi and changed the custom header to include this dlna.org_flags instead and now pause, ff and rewind works fine. 

Now if I can just limit transcoding to avi files with unsupported codecs and leave other avis alone all should be good.

Hope this can help someone else.

---

### Post by Sharft 6 on 2010-05-16
anybody else find that the audio and video doesn't sync up properly on some videos?

---

### Post by jonrasius on 2010-05-16
To me it does happen on some videos.

---

### Post by Sharft 6 on 2010-05-19
How do I organise my db so that I don't have to navigate down lots of levels in the file system?

This is what it currently takes to watch something
PC Directory -> media -> data -> me -> videos -> documentary -> choose a video

I want it to be something like this
videos -> documentary -> choose a video

---

### Post by Gonzo_Dark on 2010-05-24
This is a guide on how to get the "Media Play-function" working on a Samsung DLNA enabled TV. (tested on a UE46C6005RW)

First you need to download and install the mediatomb package from the Ubuntu software center or just use the terminal:
 
```
sudo apt-get install mediatomb
```
 
Then we need to edit the mediatomb config file, use the terminal and inset this code:
 
```
sudo gedit /etc/mediatomb/config.xml 
``` 
 
You need to delete the commend section arrows *<!-- and -->* thats around the *<custom-http-headers>* section, to reactivate *<custom-http-headers>*.
 
Inside the *<custom-http-headers>* you need to add the following lines:
 
```
<add header="transferMode.dlna.org: Streaming"/>
<add header="contentFeatures.dlna.org: DLNA.ORG_OP=01;DLNA.ORG_CI=0;DLNA.ORG_FLAGS=017000 00000000000000000000000000"/>
```
 
Then you need to change 

```
<protocolInfo extend="no"/>
```
 to 
```
<protocolInfo extend="yes"/>
```
(change no to yes - this will enable ps3 support)
 
And then you need to add the following under *<extension-mimetype>* to add avi/mkv-support;
 
```
<map from="avi" to="video/mpeg"/>
```

and then change
 
```
<map from="mkv" to="video/x-matroska"/>
```
to
```
<map from="mkv" to="video/mpeg"/>
```
 
Save and reboot the machine.

To open the program in your favorite browser you need to

[http://localhost:49152/](http://localhost:49152/)

Done

**KNOWN PROBLEMS**

The program SHOULD start with the computer BUT it is a know problem that mediatomb tries to connect to the internet before the network-manager is started, so it just closes again.

To check if your mediatomb server starts on boot, install this program;

```
sudo apt-get install upnp-inspector
```

you can find it under programs in the menu or run it in the terminal with; 

```
upnp-inspector
```

If you don't have a server running then you can start it with this command;

```
sudo /etc/init.d/mediatomb start
```

If you by mistake start two servers, then you can close them with; sudo killall mediatomb

Hope it helped, enjoy.

---

### Post by prince_niceguy on 2010-07-21
thanks folks, this made it working for my lnc630. I still cannot get ff/rewind to work... neither the mkv are getting listed in the list. any idea this can be played???

---

### Post by BridgeLife on 2010-08-03
Got Everything Working with UN55C8000, except Subtitles and Chapters...... Anyone get subs working on their Samsung TV?? Chapters are nice, but not my top priority, but I'm in dire need of Subtitle/SRT support, anyone get this working yet or have any ideas??

Thanks in Advance :-)

---

### Post by Reeman on 2010-10-07
> **dillzz said:**
> Sobrien,

Thank you for this information.  I can finally get Music + Pictures streamed to my TV.  I am however having problems with the video, i have tried endless encodings and no supported format :(.  It however works fine on the PS3 and their dlna implementation...Any ideas?
Try [Serviio]("http://www.serviio.org/") I have it serving mkv, m4v, dvd(VIDEO_TS), jpg, mp3 and aac to my Samsung series 5000 led. It works really well and just requires java6. You do not even have to install it. I just keep the java binary in a /home/eric/programs folder that I created and put startup launchers on my desktop. It can be tweaked to work with the console and can be set to several different dlna profiles like samsungs and ps3s.:popcorn:

Another non free software that seems to be coming along is [TVMOBili]("http://www.tvmobili.com/") which has a localhost:30888 browser interface. A .deb is available. It will be for a paid internet streaming services that will allow you to talk to other dlna devices remotely over the internet through their routing service. You can use their client for free for local network purposes though.

Because most dlna devices like Samsung tvs run some form of busybox Linux there is much that is starting to happen in the way of upnp dlna releases that have native linux clients. Unfortunately Samsung itself only releases a Windows only server...which doesn't work under wine and doesn't even work very well under Windows! Go figure.

---

### Post by insane2600tt on 2010-10-14
Serviio is just GREAT! if finally got rid of that flaky mediatomb! 

and now...:popcorn::popcorn::popcorn:

---

### Post by mchristian on 2010-11-07
> **insane2600tt said:**
> Serviio is just GREAT! if finally got rid of that flaky mediatomb! 

and now...:popcorn::popcorn::popcorn:



I just had the same exact experience, after trying and trying to get mediatomb to work.  then to have Serviio to work so simply, this is how it should be when people start to brag about their new amazing software items.  This is absolutely great.  If you have tried others, please save yourself the headache and try Serviio.

---

### Post by mchristian on 2010-11-08
Has anyone gotten Serviio to run at boot up and be seen by Sony Blu Ray S570 without having to click on any other keyboard items?
 
Edit:
 
I simply added it to the start applications menu.  Works fine without actually doing anything that starting the computer.  Duh!

---

### Post by el.maquis on 2010-11-14
> **Gonzo_Dark said:**
> This is a guide on how to get the "Media Play-function" working on a Samsung DLNA enabled TV. (tested on a UE46C6005RW)

First you need to download and install the mediatomb package from the Ubuntu software center or just use the terminal:
 
```
sudo apt-get install mediatomb
```Then we need to edit the mediatomb config file, use the terminal and inset this code:
 
```
sudo gedit /etc/mediatomb/config.xml 
```You need to delete the commend section arrows *<!-- and -->* thats around the *<custom-http-headers>* section, to reactivate *<custom-http-headers>*.
 
Inside the *<custom-http-headers>* you need to add the following lines:
 
```
<add header="transferMode.dlna.org: Streaming"/>
<add header="contentFeatures.dlna.org: DLNA.ORG_OP=01;DLNA.ORG_CI=0;DLNA.ORG_FLAGS=017000 00000000000000000000000000"/>
```Then you need to change 

```
<protocolInfo extend="no"/>
``` to 
```
<protocolInfo extend="yes"/>
```(change no to yes - this will enable ps3 support)
 
And then you need to add the following under *<extension-mimetype>* to add avi/mkv-support;
 
```
<map from="avi" to="video/mpeg"/>
```and then change
 
```
<map from="mkv" to="video/x-matroska"/>
```to
```
<map from="mkv" to="video/mpeg"/>
```Save and reboot the machine.

To open the program in your favorite browser you need to

[http://localhost:49152/](http://localhost:49152/)

Done

**KNOWN PROBLEMS**

The program SHOULD start with the computer BUT it is a know problem that mediatomb tries to connect to the internet before the network-manager is started, so it just closes again.

To check if your mediatomb server starts on boot, install this program;

```
sudo apt-get install upnp-inspector
```you can find it under programs in the menu or run it in the terminal with; 

```
upnp-inspector
```If you don't have a server running then you can start it with this command;

```
sudo /etc/init.d/mediatomb start
```If you by mistake start two servers, then you can close them with; sudo killall mediatomb

Hope it helped, enjoy.


It works great for me (LE32B651)! The only difference is that I've used:
 <map from="avi" to="video/x-avi"/>
I don't know if it matters.

---

### Post by damvcoool on 2010-11-25
> **Sharft 6 said:**
> How do I organise my db so that I don't have to navigate down lots of levels in the file system?

This is what it currently takes to watch something
PC Directory -> media -> data -> me -> videos -> documentary -> choose a video

I want it to be something like this
videos -> documentary -> choose a video

make a system link on the root of your filesystem to videos, and include that link on MediaTomb database.

Or use MiniDLNA.
[https://launchpad.net/~stedy6/+archive/stedy-minidna](https://launchpad.net/~stedy6/+archive/stedy-minidna)

Also you can find better luck with Rygel (included on Ubuntu 10.10)

---

### Post by yellowrubiu on 2011-01-04
Hello, first post from a total noob here so bare with me please.

I've setup an old laptop with a couple of external drives to store my photos and videos and been trying to set it up as a MediaTomb DLNA server. So far I've been able to get my Samsung UN55B8500 TV to see the MediaTomb server and can see pictures after following the edits to the config.xml file outlined in this thread.

However, I'm having a couple of problems with videos.

1) The first is that I can not get audio for the AVI files. I get a message telling me "Not Supported Audio Data."

2) The second problem is that I can not play quicktime .MOV videos. I keep getting a message saying "Not Supported File Format."

I haven't tried to solve the first problem yet but I've been spending a lot of time searching and trying to find a fix for the problem with the quicktime video. I have updated the config.xml as follows based on some of the information I've found through googling:

This is what I've done so far...

- added this [COLOR=Navy]<map from="mov" to="video/quicktime"/>[/COLOR] to the [COLOR=Navy]<mappings>[/COLOR] section
- added this [COLOR=Navy]<treat mimetype="video/quicktime" as="mov"/>[/COLOR] to the [COLOR=Navy]<mimetype-contenttype>[/COLOR] section
- added this [COLOR=Navy]<transcode mimetype="video/quicktime" using="transvideo"/>[/COLOR] to the [COLOR=Navy]<mimetype-profile-mappings>[/COLOR] section
- added this to the [COLOR=Navy]<profiles>[/COLOR] section:[INDENT][COLOR=Navy]<profiles>
      <profile name="transvideo" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <agent command="ffmpegvideo" arguments="%in %out 8300k 256k"/>
        <buffer size="57600000" chunk-size="128000" fill-size="10000000"/>
      </profile>[/COLOR]
[/INDENT]However after doing the above changes and trying to restart the server it does not start. I get a [COLOR=Navy]"fail!"[/COLOR] message.

Does anyone have a any suggestions or links that can help me resolve this? Is there any additional software needed on the Ubuntu machine besides the packages that get installed when MediTub is installed? Thanks in advance for any help you can offer.

---

### Post by prince_niceguy on 2011-01-04
> **yellowrubiu said:**
> Hello, first post from a total noob here so bare with me please.

I've setup an old laptop with a couple of external drives to store my photos and videos and been trying to set it up as a MediaTomb DLNA server. So far I've been able to get my Samsung UN55B8500 TV to see the MediaTomb server and can see pictures after following the edits to the config.xml file outlined in this thread.

However, I'm having a couple of problems with videos.

1) The first is that I can not get audio for the AVI files. I get a message telling me "Not Supported Audio Data."

2) The second problem is that I can not play quicktime .MOV videos. I keep getting a message saying "Not Supported File Format."

I haven't tried to solve the first problem yet but I've been spending a lot of time searching and trying to find a fix for the problem with the quicktime video. I have updated the config.xml as follows based on some of the information I've found through googling:

This is what I've done so far...

- added this [COLOR=Navy]<map from="mov" to="video/quicktime"/>[/COLOR] to the [COLOR=Navy]<mappings>[/COLOR] section
- added this [COLOR=Navy]<treat mimetype="video/quicktime" as="mov"/>[/COLOR] to the [COLOR=Navy]<mimetype-contenttype>[/COLOR] section
- added this [COLOR=Navy]<transcode mimetype="video/quicktime" using="transvideo"/>[/COLOR] to the [COLOR=Navy]<mimetype-profile-mappings>[/COLOR] section
- added this to the [COLOR=Navy]<profiles>[/COLOR] section:[INDENT][COLOR=Navy]<profiles>
      <profile name="transvideo" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <agent command="ffmpegvideo" arguments="%in %out 8300k 256k"/>
        <buffer size="57600000" chunk-size="128000" fill-size="10000000"/>
      </profile>[/COLOR]
[/INDENT]However after doing the above changes and trying to restart the server it does not start. I get a [COLOR=Navy]"fail!"[/COLOR] message.

Does anyone have a any suggestions or links that can help me resolve this? Is there any additional software needed on the Ubuntu machine besides the packages that get installed when MediTub is installed? Thanks in advance for any help you can offer.

User serviio instead of mediatomb. Much easier and better to compatibility with samsung tv I believe.

---

### Post by yellowrubiu on 2011-01-04
> **prince_niceguy said:**
> User serviio instead of mediatomb. Much easier and better to compatibility with samsung tv I believe.

Thanks for the suggestion. I installed Serviio and can now see the quicktime files, which is awesome, but I am still having the same problem I was having with MediaTomb with the "Not Supported Audio Data" message for the AVI files. Any suggestions?

Thanks!

---

### Post by ginobe on 2011-01-08
> **Gonzo_Dark said:**
> This is a guide on how to get the "Media Play-function" working on a Samsung DLNA enabled TV. (tested on a UE46C6005RW)

First you need to download and install the mediatomb package from the Ubuntu software center or just use the terminal:
 
```
sudo apt-get install mediatomb
```
 
Then we need to edit the mediatomb config file, use the terminal and inset this code:
 
```
sudo gedit /etc/mediatomb/config.xml 
``` 
 
You need to delete the commend section arrows *<!-- and -->* thats around the *<custom-http-headers>* section, to reactivate *<custom-http-headers>*.
 
Inside the *<custom-http-headers>* you need to add the following lines:
 
```
<add header="transferMode.dlna.org: Streaming"/>
<add header="contentFeatures.dlna.org: DLNA.ORG_OP=01;DLNA.ORG_CI=0;DLNA.ORG_FLAGS=017000 00000000000000000000000000"/>
```
 
Then you need to change 

```
<protocolInfo extend="no"/>
```
 to 
```
<protocolInfo extend="yes"/>
```
(change no to yes - this will enable ps3 support)
 
And then you need to add the following under *<extension-mimetype>* to add avi/mkv-support;
 
```
<map from="avi" to="video/mpeg"/>
```

and then change
 
```
<map from="mkv" to="video/x-matroska"/>
```
to
```
<map from="mkv" to="video/mpeg"/>
```
 
Save and reboot the machine.

To open the program in your favorite browser you need to

[http://localhost:49152/](http://localhost:49152/)

Done

**KNOWN PROBLEMS**

The program SHOULD start with the computer BUT it is a know problem that mediatomb tries to connect to the internet before the network-manager is started, so it just closes again.

To check if your mediatomb server starts on boot, install this program;

```
sudo apt-get install upnp-inspector
```

you can find it under programs in the menu or run it in the terminal with; 

```
upnp-inspector
```

If you don't have a server running then you can start it with this command;

```
sudo /etc/init.d/mediatomb start
```

If you by mistake start two servers, then you can close them with; sudo killall mediatomb

Hope it helped, enjoy.

ok ok i did just this and my samsung tv says format not supported for avi video files. please help!!!!!

---

### Post by minisori on 2011-01-19
> **ginobe said:**
> ok ok i did just this and my samsung tv says format not supported for avi video files. please help!!!!!

On my UE32C5100 tv with latest firmware (1023), and taking a look to Samsung Pc Manager packages sent by the network i saw it was using video/x-msvideo for avi files, but i must say it was working with whatever, even default mediatomb file. So try this instead:

<map from="avi" to="video/x-msvideo"/>

Another thing, for those interested, there is a working patch on mediatomb's sourceforge tracker to allow subtitles on samsung tv's without need of transcoding.

---

### Post by Fraoch on 2011-02-02
Another vote for Serviio.  It's just been updated to 0.5 which supports multiple profiles for multiple devices as well as hiding default menu items (grouping videos by "actor" for example).

Works fine with both my Samsung LN46C630 and my WD TV Live.

Audio transcoding is coming soon for those with music collections other than all MP3 (or PCM??)

---

### Post by samsung_DLNA on 2011-02-20
> **Redsandro said:**
> I've got it working, too. Full .avi and .mkv support.

**Except for some important stuff.**

[s]I'd really like to know how to **get fast-forward and rewind to work**. It doesn't. It only does pause.[/s] The buttons on my remote were programmed incorrectly :tongue:

Also, Samsung **does not play DTS audio**. Does anyone know how to transcode just DTS audio? My server is not strong enough to transcode HD video too. The video is not the problem anyway. ;)

When I play back a DTS containing MKV on the tv, it plays without audio. I tried adding the profile
```
      <profile name="vid-dts" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="ffmpeg" arguments="-y -threads 2 -i %in -acodec ac3 -ab 192000 -vcodec copy -f matroska %out"/>
        <buffer size="14400000" chunk-size="512000" fill-size="120000"/>
      </profile>
```But now the entire file will not play anymore.

[s]Finally, is there a way to **change the audio stream**? It always plays the first one, and that is usually not the English one.[/s] MediaTomb handles this fine. It's the television that might not. I can choose the audiostream just fine in XBMC. Subtitles also. :D

So anyone with the knowledge, please help! :)



Hi!
I have no problem with pause, rewind, fast forward or anything like that. My samsung 7-series tv plays just about everything I've tested so far over dlna EXCEPT for one anoying thing: DTS audio. Just about every .mkv file I've encountered has the audio encoded in dts. Is there anyone out there who has got a working method to transcode just the audio part of a .mkv-file on the fly?

I tried: 
    <profile name="dts_to_ac3" enabled="no" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <hide-original-resource>no</hide-original-resource>
        <agent command="ffmpeg" arguments="-i %in -vcodec copy -scodec copy  -acodec ac3 -ac 2 -ab 128000 %out"/>
        <buffer size="14400000" chunk-size="512000" fill-size="120000"/>
    </profile>

But that just make my tv show a "Unsupported file format" message when I try to play a .mkv-file. The arguments work fine if I convert one file to another file and skip the %in/%out buffers. In fact everything I try to transcode makes my tv show the same message (I tried to use the "vlcmpeg" profile that came with the installation of mediatomb).

A solution anyone?

---

### Post by mfdc1969 on 2011-03-04
I just bought a Series 6 Samsung LN46C610 LCD 2 weeks ago and can not get any files to play/view on the TV using Mediatomb.

I have followed all the suggestions, changes to config file and the TV seems to be able to view all folders, it sees the video files and JPGs but will not open/play. It says file format unsupported.

My computer and TV are wired using a LINKSYS 5-port switch and DLINK WBR-2310 router, ports opened in router: 1900 (any) 49152 (any).

If I take those same files and put them on a USB stick and plug it into the side of the TV they display/play perfectly.

I have used the CLI to invoke mediatomb and a few XML parsing errors have shown up. I may have done more damage than good but I removed a few comments and the config file seems to be close to what others have shown in their posts. (I know nothing of XML)

... any suggestions?

Here is my config file:

```
<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <!--
     Read /usr/share/doc/mediatomb-common/README.gz section 6 for more
     information on creating and using config.xml configration files.
    -->
  <server>
    <ui enabled="yes" show-tooltips="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:b4b208e6-def9-4250-8c06-b36d839dff7a</udn>
    <home>/home/michael/.mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage>
      <sqlite3 enabled="yes">
        <database-file>mediatomb.db</database-file>
      </sqlite3>
      <mysql enabled="no">
        <host>localhost</host>
        <username>mediatomb</username>
        <database>mediatomb</database>
      </mysql>
    </storage>
    <protocolInfo extend="yes"/><!-- For PS3 support change to "yes" -->
    <!--
       Uncomment the lines below to get rid of jerky avi playback on the
       DSM320 or to enable subtitles support on the DSM units
    -->
    <custom-http-headers>
	<add header="transferMode.dlna.org: Streaming"/>
	<add header="contentFeatures.dlna.org: DLNA.ORG_OP=01;DLNA.ORG_CI=0;DLNA.ORG_FLAGS=017000 00000000000000000000000000"/>
    <!-- Uncomment the line below if you have a Telegent TG100 -->
       <upnp-string-limit>101</upnp-string-limit>
    <extended-runtime-options>
      <ffmpegthumbnailer enabled="no">
        <thumbnail-size>128</thumbnail-size>
        <seek-percentage>5</seek-percentage>
        <filmstrip-overlay>yes</filmstrip-overlay>
        <workaround-bugs>no</workaround-bugs>
      </ffmpegthumbnailer>
      <mark-played-items enabled="no" suppress-cds-updates="yes">
        <string mode="prepend">*</string>
      </mark-played-items>
    </extended-runtime-options>
  </server>
  <import hidden-files="no">
    <scripting script-charset="UTF-8">
      <virtual-layout type="builtin"/>
    </scripting>
    <mappings>
      <extension-mimetype ignore-unknown="no">
	<map from="avi" to="video/mpeg"/>        
	<map from="mp3" to="audio/mpeg"/>
        <map from="ogg" to="application/ogg"/>
        <map from="asf" to="video/x-ms-asf"/>
        <map from="asx" to="video/x-ms-asf"/>
        <map from="wma" to="audio/x-ms-wma"/>
        <map from="wax" to="audio/x-ms-wax"/>
        <map from="wmv" to="video/x-ms-wmv"/>
        <map from="wvx" to="video/x-ms-wvx"/>
        <map from="wm" to="video/x-ms-wm"/>
        <map from="wmx" to="video/x-ms-wmx"/>
        <map from="m3u" to="audio/x-mpegurl"/>
        <map from="pls" to="audio/x-scpls"/>
        <map from="flv" to="video/x-flv"/>
        <map from="mkv" to="video/mpeg"/>
        <map from="mka" to="audio/x-matroska"/>
	<map from="avi" to="video/divx"/>
	<map from="avi" to="video/avi"/>
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
        <map from="application/ogg" to="object.item.audioItem.musicTrack"/>
      </mimetype-upnpclass>
      <mimetype-contenttype>
        <treat mimetype="audio/mpeg" as="mp3"/>
        <treat mimetype="application/ogg" as="ogg"/>
        <treat mimetype="audio/x-flac" as="flac"/>
        <treat mimetype="image/jpeg" as="jpg"/>
        <treat mimetype="audio/x-mpegurl" as="playlist"/>
        <treat mimetype="audio/x-scpls" as="playlist"/>
        <treat mimetype="audio/x-wav" as="pcm"/>
        <treat mimetype="audio/L16" as="pcm"/>
        <treat mimetype="video/x-msvideo" as="avi"/>
        <treat mimetype="video/mp4" as="mp4"/>
        <treat mimetype="audio/mp4" as="mp4"/>
        <treat mimetype="application/x-iso9660" as="dvd"/>
        <treat mimetype="application/x-iso9660-image" as="dvd"/>
        <treat mimetype="video/x-matroska" as="mkv"/>
        <treat mimetype="audio/x-matroska" as="mka"/>
      </mimetype-contenttype>
    </mappings>
    <online-content>
      <YouTube enabled="no" refresh="28800" update-at-start="no" purge-after="604800" racy-content="exclude" format="flv" hd="no">
        <favorites user="mediatomb"/>
        <standardfeed feed="most_viewed" time-range="today"/>
        <playlists user="mediatomb"/>
        <uploads user="mediatomb"/>
        <standardfeed feed="recently_featured" time-range="today"/>
      </YouTube>
      <Weborama enabled="no" refresh="28800" update-at-start="no">
        <playlist name="Active" type="playlist" mood="active"/>
        <playlist name="Metal" type="playlist">
          <filter>
            <genres>metal</genres>
          </filter>
        </playlist>
      </Weborama>
      <AppleTrailers enabled="no" refresh="43200" update-at-start="no" resolution="640"/>
    </online-content>
  </import>
  <transcoding enabled="no">
    <mimetype-profile-mappings>
      <transcode mimetype="video/x-flv" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="oggflac2raw"/>
      <transcode mimetype="audio/x-flac" using="oggflac2raw"/>
    </mimetype-profile-mappings>
    <profiles>
      <profile name="oggflac2raw" enabled="no" type="external">
        <mimetype>audio/L16</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>no</accept-ogg-theora>
        <agent command="ogg123" arguments="-d raw -o byteorder:big -f %out %in"/>
        <buffer size="1048576" chunk-size="131072" fill-size="262144"/>
      </profile>
      <profile name="vlcmpeg" enabled="no" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="vlc" arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>
        <buffer size="14400000" chunk-size="512000" fill-size="120000"/>
      </profile>
    </profiles>
  </transcoding>
</config>
```

Here is an sample of my mediatomb log file:

```
2011-03-05 11:38:28    INFO: Loading configuration from: /etc/mediatomb/config.xml
2011-03-05 11:38:29    INFO: Checking configuration...
2011-03-05 11:38:29    INFO: Setting filesystem import charset to ANSI_X3.4-1968
2011-03-05 11:38:29    INFO: Setting metadata import charset to ANSI_X3.4-1968
2011-03-05 11:38:29    INFO: Setting playlist charset to ANSI_X3.4-1968
2011-03-05 11:38:29    INFO: Configuration check succeeded.
2011-03-05 11:38:29    INFO: Initialized port: 49152
2011-03-05 11:38:29    INFO: Server bound to: 192.168.0.100
2011-03-05 11:38:30    INFO: MediaTomb Web UI can be reached by following this link:
2011-03-05 11:38:30    INFO: http://192.168.0.100:49152/
2011-03-05 12:10:36   ERROR: ActionRequest::update(): response is nil, code -115
2011-03-05 12:10:36   ERROR: ActionRequest::update(): response is nil, code -115
```

Note: code 115 repeats multiple times ...

---

### Post by mfdc1969 on 2011-03-22
My troubles have been solved with help from Sourceforge Forums and [mediatomb forums which can be viewed here]("https://sourceforge.net/projects/mediatomb/forums/forum/440751/topic/4398387/index/page/1").

Interesting to note in addition to really messing up my config file which was in the wrong location, I had to remove the .mediatomb directory in my home folder.

All is well now and working.

---

### Post by jap1968 on 2011-04-03
Not sure if this is a bit off topic: I have setup a [miniDLNA server on Linux]("http://netpatia.blogspot.com/2011/03/setup-your-own-dlna-server.html") (CentOS, but in Ubuntu it should be even easier) and tested with a Samsung series 6 LED with excellent results. :P

I consider it worths a reading, in particular for those suffering firewall related issues.

---

### Post by andka on 2011-05-09
Here is some more info for those of you who, like me, have had problems making seeking (ff, rev) work with a Samsung TV.

I just discovered that seeking works for me, and possibly has worked all the time. It is just that I should not use the "<<" and ">>" buttons at the bottom of the remote control, I should use the "<" and ">" buttons which are part of the "cross" in the middle of the remote control.

/Andreas

---

### Post by gilsonsjc on 2011-07-12
> **ydo said:**
> Installing SamyGO which can mount samba, nfs and upnp/dlna as virtual usb drives gives access to these features which are disabled over normal dlna. 
AND it is way cool to be able to ssh the TV ;-)

Would you tell me how you were able to map the samba drivers on your TV? I installed the SamyGo and wrote the run.sh script but I have these errors:

run.sh
```

#!/bin/sh
touch $1/ScriptOK
sync
rm -f /mtd_rwarea/profile
$1/SamyGO/rcSGO $1/SamyGO > $1/rcSGO_out 2>&1 &

insmod /dtv/usb/sda1/SamyGO/lib/modules/2.6.24_SELP.4.3.x-Cortex-A8/kernel/fs/cifs/cifs.ko
sleep 10; mount -t cifs -o -o guest //192.168.1.2/Public /dtv/usb/sda1/samba/
sleep 10; mount -t cifs -o -o guest //192.168.1.2/Public/Shared\ Videos /dtv/usb/sda1/shares/Videos

```

rcSGO_out
```
+ /dtv/usb/sda1/SamyGO/rcSGO /dtv/usb/sda1/SamyGO
./etc/rc.sysinit: line 94: /dtv/usb/sda1/SamyGO/opt/privateer/sbin/depmod: not found
insmod /dtv/usb/sda1/SamyGO/lib/modules/*.ko, this behavior is outdated modules are handled by the init scripts!
Replace /dtv/usb/sda1/SamyGO/lib/modules/treasure/*.ko
insmod: can't open '/dtv/usb/sda1/SamyGO/lib/modules/2.6.24_SELP.4.3.x-Cortex-A8/kernel/drivers/video/cfbcopyarea.ko': No such file or directory
insmod: can't open '/dtv/usb/sda1/SamyGO/lib/modules/2.6.24_SELP.4.3.x-Cortex-A8/kernel/drivers/video/cfbfillrect.ko': No such file or directory
insmod: can't open '/dtv/usb/sda1/SamyGO/lib/modules/2.6.24_SELP.4.3.x-Cortex-A8/kernel/drivers/video/cfbimgblt.ko': No such file or directory
insmod: can't open '/dtv/usb/sda1/SamyGO/lib/modules/2.6.24_SELP.4.3.x-Cortex-A8/kernel/drivers/usb/input/usbhid.ko': No such file or directory
mkfs.vfat 2.11 (12 Mar 2005)
real storage device at: /sys/block/sda/device/model
found gadget at: /sys/block/sdb/device/model
scsidev: sdb
fuse 30900 0 - Live 0xbf736000
insmod: can't open '/dtv/usb/sda1/SamyGO/lib/modules/2.6.24_SELP.4.3.x-Cortex-A8/kernel/net/sunrpc/sunrpc.ko': No such file or directory
insmod: can't open '/dtv/usb/sda1/SamyGO/lib/modules/2.6.24_SELP.4.3.x-Cortex-A8/kernel/fs/lockd/lockd.ko': No such file or directory
insmod: can't open '/dtv/usb/sda1/SamyGO/lib/modules/2.6.24_SELP.4.3.x-Cortex-A8/kernel/fs/nfs_common/nfs_acl.ko': No such file or directory
insmod: can't open '/dtv/usb/sda1/SamyGO/lib/modules/2.6.24_SELP.4.3.x-Cortex-A8/kernel/fs/nfs/nfs.ko': No such file or directory
Search Shares on: 192.168.1.100
192.168.1.2
portmap getport: RPC: Success
which: no hid2hci in (/dtv/usb/sda1/SamyGO/opt/privateer/sbin:/dtv/usb/sda1/SamyGO/opt/privateer/bin:/dtv/usb/sda1/SamyGO/opt/privateer/usr/bin:/dtv/usb/sda1/SamyGO/opt/privateer/usr/sbin:/dtv/usb/sda1/SamyGO/sbin:/dtv/usb/sda1/SamyGO/bin:/dtv/usb/sda1/SamyGO/usr/bin:/dtv/usb/sda1/SamyGO/usr/sbin:/sbin:/bin:/usr/sbin:/usr/bin)
Starting Bluetooth subsystem: hcidCan't get device info: No such device
 sdpd hidd.
recorder share not mounted!

```

---

### Post by mac-duff on 2011-08-08
Hi,

of corse I also have a problem with mediatomb. I can play a lot of Divx/Xvid movies but for example the current Breaking Bad episodes doesnt work. The file information which I get from VLC are:
Stream 0
  Type: Video
  Codec: XVID
  Resolution: 624x352
  Display resolution: 624x352
  Frame rate: 23.976024
Stream 1
  Type: Audio
  Codec: mpga
  Channels: Stero
  Sample rate: 48000 Hz
  Bitrate: 128kb/s

and my config is:
```

<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <!--
     Read /usr/share/doc/mediatomb-common/README.gz section 6 for more
     information on creating and using config.xml configration files.
    -->
  <server>
    <ui enabled="yes" show-tooltips="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:d047eba2-a9e7-40c2-bb7a-e69f72f7bdf7</udn>
    <home>/home/stephan/.mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage>
      <sqlite3 enabled="yes">
        <database-file>mediatomb.db</database-file>
      </sqlite3>
      <mysql enabled="no">
        <host>localhost</host>
        <username>mediatomb</username>
        <database>mediatomb</database>
      </mysql>
    </storage>
    <protocolInfo extend="yes"/><!-- For PS3 support change to "yes" -->
    <!--
       Uncomment the lines below to get rid of jerky avi playback on the
       DSM320 or to enable subtitles support on the DSM units
    -->
    
    <custom-http-headers>
      <add header="X-User-Agent: redsonic"/>
      <add header="transferMode.dlna.org: Streaming"/>
      <add header="contentFeatures.dlna.org: DLNA.ORG_OP=01;DLNA.ORG_CI=0;DLNA.ORG_FLAGS=017000 00000000000000000000000000"/>
    </custom-http-headers>

    <manufacturerURL>redsonic.com</manufacturerURL>
    <modelNumber>105</modelNumber>
   
    <!-- Uncomment the line below if you have a Telegent TG100 -->
    <!--
       <upnp-string-limit>101</upnp-string-limit>
     -->
    <extended-runtime-options>
      <ffmpegthumbnailer enabled="no">
        <thumbnail-size>128</thumbnail-size>
        <seek-percentage>5</seek-percentage>
        <filmstrip-overlay>yes</filmstrip-overlay>
        <workaround-bugs>no</workaround-bugs>
      </ffmpegthumbnailer>
      <mark-played-items enabled="no" suppress-cds-updates="yes">
        <string mode="prepend">*</string>
      </mark-played-items>
    </extended-runtime-options>
  </server>
  <import hidden-files="no">
    <scripting script-charset="UTF-8">
      <virtual-layout type="builtin"/>
    </scripting>
    <autoscan use-inotify="auto">
        <directory location="/media" mode="timed" interval="3600"
                level="full" recursive="yes" hidden-files="no"/>
        <directory location="/home/stephan/Downloads/" mode="inotify"
                recursive="yes" hidden-files="no"/>
    </autoscan>
    <mappings>
      <extension-mimetype ignore-unknown="no">
	<map from="avi" to="video/divx"/>
        <map from="mp3" to="audio/mpeg"/>
        <map from="ogg" to="application/ogg"/>
        <map from="asf" to="video/x-ms-asf"/>
        <map from="asx" to="video/x-ms-asf"/>
        <map from="wma" to="audio/x-ms-wma"/>
        <map from="wax" to="audio/x-ms-wax"/>
        <map from="wmv" to="video/x-ms-wmv"/>
        <map from="wvx" to="video/x-ms-wvx"/>
        <map from="wm" to="video/x-ms-wm"/>
        <map from="wmx" to="video/x-ms-wmx"/>
        <map from="m3u" to="audio/x-mpegurl"/>
        <map from="pls" to="audio/x-scpls"/>
        <map from="flv" to="video/x-flv"/>
        <map from="mkv" to="video/mpeg"/>
        <map from="mka" to="audio/x-matroska"/>
	<map from="rmvb" to="application/vnd.rn-realmedia"/>
        <!-- Uncomment the line below for PS3 divx support -->
       <!-- <map from="avi" to="video/divx"/> -->
        <!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 -->
        <!-- <map from="avi" to="video/avi"/> -->
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
        <map from="application/ogg" to="object.item.audioItem.musicTrack"/>
      </mimetype-upnpclass>
      <mimetype-contenttype>
        <treat mimetype="audio/mpeg" as="mp3"/>
        <treat mimetype="application/ogg" as="ogg"/>
        <treat mimetype="audio/x-flac" as="flac"/>
        <treat mimetype="image/jpeg" as="jpg"/>
        <treat mimetype="audio/x-mpegurl" as="playlist"/>
        <treat mimetype="audio/x-scpls" as="playlist"/>
        <treat mimetype="audio/x-wav" as="pcm"/>
        <treat mimetype="audio/L16" as="pcm"/>
        <treat mimetype="video/x-msvideo" as="avi"/>
        <treat mimetype="video/mp4" as="mp4"/>
        <treat mimetype="audio/mp4" as="mp4"/>
        <treat mimetype="application/x-iso9660" as="dvd"/>
        <treat mimetype="application/x-iso9660-image" as="dvd"/>
        <treat mimetype="video/x-matroska" as="mkv"/>
        <treat mimetype="audio/x-matroska" as="mka"/>
	<treat mimetype="application/vnd.rn-realmedia" as="rmvb"/>
	<treat mimetype="application/vnd" as="rmvb"/>
      </mimetype-contenttype>
    </mappings>
    <online-content>
      <!-- Make sure to setup a transcoding profile for flv -->
      <YouTube enabled="no" refresh="28800" update-at-start="no" purge-after="604800" racy-content="exclude" format="flv" hd="no">
        <favorites user="mediatomb"/>
        <standardfeed feed="most_viewed" time-range="today"/>
        <playlists user="mediatomb"/>
        <uploads user="mediatomb"/>
        <standardfeed feed="recently_featured" time-range="today"/>
      </YouTube>
      <Weborama enabled="no" refresh="28800" update-at-start="no">
        <playlist name="Active" type="playlist" mood="active"/>
        <playlist name="Metal" type="playlist">
          <filter>
            <genres>metal</genres>
          </filter>
        </playlist>
      </Weborama>
      <AppleTrailers enabled="no" refresh="43200" update-at-start="no" resolution="640"/>
    </online-content>
  </import>
  <transcoding enabled="no">
    <mimetype-profile-mappings>
      <transcode mimetype="video/x-flv" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="oggflac2raw"/>
      <transcode mimetype="audio/x-flac" using="oggflac2raw"/>
    </mimetype-profile-mappings>
    <profiles>
      <profile name="oggflac2raw" enabled="no" type="external">
        <mimetype>audio/L16</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>no</accept-ogg-theora>
        <agent command="ogg123" arguments="-d raw -o byteorder:big -f %out %in"/>
        <buffer size="1048576" chunk-size="131072" fill-size="262144"/>
      </profile>
      <profile name="vlcmpeg" enabled="no" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="vlc" arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>
        <buffer size="14400000" chunk-size="512000" fill-size="120000"/>
      </profile>
    </profiles>
  </transcoding>
</config>

```

As anyone a idea whats the problem? Maybe it is the sound.. ?

Thx
Stephan

---

### Post by JonathonO on 2011-09-18
Hi,

Just wanted to add that while I was unable to use the FF/REW buttons on the remote, the directional pad allows me to jump ahead or back a few seconds. I had it all working except this and was trying to figure out why I was getting the "Not Available" response from the Samsung TV when I hit FF/REW (pause, stop, and play worked). Didn't see it posted anywhere to try the alternate keys on the TV remote.

Fixing the headers, video mappings, and updating the firmware got it all working with my Samsung PN51D550.

---

### Post by elcamilo on 2012-02-17
Hey, I found this PPA for serviio, but it's compiled with wrong dependencies (and it's also an obsolete version):

[https://launchpad.net/~traxanos/+archive/ppa](https://launchpad.net/~traxanos/+archive/ppa)

damn!

---

### Post by Steve1961 on 2012-05-07
For those who might be interested, I've just set up miniDLNA to work with a Samsung smart PVR.  Seems to work flawlessly so far.  Just followed these instructions:

[http://linuxforums.org.uk/index.php?topic=9822.msg70397;PHPSESSID=7jv96fj1mh3p00p62cv44akhq3#msg70397](http://linuxforums.org.uk/index.php?topic=9822.msg70397;PHPSESSID=7jv96fj1mh3p00p62cv44akhq3#msg70397)

---

### Post by hop5uk on 2012-05-27
I have been trying to get mediatomb working on my Samsung UN55D8000.
From the original config file i edited the custom-header section to read
 
<add header="transferMode.dlna.org: Streaming"/><add header="contentFeatures.dlna.org: DLNA.ORG_OP=01;DLNA.ORG_CI=0;DLNA.ORG_FLAGS=01500000000000000000000000000000"/> Once i have done this ,AVI files play, but mkv files display the unsupported file format message. I have tried a few different changes to the file to fix this but have no luck in getting it to work.I have been reading in forums that mediatomb is dead and should be abandoned for something else.What is peoples opinion on this. I tried Serviio as well but can't get it to run.

---

