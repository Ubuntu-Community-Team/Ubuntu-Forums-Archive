---
title: "Network Printing Issue"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by mcgodx on 2010-10-20
I am trying to set up Ubuntu 10.10 at work for my desktop, as I am more comfortable doing most tasks that I do on Linux than I am with Windows (and the fact that it's free is a plus to my boss), and there's a problem I am running into.

We have a Ricoh 2232C printer, which is a color laser printer.  The drivers are available in Ubuntu, and it shows up when I search for a network printer.  However, when I go to print (test page or files, it doesn't seem to matter), I just get what appears to be code on the page, and it will print many blank pages (15 blank pages got through before I cancelled the job at the printer).

Here is what got printed on the page, if that helps any:

```
%!PS-Adobe-3.0
              %% %%
                   mark
                       () () (20140010201608 {setuserinfo} stopped
                                                                  cleartomark
                                                                              %%%!
```

It's probably just cut off, there may be more to it, but I have no idea what's going on.  If this can't get resolved I guess I'll have to suck it up and use Windows, which is kind of a shame since everything else seems to work swimmingly.  Never had printing issues in the past, so of the things that wouldn't work, I'm a little surprised it's printing.

Thanks again for any help!

---

### Post by chili555 on 2010-10-20
Is it a network printer that is attached to a Windows computer or is it attached to a router or switch? Please show us how it's set up in System > Administration > Printing. Please see attached.

---

### Post by mcgodx on 2010-10-20
> **chili555 said:**
> Is it a network printer that is attached to a Windows computer or is it attached to a router or switch? Please show us how it's set up in System > Administration > Printing. Please see attached.

Thank you for the reply.  Ill post a screen shot when I get to work tomorrow, however it is attached to a switch.  It is one of the large Ricoh standalone MFPs.

Thanks again

---

### Post by mcgodx on 2010-10-21
Here is a screenshot of how the printer is configured.  Thanks!

---

### Post by SeijiSensei on 2010-10-21
Apparently CUPS thinks this printer accepts raw Postscript code and interprets it to produce the printed page.  My guess is that the printer itself isn't configured to support Postscript.  If you can add PS support without interfering with anything else, I'd give that a try first.

Otherwise you might consider connecting to the printer as if it were on Windows if the printer offers an SMB interface. How do Windows machines see the printer? If they connect to shares like \\ricoh\printer, you can configure CUPS to do that, too.  Then CUPS will render the pages on your machine and send the finished output to the printer.

---

### Post by mcgodx on 2010-10-21
> **SeijiSensei said:**
> Apparently CUPS thinks this printer accepts raw Postscript code and interprets it to produce the printed page.  My guess is that the printer itself isn't configured to support Postscript.  If you can add PS support without interfering with anything else, I'd give that a try first.

Otherwise you might consider connecting to the printer as if it were on Windows if the printer offers an SMB interface. How do Windows machines see the printer? If they connect to shares like \\ricoh\printer, you can configure CUPS to do that, too.  Then CUPS will render the pages on your machine and send the finished output to the printer.

I'll have to look and see if it supports SMB, as all the Windows machines in the office connect through it by the IP address, and not through samba shares.

Thanks for the tip though, if anyone else has any other ideas that'd be cool too.

EDIT:  I couldn't figure out how to enable SMB printing on the printer (it seems to only support it as a document server, though I am not sure on that one, I will ask someone who knows more about it later on today), however I tried sharing it through a Windows machine, and I got the same result, printed out pages with the same code on it.

---

### Post by mcgodx on 2010-10-21
Also, found that if I use the generic laser PCL drivers I can print in black and white, but I'll need color for what I'm printing.  Just thought I'd update on what I have found so far.

---

### Post by mcgodx on 2010-10-21
Okay sorry to put 50 posts in a row, but I figured I'd make a new one since I solved my issue!

I didn't know if the generic drivers would work so well, but they work flawlessly.  I picked "Generic PCL 5c Foomatic/hpijs-pcl5c [en]", and color works, duplex works, and I can even maybe pick different paper trays, although that part isn't so important to me.

So anyone who has Maverick (possibly other versions as well), and needs to get a Ricoh 2232C to work, that appears to be the best bet as far as drivers go!

---

