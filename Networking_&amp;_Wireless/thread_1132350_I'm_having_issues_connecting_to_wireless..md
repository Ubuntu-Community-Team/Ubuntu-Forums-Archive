---
title: "I'm having issues connecting to wireless."
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by JoshJayK on 2009-04-21
I downloaded Wubi, and when everything installed, I got on and it worked fine. Then I tried to get on Firefox, and I realized internet wasn't connected. So I tried right clicking the computer thing on the top right hand to check the "Detect Wireless Networks" or whatever it's called, but I didn't even see the option. Then I tried to edit it and add the network manually, but I didn't know which WEP key I was supposed to use, and the options were just too complicated. Help?

---

### Post by calvinps on 2009-04-22
This is a VERY common problem for most people switching to Linux.

Go to Applications --> Accessories --> Terminal and type:

```
lshw -class network
```

and post the results when done. :)

---

### Post by JoshJayK on 2009-04-22
I don't know how to put the results here when I cant access internet on Ubuntu... O________O
Can you just list some possible things to fix this?

---

### Post by calvinps on 2009-04-22
Would it be possible just to have a wired connection for the now?

Once you do your Terminal thing, copy the entire thing and paste it on here.

---

### Post by JoshJayK on 2009-04-23
Okay I guess. I'll have to do it in like three days from now. Try not to forget about me!

---

### Post by t0mppa on 2009-04-23
You can just write ```
lshw -C network >> network.txt
``` on a terminal, which will push the output into a file named network.txt and then move the file to a computer that has internet access with a usb stick/drive, cd-rw, floppy or any other means that you have available and then paste the contents of that file over here.

---

### Post by Johanne on 2009-04-23
I'm having the same problems as you... I got ubuntu last night, and I could really use a detailed 'How to'-guide.

---

### Post by JoshJayK on 2009-04-23
Thanks guys. Uhmmm I'll try that later on in the weekend maybe. Do any of you have MSN or AIM?

---

### Post by JoshJayK on 2009-04-23
;ALSKDFGJA;DSLKGJ.

I put the image on a CD but for some reason, the extension is just FILE. TT_TT
What to do?

---

