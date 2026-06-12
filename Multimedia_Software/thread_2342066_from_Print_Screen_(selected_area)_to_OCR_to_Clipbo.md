---
title: "from Print Screen (selected area) to OCR to Clipboard"
date: 2016-11-03
forum: Multimedia Software
---

### Post by lorenzo-n on 2016-11-03
Hi,

I'm looking for a simple OCR software which provides a recognition starting from a screenshot captured and stored in the Ubuntu Clipboard.

steps:
1- CTRL+SHIFT+PrintScreen let me select an area: I select an area and I know the resulting image is temporary stored in the clipboard, ready to be pasted.
2- a simple GUI OCR software that let me "paste" the image captured (or, ideally, poll the Ubuntu Clipboard for new captured images) and scan it (eventually saving the text in the Ubuntu Clipboard again, ovewriting the grabbed image).

i do not would have this intermediate step:
- "save the captured area as image-file and load this file to an OCR software"
because I have a lot of grabbing/OCRing/text-pasting items to do.

Any idea?

Thank you,
Lorenzo

---

### Post by ajgreeny on 2016-11-03
I think you are going to be disappointed in your quest.

I have looked for a decent OCR package in Linux for some time and the best I have found so far has been tesseract, however, that requires that you save the image, which you do not wish to do.

There are a few online OCR sites but all of those that I have seen also need an image file to upload, so again will not do what you want.

Can that be done on other platforms such as Windows and Mac?  The OCR software I used in Windows over 10 years ago could not, as far as I remember, though I admit I used it very little in those days.

There is a fairly good discussion of the subject at [http://askubuntu.com/questions/16268/whats-the-best-simplest-ocr-solution](http://askubuntu.com/questions/16268/whats-the-best-simplest-ocr-solution) but most of the solutions mentioned there I have not tried.

---

### Post by QIII on 2016-11-03
OCR is great for capturing from paper. 

Have you considered just parsing the html?  Capturing an image (and disposing of it) and using OCR on it seems like a lot of extra complexity.  Is there some reason you need to do it this way?

---

### Post by lorenzo-n on 2016-11-04
thank you ajgreeny, I'll take a look todiscussion you linked.

I know my wish could be satisfacted by a bash script that polls the clipboard, automatically save images and launches a command line ocr software. maybe I'll try.

bye,
Lorenzo

---

### Post by lorenzo-n on 2016-11-04
QIII, I'm able to copy&paste from a browser, anyway thank you for your suggestion :-D

There are some cases where your source is an image, not already saved (or even not easely accessed as image file).
My request, for example, is grabbing and OCRing portion of pictures when I'm managing my photo galleries. a lot of text I would grab just selecting, such as art pieces labels (author, title...)

Have a good day,
Lorenzo

---

### Post by ajgreeny on 2016-11-04
The likelyhood is that any image you get as a screenshot and try to use OCR on is probably going to be very poor as well.

The screenshot will probably be at too low a resolution at standard display settings, which may be far to low for decent OCR use.

---

### Post by lorenzo-n on 2016-11-04
I do not think so.
If I take a screenshot of a portion of my screen, save it on an image and than open that image, and scan with the google translator app installed on my smartphone (using my smartphone poor camera), google translator is fully able to "OCRing" it, because it offers me a right translation in different language. 

I think it would be not a quality matter. OCRs of printed text (from a picture) works well. 
It just no one'd created the app I would like to use.

---

