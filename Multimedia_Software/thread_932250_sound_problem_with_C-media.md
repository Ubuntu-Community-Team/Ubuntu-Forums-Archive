---
title: "sound problem with C-media"
date: 2008-09-28
forum: Multimedia Software
---

### Post by jolato on 2008-09-28
Hi,
I run hardy 804 but I messed  up by partly updating to intrepid. I can't hear any sound anymore. I have C-media souond card and can see my card in the logs, eg:

**lspci**:

00:0e.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

**cat /proc/asound/cards**

 0 [CMI8738        ]: CMI8738-MC6 - C-Media CMI8738
                      C-Media CMI8738 (model 55) at 0xd800, irq 11

I ran **gnome-alsamixer**, but speakers setting seem ok, please see screenshot.

Could someone give me some insight into what might be the cause ?

Gr,
Jo

---

### Post by jolato on 2008-09-28
> **jolato said:**
> Hi,
I run hardy 804 but I messed  up by partly updating to intrepid. I can't hear any sound anymore. I have C-media souond card and can see my card in the logs, eg:

**lspci**:

00:0e.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

**cat /proc/asound/cards**

 0 [CMI8738        ]: CMI8738-MC6 - C-Media CMI8738
                      C-Media CMI8738 (model 55) at 0xd800, irq 11

I ran **gnome-alsamixer**, but speakers setting seem ok, please see screenshot.

Could someone give me some insight into what might be the cause ?

Gr,
Jo

I found the problem (using gnome-alsamixer, had to check some options)

---

### Post by Azyx on 2008-10-15
> **jolato said:**
> I found the problem (using gnome-alsamixer, had to check some options)

What did you check for options? I have problem with 5.1 sound. If i don't check 4 Channals i only get sound i one speaker. If i check i get sound in all but center-speaker. 

If i run Speaker-test -c6 i only get sound in frontR och frontL, and Speker-test c4. I get sound in frontL and rearR.

/Azyx

---

### Post by markbuntu on 2008-10-15
Surround sound is not enabled by default in PulseAudio so you need to do that yourself. Here is a good guide:

[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

If that doesn't work for you, you can try editing your ~/.asoundrc file like this:

[http://ubuntuforums.org/showthread.php?t=899139](http://ubuntuforums.org/showthread.php?t=899139)

Be sure to enable and turn up the extra surround sound sliders in your volume controls!!

---

### Post by go_beep_yourself on 2008-12-13
How did you make your desktop look like that? It reminds me of KDE with the big panel at the bottom.

---

