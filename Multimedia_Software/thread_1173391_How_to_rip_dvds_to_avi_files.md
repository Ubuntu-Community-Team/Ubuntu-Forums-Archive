---
title: "How to rip dvds to avi files?"
date: 2009-05-29
forum: Multimedia Software
---

### Post by cody7002002 on 2009-05-29
Is there a free program out there for ripping dvds that doesn't leave a watermark or anything? Is ripping a dvd complicated? I've never done it before

---

### Post by monsterstack on 2009-05-29
Acidrip is the programme I use for ripping DVDs. You can find some tutorials by Googling, but it isn't that hard to get going. Beware if you're American, though. The DMCA is pretty hard on people ripping DVDs, the last time I checked. I think acidrip depends on a couple of bits from the Medibuntu repositories, too.

Edit: Yeah it does:
```

acidrip
  Depends: perl
  Depends: libgtk2-perl
  Depends: lsdvd
  Depends: mplayer
    mplayer-nogui
  Depends: mencoder

```

I think the legal issues in the DMCA are to do with circumventing the copyright protection in DVDs, and not with actually ripping them itself.

---

### Post by mamamia88 on 2009-05-29
handbrake

---

### Post by logos34 on 2009-05-29
handbrake is nice, but I actually think dvdrip is better, more features/controls

---

### Post by Hallvor on 2009-05-29
dvd:rip is top notch for making quality AVIs.

---

### Post by SuperSonic4 on 2009-05-29
I think k9copy is the best choice.

---

### Post by kinematic on 2009-05-29
And those who actually know what they're doing use mencoder.

---

### Post by Uruz2012 on 2009-05-29
dvd::rip
 
Tons of option with sensible defaults. The only problem I have with it is that it doesn't support matroska. 
 
Not to derail the thread but does someone know of a program that handles mkv other than OGMRip?

---

### Post by burvowski on 2009-05-29
Somewhat related, and it saves creating a new thread:

I was burning some dvds I downloaded as ISO files to DVDs, and I got all of them right except for I messed up one and literally burned the video_ts and audio folder as a data file to the disc. Is there anyway to rip it to avi without reburning it as a video dvd first? I hope that question is worded to make sense

edit: **** I just realised I misused "literally", I think :lol:

---

### Post by monsterstack on 2009-05-29
> **burvowski said:**
> Somewhat related, and it saves creating a new thread:

I was burning some dvds I downloaded as ISO files to DVDs, and I got all of them right except for I messed up one and literally burned the video_ts and audio folder as a data file to the disc. Is there anyway to rip it to avi without reburning it as a video dvd first? I hope that question is worded to make sense

edit: **** I just realised I misused "literally", I think :lol:

You mean just transcode the .vob file to an .avi? Sure you can do that. I don't know about the GUI programmes that allow you to do it, but you can always just use ffmpeg. Something like this should do the trick:

```
ffmpeg -i **your_film.vob** -sameq **your_film.avi**
```

This command will convert the VOB file to an avi using the ffmpeg defaults. According to the ffmpeg documentation, though, perhaps this command might be better:

```
ffmpeg -i **your_film.vob** -f avi -vcodec mpeg4 -b 800k -g 300 -bf 2 -acodec libmp3lame -ab 128k **your_film.avi**
```

Where the options are,
[LIST]
[*]-f controls the type of output (avi);
[*]-vcodec controls the output video format;
[*]-b controls the bitrate;
[*]-g controls the frame skipping for smooth playback;
[*]-bf uses b-frames to make the output compatible with more players;
[*]-acodec chooses the audio conversion
[*]-ab controls the bitrate of the audio.
[/LIST]

Whew.

---

### Post by burvowski on 2009-05-29
Thanks! I'm going to give that a shot. Sorry, but I'm sort of new to terminal...how would I point it at the file I want to convert? I assume I can't simply type in just the file name, right?

---

### Post by monsterstack on 2009-05-29
No, that's right. You need to write the full path to the file. You can use Nautilus to help you out. Navigate to the folder with the vob file you want to convert and look at the toolbar of Nautilus. It will show you what folder you are in, either as icons, or as text. You can switch between the two by pressing the little button on the left. Select the text, which will look something like this:

```
/home/burvowski/DVDRIP/some_film/
```

Paste that into a terminal, but put "cd" at the beginning. Like this:

```
cd /home/burvowski/DVDRIP/some_film/
```

You will be in that directory now. Check that you're in the right directory by listing the contents of it with the "ls" command. Just type "ls" and hit enter. You should see the vob file in the list of files. Good! Now you can just go ahead and run the ffmpeg command from here, and just typing the name of the file will work. The output avi file will appear (after some amount of time), in the same folder as the vob file.

```
ffmpeg -i **your_film.vob** -sameq **your_film.avi**
```

It's worth pointing out, though, that doing the following command will work from any directory:

```
ffmpeg -i **/home/burvowski/DVDRIP/some_film/your_film.vob** -sameq **/home/burvowski/DVDRIP/some_film/your_film.avi**
```

This is useful if you want to rip the .vob from a dvd, because you can tell ffmpeg to make the avi go anywhere:


```
ffmpeg -i **/media/DVD/your_film.vob** -sameq **/home/burvowski/DVDRIP/some_film/your_film.avi**
```

I hope I managed to explain myself well enough. Good luck!

---

### Post by burvowski on 2009-05-29
Perfect instructions. Thanks a lot!

---

### Post by monsterstack on 2009-05-29
> **burvowski said:**
> Perfect instructions. Thanks a lot!

Whew. When giving people advice about terminal instructions I always feel like I've made a mistake somewhere. Used one on a regular basis for two years now, and given advice to people about it for months. You'd have thunk I'd have overcome stage fright by now.

---

### Post by cariboo on 2009-05-30
This really doesn't belong here. Moved to Multimedia & Video

---

