---
title: "Bluetooth-Alsa help."
date: 2005-12-10
forum: Multimedia &amp; Video
---

### Post by gcain on 2005-12-10
Hi Guys,

I've been trying for a few weeks to get bluetooth-alsa working on my system. At first I couldn't get anywhere but now I'm making progress and suspect there is just one problem left before its working.

When I type in btsco -v MACADDRESS I get:

Device is 0:0

At which point I'm asked for a pin, if I enter the wrong one it asks me again so this part is working right.

Then I get:

Voice setting: 0x0060
RFCOMM channel 1 connected
read info: Invalid argument

And that's the end of it; syslog tells me nothing other than that the pins were reqested and sent.

Does anyone who has managed to get this working have any idea what I can do to get it to work.

I'm running 5.10 (2.6.10-5-686) on a Dell Inspiron 9300. The headset is a Motorola HS820 which is about to be replaced by a proper set of headphones.

Any suggestions welcome, I feel like I've been batteling this for decades...

Thanks to all who comment in advance!

---

### Post by gcain on 2005-12-26
I managed to get everything to work using the latest version of btsco off CVS.

Only thing left to do now is get the Audio quality above sounding like a bad phone call.

Any one have any ideas how to do this?

---

### Post by gsanse on 2006-02-15
I am trying to do the same thing, but I cannot get a connection to the headset.  I get an authentication error every time I try to establish a connection. Could you make a description of how you made it work?

gsanse

---

