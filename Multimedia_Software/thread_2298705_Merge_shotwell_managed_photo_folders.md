---
title: "Merge shotwell managed photo folders"
date: 2015-10-13
forum: Multimedia Software
---

### Post by paulb42 on 2015-10-13
Hi
I use Shotwell to manage my photos on Ubuntu 12.04. Most of my photos are in the Pictures folder, as standard, but for reasons I can't remember now I have some in a folder called Photos. I'd like to move the Photos folder contents to Pictures, but that will confuse Shotwell. What's the best way to do this? 
I won't be too upset if it involves losing tags..
Thanks

---

### Post by TheFu on 2015-10-13
I don't use shotwell.

However, if you move all the photos to where you want them and create a symbolic link from the new location to the old location  (directory level), I would be surprised if that didn't work.  But, you may end up with duplicate images inside the shotwell DB.  The **ln -s **command is what you want.  If you do backups (and you should), check how symbolic links are handled. You do NOT want double backups for all those big image files.

If there is a way to shove all the tags back into the original photos, I would do that.  For me, the single file- the photo should be the only source of metadata about a photo. Don't know if RAW can support that - I only have a PnS Cannon and the output is .JPG files. Those support Exif.

---

### Post by paulb42 on 2015-10-30
Turns out all I had to do was move the sub folders of Photos into Pictures and Shotwell just updated its library to reflect the move. 
Bit of a non-event really!

---

