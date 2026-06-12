---
title: "How to &quot;listen&quot; to a microphone input?"
date: 2010-06-10
forum: Multimedia Software
---

### Post by boopit on 2010-06-10
Hey all. 

I have a bit of a problem here. 

I have a vinyl turntable. The only output it has are some RCA cables. I've connevted these to other RCA cables, so now, I can put it into one of the audio in jacks on my computer. It's just a standard microphone plug. In Windows, there was an option that would let me listen to the input, and this would be the only way I could listen to my vinyls. In kubuntu, I can't find any way to do so. I don't want to have to boot into Windows 7 every time I want to listen to my vinyls, so is there any way I can get around this? 

Thanks.

---

### Post by Jinger on 2010-06-10
I give you an advice, but i think that there's another way to do this. My advice involves installing Jack.

1)Install Jack:Open a terminal window and write:
```
sudo apt-get install jackd

```

2)After downloading and installing it, Jack controll will appear in "Audio and Video". Open It. 

3)A window like this will come:
[IMG]http://img138.imageshack.us/img138/9143/schermatajackaudioconne.png[/IMG]
Click on "Start" and then on "Connect"

4)Now you'll be able to say to your computer that everything comes from "input audio" must be reproduced. In order to do this follow the image and above all the arrows:
[IMG]http://img8.imageshack.us/img8/4882/schermataconnectionsjac.png[/IMG]
Every "Capture_X" must be selected and connected to system in the right column and then press "Connect"

5)Press play on your turntable and listen your music!

---

### Post by fidget84 on 2012-06-18
I don't have system or anything else on the "Writable Clients" side to connect to...

---

### Post by oldos2er on 2012-06-18
Please start a new thread, fidget84. This one's two years old.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

