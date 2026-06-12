---
title: "All I want to do is record from my soundcard :-("
date: 2009-05-03
forum: Multimedia Software
---

### Post by tropdoug on 2009-05-03
I am using Jaunty and cannot record any audio from the net, cd's or mic. I have installed, and reinstalled audacity a couple of times, none of the available I/O selections gives me any moving bars in the input monitor area, and when I press record all that happens is that the line jumps about 4 mm forward and stops. 

The gnome sound recorder sits there and does nothing period! 

Ardour won't work becuase of some problem starting Jack. 

all I want to do is record some audio from a talk on the net to listen to later. It should be simple but its driving me nuts. 

Can anyone help please.

---

### Post by tropdoug on 2009-05-06
Bump

---

### Post by adam_kimber on 2009-05-06
Welcome to Pulseaudio hell. I would say that in one of multitudia of settings that Pulseaudio has your mic is muted. I had this with my speakers when i upgraded. No sound whatsoever. Discovered my speakers were muted in one of the 'backend' settings in Pulseaudio. 

You need to install paprefs and padevchooser. 

When you click on the icon ...

[IMG]http://www.shucksmith.co.uk/fc8-PulseAudio-DeviceChooser.png/fc8-PulseAudio-DeviceChooser-full.jpg[/IMG]

...on the taskbar that had been added you need to go to Volume Control 

[IMG]http://www.students.ic.unicamp.br/~ra016378/PulseAudioVolumeControl.png[/IMG]

Looks a bit like this. Note the little mute icons. Check to see if under input devices this is not checked / highlighted.

If you get this screen you have clicked wrongly somewhere. Don't worry its designed to be confusing. :)

[IMG]http://www.shucksmith.co.uk/fc8-Screenshot-PulseAudio-Preference.png/fc8-Screenshot-PulseAudio-Preference-full.jpg[/IMG]

---

### Post by tropdoug on 2009-05-07
great info, tried it all, unfortunately not thing. The volume control shows the moving bars as the sound is picked up, but audacity just will not work, and the same for gnome recorder. Man this is frustrating. 

any other ideas?

---

### Post by Darth Buh on 2009-05-07
I'm very interested in this discussion- I'm having microphone issues as well.

I see when you have the Sink and Source selections yours is showing ALSA on hw0... how'd you get it to do that?  Mine shows only "Audigy 2 [SB0240] - ADC Capture/Standard PCM Playback.

I think there's an issue in PulseAudio translation, but darned if I can figure it out.

DB

---

### Post by Keyper7 on 2009-05-07
Ok, last post confused me. Are you trying to record from the mic or extract audio from a file?

If it's from a mic something's strange... when I had mic problems in the past the bars didn't move, showing it was disabled... apparently yours is enabled and being detected, then? Maybe it's a capture volume issue, how are the sliders in the volume applet?

---

### Post by adam_kimber on 2009-05-07
Hmmmm. Keyper7 might have a point. I was erring towards Audacity and Gnome Recorder not picking up the Pulseaudio signal. It is a go-between server thingy so its picking up the signal and being selfish and keeping it to itself. 

Try the following --> System --> Preferences --> Sound and set everything to Pulseaudio. See image below. 

[IMG]http://www.adamkimber.co.uk/images/screenshot-sound_preferences.png[/IMG]

---

### Post by Darth Buh on 2009-05-07
Yeah, mine is set up that way, however I can't get any audio to record from the microphone.

There is a test I saw to move the recording stream while recording something in Sound Recorder... when I move the stream to Monitor, it picks up audio.. when I flip it back to microphone, audio pickup goes dead.

DB

-edit- Actually, I don't get the option for a PulseAudio mixer like the image above.  I get 5 choices:

*Audigy 2 [SB0240] (Alsa mixer) - this one has all the different slider bars for Aux, CD, Microphone, etc
*Capture: Audigy 2 [SB0240] - ADC Capture/Standard PCM Playback (Pulseaudio Mixer)
*Capture: Monitor of Audigy 2 [SB0240] - ADC Capture/Standard PCM Playback (Pulseaudio Mixer)
*Playback: Audigy 2 [SB0240] - ADC Capture/Standard PCM Playback (Pulseaudio Mixer)
*SigmaTel STAC9721,23 (OSS Mixer)

and like I said before, there is nothing showing on hw0 or hw1 listed on that selection page...

Please let me know if you can think of anything, or need any more data listed.

---

### Post by tropdoug on 2009-05-09
ok, I tried that, re set audacity preferences to alsa : pulse and tried to record -- Audacity crashed I tried sound recprder -- it froze. 

so I went back to sound preferences and set it all to ALSA and tried again, same result. The I thought like Darth Buh I seem to have a lot of choices in my sound volume, or sound preferences set up (See attachments) and also when I did the tests all worked fine, except the capture test which resulted in the error box (attached) 

1st question - do I have conflicting peices of software for my sound card

2nd question, if the answer is yes then what do I do, and if the answer is no then what do i Do, (no pleasing me is there lol) 

Seriously I hope that someone can come up with an answer cos its nuts, All I want is to record a sound!

---

### Post by markbuntu on 2009-05-09
First of all, getting audacity to work with hardy is not so easy since it will not work with pulseaudio. First of all you need to set up the sound system properly. Go here for that.

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Then try this

Lets check if we can record. Leave rythmbox playing.
Open Applications/Sound and Video/Sound Recorder. Click the record button. In the PA volume control recording tab you should now see

gnome-sound-recorder: Record Stream.
right click on the volume bar and choose move stream and move it to the monitor of the output device you are using. Click stop in sound recorder and then record. Sound recorder should now be recording from rythmbox. Click stop. Change to the playback tab in the pavolume control. click the speaker on the rythmbox stream to mute it. click play on sound recorder. You should now see stream recorder in playback and hear what you just recorded.

Let's try recording from the microphone. Go back to the recording tab. click record on stream recorder and move the stream to the device instead of the monitor. Click stop. Click record again and make some noise into the microphone. You should see the volume bars move. Congratulations, you are now a recording genius.

You can make a device or monitor the default for new applications by right clicking on it like with playback.

If your microphone does not seem to be working Open the Volume Control from your panel ( the little speaker icon) and check that it is set to the proper device (your hardware). Click Preferences and make sure that the boxes for Microphone Capture and Mic Boost Capture are checked, close the box. In the Volume Control/ Switches check the Mic Boost Capture box. In /Recording make sure the Microphone is not muted (no red x on the mic icon) and turned up. (Some devices do not have a mic boost option).

If your microphone volume is very low even turned up all the way, click padevchooser/Manager. In the devices tab find under Sources alsa_input.pci........alsa_capture_0 or alsa_input_usb.... if you are using are usb device, click the Properties button. A new window will pop up. Try adjusting the volume to 150% or so. (This is a common problem with many dell laptops and others.)

Try recording again. If it still does not work check for any other mic switches or controls and play around with them.

Remember, it is the capture/recording settings that are important for recording. Playback settings get your mic to your speakers.

If you are still having problems with your mic it is most likely a problem with the alsa driver. This is a very common issue for laptop users and fixes are very hardware specific. You should try the first link in the troubleshooting section below or a forum or google search for your specific hardware.

I just cut the above from my guide for Jaunty but it should work for you. If you are still having problems or you want to get jack and ardour working or anything else sound wise go here, it is a very extensive guide for getting your sound dialed in

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by jjross on 2009-05-10
I use arecord to record the output of my sound card, if you can hear it coming out of your speakers this will record it.
The -d value is the number of seconds you want to record.
The -r value is the frequency or bit rate, I dont really remember which.
You notice the next section uses lame to make it an MP3 so make sure you have lame installed and the last part is where to save the file and the name of the file, the code I have on the end names it the date, hour and  minute so there cant be duplicate file names.
Just paste the code below into a text editor (I use Gedit) save it and make it executable and when you start it it will record the output of your sound card and save where ever you told it to.
You can also just run this in terminal, just change it to suit the location you want it saved to

> #!/bin/bash

# sound recorder

arecord -d10600 -r16000 -c1 | lame -b 64 - /home/jim/Radio/$(date +%Y-%m-%d-%H%M).mp3

---

### Post by Darth Buh on 2009-05-10
Nope, tried all of that, still no fix.

The recording from Rhytmbox works smoothly, but when I move the recording stream back to the capture device, it gets nothing.

Here's a wierd thing.

I enabled Mic Select- it defaults to Mic1.  Fine.  My microphone has a mute switch on the cord.. I turn it off, and blow into the mic, and I hear blowing in my speakers.  When I go into Preferences, and toggle it to Mic2, I can't hear blowing anymore.  Toggling it back to Mic1 brings it back to the current state.

Any ideas?

DB

---

### Post by Darth Buh on 2009-05-10
Okay, I installed the ALSA 1.0.19 from the 2/25/2009 upgrade repository.

Upon rebooting, I actually get sound when Gnome pops up upon login.

I get sound playback still; good.

Sound Recorder will not record from the microphone, still.

Audacity will record from the microphone when set to "ALSA Audigy 2 [SB0240] Mic Capture (hw:0,1).... kinda...

It records me like sounding like a chipmunk, and only for like 1 second, regardless of how much hooting and holering into the microphone I make.

Stranger and stranger....

DB

---

### Post by Darth Buh on 2009-05-11
Actually, I just gave up.

Downloaded a copy of 8.10 32-bit, full wipe of the HDD's (raid0 ^_^) and fresh install.

Oh, the issue might have been that Alsamixer only works for PulseAudio...

I found that "alsamixer -Dhw" allowed me to actually interface with my card's settings, and get it turned up to where it should have been on the recording.  Still, it's showing hw:0 on this version of PulseAudio and Alsa, and 9.04 did not.

Thanks for the support!  I wish these PulseAudio bugs would get polished off, or they'd just do away with the darn thing.

DB

---

### Post by adam_kimber on 2009-05-11
Tell me about it!

---

### Post by Darth Buh on 2009-05-11
Speaking of Audacity, I was looking at my now 8.10 config and also my wife's 8.10 config, and remembering what I saw in 9.04.

Curiously, when I open Audacity's preferences, the two default recording and output devices are listed as "OSS: /dev/dsp".  Also, when I'm using Ventrilo through Wine, I go under Mixer Track in Intrepid and it shows "PulseAudio Virtual OSS".

I didn't see this in 9.04... maybe a component is missing?

DB

---

### Post by tropdoug on 2009-05-21
BUMP!

I am going bald, thru tearing my hair out, this is one issue wqith Linux that is almost making me cast my eyes back to windows.

Desire -- to record sound being played from a website via audioacrobat to my system. 

Seems a simple enough idea

except, I cannot understand the spaghetti junction of applications,. terminology and settings, so in the interests of helping out probably many thousand of frustrated  users.

will someone tell me what the follwoing are and what I Actually need to play sound and record sound from my Nvidia CK804 sound card.


[LIST=1]
[*]What is "JACK" and what does it do?
[*]What is PULSE AUDIO and what does it do
[*]What is ALSA and what does it do
[*]What is Audacity and why will it not register sound being played from my sound card no matter what setting I choose for input source
[*]What is Ardour and why does starting Ardour completely silence all forms of sound from my sound card
[*]Why when I start Ardour will JACK not start if there is sound already being played back.
[*]Why do I have so many sound apps after following the threads on setting up sound in Linux -- What do I need and what is superfluous (see Attached image)
[*]Why do I have so many weird things in my volume control? My hardware is 1 sound card and 1 webcam USB with internal Mic -- thats IT (see attached Image)
[/LIST]

Please please help me before I crack and go back to those awful days  pleeeeeease!

---

### Post by warroomcbw on 2009-05-21
For me...it all works fine.
I have no built in mics.
In windows I had an option to record through line, mics, or stereo mix.
I only get the option of mic with jaunty.

If I want to record off my soundcard I have to physically use a jumper cord from my headphone jack to my mic jack.

Am I missing something to let Jaunty "see" my soundcard or is that just the way it works with no "stereo mix" option.


cbw

---

### Post by markbuntu on 2009-05-22
> **tropdoug said:**
> BUMP!

I am going bald, thru tearing my hair out, this is one issue wqith Linux that is almost making me cast my eyes back to windows.

Desire -- to record sound being played from a website via audioacrobat to my system. 

Seems a simple enough idea

except, I cannot understand the spaghetti junction of applications,. terminology and settings, so in the interests of helping out probably many thousand of frustrated  users.

will someone tell me what the follwoing are and what I Actually need to play sound and record sound from my Nvidia CK804 sound card.


[LIST=1]
[*]What is "JACK" and what does it do?
[*]What is PULSE AUDIO and what does it do
[*]What is ALSA and what does it do
[*]What is Audacity and why will it not register sound being played from my sound card no matter what setting I choose for input source
[*]What is Ardour and why does starting Ardour completely silence all forms of sound from my sound card
[*]Why when I start Ardour will JACK not start if there is sound already being played back.
[*]Why do I have so many sound apps after following the threads on setting up sound in Linux -- What do I need and what is superfluous (see Attached image)
[*]Why do I have so many weird things in my volume control? My hardware is 1 sound card and 1 webcam USB with internal Mic -- thats IT (see attached Image)
[/LIST]

Please please help me before I crack and go back to those awful days  pleeeeeease!

For 1,2, and 3 read this

[http://ubuntuforums.org/showthread.php?p=5931543](http://ubuntuforums.org/showthread.php?p=5931543)

For 5 and 6 go here and look in the UbuntuStudio section

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

For 7 and 8 look in the Sound Server setup section

For audacity read the special note on audacity in the Application Specific.....section.

---

### Post by tropdoug on 2009-05-25
Phew markbuntu you sure do provide a heap of information, now as well as reducing hair content I have a headache as well ;)

Thanks for all your work, man you sure have a handle on all these apps, servers, levels etc. Most of the technical stuff is a bit over me, but at least with your threads there is a great place for me to slowly work my way through it. (loved the traffic cop analogy)

I think for now I should uninstall and purge all the sound programs that I don't need or that probably do not work with what I want to do. (audacity in particular) PS - when I want to remove all the configuration files of a program, but synaptic tells me that I have to remove gnome desktop too, does that mean I just have to accept that I cannot get rid of the config files from the program I dont want?

Then I think I shall download Ubuntu Studio and load it into a spare partition I have and see if I can set that up as a sound specialised system, and bit by bit build on the other apps that I use such as kompozer, office and gimp. I dont play games so wont need anyhting along those lines, and since my idea of a computer is that it should be a tool of communication and productivity perhaps I should include a good desktop editor and skype (if I have to) Does Linux have its own skype equivelant? and then perhaps I shall be able to do what I want. )hope it doesn';t take me too long though)

Once again Markbuntu my most grateful thanks. I may yet have more questions, but for now I must study and learn. 

Douglas

---

### Post by markbuntu on 2009-05-26
the gnome desktop is just a sort of meta-list of installed applications to aid recovery. You can reinstall it after you remove those apps and it should not try to reinstall them.

If you have a spare partition that is a great idea. You can remove all your web browsers and email and all the other distracting crap and when you want to do audio production you will not be tempted to goof off and your system will run faster. You should also get Boot up manager (bum in the repos) and use it and System/Adminstration/Services to remove or turn off all the kernel services you will not be needing which will also speed up the kernel and boot time and not slow things down at critical times. You can also set update manager to manual control so it will not decide to automatically look for updates during your live recording session.

You are entirely welcome. Audacity is pretty good but not nearly as good as what you can do with rosegarden/hydrogen/ardour/jack and all the other jack stuff.

best regards,
mark.

---

### Post by tropdoug on 2009-07-09
well a long time has gone by and I am still no nearer a result. In desperation I installed the "ask & record" toolbar in my Win XP virtual box and bingo as easy as that I can record any audio or video playing on the web. Then having recorded it, I save it to my usb stick as an mp3. Now I can open it in audacity and the playback works fine, and I can edit it, if I want. BUT I still cannot get audacity to "hear" the sound streaming from the web. Funny thing but I tried to use Kno last night and it crashed due to a sound malfunction, and I now know that I have to have JACK to use with Kino, and as I already know JACK will not load, but the error message is useless. Man this is realy hard to take.

---

### Post by BubbaBlues on 2009-09-17
I've been trying to get streaming audio to record for several days to no avail. I was really hoping to find an answer here.  Alas I'm afraid there just isn't one.  I love Linux but it has some real serious shortcomings when it comes to audio.  Not even in the same league as Windows.  well maybe some day someone will come up with some hardware and some software that actually work together like they're supposed to.](*,)

---

### Post by markbuntu on 2009-09-17
If you want to record streaming audio, like a shoutcast or radio station then just get streamripper (kstreamripper for KDE). It is very easy to use.

The biggest problem with linux is too many choices, also its biggest advantage.

---

