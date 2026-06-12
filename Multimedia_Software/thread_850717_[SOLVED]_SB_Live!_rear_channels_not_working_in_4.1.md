---
title: "[SOLVED] SB Live! rear channels not working in 4.1"
date: 2008-07-05
forum: Multimedia Software
---

### Post by timzak on 2008-07-05
Hi,

I have an SB Live! with a 4.1 speaker system.  In Gutsy I had the rear speakers working fine for mp3 and ogg music files.  Not playing "surround" just playing 4 separate channels.

Now in Hardy, I cannot get rear channels working in mp3 and ogg music files.

However, this is very weird:  when I log into Hardy, there is a system sound when the login window pops up that sounds like bongos.  This sound plays in the rear channels!  But I cannot get any other sounds to play in the rear.  Frankly, I cannot understand why this one sound plays but no others do in the rear.

Any ideas?

Thanks in advance.

---

### Post by BLTicklemonster on 2008-07-05
I have 5.1 speakers, and it seems like every version of ubuntu changes how I can get all the speakers to play. Right now I have pcm, wave, wave center, wave lfe, wave surround added. Hope that helps. I really wish there were a simpler way to do this other than spending half an hour playing around hunting and pecking. Seems like audio is relegated to the back of the list of "user friendly".

---

### Post by timzak on 2008-07-06
Thanks for the reply.  I think my problem might go beyond GUI configuration.  I say this because I went through the whole shebang and enabled every option in the Alsa mixer settings, and put the volume all the way up.  

Since the Ubuntu bongos play in the rear channels (does anyone know where this sound file is located?), I think I enabled what I needed to.  But for some reason, my music is not playing through the rears.  I have a feeling it's related to PulseAudio, and might need some configuration file editing.  I'm just not smart enough to figure it out on my own.

Any other ideas out there?

---

### Post by BLTicklemonster on 2008-07-06
I never could get pulse audio to work, so I removed it. Seems like a waste of time to me.

---

### Post by timzak on 2008-07-07
Bump!

Any other ideas?  How can I get the rear channels working with my music files?  Why does it only work with the bongo sound at login window?

Thanks.

---

### Post by wolfen69 on 2008-07-07
see [this]("http://ubuntuforums.org/showpost.php?p=4835638&postcount=4"). and btw, i believe the subwoofer does not count as a channel.

---

### Post by timzak on 2008-07-07
> **wolfen69 said:**
> see [this]("http://ubuntuforums.org/showpost.php?p=4835638&postcount=4"). and btw, i believe the subwoofer does not count as a channel.

Thank you.  I'll try that out this evening and see if it helps.  By the way, here is the speaker system I am using:

[http://www.3dsoundsurge.com/reviews/fps2000/fps2000.html](http://www.3dsoundsurge.com/reviews/fps2000/fps2000.html)

I'm not sure if it is technically 4.1 or not, but they refer to it as 4.1.

---

### Post by Shazaam on 2008-07-07
> **timzak said:**
> I say this because I went through the whole shebang and enabled every option in the Alsa mixer settings, and put the volume all the way up. 

When you say you enabled everything in the "Alsa mixer settings" did you run 
```
alsamixer
```
in terminal?
The reason I ask is that there are a lot of settings that can be enabled for the SoundBlaster Live! card through the terminal. If you see a setting with a MM underneath it means its muted/disabled. Highlight it and press your M key on your keyboard to un-mute/enable (it will turn into 00).

---

### Post by timzak on 2008-07-07
> **Shazaam said:**
> When you say you enabled everything in the "Alsa mixer settings" did you run 
```
alsamixer
```
in terminal?
The reason I ask is that there are a lot of settings that can be enabled for the SoundBlaster Live! card through the terminal. If you see a setting with a MM underneath it means its muted/disabled. Highlight it and press your M key on your keyboard to un-mute/enable (it will turn into 00).

I used the GUI, not terminal (right-click speaker icon and select preferences).  There are literally close to 100 settings in the GUI, so I am guessing it is the same as alsamixer, but I will check it out tonight.  Thank you.  Also, since I am hearing the login bongos through the rear channels, I am guessing that the rear channels are on, just something else is keeping them from working after I log in.

---

### Post by BLTicklemonster on 2008-07-07
> **Shazaam said:**
> there are a lot of settings that can be enabled for the SoundBlaster Live! card through the terminal. If you see a setting with a MM underneath it means its muted/disabled. Highlight it and press your M key on your keyboard to un-mute/enable (it will turn into 00).

??? Where would one find documentation on such a wonderous thing?

---

### Post by timzak on 2008-07-10
> **wolfen69 said:**
> see [this]("http://ubuntuforums.org/showpost.php?p=4835638&postcount=4"). and btw, i believe the subwoofer does not count as a channel.

Sorry it took me so long to get to this...not a high priority right now.  But I finally tried the suggestion in the link you posted...and it worked!  Rear channels now work as they did in Gutsy.

Thank you very much.:)

---

### Post by BLTicklemonster on 2008-12-26
Sorry to drag this back up again, but I'm on a fresh install of Hardy, and even that doesn't help any more. No matter what I do, I can't get sound from my rear speakers.

---

