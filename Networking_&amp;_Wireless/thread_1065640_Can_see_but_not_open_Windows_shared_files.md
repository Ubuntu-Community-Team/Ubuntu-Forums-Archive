---
title: "Can see but not open Windows shared files"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by delboy1 on 2009-02-10
I have a Windows Home Server and am trying to open files from it on my Dell Mini 9 with 8.04 (Dell)

The problem I have is that I can mount the folder and see the files but I can't open them. For example, if I try to open an mp3 file, Rhythmbox opens but then immediately closes. Similarly, with Office files - OpenOffice opens but immediately closes, etc.

However, I can copy the file on to my desktop and then it will open normally. So the problem seems to be streaming.

Someone suggested to me last week that this is likely to be a Samba problem but that was the only information he could offer??

Does anyone have any ideas as to how I can get these files to stream

---

### Post by halovivek on 2009-02-10
whether you have given the proper rights to view and edit the files in the share folder?

---

### Post by HavocXphere on 2009-02-10
Not a streaming issue per se. Most music players download everything in one go. Same for OpenOffice.

Not a samba issue either imo.

halovivek is probably right, the problem is likely to be related to write access...more specifically the security settings on the MS box. Sounds to me like the apps are requesting R/W access, the windows box refuses and samba returns an access denied error that the apps can't handle. Copying the files opens them with R/ access so that doesn't bail. Remember to check both sharing permissions *and* security premissions (to do this temporarily disable simple file sharing)
:KS

---

### Post by delboy1 on 2009-02-10
Hmmm

No problems with any other computers my Vista laptop, my XP PC and both my and my wife's two XP work laptops can all see and open the files so not convinced it is a "security settings" issue at the WHS end. Definitely seems to be an Ubuntu / Netbook issue?

---

### Post by DiGiTGOD on 2009-02-10
You have to remember that windows and windows will "probably" work well...

However using, say, OpenOffice, to open a MS Word document, may open it a different way.

For instance, when opening a Word Document, it will open it with Read/Write by default in MSWord, however, if it doesn't have access to write, it will open a read only copy and say that in the top bar of the window.

Don't know much about open office, but that may be your problem...

To rule it out... why not just try and give Write permissions, and re-test... if that doesn't fix the problem, I'm sure everyone will hold their hands and think of a different solution...

---

### Post by delboy1 on 2009-02-10
Back home now and checked WHS Box. As I suspected all files are already set with full R/W permission. Anyone got any further thoughts?

Cheers

---

### Post by delboy1 on 2009-02-11
The problem is getting a bit weirder.

I have now found that I can open MP3 and video files in Movie Player but not in Rhythmbox or VLC. Rhythmbox starts but then immediately closes. VLC opens but reports cannot retrieve file.

I can't open any documents or spreadsheets at all. Open Office starts but immediately closes. As above all files on the WHS box have full permission granted to all users.

---

### Post by delboy1 on 2009-02-12
Anyone got any ideas that might help with this?

---

