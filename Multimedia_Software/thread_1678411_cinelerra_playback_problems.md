---
title: "cinelerra playback problems"
date: 2011-01-30
forum: Multimedia Software
---

### Post by mattgeb84 on 2011-01-30
if anyone could help with this issue i'd really appreciate it. I've been loading .mp4 files in cinerella at 720p 1280x720 when i go to play the videos in the timeline they play in slow motion, when i export the video the file it exports is also in slow motion, i put a music file in the time line as well, the music file played fine but the video still played in slow motion, i attached no effects to the video it just played like this as soon as it was imported into cinelerra
can anyone help

---

### Post by BicyclerBoy on 2011-01-30
Sounds like a progressive/interlaced frame/field rate bug ..
This problem has popped up in many apps ..

No actual solution from me sorry, other than find updated versions, look for bug fixes in forums, convert the video with ffmpeg to 720i

---

### Post by wildhostile on 2011-01-31
Hi mattgeb84,

Try to change the Audio device in Settings -> Preferences -> Playback tab (just in case...).
In the Resources window (Media folder), right click + Info on your media to see if the framerate is correct.
You should choose the same framerate in Settings -> Format (Video framerate).
What version of Cinelerra are you using? (Settings -> Preferences -> About tab).

---

### Post by mattgeb84 on 2011-01-31
> **wildhostile said:**
> Hi mattgeb84,

Try to change the Audio device in Settings -> Preferences -> Playback tab (just in case...).
In the Resources window (Media folder), right click + Info on your media to see if the framerate is correct.
You should choose the same framerate in Settings -> Format (Video framerate).
What version of Cinelerra are you using? (Settings -> Preferences -> About tab).

im using cinelerra 2.1.5cv i went to 
i went to the preference tab and changed the audio driver from esound to all other options, no help so i changed back to esound
the framerate is 30fps i chose 30fps in the format video framerate section, it still gave the same error of the audio playing in slow motion 
thanks for trying to help, do you have anything else i should check ??

---

### Post by wildhostile on 2011-02-02
Do you have the same behaviour when playing other video file format and codec?
(.dv, .avi, .mov, .mpeg... ). I think the codec of your video is h264. You could try to convert the video to see if the error is related to the media.
You can also get help on the cinelerra mailing list or the irc channel.

---

### Post by William L Herndon on 2011-02-02
when i try to save my video it shows up as text and when i export it saves each frame by them selfs

---

### Post by BCRailrodder on 2011-02-03
Don't know it this is of any help but I can't run cinerella without a lot of problems due to my memory size (1 gig) - just a thought.

---

### Post by mattgeb84 on 2011-02-03
> **wildhostile said:**
> Do you have the same behaviour when playing other video file format and codec?
(.dv, .avi, .mov, .mpeg... ). I think the codec of your video is h264. You could try to convert the video to see if the error is related to the media.
You can also get help on the cinelerra mailing list or the irc channel.

Yeah it appears conelerra has a problem with the codec of the audio it's a bit of an inconvienience but I have resolved the problem by exporting the audio to a different format
thanks for the help

---

### Post by William L Herndon on 2011-02-03
i have a similar problem in open shot

---

### Post by wildhostile on 2011-02-04
William L Herndon

"Save as..." will let you save your project (as an .xml file that can be edited with a text editor).
Export permit you to export your work (into a video or audio file). You can change the format and codec in the render dialog. It seems that you are trying to export your project into a "sequence" of images (.jpg, .tiff, or .png). You will change the format and codec (the wench tool) according to the size (resolution) of your video and according to what you want to do with it.

---

### Post by William L Herndon on 2011-02-15
i was trying mpeg along with a few others but now im going to make gif cartoons instead which i think would be better but thanks anyway

---

