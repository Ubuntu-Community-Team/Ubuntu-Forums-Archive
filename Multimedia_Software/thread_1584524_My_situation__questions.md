---
title: "My situation / questions"
date: 2010-09-29
forum: Multimedia Software
---

### Post by Colo2 on 2010-09-29
Hello. I have a few questions.

Last night, I hooked a studio PC up to the internet, and installed crunchbang (which apparently is really closely related to ubuntu.) I installed Ardour and jackd. At that point everything seemed to be ok. My dad's 2 x Delta 1010s were detected within ALSA (aplay -l).

I ran jack, jack started fine, I played music, it all seemed to be running ok. **However I couldn't test if the sound was working,** because all the equiptment to make these sound cards work is in the studio which isn't connected to the internet. So I was just going by what my computer was telling me. No errors, all seemed fine.

I went to bed all happy, so this morning I decided to take it down to the studio, hook it all up and try it.

There was no sound.
**However! **I am no sound engineer. That's my dad's business. The mixing desk seems to have loads of "mute" lights lit up on it, but there's no mute button on the desk. There's a possibility that I don't know how to make the music play through his studio equipment. So for that, I'll need to wait till he gets home. 

Then it struck me, someone told me that Delta 1010s are muted by default, so I brought the PC back into the house, hooked it back up to the internet and download envy24control. in ALSA-TOOLS-GUI. I un-muted all of the controls and took it back into the studio. I played music. The music (obviously) wasn't making any noise through my dad's equipment, but the equalizers on envy24control weren't moving either. It's as if it doesn't know that there's any sound playing.

Another thing which I noticed, which puzzled me: I don't know about Linux, but on Windows, if you hit one backspace too many in an input box, it will play a system sound if the sound card is detected, and a motherboard beep if it's not.

This Linux machine does the motherboard beep. (although it may not be capable of playing a system sound, I'm not sure.)

Any ideas of what could be going on here? If Envy24control is giving a false reading, what APP should I use? and why is jack refusing to connect?

My dad wants to go back to Windows, and I'm doing everything in my power to make him feel comfortable with Linux. 

Thanks :)

Tom.

---

### Post by cchhrriiss121212 on 2010-09-29
Hi again,
To unmute you need to open envy24, and then go to the **analogue volume** tab.
ADC means inputs and DAC means outputs.

Once you have done that I can explain how to set up jack if you post what the message window says.

---

### Post by Colo2 on 2010-09-29
Hey

I'll nip out to the studio and give that a shot. Thanks for the reply. I'll post back asap

---

### Post by Colo2 on 2010-09-29
Hello
If you are referring to this:

[IMG]http://nielsmayer.com/envy24control/Mudita24-102-Analog-Volume.png[/IMG]

I don't have that, mine looks more like this:

[IMG]http://alsa.cybermirror.org/others/envy24control/envy24_3.jpg[/IMG]

I found this online though:

> The Delta 1010 has no analog level control (apart from the +4/-10dBu switches on the analog ins and outs), so you need to set the input level in whatever external gear is plugged into the 1010's input.

So what now? :(

---

### Post by cchhrriiss121212 on 2010-09-29
Is your card a Delta 1010LT, or just a 1010?
Also I think you need to have the breakout box attached to set them up properly.

---

### Post by Colo2 on 2010-09-29
Hey

Its 2 x Delta 1010s.

Not "LT", just 1010

and they are attached to the breakouts.

---

### Post by Colo2 on 2010-09-29
Just been over to the studio to talk to my dad. When I was trying this morning, the mixing desk was muted. 

So, that might explain why no sound was working.

However there was still no life on the equalizer in envy24control.

and jack still refuses to start.

---

### Post by cchhrriiss121212 on 2010-09-29
According to another thread [here]("http://ardour.org/node/2444"), the 1010 should show up with analogue volume controls.
Do you see anything if you use alsamixer from a terminal?

---

### Post by Colo2 on 2010-09-29
I gave alsamixer a once-over too. Nothing of interest in there. (I dont think) (didn't run it from the terminal, it was in the menu)

---

### Post by cchhrriiss121212 on 2010-09-30
I found that quote you posted from the Ardour forums, and a few others that say the same thing about having no software volume control. But it should still work OK.
How are you testing the sound, with input or output?
Like I said earlier, if you want me to help you with jack, then post what the message window says.

---

### Post by Colo2 on 2010-09-30
Hey

Thank you for the reply. 

I'll go out to the studio over lunch time and re-test the audio. I'll also get a hold of the Jack error message.

Thank you for bearing with me :)

---

### Post by cchhrriiss121212 on 2010-09-30
> **Colo2 said:**
> 
Thank you for bearing with me :)
I'm surprised you are still here. I'm not sure that your Dad will be convinced by all this fiddling around though. If he really wants to stick with Windows you should accept that, as forcing Linux on people is not the way to go even if you think it is better.

You should also tell him that using jack might take a few weeks to get used to, as you will find out when you set it up.

---

### Post by Colo2 on 2010-09-30
> **cchhrriiss121212 said:**
> I'm surprised you are still here. I'm not sure that your Dad will be convinced by all this fiddling around though. If he really wants to stick with Windows you should accept that, as forcing Linux on people is not the way to go even if you think it is better.

You should also tell him that using jack might take a few weeks to get used to, as you will find out when you set it up.

He has a Windows drive too, which he is using at the moment. Every now and then I go in there and boot from the Linux drive and fiddle about. He says he's willing to use it if he gets it all set up and in a working state. I think he likes the idea of using Linux, but claims that "you need to be a bloody scientist to operate it."

If I can get it all up and going for him, he'll use it. If not, he can always boot from his Windows drive ;)

---

### Post by Colo2 on 2010-09-30
Right. I just went down to the studio, turned everything on and played some music. Here's what happened:

I put music on with Rhythmbox. The music played through the speakers (YAY.) However! No applications seem to be controlling it.

Eg: the volume control on Rhythmbox doesn't control the volume coming out of the speakers, if I mute rhythmbox, the music still comes out. ALSAMIXER controls don't make any difference to the sound and neither does envy24control. Nothing seems to effects the sound volume.

Any ideas as to why this is?

---

### Post by cchhrriiss121212 on 2010-09-30
Maybe something to do with the lack of volume control thing from envy, but applications should be able to mute themselves as it happens before sound has reached the card. 
Do other apps like vlc behave the same way?

---

### Post by Colo2 on 2010-09-30
Hey.

I'll need to check that out tomorrow, studio is all locked up now. 
I don't know your timezone, but It's 9 PM in France. Again, thanks for hanging with me this whole time. :)

Tom

---

### Post by Colo2 on 2010-10-03
Hello again!
sorry for the massive delay

I've been to check it.

Jack starts just fine, as long as no other apps are using the ALSA drivers!
Ryhthmbox runs just fine when Jack is running, (aka through jack?) 
VLC refuses to output any sound if Jack is running?

I guess I need a way to force all ALSA apps to run through jack?

Thanks :)

Tom

---

### Post by cchhrriiss121212 on 2010-10-03
Hi again,
Rhythmbox should not be able to do that as it has no jack plugin AFAIK. But you can get VLC to use jack like this with a jack plugin which is in the repos. If I want to hear some other music while recording, I use alsaplayer. Beyond that I see no reason to get everything ALSA running through jack, it is just more configuration you don't need to deal with (but ALSA through jack is possible).

Other stuff you may want to setup:
rt kernel -  the latest stable is 2.6.31.12-rt21 which is what I use. Get it from [here]("http://www.pengutronix.de/software/linux-rt/debian_en.html"). It will give better performance for audio.
Patchage is a great program that gives a cleaner version of the jack connection window.

---

### Post by Yellow Pasque on 2010-10-03
See the /etc/asound.conf I posted in your other thread if you want to run alsa apps through jack.

---

### Post by Colo2 on 2010-10-04
Hey
Thanks for your reply.
I'll download the .debs and take them over. If they require dependencies, I'll bring the computer in one evening.

Now, My dad has informed me that he needs MIDI. I haven't got a clue what that is, but whatever it is, he needs it. Does Crunchbang/Ubuntu/Ardour/Jack support midi? is it set up? if not, how do I do it?

Thanks :)

Tom

---

### Post by cchhrriiss121212 on 2010-10-04
MIDI is supported with jack and the ALSA MIDI driver, if you use patchage you will see MIDI connections there as green boxes, blue boxes are audio. It should not require any setup.
Ardour does not have MIDI support in the regular version so I would recommend Qtractor, which does everything Ardour does plus MIDI.

---

