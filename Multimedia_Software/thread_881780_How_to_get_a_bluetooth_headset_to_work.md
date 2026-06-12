---
title: "How to get a bluetooth headset to work"
date: 2008-08-06
forum: Multimedia Software
---

### Post by MES5464 on 2008-08-06
After purchasing a Motorola HT820 I was easily able to pair the device with my Lenovo X60 Tablet using the Bluetooth Manager GUI, however I was not able to direct the sound from Rhythembox to the headset. Finally, I found this wiki:

[http://wiki.bluez.org/wiki/HOWTO/AudioDevices]("http://wiki.bluez.org/wiki/HOWTO/AudioDevices")

Here I learned that in a terminal window I could use the following command to direct all sound to my headset:

gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "sbcenc ! a2dpsink device=XX:XX:XX:XX:XX:XX"

XX:XX:XX:XX:XX:XX should be replaced with the MAC address of your headset.

Now if you go to System > Preferences > Sound > Devices > Music and Movies > Sound playback you will find that the field is now blank (I presume because it cannot represent your device or it's MAC address).

You should now be getting sound to come through the headset after restarting Rhythembox.

To direct the sound back to your computer's speakers simple return to the Sound preferences dialog and change the empty field to Autodect and restart Rhythembox.

To simply using my headset, I created a launcher using System > Preferences > Main Menu and hard coded the command above. Now when I want to use my bluetooth headset I click the launcher, then open Rhythembox, and listen all I want. After I am done, I open the Sound Preferences and set the sound back to the speakers.

I hope this helps someone save some time, and is useful.

(I tried to append this to other posts on this subject but they were all in archive and didn't allow new posts.)

---

### Post by epitaph123 on 2008-08-09
This menu edit is the first time I heard audio play through my Motorola HT820 headset, thank you for this post. :) :) :)

---

