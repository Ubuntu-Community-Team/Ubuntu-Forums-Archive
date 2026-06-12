---
title: "a video audio conversion script question...."
date: 2011-09-15
forum: Multimedia Software
---

### Post by shantiq on 2011-09-15
ok simply got a bunch of flvs and i want to end up with a single audio file of roughly same kbps as original flvs   not sure how to link stages 1 and 2 confused with   &    or &&   or    ;
Stages 2 AND 3 ok with &&

using sox and ffmpeg ( going through flac as it allows easy and quick splicing with sox )



> for f in *.flv; do ffmpeg -i "$f" "${f%.flv}.flac" [COLOR="Red"]**;**[/COLOR]   (i have put a semi-colon here but not sure how to link the stages)
sox *.flac  final.flac &&
ffmpeg -i final.flac -ab 160k final.mp3 ; done 

---

### Post by dethorpe on 2011-09-15
If i've got this right, you need to do the following.
 
Convert each *.flv into a *.flac using ffmpeg
merge all the *.flac files into a single flac file using sox
convert the single flac file into mp3 using ffmpeg.
 
If thats right then you need this, done on multiple lines to make it clearer:
 
```
 
for f in *.flv
do 
    ffmpeg -i "$f" "${f%.flv}.flac" 
done 
 
sox *.flac final.flac && ffmpeg -i final.flac -ab 160k final.mp3

```
 
The loop converts all the individual flv files, then outside the loop the sox and ffmpeg conmands merge and convert the flac files using the && means the ffmpeg only runs if the sox command works and returns a true value.
 
If i've got your requirements wrong let me know and give some more explanation and I can help further

---

### Post by shantiq on 2011-09-15
hi dethorpe   thanx for reply


> for f in *.flv
do 
    ffmpeg -i "$f" "${f%.flv}.flac" 
done 

[COLOR="Blue"]works up to here then stops  does the flv to flac then does **not** move on to the sox command   sadly and that is the problem i keep having it does the for... bulk convert then stop i can add the rest manually but really want it done in one go at the terminal[/COLOR]
 
sox *.flac final.flac && ffmpeg -i final.flac -ab 160k final.mp3

---

### Post by ron999 on 2011-09-15
"works up to here then stops does the flv to flac then does not move on to the sox command sadly and that is the problem i keep having it does the for... bulk convert then stop i can add the rest manually but really want it done in one go at the terminal"

Hi
Use the "**&& \**" afterwards.

```
for f in *.flv
do 
    ffmpeg -i "$f" "${f%.flv}.flac" 
done && \
sox *.flac final.flac && ffmpeg -i final.flac -ab 160k final.mp3

```
Also, SoX might be very picky if the flv files are not similar.
So this might be needed:-
```
ffmpeg -i "$f" -acodec flac -ar 44100 -ac 2 "${f%.flv}.flac"
```

---

### Post by shantiq on 2011-09-15
hi Ron

```
done && \
```   is a new one on me



the flacs will be ok with sox i think in this instance  ( i have tested those lines in 2 parts and fine    **linking** commands was the problem

i find i often do not know whether to go for   ;    &      &&

but && \ definitely new for me   

so this works and thank you very much   will add it to the panoply:KS


```
for f in *.flv
do 
    ffmpeg -i "$f" "${f%.flv}.flac" 
done && \
sox *.flac final.flac && ffmpeg -i final.flac -ab 160k final.mp3  && rm *.flac
```



a very handy tool if one gets a concert broken down in parts and wants a single audio file thereof

---

### Post by ron999 on 2011-09-15
How about changing that last line.
From this:-
```
sox *.flac final.flac && ffmpeg -i final.flac -ab 160k final.mp3 && rm *.flac
```

Into this:-
```
sox *.flac -C 160 final.mp3 -V3 && rm *.flac
```

---

### Post by shantiq on 2011-09-15
nice:KS   staying with sox

but will require to have sox dealing with mp3   ( not a default )

thankx to Andrew46 for info  starting from Narwhal


```
sudo apt-get install sox libsox-fmt-all

```


 will add the functionality   prior to narwhal [**use**]("http://ubuntuforums.org/showpost.php?p=9859875&postcount=8")



ps    what does -V3 do   ?


**ALTERNATIVE**


```
for f in *.flv
do 
    ffmpeg -i "$f" "${f%.flv}.flac" 
done && \
sox *.flac -C 160 final.mp3 -V3 && rm *.flac
```

---

### Post by ron999 on 2011-09-15
> **shantiq said:**
> 

ps    what does -V3 do   ?

verbose:p

---

### Post by dethorpe on 2011-09-15
\ is the line continuation character, so treats the next line as part of the current one.
 
So could probably do this as well
 
```
 
...
done && sox *.flac -C 160 final.mp3 -V3 && rm *.flac

```
 
Not sure why it dosn't work on seperate lines, are you entering as 1 line at the terminal or in some other program? If so may be easier to save it as a script file then run that. Shouldn't need to get it all linked together with && then.

---

### Post by shantiq on 2011-09-15
--

---

### Post by andrew.46 on 2011-10-02
I use the double ampersand a lot: && as it stops scripts barreling along even if a single and vital command has failed. The gory details are in the bash man pages but suffice to say that in the following example:

```
command1 && command2
```

command2 is only executed if command1 is successful (reports a zero status).

---

