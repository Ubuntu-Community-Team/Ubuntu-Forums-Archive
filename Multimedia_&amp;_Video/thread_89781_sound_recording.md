---
title: "sound recording"
date: 2005-11-13
forum: Multimedia &amp; Video
---

### Post by drkemp on 2005-11-13
I recently upgraded and I can no longer record anything. There are MANY references to sound output problems, but that works fine. I have correct sound playing from XMMS, desktop sounds, audacity, etc. I have the Multimedia preferences set for ALSA. I have tried verifying settings with the gui mixer and with ALSA mixer. 
When I use the mixer I can get the mic sound to come out the speakers mixed with  audio from a player so i know the mic works, it is unmuted, etc. 
Recording VU meters always show nothing, and various apps either record nothing (gnusound), throw an error (audacity) about a device missing, or just lock up (gnome-sound-recorder).
I have no local .asoundrc. I have a card that uses "snd_ens1371".

I could use help. Im kind of stuck.

---

### Post by nalmeth on 2005-11-13
hello...
not positive this will help you, but..
previously i had problems recording my killer guitar riffs through my USB microphone, mostly running audacity, but no other app helped.
after a lot of digging i found out that while audacity sets the input device as DSP (without option to change) and what was required was DSP1.

my recommendation (worked for me): 
if you can install wine, do so. Then download the WINDOWS VERSION of audacity (download.com or whatever). This allows you to single out your particular input device (it allowed me to pickout my logitech usb mic specifically), and may solve your problem. Unfortunately, running in wine, audacity was a little skippy for me, but nothing malfunctioning. 
This shouldn't be necessary, but you do what works until someone smart enough fixes it for the rest of us..

good luck!
nalmeth

---

### Post by drkemp on 2005-11-14
interseting thought, but I do not have /dev/dsp1  and the version of audacity I have lets you pick from available options anyway.
Note that it is not just audacity that does not work. I have not found ANY sound input that works.

---

### Post by drkemp on 2005-11-14
System->Preferences->MulitMedia Selector is currently set for Alsa, and the output works fine, but doing an input TEST causes the little bar to wander back and forth until I press "OK". Then it hangs until I "Force Quit" the test app.

---

### Post by rodneyorpheus on 2005-11-16
I have exactly the same problem. Sound source is an Intel ICH5 onboard sound chip. 

Rodney

---

### Post by drkemp on 2005-11-16
ok, so I have had a little success. I went to [http://www.guerrilla.net/reference/dsp/prog_dsp.htm](http://www.guerrilla.net/reference/dsp/prog_dsp.htm) and compiled the test app that just reads /dev/dsp and then spits it back out. Then I ran alsamixer and messed with ALL the controls. I now have some audio going in. I cannot seem to get the settings required with the gnome volume control, but this works. It does not seem to stick when I log out, but I can get it back. I am not sure that things are right yet, but at least it works.

---

### Post by anil_robo on 2005-12-04
[quote=drkemp]System->Preferences->MulitMedia Selector is currently set for Alsa, and the output works fine, but doing an input TEST causes the little bar to wander back and forth until I press "OK". Then it hangs until I "Force Quit" the test app.[/quote]

I get an error message if I test sound input with alsa, but OSS gives no error - instead a bar moving back and forth, but nothing else happens. When I try to record something, the sound recorder crashes (and also tells me to inform the developers :rolleyes:)

Wish there were some help for sound recording - INstant messaging could be made so much fun in Ubuntu!

---

### Post by Hug It on 2005-12-04
I'm having the exact same problem and been searching for quite sometime for a fix. No luck so far.

---

### Post by thechitowncubs on 2005-12-04
my mic doesn't have sound either, have fiddled with everything :confused: :confused: :confused:

---

### Post by anil_robo on 2005-12-10
So many people can't record sound on Ubuntu, and in fact, one musician wrote in the forums "Ubuntu is not for musicians"! Guys, someone whose technical knowledge is good **please write a how-to on sound recording!** Not only it'll help many people in composing music, talking to their friends and family, but it'll also prevent people from migrating away from Ubuntu.

Thanks

---

### Post by graigsmith on 2005-12-11
i cant record sound either.

---

### Post by Luffield on 2005-12-11
Same problem here, with an ES1370 sound card. I tried to do the test drkemp mentioned in post #6, but it's not loading at the moment.

---

### Post by graigsmith on 2005-12-11
this is the kind of thing that should just work.  there has to be a bug or a misconfiguration somewhere.   this kind of bug is the kind of bug that drives people away from ubuntu.

---

### Post by anil_robo on 2005-12-16
I have read reviews about many musicians running away from Ubuntu just because they can't record sound. It's a serious issue because it selectively deselects a whole group of talented people from using Ubuntu, and it's sad.

I hope the developers will look into the matter (though [this poll]("http://ubuntuforums.org/showthread.php?t=102377") has a low turnout - so low hope!) in the next version of Ubuntu!

Edit: I'm using Dapper now... and the same problem lingers on!  Dapper does not have good support for sound recording either! :(

---

### Post by pherseu on 2005-12-16
I can't record either. My mic isnt working too. But I'm trying to say on [this]("http://ubuntuforums.org/showthread.php?t=104387") topic. The problem is most common ...

---

### Post by nerval on 2005-12-16
same problem here .. anybody found a solution ? (except deleting your distro and installing a different one?)

---

### Post by anil_robo on 2005-12-17
Good news!
I have successfully recorded sound in Ubuntu few times just half an hour back! Read my post [here]("http://www.ubuntuforums.org/showthread.php?t=102377#6")

---

### Post by graigsmith on 2005-12-17
[QUOTE=nerval]same problem here .. anybody found a solution ? (except deleting your distro and installing a different one?)[/QUOTE]

whats a good different distro to try? debian? or would that be too hard?  perhaps fedora?

---

### Post by ruseel on 2005-12-18
[QUOTE=drkemp]I recently upgraded and I can no longer record anything. 
[/QUOTE]

I had same problem. but after some change in alsamixer I can record now. 

In my case, problem was that 
  Mixer's "Capture"->"Capture" was "off" by default. 
  (at least, I did not change "Capture" setting by intension)

so try change "Capture" to "on".

If you are using "gnome-volumn-control", you have to add "Capture" in preference.

---

### Post by Luffield on 2005-12-19
Thanks ruseel - that solved my problem.

---

### Post by graigsmith on 2005-12-19
something is wrong with the capture device on mine, especially in audacity.  is this a problem with audacity? or with ubuntu? its recording way too quietly.

if you have the volume muted on the capture device, but it's set to record, you can still hear it.  even if it is muted.  so i am convinced something is wrong with ubuntu, because the mixer is doing wierd things.

---

### Post by graigsmith on 2005-12-21
YAY i fixed it, ran alsa mixer. and it turns out there is another volume slider for my capture device and it was at half volume.  

for the record to get it working, i had to use alsamixer. hit space on line in, to enable it as the capture device.  then unmute the capture device. turn it's volume up.
then i also had to find ac97, and ac97 capture device, and turn their volumes up, once their volume was up, i could record.

the mixer gui that comes with ubuntu sucks.  it doesn't make any sense with some of those things like the alsa mixer does make sense.  like with alsamixer it actually doesn't show a volume slider on the line in device, because the line in device is actually a toggle. not a slider. but the gui version doesn't know this.

---

### Post by mepapp on 2005-12-21
Hello. I've never posted anything before, but here's what I've figure out about audio recording which, admittedly, isn't much.

First off, I haven't gotten Audacity to work particularly well. I'm not sure why, but my little computer microphone sounds like a cheap darth vader voice changer when I record.

What I have managed to do is get ardour, an arguably far superior program, to record, (though I have been unable to listen to it yet...)

I'm going to restart my computer right now, because I killed audio playback in the process of making recording work, but if it does I'll let you know. Suffice it to say:

1) ESD seems to be a pain in the ...

2) ALSA is the way to go but for some reason isn't enabled automatically and requires some awkward configuration for the non-cogniscenti such as myself.

3)jack and qjackctl are, while a little complicated, actually really useful if you are willing to play around. 

4)Basically: 

A)synaptic jack and qjackctl, 
B)then go to system->multimedia and set ALSA for recording, 
C)then run qjackctl  (audio video in applications) and fiddle with settings (use the setup button and click on input to use what input you want), 
D)then start jack (you'll understand what that means pretty quick) 
E)then try audacity. OR, get gtk-ardour from synaptic and start that
F)If you went the ardour route, check the connections pannel in qjackctl to ensure that the things you want to use are connected to ardour
G)Make a new project, and add new "track or bus"
H)Select the little 'r' next to the track to enable recording
I)Hit the record button and then play


Hope this helps. As I write this I just tried listening to my recording and it sounds fine. If people find this useful, I'll try and make a more coherent write up of the process. Also, for those of you looking for professional quality recording, try [demudi]("http://demudi.agnula.org"), which is a low-latency debian distrobution. It has kernel level optimizations to ensure things sound clear as a bell, and actually provide a clear advantage for linux users over pc users. It has jack builtin.

good luck, and please let me know how this worked for you. I've only got a crappy nforce2 onboard sound card, but I bet somebody's got something a lot better out there who could really make use of ardour.

Anyway,

---

### Post by polpak on 2005-12-22
I too am having recording issues. I've got 2 systems running breezy.

One is a laptop with the AC97 onboard audio chipset, and the other is a desktop system with a Creative SB Audigy. Neither of them are able to record any sounds (give errors about missing sound device or they lock up the program attempting to record) however they both play music/sounds fine.

Can any offer any suggestions?

---

### Post by plutoprime on 2005-12-23
In order for laptops with ICH4 or whatever AC97 stuff to work your input system  under System->Prefences->Multimedia System Selector should be set to OSS. Alsa simply won't work (For me at least) but OSS works like a charm

---

### Post by dawynn on 2005-12-30
When I run qjackctl, I get some error messages, including the following:

13:17:24.497 Patchbay deactivated.
13:17:25.027 Statistics reset.
13:17:25.146 Could not open ALSA sequencer as a client. MIDI patchbay will be not available.
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

Should I be manually building a /dev/snd/seq file / directory?  Or am I missing a package somewhere?

---

### Post by cvmostert on 2005-12-30
[QUOTE=drkemp]System->Preferences->MulitMedia Selector is currently set for Alsa, and the output works fine, but doing an input TEST causes the little bar to wander back and forth until I press "OK". Then it hangs until I "Force Quit" the test app.[/QUOTE]

hi, i also have the problem with onboard via vt8233 sound!!! have been suffering with this problem too long now... dunno what i ought to do... do i really have to get anoter soundcard?

wouldnt want to..
hope we get this one fixed

---

### Post by nerval on 2006-01-05
What mepapp said is not working on me, more of it; it screwed up my sound completly. 

Anybody please ? Have any solution on how Ubuntu records sounds?

---

### Post by joehill on 2006-02-01
Thanks Mepapp, I have the same problem with audacity (and the defualt sound recorder tool) having a cheap, tinny sound with a high-pitched rattle.  Your solution involves pushing more buttons and using software that is a bit less intuitive, but ardour does simply record without distorting the sound.

I'd still be interested if someone can tell me what I'm doing wrong with audacity though--why do things sound fine when I listen to them in real time, but get all distorted when I record them?  I thought this was a basic thing that had been working automatically for decades.

---

### Post by cosmolee on 2006-02-02
I gotta say, this is the kind of thing that's driving me away from Ubuntu.  

As someone said, this is the kind of thing that should "just work".  I don't have the time or the patience for debugging this kind of stuff.  It's already enough that Ubuntu won't play many media types out of the box, but having to jump through such hoops just to do something simple like talking on Skype is too much to ask.  Everytime I have to re-boot into Windows to do some task which should "just work", I curse Ubuntu.  

My next move is to download the live versions of PCLinuxOS, Mepis, Kannotix, etc.  The one that requires the least of me to get a working desktop going gets my support.  

Soon to be former Ubuntu user...

---

### Post by joehill on 2006-02-02
Well, I fiddled around with my Audacity settings and most of the tinniness I was hearing before has gone away.  I changed the "Default sample format," which apparently is automatically set to "32-bit float," to 16-bit.  I don't know exactly how this works, but I'm assuming that the sound being fed to Audacity is 16-bit, so something is lost in converting it to 32-bit.

Listening closely to the sound, though, the distortion in the higher decibels in the recorded version seems higher than the distortion when I listen to it directly, and I don't know how to get rid of that.

---

### Post by joehill on 2006-02-02
Another thing--I just started Audacity up again and had the same problem I had before and then I changed the sample rate to 48000 Hz and restarted (the problem didn't go away until I restarted) and the sound was back to being acceptible.  I don't know if I've fixed the problem for good.

I also tried changing the "Default source" in the System -> Preferences -> Multimedia Systems Selector menu to OSS (I'd heard that Audacity works better under OSS) but that seems to have made the problem worse, so I went back to using ALSA.

So in summary, here are the settings that work for line-in recording on Audacity for me: 16-bit Sample format, 48000 Hz Sample rate, ALSA as default audio input source.  As I'm not an expert I can't say if there are other settings that would be better, but these are the only settings I've found to work acceptibly so far.

Also, I keep the record level very low and then amplify it afterwards, because otherwise there's a lot of distortion (even if it doesn't look like it's maxing).

---

### Post by Slim Odds on 2006-05-09
[QUOTE=joehill]Also, I keep the record level very low and then amplify it afterwards, because otherwise there's a lot of distortion (even if it doesn't look like it's maxing).[/QUOTE]

This is the wrong approach. You should keep the levels as high as possible without clipping. Otherwise you are applifying the background noise too much.

---

### Post by Turtle.net on 2006-06-11
Hi,
Just to say that when I upgraded from Breezy to Dapper, the mic wasn't working anymore for skype.
Then, i tried to verify my settings using the application Sound Recorder ... and I never achieved to record anything.
But after enabling Mic as the capture device AND enabling Capture with max volume I was able to use my microphone with skype ... but not with Sound Recorder (and I don't care).

So, don't expect much from debugging using this application.

---

