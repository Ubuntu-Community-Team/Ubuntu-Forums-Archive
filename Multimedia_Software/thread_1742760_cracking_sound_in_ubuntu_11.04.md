---
title: "cracking sound in ubuntu 11.04"
date: 2011-04-29
forum: Multimedia Software
---

### Post by simbaman on 2011-04-29
i have been experiencing crackling sound ever since i upgraded to ubuntu 10.04. the problem is persistent after i got ubuntu 11.04. in addition, there is no sound in the headphones. i got these problems simultaneously (after i upgraded to 10.04). are these issues related to each other?

---

### Post by simbaman on 2011-04-29
i meant "crackling sound" not "cracking" :)

---

### Post by benmandude on 2011-04-29
I have been having a similar issue off and on since 10.10. Certain programs would produce a crackling sound where others do not. After upgrading to 11.04 I tried playing some avi in VLC with a lot of crackling tried to other players and experienced the same but to a lesser degree. This is so frustrating, I feel we have a similar issue and hope we can get some answers.

---

### Post by Julian Luna on 2011-04-30
I have the same problem, it appears to be the whole sound, I thought it was only Rythmbox but it's the whole sound... it's crackling, clipping, whatever, it really annoys me and is fixed after I restart many times the rythmbox, which makes no sense to me... and is fixed by a little little time, then it comes back. Should I uninstall my sound drivers and install other? Which one is updated to Natty Narwhal?

---

### Post by lidex on 2011-04-30
> **simbaman said:**
> i have been experiencing crackling sound ever since i upgraded to ubuntu 10.04. the problem is persistent after i got ubuntu 11.04. in addition, there is no sound in the headphones. i got these problems simultaneously (after i upgraded to 10.04). are these issues related to each other?

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by |{urse on 2011-04-30
Oh, that's just the sound of tux's heart breaking every time unity loads. (jk)

---

### Post by simbaman on 2011-05-01
thank you lidex! here is the link:
 [http://www.alsa-project.org/db/?f=8b5519ca896436503000aac681523a4443bc55d7](http://www.alsa-project.org/db/?f=8b5519ca896436503000aac681523a4443bc55d7)

---

### Post by simbaman on 2011-05-01
thank you lidex! here is the link:
 [http://www.alsa-project.org/db/?f=8b5519ca896436503000aac681523a4443bc55d7](http://www.alsa-project.org/db/?f=8b5519ca896436503000aac681523a4443bc55d7)

---

### Post by lidex on 2011-05-01
Not a good codec to get info on...what is your setting for profile in 'Sound Preferences' on the hardware tab?

---

### Post by simbaman on 2011-05-02
analog stereo duplex

---

### Post by tedrogers on 2011-05-09
Same problem here. Crackling in VLC but fine in Movie Player.

---

### Post by poliltimmy on 2011-05-09
I have the same problem. Just wanted to weigh in. Set output to ALSA in VLC. It plays for awhile with no crackle then crashes.

---

### Post by tedrogers on 2011-05-09
Fixed, I think:

Try checking the KEEP AUDIO LEVEL BETWEEN SESSIONS option and set output to JACK AUDIO OUTPUT then SAVE.

Let me know if it works. Seems stable for me so far.

Must have been an old setting not overwritten during update, I guess.

---

### Post by poliltimmy on 2011-05-09
> **tedrogers said:**
> Fixed, I think:

Try checking the KEEP AUDIO LEVEL BETWEEN SESSIONS option and set output to JACK AUDIO OUTPUT then SAVE.

Let me know if it works. Seems stable for me so far.

Must have been an old setting not overwritten during update, I guess.

OK I feel totally stupid now. I do not know where these settings reside.

---

### Post by tedrogers on 2011-05-09
TOOLS > PREFERENCES menu at the very top of the screen on the grey bar

...or

Press CTRL+P together.

---

### Post by poliltimmy on 2011-05-09
I was right I was being stupid! Found the keep audio  level between sessions. I reset defaults and then checked it and saved. But there is no Jack listed in output. Version VLC 1.1.9.

---

### Post by tedrogers on 2011-05-09
Well to be fair ALSA was okay for me too.

Has it solved your problem then? Try updating too.

---

### Post by poliltimmy on 2011-05-09
I appreciate your patience. Listening to the 3rd song in a row with no crashes so far. I needed the additional step of changing the Device to my card analog setting as opposed to 'default'. So far so good. I did however have to disable pulse in every distro since it's inception. Do you know if these commands still works to kill it if I run into problems later? Thanks for all your help!!!!!!!

sudo chmod -x /usr/bin/pulseaudio
killall pulseaudio

---

### Post by tedrogers on 2011-05-09
> **poliltimmy said:**
> I appreciate your patience. Listening to the 3rd song in a row with no crashes so far. I needed the additional step of changing the Device to my card analog setting as opposed to 'default'. So far so good. I did however have to disable pulse in every distro since it's inception. Do you know if these commands still works to kill it if I run into problems later? Thanks for all your help!!!!!!!

sudo chmod -x /usr/bin/pulseaudio
killall pulseaudio

You're going beyond my immediate knowledge there, but I guess if it has worked in the past it should work again.

However, you should have a permanent fix and it's troubling that you have had to disable PulseAudio since all that time. I would delve deeper if you are still getting so many problems with Pulse.

Anyway, glad the VLC option fix is working for you. I'm having no trouble at all now :).

---

### Post by lidex on 2011-05-10
If you kill pulse audio, it should actually respawn. See this link for method to turn on and off:
[http://www.linuxplanet.com/linuxplanet/tutorials/7130/2/](http://www.linuxplanet.com/linuxplanet/tutorials/7130/2/)

---

### Post by kaonashigr on 2011-05-13
> **tedrogers said:**
> Fixed, I think:

Try checking the KEEP AUDIO LEVEL BETWEEN SESSIONS option and set output to JACK AUDIO OUTPUT then SAVE.

Let me know if it works. Seems stable for me so far.

Must have been an old setting not overwritten during update, I guess.

i never thought about it... thanks a lot!!!! 
(movie time now! haha! :popcorn: )

---

