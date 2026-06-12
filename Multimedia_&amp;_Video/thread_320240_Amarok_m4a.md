---
title: "Amarok m4a"
date: 2006-12-17
forum: Multimedia &amp; Video
---

### Post by Reishka on 2006-12-17
I can't seem to figure out what I'm doing wrong. No matter what I do I can't seem to get Amarok to want to play m4a files. I have the amarok-xine and the libxine-extracodecs packages installed, and I still can't get it to play. I've also tried uninstalling and reinstalling Amarok to no avail. It still says I have no codec support for m4a. Everywhere I look, I'm told that Amarok should already come with m4a support.. so.. I shouldn't be having this issue? 

Anyone have any help?

---

### Post by FullFrontaln00bity on 2008-03-20
I would like to know the answer too.

---

### Post by logos34 on 2008-03-20
try

sudo apt-get install** libxine1-ffmpeg**

---

### Post by shacamin on 2008-03-31
I just tried that, and it said I already had it installed.

With the extra codecs package, the error message changed from "No codec found" to "There is no audio channel!"

This applies to VLC as well.

---

### Post by AusIV4 on 2008-03-31
This probably won't be very helpful, but when I first installed Amarok, it wouldn't play m4a files. When I tried to play an mp3, it offered to install the appropriate codecs. After that, m4a files played as well.

---

### Post by bruno9779 on 2008-06-07
The "there is no audio channel" error doesn't have to do with the codecs.
I usually get it when amarok gets in conflict with another media player based on Xine (usually it happens to me when Kaffeine player doesn't shut properly)
Try restarting the system or check on the system monitor if you have any "zombie" media player.

Hope it helps

---

### Post by hakonatli on 2008-07-22
Excellent thanks. I typed sudo get-apt etc. as described above and it worked like a charm!

/salute

---

