---
title: "x-fi and ALSA"
date: 2009-06-30
forum: Multimedia Software
---

### Post by Magick93 on 2009-06-30
Hi all

I am trying to get my X-fi card to work with ALSA. I understand this is possible.

Currently I have sound from the card using OSS4 but there is no midi - and I very much need the midi.

I have tried following the instructions at [http://www.moobash.com/Blog/?p=611](http://www.moobash.com/Blog/?p=611)

But this did not solve my problem.

Can anyone else help?

Please note: I am not a linux expert.

---

### Post by cheesepenguins on 2009-07-01
> **Magick93 said:**
> Hi all

I am trying to get my X-fi card to work with ALSA. I understand this is possible.

Currently I have sound from the card using OSS4 but there is no midi - and I very much need the midi.

I have tried following the instructions at [http://www.moobash.com/Blog/?p=611](http://www.moobash.com/Blog/?p=611)

But this did not solve my problem.

Can anyone else help?

Please note: I am not a linux expert.
This is actually my site and guide, I updated it yesterday, try out the alsamixer section I added.

---

### Post by Magick93 on 2009-07-01
Hi

Thanks for your tutorial, and for updating it.

I tried running the alsamixer and this is what I get:
alsamixer: function snd_ctl_open failed for default: No such device or address


Any further ideas?

Cheers

---

### Post by cheesepenguins on 2009-07-01
> **Magick93 said:**
> Hi

Thanks for your tutorial, and for updating it.

I tried running the alsamixer and this is what I get:
alsamixer: function snd_ctl_open failed for default: No such device or address


Any further ideas?

Cheers

There is a app called "Multimedia System Selector", you have to enable it to appear on the main menu (right click, edit Menus), its under the Preferences pane.

Make sure ALSA is selected as default.

If it was already ALSA and no card is detected I would reinstall ALSA as though it was a fresh install of Ubuntu, then following my guide again.

I'm sorry I can't be much more use, I'm a bit of a nab when it comes to how Linux works.

---

### Post by Magick93 on 2009-07-01
Thanks cheesepenguins

I tried that, but still no joy.

I've trying to get my computer to play nicely with my X-fi card for about a month now. I can get sound using OSS but not midi.

I'm seriously considering just buying a copy of windows - I hate to admit defeat but this is just too frustrating.

---

### Post by cheesepenguins on 2009-07-02
> **Magick93 said:**
> Thanks cheesepenguins

I tried that, but still no joy.

I've trying to get my computer to play nicely with my X-fi card for about a month now. I can get sound using OSS but not midi.

I'm seriously considering just buying a copy of windows - I hate to admit defeat but this is just too frustrating.
Nobody ever wants to hear this, but try a fresh install of Ubuntu with the drivers? On a different partition to test?

---

