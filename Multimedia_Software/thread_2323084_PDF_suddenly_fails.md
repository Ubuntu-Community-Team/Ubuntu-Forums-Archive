---
title: "PDF suddenly fails"
date: 2016-05-02
forum: Multimedia Software
---

### Post by lile001 on 2016-05-02
Well all of a sudden I cannot open a valid PDF file.  

I am trying to read a PDf that was published in 2013.  It is a 680 page copyrighted book, which I cannot post here because it is copyrighted ( and too big).  I have been using this file (it is a reference book) successfully since 2013 on multiple computers and operating systems.   

Evince (aka Document Viewer) says "File type unknown (application/octet-stream) is not supported ".  I tried xpdf, which doesn't open the file but doesn't report anything either.    Okular simply says "could not open" the file.   [Qoppa PDF Studio 9]("https://www.qoppa.com/pdfstudio/") also reports that it cannot open the file, although it opens other pdf files.  


The same file appears on my Windows machine (it is in dropbox so it really is the identical file) and opens fine in Adobe reader.  As mentioned this is a reference book I use in my work almost daily, have opened it under Linux thousands of times before.  Dropbox reports this file is unchanged since 2013 and is the original version.  The file can't be the problem - it is a valid PDF that opens in valid Adobe Reader and has been opened thousands of times over many years and has not changed.  


I have checked to see if Evince and Okular are latest version, sudo apt-get install xxxx reports that they should be.  

This should be a very standard pdf, with bookmarks for chapters but no forms or advanced features.  I note that most other pdfs open fine with Evince and Okular, however I find one other fairly large PDF that won't open, giving the same error message and having been published by the same author organization.  This is a pdf  book that probably has a circulation of at least 1 million, standard reference for my field.  

I am on Ubuntu 14.04LTS,   Okular V. 0.19.3,   Evince v. 3.10.3.    

Has there been some update to Ubuntu that would cause this?  Or have three different Ubuntu PDf readers all developed the same bug?  None of those theories sound plausible.


/EDIT   here is another bit of info. I made a copy "test.pdf"  

$pdfinfo test.pdf
Syntax Warning: May not be a PDF file (continuing anyway)
Syntax Error (16): Illegal character '>'
Syntax Error: Couldn't find trailer dictionary
Syntax Error: Couldn't read xref table

I don't really know what this means, but saw it on another thread. If these issues are real, then why does it load OK in adobe reader?

---

### Post by vasa1 on 2016-05-02
It's going to be difficult to help if you can't share, for "copyright reasons", the link to the pdf file in Dropbox (which I understand is possible).

Since it works with Adobe, just use that.

---

### Post by lile001 on 2016-05-02
> **vasa1 said:**
> It's going to be difficult to help if you can't share, for "copyright reasons", the link to the pdf file in Dropbox (which I understand is possible).

Since it works with Adobe, just use that.

Adobe isn't available anymore in Linux, if I am not mistaken.   Is this yet another Linux limitation driving me back to Windows?

---

### Post by vasa1 on 2016-05-02
> **lile001 said:**
> Adobe isn't available anymore in Linux, if I am not mistaken.   Is this yet another Linux limitation driving me back to Windows?
You mentioned it works with Adobe Reader on Windows. So use that. Whether this is *yet another Linux limitation* driving you back to Windows is something only you can determine. We can't even access the pdf file.

---

### Post by lile001 on 2016-05-03
Well, thanks, that's certainly a workaround.  What I'm really looking for is a way to fix the problem, or at least report a bug.  Not sure where to go since it seems to affect several packages.  Also looking to see if this is a problem others have encountered.

---

### Post by steeldriver on 2016-05-03
It might be a bug in the poppler library (or cairo backend?) - but without a minimal working (i.e. crashing) example it's going to be hard to diagnose further

---

### Post by vasa1 on 2016-05-03
> **lile001 said:**
> Well, thanks, that's certainly a workaround.  What I'm really looking for is a way to fix the problem, or at least report a bug.  **Not sure where to go since it seems to affect several packages.**  Also looking to see if this is a problem others have encountered.

Where did that (part in bold) come from? How did you reach that conclusion? Even if you want to file a bug, you will have to provide a sample pdf.

---

### Post by lile001 on 2016-05-03
I will keep looking for more examples that I can legally post.

---

### Post by lile001 on 2016-05-03
> **vasa1 said:**
> Where did that (part in bold) come from? How did you reach that conclusion? Even if you want to file a bug, you will have to provide a sample pdf.

How did I reach that conclusion?

1.  The problem appears in three different PDF reader programs that run under Linux.

2. The problem appears in two different PDFs, which are widely distributed published works and are presumably trustworthy. 

3. The problem does not appear in the two pdf files when opened under Adobe Reader in Windows. This seems to indicate that the PDFs are not corrupt. 

4. All of the affected Linux programs could previously open this file, as of a month or two ago, and the file has not changed.  

This leads me to an hypothesis that there is a problem, under Linux, that has recently emerged, and that affects multiple packages/programs which read PDFs.  Proof of said hypothesis will require an example in the wild which I am looking for.   I would like to either find out that other people have a similar problem, or find enough evidence to file a bug report, if either is possible with more investigation.  Right now I will continue to look for such evidence.  

That about sum it up?

---

### Post by spjackson on 2016-05-03
> **lile001 said:**
> 
The same file appears on my Windows machine (it is in dropbox so it really is the identical file) and opens fine in Adobe reader.

Are you sure the files are identical? Do you get identical results for sha1sum or md5sum on both platforms?

I see that pdfinfo fails. Can you post the equivalent information (especially PDF version) from Acrobat Reader (file properties, possibly).
> 
I am on Ubuntu 14.04LTS,   Okular V. 0.19.3,   Evince v. 3.10.3.

And in what Linux configuration were you able to read the file until recently?

---

### Post by vasa1 on 2016-05-03
> **lile001 said:**
> ...
Evince (aka Document Viewer) says "File type unknown (application/octet-stream) is not supported ".  I tried xpdf, which doesn't open the file but doesn't report anything either.    Okular simply says "could not open" the file.   [Qoppa PDF Studio 9]("https://www.qoppa.com/pdfstudio/") also reports that it cannot open the file, although it opens other pdf files.  
...
Did you try the built-in pdf reader built into Google Chrome (for Linux)? I think it was or is based on Foxit, a rather competent pdf reader for Windows.

---

### Post by gordintoronto on 2016-05-04
When something used to work, and suddenly does not, there is often the possibility that there's a hardware problem. In this case, it could be memory or hard drive. Does top report the amount of memory that you think the computer has?

---

### Post by vasa1 on 2016-05-04
What is a clear blocker is the non-availability of the pdf file for others to check. Even worse is the non-availability of links even though 
> . It is a 680 page copyrighted book, which I cannot post here because it is copyrighted ( and too big). I have been using this file (it is a reference book) successfully since 2013 on multiple computers and operating systems.

so several copies have been made unless several copies were purchased? 

> The problem appears in two different PDFs, which are widely distributed published works and are presumably trustworthy. and >  This is a pdf book that probably has a circulation of at least 1 million, standard reference for my field. 

I think OP could provide more information.

---

