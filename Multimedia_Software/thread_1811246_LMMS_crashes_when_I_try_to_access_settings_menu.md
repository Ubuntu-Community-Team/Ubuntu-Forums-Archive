---
title: "LMMS crashes when I try to access settings menu"
date: 2011-07-24
forum: Multimedia Software
---

### Post by JayPeeJay on 2011-07-24
So here is what happened:

I started getting x-runs (not many, but long show stopping ones) in LMMS where I wasn't getting any before.  I started playing around with Frames settings, but that didn't solve the problem.  I tried changing the settings in JACK, but that didn't solve the problem (I should also mention that even if I try I can't get an x-run when running rosegarden, hydrogen, JACK Rack, rakkarak all at the same time with two midi controllers hooked up).

So I read on these forums that LMMS might not work that great with JACK, so I switched to usingg ALSA as the audio client.  That didn't solve the x-runs, and just increased my latency, so I want to switch back to using JACK.  However, now I can't access the settings menu.  It crashes everytime I even click on it.

I get this output from terminal:

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Segmentation fault

Any ideas on how to get the settings menu to work?  I've tried reinstalling.  Any ideas on the x-runs once I am up and running on JACK again?

---

### Post by JayPeeJay on 2011-07-26
So I did a little research into what a segmentation fault actually is, and it makes sense that it might do that if I was playing around with my buffer settings, but I would like to change it back and can't.

DOES ANYONE KNOW THE NAME AND LOCATION OF THE CONFIG FILE FOR LMMS?  I THINK I NEED TO EDIT THIS ONE MANUALLY TO CHANGE BACK TO JACK.  PLEEEEAAASSEE?

---

### Post by undeuxtrois on 2011-07-26
Hello,

I am running lmms 0.4.10~ppa-1 from ppa:tobydox/lmms. Strangely, I've never had or heard of this problem before, but after some tests I've been able to reproduce it. In fact, if I delete my current config file and run lmms, it crashes just like you describe it.

After a quick look in the [lmms bugtracker]("https://sourceforge.net/tracker/?group_id=105168&atid=640434"), it seems like it's a problem that's been around for quite some time. Until a fix comes up, here's the content of my config file which is set up for Jack.

I hope it helps.

$HOME/.lmmsrc.xml
 
```

<?xml version="1.0"?>
<!DOCTYPE lmms-config-file>
<lmms version="0.4.10">
  <MidiAlsaRaw Device="default"/>
  <Midialsaseq device="default"/>
  <app nomsgaftersetup="0" displaydbv="0" nommpz="0" configured="1"/>
  <audioalsa channels="2" device="default"/>
  <audiojack channels="2" clientname="lmms"/>
  <audiooss channels="2" device="/dev/dsp"/>
  <audiopa channels="2" device="default"/>
  <audioportaudio backend="ALSA" device="HDA Intel: STAC92xx Digital (hw:0,1)"/>
  <audiosdl device=""/>
  <midioss device="/dev/midi"/>
  <mixer framesperaudiobuffer="256" hqaudio="0" audiodev="JACK (JACK Audio Connection Kit)" mididev="ALSA-Sequencer (Advanced Linux Sound Architecture)"/>
  <paths workingdir="/home/pboivin/Documents/lmms/" fldir="/home/pboivin/" stkdir="/usr/share/stk/rawwaves/" vstdir="/home/pboivin/" artwork="/usr/share/lmms/themes/default/" defaultsf2="" backgroundartwork="" laddir="/usr/lib//ladspa/"/>
  <tooltips disabled="0"/>
  <ui manualchannelpiano="0" disablechannelactivityindicators="0" oneinstrumenttrackwindow="0"/>
  <recentfiles/>
</lmms>

```

---

### Post by JayPeeJay on 2011-07-26
Yes, that does it!  Thanks!  Still getting some x-runs, but just glad to have JACK back!  I guess I am running three synths (minimum) with effects, and tons of samples on a Pentium 4, I might be asking too much.

---

### Post by undeuxtrois on 2011-07-28
You are welcome. So, after fixing your config file, are you able to access the settings menu ? Allowing a bigger buffer size might help reducing xruns.

P.

---

### Post by JayPeeJay on 2011-07-28
Yeah, I can access the settings menu now.  Even cranking up the buffer all of the way I still get them.  It's weird, it doesn't even seem like there  is any spike in cpu usage when it happens (judging from both LMMS cpu meter as well as running system monitor.  No backround processes running either).  The x-runs only happen like once every two minutes but are up to 386 ms long.

---

### Post by undeuxtrois on 2011-07-29
This sounds curious... Have you tried adjusting the buffer size in jack  (ie. in qjackctl) ?
Also, make sure you restart lmms after making such adjustments...

---

### Post by JayPeeJay on 2011-07-29
Yes and Yes.

---

### Post by JayPeeJay on 2011-09-19
Okay, I finally eliminated the x-runs in LMMS!!!  All I had to do was upgrade 4.12.  This thing is a beast!  Can't wait to finish my jams and share with everyone.

Would have upgraded sooner but I couldn't upgrade before because apprently upgrading meant installing libjack0 which can't be done without uninstalling all my other goodies (ardour, jack, rakarrak, etc..).  Out of desperation I decided to try upgrading from a different repository and it worked!  Yay!  Still have all my other software in working order too.

---

