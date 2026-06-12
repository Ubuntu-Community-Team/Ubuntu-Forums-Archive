---
title: "disk utility"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rbrick49 on 2011-04-06
how reliable is the disk utility on ubuntu natty folks, mine just tells me my hard drive is dying only 12 months old maybe faulty and what brand do you guys recomend seagate or western digital

---

### Post by rbrick49 on 2011-04-06
how many hard drives do you have if you have 2 you would have sda,sdb, and I am just guessing sdc would be your floppy drive as I dont have a floppy drive and havent had for a long time I truly cant remember what a floppy comes up as

---

### Post by recluce on 2011-04-06
> **rbrick49 said:**
> how reliable is the disk utility on ubuntu natty folks, mine just tells me my hard drive is dying only 12 months old maybe faulty and what brand do you guys recomend seagate or western digital

From what little I can see in that screenshot, you have more than 4000 bad sectors on that drive. That would indicate failure. It would be helpful if you posted the SMART data of the drive.

---

### Post by rbrick49 on 2011-04-06
here the best I can do
when it all boils down this is probably why I have been getting corrupt installs of ubuntu

---

### Post by VMC on 2011-04-06
> **rbrick49 said:**
> how reliable is the disk utility on ubuntu natty folks, mine just tells me my hard drive is dying only 12 months old maybe faulty and what brand do you guys recomend seagate or western digital

Mine is 10 months old, and I have 1930 power cycles and it is fine. What brand is your hard drive. It should still be covered by the manufacture. I think Maxtor is 5 years. Also is it a notebook HD or desktop?

---

### Post by rbrick49 on 2011-04-06
hey vmc i live in thailand warranty here would take me forever to sort out its just easier to buy a new hard drive.its a seagate I allways used western digital in Australia not sure what to buy my computer is a desktop

---

### Post by cariboo on 2011-04-06
I'd suggest you run [Seatools]("http://www.seagate.com/www/en-us/support/downloads/seatools"), just to be doubly sure, the program will give you a fault code, if it can run at all. You can always send it back for warranty replacement, even if you buy a new drive. I don't know about you, but I can never have enough hard drives. If you haven't got a place for it in the computer, you can always put it in an external enclosure.

---

### Post by recluce on 2011-04-07
> **rbrick49 said:**
> here the best I can do
when it all boils down this is probably why I have been getting corrupt installs of ubuntu

This is a failed drive. SMART parameter 5 (reallocated sectors) has a raw value of 4045 or a "normalized" value of 2. Normalized values start at 100 or between 200 and 253, depending on manufacturer and model of drive, and count down to 0 or 1 (also depending). The threshold that Seagate defined for that parameter on your drive is 36, 2 is way below that. 

In other words: Seagate tells you the drive is toast, not Disk Utility which is merely reading the information from the drive and displays it in more human-readable form. Get all your data from your drive and replace it as soon as possible.

And +1 to cariboo907: even if you buy a new drive, send this piece of c**p back to Seagate for replacement. Why reward them for failure?

---

### Post by rbrick49 on 2011-04-07
well folks i went to the big city of roi-et
and purchased a new hard drive western digital I have just finished reinstalling natty all is good thanks for your input I have never had a hard drive fail before but anyway crap does happen I just might do what you guys suggest and take it back for warranty all is good but I still had to manually install boot loader but no hassel now as I have the code cariboo and it works,all these years of using linux and I never new that code but never had to use it before either 
thanks all Ron
ps that code is gold cariboo
an old guy told me before I went off to the army in 1969 he said to me remember this you learn something new every day dont forget it
it was so true what he said to me thanks poppa may you RIP

---

### Post by VMC on 2011-04-07
> **rbrick49 said:**
> well folks i went to the big city of roi-et
and purchased a new hard drive western digital I have just finished reinstalling natty all is good thanks for your input I have never had a hard drive fail before but anyway crap does happen I just might do what you guys suggest and take it back for warranty all is good but I still had to manually install boot loader but no hassel now as I have the code cariboo and it works,all these years of using linux and I never new that code but never had to use it before either 
thanks all Ron
ps that code is gold cariboo
an old guy told me before I went off to the army in 1969 he said to me remember this you learn something new every day dont forget it
it was so true what he said to me thanks poppa may you RIP

Also, with that Seatools link that cariboo gave, there is a section for you to see if your hard drive is still under warranty. I just checked it, and mine has a US stamp. Check if yours goes to your country code.

---

### Post by rbrick49 on 2011-04-07
made in china VMC so Iguess no 5 year warranty only 12 months
i just checked with seatools its still in warranty so it will be going back it must have five years it says 2014

---

