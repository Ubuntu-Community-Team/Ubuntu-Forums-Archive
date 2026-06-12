---
title: "Latest update has trashed my sound"
date: 2011-02-16
forum: Multimedia Software
---

### Post by Phosphoric on 2011-02-16
Update manager got me to install some updates, including Linux headers.  Now I have no sound.  It cannot find my on board sound chipset and it's even taken away Alsamixer (no such file or directory) where I went to see if anything had become muted.

Where do I start?

I'm running 10.04 64 bit and I can't even find out how to get the grub loading screen.  When I used to dual boot with Windows I could choose the previous Linux headers, now I can't even do that.

---

### Post by fabricator4 on 2011-02-16
To get the grub screen to come up, hold shift while booting.  Do this as soon as the machine gets to post.

Chris

---

### Post by Phosphoric on 2011-02-16
Thanks Chris,

now got grub men.  Selected previous set of headers and my sound card is now recognised  and Alsamixer is back.

So what do I do about the latest update?

---

### Post by Phosphoric on 2011-02-16
OK, nearly back to normal.

Put this in terminal

sudo apt-get install linux-backports-modules-alsa-$(uname -r)

(sorry, don't know how to do the code thing)

I now have recognition of my on board sound and also an additional PCI sound card.

I don't yet have full functionality of my on board sound yet but I'll try re-loading the latest driver pack from Realtek for my ALC892 chipset.

---

### Post by Phosphoric on 2011-02-16
OK, after a lot of faffing about, re-booting and removing my additional sound card, I'm now back to where I was before the updates. :p

It's too bad that updates should cause these problems.:mad:

---

