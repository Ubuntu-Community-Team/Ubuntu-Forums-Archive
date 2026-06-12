---
title: "Sound constantly cracks when playing music"
date: 2011-11-24
forum: Multimedia Software
---

### Post by Kitkin15 on 2011-11-24
So i have a HP Pavilion DV6, it has 8 Gig RAM (Came with 4), it has "Quad Core and AMD RADEON GRAPHICS" and "A6 VISION AMD", and i have it installed on my 500GB EXT HDD like i always have.

Well sense day one ive had a problem with music playback, if i play music the sound will have alot of static, and it gets worse depending on how many things i have running. I had Ubuntu on my EXT HDD with my HP Pavilion G6, and i never had this problem, and its never happened on any other laptop either. I recently re-installed Ubuntu and the problem still exists. 

Ive found out that HP laptops are starting to take a crap HP is losing their quality and i regret buying this piece of garbage from them, but im stuck with it so i want to make the best out of it, is there any way that i can fix this problem? 

Thanks

  -Kitkin15

---

### Post by boast on 2011-11-24
so is it only music that cracks, or any audio playback?

---

### Post by Kitkin15 on 2011-11-24
All Media, but it happens mainly when playing music.

Ive used all Media players for music and i have the same problem, i even messed with my sound settings and noticed little to no difference.

---

### Post by boast on 2011-11-26
I assume that going into terminal and doing "alsamixer -c 0" (or selecting another card #) and reducing the PCM level a bit doesn't remove the cracks?

---

### Post by Kitkin15 on 2011-11-30
> **boast said:**
> I assume that going into terminal and doing "alsamixer -c 0" (or selecting another card #) and reducing the PCM level a bit doesn't remove the cracks?
I didnt see anything about PCM level.... What is that exactly?

---

### Post by Kitkin15 on 2011-12-01
Ok so i found out what PCM is, and i ran a Nintendo 64 emulator, started a game, then put on music, and it was cracking. Then i lowered the PCM and the cracking continued. It only cracks when my computer is running multiple things (Which includes multiple tabs in Firefox and other very small things)

Lowering PCM didnt help :(

---

### Post by boast on 2011-12-01
I couldn't find it in the ubuntu wiki, but see if you can do this:

[https://wiki.archlinux.org/index.php/PulseAudio#Glitches.2C_skips_or_crackling](https://wiki.archlinux.org/index.php/PulseAudio#Glitches.2C_skips_or_crackling)

---

### Post by Kitkin15 on 2011-12-02
Thanks alot!! So far its working great :)

---

