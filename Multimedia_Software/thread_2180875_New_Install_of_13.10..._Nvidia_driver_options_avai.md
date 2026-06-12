---
title: "New Install of 13.10... Nvidia driver options available... then unavailable.  Arrrgg!"
date: 2013-10-15
forum: Multimedia Software
---

### Post by doug-ravennasprings on 2013-10-15
I am attempting to navigate the hell that is Nvidia driver installation on Ubuntu. I've been in live chat with Nvidia and got 'escalated'.  I'll get an email at some point. I reinstalled Ubuntu 13.10 and found in Ubuntu Software Center \  Edit \ Software Sources... the last tab is Additional Drivers.  Immediately after the new install I clicked this last tab and saw about 7-8 choices of all the various Nvidia driver versions that are available.  I was utterly amazed that this was available.  I noticed the Open Source driver was currently selected.  I chose the only proprietary driver that indicated that it was tested.  This seemed like the safest choice while getting the performance I need from my card.  I clicked on it and received a GUI crash report within a few seconds.    Now the Additional Drivers pane is completely blank with no choices.  Gone forever? Do I have to reinstall to see the list again?  That seems rather extreme.  Does anyone have any insights on this feature set?  Clearly Nvidia knows nothing about it.  Thanks in advance.

---

### Post by doug-ravennasprings on 2013-10-15
Note:  Searching for and installing an Nvidia driver directly from the Software Center created a machine that wouldn't boot (at least it gave no visual cues that it had booted correctly - assuming there's a difference)... thus necessitating the reinstall.  Absurdly bad outcome for an OS in 2013.

---

### Post by Yellow Pasque on 2013-10-15
What video card or laptop are we talking about here?:
```
lspci | grep VGA
```

---

### Post by doug-ravennasprings on 2013-10-16
This is the GTX 690 which is two 680's on a single card.

I've been in touch with Nvidia and created a post on these forums with the current instructions on getting their driver installed.
The problem is there are bugs in their setup and 32-bit applications are not supported and are rendered via software [the CPU] not the hardware GPU.  A nightmare scenario in that my $1000 card isn't being used for apps like Steam.

---

