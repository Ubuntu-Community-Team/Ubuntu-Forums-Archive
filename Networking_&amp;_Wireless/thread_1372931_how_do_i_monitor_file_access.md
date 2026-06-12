---
title: "how do i monitor file access ?"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by QuanTime on 2010-01-05
Karmic 9.10 x64 Gnome.

On my home LAN, i want to be able to monitor what files are being access on my local machine.
I had a quick look at wireshark, but it didnt do exactly what i wanted.

I have a share directory, read-only, and often divx files are streamed directly from it rather than copied first.  I want to be able to see what user is accessing what file.  Should be a fairly simple task, but im just not sure how its done.

Anyone with clues please ?  It can be terminal based, doesnt have to live and constantly updating, just a report.  But a prog with a GUI would be useful too.

Thank you in advance.

---

### Post by changingstate on 2010-01-05
I'm guessing Samba audit trails are what you're looking for. 

A quick google turned up a random blog post : [http://a32.me/2009/10/samba-audit-trail/](http://a32.me/2009/10/samba-audit-trail/)

See how that works.

---

### Post by QuanTime on 2010-01-05
yer, thats not bad, but id rather not have a logfile. rather just a direct output.  

```

lsof -i

```

Sorta along the lines, but its not really it still..  That guide has the output results, but if it was a simple command and output, id prefer that to some log file.

Anyone else ? it might be my only option.. Im just used to it from winxp days.  And its such a trivial thing, i thought it should be easy on linux.. Weird.

---

### Post by changingstate on 2010-01-05
Oh, ok. Something like smbstatus, perhaps? :)

---

### Post by QuanTime on 2010-01-05
looks like i owe you a beer.. Thats just perfect.  The UID im guessing is the user ID.. which i have to manually lookup ? there a shortcut for that too ? :)

---

### Post by SlugSlug on 2010-01-05
smbstatus |grep [file name]

and then smbstatus |grep [pid]

will show you samba user

---

