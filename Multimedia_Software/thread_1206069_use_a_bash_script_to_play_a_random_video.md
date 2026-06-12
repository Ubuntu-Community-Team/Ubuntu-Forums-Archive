---
title: "use a bash script to play a random video"
date: 2009-07-06
forum: Multimedia Software
---

### Post by richardjennings on 2009-07-06
This is a script I wrote and have been using for some time. 

The first argument is the directory to start searching from, the second is the file extension you wish to play; sans a dot.

eg.
/usr/bin/random.bash /media/disk/Tv/ avi

Thought I would share on the off chance someone else might find this useful.

```

#!/bin/bash


if [ "$1" = "" ]; then
	echo "no directory defined!"
	exit
fi

if [ "$2" = "" ]; then
	echo "no file extension defined!"
	exit
fi


FILE=$(cd ${1}; find * | grep ${2}$ | shuf -n 1) 


PATH="$1$FILE"


/usr/bin/totem "$PATH" 

```

You might see the script should really have more error prevention included, but for my usage that would be superfluous to requirement.

enjoy.

---

### Post by jpeddicord on 2009-07-07
Moved to Multimedia & Video, since this is a script and not so much a tutorial.

---

### Post by Morti on 2012-06-20
Old thread, but I found it while I was looking to a solution this week so thanks.

Scripting isn't really my thing but I've updated the script to suit my purposes better. Maybe it'll help somebody else too.

```
#!/bin/bash

DIRECTORY=$1

if [ "$1" = "" ]; then
	echo "No directory defined! Using the current directory."
	DIRECTORY="./"
fi

EXTENSION=$2

if [ "$2" = "" ]; then
	echo "No file extension defined! Using avi."
	EXTENSION="avi"
fi

FILE=$(cd "$DIRECTORY"; find * | grep ${EXTENSION}$ | shuf -n 1) 

PATH="$DIRECTORY/$FILE"


/usr/bin/totem --fullscreen "$PATH"
```

Defaults to the current directory and .avi if you just run it. I find a nice place to run it from is my videos directory so it'll just play anything from in there without arguments. If I want to play from a subdirectory, I can just tab-complete. Most of my videos have the AVI extension so there's no need for the second variable, although you can put it in if you like.

I also set Totem to fullscreen. :)

---

### Post by lisati on 2012-06-20
Back to sleep, old thread.

---

