---
title: "[Shotwell] Dealing with a complicated recovery"
date: 2014-01-25
forum: Multimedia Software
---

### Post by eternal404 on 2014-01-25
Okay, so my home folder was wiped (stolen laptop) and I could get most of my photos/videos back thanks to [Prey]("http://preyproject.com/") and [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec").

I had quite a consequent Shotwell library (20k+ items with custom events and tags) and I'd like to avoid rebuilding it from scratch.

Here is what I got:

[LIST]
[*]A recent backup of the Shotwell database (photo.db);
[*]A recent backup of my photos (no videos) in low resolution;
[*]A partial (~10%) backup of my original library (photos/videos);
[*]A partial (~70%) original library recovered with PhotoRec. The file names differ from the original, but the metadata (EXIF/M2TS) is still present.
[/LIST]

I'm looking for an optimal way of merging all this mess into Shotwell.
I'm unsure about how Shotwell handles duplicates. According to one developer, it relies exclusively on hashes.
[QUOTE=Jim][COLOR=#000000]Shotwell [/COLOR][COLOR=#000000]will use (exclusively) a full MD5 hash of the file to perform duplicate [/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]checking, which is a pretty darn accurate way to find duplicates[/COLOR][/QUOTE]


So I'd probably go that way:

[LIST]
[*]Restore the backup of the database;
[*]**Copy** the ~10% backup onto the managed directory; Shotwell should find the files by itself;
[*]**Import** the ~70% library into Shotwell, which will "recognize" the files from their hash, and detect duplicates. This should work, as [apparently]("http://csabyblog.blogspot.ie/2013/02/backtrack-forensics-file-recovery-with.html"), (most of the) files rebuilt by PhotoRec have the *exact* same hash as the originals.
[*]Lastly, the low-resolution backup. This is the tricky part: The JPEGs were shrunken, so the hashes won't match Shotwell's database. AND I stripped their EXIF metadata upon compression to save space (yeah..). BUT the filenames and directory structure are preserved.
So I tried importing an original image into Shotwell, then modifying it outside of Shotwell and stripping its EXIF data, while preserving its path and filename. And surprise, Shotwell seems to consider it the same item (it even updates the thumbnail, which proves it detected the change). So in this case, the filename clearly prevails over the hash.
So, I'd **copy **this backup onto the managed directory, and ask the copier not to erase already present items. Then I'd fire Shotwell and it should "recognize" the photos based on their path/filename regardless of their EXIF/hash.
[/LIST]

How does that sound ?

---

