---
title: "MP3/AAC Importing to Rhythmbox"
date: 2009-05-02
forum: Multimedia Software
---

### Post by Crackity Jones on 2009-05-02
Hey there.
I been put-off importing my music collection into my linux machine for a while because of the slow speed of importing from a CD and the formats that my iPod won't recognise, plus the open formats make huge music files.

Could anyone help me import CDs quickly into Rhythmbox in the MP3/AAC format please? Any help would be greatly appreciated as I love my music.

---

### Post by hansdown on 2009-05-02
Hi Crackity Jones.

Open rythmbox, click edit> preferences> music.

On preferred format, you can choose mp3, aac, etc.

If you have the proper codecs installed.

---

### Post by Crackity Jones on 2009-05-02
I don't think I do as I can not choose the preferred formats. Where can I get the codecs from?

---

### Post by hansdown on 2009-05-02
Go to stchman.com

[http://www.stchman.com/](http://www.stchman.com/)

If you are comfortable with copying and pasting, it will be fastest.

Copy and paste these into a terminal.

Click applications> accessories> terminal.

Use only the 32 bit or 64 bit line, whichever you are running.

---

### Post by Crackity Jones on 2009-05-02
Thank you so much, everything is sorted for me. :P

---

### Post by logos34 on 2009-05-02
Thought you might want to be aware of this official ubuntu advisory on Sound-Juicer (gstreamer):

> 
MP3 Encoding

WARNING: the gstreamer LAME plugin, used in the instructions below, is broken and will produce substandard quality MP3s. You can track the bug [here]("https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483"). If you want to create MP3s, it is recommended not to use Sound Juicer; use a program that doesn't interface with LAME through gstreamer instead. Good examples are [RubyRipper]("https://help.ubuntu.com/community/CDRipping#RubyRipper") and [ABCDE]("https://help.ubuntu.com/community/CDRipping#ABCDE"). 

[https://help.ubuntu.com/community/CDRipping#MP3%20Encoding](https://help.ubuntu.com/community/CDRipping#MP3%20Encoding)


I've noticed this personally.  Seems the VBR pipeline options (including 'preset=') don't seem to work right at certain settings...lame -V 2 (i.e. '--vbr-quality=2') is outputting instead at ~160kbps, and/or the id3 tags are wrong...etc

So if possible use AAC/m4a format instead.

[https://help.ubuntu.com/community/CDRipping#AAC%20Encoding](https://help.ubuntu.com/community/CDRipping#AAC%20Encoding)
(ignore the part about gstreamer0.8-faac)

Unless you have the newest generation of Ipods, you might consider installing RockBox firmware, which will give you ogg vorbis and flac support.  Vorbis lossy is superior to mp3 and at least as good as aac

enjoy ubuntu

---

### Post by hansdown on 2009-05-02
Glad you fixed it.Enjoy!

logos34, thankyou for posting that.

---

