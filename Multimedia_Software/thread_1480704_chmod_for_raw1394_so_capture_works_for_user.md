---
title: "chmod for raw1394 so capture works for user"
date: 2010-05-11
forum: Multimedia Software
---

### Post by charonred on 2010-05-11
For some reason I can't connect my JVC MiniDv camera in kdenlive (or kino) until I run this script in terminal
```
sudo chmod 666 /dev/raw1394
```
but it needs re-entering each time I reboot my PC.

How can I make this access permanent?


.

---

### Post by Stason on 2010-05-12
I do that:
```

sudo chmod a+rw /dev/raw1394
```

but it does not stick either.

---

### Post by cchhrriiss121212 on 2010-05-12
I had a similar problem a while back, the solution was to add the commands I needed to /etc/gdm/PostLogin/Default. So to break it down you just:
```
sudo gedit /etc/gdm/PostLogin/Default
```
Then paste "chmod 666 /dev/raw1394" to the file, save, and reboot to test it out.

---

### Post by no2498 on 2010-05-12
told you so lol
glad to see its working out for you

---

### Post by charonred on 2010-05-12
thanks all, got the solution from another post I had on [capture problem]("http://ubuntuforums.org/showpost.php?p=9285004&postcount=24")

> follow below solution taken from this wiki - [https://help.ubuntu.com/community/Firewire]("https://help.ubuntu.com/community/Firewire")

Method1
Ubuntu 10.04 terminal:

```
echo 'KERNEL=="raw1394", GROUP="video", MODE="0664"' |
sudo tee /etc/udev/rules.d/50-raw1394.rules
&& sudo restart udev
```

Then unload and reload raw1394,

```
sudo modprobe -r raw1394 && modprobe raw1394
```

and type in a terminal:

```
sudo /etc/init.d/udev restart
```

Next time when you restart you won't have to keep changing permissions.
works a treat and is permanent


.

---

