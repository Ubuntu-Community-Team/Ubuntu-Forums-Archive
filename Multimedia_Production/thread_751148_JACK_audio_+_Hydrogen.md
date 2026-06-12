---
title: "JACK audio + Hydrogen"
date: 2008-04-10
forum: Multimedia Production
---

### Post by Atraeus on 2008-04-10
Hi all,

I would like to start using the JACK audio server and JACK savvy programs for music creation, but I've been having some problems. As of now, I only want to route the main output ports from hydrogen to the alsa_pcm input ports using JACK. When I do this, I get no sound out of hydrogen.

I have verified that Hydrogen connects to JACK, and that my ALSA drivers are operational. If I change my audio driver in hydrogen from JACK to ALSA I get sound just fine. Just in case you need it, here is the info on my card.

00:0d.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
Subsystem: ABIT Computer Corp. Unknown device 1c1e
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
I/O ports at f000 [size=256]
I/O ports at ec00 [size=256]
Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>

Thanks in advance for any help.

---

### Post by Stochastic on 2008-04-10
Your alsa_pcm input should be a mic-in jack, not where you should send the output of an audio program.  If you're trying to play Hydrogen through your computer's speakers connect Hydrogen's outputs to the alsa_pcm outs.

If that was just a typo, and you are connecting to the right outputs, what program are you using to make the connection (patchage, qjackctl, or hydrogen internally)?

---

### Post by Atraeus on 2008-04-10
Hey Stochastic ,

I am using qjackctl to set up my connections.  What I said was probably a typo, I am 80% sure I have things connected correctly.  I've posted a screenshot of my connections window, just in case.

There is something that I am now noticing in the messages box too.  This is what happens when I boot up hydrogen after loading qjackctl.

JACK tmpdir identified as [/dev/shm]
23:03:22.675 Audio active patchbay scan...
23:03:29.436 Audio connection graph change.
23:03:29.511 Audio active patchbay scan...
23:03:29.512 Hydro: Hydrogen-1:out_L -> alsa_pcm:playback_1 failed.
23:03:29.513 Hydro: Hydrogen-1:out_R -> alsa_pcm:playback_2 failed.
23:03:29.513 Audio connection change.
cannot connect ports owned by inactive clients; "Hydrogen-1" is not active
cannot connect ports owned by inactive clients; "Hydrogen-1" is not active
23:03:29.602 MIDI connection graph change.
23:03:29.612 Audio connection graph change.
23:03:29.714 Audio active patchbay scan...
23:03:29.743 Hydro: Hydrogen-1:out_L -> alsa_pcm:playback_1 checked.
23:03:29.747 Hydro: Hydrogen-1:out_R -> alsa_pcm:playback_2 checked.
23:03:29.749 MIDI active patchbay scan...
23:03:29.750 MIDI connection change.
23:03:29.952 MIDI active patchbay scan...

Particularly the Hydrogen-1 is not active part.

---

### Post by Stochastic on 2008-04-11
Ok, most of this looks good.  I do remember having some troubles with Hydrogen & Jack when Hydrogen auto-connected itself to jack (switchable in Hydrogen's preferences panel) but it worked fine when that feature was turned off and the connection was done by hand in qjackctl - are you auto-connecting?  That may be what's causing the error message in Jack, a pre-mature attempt to connect itself to Jack before it's active then screws up your second connection.

If that's not the cause, we need to start analyzing the pieces here.  Can you get a different JACK application to play out of JACK?  Can Hydrogen be patched into a recording app and recorded?

---

### Post by Atraeus on 2008-04-14
Hey, sorry for the delayed response.

I've had some small progress with Rosegarden.  I managed to get sound when I connect the Rosegarden general midi device to the fluidsynth midi input port using JACK.  BUT, this is only because I set fluidsynth to use the ALSA drivers instead of connecting them via JACK.  When I hook up the fluidsynth out ports to the alsa_pcm in ports using JACK, I get no sound.

Additionally, I've tried syncing Hydrogen with Ardour to record and play, but I cannot get Ardour to produce any sound either.

One thing I did notice is that I cannot disconnect the Hydrogen out ports from alsa_pcm once Hydrogen is loaded.  It keeps reconnecting them for me.  I've played around with just about all the options in Hydrogen, and none of them seem to fix this.

---

### Post by Stochastic on 2008-04-15
Hmm, this really is strange.  It's obviously an issue with jack if you can't get anything out of other programs.  You might want to go into Synaptic Package Manager (in System -> Administration) find jackd and qjackctl, right click on the box beside their package, and choose mark for re-installation, then click aply.  Or you may just want to try to re-install everything when Hardy gets released in 9 days.

---

### Post by kayosiii on 2008-04-18
there is a good solution here 
[http://www.hydrogen-music.org/forum/index.php?action=show_thread&thread=545&fid=5&page=1](http://www.hydrogen-music.org/forum/index.php?action=show_thread&thread=545&fid=5&page=1)

---

### Post by Atraeus on 2008-04-25
Hey guys.  I switched from Gusty 7.10 to Ubuntu Studio 8.04, and everything works fine now.  Thanks for the help

---

