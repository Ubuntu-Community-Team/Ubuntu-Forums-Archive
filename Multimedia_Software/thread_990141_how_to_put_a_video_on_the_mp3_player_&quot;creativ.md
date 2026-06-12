---
title: "how to put a video on the mp3 player &quot;creative zen mozaic&quot;"
date: 2008-11-22
forum: Multimedia Software
---

### Post by samepate on 2008-11-22
Hello,

I have searched on forums how to put videos on my "creative zen mozaic" from ubuntu...without many results!

So I found the solution myself (after some hours) with the help of  what has been done for other MP3 players. I give my solution here in order to help other users.

First, install mencoder:

```
sudo apt-get install mencoder
```

Then reencode the video using mjpeg codec and specifying the screen resolution is 160x128

```
mencoder name_input.avi -ovc lavc -lavcopts vcodec=mjpeg -oac mp3lame -lameopts cbr:br=64 -vf scale=160:-2,crop=160:128,expand=160:128 -o name_output.avi
```

(replacing "name_input.avi" and "name_output.avi" with the desired names)

Then use gnomad2 to transfer the video on the mp3 player.

Please tell me if you have any question or if this tutorial helped you, I will be happy then!

---

### Post by Vadimir on 2009-10-21
Its very useful for me. Thanks. Can you explain parameters?
-vf scale=160:-2,crop=160:128,expand=160:128
What does mean -2? and expand

---

### Post by samepate on 2009-10-22
Hi,

this is a very good question! I have copied these options without understanding and it worked but I am sure you can use others... The "-2" can be explained like this:

[HTML]
New display width and height.  Can also be these special values:
                          0:   original display width and height
                         -1:   original video width and height (default)
                         -2:   Calculate w/h using the other dimension and the original display aspect ratio.
                         -3:   Calculate w/h using the other dimension and the original video aspect ratio.
[/HTML]

By the way, some videos (1 over 3 or 4 I would say) don't convert well and are unreadable on my MP3 player and I don't know why. Do you have the same problem?

---

### Post by jester42 on 2010-07-06
Many thanks. Now I finally have a ~/bin/vid2zen:
```
#!/bin/bash
if [ -z $1 ]
then
        echo "Usage: $0 <filename>"
        exit
fi
mencoder "$1" -ovc lavc -lavcopts vcodec=mjpeg -oac mp3lame -lameopts cbr:br=64 -vf scale=160:-2,crop=160:128,expand=160:128 -o "$1.zen.avi"

```

Life has a meaning - again :)

---

