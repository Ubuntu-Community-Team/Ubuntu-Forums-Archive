---
title: "No sound"
date: 2012-05-29
forum: Multimedia Software
---

### Post by yeh on 2012-05-29
Hello,

The sound for my computer stopped working.

I'm using Ubuntu 12.04 Dell Inspiron 1525, and the sound was working this morning. However, it stopped this afternoon. There is absolutely no sound. Headphones don't work either. "Sound Settings" comes up and detects HDMI/DisplayPort 2, Analog Output, and Headphones. The "Test Sound" under sound settings does not work either.

Thank you for any help

---

### Post by yeh on 2012-05-29
I didn't see the sticky regarding sound problems before posting this, but it doesn't seem to work for me. I get output for everything (sound card activated, all drivers detected), and everything seems to work except for the actual sound.

I included that headphones don't work to show it's probably not a hardware problem: my headphones work elsewhere.

---

### Post by yeh on 2012-05-29
I found out that alsamixer's PCM was turned off. Sorry for the bother. What I don't understand is how it turned that way. Master, headphone, and headphone were all untouched, and I didn't know alsamixer existed until I tried troubleshooting sound.

Edit: I reinstalled the drivers, kernels, and lots of other stuff before finding alsamixer's PCM. No wonder I had success in every diagnosis test. I wasn't very smart...but maybe this will help someone?

---

