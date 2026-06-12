---
title: "[SOLVED] Mythbuntu fronted help please"
date: 2008-03-08
forum: Mythbuntu
---

### Post by rickyble on 2008-03-08
I think I may have had a miss understanding but I just want to make sure I now do understand before I go down the wrong way.   I have a backend server and a separate frontend.  I chenged the install to make a small 30 gig drive my system with the exception of my home which resides on a 250 hd.  I have pointed the install of mythtv recordings to the home directory on the 250 and it shows up and reflects that in the settings.  I changed the video settings to point to home/downloads.  Underneath downloads are videos and music directories.  Both of these are shared by samba and the windows machine can save to tthem and play music and videos from them.  If I start the front end on the server it will see the videos and let me access them also and play them along with the music.  The problem is the fronted box can read the database and shows that the videos are there but it can not access them no matter what settings I seem to use the frontend can not access them. So it must be seeing them from the list in the database and not for "real".  My question from the other postings and piecing together is that I think I have to make a NFS mount on the server side and then mount them automatically from the frontend to play the videos music and recordings.  The install setup does not provide for access to the backend videos and music or recordings.  Is this correct or is that flawed.  If it is flawed please can you help me understand.  If it is correct I will get busy with the mounts and making them permenant.  Thanks in advance.

---

### Post by newlinux on 2008-03-08
Yes, each remote frontend must mount the mythvideo and mythmusic files locally. They should be mounted to the same spot on all machines.

---

### Post by rickyble on 2008-03-08
Thanks so much.  I was about to go crazy until I did some searching.  I saw yours and some other postings about mounting and making them permanent.

Is there anything that has to be done on the backend server or is this already done in the installation?  Or do I have to export the server subdirectories?

---

### Post by newlinux on 2008-03-08
I think (I don't know because I don't use mythbuntu, just have myth installed on ubuntu) the default mythvideo directory is already exported (or shared via SAMBA), but I don't know for sure...

---

### Post by rickyble on 2008-03-08
You were right they are already.  Also I found the old thread and used smb and mounted that way.  Not sure if NFS or Samba is better.  The Samba seemed to work ok.  Thanks

---

