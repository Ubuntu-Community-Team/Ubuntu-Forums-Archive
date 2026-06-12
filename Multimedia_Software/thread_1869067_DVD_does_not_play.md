---
title: "DVD does not play"
date: 2011-10-25
forum: Multimedia Software
---

### Post by Paddy Landau on 2011-10-25
Using Natty 11.04 64-bit, fully updated.

Everything on my system seems to work well, including being able to mount and read CDs and DVDs. I can also play audio CDs.

However, I cannot play DVDs. MPlayer gives the message, "Location not found." VLC finds the DVD, and tries to play it; but the DVD screen flashes on and off in a fraction of a second, and that's all that happens.

I have checked that all the usual suspects are installed, including ubuntu-restricted-extras, ffmpeg, libdvdread4.

What else can I do to get the DVD to work?

---

### Post by kc1di on 2011-10-25
> **Paddy Landau said:**
> Using Natty 11.04 64-bit, fully updated.

Everything on my system seems to work well, including being able to mount and read CDs and DVDs. I can also play audio CDs.

However, I cannot play DVDs. MPlayer gives the mess age, "Location not found." VLC finds the DVD, and tries to play it; but the DVD screen flashes on and off in a fraction of a second, and that's all that happens.

I have checked that all the usual suspects are installed, including ubuntu-restricted-extras, ffmpeg, libdvdread4.

What else can I do to get the DVD to work?

Hi try issuing the following command in a terminal.
```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

should work. then try playing the DvD again :)

---

### Post by Paddy Landau on 2011-10-25
Thank you, kc1di, that worked.

Should this not be done on the default installation? Why doesn't the forum have a ton of queries about this issue?

---

### Post by thatguruguy on 2011-10-25
> **Paddy Landau said:**
> Should this not be done on the default installation?
No, because the libraries to read DVDs are proprietary. In fact, you are technically supposed to pay for them in the U.S., Japan, and certain other countries (although I'm not sure about Great Britain).
> **Paddy Landau said:**
> Why doesn't the forum have a ton of queries about this issue?
There have been. Moreover, if you search "dvd ubuntu" on google, the very first result that comes up is [this one]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs"), which walks you through step-by-step how to enable reading DVDs.

---

### Post by Paddy Landau on 2011-10-25
@thatguruguy: Thank you for all that extra information.

So, not only do you have to buy a DVD, but you also have to pay to watch it!

Hmm... I presume, then, that the cost of my regular DVD player includes the cost of the license fee. Likewise, the cost of Windows and Mac, presumably, includes the license fee.

---

### Post by wolfen69 on 2011-10-25
> **Paddy Landau said:**
> 
Hmm... I presume, then, that the cost of my regular DVD player includes the cost of the license fee. Likewise, the cost of Windows and Mac, presumably, includes the license fee.

Yes. And doing a fresh install of windows or mac, you would not have DVD playback ability without purchasing or acquiring the codecs. No different for linux.

---

### Post by satanselbow on 2011-10-25
> **wolfen69 said:**
> Yes. And doing a fresh install of windows or mac, you would not have DVD playback ability without purchasing or acquiring the codecs. No different for linux.

The vast majority of OEM Windows machines come with "trial" dvd player software so you do have - in effect - dvd playback out the box on a new machine. The software might expire - the codec frequently does not. MPEG2 codecs are also frequently found in online windows "codec packs"

An install from a retail windows DVD would not as wolfen states include dvd playback on a clean install ;)

---

### Post by Paddy Landau on 2011-10-26
This is fascinating. Why on earth don't we have open standards for things like DVDs? Oh well, such is life.

---

