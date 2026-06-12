---
title: "Pci Tv / Tuner: got one working out-of-the-box?"
date: 2008-09-15
forum: Multimedia Software
---

### Post by ruipedroca on 2008-09-15
Do you have a Pci Tv / Tuner card?
Does it works out-of-the-box when you install (k)ubuntu?
If so, please post the brand and model!

---

### Post by Ck.asdf on 2008-09-15
In my desktop, I have a PCI Hauppage WinTV PVR 150 MCE.  I bought it from newegg.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815116620](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116620)

It works well, both in Windows, and in Linux.  The only thing I've not figured out is how to record in Linux.  That, and how to access the composite audio/video.

But, you can watch tv by playing from /dev/video0 such as:
vlc /dev/video0

You can replace vlc with your favorite player, and it may work, depending on varying things.

To change the channel, you can download ivtv-utils, which is handy.
```
sudo apt-get install ivtv-utils -y
```

A friend and I have made a small C++ program that makes changing the channel a bit easy, and once I add a couple things to it, and make it better, I may put it up on Sourceforge or something.

To see the source of the program (which you can download and compile), go to:

**Text (to view online):**
[http://ck.podzone.net/docs/chan.txt](http://ck.podzone.net/docs/chan.txt)
**Source file:**
[http://ck.podzone.net/docs/chan.cc](http://ck.podzone.net/docs/chan.cc)
**Compiled binary ('cause I'm nice):**
[http://ck.podzone.net/docs/chan](http://ck.podzone.net/docs/chan)

If you put chan in your /usr/bin, you can call it from anywhere.

It's not finished, per se, but it'll do the job.  I want to add more to it, but that'll come later.

---

### Post by ruipedroca on 2008-09-15
Ok, nice one! Correct me if I'm wrong, but that card doesn't have tuner only tv, right?

Other guys, please continue posting!

---

### Post by Ck.asdf on 2008-09-15
I don't understand your question.
It has an analogue television tuner, with a hardware MPEG encoder for recording (so it doesn't eat up your CPU).

It doesn't have a digital tuner, which means that it's not going to work with over-the-air digital tv in 2009, but if you have a cable subscription, you should be fine.

---

### Post by ruipedroca on 2008-09-18
Ooops! I ment radio tuner!

Regards

---

### Post by Ck.asdf on 2008-09-18
Yes, it does have a radio tuner, though from my experience, and lots of others, it seems, the reception is not that wonderful, even with the included antenna, but I am not sure many tuners would have a good radio.  You may have better luck, though, especially if you find a good place to put the antenna.  I did not try very hard to place it in a place of good reception.

The radio does work in Windows and Linux.  In linux, when you have that ivtv-utils installed, you can use the following commands to get your television and radio work.

```

In terminal
mplayer -vo xv /dev/video0
you can also change "mplayer" to whatever media player you want to use

Now in a new terminal
ivtv-tune -c xx -d /dev/video0

Replace xx with the channel you want to tune into.

Listen to radio
ivtv-radio -f xx.x
xx.x being the station you want to tune into.

```

---

### Post by saedelaere on 2008-09-18
Both the Pvr-150 and PVR-350 work out of the box. 
And [here]("http://home.arcor.de/saedelaere/index_eng.html") is a small frontend for those cards.

Regards

---

### Post by ruipedroca on 2008-09-18
Many thanks to both of you!!

Others, please continue posting!

---

### Post by Ck.asdf on 2008-09-18
TV-Viewer
I saw something on the page about recording ... is there such an option as scheduled recording?

---

### Post by saedelaere on 2008-09-18
> **Ck.asdf said:**
> TV-Viewer
I saw something on the page about recording ... is there such an option as scheduled recording?

Yes you can perform schedulded recordings

---

