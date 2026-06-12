---
title: "No sound for videos with usb sound box"
date: 2009-01-05
forum: Mythbuntu
---

### Post by rastoboy on 2009-01-05
Hello,

I'm *almost* in mythTV heaven at this point, except for this one nagging problem--no audio in most movies.  I have a usb sound box that works great with regular Ubuntu (sorry it's a nondescript Taiwanese grey oval box I got several years ago--I don't have the model info handy).  

It's a bit weird in Mythbuntu, though.  I can get it to work via Gnome desktop by going into Mplayer, choosing OSS driver, and choosing /dev/dsp1.  I had to set MythTV Music to use /dev/dsp1, and music plays fine now.  The Internal movie player also finds it fine, without my having done any configuration of it (unless it  uses the Music settings).  But I don't see an audio setting under the Video settings--am I missing it?

How can I convince Mplayer to use the OSS driver/device setting I found when launched from MythTV?  I've been researching the commandline switches for Mplayer, but for the life of me I can see a relevant one--surely I'm missing something?

Any input would be greatly appreciated!

---

### Post by rastoboy on 2009-01-06
Found a partial fix.  I told it to ignore the default player for avi's, so it's using the internal player, and I have sound for those.  I do believe it's possible to add the commandline switches for mplayer as well, if I can figure out the syntax.  I know it's -ao, and I need to tell it "oss" and "/dev/dsp1", and once I've figured out the syntax I'll post it here.

The man page for mplayer is a little vague on this.

---

### Post by rastoboy on 2009-01-07
it was:

-ao oss:/dev/dsp1

---

