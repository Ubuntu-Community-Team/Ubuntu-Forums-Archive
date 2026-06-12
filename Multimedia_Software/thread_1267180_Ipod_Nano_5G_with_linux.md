---
title: "Ipod Nano 5G with linux?"
date: 2009-09-15
forum: Multimedia Software
---

### Post by Graphite on 2009-09-15
Hi all,

I was recently given a new Fifth Generation iPod Nano, the one with a video camera. I can't get it to see songs that I've transferred onto it.

It mounts at /media/IPOD. Amarok 2.0.1, gtkpod and Songbird (latest versions as of this post) can see it, correctly recognise it as an iPod and transfer music to/from it with no error message. The files definitely make it onto the iPod, as Songbird can see and play the files that Amarok put there and vice versa. Additionally, exploring the iPod with a file browser shows the renamed music files.

Despite this, the iPod thinks it has "0 songs" on it. I created a "SysInfo" file with the firewireguid as described _[here](http://amarok.kde.org/wiki/Media_Device:IPod)_, (down at the moment? _[google cache](http://209.85.229.132/search?q=cache:-gzeR5OI5OgJ:amarok.kde.org/wiki/Media_Device:IPod+ipod+amarok&cd=1&hl=en&ct=clnk&gl=uk&client=firefox-a)_) but this didn't help.

I assume that Apple have changed something about how files are put onto the new iPod nano's song database and open software hasn't caught up yet.

1) Has anyone persuaded the new iPod Nanos to work with linux?
2) If so, how can I do the same?
3) If the fix needs something very difficult (e.g. finding a new key for signing the iPod's track database), what's your gut feeling for how long this tends to take after a new iPod release?

EDIT:
I'm using kubuntu 8.10.

---

### Post by jsc_moraga on 2009-09-15
I am having the same problem with Ubuntu 9.04(Gnome) and the 5th Gen Nano. It says it's syncing, the music files are on the nano, but it still says zero songs.

Using gtkpod 0.99.14 and libgpod 0.7.0.

---

### Post by Graphite on 2009-09-16
As a workaround, I've [installed virtualbox](http://www.howtoforge.com/installing-virtualbox-2.0.0-on-ubuntu-8.10-desktop), installed a spare Windows XP licence in a virtual machine then installed iTunes on it and [allowed the windows virtual machine to see my iPod](http://www.howtoforge.com/virtualbox-2-how-to-pass-through-usb-devices-to-guests-on-an-ubuntu-8.10-host).

So now I'm using the latest version of iTunes to control my iPod. I hadn't realised what a nice piece of software it is.

This setup is working well, but I'd still be grateful for a way to use my iPod with native linux apps (Amarok, Songbird, etc).

Can anyone make a suggestion?

---

### Post by vytalelementz on 2009-09-16
Have you tried rhythmbox yet? I have used this for 3rd and 4th generation nanos without any issues. To use it just import the music files to rhythmbox then you would just drag the album or artist to the ipod icon on the left panel. It basically works similar to itunes when uploading music. When finished transferring music over to your ipod, simply click the eject button that appears to the right of your ipod icon in the left panel. This should do the trick. Let me know if rhythmbox works better for you.

---

### Post by lordcris on 2009-09-16
I'm pretty sure there is not yet a linux application able to handle the nano 5g.
I had to install virtual box with a Xp of the Caribbean and use iTunes.
Nasty, but it works.

---

### Post by jsc_moraga on 2009-09-17
I tried it with rhythmbox, banshee and gtkpod. All of them can see the same music on the ipod, but the ipod itself still says "0 songs" when disconnected.

My 4th Gen nano works just fine, it's just the 5th gen one that doesn't.

---

### Post by aeriph on 2009-09-19
I've also just bought an iPod Nano 5G. I haven't tried using gtkpod with it after reading this post. gtkpod wants to initialize the ipod and i'm a bit concerned this could play havoc with it as it's not a supported model. does anyone know how long it will be before the guys at gtkpod make it compatible with the 5G? i'm assuming they will... :confused:

---

### Post by Graphite on 2009-09-19
Aeriph - I let Amarok initialise my iPod and it's fine; iTunes (running on Windows XP in a virtual machine) sees it as a perfectly healthy Windows-formatted iPod. It's working beautifully now. For all that I dislike some of Apple's aggressively closed-source and controlling policies, I have to admit that they build great products. I just wish I could get it working with a native Linux app, rather than running iTunes (huge memory hog) really slowly inside a VM.

I believe that Amarok (and pretty much anything else that talks to iPods on linux) uses the same libraries as gtkpod, so the fact that Amarok didn't harm mine should mean that gtkpod won't harm yours. There's always the option (in iTunes, if you're wiling to use it) to reset to factory settings, anyway.

Is this common behaviour for Apple? Do new models of iPod typically break Linux compatibility, or is this unique to this model?

---

### Post by magneze on 2009-09-21
Have run into this too. Pretty disappointing and yet totally unsurprising move from Apple.

---

### Post by jsindy on 2009-09-22
I am in the same boat, running Virtualbox + Windows 7 + iTunes 9, useing an SMB share on my ubuntu box to share the music. It took 14 hours to add 80gigs to iTunes. Horrible!.

I am going to try virtualbox with XP and the native virtual box folder sharing to see if it is any faster.

Hopefully 5th gens work with a native client soon!.

---

### Post by metalcoat on 2009-09-27
Alternatively you could try to help out with development as I am sure none of the developers yet have a new ipod.  You will most likely need a windows pc or a virtualbox in order to show the differences. [http://sourceforge.net/mailarchive/forum.php?thread_name=ece60cbe0909261113x2a75cd08pe084969ad7ed0721%40mail.gmail.com&forum_name=gtkpod-devel]("http://sourceforge.net/mailarchive/forum.php?thread_name=ece60cbe0909261113x2a75cd08pe084969ad7ed0721%40mail.gmail.com&forum_name=gtkpod-devel")

---

### Post by phixional ninja on 2009-09-29
Heh, so I used a pretty goofy work around for this.  It isn't terribly practical, but perhaps the fact that it worked will offer clues to some clever person as to what the underlying issue is.

I have a dual boot machine, Ubuntu 9.04 on one hard drive, Vista on the other.  All of my music is on the Ubuntu drive, and thus unavailable to Vista (or at least I haven't taken the time to install whatever it is that allows Vista to see ext3).

With my iPod fresh out of the box, I plugged it in while booted into Ubuntu, and initialized it with Rhythmbox.  Loaded on some music, ejected, iPod shows 0 songs.  Installed Banshee, took a look at the iPod, Banshee showed the music loaded on, still 0 songs when looking at the iPod unplugged from the computer.

Here's where it gets goofy.  Booted into Vista, plugged the iPod in, iTunes pops up and offers to initialize the iPod.  I do so, and iTunes also sees the songs on it.  Eject and unplug, and lo and behold, the iPod can now see and play the songs itself.  Huzzah!

Back to Ubuntu, Banshee claims that the song database (or something to that effect, I'll have to confirm terminology) is corrupt, and offers to rebuild it.  I let it, and load on more music.  Unplug iPod and...0 songs.

So, here is my current solution, without dealing with the hassle of loading 80GBs of music on to my Vista partition (I've only done this once, and just filled the iPod up, I won't bother changing the music loaded on it until this is resolved): I restored the iPod to factory settings using iTunes in Vista, but *unplugged *it before iTunes could initialize it.  Normally when you do a restore, iTunes wipes the iPod, then automatically initializes it.  If you let it, this won't work.  I then booted back into Ubuntu, and loaded the iPod up with all the music I wanted.  Back to Vista, and *then *let iTunes initialize.  All the music is still on the iPod, and playable.

It seems to me that somehow, the Ubuntu programs are incorrectly setting up the file database for the new iPods, and thus it can't find the music you put on it.  iTunes does it properly, and fortunately incorporates all the song files it finds on the iPod that were there already.

Amusing note: when I view all of the music loaded on the iPod in iTunes, it labels every song as [EXPLICIT].  Not sure why.

---

### Post by HHHhhh on 2009-10-08
I HAVE been able to get it to work.

I have writen-up a How To and posted it over at the Linux Mint forums. (Mint is a variation on Ubuntu so there should be no difference, infact the solution I have used should be workable where ever NVware runs.

Check it out and please paste your comments/issues/questions over there (as I am there more often than I am here.
[]("http://forums.linuxmint.com/viewtopic.php?f=42&t=25542")[http://forums.linuxmint.com/viewtopic.php?f=42&t=34082](http://forums.linuxmint.com/viewtopic.php?f=42&t=34082)

HTH :P

---

### Post by jsc_moraga on 2009-10-11
> **HHHhhh said:**
> I HAVE been able to get it to work.

I have writen-up a How To and posted it over at the Linux Mint forums. (Mint is a variation on Ubuntu so there should be no difference, infact the solution I have used should be workable where ever NVware runs.

HTH :P

You've gotten it to work with Windows. BFD. If I wanted to run Windows, I would just run Windows.

jsc

---

### Post by THD042 on 2009-10-25
Actually, life may get easier. AFAICT, Apple has changed some of the databases
from the esoteric mh* format to an SQLite3 database. On my 8GB Nano 5G under
/media/iPod/iPod_Control/iTunes/iTunes Library.itlp I see a couple of SQLite3 databases,
where Library.itdb contains some tables:

iPod_Control/iTunes/iTunes Library.itlp$ sqlite3 Library.itdb 
SQLite version 3.4.2
Enter ".help" for instructions
sqlite> .tables
album                  db_info                store_link           
artist                 genre_map              track_artist         
avformat_info          item                   version_info         
category_map           item_to_container      video_characteristics
composer               location_kind_map      video_info           
container              podcast_info         
container_seed         store_info           

sqlite> .mode line
sqlite> select * from item where artist="Frank Goosen";
                  pid = -1343237819282203479
       revision_level = 
           media_kind = 8
              is_song = 0
        is_audio_book = 1
       is_music_video = 0
             is_movie = 0
           is_tv_show = 0
          is_ringtone = 0
        is_voice_memo = 0
            is_rental = 0
          is_itunes_u = 0
           is_podcast = 0
        date_modified = 278090912
       date_backed_up = 0
                 year = 0
       content_rating = 0
 content_rating_level = 0
       is_compilation = 0
     is_user_disabled = 0
    remember_bookmark = 1
 exclude_from_shuffle = 1
part_of_gapless_album = 0
       artwork_status = 1
     artwork_cache_id = 116
        start_time_ms = 0.0
         stop_time_ms = 0.0
        total_time_ms = 11321309.0
   total_burn_time_ms = 
         track_number = 0
          track_count = 0
          disc_number = 0
           disc_count = 0
                  bpm = 0
      relative_volume = 0
            eq_preset = 
  radio_stream_status = 
            genius_id = 0
             genre_id = 25
          category_id = 0
            album_pid = -744237848531058920
           artist_pid = 1764508774798483360
         composer_pid = 41
                title = So_Viel_Zeit
               artist = Frank Goosen
                album = So viel Zeit
         album_artist = 
             composer = 
           sort_title = So_Viel_Zeit
          sort_artist = Frank Goosen
           sort_album = So viel Zeit
    sort_album_artist = 
        sort_composer = 
          title_order = 7500
         artist_order = 1900
          album_order = 4800
          genre_order = 2500
       composer_order = 4100
   album_artist_order = 4500
album_by_artist_order = 
    series_name_order = 100
              comment = 
             grouping = 
          description = 
     description_long = 
     track_artist_pid = 19
       physical_order = 106
           has_lyrics = 0
        date_released = 0

So far so good. Oddly enough, changing e.g. the name of an artist does not really help, it just creates a new one. But then again, I am not an expert in SQL and it could be it
was just things in a wrong order.

---

### Post by MauritsMB on 2009-10-30
It's odd because on the offical gtkpod website it says it supports up to the 5ht generation. But apparently that does not apply to the nana 5g video 8gb.
If anyone found a solution to do it without a virtual windows. Post it please!

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-30
AFAIK there's no support for 5g yet ;(

---

### Post by trailman on 2009-11-11
I have found a workaround to copy some MP3 and MP4 files from Linux to the Ipod 5G nano. However, this is not very easy if you want to copy a whole album, but if like me you just want to add some songs, some podcast or some films, this is OK.

As said, the Ipod 5G nano uses some SQLite3 databases, but modifying the data base is not enough. There are some obscure files, such as Locations.itdb.cbk to validate the database. So changing the database is not supported yet under Linux. See this gtkpod email archive on Sourceforge for more info : [http://sourceforge.net/mailarchive/message.php?msg_name=1253887389.7476.13.camel%40satan](http://sourceforge.net/mailarchive/message.php?msg_name=1253887389.7476.13.camel%40satan)

However you can replace existing MP3 and MP4 files without updating the database. A new file must have a play time lower than the original file to be able to play it till the end.

So the workaround is :
- create some dummy (but valid) MP3 and MP4 files, with different filenames and play times (using audacity and avidemux for example)
- use Windows only once to run iTunes and copy these files to the Ipod. his create the databases and the required files. All dummy MP3 and MP4 files are copied to iPod_Control/Music/f??/????.mp3 or .mp4
- boot Linux and replace all mp3 and mp4 files in these directories with empty files of the same name; this will save a lot of space
- all MP3 and MP4 files are now available on the iPod (sorted by file name). If you try to play these empty files, the Ipod returns immediately to the list.

Now if you want to add a real file, just replace an empty file with it.
However, to know which file to replace for a given filename displayed by the Ipod, some sqlite3 commands must be run on the databases. I have written a little bash script to make it easy. If somebody is interested, tell me.

To convert some video/films for the Ipod, I use avidemux 2.4.4 :
- open the video file to convert
- select AUTO / iPOD (MPEG-4ASP) / 640x480; this sets :
  - video : MPEG-4 ASP (XviD 4), 400kb/s, 640x480
  - audio : AAC (FAAC), 128kbs
  - format : MP4
- as the avidemux version I have does not let me select a higher resolution and the Ipod screen seems to be 800x500, I manually change video filters to have only one filter : "MPlayer resize" set to 800x500. This gives a full Ipod screen vidéo.
- then select File/Save start conversion

Note : ITunes refuses to copy a 800x500 video directly to the Ipod, saying that it can not be read ... but it can be (at least at 25frames/s, i have not tested 30fps). However 640x480 is accepted by iTunes (other modes not tested).

---

### Post by antitroll on 2009-11-12
Thanks trailman for the tip converting video for the ipod. Please continue to post any information you have about the nano 5g and linux.

---

### Post by trailman on 2009-11-12
OK, here are some extra infos and the script I use to copy some files to the ipod.

I have copied the following dummy files to the Ipod using iTunes (done only once) :
- a10mn_00.mp3 ... a10mn_49.mp3 : 50 audio files of 10mn (the bitrate does not matter; I used 96kb/s) to receive my real music tracks of less than 10mn (any bitrate; 192kb/s for example)
- a60mn_00.mp3 ... a60mn_19.mp3 : 20 ausio files of 60mn to receive some real podcasts
- v180mn_00.mp4 ... v180mn_07.mp4 : 8 video files of 3 hours (640x480 to make iTunes happy) to receive some real films (800x500 to have full screen video)
These files are used later as target locations (their name is the one displayed by the ipod) to store the real audio and video files.

Now every thing is done under Linux :
- connect the ipod; to mount the ipod filesystem (for me on /media/IPOD_GBL)
- list all entries available : ipod list
  all should be set as "used"
- to reset all entries to empty files : ipod remove
  this saves a lot of space on the ipod filesystem
- list all entries again : ipod list
  now they must all be set to "free" (available to copy new files)
- then copy a file to the ipod; for example : ipod copy a10m_00 myfirsttrack.mp3
- do the same for other files; for example : ipod copy v180m_03 myvideo.mp4
note : the third parameter is a pattern to select the target using its name (name displayed by the ipod) or the real target file name (file in F?? directories named ????.mp?)
- unmount the ipod filesystem and enjoy

Please find my "ipod.sh" sheel script as attachment.(rename it to "ipod" to run it)

---

### Post by MauritsMB on 2009-11-23
So there is still no Linux compatible app that works with nano 5g ?

---

### Post by thegeologician on 2009-11-26
...seems the developers of gtkpod are working on it, which is good news. 
[http://sourceforge.net/tracker/?func=detail&aid=2894503&group_id=67873&atid=519276](http://sourceforge.net/tracker/?func=detail&aid=2894503&group_id=67873&atid=519276)
(link goes funny often...)

The guy just doesn't have an iPod nano 5th gen himself yet, and as far as I gather, any donations would be highly appreciated... ;-) (no, I'm not affiliated to the project and I don't know him, but I strongly believe in OpenSoftware, so I did my share - unfortunately I can only afford a small one...)

IPod support in Rhythmbox and Amarok (and others) is by libgtkpod, as far as I understand, so this should solve our problems... :-)

---

### Post by murderslastcrow on 2009-12-15
So wait- the solution for the iPhone/iTouch 3 firmware in the official community documentation is the same database fix that would work for this nano, too?

I sure hope they can package it soon, since my friend is getting this nano for Christmas and is under the impression that, like the gtkpod site says, it supports all iPods up to the 5th Generation. So I guess the Nano and Touches are the only ones not functioning perfectly yet, but it will be here so soon!

They tried so hard to block us out, but it will never work for long. It's just a pain in the butt to use iTunes.

---

### Post by jenkinbr on 2009-12-21
I sure hope this gets fixed soon, because the VirtualBox method isn't working for me.

My Nano keeps getting disconnected from the VM then reconnected :'(

Really annoying

---

### Post by DJGibbon on 2009-12-21
According to Some Guy On The Internet, the latest git code works fine with the Nano 5G

[http://twitter.com/antilo0p/status/6641803288](http://twitter.com/antilo0p/status/6641803288)

Not sure how long this will take to be pushed out into packages. Does anyone know if there's a libgpod / gtkpod nightly PPA? Had a quick Google and couldn't see anything.

murderslastcrow: iPod generations are different between different model lines - a 5G iPod is not the same generation as a 5G Nano. In terms of Linux support, the 5G nano has got more in common with the iPhone than an iPod Classic, thanks to Apple being awkward buggers.

---

### Post by __j__ on 2009-12-22
> **DJGibbon said:**
> According to Some Guy On The Internet...

Clearly that kind of credibility is too strong to ignore. :) So I compiled libgpod from the latest git sources and gave it a go with my new Nano 5G. It's very encouraging, but not quite working. Here's what I'm seeing:

Once the iPod is properly initialized [1,2], transferring songs with metadata to the iPod and reading them back works using gtkpod or amarok. Both the iTunesCDB (used by libgpod and, as I understand, the iTunes desktop app) and the *.itdb SQLite files (used by the newest iPods) are updated.

Unfortunately the iPod itself shows no music. [This thread]("http://sourceforge.net/mailarchive/message.php?msg_name=1253887389.7476.13.camel%40satan") seems to suggest that it's due to the Locations.itdb.cbk not being correctly hashed. But the thread is a few months old now, and the current libgpod source is writing SHA1 hashes to that file... Hmmm...

Anyone else seeing anything interesting here?


[1] Make sure 'iTunes_Control/Device/SysInfo' has the 'FirewireGuid' property set. Without this the database files are created locally, but not transferred to the iPod. More info [here]("http://amarok.kde.org/wiki/Media_Device:IPod#My_iPod_does_not_show_any_music").
[2] Make sure 'iTunes_Control/Device/HashInfo' has been written to your iPod. You can generate the hash [here]("http://ihash.marcansoft.com/").

---

### Post by Rob_H on 2009-12-22
> **__j__ said:**
> Once the iPod is properly initialized [1,2], transferring songs with metadata to the iPod and reading them back works using gtkpod or amarok. Both the iTunesCDB (used by libgpod and, as I understand, the iTunes desktop app) and the *.itdb SQLite files (used by the newest iPods) are updated.

Unfortunately the iPod itself shows no music.

That's the symptom I see with the "shipping" libgpod (0.7.2) and gtkpod. Are you sure you're not still running the old code?

---

### Post by __j__ on 2009-12-22
> **Rob_H said:**
> That's the symptom I see with the "shipping" libgpod (0.7.2) and gtkpod. Are you sure you're not still running the old code?

Yes. I put a bunch of extra debug print statements in, and I see their output at the console.

```
dpkg -l | grep gpod
ii  libgpod4                             0.7.3-git-20091222-1
```

Also I don't think the 0.7.2 version has support for the Nano 5G or the new SQLite database format at all.

So are you saying that the behavior I'm seeing has been fixed in the current source tree...at least hypothetically?

---

### Post by Rob_H on 2009-12-22
> **__j__ said:**
> So are you saying that the behavior I'm seeing has been fixed in the current source tree...at least hypothetically?

I'm not saying that, but Some Guy On The Internet seems to be.

---

### Post by __j__ on 2009-12-22
> **Rob_H said:**
> I'm not saying that, but Some Guy On The Internet seems to be.

Depending on what he's saying...

[http://twitter.com/antilo0p/status/6641278100](http://twitter.com/antilo0p/status/6641278100)
[http://twitter.com/antilo0p/status/6641803288](http://twitter.com/antilo0p/status/6641803288)

It sounds like he may be reading from an Nano 5G that already had a valid database on it (i.e. written with iTunes).

It's been noted a few [different]("http://sourceforge.net/mailarchive/message.php?msg_id=1253887389.7476.13.camel%40satan") [places]("http://www.hydrogenaudio.org/forums/index.php?showtopic=45160&st=2100&p=644564#entry644564") that you can use a third party tool (e.g. libgpod) to read/write content on the iPod, and then use iTunes to touch the iPod's library in some minor way, causing it to update the check block, after which the iPod will show all the transferred content. Haven't tried this yet personally...I don't have an OS X or Windows install handy.

---

### Post by murderslastcrow on 2009-12-25
> A project to enable syncing with iPhone Firmware 3.0 is under way (30 October 2009). See: [http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/)

One must install ifuse from the Ubuntu repos. Then, installing the SVN versions (as of November 25th, 2009) of gtkpod, libgpod, usbmuxd and related dependencies (from source - the distro packages MAY NOT work!) enables:

Syncing Music.
Syncing Photos.
Syncing Videos.
Even though the support is alpha/beta in quality, it works well enough for testing purposes. In one user's case, it has operated fine syncing large amounts of Audio and video both to and from the iDevice running firmware 3.1.2. After a short "Updating Library.." setop on the iDevice the next time the Music or Video application was opened, all songs and videos were present, had album art, and played correctly. YAY!

This is from the official iPod Touch page in the community documentation. I would suspect checking out these other packages would make it Nano 5G compatible, as well?

My best friend got one for Christmas, so this should be an exciting journey into alpha quality software for her. XD Or we could just use her pre-existing XP VirtualBox. Still, I can't wait until these changes are officially packaged. A lot of people have been waiting for this for a LONG time, as far as the touch devices go.

---

### Post by Okiura on 2009-12-27
Hi Guys,

I got one of these Nano 5G's for my wife for Xmas, I didn't wanna get it but she really wanted it, and like me she only uses Linux. so it seems I bought her a useless Xmas present? any married ppl out there know the consequence of buying your wife a useless gift? lets just say it's not pretty :)

Anyway, to avoid anymore pain I started work on getting this working... and below is an attached file with a working copy of the itdb_sqlite source and header file for libpod for the Nano 5G. this is only 2 days worth of work so it still needs some tweaking, and it will most likely break compatibility with other model ipods, so if you use another model ipod it may not work after installing this

What works:
Transfer of music.
Changing of rating or id3tag info.

What doesn't:
Play lists.
Lots of other random things (assuming everything I haven't tested doesn't work)

I would like to point out here that this is just a concept so I will not be fixing any of the issues, please do not report them. the developers at gtkpod are working on Nano 5G and there work is so much better than mine :), as their doing it properly and my fix is just a ugly one I'd suggest watching there site closely for any updates to support the Nano 5G and update when the device is supported.


Okiura,



Download libpod from [http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=snapshot;h=dc09d016db68fc69f5054b5bae8c9fbf483688e2;sf=tgz]("http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=snapshot;h=dc09d016db68fc69f5054b5bae8c9fbf483688e2;sf=tgz"), copy the attached files into the src directory, build and install

---

### Post by stefanadelbert on 2009-12-28
I tried applying these changes to the latest libgpod code from the GIT repository and rebuilding both libgpod and gtkpod, but I still don't get any song appearing on my iPod 5G (16GB) after syncing.

I'll give it another go from scratch a bit later.

---

### Post by Lorenz on 2009-12-28
hm, I just ordered one - seems I have to install XP via virtualbox again then :(

---

### Post by Okiura on 2009-12-28
> **stefanadelbert said:**
> I tried applying these changes to the latest libgpod code from the GIT repository and rebuilding both libgpod and gtkpod, but I still don't get any song appearing on my iPod 5G (16GB) after syncing.

I'll give it another go from scratch a bit later.

make sure your sysinfo file has the firewireid (starting with a 0x then the 16 numbers) and model, check the README from the source on how to do that without it the checksum will be wrong and no tracks will display

---

### Post by stefanadelbert on 2009-12-28
That did the trick. Seems that I didn't have libsgutils installed. I just followed the manual instructions though and it's all working fine now.

Thanks for the help.

---

### Post by last1 on 2009-12-28
> **Okiura said:**
> Hi Guys,

I got one of these Nano G5's for my wife for Xmas, I didn't wanna get it but she really wanted it, and like me she only uses Linux. so it seems I bought her a useless Xmas present? any married ppl out there know the consequence of buying your wife a useless gift? lets just say it's not pretty :)

Anyway, to avoid anymore pain I started work on getting this working... and below is an attached file with a working copy of the itdb_sqlite source and header file for libpod for the Nano G5. this is only 2 days worth of work so it still needs some tweaking, and it will most likely break compatibility with other model ipods, so if you use another model ipod it may not work after installing this

What works:
Transfer of music.
Changing of rating or id3tag info.

What doesn't:
Play lists.
Lots of other random things (assuming everything I haven't tested doesn't work)

I would like to point out here that this is just a concept so I will not be fixing any of the issues, please do not report them. the developers at gtkpod are working on Nano G5 and there work is so much better than mine :), as their doing it properly and my fix is just a ugly one I'd suggest watching there site closely for any updates to support the Nano G5 and update when the device is supported.


Okiura,



Download libpod from [http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=snapshot;h=dc09d016db68fc69f5054b5bae8c9fbf483688e2;sf=tgz]("http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=snapshot;h=dc09d016db68fc69f5054b5bae8c9fbf483688e2;sf=tgz"), copy the attached files into the src directory, build and install

Sweet, I can't wait to try this out later. Thanks so much!

---

### Post by mattycoze on 2009-12-28
I am running Ubuntu 9.10, and had problems compiling the library from source (due cause; apparent noobieness)

Quote: Download libpod from [http://gtkpod.git.sourceforge.net/gi...83688e2;sf=tgz](http://gtkpod.git.sourceforge.net/gi...83688e2;sf=tgz), copy the attached files into the src directory, build and install

When I tried building the library from source I ran into problems:

mattycoze@mattycoze-laptop:~/src/libgpod$ sudo ./autogen.shchecking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.64
checking for automake >= 1.7...
  testing automake-1.11... found 1.11
checking for libtool >= 1.4.3...
  testing libtoolize... found 2.2.6
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... not found.
***Error***: You must have glib-gettext >= 2.2.0 installed
  to build libgpod.  Download the appropriate package for
  from your distribution or get the source tarball at
    [ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz](ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz)


I was able to install libtool from the Ubuntu repository but ran into problems when trying to install glib-gettext - I couldn't find a 'deb'. I was wondering if someone had already compiled a .deb from the source for Ubuntu users (even though this program may be buggy).

---

### Post by stefanadelbert on 2009-12-28
Here is an extract from the INSTALL file which is part of the gtkpod source:

```
The following steps were necessary to install libgpod and gtkpod on a fairly virgin Ubuntu Hardy (LTS 8.04) installation.

# required packages
sudo apt-get install autoconf flex gettext libglib2.0-dev libgtk2.0-dev libglade2-dev libid3tag0-dev libxml-parser-perl pkg-config automake gcc git-core gtk-doc-tools

# recommended packages
sudo apt-get install libcurl4-dev libflac-dev libgnomevfs2-dev libhal-dev libvorbis-dev libmp4v2-dev

# checkout libgpod and gtkpod
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/libgpod
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod

# compile libgpod
cd libgpod/
./autogen.sh
make
sudo make install

# compile gtkpod
cd ../gtkpod/
cd libgpod/
./autogen.sh
make
sudo make install

#start gtkpod
gtkpod &
```

Make sure that you have installed all the dependencies (see the two [FONT="Courier New"]sudo apt-get install[/FONT] commands).

It's probably best to build your own just to make sure that you're building against exactly the right versions of the various libraries for your system.

---

### Post by learnincurve on 2009-12-29
So what needs to be installed for nano 5g support? I got my daughter one for Christmas, and a wife's wrath barely surpasses that of a daughter who's Christmas present doesn't work. I installed libgpod and gtk-pod from git, but had no luck sync'ing. Have now patched libgpod with okiura's code, and will try again on my daughter's computer this evening. itunes in Virtualbox is HORRIBLE, and freezes the VM after transferring a few songs (even with a couple of GB thrown at it). I did install the iphone and ipod touch software as murderslastcrow suggested, tho not necessarily in the right order, and noticed no difference in behaviour. firewire-id looks like it is correct after I finally got the ipod initialized from itunes in a second virtualbox VM (the first one kept refusing to update it), so maybe the manual steps to set the firewire-id are not necessary after initializing from itunes?? Acually using Debian Sid, but the packages/versions look pretty similar to Ubuntu 9.10. Git's of libgpod and gtk-pod build fine.

---

### Post by Lorenz on 2009-12-29
can someone make this a deb file from this hacked stuff posted above? I suck so much at compiling and if there dependencies missing, I'm usually lost. Or can someone perhaps post a how-to? I'd (and perhaps many others) eternally grateful!

---

### Post by Rob_H on 2009-12-29
> **Lorenz said:**
> can someone make this a deb file from this hacked stuff posted above? I suck so much at compiling and if there dependencies missing, I'm usually lost. Or can someone perhaps post a how-to? I'd (and perhaps many others) eternally grateful!

I think the takeaway of this thread is that active development is going on so if you're not comfortable compiling from sources, you're probably better off waiting for the real package. It's still baking.

---

### Post by Lorenz on 2009-12-29
> **Rob_H said:**
> I think the takeaway of this thread is that active development is going on so if you're not comfortable compiling from sources, you're probably better off waiting for the real package. It's still baking.

yeah, fair enough :) I will try it anyway once I have some time on my hands. I agree with what has been said earlier on in this thread - lacking ipod/iphone support is a huge showstopper for people wanting to move :(

---

### Post by stefanadelbert on 2009-12-29
After patching libgpod and manually setting the firewireid my iPod works perfectly with gtkpod and rhythmbox.

For those nervous to build libgpod and gtkpod, don't be. It's not actually a big deal. Once you've build from source once you'll realise how easy it actually is. There are very straightforward step-by-step instructions on how to build libgpod and gtkpod from source in the INSTALL file which is part of the gtkpod project. It lists all the dependencies and even has commands that you can cut and paste for installing the dependencies.

You will need to install build-essential package first though, which has compiler, linker and other necessary stuff for building from source code:

```
sudo apt-get install build-essential
```

Then just follow the libgpod and gtkpod specific steps in the gtkpod project INSTALL file, which I've pasted below:

```
Quick guide for Ubuntu/Debian

The following steps were necessary to install libgpod and gtkpod on a fairly virgin Ubuntu Hardy (LTS 8.04) installation.

# required packages
sudo apt-get install autoconf flex gettext libglib2.0-dev libgtk2.0-dev libglade2-dev libid3tag0-dev libxml-parser-perl pkg-config automake gcc git-core gtk-doc-tools

# recommended packages
sudo apt-get install libcurl4-dev libflac-dev libgnomevfs2-dev libhal-dev libvorbis-dev libmp4v2-dev

# checkout libgpod and gtkpod
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/libgpod
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod

# compile libgpod
cd libgpod/
./autogen.sh
make
sudo make install

# compile gtkpod
cd ../gtkpod/
cd libgpod/
./autogen.sh
make
sudo make install

#start gtkpod
gtkpod &
```

Give it a go and you'll see that it's not all that tough.

Once you've got libgpod and gtkpod installed, you'll need to make sure that the firewire-id is set correctly on your iPod. There are some automatic ways to get this right, but I just did it the manual way. There are instructions on how to do this in the README.SysInfo file which is part of the libgpod project. I've pasted the contents of this file below. I have bolded the instructions for the manual solution.

```
Starting with the iPod Classics and the Video Nanos, libgpod needs an 
additional configuration step to correctly modify the iPod content. libgpod 
needs to know the so-called iPod "firewire id", otherwise the iPod won't 
recognize what libgpod wrote to it and will behave as if it's empty.

There are several ways to set up an iPod so libgpod can find its firewire id.

The preferred method is automatic. Make sure you have hal and libsgutils
installed before running configure/autogen.sh. If you built libgpod without
them, run configure/make/make install after you install them.

A hal callout and .fdi file will be built and installed. This will query an
iPod when it is plugged in and save the SysInfoExtended file in the proper
place. This should be entirely automatic. If you have trouble with this, see
the TROUBLESHOOTING file for some hints.

If you build with libsgutils but without hal, the next best method is mostly
automatic. You should have an ipod-read-sysinfo-extended tool available. Run
it with the iPod device path and the iPod mount point /mnt/ipod) as arguments.
For example:

    $ ipod-read-sysinfo-extended /dev/sda /mnt/ipod

This may require root privileges. It reads an XML file from the iPod and
writes it as /mnt/ipod/iPod_Control/Device/SysInfoExtended. More details on
this method can be found at http://ipodlinux.org/Device_Information.

Having the SysInfoExtended file created by ipod-read-sysinfo-extended or the
hal callout is enough for libgpod to figure out the iPod firewire id.

[B]The last method requires more manual intervention. First, you need to
determine the firewire id of the iPod. To do that on Linux, plug in the iPod
in and run (with root privileges):

    $ lsusb -v | grep -i Serial

This should print a 16 character long string like 00A1234567891231. For an
iPod Touch, this number will be much longer than 16 characters, the firewire
ID is constituted by the first 16 characters.

On FreeBSD, there is a tool to get the serial number at:

    http://50hz.ws/dev/getserial.c

Once you have the serial number, edit /mnt/ipod/iPod_Control/Device/SysInfo,
creating the file if it does not exist. (Replace /mnt/ipod with the path to
where the iPod is mounted). Add a line like this to the SysInfo file:

FirewireGuid: 0xffffffffffffffff

Replace ffffffffffffffff with the serial number you obtained in the previous
step. Don't forget the 0x before the string. After you add the FirewireGuid to
the SysInfo file you need to rewrite the iTunesDB for the change to take
effect. For example, add a new song or adjust the playcount of an existing
song and save the changes in gtkpod.[/B]

Be careful when using applications which let you manually specify the iPod
model. They may overwrite the SysInfo file and undo the changes.

Finally, if you compiled libgpod from source, you can test that libgpod can
find the firewire ID on the iPod using the test-firewire-id program in the
tests/ dir of the libgpod source. For example:

    $ cd ~/src/libgpod/tests
    $ ./test-firewire-id /ipod/mount/point
```

I'm happy to help you get this working. If you need any clarity, please let me know.

---

### Post by erissiva on 2009-12-30
> **stefanadelbert said:**
> After patching libgpod and manually setting the firewireid my iPod works perfectly with gtkpod and rhythmbox.

For those nervous to build libgpod and gtkpod, don't be. It's not actually a big deal. Once you've build from source once you'll realise how easy it actually is. There are very straightforward step-by-step instructions on how to build libgpod and gtkpod from source in the INSTALL file which is part of the gtkpod project. It lists all the dependencies and even has commands that you can cut and paste for installing the dependencies.

You will need to install build-essential package first though, which has compiler, linker and other necessary stuff for building from source code:

*code removed for quoting purposes*

I'm happy to help you get this working. If you need any clarity, please let me know.

Thank you...this worked really well.
Except it still won't work. But I think that may be because I don't know the model number. It's the Nano 8GB Black (5G, of course).
I tried with the previous generation (xB754), but it doesn't work. Google turned no results.

Get this error:
> 
Hashed file is 0 bytes long
Could not create hash value from itunesdb
Extended info will not be used.
iPod Database Import Failed:"Illegal seek to offset 0 (length 4) in file '/media/STARLIGHT/iPod_Control/iTunes/iTunesDB'.'


---

### Post by poubelle on 2009-12-30
> **stefanadelbert said:**
> ./autogen.sh


I'm unable to get here. This is the error:

"checking for LIBGPOD... configure: error: Package requirements (glib-2.0 >= 2.8.0 gobject-2.0 sqlite3) were not met:

No package 'sqlite3' found"

So I can't make install.

Unfortunately the store said no returns once the box has been opened... So now I have a $175 paperweight.

---

### Post by erissiva on 2009-12-30
> **poubelle said:**
> I'm unable to get here. This is the error:

"checking for LIBGPOD... configure: error: Package requirements (glib-2.0 >= 2.8.0 gobject-2.0 sqlite3) were not met:

No package 'sqlite3' found"

So I can't make install.

Unfortunately the store said no returns once the box has been opened... So now I have a $175 paperweight.

```
sudo apt-get install libsqlite3-dev libsqlite3-0
```

;)

---

### Post by nothingspecial on 2009-12-30
Not working here. Applied the patch. built libgpod and gtkpod. manually added the firewire id.

Have I missed something

---

### Post by poubelle on 2009-12-30
> **nothingspecial said:**
> Not working here. Applied the patch. built libgpod and gtkpod. manually added the firewire id.

Have I missed something

Me too. Got sqlite installed, installed libgpod and gtkpod. Added the FirewireID to sysinfo (and I see it has been reflected in sysinfo.extended)... but when I run gtkpod I'm still asked to initialize the Ipod, and only the old generations are available. When I run ./test-firewire-id /ipod/mount/point I get "Couldn't find firewire ID".

I wish I hadn't assumed iPods could do mass-storage. I'm stuck now with a $175 paperweight, because they won't accept returns.

Edit: I initialized it as the 4th generation and it seems to let me put music on the iPod... the iPod itself shows the double-arrow "synchronizing" screen... but when I unmount it, it tells me there are zero songs.

I used Macs for years but I really, really despise Apple right now.

---

### Post by nothingspecial on 2009-12-30
Don`t worry, they`ll get there eventually.

I am a full time linux only user who has never had a windows computer.

I took a windows computer home from work a few days ago. I haven`t managed to get it online yet. So I formatted a usb stick and downloaded the iTunes binary and put it on the windows box. It took about 20 minutes to install and when it finally did, I tried to launch it and was presented with a message along the lines of

"the default folder for iTunes is My Music and it doesn`t exist"

I have googled, tried to follow instructions and edited the windows registry for hours without success.

Don`t anyone ever tell me that linux is difficult again.

I can`t get the stupid thing to work on either os

---

### Post by nothingspecial on 2009-12-30
> **nothingspecial said:**
> Don`t worry, they`ll get there eventually.


And when they do, you`ll just plug it in and it will work, just like my wireless usb dongle and my thing that you plug into the plug socket to connect you to the router does with all my linux machines.

Instead of having the windows "wizard" fail miserably at finding the drivers from wherever it was going to.

I`ll tell you something, I can imagine how hard it is coming from a life time of windows to Ubuntu, but going the other way is a nightmare.

I chuck the cds that come with hardware in the bin. Ok, kind of wish I hadn`t now, but how come the worlds most popular operating system can`t work with a belkin wireless dongle when  linux can?

This has turned into a rant but - duh

I just want it to connect to the internet and install iTunes. What do I click?

---

### Post by poubelle on 2009-12-30
So.... gtkpod seems to transfer the music. The iPod makes the double-arrow "synchronizing" screen. Quod Libet can view the files I put on the iPod. And there's stuff like this in the iTunesDB.ext file on the iPod:

```
itunesdb_hash=73e3ebae7788f4e854e755997130c4d7b8139942
version=0.99.15GIT
id=52
hostname=myhostname
filename_locale=/home/myusername/Music/Library/Madvillain/Madvillainy/Fancy Clown.mp3
filename_utf8=/home/myusername/Music/Library/Madvillain/Madvillainy/Fancy Clown.mp3
filename_ipod=:iPod_Control:Music:F08:libgpod751634.mp3
sha1_hash=a1ba3746efd327351ba36d68c7264061c4a894e0
charset=UTF-8
pc_mtime=1262129557
local_itdb_id=8857632216725869342
local_track_dbid=1726676225595693788
transferred=1

```

Yet when I unmount and go through the iPod's main menu, it says I have zero songs. What am I missing?

---

### Post by stefanadelbert on 2009-12-30
That's exactly what I had. I'm afraid that I can't remember exactly what I did to get it going, but at one point I did connect the iPod to iTunes on a Windows box to update the software. That probably did all the initialisation, although it didn't set the firewireid. I then went back to Ubuntu and set the firewireid and connected to the patched libgpod/gtkpod and was able to setup the iPod (5th gen was in the list) and transfer songs over without hassles.

I hate to think that it was the Windows step that made the difference.

If you don't have "5th gen" in the list of available models, that hints that your build of gtkpod didn't work properly. Note that "5th gen" is right at the bottom of the list, not directly after the "4th gen" models. That stumped me initially, so just make sure that "5th gen" really isn't in the list.

---

### Post by thomaszmark on 2009-12-30
I've also just bought an iPod Nano 5G, have the same problem like this, help me to overcome this

---

### Post by poubelle on 2009-12-30
> **stefanadelbert said:**
> I hate to think that it was the Windows step that made the difference.

My understanding from all my Googling is that you do have to "touch" it with the actual iTunes client and then it -- might, possibly, maybe -- will work.

> **stefanadelbert said:**
> If you don't have "5th gen" in the list of available models, that hints that your build of gtkpod didn't work properly. Note that "5th gen" is right at the bottom of the list, not directly after the "4th gen" models. That stumped me initially, so just make sure that "5th gen" really isn't in the list.

Under iPhone?

Nope, definitely not there. Unless it's in one of the submenus...

Well in the process of all this I managed to delete about 2/3 of my MP3s. I have no idea how this happened, I can only suppose it's related to my attempts to synchronize the iPod. 

So not only have I wasted $175 and a day of my life I'll never get back, a tonne of my music seems to be lost forever.

I owned and loved Macs for years but after the last 24 hours I will NEVER buy an Apple product again. If they allowed returns this would be back on the store shelf already.

---

### Post by stefanadelbert on 2009-12-30
> **thomaszmark said:**
> I've also just bought an iPod Nano 5G, have the same problem like this, help me to overcome this

Best to read from the beginning of this thread.

[QUOTE=poubelle]Nope, definitely not there. Unless it's in one of the submenus...[/QUOTE]

It should be its own menu item. Maybe libgpod hasn't been installed properly. Probably best to start from scratch with liobgpod/gtkpod. Make sure that any repo versions of either libgpod or gtkpod are uninstalled. After building and installing ([FONT="Courier New"]sudo make install[/FONT]) of libgpod, make sure that the actual installed librarie (probably /usr/local/lib/libgpod.so.4.2.0) is the one that you've just built. Make sure there aren't any other libgpods hanging around that gtkpod might build against ([FONT="Courier New"]locate libgpod[/FONT]). Then try build and install gtkpod. You can check the libraries that gtkpod will use by running
```
ldd /usr/local/bin/gtkpod
```
Check that it refers to the patched libgpod that you built.

If iPod Nano 5G is still not in the dropdown after this, then I reckon something else is going on...

---

### Post by erissiva on 2009-12-30
Ok - so since I'm wasn't getting the model number from GTKpod before, I purged, and rebuilt from scratch.
Now the menu item is there.
Made sure FirewireID is correct (with preceding 0x).

Loads, with error:
```
Hashed file is 0 bytes long
Could not create hash value from itunesdb
Extended info will not be used.
```

Loads library, and acts like it deletes/transfers stuff, but same issue as before - iPod says "No!" and shows items as still being there. Try to play them and freezes iPod.
This is very frustrating. :(

---

### Post by Okiura on 2009-12-31
Hi all

Everyone is having the same issue of no songs showing, this is because the wrong checksum is being calculated, this is caused by incorrect info in the SysInfo file. You need to get that right first i.e. selecting the 4th Gen and sync'n will transfer your songs but the model number is wrong and this cause the checksum to be wrong and the songs not to display.

a few ppl before this post has advised how to manually check/set this info also it is in the README file in the source, if this is not working for you then your either not using a 5G or you got something wrong in the Sysinfo file. here is a list of Model numbers for the 5G's

8 Gig (silver) = xC027 (Black) = xC031 (Purple) = xC034 (Green) = xC037 (Blue) = xC040 (Yellow) = xC043 (Orange) = xC046 (Red) = xC049 (Pink) = xC050

16 Gig (silver) = xC060 (Black) = xC062 (Purple) = xC064 (Green) = xC066 (Blue) = xC068 (Yellow) = xC070 (Orange) = xC072 (Red) = xC074 (Pink) = xC075

If you still can't get this to work after setting the correct info you'll be better of waiting for the guys over at gtkpod to implement G5 support, once they have it should all be done automatically for you :)

Okiura

---

### Post by Fajman on 2009-12-31
Just tried it all...
The build went fine and FirwireID test ok but i get this error when trying to load the iPod... any ideas? (note - i selected the correct iPod model)

Extended info will not be used.
iPod Database Import Failed.

I have a black 5G Nano

---

### Post by Okiura on 2009-12-31
> **Fajman said:**
>  Extended info will not be used. 

This is not a error this is just information.

> **Fajman said:**
>  iPod Database Import Failed. 

This one is a error, wrong mount point selected, maybe. check and see where your ipod is mounted and make sure you have that mount point selected it should be "/media/ipod" or something similar. 

Okiura,

---

### Post by erissiva on 2009-12-31
> **Okiura said:**
> Hi all

Everyone is having the same issue of no songs showing, this is because the wrong checksum is being calculated, this is caused by incorrect info in the SysInfo file. You need to get that right first i.e. selecting the 4th Gen and sync'n will transfer your songs but the model number is wrong and this cause the checksum to be wrong and the songs not to display.

a few ppl before this post has advised how to manually check/set this info also it is in the README file in the source, if this is not working for you then your either not using a 5G or you got something wrong in the Sysinfo file. here is a list of Model numbers for the 5G's

8 Gig (silver) = xC027 (Black) = xC031 (Purple) = xC034 (Green) = xC037 (Blue) = xC040 (Yellow) = xC043 (Orange) = xC046 (Red) = xC049 (Pink) = xC050

16 Gig (silver) = xC060 (Black) = xC062 (Purple) = xC064 (Green) = xC066 (Blue) = xC068 (Yellow) = xC070 (Orange) = xC072 (Red) = xC074 (Pink) = xC075

If you still can't get this to work after setting the correct info you'll be better of waiting for the guys over at gtkpod to implement G5 support, once they have it should all be done automatically for you :)

Okiura

What it seems to be doing is erasing my iTunesDB file every time I unmount...which doesn't make sense. And then when I remount, it complains about the empty file. :(

EDIT: In fact, when I delete the file (That is empty) manually, gtkpod offers to create it for me. But it makes and empty one anyways. :-/

---

### Post by Okiura on 2009-12-31
> **erissiva said:**
> What it seems to be doing is erasing my iTunesDB file every time I unmount...which doesn't make sense. And then when I remount, it complains about the empty file. :(

EDIT: In fact, when I delete the file (That is empty) manually, gtkpod offers to create it for me. But it makes and empty one anyways. :-/

the iTunesDB file is not used on on the 5G so being 0 bytes in size is normal, the database files are now .itdb files. This sounds to me like gtkpod needs updating or maybe try rhytembox (the one i use). I was getting a similar error when i first tried to sync but i got the latest gtkpod from the git and seemed to fix it. 

Okiura,

---

### Post by fakaralama on 2009-12-31
Hi all, thanx for all your posts, I'm new in the forum and I've got the same problem as everyone: a brand new blue ipod 5g nano video, but I'm not able to transer the songs on it...

I'd like to ask you some questions connected to the possibilities I'm figuring out: 

1- Is it possible to contact gtkpod developers to know if a new version is going to be released soon (otherwise I'm thinking to change my ipod?)
2- If I try to use my Ipod on a Mac and then come back to Ubuntu, would there be any chances it could work there too?
3- In case I decided to put Linux on my Ipod for now, would it be then possible to come back to the original settings?

I can't figure out other ways out but these...

Cheers

---

### Post by PotHix on 2009-12-31
The same for me... :(
Get this error:

> **erissiva said:**
> 
Hashed file is 0 bytes long
 Could not create hash value from itunesdb
 Extended info will not be used.
 iPod Database Import Failed:"Illegal seek to offset 0 (length 4) in file '/media/POTHIX/iPod_Control/iTunes/iTunesDB'.'                      

GtkPod don't have an option to 5th generation of ipod nano, but i'm trying to use 4th generation. (black 16GB)

Ideas?

---

### Post by Okiura on 2009-12-31
> **PotHix said:**
> The same for me... :(
Get this error:



GtkPod don't have an option to 5th generation of ipod nano, but i'm trying to use 4th generation. (black 16GB)

Ideas?

you can't use that model it doesn't work the same way, either use the gtkpod from the GIT (5G will be in the list then) or use a diffrent application maybe somthing like rhythembox and manually change the model number in the sysinfo file to match the model number I listed above.

Okiura

---

### Post by Okiura on 2009-12-31
> **fakaralama said:**
> Hi all, thanx for all your posts, I'm new in the forum and I've got the same problem as everyone: a brand new blue ipod 5g nano video, but I'm not able to transfer the songs on it... 

Have you followed the advice from the previous posts? patched and compiled source then set the Firewire ID and model number correctly.


> **fakaralama said:**
> 1- Is it possible to contact gtkpod developers to know if a new version is going to be released soon (otherwise I'm thinking to change my ipod?)

You can contact them from their site, but that is most likely a question they get asked everyday, *Thinks of children in the back of the car "Are we there yet?"*

I have been following this project on their site and progress is good, I'd like to say it's not gonna be too long a wait .
But as I said before my fix is ugly fix and their doing it properly, to do that takes time

> **fakaralama said:**
> 2- If I try to use my Ipod on a Mac and then come back to Ubuntu, would there be any chances it could work there too?

Ok i'm not sure how to answer this cos i'm not sure on the question, but if it's about whether the mac will format a 5G for mac only like the old ipod's i don't think does that, but i'll leave that for someone else to confirm.

> **fakaralama said:**
> 3- In case I decided to put Linux on my Ipod for now, would it be then possible to come back to the original settings?

I really don't think this is even a option yet for the 5G and it most likely will not be for quite some time. 

Okiura,

---

### Post by nothingspecial on 2010-01-01
This gets worse.

So I took it to a friends house and plugged it in to his macbook, restored it, updated it, then took it home.

Now it is a read only file system. I can`t edit iPod_Contol/Device/Sysinfo.

I can`t add any music, I can`t chown or chmod it. I can`t do anything.

---

### Post by rmjb on 2010-01-01
I just downloaded the latest sources from git today to try to get this to work on my wife's christmas present (I'm in the same boat as some of you) and it's still saying 0 Songs.

Now in Rhythmbox there is the category to initialise the iPod as a 5th gen Nano with camera and I do tweak the SysInfo file after initialization. However, when I copy tracks to the iPod the following is displayed on the console:

```
libitdbprep: itdb_sqlite_generate_itdbs called with file /media/IPOD/iPod_Control/iTunes/iTunesCDB and uuid 000A2700201167EC
itlp directory='/media/IPOD/iPod_Control/iTunes/iTunes Library.itlp'
*.itdb files will be stored in '/media/IPOD/iPod_Control/iTunes/iTunes Library.itlp'
[mk_Dynamic] Processing '/tmp/fileoTJlGP/Dynamic.itdb'
[mk_Dynamic] creating table structure
[mk_Dynamic] - processing 3 tracks
[mk_Dynamic] done.
[mk_Extras] Processing '/tmp/fileoTJlGP/Extras.itdb'
[mk_Extras] re-building table structure
[mk_Extras] done.
[mk_Genius] Processing '/tmp/fileoTJlGP/Genius.itdb'
[mk_Genius] re-building table structure
[mk_Genius] done.
library_persistent_id = 0x0777989f08c90816
[mk_Library] Processing '/tmp/fileoTJlGP/Library.itdb'
[mk_Library] building table structure
[mk_Library] compiling SQL statements
[mk_Library] - inserting into "version_info"
[mk_Library] - inserting into "genre_map"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'CandiPod' into "container"
library_persistent_id = 0x0777989f08c90816
device name = CandiPod
[mk_Library] - inserting into "db_info"
[mk_Library] - processing 3 tracks
[mk_Library] done.
[mk_Locations] Processing '/tmp/fileoTJlGP/Locations.itdb'
[mk_Locations] re-building table structure
[mk_Locations] Processing 3 tracks...
[mk_Locations] done.
```

This looks promising, but the iTunes Library.itlp folder stays empty so I assume no database is written to the iPod.

I hope this helps someone fix any bugs.

- rmjb

---

### Post by nothingspecial on 2010-01-01
Why didn`t I research this first.

Plugging the stupid thing into a mac will only make matters worse.

Apparently my problem is fixable but I don`t want to mess with the file system of my sons iPod.

Hopefully plugging it into a windows box will fix this problem. Time to call my brother.

---

### Post by Okiura on 2010-01-01
> **rmjb said:**
> I just downloaded the latest sources from git today to try to get this to work on my wife's christmas present (I'm in the same boat as some of you) and it's still saying 0 Songs.

Now in Rhythmbox there is the category to initialise the iPod as a 5th gen Nano with camera and I do tweak the SysInfo file after initialization. However, when I copy tracks to the iPod the following is displayed on the console:

```
libitdbprep: itdb_sqlite_generate_itdbs called with file /media/IPOD/iPod_Control/iTunes/iTunesCDB and uuid 000A2700201167EC
itlp directory='/media/IPOD/iPod_Control/iTunes/iTunes Library.itlp'
*.itdb files will be stored in '/media/IPOD/iPod_Control/iTunes/iTunes Library.itlp'
[mk_Dynamic] Processing '/tmp/fileoTJlGP/Dynamic.itdb'
[mk_Dynamic] creating table structure
[mk_Dynamic] - processing 3 tracks
[mk_Dynamic] done.
[mk_Extras] Processing '/tmp/fileoTJlGP/Extras.itdb'
[mk_Extras] re-building table structure
[mk_Extras] done.
[mk_Genius] Processing '/tmp/fileoTJlGP/Genius.itdb'
[mk_Genius] re-building table structure
[mk_Genius] done.
library_persistent_id = 0x0777989f08c90816
[mk_Library] Processing '/tmp/fileoTJlGP/Library.itdb'
[mk_Library] building table structure
[mk_Library] compiling SQL statements
[mk_Library] - inserting into "version_info"
[mk_Library] - inserting into "genre_map"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'CandiPod' into "container"
library_persistent_id = 0x0777989f08c90816
device name = CandiPod
[mk_Library] - inserting into "db_info"
[mk_Library] - processing 3 tracks
[mk_Library] done.
[mk_Locations] Processing '/tmp/fileoTJlGP/Locations.itdb'
[mk_Locations] re-building table structure
[mk_Locations] Processing 3 tracks...
[mk_Locations] done.
```

This looks promising, but the iTunes Library.itlp folder stays empty so I assume no database is written to the iPod.

I hope this helps someone fix any bugs.

- rmjb

I see your problem here you haven't patched the source correctly... Go back to my first post and add my modified files to the "src" dir of libgpod (overwrite the originals) then build and install and try again. you have none of the messages i added for debuging in that output.

Okiura,

---

### Post by hypert on 2010-01-01
I have installed itunes on ubuntu and it works well so try it. It works on Ubuntu no matter what people says

---

### Post by Okiura on 2010-01-01
> **hypert said:**
> I have installed itunes on ubuntu and it works well so try it. It works on Ubuntu no matter what people says

I've installed it too (using WINE), it was the first thing I tried :) as far as the application goes it does work well but was far as syncing goes (with the 5G) it doesn't.

Or are you using a VM?

---

### Post by stone[no] on 2010-01-01
I've also followed the various steps in the above posts without any luck.
I'm by no means a pro on gtkpod or iPods, but this are my thoughts:

1. I'm running Ubuntu 9.04
2. I've initialized my 16GB black Nano 5. Gen. in iTunes/Windows and added some songs there.
3. I see all the previously songs in gtkpod and I can add new songs.
But when I disconnect the iPod the new songs are not available.

It seems that only "./iPod_Control/iTunes/iTunesCDB.ext and "./iPod_Control/iTunes/iTunesDB" is changed by gtkpod (although the old iTunesDB is created with a 0 size).

The new "./iPod_Control/iTunes/iTunesCDB" has not been changed. This is where the actual database is stored.

There might be a resent change in the git has broken the patch/ fix that we have applied...

---

### Post by rmjb on 2010-01-01
> **Okiura said:**
> I see your problem here you haven't patched the source correctly... Go back to my first post and add my modified files to the "src" dir of libgpod (overwrite the originals) then build and install and try again. you have none of the messages i added for debuging in that output.

Okiura,

Thanks Okiura, I patched with your source files and I still get the same behaviour :( but there are a couple more lines in the output, the last part now looks like this:

```
device name = CandiPod
[mk_Library] - inserting into "db_info"
[mk_Library] - processing 2 tracks
[mk_Library] - inserting into "track_artist"
[mk_Library] - inserting into "track_artist"
[mk_Library] 3 sqlite3_step returned 19
[mk_Library] done.
[mk_Locations] Processing '/tmp/fileNo544m/Locations.itdb'
[mk_Locations] re-building table structure
[mk_Locations] Processing 2 tracks...
[mk_Locations] done.
```

- rmjb

---

### Post by Okiura on 2010-01-01
> **rmjb said:**
> Thanks Okiura, I patched with your source files and I still get the same behaviour :( but there are a couple more lines in the output, the last part now looks like this:

```
device name = CandiPod
[mk_Library] - inserting into "db_info"
[mk_Library] - processing 2 tracks
[mk_Library] - inserting into "track_artist"
[mk_Library] - inserting into "track_artist"
[mk_Library] 3 sqlite3_step returned 19
[mk_Library] done.
[mk_Locations] Processing '/tmp/fileNo544m/Locations.itdb'
[mk_Locations] re-building table structure
[mk_Locations] Processing 2 tracks...
[mk_Locations] done.
```

- rmjb

Ok, that look more like it can you now do 3 things for me,

1st post the contents of your SysInfo file found in the Device folder on the Ipod.

2nd run this command and post the output

```
 lsusb -v | grep -i Serial 
```

3rd Confirm the Size (8g or 16g) and colour of your Nano 5G

Okiura,

---

### Post by Okiura on 2010-01-01
> **'stone[no] said:**
> It seems that only "./iPod_Control/iTunes/iTunesCDB.ext and "./iPod_Control/iTunes/iTunesDB" is changed by gtkpod (although the old iTunesDB is created with a 0 size).

This is normal the 5G doesn't use this file.

> **'stone[no] said:**
> The new "./iPod_Control/iTunes/iTunesCDB" has not been changed. This is where the actual database is stored.

this isn't the database either so libgpod will not change this file either, the tracks ar now all stored in sqlite databases in the "iTunes Library.itlp" folder

> **'stone[no] said:**
> There might be a resent change in the git has broken the patch/ fix that we have applied...

this could be the case but I did provide a download link to the version I patched against, I don't know how/if my patch will work against any other version, although it should work i'd suggest patching the one on the link i provided.

Okiura,

---

### Post by enigmatycone on 2010-01-01
I removed gtkpod, rhythmbox, libgpod, etc from my Mint 8 system.  Used a Windows XP VM to 'touch'/activate the black 5g nano.  I then compiled (latest git) libgpod (using the patch provided in this post; MUCH thanks for that patch), and compiled (latest git) gtkpod using the patched libgpod.  That patched, latest git gtkpod, is able to add/remove songs, and the changes take effect on the iPod...aka it 'works'.

So many thanks to the patch maker, and all those who've put so much time/energy into this.  

To those who still haven't gotten their 5g to 'work'... The ingredients are there guys, you just gotta put 'em together right.  And 'touching' the iPod with VM Windows DOES make the difference.  In fact, some iPods are Mac, which can create a whole new set of opportunities ;)

---

### Post by poubelle on 2010-01-01
UGH.

I have re-built and installed both libgpod and gtkpod and I'm STILL not getting the 5g menu option when I run gtkpod. 

If anyone can tell me an easy way of flushing everything that pertains to libgpod and gtkpod from my system, I would be willing to try it all over one more time. I am uninstalling gtkpod using apt-get. I'm pretty computer-savvy but I am getting so confused about how and where the Git files are and how to flush gtkpod out of there. 

I initialized my iPod on Windows at work, and the music I put on it will play, but to add more, gtkpod still asks for a model number, and as I mentioned, 5g is not making it onto the list.

This has been by far the most frustrating experience of my Linux life.

---

### Post by Okiura on 2010-01-02
> **poubelle said:**
> UGH.

I have re-built and installed both libgpod and gtkpod and I'm STILL not getting the 5g menu option when I run gtkpod. 

If anyone can tell me an easy way of flushing everything that pertains to libgpod and gtkpod from my system, I would be willing to try it all over one more time. I am uninstalling gtkpod using apt-get. I'm pretty computer-savvy but I am getting so confused about how and where the Git files are and how to flush gtkpod out of there. 

I initialized my iPod on Windows at work, and the music I put on it will play, but to add more, gtkpod still asks for a model number, and as I mentioned, 5g is not making it onto the list.

This has been by far the most frustrating experience of my Linux life.

the only thing I can think of here is you built and installed gtkpod first try and cd to the the libgpod source folder (to on downloaded from the git) and run the following:

```

make clean
./autogen.sh
make
sudo make install

```

once done cd to the gtkpod folder and do the same.

However it doesn't matter too much if gtkpod isn't letting you pick the 5G you can manually set the model number in the sysinfo and use another app like Rhythembox to sync you music, To satisfy Rhythembox dependences I just installed libgpod form apt and installed over it with the version from the GIT (but this is not the best option and is the wrong way to do it) you can also use the dpkg command to force rythembox to install without dependences

Okiura,

---

### Post by vizzini on 2010-01-02
> **Okiura said:**
> Ok, that look more like it can you now do 3 things for me,

1st post the contents of your SysInfo file found in the Device folder on the Ipod.

2nd run this command and post the output

```
 lsusb -v | grep -i Serial 
```3rd Confirm the Size (8g or 16g) and colour of your Nano 5G

Okiura,

Hallo,

this is my first post in this forum. I am using Debian Sid, but I stumbled upon this thread because of my Christmas present :)

I followed the instructions in Okiura's first post and everything builds fine. But as with some others, in my case the .itdb-files won't get written back to the iPod.

Here is what I did:

(1) used iTunes to recover the iPod.
(2) mount the iPod and start gtkpod 
(3) set iPod-model to xC062 (16GB, black)
(4) checked:
```
 lsusb -v | grep -i Serial 
  iSerial                 0 
  iSerial                 1 0000:00:02.0
  iSerial                 3 000A27001EAF5F2C
  iSerial                 0 
  iSerial                 1 0000:00:02.1

```and

```
cat /media/MYPOD/iPod_Control/Device/SysInfo
ModelNumStr: xC062
FirewireGuid: 000A27001EAF5F2C
```looks good to me

(5) add a mp3-file and save changes:
```

libitdbprep: itdb_sqlite_generate_itdbs called with file /media/MYPOD/iPod_Control/iTunes/iTunesCDB and uuid 000A27001EAF5F2C
itlp directory='/media/MYPOD/iPod_Control/iTunes/iTunes Library.itlp'
*.itdb files will be stored in '/media/MYPOD/iPod_Control/iTunes/iTunes Library.itlp'
[mk_Dynamic] Processing '/tmp/filefIbU4v/Dynamic.itdb'
[mk_Dynamic] creating table structure
[mk_Dynamic] - processing 1 tracks
[mk_Dynamic] done.
[mk_Extras] Processing '/tmp/filefIbU4v/Extras.itdb'
[mk_Extras] re-building table structure
[mk_Extras] done.
[mk_Genius] Processing '/tmp/filefIbU4v/Genius.itdb'
[mk_Genius] re-building table structure
[mk_Genius] done.
library_persistent_id = 0x221cf9e7757d52d4
[mk_Library] Processing '/tmp/filefIbU4v/Library.itdb'
[mk_Library] building table structure
[mk_Library] compiling SQL statements
[mk_Library] - inserting into "version_info"
[mk_Library] - inserting into "genre_map"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'mypod' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Podcasts' into "container"
library_persistent_id = 0x221cf9e7757d52d4
device name = mypod
[mk_Library] - inserting into "db_info"
[mk_Library] - processing 1 tracks
[mk_Library] - inserting into "track_artist"
[mk_Library] done.
[mk_Locations] Processing '/tmp/filefIbU4v/Locations.itdb'
[mk_Locations] re-building table structure
[mk_Locations] Processing 1 tracks...
[mk_Locations] done.

```the mp3-file gets copied to the iPod but the database-file in 
```
/media/MYPOD/iPod_Control/iTunes/iTunes Library.itlp
```don't get updated

(6) umount the iPod -> no songs are shown on the iPod

Any ideas?

CU
Ruppi

---

### Post by stone[no] on 2010-01-02
[QUOTE=Okiura]
this could be the case but I did provide a download link to the version I patched against, I don't know how/if my patch will work against any other version, although it should work i'd suggest patching the one on the link i provided.

Okiura,[/QUOTE]

I used the latest git... I'll try your tgz now. :-)

Also, thanks for the information on Nano 5g :-)

---

### Post by mortfrog on 2010-01-02
Hi all,

First post here also, let me start by saying thanks to everyone who is working on this, I really appreciate it.  I received a nano 5G for Christmas and  followed all of the instructions in this thread. Things almost work but the iPod still shows 0 songs.  Heres what I did:

- Downloaded patch + latest libgpod + latest gtkpod
- Copied patch files
- ran ./autogen make etc
- used iTunes (on a windows box) to reset the ipod to factory defaults
- plugged the iPod in and started gtkpod
- set the iPod model xC027 (8GB, silver) (with the 5G menu item)
- checked:

```

sudo lsusb -v | grep -i Serial
  iSerial                 1 0000:00:1d.0
  iSerial                 1 0000:00:1d.1
  iSerial                 1 0000:00:1d.2
  iSerial                 1 0000:00:1d.3
  iSerial                 3 000A27001EB993EF
  iSerial                 1 0000:00:1d.7

``````

cat /media/IPOD/iPod_Control/Device/SysInfo
ModelNumStr: xC027
FirewireGuid: 000A27001EB993EF

```Then add 2 songs:

```

** (gtkpod:4080): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed
libitdbprep: itdb_sqlite_generate_itdbs called with file /media/IPOD/iPod_Control/iTunes/iTunesCDB and uuid 000A27001EB993EF
itlp directory='/media/IPOD/iPod_Control/iTunes/iTunes Library.itlp'
*.itdb files will be stored in '/media/IPOD/iPod_Control/iTunes/iTunes Library.itlp'
[mk_Dynamic] Processing '/tmp/filea2rjxN/Dynamic.itdb'
[mk_Dynamic] creating table structure
[mk_Dynamic] - processing 2 tracks
[mk_Dynamic] done.
[mk_Extras] Processing '/tmp/filea2rjxN/Extras.itdb'
[mk_Extras] re-building table structure
[mk_Extras] done.
[mk_Genius] Processing '/tmp/filea2rjxN/Genius.itdb'
[mk_Genius] re-building table structure
[mk_Genius] done.
library_persistent_id = 0x0402f8595753de1b
[mk_Library] Processing '/tmp/filea2rjxN/Library.itdb'
[mk_Library] building table structure
[mk_Library] compiling SQL statements
[mk_Library] - inserting into "version_info"
[mk_Library] - inserting into "genre_map"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'IPOD' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Podcasts' into "container"
library_persistent_id = 0x0402f8595753de1b
device name = IPOD
[mk_Library] - inserting into "db_info"
[mk_Library] - processing 2 tracks
[mk_Library] - inserting into "track_artist"
[mk_Library] - inserting into "track_artist"
[mk_Library] 3 sqlite3_step returned 19
[mk_Library] done.
[mk_Locations] Processing '/tmp/filea2rjxN/Locations.itdb'
[mk_Locations] re-building table structure
[mk_Locations] Processing 2 tracks...
[mk_Locations] done.

```Finally eject the nano and... no songs.

thoughts?

Thanks.

---

### Post by Okiura on 2010-01-02
> **vizzini said:**
> Any ideas?

CU
Ruppi


Hi,

You have done everything correct and the gtkpod out put looks as I would expect it too... almost :) every thing in the output is being done on the PC before it is coppied to the Ipod, all the databases appear to being created correctly, it's the copying to the Ipod bit is where it looks like it is failing, you should have:

```

itdbprep: copying 'Dynamic.itdb'
itdbprep: copying 'Extras.itdb'
itdbprep: copying 'Genius.itdb'
itdbprep: copying 'Library.itdb'
itdbprep: copying 'Locations.itdb'
itdbprep: copying 'Locations.itdb.cbk'

```

At the end but I don't see it in what you have posted and that ties in with what you said about the database file not being updated. My patch only changes the way the database files are created not the way they are copied so I'm not sure on this one... but I'll see what help I can be.

With the Ipod connected can you run:

```
mount | grep /media
```

Also check the /tmp/[tmp_database_dir] folder on your PC (you need to get the full name form the gtkpod output) see if the files are still there and try and manually copy them, however I don' think they will be there :(

Okiura

---

### Post by Okiura on 2010-01-02
> **mortfrog said:**
> 

thoughts?

Thanks.

Same issue as Vizzini

---

### Post by mortfrog on 2010-01-02
This is the output from mount:
```

mount | grep media
/dev/sdb1 on /media/IPOD type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```

I checked tmp and it is empty before you click save.  Then as soon as save is done again it is empty again.  I'm not sure how to grab the files during the save process before they are deleted.  

Thanks again :)

---

### Post by Okiura on 2010-01-02
> **mortfrog said:**
> This is the output from mount:
```

mount | grep media
/dev/sdb1 on /media/IPOD type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```

I checked tmp and it is empty before you click save.  Then as soon as save is done again it is empty again.  I'm not sure how to grab the files during the save process before they are deleted.  

Thanks again :)

Darn the output is as I would expect, it not a problem with the way it is mounted... i couldn't copy them b4 they were removed either was was more to check if there left behind as the're not copied to the Ipod.

can you try with a un-patched build and see if they are copied, it will show 0 songs after but it should still try and copy the databases as I never changed any of that code.

Okiura,

---

### Post by mortfrog on 2010-01-02
I tried reverting back and it still appeared that i was having the same not copying problem so I'm poking through itdb_sqlite.c now.  I just commented out the comand which removes the tmp directory, so now i have the files, but where do i copy them onto the ipod?

---

### Post by mpapakyr on 2010-01-02
> **mortfrog said:**
> I tried reverting back and it still appeared that i was having the same not copying problem so I'm poking through itdb_sqlite.c now.  I just commented out the comand which removes the tmp directory, so now i have the files, but where do i copy them onto the ipod?

You should copy them at:
<mount point>/iPod_Control/iTunes/iTunes\ Library.itlp/

I had the same problem witch others have mentioned: it didn't copy the *.itdb files back to the ipod. The cause of the problem was that firewireGuid at the SysInfo file disappeared (as expected :)) after restoring the ipod with iTunes.

You'll probably notice that the file Locations.itdb.cbk is missing from the tmp directory, which is the reason libgpod does not copy any of the files back.

---

### Post by nothingspecial on 2010-01-02
```
gtkpod: error while loading shared libraries: libgpod.so.4: cannot open shared object file: No such file or directory
```

What have I done wrong?

I have compiled the patched libgpod from the link.

I have built gtkpod - the latest version from the git repository.
```

locate libgpod
/usr/lib/libgpod.so.4
/usr/lib/libgpod.so.4.1.0
/usr/lib/hal/scripts/libgpod-callout
/usr/share/doc/libgpod-common
/usr/share/doc/libgpod4
/usr/share/hal/fdi/policy/20thirdparty/20-libgpod-sysinfo-extended.fdi
/usr/share/locale-langpack/en_GB/LC_MESSAGES/libgpod.mo
/var/lib/dpkg/info/libgpod-common.list
/var/lib/dpkg/info/libgpod-common.md5sums
/var/lib/dpkg/info/libgpod4.list
/var/lib/dpkg/info/libgpod4.md5sums
/var/lib/dpkg/info/libgpod4.postinst
/var/lib/dpkg/info/libgpod4.postrm
/var/lib/dpkg/info/libgpod4.shlibs
/var/lib/dpkg/info/libgpod4.symbols
```

---

### Post by mortfrog on 2010-01-02
> **nothingspecial said:**
> What have I done wrong?

try: 
```

cd libgpod/
sudo make uninstall
sudo make clean
./configure --prefix=/usr/
sudo make
sudo make install
```

---

### Post by rmjb on 2010-01-02
I'm in the same situation as everyone else. I have libgpod from git, I added Okiura's two files, and I even tried commenting out the line that deletes the files from /tmp so that I can copy them over manually. But even after all of that the iPod still says there's 0 Songs.

My Sysinfo file is set up correctly, with the correct firewire id and an x in front of the model number and the model number is correct as far as I know; the model number is being set automatically.

I'm not sure I'm doing this correct, but sometimes Rhythmbox just cannot modify the iPod; sometimes it comes up in Nautilus as read only, I can't create or delete files, but other times it is modifiable in Nautilus and Rhytmbox still cannot edit the iPod, it can't change it's name or add songs to it.
I have been deleting the iPod_Control folder in order to "reset" my iPod so that Rhythmbox can reinitialize it, but most times Rhythmbox crashes when it tries to initialize the iPod.

---

### Post by mortfrog on 2010-01-02
Ok, I have done some testing, and it *looks* like Locations.itdb.cbk isn't even being generated.  I *think *that the following line is where everything fails:
```

success = itdb_hash72_compute_hash_for_sha1 (itdb->device, final_sha1,
                         cbk_hash72);

```which returns "0" and causes this if statement to execute:
```

if (!success) {
    g_array_free (cbk, TRUE);
    return FALSE;
    }

```

UPDATE:
Still tracing the problem but this is what's causing the above lines to fail:
```

static struct Hash78Info *read_hash_info (const Itdb_Device *device)
{
    //code removed for clarity
    read_ok = g_file_get_contents (filename, (gchar**)&info, &len, NULL);
    //code removed for clarity
}
```

---

### Post by nothingspecial on 2010-01-02
This is doing my head in.

gtkpod will not even see my lad`s ipod now, even if I add it manually, no errors, nothing, it`s as though it`s not there.

Before I started messing, at least it saw it.

The trip to restore it on windows was 95 miles. I can`t be doing that often.

.....I told him not to buy an iPod, but he wanted the video camera......

Well, that was the whole of Saturday wasted.

---

### Post by Okiura on 2010-01-02
The cbk file is the checksum file if this is not being created then the files are not going to be to the Ipod and manually copying them won't help either. :(

I think we can rule out source problem as we are all using the same version and it works for some and not others, and we are all using the Nano 5G, so I think this is either a missing dependency that is not required to successfully compile but is need todo this finial step (The libiphone0 and dev files maybe), or a firmware issue.


Can you guys post the output of ./autogen.sh, also confirm the Firmware you are using.

Okiura,

---

### Post by rmjb on 2010-01-02
The firmware loaded is 1.0.2 PC. Here's the output of my autogen.sh:

```
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.64
checking for automake >= 1.7...
  testing automake-1.11... found 1.11
checking for libtool >= 1.4.3...
  testing libtoolize... found 2.2.6
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.22.3
checking for intltool >= 0.25...
  testing intltoolize... found 0.41.0
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
checking for gtk-doc >= 1.0...
  testing gtkdocize... found 1.11
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.ac
Running libtoolize...
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running gtkdocize...
Running aclocal-1.11...
Running autoconf...
Running autoheader...
Running automake-1.11...
Running ./configure --enable-maintainer-mode --prefix=/usr ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for ANSI C header files... (cached) yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking whether NLS is requested... yes
checking for intltool >= 0.21... 0.41.0 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.0
checking for XML::Parser... ok
checking for localtime_r... yes
checking for struct tm.tm_gmtoff... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBGPOD... yes
checking for GLIB... yes
checking for sg_ll_inquiry in -lsgutils2... no
checking for sg_ll_inquiry in -lsgutils... no
checking for inflate in -lz... yes
checking for HAL... no
checking for LIBIPHONE... no
checking for TAGLIB... no
checking for LIBXML... yes
checking for GDKPIXBUF... yes
checking for PYGOBJECT... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for catalogs to be installed...  de es fr he it ja ro sv zh_CN
checking whether to build gtk-doc documentation... no
checking for gtkdoc-check... /usr/bin/gtkdoc-check
checking whether to build python bindings... yes
checking for python... /usr/bin/python
checking whether /usr/bin/python version >= 2.1.1... yes
checking for /usr/bin/python version... 2.6
checking for /usr/bin/python platform... linux2
checking for /usr/bin/python script directory... ${prefix}/lib/python2.6/dist-packages
checking for /usr/bin/python extension module directory... ${exec_prefix}/lib/python2.6/dist-packages
checking for python development headers... found
checking for python module mutagen >= 1.8... no
checking for more warnings... yes
checking whether gcc understands -Wno-strict-aliasing... yes
checking whether gcc understands -Wno-sign-compare... yes
checking whether gcc understands -Wdeclaration-after-statement... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating bindings/Makefile
config.status: creating bindings/python/gpod.i
config.status: creating bindings/python/Makefile
config.status: creating bindings/python/examples/Makefile
config.status: creating bindings/python/tests/Makefile
config.status: creating docs/Makefile
config.status: creating docs/reference/Makefile
config.status: creating docs/reference/version.xml
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating tools/Makefile
config.status: creating tests/Makefile
config.status: creating libgpod-1.0.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

Configuration for libgpod 0.7.3GIT :
--------------------------------

 Host System Type .........: x86_64-unknown-linux-gnu
 Install path .............: /usr
 Preprocessor .............: gcc 
 Compiler .................: gcc 	-Wall 	-Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes 	-Wnested-externs -Wpointer-arith 	-Wcast-align -Wsign-compare 	-Werror -std=c89 	-g -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2   -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
 Linker ...................: gcc   -lgobject-2.0 -lglib-2.0 -lsqlite3   -lxml2   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
 Artwork support ..........: yes
 Python bindings ..........: no
 PyGObject support ........: yes
 iPhone/iPod Touch support.: no

 Now type 'make' to build libgpod 0.7.3GIT,
 and then 'make install' for installation.

Now type `make' to compile libgpod
```

---

### Post by Okiura on 2010-01-03
@rmjb 

the only real differences between your config and mine is libiphone, taglib and sgutils. can you try a build with those packages installed.

```
sudo apt-get install libiphone-dev libtagc0-dev libsgutils2-dev
```

Okiura,

---

### Post by kswenson on 2010-01-03
The fix described in five (or six) different earlier posts works.
Here is a description of what I did:

1. Download the attachment from the post of Okuira:
  [http://ubuntuforums.org/attachment.php?attachmentid=141417&d=1261970748](http://ubuntuforums.org/attachment.php?attachmentid=141417&d=1261970748)

1a. Unpack the zipfile:
  tar -xzf NanoG5Fix.tar.gz

2. install required packages:
sudo apt-get install build-essential libsqlite3-dev libsqlite3-0 autoconf flex gettext libglib2.0-dev libgtk2.0-dev libglade2-dev libid3tag0-dev libxml-parser-perl pkg-config automake gcc git-core gtk-doc-tools

3. install recommended packages:
sudo apt-get install libcurl4-dev libflac-dev libgnomevfs2-dev libhal-dev libvorbis-dev libmp4v2-dev

4. checkout libgpod and gtkpod:
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/libgpod
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod

5. copy the files from the tar archive:
cp itdb_sqlite* libgpod/src/.

6. compile and install libgpod:
cd libgpod/
./autogen.sh
make
sudo make install

7. remove the old gtkpod if it's installed:
sudo apt-get remove gtkpod

8. compile and install gtkpod:
cd ../gtkpod/
./autogen.sh
make
sudo make install

9. modify the files installed by the package libgpod4 so that the newly installed libgpod is used:
cd /usr/lib
sudo rm libgpod.so.4.1.0
sudo ln -s /usr/local/lib/libgpod.so

10. fix the Sysinfo file (I'm not sure if this is necessary):
Do "sudo lsusb -v | grep -i Serial"
This should print a 16 character long string like 00A1234567891231.
Edit /media/IPOD/iPod_Control/Device/SysInfo, creating the file if it does not exist.
Add a line like this to the SysInfo file:

FirewireGuid: 0xffffffffffffffff

Replace ffffffffffffffff with the serial number you obtained in the previous step. Don't forget the 0x before the string.


11. Now plug your ipod into a windows machine so that it touches your ipod (not sure this is necessary).


12. Plug the ipod into your ubuntu installation and open gtkpod.  Choose the appropriate entry when it requests it of you.

Now you can use gtkpod and Rhythmbox to edit the contents of the ipod.
Among other issues, the artists don't show up in alphabetical order.

This will also be broken when there is an update to libgpod4.

---

### Post by reloweb on 2010-01-03
> **Okiura said:**
> @rmjb 

the only real differences between your config and mine is libiphone, taglib and sgutils. can you try a build with those packages installed.

```
sudo apt-get install libiphone-dev libtagc0-dev libsgutils2-dev
```Okiura,

Installing that packages and following instruction of kswenson it give me Error 2 when I try to compile libgpod:
```
make  all-recursive
make[1]: ingresso nella directory «/home/reloaded/libgpod»
Making all in src
make[2]: ingresso nella directory «/home/reloaded/libgpod/src»
  CC     libgpod_la-itdb_iphone.lo
itdb_iphone.c:27:32: error: libiphone/lockdown.h: Nessun file o directory
itdb_iphone.c:28:27: error: libiphone/afc.h: Nessun file o directory
itdb_iphone.c:29:42: error: libiphone/notification_proxy.h: Nessun file o directory
itdb_iphone.c:33: error: expected specifier-qualifier-list before &#8216;afc_client_t&#8217;
itdb_iphone.c:45: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;lockdownd_client_t&#8217;
itdb_iphone.c: In function &#8216;itdb_iphone_post_notification&#8217;:
itdb_iphone.c:48: error: &#8216;np_client_t&#8217; undeclared (first use in this function)
itdb_iphone.c:48: error: (Each undeclared identifier is reported only once
itdb_iphone.c:48: error: for each function it appears in.)
itdb_iphone.c:48: error: expected &#8216;;&#8217; before &#8216;np&#8217;
cc1: warnings being treated as errors
itdb_iphone.c:49: error: ISO C90 forbids mixed declarations and code
itdb_iphone.c:51: error: implicit declaration of function &#8216;lockdownd_start_service&#8217;
itdb_iphone.c:51: error: nested extern declaration of &#8216;lockdownd_start_service&#8217;
itdb_iphone.c:51: error: &#8216;client&#8217; undeclared (first use in this function)
itdb_iphone.c:57: error: implicit declaration of function &#8216;np_client_new&#8217;
itdb_iphone.c:57: error: nested extern declaration of &#8216;np_client_new&#8217;
itdb_iphone.c:57: error: &#8216;np&#8217; undeclared (first use in this function)
itdb_iphone.c:63: error: implicit declaration of function &#8216;np_post_notification&#8217;
itdb_iphone.c:63: error: nested extern declaration of &#8216;np_post_notification&#8217;
itdb_iphone.c:65: error: implicit declaration of function &#8216;np_client_free&#8217;
itdb_iphone.c:65: error: nested extern declaration of &#8216;np_client_free&#8217;
itdb_iphone.c: In function &#8216;itdb_iphone_start_sync&#8217;:
itdb_iphone.c:79: error: &#8216;lockdownd_client_t&#8217; undeclared (first use in this function)
itdb_iphone.c:79: error: expected &#8216;;&#8217; before &#8216;client&#8217;
itdb_iphone.c:80: error: ISO C90 forbids mixed declarations and code
itdb_iphone.c:98: error: implicit declaration of function &#8216;iphone_get_device_by_uuid&#8217;
itdb_iphone.c:98: error: nested extern declaration of &#8216;iphone_get_device_by_uuid&#8217;
itdb_iphone.c:105: error: &#8216;LOCKDOWN_E_SUCCESS&#8217; undeclared (first use in this function)
itdb_iphone.c:105: error: implicit declaration of function &#8216;lockdownd_client_new&#8217;
itdb_iphone.c:105: error: nested extern declaration of &#8216;lockdownd_client_new&#8217;
itdb_iphone.c:105: error: &#8216;client&#8217; undeclared (first use in this function)
itdb_iphone.c:117: error: implicit declaration of function &#8216;afc_client_new&#8217;
itdb_iphone.c:117: error: nested extern declaration of &#8216;afc_client_new&#8217;
itdb_iphone.c:117: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:118: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:124: error: too many arguments to function &#8216;itdb_iphone_post_notification&#8217;
itdb_iphone.c:133: error: implicit declaration of function &#8216;afc_file_open&#8217;
itdb_iphone.c:133: error: nested extern declaration of &#8216;afc_file_open&#8217;
itdb_iphone.c:133: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:133: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;lockfile&#8217;
itdb_iphone.c:135: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;lockfile&#8217;
itdb_iphone.c:141: error: too many arguments to function &#8216;itdb_iphone_post_notification&#8217;
itdb_iphone.c:150: error: implicit declaration of function &#8216;afc_file_lock&#8217;
itdb_iphone.c:150: error: nested extern declaration of &#8216;afc_file_lock&#8217;
itdb_iphone.c:150: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:150: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;lockfile&#8217;
itdb_iphone.c:150: error: &#8216;AFC_LOCK_EX&#8217; undeclared (first use in this function)
itdb_iphone.c:151: error: &#8216;AFC_E_SUCCESS&#8217; undeclared (first use in this function)
itdb_iphone.c:153: error: &#8216;AFC_E_OP_WOULD_BLOCK&#8217; undeclared (first use in this function)
itdb_iphone.c:168: error: too many arguments to function &#8216;itdb_iphone_post_notification&#8217;
itdb_iphone.c:175: error: implicit declaration of function &#8216;lockdownd_client_free&#8217;
itdb_iphone.c:175: error: nested extern declaration of &#8216;lockdownd_client_free&#8217;
itdb_iphone.c:184: error: too many arguments to function &#8216;itdb_iphone_post_notification&#8217;
itdb_iphone.c:189: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:190: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;lockfile&#8217;
itdb_iphone.c:191: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:191: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;lockfile&#8217;
itdb_iphone.c:191: error: &#8216;AFC_LOCK_UN&#8217; undeclared (first use in this function)
itdb_iphone.c:192: error: implicit declaration of function &#8216;afc_file_close&#8217;
itdb_iphone.c:192: error: nested extern declaration of &#8216;afc_file_close&#8217;
itdb_iphone.c:192: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:192: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;lockfile&#8217;
itdb_iphone.c:193: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;lockfile&#8217;
itdb_iphone.c:195: error: implicit declaration of function &#8216;afc_client_free&#8217;
itdb_iphone.c:195: error: nested extern declaration of &#8216;afc_client_free&#8217;
itdb_iphone.c:195: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:196: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:199: error: implicit declaration of function &#8216;iphone_device_free&#8217;
itdb_iphone.c:199: error: nested extern declaration of &#8216;iphone_device_free&#8217;
itdb_iphone.c: In function &#8216;itdb_iphone_stop_sync&#8217;:
itdb_iphone.c:218: error: &#8216;lockdownd_client_t&#8217; undeclared (first use in this function)
itdb_iphone.c:218: error: expected &#8216;;&#8217; before &#8216;client&#8217;
itdb_iphone.c:219: error: ISO C90 forbids mixed declarations and code
itdb_iphone.c:228: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:232: error: implicit declaration of function &#8216;afc_remove_path&#8217;
itdb_iphone.c:232: error: nested extern declaration of &#8216;afc_remove_path&#8217;
itdb_iphone.c:232: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:236: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:239: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;lockfile&#8217;
itdb_iphone.c:240: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:240: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;lockfile&#8217;
itdb_iphone.c:240: error: &#8216;AFC_LOCK_UN&#8217; undeclared (first use in this function)
itdb_iphone.c:241: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:241: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;lockfile&#8217;
itdb_iphone.c:242: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;lockfile&#8217;
itdb_iphone.c:246: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:247: error: &#8216;struct itdbprep_int&#8217; has no member named &#8216;afc&#8217;
itdb_iphone.c:250: error: &#8216;LOCKDOWN_E_SUCCESS&#8217; undeclared (first use in this function)
itdb_iphone.c:250: error: &#8216;client&#8217; undeclared (first use in this function)
itdb_iphone.c:255: error: too many arguments to function &#8216;itdb_iphone_post_notification&#8217;
make[2]: *** [libgpod_la-itdb_iphone.lo] Errore 1
make[2]: uscita dalla directory «/home/reloaded/libgpod/src»
make[1]: *** [all-recursive] Errore 1
make[1]: uscita dalla directory «/home/reloaded/libgpod»
make: *** [all] Errore 2
```

EDIT: Removing that packages I can compile libgpod, but when I start gtkpod and save the playlist it give me this error:
```
Backup Database could not be found so backing up database to /home/reloaded/.gtkpod/backupDB_xC031
```

I have Ipod nano 5G 8GB Black (xC031).

This is my Sysinfo:
```
ModelNumStr: xC031
FirewireGuid: 0x000A27001EB77DEA
```

This is my output for "sudo lsusb -v | grep -i Serial"

```
  iSerial                 3 TH267230C61J
  iSerial                 1 0000:00:1d.3
  iSerial                 3 000A27001EB77DEA
  iSerial                 3 058F312D81B
  iSerial                 1 0000:00:1d.7
  iSerial                 0 
  iSerial                 0 
  iSerial                 1 0000:00:1d.2
  iSerial                 1 0000:00:1d.1
  iSerial                 1 0000:00:1d.0

```

---

### Post by jamesarbrown on 2010-01-03
Hi,

Does anyone know 100% if libiphone-dev is needed or not?

Have been trying this morning with the git as is, and with patch applied. Ipod reads ok, but no writes to itlb databases.

Checksum in Sysinfo is in place and correct.

My system is not Ubuntu, but this thread is most active and should not be any different to f11 in this aspect.

when I try and compile with libiphone-dev 0.9.3 libgpod will not compile module (think it was) ipod-lockdown.c

If I can decide if libiphone is 100% needed I will persue its compilation.

James

```
[root@jblaptop libgpod]# ./autogen.sh --target=x86_64 --prefix=/usr --libdir=/usr/lib64
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.63
checking for automake >= 1.7...
  testing automake-1.11... found 1.11
checking for libtool >= 1.4.3...
  testing libtoolize... found 1.5.26
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.18.4
checking for intltool >= 0.25...
  testing intltoolize... found 0.40.5
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.23
checking for gtk-doc >= 1.0...
  testing gtkdocize... found 1.10
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.ac
Running libtoolize...
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running gtkdocize...
Running aclocal-1.11...
Running autoconf...
Running autoheader...
Running automake-1.11...
Running ./configure --enable-maintainer-mode --enable-gtk-doc --target=x86_64 --prefix=/usr --libdir=/usr/lib64 ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a sed that does not truncate output... /bin/sed
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for ANSI C header files... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1966080
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking whether NLS is requested... yes
checking for intltool >= 0.21... 0.40.5 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for localtime_r... yes
checking for struct tm.tm_gmtoff... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBGPOD... yes
checking for GLIB... yes
checking for sg_ll_inquiry in -lsgutils2... yes
checking for inflate in -lz... yes
checking for HAL... yes
checking for LIBIPHONE... no
checking for TAGLIB... yes
checking for LIBXML... yes
checking for GDKPIXBUF... yes
checking for PYGOBJECT... no
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for catalogs to be installed...  de es fr he it ja ro sv zh_CN
checking whether to build gtk-doc documentation... yes
checking for gtkdoc-check... /usr/bin/gtkdoc-check
checking whether to build python bindings... yes
checking for python... /usr/bin/python
checking whether /usr/bin/python version >= 2.1.1... yes
checking for /usr/bin/python version... 2.5
checking for /usr/bin/python platform... linux2
checking for /usr/bin/python script directory... ${prefix}/lib/python2.5/site-packages
checking for /usr/bin/python extension module directory... ${exec_prefix}/lib64/python2.5/site-packages
checking for python development headers... found
checking for python module mutagen >= 1.8... no
checking for more warnings... yes
checking whether gcc understands -Wno-strict-aliasing... yes
checking whether gcc understands -Wno-sign-compare... yes
checking whether gcc understands -Wdeclaration-after-statement... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating bindings/Makefile
config.status: creating bindings/python/gpod.i
config.status: creating bindings/python/Makefile
config.status: creating bindings/python/examples/Makefile
config.status: creating bindings/python/tests/Makefile
config.status: creating docs/Makefile
config.status: creating docs/reference/Makefile
config.status: creating docs/reference/version.xml
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating tools/Makefile
config.status: creating tests/Makefile
config.status: creating libgpod-1.0.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
# INTLTOOL_MAKEFILE

Configuration for libgpod 0.7.3GIT_PATCHED :
--------------------------------

 Host System Type .........: x86_64-unknown-linux-gnu
 Install path .............: /usr
 Preprocessor .............: gcc 
 Compiler .................: gcc     -Wall     -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes     -Wnested-externs -Wpointer-arith     -Wcast-align -Wsign-compare     -Werror -std=c89     -g -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -I/usr/include/glib-2.0 -I/usr/lib64/glib-2.0/include   -I/usr/include/libxml2   -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib64/glib-2.0/include  
 Linker ...................: gcc   -lgobject-2.0 -lglib-2.0 -lsqlite3   -lxml2   -lgdk_pixbuf-2.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
 Artwork support ..........: yes
 Python bindings ..........: no
 PyGObject support ........: no
 iPhone/iPod Touch support.: no

 Now type 'make' to build libgpod 0.7.3GIT_PATCHED,
 and then 'make install' for installation.

Now type `make' to compile libgpod

```

---

### Post by jamesarbrown on 2010-01-03
Ok.

Teuf (one of gtkpod developers) says the nano5g is not in the main git branch yet.... yes it appears, but it does not work for writing.

libiphone Teuf says will not be needed for the normail git (can't comment on the patch)
So Firewire id should be obtained from lsusb and manually entered into SysInfo.

I have been given a sandbox version to try and will let you know if anything comes of it.... currently can still not get to write to the itdb files.

James

---

### Post by thorne32 on 2010-01-03
I have everithing that you wrote and all went ok but it doesn't work!! 
thanks anyway

---

### Post by Okiura on 2010-01-03
libiphone should not be required for the Nano 5G (or my patch). however I think we can confirm there is a issue with libgpod copying the *.itdb to the 5G and this seems to be one of the main problems you guys are experancing atm, my suggestion to install the libiphone-dev package is purely for testing purposes as it was 1 of 3 packages I have installed and is not installed on the example of a non working build.

It seems all the builds that are failing are using 0.93 libiphone-dev the one I got from apt on Karmic was 0.94.

it would be nice if someone who is having the problem with the databases copying to try and build with iphone support (and the others mentioned in my previous post) so we rule out or confirm if one of these packages are causing us the problems.

Okiura,

---

### Post by vizzini on 2010-01-03
> **Okiura said:**
> 
It seems all the builds that are failing are using 0.93 libiphone-dev the one I got from apt on Karmic was 0.94.

it would be nice if someone who is having the problem with the databases copying to try and build with iphone support (and the others mentioned in my previous post) so we rule out or confirm if one of these packages are causing us the problems.

Okiura,

Hallo,

okay in then Debin SID repositories there is libiphone-dev with version 0.9.5. With that libgpod builds fine. Here is what autogen.sh says:
```
Configuration for libgpod 0.7.3GIT :
--------------------------------

 Host System Type .........: i686-pc-linux-gnu
 Install path .............: /usr
 Preprocessor .............: gcc 
 Compiler .................: gcc  -Wall   -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes   -Wnested-externs -Wpointer-arith  -Wcast-align -Wsign-compare   -Werror -std=c89  -g -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2   -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
 Linker ...................: gcc   -lgobject-2.0 -lglib-2.0 -lsqlite3   -lxml2   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
 Artwork support ..........: yes
 Python bindings ..........: no
 PyGObject support ........: no
 iPhone/iPod Touch support.: yes
```But unfortunately the problem still exist, no .itdb-files are written. The mk_Locations_cbk function fails  :(

---

### Post by kswenson on 2010-01-03
> **jamesarbrown said:**
> Hi,

Does anyone know 100% if libiphone-dev is needed or not?

[/CODE]

I don't have libiphone-dev installed and I'm pretty sure I never did.

---

### Post by Okiura on 2010-01-03
Ok,

going back a few post and looking at what Mortfrog posted i'd be inclined to agree with him, I don't think the the cbk file is being created and this is causing the the code to exit before the copy command is processed can anyone else confirm if the Locations.itdb.cbk file is being created? 
This is only created on a successful checksum so if this file is not being created we need to look more at why it is not been created (failing checksum) rather than why the files aren't being copied.

Okiura,

---

### Post by vizzini on 2010-01-03
Okay, I have walked my way through the source code. May be this has been wored out before, but these are my findings:

In itdb_hash72.c the function "read_hash_info" tries to open a file called "/media/MYPOD/iPod_Control/Device/HashInfo". That file does not exist on my iPod. I believe I have read somewhere, that libgpod should create this file during initialization. Does anybody know where?

CU
Ruppi

---

### Post by Okiura on 2010-01-03
> **vizzini said:**
> Okay, I have walked my way through the source code. May be this has been wored out before, but these are my findings:

In itdb_hash72.c the function "read_hash_info" tries to open a file called "/media/MYPOD/iPod_Control/Device/HashInfo". That file does not exist on my iPod. I believe I have read somewhere, that libgpod should create this file during initialization. Does anybody know where?

CU
Ruppi

Use the link below to create one and copy it in the Device directory, then try again see if it helps.

[http://ihash.marcansoft.com/]("http://ihash.marcansoft.com/")

---

### Post by reloweb on 2010-01-03
When I try to save changes gtkpod display this:
```
Backup Database could not be found so backing up database to /home/reloaded/.gtkpod/backupDB_xC031
```

Generating a HashInfo file from 
[http://ihash.marcansoft.com/](http://ihash.marcansoft.com/) gtkpod works!!!
Thanks Okiura!

---

### Post by Okiura on 2010-01-03
> **reloweb said:**
> When I try to save changes gtkpod display this:
```
Backup Database could not be found so backing up database to /home/reloaded/.gtkpod/backupDB_xC031
```


That's not a major error I get that on one of my machines but everything works ok still,i think that may be related to libiphone so you can try and build w/o as it's confirmed that package isn't needed.

> **reloweb said:**
> Generating a HashInfo file from 
[http://ihash.marcansoft.com/](http://ihash.marcansoft.com/) gtkpod works!!!
Thanks Okiura!

w00t, hopefully it works for others too, i forgot i did this, it was part of my trouble shooting when i couldn't get my patch to work (which turned out to be a mistype in the code), but i never deleted this file from my ipod though, i forgot it was there

Thanks Vizzini for reminding me about the HashInfo file too :)

Okiura,

---

### Post by vizzini on 2010-01-03
> **Okiura said:**
> 
Thanks Vizzini for reminding me about the HashInfo file too :)


Thank YOU! This did the trick! Generate a HashFile put it .../iPod_Control/Device/ and transfer works!

Unfortunately I found two issues:
(1) No transfer of cover-art (I can live with that)
(2) No correct integration of 'Compilations'

Maybe this is 'just' a sql-problem. I hope I find time to look into next week.

Again, thank you very much
Ruppi

---

### Post by Okiura on 2010-01-03
> **vizzini said:**
> Thank YOU! This did the trick! Generate a HashFile put it .../iPod_Control/Device/ and transfer works!

Unfortunately I found two issues:
(1) No transfer of cover-art (I can live with that)
(2) No correct integration of 'Compilations'

Maybe this is 'just' a sql-problem. I hope I find time to look into next week.

Again, thank you very much
Ruppi

Nice, that seems to be the fix...

Those 2 issues i'm aware of, it's because the values the Ipod looks at in the SQL tables are wrong and they need to be changed.

Also another issue is the ordering, the tracks do not display in alphabetical order this is because the ipod doesn't sort by name but a number associated with the name e.g. "Angels" would be given 100, "Crazy" would be given 200 and "Shout" would be given 300 (assuming you only had those 3 songs) atm the code assigns 100 to all songs. all these problems are being fixed in the libgpod with 5G support.

---

### Post by mortfrog on 2010-01-03
Awesome! Thanks you!! Transferring songs works!

---

### Post by thorne32 on 2010-01-04
it works!!!!! 
thanks a lot!!!!

---

### Post by nothingspecial on 2010-01-04
Why am I getting this now?

```
gtkpod: error while loading shared libraries: libgpod.so.4: cannot open shared object file: No such file or directory
```

I have followed all instructions to the letter.

```
locate libgpod

/usr/lib/libgpod.so.4
/usr/lib/libgpod.so.4.0.0
/usr/lib/hal/libgpod-callout
/usr/share/doc/libgpod-common
/usr/share/doc/libgpod4
/usr/share/hal/fdi/policy/20thirdparty/20-libgpod-sysinfo-extended.fdi
/usr/share/python-support/gpodder/gpodder/libgpodder.py
/var/lib/dpkg/info/libgpod-common.list
/var/lib/dpkg/info/libgpod-common.md5sums
/var/lib/dpkg/info/libgpod4.list
/var/lib/dpkg/info/libgpod4.md5sums
/var/lib/dpkg/info/libgpod4.postinst
/var/lib/dpkg/info/libgpod4.postrm
/var/lib/dpkg/info/libgpod4.shlibs
/var/lib/dpkg/info/libgpod4.symbols
/var/lib/python-support/python2.5/gpodder/libgpodder.py
/var/lib/python-support/python2.5/gpodder/libgpodder.pyc
/var/lib/python-support/python2.6/gpodder/libgpodder.py
/var/lib/python-support/python2.6/gpodder/libgpodder.pyc
```

---

### Post by Okiura on 2010-01-04
> **nothingspecial said:**
> Why am I getting this now?

```
gtkpod: error while loading shared libraries: libgpod.so.4: cannot open shared object file: No such file or directory
```

I have followed all instructions to the letter.

try this

```
sudo ln -s /usr/lib/libgpod.so.4* /usr/local/lib/
```

---

### Post by nothingspecial on 2010-01-04
Thanks, hlafway through trying this again at the moment.

 I take it I was supposed to remove the original libgpod4 that comes with rhythmbox. That`s the only thing I can think of that I`ve done that I don`t remember being mentioned anywhere.

---

### Post by nothingspecial on 2010-01-04
> **Okiura said:**
> try this

```
sudo ln -s /usr/lib/libgpod.so.4* /usr/local/lib/
```

Thankyou.

This didn`t work. But after using the find command, I discovered that libgpod.so.4 was actually in /usr/local/lib so that link reversed worked.

```
sudo ln -s /usr/local/lib/libgpod.so.4* /usr/lib
```

Just loading the ipod now.

One problem, my new gtkpod can`t see the music I loaded with the old one so I can`t remove it.

Any way, atleast my boy now has a useable christmas present.

Thankyou so much for your efforts in resolving this issue.

---

### Post by jamesarbrown on 2010-01-04
Thanks to Teuf of GTKPod.

Sorry this is a little rough, these are copied commands from my Fedora system, you will need to alter commands to suit your devices etc, system i386 etc etc.

This will no doubt become mainstream in due course.

ipod-system-config-extended kept complaining about sgutils, but my system had sg3utils-devel in place, I eventually found it needs libusb also.

wget [http://gitorious.org/libgpod/teuf-sandbox/archive-tarball/nano5g](http://gitorious.org/libgpod/teuf-sandbox/archive-tarball/nano5g)
mv nano5g.1 nano5g.tar.gz
gunzip nano5g.tar.gz
tar -xvf nano5g.tar
rm -rf /usr/local/bin/gtkpod
rm -rf /usr/lib64/libgpod*
rm -rf /usr/local/gtkpod*
cd libgpod-teuf-sandbox

edit configure.ac
change line
LIBGPOD_EXTRAVERSION=GIT
to LIBGPOD_EXTRAVERSION=GIT_TEUFSANDBOX (so we can check later gtkpod has picked it up and not a previous install/build)

./autogen.sh --prefix=/usr --libdir=/usr/lib64 --target=x86_64
make
make install
cd tests

check the firewire ID is set and can be read by libgpod (with ipod plugged ;))
cd tests
./test-firewire-id /mnt/IPOD
results in
FireWire ID: 000A27001ECA5B71

create the HashInfo
cd ../tools
As ROOT
./ipod-system-config-extended /dev/sdc /mnt/IPOD

cd ../..
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod
cd gtkpod
./autogen.sh --prefix=/usr --libdir=/usr/lib64 --target=x86_64

check result says
 libgpod version ......: 0.7.3GIT_TEUFSANDBOX

make
make install

gtkpod &

---

### Post by rmjb on 2010-01-05
It's finally working! I kept deleting the iPod_Control folder and that screwed up the iPod badly so I plugged it into iTunes to restore it.

When back on Ubuntu I still had to set up the SysInfo file, it was totally empty, and put in the HashInfo file. After that the iPod would still mount unwritable some times, but when it mounts writeable I can add songs and they show up on the iPod.

Finally, something works.
Thanks for all your help guys.

- rmjb

---

### Post by Kreuger on 2010-01-06
> **jamesarbrown said:**
> Thanks to Teuf of GTKPod.
Sorry this is a little rough, these are copied commands from my Fedora system, you will need to alter commands to suit your devices etc, system i386 etc etc.

When I ran autogen, it worked okay but [make failed]("http://pastebin.com/m650aaec9") for me.

---

### Post by learnincurve on 2010-01-06
Kreuger: What errors do you get when make fails? Often there is something missing that autogen/configure doesn't pick up on.

Otherwise: I followed the instructions and I think it's working, although The track I tried to transfer ended up with a different name "libgpodxxx" I think, where xxx was a number. It's my daughter's Ipod so I'm not su used to handling music/playlists. I messed around in Gtkpod, Rhythmbox and Amarok before I finally found the file on the Ipod, so not sure which app. did the trick.

For some reason I was unable to find, the  ./tools/ipod-system-config-extended executable (it wasn't built), so I just used the webpage from earlier in the thread to generate the Hashinfo file and put it manually onto the Ipod.

Thanks all for all your work on this!

---

### Post by Kreuger on 2010-01-06
> Kreuger: What errors do you get when make fails? Often there is something missing that autogen/configure doesn't pick up on.
I posted the full output on pastebin.com the link is in my last post. It doesn't seem to give me anything detailed although I dont know a lot about programming so who knows what I've missed.

---

### Post by rmjb on 2010-01-06
From your pastebin it looks like a source code error. Did you get that from git? If so you can try updating the source code, or you can download the zip file that Okiura attached earlier in this thread.

---

### Post by Kreuger on 2010-01-06
I grabbed [this]("http://gitorious.org/~teuf/libgpod/teuf-sandbox/commits/nano5g") and went from there as the wget download in the [guide]("http://ubuntuforums.org/showpost.php?p=8609782&postcount=118") jamesarbrown posted was not working.

Edit: I went through and looked for any libs I might've been missing (libiphone, swig) and now my error is a little longer.

[Link]("http://pastebin.com/m622be632")

---

### Post by BlaWiz on 2010-01-06
I've got it working halfway now ... Can upload to my nano 5g with amarok1.4 or gtkpod, but i also have to load the ipod into itunes(through virtualbox), or else i get "No Music" on my player ... (i guess its some kind of indexing problem)

Anyone know what the problem could be?

Thanks in advance :)

---

### Post by Okiura on 2010-01-07
Hi Guys

just want to clear something up as it seems it could be causing some confusion, the link/instrustion Posted to by Jamesbrown is for the 5G test branch from the libgpod developers, if you are using that version DO NOT apply may patch as it WILL NOT work and WILL break the build. 
I would recommend you try this version as it is under active development, however if it's not working for you atm you can always try my patch but remember to check back on the developers site for any updates.

If your looking to use my patch be sure to only use it against the the official git tree found on the libgpod site, i would recommend using the link from my 1st post though as that is the version I build the patch against.

To get my patch to work you need to do the following:
[LIST]
[*]Download both the source and patched files found in my first post.

[*]Extract both archives & copy the 2 files from the patch archive to the 'libgpod/scr' directory overwriting the originals.

[*]'cd' to the libgpod directory and run the following commands:```
./autogen
make
sudo make install
```

[*]Use the instructions found in the 'README.SysInfo' to set both your 'FirewireGuid' and 'ModelNumStr'.

[*]Generate a "HashInfo" file from here '[http://ihash.marcansoft.com/]("http://ihash.marcansoft.com/")' and put it in the 'Device' folder of your Ipod.

[/LIST]

This should be enough to allow you to use most applications to transfer music if you are still getting 0 tracks after following these instructions check the application your using hasn't messed up the 'SysInfo', if it's still ok be sure to read back over the previous posts the answer is most likely there some where :D 

Okiura,

---

### Post by Kreuger on 2010-01-07
I think I've found one difference. Your patch is for libgpod, I'm trying to build the latest git for gtkpod itself. I was able to build libgpod from git but my problems are with gtkpod.

---

### Post by Richard Mathie on 2010-01-07
I can confirm that with the hashinfo file it works, but rhythem box dosnt seem to be able to add stuff properly, perhaps a problem with its plugin

---

### Post by rabbit73 on 2010-01-07
I just wanted to add that I know absolutely nothing about compiling, programming or linux in general, but I'm pretty good at following directions and managed to get my wife's xmas present running with the directions in this post. Thanks to all for the hard work and saving yet another poor guy from a woman's wrath.

BTW, the only thing that seemed different for me was loading the firewire ID. I edited the sysinfo file, but when I started gtkpod and initialized it the first time (after picking the color) it added the model info and deleted the 0x from the front of the ID. Once I added it back everything was cool.

---

### Post by stone[no] on 2010-01-09
I finally have a working ipod :-)
Thanks to everyone helping to solve this problem and especially Okiura for not giving up ;-)

---

### Post by Tsubasa(IB) on 2010-01-11
I've done as Okiura say,but I have following error message when I was doing ./autogen.sh  in gtkpod-0.99.14




**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the    
`./autogen.sh' command line.                                 

processing .
Creating ./aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs                            
Copying file po/Makefile.in.in                        

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4                                                        
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.                                  
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).                                    

Making ./aclocal.m4 writable ...
Running intltoolize...          
Running aclocal  ...            
Running autoheader...           
Running automake --gnu  ...     
Running autoconf ...            
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes           
checking for a thread-safe mkdir -p... /bin/mkdir -p        
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether NLS is requested... yes
checking for intltool >= 0.33... 0.41.0 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.0
checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... yes
checking for GLIB... yes
checking for GMODULE... yes
checking for GTHREAD... yes
checking for LIBGLADE... yes
checking for LIBGPOD... no
configure: error: in `/home/tsubasa/Desktop/gtkpod-0.99.14':
configure: error: *** No package 'libgpod-1.0' found
See `config.log' for more details.
 


What I've done is get NannoG5Fix.tar.gz  and libgpod-dc09d016db68fc69f5054b5bae8c9fbf483688e2.tar.gz and put NannoG5Fix's src's files to  libgpod.
Then,I did ./autogen.sh;make;make;install in libgpod.
Next,I did as I wrote top of this message.

Would you mind teaching me what I mistook and what should I do to render IpodNano5g available for Fedora?

---

### Post by nothingspecial on 2010-01-11
I might be way off track here but I had the problem that libgpod was not where gtkpod thought it should be

Will you run

```
find /usr -name libgpod*
```

and post the output

---

### Post by Tsubasa(IB) on 2010-01-12
I did as you say.Thank you for your helping. 
I had the following massage

[root@fpc ~]# find /usr -name libgpod*
/usr/lib/hal/scripts/libgpod-callout  
/usr/local/lib/libgpod.so             
/usr/local/lib/libgpod.so.4           
/usr/local/lib/libgpod.la             
/usr/local/lib/libgpod.so.4.2.0       
/usr/local/lib/libgpod.a              
/usr/local/lib/pkgconfig/libgpod-1.0.pc
/usr/local/share/locale/sv/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/ro/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/fr/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/he/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/es/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/ja/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/de/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/zh_CN/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/it/LC_MESSAGES/libgpod.mo   
/usr/local/share/gtk-doc/html/libgpod               
/usr/local/share/gtk-doc/html/libgpod/libgpod-File-handling-functions.html
/usr/local/share/gtk-doc/html/libgpod/libgpod-Low-level-functions.html    
/usr/local/share/gtk-doc/html/libgpod/libgpod-Artwork.html                
/usr/local/share/gtk-doc/html/libgpod/libgpod.devhelp2                    
/usr/local/share/gtk-doc/html/libgpod/libgpod-The-Itdb-iTunesDB-structure.html
/usr/local/share/gtk-doc/html/libgpod/libgpod-Chapter-Data.html               
/usr/local/share/gtk-doc/html/libgpod/libgpod-Playlists.html                  
/usr/local/share/gtk-doc/html/libgpod/libgpod-Photo-database.html             
/usr/local/share/gtk-doc/html/libgpod/libgpod-Device.html                     
/usr/local/share/gtk-doc/html/libgpod/libgpod.devhelp                         
/usr/local/share/gtk-doc/html/libgpod/libgpod-Time-handling.html              
/usr/local/share/gtk-doc/html/libgpod/libgpod-Tracks.html                     
/usr/local/share/gtk-doc/html/libgpod/libgpod-Smart-Playlists.html

---

### Post by nothingspecial on 2010-01-12
Try this

```
sudo ln -s /usr/local/lib/libgpod.so.4* /usr/lib
```

Then try comiling gtkpod again

---

### Post by Tsubasa(IB) on 2010-01-13
I've gotten same message.



checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.0
checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... yes
checking for GLIB... yes
checking for GMODULE... yes
checking for GTHREAD... yes
checking for LIBGLADE... yes
checking for LIBGPOD... no
configure: error: in `/home/tsubasa/Desktop/gtkpod-0.99.14':
configure: error: *** No package 'libgpod-1.0' found
See `config.log' for more details.


and,I typed"find /usr -name libgpod*"
[root@fpc gtkpod-0.99.14]# find /usr -name libgpod*
/usr/lib/libgpod.so.4
/usr/lib/libgpod.la
/usr/lib/libgpod.so.4.2.0
/usr/lib/libgpod.a
/usr/local/lib/libgpod.so
/usr/local/lib/libgpod.so.4
/usr/local/lib/libgpod.la
/usr/local/lib/libgpod.so.4.2.0
/usr/local/lib/libgpod.a
/usr/local/lib/pkgconfig/libgpod-1.0.pc
/usr/local/share/locale/sv/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/ro/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/fr/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/he/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/es/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/ja/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/de/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/zh_CN/LC_MESSAGES/libgpod.mo
/usr/local/share/locale/it/LC_MESSAGES/libgpod.mo
/usr/local/share/gtk-doc/html/libgpod
/usr/local/share/gtk-doc/html/libgpod/libgpod-File-handling-functions.html
/usr/local/share/gtk-doc/html/libgpod/libgpod-Low-level-functions.html
/usr/local/share/gtk-doc/html/libgpod/libgpod-Artwork.html
/usr/local/share/gtk-doc/html/libgpod/libgpod.devhelp2
/usr/local/share/gtk-doc/html/libgpod/libgpod-The-Itdb-iTunesDB-structure.html
/usr/local/share/gtk-doc/html/libgpod/libgpod-Chapter-Data.html
/usr/local/share/gtk-doc/html/libgpod/libgpod-Playlists.html
/usr/local/share/gtk-doc/html/libgpod/libgpod-Photo-database.html
/usr/local/share/gtk-doc/html/libgpod/libgpod-Device.html
/usr/local/share/gtk-doc/html/libgpod/libgpod.devhelp
/usr/local/share/gtk-doc/html/libgpod/libgpod-Time-handling.html
/usr/local/share/gtk-doc/html/libgpod/libgpod-Tracks.html
/usr/local/share/gtk-doc/html/libgpod/libgpod-Smart-Playlists.html

So,there's someting wrong.

---

### Post by treeingwalker on 2010-01-13
> **THD042 said:**
> Actually, life may get easier. AFAICT, Apple has changed some of the databases
from the esoteric mh* format to an SQLite3 database. On my 8GB Nano 5G under
/media/iPod/iPod_Control/iTunes/iTunes Library.itlp I see a couple of SQLite3 databases,
where Library.itdb contains some tables:

iPod_Control/iTunes/iTunes Library.itlp$ sqlite3 Library.itdb 
SQLite version 3.4.2
Enter ".help" for instructions
sqlite> .tables
album                  db_info                store_link           
artist                 genre_map              track_artist         
avformat_info          item                   version_info         
category_map           item_to_container      video_characteristics
composer               location_kind_map      video_info           
container              podcast_info         
container_seed         store_info           

*snip*


Very interesting.  Eclipse has a database query editor, and there are JDBC drivers for SQLite.  This is very promising.  No wonder gtkpod can't deal with it.  It explains the weird error gtkpod returns when you try to load the IPod's data.

---

### Post by Tsubasa(IB) on 2010-01-14
Thanks a lot!!It works.
What I mistook is that I didn't edit libbgpod.pc in /usr/lib/pkconfig and that I didn't set Model Sum Number as  xC037.

---

### Post by Kreuger on 2010-01-14
Can any of you help me build gtkpod from git? That's where Im having trouble

---

### Post by nothingspecial on 2010-01-14
What trouble are you having, errors?

---

### Post by Kreuger on 2010-01-14
See [here]("http://pastebin.com/m650aaec9")

---

### Post by bander013 on 2010-01-16
**@Okiura** Thank's a lot! X) After reading this thread and doing some magic, I am now able to transfer music on 5g nano ipod.

As was menthioned before, all ok, except album cover art, alphabet order and compilations.

Since I am stongly interested in cover art on my ipod, maybe I can provide some help with it? Any ideas in which side I must dig for it?

PS: I used libgpod and gtkpod from dottout overlay (I am gentoo user)

---

### Post by damianusthesage on 2010-01-18
> # compile libgpod
cd libgpod/
./autogen.sh
make
sudo make install

I have tried doing this, but found a 'no makefile' after typing [make].
majordamo@majorlabour:~/libgpod$ make
make: *** No targets specified and no makefile found. Stop.

The last time I compiled anything was under Mandrake 10.0 with './configure && make && make install'

What am I doing wrong. I realise how Ubuntu has reduced the rate at which I learn, and made me unlearn important concepts, simply by making life easier. Can I really believed I haven't comiled anything in over a year?

---

### Post by nothingspecial on 2010-01-18
Did autogen.sh give any errors about missing dependencies?

You probably need  libplist-dev and libsqlite3-dev

---

### Post by fondue on 2010-01-18
with the latest version (16.01.2010 commited) i got the following error:

```
make  all-recursive
make[1]: Betrete Verzeichnis '/usr/src_f/libgpod'
Making all in src
make[2]: Betrete Verzeichnis '/usr/src_f/libgpod/src'
  CC     libgpod_la-itdb_sqlite.lo
cc1: warnings being treated as errors
itdb_sqlite.c: In function ‘run_post_process_commands’:
itdb_sqlite.c:1475: error: implicit declaration of function ‘plist_dict_get_item’
itdb_sqlite.c:1475: error: nested extern declaration of ‘plist_dict_get_item’
itdb_sqlite.c:1475: error: assignment makes pointer from integer without a cast
itdb_sqlite.c:1487: error: ‘plist_dict_iter’ undeclared (first use in this function)
itdb_sqlite.c:1487: error: (Each undeclared identifier is reported only once
itdb_sqlite.c:1487: error: for each function it appears in.)
itdb_sqlite.c:1487: error: expected ‘;’ before ‘iter’
itdb_sqlite.c:1488: error: ISO C90 forbids mixed declarations and code
itdb_sqlite.c:1493: error: assignment makes pointer from integer without a cast
itdb_sqlite.c:1494: error: assignment makes pointer from integer without a cast
itdb_sqlite.c:1506: error: implicit declaration of function ‘plist_dict_new_iter’
itdb_sqlite.c:1506: error: nested extern declaration of ‘plist_dict_new_iter’
itdb_sqlite.c:1506: error: ‘iter’ undeclared (first use in this function)
itdb_sqlite.c:1508: error: implicit declaration of function ‘plist_dict_next_item’
itdb_sqlite.c:1508: error: nested extern declaration of ‘plist_dict_next_item’
itdb_sqlite.c:1527: error: assignment makes pointer from integer without a cast
itdb_sqlite.c:1588: error: implicit declaration of function ‘plist_array_get_size’
itdb_sqlite.c:1588: error: nested extern declaration of ‘plist_array_get_size’
itdb_sqlite.c:1593: error: implicit declaration of function ‘plist_array_get_item’
itdb_sqlite.c:1593: error: nested extern declaration of ‘plist_array_get_item’
itdb_sqlite.c:1593: error: assignment makes pointer from integer without a cast
make[2]: *** [libgpod_la-itdb_sqlite.lo] Fehler 1
make[2]: Verlasse Verzeichnis '/usr/src_f/libgpod/src'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/usr/src_f/libgpod'
make: *** [all] Fehler 2
```

---

### Post by mattycoze on 2010-01-19
Feeling hopeless at this;

> **vizzini said:**
> Thank YOU! This did the trick! Generate a HashFile put it .../iPod_Control/Device/ and transfer works!

Unfortunately I found two issues:
(1) No transfer of cover-art (I can live with that)
(2) No correct integration of 'Compilations'

Maybe this is 'just' a sql-problem. I hope I find time to look into next week.

Again, thank you very much
Ruppi

I tried finding my UUID for the ipod device and it turned out to be an 8-digit one, rather a 16 digit uuid. Apparently this is because it's a FAT partition...

mattycoze@mattycoze-laptop:/dev/disk$ sudo blkid /dev/sdb1
/dev/sdb1: LABEL="MATTYCOZE'S" UUID="05AC-BA4C" TYPE="vfat" 

Someone please help :p

---

### Post by vizzini on 2010-01-20
> **mattycoze said:**
> Feeling hopeless at this;
I tried finding my UUID for the ipod device and it turned out to be an 8-digit one, rather a 16 digit uuid. Apparently this is because it's a FAT partition...
mattycoze@mattycoze-laptop:/dev/disk$ sudo blkid /dev/sdb1
/dev/sdb1: LABEL="MATTYCOZE'S" UUID="05AC-BA4C" TYPE="vfat" 


If I understand this correctly, then you have problems with generating the hash-file. With the new build of gtkpod the sysinfo-file should be created correctly, you can take the UUID from there. Maybe the leading zeros must be present and the "-" must be removed - just guessing.

CU
Ruppi

---

### Post by vizzini on 2010-01-20
Has anyone tried the new developement-version yet? It builds fine, but it seems it doesn't write the sqlite-files back. I haven't had time to look deeper into it, though.

CU
Ruppi

---

### Post by nothingspecial on 2010-01-20
> **mattycoze said:**
> Feeling hopeless at this;



I tried finding my UUID for the ipod device and it turned out to be an 8-digit one, rather a 16 digit uuid. Apparently this is because it's a FAT partition...

mattycoze@mattycoze-laptop:/dev/disk$ sudo blkid /dev/sdb1
/dev/sdb1: LABEL="MATTYCOZE'S" UUID="05AC-BA4C" TYPE="vfat" 

Someone please help :p

It`s not the uuid you need, its the firewireGuid

```
sudo lsusb -v | grep -i Serial
```

---

### Post by iga on 2010-01-20
nano 5g working just this morning, at last. 

Yesterday I got the same issue as fondue (#144).
For me it's fixed with the okiura's patch (message #32) just applied to the last devel versions availables in
[http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=summary](http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=summary)
(20 jan, libgpod snapshot)
and
[http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/website;a=summary](http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/website;a=summary)
(2009-10-19, gtkpod snapshot)

I have found in this forum all the hints for getting the nano 5g working: thanks a lot for all, specially to Okiura.

---

### Post by mattycoze on 2010-01-20
> **nothingspecial said:**
> It`s not the uuid you need, its the firewireGuid

```
sudo lsusb -v | grep -i Serial
```


hey there I tried that and this was the output;

sudo lsusb -v | grep -i Serial  
  iSerial                 1 0000:00:1a.1
  iSerial                 3 SN0001
  iSerial                 1 0000:00:1d.7
  iSerial                 3 000A27001E6E7228
  iSerial                 1 0000:00:1a.7
  iSerial                 1 0000:00:1d.0
  iSerial                 0 
  iSerial                 1 0000:00:1d.2
  iSerial                 0 
  iSerial                 1 0000:00:1d.1
  iSerial                 1 0000:00:1a.0

So i figured this would be it; 000A27001E6E7228, only because it's 16 digits (evidentially I have no idea)
* quick question; how come I need a 'firewireGuid' when I'm only connecting the ipod via a USB cable?

Generated the Hashfile, copied it into the Device directory but I still can't get gtkpod iPod manager to transfer a song to the nano video 5g.

The error message i'm getting is something like this:

Transfer of "SONG.mp3" Failed, error opening '/media/MATTYCOZE's/iPod_Control/Music/F07/libgpod700985.mp3 for writing (permission denied).

I get the same error messages for any file format I try (including .m4a) etc...

---

### Post by Kreuger on 2010-01-20
I dont know how but I was able to get it to work. However, Im having the problem that the iPod isnt showing any songs on it even though gtkpod shows it transfers.

Edit: Exaile is able to see the songs transferred but it comes up blank. I generated a hashfile and it made no difference.

---

### Post by mattycoze on 2010-01-20
Actually I don't even know whether I've may have done something wrong with the compilation of the program/patch etc.

---

### Post by tzB on 2010-01-21
> **fondue said:**
> with the latest version (16.01.2010 commited) i got the following error:
```
make  all-recursive
  ...
itdb_sqlite.c: In function &#8216;run_post_process_commands&#8217;:
itdb_sqlite.c:1475: error: implicit declaration of function &#8216;plist_dict_get_item&#8217;
itdb_sqlite.c:1475: error: nested extern declaration of &#8216;plist_dict_get_item&#8217;

```

The latest libgpod requires a newer version of libplist than that which currently ships with Karmic.  I manually downloaded and installed libplist-dev and libplist1 packages from the latest Lucid alpha and this build error was resolved.

**Edit**: Latest libgpod source now properly checks to make sure libplist >= 1.0, avoiding these cryptic error messages.

Note also that you do not need libiphone for Nano 5G.  If you don't plan to sync an iPhone or iPod Touch, you can safely configure libgpod with --without-libiphone option.  This saves a bunch more dependency hassle.

tzB

---

### Post by CharlyCanada on 2010-01-21
Hello,

I tried with success patch. The Ipod works very well and fast !

I tried to sync the IPod with rhythmbox but the ipod addon fails:
"Impossible d'activer le greffon Lecteurs portables - iPod"

I guess there is a link broken between libgpod and rhythmbox. Does somebody know why?
I tried those type of link without any success :
sudo ln -s /usr/local/lib/libgpod-0.4.0.so.0 /usr/lib/libgpod-0.4.0.so.0

Best regards and thanks so much Okiura :)

---

### Post by c901906 on 2010-01-22
Hello and a BIG thanks to Okiura. 

In addition to the kudos for Okiura, I'm using this entry as a bookmark for myself. While my Nano 5G now contains all my running tunes, the albums/artists are all out of order. I'm hoping for a solution to this. I will be back often to read additional posts.

Thanks! :D
Adam.

---

### Post by dave_didlydodo on 2010-01-22
Hi, I'm trying Okiura's method. I've got the patch and the sources of libgpod and gtkpod.  Trying to compile libgpod but after ./autogen.sh I get the following errors:

[B]checking for LIBGPOD... configure: error: Package requirements (glib-2.0 >= 2.8.0 gobject-2.0 sqlite3 libplist >= 1.0) were not met:

No package 'sqlite3' found
Requested 'libplist >= 1.0' but version of libplist is 0.12

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBGPOD_CFLAGS
and LIBGPOD_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/B]

Where do I get the latest version of libplist (tried the Ubuntu repository but it seems to the same version i have already) and sqlite3.  Help!

---

### Post by dave_didlydodo on 2010-01-22
ok, I've sorted the sqlite3 problem (looked earlier in this thread and saw that I needed libsqlite3**-dev**), but it still thinks I have an old version of libplist.

---

### Post by Kreuger on 2010-01-22
> **dave_didlydodo said:**
> ok, I've sorted the sqlite3 problem (looked earlier in this thread and saw that I needed libsqlite3**-dev**), but it still thinks I have an old version of libplist.

Im using the same version you are. Do you have libplist-dev too?

---

### Post by dave_didlydodo on 2010-01-22
9.10 Karmic

---

### Post by dave_didlydodo on 2010-01-22
..and referring to Kreuger's question - I do have the -dev version of libplist and it's version 0.12-2, which synaptic says is the most recent.

The error message thinks I have 0.12 too (good) but it wants at least V1.0. Aaaarrgh!

---

### Post by TheVoda on 2010-01-22
I tried to complie libgpod according to those advices. But after starting autogen.sh I got this error:

> checking for LIBXML... configure: error: Package requirements (libxml-2.0) were not met:

No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBXML_CFLAGS
and LIBXML_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

But I have libxml installed. How should I set up PKG_CONFIG_PATH?

> net@fermoy:~/nano/libgpod$ locate libxml
/usr/lib/libxml++-2.6.so.2
/usr/lib/libxml++-2.6.so.2.0.7
/usr/lib/libxml2.so.2
/usr/lib/libxml2.so.2.7.6
/usr/lib/libxmlparse.so.0
/usr/lib/libxmlparse.so.0.1.0
/usr/lib/libxmlrpc++.so.3
/usr/lib/libxmlrpc++.so.3.06
/usr/lib/libxmlrpc.so.3
/usr/lib/libxmlrpc.so.3.6.15
/usr/lib/libxmlrpc_abyss.so.3
/usr/lib/libxmlrpc_abyss.so.3.6.15
/usr/lib/libxmlrpc_client++.so.3
/usr/lib/libxmlrpc_client++.so.3.06
/usr/lib/libxmlrpc_client.so.3
/usr/lib/libxmlrpc_client.so.3.6.15
/usr/lib/libxmlrpc_cpp.so.3
/usr/lib/libxmlrpc_cpp.so.3.06
/usr/lib/libxmlrpc_server++.so.3
/usr/lib/libxmlrpc_server++.so.3.06
/usr/lib/libxmlrpc_server.so.3
/usr/lib/libxmlrpc_server.so.3.6.15
/usr/lib/libxmlrpc_server_abyss++.so.3
/usr/lib/libxmlrpc_server_abyss++.so.3.06
/usr/lib/libxmlrpc_server_abyss.so.3
/usr/lib/libxmlrpc_server_abyss.so.3.6.15
/usr/lib/libxmlrpc_server_cgi.so.3
/usr/lib/libxmlrpc_server_cgi.so.3.6.15
/usr/lib/libxmlrpc_util.so.3
/usr/lib/libxmlrpc_util.so.3.6.15
/usr/lib/libxmlrpc_xmlparse.so.3
/usr/lib/libxmlrpc_xmlparse.so.3.6.15
/usr/lib/libxmlrpc_xmltok.so.3
/usr/lib/libxmlrpc_xmltok.so.3.6.15
/usr/lib/libxmltok.so.0
/usr/lib/libxmltok.so.0.1.0
/usr/lib/openoffice/program/libxmlfa680li.so
/usr/lib/openoffice/program/libxmlfd680li.so
/usr/lib/openoffice/program/libxmlsec1-nss.so.1
/usr/lib/openoffice/program/libxmlsec1-nss.so.1.2.6
/usr/lib/openoffice/program/libxmlsec1.so.1
/usr/lib/openoffice/program/libxmlsec1.so.1.2.6
/usr/lib/openoffice/program/libxmlsecurity.so
/usr/lib/python-support/python-libxml2
/usr/lib/python-support/python-libxml2/python2.4
/usr/lib/python-support/python-libxml2/python2.5
/usr/lib/python-support/python-libxml2/python2.4/libxml2mod.so
/usr/lib/python-support/python-libxml2/python2.5/libxml2mod.so
/usr/lib/vlc/misc/libxml_plugin.so
/usr/lib/vmware/lib/libxml2.so.2
/usr/lib/vmware/lib/libxml2.so.2/libxml2.so.2
/usr/lib/xulrunner/components/libxmlextras.so
/usr/share/doc/libxml++2.6c2a
/usr/share/doc/libxml-parser-perl
/usr/share/doc/libxml-twig-perl
/usr/share/doc/libxml2
/usr/share/doc/libxml2-utils
/usr/share/doc/libxmlrpc-c3
/usr/share/doc/python-libxml2
/usr/share/doc/libxml++2.6c2a/NEWS.Debian.gz
/usr/share/doc/libxml++2.6c2a/changelog.Debian.gz
/usr/share/doc/libxml++2.6c2a/changelog.gz
/usr/share/doc/libxml++2.6c2a/copyright
/usr/share/doc/libxml-parser-perl/README
/usr/share/doc/libxml-parser-perl/README.Encodings
/usr/share/doc/libxml-parser-perl/changelog.Debian.gz
/usr/share/doc/libxml-parser-perl/changelog.gz
/usr/share/doc/libxml-parser-perl/copyright
/usr/share/doc/libxml-parser-perl/examples
/usr/share/doc/libxml-parser-perl/examples/REC-xml-19980210.xml.gz
/usr/share/doc/libxml-parser-perl/examples/canonical
/usr/share/doc/libxml-parser-perl/examples/canontst.xml
/usr/share/doc/libxml-parser-perl/examples/ctest.dtd
/usr/share/doc/libxml-parser-perl/examples/xmlcomments
/usr/share/doc/libxml-parser-perl/examples/xmlfilter.gz
/usr/share/doc/libxml-parser-perl/examples/xmlstats
/usr/share/doc/libxml-twig-perl/README
/usr/share/doc/libxml-twig-perl/changelog.Debian.gz
/usr/share/doc/libxml-twig-perl/copyright
/usr/share/doc/libxml2/AUTHORS
/usr/share/doc/libxml2/NEWS.gz
/usr/share/doc/libxml2/README
/usr/share/doc/libxml2/README.Debian
/usr/share/doc/libxml2/TODO.gz
/usr/share/doc/libxml2/changelog.Debian.gz
/usr/share/doc/libxml2/changelog.gz
/usr/share/doc/libxml2/copyright
/usr/share/doc/libxmlrpc-c3/changelog.Debian.gz
/usr/share/doc/libxmlrpc-c3/copyright
/usr/share/doc/python-libxml2/AUTHORS
/usr/share/doc/python-libxml2/README
/usr/share/doc/python-libxml2/README.Debian
/usr/share/doc/python-libxml2/TODO
/usr/share/doc/python-libxml2/changelog.Debian.gz
/usr/share/doc/python-libxml2/changelog.gz
/usr/share/doc/python-libxml2/copyright
/usr/share/doc/python-libxml2/examples
/usr/share/doc/python-libxml2/examples/attribs.py
/usr/share/doc/python-libxml2/examples/build.py
/usr/share/doc/python-libxml2/examples/compareNodes.py
/usr/share/doc/python-libxml2/examples/ctxterror.py
/usr/share/doc/python-libxml2/examples/cutnpaste.py
/usr/share/doc/python-libxml2/examples/dtdvalid.py
/usr/share/doc/python-libxml2/examples/error.py
/usr/share/doc/python-libxml2/examples/inbuf.py
/usr/share/doc/python-libxml2/examples/indexes.py
/usr/share/doc/python-libxml2/examples/invalid.xml
/usr/share/doc/python-libxml2/examples/nsdel.py
/usr/share/doc/python-libxml2/examples/outbuf.py
/usr/share/doc/python-libxml2/examples/push.py
/usr/share/doc/python-libxml2/examples/pushSAX.py
/usr/share/doc/python-libxml2/examples/pushSAXhtml.py
/usr/share/doc/python-libxml2/examples/reader.py
/usr/share/doc/python-libxml2/examples/reader2.py
/usr/share/doc/python-libxml2/examples/reader3.py
/usr/share/doc/python-libxml2/examples/reader4.py
/usr/share/doc/python-libxml2/examples/reader5.py
/usr/share/doc/python-libxml2/examples/reader6.py
/usr/share/doc/python-libxml2/examples/reader7.py
/usr/share/doc/python-libxml2/examples/reader8.py
/usr/share/doc/python-libxml2/examples/readererr.py
/usr/share/doc/python-libxml2/examples/readernext.py
/usr/share/doc/python-libxml2/examples/regexp.py
/usr/share/doc/python-libxml2/examples/relaxng.py
/usr/share/doc/python-libxml2/examples/resolver.py
/usr/share/doc/python-libxml2/examples/schema.py
/usr/share/doc/python-libxml2/examples/serialize.py
/usr/share/doc/python-libxml2/examples/sync.py
/usr/share/doc/python-libxml2/examples/thread2.py
/usr/share/doc/python-libxml2/examples/tst.py
/usr/share/doc/python-libxml2/examples/tst.xml
/usr/share/doc/python-libxml2/examples/tstLastError.py
/usr/share/doc/python-libxml2/examples/tstURI.py
/usr/share/doc/python-libxml2/examples/tstmem.py
/usr/share/doc/python-libxml2/examples/tstxpath.py
/usr/share/doc/python-libxml2/examples/valid.xml
/usr/share/doc/python-libxml2/examples/validDTD.py
/usr/share/doc/python-libxml2/examples/validRNG.py
/usr/share/doc/python-libxml2/examples/validSchemas.py
/usr/share/doc/python-libxml2/examples/validate.py
/usr/share/doc/python-libxml2/examples/walker.py
/usr/share/doc/python-libxml2/examples/xpath.py
/usr/share/doc/python-libxml2/examples/xpathext.py
/usr/share/doc/python-libxml2/examples/xpathret.py
/usr/share/lintian/overrides/libxmlrpc-c3
/usr/share/python-support/python-libxml2
/usr/share/python-support/python-libxml2/drv_libxml2.py
/usr/share/python-support/python-libxml2/libxml2.py
/var/lib/dpkg/info/libxml++2.6c2a.list
/var/lib/dpkg/info/libxml++2.6c2a.md5sums
/var/lib/dpkg/info/libxml++2.6c2a.postinst
/var/lib/dpkg/info/libxml++2.6c2a.postrm
/var/lib/dpkg/info/libxml++2.6c2a.shlibs
/var/lib/dpkg/info/libxml-parser-perl.list
/var/lib/dpkg/info/libxml-parser-perl.md5sums
/var/lib/dpkg/info/libxml-twig-perl.list
/var/lib/dpkg/info/libxml-twig-perl.md5sums
/var/lib/dpkg/info/libxml2-utils.list
/var/lib/dpkg/info/libxml2-utils.md5sums
/var/lib/dpkg/info/libxml2.list
/var/lib/dpkg/info/libxml2.md5sums
/var/lib/dpkg/info/libxml2.postinst
/var/lib/dpkg/info/libxml2.postrm
/var/lib/dpkg/info/libxml2.shlibs
/var/lib/dpkg/info/libxml2.symbols
/var/lib/dpkg/info/libxmlrpc-c3.list
/var/lib/dpkg/info/libxmlrpc-c3.md5sums
/var/lib/dpkg/info/libxmlrpc-c3.postinst
/var/lib/dpkg/info/libxmlrpc-c3.postrm
/var/lib/dpkg/info/libxmlrpc-c3.shlibs
/var/lib/dpkg/info/python-libxml2.list
/var/lib/dpkg/info/python-libxml2.md5sums
/var/lib/dpkg/info/python-libxml2.postinst
/var/lib/dpkg/info/python-libxml2.prerm
/var/lib/python-support/python2.5/drv_libxml2.py
/var/lib/python-support/python2.5/drv_libxml2.pyc
/var/lib/python-support/python2.5/libxml2.py
/var/lib/python-support/python2.5/libxml2.pyc
/var/lib/python-support/python2.5/libxml2mod.so


thank you in advance..

---

### Post by hshan on 2010-01-23
I temporarily enabled this ppa to download the libplist1 and libplist-dev. Compile completed for me now on karmic.

[https://launchpad.net/~pmcenery/+archive/ppa](https://launchpad.net/~pmcenery/+archive/ppa)

---

### Post by jenkinbr on 2010-01-24
> **kswenson said:**
> The fix described in five (or six) different earlier posts works.
Here is a description of what I did:

*...snip...*

ok...

So I followed the instructions as above, and ended up getting this when running gtkpod from the terminal:

```

jenkinbr@jenkinbr:/usr/lib$ gtkpod 

(gtkpod:26507): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkImageMenuItem

(gtkpod:26507): Gtk-WARNING **: Theme directory  of theme Azenis Icons has no size field


** (gtkpod:26507): WARNING **: Length of smart playlist rule field (384) not as expected. Trying to continue anyhow.


** (gtkpod:26507): WARNING **: Length of smart playlist rule field (384) not as expected. Trying to continue anyhow.


** (gtkpod:26507): WARNING **: Length of smart playlist rule field (634) not as expected. Trying to continue anyhow.


** (gtkpod:26507): WARNING **: Unknown action (33556480) in smart playlist will be ignored.


** (gtkpod:26507): WARNING **: Unknown smart rule action at 55284: 2000800. Trying to continue.


** (gtkpod:26507): WARNING **: Unknown action (33556480) in smart playlist will be ignored.


** (gtkpod:26507): WARNING **: Unknown smart rule action at 55408: 2000800. Trying to continue.


** (gtkpod:26507): WARNING **: Unknown action (2048) in smart playlist will be ignored.


** (gtkpod:26507): WARNING **: Unknown smart rule action at 56984: 800. Trying to continue.


** (gtkpod:26507): WARNING **: Unknown action (2048) in smart playlist will be ignored.


** (gtkpod:26507): WARNING **: Unknown smart rule action at 58564: 800. Trying to continue.


** (gtkpod:26507): WARNING **: Unknown action (2048) in smart playlist will be ignored.


** (gtkpod:26507): WARNING **: Unknown smart rule action at 60148: 800. Trying to continue.


** (gtkpod:26507): WARNING **: Unknown action (2048) in smart playlist will be ignored.


** (gtkpod:26507): WARNING **: Unknown smart rule action at 61738: 800. Trying to continue.


** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 33554433



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 33554433



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 33554433



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 33554433



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 33554433



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 33554433



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 33554433



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 33554433



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 33554433



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 33554433



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 33554433



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 33554433



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 33554433



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 33554433



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 33554433



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

** (gtkpod:26507): WARNING **: Unknown action type 1



** (gtkpod:26507): CRITICAL **: file itdb_playlist.c: line 473 (itdb_splr_eval): should not be reached

(gtkpod:26507): Gtk-WARNING **: Failed to parse menu bar accelerator 'Ctrl+F10'


(gtkpod:26507): Gtk-WARNING **: Failed to parse menu bar accelerator 'Ctrl+F10'


(gtkpod:26507): GLib-WARNING **: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: '/media/JENKINBR'S/iPod_Control/Music/F36/libgpod568925.mp3' could not be accessed (No such file or directory).
Segmentation fault
jenkinbr@jenkinbr:/usr/lib$ 

```

:?

---

### Post by bander013 on 2010-01-25
Not so long ago, svn version of libgbod had changed. For example, I can't compile it now X)

---

### Post by nickbnf on 2010-01-26
Christophe Fergeau recently pushed a patch to support the Nano 5G into libgpod git (see [http://gitorious.org/libgpod](http://gitorious.org/libgpod)), has somebody else tried it?

I haven't managed to make it work though, still see "0 song" on the ipod whenever I change something with gtkpod.

---

### Post by fedexnman on 2010-01-26
same story here, wife got me  ipod nano5g  for xmas,    i wish she woulda got the scandisk sansfuse it plays ogg and flac  fm/am radio, no video recording yet though. alot cheaper  too

---

### Post by george@gmsys.com on 2010-01-31
I have compiled the latest libgpod and gtkpod and I can see all the songs on the iPod Nano 5G but it is marked read only.

I can't add or delete a song.  Anyone have any clues?  This is driving me nuts now that I see others have got theirs to work.  I think this was touched with an Apple machine first if that helps.

Is there an easy was to just reinitialize the entire iPod?

Thanks

---

### Post by rmjb on 2010-01-31
I tried reinitializing the iPod many ways under Linux, but I don't think any of them every worked properly. My advice is to plug it into iTunes on Windows and let that properly reinitialize it.

---

### Post by horga_83 on 2010-02-01
What a steaming pile of dung.  My Daughter had this given to her for Christmas, not by me.  I swear I will never buy an Apple product until they smarten up.

---

### Post by nothingspecial on 2010-02-02
I just did this again on another box.

It did [SIZE="3"]_not_[/SIZE] work with the latest build of libgpod.

It did work with the build Okiura originally wrote the patch for.

You can find it linked in his post [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=8568698&postcount=32").

It also didn't work until I did

```
sudo ln -s /usr/local/lib/libgpod.so.4* /usr/lib
```

---

### Post by Kreuger on 2010-02-05
Someone please help. My girlfriend is demanding Windows for her dumb ipod and I dont want it. I need this to work :(

---

### Post by mushwars on 2010-02-05
banshee is your best bet, my brother tried them all, banshee is the only one that can sync your device.

if it ever tells you that you need to use the itunes restore utility when you get the orange and green flashing light, then you just need to reformat the device mkfs.vfat on whatever the device is like /dev/sdc 

(NOTE: I am not telling him to format his drive so dont ban me)

---

### Post by oyejorge on 2010-02-06
Has anyone had success with libgpod 0.7.90?

Just another owner of a nano 5g brick...

---

### Post by nothingspecial on 2010-02-06
I did this again 3 days ago.

Read the whole thread ;)

---

### Post by nothingspecial on 2010-02-06
Tip - use the version of libgpod linked on page 4

---

### Post by Kreuger on 2010-02-06
> banshee is your best betMade no difference.

Can I get this to work without rebuilding everything? It all works fine except the ipod showing 0 tracks. All programs (gtkpod, amarok, banshee) show files on the iPod but once it's disconnected, it's blank.

---

### Post by jaltuzarra on 2010-02-08
Hi all. thx for your helping with this issue, I've been reading the posts, but I'm just a beginner in ubuntu and I wasn't able to follow okiuras instructions, Can someone help me with simple instructions of how to do that???

Btw, I checked out gtkpod web page, and it says that the version for the nano 5g it's on the way.. but, who knows......

Does any one knows if there is someone else trying to get it done with banshee or rythmbox, or something??

---

### Post by nothingspecial on 2010-02-09
This fix will work for rhythmbox.

Which bit do you need help with?

---

### Post by jaltuzarra on 2010-02-09
well, I kind of need help with the whole procedure... :S , sorry. Like for an ubuntu beginner.

---

### Post by nothingspecial on 2010-02-10
update - see [here]("http://ubuntuforums.org/showpost.php?p=8886333&postcount=229")

---

### Post by maple03 on 2010-02-10
When I try to use howto by **nothingspecial**, I get an error while the ./autogen.sh is running:

```
checking for LIBGPOD... configure: error: Package requirements (glib-2.0 >= 2.8.0 gobject-2.0 sqlite3 libplist >= 1.0) were not met:

Requested 'libplist >= 1.0' but version of libplist is 0.12

```

What am I not doing right?

---

### Post by nothingspecial on 2010-02-10
Try ```
sudo apt-get install libplist-dev 
```

and try again.

---

### Post by maple03 on 2010-02-10
> **nothingspecial said:**
> Try ```
sudo apt-get install libplist-dev 
```

and try again.

It says:
```
libplist-dev is already the newest version.
```

---

### Post by nothingspecial on 2010-02-10
Clutching at straws here......

..... are you up to date, are you using karmic?

---

### Post by maple03 on 2010-02-10
> **nothingspecial said:**
> Clutching at straws here......

..... are you up to date, are you using karmic?
Yes, I am using karmic, and it is up to date.
libplist-dev version is 0.12-2, but they request libplist >= 1.0

---

### Post by nothingspecial on 2010-02-10
Just testing that how to now on a different install..... give me a while

---

### Post by nothingspecial on 2010-02-10
I think the problem with my how to is that I included getting the latest libgpod from git.

Remove all instances of libgpod from your home directory.

Then download from the pink here link again. The one with the nanofix file in it.

Extract it and try again.

My fault.

Have corrected the how to.

---

### Post by gshockxc on 2010-02-10
I was trying to follow your code, and I got stumped at the second step.  

```
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod
```

Here's my output:

```
fatal: could not create work tree dir 'gtkpod': Permission denied.
```

---

### Post by Kreuger on 2010-02-10
> **gshockxc said:**
> I was trying to follow your code, and I got stumped at the second step.  

```
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod
```

Here's my output:

```
fatal: could not create work tree dir 'gtkpod': Permission denied.
```
> sudo mkdir gtkpod or go into whatever directory youre using and give it general user privileges (it probably is set to root).

Edit: The guide nothingspecial posted has worked for me. Finally I can get her music on it. Thank you very much!

---

### Post by nothingspecial on 2010-02-11
> **gshockxc said:**
> I was trying to follow your code, and I got stumped at the second step.  

```
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod
```

Here's my output:

```
fatal: could not create work tree dir 'gtkpod': Permission denied.
```

Do it from your home directory.

---

### Post by gshockxc on 2010-02-11
OK, I'm lost ... or I'm just too stupid to follow.  

I went to my home directory and tried

```
/home$ git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod
```

Output: 
```
/home/gtkpod/.git: Permission denied

```

I'm not sure what I'm doing wrong.
Thanks,

---

### Post by nothingspecial on 2010-02-11
_YOUR_ home directory, not _THE_ home directory.

/home/gshockxc/ or just ~/

---

### Post by last1 on 2010-02-11
Hmm. I followed the instructions and everything installed fine, but got a few errors. I get these errors from gtkpod > 
ipod database import failed: illegal seek to offset 0 (length 4) in file '/media/OVERBOARD/ipod_Control/iTunes/iTunesDB'.'
Newly mounted ipod at 'media/OVERBOARD' could not be loaded into gtkpod.

rhythmbox shows the device but doesn't show any of the music that's on it, nor can it load tunes onto it.
 
and amarok gives me an error about it needing to initialize it, although I have already initialized it on windows > 
Media Device: could not find iTunesDB on device mounted at /media/OVERBOARD. Attempt to initialize your iPod?

Sounds like my problem's mostly with the database/initialization. It's already got music on it that I don't want to be messed with. If I tell amarok to go ahead and initialize it like it wants, will that mess up what's already on there?

---

### Post by tomfool on 2010-02-12
> **gshockxc said:**
> OK, I'm lost ... or I'm just too stupid to follow.  

I went to my home directory and tried

```
/home$ git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod
```

Output: 
```
/home/gtkpod/.git: Permission denied

```

I'm not sure what I'm doing wrong.
Thanks,
Hi to everyone!I'm trying to download gtkpod using the command up there but i don't receive any response from the server,Can anyone sends me gtkpod?Thanks

---

### Post by nothingspecial on 2010-02-12
First, try and get libgpod working and it should work with rhythmbox.

Rhythmbox and gtkpod both use libgpod.

---

### Post by tomfool on 2010-02-12
> **nothingspecial said:**
> Download libgpod and the nanofix attachment from [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=8568698&postcount=32")

Double click on both downloaded files and extract them to your home directory.

Then```


sudo apt-get install autoconf flex gettext libglib2.0-dev libgtk2.0-dev libglade2-dev libid3tag0-dev libxml-parser-perl pkg-config automake gcc git-core gtk-doc-tools libcurl4-dev libflac-dev libgnomevfs2-dev libhal-dev libvorbis-dev libmp4v2-dev build-essential libsqlite3-dev libsqlite3-0
```

```
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod
```

Copy the files in the nanofix to libgpod/src/
 ```

cp itdb_sqlite.c libgpod/src/
cp itdb_sqlite_queries.h libgpod/src/
```

One line at a time
```
cd libgpod/
./autogen.sh
make
sudo make install
```
```

cd ../gtkpod/
./autogen.sh
make
sudo make install
```

Choose your model from this [list]("http://ubuntuforums.org/showpost.php?p=8585888&postcount=58")

Then run ```
 lsusb -v | grep -i Serial
```

and take note of the 16 character firewire id of your ipod. It might be helpful if you didn`t have any other usb devices plugged in when you do that.

Then navigate in your file browser to

```
ipod/iPod_Control/Device/SysInfo
```

and make it look like this
```

ModelNumStr: xB029
FirewireGuid: 0x000A27001301221F
```

change the values for the ones you`ve just discovered. The 0x infront of the 16 character value is important.

Lastly go [[COLOR="Magenta"]here[/COLOR]]("http://ihash.marcansoft.com/")

and copy the generated file to ipod/iPod_Control/Device/ 

If you still have problems type this
```

sudo ln -s /usr/local/lib/libgpod.so.4* /usr/lib
```

That`s it.

I`ve probably made a typo so post back if something doesn`t work.

WORKS!Thanks!

---

### Post by tomfool on 2010-02-12
Does it work with Banshee?

---

### Post by nothingspecial on 2010-02-12
No, Banshee uses something else.

Devs are working on it as we speak. I don`t think any of them have this new ipod yet.

---

### Post by tomfool on 2010-02-12
That's too bad....i hope he can gets trough it!I prefer Banshee than Rhythmbox...Thanks anyway!!

---

### Post by nothingspecial on 2010-02-12
I prefer guayadeque

But it doesn`t do iPods ..........yet

I get a new version, sometimes 2 or 3 every day with improvements ;)

---

### Post by tomfool on 2010-02-12
I'll try it!does it work at 64bit?

---

### Post by nothingspecial on 2010-02-12
Yep. See [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=8772188&postcount=1") for install instructions.

Please post any support, feature requests, bugs [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1380811")

Bear in mind, this is a work in progress. That being said it is the best music player I`ve ever come across in linux. It is being very actively developed and the dev is very helpful and freindly. If you have a suggestion for improvement he will listen.

If you ever wanted to contribute to open source software this is the perfect opportunity.

Have fun and give it a good go, not just 5 minutes. You _can_ influence where this player goes.

---

### Post by tomfool on 2010-02-13
I'm using it,it's fast,but would be possible using it by gtk theme?I don't like how it looks like...

---

### Post by nothingspecial on 2010-02-13
Post in the second link of my previous post if you have a request. The developer anonbeat will reply.

---

### Post by anonbeat on 2010-02-13
> **tomfool said:**
> I'm using it,it's fast,but would be possible using it by gtk theme?I don't like how it looks like...

Can you send me an screenshot and explain what you dont like ?

Thanks

---

### Post by nothingspecial on 2010-02-13
@ tomfool

> **anonbeat said:**
> Can you send me an screenshot and explain what you dont like ?

Thanks

See? ;)

---

### Post by maple03 on 2010-02-14
The solution by **nothingspecial** worked for me too finally. Thanks :)

Though, all the artists and albums are totally unsorted and it's hard to find anything. Album covers got lost too :(

---

### Post by ZING on 2010-02-15
> **nothingspecial said:**
> Download libgpod and the nanofix attachment from [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=8568698&postcount=32")

Double click on both downloaded files and extract them to your home directory.

Then```


sudo apt-get install autoconf flex gettext libglib2.0-dev libgtk2.0-dev libglade2-dev libid3tag0-dev libxml-parser-perl pkg-config automake gcc git-core gtk-doc-tools libcurl4-dev libflac-dev libgnomevfs2-dev libhal-dev libvorbis-dev libmp4v2-dev build-essential libsqlite3-dev libsqlite3-0
```

```
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod
```

Copy the files in the nanofix to libgpod/src/
 ```

cp itdb_sqlite.c libgpod/src/
cp itdb_sqlite_queries.h libgpod/src/
```

One line at a time
```
cd libgpod/
./autogen.sh
make
sudo make install
```
```

cd ../gtkpod/
./autogen.sh
make
sudo make install
```

Choose your model from this [list]("http://ubuntuforums.org/showpost.php?p=8585888&postcount=58")

Then run ```
 lsusb -v | grep -i Serial
```

and take note of the 16 character firewire id of your ipod. It might be helpful if you didn`t have any other usb devices plugged in when you do that.

Then navigate in your file browser to

```
ipod/iPod_Control/Device/SysInfo
```

and make it look like this
```

ModelNumStr: xB029
FirewireGuid: 0x000A27001301221F
```

change the values for the ones you`ve just discovered. The 0x infront of the 16 character value is important.

Lastly go [[COLOR="Magenta"]here[/COLOR]]("http://ihash.marcansoft.com/")

and copy the generated file to ipod/iPod_Control/Device/ 

If you still have problems type this
```

sudo ln -s /usr/local/lib/libgpod.so.4* /usr/lib
```

That`s it.

I`ve probably made a typo so post back if something doesn`t work.

ok so i did all that now what? What do I open to move the songs to the ipod? If GTKPOD what settings do I select?

---

### Post by maple03 on 2010-02-15
> **ZING said:**
> ok so i did all that now what? What do I open to move the songs to the ipod? If GTKPOD what settings do I select?

I opened rhythmbox and was able to listen to the songs and transfer new to the iPod. I did not open gtkpod nor configured it in some way.

Also, when I connected my nano back to iTunes in Windows, it asked me to restore my settings. So this solution doesn't give an option for using both iTunes and gtkpod.

---

### Post by oo0juice0oo on 2010-02-20
okay so i made it just fine all the way to **lsusb -v | grep -i Serial** and i got this:
[INDENT]*can't get hub descriptor: Operation not permitted*
*cannot read device status, Operation not permitted (1)*
*can't get device qualifier: Operation not permitted*
*can't get debug descriptor: Operation not permitted*
*cannot read device status, Operation not permitted (1)*
*can't get device qualifier: Operation not permitted*
*can't get debug descriptor: Operation not permitted*
*cannot read device status, Operation not permitted (1)*
*can't get device qualifier: Operation not permitted*
*can't get debug descriptor: Operation not permitted*
*cannot read device status, Operation not permitted (1)*
*can't get hub descriptor: Operation not permitted*
*can't get device qualifier: Operation not permitted*
*can't get debug descriptor: Operation not permitted*
*cannot read device status, Operation not permitted (1)*
*can't get hub descriptor: Operation not permitted*
*cannot read device status, Operation not permitted (1)*
*can't get hub descriptor: Operation not permitted*
*cannot read device status, Operation not permitted (1)*
*can't get device qualifier: Operation not permitted*
*can't get debug descriptor: Operation not permitted*
*cannot read device status, Operation not permitted (1)*
*can't get device qualifier: Operation not permitted*
*can't get debug descriptor: Operation not permitted*
*cannot read device status, Operation not permitted (1)*
*can't get hub descriptor: Operation not permitted*
*cannot read device status, Operation not permitted (1)*
*can't get hub descriptor: Operation not permitted*
*cannot read device status, Operation not permitted (1)*
*  iSerial                 1 *
*  iSerial                 3 *
*  iSerial                 3 *
*  iSerial                 3 *
*  iSerial                 1 *
*  iSerial                 1 *
*  iSerial                 1 *
*  iSerial                 0 *
*  iSerial                 0 *
*  iSerial                 1 *
*  iSerial                 1 *


[/INDENT]when i do **lsusb -v -s 001:006** (checked it on lsusb) i get this
[INDENT]*Bus 001 Device 006: ID 05ac:1265 Apple, Inc. *
*Device Descriptor:*
*  bLength                18*
*  bDescriptorType         1*
*  bcdUSB               2.00*
*  bDeviceClass            0 (Defined at Interface level)*
*  bDeviceSubClass         0 *
*  bDeviceProtocol         0 *
*  bMaxPacketSize0        64*
*  idVendor           0x05ac Apple, Inc.*
*  idProduct          0x1265 *
*  bcdDevice            0.01*
*  iManufacturer           1 *
*  iProduct                2 *
*  iSerial                 3 *
*  bNumConfigurations      2*
*  Configuration Descriptor:*
*    bLength                 9*
*    bDescriptorType         2*
*    wTotalLength           32*
*    bNumInterfaces          1*
*    bConfigurationValue     1*
*    iConfiguration          0 *
*    bmAttributes         0xc0*
*      Self Powered*
*    MaxPower              500mA*
*    Interface Descriptor:*
*      bLength                 9*
*      bDescriptorType         4*
*      bInterfaceNumber        0*
*      bAlternateSetting       0*
*      bNumEndpoints           2*
*      bInterfaceClass         8 Mass Storage*
*      bInterfaceSubClass      6 SCSI*
*      bInterfaceProtocol     80 Bulk (Zip)*
*      iInterface              0 *
*      Endpoint Descriptor:*
*        bLength                 7*
*        bDescriptorType         5*
*        bEndpointAddress     0x83  EP 3 IN*
*        bmAttributes            2*
*          Transfer Type            Bulk*
*          Synch Type               None*
*          Usage Type               Data*
*        wMaxPacketSize     0x0200  1x 512 bytes*
*        bInterval               0*
*      Endpoint Descriptor:*
*        bLength                 7*
*        bDescriptorType         5*
*        bEndpointAddress     0x02  EP 2 OUT*
*        bmAttributes            2*
*          Transfer Type            Bulk*
*          Synch Type               None*
*          Usage Type               Data*
*        wMaxPacketSize     0x0200  1x 512 bytes*
*        bInterval               0*
*  Configuration Descriptor:*
*    bLength                 9*
*    bDescriptorType         2*
*    wTotalLength          149*
*    bNumInterfaces          3*
*    bConfigurationValue     2*
*    iConfiguration          4 *
*    bmAttributes         0xc0*
*      Self Powered*
*    MaxPower              500mA*
*    Interface Descriptor:*
*      bLength                 9*
*      bDescriptorType         4*
*      bInterfaceNumber        0*
*      bAlternateSetting       0*
*      bNumEndpoints           0*
*      bInterfaceClass         1 Audio*
*      bInterfaceSubClass      1 Control Device*
*      bInterfaceProtocol      0 *
*      iInterface              0 *
*      AudioControl Interface Descriptor:*
*        bLength                 9*
*        bDescriptorType        36*
*        bDescriptorSubtype      1 (HEADER)*
*        bcdADC               1.00*
*        wTotalLength           30*
*        bInCollection           1*
*        baInterfaceNr( 0)       1*
*      AudioControl Interface Descriptor:*
*        bLength                12*
*        bDescriptorType        36*
*        bDescriptorSubtype      2 (INPUT_TERMINAL)*
*        bTerminalID             1*
*        wTerminalType      0x0201 Microphone*
*        bAssocTerminal          2*
*        bNrChannels             2*
*        wChannelConfig     0x0003*
*          Left Front (L)*
*          Right Front (R)*
*        iChannelNames           0 *
*        iTerminal               0 *
*      AudioControl Interface Descriptor:*
*        bLength                 9*
*        bDescriptorType        36*
*        bDescriptorSubtype      3 (OUTPUT_TERMINAL)*
*        bTerminalID             2*
*        wTerminalType      0x0101 USB Streaming*
*        bAssocTerminal          1*
*        bSourceID               1*
*        iTerminal               0 *
*    Interface Descriptor:*
*      bLength                 9*
*      bDescriptorType         4*
*      bInterfaceNumber        1*
*      bAlternateSetting       0*
*      bNumEndpoints           0*
*      bInterfaceClass         1 Audio*
*      bInterfaceSubClass      2 Streaming*
*      bInterfaceProtocol      0 *
*      iInterface              0 *
*    Interface Descriptor:*
*      bLength                 9*
*      bDescriptorType         4*
*      bInterfaceNumber        1*
*      bAlternateSetting       1*
*      bNumEndpoints           1*
*      bInterfaceClass         1 Audio*
*      bInterfaceSubClass      2 Streaming*
*      bInterfaceProtocol      0 *
*      iInterface              0 *
*      AudioStreaming Interface Descriptor:*
*        bLength                 7*
*        bDescriptorType        36*
*        bDescriptorSubtype      1 (AS_GENERAL)*
*        bTerminalLink           2*
*        bDelay                  1 frames*
*        wFormatTag              1 PCM*
*      AudioStreaming Interface Descriptor:*
*        bLength                35*
*        bDescriptorType        36*
*        bDescriptorSubtype      2 (FORMAT_TYPE)*
*        bFormatType             1 (FORMAT_TYPE_I)*
*        bNrChannels             2*
*        bSubframeSize           2*
*        bBitResolution         16*
*        bSamFreqType            9 Discrete*
*        tSamFreq[ 0]         8000*
*        tSamFreq[ 1]        11025*
*        tSamFreq[ 2]        12000*
*        tSamFreq[ 3]        16000*
*        tSamFreq[ 4]        22050*
*        tSamFreq[ 5]        24000*
*        tSamFreq[ 6]        32000*
*        tSamFreq[ 7]        44100*
*        tSamFreq[ 8]        48000*
*      Endpoint Descriptor:*
*        bLength                 9*
*        bDescriptorType         5*
*        bEndpointAddress     0x81  EP 1 IN*
*        bmAttributes            1*
*          Transfer Type            Isochronous*
*          Synch Type               None*
*          Usage Type               Data*
*        wMaxPacketSize     0x00c0  1x 192 bytes*
*        bInterval               4*
*        bRefresh                0*
*        bSynchAddress           0*
*        AudioControl Endpoint Descriptor:*
*          bLength                 7*
*          bDescriptorType        37*
*          bDescriptorSubtype      1 (EP_GENERAL)*
*          bmAttributes         0x01*
*            Sampling Frequency*
*          bLockDelayUnits         0 Undefined*
*          wLockDelay              0 Undefined*
*    Interface Descriptor:*
*      bLength                 9*
*      bDescriptorType         4*
*      bInterfaceNumber        2*
*      bAlternateSetting       0*
*      bNumEndpoints           1*
*      bInterfaceClass         3 Human Interface Device*
*      bInterfaceSubClass      0 No Subclass*
*      bInterfaceProtocol      0 None*
*      iInterface              0 *
*      ** UNRECOGNIZED:  09 21 01 01 00 01 22 d0 00*
*      Endpoint Descriptor:*
*        bLength                 7*
*        bDescriptorType         5*
*        bEndpointAddress     0x83  EP 3 IN*
*        bmAttributes            3*
*          Transfer Type            Interrupt*
*          Synch Type               None*
*          Usage Type               Data*
*        wMaxPacketSize     0x0040  1x 64 bytes*
*        bInterval               1*
*can't get device qualifier: Operation not permitted*
*can't get debug descriptor: Operation not permitted*
*cannot read device status, Operation not permitted (1)*
[/INDENT]**lsusb** gives
[INDENT][I]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 05ac:1265 Apple, Inc.  [/I]**(my ipod)**[I]
Bus 001 Device 004: ID 1058:1110 Western Digital Technologies, Inc. [/I]**(external hard drive)**[I]
Bus 001 Device 005: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera [/I]**(built in webcam)**
[I]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:00b0 Microsoft Corp. Digital Media Pro Keyboard 
Bus 002 Device 002: ID 1532:0101 Razer USA, Ltd [/I]**(mouse)**
[I]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/I]

[/INDENT]i don't see a firewire id any where in there.  am i missing something? any help would be freakin awesome.  not having support for my new nano is the _**ONLY**_ thing keeping a windows partition on my laptop. thanks in advance. oh yeah, i'm running 9.10 64-bit

---

### Post by oo0juice0oo on 2010-02-20
never mind about the firewire id question....after the countless hours of me toiling with this thing it figures that an hour after i post my question i found my answer.  after some random searching i found [this page]("https://help.ubuntu.com/community/PortableDevices/iPhone#Retrieving%20and%20setting%20the%20Firewire%20GUID%20%28FirewireGuid%29") which gave me this

```
sudo lsusb -v -d 05ac: | grep iSerial | awk '{print $3}' | cut -b1-16  | xargs printf "[FirewireGuid]("https://help.ubuntu.com/community/FirewireGuid"): 0x%s\n"
```ran it in terminal, it gave me my firewire id, put it in SysInfo and now i'm set.  seems to be working fully on Rythmbox,  not in Songbird tho :icon_frown:, and i could play files from the device in Amarok (i've barely touched this program so i don't know how to work any ipod stuff with it).

---

### Post by Lithium Rain on 2010-02-21
Many, many thinks to Nothingspecial! I was so happy it worked! :D I can finally move songs to my ipod in my beloved ubuntu. ^_^

One question, though: I can't remove songs from my ipod, and the songs are all jumbled up out of order. Is this a bug or simply functionality that's still being worked on? :)

EDIT: After restarting Rythmbox, I can now remove songs by sending to Trash. But the songs being mixed up in the list remains an issue. It's not a monstrous deal, just a little less convenient to find songs.

---

### Post by jkrejci@usinternet.com on 2010-02-23
So I am finding it difficult to identify which of the many steps, suggestions, ideas, etc there are that need to be followed to get gtkpod/rhythmbox working with the nano 5g. Can someone tell me which post number or direct me to where I can find the correct directions? I am on ubuntu 9.10.

---

### Post by nothingspecial on 2010-02-23
[[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=8886333&postcount=229")

I`d like to point out that that`s all I did.

---

### Post by nothingspecial on 2010-02-23
> **Lithium Rain said:**
> 
One question, though: I can't remove songs from my ipod, and the songs are all jumbled up out of order. Is this a bug or simply functionality that's still being worked on? :)


This fix is a (marvelously, fantanstic, thankyou, thankyou) hack, coded by a ubuntu user whose wife was on his back after receiving one of these for christmas.

He is not a libgpod/gtkpod dev.

The libgpod team are aware of this and a proper fix will appear soon, watch their website. For now this is all we have.

---

### Post by Lithium Rain on 2010-02-23
> **nothingspecial said:**
> This fix is a (marvelously, fantanstic, thankyou, thankyou) hack, coded by a ubuntu user whose wife was on his back after receiving one of these for christmas.

He is not a libgpod/gtkpod dev.

The libgpod team are aware of this and a proper fix will appear soon, watch their website. For now this is all we have.

Understood, I just thought maybe I did something wrong. Awesome to have it working, though! :) :)

---

### Post by Thangalin on 2010-02-25
If everyone sends Apple some feedback, maybe they'll get the message:

[http://www.apple.com/feedback/itunesapp.html]("http://www.apple.com/feedback/itunesapp.html")

---

### Post by Thangalin on 2010-02-25
I started writing a script to do all this manual action (and fix some issues I had with package dependencies), however it appears that these instructions do not work with USB?

If anyone else wants to finish the script, please repost it. Some items I'd like to see fixed:

1) Put all the .tgz files on SourceForge.
2) Make it work for USB?

---

### Post by jordy s on 2010-02-26
i tryed to do the fix that [nothingspecial]("http://ubuntuforums.org/member.php?u=491516") posted and i did all that, and still nothing is showing up on my ipod? :s
im runing ubuntu 8.10 

im not to great with computers so dumb it down for me :p

---

### Post by nickbnf on 2010-02-26
You don't need the patches anymore, nano 5g support has been integrated in the latest git version of libgpod.

So you can now just do:
```

git clone [git://gitorious.org/libgpod/libgpod.git](git://gitorious.org/libgpod/libgpod.git)
./autogen.sh
make
sudo make install

```

to install the newest version of libgpod. It is important to ensure you have the dev libraries for hal and libusb-1.0 installed so that the hal hook works.

---

### Post by nothingspecial on 2010-02-26
> **nickbnf said:**
> You don't need the patches anymore, nano 5g support has been integrated in the latest git version of libgpod.

So you can now just do:
```

git clone [git://gitorious.org/libgpod/libgpod.git](git://gitorious.org/libgpod/libgpod.git)
./autogen.sh
make
sudo make install

```

to install the newest version of libgpod. It is important to ensure you have the dev libraries for hal and libusb-1.0 installed so that the hal hook works.

Woohoo!!!!! :)

I love linux.

---

### Post by nothingspecial on 2010-02-26
> **nickbnf said:**
> You don't need the patches anymore, nano 5g support has been integrated in the latest git version of libgpod.

So you can now just do:
```

git clone [git://gitorious.org/libgpod/libgpod.git](git://gitorious.org/libgpod/libgpod.git)
./autogen.sh
make
sudo make install

```

to install the newest version of libgpod. It is important to ensure you have the dev libraries for hal and libusb-1.0 installed so that the hal hook works.

Do you still have to find the FirewireGuid and generate the hash or does the new libgpod do that?

**EDIT**

Scratch that, it does I just read the release notes

---

### Post by nickbnf on 2010-02-26
> **nothingspecial said:**
> Do you still have to find the FirewireGuid and generate the hash or does the new libgpod do that?

**EDIT**

Scratch that, it does I just read the release notes

Yes it does but as you have seen, it can be a bit tricky. You have to compile libgpod with hal and libusb support, so that it installs a hal callout that does the hash thingy everytime you plug in the iPod.
And the newest version has got a udev callout too which apparently is now favoured over the hal one, I haven't tried it though.

Oh and you don't have to use git anymore to get nano 5g support. It has been released as libgpod-0.7.90 on sourceforge. So you can just download the tarball and install it manually.

I will probably make an Ubuntu package for 0.7.90 and stick it on a PPA this weekend if I find time.

---

### Post by nothingspecial on 2010-02-26
> **nickbnf said:**
> Yes it does but as you have seen, it can be a bit tricky. You have to compile libgpod with hal and libusb support, so that it installs a hal callout that does the hash thingy everytime you plug in the iPod.
And the newest version has got a udev callout too which apparently is now favoured over the hal one, I haven't tried it though.

Oh and you don't have to use git anymore to get nano 5g support. It has been released as libgpod-0.7.90 on sourceforge. So you can just download the tarball and install it manually.

I will probably make an Ubuntu package for 0.7.90 and stick it on a PPA this weekend if I find time.

Well I haven`t tested it yet, I have a 500 gig music collection mounted over sshfs and it`s taking ages to load.

I also had to build the latest libplist as libgpod didn`t like the one in the karmic repos.

We`ll see.

---

### Post by jordy s on 2010-02-26
hm well i donno what i did lol  i followed the steps posted by "nothing. and now when i try to load my ipod i get this 

Error initialising iPod: Problem creating iPod directory or file: '/media/IPOD/iPod_Control'.

and when i try to just open it i get 

mount point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually/)


DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


anyone got a clue??

also i removed all my music that i coudnt see on my ipod and it still says its not empty ,


computer illiterate so keep it simple ;)

---

### Post by nothingspecial on 2010-02-26
> **nothingspecial said:**
> 

The libgpod team are aware of this and a proper fix will appear soon, watch their website. For now this is all we have.

Told you so :P

I can happily report that my son`s ipod is now working perfectly, in as much as he uses it - that`s music, videos, cover art (he doesn`t do podcasts or photos)

Everything is in the correct order and as it should be.

Many, many thanks to the libgpod/gtkpod team.

---

### Post by wmaddler on 2010-02-26
> **nickbnf said:**
> You don't need the patches anymore, nano 5g support has been integrated in the latest git version of libgpod.

So you can now just do:
```

git clone [git://gitorious.org/libgpod/libgpod.git](git://gitorious.org/libgpod/libgpod.git)
./autogen.sh
make
sudo make install

```

to install the newest version of libgpod. It is important to ensure you have the dev libraries for hal and libusb-1.0 installed so that the hal hook works.

Hello,
I'm trying to use latest libgpod libraries from git but despite gtkpod is able to read songs on my iPod I keep getting "0 songs" on it.

If I use patched libgpod, on the other hand, I'm able both to read and write correctly bot sort order is totally messed up, with random order instead of alphabetic.

Any clue?

Thx

---

### Post by Toommmm on 2010-02-26
Since I don't know how to work with the terminal, when I insert ./autogen.sh I get this error: bash: /autogen.sh: No such file or directory , could anybody help? 
And also "It is important to ensure you have the dev libraries for hal and libusb-1.0 installed so that the hal hook works." which ones are that?

---

### Post by nothingspecial on 2010-02-26
Hooray

Those wonderful people at libgpod/gtkpod have just released a fix for this issue.
[COLOR="Magenta"]
This is opinion not fact - if you try to reinstall rhythmbox it will try and install libgpod4 along with it which may cause issues. I am just happy my iPod works and have decided for now to leave Rhythmbox. - feel free to see what happens if you reinstall it and let me know[/COLOR].

The first thing you need to do is remove anything that may conflict with the new software.

```
sudo apt-get remove gtkpod gtkpod-aac libgpod4 libplist-dev
```

Then we have to install the dependencies of the three packages we`re going to compile along with the tools to build them.

```
sudo apt-get install autoconf cmake flex gettext libglib2.0-dev libgtk2.0-dev libglade2-dev libid3tag0-dev libxml-parser-perl pkg-config automake gcc git-core gtk-doc-tools libcurl4-dev libflac-dev libgnomevfs2-dev libhal-dev libvorbis-dev libmp4v2-dev build-essential libsqlite3-dev libsqlite3-0 libusb-dev libusb-1.0-0-dev libxml2-dev libsgutils-dev
``` 

On a side note (ie this has nothing to do with the issue) if you would like gtkpod to convert your flac files to mp3 when it loads your ipod you have to install these 2 packages

```
sudo apt-get install lame flac
```

Ok on with the issue at hand. First you need the latest version of libplist, the one in the karmic repos just doesn`t cut it -


```
git clone git://github.com/JonathanBeck/libplist.git
cd libplist
mkdir build
cd build
cmake ..
make
sudo make install
```

Then we need the answer to our prayers, the little beauty that will make our iPods work - thankyou

```

cd
git clone git://gitorious.org/libgpod/libgpod.git
cd libgpod
./autogen.sh
make
sudo make install
```

Again, I worry about apt wanting to install libgpod4 (even though you`ve just built it) when you try and install gtkpod from the repos, so we`re going to build the latest version ourselves. Maybe you can just install regular old Karmic gtkpod, it`s just that I don`t want to break something that finally works

```
cd
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod
cd gtkpod
./autogen.sh
make
sudo make install
```

That`s it.

As usual I have probably made errors -----

***Edit, see, found one already - if you have problems opening gtkpod after all this issue these 2 commands
```

sudo ln -s /usr/local/lib/libplist* /usr/lib
```

```
 sudo ln -s /usr/local/lib/libgpod.so.4* /usr/lib
```

---

### Post by jordy s on 2010-02-26
grr problem after problem lol 

okay well i followed all of "nothingspecials" fix it steps and now my ipod wont even load 
when ever i plug it into computer it just says :

mount point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually/)

or

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

is there anyway i can reset everything  on my ipod???

---

### Post by nothingspecial on 2010-02-26
I don`t know weather this will help or hinder but did you remove the libgpod and gtkpod you built in the first how to before you tried the second.

I missed your post - sorry.

I hate it when things work for me but don`t for others. I copied and pasted those instructions on to another computer to test before I posted

---

### Post by iga on 2010-02-26
I have just followed the  [nothingspecial]("http://ubuntuforums.org/member.php?u=491516") directions (except using git, I have download libgpod, gtkpod and libplist manually).
Here the ipod nano 5g is working fine as the ~2 last months (starting with Okiura's patch),
BUT now there is no need of patch, AND now it's working the artist order, the cover art ... :D

> I don`t know weather this will help or hinder but did you remove the libgpod and gtkpod you built in the first how to before you tried the second.

I have not removed the previous compiled packages libgpod/gtkpod.
But I have removed the deb packges libplist-dev, libplist0, before to compile
[http://github.com/downloads/JonathanBeck/libplist/libplist-1.2.tar.bz2](http://github.com/downloads/JonathanBeck/libplist/libplist-1.2.tar.bz2)
I don't know if it helps.

nothingspecial, libgpod/gtkpod team, JBeck/libplist ...
Thank you very mach!

---

### Post by wmaddler on 2010-02-26
Noway.
Using latest dev snapshot I can write on iPod, but keep getting 0 songs on ipod... :(

---

### Post by agravain on 2010-02-27
> **wmaddler said:**
> 
Using latest dev snapshot I can write on iPod, but keep getting 0 songs on ipod... :(
Same thing here, although the files show when I start iTunes. I then make a trivial change (delete/add/mark a file as played) and eject the ipod from within iTunes. After that I can access the files i uploaded using gtkpod earlier.

---

### Post by Tsukasa on 2010-03-01
I had the same issue as wmaddler and agravain so here's a piece of advice:

The issue both of them describe only appears when building libgpod without libusb support. iPod nano 5g *requires* the libusb support for libgpod to be present, otherwise you'll end up with the 0 songs issue.

Simply install libusb-dev packages, rebuild libgpod and you're done.

---

### Post by nothingspecial on 2010-03-01
> **Tsukasa said:**
> I had the same issue as wmaddler and agravain so here's a piece of advice:

The issue both of them describe only appears when building libgpod without libusb support. iPod nano 5g *requires* the libusb support for libgpod to be present, otherwise you'll end up with the 0 songs issue.

Simply install libusb-dev packages, rebuild libgpod and you're done.

Is there any others you need other than libusb-1.0-0-dev that I included in the how-to? I did not install libusb-dev and it works for me.

Do you need both?

---

### Post by Tsukasa on 2010-03-01
> **nothingspecial said:**
> Is there any others you need other than libusb-1.0-0-dev that I included in the how-to? I did not install libusb-dev and it works for me.

Do you need both?

Ah, sorry, I should've been a little bit more clear :) .

As far as I can tell you're suggesting some additional patches in your post. As posted a few entries before this is no longer necessary - but introduces a new requirement: libusb.

I checked out libplist, libgpod and gtkpod from the VCS and built them normally (without any additional patchwork) or getting/setting serials on the iPod afterwards.

Might be worth a note in your post for those who want to try without any patching :) .

---

### Post by nothingspecial on 2010-03-01
> **Tsukasa said:**
> Ah, sorry, I should've been a little bit more clear :) .

As far as I can tell you're suggesting some additional patches in your post. As posted a few entries before this is no longer necessary - but introduces a new requirement: libusb.

I checked out libplist, libgpod and gtkpod from the VCS and built them normally (without any additional patchwork) or getting/setting serials on the iPod afterwards.

Might be worth a note in your post for those who want to try without any patching :) .

Done

---

### Post by dwaldie on 2010-03-01
I know this wont help you but now that I have upgraded to Ubuntu 10.4 alpha 3 my ipod nano 5g works out of the box.  I can use gpodder, gtkpod, rhythmbox and everything just works.  I have not tried Amarok, it does not look good on my netbook screen.  David

---

### Post by fraser_m on 2010-03-02
I'm using Lucid, and this works with GTKpod and Rhythmbox, but is there any way to get it working with Banshee?

---

### Post by foomor on 2010-03-03
I have installed git version of libgpod, but gtkpod says that it uses 0.7.2 in about menu. Is that okay? My ipod nano 5g is arriving tomorrow and I wouldn't like to have any mess with that :-({|=

---

### Post by foomor on 2010-03-04
Got ipod. When it's plugged, gtkpod says shows warning with messages: "Extended info will not be used", "iPod Database Import Failed". Then i am adding files, saving, it is synchronizing, and shows that takes place on ipod, but there's no music on it. Any advice, please? I have never used ipod before.

---

### Post by DJGibbon on 2010-03-04
Does anyone know whether the new iFuse release for iPhone will work with the Nano? [http://maketecheasier.com/sync-iphone-with-rhythmbox/2010/02/13](http://maketecheasier.com/sync-iphone-with-rhythmbox/2010/02/13)

I'm at work so can't try this, I might get a chance to give it a go once I get home (in about 4 hours) but if anyone knows for a fact it won't work, I'll save me efforts ;)

Cheers

Phil

---

### Post by natholas on 2010-03-04
> **DJGibbon said:**
> Does anyone know whether the new iFuse release for iPhone will work with the Nano? [http://maketecheasier.com/sync-iphone-with-rhythmbox/2010/02/13](http://maketecheasier.com/sync-iphone-with-rhythmbox/2010/02/13)

I'm at work so can't try this, I might get a chance to give it a go once I get home (in about 4 hours) but if anyone knows for a fact it won't work, I'll save me efforts ;)

Cheers

Phil

i read on some forum yesterday that it mostly works

---

### Post by colini on 2010-03-07
Hi,

I'm trying to get my nano 5g working w/ gtkpod and not having much luck.  I followed nothingspecial's instructions earlier to build libplist, libgpod, and gtkpod.  In the gtkpod about box is "gtkpod 0.99.15GIT" using libgpod "0.7.90", which I think is correct.  When I copy files to the nano w/ gtkpod there are no errors but they do not appear on the ipod.  My os is ubuntu 9.10.

Two questions:
1. Several people mentioned that you have to build libgpod w/ usb and hal support.  I think I have the dev libs for both installed, but is there any way for me to know for sure that libgpod picked up both when I compiled it?

2. Assuming I get gtkpod to work (nothingspecial and others have made me believe!!), is it possible to use gtkpod to sync sometimes and itunes to sync other times?  Will they step on each other's work?  My idea is to use gtkpod day-to-day, but use itunes when syncing run data from the nike run gadget.

Thanks everyone who has contributed to the thread, which has convinced me this is close to working.  Any help really appreciated.

thanks,
Colin

---

### Post by Kreuger on 2010-03-08
I upgraded to the lucid beta 3 and now it has stopped working

---

### Post by nickbnf on 2010-03-09
> **colini said:**
> 
1. Several people mentioned that you have to build libgpod w/ usb and hal support.  I think I have the dev libs for both installed, but is there any way for me to know for sure that libgpod picked up both when I compiled it?


Check you have both libs ('i' should be displayed):
```

$ aptitude search libusb-dev libhal-dev
i   libhal-dev                                            - Hardware Abstraction Layer - development files                 
i   libusb-dev                                            - userspace USB programming library development files

```When you run ./autogen.sh, they should automatically be picked up. To be sure, look in the config.log file and search for "$PKG_CONFIG --exists --print-errors "libusb-1.0"" and "$PKG_CONFIG --exists --print-errors "hal >= 0.5 hal < 0.6"", if you don't see any error following those lines, everything is fine!

> **colini said:**
> 
2. Assuming I get gtkpod to work (nothingspecial and others have made me believe!!), is it possible to use gtkpod to sync sometimes and itunes to sync other times?  Will they step on each other's work?  My idea is to use gtkpod day-to-day, but use itunes when syncing run data from the nike run gadget.


It works for me, I use iTunes at work and amarok at home (amarok uses libgpod as well, so when you have gtkpod working, amarok should work too!).

---

### Post by nickbnf on 2010-03-09
> **Kreuger said:**
> I upgraded to the lucid beta 3 and now it has stopped working

It is supposed to work out of the box on Lucid (for nano5g at least) as it uses a recent git snapshot of libgpod-0.7.90.  So the hack described here is (theoretically) not needed anymore.  When upgrading to Lucid, it's probably better to clean everything manually installed (libgpod in /usr/local, hal callout in /usr/share/hal/fdi/policy/20thirdparty/ and /usr/lib/hal/scripts/).

The Lucid version uses a udev callout instead of the hal one (basically the same thing, just using a different mechanism), according to libgpod's devs this is now the preferred method.

I said 'supposed' because I haven't tried Lucid myself yet...

---

### Post by nickbnf on 2010-03-09
> **foomor said:**
> I have installed git version of libgpod, but gtkpod says that it uses 0.7.2 in about menu. Is that okay? My ipod nano 5g is arriving tomorrow and I wouldn't like to have any mess with that :-({|=

Nope, you should use libgpod 0.7.90 to have nano 5g support.  Download the tarball from sourceforge and compile/install it (no need for git anymore). Remember to install libusb-dev and libhal-dev first.

---

### Post by Kreuger on 2010-03-09
> When upgrading to Lucid, it's probably better to clean everything manually installed (libgpod in /usr/local, hal callout in /usr/share/hal/fdi/policy/20thirdparty/ and /usr/lib/hal/scripts/). I completely removed Gtkpod and libgpod in Synaptic as well as the libgpod stuff in /usr/local and now it works again  :)

---

### Post by reloweb on 2010-03-10
Any news for the covers and the alphabetic order?

---

### Post by squaregoldfish on 2010-03-10
> **reloweb said:**
> Any news for the covers and the alphabetic order?

If you mean are these OK on the iPod, then yes - I'm using the latest version of libgpod (0.7.91), and it's all good. Apart from the fact that all the things starting with "The" are grouped together, but that's a relatively small issue.

Steve.

---

### Post by jordy s on 2010-03-11
blah i keep getting this error when try to use ipod:

extended info will not be used.


And when i disconnect my ipod i get :

Backup database could not be found so backing up database to /home/jordy/.gtkpod/backupDB_xC062

please specify the command to be called on the 'tools' section of the preference dialog



Anyone got a clue what i can do and how i can get music on my ipod ?
keeps it simple please im new to linux :p



- kinda i side note i just noticed that my 16G ipod only has 14.4G free, and yet i have NOTHING on it.

---

### Post by Okiura on 2010-03-13
Thanks for all the "Thank you" messages i'm glad so many ppl got this working. Also thanks to Nothingspecial for supporting other ppl with getting this working too, it's ppl like that that makes the linux comunity so great.

If anyone is still using my patch you should try checking out the latest libgpod git as support for the nano 5G is now there.


Okiura

---

### Post by squaregoldfish on 2010-03-13
> **Okiura said:**
> If anyone is still using my patch you should try checking out the latest libgpod git as support for the nano 5G is now there.Okiura

Just so you know, you don't even need the latest git - the newest release (0.7.91) has the 5G support is in that.

Steve.

---

### Post by daneel6672 on 2010-03-14
I have a fifth generation ipod nano (A1320) and it certainly does not work out of the box yet.

Upgraded to lucid:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu lucid (development branch)
Release:	10.04
Codename:	lucid
```

The ipod mounts automatically, but gtkpod gives a popup error message saying

> 
Warning: The following has occurred:

Extended info will not be used.
iPod Database Import Failed.
Newly mounted iPod at '/media/IPOD' could not be loaded into gtkpod.

So I took a look at the "About" menu and it said

> gtkpod 0.99.14
Cross-platform multilingual interface to Apple's iPod™
(using libgpod 0.7.2)


To check the libraries it was actually using:

```

$ ldd /usr/bin/gtkpod
	linux-gate.so.1 =>  (0x00919000)
	libFLAC.so.8 => /usr/lib/libFLAC.so.8 (0x00e22000)
	libvorbisfile.so.3 => /usr/lib/libvorbisfile.so.3 (0x00b90000)
	libid3tag.so.0 => /usr/lib/libid3tag.so.0 (0x0067a000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00e6f000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x002ff000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00186000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x009dc000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00c25000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00763000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x001fa000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0x00206000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00c7e000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00110000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x003a2000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00153000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x0060a000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x001a2000)
	libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0x004bf000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x00d8f000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x001a7000)
	libglade-2.0.so.0 => /usr/lib/libglade-2.0.so.0 (0x001b0000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0x00789000)
	libgpod.so.4 => /usr/lib/libgpod.so.4 (0x00aa8000)
	libcurl-gnutls.so.4 => /usr/lib/libcurl-gnutls.so.4 (0x002aa000)
	libgnomevfs-2.so.0 => /usr/lib/libgnomevfs-2.so.0 (0x00418000)
	libgconf-2.so.4 => /usr/lib/libgconf-2.so.4 (0x001c8000)
	libhal.so.1 => /usr/lib/libhal.so.1 (0x00cfd000)
	libdbus-1.so.3 => /lib/libdbus-1.so.3 (0x00585000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00475000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x05a94000)
	libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0x00a2f000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x002ea000)
	libogg.so.0 => /usr/lib/libogg.so.0 (0x002ee000)
	libz.so.1 => /lib/libz.so.1 (0x00727000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x1eb5a000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x002f5000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x002f9000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x0048e000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x005be000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00494000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x0049e000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x005ce000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x005e2000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x005ea000)
	/lib/ld-linux.so.2 (0x004a2000)
	libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0x005f4000)
	libselinux.so.1 => /lib/libselinux.so.1 (0x0064a000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x0068a000)
	libdirectfb-1.2.so.0 => /usr/lib/libdirectfb-1.2.so.0 (0x0091a000)
	libfusion-1.2.so.0 => /usr/lib/libfusion-1.2.so.0 (0x00665000)
	libdirect-1.2.so.0 => /usr/lib/libdirect-1.2.so.0 (0x00dc7000)
	libpng12.so.0 => /lib/libpng12.so.0 (0x006e4000)
	libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0x005dc000)
	libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0x0066f000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00709000)
	libexpat.so.1 => /lib/libexpat.so.1 (0x009b1000)
	libpcre.so.3 => /lib/libpcre.so.3 (0x00b34000)
	libsqlite3.so.0 => /usr/lib/libsqlite3.so.0 (0x00b99000)
	libplist.so.1 => /usr/lib/libplist.so.1 (0x0073c000)
	libimobiledevice.so.0 => /usr/lib/libimobiledevice.so.0 (0x00745000)
	libidn.so.11 => /usr/lib/libidn.so.11 (0x008b3000)
	liblber-2.4.so.2 => /usr/lib/liblber-2.4.so.2 (0x008e5000)
	libldap_r-2.4.so.2 => /usr/lib/libldap_r-2.4.so.2 (0x00a58000)
	libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0x00c40000)
	libgnutls.so.26 => /usr/lib/libgnutls.so.26 (0x03119000)
	libgcrypt.so.11 => /lib/libgcrypt.so.11 (0x00d0f000)
	libdbus-glib-1.so.2 => /usr/lib/libdbus-glib-1.so.2 (0x008f2000)
	libavahi-glib.so.1 => /usr/lib/libavahi-glib.so.1 (0x00723000)
	libavahi-common.so.3 => /usr/lib/libavahi-common.so.3 (0x00991000)
	libavahi-client.so.3 => /usr/lib/libavahi-client.so.3 (0x0099d000)
	libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0x00759000)
	libORBit-2.so.0 => /usr/lib/libORBit-2.so.0 (0x0cbd2000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x0075d000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00910000)
	libtasn1.so.3 => /usr/lib/libtasn1.so.3 (0x00a02000)
	libusbmuxd.so.1 => /usr/lib/libusbmuxd.so.1 (0x00a13000)
	libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0x00b12000)
	libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0x01286000)
	libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0x00b65000)
	libcom_err.so.2 => /lib/libcom_err.so.2 (0x00dec000)
	libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0x00a19000)
	libkeyutils.so.1 => /lib/libkeyutils.so.1 (0x00dfd000)
	libgpg-error.so.0 => /lib/libgpg-error.so.0 (0x00a21000)

```

So this looks like the file installed by the libgpod library is libgpod.so.4.

```

$ dpkg-query -S /usr/lib/libgpod.so.4
libgpod4: /usr/lib/libgpod.so.4

```

 Then to check that this was the 0.7.91 version of libgpod,

```
$ dpkg -l | egrep 'gtkpod|libgpod'
ii  gtkpod          0.99.14-2ubuntu4            manage songs and playlists on an Apple iPod
ii  gtkpod-data     0.99.14-2ubuntu4            architecture-independent files for gtkpod
ii  libgpod-common  0.7.90git20100216-0ubuntu3  common files for libgpod
rc  libgpod3        0.6.0-5ubuntu2              a library to read and write songs and artwor
ii  libgpod4        0.7.90git20100216-0ubuntu3  library to read and write songs and artwork 
ii  python-gpod     0.7.90git20100216-0ubuntu3  Python bindings for libgpod

```

Is it still broken because it's linked against an older version of libgpod?

Incidentally, this is the last time I **ever** buy an iPod.

Thanks,

Ramin.

---

### Post by Kadai on 2010-03-16
> **daneel6672 said:**
> I have a fifth generation ipod nano (A1320) and it certainly does not work out of the box yet.

Upgraded to lucid:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu lucid (development branch)
Release:    10.04
Codename:    lucid
```The ipod mounts automatically, but gtkpod gives a popup error message saying



So I took a look at the "About" menu and it said



To check the libraries it was actually using:

```

$ ldd /usr/bin/gtkpod
    linux-gate.so.1 =>  (0x00919000)
    libFLAC.so.8 => /usr/lib/libFLAC.so.8 (0x00e22000)
    libvorbisfile.so.3 => /usr/lib/libvorbisfile.so.3 (0x00b90000)
    libid3tag.so.0 => /usr/lib/libid3tag.so.0 (0x0067a000)
    libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00e6f000)
    libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x002ff000)
    libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00186000)
    libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x009dc000)
    libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00c25000)
    libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00763000)
    libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x001fa000)
    libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0x00206000)
    libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00c7e000)
    libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00110000)
    libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x003a2000)
    libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00153000)
    libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x0060a000)
    libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x001a2000)
    libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0x004bf000)
    libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x00d8f000)
    librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x001a7000)
    libglade-2.0.so.0 => /usr/lib/libglade-2.0.so.0 (0x001b0000)
    libxml2.so.2 => /usr/lib/libxml2.so.2 (0x00789000)
    libgpod.so.4 => /usr/lib/libgpod.so.4 (0x00aa8000)
    libcurl-gnutls.so.4 => /usr/lib/libcurl-gnutls.so.4 (0x002aa000)
    libgnomevfs-2.so.0 => /usr/lib/libgnomevfs-2.so.0 (0x00418000)
    libgconf-2.so.4 => /usr/lib/libgconf-2.so.4 (0x001c8000)
    libhal.so.1 => /usr/lib/libhal.so.1 (0x00cfd000)
    libdbus-1.so.3 => /lib/libdbus-1.so.3 (0x00585000)
    libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00475000)
    libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x05a94000)
    libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0x00a2f000)
    libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x002ea000)
    libogg.so.0 => /usr/lib/libogg.so.0 (0x002ee000)
    libz.so.1 => /lib/libz.so.1 (0x00727000)
    libX11.so.6 => /usr/lib/libX11.so.6 (0x1eb5a000)
    libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x002f5000)
    libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x002f9000)
    libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x0048e000)
    libXext.so.6 => /usr/lib/libXext.so.6 (0x005be000)
    libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00494000)
    libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x0049e000)
    libXi.so.6 => /usr/lib/libXi.so.6 (0x005ce000)
    libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x005e2000)
    libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x005ea000)
    /lib/ld-linux.so.2 (0x004a2000)
    libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0x005f4000)
    libselinux.so.1 => /lib/libselinux.so.1 (0x0064a000)
    libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x0068a000)
    libdirectfb-1.2.so.0 => /usr/lib/libdirectfb-1.2.so.0 (0x0091a000)
    libfusion-1.2.so.0 => /usr/lib/libfusion-1.2.so.0 (0x00665000)
    libdirect-1.2.so.0 => /usr/lib/libdirect-1.2.so.0 (0x00dc7000)
    libpng12.so.0 => /lib/libpng12.so.0 (0x006e4000)
    libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0x005dc000)
    libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0x0066f000)
    libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00709000)
    libexpat.so.1 => /lib/libexpat.so.1 (0x009b1000)
    libpcre.so.3 => /lib/libpcre.so.3 (0x00b34000)
    libsqlite3.so.0 => /usr/lib/libsqlite3.so.0 (0x00b99000)
    libplist.so.1 => /usr/lib/libplist.so.1 (0x0073c000)
    libimobiledevice.so.0 => /usr/lib/libimobiledevice.so.0 (0x00745000)
    libidn.so.11 => /usr/lib/libidn.so.11 (0x008b3000)
    liblber-2.4.so.2 => /usr/lib/liblber-2.4.so.2 (0x008e5000)
    libldap_r-2.4.so.2 => /usr/lib/libldap_r-2.4.so.2 (0x00a58000)
    libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0x00c40000)
    libgnutls.so.26 => /usr/lib/libgnutls.so.26 (0x03119000)
    libgcrypt.so.11 => /lib/libgcrypt.so.11 (0x00d0f000)
    libdbus-glib-1.so.2 => /usr/lib/libdbus-glib-1.so.2 (0x008f2000)
    libavahi-glib.so.1 => /usr/lib/libavahi-glib.so.1 (0x00723000)
    libavahi-common.so.3 => /usr/lib/libavahi-common.so.3 (0x00991000)
    libavahi-client.so.3 => /usr/lib/libavahi-client.so.3 (0x0099d000)
    libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0x00759000)
    libORBit-2.so.0 => /usr/lib/libORBit-2.so.0 (0x0cbd2000)
    libXau.so.6 => /usr/lib/libXau.so.6 (0x0075d000)
    libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00910000)
    libtasn1.so.3 => /usr/lib/libtasn1.so.3 (0x00a02000)
    libusbmuxd.so.1 => /usr/lib/libusbmuxd.so.1 (0x00a13000)
    libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0x00b12000)
    libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0x01286000)
    libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0x00b65000)
    libcom_err.so.2 => /lib/libcom_err.so.2 (0x00dec000)
    libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0x00a19000)
    libkeyutils.so.1 => /lib/libkeyutils.so.1 (0x00dfd000)
    libgpg-error.so.0 => /lib/libgpg-error.so.0 (0x00a21000)

```So this looks like the file installed by the libgpod library is libgpod.so.4.

```

$ dpkg-query -S /usr/lib/libgpod.so.4
libgpod4: /usr/lib/libgpod.so.4

``` Then to check that this was the 0.7.91 version of libgpod,

```
$ dpkg -l | egrep 'gtkpod|libgpod'
ii  gtkpod          0.99.14-2ubuntu4            manage songs and playlists on an Apple iPod
ii  gtkpod-data     0.99.14-2ubuntu4            architecture-independent files for gtkpod
ii  libgpod-common  0.7.90git20100216-0ubuntu3  common files for libgpod
rc  libgpod3        0.6.0-5ubuntu2              a library to read and write songs and artwor
ii  libgpod4        0.7.90git20100216-0ubuntu3  library to read and write songs and artwork 
ii  python-gpod     0.7.90git20100216-0ubuntu3  Python bindings for libgpod

```Is it still broken because it's linked against an older version of libgpod?

Incidentally, this is the last time I **ever** buy an iPod.

Thanks,

Ramin.

It does looks like that you have GTKPod looking for the old libgpod.
have you removed any older libgpod library before to compile and install the new one?

Have you used any "-prefix" option during configure to install the libraries into "/usr"?
If not, your newly compiled library surely is on "/usr/local/lib", and you'll require to link it to "/usr/lib"... if you do that, you can you can delete/override the old ones without removing them.

---

### Post by nothingspecial on 2010-03-16
sudo ln -s /usr/local/lib/libgpod.so.[COLOR="Red"]*(the-new-version)*[/COLOR] /usr/lib

---

### Post by perldude69 on 2010-03-16
Tried everything. Like others, gtkpod just wouldn't find my 5G. I ran this command:
dpkg -l | egrep 'gtkpod|libgpod'

rc  gtkpod                                     0.99.14-0ubuntu2                                       manage songs and playlists on an Apple iPod
rc  gtkpod-aac                                 0.99.14-0ubuntu2                                       manage songs and playlists on an Apple iPod
ii  libgpod-common                             0.7.0-1ubuntu1                                         common files for libgpod
ii  libgpod4                                   0.7.0-1ubuntu1                                         library to read and write songs and artwork

and removed libgpod-common and  libgpod4 with:
apt-get remove  libgpod4 
apt-get remove libgpod-common
I restarted GTKpod and it started working.....

-- Jim

---

### Post by daneel6672 on 2010-03-16
> **Kadai said:**
> It does looks like that you have GTKPod looking for the old libgpod.
have you removed any older libgpod library before to compile and install the new one?

Have you used any "-prefix" option during configure to install the libraries into "/usr"?
If not, your newly compiled library surely is on "/usr/local/lib", and you'll require to link it to "/usr/lib"... if you do that, you can you can delete/override the old ones without removing them.

The default build put stuff into /usr/local/ as you say. But linking against the version of libgpod that I built didn't work either (same error messages, no files visible on ipod). So I deleted the stuff in /usr/local manually and vowed to never stray from deb packages again. So I'm willing to wait until lucid links against libgpod 0.7.91.

---

### Post by Greya on 2010-03-20
Hi, i've compiled everything, double checked. (libgpod with prefix) Looks like gtkpod works, but 5g nano still does not see tracks. iTunes can see the playlist and recover it. So i need to use iTunes to fix the playlist every time...
Anyone have fully working version?

---

### Post by nothingspecial on 2010-03-20
Well, I did, but might 8 year old (whose iPod this is) put a pin number in to lock it and can`t remember it. And there`s no way of fixing that with Ubuntu.

GGGGGGGRRRRRRRRR!

](*,)

---

### Post by Mountain Dew Overdose on 2010-03-20
I also have an iPod Nano 5th Gen...and from reading every post on this thread, it would seem this is going no where at this rate...just saying :mrgreen:

---

### Post by Greya on 2010-03-20
by the way, after fixing database in iTunes i started gtkpod and i've got "iTunesDB does not match checksum in extended information file. gtkpod will try to match the information using SHA1 checksums."
looks like it is not compatible

---

### Post by Greya on 2010-03-20
after few bugs, reconnects and restarts it started to work. i will share the .debs if it will be stable

---

### Post by Greya on 2010-03-20
Good news everyone!
My amd64 build works flawlessly. Sometimes with warnings, but it works! :) Even adds album graphics.

The i386 build may work, but i did cross-compiling first time and i can't guarantee that i did not do a mistake. So try on your own risk, comment if it works.

(Karmic Coala)
[http://rapidshare.com/files/366031794/ipod5g-i386.tar.gz.html](http://rapidshare.com/files/366031794/ipod5g-i386.tar.gz.html)
[http://rapidshare.com/files/366032547/ipod5g-amd64.tar.gz.html](http://rapidshare.com/files/366032547/ipod5g-amd64.tar.gz.html)

(the .deb files, so everything can be easily removed/upgraded with synaptic)
Double-click to install :)
1. libplist
2. libgpod
3. gtkpod

---

### Post by wizzerd02 on 2010-03-20
just tried on xubuntu karmic with the i386 package.  Get errors:


something about "subprocess paste killed by signal (Broken pipe)"

---

### Post by Greya on 2010-03-21
> **wizzerd02 said:**
> just tried on xubuntu karmic with the i386 package.  Get errors:


something about "subprocess paste killed by signal (Broken pipe)"

Which deb?

I'll try to find 32bit os here and build on native platform.

---

### Post by reloweb on 2010-03-21
> **wizzerd02 said:**
> just tried on xubuntu karmic with the i386 package.  Get errors:


something about "subprocess paste killed by signal (Broken pipe)"

Same error. I'm using 32bit architecture...

Edit: You have to remove libgpod-common.
Edit: After installing the packages I start gtkpod but it won't run. It give me this error:
bash: /usr/bin/gtkpod: impossibile eseguire il file binario

---

### Post by oyejorge on 2010-03-21
There's a PPA available at [https://launchpad.net/~gilir/+archive/backports](https://launchpad.net/~gilir/+archive/backports) that has libgpod version 0.7.90. I installed it this morning and now my ipod works great!

---

### Post by Greya on 2010-03-21
**update, new links (built on native platform)**
libplist 1.2, libgpod 0.7.92, gtkpod 0.99.15

32 bit: [http://greyarium.com/ipod/ipod_5g-i386.tar.gz](http://greyarium.com/ipod/ipod_5g-i386.tar.gz)
64 bit: [http://greyarium.com/ipod/ipod5g-amd64.tar.gz](http://greyarium.com/ipod/ipod5g-amd64.tar.gz)

before installing: (To be sure that you don't have old libraries :))
[B]sudo apt-get remove libgpod-common
sudo apt-get remove libgpod4
sudo apt-get remove libplist0
sudo apt-get remove libplist
sudo apt-get remove gtkpod-data
sudo apt-get remove gtkpod
[/B]
*** Your rythmbox will be automatically uninstalled with libplist, so you have to install it later.

Double-click to install
1. libplist
2. libgpod
3. gtkpod 

after installing:
**sudo ln -s /usr/local/lib/libplist* /usr/lib**
(sorry, i don't know how to work with cmake)

if you miss your rythmox: **sudo apt-get install rythmbox**

_it works! :)_

I've applied for PPA, but it will be available in few days... if i'll have time...

---

### Post by wizzerd02 on 2010-03-21
Didn't work for me.  Not sure what I did wrong.  Got the following message when loading gtkpod:

gtkpod: error while loading shared libraries: libplist.so.1: cannot open shared object file: No such file or directory

there are several libplist files but none by that name.

---

### Post by Linuxqueen on 2010-03-21
If I am right, doesn't the new version of Ubuntu (10.04) support the 5g's without any tweaking?

---

### Post by Greya on 2010-03-22
> **wizzerd02 said:**
> Didn't work for me.  Not sure what I did wrong.  Got the following message when loading gtkpod:

gtkpod: error while loading shared libraries: libplist.so.1: cannot open shared object file: No such file or directory

there are several libplist files but none by that name.

[COLOR="Red"]sudo ln -s /usr/local/lib/libplist* /usr/lib[/COLOR]

---

### Post by wizzerd02 on 2010-03-22
Here is what happens when I type sudo ln -s /usr/local/lib/libplist* /usr/lib:

ln: creating symbolic link `/usr/lib/libplist.so': File exists
ln: creating symbolic link `/usr/lib/libplist++.so': File exists
ln: creating symbolic link `/usr/lib/libplist.so.1.1.2': File exists
ln: creating symbolic link `/usr/lib/libplist++.so.1.1.2': File exists

Then I type gtkpod and get:

gtkpod: error while loading shared libraries: libplist.so.1: cannot open shared object file: No such file or directory

---

### Post by reloweb on 2010-03-22
> **wizzerd02 said:**
> Here is what happens when I type sudo ln -s /usr/local/lib/libplist* /usr/lib:

ln: creating symbolic link `/usr/lib/libplist.so': File exists
ln: creating symbolic link `/usr/lib/libplist++.so': File exists
ln: creating symbolic link `/usr/lib/libplist.so.1.1.2': File exists
ln: creating symbolic link `/usr/lib/libplist++.so.1.1.2': File exists

Then I type gtkpod and get:

gtkpod: error while loading shared libraries: libplist.so.1: cannot open shared object file: No such file or directory
cd /usr/lib
sudo rm -rf libplist*
sudo ln -s /usr/local/lib/libplist* /usr/lib

---

### Post by reloweb on 2010-03-22
> **Greya said:**
> update for 32 bit (built on native platform)
libplist 1.2, libgpod 0.7.92, gtkpod 0.99.15

32 bit: [http://rapidshare.com/files/366438705/ipod_5g-i386.tar.gz.html](http://rapidshare.com/files/366438705/ipod_5g-i386.tar.gz.html)
64 bit: [http://rapidshare.com/files/366032547/ipod5g-amd64.tar.gz.html](http://rapidshare.com/files/366032547/ipod5g-amd64.tar.gz.html)

before installing:
**sudo apt-get remove libgpod-common**

Double-click to install
1. libplist
2. libgpod
3. gtkpod 

after installing:
**sudo ln -s /usr/local/lib/libplist* /usr/lib**
(sorry, i don't know how to work with cmake)

it works! :)

I've applied for PPA, but it will be available in few days...

Mirrors don't work...

---

### Post by edpatterson on 2010-03-22
> **Greya said:**
> update for 32 bit (built on native platform)
libplist 1.2, libgpod 0.7.92, gtkpod 0.99.15

32 bit: [http://rapidshare.com/files/366438705/ipod_5g-i386.tar.gz.html](http://rapidshare.com/files/366438705/ipod_5g-i386.tar.gz.html)
64 bit: [http://rapidshare.com/files/366032547/ipod5g-amd64.tar.gz.html](http://rapidshare.com/files/366032547/ipod5g-amd64.tar.gz.html)


From rapidshare.com
> 
This file is neither allocated to a Premium Account, or a Collector's Account, and can therefore only be downloaded 10 times.

This limit is reached.

To download this file, the uploader either needs to transfer this file into his/her Collector's Account, or upload the file again. The file can later be moved to a Collector's Account. The uploader just needs to click the delete link of the file to get further information.


I bought my 5g yesterday and would love to have it work with my laptop.

Ed

---

### Post by Greya on 2010-03-22
> **wizzerd02 said:**
> Here is what happens when I type sudo ln -s /usr/local/lib/libplist* /usr/lib:

ln: creating symbolic link `/usr/lib/libplist.so': File exists
ln: creating symbolic link `/usr/lib/libplist++.so': File exists
ln: creating symbolic link `/usr/lib/libplist.so.1.1.2': File exists
ln: creating symbolic link `/usr/lib/libplist++.so.1.1.2': File exists

Then I type gtkpod and get:

gtkpod: error while loading shared libraries: libplist.so.1: cannot open shared object file: No such file or directory

You had older version of libplist.

---

### Post by edpatterson on 2010-03-22
I recceived the following

> 
...
dpkg: error processing /home/ed/Downloads/ipod_5g-i386/gtkpod_0.99.15_i386.deb
 (--install):
 trying to overwrite '/usr/share/man/manl/gtkpod.1.gz', whis is also in package
 gtkpod-data 0:0.99.142ubuntu3
dpkg-deb: subprocess paste killed by signal (Broken pipe)

Remember, my intelligence level is that of someone who would spend $175.00 to listine to music through 1/8" speakers :-)

Ed

---

### Post by Greya on 2010-03-23
> **edpatterson said:**
> I recceived the following


Remember, my intelligence level is that of someone who would spend $175.00 to listine to music through 1/8" speakers :-)

Ed
sudo apt-get remove gtkpod-data

---

### Post by nothingspecial on 2010-03-23
> **Greya said:**
> **update, new links (built on native platform)**
libplist 1.2, libgpod 0.7.92, gtkpod 0.99.15

32 bit: [http://greyarium.com/ipod/ipod_5g-i386.tar.gz](http://greyarium.com/ipod/ipod_5g-i386.tar.gz)
64 bit: [http://greyarium.com/ipod/ipod5g-amd64.tar.gz](http://greyarium.com/ipod/ipod5g-amd64.tar.gz)

before installing: (To be sure that you don't have old libraries :))
[B]sudo apt-get remove libgpod-common
sudo apt-get remove libgpod4
sudo apt-get remove libplist0
sudo apt-get remove libplist
sudo apt-get remove gtkpod-data
sudo apt-get remove gtkpod
[/B]
*** Your rythmbox will be automatically uninstalled with libplist, so you have to install it later.

Double-click to install
1. libplist
2. libgpod
3. gtkpod 

after installing:
**sudo ln -s /usr/local/lib/libplist* /usr/lib**
(sorry, i don't know how to work with cmake)

if you miss your rythmox: **sudo apt-get install rythmbox**

_it works! :)_

I've applied for PPA, but it will be available in few days... if i'll have time...

64 bit works for me. Cheers.

---

### Post by reloweb on 2010-03-23
> **Greya said:**
> You had older version of libplist.

I have the same problem!
I remove everything from /usr/lib and create the new link to the files with this lines:

```
cd /usr/lib
sudo rm -rf libplist*
sudo rm -rf /usr/local/lib/libplist*
```

But the problem persist...

---

### Post by nickbnf on 2010-03-25
Has someone tried with Lucid? I mean without installing anything fancy, it should work out of the box.

---

### Post by PatrickMoore on 2010-03-27
but how do you create new platlists and sinc them onto the ipod...
(i have and ipod nano 3G)

---

### Post by irdo on 2010-03-28
Hello!
First I'd like to thank all the committed people in this community. I'm new to Linux (I don't know much about computers and software anyways...) and so far i got to solve all my problems just by searching the forums. Good work out there. :)
As you can probably tell from my spelling I'm no native speaker, so please excuse any mistakes i make.

I am running 9.10 Karmic Koala and followed Greya's guide for the 32 bit version. Well.. it didn't quite work out as planned.
When I try to install Rhythmbox from the software centre afterwards, I get the following error message:
> [I]
(Reading database ... 5% (this goes on until 100%)

(Reading database ... 285672 files and directories currently installed.) 
Unpacking libgpod4 (from .../libgpod4_0.7.2-1ubuntu1_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/libgpod4_0.7.2-1ubuntu1_i386.deb (--unpack): 
 trying to overwrite '/usr/lib/libgpod.so.4', which is also in package libgpod 0:0.7.92-1 
Unpacking libgpod-common (from .../libgpod-common_0.7.2-1ubuntu1_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/libgpod-common_0.7.2-1ubuntu1_i386.deb (--unpack): 
 trying to overwrite '/usr/share/hal/fdi/policy/20thirdparty/20-libgpod-sysinfo-extended.fdi', which is also in package libgpod 0:0.7.92-1 
Selecting previously deselected package media-player-info. 
Unpacking media-player-info (from .../media-player-info_3-0ubuntu1_all.deb) ... 
Selecting previously deselected package rhythmbox. 
Unpacking rhythmbox (from .../rhythmbox_0.12.5-0ubuntu5.2_i386.deb) ... 
Processing triggers for hal ... 
Regenerating hal fdi cache ... 
hal start/running, process 10759 
Processing triggers for man-db ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for desktop-file-utils ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/libgpod4_0.7.2-1ubuntu1_i386.deb 
 /var/cache/apt/archives/libgpod-common_0.7.2-1ubuntu1_i386.deb 
[/I]As long as i don't uninstall Rhythmbox via the terminal, ubuntu keeps trying to make me install libgpod4 by using the update manager, which also produces error messages about missing dependencies and so on.

But this won't be my biggest problem, as I could probably solve it by just removing the changes.

GTKPOD recognises my iPod nano 5g (i already had music on it, i am/was using windows back home. Unfortunately i only have my netbook available until the end of june, although i could probably find an internet-cafe with windows where i could install iTunes. Running iTunes on WINE didn't work out so far, my netbook seems to be too weak, it freezes during the installation). 
I also installed gtkpod-aac, as I kept getting error messages when I imported big parts of my music in gtkpod and i was optimistic/dumb enough to do additional changes before checking if everything works out... well, I hope this didn't cause my problem.
Even though I didn't change anything on my iPod except for letting gtkpod recognise all of its data **[edit: oh, i deleted an empty playlist which i accidentally created in windows to see if everything works. forgot about that]**, my iPod now tells me there wouldn't be any music on it. Checking the "Settings - About" my iPod now says 7.2GB (all the music on it) would be consumed by "other".
gtkpod still finds the music on my iPod and even manually browsing it reveals the music to be there - i can even open the mp3s on my iPod with a music player on my netbook.

Anyways, copying new music on the iPod via gtkpod doesn't seem to work. gtkpod says it's there, my iPod begs to differ.
What shall I do now? Judging from the other posts here, the old patches in this thread aren't necessary any more and I am sort of anxious about breaking even more.
Whether I could restore the music that's on it  (I read something about connecting the iPod to iTunes after putting music on it to fix the playlists in this thread) or even get it to work with Linux... anything would be fine.

---

### Post by Greya on 2010-03-28
I had the same problem first time. I had to connect ipod to the iTunes once. But my mate's ipod worked from the first time...
If you connected ipod to old gtkpod - it can break your database (i think so).

---

### Post by irdo on 2010-03-29
Plugging it into iTunes did the trick, even without synchronising it with the particular iTunes. Anyways, iTunes seems to convert the data on the iPod from category "other" to "music" and leaves a 30KB file "autorun.inf" on the iPod, which gtkpod deletes.
I also get your

                                     > by the way, after fixing database in iTunes i started gtkpod and i've got "iTunesDB does not match checksum in extended information file. gtkpod will try to match the information using SHA1 checksums."
looks like it is not compatible error.

Anyways, i will keep my iPod away from gtkpod for at least the next 3 weeks, as I'm in the Australian outback and won't get any new music. If somebody wants to take a look at the autorun.inf file just tell me, i'll upload it for you.

---

### Post by kbits69 on 2010-03-29
Thanks for this thread, folks. I actually went thru, tried it all and found none of it work. On a whim, I did a google search that resulted in finding a free program called Floola, which works flawlessly with my 5G in 9.10

[http://www.floola.com/home/](http://www.floola.com/home/)

you may need to use synaptic to download and install two additional files (floola will complain if you don't have them installed; just note them and install them). Beyond that...it's pretty much self explanatory.

HTH someone!

---

### Post by Veloteuton63 on 2010-03-31
too bad that I forgot my ipod and can't try it. It sure will make my day. Iwould be able to free these remaining 10GB occupied by WinXP on my HD ;)

-> Floola is the answer to all problems:

Download from here:

[http://www.floola.com/home/download_linux/](http://www.floola.com/home/download_linux/)

No install required - it only needs to be unpacked.

On my system a library "zlib.so" was missing, for which install instructions can be found here:

[http://www.techsww.com/tutorials/libraries/zlib/installation/installing_zlib_on_ubuntu_linux.php](http://www.techsww.com/tutorials/libraries/zlib/installation/installing_zlib_on_ubuntu_linux.php)

... that do not work, because they refer to an older version,

Just change the version number in the wget instruction:

wget [http://www.zlib.net/zlib-1.2.4.tar.gz](http://www.zlib.net/zlib-1.2.4.tar.gz)

and add a symbolic link to the file

/usr/lib/libz.so -> /usr/local/zlib/lib/libz.so

As of now WinXP is gone from my system ... again =:-))

Guess I'll even donate some money now to flooa

---

### Post by chill32 on 2010-04-01
Does floola work? I've heard that 10.04 has compatible with the new ipods such as, ipod touch and iphones.

---

### Post by oldpreacher on 2010-04-03
I thought I had it using aTunes - it was reading the songs from the iPod and showing the artwork. Then something happened, possibly when I tried to add a song from the aTunes repository and now Ubuntu 8.04 will not mount the iPod at all. 
I get an error message that says:

mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

After a minute or so the following replaces the previous error message window:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I'm new to Linux and am totally in the dark about what to do.

Anyone have a suggestion for how to get this ipod mounted again? 

I removed aTunes for now. Repeated disconnecting and reconnecting and restarts don't do anything.

---

### Post by martinbuhl on 2010-04-04
I spend a lot of time trying to get Rythmbox to work with no success. I cant get libgpod4 installed properly. Installed floola and got it to work. Seems like a pretty good solution so far. I continue to use Rhythmbox for playing back music on my labtop and use floola for copying music to the my nano 5g. 

A little tip: You need to specify the firmware id for your nano. Type "sudo lsusb -v | grep -i Serial" to find this.

:guitar:

---

### Post by edpatterson on 2010-04-04
> 
 Originally Posted by Greya  View Post
update, new links (built on native platform)
libplist 1.2, libgpod 0.7.92, gtkpod 0.99.15

32 bit: [http://greyarium.com/ipod/ipod_5g-i386.tar.gz](http://greyarium.com/ipod/ipod_5g-i386.tar.gz)
64 bit: [http://greyarium.com/ipod/ipod5g-amd64.tar.gz](http://greyarium.com/ipod/ipod5g-amd64.tar.gz)

before installing: (To be sure that you don't have old libraries )
sudo apt-get remove libgpod-common
sudo apt-get remove libgpod4
sudo apt-get remove libplist0
sudo apt-get remove libplist
sudo apt-get remove gtkpod-data
sudo apt-get remove gtkpod

*** Your rythmbox will be automatically uninstalled with libplist, so you have to install it later.

Double-click to install
1. libplist
2. libgpod
3. gtkpod

after installing:
sudo ln -s /usr/local/lib/libplist* /usr/lib
(sorry, i don't know how to work with cmake)

if you miss your rythmox: sudo apt-get install rythmbox

it works!

I've applied for PPA, but it will be available in few days... if i'll have time...

I tried all the steps again, here are my results;
An older version is available in a software channel

Generally you are recommended to install the verson from the software channel, since it is usually better supported
(Close)
Install Package

Insert nano

It opens a window with my nano's name 'Ed's Nano' and asks me to select a portable audio player. I picked 'Open VLC media player'

Errors
VLC can't recognize the input's format:
The format of
''file:///media/ED%27S%20NANO/iPod_Control/iTunes/iTunesCDB' cannot be detected. Have a look at the log for details.

The player just goes from one *.wav file to the next in very rapid succession, reading aloud the names of the songs and performers ?

Am I close? Did I pick the wrong player? Should I go back to Windows with my head hung in shame?

Ed

---

### Post by kayas80 on 2010-04-08
Does anyone know whether Ubuntu 10.04 will support the 5th generation ipod nano? Thanks

---

### Post by Vladan1021 on 2010-04-15
I used iTunes running in Virtual Box in XP. But I downloaded Floola and it works perfectly. Can transfer songs now to my iPod Nano 5G:)

---

### Post by McKracken on 2010-04-21
> **kayas80 said:**
> Does anyone know whether Ubuntu 10.04 will support the 5th generation ipod nano? Thanks

yes, it does support it already (beta2 version)

---

### Post by grege on 2010-04-21
10.04 seems to work OK sofar with an iPod Touch as well, using Rhythmbox.

---

### Post by jepong on 2010-04-27
has anyone implemented this on kubuntu and amarok?

---

### Post by nothingspecial on 2010-04-27
> **jepong said:**
> has anyone implemented this on kubuntu and amarok?

I believe, although I may be wrong, that amarok uses libgpod, so yes.

---

### Post by jepong on 2010-04-27
it seems i can;t mount my device on amarok... sheesh...

---

### Post by irdo on 2010-04-30
Ubuntu 10.04, iPod Nano.
Rythmbox is recognizing the iPod as desired and even recognizes the music on it. But as with the "dirty" fixes from before, any music I put on it gets recognized as "other", not "music" in the iPod's About Function where you can see the amounts of data stored on it. 
I didn't try it yet, but this could be solved by connecting the iPod to an iTunes, no synchronizing, just connecting so iTunes will restructure the data on board. 
Or that's at least how it worked before.
Does anyone have a solution for this? If I have to plug my iPod into Windows everytime I want new music on it, i could simply use Windows (and even enjoy Genius on my iPod). :(

---

### Post by Mountain Dew Overdose on 2010-04-30
I got mine working...I've been subscribed to this thread awhile hoping for a fix when I had 9.10, I burned, installed, booted up Lucid and now it works perfectly with my iPod Nano. As for irdo's issue...I've never had that happen with my iPod on Lucid so far or anything...try resetting it to factory settings once in iTunes, then try it in Ubuntu? Just a random suggestion off the top of my head...

---

### Post by irdo on 2010-05-13
Plugging my iPod into iTunes now gives me the "An iPod has been detected, but it could not be identified properly..." error message.

But putting music on the iPod with gtkpod iPod Manager and ejecting the iPod with Rythmbox works. 
It's a bit tricky, but better than nothing, I guess.
I'll look deeper into this when I am back home in July, till than I'm just glad to have some music with me...

---

### Post by RichardNeill on 2010-05-30
I found this post helpful.

[http://thias.marmotte.net/2010/04/apple-ipod-nano-5th-gen-fedora/](http://thias.marmotte.net/2010/04/apple-ipod-nano-5th-gen-fedora/)

I tried using the latest build of libgpod + gtkpod (as per someone's earlier very helpful post), but this along is not sufficient. What worked for me is:

1. Boot into Windows XP (ugh!).
2. Download iTunes (all 96 MB of it!)
3. Use iTunes to restore the iPod to factory settings.
4. Initialise the iPod once with iTunes. When prompted for a name, I called it "IPOD" 
(this probably doesn't matter, but Linux uses this name for the mount-point under /media)
5.Sync one MP3 onto the iPod via iTunes. This step seems to be necessary.
6. Use the latest libgpod and gtkpod builds (the version shipped with Lucid *might* be enough; the git tree certainly works).
7. Now use gtkpod, and it will work properly.

---

### Post by budman21901 on 2010-06-26
> **RichardNeill said:**
> I found this post helpful.

[http://thias.marmotte.net/2010/04/apple-ipod-nano-5th-gen-fedora/](http://thias.marmotte.net/2010/04/apple-ipod-nano-5th-gen-fedora/)

I tried using the latest build of libgpod + gtkpod (as per someone's earlier very helpful post), but this along is not sufficient. What worked for me is:

1. Boot into Windows XP (ugh!).
2. Download iTunes (all 96 MB of it!)
3. Use iTunes to restore the iPod to factory settings.
4. Initialise the iPod once with iTunes. When prompted for a name, I called it "IPOD" 
(this probably doesn't matter, but Linux uses this name for the mount-point under /media)
5.Sync one MP3 onto the iPod via iTunes. This step seems to be necessary.
6. Use the latest libgpod and gtkpod builds (the version shipped with Lucid *might* be enough; the git tree certainly works).
7. Now use gtkpod, and it will work properly.

Thank you!!  Your directions worked perfectly with a 5th gen nano (pink).  I use Lucid with all recent updates.  The name is not required, but syncing at least one tune with I tunes was.  Then it was detected immediately.  Thanks!

---

### Post by Ofloo on 2010-06-28
> **nickbnf said:**
> Has someone tried with Lucid? I mean without installing anything fancy, it should work out of the box.

Yes and it doesn't work neither is the one i've got listed in libgpod wiki, .. i have tried the git version however doesn't work, 

however my version is A1320 and when I select black 5th with vid it's an entirely different thing in gtkpod, .. gtkpod selects xC031 instead of A1320

---

### Post by bajenpojken on 2010-07-04
does a ipod nano 5g directly out of the box work with ubuntu 10.5 ?

---

### Post by Ofloo on 2010-07-14
it does show however it complains about the direcotry struct (gtkpod), i've tried various clients such as amarok, rhythbox crashes ..

---

### Post by ankspo71 on 2010-07-14
Hi,
In addition to the above suggestions, 'plasma-widget-smooth-tasks' is also another dockbarx-like alternative.

---

### Post by Colt&#1052;1911 on 2010-07-31
> **RichardNeill said:**
> I found this post helpful.

[http://thias.marmotte.net/2010/04/apple-ipod-nano-5th-gen-fedora/](http://thias.marmotte.net/2010/04/apple-ipod-nano-5th-gen-fedora/)

I tried using the latest build of libgpod + gtkpod (as per someone's earlier very helpful post), but this along is not sufficient. What worked for me is:

1. Boot into Windows XP (ugh!).
2. Download iTunes (all 96 MB of it!)
3. Use iTunes to restore the iPod to factory settings.
4. Initialise the iPod once with iTunes. When prompted for a name, I called it "IPOD" 
(this probably doesn't matter, but Linux uses this name for the mount-point under /media)
5.Sync one MP3 onto the iPod via iTunes. This step seems to be necessary.
6. Use the latest libgpod and gtkpod builds (the version shipped with Lucid *might* be enough; the git tree certainly works).
7. Now use gtkpod, and it will work properly.

Thanks for the helpful information!!!

---

### Post by Kreuger on 2010-08-19
I now have my own 5g nano and I cant get it to work. It seems when you setup more than one ipod, gtkpod gets confused and it doesnt work properly. It was thinking I was using my wife's and then my niece's as well. I tried removing it all and reinstalling using the guide and to no avail. When I try to use it, it fails to import the database. This was brand new out of the box too. I plugged it into a Win computer to use iTunes and it needed a restore but that wont work without a stable net connection (which I dont have on the Win pc). Any ideas?

---

### Post by whitethunder922 on 2010-09-01
> **RichardNeill said:**
> I found this post helpful.

[http://thias.marmotte.net/2010/04/apple-ipod-nano-5th-gen-fedora/](http://thias.marmotte.net/2010/04/apple-ipod-nano-5th-gen-fedora/)

I tried using the latest build of libgpod + gtkpod (as per someone's earlier very helpful post), but this along is not sufficient. What worked for me is:

1. Boot into Windows XP (ugh!).
2. Download iTunes (all 96 MB of it!)
3. Use iTunes to restore the iPod to factory settings.
4. Initialise the iPod once with iTunes. When prompted for a name, I called it "IPOD" 
(this probably doesn't matter, but Linux uses this name for the mount-point under /media)
5.Sync one MP3 onto the iPod via iTunes. This step seems to be necessary.
6. Use the latest libgpod and gtkpod builds (the version shipped with Lucid *might* be enough; the git tree certainly works).
7. Now use gtkpod, and it will work properly.

Confirmed that this method DOES work with the Lucid versions of gtkpod (0.99.14) and libgpod (0.7.93). Also, after following these steps I am able to use Rhythmbox just fine to sync music to my iPod Nano 5G. Banshee is unable - it claims it is too old for such an awesome device. Thanks RichardNeill!

---

### Post by MasterOfTheHat on 2010-09-09
That method did work, but I had to name the iPod as "ipod" with iTunes. "iPod Nano" nor "IPOD" would work. 

Thanks for the help, guys!

---

### Post by Eben Fourie on 2010-09-13
this is what worked for me:

i  tried various Ubuntu packages such as gtkPod, Amarok etc - no success
 
HP G61 - does not support processor virtualization.
karmic, running virtualbox 3.1.8 (xp sp3)
iPod Nano 5th Gen

iTunes 9.1.1 crashes
then downgraded to iTunes 8.2.1, but Nano wanted iTunes 9 or later
iTunes 10.0.0.68 = success :smile:

would love something that works under Ubuntu, but for now vBox with iTunes 10 seems to do the trick...

see following thread for details on vBox and iTunes 9
[http://ubuntuforums.org/showthread.php?t=1431695](http://ubuntuforums.org/showthread.php?t=1431695)

---

### Post by saegeas on 2010-10-05
I can confirm that Floola works, but nothing else I tried (which includes everything above except VBox/iTunes10) worked for me.  Thank you Floola!!  I hope either they go open source or gtkpod/libgpod gets it together soon.

---

### Post by flyingboy on 2010-10-10
i have tried floola, and while it seems to work with the actual sync, i cannot get it to work reliably. it often crashes. i think i may have installed it incorrectly though. can anyone confirm?

---

### Post by Floola on 2010-10-23
Floola 6.0 was released! Biggest new feature is Facebook integration to share music played in Floola with friends.

A couple of linux bugs fixed.

[http://www.floola.com](http://www.floola.com)

---

### Post by flyingboy on 2010-10-24
SOLUTION! SO SIMPLE!

Using a computer with iTunes (I used a PC) initialize/restore the iPod. Name it, and do not have checked voiceover, auto sync, and there is a third box that I can't remember but it should probably be unchecked (I did). Then simply plug the iPod into a computer that is running Ubuntu 10.10 Maverick Meerkat. Using Banshee, sync your iPod. You'll be all set!

Note: While I did not try anything other than Banshee, I would imagine that it works with any of the major music organizers.

So nice to be able to easily sync the iPod finally!

---

### Post by epofra2k on 2010-11-09
> **flyingboy said:**
> 
Note: While I did not try anything other than Banshee, I would imagine that it works with any of the major music organizers...

Well, I just tried that yesterday, and it doesn't work at all with gtkpod... I'm back to just one track on my iPod (the one i synched from iTunes). :(


Will try again with Banshee.


**EDIT: **I confirm that using [**THIS METHOD**]("http://ubuntuforums.org/showthread.php?p=9384264#post9384264") and then using Banshee works like a charm! :P

---

### Post by blackmail on 2010-12-03
I have used several iPODs with linux and the synch software was Rhythmbox and it had no problems... :D

---

### Post by fabrixx on 2010-12-25
I try several times with my IPOD nano 5g (floola gtkpod etc..) and finally it work.

I've compiled Banshee 1.9 ([my guide]("http://www.osside.net/?p=4958")) with libgpod 0.8 and now sync work perfectly :p


I'm happy to leave Itunes/Windows.

---

### Post by bander013 on 2010-12-26
I just had emerged gtkpod-1.0.0 and libgpod-0.8.0. 
Ipod Nano 5G works fine, everything is good. Except, gtkpod can't find covers which were added in itunes.

---

### Post by chessplayer on 2010-12-29
Hello bander013,

the Maverick sources still offer 0.7.95-1 as the libgpod version. How did you obtain 0.8.0? Is there a ppa or something where I can find that?

cheers,

chessplayer

---

### Post by fabrixx on 2010-12-29
> **chessplayer said:**
> Hello bander013,

the Maverick sources still offer 0.7.95-1 as the libgpod version. How did you obtain 0.8.0? Is there a ppa or something where I can find that?

cheers,

chessplayer

Compiled from source:
[http://sourceforge.net/projects/gtkpod/files/libgpod/libgpod-0.8/](http://sourceforge.net/projects/gtkpod/files/libgpod/libgpod-0.8/)

---

### Post by trevts on 2011-02-02
I downloaded [COLOR=Red]Banshee Media Player[/COLOR] and hooked my 5g Nano right up and transferred songs right on to it. No extra downloaded stuff or anything technical needed.

---

### Post by fabrixx on 2011-02-03
Confirmed with Ubuntu 10.10 & last banshee

---

### Post by madmarx on 2011-03-05
I had a similar problem with my ipod nano 5G under ubuntu 10.10.
For some time, I could add music and see it in the ipod, then some day my ipod would not show it anymore.
Comparing to another one that was working, i found a difference in the  "iTunes" folder: 3 files were there in the broken ipod that were not in  the working ipod: CurrentOnTheGoPlaylist.plist, iTunesCDB.ext and  iTunesSD.
I made a backup of the directory first, then removed the 3 files.
I do not know why, but my ipod 5G is back: I can add files using gtkpod and they show on the ipod !

---

### Post by DarkTide on 2011-04-07
libiphone should not be required for the Nano 5G (or my patch). however I  think we can confirm there is a issue with libgpod copying the *.itdb  to the 5G and this seems to be one of the main problems you guys are  experancing atm, my suggestion to install the libiphone-dev package is  purely for testing purposes as it was 1 of 3 packages I have installed  and is not installed on the example of a non working build.

---

### Post by life in color on 2011-06-12
Hi, just downloaded libgpod 8.0 but can't install it.

---

### Post by fabrixx on 2011-06-13
Ubuntu 11.04 have support for  ipod nano 5g now via Rhythmbox

---

### Post by life in color on 2011-06-14
rhythmbox won't work for my ipod in Ubuntu 11.04 I can edit it and play music off of it but nothing actually happens to my ipod

---

### Post by DL3wis on 2011-06-18
The patch provided by Okiura didn't work for me, it caused errors during compile. I did however get my iPod Nano 5g working after using some instructions from this forum and tinkering around. This is how I got it to work on Kubuntu 11.04:

1. Make sure your iPod has been initialised on Windows to make the filesystem FAT32.

2. Follow these instructions from stefanadelbert to re-compile and install lastest git source version of libgpod and gtkpod:

> **stefanadelbert said:**
> Here is an extract from the INSTALL file which is part of the gtkpod source:

```
The following steps were necessary to install libgpod and gtkpod on a fairly virgin Ubuntu Hardy (LTS 8.04) installation.

# required packages
sudo apt-get install autoconf flex gettext libglib2.0-dev libgtk2.0-dev libglade2-dev libid3tag0-dev libxml-parser-perl pkg-config automake gcc git-core gtk-doc-tools

# recommended packages
sudo apt-get install libcurl4-dev libflac-dev libgnomevfs2-dev libhal-dev libvorbis-dev libmp4v2-dev

# checkout libgpod and gtkpod
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/libgpod
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod

# compile libgpod
cd libgpod/
./autogen.sh
make
sudo make install

# compile gtkpod
cd ../gtkpod/
cd libgpod/
./autogen.sh
make
sudo make install

#start gtkpod
gtkpod &
```

Make sure that you have installed all the dependencies (see the two [FONT="Courier New"]sudo apt-get install[/FONT] commands).

It's probably best to build your own just to make sure that you're building against exactly the right versions of the various libraries for your system.

3. Mount your iPod and open a terminal and type in: "sudo lsusb -v | grep -i Serial" without the quotes. Then you will see a 16-character-long hash. On your iPod navigate to the iPod_Control/Device folder and open or create a file named "SysInfo". Open this up in a text editor and type in: FirewireGuid: 0x... and paste that hash in (do not omit the 0x). For example - FirewireGuid: 0x000A27001301221F. Save the file.

4. Get a HashInfo file for your device from [here]("http://ihash.marcansoft.com/") by typing in the FirewireGuid you got above. Place it in iPod_Control/Device folder.

5. That should be all there is to it! If you fire up gtkpod you should be able to transfer songs to your iPod 5g. NOTE: It may be possible this works without recompiling libgpod and gtkpod in natty. I only noticed the HashInfo file requirement after I had recompiled.

6. If you want to use Amarok to manage your iPod - you need to get Amarok to detect it as an iPod rather than a mass storage device (Apparently this used to work in KDE < 4.6). 

7. Type in a terminal:

```
udevadm info --export-db | less
```

There is a lot of output, your looking for any sections relating to your iPod. Particularly, the section that shows the data partition, in my case /dev/sdc1 (yours maybe /dev/sdb1, etc). Once you find this section, look for the line "ID_FS_UUID" and copy the ID that's with this.

8. Open /lib/udev/rules.d/90_ligpod.rules with a text editor as root. Paste this line at the bottom:

```
ENV{ID_FS_UUID}=="<ID_YOU_COPIED>", ENV{ID_FS_LABEL} ="iPod_<your_name>", ENV{ID_FS_LABEL_ENC} = "iPod_<your_name>"

```

Replace <ID_YOU_COPIED> with the ID you got from the output of udevadm and replace <your_name> with, well... your name! The name MUST start with "ipod_" or it won't work.

9. Unplug and reconnect your iPod and it should now work with Amarok! You will see it should connect as "iPod_<your_name>".

That's it, hopefully this will work for others. Unfortunately, album art does not transfer using Amarok for me. But it works using gtkpod (which is strange as they both use libgpod).

---

### Post by life in color on 2011-06-23
No success, like before I can open and transfer songs etc. but none of it actually takes effect on my ipod. The only change I've managed to make was I added a different album cover to the iPod but it didn't go to the right album. I had the idea of opening up GParted and making an ext3 partition then installing Ipod-Linux on it though i'm not sure if this would work and I don't wanna ruin my iPod. If I can have a guarantee it will work I'll clear my iPod completely and put only ext3 on my iPod but again I need some kind of positive reasoning or confirmation.

---

### Post by Zenuno on 2011-06-24
Hi all.

I have the same problem here.

---

### Post by life in color on 2011-06-26
@DL3wis never mind it works now!!!!!!! Thanks a million, I guess I just had to restart the computer for it to work, I owe you big time :)

---

### Post by zipmon on 2011-07-17
@DL3wis, thank you SO much!!! This worked perfectly on my iPod Nano 5g with Ubuntu 11.04!! I can sync it right from Banshee now with no problems, album art and everything! :D

---

### Post by rich_hemmings on 2011-09-07
@DL3wis is a hero. Works fine with my setup:
vbox Ubuntu 11.04, 5thGen Nano and Banshee (testing at work, for deployment at home!) [which reminds me, I must move my wubi install to a permanent partition...]
  
Thanks!! 

:D :D :D

---

### Post by ajayver7 on 2011-10-06
Hey guys -

New Ubuntu user here. I can confirm that this worked with my iPod Nano (5G) and Ubuntu 11.04. I can now put songs on my iPod using Banshee. Sweet! 

Thanks for everyone's help!

-Ajay

---

### Post by lolipopo on 2011-11-23
anyone having issues with: 


checking for LIBANJUTA... no
configure: error: in `/home/sr-said/gtkpod':
configure: error: *** No package 'libanjuta-1.0' found
See `config.log' for more details



i have libanjuta but it's the 2.bla bla version n i think thats the problem


someone with a solution?




i'm on Oneiric Ocelot...

---

### Post by andersgb1 on 2012-05-22
> **DL3wis said:**
> The patch provided by Okiura didn't work for me, it caused errors during compile. I did however get my iPod Nano 5g working after using some instructions from this forum and tinkering around. This is how I got it to work on Kubuntu 11.04:

1. Make sure your iPod has been initialised on Windows to make the filesystem FAT32.

2. Follow these instructions from stefanadelbert to re-compile and install lastest git source version of libgpod and gtkpod:



3. Mount your iPod and open a terminal and type in: "sudo lsusb -v | grep -i Serial" without the quotes. Then you will see a 16-character-long hash. On your iPod navigate to the iPod_Control/Device folder and open or create a file named "SysInfo". Open this up in a text editor and type in: FirewireGuid: 0x... and paste that hash in (do not omit the 0x). For example - FirewireGuid: 0x000A27001301221F. Save the file.

4. Get a HashInfo file for your device from [here]("http://ihash.marcansoft.com/") by typing in the FirewireGuid you got above. Place it in iPod_Control/Device folder.

5. That should be all there is to it! If you fire up gtkpod you should be able to transfer songs to your iPod 5g. NOTE: It may be possible this works without recompiling libgpod and gtkpod in natty. I only noticed the HashInfo file requirement after I had recompiled.

6. If you want to use Amarok to manage your iPod - you need to get Amarok to detect it as an iPod rather than a mass storage device (Apparently this used to work in KDE < 4.6). 

7. Type in a terminal:

```
udevadm info --export-db | less
```

There is a lot of output, your looking for any sections relating to your iPod. Particularly, the section that shows the data partition, in my case /dev/sdc1 (yours maybe /dev/sdb1, etc). Once you find this section, look for the line "ID_FS_UUID" and copy the ID that's with this.

8. Open /lib/udev/rules.d/90_ligpod.rules with a text editor as root. Paste this line at the bottom:

```
ENV{ID_FS_UUID}=="<ID_YOU_COPIED>", ENV{ID_FS_LABEL} ="iPod_<your_name>", ENV{ID_FS_LABEL_ENC} = "iPod_<your_name>"

```

Replace <ID_YOU_COPIED> with the ID you got from the output of udevadm and replace <your_name> with, well... your name! The name MUST start with "ipod_" or it won't work.

9. Unplug and reconnect your iPod and it should now work with Amarok! You will see it should connect as "iPod_<your_name>".

That's it, hopefully this will work for others. Unfortunately, album art does not transfer using Amarok for me. But it works using gtkpod (which is strange as they both use libgpod).

Verrry nice!

Worked for me in Precise/Rhythmbox by only performing steps 1-4!

Thanks, DL3wis

---

### Post by anark10n on 2012-06-09
Hey, there having problems with this trying to get to sync with rhythmbox, banshee or gtkpod. the former two give no error when syncing but music is still not there when i disconnect the ipod, even though it shows some space has been taken up by the synchronisation. gtkpod just plain crashes (seg faults when run from a terminal) with nothing being picked up. On Ubuntu 12.04, running cinnamon.

---

