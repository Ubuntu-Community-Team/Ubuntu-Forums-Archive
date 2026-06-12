---
title: "How to create playable video ISO"
date: 2009-01-24
forum: Multimedia Software
---

### Post by addsalt on 2009-01-24
I have ripped most of my DVDs to my hard drive in Video_TS folders. I would like to put them into an ISO format to have them in one nice container to play with VLC. If I create an ISO straight from the DVD, I have no problem playing it in Totem or VLC. When I create an ISO using ISO Master or using  mkisofs the ISO will not play. VLC gives the error:
 
dvdread demux error: DVDRead cannot open source:

and Totem gives 

Could not open location; you might not have permission to open the file.

If I mount the ISO, it will play fine. Any ideas?

---

### Post by addsalt on 2009-01-26
bump. 

Anyone have an idea - it is driving me a little crazy.

---

### Post by binbash on 2009-01-26
mkisofs -r -o file.iso /location_of_folder/

---

