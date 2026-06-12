---
title: "ESS ES1879 sound chip"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by robperry on 2007-06-12
All,

I am new to Linux so forgive my ignorance.  I installed Ubuntu Linux on a Gateway Solo 5150 333 MHZ 256MB RAM  Laptop

I am impressed with the product, however I have encountered a glitch.  While the system has an ESS ES1879 sound chip it is not recognized by Linux.  When i click of the Xed-out speaker icon I receive an error message "No volume control GStreamer plugins and/or devices found"

Is anyone able to provide me the steps to implement the sound card.

Thank you

---

### Post by Zimmer on 2007-06-12
[http://ubuntuforums.org/archive/index.php/t-12525.html](http://ubuntuforums.org/archive/index.php/t-12525.html)

Have a good read right to the end post..

People seem to have got their ES18xx cards sorted this way..

..and this could explain why it is a problem...
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/39007](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/39007)

ps. I am not an expert, only a reasonable searcher ...

---

### Post by LDRoamer on 2007-06-14
Just so you know, the fix listed in that post does not work in Feisty - at least not for me on an Armada 1750 laptop with an es1869 soundchip. That fix did work fine in Edgy though.

---

