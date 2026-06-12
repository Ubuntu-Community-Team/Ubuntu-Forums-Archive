---
title: "My Brightness resets to maximum on opening several apps !!"
date: 2012-11-25
forum: Multimedia Software
---

### Post by wizardvenkat on 2012-11-25
Whenever I switch ON my PC, I realized that the brightness resets to maximum. So I modified /etc/rc.local file with this :

```

echo 40 | sudo tee /sys/class/backlight/nvidia_backlight/brightness

```

which works fine if I enter it directly in the terminal.
But when I restart my PC, first it sets to 40 % as I mentioned in the above code (During login). But resets to 100 % after entering my desktop.

I'm using Ubuntu 12.10 on my Sony VAIO VPCCW15FG which has Nvidia graphics card in it

I also found that while opening several apps like Firefox, Thunderbird, some Wine programs and apps inside Google chrome, the brightness sets back to maximum.

What's possibly causing this brightness shift ?

---

