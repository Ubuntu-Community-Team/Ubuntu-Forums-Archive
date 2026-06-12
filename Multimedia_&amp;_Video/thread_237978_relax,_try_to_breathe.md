---
title: "relax, try to breathe"
date: 2006-08-17
forum: Multimedia &amp; Video
---

### Post by mzembe on 2006-08-17
a lot of times I update an ubuntu install where once audacity would record and it just stops working. I get sound from the speakers from the input device but audacity can't hear it.
Drives me nuts.
must be that pasound? or sdl..maybe some kind of OSS compatibility - I can't really remember all of the complications of the dependencies were. All I know is that it sucks when that happens.

---

### Post by em3raldxiii on 2006-08-17
OSS is the "legacy" linux audio system.  ALSA is the newfangled way of things.  I am not 100% what your problem is exactly ... hard to tell from your post, but here's what I think is happening:

You've installed Ubuntu and apt-installed Audacity.  You can play CDs and MP3s, and you can plug in other input devices and successfully hear them through your speakers.

But when you attempt to record with Audacity, it behaves as if it is recording, but it doesn't actually record the sounds from the inputs.

Questions:  Are there any sounds at all in the recording?  Have you adjusted your mixer to *record* from specific devices such as your line-in or your mic?  (as opposed to just making them play)

Possible solutions:  Install and mess with alsa mixer?  (Right click on your speaker icon and try preferences, or just open the volume control and check out the Capture tab).  Perhaps you could try installing JACK ... I'll see if I can find a the apt-get command.  It's a sound-server that controls ALL theinputs and outputs.  It treats programs as if they are "devices", so don't get confused if you decide to play with it.  Finally, with JACK, you might also try using ARDOUR for recording.  It's a complete audio workstation (DAW) that might be a bit heavy for your needs, but it's definitely commercial-class software (sudo apt-get install ardour).  [www.ardour.org](www.ardour.org)

Hope that helps you a little ... let me know if you need more info or if perhaps I misunderstood your question.

---

### Post by mzembe on 2006-09-30
It's a C400 dell laptop with the external cdrom... the machine freezes too if I unplug the cdrom while it's running.
Well, it turns out that if I boot without the cdrom audacity records and with the cdrom it plays audio fine but audacity won't record. I had updated the machine and afterwards the recording function 'broke' - apparantly it was a coincidence.

---

### Post by em3raldxiii on 2006-10-01
LOL that's a quirky issue, hey?  Well, I think if you want to disconnect the CDRom when it is running, you have to "unmount" it first.  Let me know if you don't know what I am talking about.

And are you trying to rip CDs directly?  If so, I believe there is a little menu script that can do it directly in Nautilus.  It might be part of the Sound Juicer package, though I am not 100% sure.

Finally, sometimes when you do updates, it changes configuration files back to default, or to new "more common default" situations.  This may have been what happened.

---

### Post by mzembe on 2006-10-02
When I'm screwing around on the guitar I record it with Audacity. At first I was using the synaptic installed audacity but I built the source version to see if that would fix it.. I guess it is just some weird hardware thing. 

Lol. "a lot of times when I update ubuntu" - ok well, maybe just that once.

---

### Post by em3raldxiii on 2006-10-03
well, not that this helps, but my wife (check my sig for a link to her stuff) records stuff with Ardour. It's right on par with proggies like Nuendo, Cakewalk, Protools ... that sort of thing.  It [COLOR="Red"]is[/COLOR] different, but you might like it.  Check out [www.ubuntustudio.com](www.ubuntustudio.com) for more on recording audio such as guitar :D.

---

### Post by TheFlamingBush on 2006-10-03
once again Emerald, you come up trumps mate! :)

ardour looks fantastic and just the ticket for a bit of recording ive been wanting to do, and your other link will do very nicely, thankyou very much! :).....ive now downloaded Ubuntu studio, and am looking for a good Guitar program! :)....since i play like crap!

LOL ;)


OH just one question!...how do i get JACK em?......ive had a look on apps and couldnt seem to find it? :-k

---

### Post by em3raldxiii on 2006-10-03
mmm, yes ... jack is the "wierdest" part of this whole process.

```

sudo aptitude install qjackctl

```

Once you have it installed, you have to start JACK before you start Ardour.  Jack treats all of your programs, files, plugins, etc etc as if they are hardware connections.  As such, you may have to tell Jack which devices to patch to.  I haven't done much more than get a basic input on my soundcard to record into Ardour.  I freely admit that I have been somewhat ... hesitant ... to go much deeper (yet).  From what I can tell, there are a ton of folks who use it for full-scale recording.

There's a fellow around here ........ **[COLOR="Red"]Dolson[/COLOR]** he goes by, he, I believe, is the resident genius when it comes to home recording with jack/ardour.  He is heading up the Ubuntustudio and the Mubuntu development teams, but he's been more than willing to chat with me about more mundane issues on occasion.

---

### Post by mzembe on 2006-10-04
Yeah, I was messing with mubuntu stuff yesterday - it's kind of a lot of trouble for plain recording but it /would/ be kinda cool to have the meterbridge retro analog stuff. 
I hear there is a this 'session management' voodoo that will allow you to start and stop several different applications that doesn't step all over your settings each time. That would be nice.

---

