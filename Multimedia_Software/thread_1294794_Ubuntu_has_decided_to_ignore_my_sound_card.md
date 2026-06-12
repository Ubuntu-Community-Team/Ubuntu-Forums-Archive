---
title: "Ubuntu has decided to ignore my sound card"
date: 2009-10-18
forum: Multimedia Software
---

### Post by kaiten7 on 2009-10-18
I've tried pretty much every possible guide and solution in here, since sound problems are pretty common, but as it seems, Ubuntu (9.10) doesn't even recognize my sound card is there. I've been trying to fix this thing for days and I feel like somehow I only made it worse

When I try to run amarok, it gives me the following error:

"The audio playback device HDA Intel (ALC268 analog) does not work. falling back to PulseAudio."
Also, I've made sure that nothing is muted (alsamixer, volume controls, everything), and since i'm on a laptop, no cables have been misplaced.

---

### Post by kaiten7 on 2009-10-19
I've just installed a fresh Ubuntu 9.10 copy on another partition, and no sound on that either. Any ideas?

---

### Post by MelDJ on 2009-10-19
what laptop is it?

---

### Post by kaiten7 on 2009-10-19
> **MelDJ said:**
> what laptop is it?

It's a Dell Vostro 1710. The sound card (don't know if I already stated) is a Realtek ALC 268 HD.

And to add another fun piece to the puzzle, I just installed a fresh copy of Vista, run around looking for every possible driver in every possible version, and nothing.

The OSs don't even detect the card at all. Not in the device manager, not even a shadow. I could have removed the card from the plug and it would make no difference.

Which is what i terribly fear... can this please NOT be a hardware issue? I really don't feel like screwing about with this laptop, and i bet it would take weeks to replace the card from a store.

---

### Post by MelDJ on 2009-10-19
in terminal type: ***[I]gksudo* gedit /etc/modprobe.d/*alsa*-base.**[/I]*[I]**conf ***[/I] [COLOR=Black]then add this to the end of the file: option snd-hda-intel model=dell-m6
it worked on my dell studio 1555, so it MAY work on your laptop. hope it does
[/COLOR]

---

### Post by kaiten7 on 2009-10-21
I'll give that a shot, thanks. I don't have high hopes for it tho, since i've read the mother of all sound-related-FAQs on the forums, and it had a list of commands like those to add. I basically added every one who had a remote chance of being related with my laptop, still no success.

I'm not exacly sure of what I'm talking about here, but I think that doing what you said just enables the Alsa driver to recognize the card. Problem is, it's not even working on vista anymore, and i've installed vista before and didn't even NEED to go running about looking for sound drivers.

I'm screwed any way I look at it =(

---

