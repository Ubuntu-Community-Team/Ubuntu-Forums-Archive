---
title: "FLAC files won't play in any application"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by dalert0140 on 2007-02-03
I'm trying to play some flac files but none of the audio players will let me! Totem,mplayer,exaile,xfmedia, etc. I tried googling it  and the closest I could find was a bug in xine-lib1.1.13 around a year ago i have xin-lib1.1.12 installed but FLAC files still won't play. Mp3 ,wma are fine though.

I'm using edgy by the way. Anyone with similar issues?

---

### Post by dalert0140 on 2007-02-03
Totem and gstreamer doesn't work either. All the other fixes for this seem to be from Dapper. Anyone having a similar issue in Edgy?

---

### Post by MetalMusicAddict on 2007-02-03
Have you installed the FLAC package?

---

### Post by dalert0140 on 2007-02-03
I used aptitude to install FLAC,flac123 and I can see that I have the libflac7 library installed. Is there any other package I'm missing?

---

### Post by MetalMusicAddict on 2007-02-03
No. The FLAC package with the Ubuntu icon next to it should have done it.

---

### Post by dalert0140 on 2007-02-03
Rhythmbox says that the MIME type of the file coould not be identified. Gnome though identifies it as a audio/x-flac

---

### Post by bremen on 2007-02-06
I'm having similiar problems.  Although for me xine won't play flac files created by grip, but it will play flac files created by kaudiocreator.  Also gstreamer will play both (as will winamp if it matters)

---

### Post by bananabob on 2007-05-01
I have had this problem with Amorok. So I tried Rhythmbox. The files wouild play there. So I thought I would try Exaile, the files were not even recognised as beeing in the directory with that.

So I thought what next. I installed Flac123 and that played them ok. So I used Flac to decode the files back to waves and then encode them back to flacs, and they now play fine in Amorok.

I wonder how many flac files I have like that?

---

### Post by musicinmybrain on 2007-05-01
> **bananabob said:**
> So I used Flac to decode the files back to waves and then encode them back to flacs, and they now play fine in Amorok.

Good news: Latest version of FLAC lets you re-encode FLACs in place (for example, if you want to take advantage of compression improvements since 1.1.2).

Bad news: Feisty ships with 1.1.2. You'll have to compile 1.1.4 from source if you want it.

Edit: I should clarify that only the encoder/decoder has changed (more compression and speed improvements, mostly) since 1.1.2. The format is the same, so 1.1.2 can decode files created by 1.1.4.

---

### Post by bananabob on 2007-05-01
If anyone wants a couple of PERL scripts to do the decode/encode I have them available for [download]("http://linux.eaton.net.nz/downloads")

---

