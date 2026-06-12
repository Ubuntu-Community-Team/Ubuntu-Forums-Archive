---
title: "Please help with audio in Ubuntu"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by Tenson on 2007-07-16
Hello,

I have been using Ubuntu Studio for about 1 week now and am really liking it so far! :) Thanks to all who helped make Ubuntu what it is!

Now, I have bought a Presonus Firebox audio interface to use, as I read of people having some success getting it to work in Ubuntu.

I followed some of the posts I read here about how to get it working and so far I have got Jack to start and I can play music in Audacity when I select Jack as the output device.

So I am doing okay so far! But...

Q1)  I can't figure out how to select which outputs and inputs to use. For example in Audacity if I wanted to play back one track on the second pair of analogue outputs, how do I go about that?

Q2) My next question is how do I get it to work with general Ubuntu stuff? It works in Audacity and I assume other programs that can use Jack... but how do I get Ubuntu itself to output sound from the Firebox? For example if I want to play a DivX in VLC how do I get that to play sound? I can only select ALSA, ESD or OSS in the 'Sound' options. Is there some way to make normal system sounds output to Jack? Do I install a 'Freebob' driver? (how do I do that?) I'm a bit confused.

Help on either of those questions is GREATLY appreciated!

Thank you.

---

### Post by Tenson on 2007-07-17
Hello?

Do I take this to mean only programs that can use Jack can output to a firewire audio interface? That sucks big time #-o

---

### Post by Footer on 2007-07-17
Hey, I'd like to help but I'm kind of a newb. to audio recording in Linux.  What do you mean by "Jack"?  I don't have that as an output device in Audacity.  I just have OSS (/dev/dsp) and a bunch of ALSA stuff.  The only way I can get sound out is to start Audacity with aoss which I had to install.

I'd like to record some stuff off of vinyl but when I hook the jacks up to my mobo sound input (I just have sound coming off my motherboard, no soundcard), I can't seem to get a signal no matter what I select for a recording device.

I know our problems aren't that similar but I wanted to just chime in and let you know someone else out here is struggling just like you!

Thanks!

---

### Post by dabl on 2007-07-17
I've been using Audacity to record from vinyl (and 78 rpm shellac, too).  What sound system are you trying to use?  I'll help you if I can.  :)

---

### Post by Footer on 2007-07-17
> **dabl said:**
> I've been using Audacity to record from vinyl (and 78 rpm shellac, too).  What sound system are you trying to use?  I'll help you if I can.  :)

Sound system?  I'm not sure what you mean ... ?  I've got an Asus M2N SLI-Deluxe mobo with onboard sound.  I've tried plugging the input into the mic and line in with no success.  I'm using Audacity and under preferences and audio I/O, I've got OSS: /dev/dsp and a host of ALSA devices for both playback and recording as well as OSS: /dev/dsp1under recording.  None of these seem to give me any signal from my turntable.  How can I find further details about my onboard sound?

VERY frustrating!

---

### Post by dabl on 2007-07-17
OK. I was referring to the particular integrated sound chip.  There are 2 ways to find out -- you can pick.

1. Open System>Preferences>Hardware Information, and see what it says about the audio subsystem.

2. Open the console and enter ```
lspci
``` and see what it says (assuming the chip is on the PCI bus, which they mostly are).

---

### Post by dabl on 2007-07-17
> **Footer said:**
>  None of these seem to give me any signal from my turntable.
VERY frustrating!

You will undoubtedly need to use a preamplifier.  The turntable output signal is too low to run straight into your "line in" jack.

Most receivers have a pre-amplifier.  The bad news is, most of the new ones do NOT have "phono in" RCA jacks for the turntable cables.  You'll need a friend with a receiver that has a pre-amp with "phono in" and also "tape out" jacks.  Then you get a "Y" cable that has RCS plugs on one end, and a 1/8" plug on the other, to go into your sound card's "line in" jack.

---

### Post by Tenson on 2007-07-17
Hi,

You can also get separate phono pre-amps (phono-stage) such as these - [http://www.needles-and-spins.co.uk/cat_phono.cfm](http://www.needles-and-spins.co.uk/cat_phono.cfm)

I know the guy who runs that site via another forum, he is a good guy.

I think I am going to have t  go back to the dreaded XP since I can only get sound from programs that use Jack (Freebob). So far that is only the dedicated recording software. VLC should be able to apparently but I can't make it do it. Supposedly its needs a recompile :( But even then internet sounds from flash movies, java programs, anything else, program sounds won't work so it makes me pretty depressed!

If anyone has good news for me like a way to get ALSA to output to Freebob then they better let me know soon or I will have been Microshafted.

---

### Post by Footer on 2007-07-17
Tenson & dabl -- Thanks for the info.  You are both correct, I think I'm going to need a pre-amp.  I did manage to get a signal directly from my turntable.  I'm using KDE and via Kmix, I set the input source to "line" and then cranked up the "Front Mic" and "Front Mic Boost" sliders on the Output tab and then I was able to hear what was being recorded.  But when I went to play it back, it was very low volume even with the volume cranked, so I gather like you say, a pre-amp is in order here.  I'll take a look at that link you provided Tenson and check that out.  I do have an older receiver that I might be able to make work for this project as well.

Man, it sure is complicated!  Thank goodness for CDs!  Sure makes life a lot easier these days but some of that great older music from the 70s/80s that's locked on vinyl would sure be nice to digitize as well!

Thanks for the info!

---

### Post by Tenson on 2007-07-17
> **Footer said:**
>   I do have an older receiver that I might be able to make work for this project as well.

Make sure it has a phono input. As you have discovered, normal line input from a CD, mini-disk etc.. and phono from record players are not the same. And it is not just a level boost, it applies a special EQ called RIAA as well.

Oh, this turntable has a phono preamp built in. It is a good deal for recording old records and will make them sound better than ever, unless you already have a very good turntable (and I don't mean a 1210 :p ). [http://www.needles-and-spins.co.uk/pd_project_debut.cfm](http://www.needles-and-spins.co.uk/pd_project_debut.cfm)

---

### Post by dabl on 2007-07-18
> **Footer said:**
> 
Man, it sure is complicated! 


Heh!  Try setting up to record different brands of 78s from the 1940s, and THEN you'll find out what "complicated" really is!

:)

---

### Post by miltonics on 2007-09-18
So you never figured out a way to pipe the system sounds into freebob?

---

