---
title: "M-audio fast track usb help"
date: 2010-01-07
forum: Multimedia Software
---

### Post by punkdrummer09 on 2010-01-07
Hello. I am trying to use Audacity to record some music, but I need help on getting my M-Audio Fast Track USB set up correctly. For some reason, I can only record in stereo and not in mono. If anyone has this working properly, any help would greatly be appreciated. Thank you in advance.

-Eric

---

### Post by JC Cheloven on 2010-01-22
Hi Eric,
To be sure, we are talking about [this card]("http://www.m-audio.com/products/en_us/FastTrack.html"), right?

I usually use Traverso and didn't have any problem recording in mono with this card. I only had to choose that option for the armed track(s). 

I guess the problem could be on how you set up audacity. Were you able to record in mono with another soundcard? 

What's your setup while recording (a condenser mic + guitar, or only an instrument ...), and what do you obtain exactly (a stereo wave with silence on the right channel... ??)

---

### Post by punkdrummer09 on 2010-01-22
Yes, well it's not that exact one, but I'm pretty sure they're the same. Here's a link to the actual one: [http://www.google.com/products/catalog?hl=en&source=hp&q=m-audio+fast+track+usb&um=1&ie=UTF-8&cid=2417465105404359933&ei=HOhZS8L9MYGYtgejr6CkAg&sa=X&oi=product_catalog_result&ct=result&resnum=3&ved=0CCwQ8wIwAg#ps-sellers](http://www.google.com/products/catalog?hl=en&source=hp&q=m-audio+fast+track+usb&um=1&ie=UTF-8&cid=2417465105404359933&ei=HOhZS8L9MYGYtgejr6CkAg&sa=X&oi=product_catalog_result&ct=result&resnum=3&ved=0CCwQ8wIwAg#ps-sellers)


No, I haven't tried recording with another sound card. My setup is just a guitar. In the Audacity preferences, I change the device to the Fast Track, and the channel to mono, but when I try recording, it doesn't record any sound. When I record in stereo, it's only the right channel that works. When I switch from mono to stereo, I make sure I switch the setting on the Fast Track too.

---

### Post by JC Cheloven on 2010-01-23
Well, I'm almost sure that there is only a problem with your software settings, not with the hardware. 

When your software records in mono, typically it grabs only one of the channels, be the right one or the left one (usually you can choose whithin the program which one you want). Looking at the images [here]("http://www.accentmusic.com/includes/view_image.php5?imgd=bjMKXnrw2&imgProdID=72243"), it seems clear that the guitar input goes thru the right channel of your card. Your audacity is surely configured by default to grab the left channel in mono. That way everything is coherent. Simply find where to tell audacity to record from the right channel in mono (sorry I don't use Audacity, never worked fine for me).

In order to discard the card (he he, some poetry here) as the source or your problem, you could test with some other program, such as mhwaveedit, traverso, sweep,... even ardour ...   Let us know how was it ;-)

---

### Post by punkdrummer09 on 2010-01-23
Ok thanks. I'll try to find that out. So I just downloaded Traverso, but it still doesn't work? I don't know if I'm doing something wrong? I attached 2 attachments. The first one during recording, and the second one after. I still can't hear anything..

---

### Post by JC Cheloven on 2010-01-23
Hi Eric, I'm quite experienced with traverso, so I have now better chances to go deeper into your problem:

I see what I'd expect: it can be appreciated in both images that your guitar goes through the right channel. You should hear at least the right channel at playback, though. Try one or more of the following:

- Start by un-arming the track (shouldn't hurt but you don't need it armed). Place the mouse anywhere over the track and press A shortly.

- Place the mouse anywhere over the clip, press-and-keep the G key and move the mouse towards the top of the screen (without pressing any button). This way you adjust the gain of the clip. It seems to have very little volume. 

- The driver seems to be ok (seen at the bottom left corner), but there may be a silly problem: Click in that corner; there is an 'alsa device' drop menu in the dialog. Choose your fast track card from that (not 'default'). Click 'restart driver' and check that alsa appears at the bottom left (not the Null driver or otherwise).

At any time you want to play to check, you can press SHIFT twice quicly (the playhead goes to the beginning), then the SPACE bar for playing.

When you get it working: to record in mono, place the mouse over the track, press B shortly (the Bus selector dialog appears) and select the right one (as it is the one of your guitar).

Note 1) If you plan to use traverso further, I'd recommend you to use the 0.49.1 version. There are PPAs from what you can install comfortably, for example: [https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)  (lots of updated audio goodies there :-) )

Note 2) Just in case, please, post the output of this command:

```
aplay -l
```

Cheers

---

### Post by punkdrummer09 on 2010-01-23
Well, I followed your steps and still no sound. I raised the volume, and I changed the channel to the right one. I added another screen shot. Here's the aplay -l outcome: 


eric@eric-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Track [Fast Track], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

Am I doing something wrong???

---

### Post by JC Cheloven on 2010-01-23
Well, from what I see in the picture, you should be listening a huge thunder! So, our checking list by now, is:

- Your sound card is recognized in the system, seen in the aplay output.
- You can record form your card, also in mono :-) as it's visually seen.
- You can't listen the playback from traverso 
- You did hear the playback from audacity

I think this alows us to discard the possibility of a hardware problem, as you can both record and play (but with different programs). 

Your problem would be solved by either 1) making audacity record to mono, or 2) making traverso sound. I can't help whith the first one (perhaps anybody else?). Will try with the second:

1) At the bottom of traverso's window there is a blue icon (info). Click that and look for any messages that could give us a clue.
2) You don't have other apps using sound, right?
3) Didn't happen for me, but perhaps PulseAudio is getting in your way. Please create a file ~/.pulse/client.conf (be careful with the dots). Edit it to put a single line: "autospawn=no" (whithout the quotes). Now, before launching traverso, execute "pulseaudio -k" (no quotes). To go back to normality after closing traverso, "pulseaudio -D".
4) If you didn't before, update to the most recent traverso. If you have a problem with PPA's, just ask me.

Sorry for not being able to help with audacity. If it works fine for you, perhaps it would be an easier way to solve your problem (there surely must be an easy way to choose which channel to record from in mono).

---

### Post by punkdrummer09 on 2010-01-23
I attached a screen shot of the messages window. Well, I might have had rythmbox open at the same time. I'll wait for the other steps after you see the messages. By the way, thanks for everything :D

---

### Post by JC Cheloven on 2010-01-23
Yes, as you see alsa has fallen to capture mode only, probably because other app was using sound (your rythmbox) at the same time. Note that the alsa driver can handle only one source at a time. 

Before going any further, I'd try closing both rithmbox and traverso. A system restart shouldn't be necessary, but do it now if you want to be sure. Open traverso (only!), and try out again. It should work.

---

### Post by punkdrummer09 on 2010-01-23
So I only opened Traverso and still nothing...no sound. :/

---

### Post by JC Cheloven on 2010-01-23
> **punkdrummer09 said:**
> So I only opened Traverso and still nothing...no sound. :/

Well, see what are the messages in this state. You can copy-paste the text in the window, no need to post the image of the window.

Then proceed with the pulse audio thing. Let's see what messages are now.

If still no sound, proceed to the newer version of traverso. It's worth, I found it much more stable and overall better.

If still no sound, I guess I'll have a hard time in helping you. 
You do have sound with another apps through your fast track, true?
You are using karmic, true?

EDIT: I've been playing a while with audacity for you, to see if I could find the way of choosing the channel for mono recording. Didn't find it :confused: . Can't believe there is no way, though.

---

### Post by punkdrummer09 on 2010-01-24
I updated Traverso, did the pulseaudio thing, but no sound:(. Here's the messages:


p, li { white-space: pre-wrap; }     [IMG]http://ubuntuforums.org/iconinfo[/IMG]
  23:12:46 : 
  Project Untitled loaded
    [IMG]http://ubuntuforums.org/iconcritical[/IMG]
  23:12:46 : 
  Unable to set Audiodevice Thread to realtime priority!!!This most likely results in unreliable playback/capture 

and lots of buffer underruns (== sound drops).In the worst case the program can even malfunction!Please make sure you run this program with realtime privileges!!!

Yes, I'm using Karmic.

---

### Post by punkdrummer09 on 2010-01-24
Well playback doesn't work on Traverso, but I did export something and it worked. I guess it's just the playback on Traverso?

---

### Post by rsijrier on 2010-01-24
Hi,

Traverso defaults to send it's Master Out to the first available hardware channels it found. Probably due how your system is configured, this might not work.

Go to the Preferences Dialog -> Sound System and choose your audiodevice by name in the dropdown combobox, or the system default one.

Try the system default and the one that's the card you want to use (since you have 2 cards). One of these 2 options will likely work.

The next version of Traverso will have an option to route the Master Out Bus channels explicitly to any hardware channel of your choice.

Hope this helps.

---

### Post by JC Cheloven on 2010-01-24
EDIT: I just saw what rsijrier said while I was writing my post. Please do first what he says. It's simpler and he's probably right. My post follows.
_______________________

It's weird. I am confused: There are no messages about problems loading the alsa driver, the alsa driver appears in the left botton corner (yes?), you can record, you can export, but still you hear no sound from Traverso... And you do hear sound through this card when using another apps...  

PLease: which application do you use to hear you recordings / exports made with traverso? They are pulseaudio-based I guess (totem or similar?)

As sound in traverso had always worked (for me and for everybody I knew, before you), I'm suspecting that there must be something problematic in your system, or at least something what interferes in the way traverso does its thing. It could be:

1) pulseaudio messing things around (quite frequent). You said you already tried that pulseaudio thing (it actually disables pulseaudio). Yust to be sure: when you do the "pulsdeaudio -k", the speaker icon in your upper panel disappears, right?

2) The real time priority. As you see, traverso is complaining about not having that. I didn't experienced seriuos problems with this in my systems, although I've hear from people who did (and I have rt in my main machine though). As rt is considered "a must" if you are involved in audio anyway, I'd take the opportunity to install the realtime kernel and to allow real-time access for your apps. Please refer to 
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
scroll down to "real time kernels & xruns", and do the thing. This ends up with an extra entry in grub, allowing you to choose booting with the rt
linux kernel, or with the regular one. The "real time support" part of this link, also applies to you.
 
3) Alsa trying by all means to playback through device 0, which is the default, and which is assigned to your ATI device (is it your internal soundcard?). It shouldn't being doing that, but we could try blaklisting the module, so that the internal card become invisible to linux. Please run "lsmod" and post the output to see if we can identify which module is it. 

Well... this is getting a bit complicated. It shouldn't at all. I'm sorry for that.

---

### Post by rsijrier on 2010-01-24
Hi JC :)

to make things somewhat clearer:

1) yes, Traverso does _not_ work with pulseaudio, so pulseaudio has to be killed first

2) Real Time priority means: if the audio device wants the application to process audio, the Operating System should _instantly_ give all CPU power to the audio application. This requires special privileges, which can be set in the /etc/security/limits.conf file
The linux kernel however does some more jobs then just giving the cpu to the audio application, it sometimes has to finish stuff first before giving CPU time to the audio application. When you run with very short latencies this time could be too long, and you get a sound drop. A Real Time kernel has been tweaked a lot to avoid this.

3) As I explained, this problem can be solved by explicitly choosing the audio device of your choice in the preferences dialog in Traverso, and hitting the 'restart driver' button.

Have fun!

---

### Post by JC Cheloven on 2010-01-24
Hi, rsijrier, nice surprise!
I think Eric already did that. At least I adviced that (from my previous post):

> **JC Cheloven said:**
>  
(...)
- The driver seems to be ok (seen at the bottom left corner), but there may be a silly problem: Click in that corner; there is an 'alsa device' drop menu in the dialog. [COLOR="Red"]Choose your fast track card from that (not 'default').[/COLOR] Click 'restart driver' and check that alsa appears at the bottom left (not the Null driver or otherwise).
(...)

Greetings

---

### Post by rsijrier on 2010-01-24
Ah, didn't see you explained that already!

Greetings, Remon

---

### Post by punkdrummer09 on 2010-01-24
Well, umm, I feel really dumb right now...Playback does work, but from the Fast Track. I plugged in my headphones in to the Track, and it was working. I thought the playback would come out from my system :/ This is totally my fault...lol Thanks for everything guys. I'm pretty sure this is what it was the whole time. Oops, sorry if i wasted your time..

---

### Post by rsijrier on 2010-01-24
Hehe, glad you found the problem :D

---

### Post by punkdrummer09 on 2010-01-24
Yeah lol Is there a way to make the sound come out from my laptop instead of the Track itself? or that's the only way?

---

### Post by JC Cheloven on 2010-01-24
Well, It was turning me mad :-D  
You have learnt a few things in the way, true? It suffice for me.

Currently you have to choose one of your soundcards from traverso, and work with it (afaik).

Please don't forget marking the thread as 'solved' using the thread tools.

---

### Post by punkdrummer09 on 2010-01-24
Ok, now new problem after shutting down my laptop, traverso doesn't capture the Track anymore, the meters don't move anymore. I haven't changed anything. Everything is the same. This is in the messages: 
 p, li { white-space: pre-wrap; }     18:41:37 : 
  Unable to set Audiodevice Thread to realtime priority!!!This most likely results in unreliable playback/capture and lots of buffer underruns (== sound drops).In the worst case the program can even malfunction!Please make sure you run this program with realtime privileges!!!

Any suggestions?

---

### Post by JC Cheloven on 2010-01-24
> **punkdrummer09 said:**
> Ok, now new problem after shutting down my laptop, traverso doesn't capture the Track anymore, the meters don't move anymore. I haven't changed anything. Everything is the same. This is in the messages: 
 p, li { white-space: pre-wrap; }     18:41:37 : 
  Unable to set Audiodevice Thread to realtime priority!!!This most likely results in unreliable playback/capture and lots of buffer underruns (== sound drops).In the worst case the program can even malfunction!Please make sure you run this program with realtime privileges!!!

Any suggestions?
The message is not fatal, usually doesn't lead to any problems.

Try closing everything, traverso included, unplug the fasttrack, wait some 10 seconds, plug it again. Optional: confirm that it is listed in "aplay -l". Open traverso again.

--> Of course, confirm that the fasttrack is the explicit choice in the driver dialog of traverso.

---

### Post by punkdrummer09 on 2010-01-24
I closed everything and the Fast Track is under aplay -l, and it's the device for Traverso, so I don't understand why it isn't capturing it anymore. I can hear sound through the Track using my headphones. Any idea why this is happening?

p.s Thread is marked solved already.

---

### Post by JC Cheloven on 2010-01-25
May be again a matter of buses (channels)?

Perhaps you're playing your guitar on the right channel and trying to capture from the left one? (remember: hover the mouse on the armed track and press B to see which channel is being captured).

EDIT: or you didn't raise the guitar gain knob in The frasttrack?
Can't figure out anything else...

---

### Post by punkdrummer09 on 2010-01-25
No all of that is correct. I don't know why this is happening. If it worked, then it should work again, I think you can stop helping me now. Hopefully it'll fix soon. Thanks for everything though :D

Note: Evertime I restart the driver in the sound system of traverso, I get the realtime priority message. Could this possibly be it?

---

### Post by JC Cheloven on 2010-01-25
> **punkdrummer09 said:**
> No all of that is correct. I don't know why this is happening. If it worked, then it should work again, I think you can stop helping me now. Hopefully it'll fix soon. Thanks for everything though :D

Note: Evertime I restart the driver in the sound system of traverso, I get the realtime priority message. Could this possibly be it?
I don't think so, but RT is a good thing anyway. Try and see (gave you instructions in a previous post).

OK, my farewell :lolflag:  See you in the forums.

---

