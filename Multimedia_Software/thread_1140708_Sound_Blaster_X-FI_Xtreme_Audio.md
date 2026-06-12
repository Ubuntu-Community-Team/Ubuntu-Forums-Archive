---
title: "Sound Blaster X-FI Xtreme Audio"
date: 2009-04-27
forum: Multimedia Software
---

### Post by uktvfan on 2009-04-27
Hi everyone,

I am brand new to Ubuntu.  I just installed it (dual boot with M$ Vista) and I have a sound blaster X-Fi Xtreme Audio sound card.  I've tried working with alsa, and frankly I'm clueless as to what I am doing.  How can I get sound working.  

Please be gentle.  Again, I am so new to this that the dust has not had time to settle.

Thanks in advance!
Mike

---

### Post by MasterJS on 2009-04-27
I found something that worked for me, but i cannot guarantee it'll work for you. I found that Alsa was pointing to the onboard sound of my motherboard rather than my Soundblaster card. I went into the BIOS and disabled the onboard sound. That caused Alsa to point towards the Soundblaster. Hope it works for you.

---

### Post by uktvfan on 2009-04-27
Thanks for the reply MasterJS! I tried that and had no luck.  Any other help will be greatly appreciated!

Thanks,
Mike

---

### Post by sentrydogman on 2009-05-16
I'm as green as a new ear of corn with this here Ubuntu Linux stuff. I also have the
same soundcard and no sound and I'm praying for some helpful hints, since w/o
sound, this thing is wuthless. :o(

Wells P. Martin
Stamford, CT
[email]wellsp@att.net[/email]

---

### Post by thatboysabin on 2009-05-19
I downloaded the driver from the soundblaster website... extract it to some directory.

I opened a terminal (applications > accessories > terminal), browsed to the directory where i extracted it, typed the following commands:

> sudo make
sudo make install


I rebooted and I now have sound.

I have a soundblaster x-fi xtremegamer.

---

### Post by jeg on 2009-06-07
Where on the Soundblaster website did you find a Linux driver for the X-Fi Xtreme card?  They only seem to support Windows.

(Or if anyone else knows, please let me know.)

JEG

---

### Post by thatboysabin on 2009-06-24
[http://support.creative.com/Products/Products.aspx?catid=209](http://support.creative.com/Products/Products.aspx?catid=209)

---

### Post by Snocrash on 2010-01-26
OK. There is now a kernel module included for the X-Fi sound cards. I compiled 2.6.32.3 and it seems to be working. I was just wondering if this is basically the same code as the driver from creative? If not, does one work better then the other?? anyone know???

Thanks,

-Sno

---

### Post by Snocrash on 2010-01-28
::Bump::

---

### Post by s.maciek on 2010-03-02
Did you install the card ? I am trying to, so please answet as fast as you can :-).
And if you have installed this, plz tell me how ;].
Greetz.

---

