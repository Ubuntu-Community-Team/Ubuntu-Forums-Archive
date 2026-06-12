---
title: "Bluetooth Headset Connection Problems"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by BoardDWorld on 2008-01-07
I would like to connect my headset, preferably as A2DP, and would like my system to default the sound to this headset for everything when connected. I have viewed many guides yet nothing seems to resolve my problem. The problem is it bonds and I have set it to trusted but it doesn't stay connected for more than a second and will only attempt to connect when forced with the following command:

```
sudo hidd --connect 00:0D:3C:A3:B3:6E
```.

or when going to Blueman, selecting the headset device then Properties-Get Service List

I have installed Blueman, the Bluetooth Alsa package, created .asoundrc and added the following:

```
pcm.bluetooth {
	type bluetooth
        device "00:0D:3C:A3:B3:6E" #optional, connects to specific device instead the default one
        profile "auto"             #optional, supported profiles are: auto, hifi and voice 
}
```


Any help would be greatly appreciated.

---

### Post by BoardDWorld on 2008-01-08
bump

---

### Post by BoardDWorld on 2008-01-09
Well I'm another few steps closer, I installed the package bluez-utils, removed bluetooth-alsa from the repo's and then issued the following commands:

```
sudo modprobe snd-bt-sco
```

This modprobe command is now allowing me to connect my headset with the following command:

```
btsco -v 00:0D:3C:A3:B3:6E
```

Once connected I can see the headset in Skype, both ear pieces and the mic. work perfectly. Now I need to know how to tell my system to use it. This info was source here:
[http://www.linux.ie/articles/bluetoothheadset.php](http://www.linux.ie/articles/bluetoothheadset.php)


Previous to this I got the a2dp sound working using this method (the old method):
[http://wiki.schneidexe.de/linux/howtos/a2dp](http://wiki.schneidexe.de/linux/howtos/a2dp)

though this doesn't work for games and more or less doesn't work with Skype(you get only the right earpiece and no Mic.). You also need to issue a series of commands "everytime" you connect and disconnect the headset depending what you want to use the headset for...

I don't understand why this should be so difficult. This would be the first thing I have come across that works "FAR" better in XP and Vista. There should only be the simple initial pairing which defaults "ALL" audio to the headset when connected. Then the minority that want to play around with specific audio types can tune it to suit them selves. When the headset is switched off it should automatically switch back to the systems PCI sound. The current status of Bluetooth under Linux is very cumbersome.

---

### Post by MrBordello on 2008-01-15
try to make your ~/.asoundrc look like this:
```

pcm.bluetooth {
type bluetooth
}

pcm.!default {
 type plug
 slave.pcm "bluetooth"
}

```
Or even this:
```

pcm.!default {
type bluetooth
}

```
To default to the headset, but be warned: On my machine it seems not to default back to the soundcard, if the headset is not present - and often it just doesn't work (especially after reboots).
This works, as far as I know, only with Blueman installed!

---

### Post by pixolex on 2008-02-24
> **BoardDWorld said:**
> Well I'm another few steps closer, I installed the package bluez-utils, removed bluetooth-alsa from the repo's and then issued the following commands:

```
sudo modprobe snd-bt-sco
```

This modprobe command is now allowing me to connect my headset with the following command:

```
btsco -v 00:0D:3C:A3:B3:6E
```

Once connected I can see the headset in Skype, both ear pieces and the mic. work perfectly. Now I need to know how to tell my system to use it. This info was source here:
[http://www.linux.ie/articles/bluetoothheadset.php](http://www.linux.ie/articles/bluetoothheadset.php)


Previous to this I got the a2dp sound working using this method (the old method):
[http://wiki.schneidexe.de/linux/howtos/a2dp](http://wiki.schneidexe.de/linux/howtos/a2dp)

though this doesn't work for games and more or less doesn't work with Skype(you get only the right earpiece and no Mic.). You also need to issue a series of commands "everytime" you connect and disconnect the headset depending what you want to use the headset for...

I don't understand why this should be so difficult. This would be the first thing I have come across that works "FAR" better in XP and Vista. There should only be the simple initial pairing which defaults "ALL" audio to the headset when connected. Then the minority that want to play around with specific audio types can tune it to suit them selves. When the headset is switched off it should automatically switch back to the systems PCI sound. The current status of Bluetooth under Linux is very cumbersome.

I'm using a headset Nokia BH-204 with skype and ubuntu.

The only way to know the mac address for me is use this command:
```
hcitool con
```

Just with the modprobe and btsco commands i can connect, ear and speak, after changing the sound device for BT headset in skype configurations.

But it's not to easy, it's not the Ubuntu way...it should be simple, like my bluetooth mouse, activate, password, and the cursor is moving...If the BT gnome applet detects a sound device, why it can't just activate de BTSCO command? 

I'm also having beeps of connection/disconnection every time that there is no sound or activity, It's normal?
```
driver is not in use
disconnected SCO channel
speaker volume: 4 mic volume: 13
speaker volume: 4 mic volume: 13
i/o needed: connecting sco...
connected SCO channel
Done setting sco fd
speaker volume: 4 mic volume: 13
driver is not in use
disconnected SCO channel
speaker volume: 4 mic volume: 13
speaker volume: 4 mic volume: 13
speaker volume: 4 mic volume: 13
i/o needed: connecting sco...
connected SCO channel
Done setting sco fd
speaker volume: 4 mic volume: 13
speaker volume: 4 mic volume: 13
driver is not in use
disconnected SCO channel
```

---

### Post by oddiofile on 2008-04-18
I'm sorry, but where does snd-bt-sco come from? I've searched the options in my kernel
(2.6.24, 2.6.25) and it isn't there. Is there some sort of alsa package that contains this driver that I am missing?

# lsmod | grep sco
sco                    12992  0
bluetooth              53636  8 sco,rfcomm,l2cap,hci_usb

---

### Post by psyke777 on 2008-05-09
> **oddiofile said:**
> I'm sorry, but where does snd-bt-sco come from? I've searched the options in my kernel
(2.6.24, 2.6.25) and it isn't there. Is there some sort of alsa package that contains this driver that I am missing?

# lsmod | grep sco
sco                    12992  0
bluetooth              53636  8 sco,rfcomm,l2cap,hci_usb

linux-ubuntu-modules-(version)-generic

---

### Post by psyke777 on 2008-05-09
[http://ubuntuforums.org/showthread.php?p=4910397#post4910397](http://ubuntuforums.org/showthread.php?p=4910397#post4910397)

---

