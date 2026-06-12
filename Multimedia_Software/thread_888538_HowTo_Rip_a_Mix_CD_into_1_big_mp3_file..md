---
title: "HowTo: Rip a Mix CD into 1 big mp3 file."
date: 2008-08-13
forum: Multimedia Software
---

### Post by jay019 on 2008-08-13
So, I wanted to rip a mix CD in SoundJuicer and Grip but not as a bunch of seperate tracks, but as one mp3. Using those apps does not give me the option to do what I want so I had to work out how to do it myself. This is what I did.

Firstly some things you will need...
cdparanoia & lame

To rip the cd as 1 track: in a terminal type...
```

cdparanoia 1- filename.wav

```

Then to encode to mp3: in a terminal type... (replacing all fields as necessary)
```

lame -b 160 -h --tt "Title of Mix" --ta "Mix Artist" --tl "Album Name" --ty "YEAR" --tg "Genre" filename.wav filename.mp3

```
the "-b 160" means a bitrate of 160kbps change this as needed. "-h" is for high quality, takes longer but is worth it. To see what else you can do with lame just type "man lame" in a terminal.

And there you have it, ripping a mix CD as one mp3.


Further to this I also created a shell script to make things a bit easier, for this to work you need to have zenity installed...

```

#!/bin/bash

CDP=$(which cdparanoia);
ENC=$(which lame);
ZEN=$(which zenity);

TA=$($ZEN --entry --title="Artist" --text="Enter the Artist name:");
TT=$($ZEN --entry --title="Title" --text="Enter the Title:");
TL=$($ZEN --entry --title="Album" --text="Enter the Album name:");
TY=$($ZEN --entry --title="Year" --text="Enter the Year:");
TG=$($ZEN --entry --title="Genre" --text="Enter the Genre:");
BR=$($ZEN --entry --title="Bitrate" --text="What bitrate:");

FN=$(echo "$TA" | sed 's/ /_/g')-$(echo "$TT" | sed 's/ /_/g');

`$CDP 1- $FN.wav`
`lame -b $BR -h --tt "$TT" --ta "$TA" --tl "$TL" --ty "$TY" --tg "$TG" $FN.wav $FN.mp3`
rm $FN.wav

echo "Done!!!";

```

PS. This script is very basic and does no error checking. If you make a mistake then you will need to Ctrl+C to exit. If there is enough interest I may update the script to do some basic error checking.

Hope this helps.  

Your fellow (Drum & Bass) mix CD fan.

Jay

---

