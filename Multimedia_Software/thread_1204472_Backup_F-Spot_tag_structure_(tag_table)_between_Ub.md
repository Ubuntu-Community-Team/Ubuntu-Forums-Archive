---
title: "Backup F-Spot tag structure (tag table) between Ubuntu installs?"
date: 2009-07-04
forum: Multimedia Software
---

### Post by skyttan on 2009-07-04
Hi!

I have searched the internet for hours now and I still haven't found an answer!
I recently installed Ubuntu 9.04 from scratch. I had my pictures wich I organised with F-Spot backed up. I made F-Spot write metadata into my photos so when I imported them again into F-Spot earlier this day all my photos are correctly tagged - but the problem is that all the tags are under "Import Tags" instead of being organised in a "tag table" as before (in 8.10), e.g. "Events -> Birthdays - Johnny's Birthday 2008" and so on.
While searching the internet I discovered that F-Spot stores this architecture of tags in *~/.gnome2/f-spot/photos.db* along with everything else. I opened the file with both sqlite3 and sqlitebrowser but I don't understand how to use them. [Here]("http://f-spot.org/Database") it says (manually copied and set up table):
Photo_tags table -> This table holds the association of tags to photos.

  Field name -> Meaning:
  photo_id   -> Photo ID on the photos table
  tag_id     -> Tag ID on the tags table

My question is: **Is it possible to back up and restore this tag table so I doesn't have to manually organise all my tags (set parent tags etc.) every time I install Ubuntu / another distro with Gnome / F-Spot from scratch?**

---

### Post by msktje on 2009-07-09
Hello,

I think you actually stated the anwser yourself. Normally everthing is stored in photos.db 

What i tried with karmic to check this was:
boot from live cd
start f-spot
close f-spot
go to ~/.gnome2/f-spot/photos.db 
remove this photos.db and paste yours
start f-spot
in my testcase i had my labels in the correct place even with sublabels
next you can chose update pictogram. to view your photos

this way you can check if everythink is correct.

one thing: be sure that the path to the foto's are the same. I had the problem because i hadn't label my usb disk. One time it was sdb the other time it was sdc.

---

