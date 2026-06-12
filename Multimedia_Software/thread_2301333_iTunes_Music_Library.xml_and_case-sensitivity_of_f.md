---
title: "iTunes Music Library.xml and case-sensitivity of file paths"
date: 2015-11-01
forum: Multimedia Software
---

### Post by David_Westwood on 2015-11-01
Hi,
 
I've  been trying to move my iTunes music library from a case-insensitive  system (iTunes 12.3.1.23 in Windows 8.1) to a case-sensitive system  (Linux Mint 17), and I'm encountering problems with the "iTunes Music  Library.xml" file. In Windows, it doesn't matter that the specified path  in the .xml document doesn't exactly match the name of the  corresponding file. For instance, the .xml document lists the path of  The Beatles' "A Taste of Honey" as /.../04%20A%20Taste%20of%20Honey.m4a  but the filename is "04 A Taste Of Honey.m4a". The only difference is  that "of" is capitalized in the filename, but not in the path specified  in the .xml file. This causes the track's metadata not to be imported in  Linux because it's looking for "04 A Taste of Honey" with the lowercase  "of". Is there a way to rewrite the iTunes Music Library.xml file so  that it matches the filenames to the paths in a case-sensitive way?
 
Thanks!

---

