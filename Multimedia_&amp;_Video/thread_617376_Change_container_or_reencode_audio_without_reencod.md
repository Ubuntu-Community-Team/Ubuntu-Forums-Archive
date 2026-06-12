---
title: "Change container or reencode audio without reencoding video"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by ralyon on 2007-11-19
Problem: I would like to change the container or reencode the audio of a video stream without modifying the video encoding. The video from what I can find out is a MPEG transport stream and the audio is in a a52 container. Video works fine but I need the audio in an AC3, AAC or PCM.

Details: I have a mythtv backend with a hauppauge analog and a pchdtv digital tuners. With the upnp built into mythtv I can connect and play my recordings on my playstation 3 that have not been reencoded by mythtv yet. The analog recordings play fine, but on the digital recordings, which are ATSC over the air broadcasts, will play video, but there is no audio and the ps3 says there are no audio channels. I can play them in linux with vlc, but they are a little choppy and its a pain to find them by browsing the filenames.

What I've done so far: I have tried using transcode with a -P 1 to pass the video through, but it always tells me that I'm using an incompatible container. I have tried ffmpeg, mpeg2enc and mpeg in the -y so far, all with ac3 for the audio. 

Can someone direct me on what I can do to accomplish this? I would prefer a cl option so that I can have mythtv automatically do it after its recorded. Thanks in advance for any help and or advice. Let me know what other details can be helpful as well.

---

### Post by shirilover on 2007-11-19
a52 is AC-3 audio.

The following is taken from the description for liba52:
```

liba52 is a free library for decoding ATSC A/52 streams. The A/52
standard is used in a variety of applications, including digital
television and DVD. It is also known as AC-3.

```

---

### Post by disturbedite on 2007-11-19
aften can transcode ac3 audio as well.

---

### Post by ralyon on 2007-11-19
> **shirilover said:**
> a52 is AC-3 audio.

OK, hard to find info on this stuff unless you know what you are looking for. From what I can tell, the A/52 in the ATSC broadcasts is a Revision B and I'm guessing that the PS3 doesn't support that revision, only the earlier revisions, although I can't seem to find anything definite about that. I'm guessing that I just need to reencode to an earlier version.

I'm trying with mencoder today with several different switches but no joy there either. I will continue to play around and maybe I'll stumble across it eventually. :(

---

### Post by ralyon on 2007-11-25
I got it!!! :guitar: No reencoding was needed and Mythtv had all the software I needed already. The difference was only the container, which was MPEG Transport Stream (TS) and needed to be an MPEG Program Stream (PS).

This is what I finished with. Under mythtv-setup, General, I created a User job named PS3 (name it whatever you want). Here is what I put under command *(note that my recordings are stored in /var/mythtv which will need to be changed to where you keep your recordings)* (Edit: replaced this with %DIR%):

```
mythtranscode -c %CHANID% -s %STARTTIME% -p autodetect -m -e dvd -l; mv %DIR%/%FILE% %DIR%/%FILE%.old; mv %DIR%/%FILE%.tmp %DIR%/%FILE%; mythcommflag -c %CHANID% -s %STARTTIME% --rebuild --clearcutlist
```

**Breakdown**:
The first 3 switches for mythtranscode (-c, -s, -p) are required (read the help if you need to know). "-m" makes it stay in mpeg, "-e dvd" makes it a dvd compatible stream type (ps didn't work, weird), -l tells it to use the cutlist to cut out commercials (not the skiplist that commercial detection gives you).

The first "mv" command simply creates a backup of the original recording and can be removed if you don't want a backup (I already have but I thought it would be nice to include). The second "mv" moves the newly created file in place of the original one (it will overwite it without the fist "mv" command).

The last command rebuild the seek table on the new file and clears the cutlist since it has already been used. I didn't see an option to clear the skiplist so make sure to turn off commercial skipping since they are now gone. I'm open to suggestions on this.

Now to use it just bring up the menu for the recording and select Job Options and Begin PS3 or whatever you named it. I did notice that it takes about a minute to actually start playing. I'm not sure what causes that, might even be my physical network (gigabit ethernet). I would like to hear what other people experience with this as well.

Happy watching. :cool:

Edit: Replaced hard directory mapping with %DIR%. This should now work exactly as typed.

---

### Post by mjatromp on 2007-12-16
Whenever I play back a program that is transcoded this way, mythtv backend cpu utilization goes to 100% and stays at 100% even after the stream is done playing. When I play again, my second cpu goes to 100%...

Whatever happened to the 'record as program stream' option in the backend?

Marcel
--

---

### Post by ralyon on 2007-12-18
> **mjatromp said:**
> Whenever I play back a program that is transcoded this way, mythtv backend cpu utilization goes to 100% and stays at 100% even after the stream is done playing. When I play again, my second cpu goes to 100%...
--

I will take a look at this tonight. BTW, where are you playing this from, Backend/Frontend, seperate Frontend or PS3?

> **mjatromp said:**
> Whatever happened to the 'record as program stream' option in the backend?

Marcel
--

I'm not aware of that option, can you fand any info on it?

ralyon

---

### Post by mjatromp on 2007-12-19
> **ralyon said:**
> I will take a look at this tonight. BTW, where are you playing this from, Backend/Frontend, seperate Frontend or PS3?

Separate backend serving PS3

> **ralyon said:**
> I'm not aware of that option, can you fand any info on it?

Used to be in the older mythtv releases. A reference is made in [http://digitalmedia.oreilly.com/2005/12/07/myth-tv.html](http://digitalmedia.oreilly.com/2005/12/07/myth-tv.html). There is an old setup guide that has a screenshot showing the option as well, but I couldn't find it.

Marcel
--

---

### Post by ralyon on 2007-12-20
I found exactly what you described with CPU usage when viewing an hd broadcast. The first CPU would max out on the first show and stopping and starting a different show maxed out the other CPU. I am thinking this would only last the duration of the show. I will test this out later. I checked and it is mythbackend that is sucking up the CPUs. A restart of mythbackend clears out the CPUs right away at least.

I started with MythTV in June of 06, most likely why I hadn't heard of this option to save as a PS. I found this comment from the [Mythtv wiki]("http://www.mythtv.org/wiki/index.php/Video_capture_card") which leads me to believe this is a function of the card itself and not Mythtv.
> Some cards have a hardware Program ID filter (hardware pid) which means the card can extract the required program stream from the transport stream itself.

---

### Post by v0rtical on 2008-01-22
Make any headway with this?  I'm having the same "no audio" problem on my PS3 with recorded OTA ATSC.  I would really love to get this working without having to reboot the backend after watching every show...

Keep up the good work guys!

---

### Post by ralyon on 2008-01-24
Sorry, I haven't had much time to work on this. However, you don't need a full reboot, just ```
sudo /etc/init.d/mythtv-backend restart
``` will do the trick and is much faster.

---

