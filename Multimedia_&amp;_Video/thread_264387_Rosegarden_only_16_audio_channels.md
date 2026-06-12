---
title: "Rosegarden only 16 audio channels?"
date: 2006-09-24
forum: Multimedia &amp; Video
---

### Post by InterFerencz on 2006-09-24
Hello, I'm new here. Also new to Linux. I decided 2 weeks ago to switch from Windows to Linux-Ubuntu. You know why. I mainly use my PC for recording and mastering music. Now I use Rosegarden and it (finally) works ok, but I can ónly use 16 audio channels. Is this because I use the internal audio on the motherboard because Linux does not support my Maya 44? If so, can you give me some advice which card is preferred?

Thanks in advance,

Ferencz.

---

### Post by damu on 2006-09-25
For audio recording, I would strongly recommend to use Ardour. It comes with  full automation for the mix , and is way more advanced than Rosegarden in that respect. The only limitations in Ardour are your hardware limits!

Rosegarden is perfect for midi composition and arrangement though. 

So what you could do is start both programs, and sync them through JAck.

To do that, go in the option of Rosegarden , you will find an option for Rosegarden to be synced to Jack.
In Ardour, you can also sync to Jack.

Now any time you will run your song from one program or another both will run. 
You can this way synced more programs...you could add Hydrogen for example.

One last thing. One your midi recordings are over, you will probably want to have all your tracks in Ardour to mix everything. So, you can do that in one recording session. In Ardour, create as many tracks as midi tracks you have in Rosegarden. For each track you assign from the input of Ardour's mixer one output of Rosegarden. When everything is jacked properly, you can trigger the record option for  all these tracks in Ardour and record.

Enjoy!

---

