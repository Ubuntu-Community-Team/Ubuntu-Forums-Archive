---
title: "how can i merge  two files with ffmpeg?"
date: 2010-03-31
forum: Multimedia Software
---

### Post by luofeiyu on 2010-03-31
how can i merge  two files with ffmpeg?
one is : /home/pt/t/pa1.flv
the other is :  /home/pt/t/pa2.flv

1\to merge with ffmpeg
ffmpeg  -i  /home/pt/t/pa1.flv  -i  /home/pt/t/pa2.flv  -vcodec copy -acodec copy   /home/pt/t/dd.flv
the problem is: the merged file ( /home/pt/t/dd.flv ) just contain one file--the first one
/home/pt/t/pa1.flv,there is no the second file--/home/pt/t/pa2.flv  in the /home/pt/t/dd.flv
what's wrong?it's a bug of ffmpeg??

2\to merge with cat command
cat /home/pt/t/pa1.flv   /home/pt/t/pa2.flv  >>   /home/pt/t/dd.flv
the problen is the same as :to merge with ffmpeg
no second file in the  /home/pt/t/dd.flv
what's wrong?

---

### Post by FakeOutdoorsman on 2010-04-01
Can you provide some information on the inputs?  Try this:
```
ffmpeg -i pa1.flv -i pa2.flv
```
The method to combine the videos will depend on the type of video inside the FLV container.

---

### Post by moetunes on 2010-04-01
The docs for ffmpeg kinda hint that you can merge avis but I can never get it to work. I use avidemux2 for that - it has an option in file-append to join two video files. The only solution I've found so far.

---

### Post by iLag!!!!! on 2010-04-01
```
cat pa1.flv pa2.flv | ffmpeg -i - -vcodec copy -acodec copy -f flv paCombined.flv
```
This works for me, but I haven't tested it with flv files yet.

---

### Post by mole84 on 2010-04-01
The best way I have been able to do this with ffmpeg is bite the bullet and convert to mpg and then merge them. 

```

#convert all to mpg
for k in 1 2 3 4
do        
       ffmpeg -i ${k}.wmv -sameq ${k}.mpg    
done
    
#combine mpg files
cat *.mpg |\ffmpeg -i - -sameq $destdir${i}.mpg

```

---

