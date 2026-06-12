---
title: "Story of installing a Brother MFC440CN printer"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by PoppaK on 2011-05-20
I have just spent 6 hours over 6 days to get my network printer working with Ubuntu 10.4.  The printer was a Brother MFC-440CN, which was the first problem.  Installing the printer drivers was not straight forward and I finally resorted to a script I found on one of the forums.  

The printer was connected to a wireless router with an ethernet cable.  I have three other computers, all Windows, which have no problem printing on this printer. The real problem was that after the installation, Ubuntu could not find the printer.  The printer showed, but every time I tried to enable it, it could not connect because the printer 'could not be found'.  The printer properties showed:
Description: MFC440CN
Location: 192.168.1.39
Device URI: lpd://BRN_BF93081/BINARY_P1
All of these values were entered automagically by the driver installation process.  The Description and Location were clearly correct.  I was not sure of the URI because I did not know what it is.  BRN_BF93081 is the printer's name entered by the Brother factory and probably unique.  I had a feeling that the problem was with the URI, but I could not find its definition or syntax.  I went to several books, Ubuntu and others.  Some of them referred to URI, but none of them defined it.  Typically the texts said 'enter the URI' without telling you what it was or how to find it.  I finally found the answer in Wikipedia.  URI is a combination of URL and URN, the printer network address and printer name.  I first changed
Device URI: lpd://192.168.1.39/BINARY_P1.
It worked!  Then I thought 'What kind of a name is BINARY_P1'?  So I changed it to the real printer name:
Device URI: lpd://192.168.1.39/BRN_BF93081.
That worked too.

I hope this note will someday save someone a lot of frustration.  Who ever thought of using Wikipedia to install a printer and why did the driver installation screw up the URI?  How many of you know the syntax of a URI?

---

