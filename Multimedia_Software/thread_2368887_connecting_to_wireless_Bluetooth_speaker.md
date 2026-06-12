---
title: "connecting to wireless Bluetooth speaker"
date: 2017-08-16
forum: Multimedia Software
---

### Post by rawlins02 on 2017-08-16
I'm hoping to use bluetooth to play music through the Jams Classic 2.0 mini speaker I just charged up. It turns on showing a blue light and makes a sound suggesting it is on. The bluetooth indicator on my Ubuntu 16.04 laptop says it's on and visible. I've installed bluez and several related packages. Used the bluetooth GUI to connect. GUI says connected and link quality is 100%. I play music with VLC, Rhythmbox and Totem movie player. In Pulseaudio Jams speaker is showing up under input devices and configuration as 'headset'. The music playing now through VLC is coming out of the laptop speaker, but not the Jams speaker. Seems I am close to getting this working.

---

### Post by jeremy31 on 2017-08-16
See if the bluetooth audio device is selected in sound settings

---

### Post by rawlins02 on 2017-08-16
Solved, sort of.... Music came through speaker when I removed the device and then in Bluetooth GUI and then reconnected. Possibly also by selecting the Jams speaker in Pulseaudio. One of those cases where enough trial and error will get the job done. But then bluetooth just went away in my system tray. Guessing the connection was dropped.

---

### Post by rawlins02 on 2017-08-16
After bluetooth went off I had to reinstall and reconnect the Jams speaker and repeat all the steps again. Maybe I don't know what I'm doing. If bluetooth goes off again unexpectedly I'll go out and buy a 1/8" cable and connect the speaker that way.

---

### Post by rawlins02 on 2017-08-16
Two issues. 

1) If the speaker is turned off. I need to remove it from the device list in Blueman GUI, re-pair it with bluetooth, and connect it again, to get it to work.

2) Bluetooth has shut off on it's on twice this afternoon. I then need to log in and out again to get it to turn on.

I'll admit I'm a novice with bluetooth on Ubuntu. Nevertheless, I've returned this thread to unsolved.

---

### Post by mc4man on 2017-08-17
Maybe take a read here, I've got it working ok here with small caveats about dual booting. 
Note that for a Ubuntu install blueman is not needed & in the case of above could be counterproductive
[https://ubuntuforums.org/showthread.php?t=2365083&p=13661744#post13661744](https://ubuntuforums.org/showthread.php?t=2365083&p=13661744#post13661744)

If wishing to pursue & unclear always best to ask first.

---

### Post by rawlins02 on 2017-08-18
> **mc4man said:**
> Maybe take a read here, I've got it working ok here with small caveats about dual booting. 
Note that for a Ubuntu install blueman is not needed & in the case of above could be counterproductive
[https://ubuntuforums.org/showthread.php?t=2365083&p=13661744#post13661744](https://ubuntuforums.org/showthread.php?t=2365083&p=13661744#post13661744)

If wishing to pursue & unclear always best to ask first.

Since I may not use this speaker very often, I'll not pursue this further until I make additional tests and gather more data on the problems. I'll try without blueman as you suggest. Your how-to looks helpful. Will get in touch if I wish to delve deeper.

---

