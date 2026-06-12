---
title: "Alternative to YAMB?"
date: 2010-10-13
forum: Multimedia Software
---

### Post by edco76 on 2010-10-13
[FONT=Verdana][SIZE=2]I have some video files that are in [/SIZE][/FONT][FONT=Verdana][SIZE=2]H.264/MPEG-4 with 5.1ch AAC audio. I also have the 2 channel audio. I cant stream or play MPEG-4 w/5.1 with my 360 so I need to remux the video with the 2 channel audio. Its easy as pie with YAMB but how can I do it with Linux?[/SIZE][/FONT]

---

### Post by ron999 on 2010-10-13
> **edco76 said:**
> [FONT=Verdana][SIZE=2] Its easy as pie with YAMB but how can I do it with Linux?[/SIZE][/FONT]

Hi
YAMB is a GUI for the program MP4Box.
I don't know of an equivalent for Linux.

MP4Box is the command-line program.
To install MP4Box with Ubuntu it's part of the package named **gpac** from the Ubuntu repository.

And the gpac website is here:- [http://gpac.sourceforge.net/doc_mp4box.php]("http://gpac.sourceforge.net/doc_mp4box.php")

---

### Post by edco76 on 2010-10-13
> **ron999 said:**
> Hi
YAMB is a GUI for the program MP4Box.
I don't know of an equivalent for Linux.

MP4Box is the command-line program.
To install MP4Box with Ubuntu it's part of the package named **gpac** from the Ubuntu repository.

And the gpac website is here:- [http://gpac.sourceforge.net/doc_mp4box.php](http://gpac.sourceforge.net/doc_mp4box.php)
Thanks. Could Avidemux do what I need to do?

---

### Post by ron999 on 2010-10-13
> **edco76 said:**
> Thanks. Could Avidemux do what I need to do?

I dunno.

Does your file need to be mp4, or will it be OK to use mkv file for the job?

---

### Post by edco76 on 2010-10-13
> **ron999 said:**
> I dunno.

Does your file need to be mp4, or will it be OK to use mkv file for the job?
Needs to stay mp4. 360 wont play mkv I'm pretty sure.

---

### Post by edco76 on 2010-10-13
also, I really want to avoid actually encoding the entire video. That takes forever. Before I was able to cut the 5.1 audio and add the 2ch in like 5 minutes for a whole movie.

---

### Post by ron999 on 2010-10-13
OK, get your head around MP4Box.

First find out the tracks inside your mp4 file like this:-
```
MP4Box -info filename.mp4
```
This will show your track ID numbers 1, 2, 3 etc.

Choose which tracks you need then create a new mp4 file like this example:-

```
MP4Box -add filename.mp4#trackID=1 -add filename.mp4#trackID=2 newfile.mp4
```

Using MP4Box doesn't re-encode. It just re-packages (very quickly).

---

### Post by edco76 on 2010-10-13
> **ron999 said:**
> OK, get your head around MP4Box.

First find out the tracks inside your mp4 file like this:-
```
MP4Box -info filename.mp4
```This will show your track ID numbers 1, 2, 3 etc.

Choose which tracks you need then create a new mp4 file like this example:-

```
MP4Box -add filename.mp4#trackID=1 -add filename.mp4#trackID=2 newfile.mp4
```Using MP4Box doesn't re-encode. It just re-packages (very quickly).
I got an error

```
Error - 2 input names specified, please check usage

```

---

### Post by ron999 on 2010-10-13
Is the 2-channel audio in a different file than the video?

---

### Post by edco76 on 2010-10-13
> **ron999 said:**
> Is the 2-channel audio in a different file than the video?
Yeah. Even a different folder. Here is what I am entering

```
MP4Box -info The Fourth Kind.mp4

```

I dont have any other files named that.

---

### Post by ron999 on 2010-10-13
You have spaces between the words in the file name.
So put it in quotes. 
MP4Box -info "The Fourth Kind.mp4"

---

### Post by edco76 on 2010-10-13
> **ron999 said:**
> You have spaces between the words in the file name.
So put it in quotes. 
MP4Box -info "The Fourth Kind.mp4"
```
Error opening file The Fourth Kind.mp4: Requested URL is not valid or cannot be found

```

---

### Post by ron999 on 2010-10-13
OK
Look for a different program to use instead of MP4Box.

---

### Post by edco76 on 2010-10-13
> **ron999 said:**
> OK
Look for a different program to use instead of MP4Box.
lol ok. Thanks for the help anyway.

---

### Post by edco76 on 2010-10-14
bump.

Still no luck.

---

### Post by ubuntubrian on 2011-06-15
I just found this thread and I installed MP4BVox yesterday, works great. I got the same error about the URL and realized that it was spaces in the file name. I didn't put it in quotes, I renamed it without spaces and the error resolved.

---

