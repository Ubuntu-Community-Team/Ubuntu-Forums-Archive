---
title: "No sound in 1004LTS clean install"
date: 2010-12-20
forum: Multimedia Software
---

### Post by rnsc on 2010-12-20
I have just upgraded from 0810 to 1004 LTS.

Everything is done but the sound.  It does not work.  Check the volume control.  No volume control.  Found the posts saying to add the Indicator thing, now I have a button to bring up gnome-volume-control.

Volume control is up.  No sound.

I have an ASUS P4C-800 using the sound built into the Intel chipset.

The "Sticky" for sound is from 2006, and the links to alsa do not work.

But this is a clean install, fully updated on a distribution 8 months old.  Shouldn't *sound* work?  

I would greatly appreciate any guidance.

---

### Post by markthekdeguy on 2010-12-21
i may not be much help, but seeing as you've had no replies yet,
Yes, sound should work, although for some folks, sound on Linux is going
through a bit of a change of late. due mainly to something called 'Pulseaudio'
which pushes and routes audio al round the PC.

I use 'Kubuntu' which doesn't have 'pulseaudio'
but a couple of basic suggestions...

maybe the audio is playing, but the levels are down,
on Ubuntu i needed to  
' sudo apt-get install  pavucontrol '
this unhelpful box, when installed presents you with sliders for different parts
of the sound system, you may spot one that one is low, or off.

my next suggestion is maybe a similar solution so
sudo apt-get install gnome-alsamixer
and enable all channels in the config before you start ..
strangely some audio channels aren't always shown by default.
sods law and all that.   .. hope this helps at least a tiny bit.
Mark

---

### Post by rnsc on 2010-12-23
Mark,
Thank you.  Both of your suggestions are helpful tools, but I got over the hump, albeit in an unsatisfying way.  What I overlooked is that in my transition I also moved from a P3-800 with an SB Live! card to a P4 with on-board sound.  I have always stuck with Intel chipsets and ASUS boards in the belief that they are the center of the mainline, and as such will avoid all compatibility problems.  I guess not.  I put in an SB Live! card, disabled the on-board audio, and it just worked, as expected.  So it must have been a driver problem - the distribution not supporting the audio in the Intel chipset.  This surprises me very very much.

Two requests:

How would I have proceeded?  Perhaps the answer is that I tossed out the sticky post too fast.  Since the links in it were bad and it was from 2006, I figured that it was probably no longer valid due to evolution of the sound system.

If you have the knowledge and time, a helpful stickly would be to outline the various audio stuff and their relationship.  There is OSS, Alsa, PulseAudio, and who knows what else.  I expect that some is at different "levels" (layers of software), other is old, other is new, other is different parts of the system so both are needed.  Things are just bounced around like everyone knows, but I don't, and I expect that many if not most people don't.  A well structured overview, probably with a picture would help, would put many people worlds ahead!

Don't know if you are the one to make this overview.

Thanks for your help.

--Ray

---

### Post by markthekdeguy on 2010-12-24
Hi Ray, I'm probably not the one really mate, but having been using Linux since 1998 i've seen a few changes, i'm not sure if my memory serves me well enough to be guiding anyone much.
 
But i do expect things to be fixable and logical, as far as my brain will allow ... and i see no reason to make things unnecessarily tricky, or stick with something out of habit that isn't wotking, instead of moving forward.

all i can offer Ray is my latest experience and opinions..
most of it is probably wrong, so anyone writing in to point errors out,
i know !!  -  these are just my thoughts.

I understand what you mean, with a SB Live! card, moving to a P4 with on-board sound,  i like the SB Live! cards, they actually mix audio streams in *hardware*, rather than do it in software, which i regard as a mainly cost-cutting exercise.

Here's a little bit of background..   Ray,
in the mid or late 90's home modems were either plug inside the PC
or the standalone type, looking a little like a basic version of todays modem / routers. internal modems were cheaper,
time and tech moved on, companies got smarter and wanted to cut costs,
the Internet was just getting popular, large sales were on the horizon.
so, it seems, some bright spark figured, they could make modems cheaper by reducing the number of bits inside,

indeed they could do the same job with a cheap chip and
software, and so load the firmware in at power-up.
before this, internal modems didn't really need drivers, new serial ports
just appeared in windows after you plugged the modem in.

These new internal modems' looked basically  the same as the old ones but they wouldn't work without a driver. they were known as 'win-modems'
You could still buy the nice external modems with the flashing lights on, but they were pricey. but i preferred them :)

As its 12 or so years ago, not sure, Linux support for these 'evil windows modems' was done only by the community, Linux was more underground back then, and the manafacturers certainly didn't support us.
it was a little tricky back then to get these 'evil windows modems' going under Linux .. but we did, what a talented community we have to thank.

Now, years on, this seems to be a 'similar difference' between sound cards like the venerable SB Live! and many on-board sound cards.
there are many variations of say, the hugely popular HDA-INTEL standard, lots of different chipsets trying to comply, same seems to be true of Intel's earlier AC'97 standard, it has many variants too. and is still in wide use.
some sound chipsets will have or support different features
so how close they stick to the 'standards' is anyones guess. many combinations. it would help enormously if hardware vendors would
publish technical details, make drivers available,..  etc 

I remember reading a few years ago, that the ALSA driver for some  SB Live! cards was a little 'broken' - but i loved it, i had a few stereo outputs, - headphones, stereo TV, monitor speakers, woofer etc etc .. it was a great Linux Home entertainment / VOIP / fun system .. the many in / outs on the SB Live! were a luxury, that Windows was unable to offer me, i only played the 'Thief' games on windows anyway.

Maybe the SB Live!  vs  the onboard card was an example of old 'hardware mixing' versus the software mixing that perhaps ALAS's 'DMIX'  was doing for the on-board card... 

some people have ALSA problems, i have pulseaudio problems. i dont bloody  like  it  yet, -  its still flaky on my hardware :(

For years, ALSA has been the main sound system on Linux,
but it is said it is too complicated, and has problems, maybe,
nothing is perfect, but  there has been so much work done on it,
it works. its pretty mature, proven code.

Different programs were written for different sound systems, ESD, ARTS PULSEAUDIO and JACK are servers .. they play sound for programs, instead of direct to the soundcard itself, which could tie up the card.

these  'sound servers' allow tricks, like mixing different streams  (like VLC  and Skype at the same time, say) or sending audio across a network.

PULSEAUDIO aims to tidy up all these different standards, and capabilities and 'wrap' these programs and keep everything sweet.

Earlier incarnations of PULSE seemed less than sweet, with many users needing to have to install  things like ' pavucontrol ' to set individual levels and enable and set some channels. many more users having no issues at all. It seems to me to be a combination of hardware, and drivers.

I use KDE, have done for years,  sound was pretty simple back then, Redhat's 'sndconfig' tool allowed setup and, if you were lucky, you heard Linus Torvalds tell how he pronounces his name.

Gnome distros mainly use PULSEAUDIO, so i dont use either much,
Gnome-Ubuntu 10.04 LTS  worked reasonably, but suffered total audio loss every other time i used Skype till reboot. so, back home on KDE, i installed Pulseaudio, got it working, but it was still unreliable and audio quality suffered. these issues will get sorted in time i guess.

In KDE i use ALSA - and suffer no audio issues or glitches any more.
i can watch DVB-TV, have VLC playing soothing music, Amarok playing a podcast, youtube playing, and be chatting on Skype and stuff all at the same time on this laptop, (as a test)  and it proves the .ALSA is great.

A strange ALSA / Skype thing thats puzzled me is Skype audio in, from my mic ... on the first skype test call, it all works well. i unhide all kmix's channels (i hate hidden options) i see both mic channels, makes sense.
it works.
then reboot.
Skype test call, audio is distorted, slow, both, or completely gone.
hmmm.
check Kmix again. weird,  a new mixer channel has just appeared since reboot ... the channel is 'digital'  its at zero. it wasn't there before i rebooted, anyway,  turn the digital up, skype mic works a treat.
odd. i think this is an ALSA / skype interaction or 'feature' not sure yet.
anyway, this may not help much, but thats how i see it working,
maybe it'll mean something ..
Mark ..

---

### Post by rnsc on 2011-01-02
Mark, thanks for taking the time to walk through the history.  It of course is not directly applicable to the problem at hand, but it is always useful to have a handle on history and the meandering path that things have taken.  I will probably stick with the Live! card for now, seeing as how it works.

I have another question which is off topic of the thread, but since it is my thread in some sense, and it is sound related...

Do you know how 44.1KHz sounds are interpolated (resampled) to 48KHz for the sound card?  I know that almost all of them actually do the digital to analog conversion at 48KHz, and the the Live! does something obnoxious like nearest neighbor interpolation which sounds horrible.  My understanding is that someplace in the layers a better algorithm is used for the interpolation.  I am interested is learning more about it so that I can ensure that it is a very good algorithm so my music sounds as good as it can given my budget.

Can you tell me where I would look for the 44.1 -> 48 KHz resample?

Thanks (Either way).

--Ray

---

### Post by markthekdeguy on 2011-02-12
Sorry Ray if you're still there mate, i haven't been around for a while. i apologise.
hope you got your sound sorted.

---

