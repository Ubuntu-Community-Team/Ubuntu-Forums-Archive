---
title: "Unknown file extension, need to rename multiple"
date: 2009-03-18
forum: Multimedia Software
---

### Post by jesterthejedi on 2009-03-18
Okay so I save the video files from my cache from firefox when I go to youtube. This lets me view them later or offline. The problem is that it can end up being a lot of videos and they all are named C592149Cd01 or similar. With no file extension this makes using a rename command impossible. Ideally I want to batch add file extension, and or rename the file too. Any ideas how this can be done in terminal or a script.

---

### Post by lovinglinux on 2009-03-18
Use pyRenamer gui.

```
sudo apt-get install pyrenamer
```

In the "Patterns" tab you can use these settings for example:

Original file name pattern: **{X}**
Renamed file name pattern: **video_{num3}.flv**

This will rename all files to **video_** followed by 3 digit sequential numbers and by the flv extension like this:

[B]video_000.flv
video_001.flv
video_002.flv[/B]

Use** {num4}** for 4 digits and so on.

---

### Post by kaibob on 2009-03-18
> **jesterthejedi said:**
> ...Ideally I want to batch add file extension, and or rename the file too. Any ideas how this can be done in terminal or a script.

The method suggested by lovinglinux is probably best. But, the following shell script will also do what you want:

```
#!/bin/bash

cd /target/directory

count=001

for file in * ; do
   cp "$file" "video_${count}.flv"
   count=$(printf "%03d" $((count+1)))
done
```

As a precaution, I used copy (cp) rather than move (mv). You need to change the /target/directory.

Have a look at the following thread for other command-line alternatives: 

[http://ubuntuforums.org/showthread.php?t=1098902](http://ubuntuforums.org/showthread.php?t=1098902)

---

