---
title: "[SOLVED] Microphone not working. Flat outta ideas."
date: 2008-11-02
forum: Multimedia Software
---

### Post by Bios Element on 2008-11-02
So I've got Ubuntu 8.10 working with Pulseaudio about 100%. But there's one problem, I can't use my mic. Now I've got a headset and speakers configured and working just fine but for some reason I can't get the speakers to record. It sees them, But it can't actually register any input.

I've spent several hours trying with alsamixer and stuff and I'm just outta ideas so if anyone could help out and lemme know what I'm not doing (Or doing wrong) That'd be helpful. It's really important i get this up and running because I have to use it for a business meeting soon. >.>

---

### Post by Bios Element on 2008-11-03
Bump, I find it hard to believe no one has any idea what's up with this. Problem seems to be related to Alsa, Not Pulseaudio. >.>

---

### Post by tiggsy on 2008-11-04
Give us a clue? Seems no solution here

---

### Post by subterrific on 2008-11-04
I have this problem too, output works fine, but input doesn't work and even causes some applications to use 100% cpu when trying to record. The only thing I've found that works so far is to kill pulseaudio, then everything works perfectly. If anyone can shed some light on this, I'd rather have pulseaudio properly configured than just kill it.

---

### Post by markbuntu on 2008-11-04
Pulseaudio has probably defaulted to your usb device. You can change that with pavucontrol, the Pulse Audio Volume Control. More on getting pulseaudio and everything else to do with sound working properly here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by riyasmp on 2008-11-04
guys i am having a problem with my skype and 8 10.

i was using 8 04 so far and using skype on it was alright. to make skype work on 8 04 i had to go to master volume>options>input source and change the input source from mike to line and put it back to mike. Interestingly skype failed to work if i don do it. I had to do it only once the ubuntu starts up. If i din do it callee couldnt hear my voice but I could hear them. anyway i was OK with that.

when i upgraded to 8 10 the problem was different. I was not able to make a call at all. it started giving me the error message "problem with audio play back" when ever i call anyone. i went sound devices and played with input output source and got it right with option "pulse" for input source, output source and ringing.

now i am able to make calls but the callee cannot hear my sound. I applied the trick i used for 8 04 but its not working. i am not getting the playback message when i call "echo"

i tried recording sound on sound recorder but its not recording instead it hangs whenever i try recording my voice. But on audacity i am able to record my voice and play it without any problem.

The sound device on master volume is set for HDA intel Alsa mixer. i have played with other options as well but its not working.

guys i am not a computer engineer and if anyone can give me some input how to get around it in a simpler way without using computer jargons it would be a great help.

Thanks in advance

---

### Post by TeoK on 2008-11-04
How is it exactly "solved" thread?

my mic doesnt work in 8.10.
it was working few days ago with 8.04

when I try to record something on youtube (in firefox 3) - nothing happens - neither mic nor my webcam are recognized by flash 10.

the only way to record is to do it in Flock ( which still uses flash 9) and kill pulseaudio prior to that.

mehtinks ibex was rushed.

---

### Post by tpapastylianou on 2008-11-26
I've had the mic not working problem with my alienware m9700 laptop for about 2 years, read every single forum post in every single forum out there, lots of suggestions, but nothing worked. In the end I stumbled accidentally on a solution.

Go to alsamixer from the console (not the gnome gui one), and play around with all the settings. if I remember correctly, the magic combo that immediately produced sound from my mic for me was a combo between surround and vrefout. (specifically, switched surround from shared to independent, and vrefout to 3.7)

the reason it's important to do it in the console version, is that the gui version doesn't present you with all the options. (for instance, vrefout only had 2 values to choose from, neither of which worked, wereas alsamixer had extra ones to choose from, which did the trick.)

Finally, after 2 years, I'm using skype on linux and don't have to boot into XP just to talk :)

---

### Post by whistlerspa on 2008-12-22
My Mike works but not when I try to use it with Skype - Ubuntu 8.04 64bit

---

