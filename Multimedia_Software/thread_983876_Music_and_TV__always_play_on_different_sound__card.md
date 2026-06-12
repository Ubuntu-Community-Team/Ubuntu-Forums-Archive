---
title: "Music and TV  always play on different sound  cards"
date: 2008-11-16
forum: Multimedia Software
---

### Post by mlgdr on 2008-11-16
Hi, 

I have 8.10 installed and two sound card in my system (one nForce2 onboard sound chip and a separate card). When I start xawtv for watching TV I have to plug the speakers into the line-out of the onboard chip to hear the sound. All music players and system sound is routed to the separate card. To hear it, I have to plug the speakers into the line-out of that card.

The preferences in Preferences/Sound are set to Alsa-sound. I honored the suggestions of the alsa wiki and the onboard sound card is always device 0. What do I have to to, to get TV and music routed to the same sound card.

Regards 

    Martin

---

### Post by lovinglinux on 2008-11-16
This is probably because your TV card came with an internal cable to send the sound directly to the motherboard.

Connect the line-out from your TV card into the line-in of the separate card. Then raise the volume of "Line-in" in the separate card to listen it.

I don't have two sound cards here, just onboard, but this is the way I have been watching TV on Windows and Linux since I got the TV card years ago. I never bothered to install the cable from the TV card to the motherboard.

---

### Post by mlgdr on 2008-11-16
That's what I did. I plugged the cable from the TV card to the line-in of the onboard sound. And thats the default card (alsa device 0). The problem is the normal sound. It always comes from the extra card. 

Martin

---

### Post by lovinglinux on 2008-11-16
> **mlgdr said:**
> That's what I did. I plugged the cable from the TV card to the line-in of the onboard sound. And thats the default card (alsa device 0). The problem is the normal sound. It always comes from the extra card. 

Martin

It seems that you want everything passing through the onboard card, so open the computer case and remove the extra card if you don't want to use it. Otherwise, just plug the cable from the TV to the extra card instead of the onboard and all sound will be managed by it.

---

