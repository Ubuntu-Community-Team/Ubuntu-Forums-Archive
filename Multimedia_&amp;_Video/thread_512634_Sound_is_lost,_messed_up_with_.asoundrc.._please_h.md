---
title: "Sound is lost, messed up with .asoundrc.. please help"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by sunshine12 on 2007-07-29
I have Soundcard from C-Media, CMI8738 chip.
It is detected by ubuntu and working, but not separate output from all 4.1 channels.
So, I searched sites to rectify that problem. and changed "**.asoundrc**" file in the home directory.

and my sound is lost, I can't hear anything from my speaker. I removed whatever I have written in .asoundrc file but problem persists... then removed it and created again with the following text.....

pcm.cmipci {
           type hw
           card 0
        }

        ctl.cmipci {
           type hw
           card 0
        }



So, In effort to make better sound output, I messed up all the things and lost the sound..
help me to get back sound.. 

Thanks..

---

### Post by Chymera on 2007-07-29
I have the exact same sound card and have the exact same problem (5.1 card but only 4.0 output, in stereo mode). There are a lot of wannabe guides as to how you might get it working, most of them including that .asoundrc stunt. 

DONT TRY THEM OUT! I already did, and one of them messed my computer so badly that i had to reinstall ubuntu. You problem can, luckily, be fixed quite fast. Delete the .asoundrc file altogether (if you have one in home and another one in home/<yourusername> delete them both), and if you have also played around with your audio mixer, whilst following some smart-a** instructions, make sure all IEC958 switches (under edit->pref) are unchecked.

I have tried to get that working for about 1 month now, and as far as i know its impossible. However if you want to risk getting in a worse predicament, just to get your ubuntu to recognise a CMI8738 properly, and find out smth helpful pls pm me about it :).

---

### Post by sunshine12 on 2007-07-29
thanks Chymera for replying,

Deleting  .asoundrc file didn't solve my problem. And yes you are right I have changed setting with audio mixer, and unchecked that IEC958 switches, but the problem remains.

Sound is still absent.... what should I do now??
Thanks

---

### Post by sunshine12 on 2007-07-29
there is another file named..   .asoundrc.asoundconf        whta is that?  should I delete that too?
please help, otherwise I have to reinstall ubuntu.
thanks

---

### Post by sunshine12 on 2007-07-29
Ok, solved the problem and somehow suceed to get back the sound.

removed .asoundrc and .asooundrc.asoundconf

then,

asoundconf list
asoundconf set-default-card CMI8738

Solved the problem..
Thanks Chymera..

---

### Post by Chymera on 2007-07-30
np, did you just get your sound back or did you even get it running properly (by that i mean proper 4.1 , with separate channels for each speaker)

---

### Post by sunshine12 on 2007-07-31
> **Chymera said:**
> np, did you just get your sound back or did you even get it running properly (by that i mean proper 4.1 , with separate channels for each speaker)

Just get back the sound.. 
Not proper 4.1, with separate channels for each speaker, and I am not trying it now until I find the reliable and working solution.
If you get the solution then please post it, so I can use it. If I will get I'll post it to all.
Thanks.

---

