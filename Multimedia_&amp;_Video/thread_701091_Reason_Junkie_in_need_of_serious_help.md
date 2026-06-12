---
title: "Reason Junkie in need of serious help"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by Afrikprophet on 2008-02-19
Ok so I thought I had this whole thing down when I installed wine and actually got it to run reason. However I have been having a nightmare deaing with all of the skips and pops that I am getting from it now. So Basically I have 2 issues

1. Has anyone figured out a way to make reason run smoothly in Wine?

2. is there a good tutorial for some one who is still a bit of a linux novice to string together apps to make something similar to Reason. I saw that phillipcamaniac did something like that [here]("http://ubuntuforums.org/showthread.php?t=203845&highlight=propellerheads&page=3") (about half way thru the thread) but he hasn't been on the forums for a while. I wouldnt even know where to start. I have alot of the programs but have no ieda how to put them together. 

any help will be appreciated. thanks!

PS. I'm a simple guy and I don't mind reading simple things even if the first step in a tutorial is "turn the machine on"

---

### Post by chipants on 2008-02-19
well, i'm not the best teacher, by a long shot. but, i can tell you where you should start a personal research project.

1) JACK - jack, in simple terms, is an application that lets audio applications to exchange audio data back and forth. ([http://jackaudio.org/](http://jackaudio.org/))

2) qjackctl - is a simple graphical front-end to jack. it includes a patchbay which lets you connect and disconnect virtual inputs and outputs of jack-aware audio applications. ([http://qjackctl.sourceforge.net/](http://qjackctl.sourceforge.net/))

3) jack-rack - is a very awesome effects-rack type of application. in a goofy way, it sort of resembles reason... but a fair bit uglier, and only for effects. using JACK, you can connect an audio source to jack-rack. the audio source could be any jack-aware audio application that spits out audio, or even an instrument or microphone plugged into your soundcard. the processed sound from jack-rack can then be routed to an application that records audio, such as ardour or audacity, or just straight to your soundcard's audio output. ([http://jack-rack.sourceforge.net/](http://jack-rack.sourceforge.net/))

it would be in your best interests to read as much as you can to understand JACK before going any further. it is probably the single most important piece of professional audio software for linux, at the moment. now, the apps mentioned above *do not* make any sound on their own. you will also need physical instruments to plug into your soundcard, or synth applications to make some noise. i personally like zynaddsubfx a lot. but, there are many, many, many synths for linux and jack.

it'll be pretty tough (eh, impossible) to find an all-in-one sort of application like reason on linux. but, if you can get into a modular mindset with respect to sound apps, you can be very happy indeed.

---

