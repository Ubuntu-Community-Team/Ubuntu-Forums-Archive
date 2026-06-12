---
title: "Howto: use bluetooth audio with jaunty"
date: 2009-05-03
forum: Multimedia Software
---

### Post by mokbuntu on 2009-05-03
I am trying to connect my jawbone headset to Jaunty.  Through the bluetooth gui, i can pair witht he jawbone headset.  But i cannot connect to it.  I tried to run hcitool con and it does not show any active connections.

Update:
i had followed this website to setup audio.  [https://help.ubuntu.com/community/BluetoothAudio](https://help.ubuntu.com/community/BluetoothAudio)
After running this command,
gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "sbcenc ! a2dpsink device=XX:XX:XX:XX:XX:XX"
my sound card stopped working.  Even after trying all the steps mentioned in the link.

WHenever i play something, i just hear some crackling sound.
Please help

---

### Post by pauna on 2009-05-03
> **mokbuntu said:**
> I am trying to connect my jawbone headset to Jaunty.  Through the bluetooth gui, i can pair witht he jawbone headset.  But i cannot connect to it.  I tried to run hcitool con and it does not show any active connections.


Hmm, I set up my Nokia stereo bluetooth headset yesterday with my Jaunty laptop using instructions from [https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset) using the following deviations.

- Step 14, ignored modprobes (not necessary with Jaunty)
- Step 16, I didn't have a BT device but it seems to work anyway
- Step 17, used Jaunty's default BT GUI to pair the devices
- Step 24, could not get the test sounds to work
- Step 27, but it all worked ok in the end

---

