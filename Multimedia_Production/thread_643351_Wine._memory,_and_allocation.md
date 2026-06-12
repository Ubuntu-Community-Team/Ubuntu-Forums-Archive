---
title: "Wine. memory, and allocation"
date: 2007-12-17
forum: Multimedia Production
---

### Post by Alexstone on 2007-12-17
Hello, my first post, and it concerns memory usage by Wine.

I am using a dual core AMD 5600+ X2 with 4gb of ram for writing music. (I´m a fulltime composer of classical and film music.)

I have ubuntustudio installed, and have been very impressed with what i´ve been able to achieve so far, running Linuxsampler (Qsampler gui) with Jack with latency between 5-6ms, which is more than enough for speed of input and accuracy of playback performance.

I write midi charts and go to audio performance in Reaper, running in Wine, with wineasio. So far so good, and Reaper behaves rather well. 

And, as i´ve tweaked settings for the RT kernel, my Memlock setting is 2048MB, as i run big orchestral sample templates and need the memory address. This works well too, and apart from the limitation of midi ports into, and out of wine, for Reaper, things are going ok.

So now the challenge.

I also use Orchestral VST´s. Most of these work ok in Wine, but are short on memory. Where a big 1st Violins template would chew about 700-800MB of presample ram in Win, I´m getting less than half of that in Reaper, in Wine, before a low memory message from the VST itself.

My question is, how can i tweak Wine memory space to a level i require, and how do i increase the number of addressable midi ports in Alsa, so Wine can see them, in Wineconfig/Audio?

I am new to Linux, and have been researching fairly heavily to get up to speed with using the distro, and programmes within it, so if any answers and suggestions could reflect that, i would appreciate it.

Finally, kudos to the developers of Ustudio. For me at least, it runs a lot better, and faster than Win, and doesn´t glitch or twitch when I´m recording.
Additionally, i have to commend the developers of Wine, Jack, and Qsampler. I had a brief shot at Linux about three years ago, and things weren´t quite ready then, but i think we´re pretty close now.
Muse, Musescore, Ardour, and quite a few of the other programmes are maturing nicely.

Any help with this would be appreciated.

Alex.

---

