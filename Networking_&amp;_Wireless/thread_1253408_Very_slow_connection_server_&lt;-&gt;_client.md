---
title: "Very slow connection server &lt;-&gt; client"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by obg123 on 2009-08-30
I have a private server which accepts ssh connections (local and external). This server runs Ubuntu server 8.10. I have had no problems with connection speed, when accessing external sources from this server. However, when I transfer files (sftp or scp) to or from this server using a Windows client, I get rates of max 3-4 MB/s. It should be at least twice that much on a wired 100 Mbps network using rather modern computers.

The big surprise, however is when I use my laptop (which was almost top of the line a year and a half ago), running Ubuntu 9.04 through a wireless link, I get rates from 150-170 kB/s!? Downloading (http, ftp...) from external sources I usually get rates higher than 1 MB/s through the same link plus an 18 Mbps ADSL connection. Of course, this is not acceptable!

Now, this feels rather awkward, as I am not a beginner with Linux. I do have a hard time finding my way around Ubuntu, however, as there are lots of differences from other distributions. Here, I really don't know even where to start... :( So, could anyone please point me in the right direction?

---

### Post by Iowan on 2009-08-30
On earlier versions, internet access sometimes suffered due to IPv6.  Dunno if IPv6 might affect server access or not.

---

### Post by obg123 on 2009-08-30
Yes, good idea. I actually planned to disable IPv6 for other reasons as well (before I forgot about it). Do you know straight away how to do that, or shall I research (which I don't really have time for right now)?

---

### Post by Iowan on 2009-08-30
Unfortunately, the "Disable IPv6" link in my sig is a couple of versions old.

---

### Post by obg123 on 2009-09-02
Ok, with IPv6 disabled, I get an increase in transfer rate. Now I'm up to 650 kB/s with scp. This is still not acceptable. I am currently doing an external download to the same server which ticks at about 30 kB/s. It gets completely suffocated by my scp...

Something is very fishy here, and I don't understand what it might be. Please, I need help!

---

### Post by obg123 on 2009-09-10
Isn't there anyone who at least could tell me where to start looking? Another clue is that it takes very long time (6-7 sec before anything happens using ssh) to log in from my Ubuntu 9.04 workstation. I have upgraded (dist-upgrade) the server now. - Still no change... :(

---

### Post by obg123 on 2009-09-14
Well, this was some source of information... :( All I needed to do was to add both sites to the hosts file, in order to prevent the reverse lookups issue. Now the logins are instant and transfer rates is still a bit low at round 1 MB/s, but acceptable.

Is anybody reading this?

---

### Post by Iowan on 2009-09-14
> **obg123 said:**
> Is anybody reading this?Yup. I thought the SSH login to my server was slow because it was a P200, but the P500 is just as slow. Which "sites" did you add to the */etc/hosts* file?

---

