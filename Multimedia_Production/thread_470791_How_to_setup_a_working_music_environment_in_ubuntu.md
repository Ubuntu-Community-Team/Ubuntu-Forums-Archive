---
title: "How to setup a working music environment in ubuntu studio?"
date: 2007-06-11
forum: Multimedia Production
---

### Post by canitb on 2007-06-11
Hi, I have searched a few days now, and I'm trying to figure out an easy way to learn ubuntu setup.

I an a cubase and Logic user and are very familiar with these boxed solutions, so working with different programs sounds great, but I don't get really how to replace the funksjons in cubase that I know.

I get that JACK plays a important part in this, to connect the programs together.

What I am looking for is a Audio program where i can record my audio, I want a sampler that I can connect with a midi program so I can play my own samples and AKAI samples, and I want some plugins that you can connect and play via midi aswell, doesn't have to be vst(I know vst is some issues with copywright).

[B]So that's the abillity to manage Audio, Midi, Sampler, Synths, and Effects ontop of this.
I want to be able to mix this so that I can have some audio recordings, and some instruments using sampler, and some using synth, like you would do in a normal cubase production.[/B]

So my question is how to setup this, and what is the best programs for this?


I will try write down what I know so far:

-----------------------------------------------------------------------------------------

Connecting everything together:
JACK, with it's graphical wraparound.

Audio mixing and recording:
Ardour2

Midi:
Rosegarden?? Is there a better midi program?

Synths:
can be implemented in rosegarden it looks, but how?

Sampler:
Qsampler? I'm not sure how to setup a good sampler with linux.
Qsampler was not included in ubuntu studio.

[B]And how to work with all is tha biggest question that I'm struggling with,
that you have a master player that starts all orher programs and uses it so it works like a complete system.[/B]
-----------------------------------------------------------------------------------------

This question is the only thing keeping me on windows still, I wanto change but it's to complicated to just start the switch, I'm missing some overall guide how to manage simple cubase tasks.

Would really appreaciate some feedback on this, or if somone knows any good guides..

---

### Post by canitb on 2007-06-13
too much info.. ;)

---

### Post by kayosiii on 2007-06-14
Yup the first thing you need to get up and running is jack and you almost certainly want to get it up and running with realtime privilages. I think but am not sure if ubuntu-studio does this out of the box.

The main app used to control jack is qjackctl. The other app I reccomend installing is patchage. which lets you manage jack in a very nice way.

Sing out if you are having any difficulty so far.

For multitrack recording you probably want Ardour2 (you won't be able to use this until you get jack running.

The most comprehensive tool for midi is Rosegarden the only serious deficiency it has is lack of automation. To get the most out of rosegarden you will need to have jack running.

The current alpha version on Muse supports automation but it is very alpha. For Drum patterns Hydrogen does an excellent job.

There are a couple of ways of getting Output from Rosegarden. The first  is to start up an external softsynth. (Zynaddsubfx works and sounds perty) then use patchage to connect the GM output of Rosegarden to the input of Zynaddsubfx... 

If you right click on the title of a track you should be able to select what type of track it is.
There are 16 channels of GM and 16 channels of MidiOutput System device (which I guess is supposed to be used for hardware samplers) and 24 slots for synth plugins....

This last option is probably the one you are interested in. This will let you play any dssi based synth you have in your system. 

You might also want to have a look at wired.... It is in a really early state of development but as of yet is the only prog I know that can play akai sampler files. though there is a program called abrowse that can convert some types. Wired is very crashy and feature incomplete. but you might get some mileage.

Other synths 
  Zynaddsubfx (very perty)
  Amsynth
  fluidsynth (plays soundfont files)
  qsampler (plays gigasampler files)
  Om (build synth from network of components)

There are more but these are the ones I am familiar with.

So whats the deal with qsampler. Qsampler is a frontend for linux sampler and linux sampler has been removed from the Debian/Ubuntu repositiories because of issues with the License.
The good news is that you can find linux sampler binaries here [http://download.linuxsampler.org/packages/debian/](http://download.linuxsampler.org/packages/debian/)
but As i said it may not be of much help to you since currently it only does giga files are far as I can make out.

Working with it all.
Ok the basic workflow looks like this.
Start Jack (or better yet have qjackctl start jack for you when you log in - there is an option for this in the settings).
Start Patchage.
Start Rosegarden if you want midi, Start Ardour if you want audio beyond what Rosegarden provides. Start the external softsynths you want to use. Use patchage to make the connections. (Currently LASH is being developed to make all this simpler)... 
[http://lash.nongnu.org/](http://lash.nongnu.org/)
ie save complete sessions and open them back up later.

Playback syncronisation  between applications can be achieved through Jack - in rosegarden check under settings -> configure Rosegarden ->Sequencer -> Syncronisation.

[http://www.out-of-order.ca/tutorials/ardour/](http://www.out-of-order.ca/tutorials/ardour/)

Other than that try searching this forum for similar threads

---

### Post by coffeecat on 2007-06-16
As far as Rosegarden is concerned, you might find the  [Rosegarden Free Companion](http://rosegarden.sourceforge.net/tutorial/en/chapter-0.html) useful.

---

### Post by canitb on 2007-07-09
Thanx very much for reply.  Much info, so I will have to try it out b4 I maybe have more questions.

---

