---
title: "dpgconv troubles"
date: 2009-09-11
forum: Multimedia Software
---

### Post by Squigy Dunkens on 2009-09-11
Hi, I've been trying to get videos on my DS, so I looked around for a way to convert my videos to DPG format, and found [dpgconv]("http://theli.is-a-geek.org/blog/static/dpgconv"). I downloaded [dpgconv 8]("http://theli.is-a-geek.org/files/dpgconv/dpgconv-8.py.gz"), and [mpeg_stat-linux]("http://bmrc.berkeley.edu/ftp/pub/multimedia/mpeg/stat/"). I placed mpeg_stat, and mpeg_stat.1 in /usr/bin. Then, after making it an executable, I placed dpgconv-8.py in /home/squigydunkens/DPG, and placed my video in the same place. in the terminal, I switched to the /home/squigydunkens/DPG directory, and ran ```
python dpgconv-8.py habaneroshowdown.mp4
```, and it spit this at me:```
Error:
/usr/bin/mpeg_stat: 1: 
                       d&#65533;0&#65533;&#65533;&#65533;G&#65533;-&#65533;&#832;&#65533;X&#65533;D&#65533;&#65533;&#65533;P&#65533;&#65533;^&#65533;&#65533;&#65533;4]P&#65533;&#65533;V[&#65533;&#832;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;: not found
/usr/bin/mpeg_stat: 2: Unexpected: not found
/usr/bin/mpeg_stat: 3: Improper: not found
/usr/bin/mpeg_stat: 4: File: not found
/usr/bin/mpeg_stat: 5: Syntax error: ")" unexpected

``` Anyone know how I could fix this?

---

### Post by purgatori on 2009-09-11
Perhaps try a version prior to 0.4, and see if it still errors out?

---

### Post by Squigy Dunkens on 2009-09-12
```
squigydunkens@Yooten:~/DPG$ python dpgconv-0.3.py habaneroshowdown.mp4
Converting habaneroshowdown.mp4
Transcoding video:   done
Traceback (most recent call last):
  File "dpgconv-0.3.py", line 220, in <module>
    conv_file(file)
  File "dpgconv-0.3.py", line 182, in conv_file
    frames = conv_vid (file)
  File "dpgconv-0.3.py", line 116, in conv_vid
    origframes = int(m.group(1))
ValueError: invalid literal for int() with base 10: ''

```

---

### Post by Squigy Dunkens on 2009-09-16
since no one seems to have an answer, does anyone know of anything else i could use to convert videos to dpg format?

---

### Post by ubunny on 2009-11-29
--

---

### Post by ubunny on 2009-11-29
works fine, just make sure your file does not include spaces, I do that and mp4 conversion works.

---

