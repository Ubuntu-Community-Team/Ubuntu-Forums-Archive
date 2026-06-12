---
title: "[SOLVED] Problem with Bluetooth, Headset, and Skype"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by wieman01 on 2007-06-25
I few days ago I had to install Feisty 'cause Dapper died on me out of a sudden. Now I am looking for a reasonably simple guide in order to install my Bluetooth headset (Plantronics) so that it works with the latest version of Skype. For some reason I cannot find anything at all.

Does anybody know a good guide? I hate to admit it but I am stuck...

_Specs:_

> Kubuntu Feisty Fawn
> KDE
> Plantronics 590
> Billionton Bluetooth Dongle
> Skype v1.4

Does Skype 1.4 support Bluetooth devices at all?

---

### Post by wieman01 on 2007-06-26
Anybody? Friendly bump...

---

### Post by wieman01 on 2007-06-27
Once again answering my own question...

I have reverted back to Skype v1.3 which works fine for me. My Bluetooth headset connects via "btsco":
> btsco -v *[COLOR="Red"]mac_address[/COLOR]*
Although "btsco" has been deprecated it is still functional and will continue to be so until is it replaced by the latest ALSA bluetooth developement. But that's still a far cry, I could not get it to work properly.

"btsco" does a fairly reliable job. Thread closed!

---

