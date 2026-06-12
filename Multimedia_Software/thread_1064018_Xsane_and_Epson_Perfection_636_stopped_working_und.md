---
title: "Xsane and Epson Perfection 636 stopped working under HArdy"
date: 2009-02-08
forum: Multimedia Software
---

### Post by bdalzell on 2009-02-08
Today when I tried to scan a document I had a failure of Xsane. previously it has worked on my system with my Epson scsi scanner, a Perfection 636.
I have Hardy installed.

When I click get preview the scanner scans and all of the full sized letter sized document show briefly in the XSane Preview window in a sort of ghosted
mode and then when the ghost mode turns off only the top 6 centimenters of 
the document show. 

If I go ahead and click the scan button I get the following error:
Error during CMS conversion. Could not open scanner ICM profile.

Xsane does recognize that the scanner is an Epson Perfection 636 according to the Options and Advanced Options window.

---

### Post by xc3RnbFO8P on 2009-02-08
Try to uncheck "Preferences / Enable Color Management.

---

### Post by bdalzell on 2009-02-09
Thanks for the reply.

It was unchecked. So I checked it and immediately got got an error:
Error during CMS conversion. Could not open scanner ICM profile.
Then I unchecked it and Xsane worked.

Of course the computer had been turned off overnight.

Attach twilight zone musical theme here.

---

### Post by xc3RnbFO8P on 2009-02-09
> Attach twilight zone musical theme here.
:)

---

### Post by bdalzell on 2009-12-03
Since I asked the question twice I have posted the solution that worked under the other instance of the quuestion here:


[http://ubuntuforums.org/showthread.php?p=8434207#post8434207](http://ubuntuforums.org/showthread.php?p=8434207#post8434207)

---

### Post by bdalzell on 2009-12-04
I had to turn ot CMS conversion.

---

