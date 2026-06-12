---
title: "Intrepid 8.10 - No mic saga (Skype etc)"
date: 2008-12-09
forum: Multimedia Software
---

### Post by ShepHeard on 2008-12-09
Hi there,

let me give you guys a little history: Basically, for some reason I can't use our router at my new home with Windows, but it works fine with Linux. So, I decided to resurrect my moth-balled Ubuntu partition. (Ironically, it was seemingly unresolvable problems with networking (wired at work, wireless at my old home) that led me to, regrettably, revert back almost entirely to Windows.)

I did a clean install of Ubuntu 8.10 (I'm now at UCT in SA - >600 MB in less than 30 sec!!) and loved the reworked networking help thing. Connected no probs both to wireless and wired. Excellent!

Now, having just moved from France/UK to South Africa, I thought that maybe Skype would be a good idea to try. ... Oh dear.

I dutifully installed Skype and bought myself a funky headset. 

However, Skype at first gave me the "*problem with audio playback*". I had a good look around these fora, and tweaked a few things and seemingly got past that. 

Then, during the test call, it just would not record my voice.

**_Problem 1:_ If I play with the Skype Audio settings too much (i.e. trial and error trying every combination of input device) Skype crashes.**

Either way - I could not get it to record, and with some of the options I get the "*problem with audio capture*" error.

So, I searched everywhere on various fora and tried various tricks and tweaks.

I tried:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

nothing

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

still no joy

[http://ph.ubuntuforums.com/showthread.php?t=956302](http://ph.ubuntuforums.com/showthread.php?t=956302)

as far as the bit where he says:

> if not. Click on the next tab, probably something like 'recording' and do the same.

If not. Check under options. In my case there were two Input sources. 

However, I'm not sure which options her refers to, as there are none in the window we're looking at at this stage.

So, I tried:

[http://ph.ubuntuforums.com/showthread.php?t=997506](http://ph.ubuntuforums.com/showthread.php?t=997506)

too - still nothing...! Gah!

This isn't just a problem with Skype, because I can't get the PulseAudio input monitor to register anything with either my headset or system mic. 

So, **_Problem 2:_ I can't get my mic to work in Ubuntu 8.10**

Additionally, **_Problem 3:_, when I try the various options in System/Preferences/Sound/Sound Capture and click test, either I occasionally hear a crackle and then nothing or most often I get the "*Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'*" Error, and then the Sound application crashes and I have to kill it.**

I realise this is a long post, but I just want to show what I've tried. This is the problem with Ubuntu, and one of the reasons that people will give up on it, unfortunately. I litterally spent five hours yesterday evening trying to get Skype to work, and still couldn't, and far too frequently programmes would crash.

From reading several posts the problem seems to be linked to PulseAudio, and the fact that Ubuntu have been a bit slack in integrating it... I love Ubuntu, and hope that you guys can help me out.

Cheers - Shep!

PS - I have a HP Compaq nx6325.

---

### Post by mgangav on 2008-12-09
Smashing. I have the same problems. My front mic is just not working, even after trying all those aforementioned solutions.

---

### Post by ShepHeard on 2008-12-09
Haha - we're definitely not alone..!

Just to say, I can't get anything out of the mic - when I try and test it with sound recorder either it does nothing and crashes or says my sound setup is invalid... 

Gah - this is really really irritating as I'm paying for a Skype account I've no way of using..!

---

### Post by ShepHeard on 2008-12-09
**_[COLOR="Red"]!!EDIT - This may work, but see my post below...!![/COLOR]_**

Solved! (For me anyway..!)

So, after easily 12 hours of continuous searching, tweaking and general ball-ache, I've got it (skype) working. 

In the end I **uninstalled pulseaudio**. (OK, there may be problems with future distros, but hopefully Ubuntu will have solved the integration problems by then... (I'm sure pulseaudio's great, but if it breaks my PC then it's gotta go..))

I tried (as per [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6149347&postcount=51")) to just stop it loading, but it didn't work. (Sorry psyke83, nice idea, but no joy)

So, I did the following: (as per [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=973637&highlight=skype") thread - Thank you DSCP46 *et al*.)

```
sudo apt-get remove pulseaudio
sudo apt-get install esound

sudo rm /etc/X11/Xsession.d/70pulseaudio (You may want to back this up)
```

then

Under **System -> Preferences -> Sound**
Make sure they are all set to 'Autodetect'.
The only one you will have to set manually to ALSA is 'Sound Capture' under 'Audio Conferencing'.
Note at this point Pulseaudio is now nolonger an option under these drop menus.

Under **System -> Preferences -> Sessions**
Deselected or Remove the Pulseaudio Manager

then

```
cd ~
rm .asound* (Again! You may want to back this up)
```

(you may need to rm /etc/asound.conf too)

Then, just to be sure pulseaudio was gone, and 'cos a few people said it hung around, I did:

```
sudo apt-get --purge remove pulseaudio

sudo apt-get autoremove

sudo apt-get remove pulseaudio-utils
sudo apt-get remove pulseaudio-module-conf
sudo apt-get remove pulseaudio-module-hal
sudo apt-get remove pulseaudio-module-x11
sudo apt-get remove libpulsecore5
sudo apt-get remove gstreamer0.10-pulseaudio
sudo apt-get remove libpulse-browse0
```

Then re-booted, and checked the ALSA settings by going

```
$ alsamixer -Dhw
```

Cool - Skype passed the echo123 test, and I could hear my voice. Granted there was a lot of noise, but I'm infinitely further forward then I was earlier this evening (and one step further from Windows...)

I'll report back if I experience any problems, have any other ideas etc.


Cheers!

---

### Post by ShepHeard on 2008-12-11
Gah. OK - scrap that - it worked fine for one whole evening.. I spent about 40 happy minutes speaking to my girlfriend last night when suddenly the mic cut out. 

I'm now back to square one - nothing's changed but my mic won't work and sound capture just crashes...

Any ideas?? Please help! Why would the mic suddenly fall over? 

I may re-post this as a new thread.

---

### Post by ShepHeard on 2008-12-12
So, just to update - I gave up on that install of 8.10 - I got to the point where I couldn't remember what I'd done any more. So, I did a clean install, and tried, first of all, every possible permutation of the settings in System>Preferences>Sound and Skype. Still nothing. Nada. Each time I tried Sound recorder, it crashed. No mic in Skype.


So. I uninstalled Pulseaudio completely again. Then I followed [[COLOR="Blue"]these[/COLOR]]("http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/") instructions to make sure ALSA was set-up properly.

Again - Skype now works, though I don't think the mic quality is great. Again - I'll see how long this 'fix' works.

However, can someone please tell me, why does the internal mic not work for so many people??

---

### Post by Mephi on 2008-12-12
I'm having the same issue, no Mic in skype. 
Tried this, tried all of the above. Nada...

Mephi

---

### Post by ShepHeard on 2008-12-12
Well, the mic's working, but the sound quality is terrible. People can only hear every other word I'm saying as there is loads of background noise. It's like there's an overkill on the gain, yet there is no control to set the gain. 

Can anyone out there help?? The sheer volume of posts reporting these kind of issues suggests it's not a minor problem. Worse, while one fix will work for one guy (i.e. updating/tweaking ALSA etc) it does nothing for the next. Could I ask - who has Skype and PulseAudio working?

I might try and hunt down an older version of Ubuntu and see if that solves it. I'm not sure though - now I've completely erased PulseAudio yet the recording quality's rubbish. There's no problem with playback though. 

It's kind of a race to see what I can fix first - Ubuntu's sound recording problems or my Windows internet connection issues... Come on Ubuntu!! I need Skype to speak to my girlfriend as she's in France and I'm in RSA... Help me keep my relationship going!!!

---

### Post by ShepHeard on 2008-12-14
OK. Update - I followed [[COLOR="Blue"]these[/COLOR]]("http://ubuntuforums.org/showthread.php?t=962695") instructions to make sure the ALSA drivers etc were up-to-date. 

I then set the mic boost to about 50% which seems to have fixed the mic quality problem...

As before, I'll see how it goes...

[Hmmm, this request for help is becoming a bit of a blog... :o) ]

---

### Post by BentSlightly on 2008-12-29
How did it go?

---

### Post by Olnex on 2008-12-30
Same problem here, mic works in 8.04, but not working in 8.10, I'm now using OpenSUSE 11.1 and mic works, Ubuntu's greate, but they cannot even make mic working which used to be working.

---

### Post by B Crowther on 2009-01-04
I give you every sympathy, I have been down this road.

Pulse Audio barks like a dog, and is certainly messed up. In all previous versions of Ubuntu I have used my front microphone jack for Skype, just plug in my headset when needed. In 8.10, if I plug the mike in, all sound dies, and I need to reboot to get it going again (there is probably a command I could run to restart the sound server, but I don't know what it would be).

Even murkier, the regular Skype program won't get any sound in Intrepid.

BUT, Skype-static-oss is in the Medibuntu repos, "This package contains the "static-oss" Skype variant, which ships its own Qt4
libraries instead of using the ones available on the user's system, and uses
the Open Sound System (OSS) instead of the Advanced Linux Sound Architecture
(ALSA).", and it works beautifully, so long as I don't use the front mike jack!

Regards,
Bruce.

---

### Post by ShepHeard on 2009-01-12
Hi all,

thanks for your replies - sorry I've not replied sooner, but New Year's holiday, plus the girlfriend who was behind this whole Skype thing is over to visit..

Anyway - in all honesty, the experience so far is mixed, and largely illogical.

Whilst I was in the midst of these Ubuntu problems, I also thought I'd give another variety of linux a go. I'm sure that I'd read that Fedora had in been more pro-active in their integration of Pulse Audio, so I created myslelf a KDE-Fedora 10  live USB key (what a great thing that is - an operating system on a pen-drive. If only we could get around the 2Gb persistant memory limit it would be perfect). 

I installed Skype, and, out-of-the-box... All the same problems... However, as suggested in one of the links above, I first tried 

pkill-all pulseaudio

and it worked with Fedora whereas it had no effect at all in Ubuntu. However, the sound was only mono after that. (This, I guess, could be fixed by optimising the ALSA drivers etc..??)



But, back to Ubuntu.

Despite all I have done, my success is, at best, erratic. 

To be fair, to a large degree it does work now, but it has been a massive hack.

However, sometimes is doesn't. For no reason other than the fact that I tried on a saturday rather than a sunday, or maybe the changing position of Jupiter in Scorpio.

It's difficult to report as a bug, as the symptoms are often different and irreproducible.. 

Often, if the mic doesn't work, I simply ctrl+alt+backspace and this clears it. However, sometimes it doesn't. In which case even switching off, unplugging, removing the battery and completely re-booting does nothing. I just have to wait for the astrological conditions to improve.

I also have to be sure that I have my headset plugged in when I boot up. Otherwise sometimes (but by no means always) when I plug the headphones in the speakers don't cut out. 

I don't really understand, as I don't change the settings or anything. 


Thanks for the suggestion re Skype-oss - I've not tried it yet, but I'll be sure to when I get the chance, though to be honest, now that I've got it working after a fasion, I'm wary of playing around too much more.

It's a shame that I feel my Ubuntu is so 'delicate', but there we go. I'll persevere, but I hope by the next release the sound integration is more 'robust'.

I fully expect that this problem may be HP Compaq nx6325-specific, but even a cursory glance around Ubuntu, and other distro fora shows this porblem to be fairly common-place.

Until these things are fixed I guess Ubuntu, and linux in general, cannot truly target Windows users who have become accustomed to plug-and-play. 

Don't get me wrong - I love my Linux partition, and I love getting 'behind the scenes' so-to-speak,  but sometimes I need things to just work.

Hopefully this won't elicit the same kind of arrogant response that [this]("http://www.matusiak.eu/numerodix/blog/index.php/2008/12/19/linux-audio-confusing-as-ever/") poor guy got! 


Well - that's all for now.

Comments/Tips/Suggestions all welcome - Happy 2009 one and all.

:o)

---

### Post by ShepHeard on 2009-01-23
Just a little update on things I've noticed.

Sometimes, when making the skype test call, the mic will not record, yet there will be clicking noises as I mute and unmute the input vol, and digital input volume. This is infact because under the swithces tab, the 'mic' check box has been mysteriously become unchecked. 

The other night, I was using skype, and then, foolishly, I started Firefox during the call. after a moment or two, the mic failed in Skype, and the only way to get it working again was to shut down the laptop, AND remove the battery. 

I thought the ALSA mixer could handle multiple applications using the sound card?

---

### Post by sihelset on 2009-01-24
Hi, and thanks for this thread. I have Ubuntu 8.10 x64, got into trouble with skype,..tried a lot of things, nothing worked except this receipt...

---

### Post by pixies7 on 2009-01-25
The solution of ShepHeard worked fine for me.

I have an HP DV7 1140EB, running 64-bit Intrepid Ibex

First I had no sound at all, therefore I added irqpoll to kernel command
See [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4140](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4140) and [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4117](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4117) on Alsa-project and see [http://ubuntuforums.org/showthread.php?t=799842](http://ubuntuforums.org/showthread.php?t=799842) [^] to see how to add the irqpoll 

Then I finally had sound (after one week of struggling, compiling new kernels, installing new drivers, ...).

Then I still had no microphone, but wit this thread I have resolved my issue, my internal mic as well as an external mic work fine

Thx guys.

---

### Post by ShepHeard on 2009-01-25
Hi - cheers for your replies! If my struggles can help a couple of others, it makes it all a little easier to bare..! :)

Please do let me know how you get on - I'm particularly interested in how stable your 'hack' is, and whether you experience some of the same problems as me...

Just to say though - I don't want to take any credit for the actual solutions, I'm just trying to bring them together in one place, and sharing my personal experiences. 

Good luck - Happy Skyping! ;)

---

### Post by ShepHeard on 2009-01-28
I noticed [here ]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")that soundcheck has released a new script to update ALSA to the lastest version. 

So, I did that, and then Skype completely fell over. So, I tried B Crowther's suggestion and installed the skype-static-oss package. This reinstalled the dreaded Pulseaudio at the same time, but I have to say, so far it works... However, the Skype audio quality seems to have taken a hit. 

I'll report back on how stable this solution is.

S

---

### Post by Captaingracekidd on 2009-02-07
Hi, I also had problems getting the mic to work in Intrepid, i tried messing around with the .asoundrc file as this post suggested ([HTML]https://bugs.launchpad.net/ubuntu/intrepid/+source/pulseaudio/+bug/295832/+viewstatus[/HTML]) but it left me with a skype that would open for 1 sec and then shut down.

Then I found this post [HTML]http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/[/HTML] and it worked!! 

Im not sure if this will mess up other stuff for me as Im a kind off living on the edge cracking away kinda intermediate at ubuntu. 

Hope this helped someone.

---

### Post by am15 on 2009-02-08
I have updated alsa, hacked pulseaudio and skype from an earlier thread but still my webcam mic is not being detected.  Is the only to remove pulseaudio and use esound?  Has anyone found a way to detect usb mic with pulseaudio working?

---

### Post by ShepHeard on 2009-02-10
As a general update, I'm still not convinced by the Skype-oss solution; it still crashes if I use another sound-using programme (including firefox), and requires a complete reboot to work. However, I'll wait a while before I abandon 8.10 (though I may give openSUSE a try, just to see how laptop/distro-specific these problem are).

However, it does seem more stable - i.e. I can see a reason for it failing.


IMPORTANT - I found out that Ubuntu defaults to having the mic muted, so it's important to toggle the mute swith using the sound manager (double click the volume icon, go to the second tab and check the microphone slider - see that the second icon underneath is not muted).


am15 - To be honest, I'm not convinced that your problem is pulseaudio-related. Back when I was having all these problems, if I used my flat-mate's webcam the built-in mic worked fine. My pulseaudio problems all stemmed from my on-board sound. Rather, you may have driver issues - have you tried searching the forum with your make and model of webcam?

---

### Post by exazonk on 2009-02-11
After a clean install of Ubuntu 8.10 and skype, and then updating everything, skype didn't work out of the box. However, after playing with various combinations of the different sound options it started working without problems. The biggest thing for me was finding the mixer panel, adding two mics and turning the capture volume all the way up.

This was also on a Dell D830 which has no internal microphone, so I had to use an external microphone (mic).

Before using skype it is important to use Gnome's default sound recorder as this has a mic level graph which gives you instant feedback on how well your microphone is working.

---

### Post by barretr on 2009-02-12
See: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/147298/](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/147298/), particularly: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/147298/comments/26](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/147298/comments/26)

I have an Acer notebook, in my case, adding the following line to: /etc/modprobe.d/options (open with root access) & rebooting fixed the problem.
```
options snd-hda-intel model=acer position_fix=1 enable=yes
```

Hope that helps - I was tearing my hair out with this one.

Many thanks to Turion for their solution.

---

### Post by naeem.ally on 2009-02-18
Hi

I have a t61 and after reading quite a few posts i made this change and it worked for me.

1.go to System > Preferences > Sound
2.under the "device" tab there is a field Sound capture
3.change the drop down list to HDA intel AD198x Analog (ALSA)

Under Volume Control i set the volume for Capture to full, it stills shows that its mute but it unmutes itself while making a call on skype.

---

### Post by florinm on 2009-02-20
Hello,

I've had the same problem with microphone. At first, my microphone didn't worked in either sound recorder and or Skype test call. After following some tutorial, posts, etc (where so many, I can`t remember which one, or what I have done to my sound settings), my microphone worked  with sound recorder, but not in Skype. Now Skype is working because I've changed the order of the input devices (right click on volume icon,Open volume control, Options, "first" Input device set on Front Mic, "second" Input device set on Mic).
Now I can hear my voice recorded with Skype test call, but not with Sound Recorder. Probably changing the order of the Input devices will inverse the situation.
I should mention that I have a Asus X55SV Series laptop.

---

### Post by pfaltynek on 2009-03-02
> **barretr said:**
> See: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/147298/](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/147298/), particularly: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/147298/comments/26](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/147298/comments/26)

I have an Acer notebook, in my case, adding the following line to: /etc/modprobe.d/options (open with root access) & rebooting fixed the problem.
```
options snd-hda-intel model=acer position_fix=1 enable=yes
```

Hope that helps - I was tearing my hair out with this one.

Many thanks to Turion for their solution.

Which model of Acer concrete do you have? I'm trying to get this work on Extensa 5620 but still no result :(

---

### Post by barretr on 2009-03-02
I don't think the model type matters. Are you using the same sound hardware(hda-intel)?

---

### Post by pfaltynek on 2009-03-02
> **barretr said:**
> pfaltynek, I don't think the model type matters. Are you using the same sound hardware(hda-intel)?

Yes, I'm sure my sound HW is HDA Intel, ALC268 Analog

Are necessary any prerequisities to make it work? (Upgrade alsa, backport or restricted modules ...)?

---

### Post by barretr on 2009-03-02
Are you receiving the following message when you click 'Test' under Sound Capture in Sound Preferences?:
"Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'"

Upgrading ALSA couldn't hurt, but I was still receiving that error after doing so.

---

### Post by pfaltynek on 2009-03-02
> **barretr said:**
> Are you receiving the following message when you click 'Test' under Sound Capture in Sound Preferences?:
"Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'"

I was still receving this error after upgrading ALSA.

No, I' have no error message for testing Capture in Sound Preferences.

My alsa-utils package has version 1.0.17 if this should be helpful...

---

### Post by barretr on 2009-03-02
pfaltynek, have a look at the following how-to - if you haven't done so already: 

[http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)
[http://ubuntuforums.org/showthread.php?t=843012&highlight=microphone](http://ubuntuforums.org/showthread.php?t=843012&highlight=microphone)

Are you using the onboard mic? If so, you might try an external mic instead.

---

### Post by Bogdanovist on 2009-03-15
This may be an irrelevant point but several people in this discussion (and similar) have pointed out that GNOME defaults to muting the microphone and 'PC Speaker', which on my laptop (Toshiba Satellite) appears to correspond also to the front headphone jack.

I was getting the 'problem with audio playback' error trying the skype test call, so I tried a bunch of the suggested solutions to no avail. I then re-installed (I have very little data stored locally so this is no big deal for me) and check the GNOME sound settings. Sure enough when I removed the default muting of the PC Speaker and microphone Skype now works fine (I'm runing 8.10).

I'm sure many of you have done this simple step and are still having problems, but for anyone reading this, I'd make sure you check this first, would have saved me much time (and avoided feeling like a putz when I found the simple silly solution. #-o).

---

### Post by MrSnowmiss on 2009-03-15
..

---

### Post by pfaltynek on 2009-03-15
> **barretr said:**
> pfaltynek, have a look at the following threads(if you haven't done so already): 

[http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)
[http://ubuntuforums.org/showthread.php?t=843012&highlight=microphone](http://ubuntuforums.org/showthread.php?t=843012&highlight=microphone)

Are you using the onboard mic? If so, you might try an external mic instead.

Thank you for provided links. I have solved this issue by installing Ubuntu 9.04 + upgrading alsa using the script from link you provided. Now I can sucessfully use Skype on my laptop without need of external mic.

---

### Post by bdelacey on 2009-03-18
Thanks, barretr, for your posts - helped me get both internal and plug-in microphone working with an Acer Aspire and Ubuntu/Linux 2.6.27-11

---

### Post by barretr on 2009-03-29
Glad those threads were of help. :)

---

### Post by jaypmcwilliams on 2009-11-17
> **ShepHeard said:**
> **_[COLOR="Red"]!!EDIT - This may work, but see my post below...!![/COLOR]_**

Solved! (For me anyway..!)

So, after easily 12 hours of continuous searching, tweaking and general ball-ache, I've got it (skype) working. 

In the end I **uninstalled pulseaudio**. (OK, there may be problems with future distros, but hopefully Ubuntu will have solved the integration problems by then... (I'm sure pulseaudio's great, but if it breaks my PC then it's gotta go..))

I tried (as per [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6149347&postcount=51")) to just stop it loading, but it didn't work. (Sorry psyke83, nice idea, but no joy)

So, I did the following: (as per [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=973637&highlight=skype") thread - Thank you DSCP46 *et al*.)

```
sudo apt-get remove pulseaudio
sudo apt-get install esound

sudo rm /etc/X11/Xsession.d/70pulseaudio (You may want to back this up)
```

then

Under **System -> Preferences -> Sound**
Make sure they are all set to 'Autodetect'.
The only one you will have to set manually to ALSA is 'Sound Capture' under 'Audio Conferencing'.
Note at this point Pulseaudio is now nolonger an option under these drop menus.

Under **System -> Preferences -> Sessions**
Deselected or Remove the Pulseaudio Manager

then

```
cd ~
rm .asound* (Again! You may want to back this up)
```

(you may need to rm /etc/asound.conf too)

Then, just to be sure pulseaudio was gone, and 'cos a few people said it hung around, I did:

```
sudo apt-get --purge remove pulseaudio

sudo apt-get autoremove

sudo apt-get remove pulseaudio-utils
sudo apt-get remove pulseaudio-module-conf
sudo apt-get remove pulseaudio-module-hal
sudo apt-get remove pulseaudio-module-x11
sudo apt-get remove libpulsecore5
sudo apt-get remove gstreamer0.10-pulseaudio
sudo apt-get remove libpulse-browse0
```

Then re-booted, and checked the ALSA settings by going

```
$ alsamixer -Dhw
```

Cool - Skype passed the echo123 test, and I could hear my voice. Granted there was a lot of noise, but I'm infinitely further forward then I was earlier this evening (and one step further from Windows...)

I'll report back if I experience any problems, have any other ideas etc.


Cheers!



I decided to follow up on this thread & went to remove pulseaudio & install esound in synaptic. BE VERY CAREFUL!!!! It, by default, REMOVES Ubuntu Desktop & Ubuntu Studio Desktop.... NOT SOMETHING I'M GONNA TRY. I'll find some other way to fix the internal mic issue.   ( Ubuntu Intrepid 8.10 AMD64, Gateway M1631u.)

---

