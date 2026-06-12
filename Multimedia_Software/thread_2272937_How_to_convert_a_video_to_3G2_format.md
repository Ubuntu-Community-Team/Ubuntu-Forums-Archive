---
title: "How to convert a video to 3G2 format?"
date: 2015-04-09
forum: Multimedia Software
---

### Post by remmas-sido on 2015-04-09
Hello guys 
Is there a command line way, or GUI software that's able to convert a video to 3G2 format in order to be compatible with mobile phones?

---

### Post by Vladlenin5000 on 2015-04-09
Avidemux should do it, provided all the needed codecs are installed.
But which phones still need it? All smartphones can handle most if not all common video formats nowadays...

---

### Post by remmas-sido on 2015-04-09
> **Vladlenin5000 said:**
> Avidemux should do it, provided all the needed codecs are installed.
But which phones still need it? All smartphones can handle most if not all common video formats nowadays...
For example Nokia-C family, I know that now days there are smartphones that can do anything for you, but for me I like to stay basic. My primary goal is to listen to music that's all.

---

### Post by mc4man on 2015-04-09
winff > Convert to "Mobile Phones", pick appropriate preset for target device. one preset example in screen

---

### Post by andrew.46 on 2015-04-09
I dug the following out of my archive of conversions:

```

ffmpeg -i <input> \
           -s qcif -c:v h263 \
          -c:a libopencore_amrnb \
          -ac 1 -ar 8000 -r 25 -ab 12200 \
          output.3gp

```

and I have not retested it, doubtless it needs some alteration, especially the resizing! Perhaps this will be a start for you at least?

---

### Post by ahmetdemir2 on 2015-04-11
thanks the code

---

### Post by remmas-sido on 2015-04-12
> **mc4man said:**
> winff > Convert to "Mobile Phones", pick appropriate preset for target device. one preset example in screen
I could not find the preset that you showed in your picture. Is there some kind of configuration? what version of WinFF are you using? mine is 1.4.1

---

### Post by mc4man on 2015-04-13
> **remmas-sido said:**
> I could not find the preset that you showed in your picture. Is there some kind of configuration? what version of WinFF are you using? mine is 1.4.1
I guess it's not in 12.04's winff default presets.
You could try adding it & see if the parameters work - to do

install libfaac0 if not already installed
Then open ~/.winff/presets.xml in a **text editor**
Scroll down to bottom, replace the last line </presets> with this

```
  <cdma3g>
    <label>CDMA Phone Audio (3g2)</label>
    <params>-f 3g2 -ar 22050 -ab 128k -acodec libfaac -vf scale=176:144 -r 14.985 -vn</params>
    <extension>3g2</extension>
    <category>Mobile Phones</category>
  </cdma3g>
</presets>
```

In other words you are adding a new section & *then ending the file as before with a </presets> line that starts from the far left, no indent.* If this forum code box doesn't keep formatting then adjust after the copy & paste to match what's used in that file, ie.  the </cdma3g> lines are indented 2 spaces , the rest 4

---

### Post by remmas-sido on 2015-04-13
> **mc4man said:**
> I guess it's not in 12.04's winff default presets.
You could try adding it & see if the parameters work - to do

install libfaac0 if not already installed
Then open ~/.winff/presets.xml in a **text editor**
Scroll down to bottom, replace the last line </presets> with this

```
  <cdma3g>
    <label>CDMA Phone Audio (3g2)</label>
    <params>-f 3g2 -ar 22050 -ab 128k -acodec libfaac -vf scale=176:144 -r 14.985 -vn</params>
    <extension>3g2</extension>
    <category>Mobile Phones</category>
  </cdma3g>
</presets>
```

In other words you are adding a new section & *then ending the file as before with a </presets> line that starts from the far left, no indent.* If this forum code box doesn't keep formatting then adjust after the copy & paste to match what's used in that file, ie.  the </cdma3g> lines are indented 2 spaces , the rest 4
Where I can find ~/.winff/presets.xml

---

### Post by mc4man on 2015-04-13
> **remmas-sido said:**
> Where I can find ~/.winff/presets.xml

Home Folder > ctrl+h to show hidden files > .winff
or 

```
gedit  ~/.winff/presets.xml
```

or

```
nautilus ~/.winff/
```

---

