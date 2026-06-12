---
title: "radion all in wonder 9000"
date: 2007-09-24
forum: Multimedia &amp; Video
---

### Post by Cherio on 2007-09-24
Please help I'm new to Ubuntu. I have been a windows user all my life and never had a problem installing and running things. I would consider myeself prety computer savy but im having problems with my video card.

I have a radion all in wonder 9000 pro and i downloaded all the drivers... (i think) And all i get when i plug the card in is vertical dashed blue and red lines on the screen.

I cant get it to work at all Please help!

---

### Post by w4ett on 2007-09-24
The correct drivers for your card are included by default in Ubuntu. (xorg-driver-ati)

your card is not supported by the proprietary driver fglrx.  Only the 9500 cards and above are supported by  the restricted drivers  See:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I'd start by reconfiguring your xorg.conf.....boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"] "ati"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

Good Luck.

---

