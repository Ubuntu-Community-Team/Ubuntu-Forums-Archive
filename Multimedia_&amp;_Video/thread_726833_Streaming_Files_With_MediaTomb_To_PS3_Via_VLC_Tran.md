---
title: "Streaming Files With MediaTomb To PS3 Via VLC Transcode"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by nerm on 2008-03-17
Hello,

I am attempting to stream *.avi (xvid and divx) and *.ogg files to my PS3 via MediaTomb so I can watch videos and listen to music. (**N.B** My existing configuration with Mediatomb has enabled my to succesfully stream some xvid and divx video and all MP3 files.)

As the PS3 does not currently support xvid/divx consistently and .*ogg at all, I am attempting to use VLC to transcode my videos and music on the fly, then stream the output via Mediatomb to my PS3.

I found a Gentoo HowTo ( [http://gentoo-wiki.com/HOWTO_MediaTomb]("http://gentoo-wiki.com/HOWTO_MediaTomb")) of which much of its content is applicable to what I am attempting to do.

Although I have followed the Gentoo HowTo closely I have not been able to get my Ogg or Div/Xvid files to be sent to the PS3 successfully (I encounter the same unsupported data errors as with my existing Mediatomb configuration). 

Has anyone else attempted to transcode files on the fly (especially *.ogg and xvid/divx files) and stream to a PS3 via Mediatomb succesfully? If so could you please share your experiences?

Many Thanks

---

### Post by finwe on 2008-03-17
I've successfully got both vlc and ffmpeg to work when following the guide at the gentoo-wiki. So I can confirm that it works, though I sometimes get error messages which interrupts the movie.

---

### Post by nerm on 2008-03-18
Welll I've now completeley borked my mediatomb install on Dapper, so I'm going to wait unitl Hardy arrives before I play with this some more.

---

### Post by Lonergan on 2008-03-26
> **finwe said:**
> I've successfully got both vlc and ffmpeg to work when following the guide at the gentoo-wiki. So I can confirm that it works, though I sometimes get error messages which interrupts the movie.

Does that include FLAC files?  Jin seems to think that these must be transcoded to mpeg2 rather than pcm/wav files.  The PS3 however, is capable of handling PCM files (twonkyvision's twonkymedia 4.4.4 under Windows can do this).

---

### Post by amak79 on 2008-05-30
> **Lonergan said:**
> Does that include FLAC files?  Jin seems to think that these must be transcoded to mpeg2 rather than pcm/wav files.  The PS3 however, is capable of handling PCM files (twonkyvision's twonkymedia 4.4.4 under Windows can do this).

MediaTomb SVN 1821 is capable of streaming transcoded audio to the PS3. This includes FLAC files and online streams such as SHOUTcast.

---

### Post by Lonergan on 2008-07-09
> **amak79 said:**
> MediaTomb SVN 1821 is capable of streaming transcoded audio to the PS3. This includes FLAC files and online streams such as SHOUTcast.

Is this by default without much tinkering?  I have Fuppes running now and it is working but I had to hack the config file quite a bit to get it to run properly.

---

### Post by amak79 on 2008-07-11
> **Lonergan said:**
> Is this by default without much tinkering?  I have Fuppes running now and it is working but I had to hack the config file quite a bit to get it to run properly.

It will require a minor change to the agent tag in the default oggflac2raw transcoding profile. The MT devs might include this by default or at least provide instructions in the config.

---

