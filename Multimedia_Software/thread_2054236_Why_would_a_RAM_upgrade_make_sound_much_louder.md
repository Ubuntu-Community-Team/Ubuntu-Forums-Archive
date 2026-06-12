---
title: "Why would a RAM upgrade make sound much louder?"
date: 2012-09-06
forum: Multimedia Software
---

### Post by vexorian on 2012-09-06
This is a mystery. 

Ever since 12.04 I noticed that the volume control got a little too loud in some area and too soft in another. I got used to it, making sure not to use the keyboard control and instead used only the mouse control. For my usual music needs, I learned to leave the volume at around 75% of its bar space.

Today I decided I needed a RAM upgrade. Bought chip, installed, tested it with memtest. All seems fine. But now , pulseaudio is much, much louder o_O. I have to move the bar to around 40% if I don't want it to explode my ears.

I am baffled, does anyone have a rational explanation for this?

---

### Post by sonicb00m on 2012-09-07
A rational explanation would be that you maybe updated with apt and something was changed. Or another application you used has changed PA settings.

It's not your RAM upgrade. That will just be coincidence.

---

### Post by Epodx64 on 2012-09-07
> **sonicb00m said:**
> A rational explanation would be that you maybe updated with apt and something was changed. Or another application you used has changed PA settings.

It's not your RAM upgrade. That will just be coincidence.

Yeah, the Ram definitely has nothing to do with it. You should try loading up PulseAudio and adjust from within it you probably have some settings high and some low or load whatever that gets you to the mixer I use Kubuntu so I have Kmix

---

### Post by vexorian on 2012-09-07
> **sonicb00m said:**
> A rational explanation would be that you maybe updated with apt and something was changed. Or another application you used has changed PA settings.

It's not your RAM upgrade. That will just be coincidence.
Before installing I had a web browsing sesion that began by rebooting (Had to look into Bios settings for a second so I restarted the computer). Then browsed the web and turned the PC off before upgrading.

What apps are known for changing pulse audio configuration?

---

### Post by jaithehulk on 2012-09-08
A RAM upgrade would never make sound much louder...

---

### Post by vexorian on 2012-09-08
I am not arguing that it makes sense it did. But pulse audio is ridiculous enough and the RAM upgrade was the only significant change between both states. It could easily be a lame pulse audio bug that makes it behave differently with different RAM amounts.

---

### Post by Yellow Pasque on 2012-09-08
The only way to know for sure is to pull the RAM out and test the volume..

---

### Post by afulldeck on 2012-09-08
> **Temüjin said:**
> The only way to know for sure is to pull the RAM out and test the volume..

Yes. That is the quickest and easiest way to check.

---

### Post by jaithehulk on 2012-09-08
> **Temüjin said:**
> The only way to know for sure is to pull the RAM out and test the volume..

I do agree with this... this sure is the quickest way!!!!:P

---

