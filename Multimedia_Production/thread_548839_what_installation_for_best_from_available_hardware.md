---
title: "what installation for best from available hardware?"
date: 2007-09-11
forum: Multimedia Production
---

### Post by directcharitycontribution on 2007-09-11
or, "[the goal here is to get a minimal working setup which you can use as a basis for further exploration]("http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/c4b39482154feb03ca256f8100150ad9?OpenDocument")" finding "[the missing part of the puzzle]("http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/c4b39482154feb03ca256f8100150ad9?OpenDocument")". common denominators! when, or if, i get nothing better to do, i will try to explore sub-applications.

_*the situation*_

broadband connected P4 box with soundcard with midi joystick port, stand alone midi music keyboard and midi leads.

have jack + control, jackrack, hydrogen, and ardour  installed.

_*the intention*_

to record to notation and soundfile playing from both external keyboard and other inputs and software synth.

_*the action*_
basically what software installation is needed to get best out of existing hardware inventory?

---

### Post by stmiller on 2007-09-12
Rosegarden is the king of midi right now. Install rosegarden. Rosegarden handles all of the soft synths and so forth.

Ardour is adding midi support right now, so when the next Ardour update comes out with midi, Ardour will be aweseome.

---

### Post by directcharitycontribution on 2007-09-12
thanks for your reply.

the rosegarden won't start tho. as it has integrated score editor i am keen on this.

what softsynth is most effective with the previous applications configuration.

---

### Post by kayosiii on 2007-09-13
Ok first thing you want is jack up and running....
so qjackctl also known as Jack Control... Look here or elsewhere for advice on setting up jack (it can be reasonably involved to get best performance).

I then reccomend getting patchage up and running (for audio and midi routing).

You want to get any dssi stuff installed and you may as well make sure you have any  ladspa plugins installed (from the repository. 

Next you want rosegarden possibly but there are other choices. I reccomend Zynaddsubfx and Amsyntth as external midi synths if you have any soundfonts you can use these with qsynth and gigasample files can be used with qsampler (though you will need to install linuxsampler from the linuxsampler site however). These can all be routed into rosegarden by connecting them to rosegardens gm midi port.

---

### Post by directcharitycontribution on 2007-09-14
have jack + control. have had hydrogen running.

will look @ patchage. not

really want score editing so roseg@rden really in focus

am going to write some log of this. text is my primary faculty.

---

### Post by directcharitycontribution on 2007-09-16
*will have a workthrough this following;*

[http://ubuntuforums.org/search.php?searchid=27515953]("http://http://ubuntuforums.org/search.php?searchid=27515953")

[http://www.google.co.uk/search?num=50&hl=en&safe=off&rlz=1B3GGGL_enGB239GB239&q=linux+computer-music+guide&btnG=Search&meta=]("http://www.google.co.uk/search?num=50&hl=en&safe=off&rlz=1B3GGGL_enGB239GB239&q=linux+computer-music+guide&btnG=Search&meta=")

[http://www.soundonsound.com/sos/Feb03/articles/linuxaudio.asp]("http://www.soundonsound.com/sos/Feb03/articles/linuxaudio.asp")

[http://ubuntuforums.org/archive/index.php/t-446181.html]("http://ubuntuforums.org/archive/index.php/t-446181.html")

[http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/c4b39482154feb03ca256f8100150ad9?OpenDocument]("http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/c4b39482154feb03ca256f8100150ad9?OpenDocument")

[http://sound.condorow.net/]("http://sound.condorow.net/")

[https://help.ubuntu.com/community/MidiHardwareSynthesisSetup]("https://help.ubuntu.com/community/MidiHardwareSynthesisSetup")

[http://en.wikipedia.org/wiki/List_of_Linux_audio_software]("http://en.wikipedia.org/wiki/List_of_Linux_audio_software")

[linuxaudio.org/members]("http://www.linuxaudio.org/members")

[http://www.n-ism.org/Projects/Microtonalism/manual.pdf]("http://www.n-ism.org/Projects/Microtonalism/manual.pdf")

[[IMG]http://rosegarden.sourceforge.net/tutorial/pixmaps/sound-diagram-master.jpg[/IMG]]("http://rosegarden.sourceforge.net/tutorial/en/chapter-2.html")[IMG]http://plugin.org.uk/meterbridge/jf.png[/IMG]
[[IMG]http://www-uxsup.csx.cam.ac.uk/pub/doc/suse/suse9.0/userguide-9.0/sound_gamix.png[/IMG]]("http://www-uxsup.csx.cam.ac.uk/pub/doc/suse/suse9.0/userguide-9.0/ch18.html")

*and try somethings with a spreadsheet. eg*. [alsa hardwares compatible]("http://bugtrack.alsa-project.org/main/index.php/Matrix:Main")

_*BLUNT*_:
[COLOR="Lime"]onboard sound + FluidSynth[/COLOR] (meaning the motherboard does the MIDI work),
or,
[COLOR="Lime"]MIDI enabled sound card + soundfonts[/COLOR]

*generic linear flow chart with parenthised proprietary example requirements or suggestions*
[COLOR="Magenta"]I/O[/COLOR] <> [COLOR="Magenta"]processes[/COLOR] <> [COLOR="Magenta"]I/O[/COLOR]

[IMG]http://jamin.sourceforge.net/en/using/qjackctl.jpg[/IMG]

*maturity or dimension*

_*[COLOR="Magenta"]COMPACTS:[/COLOR]*_ jack + control + jamIn, patchage, jackrack/fx, vkeybd, softsynth, rosegarden, hydrogen, ardour
*_[COLOR="Magenta"]SPEARATES[/COLOR]:_*

[[IMG]http://www.sonicvisualiser.org/images/sv2-thumb.png[/IMG]]("http://www.sonicvisualiser.org/")   

*specific forum application configuration guides eg.*

[linuxaudio.org/members]("http://www.linuxaudio.org/members"),  [ardour.org/node/1147]("http://ardour.org/node/1147"), [jamin.sourceforge.net/en/uibasics]("http://jamin.sourceforge.net/en/uibasics.html"), 
[http://jackaudio.org/applications]("http://jackaudio.org/applications"), 
[http://64studio.com/manual/audio/rosegarden]("http://64studio.com/manual/audio/rosegarden")

[[IMG]http://quicktoots.linuxaudio.org/toots/ardour/images/diagram-route_ds.png[/IMG]]("http://quicktoots.linuxaudio.org/")


$ sudo rosegarden ... can start rosegarden on own for 'study'. [http://ubuntuforums.org/showthread.php?t=554163]("http://ubuntuforums.org/showthread.php?t=554163")

desk: 
[quicktoots.linuxaudio.org/toots/ardour/Basic_editing_howto.html]("http://quicktoots.linuxaudio.org/toots/ardour/Basic_editing_howto.html")
[configure general midi keyboard]("http://ubuntuforums.org/showthread.php?t=541609")
[confiure vst plugins]("http://ubuntuforums.org/showthread.php?t=557466")
[hardwares compatible]("http://www.studio-to-go.com/index.php?option=com_content&task=view&id=27&Itemid=82")
[alsa hardwares compatible]("http://bugtrack.alsa-project.org/main/index.php/Matrix:Main")
[mcintire.virginia.edu/music]("http://www.virginia.edu/music/VCCM/vccm_research.html")

---

