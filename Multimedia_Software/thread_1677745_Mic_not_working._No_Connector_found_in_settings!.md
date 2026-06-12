---
title: "Mic not working. No Connector found in settings!"
date: 2011-01-29
forum: Multimedia Software
---

### Post by goun on 2011-01-29
Hello,

I installed Ubuntu 10.10 (although in the System->About Ubuntu is mentioned that I have Ubuntu 11.04    - the Natty Narwhal, I don't know why) and I can not make the microphone from my headset to work. I used to have the Ubuntu 8.04 (I think so) and the mic used to work normally.

I searched in forums without success! Everyone proposes to change the Connector in the Sound Settings but I do not have such option (you can see the attached image). What should I do?

Thank you in advance!

---

### Post by lidex on 2011-01-29
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by goun on 2011-01-31
Thanks for the replying! Here you are: [http://www.alsa-project.org/db/?f=7908492fd3e04c7e4f2750fcb2c733056b94720f](http://www.alsa-project.org/db/?f=7908492fd3e04c7e4f2750fcb2c733056b94720f)

---

### Post by goun on 2011-01-31
Mic works!

In order to do so, I changed the default value of input source from mic to cd and then back again from cd to mic! Then the change was actually applied.

I had exactly the same issue with Ubuntu 9.04: I had to change from mic to cd and then back to mic again every time I booted my Ubuntu. Is it some kind of bug?

---

