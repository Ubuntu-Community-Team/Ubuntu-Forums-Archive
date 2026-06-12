---
title: "novie needs help wth getting artist, etc., info for media copied to disk"
date: 2014-02-11
forum: Multimedia Software
---

### Post by squakie on 2014-02-11
I've built a few media centers based around the Raspberry Pi, and use data stored on my desktop to help with that.  I've gotten movies, music, pictures, etc., all working, but not knowing squat about the simplest of things with audio, I could use a little help.  When loaded into XBMC, a lot of the data like artist and album for "albums" or individual songs isn't found.  I've looked through the net, and as best I can tell this can be because some of them (being older or perhaps compiliations) don't have something called ID3 strings.  I found free tool for Windows called MediaMonkey that looked like it might be able to help fix that and perhaps help organize things better for input to XBMC as well.  Searching for mediamonkey in synaptic package manager didn't reveal any ubuntu packages that might have mediamonkey in the description (like "linux equivalent of MediaMonkey").

Is there some gui based tool that can do the same type of thing?  If so, will it do any better at finding album/artist info online than XBMC already does?

---

### Post by varunendra on 2014-02-13
As far as I know, ID3 tags are relevant to only MP3 and similar audio file formats.

Haven't heard of MediaMonkey, but the last time when I was searching for such tools (and I was a Windows user then), the best one I could find was **EasyTag**. But it is audio-only tool. It does not handle video files.

If you think it can be useful for you, it is originally a Linux program and is available in default repositories.

For details/description -
```
apt-cache show easytag
```

To install -
```
sudo apt-get install easytag
```

Powerful tools can also be dangerous (may rename/tag the files incorrectly based on the available wrong information in them). As such, I'd strongly recommend to keep a backup of all your files on which you are going to use it. You may edit their tags in parts, and delete the original copies when you are satisfied that they were tagged correctly (keeping backups is a good idea anyway).

---

### Post by squakie on 2014-02-13
Thanks!  I haven't really checked the file types, to be honest.  I know I "ripped" them (I guess that's the term) from CDs to my hard disk, and one time only when I opened up XBMC it actually showed some things for some of the music.  Since then however it's been gone - only there once and can't seem to get it back.

I think I'll try the tool you mentioned by copying a small subset at a time to at "work" folder and see how things turn out.

Thanks!

---

### Post by Yellow Pasque on 2014-02-13
When it comes to tagging, an ounce of prevention is worth a pound of cure. A good CD ripper program should look up the info in cddb/freedb (CD databases) and fill in the tags/metadata automatically.

Clementine has a feature to automatically complete tags (it's a bit hit or miss though). If you have your music well-organized with a consistent filename scheme, you may be able to find some scripts to automate the process (and IIRC, easytag supports creating tags from filenames). If you have a jumbled music collection, then you're in for a lot a tedious work.

Note: I guess something could be wrong with XBMC reading tags, but I don't use it, so can't comment there.

---

