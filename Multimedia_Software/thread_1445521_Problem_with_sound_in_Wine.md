---
title: "Problem with sound in Wine"
date: 2010-04-02
forum: Multimedia Software
---

### Post by ReiKo90 on 2010-04-02
Hello,

Well, my friend is having major sound problems when she is trying to  play Counter Strike 1.6 on her Ubuntu (latest version). She can only  play it trough Wine emulator and Wine itself is updated to latest  version.

From what she told me and I seen - most of the times she doesn't have  sound at all. 


Can you maybe point me on what should we do about it? I Googled some  "solutions" like disabling OSS and etc. but it doesn't make any  difference (killall pulseaudio for example removes all of her sound like  YouTube sound and etc.).

Thank you.

---

### Post by ron999 on 2010-04-02
Hi
When I had sound problems with Wine I changed the Wine audio driver from OSS to Esound.
To do this type **winecfg** into the terminal.
When Wine's configuration window opens select 'Audio'.
Then uncheck the OSS Driver box and check the Esound Driver box instead.
Then 'Apply'.

---

### Post by ReiKo90 on 2010-04-02
Hello Ron,

hmm will try to do that. Did you have "no-sound" problem or something more specific?

Thanks.

---

### Post by ron999 on 2010-04-02
Hi
I was running Spotify in Wine. The music kept coughing and spluttering, it couldn't keep up.
Now since I changed that driver to Esound it's perfect. Spotify rocks.

---

### Post by ReiKo90 on 2010-04-05
> **ron999 said:**
> Hi
I was running Spotify in Wine. The music kept coughing and spluttering, it couldn't keep up.
Now since I changed that driver to Esound it's perfect. Spotify rocks.

We tried the following:

Uncheck ALSA and OSS and turn on ESound - not working
Uncheck ALSA and ESound and turn on OSS - not working
Uncheck Esound and OSS and turn on ALSA - not working


She also told me that SOMETIMES but really rarely has sound for a about minute or so but it is also shuttering and what not.


When she try to use "Test sound" she gets: "Audio test failed!"

Any tips?

Thanks.

---

### Post by maggu on 2010-04-05
In hardware acceleration drop down, select "Emulation".

---

### Post by ReiKo90 on 2010-04-05
> **maggu said:**
> In hardware acceleration drop down, select "Emulation".

Will try. Thanks.

---

