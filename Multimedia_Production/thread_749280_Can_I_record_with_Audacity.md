---
title: "Can I record with Audacity?"
date: 2008-04-08
forum: Multimedia Production
---

### Post by BetterSense on 2008-04-08
I've plugged a line in into the blue jack on my motherboard, which TFM says is the line-in. However Audacity doesn't record anything. I've fiddled with all the capture options in Preferences (OSS, ALSA) and also in the Sound menu in Ubuntu. The LINE slider in alsamixer is maxed and so is the MIC. Input volume in Audacity is set to max. I know I have sound coming in because I've plugged the line into a headphone amp.

Is there some sort of trick to it?

---

### Post by Stochastic on 2008-04-08
I'd say attempt to record with a different program (maybe Rezound) so you can determine if it's an Audacity issue or if it's an ALSA sound capture issue -- though if the test in Ubuntu's sound settings worked, chances are it's Audacity.


Open Edit >> Preferences and double check the Audio I/O settings (set them to ALSA default).

---

### Post by BetterSense on 2008-04-08
What I ended up  doing, is double-clicking on the speaker icon, going to edit->preferences, checking the 'capture' box, and sliding the slider up.

 Which really bothers me because it's like a 'hidden slider' that isn't in alsamixer. I checked in alsamixer to make sure the line slider was up.  I don't like things hidden in the GUI.

---

### Post by Stochastic on 2008-04-08
Yeah Audacity is on my list of applications with weird interfaces and strange behaviors.  There are many other wave editors available, but audacity is one of the only ones that works on linux, mac, and windows so it's a popular choice for magazines to default to for "how to podcast" articles.

---

