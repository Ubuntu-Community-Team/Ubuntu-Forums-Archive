---
title: "Microphone Problem"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by Prosis on 2007-07-16
Hello

I have a Toshiba A100 laptop with a realtek soundcard.  The soud works perfectly well.  But I can't get the thing to record anything.  I've searched a lot and found no answer to this.

With Windows, all I have to do is launch a recording application and record but with Ubuntu, I can't do it and I have never been able to do it either.

Can anyone help me?

thank you

---

### Post by Prosis on 2007-07-16
No one knows?

Because that's what is going to stop me or not from installing Ubuntu.  I'm a musician so I need to record music. :guitar:

---

### Post by fredj on 2007-07-16
Double click on the speaker icon in the system bar to open the alsa mixer. Use the Edit->Preferences menu
to add the appropriate recording controls and switches. Make sure they are unmuted and the volume levels
are set to at least 70 percent.

If you still have problems then post again but please don't threaten not to install Ubuntu because no one cares
about that. If you are a real musician then you probably can't afford to install Windows.

---

### Post by Prosis on 2007-07-17
Thank you for your reply, I will try this when I come home tonight :)

And it wasn't a threat at all lol, it was just an affirmation, if I can't have a microphone I can't have Linux.  I'm not a "customer" type of guy "if I can't have that then I won't have it at all" especially since this is open source. ;-)

And as far as Windows, I can't afford it but it came with my computer.  I just don't want it lol :P

---

### Post by Prosis on 2007-07-17
I can hear myself through the speakers but I am completely unable to record it...I tried it with the gnome-sound-recorder and Audacity :confused:

---

### Post by Gremlinzzz on 2007-07-17
I have audacity recorder working. think you have to set the mic i set mine for front.right click on volume icon open volume control manager click edit / perferences put a ckeck in all the boxs choose options  tab and set mic.
i:guitar:

---

### Post by CalvinK on 2007-09-13
> **Gremlinzzz said:**
> I have audacity recorder working. think you have to set the mic i set mine for front.right click on volume icon open volume control manager click edit / perferences put a ckeck in all the boxs choose options  tab and set mic.
i:guitar:
I have the same problem with my Toshiba A200 laptop. I tried to recompile alsa and add the realtek patch. Alsamixer doesn't show capture neither Kmix. I am unable to record anything except when using the frontmic (with many problems : bad sound, larsen effect ...). I posted my data at launchpad... I have no response yet. :confused:

---

