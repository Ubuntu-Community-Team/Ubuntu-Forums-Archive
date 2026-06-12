---
title: "ffmpeg output folder option"
date: 2011-03-05
forum: Multimedia Software
---

### Post by surfmonkee on 2011-03-05
running ffmpeg on my fujitsu laptop for converting content to watch on my psp.

i go to the folder where the content is using terminal and then enter the commands for ffmpeg to process the content and rightly it spits it back in the same folder as the original

is there a command i can add to the command i use now, which will make ffmpeg put the processed video in to another directory?

i dont want to have ffmpeg use the same folder as the original and then move the file with a script, i want ffmpeg to process content straight to a different directory.

here is the commands i use atm, what could i add to this to make ffmpeg spit out the file to say my Videos folder or a dedicated psp folder?

fujistu:/media/data/movies$ ffmpeg -i example.avi -r 29.97 -b 564k -ar 48000 -ab 128k -s 368x208 -f psp example.mp4

---

### Post by ajgreeny on 2011-03-05
You need to specify the full path to the output file in your command, so rather than just **example.mp4** you should use **/home/folder/you/want/example.mp4 	**

---

