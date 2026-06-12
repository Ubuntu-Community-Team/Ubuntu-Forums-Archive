---
title: "help me make my genius ge111 webcam to work stable with gspca driver"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by edemark on 2007-05-09
Hi all

I have a problem with my genius ge111 webcam. It is supported by the gspca driver [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) I use the latest driver (20070508) from this site. I get my webcam start up and work nicely. However within generally 1 minute camera freezes (the time till freezing varies between some 10 seconds to up to 90 seconds) always. I compiled the driver myself from the source.
Thus i would need some help to make my cam working stable without freezing.

Thank you

---

### Post by edemark on 2007-05-10
Any idea? Anyone has the same webcam and got it work?

Please help me resolve this!

Thanks

---

### Post by edemark on 2007-05-10
ok 

So i got a bit further. Enabling v4l module in xorg.conf (adding the line: load   "v4l"  to the modules section of the file) made my webcam much more stable though it steel freezes but not that soon and not always.

Any ide how to make it more stable?

thanks

---

### Post by edemark on 2007-05-11
Hi all again

It makes me somehow sad that i am writing this thread to myself and by myself and there is no answer, not even a word.
Anyway i just wanted to tell me if it helps that camera is far more stable in pclinux os. IE in that linux i am able to change workspace without having my cam freezed. In Ubuntu cwitchintg workplace means frozen cam image.

Any (literrally ANY) help would be appreciated

thanks

---

### Post by edemark on 2007-05-14
someone!!! HELP please

---

### Post by edemark on 2007-05-17
So i shall just give up on this subject
One think makes me sad: my cam works flawlessly in pclinuxos

bye

---

### Post by ranarion on 2007-06-04
I will try to look into this. I'm sorry to see no one answered to your post, but there's something you can do to increase your chances for an answer: As paradoxical as it may sound, don't reply to yourself. In other forums, this can be used to "bump" your thread and get it to the top of a topic; here, however, there is a button to show "unanswered posts" and a lot of regulars use this to get to unsolved problems. If you reply to yourself, however, this won't work...

---

### Post by ranarion on 2007-06-06
Strangely enough, on one of my two Feisty machines, it works by simply plugging it in, on the other, it does not work at all. The machine on which the camera works runs a 2.6.20-16-generic kernel, the other runs a 386 kernel. It may be possible that those use different modules... What kernel did you run it on?

---

### Post by edemark on 2007-09-05
Hi

I just wanted to say thanks you for your reply
The truce is that i had not checked back to this thread to see if someone has responded until now
Actually I am using the generic kernel and installed the 2007/05/08 driver from this site [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)
The camera is running so unstable that is no worth starting it.
Once again it was running really ok on dapper (i have never installed edgy)now i am running feisty

thansk again for your reply

---

### Post by ranarion on 2007-09-18
Actually, I start to suspect problems with the USB chipsets here, but I assume that only driver developers can help further...

---

### Post by ranarion on 2007-10-11
It seems to work now, on Ubuntu 7.04 (Feisty) with a 2.6.20-16-generic kernel.

---

