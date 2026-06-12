---
title: "Java  capture problem"
date: 2010-08-11
forum: Multimedia Software
---

### Post by dansan on 2010-08-11
I have been trying unsuccessfully to record a speech sample at [http://www.voxforge.org/home/read](http://www.voxforge.org/home/read). I can record my voice crystal clearly with Audacity, so sound is working fine, but the website uses a Java applet.

Clicking *record* generates the following message in the applet:

```
java.security.AccessControlException: access denied
(javax.sound.sampled.AudioPermission record)
```

Opening ff in terminal provided the following information on what happened while I tried to use the applet:

```
Capture uploadWavFile is:/tmp/VF-dir5714653586339963972.tmp/a0165.wav
java.security.AccessControlException: access denied
(javax.sound.sampled.AudioPermission record)
duration1:0.0
```

Would someone point out what I need to do to permit access? I've seen some suggestions about changing .java.policy, but in Lucid this seems to be done with Java Policy Tool. Would doing this in terminal be simpler?

Daniel

---

