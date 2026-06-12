---
title: "sub to srt converter"
date: 2009-12-20
forum: Multimedia Software
---

### Post by A_M_S on 2009-12-20
Hello.

How can i convert a .sub file to .srt?


Tnx.

---

### Post by A_M_S on 2009-12-20
Found it!
Subtitle editor will do the job! :)

---

### Post by gtupkd on 2010-03-12
Where/what is subtitle editor?

---

### Post by benklaasen on 2011-03-03
Here it is: [http://home.gna.org/subtitleeditor/](http://home.gna.org/subtitleeditor/)

...or type "subtitle editor" into the search box in Ubuntu Software Center.

---

### Post by Deshen on 2011-06-25
Hello

I am using Ubuntu 11.04  64bit and neither Subtitle Editor or Gnome Subtitles works, just thought I would add this if anyone else experiences the same problem?[COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C]
[/COLOR][/FONT][/COLOR]

---

### Post by mszef on 2011-11-27
Hello,
I wrote simple app called 'To SRT Converter' which allows such conversion. Requires Mono v2.10+ but does what you need. You can grab it at:
[http://znetcs.pl/ToSrtConverter](http://znetcs.pl/ToSrtConverter)

Cheers

---

### Post by cankara46 on 2012-05-31
Gnome Subtitles does it in a second. Gnome Subtitles is available in Ubuntu Software Center. Install it, You will find it in Sound and Video.  Run the program, open the sub file, click on File and select Save as, then save it in srt form. That's it.

---

### Post by SpeedyGonsales on 2012-06-09
```
sudo apt-get install gaupol
```

It is not subtitle workshop with preview, but it does subtitle conversions without any error.

---

### Post by shantiq on 2012-06-10
> **SpeedyGonsales said:**
> ```
sudo apt-get install gaupol
```

It is not subtitle workshop with preview, but it does subtitle conversions without any error.



sorry speedy but i have tried Gnome Subtitles and Gaupol and Subtitleeditor and none of them accept


.sub    files     are we talking about   those files [ATTACH]219478[/ATTACH] MicroVDV files


which come with an idx file too   and are found on DVD      or are we talking about something different here?



i extracted the .sub and the .idx   from a dvd    with this line of code here


> mencoder dvd://THE_DREAMERS  -nosound -ovc frameno -o nul -sid 1 -vobsubout subtitle-en -vobsuboutindex 0 -vobsuboutid en


and then wished to turn it into a srt file which is currency in Ubuntu    but no luck thus far....


Any chance of clarification here


i enclose both the idx and sub

---

