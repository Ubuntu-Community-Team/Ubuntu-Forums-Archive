---
title: "Amarok will not play MP3's"
date: 2008-07-04
forum: Multimedia Software
---

### Post by james_xxx on 2008-07-04
Yet once again, Amarok will not play MP3's. ALL other audio apps will. All codecs are installed.

I had this happen in Gutsy, too, but then all I had to do was delete /.kde/share/apps/amarok and start over. This time that is not helping. All I get is the prompt asking me whether or not I want to install the codecs.

I would be grateful for any suggestions.


[I am reposting this, as the title in my last post became SERIOUSLY botched.]

---

### Post by james_xxx on 2008-07-04
OK, after seeing another related post, I got Amarok to work by running it as root [i.e. using 'sudo'].

This seems kind of strange. 

Anyone know of a workaround?

---

### Post by vandervelde on 2008-07-04
I have same problem (with sudo program is working perfectly)...i think there is some problem with permissions in amarok folders/files, something which sudo override...

---

### Post by james_xxx on 2008-08-26
I just thought I'd post again to this thread to attempt again to find a solution to this issue. 

To recap, Amarok plays MP3's just fine if run as root, but if run by user, it claims it cannot play MP3's.

Any suggestions are welcome!

---

### Post by ShadowWraith on 2008-08-26
If this problem is related to libxine1-ffmpeg, this is a problem with the repositories that I can't figure out how to resolve. But you can get the latest and compatible version here:
[https://launchpad.net/ubuntu/hardy/+package/libxine1-ffmpeg](https://launchpad.net/ubuntu/hardy/+package/libxine1-ffmpeg)
Choose your architecture, make sure it ends in 3.1 and not 3, download, and install using sudo dpkg -i package_name.deb

---

