---
title: "Can you place a .txt file onto a pdf from the command line?"
date: 2021-09-27
forum: Multimedia Software
---

### Post by 74bravo on 2021-09-27
Hi there, using Ubuntu 18.04.

I have a .txt file with about 85 words on it that I would like to overlay on to a pdf.  The pdf has boxes and borders and lines, and I am looking for a way to place the contents of the .txt file onto the pdf, resulting in a new pdf. 

Can something like that be done from the command line?

Thanks~

---

### Post by TheFu on 2021-09-27
Perhaps **pdfattach** will work?  It is part of the poppler-utils package.
 
OR use pandoc to make PDF from many other formats. 
```
$ pandoc test.txt -o test.pdf
```

And use **pdfunite** to place the new PDF into the old one, creating a new PDF as the result.
```
$ pdfunite sample1.pdf sample2.pdf sample.pdf
```

I don't know how to batch place an annotation onto a specific page, into a specific location. Well, not without custom programming. 
You might have a completely different purpose.

---

### Post by vanadium on 2021-09-28
pdfunite will append files in one PDF, but not superimpose one page on another. qpdf has an --overlay option, whereas pdftk has the "stamp" or "multistamp" options to overlay.

---

### Post by 74bravo on 2021-09-28
Thanks for the suggestions!  Will give them a try.

---

