---
title: "mythbuntu 8.04 media library help"
date: 2008-11-02
forum: Mythbuntu
---

### Post by zf3636 on 2008-11-02
how can i send my video files and mp3s to my myth frontend and access them in my media library, i can play dvds and cds but do not know how to store them to create a video library without taking up too much space on the hard drive.

---

### Post by volkswagner on 2008-11-02
> **zf3636 said:**
> how can i send my video files and mp3s to my myth frontend and access them in my media library, i can play dvds and cds but do not know how to store them to create a video library without taking up too much space on the hard drive.

You may need to clarify here.

Where are "my video files" located?  Are they on an external hard drive or remote PC?

You can rip cd's an dvd from mythtv.  The directory where to rip them is specified in the respective setup screens.  Music and video settings.

To reduce the size of a dvd you may need to transcode.

CD rips can be large lossles format or small mp3's with 128kbps sample rate to reduce file size.

---

### Post by SiHa on 2008-11-02
As a follow-up to Volkswagner, your videos & music should be stored in **/var/lib/mythtv/videos** & **/var/lib/mythtv/music**, on your backend machine.

Checkout this thread:
[http://ubuntuforums.org/showthread.php?t=908779](http://ubuntuforums.org/showthread.php?t=908779).

For a guide on mounting these directories so that they can be accessed on your frontend.

HTH

Simon

---

### Post by zf3636 on 2008-11-03
I have a single drive which i have used to install mythbuntu 8.04 on, most of the setting are set to default recording, i am yet to set the file directories once i have learned how.Thank you for a quick reply will act on the links you have provided.

---

### Post by zf3636 on 2008-11-03
> **volkswagner said:**
> You may need to clarify here.

Where are "my video files" located?  Are they on an external hard drive or remote PC?

You can rip cd's an dvd from mythtv.  The directory where to rip them is specified in the respective setup screens.  Music and video settings.

To reduce the size of a dvd you may need to transcode.

CD rips can be large lossles format or small mp3's with 128kbps sample rate to reduce file size.

i have a external drive which i want to transfer to the one on mythbuntu 8.04 so when i click my videos i can then view or watch videos, when i place a dvd to transcode reply i get this not xml

---

### Post by SiHa on 2008-11-03
The directories **/var/lib/mythtv/videos & /var/lib/mythtv/music** should already be on your backend machine - assuming you istalled the Mythmusic & Mythvideo plugins.
Copy your media files from the external drive to these directories, and a frontend on the same machine will be able to play them straight away. If you need to play them from a remote frontend, you will need to setup the nfs share, as described above.

---

### Post by zf3636 on 2008-11-04
SOLVED! I have know created my directories,now i have a working media library 
and music library thank you SiHa Volkswagner for your quick reply and help.

---

