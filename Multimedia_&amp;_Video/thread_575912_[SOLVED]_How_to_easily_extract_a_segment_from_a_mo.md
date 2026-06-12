---
title: "[SOLVED] How to easily extract a segment from a movie / concatenate movies together?"
date: 2007-10-14
forum: Multimedia &amp; Video
---

### Post by berliita on 2007-10-14
1. I've got a huge MPG file of a full feature film in my hard-drive. I'd like to copy a single scene from the movie into an MPG file of its own. I know the start and end times of the scene i'm interested in. How can i accomplish this task? One way would be to employ Kino or Cinelerra, but this would entail a lengthy import stage. I'd like to avoid that. Is there an easier way to go about it, preferably a  shell command?

2. I've got several MPG files in my hard-drive, representing different scenes of the same movie. I'd like to reconstruct the original movie, by concatenating the scenes together into a single MPG file. I could use Kino or Cinelerra. But Is there a simpler way to do this, such as a shell command?

---

### Post by oxenfrogga on 2007-10-14
Hi berliita,

most probably transcode will solve your needs. It got a GUI: gtranscode.

Harald

---

### Post by berliita on 2007-10-15
Thanks, oxenfrogga,
Could you give some examples of its use? It's a rather complex application, and its documentation is not very friendly.

---

### Post by orange2k on 2007-10-15
Avidemux is much easier to operate in my experience...

---

### Post by anaconda on 2007-10-15
mencoder is "easy":
```
 mencoder movie.mpg -o movie2.mpg -ovc copy -oac copy -ss 5:00 -endpos 8:00
```

THis would take 5min-8min from the first movie.mpg ans save it to the movie2.mpg.

(actually I dont remember if this starts from 5min and continues 8 minutes after that or would it start from 5 min and stop at 8 min, whatever..)

and to combine 2 videos: 
mencoder movie2.mpg movie3.mpg -o movie_combined.mpg -ovc copy -oac copy 

[http://bro1.centras.info/mencoder_editing.html](http://bro1.centras.info/mencoder_editing.html)

---

### Post by berliita on 2007-10-15
Thanks, orange2k and anaconda, for your replies.

orange2k, i was able to use Avidemux to concatenate two movies, by opening the first one, and then appending the second one using the File->Append... dialog. That's cool. However, i couldn't figure out how to create a new movie from a fragment of another one. I guess one should begin by marking the selected interval using the "Set Marker A" and "Set Marker B" items of the "Edit" menu. But how does one proceed from there? There's a "Save Selection as JPEG images..." option on the "Save" submenu of the "File" menu, but no "Save Selection as MPG movie...".

anaconda, your concatenation command worked like a charm. But the copy-and-paste command copied only the audio track; the picture was not copied along. And by the way, the "ss" and "endpos" options take seconds as input, and the "endpos" option determines the time interval, so in order to copy the fragment of "movie.mpg" from 5:00 (min) to 8:00 (min), the value of the "ss" option should be 300 (5 min x 60 sec) and the value of the "endpos" option should be 180 (3 min x 60 sec).

---

### Post by orange2k on 2007-10-15
> **berliita said:**
> Thanks, orange2k and anaconda, for your replies.

orange2k, i was able to use Avidemux to concatenate two movies, by opening the first one, and then appending the second one using the File->Append... dialog. That's cool. However, i couldn't figure out how to create a new movie from a fragment of another one. I guess one should begin by marking the selected interval using the "Set Marker A" and "Set Marker B" items of the "Edit" menu. But how does one proceed from there? There's a "Save Selection as JPEG images..." option on the "Save" submenu of the "File" menu, but no "Save Selection as MPG movie...".


Once youve selected marker A and B, just select save and you will extract that part of the movie to a seperate file...

---

### Post by berliita on 2007-10-15
Thanks, orange2k, it works. One little snag, though: i tried to copy and paste from a MOV file, and it only copied the picture; not the soundtrack. But i can always convert to MPG first.

---

### Post by berliita on 2007-10-15
Oh dear! orange2k, i'm afraid there's a slight problem i've just noticed. Namely, the soundtrack is copied at double speed. I didn't notice it before, because i was experimenting on a silent movie... (Well, it had background music, but the music sounded normal to me even when playing at double speed...)

The problem seems to rest with the format of the input file. When i use MPG as the input file format, the soundtrack is copied correctly; but when i use MP4 as the input file format, the soundtrack is copied at double speed. Do you know how to overcome this, or, alternatively, how to convert an MP4 format to an MPG?

---

### Post by orange2k on 2007-10-15
> **berliita said:**
> Oh dear! orange2k, i'm afraid there's a slight problem i've just noticed. Namely, the soundtrack is copied at double speed. I didn't notice it before, because i was experimenting on a silent movie... (Well, it had background music, but the music sounded normal to me even when playing at double speed...)

The problem seems to rest with the format of the input file. When i use MPG as the input file format, the soundtrack is copied correctly; but when i use MP4 as the input file format, the soundtrack is copied at double speed. Do you know how to overcome this, or, alternatively, how to convert an MP4 format to an MPG?

Well, I have to admit, I have only tried Avidemux on mp4 (xvid in avi container) without mpg conversion. I suggest you take a close look at the available audio settings, maybe there is something there that you can do to make it work right...:confused:

---

### Post by berliita on 2007-10-15
Thanks, orange2k. My mistake, i'm afraid. I hadn't changed the selected item in the "Format" drop-down box to MP4; i'd just saved the selection under a name having a file extension "mp4", expecting the application to figure out the required output format from the extension, like ffmpeg does. But the "Format" drop-down was set to "AVI", not "MP4". So everything's cool. Thanks a lot. :)

I'm leaving this thread open, for the time being, because i'd still like to know how to accomplish the copy-and-paste task using mencoder (or any other command-line utility).

---

### Post by berliita on 2007-10-15
OK. I've got mencoder to perform the task of taking an MP4 file ("input.mp4"), copying the scene that extends from 5:00 min. to 8:00 min., and pasting it in an MP4 file of its own ("output.mp4"), by issuing the following command:
```

$ mencoder input.mp4 -ss 300 -endpos 180 -ovc lavc -ova pcm -o output.mp4

```

If the output file format is to be MPG, simply change "output.mp4" to "output.mpg" in the command above.

If the input file is MPG, you can also use anaconda's suggestion, namely:
```

$ mencoder input.mpg -ss 300 -endpos 180 -ovc copy -ova copy -o output.mpg

```
This command applies whether the output file format is MPG or MP4, as long as the input file format is MPG (but if it's MP4 you must use the former command).

In both cases, if you want the copied fragment to extend from a given second to the end of the movie, just leave the "endpos" option out.

Thank you, anaconda, for doing most of the work of figuring out how to get mencoder to do the tasks i had asked about.

---

