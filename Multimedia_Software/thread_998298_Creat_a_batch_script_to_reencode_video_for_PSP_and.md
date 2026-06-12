---
title: "Creat a batch script to reencode video for PSP and rename the files"
date: 2008-11-30
forum: Multimedia Software
---

### Post by Drezliok on 2008-11-30
I have never done any scripting ever. But I want to reencode some old movies to play on my PSP and to name them accordingly.

So I can rename all the files and have PSP in the name so I know it's for my PSP.

I have been using Avidemux GUI to do it until now but I have to go one by one. I want to do all of them in one night while I sleep.

Anyone have any idea on how this can be done? Links to howtos would be cool too.

I want to learn this stuff.
Thankyou for your time,
Drezliok

---

### Post by Drezliok on 2008-11-30
If this thread is in the wrong section could I get a mod to move it?

Yes I am doing a small bump.

---

### Post by Drezliok on 2008-12-02
I have never needed to bump my threads up 2 times.

Any and all help is appreciated.

---

### Post by cyfur01 on 2008-12-02
I found [this.]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-handheld-psp.html") sounds like what you want.

However, in order to get this to work, I had to switch the acodec=aac option to acodec=libfaac, which if I'm not mistaken, requires "libfaac0" (sudo apt-get install mencoder libfaac0).

In the end, the command looks like this:
```

mencoder -ofps 30000/1001 -af lavcresample=24000 -vf harddup -of lavf \
    -oac lavc -ovc lavc -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:acodec=libfaac \
    -lavfopts format=psp \
    input.video -o output.psp

```

To make a script to automate this for multiple files:
```

#!/bin/bash

# In case user forgets to input file names
if [ $# -eq 0 ]
        echo "USAGE: avi2psp <FILE(S)>";
        exit 1;
fi

# For each input file
for FILE in "$@"
do
        mencoder -ofps 30000/1001 -af lavcresample=24000 -vf harddup -of lavf \
        -oac lavc -ovc lavc -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:acodec=libfaac \
        -lavfopts format=psp $FILE -o ${FILE%.[^.]*}.psp
done

```

If you're new to shell scripting, the backslashes ("\") allow a command to run over more than one line, "$@" creates a strings of all the input arguments, which in this case will be the input files that the for loop cycles through, and the whole "${FILE%.[^.]*}" expression removes the extension from the file currently being processed so it can be replaced with ".psp" (I can't guarantee it will work perfectly in every case).

Also, don't forget to give the script executable permissions:```

chmod +x avi2psp

```
Then you can run it:```

./avi2psp video1 video2 etc

```

---

