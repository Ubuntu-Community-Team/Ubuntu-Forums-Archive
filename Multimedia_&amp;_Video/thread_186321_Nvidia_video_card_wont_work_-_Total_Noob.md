---
title: "Nvidia video card wont work - Total Noob"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by ZylogZ80 on 2006-06-01
Hello,

I just picked up a second hand older machine (P3, 192mb RAM, 30gb HDD) with an NVidia TNT2 card. I tried installing Ubuntu 6.06 and 5.10, and it didn't work on either. I get part of the way through the installation, and after it says that it's going to start X it just hangs at a black screen with a while cursor. I tried installing under VGA compatibility mode and it seemed like it was working, but I got an error saying that it couldn't start X because no displays were found. 

I removed the video card and was able to install dapper just fine with the on-board video, but the performance is absurdly poor. How can I get the driver for the TNT2 to work if I cant boot into X when the card is in? I'm a total noob, and am scared to death of editing config files and working with the command line. I saw some tutorials, but they are pages long and I don't quite get what I am supposed to do. Can anyone help me?

Thanks in advance.

---

### Post by spin2cool on 2006-06-01
Some suggestions off the top of my head:

From a console, login and then type:
```

sudo /etc/init.d/gdm stop 
sudo dpkg-reconfigure xserver-xorg 
sudo dpkg-reconfigure gdm 
sudo /etc/init.d/gdm start

```

If you still crash, try:
```

sudo apt-get install nvidia-glx

```

and then repeat the above steps.

---

### Post by ZylogZ80 on 2006-06-01
Thank you. I kind of stumbled upon doing some of that. I edited xorg.conf too. It's "working" but nothing higher than 640x480... I'll try your suggestions too. Thanks.

---

### Post by ZylogZ80 on 2006-06-01
Wow. Thank you so much.

This helped and Ubuntu is up and running.

Again, thank you.

---

