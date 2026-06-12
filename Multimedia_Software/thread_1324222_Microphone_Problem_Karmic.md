---
title: "Microphone Problem Karmic"
date: 2009-11-12
forum: Multimedia Software
---

### Post by LaughingHorse on 2009-11-12
This is a very strange problem.

When I first upgrade to Karmic last month. I was amazed to find audacity and skype both working perfectly. I have Unbutu Studio installed on my dell 8300.

I was and still am able to record streams in audacity, however **about a week ago there were some upgrades to packages. After the upgrades**, and I'm not sure which ones they were... my **microphone that WAS working perfectly is no longer working.**

**Here is what I did so far...**
=> I tried sound recorder. It will not record.

=> I went to terminal and typed alsamixer put everything on high.
     Sound recorder still will not record.

=> I tried skype. I can make a call. I can hear the other person. But my microphone is not working.  

**The Weird:**
When I try making a test call on skype and I can hear myself talking through the speakers, but the sound is not picked up in skype.

When I use Sound recorder: If I talk into the mic, I can hear it through my speakers. But I can not record. 


I have seen posts saying "go to System=>Preferences=>Sounds "
While I may be stupid, in my  System=>Preferences there is no "Sounds" I do have a 
"Pulse Audio Preferences" and a volume control.

From System=>Preferences=>Volume Control
I look at "Input" there... Input volume is greyed out. 
There is a box with "Choose a device for sound input"
And there is nothing in the box. So I have no way to chhose a device for sound input from there.

I went to** Applications=>Sound & Video=> GNOME ALSA Mixer**

It shows: SigmaTel STAC9721,23
**The following check boxes are all unchecked:**
Tone
3D Control - Switch
Surround Phase Inversion
Mic Boox (+20dB)
IEC958 Optical Raw
Analog Capture Boost
Audidgy Analog/Digital Output Jack
HD channel Capture
HD source Capture
Sigmatel 4-Speaker Stereo

Only one box is checked and that is:
External Amplifier

In the GNOME ALSA Mixer
The mic volume control is all the way up.

**Moving on to Sound Recorder**:
The only option I have from "Record from input" is Capture.
When I try to record through my mic... the recording "level" never moves.

**PulseAudio Volume Control**
Input Devices:
Under "Show"... The drop down menu has the following:
All Input Devices
All Except Monitors
Hardware Input Devices
Virtual Input Devices
Monitors

All Input Devices and Monitors give me "Monitor of SB Audigy Analog Stereo
Hardware Input Devices gives me "No input devices available"

**So My Question is**
Any ideas on how to get my system to once again recognize there is a microphone? Again. Immediately after upgrading to Karmic, everything (pulse, audacity, sound recorder, skype, etc) were all working perfectly.

Then after a recent upgrade of packages about a week ago, now my system does not recognize my microphone. 

Thanks in advance for your suggestions and help on what to do.

---

### Post by danushk on 2009-11-12
hi ,

Can you check your alsa version using the command below in the terminal 

*cat* /proc/asound/[I]version

[/I]i also upgraded my Alsa  and after that Mic stopped working.

Mic is perfectly working on Windows too.

I am also having the same issue as yours.

---

### Post by LaughingHorse on 2009-11-12
Hi danushk,

I did it and got
Advanced Linux Sound Architecture Driver Version 1.0.20.

---

### Post by danushk on 2009-11-12
Hi,

This is my output , because i manually upgraded by compiling the sources.

Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Nov 11 2009 for kernel 2.6.31-14-generic (SMP)

when i had [I]Advanced Linux Sound Architecture Driver Version 1.0.20 
[/I]mic worked perfectly. But sound was not perfect , it was scratchy. 

but after upgrading to Driver Version 1.0.21 mic is not working as well.

Mic works on windows , so nothing wrong with my mic.

I am still struggling to get this fixed !

Help me !!!!!

---

### Post by Nick Brohman on 2009-11-18
G'day,

I've had the same problems for a day or so & have just now opened sound preferences.

I had set my Hardware to Analog Stereo Duplex an hour ago but to no avail, I could not record sound.

I switched around stereo settings and back to Analog Duplex and I can now record sound. 

When I can I will make a Skype call to test that...just did a test call & now have audio...go figure!!

As a new user, this was a perplexing problem for me, I hope it may help you

Cheers...Nicko

---

### Post by Nick Brohman on 2009-11-18
G'day again, 

I must elaborate on my last post.

I removed Pulse when having problems with sound quality but[COLOR=Red] followed this thread[/COLOR] to set up ALSA :-

<http://ubuntuforums.org/showthread.php?t=1130384&highlight=markbuntu>

I don't know if that will link you to it as I'm uncertain of adding links as yet.

Two days ago all was fine, yesterday morning my audio out in Skype was missing. I could hear myself, amarok was able to play the music but everything I could think of wasn't helping me.

I went back to ***markbuntu's*** thread this am & [COLOR=Red]***r******e-installed Pulse***[/COLOR] but took off any KDE 'applications' (I am a learner), I also made sure that **any add ons were not going to delete Skype.**

I can't launch the PulseAudio Device Chooser, but do have the **Pulse Sound Preferences** in System->Preferences, it comes with the Pulse pkges.

I enabled [COLOR=Red]**Analog Stereo Duplex **[/COLOR]but got no joy when making a test call or using Sound Recorder.

I found this thread by LaughingHorse & went back to the Sound Preferences, changed several stereo choices without joy, finally went back to[COLOR=Red]** Analog Stereo Duplex**[/COLOR] & I had audio out.

I now get a screech when I log in (1st since my post above) so I will turn down my speakers' volume control before my next boot, thankfully I was able to do so before being deafened this time.

I'm not sure why I got that screech but have an idea it might have something to do with mic boost. I'll test that theory later. 

Once again, I hope this helps you,

Cheers...Nicko  :)

---

### Post by Nick Brohman on 2009-11-19
Well, I'm as useful as an ashtray on a motorbike.

I've taken my headset off the front mic as I got the screech when firing up again (sorry, old steam buff), lost volume/audio in amarok, removed front mic, now have amarok raging. have not made test call as am chilling out 'cos I'm totally flummoxed by this scenario & the blues are curing my ills.

Will investigate further...yer wouldn't be dead for quids, eh? 1 step forward, 5 steps back for me...back to projectM & peter Green

Cheers..nicko

---

### Post by Nick Brohman on 2009-11-19
Update on last post...not sure exactly what the problem is ...have removed the headset & fiddled with Pulse volume control...I still have a hiss in my speakers but turning down mic boost helps a bit.
 
Also adjusting Front helps stop the squealing.

I think some of my Skype problems stem from their end...I have no control over their Server settings.

I can use Skype & have the ALSA Gnome Mixer visible during calls. That helps to get a very reasonable sound quality.

The call made this morning had crackles but that is most probably his end as it doesn't happen during the test call. The overall sound was good considering I was talking to someone10,000 km away.

Audio with Amarok is good but I haven't tried any concert DVDs as yet. Will do that later when time permits.

Cheers...Nicko  :)

---

### Post by neerajadsul on 2009-11-19
I had same problems, especially with Skype.

1. I disabled - "Allow Skype to Adjust Sound Levels".
2. Closed all the applications using sound devices.
3. Then configured each device Sound Preferences -
[INDENT]Input[/INDENT]
[INDENT]Output[/INDENT]

After these settings, everything started working without any problem.

---

### Post by Nick Brohman on 2009-11-19
> **neerajadsul said:**
> I had same problems, especially with Skype.

1. I disabled - "Allow Skype to Adjust Sound Levels".
2. Closed all the applications using sound devices.
3. Then configured each device Sound Preferences -[INDENT]Input[/INDENT][INDENT]Output[/INDENT]After these settings, everything started working without any problem.
  
Thanks for that info, I'll do the same.

Cheers...Nicko  :)

---

### Post by LaughingHorse on 2009-11-21
This is really weird...

I can talk into my external microphone. The sound comes through the speakers.
I open Sound Recorder... I talk into my microphone... The sound comes through my speakers, BUT... the level meter in sound recorder do not move, and I can not record.

Sure the record option works, but it records no sound.

I tried recording from my microphone in audacity. Same thing. It will not record. I can record streams in audacity. Just not my microphone.

I removed and re-installed both pulse and alsa. 

And still under "Sound Prefrences" 
The microphone is greyed out. And the filed under "Choose a device for sound input" is empty.

So apparently, Pulse does not seem to know my microphone exists. Any ideas?

My system did work perfectly until an upgrade in pulse a few weeks ago.

Any ideas for a fix will be greatly appreciated.

---

### Post by sambarluc on 2009-11-23
I had exactly the same problem on the new Kubuntu 9.10 64bit. I completely removed all pulseaudio components, and installed alsa instead. Now it works fine, apart from the fact that microphone volume is very low, as it was with alsa on 9.04. Probably it's not the best solution, but it works.

---

### Post by tolito-cr on 2009-11-30
hi neerajadsul... could you please explain a bit further what is it that you did? Back in Jaunty I had everything working find, and being a newbie to Ubuntu I just regret having moved so quickly to Koala (though it is much nicer in many things, but I need skype and to record sound!!!)....

Anyways, I've fiddled with as many options I have in the sound preferences, but it seemed to have more options in Jaunty... OPEN TO SUGGESTIONS.

cheers,

eduardo.

---

### Post by bxcrx on 2009-12-04
We're all having the same problem here:

[http://ubuntuforums.org/showthread.php?t=1339409](http://ubuntuforums.org/showthread.php?t=1339409)

See if it works with the Live Karmic CD if it does then we all suffer from the same problem found here:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/460351](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/460351)

---

### Post by bwsmith7 on 2009-12-05
Thanks Nick, I was having the same problem with my mic, but by opening Sound Preferences, setting my Hardware profile as Analog Stereo Duplex, and setting my Input Connector to Microphone 2, I managed to get the mic working.  I did have to amplify the input volume, however. 

This fix worked, but it's kind of annoying because I am running a Lenovo Y510 with surround sound, so I have to reset my Hardware profile and mess around with GNOME ALSA mixer each time I want to use the laptop speakers.  

This is my first time using Ubuntu and I love it so far, despite the hiccups. I hope this problem (and the upside down webcam) will be fixed soon.

---

### Post by Nick Brohman on 2009-12-05
No worries BW, I'm still not able to use Sound Recorder but I've just downloaded Ardour & will try things with that. I've got to practice as I have about 500 vinyl to put on the HDD.

I've got to wait until I can do a back-up so that I can do a fresh install of 9.10 before adding the LPs to my HDD, not sure when I'll have the know-how, but I'll post the results...hey, it's Sunday, so I'll start mucking around with Ardour today....and I've just thought of how I might be able to get the fresh install going shortly...**.thanks**, reading your post got me thinking for a change...

Cheers...Nicko  :)

---

### Post by LaughingHorse on 2009-12-06
I did a fresh install of Ubuntu Studio and Alsa just minutes ago.
Yes, I rebooted after then went to check things out.

On System | Sound Prefrences | Input

The Input Volume is still greyed out. the box by "Mute" and the word "Mute" are still greyed out.
There is no input level
The listing field under "Choose a device for sound input:" is still blank. 

Interesting I also had a look at JACK

[https://wiki.ubuntu.com/Testing/Cases/UbuntuStudio](https://wiki.ubuntu.com/Testing/Cases/UbuntuStudio)
Main Menu | Applications | Sound&Video | Audio Production | JACK Control

Following the instructions for testing Ubuntu Studio
# Click on the Setup button.
# In the Parameters section click the Realtime box.
# Click the OK box at the bottom.
# Now click Start.
# "Started" should now be displayed in yellow on the display. 

10:38:10.092 Patchbay deactivated.
10:38:10.094 Statistics reset.
10:38:10.253 ALSA connection graph change.
10:38:10.436 ALSA connection change.
10:39:05.865 Startup script...
10:39:05.866 artsshell -q terminate
sh: artsshell: not found
10:39:06.271 Startup script terminated with exit status=32512.
10:39:06.272 JACK is starting...
10:39:06.272 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
10:39:06.277 JACK was started with PID=2756.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1217427776, from thread -1217427776] (1: Operation not permitted)
cannot create engine
10:39:06.674 JACK was stopped successfully.
10:39:06.675 Post-shutdown script...
10:39:06.676 killall jackd
jackd: no process found
10:39:07.098 Post-shutdown script terminated with exit status=256.
10:39:08.393 **Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.**

I have not compiled anything manually.
I have used Synaptic to install and uninstall everything, except this last time today (which was done after testing JACK). 

My sound card works, as I can talk through my mic and I hear it through the speakers. The system just does not recognize I have it plugged in. And This is the same whether I use an external mic plugged in through the mic plug, or a USB mic.

Any ideas?

Nick, like you I have a huge amount of records, and tapes I need to transfer. Also I can not use skype which is totally frustrating.

---

### Post by Nick Brohman on 2009-12-06
G'day LaughingHorse,

The fix seems to be a re-install of 8.04...rather a hassle for me as I can't get a system back-up to work for me.

I tried to record in Ardour but need to study the Manual a tad more...a lot more really (a lot of it confuses me). I'll try again in the near future.

I also have tried all 5 'Record from input...' settings in Sound Recorder to no avail.

I have a lot of my LPs on mini disc but as Sony don't seem to want to support my 2nd generation player/recorder, I have to find an alternative....record over a few of my 'Party' discs which is a pity as I spent a lot of time making up those discs

I've had a look at this thread:-

[http://ubuntuforums.org/showthread.php?t=1313277&highlight=Skype](http://ubuntuforums.org/showthread.php?t=1313277&highlight=Skype)

It seems to be a major fault with 9.10.

I've run ALSA Mixer in Terminal but could not change anything there to see if that helped.

I've looked for gnome-volume-control in Terminal but could get no connection. I got a 'WARNING **: Connection failed, reconnecting..." message.

The only Gnome Vol. Control in Synaptics is the ALSA Mixer

Like you, I get the same results when running JACK in Terminal.

As time is on my side (I hope), I can wait for this to be resolved.

Skype works well, I have good Audio & Video there.

I don't want to re-install Pulse because it will muck up all the work I've done to get a good sound with Amarok14 & Skype.

I won't put in a bug report as my account at launchpad isn't recognised and it's too much of a hassle for me to try to get another one...I tried to put in a bug report about FSpot several times but kept being told my email address wasn't recognised yet I registered about 2 mths. ago.

I don't have enough PC smarts to do anything other than wait for the advice that I have asked for (how to do the back-up needed), then do a clean install of 8.04 and wait for 10.04. For this new to computer user (since late Aug. this year), 9.04 & 9.10 are really tough OSs to come to grips with.

I've learnt a lot in the last 4 mths. but not enough to re-write anything to get it running properly.

BTW I'm using 2.0.0.47 Skype and that seems to work well once the Sound Device is set to my card...the latest Beta Skype is a hassle for a lot of users tho' I had it working after a bit of tweaking.

Sorry I can't do any more, LaughingHorse, I'm as flabbergasted as you and many other users..

Cheers...Nicko

---

### Post by LaughingHorse on 2009-12-06
RE: Recording LP's and tapes. Here is what I was doing until my mic connection broke.

I out to try it again and see what happens though...

I was plugging in a MD recorder I had transferred tapes to, into the microphone connection . Then I would record in Audacity.

Now Audacity can be a bit tricky to get working for recording a stream.
What I found is if I set the project rate for 48000 or lower. I useAlsa: SB Audigy 2 ZS [SB0353]: ADC Capture/Standard PCM Playback (hw:0,0)
or one of the other ALSA: SB Audigy settings
I have an Audigy card.

Then I record. What I found works best it to just start the recording, record the entire side, or tape. Then save the entire recording. Then highlight the first song, and save it. Delete the first song, highlight the second song and save it, etc. Until I'm done.

Also on the Volume Control settings make sure in configuration it is set to something with Analog. That was the only way I could get Audigy working to record streams.

Allen

---

### Post by Nick Brohman on 2009-12-06
G'day Allen,

 I thank you for the tips...I was lost in Audacity as well but now I know more, I'll get stuck into it when I get things right on my PC....I've got the MD Walkman & stereo close at hand & connect both thru' the rear Mic.

More knowledge for me is much appreciated....thank you once again.

Cheers...Nicko  :):)

---

### Post by LaughingHorse on 2009-12-09
You are welcome Nick.

I have finally solved my mic problem. This may help you. And it may help anyone who has the same problem.

I went in to Gnome ALSA Mixer

The following Boxes Checked:
=> Tone
=> 3D Control - Switch
=> Surround Phase Inversion
=> ICE958 Optical Raw
=> Sigmatel 4-Speaker Stereo

***** CRUCIAL: Audigy Analog/Digital Output Jack MUST NOT BE CHECKED! *****

I found **To Use Microphone [Skype, Sound Recorder]**
**Sound Preferences** (Or Applications | Pulse Volume Control | Configuration)  :
**Hardware: Profile** - Analog Surround 5.1 Output + Analog Stereo Input
NOTE: When anything Digital is on, the mic is NOT working.

I went into Terminal. typed alsamixer as well. Made sure the mic was not muted.

And my mic started working. I then tried setting Hardware Profile to various different settings. Some had very weak sound from the mic, and some no sound.

I also found that To capture a stream in Audacity: 
Sound Preferences:
**Hardware: Profile** - Must be set to Any of the Analog Stereo Output choices.

I hope this helps.

---

### Post by Nick Brohman on 2009-12-10
Thanks Allen,

I seem to have a different Gnome ALSA mixer, mine doesn't give me those boxes. I'll go back to the terminal to check zacchary what I have there....I do want to get Sound Recorder going plus sound in Movie player.

Dozen madder, I'm copying your post to store for future reference & study.

It has been a hot day here & I've been stymied by not being able to access the Forum for some technical reason...I'm not going to do anything until I've had some R & R.

I think you will have helped many tho', as frustrating as it has been.

Cheers...Nicko  :(

---

### Post by zampes on 2009-12-10
Hi everyone!
I had the same problem as all of you. I solved my mic issues by going to a terminal and typing 'alsamixer', this took me to the alsa mixer console. There I configured the mic the way you can see in the picture. In order to try it out in realtime, I had my 'sound preferences' on screen to see what combination would make it tick and some music playing so I wouldn't have to keep saying 'testing testing testing' while trying the different combinations. :)  Note: I also used the 'microphone 2' in sound preferences. 
This works then for a HP Pavilion DV4 1220us, ATi 3200, Turion X2 64 bit under Ubuntu 9.10 Karmic Koala 64bit.

Post again, I may be of some help!
By the way, you navigate the mixer with the arrows and change 'on/off' values with m and 'up' and 'down'.
:guitar:

---

### Post by Nick Brohman on 2009-12-10
Thanks zampes,

Being a new computer user, there's a lot for me to learn...it took me a few minutes to realise that 'arrows' are on the keyboard...opened both alsamixer & alsamixergui in Terminal and I find that I can work on some but not all of the controls.

I don't have Pulse so I can't open Pref.->Sound....I'm going to live with this situation at the moment.

When I open alsamixer in Terminal, I'd like to open 'All' not just 'Playback'...I might get to use Sound Recorder then.

I can use both Front Mic & Mic...I have my headset on Front and run my Walkman & stereo thru' the Mic without problems at the moment...I have good Audio with Skype & Amarok so the problem is not urgent at present but I would like to resolve it in the future.

Thanks again, it's more knowledge for me.

Cheers...Nicko  :P

---

### Post by zampes on 2009-12-11
And now, on a second try the morning after, the solution I proposed earlier doesn't work either...
Sorry guys, it really did work last night, but using skype this morning everything died again...

---
Damn!:(

---

### Post by VertexPusher on 2009-12-11
> **zampes said:**
> And now, on a second try the morning after, the solution I proposed earlier doesn't work either...
Sorry guys, it really did work last night, but using skype this morning everything died again...
Keep in mind that PulseAudio resets ALSA's mixer settings every time it is launched. If you want your customized mixer settings to persist between sessions, you have to remove PulseAudio.

---

