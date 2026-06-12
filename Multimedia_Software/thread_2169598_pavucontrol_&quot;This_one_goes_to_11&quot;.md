---
title: "pavucontrol: &quot;This one goes to 11?&quot;"
date: 2013-08-22
forum: Multimedia Software
---

### Post by BuntuSeriously on 2013-08-22
Greetings.

Have a quick question for the community; one which has eluded my efforts to find any sort of answer so far.

Here goes:

Can someone explain the deal with the "153%" volume control level which is ostensibly furnished via  pavucontrol?

  Unless I'm missing something here, this seems to be an absolute  fallacy limited by physical hardware.  If not, then it seems as though  we're playing around with the dangerous possibility of front-end  overload for connected equipment; and megabuck damage beyond mere  clipping at the top levels.

  So, what's the scoop?  Does pavucontrol really dig into areas of  firmware which shouldn't be messed with at the hardware level, pushing  things to well beyond manufacturer's specifications; or is it just another odd  example of "This one goes to 11 (or 15.3, in this case ;o)?"

  *"Enquiring minds want to know..."*


Thanks a bunch; and have a great day :)

---

### Post by tgalati4 on 2013-08-22
Having come back from a 55,000 square foot venue with 90,000 watts, I can safely say that is how it is designed.  It doesn't go to 11, it goes to 11 deciBels which is ~153% on a linear scale.  In professional audio equipment it is quite common for Master Faders to go to +10dB.  You set the house level sound at 0dB for input gains and the output might be 95dB which is loud and at a level that will cause hearing damage for prolonged periods (4-8 hrs).  +10dB allows you to push the system to 105dB which is really loud.  Jet engines are 140dB and most rock concerts come in at 110 to 120dB which is why your ears ring after a concert.

So don't worry about it.  But yes, you can blow your equipment if you are not careful or you do not know what you are doing.  How the soundchips in your laptop distort and what level is for you to figure out.  But if you have a professional sound card hooked up to it, it should handle +10dB without a problem.

---

### Post by Yellow Pasque on 2013-08-23
The capability is helpful when hardware/drivers don't behave correctly.

---

### Post by BuntuSeriously on 2013-08-23
Thanks for the input, folks.  Interesting insights . . .

My concern really surrounds the Totally Clueless End User (TCEU), aka grandma, who might bumble into the pavucontrol UI while watching 700 Club rebroadcasts on her snazzy HP or Dell.  Having a low battery in her hearing aid, she cranks things up to 11 and leaves it there; thinking the distorted sound is just Pat Robertson talking about pot laws again.

Now, if she could wind up toasting anything on her dandy shrink-wrapped system, it would seem irresponsible of the pavucontrol team to allow this feature to be accessible (without clear warning) by TCEUs; as there is no telling who might do what with their distros in our big bad world.

Reasonably, my guess is this _*isn't*_ the case, and all is well for the Ubuntu grannies out there.  If not, we've got a feature here which is waay too sharp to allow unfettered access by default; and should have some basic safeguards in place.

Don't know if anyone can address this; but it would sure be appreciated for those of us who work with the TCEUs of the world ;)


Thanks again; and have a great day --

---

### Post by tgalati4 on 2013-08-23
*pavucontrol* is not installed by default.  You have to go through a few steps to install it.  Chances are, your grandma will use the multimedia buttons on the laptop itself.  She will complain that it is not loud enough for 700 Club reruns.  A shrink-wrapped laptop is designed to be tossed when it breaks.

The venue I was in had several slim PC's behind 70" touch-screen displays.  They need 3" of air clearance and they have 0" so they shut down due to thermal overload.  The sound chips have fried so no more video conferencing on these $8,000 displays.  High tech meets low tech.

---

### Post by BuntuSeriously on 2013-08-23
"High tech meets low tech."

I can relate.  Some of those slim babies bit it with 3 feet of airspace @ comfortable RT courtesy of Vista.  An elderly in-law's son (globetrotting M$ exec) dumped the demise of her "Vistafied" mobo on me after I installed FOSS on the system as a favor.  Who needs enemies...

*All fun aside, *and FWIW, pavucontrol IS installed as the default on Xubuntu 12.04; the very distro which I call home.  Gotta deal with it, however; as it's the fav over here for other reasons.

On that note, anyone know how to set the upper volume limit to 100% with PA?  Willing to dig in if there's a way :D

Curiouser and curiouser . . .


Thanks a bunch --

---

### Post by Yellow Pasque on 2013-08-23
If you're really concerned about it, I wouldn't use pavucontrol. Binding keys to volume scripts seems like a better way to go.

---

### Post by tgalati4 on 2013-08-23
*pavucontrol* is not installed on Linux Mint Mate 14 (based on 12.10), I don't know what other distros that have it installed by default.  You can download the [source]("http://freedesktop.org/software/pulseaudio/pavucontrol/") code and change it then recompile it.  It would take 1 to 2 hours of your time and it's a good learning experience.

If you decide to modify it, enable source code in your software repositories then download it directly through the software repositories.

---

### Post by BuntuSeriously on 2013-08-24
Thanks for the tip, Temüjin.  Might be a bit of a neanderthal, but I'd rather work with what we've got rather than cut the applet completely out.  Hey, there's good stuff in there!

However, if it's a matter of having to completely overhaul the app from source, I might be inclined in a direction like this soon enough ;)

Which brings me to another carriage return.  Is there nothing in the way of a simple "volume limit" config mod for this problem?  I mean, really, everyone knows that a pocket knife needs to fold away when you don't want to cut anything; and this baby seems to be real sharp as served out to the 'buntu masses...

Any devs out there with some savvy to share???

Just wondering --


Thanks again

---

### Post by tgalati4 on 2013-08-24
*pulseaudio* is an audio framework that was added to allow each application to control its own sound level, allow audio streams to be sent elsewhere, and some unique mixing capability.  ALSA was the previous audio framework and it still works and has a lot of capability which may do what you want.  *pulseaudio* was buggy when it first came out, and eliminated (or hid) a lot of capability that ALSA users expected.  Not unlike when Unity first came out.  Here's a rant that helps explain the situation.  [http://wiki.marklesh.com/How-to/Asoundconf](http://wiki.marklesh.com/How-to/Asoundconf)

Perhaps an ALSA configuration will provide such limits.  I don't know how to do it within *pulseaudio*, without modifying *pavucontrol* because "there are no user-serviceable parts inside."

---

### Post by BuntuSeriously on 2013-08-24
[http://wiki.marklesh.com/How-to/Asoundconf](http://wiki.marklesh.com/How-to/Asoundconf)

Brutal.  Now I'm getting peeved.  Thanks, tgalati4, for that link BTW...

Well, I just grabbed the source for 0.99.2 (match for the exe in Xu 12.04) and attempted a go @ editing the params of interest.  Found what looked to be the quary in pavucontrol.h, set up my box for the make, and found there's an apparent morass of dependencies which cannot be resolved without a real fight.  

No user servicable parts inside, indeed.  This is getting ridiculous right about now.

Now, if I want to just ditch & dump PA from 12.04, I've been given to understand that it'll screw up everything BY DESIGN.  If correct, that's a real slap in the face after spending a boatload of time cleaning up the whole LTS at my end; spending weeks of hemorrhoid cream drilling down into the squash and setting numerous things just as I want and need them for downstream installs.

Arrrgh.  Why does everything have to be so {uninstalled} complicated?!?  Thought I left this kind of crap back in sunny Washington...

Okay.  Just had an idea: Would yanking the whole thing from filesystem.manifest for a clear install avoid some of the problems which have been reported after pulling PA from a finished setup?  Might be worth a blind shot; but my gut instinct tells me we'll probably wind up with flakeware which will not connect sound with things like Skype and Flash; and that it'll be a PITA to get the distro hooked back into ALSA.  Still can't believe Xubuntu decided to dump the simple XFCE Mixer arrangement which they had working well in 11.10 to buy into these headaches.

Guess I'll try digging out the squash.  It's a beautiful day anyway...


:mad:

---

### Post by tgalati4 on 2013-08-24
You make some good points.  *pulseaudio* as an audio framework has improved.  You rarely hear the screams from users now--like you did when it first came out.  The older mixers were based on alsamixer which was quite configurable and only went to 100% volume or Unity Gain.  You should be able to install *alsamixer* and run it alongside *pulseaudio*.  I don't believe they conflict since *pulseaudio* is a framework one layer above the existing sound layers: alsa, esd, oss, and jack.

If you pulled the *pavucontrol* source from the Xubuntu 12.04 repository, then there should be no unresolved dependencies.  The 1 to 2 hours it takes to compile is the the time it takes to set up your [build]("https://help.ubuntu.com/community/CompilingEasyHowTo") environment.  You would have unresolved dependencies if you tried to compile a newer *pavucontrol* from 12.10 or 13.04.  That will definitely lead to *dependency file hell*.

And you are correct.  Dumping *pulseaudio* now will break a lot of applications that have hooks into it.  You can certainly spin your own distro without *pulseaudio*, but then you will have to fix the applications (through patches with dummy links) that depend on it.

Try loading *alsamixer* and see if that works.  If so, then your problem is easier by just removing *pavucontrol* from your distro spin.  Use *alsamixer* or *amixer* instead.

---

### Post by Yellow Pasque on 2013-08-24
Some relevant discussion here: [https://bbs.archlinux.org/viewtopic.php?id=127499](https://bbs.archlinux.org/viewtopic.php?id=127499)

---

### Post by tgalati4 on 2013-08-24
The gtk3 dependencies might create a problem but Temujin's link gives some hints.  So you are not the only one who has tackled this problem.

---

### Post by BuntuSeriously on 2013-08-24
Thank you both for the helpful advice/input (now that definitely goes to 11 :o)

Dead tired right now; and a busy day tomorrow.  Will probably get back to this Monday, glutton for punishment that I am.  The dependency thing definitely took me by surprise; looks like something might trashed inside my 'buntu (ugh).  I'll cut-'n-paste the static from xterm once the fatigue goes down below PulseAudio-level.

BTW -- dropping PA from filesystem.manifest did absolutely nothing in a fresh remaster: Still getting a handle on the guts of the machine.  Live & Learn . . .


Take care; and have a great weekend --

---

### Post by coldraven on 2013-08-25
I shared an apartment with my girlfriend above our elderly and deaf landlady. She would crank up her monster TV to 11 and then fall asleep, it was really loud.
Luckily her fusebox was outside her door. I used to go downstairs and briefly switch off her entire apartment. The TV would reset to it's default volume. Oh joy :)
From the "Evil Things Wot I Have Done" files.

---

### Post by BuntuSeriously on 2013-08-26
Back again.

New week, tried to figure out what's going on with the dependency hell which I seem to have stepped into. As promised, here's what ./configure burps out is needed for the games to begin:

No package 'gtkmm-3.0' found
No package 'sigc++-2.0' found
No package 'libcanberra-gtk3' found

Fair enough.

After the requisite attempt @ connecting with gtkmm-3.0 via

sudo apt-get install gtkmm-3.0

I am repaid with

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libgtkmm-3.0-1' for regex 'gtkmm-3.0'
Note, selecting 'libgtkmm-3.0-dbg' for regex 'gtkmm-3.0'
Note, selecting 'libgtkmm-3.0-dev' for regex 'gtkmm-3.0'
Note, selecting 'libgtkmm-3.0-doc' for regex 'gtkmm-3.0'
libgtkmm-3.0-1 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgtkmm-3.0-dev : Depends: libgtk-3-dev (>= 3.4.0) but it is not going to be installed
                    Depends: libglibmm-2.4-dev (>= 2.32.0) but it is not going to be installed
                    Depends: libcairomm-1.0-dev (>= 1.9.2) but it is not going to be installed
                    Depends: libpangomm-1.4-dev (>= 2.27.1) but it is not going to be installed
                    Depends: libatkmm-1.6-dev (>= 2.22.2) but it is not going to be installed
                    Depends: libgdk-pixbuf2.0-dev (>= 2.22.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

That last, culminating  line,

```
Unable to correct problems, you have held broken packages.
```

gets me in the context of the complaints further up the output; as I'm not sure putting on a long list of Depends on at this juncture will ever resolve the underlying issue.  For the record, again, this isn't an "unstable distribution;" as 12.04 is the basis from which I'm working.

Thinking the problem might be solved rather simply (HAHAHA), I decided to give a try to the other two core dependencies before bugging the community.  So, with further adieu, here's the booty from the Terminal for our other friends:

```
sudo apt-get install sigc++-2.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package sigc++-2.0
E: Couldn't find any package by regex 'sigc++-2.0'

```

```
sudo apt-get install libcanberra-gtk3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libcanberra-gtk3

```

So, as can be seen, Satan is indeed alive and well; thriving in the confines of my humble, tired old Thinkpad.  Not wanting to feed him any more than necessary, I once again come to the community for a blessing and banishment ritual...

On that note, coldraven,

[https://www.youtube.com/watch?v=64E65-fVXPU](https://www.youtube.com/watch?v=64E65-fVXPU)

*"Just say no..."*

---

### Post by tgalati4 on 2013-08-26
The package errors that you encountered are just suggestions.  You have to do a little research to figure out what the real errors are.  That is why it is called *Dependency File Hell*.

For example, there is no package called *sigc++-2.0* even though it tells you that you are missing it.  So it must be a metapackage (a large collection of packages like ubuntu-desktop) or buried in a library with a slightly different name.

tgalati4@Mint14-Extensa ~ $ apt-cache search **sigc++-2.0**
tgalati4@Mint14-Extensa ~ $ apt-cache search **sigc++**
libsigc++-2.0-0c2a - type-safe Signal Framework for C++ - runtime
libsigc++-2.0-dev - type-safe Signal Framework for C++ - development files
libsigc++-2.0-doc - type-safe Signal Framework for C++ - reference documentation
libapp-control-perl - Perl module for apachectl style control of another executable
liberis-1.3-19 - WorldForge client entity library
liberis-1.3-19-dbg - WorldForge client entity library - debugging library
liberis-1.3-dev - WorldForge client entity library - development files
liberis-doc - WorldForge client entity library - API documentation
libsigc++-1.2-5c2 - type-safe Signal Framework for C++ - runtime
libsigc++-1.2-dev - type-safe Signal Framework for C++ - development files
libsigc++-dev - Type-safe Signal Framework for C++ - development files
libsigc++0c2 - Type-safe Signal Framework for C++ - runtime
libsigx-2.0-2 - interthread communication library for C++ - runtime
libsigx-2.0-dev - interthread communication for C++ - development files
libsigx-2.0-doc - interthread communication for C++ - reference documentation

As a general rule, when compiling packages from scratch you always need the *-dev (development) files.  Doc files are documentation which you may want to read.  Dbg files are debugging libraries that are helpful when you turn on the debug switch when compiling.  Your code will run slow, but you may get helpful debug messages.

Regarding libgtkmm, on my system (12.10) I have the following:

tgalati4@Mint14-Extensa ~ $ apt-cache search libgtkmm
libgtkmm-2.4-1c2a - C++ wrappers for GTK+ (shared libraries)
libgtkmm-2.4-dbg - C++ wrappers for GTK+ (debug symbols)
libgtkmm-2.4-dev - C++ wrappers for GTK+ (development files)
libgtkmm-2.4-doc - C++ wrappers for GTK+ (documentation)
libgtkmm-3.0-1 - C++ wrappers for GTK+ (shared libraries)
libgtkmm-3.0-dbg - C++ wrappers for GTK+ (debug symbols)
libgtkmm-3.0-dev - C++ wrappers for GTK+ (development files)
libgtkmm-3.0-doc - C++ wrappers for GTK+ (documentation)
libgtkmm-utils-dev - utility library written on top of gtkmm - development files
libgtkmm-utils2 - utility functions, classes and widgets written on top of gtkmm

So I have a choice between versions 2.4 and 3.0.

Did you try *alsamixer*?  It only goes to Unity Gain (100%).  You can uninstall *pavucontrol* solving your initial problem.

---

### Post by BuntuSeriously on 2013-08-27
"The package errors that you encountered are just suggestions.  You have  to do a little research to figure out what the real errors are.  That is  why it is called *Dependency File Hell*."

Now, that gave me a chuckle to start my day.  To those around me, I am known for my sense of humor --

In light of everything, I am certainly glad for the options here.  Looking @ ALSAMIXER is on the list *du jour*...

Off to another long one; but I'll be back with a bit more chaw when it fits.


Have a great one, folks ;)

---

### Post by Ranko Kohime on 2013-08-27
> **BuntuSeriously said:**
> On that note, anyone know how to set the upper volume limit to 100% with PA?  Willing to dig in if there's a way :D
It is 100%, at least for me.

To mean that my volume keys only take it up to 100%, I have to open pavucontrol and take the slider farther with my mouse.

To the point of the OP, It is my belief, (which I cannot say rests on solid evidence, unfortunately), that currently in Ubuntu the situation is that Alsa manages the hardware, and Pulseaudio manages the clients.  Therefore, the Pulse server would merely be sending a distorted signal to the Alsa server.

But I could be wrong!

---

### Post by BuntuSeriously on 2013-08-28
Thanks for the post, Ranko Kohime.  Got me thinkin' again.

So, with a couple of hours just laying around waiting to be used, I broke out one of my ancient LPT-connected 12-bit ADCs; and did the following measurements between a test system and a monitoring system to try and put an end to this once and for all.

Here 'tis --

Test waveform: 200Hz sine; courtesy of Audacity (default 1.0 amplitude)
Test system: Cheap (but sturdy) ASROCK 770 Extreme3 w/integrated NVIDIA HD Audio

Procedure: Using both XP SP2 (Media Player Classic) and Xubuntu 12.04 (PA/Parole), play the test waveform into the 12-bit ADC @ max volume through the test system, observe the waveforms via the monitoring system, & take all readings from there.

Result: [INDENT]>> MPC via XP SP2 yielded a smooth, 1850mV peak (3700mV pk-to-pk) waveform @ 100% volume level from the ASROCK 770.

>> On the same system, PA/Parole via Xu 12.04 produced a smooth, 1850mV peak (3700mV pk-to-pk) waveform @ 100% volume level.  At 153%, the waveform resembled a nearly clean square (thoroughly clipped sine), with a solid 1850mV peak (3700mV pk-to-pk).
[/INDENT]
 
In sum (and as I toddled around in the OP), the whole 153% thing is essentially, as a dear friend of color was known to say, *"there to make you think you got something"* unless, perhaps, you have a system which is crippled in some way @ the driver level.

FWIW on that note, I had the privilege of horsing around with a Vostro 1015 back in 2010; and had to live with the fact that Dell seemed to have artificially set the volume level for this peach @ about 40% max (under XP SP2).  In consideration of the unit's price point, I assume this was to force an annoyance-based upsell to the next model (it didn't work).

Perhaps that is what this is all about: Workarounds for odd HW/FW issues?  If not, we truly have a "useless member" which does nothing more than provide an internally over-amped clipping zone...

In any event, I wasn't able to get anything unexpected out of the firmware/hardware which I tested. The silly thing seems harmless enough --

That's it?


P.S.: Forget about compiling pavucontrol out here as part of the "great unwashed."  Open source, indeed; modifiable _NOT_ outside of "the know."

;)

---

