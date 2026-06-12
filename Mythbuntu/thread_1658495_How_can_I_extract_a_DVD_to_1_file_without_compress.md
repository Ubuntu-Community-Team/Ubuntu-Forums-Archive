---
title: "How can I extract a DVD to 1 file without compression?"
date: 2011-01-02
forum: Mythbuntu
---

### Post by myth01 on 2011-01-02
Hi

I've just set up a fileserver (in an Antec 300 - brilliant case) to provide 4TB of disk space (with room for more) over NFS to my mythTV backend so am trying to back up my DVDs to hdd.  After a lot of experimentation and Googling I still can not find a suitable application (or collection of) that can help me achieve what I'm after which is:

1) To extract the main feature only (no menus/specials features)
2) To extract the best English soundtrack only (ie 5.1ch vs 2ch)
3) To extract the English subtitle track
4) To end up with 1 file per title, either .vob or .mpg (mostly for ease of administration)
5) No requirement for transcoding/compressing (space is not an issue)
6) Something quick (if at all possible)



I have tried:
1) K9Copy - normally really really good, but can't get it to extract to 1 single file 
2) cat - cat'ting together the vobs made by K9Copy which mostly works ok but time scale only shows the length of the first vob to be cat'ted.
3) vobcopy - can't select audio track and English isn't always the first track, also had some aspect ratio issues.

With over 200 movies and 6 boxsets to get through, a preference would be low-interaction CLI-based.  Like setting up a command line or two, or a script and then it's just a case of putting the disc in and running.

Is this even possible?  How do you copy yours?

I appreciate the help.
Matt

---

### Post by thatguruguy on 2011-01-02
Use handbrake.  You can use it with a gui or cli, and you can set it to rip your dvds at whatever quality you want

---

### Post by BicyclerBoy on 2011-01-02
DVDRip or MakeMKV 

DVD::Rip dumps VOBs to disk & can do demux/transcoding as well..

Can just dump ISO images..Some players work with ISOs..

---

### Post by nickrout on 2011-01-03
```
mplayer dvd://1 -dumpstream -dumpfile myfilm.vob
```

where 1 is the title you want - 1 is usually the main film, but you may want to experiment with simply ```
mplayer dvd://n
```

where n starts at 1 and works up, till you find the right title.

Handbrake makemkv and dvdrip are the WRONG answers if you want a vob/mpg result and speed.

---

### Post by myth01 on 2011-01-03
Cheers everyone.  I'm going to go through these suggestions today.  So far I've tried:

```
mplayer dvd://1 -dumpstream -dumpfile myfilm.vob
```

I've re-done a few of the discs I was having trouble with but am still getting the same problems.

Problem disc  1:
mplayer shows audio tracks as:

```
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
audio stream: 1 format: ac3 (5.1) language: en aid: 129.
audio stream: 2 format: ac3 (5.1) language: fr aid: 130.
audio stream: 3 format: ac3 (5.1) language: de aid: 131.
audio stream: 4 format: ac3 (stereo) language: en aid: 132.
number of audio channels on disk: 5.
```

but German 5.1ch is what gets played in myth.  I can switch to the english track but I want to rip the disc with ONLY the english 5.1 track.  I've tried using -ausid <ID> for the correct track but all tracks still get dumped out.

Problem disc 2:
The aspect ratio is wrong playing back the dumped file in myth, but is fine when mplayer plays it (from the terminal)

Another strange thing just happened, I put another DVD in the drive and I was immediately logged out...?

How do I control/limit the audio tracks that get saved using mplayer, and how can I fix the aspect ratio?

Thanks again for your help, this is beginning to drive me nuts and I don't want to have to load up windows.

---

### Post by myth01 on 2011-01-03
I've had a really quick look at Handbrake (GUI) but it only seems to want to transcode.

All I'm after is:

- 1 single file (storage groups in 0.23.1 don't recognise VIDEO_TS/iso structures (?))
- Exact copy of main feature (storage is not an issue, and it's faster to extract)
- Ability to select audio/subtitle tracks to be extracted
- Preferably a working time scale (so cat is a last resort)

---

### Post by Senkoboy on 2011-01-03
Rip DVD in Myth, when it worked, did what you are looking for.  The last time I reinstalled myth .23 I can't get it to work.  Now in Myth .24 it has been removed.

---

### Post by tgm4883 on 2011-01-03
> **myth01 said:**
> I've had a really quick look at Handbrake (GUI) but it only seems to want to transcode.

All I'm after is:

- 1 single file (storage groups in 0.23.1 don't recognise VIDEO_TS/iso structures (?))
- Exact copy of main feature (storage is not an issue, and it's faster to extract)
- Ability to select audio/subtitle tracks to be extracted
- Preferably a working time scale (so cat is a last resort)

You will likely need to transcode, because of the lack of iso/video_ts support. I myself use handbrake for space concerns, even though I use 0.24 which has iso support.

---

### Post by mjitkop on 2011-01-03
I like k9copy as well but I only use the GUI version, I am not familiar with the options of the CLI.

It seems that you should be able to use k9copy to rip the main movie as a single file. Take a look at section "Ripping a DVD Title with K9Copy" on [this page]("http://home.comcast.net/%7Edsbonnell/K9copy.htm"). I'm guessing that if you adjust the file size to match the total size of all the VOB files of the movie on the DVD itself, you should have a single file that is not compressed. If I have time tonight, I will try it because it may be something I want to do in the near future too.

I just realized that it may not let you select audio and subtitle streams so that will probably not work for you unfortunately.

[COLOR=Black]Note that it could be tricky with recent DVDs to select the right DVD title. I usually start playing the DVD first in VLC and check which title number it is. Recent DVDs have a special encryption mechanism that fools ripping applications and make it look like there are several versions of the main movie in different title numbers.[/COLOR]

---

### Post by Senkoboy on 2011-01-03
I am running myth.23 Iso's made with K9Copy work just fine.

I used MakeMKV  this weekend to make a MKV copy, one file.  Worked as well.  

I have never got K9copy to make a perfect rip of the video files into one file, but I don't know what I am doing :lolflag:

---

### Post by perspectoff on 2011-01-03
> **mjitkop said:**
> I like k9copy as well but I only use the GUI version, I am not familiar with the options of the CLI.

It seems that you should be able to use k9copy to rip the main movie as a single file. Take a look at section "Ripping a DVD Title with K9Copy" on [this page]("http://home.comcast.net/%7Edsbonnell/K9copy.htm"). I'm guessing that if you adjust the file size to match the total size of all the VOB files of the movie on the DVD itself, you should have a single file that is not compressed. If I have time tonight, I will try it because it may be something I want to do in the near future too.

I just realized that it may not let you select audio and subtitle streams so that will probably not work for you unfortunately.

[COLOR=Black]Note that it could be tricky with recent DVDs to select the right DVD title. I usually start playing the DVD first in VLC and check which title number it is. Recent DVDs have a special encryption mechanism that fools ripping applications and make it look like there are several versions of the main movie in different title numbers.[/COLOR]

+1

I only do this for DVDs of family videos I made in the past and for business DVDs. I never advocate ripping commercially copyrighted DVDs. 

k9copy can extract to MPEG-4 (mp4) and MPEG-2 (mpg) output (or to other encoding formats), and you set the size of the file you'd like. The compression is adjusted accordingly.

As you already realise, k9copy already has the nice feature of being able to select the titles/components to transcode, and even to preview each title before you select it.

You won't want to have your hard drive cluttered with 4 Gb (or 7 Gb for HD) files -- you'll want to have some degree of compression that you can adjust to your taste.

---

### Post by thatguruguy on 2011-01-03
> **tgm4883 said:**
> You will likely need to transcode, because of the lack of iso/video_ts support. I myself use handbrake for space concerns, even though I use 0.24 which has iso support.

Yeah, but he says he doesn't want to transcode, and nickrout told him that using handbrake would be WRONG in capital letters.

---

### Post by thatguruguy on 2011-01-03
Incidentally, myth01, the mpeg2 used for DVDs is already lossy compression.  As such, you can't really extract a DVD "without compression", because the video is already compressed.  What you want is something that will keep the video at or near DVD quality, visually. Handbrake can work for that and meet your other requirements, but use whatever you want.

---

### Post by myth01 on 2011-01-03
Thanks guys for your input, I appreciate everyone's comments and ideas.

> **tgm4883 said:**
> You will likely need to transcode, because of the lack of iso/video_ts support. I myself use handbrake for space concerns, even though I use 0.24 which has iso support.

I've just upgraded to 0.24 but an audio issue means I am now all out of bank holiday to experiment further with VIDEO_TS/iso. :(

> **Senkoboy said:**
> Rip DVD in Myth, when it worked, did what you are looking for. The last time I reinstalled myth .23 I can't get it to work. Now in Myth .24 it has been removed.

Now that I'm on 0.24 I won't be using mythtv to rip the DVDs but out of curiosity, did it use it's own ripper or did it call another one?

> **mjitkop said:**
> I like k9copy as well but I only use the GUI version, I am not familiar with the options of the CLI.

I actually noticed a setting in K9Copy just now that hasn't been in previous versions (at least not that I've noticed before).  In the output drop-down box is the option of MPG *extraction*.  Which does exactly what I was after (ie any titles/audio tracks selected saved as 1 .mpg file).

> **perspectoff said:**
> I only do this for DVDs of family videos I made in the past and for business DVDs. I never advocate ripping commercially copyrighted DVDs...
...
...You won't want to have your hard drive cluttered with 4 Gb (or 7 Gb for HD) files -- you'll want to have some degree of compression that you can adjust to your taste.

I am only ripping DVDs which I already own, and still have (and will keep) the disc for. I was expecting someone to mention it ;) No-one ever seems fussed about ripping CDs...

Now that 1TB drives are so cheap (<£40 on ebuyer [can I say that?]) I'm not too bothered about the file size.  Everything I have should fit on 2TB and I don't have the patience to wait for transcoding :-|

> **thatguruguy said:**
> Incidentally, myth01, the mpeg2 used for DVDs is already lossy compression.  As such, you can't really extract a DVD "without compression", because the video is already compressed.  What you want is something that will keep the video at or near DVD quality, visually. Handbrake can work for that and meet your other requirements, but use whatever you want.

Cheers for the info thatguruguy and apologies for the bad wording previously.

I'm going to give K9copy another go and see how I get on with mpg extraction, iso and VIDEO_TS folder creation (now that myth supports it) and see what works best in mythvideo.

Some when down the line I accept I may need to transcode but would rather be in a position where I can run a script to do it in batches overnight, rather than have to wait and insert each disc every hour or so.

---

### Post by nickrout on 2011-01-03
> **myth01 said:**
> Cheers everyone.  I'm going to go through these suggestions today.  So far I've tried:

```
mplayer dvd://1 -dumpstream -dumpfile myfilm.vob
```

I've re-done a few of the discs I was having trouble with but am still getting the same problems.

Problem disc  1:
mplayer shows audio tracks as:

```
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
audio stream: 1 format: ac3 (5.1) language: en aid: 129.
audio stream: 2 format: ac3 (5.1) language: fr aid: 130.
audio stream: 3 format: ac3 (5.1) language: de aid: 131.
audio stream: 4 format: ac3 (stereo) language: en aid: 132.
number of audio channels on disk: 5.
```

but German 5.1ch is what gets played in myth.  I can switch to the english track but I want to rip the disc with ONLY the english 5.1 track.  I've tried using -ausid <ID> for the correct track but all tracks still get dumped out.

Problem disc 2:
The aspect ratio is wrong playing back the dumped file in myth, but is fine when mplayer plays it (from the terminal)

Another strange thing just happened, I put another DVD in the drive and I was immediately logged out...?

How do I control/limit the audio tracks that get saved using mplayer, and how can I fix the aspect ratio?

Thanks again for your help, this is beginning to drive me nuts and I don't want to have to load up windows.

I think it is the -aid parameter you want, not the -ausid.

You could try makemkv. This is a commercial proram, although presently free as it is in beta.

It makes an mkv of the tracks you want, but does not transcode (merely repackages).

Lets you choose which audio and subtitle tracks to include too.

---

### Post by williammanda on 2011-01-03
I've been using MakeMKV for a while now and I'm very satisfied. It is in beta now and free and will be free when released for DVD's. It doesn't compress but packages the audio and video in mkv format. It allows you to select what you want to record ie video and audio. The ripping time is comparable to the .23 mythvideo. Also it doesn't use alot of cpu when ripping. There hasn't been any issues with ripping a Sony or Disney DVD. Mythtv, VLC, or any other media player all work with mkv files.

---

### Post by BicyclerBoy on 2011-01-04
Mplayer is probably closest to the leading edge of solving DVD access problems.

But to clarify..
dvd::rip can dump a DVD image to HDD to reduce hammering the optical drive. Not sure if this is ISO.
dvd::rip can dump to VOBs with NO (extra) compression no transcoding

But I have found dvd::rip to have serious TOC/navigation problems with recent releases.

MakeMKV is painful as it auto-expires & is then useless. The DVD features are meant to be functioning regardless of beta or registered.

---

### Post by JDorfler on 2011-01-04
Make sure you have libdvdcss2 installed.  Open up Brasero Disk copier.  Copy the disc as an ISO where ever you want.  Make sure you rename the file after the movie you are ripping.  Heck, you can do this to a ton of DVDs, then open up HandBrake and have it look at the ISOs, line them up, start transcoding, go to bed, and you are good to go by the morning.

---

### Post by myth01 on 2011-01-04
> **BicyclerBoy said:**
> MakeMKV is painful as it auto-expires & is then useless. The DVD features are meant to be functioning regardless of beta or registered.

I was just giving MakeMKV a try and I quite like it's simplicity.  What autoexpires?  The software or the files it creates?  That's seems a shame...

---

### Post by BicyclerBoy on 2011-01-04
You'll find out...

The program expires and then requires another free download/compile cycle.

Just a bit a a pain but it is still free..

Frightening thought expiring the output files...
The files it generates should be fine, the whole point of .mkv container is that is open standard.

---

### Post by rhpot1991 on 2011-01-04
I can fully recommend makemkv.  First of all the mkv format is completely open, so it is a great choice and well supported in linux.  As far as makemkv itself, the dvd functionality is completely free, the blu-ray functionality is the paid part.  Everything is completely free while in beta, but the key expires each month and there is normally a day or so overlap before a new one is available.  You can avoid this by purchasing, but it really isn't that annoying.  The files it produces don't expire, just makemkv itself, normal registration key stuff.

---

### Post by thatguruguy on 2011-01-05
> **nickrout said:**
> I think it is the -aid parameter you want, not the -ausid.

You could try makemkv. This is a commercial proram, although presently free as it is in beta.

It makes an mkv of the tracks you want, but does not transcode (merely repackages).

Lets you choose which audio and subtitle tracks to include too.

It changes/repackages the files on the DVD, but doesn't transcode them?  That's really neat. Incredible, even.

---

### Post by nickrout on 2011-01-08
well strictly it repackages the **streams** in the .vob containers on the dvd into streams in mkv containers on the hard drive. It doesn't re-encode at all, merely remux (leaving out the streams you do not want).

Of course if you want to save space, then you can feed the resulting mkv to handbrake or avidemux or some command line formula and reduce to something modern like h.264.

---

