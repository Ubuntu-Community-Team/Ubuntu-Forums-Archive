---
title: "Video chat from Ubuntu to Windows"
date: 2011-01-18
forum: Multimedia Software
---

### Post by artemis999 on 2011-01-18
[SOLVED]
Hello!
I'm using Ubuntu 10.10 on my PC and I would like to video chat with my parents, which are using Windows. I have read all the solutions given to problems similar to mine, but none of them work. I have tried Skype, Ekiga, Pidgin plugins, Gmail chat... none of them allow me to share the video. If anyone knows how I could make this video calls work, please let me know.
Thx

---

### Post by gordintoronto on 2011-01-18
Use Skype.

If you have a webcam, install Cheese to see if it works with Ubuntu. You might need to look at page 28 of Full Circle Magazine, issue 44.

---

### Post by fluorescentblack on 2011-01-18
Im using Skype with my 10.10 and video chat with skype for windows . 

have you tried to see yourself or "test" if your webcam is working with skype? its somewhere in  Options> Video Devices. Check if there's a webcam available. if yes, click on "Test". hopefully, you'll see your own video. :) 

if you cant select a webcam in the list, i would assume your webcam isnt supported. if so, i wouldnt be of help since its been ages since i researched on webcam issues. hopefully someone would be able to point you to the right direction. :)

---

### Post by artemis999 on 2011-01-19
Well, this is the problem..the camera is working because I can see myself if I'm using Cheese. It is simply skype that won't work...the only thing that I can do is do start Cheese and share my screen, but i was hoping for a better solution :P

---

### Post by gordintoronto on 2011-01-19
Starting Skype by opening Accessories/Terminal and pasting in this command might work:

bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

---

### Post by artemis999 on 2011-01-20
[LEFT]Thank you very much gordintoronto! Your answer solves my problem! :P _[U] _[/U]
__[/LEFT]

---

