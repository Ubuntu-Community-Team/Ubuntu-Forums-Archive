---
title: "Help converting Movies"
date: 2010-02-28
forum: Multimedia Software
---

### Post by skibum3027 on 2010-02-28
I'm trying to convert my movie collection from DVD format (Video_TS and Audio_TS folders) into something a lttle less space hogging. It's important to me that I still have a quality recording. What is the best way to go about this? In case it matters I'm using Kubuntu 9.10 Karmic (64 bit)
I've looked at...

dvd:rip - I can't get the transcode button to be clickable
acid-rip - fails to load anything in the dvd folder format
k9copy - crashes every time i start a rip
winff - no support for dvd folder format

In windows I used to use DVDfab for this process. What's the best way of approaching this? What file size should I leave for each dvd? Is this process really worth my time or should I just suck it up and go buy another 2 tb?

I googled all of this... and tried lots of things... so it's possible (if not likely) that I screwed at least one of these apps up that should otherwise be working just fine...

---

### Post by linux_paul on 2010-03-02
k9copy has always been my personal choice for easy/reliable backups of movies, but as of late it doesn't seem to work. Still looking for a reason why. I never had much luck with any of the others.

I'm considering creating a windows Virtual Box machine to try backing up dvds.

---

### Post by Enigmapond on 2010-03-02
Try winff...this is a great programme works very well. It a GUI for ffmpeg.

EDIT: Sorry I missed that fact that you tried this already...oops

---

### Post by Chemical Imbalance on 2010-03-02
Maybe give Avidemux a try?  
Not sure if it will read those DVD ripped folders though...

---

### Post by linuxloon on 2010-03-02
I've had good luck with HandBrake

---

### Post by chewearn on 2010-03-02
**Which application to use?**
I have personally used Avidemux before for the transcoding.

Pros:
1. a lot of options to play with, if you want to preserve the best quality possible while squeezing file size as far as possible.
2. have options to adjust pixel aspect ratio (necessary, because DVD-Video mpeg stream is not 1:1 compared to typical PC video files)
3. options for de-interlacing (required for DVD-Video which are encoded in interlaced format, while typical PC video format is non-interlaced).
4. option for cropping noise lines around video borders.

Cons:
1. time consuming in deciding which codec to use
2. steep learning curve to understand what each option do what
3. find the best options to set for that particular codec
4. transcoding process itself is time consuming, especially for 2-pass.
5. transcoding will cause worse video quality, no matter what you do because it's lossy compression (though it can be minimised to be imperceptible)

[B]Worth it to convert video, or just pony up for larger storage?
[/B]1. depending on how many DVD-Video you have
2. how much time you are willing to devote to it
3. or how much cash you are willing to spend on larger storage to make the problem go away

---

