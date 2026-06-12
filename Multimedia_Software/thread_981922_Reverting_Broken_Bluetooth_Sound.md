---
title: "Reverting Broken Bluetooth Sound"
date: 2008-11-14
forum: Multimedia Software
---

### Post by Cerin on 2008-11-14
I recently bought a Dell-Mini, with Ubuntu preloaded. Everything worked flawlessly right out of the box, with the exception of Bluetooth sound.

So I decided to and tried get Ubuntu to direct sound to a Bluetooth headset using reference howtos like:

[http://forums.overclockers.com.au/showthread.php?t=694010](http://forums.overclockers.com.au/showthread.php?t=694010)
[https://help.ubuntu.com/community/BluetoothAudio](https://help.ubuntu.com/community/BluetoothAudio)

Unfortunately, not only did these guides not work, but now my original sound card has disappeared, so I have no sound at all. cat /proc/asound/cards used to show an Intel sound card, but now all it shows is:

 sudo cat /proc/asound/cards
 1 [Headset        ]: Bluetooth SCO - BT Headset
                      BT Headset 1

I tried reverting the configuration in the howtos, but it hasn't fixed my sound. How do I recover my original soundcard?

---

