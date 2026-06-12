---
title: "HOW-TO: Download and encode flash videos (Youtube, etc) with ffmpeg script"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by PinkFloyd102489 on 2008-01-28
I made this script up because all of the other ones, like pytube, werent working for me. I think that Youtube stopped the direct download of their URLs or something, so I wrote this one.


```
#!/bin/bash

zenity --warning --title "Attention" --text "Please load the video in your browser and then hit Ok."

#Naming the file
NAME=$(zenity --entry --title "Enter file name" --text "Enter what you wish to name the file, followed by the 
extension. EX: mymovie.mpg")

#Moving and encoding

sleep 3

cd /tmp --message

gksu mv Flash* ~ --message "Please give root permissions before continuing."

cd ~

ffmpeg -i Flash* $NAME | zenity --progress --pulsate --title "Encoding..." --text "Encoding file..." --auto-close --auto-kill

sleep 3

mv $NAME ~/Desktop

rm Flash*

cd ~/Desktop

chown $USER:$USER $NAME

zenity --info --title "Finished" --text "Done encoding $NAME. File has been moved to Desktop"

```


If you want to encode to something other than mpg, just specify it in the file name. I'll probably try and update the script to where you can choose from a list in the Zenity box that pops up.

If you take a look at the script, it doesnt grab from a URL. It prompts you to load the video in your browser first, then grabs the file from /tmp and encodes it.

---

