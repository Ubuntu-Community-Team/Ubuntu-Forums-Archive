---
title: "Subtitles as srt from sub/idx"
date: 2019-09-27
forum: Multimedia Software
---

### Post by John Jason Jordan on 2019-09-27
Xubuntu 16.04, up to date.

I have a collection of DVDs from other countries that I need to rip and encode to .mkv files. Most have subtitles, and they are almost always fuzzy vobsubs on the DVD. I use MakeMKV to rip and encode them and then use MKVToolNix-GUI to extract the vobsubs as mks files. And then I use mkvextract to get sub/idx files out of the mks files. 

So far, so good. But I'm stuck on converting the sub/idx files to srt files. I know this requires OCR work, and the results will need some cleanup, but I don't have any tools to do the OCR. I did find an online converter here: [URL="https://subconverter.com/convert-sub-idx-to-srt-online"] , but it doesn't always do a very good job, plus I'd rather have control of the process myself. I do have Tesseract installed, but I can't figure out how to get it to OCR the text in the .sub file while maintaining the timecodes in the .idx file.

Researching here I find people have recommended all kinds of subtitle editors, but I have used all of them over the years and none can import a sub/idx file, or if they can, all they can do with it is export as another sub/idx file, i.e., they have no OCR capability. 

Any suggestions welcome!

---

### Post by TheFu on 2019-09-28
**avidemux** can convert the glyphs into text.  It will ask for training/confirmation and store the glyph-to-character mapping in a file which gets reused for the same disc, but can be helpful for discs produced by the same vendor.  It has been a few years since I converted my DVD collection, so I don't remember exact details about the process, just that wasn't intuitive the first time.  There were 3 steps without a wizard in avidemux to create the srt file.  A web search should be able to find a guide.  [http://write.flossmanuals.net/avidemux/extract-dvd-subtitles/](http://write.flossmanuals.net/avidemux/extract-dvd-subtitles/)  found it.

Not too hard, just tedious, but every file using the same fonts is easier and easier with fewer and fewer confirmations needed.

For lurkers:
subs are little pictures. They need OCR to figure out which character the little picture should be as text/ASCII. 
srts are text/captions.

Broadcast TV sends out Captions, which are text. UTF-8/16/32 wasn't popular when the standard for  DVDs was decided. DVDs use subtitles (little images), because they wanted to support any language and some other symbols, the little images were decided best.

---

### Post by shag00 on 2019-09-29
I am in a similar situation of needing to translate picture file subtitles to text ones. I am also trying to migrate from Windows to Linux and have recently spent a lot of time chasing down this issue and have discovered that there are no OCR capable subtitle editors available for linux as native linux programs. In total there are less than a dozen linux subtitle editors, including non OCR capable, on offer and most have not been updated for many years. There is one which may work which is called Subtitle Edit but I cannot get it to work. It supposedly runs under Mono but not for me so I opened a GIT ticket and the program author has responded to me and has sent me a couple of beta offerings to test but no luck yet. I have used this program for years under Windows and it really is very good and well maintained.

What would be good and really helpful would be if you could try it out and when(if) you have a problem open a GIT ticket [https://github.com/SubtitleEdit/subtitleedit/issues](https://github.com/SubtitleEdit/subtitleedit/issues)  to let the author know there are linux users who want to use his excellent program. Please don't confuse this program with a similarly named one, Subtitle Editor.

To use this program you need to install at least:
mono-complete
tesseract-ocr
vlc
libvlc-dev
libmpv-dev
libhunspell-dev

Download the portable version of the program and unzip it. Using the CLI, navigate to the directory you just unzipped and enter: 
```
mono SubtitleEdit.exe
```

---

### Post by Holger_Gehrke on 2019-09-30
Another option for use on the command line is the package 'subtitleripper' from the repositories. It contains - among other things - the program vobsub2pgm which will split sub/idx into lots of pgm or ppm image files which you can then feed to the OCR of our choice. It also creates a template for an srt file with timing information and placeholders for the text(s) generated from the images.

Holger

---

