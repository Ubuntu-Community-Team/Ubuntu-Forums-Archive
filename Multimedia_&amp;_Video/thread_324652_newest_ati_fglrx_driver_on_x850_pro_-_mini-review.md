---
title: "newest ati fglrx driver on x850 pro - mini-review"
date: 2006-12-24
forum: Multimedia &amp; Video
---

### Post by thePuck on 2006-12-24
Well, after a fresh install of edgy I did a fresh install of the [8.32.5 driver ]("http://ati.amd.com/support/drivers/linux/linux-radeon.html"). I have a radeon X850 pro AGP card running on an Abit AI7 board. Card is not overclocked, card bios are not modded, and PCI and AGP buses are locked at default 33/66.

Install went flawlessly (but then again I have always had good luck with their install) and configuration was normal. Composite still had to be set to off to get DRI to work. After reboot everything was fine. Glxgears gave about 8k fps and $ glxinfo | grep direct came back yes. Fglrxinfo came back correct as well.

Now, the main issue for people with the X800 and X850 cards in linux is the heat. Seems the fglrx driver heats the card to some degree and that causes people's fans to start spinning faster. I have a pretty well built box with lots of fans and such, so things generally keep pretty cool in there. I had never noticed a fan change before, so I wanted to see if the heat was still there on the new drivers. Since no equivalent of ATItool exists in linux, I simply rebooted into windows and checked the vid temps, which should not have changed too much simply by booting windows (even if you want to say the gart loading and such would have given it a boost of a couple degrees c, this is too much). The difference after between linux idle and windows XP idle was 45C to 36C. This is a huge difference.

My card doesn't change fan speeds until 65C, so that is why I never heard it. I don't know what to do, really. My goal is to completely migrate from XP over the next six months or so to give my wife time to acclimate. But gaming is an issue for both my wife and I and without the ATI drivers my card doesn't get 3d acceleration. And 9 degrees celcius is a huge jump, even if it is not all that hot in terms of the card. It can't be good for the card.

Anyway, those are my general thoughts. I am going to go back to the open source driver till I can figure out a better way.

---

### Post by jdeaton on 2006-12-31
I've been experiencing the same thing with the drivers on the x850. Has anyone had any luck finding a place to look to see if this being solved?

---

### Post by thePuck on 2006-12-31
The only thing I can suggest at this point is emailing ATI and bugging them about this issue. Otherwise...I have gone back to the open source ati drivers. 

Interestingly, the boot up hang I get sometimes when USB ports are loaded seems to start happening when I install the fglrx drivers. I don't know what to think of that.

---

