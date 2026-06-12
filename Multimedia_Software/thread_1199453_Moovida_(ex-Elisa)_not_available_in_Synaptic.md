---
title: "Moovida (ex-Elisa) not available in Synaptic"
date: 2009-06-28
forum: Multimedia Software
---

### Post by b9k9kiwi on 2009-06-28
I'd dearly love to try Moovida along with a near redundant Hauppage card which I plan to move from my Win PC into my Ubuntu PC - I can't get Moovida to install, however.

I have slavishly followed the LaunchPad instructions to add the PPA resources to Administration/Software Sources and the latter confirms that the sources are recognised and available.  A search for Moovida in Synaptic returns no result (although a search for Elisa is successful). So, no joy.

Any advice would be appreciated.

---

### Post by kostkon on 2009-06-28
> **b9k9kiwi said:**
> I'd dearly love to try Moovida along with a near redundant Hauppage card which I plan to move from my Win PC into my Ubuntu PC - I can't get Moovida to install, however.

I have slavishly followed the LaunchPad instructions to add the PPA resources to Administration/Software Sources and the latter confirms that the sources are recognised and available.  A search for Moovida in Synaptic returns no result (although a search for Elisa is successful). So, no joy.

Any advice would be appreciated.
Try using the full search in Synaptic and not the quick-search option.

You can check if the package exists like this:
```
apt-cache policy moovida
```

---

### Post by sloggerkhan on 2009-06-28
have you looked for updates?
I have the moovida PPA installed and it works fine for me.
Usually if the PPA is installed properly and no package shows up, try clicking the reload button in synaptic.

---

### Post by b9k9kiwi on 2009-06-29
Thanks for the quick responses - a Synaptic reload seemed to do the trick.

I am using Moovida as I write and although not gobsmackingly impressive it will suit my purposes for now ( I expect development will continue).

b9k9kiwi

---

### Post by sloggerkhan on 2009-06-29
I just wish there were something like moovida that used mplayer instead of gstreamer.

---

