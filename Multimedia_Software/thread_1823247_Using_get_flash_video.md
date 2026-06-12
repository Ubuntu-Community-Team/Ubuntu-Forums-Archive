---
title: "Using get_flash_video"
date: 2011-08-11
forum: Multimedia Software
---

### Post by kle on 2011-08-11
I want to be able to download and save the occasional news item - flash videos (mostly from BBC World and Aljazeera) - without having to go through Youtube. 

So I find that Google has what I need, or so it would seem:
[http://code.google.com/p/get-flash-videos]("http://code.google.com/p/get-flash-videos")

But i must be missing something! I run: 

[I]get_flash_videos [http://news.bbc.co.uk/2/hi/programmes/hardtalk/9560793.stm](http://news.bbc.co.uk/2/hi/programmes/hardtalk/9560793.stm)
[/I]
This returns: 
[INDENT]Downloading [http://news.bbc.co.uk/2/hi/programmes/hardtalk/9560793.stm](http://news.bbc.co.uk/2/hi/programmes/hardtalk/9560793.stm)
Using method 'bbc' for [http://news.bbc.co.uk/2/hi/programmes/hardtalk/9560793.stm](http://news.bbc.co.uk/2/hi/programmes/hardtalk/9560793.stm)
open3: exec of rtmpdump --rtmp rtmp://http://news.downloads.bbc.co.uk.edgesuite.net/ --pageUrl [http://news.bbc.co.uk/2/hi/programmes/hardtalk/9560793.stm](http://news.bbc.co.uk/2/hi/programmes/hardtalk/9560793.stm) --flv BBC_-__Do_whatever_it_takes_to_get_him_to_talk.flv --app ?_fcs_vhost=http://news.downloads.bbc.co.uk.edgesuite.net&at=my1HiMAC1265be6c85ac1827092095cde30440aaba23754c4aa43860751c0 --playpath mps_h264_hi/public/news/world/764000/764047_h264_1500k?at=my1HiMAC1265be6c85ac1827092095cde30440aaba23754c4aa43860751c0 --tcUrl rtmp://http://news.downloads.bbc.co.uk.edgesuite.net/?_fcs_vhost=http://news.downloads.bbc.co.uk.edgesuite.net&at=my1HiMAC1265be6c85ac1827092095cde30440aaba23754c4aa43860751c0 --swfUrl [http://news.bbc.co.uk/player/emp/2.11.7978_8433/9player.swf](http://news.bbc.co.uk/player/emp/2.11.7978_8433/9player.swf) failed at /usr/share/perl5/FlashVideo/RTMPDownloader.pm line 131

Make sure you have 'rtmpdump' or 'flvstreamer' installed and available on your PATH.
Download failed, no valid file downloaded[/INDENT]
In other words: No go. 

What have I done wrong?

---

### Post by kle on 2011-08-11
This seems to work for me (64-bit Ubuntu Lucid): 

Rather than the three-line sudo apt-get install etc. directions on the page I initially quoted, go straight to the Debian package ("for Debian and Ubuntu") here: 
[http://code.google.com/p/get-flash-videos/downloads/list]("http://code.google.com/p/get-flash-videos/downloads/list")

AND from repos, install *flvstreamer*

Now the command line 
*get_flash_videos [http://news.bbc.co.uk/2/hi/programmes/hardtalk/9560793.stm](http://news.bbc.co.uk/2/hi/programmes/hardtalk/9560793.stm) *
downloads this week's edition of "Hardtalk" to my "Home" folder.

---

### Post by andrew.46 on 2011-08-12
Works nicely in the presence of rtmpdump:

```

andrew@skamandros~/Desktop$ get_flash_videos-1.24 'http://news.bbc.co.uk/2/hi/programmes/hardtalk/9560793.stm'
Downloading http://news.bbc.co.uk/2/hi/programmes/hardtalk/9560793.stm
Using method 'bbc' for http://news.bbc.co.uk/2/hi/programmes/hardtalk/9560793.stm
RTMPDump v2.3
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
Starting download at: 0.000 kB
INFO: Metadata:
INFO:   duration              283.56
INFO:   moovPosition          28292464.00
INFO:   width                 640.00
INFO:   height                360.00
INFO:   videocodecid          avc1
INFO:   audiocodecid          mp4a
INFO:   avcprofile            77.00
INFO:   avclevel              30.00
INFO:   aacaot                2.00
INFO:   videoframerate        25.00
INFO:   audiosamplerate       44100.00
INFO:   audiochannels         1.00
INFO: trackinfo:
INFO:   length                7089000.00
INFO:   timescale             25000.00
INFO:   language              eng
INFO: sampledescription:
INFO:   sampletype            avc1
INFO:   length                12505088.00
INFO:   timescale             44100.00
INFO:   language              eng
INFO: sampledescription:
INFO:   sampletype            mp4a
BBC_-__Do_whatever_it_takes_to_get..._to_talk.flv: 99% (27971.14 / 27999.14 KiB)
Done. Saved 28642449 bytes to BBC_-__Do_whatever_it_takes_to_get_him_to_talk.flv

```

---

### Post by kle on 2011-08-12
Hi Andrew, thanks for your reply!

But I see I still have not quite got it. 
Yes, the video I tried to download yesterday ended in my home folder. But I have trouble with others.   
kle@kle-laptop:~$ get_flash_videos 'http://www.bbc.co.uk/news/business-14510946'
[INDENT]Downloading [http://www.bbc.co.uk/news/business-14510946](http://www.bbc.co.uk/news/business-14510946)
Using method 'bbc' for [http://www.bbc.co.uk/news/business-14510946](http://www.bbc.co.uk/news/business-14510946)
Error: Couldn't find BBC XML playlist URL in [http://www.bbc.co.uk/news/business-14510946](http://www.bbc.co.uk/news/business-14510946) at /usr/share/perl5/FlashVideo/Site/Bbc.pm line 54.

Couldn't extract Flash movie URL. This site may need specific support adding,or fixing.

Please confirm the site is using Flash video and if you have Flash available check that the URL really works(!).

Check for updates by running: /usr/bin/get_flash_videos --update

If the latest version does not support this please open a bug (or
contribute a patch!) at [http://code.google.com/p/get-flash-videos/](http://code.google.com/p/get-flash-videos/)
make sure you include the output with --debug enabled.
Couldn't download any videos.
[/INDENT]

As you see, the link here has no extension. But it is a flash movie. And I can play it online. 

Another link looks like this, with an html extension:  
[http://english.aljazeera.net/programmes/peopleandpower/2011/08/201189141348631784.html](http://english.aljazeera.net/programmes/peopleandpower/2011/08/201189141348631784.html)

How does one "get" videos from such links? I use flvstreamer, which is in the repos for Lucid, rather than RTMPdump, which is not (PPA for Lucid is "deprecated")

---

### Post by ron999 on 2011-08-12
> **kle said:**
> 
How does one "get" videos from such links? I use flvstreamer, which is in the repos for Lucid, rather than RTMPdump, which is not (PPA for Lucid is "deprecated")
Hi
Update the program first.
Use this command:-
```
sudo get_flash_videos --update
```

Then try to download again:-
```
get_flash_videos 'http://www.bbc.co.uk/news/business-14510946'
```

---

### Post by andrew.46 on 2011-08-12
Actually I could not download this video with 1.24:

```

andrew@skamandros~/Desktop$ g**[COLOR="Red"]et_flash_videos-1.24 'http://www.bbc.co.uk/news/business-14510946'[/COLOR]**
Downloading http://www.bbc.co.uk/news/business-14510946
Using method 'bbc' for http://www.bbc.co.uk/news/business-14510946
Error: Couldn't find BBC XML playlist URL in http://www.bbc.co.uk/news/business-14510946 at /home/andrew/bin/get_flash_videos-1.24 line 1135.

Couldn't extract Flash movie URL. This site may need specific support adding,
or fixing.

Please confirm the site is using Flash video and if you have Flash available
check that the URL really works(!).

Check for updates by running: /home/andrew/bin/get_flash_videos-1.24 --update

If the latest version does not support this please open a bug (or
contribute a patch!) at http://code.google.com/p/get-flash-videos/
make sure you include the output with --debug enabled.
Couldn't download any videos.

```

But the newest version from git had no such problem:

```

andrew@skamandros~/Desktop/get-flash-videos$ **[COLOR="Red"]./get_flash_videos --version[/COLOR]**
get_flash_videos version 1.25 (http://code.google.com/p/get-flash-videos/)
andrew@skamandros~/Desktop/get-flash-videos$ **[COLOR="Red"]./get_flash_videos 'http://www.bbc.co.uk/news/business-14510946'[/COLOR]**
Downloading http://www.bbc.co.uk/news/business-14510946
Using method 'bbc' for http://www.bbc.co.uk/news/business-14510946
Downloading http://news.downloads.bbc.co.uk.edgesuite.net/mps_h264_hi/public/news/business/765000/765070_h264_1500k.mp4?at=7rxHzDuY6327183b0e8e5fbc9121b1337ed0ce7dcadc88b14aa5680b38280...
765070_h264_1500k.mp4: 100% (20289.84 / 20289.84 KiB)
Done. Saved 20776800 bytes to 765070_h264_1500k.mp4


```

---

### Post by kle on 2011-08-12
Very grateful for your help on this, Andrew and Ron
 
First, Ron: No go. I did as you suggested: 
kle@kle-laptop:~$ sudo get_flash_videos --update
[INDENT]You already have the latest version.[/INDENT]

kle@kle-laptop:~$ get_flash_videos 'http://www.bbc.co.uk/news/business-14510946' 
[INDENT]Downloading [http://www.bbc.co.uk/news/business-14510946](http://www.bbc.co.uk/news/business-14510946)
Using method 'bbc' for [http://www.bbc.co.uk/news/business-14510946](http://www.bbc.co.uk/news/business-14510946)
Error: Couldn't find BBC XML playlist URL in [http://www.bbc.co.uk/news/business-14510946](http://www.bbc.co.uk/news/business-14510946) at /usr/share/perl5/FlashVideo/Site/Bbc.pm line 54.[/INDENT]
etc. 

However,I see from another thread ("Compiling get_flash_videos from git") that you have put in a lot of effort to use the solution suggested here by Andrew - using "the newest version from Git". I'm afraid I don't understand much of your dialogue with Theo and MadCow. 

(I admit I had never heard of "Git" before.)
Have you reached a conclusion, and can it be shared? (I repeat I am using LTS Lucid)

Andrew: I have no idea how to get the version 1.25 
[INDENT]kle@kle-laptop:~$ cd /usr/share/doc/get-flash-videos
kle@kle-laptop:/usr/share/doc/get-flash-videos$ ls -a
.  ..  changelog.Debian.gz  copyright
kle@kle-laptop:/usr/share/doc/get-flash-videos$ ./get_flash_videos --version
bash: ./get_flash_videos: No such file or directory
[/INDENT]

---

### Post by ron999 on 2011-08-12
Hi
What happens with this command:-
```
get_flash_videos --version
```

---

### Post by andrew.46 on 2011-08-12
> **kle said:**
> Andrew: I have no idea how to get the version 1.25

Looks like Ron999 is pretty much on top of that and you should [follow his lead here]("http://ubuntuforums.org/showthread.php?p=11146416") :).

---

### Post by kle on 2011-08-13
To Ron:
After I had run update, I still have version 1.24:
 
[INDENT]kle@kle-laptop:~$ get_flash_videos --version
get_flash_videos version 1.24 ([http://code.google.com/p/get-flash-videos/](http://code.google.com/p/get-flash-videos/))[/INDENT]

To Andrew: 
Are you telling me I should run the following in terminal? It looks a bit Chinese to me, so I would like confirmation before I go for it:

[INDENT]git clone git://github.com/monsieurvideo/get-flash-videos.git && \
cd get-flash-videos && make && \
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname get-flash-videos \
	--pkgversion "`date +%Y%m%d`-git" --backup=no --deldoc=yes --default
[/INDENT]

---

### Post by ron999 on 2011-08-13
> **kle said:**
> 
[INDENT]kle@kle-laptop:~$ get_flash_videos --version
get_flash_videos version 1.24 ([http://code.google.com/p/get-flash-videos/](http://code.google.com/p/get-flash-videos/))[/INDENT]

Are you telling me I should run the following in terminal?

Hi
This is a method to use.

Install the dependencies:-

```
sudo apt-get install build-essential git-core checkinstall libhtml-parser-perl libtie-ixhash-perl liburi-perl libwww-mechanize-perl libwww-perl libxml-simple-perl perl

```
Then paste and run this ***single*** command:-
```
cd ~/ && \ 
git clone git://github.com/monsieurvideo/get-flash-videos.git && \
cd get-flash-videos && \
make && \
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname get-flash-videos \
--pkgversion "1.2.5+git$(date +%Y%m%d)" --backup=no --default --deldoc=yes
```

When it's finished, run this command again:-
```
get_flash_videos --version
```

And try the BBC link again:-
```
get_flash_videos 'http://www.bbc.co.uk/news/business-14510946'
```

---

### Post by kle on 2011-08-13
YES!
Thank you, Ron! Everything worked without a hitch. 

Result installation:
[INDENT]Done. The new package has been installed and saved to 
/home/kle/Desktop/get-flash-videos_1.2.5+git20110813-1_amd64.deb[/INDENT]

Result version:
[INDENT]kle@kle-laptop:~/get-flash-videos$ get_flash_videos --version
get_flash_videos version 1.25 ([http://code.google.com/p/get-flash-videos/](http://code.google.com/p/get-flash-videos/))[/INDENT]

Result download of previously undownloadable flash:
[INDENT]kle@kle-laptop:~/get-flash-videos$ get_flash_videos 'http://www.bbc.co.uk/news/business-14510946'
Downloading [http://www.bbc.co.uk/news/business-14510946](http://www.bbc.co.uk/news/business-14510946)
Using method 'bbc' for [http://www.bbc.co.uk/news/business-14510946](http://www.bbc.co.uk/news/business-14510946)
Downloading [http://news.downloads.bbc.co.uk.edgesuite.net/mps_h264_hi/public/news/business/765000/765070_h264_1500k.mp4?at=6O94u4sWd3f5c58075f0ad10c1f9e4ab72813e461b69a1d44aa69dbdfae00](http://news.downloads.bbc.co.uk.edgesuite.net/mps_h264_hi/public/news/business/765000/765070_h264_1500k.mp4?at=6O94u4sWd3f5c58075f0ad10c1f9e4ab72813e461b69a1d44aa69dbdfae00)...
765070_h264_1500k.mp4: 100% (20289.84 / 20289.84 KiB)
Done. Saved 20776800 bytes to 765070_h264_1500k.mp4
[/INDENT]

---

### Post by heyup on 2012-08-19
> **ron999 said:**
> 
```
get_flash_videos 'http://www.bbc.co.uk/news/business-14510946'
```
I'm testing the latest version of get_flash_videos but I'm having problems using it to download videos from the BBC.

The above video works OK, but I get an error message trying to download others. For example:-

get_flash_videos 'http://www.bbc.co.uk/programmes/b01lt276'

get_flash_videos 'http://www.bbc.co.uk/programmes/p00xj85p'


Is this a get_flash_video problem, or am I doing something wrong?

---

### Post by heyup on 2012-08-20
Apologies. Now solved.
 
get_flash_videos does not support iplayer, but get_iplayer does.

---

