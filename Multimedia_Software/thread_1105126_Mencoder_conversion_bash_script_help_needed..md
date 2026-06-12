---
title: "Mencoder conversion bash script help needed."
date: 2009-03-24
forum: Multimedia Software
---

### Post by LaLLi on 2009-03-24
Hi,

I have a Rockchip MP4 video player. After long search I found a working mencoder command to make videos my player accepts. I usually convert a bunch of videos but atm I need to do it one at a time.

Can someone help me with creating a working script to convert all videos with one command?

I have a folder where I copy my files to be converted. ATM my mencoder command makes the coversion and saves the finished video to a nother folder.

Here's the mencoder script:
```
#!/bin/bash
mencoder -noodml $1 -of avi -o valmiit/$1 -ofps 15 -vf-add scale=320:240 -srate 44100 -ovc xvid -xvidencopts bitrate=500:max_bframes=0:quant_type=h263 -oac lavc -lavcopts acodec=mp2:abitrate=96
```

All the files will be .avi

thanks for any suggestions.

---

### Post by Bachstelze on 2009-03-24
A simple [font="monospace"]for[/font] loop will do:

```
#!/bin/sh

for i in *.avi; do
    mencoder -noodml $i -of avi -o valmiit/$i -ofps 15 \
      -vf-add scale=320:240 -srate 44100 -ovc xvid \
      -xvidencopts bitrate=500:max_bframes=0:quant_type=h263 \
      -oac lavc -lavcopts acodec=mp2:abitrate=96
done
```

---

### Post by LaLLi on 2009-03-24
Thank you, works very well.
I tried a for loop but failed..can't remember why.

---

### Post by mysoogal on 2009-05-24
```
root@ubuntu:~/Videos# sudo bash encode
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
root@ubuntu:~/Videos# 

```


changed .avi to mpeg

and run it using sudo bash encode

script not running

---

### Post by xzero1 on 2009-05-24
> and run it using sudo bash encode

script not running     If I understand what your are trying to do -- sudo should not be needed, bash scripts have a ".sh" extension, must be executable and may be run as "sciptname.sh".

---

### Post by mysoogal on 2009-05-25
oh crap, maybe this is why its not completing the whole script

i named the bash script just h264 with the sh :O

could this be a problem why its not picking up jpgs

---

