---
title: "Kodak ESP 3250 64 bit Drivers"
date: 2011-01-15
forum: Multimedia Software
---

### Post by 'Bohr124365 on 2011-01-15
Hi guys,

I've recently upgraded to x64, but I'm struggling to get the drivers working for my Kodak ESP 3250 printer. I've installed the CUPS driver and I'm using the driver package for the ESP series of printers, but it's not working great. It printed a beautiful test page, which was good! But then I tried to print a PDF document out. Page one came out beautifully - much faster than on Windows - but it hangs half way through the second page. I've tried printing other documents, and it hangs on all of them, even the test page. And when I say hangs, it prints about half the page, and just sits there with the paper half in it, waiting...

Any ideas would be much appreciated! It appears it can work, just intermittently! 

Cheers,

Tom.

---

### Post by 'Bohr124365 on 2011-01-17
Update:
I restarted the machine, and I've managed to get the first two pages of the document to print. After that, however it just hangs. The printer still says 'printing' on it, however it instantly clears from the print queue. Perhaps an issue with it spooling too quickly?

---

### Post by paulnewall on 2011-01-29
I think there is a problem with c2esp. If your document is large and your PC is very fast you get way ahead of the printer.
The printer will timeout if it does not get sent something regularly from the PC.
I am working on an update to fix this.

---

### Post by 'Bohr124365 on 2011-01-29
Thanks for your reply, Paul. The document was text PDF of about 140KBs, but I've tried other documents and they all behave the same way, unfortunately. It's a shame Kodak can't support Linux, as that's one of the only factors holding me back on fully switching to Ubuntu!

---

