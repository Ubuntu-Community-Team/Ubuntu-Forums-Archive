---
title: "Trust WB-3320X Webcam help"
date: 2009-10-03
forum: Multimedia Software
---

### Post by daithi81 on 2009-10-03
Hello, I am using Ubuntu 9.04 and this webcam. It appears to work fine out of the box when using Ekgia, however I bought it for use on Skype. When I go to test it on Skype I just get an image of green and purple lines, and the mic output is just static. I searched the web for answers, but haven's stumbled across an answer yet.

Any ideas?


(Move if in wrong forum please)

---

### Post by daithi81 on 2009-10-03
No suggestions?

---

### Post by daithi81 on 2009-10-04
Ok, partial solution to this problem. Simply type the following in terminal:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

and the green lines will be removed. However, running it from applications>internet>skype still leads to the same problem, so the above command must be always used.

---

### Post by daithi81 on 2009-10-06
Ok, this solution above resolved the video problem, but I get no audio from the webcam.

Any ideas?

---

### Post by daithi81 on 2009-10-07
[SIZE="7"]Hello[/SIZE] [SIZE="6"]hello[/SIZE] [SIZE="5"]hello[/SIZE] [SIZE="4"]hello[/SIZE] [SIZE="3"]hello[/SIZE] [SIZE="2"]hello[/SIZE] [SIZE="1"]hello...[/SIZE]

---

### Post by Urras on 2009-12-04
Hiiiiiiiiii 

 sorry I'm here because I have the same problem with 9.10... My trust WB-3320X don't work with aMSN and Skype...Help

---

### Post by Marco_A on 2010-01-08
> **Urras said:**
> Hiiiiiiiiii 

 sorry I'm here because I have the same problem with 9.10... My trust WB-3320X don't work with aMSN and Skype...Help

Hi,
I had the same problem with the same cam on Ubuntu 9.10 x86_64.
I solved this way:

1. the system pointed to 64bit libraries, so I have to launch skype using this command:
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

2. edit the file /home/<USERNAME>/.Skype/<YourSkypeUserID>/config.xml:
```
gedit /home/<USERNAME>/.Skype/<YourSkypeUserID>/config.xml
```Scroll the file to find the <Video> section.

Add the following 2 lines between <Video> and </Video> tags:
```

  <CaptureHeight>480</CaptureHeight> 
  <CaptureWidth>640</CaptureWidth> 

```

3. Save, close and restart Skype.

Hope it helps,

MarcoA

---

### Post by miroi on 2011-10-08
[QUOTE=daithi81;8052477]Ok, partial solution to this problem. Simply type the following in terminal:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```and the green lines will be removed. 

------------

Excellent ! This solutions helped me for Ubuntu 11.04.

Concerning implementing LD_PRELOAD into Skype launcher, I made:

sudo mv /usr/bin/skype /usr/bin/skype_orig

and I created own launcher:

sudo vi /usr/bin/skype

containing

#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype_orig


sudo chmod ugo+rx /usr/bin/skype


Best, Miro

---

