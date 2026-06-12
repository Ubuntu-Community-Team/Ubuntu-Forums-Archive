---
title: "What do you use to split a long MP3 recording?"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by t2000kw on 2007-11-21
I will be recording a convention this weekend on an MP3 player for someone who is handicapped and won't be able to attend. 

I have the option of making several recordings of the talks, which is not convenient at all for me and may miss some information) or to make a long recording in MP3 format for the morning and afternoon sessions, then somehow splitting them into smaller files, one for each talk. 

What do you recommend or what have you used to split MP3 files into smaller ones?

---

### Post by djheadley on 2007-11-22
I use Audacity.

---

### Post by tgalati4 on 2007-11-22
If you are not going to processing (fade in, fade out, EQ, etc) then a good command line tool is sox.

>sudo apt-get install sox
>man sox

---

### Post by dips_xe on 2007-11-22
i second audacity, very easy and quick !

---

### Post by Yellow Pasque on 2007-11-22
I use a command line tool called mp3splt

---

### Post by angelsguitar on 2007-11-22
Audacity has a feature that automatically splits a large recording into several small ones, based on the section markers you put.

---

### Post by t2000kw on 2007-11-22
> **angelsguitar said:**
> Audacity has a feature that automatically splits a large recording into several small ones, based on the section markers you put.

Using Audacity (1.3.3), I tried even selecting part of a file to export and I get the MP3 but I get silence in place of the part I did not select. I used the version Synaptics gave me, but I do have other repositories enabled. Should I uninstall this version, un-enable the other repositories, then reinstall it?

---

### Post by angelsguitar on 2007-11-23
That's weird. I installed mine from Synaptics, and works flawlessly.  Do you have the LAME mp3 libary installed?

---

### Post by eye208 on 2007-11-23
The benefit of using mp3splt instead of Audacity is that the audio stream will not be re-encoded, i.e. there will be no loss of quality. Audacity can only handle uncompressed audio; anything else needs to be converted from and to the compressed format, introducing artifacts in the case of lossy compression.

There is also a graphical front-end for mp3splt, but it is not in Ubuntu's repositories yet.

See here for more info: [http://mp3splt.sourceforge.net/](http://mp3splt.sourceforge.net/)

---

### Post by t2000kw on 2007-11-23
> **angelsguitar said:**
> That's weird. I installed mine from Synaptics, and works flawlessly.  Do you have the LAME mp3 libary installed?

Yes, both lame and lame extras, in case it mattered. I get MP3 encoding, and I can export the changed wav file in the tutorial to an MP3 without a problem as far as making it an MP3.

---

### Post by t2000kw on 2007-11-23
> **eye208 said:**
> There is also a graphical front-end for mp3splt, but it is not in Ubuntu's repositories yet. See here for more info: [http://mp3splt.sourceforge.net/](http://mp3splt.sourceforge.net/)

Which of the three files here do I need to download?

[http://mp3splt.sourceforge.net/mp3splt_page/home.php](http://mp3splt.sourceforge.net/mp3splt_page/home.php)

and is the version for Dapper working in later versions?

---

### Post by angelsguitar on 2007-11-23
> **t2000kw said:**
> Yes, both lame and lame extras, in case it mattered. I get MP3 encoding, and I can export the changed wav file in the tutorial to an MP3 without a problem as far as making it an MP3.

Well, I really don't have any idea about what's happening there. :confused: If you select part of the file and use "Export Selection" it should work alright...

The way I split is placing markers where I want the large file divided (use a marker track for this) and then using the "Export Multiple" command from the File menu.  See if it helps.:)

---

### Post by t2000kw on 2007-11-24
> **angelsguitar said:**
> Well, I really don't have any idea about what's happening there. :confused: If you select part of the file and use "Export Selection" it should work alright...

The way I split is placing markers where I want the large file divided (use a marker track for this) and then using the "Export Multiple" command from the File menu.  See if it helps.:)

I was trying to do it one piece at a time, but it would even be better to do what you mentioned, if only it was apparent to me how to put multiple markers on the file. I can put one at a time, or select a section. Since there is a way to put multiple markers on the file, could you explain how to do that? I've tried holding the control key down while clicking on the split points, which would seem to be the most intuitive way of doing that, but it's not supported.

---

### Post by angelsguitar on 2007-11-24
> **t2000kw said:**
> I was trying to do it one piece at a time, but it would even be better to do what you mentioned, if only it was apparent to me how to put multiple markers on the file. I can put one at a time, or select a section. Since there is a way to put multiple markers on the file, could you explain how to do that? I've tried holding the control key down while clicking on the split points, which would seem to be the most intuitive way of doing that, but it's not supported.

Well, first of all, pardon me, because the correct word in Audacity is Label, not marker.  I initially used the incorrect term and wanted to correct it to avoid confusion.

First, add a Label track by going to Tracks - Add New - Label Track. Then, to add a Label, click on the area you want it first, then press Ctrl+B.  You can set the label's start and finish locators by dragging the small circle (for me it kinda looks like an eye) on the center of the label indicators. Also, you can put a name on the label by clicking on the small square on top of it (the name is important;you can use these names to name the files resulting from the split operation later).  Do this for every marker you need on the file.  After you have your large file with all the labels indicating the sections where you want to split, select File - Export Multiple, configure the options for the split, and that's about it.

Hope this helps.:)

---

### Post by t2000kw on 2007-11-24
Sounds easy enough. I'll get to try this out tomorrow evening with a recorded assembly that would be best split into individual talks instead of simply a morning session and afternoon session. 

Thanks!

> **angelsguitar said:**
> Well, first of all, pardon me, because the correct word in Audacity is Label, not marker.  I initially used the incorrect term and wanted to correct it to avoid confusion.

First, add a Label track by going to Tracks - Add New - Label Track. Then, to add a Label, click on the area you want it first, then press Ctrl+B.  You can set the label's start and finish locators by dragging the small circle (for me it kinda looks like an eye) on the center of the label indicators. Also, you can put a name on the label by clicking on the small square on top of it (the name is important;you can use these names to name the files resulting from the split operation later).  Do this for every marker you need on the file.  After you have your large file with all the labels indicating the sections where you want to split, select File - Export Multiple, configure the options for the split, and that's about it.

Hope this helps.:)

---

### Post by t2000kw on 2007-11-24
> **angelsguitar said:**
>  After you have your large file with all the labels indicating the sections where you want to split, select File - Export Multiple, configure the options for the split, and that's about it.

Hope this helps.:)

I used Export-Multiple but only one of the three test files got exported. It looks like no matter which of the labeled files I click on, even if I "select" all three of my test files, I only get the first one exported. But it does export, so I suppose that I can do it once each time for every file I want to create. It seems as if the multiple option isn't working or requires some other action on my part. The labeling works fine for tht first file, though, whether I use the "sequential numbering" system or actual filenames based on the labels of the track sections made.

---

### Post by angelsguitar on 2007-11-25
> **t2000kw said:**
> I used Export-Multiple but only one of the three test files got exported. It looks like no matter which of the labeled files I click on, even if I "select" all three of my test files, I only get the first one exported. But it does export, so I suppose that I can do it once each time for every file I want to create. It seems as if the multiple option isn't working or requires some other action on my part. The labeling works fine for tht first file, though, whether I use the "sequential numbering" system or actual filenames based on the labels of the track sections made.

Well, that's strange.  :confused: It should work fine. I'm simply out of ideas... Maybe you can try uninstalling and installing their stable version (1.3.3 is a beta version; their stable is 1.2.6 at the moment), or posting a question in the audacity forum ([http://audacityteam.org/forum](http://audacityteam.org/forum)). Hope you can solve the problem.

---

