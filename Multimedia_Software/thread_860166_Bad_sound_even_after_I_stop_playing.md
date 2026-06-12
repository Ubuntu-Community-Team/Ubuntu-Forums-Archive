---
title: "Bad sound even after I stop playing"
date: 2008-07-15
forum: Multimedia Software
---

### Post by jsiei97 on 2008-07-15
Hi 

I have a funny little problem that I never had in the past
(but then I have tried to avoid alsa...)

Right now I have a Ubuntu 8.04 that is up to date.

Since the problem is a little bit hard to explain I took a video with my mobile phone, and since I could not attach it to this thread I put it on youtube so it would be easy to look at. 

[http://www.youtube.com/watch?v=5TfhPxdfIho - The sound problem]("http://www.youtube.com/watch?v=5TfhPxdfIho")


Step by step:
1. Start audacious and play some mp3
2. Wait a little and do nothing (the sound is ok)
3. Move the pointer in the background or move some windows, 
  there is a strange and annoying sound.
4. Stop audacious and the sound is still there (when I move the pointer)
5. Stop alsa with "/etc/init.d/alsa-utils stop" and no more problem,    this is just to prove that I don't have a hardware problem with electric interference. 

Note.
The video is with kde4, but the problem is still there even if I use gnome or e16.

I usually uses xmms, but since the original xmms is no longer avail I have tried to use audacious since that is nearly the same thing. 

Do you have any good idea on what this can be?
Or do you have any good idea on what I can try to get rid off the problem?

Thanks
Johan

---

### Post by deadgobby on 2008-07-15
I watch your vid and if that is your speaker right of the the monitor. Move the speaker away from the monitor. Your speakers has magnets and may cause electromagnetic field disturbance. So when you are playing music and the sound have static while you are moving your mouse around while clicking down. Because the electromagnetic fields comes into play. It stops when you no longer have the speaker play any sounds. Besides that is not good to place a speaker in close range to your monitor. You'll may burn out the monitor in no time quick. Yet, slowly watch the color of your monitor fad out to one side.  
 You can see/hear if that is the problem by moving the speaker out of range at one step at a time. Play music and do what you did to get the interference. Keep on moving the speaker away till it does it no more. To be safe. Move it more out of the electromagnetic field range. 
 As I see it. The speakers need to move away from the monitor either way. If that black box on the right side of your monitor is indeed a PC speaker with the green light on the bottom. You got electromagnetic field in play. Both the monitor and the speaker. 
Gobby

---

### Post by jsiei97 on 2008-07-15
> **deadgobby said:**
> I watch your vid and if that is your speaker right of the the monitor. Move the speaker away from the monitor. Your speakers has magnets and may cause electromagnetic field disturbance. So when you are playing music and the sound have static while you are moving your mouse around while clicking down. Because the electromagnetic fields comes into play. It stops when you no longer have the speaker play any sounds. Besides that is not good to place a speaker in close range to your monitor. You'll may burn out the monitor in no time quick. Yet, slowly watch the color of your monitor fad out to one side.  
 You can see/hear if that is the problem by moving the speaker out of range at one step at a time. Play music and do what you did to get the interference. Keep on moving the speaker away till it does it no more. To be safe. Move it more out of the electromagnetic field range. 
 As I see it. The speakers need to move away from the monitor either way. If that black box on the right side of your monitor is indeed a PC speaker with the green light on the bottom. You got electromagnetic field in play. Both the monitor and the speaker. 
Gobby

Thanks

but this was my first guess, and unfortunately not the problem.

I have tried to move the speakers away from the monitor, approximately 0.5 meters. (still the same)

I even got my self a "noise cancel filter" for the power-line, if the disturbance went over the power line (but still the same)

And if it was the magnetic field from the monitor, stopping alsa would not change anything???


Is it possible to kill the sound server, 
and have the application to talk directly to the kernel?  

BR
Johan

---

### Post by jsiei97 on 2008-07-15
I connected my normal stereo with a long cable and played with that one instead, just to verify that my computer-speakers are ok.

And unfortunately I got the same disturbance there as well, so I don't think it is a hardware problem.

BR
Johan

---

### Post by jsiei97 on 2008-07-17
This seems to be a tricky issue since no one seems to know what it is...


If I look at the problem in another way.

Do anyone has any good idea on what to check so I can zoom in on the problem?

Can I change the sound server? and use something else?
(I have seen some issues that points in the direction that this is not possible???)

BR
Johan

---

### Post by deadgobby on 2008-07-17
Well poop on a stick. It is some sort of interference going on. Do you get the same results if you use VLC or other music player? What sound card do you use? I have a Sound Blaster and I use head with two PV speakers and I cannot replicate the interference as you get. However I do not use audacious. I use VLC. 
Gobby

---

### Post by deadgobby on 2008-07-17
Oh here is a thought. I wounder if your Video card is causing the interference with the sound card.

---

### Post by jsiei97 on 2008-07-20
> **deadgobby said:**
> Well poop on a stick. It is some sort of interference going on. Do you get the same results if you use VLC or other music player? What sound card do you use? I have a Sound Blaster and I use head with two PV speakers and I cannot replicate the interference as you get. However I do not use audacious. I use VLC. 
Gobby

I installed vlc and the vlc-plugin-pulse 
(and made sure the vlc-plugin-alsa was not installed)

And I have not seen the disturbance for a while now... so I am kind off happy :popcorn:

So I figure this is some kind off audacious-bug??? 
Anyway thanks for the vlc tip :)

Thanks
Johan

---

### Post by deadgobby on 2008-07-22
Not a problem. I am happy that VLC is playing music with out any nasty play back.
Gobby

---

