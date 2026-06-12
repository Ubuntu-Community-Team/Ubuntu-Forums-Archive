---
title: "Windows WMW files to mp3"
date: 2008-12-02
forum: Multimedia Software
---

### Post by bob brazie on 2008-12-02
Is there any recommendations on a program to change windows media music files to the mp3 format?

Thanks in advance. Bob.

---

### Post by balticman on 2008-12-04
Do you mean WMV files? If so FFMPEG is your friend. It should have no problem convrting to MP3.

---

### Post by bob brazie on 2008-12-04
The extension is .WMA and it is a collection of song's I have.

I just purchased a GPS which also has the option to run a patch cord from it to the line in on my CD player in my truck. However the GPS will only play mp3 files.

Where might I find this FFMMPEG?

---

### Post by balticman on 2008-12-05
Its either included by default or available through synaptic.

Its a command line utility,incredibly powerfull and useful. For your purpose you need to navigate to the directory where the wma files are and then input

ffmpeg -i yoursong.wma yoursong.mp3

That should be it.

For an introduction and some useful shortcuts try 

[http://www.catswhocode.com/blog/os/19-ffmpeg-commands-for-all-needs-824](http://www.catswhocode.com/blog/os/19-ffmpeg-commands-for-all-needs-824)

---

### Post by bob brazie on 2008-12-05
I'll give it a try. Can it do more thatn one song at a time? Say a folder that has all of one albums songs in it?

---

### Post by balticman on 2008-12-05
As its command line I am sure you can process more than one file at a time. Not sure what the command would be though. For 1 album you might be just as quick repeating the command for each conversion.

---

### Post by FakeOutdoorsman on 2008-12-05
I the stock version of ffmpeg from the Intrepid repository will not properly encode to mp3.  This is a restricted format, but you can get it to work by using the ["unstripped" ffmpeg libraries]("http://ubuntuforums.org/showpost.php?p=6207546&postcount=3") [link to forum post].  These will provide encoding support for restricted formats.

ffmpeg by default will encode to 64 kb/s.  You can change the bitrate with "-ab":
```
ffmpeg -i yoursong.wma -ab 128k yoursong.mp3
```

---

