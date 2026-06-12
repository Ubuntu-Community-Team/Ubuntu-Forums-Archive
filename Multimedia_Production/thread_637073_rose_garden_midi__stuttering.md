---
title: "rose garden midi  stuttering"
date: 2007-12-10
forum: Multimedia Production
---

### Post by Smbrandes on 2007-12-10
Rosegarden is now stuttering through midi files producing a drunken almost jazz like effect. I have no Idea what might be causing it. It worked fine yesterday does not now. If anyone has had any experience with a similar problem let me know. Additionally I cannot manage to get rosegarden to make sound if i enable jack. Not sure why that is either. IN fact the more I try to fiddle with the whole sound applications the worse things gets.  For example I managed to set up aeolus yesterday and run it from the virtual keyboard, work allright a little static. today nothing. Basically, it appears to me that ubuntu is no where near ready for prime time in regards to sound production. I have wasted many hours trying to get things to work, wandered all over the forum looking for applicable help. And all I was after in the first place was making a recording from the sound produced by rosegarden from a midii file so I could convert it to wav. Efforts there too failed achieving only a recording that sounded like an old 78 record played in a closet on the other side of the house, vague static and no volume. 
Why is there no simple how to anywhere, and how come it is so bloody diffiuclt to get any of these apps to work properly, and why is it audacitiy is impossible to get to work with the alsa stuff. I am going to have to go back to windows to get any of this done. Which sucks, because basically ubuntu has been working well for the resto f the things asked of the evil little computer box.

---

### Post by stevesg1 on 2007-12-10
first, trash 7.10.clean install 7.01 w/ gstreaming media drivers
installl restricted drivers
get the complete meta pkg for the low latency kernel
get the flavor of jack that has qt front end control 
get rosegaden
get a native linux softsynth (some of them allow rec from alsa mixer capture)

boot into low latency kernel
launch in following order: jack, roseg, softsynth
load a stadard midi file in roseg
play (roseg should've made correct jack connections)
screw w/ jack config (buffers) to minimize Xruns
capture thru softsynth rec
you maybe able to bounce output to ardour thru jack
ignore audacity

if this sounds stupid, it is

imho linux and corresponding apps are not ready for audio production

---

### Post by Stochastic on 2007-12-10
Smbrandes, please ignore stevesg1's post it seems to be some ranting about personal issues they see in linux software in general (but your post doen't fair much better) imho.  There should be no need to downgrade ubuntu to make things work.

Linux audio is not quite fully functional out of the box, but with some understanding and tweaking, things tend to work very well for me.  It does take a little learning however.

To get Rosegarden to output through jack try running ```
timidity -Oj -iA
```
I'm not sure what to tell you about the stuttering, other than it might be due to resources being tied up elsewhere?  Try a reboot and make sure nothing else is running that could be hogging major resources.

I'm not a fan by any means of Audacity and personally I think it's famous among podcasters etc simply because many Mac OSX people use it.  I'd reccommend Ardour, Rezound, or Jokosher to replace it.

---

### Post by Smbrandes on 2007-12-10
Down grading into 7.01 does not appeal, there is too many other things to fiddle with in a reinstall. I tried Stochastics simple advice, to no avail. It did properly link the rosegarden app through timidity across jack but no sound resulted. Without jack the midi still stutters uner rosegarden after a fresh reboot. I cant fathom what would be hogging the systems resources as I turned off compiz and the cpu monitor only shows no more than 40% use when playing the file, with usage generally in the teens.
 I looked over stevesg1 advice, and followed the instructions except for the bit about a fresh install downgrade. since the whole point was to install ubuntu studio 64bit on an amd 64 bit chipset. So that build ought to have the low latency kernel by default and it definitely had qsynth and a qt Jack straight off the dvd. 
 Audacity was the first choice since I have used it in windows for some time and it has a zero crossing feature which makes editing pretty close to seamless. I am not by any long shot a professional sound person at all, It just happens that sometimes I need to work on recordings and had just enough exposure to sound engineering, a friend was the audio engineer at Oberlin conservatory. He is a mac person. I have had a long dislike of both windows and mac stuff but I grew up in the land of Dos and basic, so Linux has always had an attraction but I never felt it was close to useful enough until this recent reattempt at Linux. So if my previous post sounds a little discouraged, it is simply because after a fair chunk of invested time and tweaking, it seems that with every effort somehow the utility of Linux for audio work gets more and more remote. Which is decidedly a disappointment since the Linux concept and gnu and all that is an excellent idea.    However, it certainly does not appear to be ready for wide public consumption for a variety of reasons. One is to example Stochastic's advice, there is no earthly reason why that set of switches would ever occur to the average user without digging through mountains of randomly separate documentation. 
So in summary I am nowhere yet closer to solving the problem or problems. IN any event thanks for the input. 
 The only thing I can tink of is that in fiddling with some other buttons somewhere in the alsa mixer it is muddling up the rosegarden midi processing.

---

### Post by Stochastic on 2007-12-11
you're very right, linux is not fully ready for every user yet - it's still working on issues that are bigger for some users.  We really need to get PulseAudio and Lash fully implemented (and with a nice user interface) so that more apps get along nicely in a easier/simpler manner.  I personally never use rosegarden but I understand that some people are big midi musicians.

Are you getting audio out of jack normally?  Can you get any synths to run through jack?

Just to note, there is no 7.01, there was a 7.04 (feisty), and a 6.10 (edgy) with only a 7.04 ubuntustudio before 7.10.  Also, ubnutustudio 7.10 no longer uses the lowlatency kernel, it now has a realtime kernel that is much better for audio.

Can I also suggest that you try opening patchage to connect the output of timidity into the input of either ardour or rezound to make an audio recording (wav).

Also an area I think ubuntustudio really could use some help is in getting some good tutorials together.  I'd suggest that anyone, even with a bit of a grounding with using it, should write a little blog or two, then there'd be plenty of tidbits of knowledge for newcomers to gather.  A couple little "this is how I put this song together" style posts could really help but I've yet to see many of them.

---

### Post by stevesg1 on 2007-12-11
stochastic...I've been producing/creating audio since splice blocks and razor blades. I have no loyalty to any hw/sw/OS. When a tool gets in my way when I'm trying to create, it gets discarded. My motivation to explore linux audio was from a desire to experiment with Csound and Pd. 

You're right _7.04_ is the last ubuntu distro I got to work. I find the names cutesy-stupid.

In essentially all real-world production studios, anything digital happens on a mac (protools, logic) or windows (cubase, sonar, samplitude). The Linux audio distros are interesting, but essentially useless.

---

### Post by Smbrandes on 2007-12-11
Well following Stevesg1's advice did produce a result worth reporting. I discovered a dialogue box called message on the qsynth, that gave the following information.

JACK tmpdir identified as [/dev/shm]
Enhanced3DNow! detected
SSE2 detected
fluidsynth: warning: ALSA sequencer buffer overrun, lost events

Does this mean for some reason there is insufficient memory available to complete the operation?  Or is it that for some reason there has been a limit placed on the amount requestable by on of the apps  which causes this error? 
Rosegarden itself seems a bit slow in redrawing its gui. Maybe that is an indication of a similar problem. None of the other apps I have used on this system have exhibited any slowness at all  in redrawing graphics. 

I did manage to get the midi chopiness to go away by undoing some other thing that I had fiddled with while trying to get aeolus to run properly, but it still certianly does not work under jack. So no closer to the goal.

---

### Post by stmiller on 2007-12-12
Are you using a low-latency kernel?

Ubuntu has not provided pre-made low-latency kernel for Gutsy yet in the apt-get repos. So you'll have to compile or fetch your own from elsewhere for now.

Next thing to try like someone above said is to increase the buffer settings in qjackctl.

Linux *is *ready for prime time with audio, but is somewhat of a pain to set up. I made [this]("http://www.scottmillercomposer.com/tmp/strings1.mp3") short tv sound clip entirely in Linux using Ardour, Rosegarden, LinuxSampler, and others.

---

### Post by Smbrandes on 2007-12-12
I was under the impression Ubuntu studio shipped with a real-time kernel, I will have to look into that. But in terms of expected latency jack is reporting 2.67millesonds, which is not terrible, but also not exactly real-time. Also I have stamped out the xruns more or less, the only time they occur is when opening a jack dependent app.. In any event I see no reason why it should still not be functioning. The security file was adjusted to improve Jacks priority and I set the memory lock to 50 percent of the available memory (1 gigabyte)  for audio purposes.

---

### Post by Smbrandes on 2007-12-12
had time to check the kernel doing the following produced

$ uname -a
Linux Incorrig 2.6.22-14-rt #1 SMP PREEMPT RT Sun Oct 14 22:53:32 GMT 2007 x86_64 GNU/Linux


the rt at the end of the version number stands for real-time. So Ubuntu studio does ship with the real-tiime kernel which is better than the older low latency.

---

