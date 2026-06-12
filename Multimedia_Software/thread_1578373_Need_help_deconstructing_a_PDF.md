---
title: "Need help deconstructing a PDF"
date: 2010-09-20
forum: Multimedia Software
---

### Post by gradysghost on 2010-09-20
I've come across a strange situation at work, and I'm trying to solve it.  Here's the short version:

A department's website currently has links to PDFs.  These PDFs contain forms that the user fills out, and they also contain buttons that supposedly send copies of those PDFs to various email accounts in the department.  But this is really inefficient, and the forms do not work in Mac or Linux, which the department would like to remedy.

Furthermore, the department has changed directors and much of its staff, and now **nobody knows what email addresses these PDF forms send emails to**.  It's my job to fix this.  I would like to redo these forms so that they're web based (which I'm perfectly capable of doing), but I need to get the department caught up by finding out what email addresses the PDFs are sending themselves to.

**How can I deconstruct a PDF to a point where I can determine the actions taken when the buttons in the PDF get clicked?**  Are there any native Linux tools to help me do this, FOSS or otherwise?  I've tried pdfedit, but it's very confusing, and I can't figure out how to convince it to do what I need it to do.  pdftk doesn't seem to have the functionality I need, either.

Can anybody here offer me any advice?

Thanks in advance!

---

### Post by efflandt on 2010-09-20
You might try adding **openoffice.org-pdfimport** package with Synaptic and see if that can do it.  It opens a pdf file in openoffice Draw.  But I don't have any pdf fill out forms or with links on my new PC (just a cups-pdf of a web page) and IRS 1040 fill out form seemed to error (maybe locked to avoid modification).

---

### Post by gradysghost on 2010-10-27
I'll be closing out this ticket.  I've discovered that the PDF in question has some crazy ColdFusion scripting embedded in it for processing, and there's someone else who has permissions to edit it.  This isn't my problem anymore.  Thanks, though.

---

