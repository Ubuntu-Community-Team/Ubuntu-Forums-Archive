---
title: "Restarted my Nexus 4 and now Ubuntu won't connect to my cellular network, says denied"
date: 2015-01-06
forum: Mobile Technology Discussions (CLOSED)
---

### Post by I.Bun.Tu on 2015-01-06
I installed Ubuntu for devices about 2 months ago on my Nexus 4 following these instructions:

  [http://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/](http://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/)
  I unlocked my device and connected it to the computer and installed using the following command:

  ubuntu-device-flash --channel=ubuntu-touch/ubuntu-rtm/14.09 --bootstrap
  
Everything has been working fine until last Monday afternoon (8 days ago) when I  restarted the phone and could no longer connect to my cellular network. I  am using WIND Mobile and I live in Toronto. 


  In the network settings under the cellular section, where it would  display the network name and connection strength, instead it just says  "Denied" with a blank connection status (or 0 bars of connectivity; the  triangle outline).


  I have tried restarting and powering off, and leaving the phone off  for a day, etc. nothing has seemed to work. I swapped out SIM cards with  my Mom who is with Fido and her sim card connects to her network  perfectly.


  I also tried my house-mates SIM (he is with Koodo) and he got the same thing, his network is Denied.


  I have also tried my WIND sim card in other phones and it has no issue connecting to my network.


  I know that Koodo, WIND, Mobilicity, etc. use the same range of frequencies to connect. And that Bell, Rogers, Fido use a different range of frequencies.


  It seems that a recent update or something for Ubuntu Touch has given  it an error in connecting to the frequency ranges for Koodo/WIND/etc.  while the frequencies for the big wig companies are unaffected.

  
What can I do about this? My ubuntu phone has become unusable.

  phablet@ubuntu:~$ system-image-cli -i
current build number: 12
device name: mako
channel: ubuntu-touch/ubuntu-rtm/14.09
last update: 1969-12-31
version version: 12
version ubuntu: 20141218
version device: 20141119
version custom: mako-1.1

  My phone says it is up to date. Please let me know if I can provide  any more information or how I can troubleshoot this issue. Thanks.

---

### Post by slickymaster on 2015-01-06
*Moved to the ***Mobile Technology Discussions*** sub-forum*

---

### Post by I.Bun.Tu on 2015-01-06
While working with the guys in the #ubuntu-touch freenode irc channel I eventually flashed my Nexus 4 back to android and connected to my mobile network. The Ubuntu Touch guys believe this caused a radio fw update. I was then able to reflash and reinstall the latest stable version of Ubuntu Touch and reconnect to my mobile network. Definitely not an ideal situation but at least I am connected again and I don't have to use Android or iOS.

---

