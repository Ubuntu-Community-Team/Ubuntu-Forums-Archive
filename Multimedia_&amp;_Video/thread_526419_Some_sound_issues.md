---
title: "Some sound issues"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by Metallion on 2007-08-15
I´ve got a couple of issues here and am a bit pessimistic about solving some of them but can´t hurt to try now can it?

I have recently installed Ubuntu on this machine which was running windows before. I have however been using ubuntu without many problems at my job since half a year.

1) My microphone doesn´t work. This is very strange since it worked when I installed skype on my first boot but somehow, it doesn´t work any more now. I did enable surround sound inbetween but I don´t think that should change anything about my mic. I tried reinstalling the alsa drivers with one of the guides on this site but it didn´t help. I also checked the recording volume which is allright. 

I get the following message when I try to start a skype call: Call failed: problem with audio capture.

If I check the sound preferences (where capture is set to alsa) it gives me this: gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource busy or not available.

Looks like there´s some lock file somewhere which isn´t deleted properly or something but where can I found those?

2) VLC stutters terribly when playing any kind of sound in it. Rythmbox has no problems however. Usually VLC doesn´t need any codecs so I thought that couldn´t be the problem.

3) I have really bad sound quality when watching some flash movies on newgrounds.com. Youtube doesn´t give me any problems there though.

I´m using an nvidia nforce3 motherboard with onboard realtek ac97 audio. I thought about installing the official realtek drivers but i´ve seen many forum posts of people using those and losing their sound so I thought I wouldn´t go on with that without any further reccomendation.

---

### Post by jmate24 on 2007-08-16
hi, my name is jmate24 i just need to know more about your computer.

1. what other audio devices do you have connected to your computer
2. are the audio connectors connected to the correct jacks (line in, microphone in, speaker out).
3. have you added any new hardware recently (anything external/usb drives count too).
4. how much RAM do you have
5. what type of processor (x86, AMD64, Intel64)
6. what version of Ubuntu(6.06, 6.10, 7.04)


thank you, that would be most helpfull.

jmate24:)

---

