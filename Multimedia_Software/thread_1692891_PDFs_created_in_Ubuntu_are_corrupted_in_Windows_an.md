---
title: "PDFs created in Ubuntu are corrupted in Windows and OS X"
date: 2011-02-22
forum: Multimedia Software
---

### Post by Curtos on 2011-02-22
I hope this was the right subforum for this post. :) 

I can't find any information on this online, which surprised me. Any PDF that I create or edit in Ubuntu, through printing to pdf or editing with Evince, etc, opens and looks fine in Ubuntu, but will not open in either Windows or OS X. 

I never really see the problem until I try and email a PDF to someone and then I remember the problem again. It's rather frustrating. Does anybody know what's going on or how I could fix it/locate the issue?

Thanks,

Curtos

---

### Post by aeiah on 2011-02-22
corrupted in what way? its possible that the PDFs are calling for fonts which do not exist. this may or may not mean the pdf looks messed up and filled with gibberish on another system, depending on if it can find a suitable font replacement or if the font is embedded in the pdf. do you have windows fonts installed? have you tested it with common fonts? this shouldnt be a problem though, but its worth a look. 

can you attach a sample pdf that doesn't work?

---

### Post by Curtos on 2011-02-22
Here's one that's been verified to fail when opening in Windows 7. 

This is the error: "There was a problem reading this document (14)." 

I downloaded the form, filled in a field with Document Viewer, and saved it. When printing to PDF, the document opened successfully, so this may be specific to forms.

---

### Post by kelver69 on 2011-02-23
I just tried opening it on a computer running XP and it had an error and wouldn't open.

---

### Post by Curtos on 2011-02-23
> **kelver69 said:**
> I just tried opening it on a computer running XP and it had an error and wouldn't open.

Thanks for confirming. I can open that form, after filling fields, in Ubuntu (Maverick) without a problem. I've tried searching with more specific queries related to Document Reader and forms, but still haven't found anything.

---

### Post by sebastien_vigneau on 2012-11-09
The bug has been reported by several people in [launchpad]("https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/897322?comments=all"). As a way around, it is possible to convert (and flatten) the pdf in ps using pdf2ps, then converting it back to pdf using ps2pdf. I hope it helps...

---

### Post by monkeybrain2012 on 2012-11-09
> **sebastien_vigneau said:**
> The bug has been reported by several people in [launchpad]("https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/897322?comments=all"). As a way around, it is possible to convert (and flatten) the pdf in ps using pdf2ps, then converting it back to pdf using ps2pdf. I hope it helps...

This is an old thread, the bug has been fixed. I filled the form with okular and evince and in both instances have no problem opening and viewing in WInxp (virtual box) I should have read the date before I waste my time checking.

---

### Post by lisati on 2012-11-09
If, as has been suggested, the bug has been fixed, we can safely let this thread go back to sleep.

---

