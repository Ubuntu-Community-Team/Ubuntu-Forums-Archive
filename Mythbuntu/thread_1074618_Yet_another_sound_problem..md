---
title: "Yet another sound problem."
date: 2009-02-19
forum: Mythbuntu
---

### Post by Anthus on 2009-02-19
Hello all!

I'm sure this will be simple for some of you, but this problem is driving me nuts!

I cannot get sound to work on live TV.  I have searched around, and tried everything.

Here's the symptoms.

If I go into the volume controls in Ubuntu and unclick the "mute" on the line-in, I immediately get sound, even when not in the MythTV Frontend.  If I go into the front-end, I get a double sound.  it plays the sounds twice... (double the voices, for example)  

If I mute the line-in, I get no sound in the front-end.

Can anyone tell me what I need to do here?

Thanks!

Anthus

---

### Post by allene222 on 2009-02-19
As an experiment you might rename asound.conf temporarily so that you are using the default alsa settings and see if that makes a difference.  Also, make sure you don't have a .asoundrc file that has changed things and if you do try renaming it as well.

Allen

---

### Post by Anthus on 2009-02-19
I can't seem to locate either of these files.  Can you tell me where they are / should be?

---

### Post by Anthus on 2009-02-19
Okay, I'm pretty sure that I don't have either of those files.

Does anyone else have any suggestions?

Should I have the line-in muted in the volume_control?  With it muted, will Myth still have access to the line-in?

If it should not be muted, how do I get the sound to stop being played while I'm not in the front-end?

Thanks in advance for your help with this!

---

### Post by Anthus on 2009-02-24
Anyone?  

Someone surely has run into this before!

---

