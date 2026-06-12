---
title: "how autoplay dvd in ubuntu 10.04?"
date: 2010-05-02
forum: Multimedia Software
---

### Post by ramire on 2010-05-02
dear geeks
how autoplay dvd on insertion in ubuntu 10.04?
cant find the settings menu [IMG]http://www.ubuntugeek.com/images/au/3.png[/IMG]

tnx

---

### Post by cariboo on 2010-05-02
Can you play DVD's at all? Do you get the window in the screen shot when you insert a DVD?

---

### Post by zeroseven0183 on 2010-05-02
Hi!

1. open the File Browser (or just any folder in your Places menu)
2. click **Edit** and select **Preferences**
3. under the **File Management Preferences**, go to **Media** tab and you'll see something like this

[ATTACH]155110[/ATTACH]

then,
5. select the appropriate application to launch your DVD

Be sure you have the necessary codecs/packages before you can play your DVD. You can install the **libdvdread4** package ```
sudo apt-get install libdvdread4
``` or simply the whole **Ubuntu Restricted Extras** (large-size download) from Ubuntu Software Center.

Please see also [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) for a more complete guide then let us know when you're done or if you need further help.

---

