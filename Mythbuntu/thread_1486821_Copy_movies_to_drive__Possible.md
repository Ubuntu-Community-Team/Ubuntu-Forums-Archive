---
title: "Copy movies to drive?  Possible?"
date: 2010-05-18
forum: Mythbuntu
---

### Post by Sternfan on 2010-05-18
Hi all,

I have been giving some thought to setting up a Mythbuntu box.  One of the things I was thinking of doing was putting in a huge drive (2TB) and copying movies (DVD & BD) to the mythbuntu box so I could just pick them from a menu.  Is this possible?

Thanks,
Rob

---

### Post by LowSky on 2010-05-18
Yes, one of MythTV's main features is to use it for movie storage.

---

### Post by klc5555 on 2010-05-18
Ripping DVDs (from mythtv's ripper, which is a bit finicky, or from an array of specialized 3rd-party rippers) for viewing from a menu in myth is standard. 

I could be mistaken, but I don't think Blu-Ray is supported in myth yet, though is scheduled to be in 0.24.

---

### Post by JMcFly on 2010-05-18
It is possible, I have it set-up in 9.10 but it was a bit of a chore, with several issues:
1. I have to transcode every DVD to play it back (several hours to transcode vs 25-30min to rip an ISO); ISOs play the video too quickly with the audio at the normal rate so they're unsynced.
2. ISOs cannot be played from within storage groups, so you must network mount the storage drive on every frontend manually and put that location in media settings -> videos (I think thats the right location in the frontend menu)
3. Transcode progress bar shows only ~50% completed if left to run overnight on a dual-core 2.4ghz, if I cancel out and scan videos I'll sometimes get the .vob other times nothing.
4. I can't find a way to transcode a previously-ripped ISO
 
Has 10.04 fixed these issues?

---

### Post by ian dobson on 2010-05-18
> **klc5555 said:**
> Ripping DVDs (from mythtv's ripper, which is a bit finicky, or from an array of specialized 3rd-party rippers) for viewing from a menu in myth is standard. 

I could be mistaken, but I don't think Blu-Ray is supported in myth yet, though is scheduled to be in 0.24.

Hi,

I'm supprised that Blu-Ray should be supported in linux/MythTV the whole DRM thing really goes against the open source/hide nothing policy. The whole DRM thing relies on a secret key/processing. If your talking about Blu-rays ripped to MKV's that's possible today with MythVideo.

Regards
Ian Dobson

---

### Post by iamlindoro on 2010-05-18
> **ian dobson said:**
> Hi,

I'm supprised that Blu-Ray should be supported in linux/MythTV the whole DRM thing really goes against the open source/hide nothing policy. The whole DRM thing relies on a secret key/processing. If your talking about Blu-rays ripped to MKV's that's possible today with MythVideo.

Regards
Ian Dobson

[http://svn.mythtv.org/trac/changeset/24368](http://svn.mythtv.org/trac/changeset/24368)
[http://svn.mythtv.org/trac/changeset/24369](http://svn.mythtv.org/trac/changeset/24369)
[http://svn.mythtv.org/trac/changeset/24370](http://svn.mythtv.org/trac/changeset/24370)
[http://svn.mythtv.org/trac/changeset/24371](http://svn.mythtv.org/trac/changeset/24371)
[http://svn.mythtv.org/trac/changeset/24372](http://svn.mythtv.org/trac/changeset/24372)
[http://svn.mythtv.org/trac/changeset/24373](http://svn.mythtv.org/trac/changeset/24373)

---

### Post by Sternfan on 2010-05-18
Thanks everyone for the responses:  Since about 1/4 of my movie collection is BD (and growing), I think I need to wait for BD support (sounds like myth .24).

Since I haven't set up a Mythbuntu box yet, I have no idea what transcoding means - It sounds like I have a choice between ISO's and transcoding?  What format does the transcoding use?

Thanks,
Rob

---

### Post by ian dobson on 2010-05-18
> **iamlindoro said:**
> [http://svn.mythtv.org/trac/changeset/24368](http://svn.mythtv.org/trac/changeset/24368)
[http://svn.mythtv.org/trac/changeset/24369](http://svn.mythtv.org/trac/changeset/24369)
[http://svn.mythtv.org/trac/changeset/24370](http://svn.mythtv.org/trac/changeset/24370)
[http://svn.mythtv.org/trac/changeset/24371](http://svn.mythtv.org/trac/changeset/24371)
[http://svn.mythtv.org/trac/changeset/24372](http://svn.mythtv.org/trac/changeset/24372)
[http://svn.mythtv.org/trac/changeset/24373](http://svn.mythtv.org/trac/changeset/24373)

From the last commit in the patch set:-
what does not work
The big one: Decryption. This is for unencrypted disks and folder structures only.

Regards
Ian Dobson

---

### Post by iamlindoro on 2010-05-18
> **ian dobson said:**
> From the last commit in the patch set:-
what does not work
The big one: Decryption. This is for unencrypted disks and folder structures only.

Regards
Ian Dobson

I know this.  I wrote it.  ;)  Regardless, Myth *does* now play Blu-ray disks.  Just not encrypted ones.

---

### Post by LowSky on 2010-05-19
> **Sternfan said:**
> Thanks everyone for the responses:  Since about 1/4 of my movie collection is BD (and growing), I think I need to wait for BD support (sounds like myth .24).

Since I haven't set up a Mythbuntu box yet, I have no idea what transcoding means - It sounds like I have a choice between ISO's and transcoding?  What format does the transcoding use?

Thanks,
Rob

Transcoding is usually used to take a larger file and making it smaller. So if you like to record HD video, and who doesn't, you can use transcoding to shrink the file to a much smaller and manageable size using like h.264 or xvid codecs, or whatever you like. Its also useful for shrinking the viewing size so you can copy the videos to a device like an iPhone or portable media player, or an older computer that cannot handle HD.

---

### Post by williammanda on 2010-05-19
> **Sternfan said:**
> Thanks everyone for the responses:  Since about 1/4 of my movie collection is BD (and growing), I think I need to wait for BD support (sounds like myth .24).

Since I haven't set up a Mythbuntu box yet, I have no idea what transcoding means - It sounds like I have a choice between ISO's and transcoding?  What format does the transcoding use?

Thanks,
Rob

I use this sodtware to rip dvds.

[http://www.makemkv.com/](http://www.makemkv.com/)

They also handle blueray as well. You could rip your BD and then play them in mythtv.

---

### Post by williammanda on 2010-05-19
> **ian dobson said:**
> Hi,

I'm supprised that Blu-Ray should be supported in linux/MythTV the whole DRM thing really goes against the open source/hide nothing policy. The whole DRM thing relies on a secret key/processing. If your talking about Blu-rays ripped to MKV's that's possible today with MythVideo.

Regards
Ian Dobson

How does mythvideo rip to a mkv format?

---

### Post by Sternfan on 2010-05-20
Since I am going to be doing some transcoding, looks like I am going to go with the quad.

What is mythvideo?  Is it built-in to mythbuntu?

Rob

---

### Post by williammanda on 2010-05-20
> **Sternfan said:**
> Since I am going to be doing some transcoding, looks like I am going to go with the quad.

What is mythvideo?  Is it built-in to mythbuntu?

Rob

Yes it is apart of mythtv.

[http://www.mythtv.org/wiki/MythVideo]("http://www.mythtv.org/wiki/MythVideo")

---

### Post by nickrout on 2010-05-21
> **Sternfan said:**
> Since I am going to be doing some transcoding, looks like I am going to go with the quad.

What is mythvideo?  Is it built-in to mythbuntu?

Rob

you do not need to do any transcoding. Simply use makemkv to convert your dvds and blurays to mkv files. They are not transcoded, simply decrypted and re-packaged into the mkv container.

---

### Post by Sternfan on 2010-05-24
Nick, thanks for the help.  Will VLC play .mkv files?

---

### Post by nickrout on 2010-05-24
Yes VLC will play them, as will the internal player and mplayer.

---

