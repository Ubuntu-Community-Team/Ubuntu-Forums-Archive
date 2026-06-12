---
title: "Software Monitoring in ArdourVST"
date: 2007-07-14
forum: Multimedia Production
---

### Post by skipkent on 2007-07-14
I have ardour vst compiled and running fine, and can get a great sound in realtime on my guitar with the phenomenal SimulAnalog guitar effects.  Problem is, with Software Monitoring enabled, everything sounds great until I hit Play or Record, then the effected guitar sound changes to a dry sounds.

Is it possible to record while monitoring an effected signal?  I've tried every sort of routing imaginable.

Thanks,

-skent

---

### Post by skipkent on 2007-07-15
quick update:  I'm all set with this now.  Ardour does not behave exactly like Cubase or Tracktion, and despite the initial frustrations, that is NOT a bad thing!

Ardour's way is a great way and totally works when you start to get it.

For software monitoring, set up stereo bus tracks for any inputs you are recording and wish to monitor.  If your recording a guitar, assign the inputs directly to that bus (as well as to the guitar track of course).  The guitar track itself will cut out when you hit play/record, but that bus will play just fine, along with whatever fx you put on it.  Put on your amp sim (SimulAnalog are the ABSOLUTE BESTEST ; ) and whatever else you like on that send 'guitar monitor' track as I like to call it and record away.

If, like me, you want to have the Hydrogen drum machine kicking along in the background, do the same thing with that.  Create a 'drum monitor' bus and route hydrogen into it (to the Ardour bus only, not to the sound card outs).

Lastly, and this is optional, go to Ardour's Options menu and click on 'Rec-enable Stays Engaged'.  Now make sure all you record buttons are disengaged.

Now you can hit 'play' and jam and tweak the fx and levels on the sends (that you listening to) and hear exactly what you're going to hear when you record.  To record, just click the enable button on your guitar track (the guitar track itself, not the send track) and you're off and running.

Once you get a take you like, listen to it and you'll find that everything was recorded dry as a bone.  Hit 'ALT M' to bring up the mixer and drag the fx from your guitar monitor bus channel onto the guitar channel itself.  Right-click 'activate all' and give it a listen.  Sa-wheat or what?  ; )  If you've recorded Hydrogen as well on another track, be sure an mute Hydrogen itself at this point so you're just hearing the recorded track without hearing Hydrogen (or just hit mute on the drum monitor bus).

Hope this helps and makes sense to anyone who might be searching or googling on this.  

Ardour is a PHENOMENAL program.  Stick with it, make a donation if you can and GET THOSE METERS BOUNCING!

; )

-skent

---

