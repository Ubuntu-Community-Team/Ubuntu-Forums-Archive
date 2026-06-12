---
title: "FTP stops transferring"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by davethewave83 on 2012-01-16
When I am transfering files over FTP (FTP server = Filezilla/xampp) it copies about 697Mb and then stops. There's no error message, it just stops/stalls/pauses. It still says copying and 54 minutes remaining, but after 3 hours it still says 54 minutes, and is still only 697Mb done. 

If I press the X to close the progress window, the X greys out, but the window stays open. 

what's up? Is this a timeout issue with my server?

---

### Post by lz1dsb on 2012-01-16
I could be an issue with your FTP server. So you should check it out. Which FTP server package are you using?
But also the client itself should be checked? For the record. Did you check transferring the same file with another FTP client?
And is it always the same? I mean is it always stopping at a particular point...

---

### Post by davethewave83 on 2012-01-16
> **lz1dsb said:**
> I could be an issue with your FTP server. So you should check it out. Which FTP server package are you using?
But also the client itself should be checked? For the record. Did you check transferring the same file with another FTP client?
And is it always the same? I mean is it always stopping at a particular point...

The server is Filezilla on Xampp (Windows) 
the client, I'm just using regular nautilus/gnome, typing the address in and browsing like a folder. 

With Xampp on windows I also set it up to allow browsing via HTTP, so I just download the files with HTTP and there's no issue. The files complete 100% with HTTP, FTP stalls out at random times.

---

### Post by lz1dsb on 2012-01-16
That's interesting. Did you try it out with another FTP client?
I think it's worth a try. I often use Filezilla as FTP client...

---

