---
title: "unable to download MP3 file"
date: 2011-05-05
forum: Multimedia Software
---

### Post by alwaysonnet on 2011-05-05
[FONT=Lucida Console]I've been trying to download an MP3 file from a download link, but  I've been encountering a problem. The thing is whenever I click on the  "Download" button it always starts opens and plays the songs instead of downloading the  file.

I'm running on Ubuntu 10.10.

Please help me out.[/FONT]

---

### Post by Ibidem on 2011-05-05
What browser? if it's firefox, go Edit>Preferences and click the Applications tab; find the right line, click, and select something else.

---

### Post by alwaysonnet on 2011-05-05
[FONT=Georgia]I'm using firefox. I went to Edit->Preferences->Applications Tab, but didn't find MP3 in the list.

any alternatives?[/FONT]

---

### Post by K_45 on 2011-05-05
Right-click the link, choose save link as . . .

---

### Post by alwaysonnet on 2011-05-05
Nope, its not working. :(

---

### Post by andrew.46 on 2011-05-07
Perhaps right click on the link, select 'Copy link location' and then use wget to transfer the file. Syntax would be simply:

```
wget *[COLOR="Red"]link_location[/COLOR]*
```

If this simple strategy does not work can you give the address of the page or mp3 file that you are trying to download?

---

### Post by alwaysonnet on 2011-05-09
@K_45,

Your suggestion has worked. Infact I was trying the same thing, but the song which I'm trying to download has a long name, could not able to figure out the extension. Now that I've tried and is working fine.

---

