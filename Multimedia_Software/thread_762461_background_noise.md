---
title: "background noise"
date: 2008-04-22
forum: Multimedia Software
---

### Post by Inferied on 2008-04-22
I hear a background noise in my earphones all the time... It is louder when I use Amarok.

---

### Post by Stason on 2008-04-22
It is a common issue. Somehow I think it is related to drivers. Ubuntu relinquish control over the sound device if there is no sound and when that happens it picks up interference from hard drives or something else. Windows drivers do not release the device and hence it is always active and there is no such idle whining noise. I start thinking about looping an empty sound file to keep the audio device loaded and avoid that loop noise.

If you hear the noise all the time - then that's a different story. It might be related to some fault in your equipment.

---

### Post by Inferied on 2008-04-22
Yup, I hear it all the time, even when I'm playing a song there's background noise... Will it go away if I change headphones?

---

### Post by dperfors on 2008-04-22
I don't think that will help, I have this problem sometimes on Windows as well.
For me the problem comes when I set the OS sound control on 100%. This sound control is communicating directly with the driver...
When controlling the sound volume in the media player it doesn't remove that noise, but when I lower the "OS" sound, the noise goes away...
Hope this helps :)

---

