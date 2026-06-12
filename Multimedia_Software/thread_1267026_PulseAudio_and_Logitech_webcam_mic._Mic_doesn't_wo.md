---
title: "PulseAudio and Logitech webcam mic. Mic doesn't work."
date: 2009-09-15
forum: Multimedia Software
---

### Post by Blackie_Chan on 2009-09-15
Hi

I have a logitech quickcam communicate STX (which has an inbuilt microphone). I've also installed the latest Skype 2.1 beta. Now, I'm trying to get the microphone to work but it isn't I need ideas on what I can do to fix the problem.

When I run pavucontrol, and watch my webcam mic's progress bar while talking to it, it moves, but I am not hearing what I'm saying coming out of the speaker. As a result when I use Skype, the mic does not pick up my voice.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=128686&stc=1&d=1253022930[/IMG] 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=128685&stc=1&d=1253022927[/IMG]

Thanks in advance.

---

### Post by Blackie_Chan on 2009-09-16
I have solved my problem. All I had to do is disable pulse audio's autospawn and then change my Skype sound settings. 

1. Disable autospawn. 
Open ***~/.pulse/client.conf*** with your favorite editor and add ***autospawn = no***

2. Stop pulse audio. 
In your terminal, run ***pulseaudio -k***

3. Run Skype and change audio settings:
[img]http://ubuntuforums.org/attachment.php?attachmentid=128839&stc=1&d=1253138632[/img]

4. After using Skype to make my long distance call, I just restart pulse audio
In your terminal, run ***pulseaudio -D***
After step 3, I had to run "Gnome Volume Control" and unmute the Master Playback control in Alsa mixer.

---

### Post by Zoey.Marie on 2009-09-18
I don't have skype, and my client.conf file was in /etc...

and I still can't get it to work. :(

---

### Post by Blackie_Chan on 2009-09-19
> **Zoey.Marie said:**
> I don't have skype, and my client.conf file was in /etc...

and I still can't get it to work. :(

If you create and add **~/.pulse/client.conf**, the autospawn setting will override the value in /etc/pulse.

---

### Post by Blackie_Chan on 2009-09-28
> **Zoey.Marie said:**
> I don't have skype, and my client.conf file was in /etc...

and I still can't get it to work. :(

What are you using the webcam mic for? How do you plan on using it? If I knew what you are using it for, I can see how the app works on my computer.

---

### Post by Zoey.Marie on 2009-09-28
Oops. I suppose I should've updated this when I finally got it to work...

I'm not sure how I did, but I did. After I changed the auto-spawn thing, I just tinkered around with sound settings (under system>preferences>sound) and then played around in the programs that I was trying to get it to work in (Ardour, JACK, Audacity, Pure Data, ...) and had to find the specific settings that worked for it. I had to change all the "default" values in the input device field to the "hw:" whatever thing that it is in, and then I needed to make sure that I wasn't running any sound program with a sample rate of 16000Hz (or else it wouldn't work).

I'm pretty sure that's all I did. <3

---

