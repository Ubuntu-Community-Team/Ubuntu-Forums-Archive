---
title: "Can you provide insight as to the intermediate files of DeVeDe DVD authoring"
date: 2012-01-09
forum: Multimedia Software
---

### Post by rocksockdoc on 2012-01-09
I'm trying to learn how to author a DVD disc starting from avi and mp4 files.

Choosing to use DeVeDe on Ubuntu, I selected two movies, one as an MP4 and another as two AVIs and burned those to a DVD disc using DeVeDe 3.16.8 ... and I was just wondering about the purpose and potential use of the intermediary files before I deleted them.

Given this listing of the files, is my assumption of what can be done with them correct?

By way of starting point, this is just the input 1st movie as a mpeg-4 file (with subtitles):

[LIST]
[*]2,342,780,295 bytes --> movie.mp4
[*]4,096 bytes --> Subtitle directory
[/LIST]
And this is the 2nd input movie as two avi files (no subtitles):

[LIST]
[*]733,892,608 bytes --> movie_1of2.avi
[*]731,940,864 bytes --> movie_2of2.avi
[/LIST]
Here is the final output  DVD iso containing the two movies, subtitles, & a menu:

[LIST]
[*]4,129,222,656 bytes --> movie.iso
[/LIST]
I realize the VIDEO_TS & AUDIO_TS directories are simply the DVD in a 'data' format as opposed to a DVD ISO format (where the backup, information, and video files are in whatever order the operating system dictates and not in a "DVD order"):

[LIST]
[*]18,432 bytes --> VTS_01_0.IFO  (these are the information files)
[*]18,432 bytes --> VTS_01_0.BUP (these backup files are stored farthest away from their VOB counterparts in a DVD ISO format but not here in the list directory format)
[*]5,820,416 bytes --> VTS_01_0.VOB (these are the video files)
[*]45,056 bytes --> VTS_01_1.VOB
[*]61,440 bytes --> VTS_02_0.IFO
[*]61,440 bytes --> VTS_02_0.BUP
[*]45,056 bytes --> VTS_02_0.VOB
[*]1,073,709,056 bytes --> VTS_02_1.VOB
[*]66,238,464 bytes --> VTS_02_2.VOB
[*]49,152 bytes --> VTS_03_0.IFO
[*]49,152 bytes --> VTS_03_0.BUP
[*]45,056 bytes --> VTS_03_0.VOB
[*]79,8,226,432 bytes --> VTS_03_1.VOB
[*]79,872 bytes --> VTS_04_0.IFO
[*]79,872 bytes --> VTS_04_0.BUP
[*]45,056 bytes --> VTS_04_0.VOB
[*]1,073,709,056 bytes --> VTS_04_1.VOB
[*]1,073,709,056 bytes --> VTS_04_2.VOB
[*]36,227,072 bytes --> VTS_04_3.VOB
[*]45,056 bytes --> VIDEO_TS.VOB
[*]14,336 bytes --> VIDEO_TS.IFO
[*]14,336 bytes --> VIDEO_TS.BUP
[/LIST]
**But what good (or use) can be made of these intermediary MPG movie files?**

These appear to be the original two-part equal-sized AVI movie (now converted to two unequal-sized mpg files):

[LIST]
[*]1,139,947,520 bytes --> movie_01_01.mpg
[*]798,226,432 bytes --> movie_01_02.mpg
[/LIST]
And this apears to be the original mp4 file converted to an mpg file:

[LIST]
[*]2,189,510,656 bytes --> movie_02_01.mpg
[/LIST]
This must be the subtitles:

[LIST]
[*]72,167 bytes --> movie_sub_tmp.sub
[/LIST]
This appears to be the menu wording (with a transparent background):

[LIST]
[*]3,507 bytes --> movie_menu0_bg_active_out.png
[*]1,437 bytes --> movie_menu0_bg_inactive_out.png
[/LIST]
These appear to be the static menu background:

[LIST]
[*]84,527 bytes --> movie_menu0_bg.png
[*]3,566 bytes --> movie_menu0_bg_select_out.png
[/LIST]
These appear to be the same menu itself (as a static 30-second video file):

[LIST]
[*]5,816,320 bytes --> movie_menu_0.mpg
[*]5,822,464 bytes --> movie_menu2_0.mpg
[/LIST]
And, I have no idea what these might be useful for:

[LIST]
[*]3,453 bytes --> movie.xml
[*]502 bytes --> movie_menu_0.xml
[/LIST]
Any clarification from the experts as to what purpose these intermediate files serve, and more importantly, what future purpose can be made of them would be great!

---

