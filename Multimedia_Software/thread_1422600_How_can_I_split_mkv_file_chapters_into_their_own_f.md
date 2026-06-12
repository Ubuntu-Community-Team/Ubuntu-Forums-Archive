---
title: "How can I split mkv file chapters into their own files?"
date: 2010-03-05
forum: Multimedia Software
---

### Post by BatPenguin on 2010-03-05
Hello all,

I've tried researching this quite a bit but cannot seem to find a way to do this. So, what I have is a DVD (a kids' DVD) that I've ripped as an MKV file. It's music, so there's plenty of different songs, like over 50...lots of chapters. Now it's one big, nice MKV with proper chapters and all...but the problem is of course that "play that song" is hard to do, have to skip around. So, I'd like to split all these chapters into their own files, that'd be much easier to manage.

I've install mkvextra, mkvmerge, mkvmerge-gui etc. but I cannot seem to find a way to either in the gui or on the command line to just get it to split the file according to the existing chapter information. Apparenlty if I spent the whole day writing down timecodes, I might create a monster command line that could do it, but there's gotta be an easier way. Does anybody have any tips about how to do this? Perhaps a way of extracting the chapter times from the file into a txt file and using that as an input for the "mkvmerge --split" command. Does anybody have ideas about how to do this?

Thanks in advance.

---

### Post by killerbyteeire on 2011-08-23
One way of doing this is using the chapter editor in mkvmerge gui to export an xml of the chapter information. Then using excel or other spreadsheet software select the chapter start times. You can put the times in a row and then export to csv. The text in the csv file can be directly pasted into the split after timecodes box in mkvmerge gui.

The times have to be in chronological order however because the splitting doesnt work properly then and mkv files of about 1 mb are created.

Slow and tedious I know but I cant find any software that do this automatically at the moment. Hopefully someday somebody will make software that can do this automatically.

---

### Post by handy on 2011-08-23
Couldn't you just go through with DeVeDe & cut the .mkv chapters up into individual files?

---

### Post by qyot27 on 2011-08-23
MediaInfo ([PPA](https://launchpad.net/~shiki/+archive/mediainfo), or [manual download](http://mediainfo.sourceforge.net/en/Download/Ubuntu)) will display the chapter times.  Just copy the chapters readout/dump the results to a file, format it a bit more properly, and give it to mkvmerge's split by timecodes function as previously mentioned by killerbyteeire.
```
mediainfo input.mkv
```
The chapters will be listed at the end, under the Menu category.


[quote=handy]Couldn't you just go through with DeVeDe & cut the .mkv chapters up into individual files?[/quote]
The OP was talking about music, and in any case this wouldn't be lossless unless DeVeDe allows for Direct Stream Copy operations.



Of course, considering the OP is 17 months old, this is probably just a post for posterity's sake.

---

