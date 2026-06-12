---
title: "lightweight media center?"
date: 2009-07-13
forum: Multimedia Software
---

### Post by jpeddicord on 2009-07-13
Here's the situation: I have an old PIII box in the corner with an old ATI Rage 128 card that I've been using as a makeshift media center. Runs surprisingly well with GNOME, and doesn't really choke on a YouTube or Hulu video. I've been wanting to turn it into more of a cheap media box. At first I installed Elisa and put it into its own Openbox session, but was having issues with playback, not to mention that Elisa was discontinued. Elisa's successor, Moodiva, for all intents does not run.

Is there any keyboard-friendly, fast, no-frills media center application/framework out there?

---

### Post by jpeddicord on 2009-07-15
Scratch that - Moovida is now working flawlessly. Didn't realize it at first, but the R128 card runs better in 24-bit color, which can be used by changing the Screen section of xorg.conf to the following:

```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 24
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "768x576" "640x480" "384x288"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "768x576" "640x480" "384x288"
	EndSubSection

EndSection

```

---

### Post by MonsterTrimble on 2009-10-05
How is Moovida so far? I'm looking at using a P4 with a Rage 128 for a similar set up.

---

### Post by jpeddicord on 2009-10-05
> **MonsterTrimble said:**
> How is Moovida so far? I'm looking at using a P4 with a Rage 128 for a similar set up.

Loving it so far. Moovida has some quirks, and it's missing a Last.fm plugin, but I like a lot about it. Very easy to navigate.

---

### Post by MonsterTrimble on 2010-01-19
Cool - I'm trying it out using the netbook remix, so wish me luck!

---

### Post by joep-vd on 2010-02-02
How did it work out?

---

### Post by MonsterTrimble on 2010-03-16
Not well. The system worked OK (used E17) owever the RAGE 128's S-video & my TV had issues connecting and Moovida had display size problems and was doggy. I abandoned the project because it was too much of a pain.

---

