---
title: "Digital Picture Workflow"
date: 2013-02-03
forum: Multimedia Software
---

### Post by ianp5a on 2013-02-03
Does anyone use an integrated workflow for dealing with photos that includes my requirements?:
1) Integrated import from Camera (USB) Including video files.
2) Non destructive tweaking. Crop/Curves/White balance/sharpen etc.
3) Integrated Upload. To Flikr/Picasa etc.
There should be no file renaming and mamagement. So preferably a single application like Shotwell.

I've tried several programs but none do all 3 steps seamlessly
[FONT="Courier New"]
**Program.....Import..Non-Detruct..Tweak..Upload**
----------------------------------------------------
**Shotwell**.....Good......OK........Poor...Good
**Digikam**......Good......no........Good...Good
**Raw Therapee**..no.......OK........Good....no  
**Darktable**.....OK.......OK........OK......OK
**F-Spot**........OK.......OK........OK......OK (added. Thanks)
[/FONT]
OK it seems that when collating this table, I've discovered that Darktable ticks all the boxes. We have a winner!

I'm posting this question anyway to see if anyone has an alternative solution for an integrated workflow solution. Or corrections to my table.

I find Darktable the most confusing of all the programs as well. So I'm not sure if it imports video files. Meaning I'd have to check each time then use another program after all.

---

### Post by N00b-un-2 on 2013-02-03
F-Spot was awesome back in the day.  Haven't used it in a long time though.

---

### Post by ianp5a on 2013-02-03
Thanks for the reminder. F-Spot also appears to be an all rounder.

---

### Post by ianp5a on 2013-02-04
Question. There appears to be very few photgraphic discussions here. Is there somewhere else all the photographers on Ubuntu go? Or am I missing something?

---

### Post by xc3RnbFO8P on 2013-02-04
> **ianp5a said:**
> Question. There appears to be very few photgraphic discussions here. Is there somewhere else all the photographers on Ubuntu go? Or am I missing something?

You could start a thread on the Café

Have you tried Picasa 3.9 on PlayonLinux 4.1.9
[http://ompldr.org/vaDd3aQ/Picasa%203.9%20linux.png]("http://ompldr.org/vaDd3aQ/Picasa%203.9%20linux.png")

---

### Post by ianp5a on 2013-02-04
Thanks: I stopped using Picasa when they dropped the Linux version.
It did a good job. Except the Linux version didnt cope with Video. And I'm not sure about Raw. But I get the impression they dont want to support it.

---

### Post by ianp5a on 2013-02-14
I'm still keen to hear if anyone else has a better workflow. But so far, here is the state of my progress:

_Old way with **JPEGs** only._
**Import - Browse - Tweak - Upload**: = Shotwell
**Pros**: - This all works seamlessly with non-destructive editing avoiding fiddling with filenames.
**Cons**: - Many tweaking commands are missing. Sharpening and contrast controls and curves. Raw handling is confusing as Shotwell is trying to be too clever.

_Working with **Raw**:_
**Card Import** = Rapid Picture Downloader. Others were not so flexible
**Browse/Manage ** = DigiKam
**Tweak Jpegs** = DigiKam (Non Destructive)
**Raw Develop** = Raw Therapee  (others were tricky)
**Web Upload** = DigiKam

I'm still verifying this process but, unlike my happy JPG only days, where Shotwell did all my tasks in one program, I'm now using separate programs with DigiKam as the core manager. All 3 programs mentioned above are very customisable to allow the  workflow to work.

So far I've tested: Shotwell, Raw Therapee, Darktable, F-Spot, Gwenview, Rawstudio, Digikam, Rapid Picture Downloader, Fotoxx
TODO: Geeqie, GTKRawGallery, Photivo, UFRaw, Darkroom, gThumb

Please let me know if I'm missing a trick!

---

### Post by eric-yorba on 2013-02-14
Anything in particular you'd like to see in Shotwell's RAW support?  We're trying to fix a bunch of RAW issues for 0.14.

---

### Post by ianp5a on 2013-02-15
Eric

Regarding photo management, Shotwell creates jpegs from raw on the fly with "_shotwell_ in the file name. However these appear as new separate pictures. This confuses me. Are they meant to appear separate files?

Also, these 'new' jpegs appear very dark. Regardless of the developer chosen.

Regarding developing raw, the dedicated raw development tools have very many adjustments, all seen as essential to the various users. However they are all complex to use. A simplified toolset would be welcomed. Picasa does a good job here. Where multiple previews let you shoose the result you want.  If anyone needs more they will use the specialist tools anyway. 

Regarding adjusting jpegs, 'Sharpen', and 'contrast' adjustments would be essential additions.

Shotwell does a good job covering the entire jpeg workflow. I appreciate it more now I'm having to use lots of individual programs.

---

### Post by eric-yorba on 2013-02-15
> **ianp5a said:**
> Regarding photo management, Shotwell creates jpegs from raw on the fly with "_shotwell_ in the file name. However these appear as new separate pictures. This confuses me. Are they meant to appear separate files?

Also, these 'new' jpegs appear very dark. Regardless of the developer chosen.

When you have the developer set to "Shotwell," it will develop photos behind the scenes and name them as you described.

In Shotwell 0.11-0.13, the support for the camera developer isn't great due to a number of bugs.  We've already got most of this fixed for the upcoming 0.14 release.

> Regarding developing raw, the dedicated raw development tools have very many adjustments, all seen as essential to the various users. However they are all complex to use. A simplified toolset would be welcomed. Picasa does a good job here. Where multiple previews let you shoose the result you want.  If anyone needs more they will use the specialist tools anyway. That's not a bad idea, actually.  Someday we'd like to offer full, parametrizable RAW development, but that's pretty far off (unless we get some big donations and/or a lot of outside contributions!)

Another thing we'd like to do is to make sending RAW files to external developers a smoother process.

> Regarding adjusting jpegs, 'Sharpen', and 'contrast' adjustments would be essential additions.The current color adjustments should let you adjust contrast.  As for sharpen, we do have a ticket for that:
[http://redmine.yorba.org/issues/690](http://redmine.yorba.org/issues/690)

---

### Post by ianp5a on 2013-02-17
Thanks Eric. Can't wait.

---

