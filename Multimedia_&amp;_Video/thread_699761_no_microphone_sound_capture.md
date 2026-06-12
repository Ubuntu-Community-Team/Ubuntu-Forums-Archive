---
title: "no microphone sound capture"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by kaiju on 2008-02-17
i've searched allover the forums and google too, but nothing i've tried had any results: i just can't get the sound recording through the microphone to work.
i do get some sound from the microphone, but it's awfully silent and it won't get louder even though i've enabled everything that looked like microphone or capture from gnome-volume-control and adjusted all the volume levels to maximum.

since the very same microphone is performing well on another gutsy install, i'm sure this has to do with the sound card (intel onboard with c-media chipset), for which volume-control lists the following devices:
0: intel ich5 (alsa mixer)
1: c-media electronics cmi9761a+ (oss mixer)

i've found that the volume level increases a lot when the jack is only plugged in halfway (but of course it's hard to keep the jack plugged in halfway, and this makes the recording very noisy, too).
gnome's sound recorder is also giving me an overly meaningful message "Your audio capture settings are invalid. Please correct them in the Multimedia settings"

any ideas, folks?

---

### Post by stooshbunutu on 2008-02-18
The fact that it works best when the microphone is only half way plugged in seems to suggest that there is a problem with the actual connection rather than the computer software. As the microphone works well on another computer then it must be that there is a problem with your microphone jack on your computer, I suggest you borrow a microphone off a friend (if not you can get one from poundland - it actually works quite well) to see if you can get any microphone working on your pc. Also try cleaning your microphone port, blow into it or wipe it with a cloth or cotton bud or something. I had a problem similar once with my headphones,

Hope this helps :)

---

### Post by kaiju on 2008-02-18
thanks for your advice.
the problem is that i have two microphone ports, and it's the same situation, no matter which one i plug the jack into.
i'm thinking that the connection between the mono microphone and the stereo soundcard is somewhere not handled properly, so it must be a hardware thing i guess.

---

### Post by NickD-NLUG on 2008-03-13
Hey Kaiju, are you still seeing this issue?  I've got the same card, and my microphone doesn't work either.  I was wondering what you did to solve the problem....

---

### Post by kaiju on 2008-03-25
> **NickD-NLUG said:**
> Hey Kaiju, are you still seeing this issue?  I've got the same card, and my microphone doesn't work either.  I was wondering what you did to solve the problem....

well i've temporarily given up on using the microphone. i was thinking of switching around left, right and ground through another jack and some cable, but then i was too lazy to do that :p

did you in the meantime manage to solve the issue?

---

### Post by riyasmp on 2008-03-30
guys i  have the same problem:( i using ubuntu 7 10 on my sony vaio vgn fs285b laptop. when i installed skype recently my mic was not working ie, it was not recording the voice. i tested my sound system and was found that the sound capture is not working. ALSA- advanced linux sound architecture is the one shown against the sound capture in sound preferences.

when i test that the following message appears 

Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

i took the sound recorder and tested if i can record something.but again no sound when i am playing it back but the cursor moves as it is playing something.

my sound system is working fine on windows and i can chat with mic

can anyone help please, thanks in advance

---

### Post by riyasmp on 2008-03-30
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/18476](https://answers.launchpad.net/ubuntu/+question/18476) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				one of the forums has helped me really

my recording was not working properly and it got solved when qarecord was installed

these are the commands that u have to put in terminal

sudo apt-get update

sudo apt-get install qarecord

once qa record is installed i think recording will be alright and u will be able to use skype:)

---

### Post by adster101 on 2008-03-31
@riyasmp - I installed qarecord but still no luck.

What are your other settings? 

This headset works on Win XP so it must be the set up on my laptop.

What ALSA setting do you have?

---

### Post by riyasmp on 2008-04-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/37736](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/37736) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **adster101 said:**
> @riyasmp - I installed qarecord but still no luck.

What are your other settings? 

This headset works on Win XP so it must be the set up on my laptop.

What ALSA setting do you have?

Hi adster

I was about to make another post here on the same topic. My sound system was working fine when i installed qarecord and then stoped recording when i restarted the computer. I couldnt find any fix for it yet but there is a way to make recording work each and every time u restart ur compueter. pls read the first post 

on the link [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/37736](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/37736)

. changing mic to front mic and back to mic makes it work.lol sounds silly but it works.

pls let me know how did u go with that

---

### Post by adster101 on 2008-04-05
I found the problem. 

I open Alsa Mixer (by double clicking the system tray panel on my desktop) and then going to Edit > Preferences. I ticked every option and then noticed that my line-in and mic in channels were switched off (muted). As soon as I switched them on and adjusted the levels it all works! 

So I guess no bugs or anything just turning on the line-in channel did the trick!

Have to be careful and turn off the PC Speaker tho, otherwise all is good.

There is another bug that I get that I only get sound out of one speaker until I adjust the volume. Then the right speaker comes on as if by magic.

Maybe I should report that or see if it has already been reported.

Thanks!

---

### Post by NickD-NLUG on 2008-05-21
> **adster101 said:**
> I found the problem. 

I open Alsa Mixer (by double clicking the system tray panel on my desktop) and then going to Edit > Preferences. I ticked every option and then noticed that my line-in and mic in channels were switched off (muted). As soon as I switched them on and adjusted the levels it all works! 


Thanks for this, I double checked all the AlsaMixer settings, and its now picking up my voice very faintly.  I suspect I now need to invest in a half decent microphone ;)

---

