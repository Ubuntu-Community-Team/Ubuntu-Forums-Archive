---
title: "Skype and microphone problems"
date: 2006-09-29
forum: Multimedia &amp; Video
---

### Post by kaitenbushi on 2006-09-29
I have installed Skype 1.3 beta, but I just can't get it to work. When I do a test call, it calls for a second, and then breaks with the error message "Problem with sound device".
My headset plays music in Sound Juicer, and my mic records fine in Sound Recorder. In Multimedia Systems Selector testing output works fine, but when I test input, I am only able to hear the recording sound for a second or so. 
My sound card is ESS AudioDrive ES1869.
If anyone has some help to offer, I would be deeply grateful.
BTW, I am quite new to Ubuntu.

---

### Post by kaitenbushi on 2006-09-30
I have managed to get Skype working now, but it works very irregulary. When I reboot the machine and start Skype, it will work only around half of the times. 
More detailed:
If I, after reboot but before starting Skype, start Multimedia Systems Selector and test Default Input Plugin (Input: ALSA), I will sometimes get
1: a "testing pipeline" window, 
and other times 
2: a window saying "Resource is busy or not availiable". 
When I afterwards start Skype and call a test call, it will either
A: connect, call for a second and give the error message "Problem with sound device"
or
B: work fine

The pattern is: when I get 1 I will get A, and when I get 2 I will get B (not the other way around as I would think would make a bit more sense)

So my sound system seems to behave very irregulary after reboot. Any help would be appreciated.

---

### Post by cakmin on 2006-10-08
> **kaitenbushi said:**
> I have managed to get Skype working now, but it works very irregulary. When I reboot the machine and start Skype, it will work only around half of the times. 

Not sure if this is of a help but I used to have a problem with Skype and my headset (microphone). I played around with alsamixer, under the playback menu I went to mono out, choose mic and then press tab to get into Capture menu, went to capture bar, increase it up to 100 and went to mic press space bar.

I also played with the sound symbol located next to the date bar.
Double click on it, and then choose capture and make sure the microphone sign under the mic and capture bars are not crossed.

It works for me although it is not perfect. At least I can hear my voice when I do a test call now.

---

### Post by Marco Modesto on 2006-10-19
This worked with me:

to get your mic working, if skype is not recording from it, try the following:

- switch to the alsamixer view 'Capture' with TAB or start it with command:
:~> alsamixer -V capture -c CARDNUM
Where CARDNUM is 0 or 1 or 2 ...

- make sure you have 'Mic' and 'Capture' sliders marked FULL SOUND (selected as CAPTUR). To do this hit space.

Now maybe your mic sound is working.

Credits for this tip and another solutions for this problem:
RockHound
[http://forum.skype.com/lofiversion/index.php/t66544.html](http://forum.skype.com/lofiversion/index.php/t66544.html)


[]s

Marco Modesto.

---

