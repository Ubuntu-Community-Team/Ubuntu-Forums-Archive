---
title: "Can you record sound in Ubuntu? Vote here!"
date: 2005-12-11
forum: Multimedia &amp; Video
---

### Post by anil_robo on 2005-12-11
I can see that many people are having problems with sound recording. I'm one of those unfortunate ones. Let's see if I've got some company! Go ahead and vote! Let the developers know about us!

---

### Post by 23meg on 2005-12-11
I can record with my laptop's internal sound device, but not my external one yet, since I can't get it to work with JACK.

---

### Post by anil_robo on 2005-12-12
Unfortunately I have a Dell Inspiron 6000 and it doesn't come with built-in mike! Pretty rare for laptops not to have built-in mike, and mine is the one :(

I'd use sound recording to talk to my friends and family living 9000 miles away, if I get sound recording to work! I have some AC'97 audio controller which doesn't work with recording in Ubuntu. I also tried external mike, USB mike etc. and nothing works! :(

---

### Post by aysiu on 2005-12-12
[QUOTE=anil_robo]Go ahead and vote! Let the developers know about us![/QUOTE] The best way to let the developers know about bugs is to file a bug report: [https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/)

---

### Post by anil_robo on 2005-12-12
I never thought it's a bug! I kept thinking it may be due to my "n00bness" and "technological incompetence" :P
Nevertheless thanks for the link... I'll forward my request to the devs! :)

---

### Post by anil_robo on 2005-12-17
I've been working hard to get skype working with my voice in Ubuntu. Apparently there was a sound recording problem, and I never had encouraging results, except tonight. I am able to record sound now, sometimes. All I did was to set "capture" to "on" in the mixer.

 Here are the results:

1. Sound recording never worked for me with Logitech Quickcam for Notebooks (USB) built-in mike.

2. However, if I insert a conventional (jack) microphone in the soundcard hole, I can send sound "normally" to skype sound test service with the following conditions:
(a). I must never run the applications called "sound recorder" and "recording level monitor". Once I run any one of these, I can no longer record any sound unless I logout and relogin.
(b). I must never play a sound using XMMS which uses ALSA as its primary sound driver. Playing XMMS even once causes skype sound testing service to report "error in sound device".
(c). Skype must have selected the default sound device.
(d). In system sound mixer (double click the volume icon in panel), I must have selected my soundcard as "Intel ICH6 (ALsa MIxer)".
(e). The capture level for mike should be maximum, but the playback from mike should be zero.
(f). The capture level and playback level from "capture from capture" must both be zero.

Once all these conditions (a-f) are satisfied, I am able to record sound through skype sound testing service. Ubuntu sound recorder crashes it all! It simply freezes whatever sound recording I was getting previously! Same with XMMS.

If I want to talk to mom using skype, I have to do the following:

1. Restart the computer and log-in.
2. Start skype.
3. Select my mom's ID and press the call button.
4. Talk to her! :)

If I run Sound recorder, Recording Level Monitor or XMMS, skype fails 100% of the times!

And once skype fails, I can't get "any" playback or recording from the computer unless I restart.

It effectively means that I have to restart everytime I want to use skype, and I have to restart once again once I have finished using skype!

:(

Any ideas?
[]("http://www.ubuntuforums.org/showthread.php?t=102377#6")

---

### Post by cvmostert on 2005-12-31
sound worked great on my previous motherboard... onboard sound... yamaha... but...

on my new motherboard with VIA onboard sound... nothing whatsoever! cant get it figured out... when i play sounds in all players, it works... well i can see the progressbar etc. but i cant hear any sound... does not record anyhow... tried with audacity...

but.. i booted knoppix live and audacity actually recorded something... ofcourse i could not hear anything... just saw it :-)

gives me a headache!

---

### Post by anil_robo on 2005-12-31
Hopefully Dapper will bring a fix to all the sound woes! I can only hope, because the Dapper Live/Install CD I downloaded never work! :( If someone has tried Dapper successfully, please let us know how is the status of sound playback and recording in Dapper :)

---

### Post by dawynn on 2005-12-31
Let's me add my 2 cents...

Ubuntu -- A Debian-based distribution with semiannual stable releases based on the unstable Debian repository.  Goal is that everything "just works".  However, Sound Recording does not seem to "just work" for a significant portion of users (and those for whom it *does* work seem to have executed significant tweaking)

Agnula / Demudi ([www.agnula.org](www.agnula.org)) -- A Debian-based distribution based on a combination of stable / unstable / hoary repositories.  Goal is that multimedia applications (especially sound applications) "just work".  JACK is fully supported, including all kernel tweaks required.

Hmm.  Ubuntu does pretty well *playing* sounds, and overall tends to have everything working fine (at least in my personal experience) -- except for recording sounds.  Meanwhile, Agnula is built for multimedia applications to just work, but because the distribution is based on stable, the packages are out of date.  Agnula does have a Testing version, but it doesn't interact well with Ubuntu (I tried).

Perhaps the Ubuntu experts could work with the Agnula experts to figure out how to get multimedia applications working in Ubuntu.

Other related issues:
The free version of OSS is "deprecated" according to some websites -- although it seems to have been more recording-friendly than ALSA.

ALSA works for listening, but JACK seems to be the best resource to work with recording in ALSA.

JACK requires extra tweaking (including internal kernal tweaks) to get it to work.  It won't work straight out of the box in Ubuntu.

ESD and Arts both seem to lock-up ALSA resources making any kind of sound recording impossible while these systems are running.  I haven't found any software that actually uses Arts / ESD for recording.

Recording in Ardour requires JACK to be working.

Recording in Audacity requires either OSS (deprecated) or portaudio version 19 (not stable, and not packaged for Debian systems yet).

Any suggestions?

---

### Post by earobinson on 2005-12-31
i dont even own a mic to test :(

---

### Post by mckay on 2006-01-02
It seems that lots of people using Linux have a problem getting their microphone to work properly. I am one of these peoples and am requesting help because I have run out of places to look and I am going insane trying to get my mic to work. If anyone can help at all, please do.

Here is my problem: I am running Ubunty-Breezy Badger 5.10 with the Kubuntu Desktop. I have the Creative Audigy 2 ex (though I have had this exact problem on any system, and any sound-card I have had). I can hear my mic, but I cannot record anything from it. When I press record in Audacity it says "Error While opening sound device. Please check the input device settings and the project sample rate." I have not been able to get this to work, but the sound works fine for everything.

Does anyone know what I need to do to get this working? I use my computer for a phone (using Kiax) so this is quite the bothersome problem as I am phone-less unless I log into WindowsXP.

---

### Post by veratyr on 2006-01-02
My Audigy 2 card doesn't even give me the option to select a capture source in ubuntu. The capture tab in volume control just isn't there...?

---

### Post by anil_robo on 2006-01-02
[quote=earobinson]i dont even own a mic to test :([/quote]
Can you please buy a $1 microphone for testing purposes (I read that in your profile description)! ;)

---

### Post by anil_robo on 2006-01-02
[quote=veratyr]My Audigy 2 card doesn't even give me the option to select a capture source in ubuntu. The capture tab in volume control just isn't there...?[/quote]
 
Double click the sound volume icon in the system tray. In the sound properties window that opens up, click Edit--> Preferences. There you can check "capture" box and it'll show up.
 
Once the capture shows up, you can turn it on and possibly record sound. Make sure no other sounds are playing before you attempt to record sound.

---

### Post by Nexus6 on 2006-01-05
i a newbie of linux and ubuntu and have just been working with it for just a couple of days. so i really dont know anything about it but.

it looks like people have a lot of problems with the sound card and REAL big problems with their recordings of sound. 

and maybe i can help. becaus i had some problems whit my soundcard that worked out after all. from the begining i had sound in my speakers so the out-line worked just fine but not my recording of sound. 

the goal was to get Ardour working and from the begining it look kind of hard and i spend a lot of houres reading in forums and websites, but nothing could help me.

but when i solved the problem and it was kind of easy and i hope it will work out for everbody else to. 

and i fixed everthining with the alsamixer. and now both the mic and the line in works great. 

so just download and install the alsamixer then you start the program buy just write...

alsamixer

the program will start then goto the capture by pressing F3 and there you will find the possebillities to set the controll and level of the input and the mic.

it worked out fine for me.

besides from alsamixer i use jack and jackd and qjackctl but i dont know if you need them.

---

### Post by mpvano on 2006-01-05
Make sure you are NOT running the esd (enlightenment!) sound daemon.

It takes over your sound system for exclusive use by its client programs to make cute noises in gnome! It's also loaded by default if any of the default gnome desktop audio applications are started.

ESD is yet another "scheme for world domination" style program API that just assumes you will never want to run any audio programs that are written any other way and may prevent you from doing so when it's installed. Unfortunately, it's part of most default gnome installations, and can be hard to work around. It's supposed to stay out of the way of other audio programs, but it's never really worked properly that way.

Even if it's not loaded permanently, many of the audio programs supplied with ubuntu have been recompiled by the Ubuntu packagers to default to loading the ESD sound daemon and then using it for output unless you give them different instructions at startup. Some of these are even background programs you're note aware have been loaded.

Go to your "sound" preferences and  make sure "enable sound server startup" is not checked. Then go to "multimedia systems selector" preferences and make sure the default for desktop programs is OSS for default sink and default source. Then check the preferences, man pages and documentation for every sound application you use to make sure they're not set to use esd for output.

At any time you are having trouble starting other sound applications, open the "System Monitor" program in "System Tools" and select the "processes" tab. Look for "esd" in the list. If it's there, one of your sound programs is set to use it for sound output - unfortunately, in some cases programs load it and don't specify that it be unloaded when they quit. You can try killing it from that application, but If it was started as root, you'll need to use sudo and the "kill" command to get rid of it. It can keep coming back from the dead like a character in a bad horror film.

Hope this helps sort out at least ONE of the more commonly confusing parts of sound in all gnome based systems....


Mario

(PS - KDE user's shouldn't gloat - they've got their own esd-like sound daemon installed, called "arts" that can cause similar problems).

---

### Post by encompass on 2006-01-05
I have sound recording but my sound is very faint.  I have trid the mic boost, but it only helps to the point that if I speak right in the mic and speak loadly, they can hear my voice fine.  I have trioed different mics, but to no avail.  If you have some ideas I am up for it.

---

### Post by anil_robo on 2006-01-05
[quote=encompass]I have sound recording but my sound is very faint. I have trid the mic boost, but it only helps to the point that if I speak right in the mic and speak loadly, they can hear my voice fine. I have trioed different mics, but to no avail. If you have some ideas I am up for it.[/quote]
 
1. Test your mike on another computer. There may be some problem with the mike itself.
2. Check your sound recording levels by double-clicking the speaker volume icon. Make the sliders for "capture" maximum and then test recording again.

---

### Post by mpvano on 2006-01-05
The default controls displayed in the gnome-volume-control mixer (the one in the panel on ubuntu) do NOT usually contain the switch that some sound cards use to increase the microphone gain to a usable level.

Try opening the mixer and browsing the "preferences" dialog under the edit menu (why it's there is a mystery). First check everything so ALL controls are displayed. You can disable the ones that obviously are not hooked up to anything once you've satisfied yourself that that's really true.

Make sure you do this in both the OSS and ALSA flavored mixers. Then look for a switch marked something like "Mic Boost (+20db)" If you find one like that, usually in a tab called "switches", try setting it to on.

This setting is needed with some microphones to get reasonable sound levels, but for some reason, I've NEVER seen it come up in the gnome-volume-control until I go into preferences and "unhide" it.

hope your problem is this simple,

Mario

---

### Post by srt4play on 2006-01-05
Sound recording works real well for me for both a mic plugged into my soundcard and recording general sound output through ossrecord.

The commercial OSS system is awesome.

---

### Post by sup on 2006-01-08
My experience is as follows (took me couple of hours to find out, especially the fact that for microphone in order to work, it has to be unmuted - the irony of it is that I know for sure I must have muted it myself at some point): I do not need to reboot in order to get various things on my system to work and basically the only thing to get them work is to change default source and default sink (does onybody know what these two stand for, what they mean? I have no clue) in system>preferences>multimedia system selector:
note:I have got laptop with microphone, reproductors and soundcard integrated, lspci gives this:
```
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

```
1)ALSA gives me some strange errors when trying to use sound recorder and microphone (I think that maybe reboot would do something about it but I have got smarter ways than reboot), Skype is however working correctly and other sound application work as well. However, they often crash (especially rhythmbox) when I try to play more than one source of sound at a time.
2)ESD skype si working correctly, more applications can play sound at the same time, sound recorder does not work at all
3)OSS, skype works correctly, only one application can play sound at a time, sound recorder works perfectly.
4)have not tried Art, KDE is not my cup of tea.

>>Skype always says "problem with sound device" whenever I try to use it when some other application plays sound (even when using ESD) and the only way around it is to restart skype (and mute the sound application before that, but it is better to close it straightforwardly since it refuses to play sound after I stop using skype). When I want to for example listen to music again, I need to close skype and then start sound playin applications.

>>ESD is the only way to achieve programs not crushing when I try to use rhythmbox and vlc at the same time

>>OSS is the only one to be able to record sound with sound recorder, but programs crush when started more than one at a time.

So I usually use ESD, when I want to use skype I close all aplications using sound, use skype, close skype and start those applications once again adn when I decide to record sound with my microphone, I change to OSS, close all applications usinfg sound, record the sound, change to ESD and open those application again. Well, compared to others here it is not that bad, but it would be nice not having to close and start rhythmbox all over all the time. It is just lucky me I record sound once a hlaf a year and use skype once a fortnight.

---

### Post by ioannis.th on 2006-01-10
I got it!:) :) :) Just run alsamixer on the command line, (if you don't have it install it) and scroll to the right at the capture sliders. One which is turned down is hopefully for you. Me, I have a SB live! platinum and I can record my guitar by turning up the livedrive slider, and having pressed spacebar beforehand to activated. The strange part is that kmixer doesn't do the same although it has the same slider too.

Note to ubuntu devs. With all the respect guys, things like that shouldn't happen, I mean the whole situation about this 3 page thread along with its poll. At least not if you want to keep your distribution's status as "human" linux. It was working on hoary, and it is a feature needed by LOTS of people. I know ubuntu is free etc etc but when someone needs to record something quickly ( a musical idea for example )  and discovers recording doesn't work, he won't care much about ubuntu being free, he wants it to be useful too.

---

### Post by anil_robo on 2006-01-13
[quote=ioannis.th]I got it!:) :) :) Just run alsamixer on the command line, (if you don't have it install it) and scroll to the right at the capture sliders. One which is turned down is hopefully for you. Me, I have a SB live! platinum and I can record my guitar by turning up the livedrive slider, and having pressed spacebar beforehand to activated. The strange part is that kmixer doesn't do the same although it has the same slider too.

Note to ubuntu devs. With all the respect guys, things like that shouldn't happen, I mean the whole situation about this 3 page thread along with its poll. At least not if you want to keep your distribution's status as "human" linux. It was working on hoary, and it is a feature needed by LOTS of people. I know ubuntu is free etc etc but when someone needs to record something quickly ( a musical idea for example )  and discovers recording doesn't work, he won't care much about ubuntu being free, he wants it to be useful too.[/quote]

I agree with every alphabet in these two paragraphs! I'm hoping Dapper would bring back some joy! :)

---

### Post by SolidAndShade on 2006-01-15
If you have problems recording sound, try doing as previous posters said and checking boxes under Edit > Preferences in the volume control window to display more sound card controls. Also, try looking at File > Change Device in the volume control window. Some sound cards are recognized as different devices by OSS and ALSA, and if your sound recording program works with OSS and not ALSA or vice versa, you can use this feature to set the sound input volume for the sound architecture that you're currently using.

---

### Post by chaumurky on 2006-01-15
My mic would cut out each time I touched the volume or mute control (CS4236 chip). Turning the mic gain on and then off would get it going again. I put this line:
 
```

amixer sset 'Mic Playback Boost' on && amixer sset 'Mic Playback Boost' off

```

Into a couple of scripts for audacity and gtkguitune (guitar tuner) which, in turn, launches the application. I point the existing menu items to these scripts and it works flawlessly. I've mentioned elsewhere that I'm discovering Linux has as many corks as there are holes! Here's a perfect example...

---

### Post by MJSOnline on 2006-01-27
[QUOTE=anil_robo]Unfortunately I have a Dell Inspiron 6000 and it doesn't come with built-in mike! Pretty rare for laptops not to have built-in mike, and mine is the one :(

I'd use sound recording to talk to my friends and family living 9000 miles away, if I get sound recording to work! I have some AC'97 audio controller which doesn't work with recording in Ubuntu. I also tried external mike, USB mike etc. and nothing works! :([/QUOTE]

I too have the AC'97 clip set in my sis motherboard.  No joy here using my Audio 50 headset...  Anyone got any ideas? Matthew

---

### Post by joehill on 2006-02-01
I'm trying to digitize some cassettes through line-in and, after getting the alsamixer thing worked out (the default seems to be no record and no play from line-in) I'm able to record from line-in but the quality is terrible.

If I simply listen to the cassette (cassette --> sound-card/alsa --> headphones) the quality is fine.  But when I record and play back everything is accompanied by high pitched rattling.  It's like this whether I record in my own compiled audacity (the one available through synaptic apparently is compiled without alsa support and simply doesn't work) or through the plain sound recorder.  Messing with the recording levels doesn't seem to do much.  I don't know what other settings there are to play with.

Any ideas on what causes this?  Thanks!

---

### Post by wook on 2006-02-08
I've installed Breezy Badger on  an older Dell computer.  I'm a n00b to Ubuntu, but not Linux.

I'm trying to get Skype working, but can't use the mic.  I can hear the Skype test echo123 as well as anything outputing sound, but can't record anything.  I found this thread and setup my system as it says below, but it didn't help.

lspic shows...

Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)

Alsa Mixer shows...

SBLive! Value (CT4780)

Should I abandon the mic for a USB headset.  What's the best combination for Skype?  Any help would be appreciated.


[QUOTE=mpvano]Make sure you are NOT running the esd (enlightenment!) sound daemon.

...

Go to your "sound" preferences and  make sure "enable sound server startup" is not checked. 

Then go to "multimedia systems selector" preferences and make sure the default for desktop programs is OSS for default sink and default source. 

Then check the preferences, man pages and documentation for every sound application you use to make sure they're not set to use esd for output.

...

At any time you are having trouble starting other sound applications, open the "System Monitor" program in "System Tools" and select the "processes" tab. Look for "esd" in the list. [/QUOTE]

---

### Post by patrick295767 on 2006-03-05
Try to make it work : Skype   With  USB Microphone Logitech ([http://ec1.images-amazon.com/images/P/B00009EHJV.01._PE33_.Logitech-USB-Desktop-Microphone._SCLZZZZZZZ_.jpg](http://ec1.images-amazon.com/images/P/B00009EHJV.01._PE33_.Logitech-USB-Desktop-Microphone._SCLZZZZZZZ_.jpg))
  
U can have fun and wont make it ... 
  
Greetings, 

Pat'

---

### Post by Dingo_aus on 2006-03-15
Thanks for this post - I didn't realise that KRec was blocking skype - I'd always try KRec before trying Skype and Skype would never work.

I've now finally got Skype to work.

For the record, using Xmms first doesn't seem to be a problem for my Skype.

---

### Post by detyabozhye on 2006-03-18
It took a littlt tweaking, and I don't remember what I did, but I got it working nicely.

---

### Post by sidd-tx on 2006-04-10
Mic can record on my Toshiba portege 7200 series laptop, but Skype doesn't work. I think that is more an issue with Skype using oss instead of alsa. But it still is annoying....

---

### Post by dudus on 2006-04-10
it's broken for me in dapper but worked flwalessly in breezy

---

### Post by hyg53 on 2006-05-12
[QUOTE=dudus]it's broken for me in dapper but worked flwalessly in breezy[/QUOTE]
same for me. I can not call people anymore since I use Dapper ](*,) 
I can hear the sound that comes from the microphone, but the applications donc't catch it.

---

### Post by patrick295767 on 2006-05-12
[QUOTE=hyg53]same for me. I can not call people anymore since I use Dapper ](*,) 
I can hear the sound that comes from the microphone, but the applications donc't catch it.[/QUOTE]
  
I have impression that Dapper is still rather BUGGY for this special sound recording,   hmm :-(
that 's not soo great ... Hope it'll be as great as previosu hoary & breezy :-)
  
Some bugs are fixed, but the problem is that others can be created !
  
I hope we wont arrive to the same situation of microsoft (i.e. XP)
were bugs and worst OS couldnt be thought to be possible ever with higher & newer OS versions. Ahhh Bill ... :neutral: 
  
Greetz

---

### Post by Sef on 2006-05-13
> I have impression that Dapper is still rather BUGGY, 

The biggest problem with Dapper has been the sound.  The AC 97  have had problems.   It's getting fixed though problems can still crop up.  I lost my sound after the most recent update and changed my preferences in sound to get it working.  Why did this act up now and not before, I don't know.

---

### Post by iNerdSure on 2006-05-20
It took me months from Breezy launch to get sound working for my laptop Acer4060. But recent updates to Breezy 5.10, on my Acer 4061 laptop, have created strange characteristics in the sound that is recorded through the laptop microphone or headset microphone. The sound is like a super low bass version of Darth Vader in Star Wars! :twisted: 

Sound when played from music CDs, or DVDs, sounds perfectly ok. Problem occurs only recording voice from laptop mic or headset mic, or during Skype calls, listeners thought they are listening to some deep voice "monster"! :confused: 

Anyone encountered similar problems or have suggestions on how to rectify this monster sounding voice. Thank you

---

### Post by abalone on 2006-05-21
AC'97, VIA 8237 on-board audio, quality pathetic and/or nothing works... ](*,) 

It has always been like that (Hoary, Breezy, current Dapper preview).

Audacity: I feel comfortable with this app, in Windows anyway. Records anything but the result is so distorted it's worthless. I compiled it with portaudio once but the resulting build was even less useful (because I'm a n00b l4m0r. I wasn't even sure what "portaudio" actually is. Or how to find out whether it's doing its thing, whatever thing that is.) 

Rosegarden4: No idea how to get that thing to record anything other than slightly staticy silence. That's when it doesn't lock up computer for good while loading, depending on what else is running (esd, jackd, artsd, whatever.) 

"JACK is losing sample frames." But what does it do with those it's not losing? 

Can I record any other applications or do they have to be jackified in some way?

Gnome Soundrecorder: Works!! Well - worked. Not working anymore. Now it won't let me record from "Capture" and instead switches to "Microphone" no matter what I tell it. Besides Mic, it also activates the input "IEC958 Playback AC97-SPSA" in the mixer. Right now I just want to record stuff I'm running on this computer. Is that too much to ask?

Those KDE toy recorders: Complain about something or other and/or record silence. I remember one of them once worked on some 9.x SUSE. 

Oh, and *playing* sound works fine, with everything, except at high volumes where it does get a tad more distorted than I'm used to from Windows. (Well, I don't have the equipment to test the surround sound stuffs.) 

I'm not sure I should blame Ubuntu since Linux in general never really worked all that well on any computer I tried it on and while fiddling got me dualhead and antialiased fonts and other such amenities I never made much progress with sound. Or suspend and hibernate. Or power saving. Or MIDI. 

I don't *want* to go back to Windows, though... 

I would consider buying a new soundcard if only I knew which *and could expect to get it to work*... :confused: (Look, it's making *me* use smilies. It's *got* to be bad...)

Well, as of now **42 users** said it worked for them. So what soundcards are they using? What software are they using?

---

### Post by Turtle.net on 2006-06-11
Hi,
Just to say that when I upgraded from Breezy to Dapper, the mic wasn't working anymore for skype.
Then, i tried to verify my settings using the application Sound Recorder ... and I never achieved to record anything.
But after enabling Mic as the capture device AND enabling Capture with max volume I was able to use my microphone with skype ... but not with Sound Recorder (and I don't care).

So, don't expect much from debugging using this application.

---

### Post by bilange on 2006-06-16
Ive been able to record with a microphone using skype, with a SoundBlaster audigy.

The problem is, you really have to use alsamixer (type in "alsamixer" in a console) to control most of your soundcard parameters correctly. Other mixers, graphical or not, seems to be incomplete as in they wont control much on the soundcard except the main stuff. (Or at least, this is the overall impression I have reguarding sound mixers)

Steps used to make it happen: 

1. Install Skype and skype_dsp_highjacker (sp?).
2. Type alsamixer in a console.  
3. Press the TAB key to switch from the "playback" settings to the "Capture" settings. Note that this will make the [ ] brackets move over Capture , so you have confirmation that you're currently messing with Recording/Capture settings, and _not_ playback.
4. Use only one of the following paragraph (Using both will give unexpected results):

a. If you need to record from a microphone (skype), mute everything except the microphone one (its called "Mic" on my setup), which needs to be maxed out.
b. Instead, if you intend to make a shoutcast server (aka "radio over the internet"), you need to mute everything except the PCM, Wave, or other synonyms, YMMV depending on your soundcard. Just remember though, if you want to use this same soundcard to talk over skype, having the PCM/Wave bar NOT muted will result in having echoes in the conversation. 


5. Optional: For convenience's sake, go back to "Playback" mode by pressing tab again, select the microphone and cut the volume. It's just to make sure the sound from your microphone wont be played back in your speakers.
6. Just quit pressing Escape. Sometimes you may need to hit Escape twice to really get out.
7. Test it out.

---

### Post by quicktime1 on 2006-06-16
I have a USB Samson C01U Mike and I cant get it to work either. The mixer recognises it correctly, but when I try recording I get nothing.

---

### Post by Turtle.net on 2006-06-18
Hi,
When you say 
[quote=bilange]
1. Install Skype and skype_dsp_highjacker (sp?).
[/quote]
first what skype_dsp_highjacker is ? and where do you find it (special repo ?)

---

### Post by Celestianpower on 2006-06-19
My problem is slightly different:

[LIST]
[*]I can hear sound fine - totem doesn't give me issues at all.
[*]I can record sound in Sound Recorder, but the selection defaults to "Capture" and I have to manually change it to "Microphone" for it to work
[*]Audacity and Skype don't work - "Error initialising Audio i/o player" and "Problem with sound device" respectively
[/LIST]

Can anyone help?

CP

---

### Post by Zimmer on 2006-06-19
[QUOTE=Celestianpower]My problem is slightly different:

[LIST]
[*]I can hear sound fine - totem doesn't give me issues at all.
[*]I can record sound in Sound Recorder, but the selection defaults to "Capture" and I have to manually change it to "Microphone" for it to work
[*]Audacity and Skype don't work - "Error initialising Audio i/o player" and "Problem with sound device" respectively
[/LIST]

Can anyone help?

CP[/QUOTE]
This link, post #3 will direct you to two good posts for sound problems that solve Audacity issues, and post #4 the comfort reply that at least one of them works.. :)
Audacity works for me...recorded a wedding the other week and then the church choir, through a Soundcraft mixer direct to the line in of the computer using Audacity with Ubuntu.

---

### Post by Oceola on 2006-06-23
I have an older Ensonic Card 1371, the Device manager identifies pretty near all the functions and I can either record using the "Sound Recorder" or use "Audacity."
In order to use Audacity I have to go to /System/Preferences/Sound/ and uncheck the block marked "Enable sound server startup", in order to return the system sounds I just recheck it after I've done with the Audacity Session.

It's a lot better than what I did in Hoary where I would go into the System Monitor and "End" the esd functions in order to use Audacity, I did leave the Mixer going though.:D

Edit: in order to save files in an mp3 format in Audacity you need libmp3lame.so for some reason this file didn't get automatically recognized by Audacity at first and if it's not in your system you can usually find it somewhere in Google Linux, just search for that file name but be careful what you download. Place it in the directory where Audacity wants to look for it.

---

### Post by bertschollaert on 2006-06-25
Hello,

I tried all of the above, but still my voice is not recorded in Skype. lspci gives me this for multimedia audio: 0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH 5R) AC'97 Audio Controller (rev 02)

in Alsamixer all are on and unmuted. Capture is on mic. 
I can hear sound fine. In WinXP all works well.
What else is there to try?

Thank you in advance

---

### Post by nekator on 2007-02-24
Has anyone managed to use skype on ubuntu Dapper Drake....AT ALL...

---

### Post by nekator on 2007-02-24
Oh well, I tried doing what Anill-robo recommended without any luck...Can anybody tell me WHY the hell would anyone go on to compile a program like Skype for Ubuntu when nobody seems to be able to use it in Dapper Drake? Why go through all that trouble...Once again I feel let down by ubuntu and "subnormal" when everybody else seems to be getting on with their life and enjoying their weekend. I suppose I&#314;l have to go back to windows in order to use Skype...

Not the best of days...crap.

---

### Post by ahaslam on 2007-05-06
Everything worked great in Dapper but it's all screwy in Feisty.
I can't capture the output from my sound card & even if I could, my audio profiles aren't recognised :mad:

---

### Post by mike4ubuntu on 2007-05-31
cannot record sound at all.  The simple sound recorder app allows me to press the record button, but nothing seems to be actually recorded.  No way to save file or play it.

---

### Post by eye208 on 2007-06-01
I managed to record sound and use Skype with Ubuntu on a C-Media onboard card, a Terratec card (Crystal chip) and a Centrino notebook.

Sometimes you have to tweak the ALSA mixer to find the right setting. Soundcard mixers have many options and can be quite confusing at first. Linux is no different from Windows in this matter.

If you have two soundcards in the computer, either switch one off in the BIOS or make sure ALSA assigns static indices to them so that they don't switch positions in a random fashion on boot-up. Keep in mind that some analog TV cards bring their own sound devices too (such as the Philips SA7xxx chips).

---

### Post by tquinnathome1 on 2007-06-18
I have no idea how to even use the Sound Recorder on my Ubuntu! I'd like to record music Internally, (y'know - without a Microphone, straight from a flashplayer and what not), I've heard it can be done, however I have no idea how to do it, and nothing online has been much help to say the least! :(

---

### Post by dabl on 2007-06-18
It took some fiddling and experimenting with the ALSA mixer, but it wasn't that hard -- nothing new needed to be installed, I just needed to figure out that obscure little GUI and its obscure little menu.  :D

p.s. Kubuntu's ALSA mixer is also non-intuitive, FYI.

---

### Post by icechen1 on 2007-06-18
No,thanks to Sigmatel and Hda-intel(ICH7) :( I want to record sound...
Already using ALSA 1.0.14 final and no result.
I can hear sound fine though.

---

### Post by ticopelp on 2007-06-18
I couldn't get sound recording to work at all in Ubuntu, and an hour's worth of searching the forum ended up with  almost all dead ends and unanswered questions, so I kind of wrote it off. So no.

---

### Post by KTULU23 on 2007-06-19
yes.. finally/ the sound recorder is now recording from the line in and in alsa mode..
/seemed like there was some confusion about which line in was in use, selecting "mic 1" or "mic 2" in the options seem to sort it..

ok.. now ive done more experimenting and i can record the computer output [playing and recording with alsa, using sound recorder and xmms]  

the preferences menu in the volume control window allowed me to make it show "main mix" and "mix mono" in the switches menu.. then i could choose em and rec.

seems bizarre that the option to record main mix isnt available as a default..

also that the sound recorder *usually* won't playback the recording untill its saved..

anyone know of any good hints on making jack work? im using ubuntu7studio and i think ive installed the files for jack.. someone suggested it might need to be "allowed" by ubuntu? 

cheeers

---

### Post by mybunche on 2007-06-23
Yes, using Sound Recorder on Ubuntu 6.10. Level was a bit down so opened Volume Control, edit preferences and checked mic boost (+20db), records nicely.
Would like to change the default save location though from /tmp. Using a Dell Dimension 1100 desktop, mic plugged in at rear.

---

### Post by oxalá on 2007-06-24
ugh.
i know this is a weak thing to ask, but why is this so hard?
not Linux in general, not Ubuntu, but recording sound in particular.

---

### Post by evtiest on 2007-07-23
No recording but after running alsamixer from the command line and adjust line (was 0) it was running fine

---

### Post by nlbs on 2007-09-15
> **ioannis.th said:**
> I got it!:) :) :) Just run alsamixer on the command line, (if you don't have it install it) and scroll to the right at the capture sliders. One which is turned down is hopefully for you. Me, I have a SB live! platinum and I can record my guitar by turning up the livedrive slider, and having pressed spacebar beforehand to activated. The strange part is that kmixer doesn't do the same although it has the same slider too.

Note to ubuntu devs. With all the respect guys, things like that shouldn't happen, I mean the whole situation about this 3 page thread along with its poll. At least not if you want to keep your distribution's status as "human" linux. It was working on hoary, and it is a feature needed by LOTS of people. I know ubuntu is free etc etc but when someone needs to record something quickly ( a musical idea for example )  and discovers recording doesn't work, he won't care much about ubuntu being free, he wants it to be useful too.
Hi! I've opened Alsamixer but What to do now ??
Plese Plese help me I am lost.
[IMG]http://img440.imageshack.us/img440/7742/screenshotneelzigmoydql6.png[/IMG]

---

### Post by tpedwards on 2007-09-18
I finally got it to work after playing with kmix (which breaks it) and alsamixer which worked and the Audigy 2 volume control which mostly worked. I agree with others, this is far too complicated. Then again, there are relatively few standards when it comes to sound hardware.

tpedwards
Huntsville, AL
:popcorn:

---

### Post by cleanbarn on 2007-09-30
I can record sound in Ubuntu reliably. It took several steps.

Quick Summary: a.) I compiled ALSA with usb_audio support b.) blacklisted snd_hda_intel the driver for the on board audio card c.) bought and use USB headphones with microphone

My laptop is a Gateway ML6703.  It has Intel High Definition Audio built in on the Motherboard.  ( by default uses the snd_hda_intel driver. To see which hardware you have use lspci, to see which drivers are loaded use lsmod  or lsmod | grep snd )

There is a problem with the HDA hardware and the ALSA drivers using a microphone.  Recompiling the latest stable ALSA ( 1.0.14 ) did not fix the problem for me. 

I compiled ALSA according to the instructions at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) 
except I added:  sudo ./configure --with-cards=hda-intel,usb-audio
complete compile instructions are at end of this post.
You might be able to skip this step and just black list the snd_hda_intel driver
and allow snd_usb_audio to be card "0"

I bought a "cyber acoustics" USB headphones with attached microphone.

I blacklisted the snd_hda_intel driver, note this disables the on board Intel HDA sound,
however this is necessary for Skype and other applications to see the USB sound device as  "card 0"

To blacklist snd_hda_intel driver
sudo echo snd_hda_intel >> /etc/modprobe.d/blacklist

(or edit the file /etc/modprobe.d/blacklist and add snd_hda_intel on a line by itself)

Allow USB Audio to be "card 0" edit the file  /etc/modprobe.d/alsa-base
and comment out the line that reads
options snd-usb-audio index=-2
by inserting a # as the first character so it reads
# options snd-usb-audio index=-2

Now reboot

Set the volumes back up they get re-set to zero when you change drivers

I could record using arecord -f cd -d 5 test.wav
and after a couple of trys I also got skype to work and make a test call.




Apendix: Compiling ALSA



My complete compile for ALSA looked like:


sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver-1.0.14.tar.bz2
sudo tar xjf alsa-lib-1.0.14a.tar.bz2
sudo tar xjf alsa-utils-1.0.14.tar.bz2

    *

      Compile and install alsa-driver

cd alsa-driver-1.0.14
sudo ./configure --with-cards=hda-intel,usb-audio
sudo make
sudo make install

    *

      Compile and install alsa-lib

cd ../alsa-lib-1.0.14a
sudo ./configure
sudo make
sudo make install

    *

      Compile and install alsa-utils

cd ../alsa-utils-1.0.14
sudo ./configure
sudo make
sudo make install

---

### Post by Peter Wagner on 2007-10-25
It took me some time to get Skype running int the direction off me. At the end I even don't know which of my mouse-in-a-labyrinth steps was the right one, I remember it was marking "input" as "line in", not "microphone in the "Sound Recorder" (I know it only in Czech, zaznam zvuku, it's the standard recorder in Ubuntu).

Beginning with Ubuntu 7.10 this application ceased working, warning me something like "check your multimedia settings" which I don't know what it means. The "sound" settings in System - Options? The hardware settings there?

Anyway, Skype is running well, so it's rather a problem of this application than of my settings. So I've just tried Audacity and everything is going fine.

So, at the end the pragmatic solution (I'm still not in favour of, but we're on Earth, not in heaven.

---

### Post by vwbug on 2008-01-09
No, can't record anything.  Sound works great as far as listening. But can't record. Wish there were some program like Polderbits for Ubuntu. Tried several programs, but no luck.

---

### Post by Gourgi on 2008-01-09
> **vwbug said:**
> No, can't record anything.  Sound works great as far as listening. But can't record. Tried several programs, but no luck.

same here :( i can't record anything.
my soundcard is onboard , see details [http://www.msicomputer.com/product/p_spec.asp?model=K8N_Neo4_Platinum/SLI]("http://www.msicomputer.com/product/p_spec.asp?model=K8N_Neo4_Platinum/SLI"). 
it is Creative sound Blaster Live 24-bit H/W audio 7.1 CH Surround Sound ,   if anyone wants to help me :icon_frown::icon_frown:

---

### Post by Nerdriot on 2008-01-10
I am... utterly... confused.

I've done, literally, everything suggested, and I'm at a loss.

I've changed setting in alsamixer, as suggested. I've also stopped other programs from using the audio, such as ESD and even volume control, which finally allowed Jackd to run and connect.

Now, when I run Sound Recorder, it says, "Your audio capture settings are invalid. Please correct them in the Mutlimedia settings."

Well, I'd love to do that, but I can't find the "Multimedia settings" anywhere. I saw someone post saying it was in System > Preferences, but I can't find it there. Sadface.

Usually, when I boot up, and try to run Ardour, it tells me that Ardour may already be running, or something similar, and then it closes. So, I have to disable ESD, and gnome-volume-control, just to get it to load. Then, I can load Jackd and connect things, but there's no sound when I record.

Heeeeeeeeeeeeeeeeeeelp.

---

### Post by Nerdriot on 2008-01-19
Bummmmmmmmmmmp.

---

### Post by cdtech on 2008-01-26
> **anil_robo said:**
> I've been working hard to get skype working with my voice in Ubuntu. Apparently there was a sound recording problem, and I never had encouraging results, except tonight. I am able to record sound now, sometimes. All I did was to set "capture" to "on" in the mixer.

 Here are the results:

1. Sound recording never worked for me with Logitech Quickcam for Notebooks (USB) built-in mike.

2. However, if I insert a conventional (jack) microphone in the soundcard hole, I can send sound "normally" to skype sound test service with the following conditions:
(a). I must never run the applications called "sound recorder" and "recording level monitor". Once I run any one of these, I can no longer record any sound unless I logout and relogin.
(b). I must never play a sound using XMMS which uses ALSA as its primary sound driver. Playing XMMS even once causes skype sound testing service to report "error in sound device".
(c). Skype must have selected the default sound device.
(d). In system sound mixer (double click the volume icon in panel), I must have selected my soundcard as "Intel ICH6 (ALsa MIxer)".
(e). The capture level for mike should be maximum, but the playback from mike should be zero.
(f). The capture level and playback level from "capture from capture" must both be zero.

Once all these conditions (a-f) are satisfied, I am able to record sound through skype sound testing service. Ubuntu sound recorder crashes it all! It simply freezes whatever sound recording I was getting previously! Same with XMMS.

If I want to talk to mom using skype, I have to do the following:

1. Restart the computer and log-in.
2. Start skype.
3. Select my mom's ID and press the call button.
4. Talk to her! :)

If I run Sound recorder, Recording Level Monitor or XMMS, skype fails 100% of the times!

And once skype fails, I can't get "any" playback or recording from the computer unless I restart.

It effectively means that I have to restart everytime I want to use skype, and I have to restart once again once I have finished using skype!

:(

Any ideas?


I have this same problem. If I want to use skype, I have to do a "sudo /etc/init.d/alsasound restart"
then it seems to work fine. If I open up the volume control or even alsamixer, my skype sound is inop. I have to restart alsasound again.

I can use the " sudo arecord -f cd test.wav " (to record from my headset mic) and it tells me somethings busy, but if I restart alsa, it works fine.

I'm thinking its a config problem that I'm overlooking but I'm so far into it that I'm starting to overlook small things now. I think I'll take a break for a couple of days and clear my mind. lol

---

### Post by cdtech on 2008-01-26
> **Nerdriot said:**
> I am... utterly... confused.

I've done, literally, everything suggested, and I'm at a loss.

I've changed setting in alsamixer, as suggested. I've also stopped other programs from using the audio, such as ESD and even volume control, which finally allowed Jackd to run and connect.

Now, when I run Sound Recorder, it says, "Your audio capture settings are invalid. Please correct them in the Mutlimedia settings."

Well, I'd love to do that, but I can't find the "Multimedia settings" anywhere. I saw someone post saying it was in System > Preferences, but I can't find it there. Sadface.

Usually, when I boot up, and try to run Ardour, it tells me that Ardour may already be running, or something similar, and then it closes. So, I have to disable ESD, and gnome-volume-control, just to get it to load. Then, I can load Jackd and connect things, but there's no sound when I record.

Heeeeeeeeeeeeeeeeeeelp.

Type in a terminal :
```
alacarte
```

and you can just add it to your drop downs. I put mine as a shortcut in my top bar (seems I'm always adding things).

---

### Post by Nerdriot on 2008-02-03
Ahh geez, I figured out the problem. It wasn't a Ubuntu problem, or a sound card problem. It was stupid human error.

I went into "setup" in Jackd to see if I was missing something. I'm using the RT kernel, so I set it to "Realtime", and then, I went to select my input/output. I never noticed the "arrows" to the right of the boxes, and when I clicked on the one beside "Input", I saw my usb microphone. I selected it. Then, went to volume control, to "file", and changed to my usb mic device, turned the volume up, and there it was. I was finally able to record.

I am an idiot.

---

### Post by cdtech on 2008-02-04
Awesome, glad you got it working.

---

### Post by cdtech on 2008-02-04
> **anil_robo said:**
> 
(a). I must never run the applications called "sound recorder" and "recording level monitor". Once I run any one of these, I can no longer record any sound unless I logout and relogin.
(b). I must never play a sound using XMMS which uses ALSA as its primary sound driver. Playing XMMS even once causes skype sound testing service to report "error in sound device".
(c). Skype must have selected the default sound device.
(d). In system sound mixer (double click the volume icon in panel), I must have selected my soundcard as "Intel ICH6 (ALsa MIxer)".
(e). The capture level for mike should be maximum, but the playback from mike should be zero.
(f). The capture level and playback level from "capture from capture" must both be zero.

If I run Sound recorder, Recording Level Monitor or XMMS, skype fails 100% of the times!

And once skype fails, I can't get "any" playback or recording from the computer unless I restart.

It effectively means that I have to restart everytime I want to use skype, and I have to restart once again once I have finished using skype!

:(

Any ideas?


I have the same problem I'm trying to work out now.  Rather than log out, try restarting alsasound:

sudo /etc/init.d/alsasound restart

Then things are back to normal.  Still working on this one.

Let me know if this works for you as well.

Thanks

---

### Post by luke16 on 2008-02-19
It works for me. Sometimes. When it does wok, the volume levels are incredibly low. Mic boost does nothing.

---

### Post by Yes on 2008-02-19
I could on my previous computer, never tried on my current one.  

It's a bit hard to tell how easy it was to get it working, I tried pretty much everything online trying to get it to work, until I figured out that my mic was broken.  My headphones worked the first time I plugged them in, but of course the quality wasn't all that great.  I'm not sure if that's because of Ubuntu or because I wasn't using a real mic.

---

### Post by pwn on 2008-02-19
Doesn't work

---

### Post by sonrock3 on 2008-02-20
Worked at 1st (soon after new install Ub 1.10, and after few simple sound settings adjusted)#
but then failed (after Xine + realplayer10 + Hexplay installed) - and attempts to fix have failed so far, inc:
reinstall Sound Recorder after total remove (altho never disappeared from menu)

Can hear sound OK via Realplayer + Rhythm box - inc. net BBC stream.

---

