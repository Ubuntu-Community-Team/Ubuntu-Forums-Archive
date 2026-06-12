---
title: "CalfjackHost Won't work when EXPORTING TO SESSION in ARDOUR"
date: 2010-09-18
forum: Multimedia Software
---

### Post by mas_sergio on 2010-09-18
Ok this is where I am stuck at! I configured Calf plugins to be audible in ardour on recordings meaning you can hear it fine. Now this is where the problem starts whenever I click "Export Session" those nice effects I took my time tweaking get somehow pushed out of the exported .wav file. So that means while playing the file in ardour I hear RECORDINGS + EFFECTS from CALF but when I export the EFFECTS ARE NO LONGER THERE(why?). I don't get any error messages either. I really love Calf and they're Delay plugin but it just wont work. None of them do. You can hear them live but it won't let me apply the effect onto a recorded audio file in Ardour. What's wrong? Please tell me there's a fix. ](*,)](*,)

---

### Post by cchhrriiss121212 on 2010-09-18
Are you using the plugins from within Ardour or do you connect them externally?

---

### Post by mas_sergio on 2010-09-18
Externally with Calf and Jack... i connect it to ardour and i hear it fine but when i click the export button those (effect) sounds won't export along with the file. That's where im lost. I can use the CALF plugins in the mixer but some require STEREO recordings with jack i can use calf plugins on mono recordings. It's more efficient for me thru the jack system wich allows me to use it on mono recordings than using it in the mixer(wich works stereo only for most CALF plugins). I perfer using it via jack becuase of this. I don't want to record in stereo the final mix down will be stereo. It's easier using jack for me Get what I mean? :/

---

### Post by cchhrriiss121212 on 2010-09-18
Yes, I use effects the same way through jack, it gives you more flexibilty, but it is a more complex way of doing things sometimes.

If your recording chain anything like this:
Capture>Ardour track>calf>master 

Your effects won't record, because they are not being recorded as a part of the wav for each track. When Ardour exports, it will just take all the info from each track, and not apply the calf effects you have in your chain. 

What you can do is record a final mix in real time using jack like this:
tracks>calf>Master>time machine

Or else apply effects before they are recorded to disk like this:
Capture>calf>Ardour track>Master

If that is not helpful then could you post how you are connecting everything together.

---

### Post by mas_sergio on 2010-09-19
well pretty much what im trying to do is use JACK's CALF plugins to record like to EDIT somethings that are already recorded.

*Example: Someone recorded vocals and now after I hear the play back I decide to add a Delay via CALF in JACK becuase if I do it via MIXER calf states it has to be STEREO and if i make a MONO recording stereo it will double the vocals (making them sound metalic and awful). I decide it would sound nice with a nice little delay from CALF via JACK wich allows me to do the effect whether it's mono or stereo recording but this effect won't export is where my problem is at.*

Get me now?

I'm not sure if you said it's impossible or if you posted a work around? I can't RECORD LIVE no way.. not vocals anyways. Vocal's have to get cleaned up and then waxed up. Theres alot of things that get done to artists vocals. A few examples, compression, EQ'ing, nosie removal... recording the EFFECT LIVE would be unwise as ur vocals will um yeah be altered. Let me explain it like this, if your going to clean a car, do you first whipe off all the dirt and such and then apply the wax to make it shine? Or do you wax it while its dirty? In music generes we have to CLEAN VOCALS then POLISH(or wax lol) them. If CALF won't work that way I'll try looking at a LADSPA plugin but I can't say I'm to fond of the other delay plugins I've seen so far. The Calf plug in has a great sound sucks to not use it(unless its on a stereo recording). Gave such a smooth sound to. :/


If you still need help seeing what I'm trying to do check my artist page or youtube page (higher quality) [COLOR="Blue"][http://www.myspace.com/massergio]("http://www.myspace.com/massergio")[/COLOR] and listen to the song "Cosquilla"-**_ HQ 480p link CLICK _**[here]("http://www.youtube.com/watch?v=LR_1UpUaKvg") then wait for after the chorus starts i start talking and u hear a delay... those kind of effects are normally mixed in AFTER my vocals are recorded onto HArd Disc... I'm not sure if you said it's imposible in jack + Ardour unless i do it live AS IM RECORDING (wich i tried as well before posting but failed somehow). I can't do it like that anyways cuz its one of those situations where u have to listen to the mix and see if the delay is appropriate for the final mixdown of the project. Whether or not my problem gets solved I'm always grateful you all took the time to read this, much love (non homo way of course) lol peace. 

:guitar:


[SIZE="1"]***I think a later version of Ardour is supposed to override this situation I'm having with the Ardour Mixer in the future but I'm not sure I read it somewhere that it won't do that Stereo/Mono only thing that it does in later versions.[/SIZE]

---

### Post by cchhrriiss121212 on 2010-09-19
I do understand what you are doing, but I should explain myself better as I did not suggest you record everything live, I was trying to explain how Ardour export works.

You see, when you export a session from Ardour it will take all the recorded data in one quick scan (ie non-realtime) and produce a final mix. The effects you are using have not been recorded so they are not included in this exported mix.

So how to get it right? Lets go with your example of a vocal track that needs delay:
In order to get the delay recorded, you need to take the signal from the pure vocal track that is in Ardour, route it through calf, and *then record it again* to a new track. This is what I mean by real time.  


But if you want a mono delay plugin, there are loads in jack rack/LAPSDA.

---

### Post by mas_sergio on 2010-09-25
ah, then i guess ladspa is the way to go here then. Thanks for your help Chris. I understand what you meant now.:KS :)

---

### Post by mas_sergio on 2010-10-01
I found a way to use it in the mixer. Normally when you record a mono recording and try to apply Calf's Vintage Delay plugin to it you get this error message in Ardour:

[SIZE="3"][I][B]"You attempted to add a plugin (Calf Vintage Delay).
The plugin has 2 inputs
but at the insertion point there are 
only 1 active signal streams.

This makes no sense - unless the plugin supports side-chain inputs. A future version of Ardour will
support this type of configuration." 
[ok][/B] [/I][/SIZE]

After you click "OK" the mixer dialog box disapears and your effect WILL NOT GET ADDED unless you do a stereo recording... I found a work around for this for mono recordings. I can't belive I solved my own problem so simply.

This may feel wierd doing but it works! Look for GVerb (you should have this if you downlaoded ubuntu studio repos) now add GVERB! Double click it(or right click it) in mixer and select Bypass/Deactivate. DONE! Now try adding the Calf Delay Plugin and it should work PERFECTLY in the mixer! I did a test and exported it. No errors to report. If you don't want to "bypass" the Gverb just put all settings to the far left and put the "DRY" setting to 0. This works. Calf Vintage now works in mono recordings (with stereo effects as well) using GVerb as a work around to adding mono support in Ardour. Check it out! It works. Can't belive it. Yay! :)


[SIZE="1"][B]Technical stuff:

for those who are interested in an explenation basically Calf uses stereo effects and needs a stereo recording. GVerb somehow (some way) makes a mono track STEREO for it's effect. By having Gverb and Calf Vintage Delay in 1 mixer channel you get that stereo track you need FORCED into the mono track enabling Calf Vintage delay to work IN FULL STEREO, even if Gverb is disabled/bypassed, go figgure. Just make sure you have "Stereo" selected under channels when you get to the export screen so that your applied Delay effects (if applied in stereo) are played back in stereo. =]
[/B][/SIZE]

---

