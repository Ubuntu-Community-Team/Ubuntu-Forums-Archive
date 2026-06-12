---
title: "Help getting Ardour and Hydrogen to play together"
date: 2007-08-22
forum: Multimedia Production
---

### Post by jondecker76 on 2007-08-22
I've got the hang of jack and routing signal paths.
I'm getting better at ardour...
And i've got Hydrogen down pretty good.

For some reason, I can't combine the 3 like I want to.

I start Jack, then start hydrogen and ardour.
In ardour I create a stereo track. I then connect the master outs to my pcm outs. So far so good.
Now with hydrogen, i connect the outs to track 1 in

So, it should be Hydrogen L/R out ->Ardour Track1 L/R in 
Ardour Track1 LR out - > Ardour Master L/R in
Ardour Master L/R out -> Alsa_pcm 1 and 2

I set Ardour to time master, and select the Jack dropdown.
I set Hydrogen to use Jack transpose.
 I hit play on any of the transports and everything starts playing as it should...
However, there is no sound to be heard!!

If I connect Hydrogen directly to the pcm outs, i can hear it fine. But if I connect it to a track in ardour, and then take ardour to the pcm outs, I don't hear anything, nor do I see the peak meters jumping on the ardour track.

Why am I not getting sound like it appears I should?

thanks,

Jon

---

### Post by nalmeth on 2007-08-22
Can you please post a screenshot of your connections window?

Have you altered the software/hardware monitoring settings in Ardour? Did you remember to arm the track for recording? 

It shouldn't matter, but do you have any different results when manually playing the apps, rather than using Jack Transport?

---

### Post by jondecker76 on 2007-08-31
Ok, I finally had some time to look deeper into this and get some screenshots. Here is a quick synopsis:

First I opened JackCtl and started the Jack server. I then Opened Ardour and Hydrogen.

Just to test things out, I first added a track in Ardour. I set up the routing as:
Microphone->Track1 in Ardour->Master Outs->Alsa Playback. I can then speak in the microphone and hear results on my monitors. (Screen below)
[IMG]http://i229.photobucket.com/albums/ee95/jondecker76/UbuntuForums/JackArdour.png[/IMG]
This test proves that ardour can receive input and output the audio to my monitors.



The next test I did was connect Hydrogen with Jack. In this routing:
Hydrogen->Alsa Playback
Again everything works as expected - I hit play in either Jack Transport or Hydrogen and I get the sound as expected out of the monitors.
[IMG]http://i229.photobucket.com/albums/ee95/jondecker76/UbuntuForums/HydrogenArdour.png[/IMG]


Now I get to the part that I want to link Ardour and Hydrogen together. In this routing:
Hydrogen Out->Audio1 In in Ardour->Master Outs in Ardour->Alsa playback
I thien start the transport..  In Hydrogen I can see the level meters bouncing, but no visual activity at all in Ardour, and no sound at all..
[IMG]http://i229.photobucket.com/albums/ee95/jondecker76/UbuntuForums/JackArdourHydrogenRecOff.png[/IMG]


Ok, so now I try something different. I leave the routing the same, but I hit the Record button on Audio1 (my only ardour track) and then hit play on the Transport (without enabling the master record button). The results this time - Level meters are bouncing in both Hydrogen and Ardour - but still no sound!!
[IMG]http://i229.photobucket.com/albums/ee95/jondecker76/UbuntuForums/JackArdourHydrogenRecOn.png[/IMG]

Now for my last try - Same routing again, accept this time I hit the record button on my Audio1 track, and enable the master record button in Ardours transport then hit play...  The level meters bounce in both Hydrogen and Ardour again, and I get sound!! But I am recording :(
[IMG]http://i229.photobucket.com/albums/ee95/jondecker76/UbuntuForums/JackArdourHydrogenFullRecord.png[/IMG]

What I want is to be able to route my hydrogen output through a mixer strip in Ardour andbe able to hear and mix it with Ardour without having to record it.. Kind of like a "Live Music" mode where the output goes to my monitors without having to record it.

Can anyone help me?

---

### Post by nalmeth on 2007-09-01
>  Now I get to the part that I want to link Ardour and Hydrogen together. In this routing:
Hydrogen Out->Audio1 In in Ardour->Master Outs in Ardour->Alsa playback
I thien start the transport.. In Hydrogen I can see the level meters bouncing, but no visual activity at all in Ardour, and no sound at all..
--
Ok, so now I try something different. I leave the routing the same, but I hit the Record button on Audio1 (my only ardour track) and then hit play on the Transport (without enabling the master record button). The results this time - Level meters are bouncing in both Hydrogen and Ardour - but still no sound!!OK, this may destroy your latency when recording something else at the same time, but if you specifically need hydrogens output going thru Ardour in this way, this is what you do:

In Ardour's window menu, go to Options -> Monitoring -> Software Monitoring
(default should be Hardware Monitoring)
You should hear Hydrogen coming through on the quoted steps in your post.

But can't you just route Ardour *and* Hydrogen-out to ALSA, using JACK Transport to keep the two in sync? Maybe I misunderstand

---

### Post by jondecker76 on 2007-09-01
I'm already set up for software monitoring, so thats not it.

I'm not sure if we are talking about the same thing..  Maybe if you could describe the normal workflow of say:
-I recorded my guitar passage and laid the regions out in a track
-I make a new track (or tracks) for drums
-I want to hear the drums play with my guitar that was recorded/laid out in ardour so that i can test it before recording
- Once the drums are don in hydrogen, record them into the ardour tracks

The only way I can see to play my guitar in ardour and practice laying out  and listening to my hydrogen drums at the same time would be to route the outputs of both ardour and hydrogen to alsa_pcm.
But it would make sense to have hydrogen tracks running through my ardour tracks so I can mix etc before recording, then when ready just enable the record button on that ardour track.

what am I missing?

---

### Post by nalmeth on 2007-09-01
I see what you're saying now, and recreating your steps I got the same outcome. Hydrogen will playthru Ardour (Hydrogen out -> Ardour Audio 2 -> Ardour Master -> ALSA) when the transport is stopped. But when you start playback, you can't hear Hydrogen unless you are actually recording it into a track. 

What kind of mixing do you do to the drums before recording them? If its simply volume or gain adjustment you could do them thru hydrogen, or afterwords by applying plugins to the drum track. 

You could use jackeq or jack-rack for live monitoring, or in Ardour, make a recording in the track anyway, and either delete the region afterwards, or use the playlist feature for the track. 
Won't the timing be different between the guitar and drums anyway?

Your methodology is different from mine, which is why I didn't quite get what you are saying.. 

I usually record the guitar ideas first without drums/bass, then arrange the song, figure out and record the drums, then re-record the guitar overtop of the drums so that everything is in time, and add bass/solo after that. 

In any case you seem to be right that Ardour doesn't seem to route the hydrogen signal through during playback, unless its actually recording. I thought software monitoring would take care of this, but there is something we are missing.

---

### Post by jondecker76 on 2007-09-01
I'll figure it out eventually I guess. A lot of my poblems stem from my old production methods in Windows. I'm sure it'll get easier once i fully understand the workflow under linux.

What I'm doing for now is just routing both Hydrogen and Ardour both to alsa_pcm, then when I'm ready to record i route it to a track to record. I just like to stop periodically so I can play the drums and guitar parts together so i can see how it sounds. It would just be nice if it could be done without having to change routing constantly in Jack to get this accomplished.

Though I am progressing - I'll attach a piece I'm working on right now- needs a lot of work but I'm just trying to get the right mood for the music

---

### Post by nalmeth on 2007-09-02
Hey man, that sample sounds great!

Very clean sound, and I like the guitar parts. Of course it stops right when it sounds like its going to pick up.

I think it would be cool if we all started posting things we made in Ubuntu, maybe all in one thread, or however works.

Right now I'm not doing much recording. I'm having some problems with my Firepod, and working on installing 64Studio today. That and I just moved all my gear. 
I'll try to find my backups, maybe I'll find something I want to post :)


See you around

---

### Post by jondecker76 on 2007-09-02
Thanks

I have a few things I'm working on, once i get a complete composition under my belt in linux I'll post my results. Time is the enemy right now, but I'll get one finished eventually.

Unlike a lot of people, I rarely lay out a whole track at a time - i like to do it in chunks (like in this example just up to where it is going to pick up). I feel it makes it easier than laying out an entire guitar track then trying to build everything around that.

I'll definitely be posting some of my work as I finish them!

---

### Post by paulg on 2007-09-18
Hey guys, this may be what you want. Try routing the Hydrogen outputs to the Master 'inputs' for Ardour. That should work. 

I would recommend a new stereo bus for the hydrogen track so that you have independent slider, pan and plugin spaces for the Hydrogen track within the Ardour mixer. So Hydrogen outputs to new_bus inputs, new_bus outputs to master inputs.

Let me know if this gets you where you wanted to be.

---

### Post by paulg on 2007-09-18
Hey guys, this may be what you want. Try routing the Hydrogen outputs to the Master 'inputs' for Ardour. That should work. 

I would recommend a new stereo bus for the hydrogen track so that you have independent slider, pan and plugin spaces for the Hydrogen track within the Ardour mixer. So Hydrogen outputs to new_bus inputs, new_bus outputs to master inputs.

Let me know if this gets you where you wanted to be.

---

### Post by jondecker76 on 2007-09-18
Thanks paulg - i will try this when I get home. Never thought of using a bus for this purpose before..

thanks again

Jon

---

