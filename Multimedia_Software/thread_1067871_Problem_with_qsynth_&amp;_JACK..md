---
title: "Problem with qsynth &amp; JACK."
date: 2009-02-12
forum: Multimedia Software
---

### Post by jonobo on 2009-02-12
Hi @ all, 

i got a problem with qsynth & JACK.

I am running Ubuntu 7.04.

My JACK is self compiled and normally runs well with my Ardour DAW.

Now i want to record the Output of qsynth with Ardour (qsynth is a frontend for fluidsynth, which turns MIDI-Signals into cool sound through playing samples from .sf2-Soundfont-Files).

So i need qsynth to run with JACK. It runs fine with "ALSA" or "File" as a Driver, but if i chose qsynth -> Setup -> Audio -> Audio Driver: Jack i get this Error-Message:
```
01:26:04.566 Qsynth1: Creating synthesizer engine...
01:26:04.593 Qsynth1: Creating audio driver (jack)...
01:26:04.607 Qsynth1: Failed to create the audio driver (jack). Cannot continue without it.
fluidsynth: error: Jack server not running?
01:26:07.061 Qsynth1: Destroying synthesizer engine...
01:26:07.061 Qsynth1: Synthesizer engine terminated.
```

I have JACK running fine before i start qsynth - so what is going wrong here?
Is qsynth trying to start another JACK, if yes, how do i prevent that?
Isn't qsynth finding the running JACK, and if yes, why not?
Or is it a totally different problem?

What works:
Rosegarden -> Midi Output to qsynth running with ALSA-Driver.
Rosegarden -> Midi Output to amsynth through JACK/qjackctl -> Record that signal with Ardour through JACK/qjacktctl.

What i want:
Rosegarden -> Midi Output to qsynth running with JACK/qjackctl -> Record that signal with Ardour through JACK/qjackctl.

Long story, short Message: can anybody help?

:guitar:

---

### Post by jonobo on 2009-02-12
Status: me, myself and i sorted it out and solved the problem.

:KS

Short:
- Deinstalled my old Versions of fluidsynth/qsynth.
- Downloaded, compiled and installed newest Versions of fluidsynth/qsynth.

Reason:
- My new version of JACK was no longer compatible with the old client-programs.

Details:
I wrote down the details over here;
[http://ooommm.org/sudelwiki/index.php?title=Get_qsynth_and_fluidsynth_running_with_JACK_on_Ubuntu_Feisty_Fawn_7.04](http://ooommm.org/sudelwiki/index.php?title=Get_qsynth_and_fluidsynth_running_with_JACK_on_Ubuntu_Feisty_Fawn_7.04)

:guitar:

---

