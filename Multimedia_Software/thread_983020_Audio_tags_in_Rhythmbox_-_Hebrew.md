---
title: "Audio tags in Rhythmbox - Hebrew"
date: 2008-11-15
forum: Multimedia Software
---

### Post by VitaminCPP on 2008-11-15
I have some mp3 files with tag information (title, group, year, album, etc) in Hebrew. I don't know what encoding is it, but definitely not UTF-8, because Rhythmbox shows gibberish istead of the information. I want to change the encoding to UTF-8. I tried EasyTag, but it seems to not do what I want.
By the way, Nautilus recognize file names properly.

How do I accomplish encoding change?

---

### Post by Euphorion on 2008-11-15
Your Problem will probably become one of trial and error centred around the following:

The ID3 Tags contained in your MP3 files can be one of the following:
ID3v1, ID3v2.3 or ID3v2.4 which use different character set encoding.

ID3v1 specifies no specific character coding and has a limited number of fields with very limited sizes, and is seldom used these days.

IDv2.3 is the most common standard in use and uses ISO 8859 1 or UTF-16 character set encoding, here UTF-16 is very common.

IDv2.4 is the latest standard and uses UTF-8 character encoding.

For further details and interesting reading see [http://en.wikipedia.org/wiki/ID3](http://en.wikipedia.org/wiki/ID3)

In Ubuntu I use EasyTag and Grip, especially in Grip you can set the encoding easily and it is well described in the Help Section Configuring Grip. Grip is a rip and encoding programme but could be of help in finding out how your tags are encoded.

Despite being an absolute Ubuntu fan, when playing about with MP3 Tags you cannot beat MP3Tag which is only available as a Windows Programme from [http://www.mp3tag.de/](http://www.mp3tag.de/) (available in many languages), you could of course run it in Wine under Ubuntu.

Hope this helps somewhat.

---

### Post by ebash on 2008-11-16
Rhythmbox is using gstreamer for handling all media files. Currently gstreamer can read ID3v1, ID3v2.3 and ID3v2.4 but can only write ID3v1 and ID3v2.4. As it was described in the previous post ID3v1 is no good for other characters than English on the other hand ID3v2.4 is not supported by all hardware players (mine doesn't). The most portable solution is to use ID3v2.3 which doesn't have write support out of the box in gstreamer.

If you still have your original content you can try to re-encode them with sound-juicer. It's also possible to re-encode the files with a shell script, try to see if the following command will add proper ID3v2.4 tags:

```
gst-launch filesrc location=original.mp3 ! id3demux ! id3v2mux ! filesink location=copy.mp3

```

Replace *original.mp3* with one of your MP3s and *copy.mp3* with the new file name. **WARNING**: DO NOT use the same file name for the original and the copy otherwise you will lose your MP3.

For better portability with hardware players, there's a plugin in gstreamer's bugzilla that adds support for writing ID3v2.3 tags. The source code of the plugin, the build instructions and the user manual are in this bug:

[http://bugzilla.gnome.org/show_bug.cgi?id=459226]("http://bugzilla.gnome.org/show_bug.cgi?id=459226")

Download the .tar.gz file and follow the instructions in the file README.txt.

---

### Post by VitaminCPP on 2008-11-16
I don't know how to change multiple tags encoding neither in EasyTag nor in Grip. Have searched around without success. Can anyone bring me simple step-by-step instructions, please? 

I tried Audio Tag Tool also... I think that the problem is that EasyTag and such tools don't recognize tags in my encoding, too. They show gibberish in tag information, like Rhythmbox.

---

