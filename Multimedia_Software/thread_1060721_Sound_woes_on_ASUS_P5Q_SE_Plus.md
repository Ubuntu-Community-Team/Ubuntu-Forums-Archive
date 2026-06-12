---
title: "Sound woes on ASUS P5Q SE Plus"
date: 2009-02-05
forum: Multimedia Software
---

### Post by raevol on 2009-02-05
Crossposting this from _[here](https://answers.launchpad.net/ubuntu/+question/59586)_ because I'm not getting much of a response there.

I have an ASUS P5Q SE Plus motherboard. It has an onboard VIA VT1708s soundcard. With the default Intrepid alsa installed, audio only comes out of the "rear" audio port, as opposed to the "front" audio port as it should. This is not the ports located on the front and rear of the case, borth ports are on the back of the case, but one is for "front" speakers and one for "rear" in a surround sound speaker setup. This is due to an incorrect driver being used by the outdated alsa version in Intrepid.

I can upgrade my alsa with the script _[here](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)_ to solve this problem, HOWEVER THIS CREATES ANOTHER PROBLEM. With this solution I can only get sound from one application at a time. If another application opens that uses audio, all previously playing audio stops and will not come back until the muted application is closed and reopened, stopping audio in all other applications.

I think that the alsa version in Intrepid needs to get upgraded to fix this so that we don't need to jerry-rig our alsa setup and break pulse audio, but I am not a developer and don't know for sure.

I've also tried the pulse audio fixes in _[this](http://ubuntuforums.org/showthread.php?t=789578)_ thread, but I'm still not able to get sound from multiple applications. I've noticed that the pulse audio device chooser does not save my settings between logins, but even with the device tagged as "Simultaneous" chosen I can't get sound from multiple applications.

Please, any help would be greatly appreciated! I really want to be able to listen to music while I do other things, and I don't understand why I can't do this in the latest version of ubuntu.

---

### Post by raevol on 2009-02-07
Not sure what the policy is on bumping? Should I make a new thread? Still need help...

---

### Post by raevol on 2009-02-09
Bump.

---

### Post by raevol on 2009-02-10
Bump? I feel like this is incredibly immature, could someone suggest a different avenue to get a response?

---

### Post by raevol on 2009-02-13
Bump...

---

### Post by raevol on 2009-02-18
*does the bump dance* Hope this gets a reply before Jaunty.

---

### Post by raevol on 2009-02-20
Finally solved this by editing my /etc/asound.conf as described here:

[http://www.pulseaudio.org/wiki/PerfectSetup#ALSAApplications](http://www.pulseaudio.org/wiki/PerfectSetup#ALSAApplications)

---

### Post by priegog on 2009-09-09
Hi, I'm thinking of buying a laptop with that same sound chipset. Has this issue been solved in Jaunty (and/or karmic, if you've tried that)?
You'd help me a lot.
Thanks

---

### Post by raevol on 2009-09-09
It has been resolved in Jaunty, yes.

---

### Post by priegog on 2009-09-09
Thanks a bunch, man. I think I know what my new laptop will be...

---

