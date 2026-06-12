---
title: "FFMPEG .flv to .mp3 batch convert"
date: 2010-03-15
forum: Multimedia Software
---

### Post by Robert Lutken on 2010-03-15
Hi there i have a file with about 6 .flv files and i wish to batch convert them to libmp3lame  i have tried making a 
#!bin/bash script with all the files in e.g.
```
ffmpeg -i filename.flv -sameq -acodec libmp3lame -f asf filename.mp3
```
i have inserted all the filenames indivdually into the script but when i ran it i got too many errors and i was wondering if someone knew a quicker way to do it e.g. a script that would batch convert all .flv files in that folder to .mp3 format 
thanks all 
Welshy_Rob

---

### Post by andrew.46 on 2010-03-15
Hi Robert,

An easy way to do this is with a for loop:

```

for f in *.flv
      do 
      ffmpeg -i "$f" -acodec libmp3lame -ab 128k "${f%.flv}.mp3"
done

```

Thanks again to mc4man for showing me this technique a while back :).

Andrew

---

### Post by Robert Lutken on 2010-03-15
Hi, andrew.46 

just a few questions.
!) do i put my file name "flv's" into ```
 *.flv 
``` into where the * is? 
2) do i need to make this a script e.g. chmod? 

Thanks again =)

---

### Post by andrew.46 on 2010-03-15
Hi Robert,

> **Robert Lutken said:**
> just a few questions.
!) do i put my file name "flv's" into ```
 *.flv 
``` into where the * is? 

No you don't, the '*' is a wildcard character so it will match file.flv, another_file.flv etc etc with no intervention required from you.

> 2) do i need to make this a script e.g. chmod? 

You *could* incorporate this into a script but the easiest way is to simply navigate to the directory containing all of your flv files and paste the whole *for* loop into the terminal window.

BTW it may be well worth your time and trouble to beef up your copy of FFmpeg a little by having a quick read of this guide:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

All the best,

Andrew

---

### Post by Robert Lutken on 2010-03-16
Hi again 
Thanks for your help i will try it when i get back tonight
so just to clarify i cd into my directory with all the flv files in and then paste
```

for f in *.flv
      do 
      ffmpeg -i "$f" -acodec libmp3lame -ab 128k "${f%.flv}.mp3"
done

```
into terminal correct, i dont need to modifigy that code at all ?
that correct?
and thanks for that link iv'e seen that before :D 
thanks again 
Rob

---

### Post by andrew.46 on 2010-03-16
Hi Robert Lutken,

Exactly :). You certainly can modify the FFmpeg line if you wish to alter the bitrate or make other changes but the syntax I have given should furnish a start at the very least.

Andrew

---

### Post by Robert Lutken on 2010-03-16
andrew.46,

Thanks it works a charm :D cheers 
Rob

---

### Post by andrew.46 on 2010-03-16
Hi Robert,

That is great news :). If you keep this little loop stored away you will find many more variations and uses for it, pun intended :).

All the best,

Andrew

---

### Post by OxentroT on 2010-06-21
> originally posted by andrew.46
Hi Robert,

An easy way to do this is with a for loop:

Code:

```
for f in *.flv
      do 
      ffmpeg -i "$f" -acodec libmp3lame -ab 128k "${f%.flv}.mp3"
done
```

Thanks again to mc4man for showing me this technique a while back .

Andrew 

(((OUTSTANDING!)))

And combined with navigating with terminal to my destination folder?
Worked like a charm right off bat! This is amazing! 
So many rare tracks out there in .flv format.
The quest continues


Thanks Guys!

:guitar:

---

### Post by bigdee973 on 2011-10-16
im just wondering why are you putting f in 'for f in *.flv' and what the "${f%}.flv" is doing

---

### Post by andrew.46 on 2011-10-17
> **bigdee973 said:**
> im just wondering why are you putting f in 'for f in *.flv' and what the "${f%}.flv" is doing

The 'f' in this for loop is designed to be one or multiple input files, can be any letter you wish as long as use is consistent throughout the loop. The other syntax is a simple pruning method. Try the following to see how it works:

```

andrew@skamandros~$ f=filename.ext
andrew@skamandros~$ echo $f
filename.ext [COLOR="Red"]<------- The full variable.[/COLOR]
andrew@skamandros~$ echo "${f%.ext}"
filename [COLOR="Red"] <--- Note the .ext has been removed.[/COLOR]
andrew@skamandros~$ 

```

It is a simple method of removing the final few letters to make the final filename in the for loop *filename.mp3* rather than *filename.flv.mp3*. If you hunt this out in the bash man pages you will see the details under 'Remove matching suffix pattern'. Hope this makes it a little clearer?

---

### Post by nothingspecial on 2011-10-17
> **bigdee973 said:**
> im just wondering why are you putting f in 'for f in *.flv' and what the "${f%}.flv" is doing

Hi read the section about parameter expansion in this wiki

[http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)

---

### Post by bigdee973 on 2011-10-17
thanks i see that it is indeed pruning the code. thank you i learned something new. but could u please help me out with these questions... i need to know this so i could better understand whats going on in the code.

1.what is the "$f" in ffmpeg -i doing? Im guessing it is telling the computer use the same name from the .flv files in the mp3s? (i use ffmpeg alot but i still dont know how to take the name from source and apply to new file without having to type it manually so im guessing this is how u would do that)

2. i dont see you declaring f into anything. Is the command 'for f in *.flv' declaring/saying f=every .flv file(*.flv)

sorry for being so ignorant/annoying but i really want to know so i could know whats going on instead of using the code mindlessly.

---

### Post by nothingspecial on 2011-10-17
"$f" is a variable containing the output of *.flv which is indeed every file ending in .flv

The variable can be (almost) anything eg
```

for banana in *.flv; do echo "$banana"; done
```

Go back to that link I gave you and read the sections on variables then go to the next section which talks about Patterns. It is all explained there.

---

### Post by bigdee973 on 2011-10-17
> **nothingspecial said:**
> Hi read the section about parameter expansion in this wiki

[http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)

thank you,that was very helpful information.  i learned something very interesting with parameters expansion and patterns.  That link made it much clearer thank you so very much for sharing your knowledge with me :)

---

