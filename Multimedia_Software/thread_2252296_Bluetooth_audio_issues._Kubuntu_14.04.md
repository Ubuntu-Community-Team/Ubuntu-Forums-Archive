---
title: "Bluetooth audio issues. Kubuntu 14.04"
date: 2014-11-10
forum: Multimedia Software
---

### Post by Tadaen_Sylvermane on 2014-11-10
According to the bluetooth widget my headset is connected including to the audio service. My headset is selected as the primary for all Audio Playback in the Device Preferences. When I go to the Audio Hardware Setup tab I can select the headset and change the profile, in this case A2DP or Telephony Duplex. I get no sound out of this headset right now, even though it was working perfectly an hour ago. When I change the profile to A2DP and apply and ok, then go back into the Hardware Setup it is back on Telephony Duplex, still with no sound of any kind. After disconnecting and reconnecting the bluetooth a few times it works fine. How to solve so it works first time every time?

---

### Post by Jim_Menegay on 2014-11-12
I'm having the same problems with Ubuntu 14.04, a Logitech H800 headset, and a USB-BT400 Bluetooth dongle.  It seems to be conflict/race conditions between the sound configuration dialog and the bluetooth configuration dialog.  The sound configuration doesn't want to "remember" the AD2P choice when the bluetooth connection is lost.

---

### Post by Jim_Menegay on 2014-11-12
I found this which looks like a fix: [https://launchpad.net/ubuntu/+source/unity-control-center/14.04.3+14.04.20140922-0ubuntu1](https://launchpad.net/ubuntu/+source/unity-control-center/14.04.3+14.04.20140922-0ubuntu1)
Haven't tried it, though.

---

### Post by Photobug on 2014-11-12
> **Jim_Menegay said:**
> I found this which looks like a fix: [https://launchpad.net/ubuntu/+source/unity-control-center/14.04.3+14.04.20140922-0ubuntu1](https://launchpad.net/ubuntu/+source/unity-control-center/14.04.3+14.04.20140922-0ubuntu1)
Haven't tried it, though.

I am willing to try it.  Just not sure what to do with this link though.  I downloaded the "tar" version.  How do I install it?

---

### Post by kuckunniwi on 2015-01-26
I got it working back in 13.04, following these suggestions: [http://www.tooleweb.ca/blog/?e=8](http://www.tooleweb.ca/blog/?e=8)

If I remember correctly, it worked, but still gave me enough headaches to decide to ditch bluetooth altogether and revert back to good ol' wired connections...

Did either of you end up trying the *unity-control-center* solution? If so, how did it work out? T'would be nice to know if any progress has been made in the field, and whether it's worth giving it another try.

It really is amazing that bluetooth is **still** such an issue, ever since it *was broken* back in Jaunty...(see [how Ubuntu's broken bluetooth support came to be]("http://blog.projectnibble.org/2010/08/08/how-ubuntus-broken-bluetooth-support-came-to-be/")). Bluetooth is becoming more and more common to free us from wires in so many different *fields*, from keyboards, mice, headphones, speakers, etc. Particularly in the audio field, a lot of advances have been made in compression methods and sound quality. It strikes me as odd that it's not more of a priority to have out-of-the-box compatibility for these things...(spoken like a true hypocrite, who does nothing to contribute to development...but still true, nonetheless) ;)

---

