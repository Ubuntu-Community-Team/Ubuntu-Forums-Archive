---
title: "Handbrake and  Bash while looping help and quiting scripts"
date: 2011-08-31
forum: Multimedia Software
---

### Post by juliushibert63 on 2011-08-31
I've written a bash script cobbled from bits and pieces online to loop through all files in a dir and run them through HandBrake to convert them to iPhone ready videos. 

Currently the script just processes .mkv files but I'd like to try and get it to process .avi files but can seem to find a simple way to do so. 

Is there a simple bit of code to basically do the following. 

```
While files (*.mkv OR *.avi) in dir 
Do ..... Loop

```

Also when ever I quit the script by killing it in terminal via Ctrl+C it only quits the currently running command and not the whole script. Ie if it's running the part where its processing video using HandBrake and I press Ctrl+C then just HandBrake quits and the rest of the script continues. 

Here's the script in it's entirety:

```
#!/bin/bash

# Date Created 30/08/2011
# Date Modified: 30/08/2011

# Script runs through all the mkv and avi files the encoding directory
# changing them into iPhone ready m4v files.

# Setup variables of encoding folders


sourcedir="$HOME/HandBrake-Encoding/Queue"
destdir="$HOME/HandBrake-Encoding/Complete/iPhone"

cd "$sourcedir"

echo "########### Changed to dir $sourcedir"
for i in *.mkv; do

	echo "########?File to encode is $i"
  	HandBrakeCLI -i "$i" -o "$destdir/${i%.*}.m4v" --preset="iPhone & iPod Touch" 
  	
  	echo "#######removing file $i"
  	#rm -rf "$i"
done
exit 0
```

---

### Post by handy on 2011-08-31
Oops. Misunderstood.

---

