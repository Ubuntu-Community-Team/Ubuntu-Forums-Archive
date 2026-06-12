---
title: "Acer TM2420 with Atheros AR5005G"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by Redeyes_Gambit on 2006-07-12
}{i,

I'm trying to get my dual-booting laptop's wifi to work in Ubuntu, and have had some success. However, that success has made it all the more confusing lol.

Ok, so here's the deal:

For some reason, when all this started out, Ubuntu wouldn't "see" the network when it was set to WPA-psk encryption. SO after dinking around for many hours on the forums I finally stumbled across a post that lead me to try setting my AP (Access Point) to have NO encryption, so Ubuntu could "see" the network. Then, after the network was "visible" to Ubuntu I could pull the old switcheroo and set it to  WEP encryption. (NOT WPA-psk encryption, which is what the AP was set too when Ubuntu _couln't_ see the network, but WEP encryption.) A Brilliant plan! 

So that's just what I did; I set the wireless AP to use NO encryption. Several set settings, switched swithces, dialed dials, and buttoned... er... buttons later and TADA! Working, un-encrypted, visible network in Ubuntu. Big grins ensue. However the kingdom is without walls at this point; and that makes me nervous. So, I go to set up WEP encryption in the AP, which goes as smooth as setting up a wireless AP can go (read as: makes-one-borderline-neurotic.) Some time later: SUCCESS! WEP encryption set up in the AP!

A quick jaunt back to Ubuntu to set up the key and settings and all that... Typedy type one very long 128 bit WEP key in... set default gateway device to ath0 and VIOLA! WORKING ENCRYPED NETWORK! Bigger grins ensue. 

And this folks would have been where the story would have ended had it been cell-shaded, and made by disney. The prince and his laptop, living in wireless encrypted bliss. Sadly it was not to be.

So I'm all happy thinking I finally got everything set. So I jump back into windows to do some stuff. I set up windows to use WEP encryption, typedy type long key yada yada... BADA! Windows is now on the WEP encrypted network. So I start working away only to find that when everything is set to use WEP, windows keeps losing the wireless connection even when I am only three feet from the AP. *head hits desk* DEFEAT!

Windows worked just fine without ANY dropping when the network was set to WPA-PSK encryption, however for some reason it doesn't seem to like WEP (Why? I dunno. it's windows.)

So it's back through a bagillion settings to set the AP back to use no encryption... setting up ubuntu... setting up windows...

And tada! Working network again. no dropping under windows. working network under Ubuntu. And thats all fine and dandy, dandy and fine, except my network is open for anyone who so pleases to jump on and use my DSL bandwidth and file server. Not so dandy and fine.

So my question is this:

1: how do you get WPA-PSK (Not WEP) to work in Ubuntu??

---

