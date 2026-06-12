---
title: "Simple MIDI Setup"
date: 2010-04-16
forum: Multimedia Software
---

### Post by the_prof on 2010-04-16
Hi there, I was hoping somebody could help me out here, because I'm getting absolutely nowhere.  

I've been using Ubuntu for a while now, and I've only just got around to starting setting up my MIDI gear.  

All I want to do (for the moment) is get my MIDI keyboard (an M-Audio Keystation) hooked up so I can effectively play it through the internal sound card of my laptop.  

Ubuntu appears to recognise the keyboard itself, and I've managed to control Hydrogen using it, so I know it's working.  Now all I really want to do is patch the MIDI through to some kind of midi software synth, so I can play it like a piano.  

I tried Rosegarden, which I couldn't get any sound out of at all.  I tried Ardour, which just baffled me.  I've been through just about every source I can find on the Internet, but nobody seems to be able to explain in simple terms how to get a basic MIDI setup working properly.  

I'm not enough of an expert to know exactly what I need to do this, or what terms to put into a search engine to find what I need.  It's a pretty simple task on Windows, so I'm baffled as to why I can't get it to work with Linux.  

Any ideas much appreciated.  I'm running Karmic (not studio), and my soundcard is just the built-in Realtek model (which seems to work fine for most things). I'm running Jack too, which appears to work for most things.

---

### Post by cchhrriiss121212 on 2010-04-16
> I'm not enough of an expert to know exactly what I need to do this, or what terms to put into a search engine to find what I need. It's a pretty simple task on Windows, so I'm baffled as to why I can't get it to work with Linux.
You just need a synth program, and you don't need to be an expert to get one. Open source programs are harder to find as they are not advertised and sold as products, which is where the repositories come in handy. Try typing "synth" into synaptic.
Some synths I like:
Zynsubfx
Phasex - get this here [http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/p/phasex/](http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/p/phasex/)
AMS
Bristol

Once you have installed one, get jack running and open the synth, then connect the midi stream of the keystation to the synth in the alsa tab of the connections window in jack. You can also use a program called patchage to connect audio and midi, which I find easier to use than the jack connections window.

Rosegarden is not a synth, it is a midi sequencer, which you can use to record and edit. Ardour is a multitrack recording program like cubase and it is quite good if you ever want to record something.

---

### Post by the_prof on 2010-04-18
Ah, that's wonderful!  I managed to get ZynAddSubFX going very quickly and easily.  Thank you very much indeed.  

It seems my main source of confusion was that Ubuntu doesn't seem to come bundled with some sort of General Midi synth set as the likes of Windows does - which means that when you run a sequencer, you can usually just play around with the sounds.  

I had a go of setting up FluidSynth, but I was not so lucky.  I managed to get myself a GM/GS wavetable soundfont through the repository, but I couldn't seem to get ALSA or Jack to recognise it.  Do you have any tips?  

I tried qSynth, but didn't really get any further.  It seemed to be running OK, but I could find no way of getting my MIDI keyboard to control the sounds.  

Sorry about my naíve questions - I don't really know a great deal about the sound systems on Linux, or for that matter on any platform.  Hope you can help further.

---

### Post by markbuntu on 2010-04-19
Here is some links just for you

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

If you are having trouble setting up jack in UbuntuStudio:

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

Excellent ardour tutorial here:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

If you are wondering how to sync applications together through jack:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

good luck.

btw, the best place to get answers for these sort of questions is in the UbuntuStudio forum which is the one after this one.

---

### Post by cchhrriiss121212 on 2010-04-19
Qsynth is a gui for fluidsynth, and I have not tried them out yet as there are so many other synths I've been using. Is there any reason in particular you wanted to use them?

> btw, the best place to get answers for these sort of questions is in the UbuntuStudio forum which is the one after this one.
+1 for this

---

### Post by the_prof on 2010-04-19
Excellent stuff, thanks guys.  Thanks for the links markbuntu, I shall peruse them over the next day or two.  I'm still a little baffled by the sheer amount of stuff needed to get something I thought was quite basic going, but this all points to some general progress in the field - I hope it continues!

The reason I wanted Fluidsynth in particular is that it allows for support of a full GS wavetable Midi bank, as opposed to what appear to be mostly VST style synth modules.  Most importantly, it allows one to use Soundfonts, of which I have a good few I paid good money for over the years, so this capability would mean quite a bit to me.  

I'm trying to set up a small PC with my midi keyboard (eventually) for live performances, and I noted that with a relatively low-spec PC I could achieve some of the results I wanted with Ubuntu.  

I deliberately haven't gone down the Ubuntu Studio route because I fear it might be a bit heavy for my setup.  I could be completely wrong, however.  

I will eventually want to get into sequencing and recording, but my main concern is simply getting my keyboard to 'play' the right sounds through the soundcard.  

Thanks again for all your help and advice.

---

