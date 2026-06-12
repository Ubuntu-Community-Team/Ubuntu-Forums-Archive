---
title: "HOWTO: Unmute TV stations that have static"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by soulmatic09 on 2007-12-16
The TV tuner driver that comes with Linux has a default option to mute TV stations that have static. It's pretty annoying, because the slightest amount of static may render the TV mute. What you need to do is turn the "automute" variable in the driver to "0"

Here's how:

1) create a file in the /etc/modutils/ folder called "bttv"

2) put the following code in the file:
```
options bttv automute=0
```
3) login as root (type "sudo bash" in the terminal)

4) type the following commands in the terminal:
```
echo "bttv" >>/etc/modules
```
```
update-modules
```
```
modprobe -v bttv
```

That should do it. Open up you TV viewing program, and you're done!


Sources:

List of driver variables:
[http://www.mjmwired.net/kernel/Documentation/video4linux/bttv/Insmod-options](http://www.mjmwired.net/kernel/Documentation/video4linux/bttv/Insmod-options)

Instructions to change the variable under Debian GNU/Linux
[http://wiki.linuxhelp.net/index.php/Bttv_Setup](http://wiki.linuxhelp.net/index.php/Bttv_Setup)

---

### Post by soulmatic09 on 2007-12-16
Another way to change it is if you are using the Zapping TV Viewer.

Click "Controls" and uncheck "Automute"

---

