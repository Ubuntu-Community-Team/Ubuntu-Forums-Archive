---
title: "Upnp for xbox 360"
date: 2006-11-08
forum: Multimedia &amp; Video
---

### Post by chedabob on 2006-11-08
Has anybody succesfully got a media server running that can be recognised by xbox 360? I tried uShare but it crashed whilst reading the folder

---

### Post by dpw2atox on 2006-11-08
no luck here, i am not even aware of what applications will work to offer this ability.

---

### Post by uglysmurf on 2007-01-09
try: [360 Media Server]("http://sourceforge.net/projects/x360mediaserve/")...worked like a charm for me

---

### Post by sshetye on 2007-03-30
360 media server cannot transcode video. I've recently ditched Windows Media Center for Ubuntu. Is there really no Linux uPnP media transcoding server which can transcode and stream xvid,divx / ac3 in a manner the XBOX 360 can pick up?

I really wish there is some open source project out there aiming for this ... I've come too far to go back to Window Media Center or dual boot. I'm not sure VMWare can give the performance I'd need.

Damn ... maybe a Vista Ultimate license is needed. Just what I was trying to stay away from !!

---

### Post by TheKnudson on 2007-05-02
I know about [fuppes]("http://fuppes.ulrich-voelkel.de/index.php?page=features") being able to transcode music (flac ogg -> mp3). No video transcoding whatsoever.

---

### Post by noble on 2007-05-24
hi

since the new spring update offered more supported video formats to transcode - I wanna ask if there is any software whicht allows me to set up my linux box to stream to my xbox360

found twonkyvision whicht supports xbox360 but didn't test the trial to know how well it works.

so is there a way to stream - there are programms like tversity for windows and xbox360 connect for mac os x they work like a sharm but what about linux ?

---

### Post by mozetti on 2007-05-24
As far as I can tell, there isn't a native linux app for this. You might be able to run TVersity in a Windows-Virtual-Machine, but I haven't tried it. My wife's laptop dual-boot's Windows & Ubuntu, so I just leave it running Windows most of the time and run Tversity on it.

I think it has something to do with the ability to transcode the audio track of the video file, which is WMA.

---

### Post by noble on 2007-05-24
hmm, but since the new spring update there are also other video formats supported - so its not necessary to transcode into wmv to get the videos playing on the 360 console.

---

### Post by tgm4883 on 2007-05-24
Try twonkymedia.  It runs in linux and says it can do video.  There is a trial too.  It's $40 USD if you like it

---

### Post by noble on 2007-05-25
I tried twonk but I wasn't able to transcode and play oter movies then wmv and those supported natively by my xbox 360. thats not the solution for the problem of us ;)

---

### Post by gamma on 2007-05-26
Thanks for the tip on Twonkymedia, I was surprised to see it streams video. Is there any solution out there to convert files to something playable on the 360 in Linux? As far as I can tell VLC using ffmpeg can encode WMV video, but it can't encode WMA audio, so I get videos without sound.

---

### Post by lando786 on 2007-05-26
ps3 user here searching for the same features in an app any1 had any luck with mythtv im trying but dont really understand it

---

### Post by tgm4883 on 2007-05-26
> **lando786 said:**
> ps3 user here searching for the same features in an app any1 had any luck with mythtv im trying but dont really understand it

Well the PS3 runs linux so you could throw a mythtv frontend on there or maybe elisa

---

### Post by noname101 on 2007-05-27
If you have the latest update on your 360, then you can stream MPEG 4 files to it, with FAAC as the audio codec.

[Stream videos to xbox 360 with patched ushare]("http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/")

On the geexbox's forum, somebody said that streaming mp3's doesn't work, it might be the patch. Also ushare supposedly has a 1,000 file limit. [X360mediaserve]("http://sourceforge.net/projects/x360mediaserve/") supports mp3's only, you can use it while running ushare. You can change what computer your connecting to on the 360. Since x360mediaserve doesn't run on the same port it'll show it too. On the 360 go to options | computers | windows computers | disconnect, then click music or something, and it'll search for computers. It should show both. I'm using the 0.02-testing version of x360mediaserv, the other version wasn't working.

---

### Post by noble on 2007-05-28
that sounds amazing - hopefully they are making all the stuff more usable like tversity for windows without limits and full support. it must be possible. i think.

so i am looking forward to a perfect solution which starts with the the ushare patch ;)

---

### Post by gamma on 2007-05-30
> **noname101 said:**
> If you have the latest update on your 360, then you can stream MPEG 4 files to it, with FAAC as the audio codec.

[Stream videos to xbox 360 with patched ushare]("http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/")

On the geexbox's forum, somebody said that streaming mp3's doesn't work, it might be the patch. Also ushare supposedly has a 1,000 file limit. [X360mediaserve]("http://sourceforge.net/projects/x360mediaserve/") supports mp3's only, you can use it while running ushare. You can change what computer your connecting to on the 360. Since x360mediaserve doesn't run on the same port it'll show it too. On the 360 go to options | computers | windows computers | disconnect, then click music or something, and it'll search for computers. It should show both. I'm using the 0.02-testing version of x360mediaserv, the other version wasn't working.

I tried converting the videos following the guide, and I installed the debs from the blog, and my 360 can connect to my PC, but for some reason no videos are found on the 360. Any ideas?

---

### Post by noname101 on 2007-05-31
Sorry about that I forgot to patch the source before compiling it, it should work now hopefully. Re download it on my web site, make sure you're not running ushare though, when you reinstall.
Oh yeah if your xbox 360 doesn't detect it, restart ushare.

[Download updated 32bit package]("http://linux.vanvalkinburgh.org/files/geexbox/ushare_patched/ushare_0.9.10-1_i386.deb")

---

### Post by lando786 on 2007-05-31
> **tgm4883 said:**
> Well the PS3 runs linux so you could throw a mythtv frontend on there or maybe elisa

i could but i prefer to not dual boot besides my current tv is sd so it looks really bad :( Tversity rocks on windows gonna test the ushare patch and post my luck with it

---

### Post by tgm4883 on 2007-05-31
> **lando786 said:**
> i could but i prefer to not dual boot besides my current tv is sd so it looks really bad :( Tversity rocks on windows gonna test the ushare patch and post my luck with it

???  You prefer not to dual boot the PS3?  And what does that have to do with your tv being SD and looking like crap?  You post confuses me as I thought you were looking for a way to stream media to your PS3.

---

### Post by noname101 on 2007-05-31
You can also convert videos to a format playable by the xbox 360 with ffmpeg.
```
ffmpeg -y -i input.avi -vcodec h264 -b 1000000 -acodec aac -ar 48000 -ab 160 -f mov output.mov
```

Go [here]("http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/#ffmpeg") for packages with aac support, and also for a nautilus script for gnome users. Using the nautilus script is faster, all you have to do is right click on the file, and select scripts, then convert-360.sh. I converted two videos with ffmpeg and they both played on my xbox 360, one was a avi, and the other was a wmv. The wmv file wouldn't convert with avidemux. And yes I know wmv's can be played on the xbox, it was for testing, but not all wmv's can be played on the 360.

---

### Post by graveson on 2007-06-02
FYI,
I am using tversity in VMWARE with no problems. I have not found anything close to it in Linux so far ie something that can transcode on the fly

---

### Post by tj71587 on 2007-06-05
I am very new to linux, but did set up a server using samba that is recognized by windows machine, but I really want to get this up for 360, can anyone setup a howto for the best free xbox 360 software?

---

### Post by dasbooter on 2007-06-05
I don't want to upgrade the kernel on my xbox 360 as I am thinking of booting linux on it so I can only play wmv files right now. 

I have switched from suse linux that I guess had compiled windows media audio encoding capability (wmav1,wmav2) into ffmpeg but cannot seem to find a package that has the same for Ubuntu feisty. If anybody knows how I can get support for encoding this way please let me know.

This works in suse:

ffmpeg -i /home/dasbooter/2nd_storage/movie.avi -acodec wmav1 -vcodec wmv2 -ac 2 -qscale 3 /home/dasbooter/1rst_storage/visual_media/movie.wmv

but gives this in Ubuntu:

Unsupported codec for output stream #0.1

With what I have seen in ubuntu I find it hard to believe that some clever person hasn't compiled in support for encdoing wma with ffmpeg

---

### Post by joters on 2007-06-06
[http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/](http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/)

:popcorn:

---

### Post by alex-eduardo on 2007-06-25
I've got Tversity running on a windows box, with transcoding working fine (to PS3). On my fesity-box I could get Tversity running through wine, but not on-the-fly transcoding, unfortunately.

The other UPnP servers I've played around with are geebox and fuppes, but have ended up with MediaTomb.
It doesn't do transcoding, but is otherwise a well rounded, easily installed and configured UPnP server. Don't believe the hype about a smooth AJAX interface; it sucks a little bit, but at least doesn't try to do too much.

So because I don't want a big, bloated, heavy UPnP A/V server, MediaTomb seems like the best option for me. (The media-browser on the PS3 FW 1.80 is pretty basic in terms of grouping/searching/presenting anyways, so I don't need an overengineered backend either)

Anyways, so I logged a [request]("http://sourceforge.net/tracker/index.php?func=detail&aid=1742819&group_id=129766&atid=715783") for allowing hooking in an external on-the-fly transcoder with the guys over at the SF-project, and the lead guy said it was in the pipeline and he would start looking at it in a couple of weeks. 

There seems to be only one guy working on this thing, so if you're also waiting for a FOSS transcoding UPnP server for linux give "jin_eld" a pat on the back  (and tell him to hurry up ;P )

my $0.02

-Alex

---

### Post by tj71587 on 2007-07-06
I successfully am sharing mp3 using x360mediaserve, but i am unable to share my .m4a files...

Writing stream for file /etc/export/Ipod/Bandcamp/Wanna Dnace/Get To You.m4a

/home/tj/Desktop/x360mediaserve-0.0.1/ScriptDir/m4amp3

/etc/export/Ipod/Bandcamp/Wanna Dnace/Get To You.m4a

java.io.IOException: Cannot run program "/home/tj/Desktop/x360mediaserve-0.0.1/ScriptDir/m4amp3" (in directory "/home/tj/Desktop/x360mediaserve-0.0.1/ScriptDir"): java.io.IOException: error=13, Permission denied


Thats an example of the error i get, I gave chmod 777 instead of 755 when I installed it again.  Does anyone know of a fix for this or does it only share mp3s?

---

### Post by alb_gra on 2007-08-03
Sorry for bumping this up, but i think this is the best thread for asking my question.

I have ushare patched for xbox360 (deb downloaded from [http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/](http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/)   ), and it seems to be installed succesfully.

In fact, if i run ushare without demon optoin (-D) and in verbose mode, i can see work perfecty.

My only problem is i cant detect the linux box with ushare from the xbox360 (on the dashboard, i select multimedia -> video -> computers -> answre yes -> detect nothing :( )

¿Am i doing something wrong?, ¿any ideas?

Thank you!

PD: Sorry for my english :(

---

### Post by nutz on 2007-08-17
Has anyone gotten fuppes to work with Ubuntu?

---

### Post by dawguk on 2007-09-16
Shameless bump...

For those people still wanting to UPnP their media files for their Xbox360 or or DLNA for their PS3, the latest un-patched official released of ushare (v1.0) now works with both consoles.

I'm using Fedora7 (*gasp*), and this version is in their repo, so I'm sure Ubuntu are doing the same thing (?) It works faultlessly for me, and this is a fresh build.

There is a degree of tweaking required to get it to run and share as a daemon at boot time however. The default config runs ushare as the ushare user, so make sure that ushare has access to your media files (I just run the daemon as root - not advisable for those not knowing what they are doing).

In /etc/init.d/ushare, I had to manually add the option "--xbox" to start with xbox support. Likewise, starting it with "--dlna" will work for you PS3 users.

Next thing, in /etc/rc.d/ you need to make sure that ushare starts after networking, or it will fail because it can't find eth0, etc. This had me stumped for a while - if you need to know how to sort it, read up on changing your runlevel priority lists.

For converting my video files, I use avidemux. Open the video you want to convert, and use these settings:

Video: Mpeg4 (lvac)
Audio: FAAC
Format: MP4

Ensure that you use the .mov file extension, for compatability. Took a while to get everything together, but now that it works, I can barely fault it.

Hope that helps a little,
Pz.

---

### Post by David Mulligan on 2007-09-18
dawguk:  Does ushare give you on the fly transcoding or are you converting the videos before hand?

---

### Post by dawguk on 2007-09-21
Sadly Ushare doesn't transcode on the fly. But then I haven't been able to find a working, reliable open source equivalent.

I refuse to have a VM running Windows to transcode my videos!

---

### Post by damvcoool on 2007-09-21
> **dawguk said:**
> Sadly Ushare doesn't transcode on the fly. But then I haven't been able to find a working, reliable open source equivalent.

I refuse to have a VM running Windows to transcode my videos!

Have you tried Fuppes
[http://fuppes.ulrich-voelkel.de/](http://fuppes.ulrich-voelkel.de/)

it does Transcoding on the fly.

---

