---
title: "I have lost all music playing capabilities in any program"
date: 2008-10-09
forum: Multimedia Software
---

### Post by Bryan P on 2008-10-09
I have been working on a rather fresh install of Ubuntu 8.04 on an IBM R51 Laptop. All has gone well until today when I lost the capability to play any mp3 music. I was using rhythmbox to listen to my mp3's yesterday and today rhythmbox does not play. 

This is not a sound card issue as I do have sound when on the internet and when watching movies from DVD. But when I press play in rhythmbox it just sits there and acts like it is going to play, but it will not. I have tried to remove and re-install rhythmbox which did not help. Thinking that it was a rhythmbox program bug I installed Amrok and Songbird, both of witch do the same thing, act like they are play but do not. I do not get any error messages when trying to play the mp3's and I have the required codecs to play mp3's. 

I have only been using Linux for 3 months now and have never had this problem before. 

Has any body else run into this problem or have any suggestions?

---

### Post by chmosbrook on 2008-10-09
Make sure you PCM mute is not engaged in the Volume control

---

### Post by Bryan P on 2008-10-09
Thanks, Chmosbrook
My problem isn't that it is muted, it is more that the music programs will not play as a function. I press play and nothing happens. The counter next to the play button does not start counting the time of play and the place marker showing the position in play will not move. This only happens when playing music files and I have no problem playing videos.

---

### Post by Interpreter on 2008-10-09
> **Bryan P said:**
> This is not a sound card issue as I do have sound when on the internet and when watching movies from DVD. But when I press play in rhythmbox it just sits there and acts like it is going to play, but it will not. 

Fear not, for it IS exactly what you think it is not, or  well..it's more of a selected-drivers-issue, tinker with the audio settings for abit (ALSA, autodetect,...) I'll post "proper" help after work (~9hours) or friday afternoon.

---

### Post by Bryan P on 2008-10-09
Thanks, Interpreter
I will look forward to that help. As an update, last night after monkeying around with this issue I shut down my laptop, something that I normaly do not do. Normaly I leave my laptop up and logon 100% of the time. With this in mind I have not shut down or rebooted my laptop for about a week and this morning I rebooted the laptop and all is working again. All my files play just fine. This is good news but I still do not know what caused the original issue. Does any body know of a bug within Ubuntu that causes this issue when a laptop is left up and running for extended periods of time??? The automatic updater has run in the last couple of days but no notification of "reboot required" was found after update.

---

### Post by Interpreter on 2008-10-09
Well it's basically related to that driver thing.
The sound GUI is badly implemented one might say.

Depending on what device you select for certain tasks you might end up "locking" all sounds that should come thru that device to it for the end of time or the next reboot err I mean ctrl+alt+backspace..trigger event sausage fest.

Even if you change it back to some other device.
The system then knows that you want the new setting to be used by default...but that doesnt really "unlock" the old device.
That's why I tend to use "tinker with it" instead of "look into it" or "rtfm" and the likes.
Aww bugger, bit awkward to explain that. My own knowledge is very limited and somewhat hazy at best.Sry.Cool that it worked out. Or..did it not yet totally fully awesomesauce fix it self there?


It has nothing to do with the update and all it's shizzle, fyi/for the case that you run into similar hassle soonish.

---

