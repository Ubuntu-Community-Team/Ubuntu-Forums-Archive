---
title: "Sort pictures into folders by EXIF information?"
date: 2010-01-23
forum: Multimedia Software
---

### Post by SnowPunk98 on 2010-01-23
I have all of my pictures manually sorted into all kinds of folders and sub-folders, very messy to say  the least. Currently I have everything in /home/user/Pictures.

I have started manually sorting everything into dated folders within a year sub-folder, so for example I am doing the following.

- 2009
 -- 01-25-2010
   --- Pictures
-- 01-30-2010
  --- Pictures

I have 15,308 images in 351 folders at the moment. Does anyone have an easy/safe way of running something to run through /home/user/Pictures and move everything into the above structure?

If I can do that, I plan on going through the folders and labeling the ones that have a specific event. For example "12-25-2009 - Christmas" this I know would need to be done manually which is fine.

I am also running Windows 7 and am not opposed to using some Windows application to get this done.

Lastly, I would like to automate the process moving forward. When I plug my SD card in I would like for the pictures to automatically be put into the same location and structure.

---

### Post by kaibob on 2010-01-23
I assume you are looking for a regular application with a GUI. I don't know of one that will do what you want. Hopefully another forum member will be able to help. 

As practice, I wrote the following shell script, which does what you want. To use this script, you need to install exiv2, a small utility that's in the repo's. You also have to change the source and target directories in the script.

This script can be used to transfer photos from an SD card. All you have to do is plug in the card and run the script. It works recursively, so it should get all photos on the card. 

Because of the huge number of files involved, I do not believe you can safely use this script to copy the 15,308 images. I've never written a shell script to handle something that large and the results could be unpredictable. 

```
#!/bin/bash

source="/source/directory"
target="/target/directory"

find "$source" -type f -iname "*.jpg" | while read file ; do
   date=$(exiv2 "$file" 2> /dev/null | awk '/Image timestamp/ { print $4 }')
   [ -z "$date" ] && echo "$file" >> ~/error.txt && continue
   year=${date%%:*}
   month=${date%:*}
   month=${month#*:}
   day=${date##*:}
   mkdir -p "${target}/${year}"
   mkdir -p "${target}/${year}/${month}-${day}-${year}"
   cp "$file" "${target}/${year}/${month}-${day}-${year}"
done
```

---

### Post by SnowPunk98 on 2010-01-24
A script is totally fine with me. YOu don't think this script will work on the number of images I need to sort?

---

### Post by kaibob on 2010-01-24
> **SnowPunk98 said:**
> A script is totally fine with me. YOu don't think this script will work on the number of images I need to sort?

I honestly don't know. I tested the script with nested directories of at most 300 photos, and it worked fine. But, copying 15,308 images may involve operating-system or resource constraints about which I know little. Sorry I couldn't be of more help.

---

### Post by dhughes on 2011-03-24
pyRenamer is pretty good for renaming but I'm not so sure about the sorting into directories and sub-directories part, a bash script may be better for that modify some of kaibob's script maybe.

 I know what you mean when you say 'easy/safe way' I like pyRenamer for renaming especially digital camera pictures that tend to reuse the same filename. 

 Sorting family pictures when I come across to different pictures but both with the same filename e.g. two with 100_1100.JPG but taken at different dates, EXIF data in the picture properties is great for sorting that, as well as looking at the picture obviously but that's not possible with tens of thousands of pictures.

 I use pattern {imagedate}{1} to make 100_100.JPG into 24MAR2011100_1100.JPG so it's unique compared to another 100_1100.JPG taken on a different date.

---

