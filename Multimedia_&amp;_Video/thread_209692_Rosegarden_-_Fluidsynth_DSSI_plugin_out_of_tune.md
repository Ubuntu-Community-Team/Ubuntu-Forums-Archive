---
title: "Rosegarden - Fluidsynth DSSI plugin out of tune"
date: 2006-07-05
forum: Multimedia &amp; Video
---

### Post by matiouz on 2006-07-05
Hi,
I'm using the DSSI plugin FluidSynth and the output is directed to jack.
All the instruments seem to have the same tune but they are out of tune
compared to a real instrument.
I suppose I should change some jack settings? Are there settings for the
fluidsynth plugin also ?

Another question:
Since my computer is not powerful enough, I have a lot of xruns even if I
use only 5-6 tracks. Since I don't need high quality sound, I'd like to
know
if there are ways to reduce the xruns :
change jack settings ?
use another soundfont ? (do you know some)

Thanks for your suggestions.

---

### Post by Sheik Yerbouti on 2006-07-07
Just a guess you don't happen to have a master midi keyboard with a modulation wheel do you? I do and if the mod wheel gets moved by my cat that can quickly make things seem out of tune.

On the jack question raise your frames/period setting to reduce xruns. And or compile the vanilla kernel with realtime preemption (see the wiki). If you follow the wiki instructions to the letter you should have no problems really. Or if compiling kernels is not your cup of tea try a multimedia distribution like Demudi, or Dyne:Bolic on another partition. Or you could just run Dyne:Bolic as a live CD.

---

### Post by kellogs on 2006-07-13
I Have not yet checked rosegarden 1.2.3(new version) and im using the stock one in dapper, I recommend you to use periods 4096 and 48000 hz in jack, and uncheck jack init in rosegarden. So it starts and connects to jack settings by default(first you'll have to init jack).

with those settings(a bit high, but excellent for stability) I get no disconnections or drops from jack, the only problem is rosegarden is a bit out of sync. but for example, hydrogen has got absolutely perfect sync, even with this high period/buffer, and I can connect about a dozen instances of synths(qsynth, zynadd) with no hangs or drops or whatever.

Have to check rosegarden 1.2.3 with DSSI they said it works lots better from old version(dapper one).

---

### Post by aldous on 2006-07-13
I had problems with Fluidsynth being out of tune.  In fact, it was just playing at a samplerate of 48000 and jack was set to use 44100.  Check your samplerates, and I bet you'll find the issue.

---

### Post by ceenvee703 on 2007-06-21
I realize this thread is a year old but I'm having this very problem. Installed Ubuntu Studio over the top of 7.04. If I try to use Qsynth, it plays, but it is way out of tune relative to my Yamaha P-70 digital piano. Both Qsynth and JACK are at 44100, and my P-70 does not have a mod wheel.

EDIT: There's nothing like posting to a forum to make you solve a problem the second after you post. I set sample rate to 48000 with both Qsynth and JACK and problem solved, all in tune.

---

