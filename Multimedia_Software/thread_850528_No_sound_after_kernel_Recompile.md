---
title: "No sound after kernel Recompile"
date: 2008-07-05
forum: Multimedia Software
---

### Post by Chris Murphy on 2008-07-05
Not sure if this is precisely the right section for this question, feel free to move mods.

Recently I've been playing around with recompiling the kernel to learn more about linux.  Everything works great, except my soundcard!  I've tried kernel 2.6.25.9, 2.6.25.10 and 2.6.24, even if i copy the .config from my current working kernel (2.6.24-19_generic), and change nothing then compile I end up with no sound.  If i then reboot an select my old generic kernel every works.  This is driving me crazy!

Volume control shows a muted symbol and displays:
"The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

I have GStreamer plugins installed, and have attempted reinstalling them but this has made no difference.

Under sound prefrences if i try to play a test sound it displays:
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback."

I have an Asus P5K board with an onboard surround sound card running an up to date install of Hardy.

Any help is appreciated.

---

### Post by tesna on 2008-07-05
I was also experiencing this when I tried to compile for the first time the 26.25.9 kernel few days ago. It turns up I forgot to enable sound modules for my chipset (Intel HD Audio) in the kernel config. I was thought I didn't need to do anything to the .config file after I copied it. Then I tried to run make menuconfig then load your .config file from there. Then make sure that my soundcard modules are checked. After recompiling, my sound is back in the new kernel. Maybe you can try this too.

---

### Post by Chris Murphy on 2008-07-05
Thanks!

That solved my problem!

Cheers,

---

### Post by the8thstar on 2008-07-06
> **tesna said:**
> I was also experiencing this when I tried to compile for the first time the 26.25.9 kernel few days ago. It turns up I forgot to enable sound modules for my chipset (Intel HD Audio) in the kernel config. I was thought I didn't need to do anything to the .config file after I copied it. Then I tried to run make menuconfig then load your .config file from there. Then make sure that my soundcard modules are checked. After recompiling, my sound is back in the new kernel. Maybe you can try this too.

How do you modify the kernel config?

---

### Post by Zelaznog on 2008-07-06
I have this same problem, but could you be a little more specific? I'm new on this Ubuntu thing and did not get a word of what you've just said.

---

