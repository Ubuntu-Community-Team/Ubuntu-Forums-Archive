---
title: "[SOLVED] mplayer command to start video over"
date: 2007-11-07
forum: Mythbuntu
---

### Post by dan5000 on 2007-11-07
Hi,

I am using the mplayer resumer script which works great. I am able to resume a movie from where it was previously exited. I would like to program my remote to allow me to restart the movie from the beginning.

I had this working on a previous myth box but I have forgotten how to do it. I know how to map the keys in my lirc config file but I am stuck as to the mplayer command that enables me to restart a file at the beginning. I thought it was ctrl-B or something similar but that is not working. I have looked at the slave.txt file and there is nothing there for what I want.

Any thoughts/suggestions?

Thanks. :confused:

---

### Post by dan5000 on 2007-11-07
Solved!

I had forgotten that the mplayer resume script is no longer needed and that the internal player sets a bookmark. Basically, use the internal player and not mplayer.

The command is ctrl-B as I thought but it is run against the internal player and not mplayer.

Cheers!

---

