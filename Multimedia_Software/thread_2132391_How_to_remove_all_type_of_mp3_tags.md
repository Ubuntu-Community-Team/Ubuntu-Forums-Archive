---
title: "How to remove all type of mp3 tags?"
date: 2013-04-04
forum: Multimedia Software
---

### Post by ilcontegis on 2013-04-04
Hello

I generally use exfalso and easytag to tag my mp3 but this time I am really having an hard time!
I got some mp3 from a friend, and I wanted to change the tag. Doesn't matter what I change after saving everything comes back how it was. Even if I delete completely the id3 tag everything returns back to how it was.

Do you have any idea of what happened? I guess those mp3 are using another type of tagging which is not id3 nor ape...but I have no clue how to see that.
The best for me would be to clean up completely the mp3 but I have no idea how to do that.

I would be happy to receive your assistance if possible.
Thank you!

---

### Post by kostkon on 2013-04-04
Try the following, it works for me:

In EasyTag, press CTRL+A to select all the files in question, then select *File &#8594; Remove Tag(s)* from the menu, and then CTRL+S or press the save button to save the changes; after doing that **close** EasyTag and then reopen it, select the files you want again, start tagging them and then save the changes and you should be fine.

You may need to repeat the above steps more than once.

The problem could be that your files have already id3v1 tags embedded in them and it appears that some players/libraries give them precedence over the id3v2 tags (that easytag creates) when they need to show the track info.

---

### Post by ilcontegis on 2013-04-05
Thank you for your answer. Unfortunately it did not work.
By doing your technique, I just cancel the id3v2 tags, but once I reopen easytag all the information is still there. I cannot get rid of it.

Any other suggestions?

This is the content of one of the mp3

> ##@]
LAME3.96.1
"TALB
Set the World on FireTCON
MetalcoreTIT2
01. New ReligionTPE1
Black Veil BridesTPE2
Black Veil BridesTRCK
1TYER
20113DI


Thank you

---

### Post by kostkon on 2013-04-05
> **ilcontegis said:**
> Thank you for your answer. Unfortunately it did not work.
By doing your technique, I just cancel the id3v2 tags, but once I reopen easytag all the information is still there. I cannot get rid of it.
Yes, once you cancelled your tags, did you repeat the process to cancel the bad ones??

By that I mean, reopen easytag, find the tags you want to get rid of, select remove all tags again, save, exit and reopen?

---

### Post by FakeOutdoorsman on 2013-04-05
Example using ffmpeg:
```
ffmpeg -i input.mp3 -codec copy -map_metadata -1 output.mp3
```

---

### Post by ilcontegis on 2013-04-06
Thank you.

I installed sound converter and I made .ogg files.
Then I manually created the tag files as they became empty.
That took a bit of time but at least I could somehow solve my problem.

Thank you very much!

---

### Post by FakeOutdoorsman on 2013-04-06
Re-encoding isn't the optimal solution, but maybe I misunderstood what you were trying to do.

---

