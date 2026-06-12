---
title: "Visual Equalizer"
date: 2007-11-08
forum: Multimedia Production
---

### Post by LobbyDizzle on 2007-11-08
I just purchased a 50" Samsung DLP and got it running as a secondary monitor... I was wondering if there were any programs that had a visual equalizer or any other cool visual effects like that. The only catch is, I want to let my guests be able to change music using my laptop while the equalizer is open in the Samsung.

I'm guessing I need to find a music player that has visual effects that opens up in a new screen. I just have no idea where to look.

---

### Post by mcduck on 2007-11-09
You are talking about a visualization, not about equalizer? Try Audacious, and install all libvisual-packages from repositories as well. You'll get a couple of good visualization plugins for audacity, and they run on a separate window so you can move it to your other display and maximize it.

---

### Post by Stochastic on 2007-11-09
Yeah, you were confusing terms.  Equalization changes what frequency levels are in your music (bass, treble, mids etc...).  It sounds like you want Visualization which is cool looking graphics that correspond by algorithm to the music that's being played.  Audacious has these and Amarok also has that feature but you'll need to install libvisual.  In gutsy it's libvisual-0.4-0

---

### Post by LobbyDizzle on 2007-11-12
It says I already have the newest versions of the plugin. Where do I go under Adacious in order to open the Visualizations in a separate window? 

Also, I do not have the secondary plugged in right now, but when I tried to drag a window from one screen to another it did not let me. It just hit the side of the screen and stopped, but the mouse can go over on its own.(I know this is a question for another area but might as well try)

---

### Post by Stochastic on 2007-11-12
For audacious I found that you'll need to install audacious-plugins audacious-plugins-extra and audacious-plugins-ugly (you may also want audacious-crossfade) then with audacious open go to preferences (ctrl +p) and select plugins at the bottom, then at the top right choose the visualizations tab, and pick your flavour.

I personally found the Paranormal Visualizations to be best for me and they are very customizable within the preferences dialog if you start playing around.

---

### Post by LobbyDizzle on 2007-11-12
I am a noob, so where do I find these plugins and how are they installed? Could you please do a step by step? That would be great.

---

### Post by mcduck on 2007-11-13
Just like any other program. Open the Synaptic (in System/Administration/Synaptic Package Manager), click the Search-button, search for 'audacious', right-click on any packages you wish to install and select 'Mark for Installation'. When done, click the Apply-button and Synaptic will download and install them for you.

edit: This might be useful read for you: [How to install ANYTHING in Ubuntu!]("http://monkeyblog.org/ubuntu/installing/")

---

