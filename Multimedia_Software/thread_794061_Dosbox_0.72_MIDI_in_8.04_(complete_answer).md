---
title: "Dosbox 0.72 MIDI in 8.04 (complete answer)"
date: 2008-05-14
forum: Multimedia Software
---

### Post by Malor on 2008-05-14
I saw an archived thread that had a mildly painful approach to getting MIDI going in DOSBox.  It worked, but it can be much easier.  This is a repeat of what I added to that thread.

To get Dosbox 0.72 MIDI working with Ubuntu 8.04:

[LIST=1]
[*]Go into Synaptic Package Manager and install these packages:
[LIST=A]
[*]dosbox
[*]timidity
[*]fluid-soundfont-gm
[*]fluid-soundfont-gs
[/LIST]
[*]Open a command prompt, and type **sudo gedit /etc/timidity/timidity.cfg**
[list=A]
[*] The last line in the file says "source /etc/timidity/freepats.cfg".  Put a # mark at the beginning of that line to comment it out.  We're going to use a soundfont instead. (which we installed in the prior step.)
[*]On the next line, type: **soundfont /usr/share/sounds/sf2/FluidR3_GM.sf2**
[*]Save and exit
[/list]
[*]Restart timidity with **sudo /etc/init.d/timidity restart**
[*]If you don't already have a dosbox.conf you want to use, type **dosbox** and hit enter.  Dosbox will pop up.  At its command prompt, type: **config -writeconf dosbox.conf**.  This will generate one for you.  Then type **exit** to quit dosbox.
[*]Type **gedit dosbox.conf**.
[*]Click the Find button, type **mpu401=** and click Find.  You should see a line highlighted.  Close the search popup.  
[*]The three lines starting with mpu401= should look like this:
```
mpu401=intelligent
device=alsa
config=128:0
```
[*]Save and exit[/list]

Ok, MIDI sound should now work in DOSBox.  You will most likely want to edit the dosbox.conf file further, to mount your dos game directory as your C drive, but the part I'm addressing here is now fixed.

It's possible that the correct kernel modules *might* not get loaded the very first time you run timidity.  You *might* need to reboot.  (you can also manually load them, but it's easier to just reboot.)  They'll definitely be loaded correctly after a restart, so this is one-time-only thing.

If you have a GS-capable game, you have also installed a GS patchset as well. (GS is an advanced version of General MIDI.)  If you have any games that will support it, you can modify the timidity.cfg to load **FluidR3_GS.sf2** instead of **FluidR3_GM.sf2**.

edit: also note that if you're an advanced timidity user, and need to give it other arguments, put them in the file /etc/default/timidity, in the quotes after TIM_ALSASEQPARAMS, and restart it as above.  The defaults seem fine for dosbox.

---

### Post by elfuego on 2010-12-17
Using the instructions above I've set up timidity and dosbox and started a game. Music played correctly until I pressed alt+enter to go into full screen mode. The sound (midi only!) got completely distorted afterwards, and stayed distorted even after restarting timidity and dosbox (full screen or windowed) and no amount of tinkering the config files of both programs helped. Timidity plays .mid files perfectly.

I've tried using different soundfonts, killing and restarting timidity, changing dosbox.conf to use more/less CPU or to use different sound cards with different settings.

CPU is Core2Duo 1.73Ghz and sound card - intel integrated. Any suggestions? Thanks!

---

### Post by Haur on 2011-05-17
So yeah really old tread bumped again. I tried these instructions and then tested two games, Daggerfall and Quest for Glory 1 ega and GM in daggerfall and MT-32 in QFG didn't work.

Anybody know if this is possible with the current versions of dosbox and ubuntu?

---

