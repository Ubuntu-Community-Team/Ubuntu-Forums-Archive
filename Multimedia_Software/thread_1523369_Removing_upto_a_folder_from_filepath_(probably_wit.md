---
title: "Removing upto a folder from filepath (probably with awk)"
date: 2010-07-03
forum: Multimedia Software
---

### Post by sea_monkey987 on 2010-07-03
> 
Background story (TL;DR)

I know my title is horribly confusing but I couldn't come up with better wording.  I'm trying to batch encode some old mpeg2 vids to x264.  After much playing around, I've finally found some settings that work across the board in preserving quality.  The good news is the converted vids are about half the size.

I'm using handbrake to do this and with over a thousand clips, converting via the gui would be way too time consuming.  Naturally CLI is much faster for something like this.  I've found all the flags and arguments to pass to handbrake

So, suppose my vids are in ~/MyVideos.  I want to store my converted vids in ~/ConvertedVids.  The problem is that there is a whole folder hierarchy after ~/MyVideos that goes several levels deep; I want to preserve this.  In handbrake, the output file is a parameter like so:
```
handbrake_cli -i input_file -o output_file
```
I know stripping away the filepath upto ~/MyVideos/ should be trivial with awk.  I don't know awk and was wondering if someone here could give me the command I need.

---

### Post by DaithiF on 2010-07-03
you probably don't need awk.  something like:
find MyVideos -name '*.avi' | while read pathtoconvert
do
newfile=~/ConvertedVideos/${pathtoconvert#*MyVideos/}
handbrake-i $pathtoconvert -o $newfile
done

---

### Post by sea_monkey987 on 2010-07-03
That worked brilliantly.  Thank you very much!

---

