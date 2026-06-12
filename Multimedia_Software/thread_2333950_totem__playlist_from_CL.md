---
title: "totem : playlist from CL"
date: 2016-08-14
forum: Multimedia Software
---

### Post by crackers_altitude on 2016-08-14
Is there a command line (CL) flag or some special syntax for totem to take a list of videos as arguments on the CL? Something like

totem --list=video1.m4v,video2.m4v,...videoLast.m4v

I haven't gotten the hang of the GUI yet to do this. If there's a file to read in on the CL I didn't get that either.

---

### Post by mc4man on 2016-08-15
Yeah, just lose the --list=  (and put a space between file names )
If prompt at containing files then totem ./file1 ./file2 ./file3  or if spaces in file name then ./'file1' ./'file2' ./'file3'
If not at prompt containing the use full path from prompt, totem /path/to/file1 or /path/to/'file1'  ect.
or just create a .m3u file & play that

---

### Post by crackers_altitude on 2016-08-15
well it works just like I expected now. I don't know what was going on before but the gray matter is suspect. thanks anyhow.

---

