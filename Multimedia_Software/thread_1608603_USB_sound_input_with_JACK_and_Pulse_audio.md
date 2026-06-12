---
title: "USB sound input with JACK and Pulse audio"
date: 2010-10-29
forum: Multimedia Software
---

### Post by buddykoerner on 2010-10-29
Hello,


 For a long time i have been messing around with Jack and Pulse audio  on my system. My final goal is to get Ardour running and that means that  i need JACK to be running as well. As i was writing a post because i  was unable to get JACK to start, it for some reason started working  for me. It could have been from something i did but never restarted my  computer.


 I wish i could just switch over to Ubuntu Studio but have been  unsuccessful because my CD drive is broken and am not able to boot from  the USB flash drive that I made with the ubuntu studio image file. any  help here would be appreciated as well...


 anyways....


 I have the following installed (hopefully correctly): Ardour,  qjackctl, LSDPA effects "rack", Jack rack, JAMin, calf-plugins, Lv2  audio plugins. I also have Pulse Audio installed.


 There are other things installed that are involved with the two programs but those are the ones that seem relevant.


 I start qjackctl, and then am able to click "start". I get no error message (woohoo) and the program starts.


 I then go into connections and under the Audio tab i see: (readable)  System: Capture1 Capture 2, (writeable) system: Playback 1 Playback 2.


 I am able to connect to these and can hear that my internal Mic  through my speakers. This is good and makes me happy for now because it  means that JACK is working to some extent.


 What i WANT is to be able to connect to my USB sound input.


 Under system preferences, Sound: I am able to see two options under  the hardware tab: (Internal audio) and (PCM 2900 audio codec). The same  goes for the Input and Output tab. I believe that this is my USB input  from my Mixer.






 Any help would be great




 Thanks,
-Buddy

---

### Post by cchhrriiss121212 on 2010-10-29
Hello Buddy,
You have made a good start with setting things up. Jack works best with supported devices, what is the USB input you are referring to? Brand, model etc.
Are you intending to use both the USB device and the onboard sound at the same time? Or do you just want the USB? 

Regarding studio, you can install all the packages by upgrading through software center or synaptic. But you have all the packages you need already so I would not bother. The only additional thing to install would be a low latency or rt kernel which are tweaked for audio usage. I can explain how to install that if you like, once you get these other issues sorted out.

---

