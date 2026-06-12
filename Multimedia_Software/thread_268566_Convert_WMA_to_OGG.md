---
title: "Convert WMA to OGG"
date: 2006-09-30
forum: Multimedia Software
---

### Post by alecjw on 2006-09-30
Is it possible to convert WMA (with DRM) to OGG (without DRM)?

And what bitrate would you consider to be CD quality? I know that a CD is thoreticallty about 1114kb/s, but I doubt that they're really recorded at such high bitrate.

---

### Post by slimdog360 on 2006-09-30
You would first have to rip the .wma file and get rid of the drm stuff. Dont ask me what application would do it though. Then convert to .ogg. but as 100000 people will tell you its bad to convert from one lossy format to another.

---

### Post by TheRingmaster on 2006-09-30
you could try soundkonverter or soundconverter (I don't know how it is spelled). It is in the respositories.

---

### Post by alecjw on 2006-09-30
Isuppose it would be simpler to buy the actual CD. Only £1 more.

---

### Post by tagra123 on 2006-09-30
I think grip will do what you are looking to do.

I think its in the reposotories too.

Try

apt-get install grip

---

### Post by bruce89 on 2006-09-30
Surely you could write the WMA to a CD (would be easier in Windows, not sure if you still have it) and then use Sound Juicer to rip it into **Vorbis**. (not ogg, it's the container for Vorbis)

---

### Post by user1397 on 2006-09-30
while we're on this topic, what is the filname extension for audio cd's? im talking about your regular music cd, the one you would put into a car cd player;)

---

### Post by bruce89 on 2006-09-30
> **erik1397 said:**
> while we're on this topic, what is the filname extension for audio cd's? im talking about your regular music cd, the one you would put into a car cd player;)

They don't have an extension it seems, but it is an uncompressed 44,100 Hz 16bit Waveform file.

---

### Post by alecjw on 2006-09-30
> **erik1397 said:**
> while we're on this topic, what is the filname extension for audio cd's? im talking about your regular music cd, the one you would put into a car cd player;)

There are no files on a CD.
I think this is how a CD works.
There's a few bytes of data at the beginning of the CD saying something like "Track 1 starts at memory unit 0x635b6da6f, Track 2 starts at 0x578d5686c87e" etc. Like on an audo tape cover, "Track two (5:36)" etc. So you'd skip to 5:36 to listen to track 2 on a tape. The audo on a cd is like a tape, but digital - just 1 long file, but the computer can work out where each track starts and stops.
Windoze makes up .cda files, but they don't actually exist. It also makes up the CDFS filesystem, which van refer to various iso filesystems or UDF.

---

### Post by user1397 on 2006-10-03
> **alecjw said:**
> There are no files on a CD.
I think this is how a CD works.
There's a few bytes of data at the beginning of the CD saying something like "Track 1 starts at memory unit 0x635b6da6f, Track 2 starts at 0x578d5686c87e" etc. Like on an audo tape cover, "Track two (5:36)" etc. So you'd skip to 5:36 to listen to track 2 on a tape. The audo on a cd is like a tape, but digital - just 1 long file, but the computer can work out where each track starts and stops.
Windoze makes up .cda files, but they don't actually exist. It also makes up the CDFS filesystem, which van refer to various iso filesystems or UDF.arite, thanks for clearing that up with me.

---

### Post by disembodied on 2007-02-20
I am not sure if you found the program you were looking for to convert from DRM protected WMA to ogg or not (let us know if you did and what it is)... but if you still have windows (because it relies on the .net framework) there is a program called muvaudio2 ([http://www.muvaudio.com](http://www.muvaudio.com)) that is legal and will get rid of DRM protection and convert the file to multiple formats (including ogg vorbis).
It costs something like $20 but its worth it (I own it and use it on windows to convert everything) and it works really well. Basically it functions by playing the song and re-recording the sound... but it does it with 'virtual cables' that allow you to do more then one at a time and also avoids getting computer sounds and what not.

Hope that helps, this program is seriously amazing - the songs sound perfect (since its not converting from one lossy format to another, its actually 'playing' the song and rerecording it in a new format) and its pretty easy to use.

-Marcus

---

### Post by sinisterstuf on 2010-05-20
In windows if you view the contents of an audio CD there is a list of files in .cda format (which I always assumed stood for CD Audio). Copying these files to your hard disk is useless. They are very small and may just be links to data on the CD that might be organised as one of the previous commenters said.

---

### Post by K.Mandla on 2010-05-20
Thread closed. Necromancing. Moved to Multimedia and Video.

---

