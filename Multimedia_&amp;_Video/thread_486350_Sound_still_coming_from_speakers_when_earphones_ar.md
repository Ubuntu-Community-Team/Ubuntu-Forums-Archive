---
title: "Sound still coming from speakers when earphones are plugged in."
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by BeauX1 on 2007-06-27
I've searched yet have not come across an answer that helps solve my problem

**The Problem:**

Speakers work fine, headphones work fine. Except when I plug my headphones in, audio still emits from the speakers.

I am using an Intel HDA.

Anyone shed some light on this issue?

Cheers.

- Beau

---

### Post by RTrev on 2007-06-30
> **BeauX1 said:**
> I've searched yet have not come across an answer that helps solve my problem

**The Problem:**

Speakers work fine, headphones work fine. Except when I plug my headphones in, audio still emits from the speakers.

I am using an Intel HDA.

Anyone shed some light on this issue?

Cheers.

- Beau

I don't believe this would have anything to do with Ubuntu, but would rather be a function of your speaker system.  Presumably the speakers have a headphone jack, and if a plug is inserted it's supposed to cut off the sound to the speakers.  Apparently it isn't working.

My own solution is to run an extension from the audio out on the back of the computer, which gives me a handy jack within reach.  If I want to use  my headphones, I just unplug the speakers from this jack and plug in the headphones.  

I don't think this is under any kind of software control.. it's specific to the hardware of your speaker system.

HTH.

---

### Post by afffffff on 2007-07-02
Im having this same problem on a laptop toshiba satellite a135, and the problem is in ubuntu, because with windows vista this doesnt happen.

Still looking for a solution :(

---

### Post by ajopaul on 2008-01-22
I have a dell 1520 and have the same problem! Any solutions ?

---

### Post by edm1 on 2008-01-22
I've never had this problem but i think it can be fixed by opening the sound mixer (double click on the speaker icon). Go to 'Switches' and play around with any checkboxes in there.

---

### Post by ajopaul on 2008-01-22
Have just two check boxes there *Line in as output * and *ADCMux*

---

### Post by ajopaul on 2008-01-22
and no effect either remember seeing a option like *Headphone jack sense* in feisty which is missing in mine.. 

My sound card 
 [I]00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
[/I]

and the method i used to install sound drivers

[I]    *  sudo apt-get install module-assistant
    * sudo m-a update
    * sudo m-a prepare
    * sudo m-a a-i alsa
[/I]

---

### Post by surgey on 2008-07-22
[FONT="Comic Sans MS"][COLOR="DarkRed"]**I have the same exact problem as the original question. But I find that if I just simply plug my headphones in and out once or twice the sound goes just to my headphones. It seems when I first plug the phones in and play something the sound comes from the speakers and phones. So if I unplug the phones and plug them back in it will then send sound just through the phones. But as I said sometimes it takes 2 tries. Other than that I cannot seem to find any other solution. **[/FONT][/COLOR]:-({|=

---

