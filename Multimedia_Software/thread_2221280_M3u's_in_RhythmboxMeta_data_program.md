---
title: "M3u's in Rhythmbox/Meta data program"
date: 2014-05-01
forum: Multimedia Software
---

### Post by cranerja on 2014-05-01
I have about 50 gbs of horrifically unorganized music. The only sorting done has been through m3u's created in Windows. What I'm looking for is a program that can either; Correct the m3u files by changing the C:\\ part in the filepath or; a program that scans each mp3 and sets the meta data accordingly.
Either of these exist?

---

### Post by tgalati4 on 2014-05-01
*easytag* can fix ID3 tags.  With clever use, you can auto-fill ID3 tags based on filenames.  Otherwise, you would need to write a script to read the m3u files and then use command-line ID3 tools to update the track information.

Many music players can fix ID3 tags as well.  Load a directory of tracks into *rhythmbox* and try fixing from within *rhythmbox*.

Open a terminal:

```
apt-cache search ID3
```

---

### Post by Yellow Pasque on 2014-05-01
I think what you want is to use sed command to replace one string with another.
sed syntax always drove me crazy, so hopefully, someone else can give you the exact command if you can't figure it out.

---

### Post by cranerja on 2014-05-01
You misunderstand, these files are not organized at all including filenames. I'd need a program that scans the audio and compares it do a database, similar to how many phones can now.
 
I don't know how sed works either o:

---

### Post by Yellow Pasque on 2014-05-01
> **cranerja said:**
> You misunderstand, these files are not organized at all including filenames. I'd need a program that scans the audio and compares it do a database, similar to how many phones can now.

I thought you wanted to replace C:\WindowsMusicPath\filename with /home/whatever/filename in the m3u file? sed would do that.

---

### Post by cranerja on 2014-05-02
I know, that part was to the other response. I haven't figured out how to separate responses. I'll look into sed, just haven't heard of it

---

