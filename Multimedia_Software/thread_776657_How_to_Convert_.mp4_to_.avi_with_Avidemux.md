---
title: "How to Convert .mp4 to .avi with Avidemux?"
date: 2008-04-30
forum: Multimedia Software
---

### Post by arashiko28 on 2008-04-30
I have a few days struggling with this. I got tired of looking for a solution to play some .mp4 videos without overclocking my processor and eventually overheating. So All I need is a guide to convert .mp4 to .avi with avidemux or any other video converter. I already have avidemux installed, but tends to confuse me especially because I can't resize the window, but I don't care about that. I want to convert these videos, please help!!!:confused::confused::confused::confused:

---

### Post by uheaven on 2008-05-30
Bump..

---

### Post by prshah on 2008-05-30
> **arashiko28 said:**
> I want to convert these videos, please help!

Try [http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016) for a GUI method.

---

### Post by shirilover on 2008-05-30
I take it you wish to convert a high definition(720p) mp4 file to a standard definition(704x400) avi.

Here is a simple howto -> [http://www.avidemux.org/admWiki/index.php?title=Encoding_animation_with_Xvid](http://www.avidemux.org/admWiki/index.php?title=Encoding_animation_with_Xvid)
requires that you have libxvidcore4 installed.

To reduce the resolution of the video; i.e., 1280x720 -> 704x400, press the filters buttion.
In the list at the left select transform, choose MPlayer resize and press the large + button.
Enter the width and height of the resulting video you wish and select Lanczos3 from the dropdown box, then hit OK.
This should put your resizing filter into the active filters list at the right.

---

### Post by ubuntu-freak on 2008-05-30
I recommend WinFF for video conversion. Complete at least Part 1 & 3 of my [Multimedia & Video How-to](http://ubuntuforums.org/showthread.php?t=766683). All you have to do is copy and paste the relevant commands, then download and install WinFF.
 
Nathan

---

