---
title: "Ati Radeon X800 / Ubuntu 7.04"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by fragment on 2007-05-30
I'm new to Ubuntu, and I'm finding it difficult to find and install the correct video drivers.

I have a Radeon X800 AGP, and currently my 21" CRT screen is set to a resolution of 1024x768. The screen is capable of over 1600x1200...

Could anyone lend me a hand? I've used Linux before but i'm out of practice, so I should be considered a noob!


Any help is appreciated, thank you!

---

### Post by eye208 on 2007-05-30
Open a terminal window (from the applications menu), maximize it and enter "sudo dpkg-reconfigure xserver-xorg". You will be asked for your password. In the following wizard you can change the configuration of the screen. At one point you can choose from a list of display resolutions. This is where you can enable 1600x1200. Leave all the other values unchanged and skip automatic detection of graphics card and monitor. After you are done with the wizard, press Ctrl-Alt-Backspace to restart graphics mode or just restart the computer. Your display will then use the highest resolution you selected from the list.

---

