---
title: "music scoring / sequencer behavior query"
date: 2010-12-20
forum: Multimedia Software
---

### Post by wog on 2010-12-20
I'm not a musician and I have a musical and Linux software question.

I once saw something in a Mac music scoring app where running your mouse up and down the scale on the little horizontal lines would actually sound each note in turn. Unfortunately I don't remember what the name of the Mac program was, although it was before the days of the iMac.

What is that sort of 'note sounding' behavior called in music software? Are there any Linux programs that do that?

Thanks in advance if you can name the Mac program, the note-sounding behavior or suggest a Linux program that does this. I am completely lost.

---

### Post by lasconic on 2010-12-20
You can try MuseScore : [http://musescore.org](http://musescore.org)
It's in the ubuntu repository too.

---

### Post by cchhrriiss121212 on 2010-12-20
I think you are referring to a piano roll, did it look like this one?
[http://www.cakewalk.com/products/USBMusicPack/pianoroll.htm](http://www.cakewalk.com/products/USBMusicPack/pianoroll.htm)
> 
What is that sort of 'note sounding' behavior called in music software? Are there any Linux programs that do that?There are a few ways of using a computer to create sound. The most commonly used are:

[LIST]
[*] A software synthesizer - synths produce noise and can be altered using filters and envelopes. There are plenty of these for linux: phasex, bristol, yoshimi, AMS etc. just type "synth" into the software center and try one out. You can play them with a virtual keyboard.
[*]Using samples - samples are recordings of actual instruments that can be played back at certain pitches or volumes controlled by a computer. On linux you can use qsynth to play sf2 files which contain large banks of samples. There is also hydrogen which is a very good drum sequencer.
[/LIST]
Both of these can be used with MIDI which is a way of saving a digital score of music.

This stuff might be more than you are looking for right now but it is all there in the repos if you ever wish to try it out. For an introduction to audio production on computers, I recommend LMMS which is a complete package of tools and instruments. It is very easy to set up and includes various synths to play with.

---

### Post by wog on 2010-12-20
lasconic:
I have musescore in Windows. I guess I might as well install it here, but I haven't been able to get this note-sounding behavior from it.

How do I set musescore to do this behavior?

cchhrriiss121212:
It isn't a pianoroll, although I'm considering using one if I can't get this behavior out of a music scoring program. The musical environment I wanted involved something that looks like sheet music (I was sort of hoping I could use it to learn to read sheet music over time). Hell, I'd be willing to try to use Windows programs under Wine to get this note-sounding behavior!

Thank you for the "synth" search suggestion. I will try all of those. As I said, I'm not a musician, so piano keyboards aren't going to make a lot of sense to me at first.

So far, drum sequencer software has looked impenetrable. I briefly tried Sony's sample looper program, but could never figure out how to get different pitches out of a given sample besides the pitch the sample was already in. Hopefully qsynth will be easier to figure out, or will contain a good, step-by-step tutorial.

I will try LMMS at some point. If I was thinking of trying FL Studio through Wine, I might as well try something Linux-native first.

---

### Post by cchhrriiss121212 on 2010-12-20
I forgot to add: some synths will require you to use the jack sound server, which is designed for low latency audio. Jack will require additional setup work as it is still not very user-friendly.

Zynaddsubfx is a synth that will work without jack and has a built in virtual keyboard. I think a keyboard is easier to use than sheet music, but you can decide that for yourself. 

White keys = happy
Black keys = sad

---

### Post by wog on 2010-12-20
cchhrriiss121212:
I installed Jack Control, so presumably it installed what it needed to (although I don't know that for certain).

I learned about a couple of the lower latency settings yesterday and set them (just to make my system faster), but I don't know what else I have to set, if anything.

Is there a guide on what I need to set to make LMMS work right? Or maybe a script I can run?

---

### Post by cchhrriiss121212 on 2010-12-20
> I learned about a couple of the lower latency settings yesterday and set  them (just to make my system faster), but I don't know what else I have  to set, if anything.
Low latency is not all that crucial unless you want to record things (even then you can still get around it). With a modern onboard soundcard you could probably get around 10ms latency, maybe lower if you only use playback. What you should aim for first is stability so see if jack runs OK (if you see xruns, you need to change your settings) on default settings and then tweak them if you like. 

> Is there a guide on what I need to set to make LMMS work right? Or maybe a script I can run?
Just FYI you don't need jack to run LMMS, in fact it works much better without jack. There is nothing special you need to do to use LMMS, just start it up and it should work using ALSA. Setup wise it just has a latency value in the preferences menu and not much else.

---

### Post by wog on 2010-12-21
Okay, first thing: I don't know what xruns are. All I learned how to do was fiddle with a couple of vm settings, which as far as I currently understand change the amount of time the system browses files in the system before it goes ahead and does something. So:
```
vm.swappiness = 20
vm.vfs_cache_pressure = 50
```
in /etc/sysctl.conf
...is there something else that has an effect on latency?

Regarding jack: should I uninstall it?

---

### Post by cchhrriiss121212 on 2010-12-21
You don't need to do any kind of system file tweaking to use audio programs. If you are having problems then explain what they are and I can help.
If you just want to fiddle around with things for fun, these things will help you cut latency:
Disable compiz and wireless connections
Install low latency/rt/liquorix kernel
Add cpu scaling icon to taskbar and set it to performance
Use a lightweight DE
> 
Regarding jack: should I uninstall it?
No you can leave it there and just play around with it if you like. It won't do anything until you open up jack control and press start. My point is that it is not necessary for what you want to do.
> Okay, first thing: I don't know what xruns are.
When running jack with settings that are too low for your system, you will see xruns in the message window. They are bad as they denote audio glitches and dropouts.

---

### Post by wog on 2010-12-21
Okay, I'll make a note of those low latency settings and play with them later.

I tried turning jack on once. Thankfully I noticed it can also be turned off, so I'm happy enough just to leave it off for now.

I like LMMS so far, although it's a bit of a climb in terms of learning curve. I'll have to get to work on the tutorial and see if I can make it do anything other than a simple organ noise.

The mouse-overs contain no words or symbols of any kind. Is there a way I can fill them with anything? It might make learning how to use LMMS easier.

---

### Post by cchhrriiss121212 on 2010-12-21
> The mouse-overs contain no words or symbols of any kind. Is there a way I can fill them with anything?
Not that I know of, but you should get the hang of things eventually. Here is a simple video tutorial which shows you the basics:
[http://www.youtube.com/watch?v=EqrRwsqrBZc](http://www.youtube.com/watch?v=EqrRwsqrBZc)

---

### Post by lasconic on 2010-12-22
In MuseScore, create a new score (File -> New), choose a flute for example.
Enter note entry by pressing N, Press C. It will put a C on the staff, use the Up and down arrows keys to hear the notes on the staff.

---

### Post by wog on 2011-01-16
Can I shut compiz off without uninstalling it, and if so, how?

---

### Post by cchhrriiss121212 on 2011-01-16
> **wog said:**
> Can I shut compiz off without uninstalling it, and if so, how?
Go to preferences>appearance and set effects to "none".

---

### Post by wog on 2011-01-17
Wow! That made a lot of difference! :) I'm finding I like the low latency far more than the Compiz effects I was getting. :)
Is there really a lot of latency improvement between No Effects and no Compiz?

What Desktop Environments are low latency? I once tried XFCE, but that was kind of traumatic. Are there alternatives?

I'm currently using Gnome (inasfar as I understand the concept of a DE).

---

### Post by cchhrriiss121212 on 2011-01-17
> Is there really a lot of latency improvement between No Effects and no Compiz?
No effects = no compiz. When no effects is selected, you will be using [metacity]("http://en.wikipedia.org/wiki/Metacity") instead of compiz.
> What Desktop Environments are low latency? I once tried XFCE, but that was kind of traumatic. Are there alternatives?

I'm currently using Gnome (inasfar as I understand the concept of a DE).
Latency is an audio thing and DEs are a graphical thing, so no DE can really claim to be low latency. However, the lighter your DE is, the more resources you will have free for things like audio, and on mid-low end machines this can really make a difference. Some lightweight DEs to try:
XFCE
LXDE
IceWM
Enlightenment

For further research, take a look at [AVLinux]("http://www.bandshed.net/AVLinux.html") which is an OS designed for low-latency work. It is based on Debian and uses the Liquorix kernel with LXDE, also includes many of the best audio programs.

---

