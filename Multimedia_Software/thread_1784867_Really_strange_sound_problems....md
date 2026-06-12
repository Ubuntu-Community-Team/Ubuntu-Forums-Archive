---
title: "Really strange sound problems..."
date: 2011-06-17
forum: Multimedia Software
---

### Post by Antarctica32 on 2011-06-17
Well I'm having some pretty odd problems with an HP pavilion I just finished installing on. It has line-out, line-in, and mic ports on the front and line-in, line-out, mic, side, rear, and sub on the back. For some reason audio works fine on the back line-out but whenever I plug headphones or another set of speakers to the front no sound comes out of the front and the sound that comes out of the back (which you would expect to be turned off when i plug something in the front) just gets all distorted. This is the part where it gets really weird. When i plug in headphones into the frontal mic port i can hear the sound! Its really weird but I just plug in headphones to the frontal microphone port and it acts as if the mic port is a line-out! Other than that everything works fine, including the frontal line-in. I am putting together this ubuntu box for somebody else who doesn't know anything about computers really so I want it to be working fine. All help of any kind is greatly appreciated. Thanks in advance.

---

### Post by Antarctica32 on 2011-06-17
bump

---

### Post by wolfgangmcq on 2011-06-17
I've had similar (but not quite as odd) problems on pretty much every Ubuntu machine I've had, of some sort or another. Here's my procedure for fixing it:

[LIST=1]
[*]Open a terminal, and enter speaker-test
[*]Open System->Preferences->Sound
[*]Go to the Applications tab, make sure speaker-test is working
[*]Try every possible combo of the options under Hardware and Output until everything works.
[*]Put in headphones, and make sure it still works.
[/LIST]
Good luck!

---

### Post by Antarctica32 on 2011-06-17
no luck 

I tried every possible combo. 
I think it has something to do with the wrong driver, or maybe a hardware problem. I know a way to find out. 

I run a live CD (or usb) and see if it works.

---

### Post by lidex on 2011-06-18
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Antarctica32 on 2011-06-18
Ok so I booted from a lucid USB drive with the same problems as before. This doesn't really prove much being as the live usb uses the same driver as my install probably. I'm going to boot from something non-ubuntu and see if that fixes it. If it does it means its probably a driver problem. 

@lidex
 ok so i ran the command and it gave me this as my link:

[http://www.alsa-project.org/db/?f=47a3e9e71f7774fd6ec75bd1d49c8971075dd5fd](http://www.alsa-project.org/db/?f=47a3e9e71f7774fd6ec75bd1d49c8971075dd5fd)

---

### Post by Antarctica32 on 2011-06-18
so I opened the HP up again to take a closer look to see if any thing was notably wrong with the hardware. There are 3 white cables leading away from the 3 audio port. 2 of them join together to create a single green port thing that was attached to a matching green port thing on the mobo. The port is NOT one of the more commonly used audio cables like in the attached image. It uses some weird port only useful to this specific computer. In little white print next to it on the mobo it is printed AUDIOPCI. Then the third wire goes to a similar but white port that says: Line_In_Front. Then I noticed a third one of these ports but black near by, labeled: CD_In. This port however has nothing coming from it. I highly doubt any of this matters, but it is interesting to note. I never really liked the pavilion series, they were to hard too work with, to0 cramped.

---

### Post by lidex on 2011-06-18
Which of these configurations matches your hardware:
```

  3stack	3-jack in back and a headphone out
  3stack-digout	3-jack in back, a HP out and a SPDIF out
  5stack	5-jack in back, 2-jack in front
  5stack-digout	5-jack in back, 2-jack in front, a SPDIF out
  6stack	6-jack in back, 2-jack in front
  6stack-digout	6-jack with a SPDIF out
```

---

### Post by Antarctica32 on 2011-06-18
none of them really. 
to be exact I have Line-in, line-out, and mic in front. And then I have 6 in back (mic, in, out, sub, rear, and side), but I also have a digital out and in. Hope that helps. 
Thanks soo much for your help! I really need this thing working fine and I appreciate your help.

---

### Post by lidex on 2011-06-18
I would vote for '6stack-digout'
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=6stack-digout" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by Antarctica32 on 2011-06-18
```
options snd-hda-intel model=6stack-digout
```

Why did you tell me to do that? The echo thing? Doesn't echo just repeat whatever you have in quotes?

---

### Post by lidex on 2011-06-18
> **Antarctica32 said:**
> ```
options snd-hda-intel model=6stack-digout
```

Why did you tell me to do that? The echo thing? Doesn't echo just repeat whatever you have in quotes?

I was screwing with your head just to see if you would do it;)
Kidding!
The second part of that command adds the echoed text to alsa-base.conf so you don't have to manually edit the file.

---

### Post by Antarctica32 on 2011-06-18
Ok, I booted from a natty usb with no difference. Same exact problem.

---

### Post by lidex on 2011-06-18
How about from the hdd?

---

### Post by Antarctica32 on 2011-06-18
Ow sorry I completely forgot, i was playing around with unity on natty. Yeah it appears to work now with one little exception. When I plug a TRS into the line-out on the front it sends the audio to the headphones or whatever I just ho0ked up, but it continues to send it to the rear line-out, my speakers. Its not that big of a problem at all really. Thank you sssooo much!!  

 In the words of Choi to Neo: "Hallelujah. You’re my savior, man. My own personal Jesus Christ."

But I have one final question. What caused all this? Did the driver just not work too well with the hardware? Or did the hardware make it seem that it was something different than what it really was? That would explain why even after I tried different OSs it still gave me the same result. Once again I can not thank you enough.

---

### Post by lidex on 2011-06-19
The hardware configuration is different than the generic parser assumes (for your codec) so you have to tell it to use another layout, or pin configuration.

---

