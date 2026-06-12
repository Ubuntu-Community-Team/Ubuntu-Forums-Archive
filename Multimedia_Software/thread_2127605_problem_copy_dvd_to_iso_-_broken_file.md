---
title: "problem: copy dvd to iso - broken file"
date: 2013-03-20
forum: Multimedia Software
---

### Post by alfh on 2013-03-20
1. I started brasero and chose to copy the dvd to image file.
2. Brasero reported success.
3. Playing file in VLC, working flawlessly until unexpected exit at approx. 1 hour 28 mins 20 sec. No error message.
4. Trying the file in Movie Player. Unexpected exit at the same time, with this message: "An error occured. Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed."
5. Check that all libraries and ladidah from medibuntu repo are installed. They are. 
6. Repeat steps 1 through 5.
7. Get the ppa [https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools) and replace wodim with cdrecord and geniosimage with mkisofs.
8. Throw out brasero and install k3b.
9. Repeat steps 1 through 5, with k3b not brasero.
10. Ask ubuntuforums for help.

Additional info: The dvd plays without a hitch on our standalone dvd player. It also played without problems on vlc prior to making the iso image. After making the image both VLC and Movie Player chokes on the dvd (not the image) at approx. 1 hour 28 mins 20 sec. As might be expected, I'm stumped and puzzled. How come both brasero and k3b reports "success" when in fact the image must be broken?

Thankful for any and all input.

---

### Post by ManamiVixen on 2013-03-20
1 Hour and 28 Minutes is the EXACT length of a typical Music CD. Essentially none of the music playback, video playback, or Disc Copy applications expect a music DVD. That is your issue.

---

### Post by alfh on 2013-03-20
Sorry, I don't understand. You mean the copy function of both brasero and k3b thinks this movie dvd is a music CD?

---

### Post by alfh on 2013-03-22
Bump!

---

### Post by alfh on 2013-03-23
...and: bump...

---

