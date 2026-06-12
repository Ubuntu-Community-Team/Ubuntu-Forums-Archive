---
title: "Easy OCR software for thousands of pages text extraction?"
date: 2017-05-31
forum: Multimedia Software
---

### Post by marseille2 on 2017-05-31
Hi, I'm trying to help out a non-profit convert old documentation to digital format (probably PDF). Since the paperwork dates back almost 40 years, I'm thinking almost 6000 pages of text (as well as images) would need extraction. Is this possible to complete in an easy, efficient and reliable fashion? I saw the [OCR community page]("https://help.ubuntu.com/community/OCR") but don't know if I can trust it or if the solutions will be too difficult or over-the-top (there might be more than 1 person working on this task and usability should be simple). Suggestions welcome (software with a GUI is good too for multiple-user simplicity).

---

### Post by QIII on 2017-05-31
Well, other than the fact that it was last updated in 2015, the information should be as trustworthy and safe as any you might receive here -- given that those who maintain the community wikis are the same folks that hang out here.  :)

I can't vouch for any specific software package (they may not all still be maintained) and I don't know what "simple usability" might look like to you.  You could always look at several of them, test them out, and see what you find to be the most suitable for your purposes.

---

### Post by marseille2 on 2017-06-01
Ok I've tested 2 so far... gimageReader and yagf. Both have crashed on me but I'm not sure why. The latter gave me a seg default after one run (it did scan). The scan itself almost went well but it didn't pull in any text that made sense. gimageReader actually did pull some nice OCR, and it does scan available images (without scanning). It's just slow and I can't get it to start again with the scanner (printer). I guess they both use tesseract or something... Could it be my printer that's causing me issues?

---

### Post by SeijiSensei on 2017-06-01
I've never had much success with open-source OCR software myself.

---

### Post by Keith_Helms on 2017-06-01
I tried out the Linux OCR offerings and none worked all that well.  I ended up using Abbyy Finereader in a Windows VM.  It cost me a little over $100, but it worked much better and was worth it to avoid endless corrections to text.

---

### Post by QIII on 2017-06-01
Well, if it works that's the main thing!  Use what works!

Let the FLOSS purists do thrir thing.  You do yours.

---

### Post by Autodave on 2017-06-03
If you are  saving them as PDFs, then why not just scan and save as PDF? Obviously, if it is stored in digital format, it should be readily available to view and print from where ever it is stored. Or JPG format.

---

### Post by marseille2 on 2017-06-03
Well the goal is to figure out how to replace (paid) print publications. The average book is about 150 pages long but it's a small book. Some of the publications are really really old (font is the old typewriter thing), and it might be that retooling the content is needed to repackage. So extraction was a big thing on my mind as a solution.

---

### Post by gordintoronto on 2017-06-04
> **Autodave said:**
> If you are  saving them as PDFs, then why not just scan and save as PDF? Obviously, if it is stored in digital format, it should be readily available to view and print from where ever it is stored. Or JPG format.

But it's not searchable, and that's one of the big benefits of digital format.

---

### Post by gordintoronto on 2017-06-04
> **marseille2 said:**
> Well the goal is to figure out how to replace (paid) print publications. The average book is about 150 pages long but it's a small book. Some of the publications are really really old (font is the old typewriter thing), and it might be that retooling the content is needed to repackage. So extraction was a big thing on my mind as a solution.

You might find a service bureau such as a Fedex store which can do the job. Using a sheet-fed scanner is about 40 times as fast as placing each page on the scanning bed. At my office we have a high-end Xerox printer/scanner which produces searchable PDFs, but the monthly rental is outrageous.

Several years ago I bought a very cheap Lexmark multi-function printer which came with OCR software for Windows, and the OCR is remarkably good. When the ink cartridges ran out, the device became a full time scanner, and it scans just fine in Linux.

---

