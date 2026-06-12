---
title: "Handbrake Script"
date: 2010-05-03
forum: Multimedia Software
---

### Post by darthrax on 2010-05-03
Hi All,

Scripting after some time now... I've recently started watching videos on my iPhone and have come to the realization that theres no really easy way (I mean mostly automatic) of ripping files. I tried Artista Transcoder and Handbrake. They're both good programs but I've got more experience with handbrake so i wrote a little right-click script for nautilus which rips videos into whatever format you want based on the presets. 

to install handbrake from the ppa: (only works for 9.10 & 10.04 check the ppa for a how to on installing in earlier versions)
```
sudo add-apt-repository ppa:handbrake-ubuntu/ppa && sudo apt-get update && sudo apt-get install handbrake-cli
```


Copy the following code into a file and place it into ~/.gnome2/nautilus-scripts folder

```
#!/bin/bash
# Right-click video ripper for HandBrakeCLI
# Owner: 
#   Anand Kapre
#   ak@anandkapre.com
# Licence: GNU GPL
# Copyright (C) Anand Kapre
# Dependency:
#   HandBrakeCLI
# Created on Tuesday May 4th 2010
# Tested on Ubuntu 9.04 Jaunty Jackalope, 10.04 Lucid Lynx

# Uncomment the preset of your choice below
#ripto="Universal"
#ripto="iPod"
#ripto="AppleTV"
#ripto="Normal"
#ripto="High Profile"
#ripto="Classic"
#ripto="AppleTV Legacy"
#ripto="iPhone Legacy"
#ripto="iPod Legacy"
ripto="iPhone & iPod Touch"

folder=$(pwd)
for arg in "$@"
do
pid=$(pidof HandBrakeCLI)
if [ $pid -gt 0 ] ;
then
  sleep 5
else
gnome-terminal --geometry=75x10 -x HandBrakeCLI --preset "$ripto" -i $folder/"$arg" -o $folder/"$arg".mp4 && sleep 5
fi
done
```

hope this helps someone...enjoy

---

### Post by K.Mandla on 2010-05-04
Moved to Multimedia and Video. :)

---

### Post by jmoorse on 2010-05-18
FYI this doesn't work if there are spaces in the path.

editing: $folder/"$arg" to "$folder"/"$arg" did the trick

---

### Post by Paresh on 2010-05-18
If you have zenity installed, you can try

```
ripto=$(zenity  --list  --text "Choose the format to rip to .." --radiolist  --column "Pick" --column "Opinion" TRUE Universal FALSE iPod FALSE AppleTV FALSE Normal FALSE "High Profile" FALSE "Classic" FALSE "AppleTV Legacy" FALSE "iPhone Legacy" FALSE "iPod Legacy" FALSE "iPhone & iPod Touch");
```

to give you a nice selection dialog.

If you want zenity, it's in the repository ```
sudo apt-get install zenity
```

---

### Post by iceman2k3 on 2010-09-16
Hi thanks a lot for the script!

little hack for subtitile :

```

# subtitle
file_name=$arg
file_title=`echo $file_name|sed 's/\..\{3\}$//'`

if [ -e ${file_title}.srt ]
then
gnome-terminal --geometry=75x10 -x HandBrakeCLI --preset "$ripto" -i $folder/"$arg" -o $folder/"$file_title".mp4 -srt-file ${file_title}.srt --srt-lang fra && sleep 5
else
gnome-terminal --geometry=75x10 -x HandBrakeCLI --preset "$ripto" -i $folder/"$arg" -o $folder/"$file_title".mp4 && sleep 5
fi


```I've add $file_title var to strip out .avi at the end of the ouput (movie.mp4 instead of movie.avi.mp4)

---

### Post by mastermindg on 2012-02-01
How can this be modified to allow for batch processing? I've got a folder of videos that I'd like converted.

---

