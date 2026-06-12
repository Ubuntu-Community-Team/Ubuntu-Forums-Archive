---
title: "Nvidia 180 series really looks promising! (gtkperf benchmark)"
date: 2008-11-21
forum: Multimedia Software
---

### Post by pelle.k on 2008-11-21
I just installed the newest BETA driver, 180.08. Nvidia claims big improvements in some areas wit this one.
It seems they've done a very good job with the 180 series, look at a gtkperf benchmark i just did (nvidia 177.80 from repos vs 180.08 BETA)

```

[COLOR="DarkOrange"]177.80[/COLOR] [COLOR="SeaGreen"]177.80+tweaks[/COLOR] [COLOR="Sienna"]180.08[/COLOR]

GtkComboBox		1.34 1.00 0.90
GtkComboBoxEntry	0.82 0.57 0.60
GtkSpinButton		0.26 0.18 0.19
GtkProgressBar		0.17 0.11 0.11
GtkToggleButton		0.40 0.30 0.22
GtkCheckButton		0.09 0.08 0.07
GtkRadioButton		0.34 0.29 0.27
GtkTextView - Add text		1.18 0.40 0.41
GtkTextView - Scroll		0.66 0.36 0.36
GtkDrawingArea - Lines		0.43 0.39 0.40
GtkDrawingArea - Circles	0.57 0.57 0.61
GtkDrawingArea - Text		4.96 0.70 0.65
GtkDrawingArea - Pixbufs	0.38 0.08 0.06
 --- 
Total time:			[COLOR="DarkOrange"]11.60[/COLOR] [COLOR="SeaGreen"]5.04[/COLOR] [COLOR="Sienna"]4.84[/COLOR]
```

**EDIT: Because of human error (erhm, mobile GPUs scale up and down on their own), i've redone this benchmark with a static GPU speed, AND i've also included the performance tweaks psyke pointed out in post #2, which actually brings 177.80 VERY close to that of the new 180.08 driver. At least in gtkperf ;)**

Also, the "stuttering" effects you get in compiz on mobile video cards (such as my 8600M GS) are now (almost) completely gone!

---

### Post by psyke83 on 2008-11-21
Stuttering on an 8600M GS, are you kidding? ;) It's more likely because you've got DynamicTwinView enabled, which is accidentally throttling compiz. See: [http://ubuntuforums.org/showpost.php?p=6197465&postcount=23](http://ubuntuforums.org/showpost.php?p=6197465&postcount=23)

As for the performance benchmarks - did you try the benchmarks with a properly configured 177.80 driver? Look here: [http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

(As you can see from the note, these settings are now set by default in the latest driver).

---

### Post by pelle.k on 2008-11-21
> Stuttering on an 8600M GS, are you kidding?  It's more likely because you've got DynamicTwinView enabled, which is accidentally throttling compiz.
No, single lcd screen (unless DynamicTwinView is activated by default somehow). "normal" desktop effects. This is not an isolated incident however. I've owned more than one laptop with a mobile nvidia GPU.
Also, this issue is known, and there exists workarounds (hacks) such as setting the driver to somthing else than performance mode 0.
If you've never experienced it, good for you :)

EDIT: I see that DynamicTwinView is activated by default. However, 50hz are more than good enough, since at full throttle compiz performs admirably. Also, this is not stutter like "50hz", it's more random (all through the animation). Sometimes a compiz minimize effect is fluent, other times 10 frames are fluent, then there's like one or two frames, for the rest of the animation.
Either way, this thread is not a support thread (at least i'm not asking for advice), but more of a general appreciation for nvidia latest driver.

> As for the performance benchmarks - did you try the benchmarks with a properly configured 177.80 driver?
You mean turning of glyphcache, SHMPixmaps off, and all of that? Yes, it's certainly better (but not as good as the 180 series), and while i can certainly do that, this is better yet.
And no, i didn't do the benchmark with a modified driver, since i'm just pointing out the difference on a vanilla install.

Either way, this is not a cry for help in any way. I'm just very glad nvidia is improving :)

---

### Post by psyke83 on 2008-11-21
> **pelle.k said:**
> No, single lcd screen (unless DynamicTwinView is activated by default somehow). "normal" desktop effects. This is not an isolated incident however. I've owned more than one laptop with a mobile nvidia GPU.

It IS activated by default, even on single-screen setups - that's the problem. If your screen has a refresh rate of 60Hz, the driver will mis-report it as 50Hz, and compiz will throttle to 50fps. That will give the impression of stuttering. Read the post I linked to earlier - it's well worth disabling this option.

---

### Post by pelle.k on 2008-11-21
Hey psyke. Bad timing i guess, but i reflect on that in my latest edit! :)
Anyway, i still appreciate you advice (and i did not now that)!

---

### Post by psyke83 on 2008-11-21
> **pelle.k said:**
> 
EDIT: I see that DynamicTwinView is activated by default. However, 50hz are more than good enough, since at full throttle compiz performs admirably. Also, this is not stutter like "50hz", it's more random (all through the animation). Sometimes a compiz minimize effect is fluent, other times 10 frames are fluent, then there's like one or two frames, for the rest of the animation.
Either way, this thread is not a support thread (at least i'm not asking for advice), but more of a general appreciation for nvidia latest driver.

Well, I recommend you disable the option. Running compiz at 50fps on a 60Hz screen will result in constant stutter - it needs to match the screen. You'll also see stuttering for video playback until you disable the option.

---

### Post by psyke83 on 2008-11-21
> **pelle.k said:**
> Hey psyke. Bad timing i guess, but i reflect on that in my latest edit! :)
Anyway, i still appreciate you advice (and i did not now that)!

Oops ;).

---

### Post by pelle.k on 2008-11-21
update :) (first post)

---

