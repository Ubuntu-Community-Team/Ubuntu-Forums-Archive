---
title: "Webcam works when launching skype via terminal only?"
date: 2010-10-01
forum: Multimedia Software
---

### Post by Alexand3rS on 2010-10-01
Hi, I'm fairly familiar with computers, but I'm also fairly new to Linux and Ubuntu.

So, I'm trying to set up Skype on my Ubuntu, but I'm having some trouble with the webcam. After following instructions here: [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) , I managed to get my Logitech webcam working in "Cheese Webcam Booth". However, it would not show in Skype's test box when I tried. That website also told me to put a line in its Command field in the Launcher Properties box:
 
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype' 

After I tried that, it still wouldn't show up. The website recommended that I put the same line into the console and see if it would throw an error at me. It didn't. Skype started up and I could now see my webcam feed in the test box. However, the strangest thing to me is that when I closed the terminal, and started Skype normally, it wouldn't work again.

So it seems that the webcam feed only works when I start Skype via the Terminal with the above line.

Anyone want to help? I'm totally fine with starting Skype that way every time but my mum is going to be using this computer to chat with relatives and it would be too much trouble for her to fiddle with the console. Can anyone tell me how to fix the problem or can someone help me create some sort of icon that will execute that command when I click it?

Thanks very much!

---

### Post by Alexand3rS on 2010-10-02
Sorry, but....... *bump*

---

### Post by Alexand3rS on 2010-10-04
anyone? ... :(

---

### Post by Israphel on 2010-10-04
I bought a webcam today and I had this problem too (not the only one).

Just create a blank file (with Gedit or whatever) and write:

```

#!/bin/bash
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

```


Save it somewhere as "skype.sh" and give it execution permission:

```

sudo chmod +x skype.sh

```


Now create a link to that file in your menu.

Put the sh file in a hidden place, if you want.

---

### Post by Alexand3rS on 2010-10-20
Hey thanks! Solved my problem!! :grin:

---

