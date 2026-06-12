---
title: "MP3 tag editor/rename recommendations?"
date: 2014-05-15
forum: Multimedia Software
---

### Post by spockswhitepants on 2014-05-15
Lots of great native apps on Linux but of all things I'm struggling to find a tag editor that will really work on Linux... I would hate to have to do something this simple inside a Win 8.1 VM.

So far I have tried:

**puddletag** - I can't figure out what it is doing with the rename directories functionality... nothing good is all I can tell. It always moves them back several levels... leaving me to create a bunch of temporary directories for files I am bringing in just so it ends up in the right place... often it will try to build paths below the root where it just generates a bunch of errors in the background and does nothing. The directory functionality doesn't seem to be very usable. 

**easytag** - I can't get the genre tag editing to work with custom values. I have it set to "text only" in the options. Yet no matter what I enter it will change it to "Blues". Always. Because it is the first in their list of hardcoded genres I guess? There should be a way around this but I haven't been able to find anything that works yet. If anyone can point out the error of my ways this might work for me. Despite the fact that I also get seg faults when using the rename directory functionality... though maybe those are fixed in the latest version. But I haven't been able to build the latest version so I am stuck with the repository version.

Is there a good solution I am missing out on? I just used Foobar2000 for this under Windows (and many other programs before that) and they were all perfectly servicable. Seems like this should be a pretty simple task where there should be some good native apps out there capable of doing it.

---

### Post by deadflowr on 2014-05-15
Cowbell?
it's in the software center.

---

### Post by ron998 on 2014-05-15
> **spockswhitepants said:**
> ... But I haven't been able to build the latest version so I am stuck with the repository version.
Hi
If you do feel inclined to build the latest version of **EasyTAG**, I posted some information here ---> [http://ubuntuforums.org/showthread.php?t=2216435&p=12984884#post12984884](http://ubuntuforums.org/showthread.php?t=2216435&p=12984884#post12984884)

---

### Post by tgalati4 on 2014-05-15
There are a few different versions of ID3 tag and one of those differences is how Genre's are handled.  So you can try building the latest version of *easytag* to see if Genre's work the way you expect.  I'm sure custom Genre's are stored as an XML file somewhere, but you will have to search for it.

---

### Post by HiImTye on 2014-05-16
if you want to use a graphical program, Ex Falso is pretty good. if you're comfortable with the command line, eyeD3 is great. it's what I use.

---

