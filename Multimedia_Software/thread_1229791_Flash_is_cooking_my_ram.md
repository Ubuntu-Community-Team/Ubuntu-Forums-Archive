---
title: "Flash is cooking my ram?"
date: 2009-08-02
forum: Multimedia Software
---

### Post by johnuk on 2009-08-02
Hardy Heron, freshly installed, all updated etc

But I can't for the life of me get Flash running okay. It works, but once I open more than one or two videos, or too many tabs and a video, I just get the grey screen.

I've heard in the past that the Adobe flash for Ubuntu has serious RAM allocation problems. Looking at my system monitor, I have about 255mb of RAM assigned to firefox, but I have only two youtube videos open and they're both greyed out.

Is this a RAM issue or something else maybe? If it's RAM, are there any alternatives to Adobe's player? Medibuntu? 

I'd like to be able to stream the videos, not have to download them. I don't watch TV, but I am a youtube wh0re. The flash problem is one of the major bums about unbuntu for me.

Thanks for the time and effort! John

---

### Post by Ernesto RD on 2009-08-02
makes two of us! im using jaunty,  tried hardy, back to jaunty, reinstalled flash plugin from every place i could find, i even changed the damn video card! and i just cant get flash to perform ok. Its allways choppy, and in full screen is practically frame by frame.
If i dont find a solution for this, im gonna have to give up on ubuntu and go back to windows :(
it would be a damn shame, cause in most other things ubuntu (and linux) is so nice.

---

### Post by johnuk on 2009-08-03
I get the choppy frames as well, sometimes the video will just halt while the audio continues for a few seconds.

Running a gig of RAM. Which isn't a lot, but it should be enough.

I just had a brainstorm and had a watch of my system monitor while I tried to purposefully grey out some youtube videos.

Surprisingly, the RAM allocation only went up by tens of MB even with five or so videos open.

It did start getting choppy at that point, but I still had ~500mb free and 200mb allocated to swap.

What I did notice was the CPU usage peak up to the 90's and quite often it'd hit 99% - and then I'd be getting the skippy frames.

I have an athlon 64 dual core 3200+, which I think runs at 2GHz - they have the specification here, [http://www.techpowerup.com/cpudb/62/AMD_Athlon_64_3200+.html](http://www.techpowerup.com/cpudb/62/AMD_Athlon_64_3200+.html)

Could it be something to do with the way the plugin is allocating tasks to the processor, causing it to overload too easily? Maybe I've made some noob error in selecting a version when I originally downloaded it, but I imagine I'd have checked that out.

---

### Post by cottfcfan on 2009-08-03
This issue has occured on many threads, and I only know of one solution.
 In boot/grub/menu.lst, add to the Kernel acpi=off, this solved my high cpu usage, video now plays fine and system is more responsive.
 I`m sure this is an acpi/kernel problem.

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101][B]Remove PulseAudio, it may cure the problem

[ubuntu][/B][/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.

[/B][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")

---

### Post by johnuk on 2009-08-04
Thanks for the help!

I've edited my Grub to read;

> ## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3be6e53b-c160-41c7-8bdd-45ec96a9a01f ro quiet splash **acpi=off**
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

And tried booting through that. I'm evaluating the crashability of flash at the moment and will let you know how I get on.

So far, I'm still experiencing one problem, which is sometimes if I click a new video on related or similar columns, it'll be grey but with audio when it starts. For some reason, if I click refresh a couple of times, the video will appear as well.

Playing Flash in an offline player isn't an issue at all, and all my sound is working fine. Other formats of videos will also play fine in offline players. It's when I try browsing something like youtube online in Firefox when I get the grey out. Often it'll start by only killing the video stream, leaving the audio going. Eventually it develops to a point where it won't even start the audio stream. I have to close the flash based sites and start again, sometimes I need to close Firefox as well.

It can't be the RAM if Sys Mon is telling me I have 500mb spare and each new video is only using up 2% of that when run online in Firefox. Something else must be upsetting things, and upsetting this nerd at the same time! :P

This is a big downfall for a modern OS, I can't imagine it's a problem with the shell or kernal it's self - I'm guessing plugin.

---

### Post by johnuk on 2009-08-05
Okay, I had some videos grey out this morning and last night. Same thing, close other tabs, click refresh a few times and they're back. This is booting thru the .23 acpi=off line at grub.

Some of them were greying out with no other flash sites open and just one or two other tabs. It's almost like it forgets to bother with the video stream sometimes and need reminding with some refreshes.

I'll continue trying it, but any more help would be welcome! Seems like quite a big issue for so few replies. There must be tons of people who've had this.

---

### Post by cottfcfan on 2009-08-05
Ive been trying "noapictimer" but evertime i open a program i get fine yellow lines flashing on the screen, frequent lockups, and in only works on kernel 2.6.31rc5.
Back to acpi=off for me. But now i have no suspend, and have to manually power off, unless anyone has any suggestions?

---

### Post by johnuk on 2009-08-06
acpi=off

doesn't seem to be working so well for me. I had another look at the sys mon while I was messing around with the browser. With one youtube video open, the CPU is at about 50%. Open one more and it goes to 80% and stays around there - so the cpu is overloading.

Mine will shutdown, but the flash is still an issue, what a pain in the a5s.

---

### Post by johnuk on 2009-08-09
Not wanting to spread any false hopes, I finally decided to install my favourite, Opera. I hadn't bothered when I started using Ubuntu since I couldn't get Firefox off, and didn't want useless extra browsers, so thought I'd get used to Firefox.

I don't like it, Opera has always been my weapon of choice.

I now have five youtubes playing simultaneously. The CPU is at full capacity, and they're a bit jumpy flicking back and forth between them, but no greying out so far.

What's more, when I pause the videos, the CPU usage falls back to nothing.

Hopefully, this is the answer. GO OPERA!

Seems when Firefox runs the plugin, it's locking the CPU usage even with the videos or ads paused.

I'll keep checking it out and let you know how it goes, but wanted to post up now so, if it works, no one else is wasting time trying to work out what to do. 'Stall it up and see how you get on, I'd be interested to hear.

Might also be worth installing something to strip unwanted flash ads from sites.

---

### Post by johnuk on 2009-08-14
All goes well on the Opera front - Opera all the way amigos :popcorn:

---

