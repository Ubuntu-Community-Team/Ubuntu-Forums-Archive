---
title: "Streaming Audio Server, Sound card required?"
date: 2009-08-27
forum: Multimedia Software
---

### Post by InkyDinky on 2009-08-27
I feel sheepish asking this but, if I want to setup a streaming audio server does that box need to have a sound card in it? 

Which leads me to another question. Basically what does the sound card do (that the CPU doesn't/can't)?

If I do need a sound card I have to ask, why? Isn't that PC just streaming data packets out the door? Does the sound card need to do some processing of those bits before sending out the packets? What is the difference between those packets and the raw source file (mp3, ogg, whatever have you)?

If I don't need a sound card then I have to ask the stupid question of (and I can't imagine streaming audio servers have a sound card in them so I assume this is the right answer), why can't I play music on my computer without a sound card? Is it really just the specialization and unburthening of the (audio) processing on the CPU? And I assume now that the design of a computer takes into account that there is a special piece of hardware available to do this and therefore when one isn't present things break? Or can emulation of the soundcard be done? It took me a while to figure out why I couldn't even watch a movie clip on my computer that doesn't have a sound card in it. Only VLC gracefully handled the absence of a sound card whereas mplayer and others choked.

Sorry for so many questions in one but I'm ready to be enlightened. So far Howstuffworks.com and similar sites really haven't given me the answer I was looking for.

---

### Post by ErwinJunge on 2009-10-02
First off: interesting question :)

After thinking about it for a bit, I can't see any reason to NEED a soundcard if you are only using the machine as a server for streaming media. Just like you said, you're only pumping datapackets out the door.

About the choking: that's down to the programs trying to play a file with (among other things such as video) audio in it. Those programs then try to put the audio somewhere, fail to do so and stop. If you had launched mplayer from the commandline you probably would have gotten an error (not going to remove my soundcard to try it for you though :D).

Now as to why you need a soundcard to play sounds and actually hear something: quality issues aside (which is what hardware soundcards are mostly used for nowadays, that and having an enormous amount of different input/output ports for editing purposes) you still need somewhere to plug in your speakers/headphones. Good luck trying to put the plug in your cpu ;)

---

