---
title: "OCR Application for 14.04 LTS?"
date: 2015-02-03
forum: Multimedia Software
---

### Post by Tibetan Wolf on 2015-02-03
Hello, I'm looking for a working & tested free OCR application for Ubuntu 14.04 LTS.

I've already tried installing both YAGF and OCRFeeder and none of them really work for me (and lately OCRFeeder keep on crashing...).
The main target language is Italian, by the way. Both applications were also tested along with both Cuneiform and Tesseract-ocr (as OCR engines).

I'm quite new to Linux & Ubuntu Linux. Does anyone know any working OCR software to suggest? 

Thanks,
Nick

---

### Post by ajgreeny on 2015-02-03
I gave up looking for a program for OCR with any sort of GUI and decided to go with tesseract 3.13.12-2 from the repos.  It seems to be very accurate if you have a good high resolution image, and that image no longer has to be in the form of **file.tif** as it used to be with version 2; now most image formats are readable, certainly jpg, png and tif or tiff are all acceptable, which is a great deal better than having to convert any other image format to .tif.

The big thing that we need to help with using OCR is both a way of feeding pages from, for example, a book or similar where there may be several pages to scan and OCR, and if possible some GUI for those who fear the terminal.

I suggest you scan at a resolution of 600dpi for best accuracy, and preferably in lineart or greyscale, then use this very simple command ```
tesseract infile.png outfile
```from the folder where the image is sited.  Do not put a .txt suffix on the outfile name; that will be done by the application itself.

---

### Post by Tibetan Wolf on 2015-02-04
Thanks, ajgreeny. Probably my system will freeze processing a 600dpi image through tesseract (it happened with the GUI programs), but that command is very useful.

Honestly, I'm looking for a program with a GUI, but it seems like an impossible mission now... I cannot find anything else in the repository (any ppa? no idea).
 Perhaps people don't need OCR any more? well, at least *nix people...

---

### Post by SeijiSensei on 2015-02-04
I suspect that OCR is a pretty difficult task, and there aren't that many developers interested in the problem to fashion good open-source solutions. You're probably right that it isn't as big an issue for people in *nix environments where paper documents have never been all that common.  The only people I know who still seem wedded to paper are my attorney friends, and they're all using Windows.

---

### Post by ajgreeny on 2015-02-04
Just try tesseract using the command I gave you for your own files; it may just take a long time to recognize the text in the image, but I don't recall it being extremely resource hungry even when I was using a single core Sempron 2400+ a couple of years ago.

I am sure it must also be possible to write a simple script to automate the activities of scan, save image, OCR, and lastly open the .txt file in a gui application; I just can't be bothered as I so seldom need to OCR anything these days.

---

### Post by Tibetan Wolf on 2015-02-05
SeijiSensei & ajgreeny, thanks so much for your replies.

@ajgreeny, at this point I will just try tesseract-ocr with the command line (according to the installation instructions on project website, I should install the language training data package too...).

Still looking for a working graphical interface though (maybe someday...)

---

### Post by ajgreeny on 2015-02-07
Not sure about the language training data package, for English  all I needed was the English language tesseract package in the repos, so I think you will need the Italian version instead, ie **tesseract-ocr-ita**

---

### Post by josh109 on 2015-02-08
I'm not sure if this will be usefull, but here we go.


If you *absolutely *have to have one, you can find a good Windows one and try to run it with [wine.]("http://winehq.org")

---

### Post by Tibetan Wolf on 2015-02-08
@ajgreeny, yes, for each language you should also  install the proper language training data package (e.g. tesseract-ocr-ita). 
Both YAGF and OCRFeeder don't install any additional training data packages as far as I know, and probably this is one of the reasons why they works pretty bad in my language... (without mentioning the overall and unrelated GUI issues/missing features...).
As for English, apparently there's also a language training data package available: [https://code.google.com/p/tesseract-ocr/downloads/list](https://code.google.com/p/tesseract-ocr/downloads/list)
(info here: [https://code.google.com/p/tesseract-ocr/wiki/ReadMe](https://code.google.com/p/tesseract-ocr/wiki/ReadMe))

@josh109, thanks for your reply, but I was  looking for some front-end for Ubuntu 14.04 or something with a fully working GUI...

---

### Post by ajgreeny on 2015-02-08
I installed it from the repos and doing so that way, the language package tesseract-ocr-eng is a dependency; other languages can also be added but the English version can not be removed.

---

### Post by Tibetan Wolf on 2015-02-09
So that's the reason why also those two GUI programs work way better in English... In my opinion they should at least notify the users who choose any different language about the optional training data packages...

---

