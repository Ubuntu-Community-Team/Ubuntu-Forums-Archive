---
title: "microphone amplification needed"
date: 2009-11-07
forum: Multimedia Software
---

### Post by Piscium on 2009-11-07
With Jaunty, just setting my microphone volume to 100% was not loud enough for Skype and other applications. I found somewhere a tick box whereby I could amplify the microphone input by - I think - 30 db. Then I could use the microphone volume control to fine tune its volume.

Now I am using Karmic and cannot find something similar to the 30 db amplification. Any ideas?

---

### Post by Piscium on 2009-11-07
> **Piscium said:**
> With Jaunty, just setting my microphone volume to 100% was not loud enough for Skype and other applications. I found somewhere a tick box whereby I could amplify the microphone input by - I think - 30 db. Then I could use the microphone volume control to fine tune its volume.

Now I am using Karmic and cannot find something similar to the 30 db amplification. Any ideas?

Found a way to amplify the microphone. I downloaded this package with Synaptic:
gnome-alsamixer

The sound quality is not great but it fixes the volume issue.

---

### Post by finngruwier on 2009-11-16
I have the same problem - microphone signal is very low. I thought there was a problem with the microphone in my headset so I went out and bought a stand-alone microphone, buth the problem is still exactly the same.

In earlier versions of Gnome-alsamixer there was a check box for mic boost, but is seems to be replaced with a boost slider button. By boosting the mic signal with this button I can get the volume higher, but the background noise increases *dramatically*. It's a brand new PC and it should have very good audio capabilities, so I definately can't blame the PC for the backgroud noise. It must be a Ubuntu problem.

How come Ubuntu always have problems with sound? It's very frustrating! :-(

---

### Post by finngruwier on 2009-11-16
I have now found out that my problem is in fact this one:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217789](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217789)

---

