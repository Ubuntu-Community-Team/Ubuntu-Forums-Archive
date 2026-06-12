---
title: "Skype Configuration with &quot;Plantronics CS-60 Wireless Headset&quot;"
date: 2010-12-30
forum: Multimedia Software
---

### Post by sembagdod on 2010-12-30
HI!, 
On "Windows XP"
I was able to choose "CS-60" from the Skype options (AS MIC and Speaker), and by doing that i was e able to listen to music or any Windows sound while others use voice chat on skype (at the same time)

On "Ubuntu 10.10" with Skype 2.1.0.81
I can choose the "CS-60" only from the "Pulse Audio Volume Control"
and when i checked Skype option it shows only "PulseAudio Server (local)" hence i can't use the PC sound if anyone was on Skype call. 

In addition i have to keep switch between "CS-60" and "Internal Audio Analog Stereo" before and after each Skype call. 

Any one cal help?

---

### Post by marseille on 2010-12-30
hi:) join our skype discussion here and check out the links to see if any of them can help.

[http://ubuntuforums.org/showthread.php?t=1656246&highlight=skype](http://ubuntuforums.org/showthread.php?t=1656246&highlight=skype)

---

### Post by sembagdod on 2010-12-31
Thanks marseille, 
In fact i went through those forms while i was configuring my sound for the first time, but all what i got is temporary solution which set the  "Pulse Audio Volume Control" to the required Mic and speaker and it will work with Skype as well. 

What am looking for is to enable the skype choose another external sound device, like in my case "Plantronics CS-60".

in Windows XP, i was able to choose the sound source from Skype options, and choose another sound source for my Desktop speakers
that will enable me to use skype, with my wireless headphone and use the desktop speakers to listen to music (at the same time)
I believe this is new subject on the given forms. 

Regards

---

### Post by marseille on 2010-12-31
So I'm assuming you already chose your particular mic in Pavucontrol but Skype only gives you one option for ``PulseAudio server local''. Correct? If so, are you saying that you *just* can't listen to music/videos/etc. while you chat... in other words, all other sounds are muted or just other sounds within Skype?


> Pavucontrol >> Input Devices >> Port

[IMG]http://ubuntuforums.org/picture.php?albumid=266&pictureid=7285[/IMG]


> Skype >> Sound Devices >> Microphone >> PulseAudio server (local)


[IMG]http://ubuntuforums.org/picture.php?albumid=266&pictureid=7286[/IMG]

---

### Post by marseille on 2010-12-31
Although, I am just a user and can't profess to be an expert (other folks will surely come along and help us on our Skype journey to be sure), prior to the advent of Lucid I use to use IDJC. I never used it with Skype but many others have[ [https://encrypted.google.com/search?q=recording+skype+with+IDJC&hl=en&num=10&lr=&ft=i&cr=&safe=images&tbs=,qdr:y](https://encrypted.google.com/search?q=recording+skype+with+IDJC&hl=en&num=10&lr=&ft=i&cr=&safe=images&tbs=,qdr:y) ] . I also saw another python (i think) Skype recording app in Synaptic.

I want to add a note about Alsa/Jackq [ [http://alsa.opensrc.org/index.php/JACK](http://alsa.opensrc.org/index.php/JACK) ]. The reason I bring this up is because it's probably easier for you to route your audio through jack if you're going to use multiple mics and/or other external AV gear. In fact, many audiophiles simply prefer using ALSA alone.

There's a whole lot of information about that so searching the topic will serve you better than my mere words.

*   *   *   *

Let us know how things go and if I can think of anything to add I'll share. In the meantime, I highly recommend ubuntustudio forum threads. The hot-shots are in there and could probably solve this issue much quicker.

---

### Post by sembagdod on 2011-01-01
Thanks Marseille
Yes in fact what did you describe is exactly what am facing and the answer to your question " in other words, all other sounds are muted or just other sounds within Skype?"  yes, all sounds comes within skype. i also attach 2 screenshot to clarify more. 
also i went through some of the links and topics that us suggest, and i believe "FUSD" can solve my problem "not sure", but i wasn't able to install it...as am new to Linux world, and they said i have to read the LFS-Book and should be able to create new kernal and enable the DEVFS ...etc to be able to Run it !
anyway i will try my best and update you in case i found the solution. 

Thanks for your help. 


[IMG]http://ubuntu-ky.ubuntuforums.org/attachment.php?attachmentid=180244&stc=1&d=1294264303[/IMG]

[IMG]http://ubuntu-ky.ubuntuforums.org/attachment.php?attachmentid=180245&stc=1&d=1294264541[/IMG]


Regards

---

