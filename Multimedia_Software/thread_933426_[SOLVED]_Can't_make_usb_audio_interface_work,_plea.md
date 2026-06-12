---
title: "[SOLVED] Can't make usb audio interface work, please Help!"
date: 2008-09-29
forum: Multimedia Software
---

### Post by procastino on 2008-09-29
Hi All!
I've just received a Behringer podcast Studio, wich is mainly a mic, a mixer and a UCA200 , usb audio interface. I've been trying for hours to make it work, and researching this forum I've found some people that say that for them it was just plug n' play. I must be doing something very wrong (I use to), but i don't know what! Card is listed when I write aplay -l on terminal, but then I can't record any sound from it...
I'm using 8.04.
Thanks

---

### Post by markbuntu on 2008-09-29
Which application are you using for recording and how do you have it setup for audio input or plugin.

---

### Post by procastino on 2008-09-29
Well, I've tried with Ubuntu's sound recorder and jack and they don't work, now i've just installed Audacity and with this application it works (but with quite low volume). I'm trying gtk-recordmydesktop, wich is mainly the program I need to work with. In it's sound options - Device - - DEFAULT. I'm trying to use jack to define it's audio input, but it says jack_lsp returned no ports and doesn't let me record (message: error 768 could not open/configure sound card).
Jack gives me the following message qhen I run it "could not connect to jack server as client"
Hope I've made myself understood, I'm a bit fuzzy right now... :)

---

### Post by markbuntu on 2008-09-29
Well, the card is sort of working so we know it is not a driver issue so much as a setup issue. Look in my guide here. It has advice on getting applications to work, and jack and some usb stuff that while mostly about usb headphones may point you in the proper direction for your quest. No need to follow it, which is sort of impossible anyway, just read the parts and look in the links that grab your interest.


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by procastino on 2008-09-30
Uff! Thanks very much markbuntu for your guide and help, now my USB Audio Device works on most of the applications and I understand much more about audio in Ubuntu. The last problem I haven't solved yet is gtk-recordmydesktop, which still tries to capture from the onboard sound card instead of the USB which I've got as default . Does anyone know how this can be solved?

---

### Post by procastino on 2008-10-01
Ok now, I've got my recordmydesktop working! It cost me a pretty much, but I'm quite dumb with this things. Apart from markubuntu guide that is already linked in this thread, this other site helped me too [http://www.linuxplanet.com/linuxplanet/tutorials/6491/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6491/1/)

Just if anyone is thinking about it, I've got Behringer podcast studio, which has an USB uca200 as audio interface, and it gives enough sound quality for me.

If you want to see my screencasts go to [http://tuchomendeztitoriais.blogaliza.org](http://tuchomendeztitoriais.blogaliza.org) , they're in Galician so I suppose they won't be very useful for most of the people. Next ones will sound better!

---

### Post by markbuntu on 2008-10-01
Ok, glad to help out. Now could you please mark this thread as solved using the thread tools above. 

That way people looking for solutions will go "Oh, he has figured it out I should go there, and people offering help will not be wasting their time looking in a thread that is already solved.

Thank you.

---

### Post by procastino on 2008-10-02
Sure, truth is I wanted to but I didn´t know how.

---

### Post by kommado on 2010-04-20
Dear Procastino,

Have you tried this device with Internet DJ console?
I'm planning to buy it but I don't know about the compatibility.

Thanks in advance.

---

### Post by procastino on 2010-04-21
I'm sorry, I haven't tried.

---

