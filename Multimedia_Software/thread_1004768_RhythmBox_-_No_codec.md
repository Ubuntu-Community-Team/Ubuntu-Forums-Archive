---
title: "RhythmBox - No codec"
date: 2008-12-07
forum: Multimedia Software
---

### Post by russofris on 2008-12-07
Good afternoon,

When Rhythmbox 0.11.6 scans my library, it determines that there are a number of files for which I do not have a codec installed.  It then offers to search for a codec.  The result of the search is fruitless, and no suitable codec is found.  Here are my current issues.

1:  At no point is there any indication of what file is affected, what the file extension is, or what codec was used to compress it.  This makes tracking down the codec by hand, or transcoding the file to a compatible codec, extremely difficult.

2:  When searching for a codec, a button to "purchase licensed codecs" is presented without any indication of whether the "licensed codecs" will resolve the issue I am facing.  I feel that this is both misleading and immoral.  The button should only be presented in cases where it is 100% certain that the licensed codec pack contains the codec needed for playback.

Do either of these two issues constitute a launchpad defect?

Frank

---

### Post by russofris on 2008-12-07
Upon further examination, I have located the import errors log.  The affected files are rmj files (files compressed with a codec from the misguided company RealNetworks).  I have purged my library of this blight.

Frank

---

### Post by Valde_91 on 2008-12-08
Same here! But How did you find which files aren't play? 

Thanks Valde_91

---

### Post by russofris on 2008-12-09
Look at "Library" on the left.  There will be a red icon under it called "Import Errors".

Frank

---

