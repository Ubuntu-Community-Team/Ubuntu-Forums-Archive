---
title: "MythMusic fails to play certain files"
date: 2009-12-29
forum: Mythbuntu
---

### Post by ChrisHogevonder on 2009-12-29
I'm currently playing around with Mythbuntu and I keep on running into one rather annoying thing...

All my files are stored on a linux host and are shared with my mythbuntu test-machine by the means of a NFS-share.
This works fine for most of my mp3's, but for some reason some of the files won't play in MythMusic, while they will play using mplayer of mpg123 on the same machine.

Some info/output:
From mplayer, this file plays without a problem:
```
Playing 01. Gare Du Nord - Come to the Ball.mp3.
Audio only file format detected.
Clip info:
 Title: Come to the Ball
 Artist: Gare du Nord
 Album: Love for Lunch
 Year: 2009
 Comment: -WV-
 Track: 1
 Genre: Jazz
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 320.0 kbit/22.68% (ratio: 40000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
```Full path:
/media/Media/Music/Gare Du Nord/(2009) Love for Lunch/01. Gare Du Nord - Come to the Ball.mp3


This file won't play in MythMusic, but plays flawless in mplayer:```

Playing 01. Gare Du Nord - The Phantom.mp3.
Audio only file format detected.
Clip info:
 Title: The Phantom
 Artist: Gare du Nord
 Album: Jazz In The City
 Year: 2008
 Comment: 
 Track: 1
 Genre: Jazz
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
```Full path:
/media/Media/Muziek/Gare du Nord/(2008) Jazz In The City/01. Gare Du Nord - The Phantom.mp3

The only error I get in the logs when I try to play the last file is the following:
```
2009-12-29 20:04:21.433 AO: Killing AudioOutputDSP
2009-12-29 20:04:21.433 Opening audio device '/dev/audio'. ch 2(2) sr 44100
2009-12-29 20:04:21.433 Opening OSS audio device '/dev/audio'.
2009-12-29 20:04:21.439 AudioOuputOSS: Unable to open mixer: 'ALSA:default'
2009-12-29 20:04:21.439 AO: Audio fragment size: 4096
2009-12-29 20:04:21.441 AO: Audio Stretch Factor: 1
2009-12-29 20:04:21.442 Audio Codec Used: not set
2009-12-29 20:04:21.442 AO: kickoffOutputAudioLoop: pid = 26545
2009-12-29 20:04:21.442 AO: OutputAudioLoop: Play Event
2009-12-29 20:04:21.443 AO: Ending reconfigure
2009-12-29 20:04:21.582 AO: no change exiting
2009-12-29 20:04:21.588 AO: OutputAudioLoop: Play Event
**2009-12-29 20:04:51.539 Could not open file (/media/Media/Muziek/Gare du Nord/(2008) Jazz In The City/01. Gare Du Nord - The Phantom.mp3)**
2009-12-29 20:04:51.539 AV decoder. Error: -2
2009-12-29 20:04:51.548 AO: OutputAudioLoop: Play Event

```The Mythbuntu user, used for running MythTV, has full access to this NFS-share (read and write) and the output from Mplayer was generated from a console using the same user.
Problem doesn't seem to be the specific file, but the folder containing the files (non of the mp3's from the album "(2008) Jazz In The City" plays...) or the encoding of the files. But since the log output doesn't provide any info about why it fails, I'm at a lost here...
Also the meta-data seems to be imported correctly into the database...

Who can give me some advice about where to continue the search for the problem?

---

### Post by bernied on 2010-01-24
Hi. 
Maybe you've already solved this?

I found this post because I had almost the same problem.

Anyway, the problem for me was the execute bit on the directories containing the music files. Directories must be 'executable' to be browseable (I think), it's not enough for just the files to be readable. 

I fixed it by chmod +x on all directories. I used [this advice](http://movabletripe.com/archive/recursively-chmod-directories-only/).
so I did something like this on the file server:
```
# cd /mnt/where/my/music/is
# find . -type d -exec chmod +x {} \;
```
If you don't want to enable all users to browse directories, then you'll need to make sure that user/group ownership is sorted out for all directories and the x bit is set for user/group as appropriate.

---

### Post by SiHa on 2010-01-25
It's not the '(' and ')' in the directory name is it?

---

### Post by gunterhausfrau on 2010-06-09
I think I may have the same issue. I keep getting "AV decoder. Error: -2" in the logs. I have gone and made all the directories executable. The one thing that is maybe a bit wonky is that I have the music files copied over into my home directory, is that bad?

whenever I try to play music. I see the files, I see the length of the songs, but when I try to play them, it just sits there. If I go to the "import file" and play the file, yep, music.

---

### Post by natuk on 2011-01-22
Same problem here. Directory is executable, files appear in mythmusic but not played. Files play normally in Rhythmbox.

---

### Post by geobre on 2012-01-28
Hi,

I don't think there are any problems really. It seems like mythfrontend does not want to play streamed mp3:s, thus error:-2
(In this setup we assume you have a main mythbuntu box that hosts the music, and another mythbuntu box where you want to play the music)

If you try this on your machine that does not want to play mp3 via mythfrontend:

Open up a console and execute this:
sudo apt-get install nfs-common

That will install nfs-support so you can mount an nfs-share (that is, your music share from your main mythbuntu box)

Then you have to edit your /etc/fstab and add this line:
SERVER:/var/lib/mythtv/music /var/lib/mythtv/music nfs rsize=8192,wsize=8192,timeo=14,intr

Exchange SERVER for your server name (if you have a dns) or IP-number.

Save, exit and execute
sudo mount -a

After this you should be able to play your music files as files, not as a stream.

Hope it helps.

(nfs export from your main mythbuntu box is most probably already in place, since that is the default setup when installing mythbuntu. Othervise you will have to export the music folder first.)

---

