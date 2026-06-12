---
title: "Window Focus on 0.23 Frontends"
date: 2010-06-30
forum: Mythbuntu
---

### Post by sox2001 on 2010-06-30
Hello there,

I've been pondering this problem for a while, I've had a search through forums and bug reports but the issues described there, although similar do have differences and no solutions posted there have worked for me.

I have a Master Backend with Frontend 0.23 running absolutely fine, no issues now. I did have a major issue with screen dimming because of an apparent Nvidia incompatibility with Sony HDTVs, but that's mysteriously cleared up now. Anyway I digress.

I've setup a frontend on my main PC in my bedroom on Linux Mint 9 (0.23fixes) and a frontend on an O2 Joggler (see shop.02.co.uk/joggler) (awesome £50 mini touchscreen frontend) running on Ubuntu Karmic 0.23fixes. Now both these new frontends when watching a recording (ie, watching LiveTV when the frontend on the Main Backed is watching TV,only one tuner you see) you have to alt+tab away from Myth and back again before you have window focus and can input keyboard commands. This doesn't happen when watching LiveTV on any frontend when other frontends are idle.

The forums posts I've seen so far seem to point to overall loss of focus in myth, where my problem only applies when watching the recording of a tuner in use and not when watching LiveTV.

To recap the problem in bullet points:

[LIST]
[*]Loses window focus when watching a recording, can't apply keyboard commands.
[*]Have to alt+tab away from myth and back again to get window focus back. Also switch desktops works the same.
[*]Doesn't happen on any frontend when watching LiveTV.
[*]Happens on 0.23fixes on Linux Mint 9 and 0.23fixes on Ubuntu Karmic.
[/LIST]

Thinking about it, the main frontend is running XFCE and both the others which have problems are running Gnome...could this be the issue? Will try tonight.

Any other thoughts, people with same problem please lets hear your ideas.

---

### Post by sox2001 on 2010-07-01
Update, after another attempt at fixing the issue last night it emerged:


[LIST]
[*]This only happens when another frontend is watching LiveTV
[*]Window focus on the Frontend watching LiveTV is fine
[*]Window focus on any other frontend while another is watching LiveTV loses window focus
[*]Watching old recordings is fine, its only when watching a recording which is ongoing.
[*]it is not an issue with gnome/xfce as far as i can tell, it happens on both.
[/LIST]

---

### Post by LowSky on 2010-07-01
Make sure desktop effects are off.

---

### Post by sox2001 on 2010-07-03
Yes desktop effects are off, no difference. They were on in Linux Mint 9 but not on on the Karmic installation, I turned them off on Mint, no affect.

---

### Post by nickrout on 2010-07-03
switch to xfce and see if it fixes things.

sudo aptitude install mythbntu-desktop

---

