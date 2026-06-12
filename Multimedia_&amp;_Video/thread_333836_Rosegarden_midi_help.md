---
title: "Rosegarden midi help"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by chocolatemintmocha on 2007-01-08
Hi I just downloaded the Rosegarden Midi interface, and I recieved an error. When I start the program a popup window says "Sequencer startup failed: MIDI subsystem has failed to initialise". I installed timidity and jackd, but had no luck. Any suggestions?

---

### Post by Magnes on 2007-01-08
Have you tried installing Rosegarden from the repository (in Synaptic or with apt-get)?
What soundcard do you have?

---

### Post by Unterseeboot_234 on 2007-01-09
Read up on the UbuntuStudio. You HAVE to have the sequencer turned on. Without that sequencer running, JACK and/or anything else you try to run will crash.

[**UbuntuStudio Wiki**]("https://help.ubuntu.com/community/UbuntuStudioPreparation")

From that, I learned you have to 
```
sudo modprobe snd-seq
```

That starts the sequencer, before you get JACK started. Evidentially, sound on Linux is very versatile but very annoying to set up. The above modprobe is to get the ALSA midi sequencer going. Might not be what you want. I have several other packages making sound. I have Rosegarden getting up to GUI without crashing. What I don't have is any sound. None.

Having said all that. I think I will have to go back to the Rosegarden user forums. I did read of one user that had JACK, TiMidity, Rosegarden. One of the devlopers of Rosegarden doesn't like that set-up. In FAQ at [www.rosegardenmusic.com](www.rosegardenmusic.com) they talk about FluidSynth, then find a soundbank of soundfonts, and then loading everything up at once in the terminal.

So, I'll watch this thread. Sound is a problem because you might be trying to use a USB midi, or an onboard sound chip with a Soft Synth, a firewire .midi, a midi keyboard through the joystick plug and on and on and on. Me, I'm trying to use a soft synth with an onboard sound chip. I want to be able to open a .wav and save out .midi, or ogg or .auf. Windows can do it. Why can't linux?

---

### Post by sgx on 2007-01-09
[ Why can't linux?[/QUOTE]
Install jackd, qjackctl, vkeybd and zynaddsubfx.
Start them as root user in that order. Put zyznaddsubfx on a second
desktop. The timings in the softsynth should later be changed to match
jackd. In qjackctl, there is a midi panel and an audio panel. In midi,
you must select the midi softsynth (zyn in this ezample) and vkeybd
or your midi keyboard, and then press the 'connect' button, and in the audio panel, select zyn and alsa_pcm, and press the connect button.
Now you have music. Zyn also has its own larger virtual keyboard, if desired. Enjoy! Substitute mx44, amsynth, fluidsynth as desired...

---

### Post by Unterseeboot_234 on 2007-01-10
Hey, many thanks for your post, SGX, but there's still problems. I'm about ready to ditch Rosegarden for the 2nd time. One little glitch in Rosegarden and linux crashes with no hope of recovery.

Your advice works if we want to hire a pianist to come over and play a keyboard for us.

Sad, really sad, that Rosegarden includes sample .midi files but NOT ONE soundFont!!!!! I can hook up all the plug/links in JACK, look in the setup within Rosegarden and it will tell me Audio/midi are fine. Hit the Play button and no sound. Peruse the Rosegarden forums and FAQ and they tell you Rosegarden needs soundFonts. Maybe Rosegarden can route through something with soundFonts already there????

So, after saying all that, can we use something Linux to record??? Any music file format and then export to .midi???? .midi offers so much for external things like sheet music.

Thanks, EVERYBODY on these Forums. I've learned and accomplished a lot.

---

### Post by fredbird67 on 2007-01-18
In response to Unterseeboot_234, I too had that problem with Rosegarden with Ubuntu.  Also, the very same thing happened to me on Kubuntu as well.  I then tried Rosegarden on MEPIS, and it ran beautifully, and that's the distribution I've been running ever since.  Hopefully the mods won't kick me out over saying that, but in this area, MEPIS just happened to shine where Ubuntu crashed.

However, I'm also curious about whether the MIDI and Rosegarden situation has improved in Herd, the next release of Ubuntu.  Has anybody here tried anything MIDI-related yet in Herd, and if so, how'd it go?  If the situation has improved, I'd like to be able to get back to having a choice of desktops to boot up with the Ubuntu/Kubuntu/Xubuntu combo loaded, although if I had to choose just one desktop to work with, it'd be KDE, and that's all that MEPIS has, but I prefer to have a choice in desktops available, ya know?

Fred in St. Louis

---

### Post by sgx on 2007-01-19
[QUOTE=Unterseeboot_234;1992512]Hey, many thanks for your post, SGX, but there's still problems. I'm about ready to ditch Rosegarden for the 2nd time. One little glitch in Rosegarden and linux crashes with no hope of recovery.

snip

there is a soundfont at [www.hammersound.net](www.hammersound.net)
called 'fluid', it is in the 'collections' area of the soundfont section
browse a bit, you'll find it, about 60 meg , I have used it
with qsynth/fluidsynth (no relation) its a general midi set that sounds great...google 'dave philips fluidsynth' the ...'sounding edge' link is a handy tutorial, he has many! Mepis is a good alternative, and for
musicians, a killer interface of scrolling multiple desktops can be set up!
Get dssi and hexter, as hexter can load thousands of free yamaha dx7
preset banks, utilize ecamegapedal and creox for fx, and don't rule out
muse as a sequencer, it is actively developed too...

---

