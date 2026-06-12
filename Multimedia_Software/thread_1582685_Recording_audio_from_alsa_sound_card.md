---
title: "Recording audio from alsa sound card"
date: 2010-09-26
forum: Multimedia Software
---

### Post by jhaskins75 on 2010-09-26
I posted my question on Linx.com, but have not received an answer after 75 viewers to my question:
Ok my respected Linux genius. This is my project. First I have a Windows / Linux combo OS set-up!
In my windows, I use the latest realtex sound driver as this gives me  complete control with recording output control and Microphone gain  control. In the set-up, there is a stereo mixer component with is  necessary to engage the direct sound recording from my sound card. To  make this all come together, I use a sound recording software [ free  sound recorder 9 ] and to convert the recording to a wma, wav, or meg, I  use Roxio 10 to produce audio cd's to play on all CD Players.

The challenge for me in Linux is to create the same set-up with Linux applications to produce the same professional results.
Presently, my kubuntu 10.04 has Alsa sound drivers, with a version of  realtek incorporated. I have the Alsa mixer software as well as Audacity  as the sound recorder program. But no matter what I do, audacity  depends on the microphone to record, which makes the final recording  pure crap. If I lower the microphone boost or gain in my Alsa mix, then  Audacity can not record the ambient sound from the speaker output and it  will only recognize mono and pulse as the sound method. With the pre  mention set up, Who has a set up identical to what is offered to windows  that will do exactly the same for Linux. I basically want to record  directly from the sound card in my Linux, without depending on using my  microphone and then a CD burning program to make the conversion to MPEG  or the necessary file format for the burned CD to play in all CD  players, not just on a PC)    I am trying to stay away from command line  language in the terminal. I really need a replacement for Audacity,  cause Free Sound Recorder is made for Windows Platform......I need a  Linux sound Guru for the answer.....
ALSO...I am not doing this to pirate music....I have over 3,450 music  track inside my Rhapsody subscription and I like to record music for  personal listening on my portable CD player and at 0.99 per track charge  to do this in Rhapsody, I might as well by a recording studio and hire  the singing artist.
Basically in short..I need to know if there is a setting I can engage in my Alsa Mixer panel that will allow me to record directly from my sound card without using my microphone as a default. When I mute the microphone in my Alsa control panel, my Audacity program will not record using the microphone, which I do not want to use anyway. I just want to record straight from my sound card, as this eliminates all hiss, distortion that is inherited with using a microphone.:confused:

---

### Post by kevingp12 on 2010-10-03
awww im sorry you dont have an answer, im new to linux i just came across this post because i was looking for something that had to do with a hiss in my soundcard recording.. well actually i might help i mean ive only been using this for a week, well maybe you know this or not but here what i got..
i use audacity for my recording and i actually record off my maudio fast track pro external sound card.
i came aound to this post actually  yesterday.. 
maybe this can help.
[http://stream-recorder.com/forum/showpost.php?p=15384&postcount=2](http://stream-recorder.com/forum/showpost.php?p=15384&postcount=2)

just follow the steps , it has to work because i did it and it worked, i basically recorded the audio coming out of my soundcard directly to audacity..

---

### Post by kevingp12 on 2010-10-03
hey tell me if it worked..

---

### Post by jhaskins75 on 2010-10-04
Thank you for the timely advice! I am still unable to record directly from my sound card using linux Alsa setup. I opened my sound control console, but do not see the ' Mix ' feature to engage the process. If I go into my Alsa mixer panel and mute the microphone, then audacity cannot sense the ambient music. I need to be able to record directly from my sound card. I also use realtek ALC888 as my sound driver in Linux, but it to has no feature available to set for direct recording from my sound card, or at lease I do not see it I was told to use KMix to set it, but the mix feature is not there. What software are you using, as if I do your setup, I may be able to duplicate it. John...:(

---

### Post by 1redapple on 2011-11-17
I have the same problem here ... if somebody can help me :D mu kubuntu doesnt detect my mic :(

---

