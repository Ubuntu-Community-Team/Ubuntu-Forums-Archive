---
title: "How to create a true network scanner"
date: 2015-11-18
forum: Multimedia Software
---

### Post by spillemw on 2015-11-18
I have a Brother 7650 DCN that is network attached.
However, if you want to scan across the network, you must select a PC that is on and preferably not too far away as you may have to accept the incoming scan.
Alternatively, with sane, you can acquire the scan from the scanner as well.
That is not a true network scanner of course.

What I want to do is to scan to one of the ubuntu servers on my network, save the scan (preferably in a PDF format) in a directory, then email the contents of that directory and erase the directory afterwards.

The latter part is easy : I can set up a cron job that checks a directory every 5 minutes or so and emails the contents.

However, I do not know how I listen on my ubuntu server for an incoming scan.  I also do not know what format the Brother printer sends the information in.  I guess I have to listen on a certain port, but i dont know which port.
I cannot find a daemon that does this already.

Any help?

---

### Post by tgalati4 on 2015-11-18
How far apart is the printer from the server?  This Use Case might be easier if the printer is hung off the server with a USB cable.  Then share the printer from the server's CUPS.  

Otherwise, check the Completed Jobs page

```
http://localhost:631/jobs?which_jobs=completed
```

Perhaps write a curl script to to detect a network scan request.

Most true network scanners will scan, store and forward the scans right from the printer itself.  It has a file server built-in.  They are not cheap.

---

