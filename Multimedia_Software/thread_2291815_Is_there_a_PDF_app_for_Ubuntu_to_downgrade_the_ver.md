---
title: "Is there a PDF app for Ubuntu to downgrade the version?"
date: 2015-08-23
forum: Multimedia Software
---

### Post by Old_Printer on 2015-08-23
I have an AccuSet 800 Plus imagesetter from 1997. I need to input PDFs at the 1.2 version. LO outputs 1.4. I tried a test. It won't make it through the RIP. In Windows I print to a virtual Abobe PDF printer, version 1.2 preset that I've established in Acrobat 7.

I'm thinking I could try to load Acrobat 7 in Wine, but I thought I would ask to see if anyone knows of a PDF virtual printer that I could download from the Software Center that would offer the older versions as an option.

I use Corel 9 & X4 for all typesetting. It looks as though I could depend on LO, at least I certainly want to give it a try.

Thanks in advance,

Old_Printer

---

### Post by coldraven on 2015-08-23
In this thread they use Ghostscript to reduce the file size but I see in the second parameter "-dCompatibilityLevel=1.4".
[http://ubuntuforums.org/showthread.php?t=1133357](http://ubuntuforums.org/showthread.php?t=1133357)

Also here:
[http://superuser.com/questions/25598/linux-pdf-version-converter](http://superuser.com/questions/25598/linux-pdf-version-converter)

I'm no expert in this but maybe it will also do version 1.2, it's worth a try.

Edit: After a quick search I found this:
> The pdfwrite device outputs PDF.  Please refer to [Ps2pdf.htm]("http://ghostscript.com/doc/current/Ps2pdf.htm") for the extensive pdfwrite device options.

Which takes you here where it states that version 1.2 is an option. So it looks like you're in luck :)
[http://ghostscript.com/doc/current/Ps2pdf.htm](http://ghostscript.com/doc/current/Ps2pdf.htm)

---

### Post by Old_Printer on 2015-08-23
Thanks for the reply, coldraven. I really appreciate it. This is going to be some good reading for me.

I'll post back when I get something working.

Thanks again,

Old_Priner

---

### Post by coldraven on 2015-08-23
I forgot to mention that Ghostscript is most likely already installed on your system. It definitely is on Ubuntu 14.04. 
Typing ```
gs --version
``` gives me version 9.10

---

