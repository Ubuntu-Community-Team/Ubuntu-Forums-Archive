---
title: "Rosegarden and timidity...weird problem"
date: 2009-02-09
forum: Multimedia Software
---

### Post by acoccimi on 2009-02-09
I'm running Ubuntu 8.10 on my EeePC (the Eeebuntu edition). I have timidity and Rosegarden installed. Before, timidity worked from the command line and Rosegarden worked in X (although it was slow). Now, neither works. Or should I say, ALMOST neither works. Apparently, timidity works from the command line *only* when Rosegarden is running (that's the weird part), but it is quite slow (what with Rosegarden running and all). I have eawpatches installed and properly set up. I tried completely removing timidity and reinstalling it, but still no go. How can I get my tiny laptop to play midi files again?

P.S. I am also a bit confused by what little support there is for ALSA. It's a pain to work around, because many applications use it. Apparently, my audio runs through PulseAudio...*no* clue what that is.

EDIT: There is a new symptom: using verbose mode, I found out that timidity running from a command line has one extra line when it doesn't work (when Rosegarden isn't running)

"Audio device buffer: 2 x 8192 bytes"

...which I also can't find any meaning.

EDIT 2: I experimented with the -O? option, and it works with -Oe. Now, how do I make it default?

EDIT 3: Now -Oe gives me gibberish in the command line. Rosegarden still has no sound. Timidity no longer works at all, Rosegarden running or not. Please help me!

---

