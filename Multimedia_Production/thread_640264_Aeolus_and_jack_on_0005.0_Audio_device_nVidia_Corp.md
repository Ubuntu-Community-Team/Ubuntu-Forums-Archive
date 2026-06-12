---
title: "Aeolus and jack on 00:05.0 Audio device: nVidia Corporation MCP61 High Definition Aud"
date: 2007-12-14
forum: Multimedia Production
---

### Post by Smbrandes on 2007-12-14
A minor victory in the road to making use QTJack. With the 00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2) and a Amd 64 Athlon 4699+ w/ 1gig of memory it took all manner of fussing with the options to remove those nasty little xruns. Xruns cause horrid popping due to losing data at the instant of xrun. These are the settings needed to produce a quasi stable Jack configuration. (ot convinced a totally stable configuration exists, still achieve xruns once every few minutes which is better than continuously with Realtime checked on, Hardware monitor checked on, monitor, checked on. Frames=128, sample rate 48,000, buffer=4. The last one is the oddball thing that took a while to work out. IN any event that allowed Aeolus to by played with the virtual midi keyboard. May try to work out how to use real keyboard over the weekend. Have yet to get any other combination of apps to work with jack. For some reason there is never any audio output, All apps that can generate output work without jack, have tried rosegarden, hydrogen, zynaddsub Jack is peculiar, Jack is not very friendly. Jack apparently needs a good whack to get it working but which hammer to apply? Or is it these other apps that are not very friendly with Jack? Maybe the Ubuntu studio types should sort out a better documentation to explain how to make these apps make output. Connecting them is the easy part you just play with the fun little connector box and away you go, but nowhere. 
 By the way Aeolus is a fun little synthesiser. Looks like it has some potential.

---

### Post by deadgobby on 2007-12-14
Well what can expect for some thing that is for free. I have pack away all my midi stuff and ready for a move. I have to try out that soft synth. 
Gobby

---

### Post by Smbrandes on 2007-12-14
Welll put about the free. Actually what works for free is a miracle. Now a partial solution. to further problems. Enabling sound output from Jack required turning all the sound volumes on. Seems straightforward except for the fact that there appears to be two different sound entities, for lack of a better word since the terminal command $ sudo asoundconf list yields only NVidia, but after installling gnome mixer it decided to govern something called Realtek ALC833 OSSmixer. This can also be obtained by check the default system mixer under the speaker icon on the main task bar by double clicking and then going to the File tab and switching devices. My guess is that some of the above software still is using OSS which I was under the impression was deprecated for ALSA. That is just a guess, if someone has a better explanation it would be interesting. So having digressed, once the volumes are up Jack will make sound under Rosegarden, and zynsubadd, and Qsynth. 
   Rosegarden needs to be adjusted in one way if it is coupled to Qsynth through Jack. There is a drop down menu that says general midi as a default. If you fiddle with it there are other synth settings you must find the appropriate setting which in this case is Soft Synth. Then on the Qsynth app you must make sure all the buffer numbers and sample rates match those of Jack. That is under the set up section called Audio. Then you must load a sound font under the Sound font section and then finally on the main gui you must use the channel button to engage a sound channeel. Now assuming you have all that connections under jack correct it will work. Make sure you check these connections again after you restart the qsynth engine. So that ought to be some progress.

---

