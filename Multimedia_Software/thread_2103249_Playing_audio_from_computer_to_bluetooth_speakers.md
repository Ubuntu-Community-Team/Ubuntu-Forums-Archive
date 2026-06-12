---
title: "Playing audio from computer to bluetooth speakers"
date: 2013-01-09
forum: Multimedia Software
---

### Post by mastermindg on 2013-01-09
I'm running Kubuntu 12.04 on my desktop with a bluetooth usb adapter. I am able to connect and pair with devices including speakers (JamBox). I'm using Bluez to configure my devices. Currently my JamBox is showing as Paired and Audio Sink is selected. I found another post [here]("http://forums.opensuse.org/english/get-technical-help-here/multimedia/474764-bluetooth-headset-connected-but-sound-plays-thru-speakers.html") that refers to configuring a headset in Phonon, however I'm not seeing a bluetooth device in Phonon's settings (even with "Show Advanced devices" checked). 

Has anybody been able to play audio from bluetooth in Kubuntu 12.04? If so, let me know how to get this worked out. Thanks!

---

### Post by kuckunniwi on 2013-12-11
I'm having the same problem. I can pair with the bluetooth device, but it doesn't show up in Kmix or Phonon. I've looked everywhere and can't find a solution. Were you able to find a workaround of some kind? If so, it would be greatly appreciated...Thanks!

---

### Post by kuckunniwi on 2013-12-11
If you haven't been able to solve the problem, this here worked for me: [http://www.tooleweb.ca/blog/?e=8&weblogmessage=Your+comment+has+been+stored.+Because+comment+moderation+is+enabled%2C+it+is+now+waiting+for+approval+by+an+editor.#message](http://www.tooleweb.ca/blog/?e=8&weblogmessage=Your+comment+has+been+stored.+Because+comment+moderation+is+enabled%2C+it+is+now+waiting+for+approval+by+an+editor.#message) 

Wow! I'd been trying to get this thing to work for months and was just about to give up/throw my headphones out the window! Just follow the instructions (it won't let you install padevchooser, which is no longer available) and it ought to work. After installing and rebooting, I opened Blueman, deleted the device, searched, added, paired, set-up > A2DP sink (send audio), connected, and...voila! Device now shows up in Phonon! Thank God for that! All credit goes to Rob for posting the solution!

---

