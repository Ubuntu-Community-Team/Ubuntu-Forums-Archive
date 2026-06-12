---
title: "Saving projects that use multiple applications (eg, ardour, hydrogen, seq24, etc)"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by philipacamaniac on 2006-08-05
Is the UbuntuStudio team planning on creating some kind of GUI for opening projects? The way I'm doing things now takes way too long and is too confusing.

Currently - I'll save a beat in Hydrogen as an h2song, and save the bassline as a MIDI sequence in seq24, and then save the actual bass sound in qsynth as a template, and then save all the JACK connections in qjackctl. Then if I want to open all that back up - holy crap!

Wouldn't it be great if UbuntuStudio had a GUI that listed all your songs/projects (and listed what components each uses), and then opens up all the apps with files and settings already loaded. It seems like the opening part would be pretty easy to program (most apps can load files and settings from the CLI), but I don't know how saving would work.

Another feature that would be great is a Sound Library. Imagine a organized list of pianos, basses, synths, etc.  Just choose a sound, and it loads the appropriate qsynth/ams/zynaddsubfx/specimen/etc settings. And it would be even cooler if it also created a ready-to-go sequencer track in Seq24.

Trust me when I say, though, this is the killer UbuntuStudio app, once someone creates it.


Off Topic - why don't Seq24 MIDI connections show up in qjackctl? Seq24 doesn't seem to save its MIDI options internally. If they would show in qjackctl, I could save them that way. Otherwise, is there a better alternative to Seq24?

---

### Post by dolson on 2006-08-05
Right now, there isn't really an Ubuntu Studio Team. It's just me and a couple other people who work on some packages when we have spare time. I also put info into the wiki site when I have time. But I don't have as much time now as I used to.

But it sounds to me like you want something like... LASH.

Like this: [http://lash.nongnu.org/screenshot.png](http://lash.nongnu.org/screenshot.png)

---

### Post by philipacamaniac on 2006-08-05
Hey, it's a team, even when it's only a few people working part time.

LASH looks like a good start for a song/project manager. It doesn't support enought client apps yet, but at least it's what I was looking for. Although, I'd rather see a manager that doesn't require code changes in the client apps.


But a question remains - how do you guys open and save your multi-app projects? What file structure conventions do you use?

---

### Post by dolson on 2006-08-06
Well LASH is the standard, since before when it was called LADCCA. Really, I think what you want would be almost impossible.

I started work on the Ubuntu Studio Launcher to resolve this, but using template files only, and I found that some apps did not allow you to load a file at launch, which is both retarded and puzzling. This isn't to say that it couldn't be done, but I'm not working on it any more than I have in the past. LASH is more advanced and should be the standard, in my opinion.

Clients should only have to write the code once, and it's just a matter of time before they do. Some will be stubborn, I'm sure, but then, there are apps that don't support JACK even, so yeah.

Ideally, we'd just have a single app to do everything. I realize this is not how Linux usually works, but it's something I'm learning very quickly, that this is one example of a time where the Linux ideology just gets in the way of production. It's also the only example that comes to mind.

---

### Post by kellogs on 2006-08-06
I think the workflow in linux is quite different. We've got the freedom of opensource projects... programs are independently created, there is no central plugin program/ standard like windows where people load dependent librarys or plugins(look at kompakt/kontakt for example). that has some good points, the freedom of connecting everything and having it working without too many incompatibility problems.... and the lack of a centralized application to have all loaded at init time. so by now we will have to wait for the application which does all of this, if it is created by somebody in the future...

while this happens, we will have to load a bunch of plugins before loading the music application we use in linux... well we have jack, it could be worse.. ;)

---

### Post by dolson on 2006-09-11
> **philipacamaniac said:**
> Off Topic - why don't Seq24 MIDI connections show up in qjackctl? Seq24 doesn't seem to save its MIDI options internally. If they would show in qjackctl, I could save them that way. Otherwise, is there a better alternative to Seq24?

No, there is nothing better than seq24. Seq24 is the bee's knees. Seriously.

Run it as: seq24 --manual_alsa_ports

And voila! You can now connect it in JACK Control.

---

### Post by kellogs on 2006-09-11
the only thing I see as a problem is that in windows you have the Vst format, which is able to read the state of all the knobs of a vsti/vst synth. this state is known as standard .fxb patch, or preset/presets and is loaded at the same time you load all the synths in the project in many applications (ie. Fl Studio) Something like that is needed in linux apps, so the problem of synth /patch loading would be resolved. 

I dont know the project LASH, but if there is a way to make the synths load their last state/patch as in fxb... that should be fantastic, no more need to load every plugin and load every synth-dependent-format again.

---

### Post by dolson on 2006-09-11
> **kellogs said:**
> the only thing I see as a problem is that in windows you have the Vst format, which is able to read the state of all the knobs of a vsti/vst synth. this state is known as standard .fxb patch, or preset/presets and is loaded at the same time you load all the synths in the project in many applications (ie. Fl Studio) Something like that is needed in linux apps, so the problem of synth /patch loading would be resolved. 

I dont know the project LASH, but if there is a way to make the synths load their last state/patch as in fxb... that should be fantastic, no more need to load every plugin and load every synth-dependent-format again.

Yes, that is the goal of LASH. Some synths support it already, such as ZynAddSuybFX. Hopefully it will spread to every worthwhile software synth.

---

### Post by zettberlin on 2006-09-11
> **dolson said:**
> LASH is more advanced and should be the standard, in my opinion.



This i agree: there need to be a standard for total recall and as evolution takes its toll, apps that do not support LASH will be left behind as those are, that did not support jack (though it is a shame in some cases like Audacity to name only the greatest loss if you work jackd-only).

I put some effort in static scripts that can load several apps with correct connections and patch/projectfiles:

[http://www.linuxuse.de/snd/law-en.html](http://www.linuxuse.de/snd/law-en.html)

but those are made for a known predefined set of applications and will work only as long, as you write your Music into their predefined files - so in the end they can only serve sufficiently as tutorials or for quite basic work. Once you are familiar with the system you will want to do things your own way and to hack the scripts is quite clumsy and still limiting intuitive work.

For example:
 you run a script, that loads Zynadd plus Muse to play it. If you want to change the sounds for muses own drummachine, there is no Problem next time, since muse can remember the settings of simpledrums. Same with changing the loaded Zynaddpatch (as long as you save it under the same name as the loaded one) but now you want to add specimen to your set and you will encounter the problem, that the script does not know about specimen and muse cannot remember/reload the sampler next time you run the script. You would need to add the commands to load specimen  before muse is being started to the script...
Only a daemon like LASH could solve this.
So let us have fun with what we have and promote the developement of LASH..:grin: .

---

### Post by dolson on 2006-09-12
Audacity's development version had JACK support.

---

### Post by capsid on 2006-09-26
> Currently - I'll save a beat in Hydrogen as an h2song, and save the bassline as a MIDI sequence in seq24, and then save the actual bass sound in qsynth as a template, and then save all the JACK connections in qjackctl. Then if I want to open all that back up - holy crap!

Tell me about it.  I'm coming from Reason on windows, so it's quite a shock to manage all these connections between programs.  I'm trying to make a workflow that puts as much in seq 24 as possible.  Like, instead of saving a hydrogen drum track, I'll just make the beat in seq24 and send it to hydrogen. When I open hydrogen, all I have to do is Alt-D and load my kit. It also helps to open your regular apps in a regular order so Seq24 *kind of* remembers its connections.  Most sound sources seem to auto-connect to pcm_out, which helps.

It would be great if you could change synth parameters with midi control/program messages so you could essentially embed the synth sound in the midi file as well.

---

### Post by dolson on 2006-09-26
capsid, your last sentence might be possible. You should email a feature request to Rob and see what happens. He has a big list of features, and not a big list of coders. I have looked at the code a bit, but it's still over my head, so I can't help out at this point in time..

In any case, doing all the connecting isn't too bad, if you are lucky and JACK doesn't quit on you. Then you have to restart most applications. That is the biggest pissoff of all, for me personally.

I have compiled ZynAddSubFX and seq24 with LASH support, but I haven't tested it out much yet.

By the way, running seq24 with --manual_alsa_ports might help make connections easier, since you can do it all in JACK or ALSA's MIDI connection GUI.

---

### Post by dolson on 2006-09-26
Looks like it already is possible, I just saw this on the mailing list:

> >> in a sequence window, change the event view ("Event" button on the
>> bottom side) from 'Note velocity' to 'Volume' or 'Program change'
> 
> Ok I figured that much out myself. Where do I press/click to insert the 
> actual event?
> 

there is a rectangle, between the pianoroll the velocity pane.

here you can add new events (of type: you selected it just before) just
like you do for adding new notes, then you can change their value in the
velocity pane

I haven't tried it yet myself.

---

### Post by kellogs on 2006-09-27
> Looks like it already is possible, I just saw this on the mailing list

I know this one ;). You can change events like notes, for example you can change between patches on the same midi channel and the same block/track in seq24. I use it to give naturality to some basses, for example if you have 2 different bass programs in a soundfont and one of them sounds scratchy/noisy you can change the (program) event between them. I miss random velocity feature that would be 'teh bollocks'. I think seq24 is a beast. did you know you can change note-length with the central mouse click? I use that for long string notes.

Seq24 have got some impressive multitimbral capabilities that other soft in windows makes you pay for. and all this done quite easily!

---

