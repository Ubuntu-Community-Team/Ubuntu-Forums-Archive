---
title: "Solution to get mutiple LIRC remotes working"
date: 2015-03-21
forum: Multimedia Software
---

### Post by Fisher on 2015-03-21
Two years ago, I posted this thread: [http://ubuntuforums.org/showthread.php?t=2043121&highlight=lirc](http://ubuntuforums.org/showthread.php?t=2043121&highlight=lirc)
Finally I found a way to make it work, and decided to share with the community.
First of all, I found that the default lirc init scripts won't work with more than one receiver.
Randomly surfing the web, I found this blog post: [http://mythtvblog.blogspot.com.br/2008/04/setting-up-lirc-with-multiple-devices.html](http://mythtvblog.blogspot.com.br/2008/04/setting-up-lirc-with-multiple-devices.html)
This gave me some ideas!!
The principle is simple: I start lirc with a remote, and make it listen to some port, then make it again and again till I have all the remotes set. Then I start another lirc instance and connect the other listening lirc.
Here's the script I'm using:

```
#! /bin/sh
echo "Starting LIRC"

# Preparing the "environment"
dir="/var/run/lirc"
if [ -d "$dir" ]
then
	echo "$dir found! Doing nothing!"
else
	echo "$dir not found, creating it."
	mkdir /var/run/lirc
fi

# Starting Remote Wonder II and listening on port 9988
echo "Starting Remote Wonder II (devinput)"
/usr/sbin/lircd --driver=devinput --device=name='ATI Remote Wonder II' --pidfile=/var/run/lirc0.pid /etc/lirc/lircd2.conf --output=/var/run/lirc/lircd2 --listen=127.0.0.1:9988

# Starting Remote Wonder I and listening on port 9987
echo "Starting Remote Wonder I (atilibusb)"
/usr/sbin/lircd --driver=atilibusb --device=/dev/lirc0 --pidfile=/var/run/lirc1.pid /etc/lirc/lircd1.conf --output=/var/run/lirc/lircd1 --listen=127.0.0.1:9987

# Connecting both controllers to make then detectable.
echo "Connecting this mess!!"
/usr/sbin/lircd --device=/dev/lirc --pidfile=/var/run/lircd.pid --connect=localhost:9988 --connect=localhost:9987 /dev/lircd

# Creating symlink
file=/dev/lircd
if [ -h "$file" ]
then
	echo "$file found! Doing nothing!"
else
	echo "$file not found, creating symlink."
	ln -s /var/run/lirc/lircd /dev/lircd
fi
```

It's just quick and dirty, but is working for me!!
You can alter it adding remotes as you wish, just be careful to specify different pidfiles, devices and ports.
I can see both remote's key presses shown on irw, but irsend list "" "" shows no remote.
Remember to disable lirc on /etc/init.d, or like me, put this script on /etc/init.d/lirc. I think it's not a good idea. Anyway it's nice to keep an backup of the original file and this one, just in case...
I hope this can help someone as it had helped me.
By the way, now I have two remote wonders :-)

---

### Post by dino99 on 2015-03-22
That's great, and thanks for sharing

but have you sent a bug report about lirc not able to deal with several devices by default ? i think it should, and then be fixed.

---

### Post by Fisher on 2015-03-22
No, I had not sent any bug reports...
Just could not resist... Found my old pixelview remote and made it to work :-)

My remote looks like the one in this picture: [http://www.prolink-usa.com/image/TV-CX883P+_2_3.jpg](http://www.prolink-usa.com/image/TV-CX883P+_2_3.jpg)  

First, I created a new keymap, since many keys weren't working:
```
# table pixelview, type: UNKNOWN
0x01 KEY_1
0x0b KEY_2
0x1b KEY_3
0x05 KEY_4
0x09 KEY_5
0x15 KEY_6
0x06 KEY_7
0x0a KEY_8
0x12 KEY_9
0x02 KEY_0
0x03 KEY_TIME
0x1e KEY_POWER
0x13 KEY_AGAIN
0x10 KEY_KPPLUS
0x18 KEY_MUTE
0x00 KEY_INFO
0x16 KEY_UP
0x14 KEY_DOWN
0x17 KEY_LEFT
0x1f KEY_RIGHT
0x1c KEY_OK
0x19 KEY_CAMERA
0x1a KEY_SEARCH
0x04 KEY_PREVIOUS
0x0c KEY_NEXT
0x0e KEY_RECORD
0x1d KEY_STOP
0x08 KEY_PLAY
0x0f KEY_PAUSE
0x0d KEY_TV
0x07 KEY_RADIO

```

I changed CH+, CH- Vol+, Vol- and zoom to be up, down, right, left and ok, since I intend to use it on Kodi.
I saved the file on /etc/lirc.
Then, to avoid confusion, I copied /usr/share/lirc/remotes/devinput/lircd.conf.devinput to /etc/lirc/lircd3.conf, and changed both remote names from devinput to cx88.
After all this I added these lines to my script, just before the first remote:
```
# Prepaing Pixelview's remote 
echo "Starting CX88 (devinput)"
ir-keytable -c
ir-keytable --write /etc/lirc/cx88.keymap

# Starting the stuff
/usr/sbin/lircd --driver=devinput --device=name='cx88 IR (Prolink Pixelview MPEG' --pidfile=/var/run/lirc4.pid /etc/lirc/lircd3.conf --output=/var/run/lirc/lircd4 --listen=127.0.0.1:9989

```

And modified this line:
```
/usr/sbin/lircd --device=/dev/lirc --pidfile=/var/run/lircd.pid --connect=localhost:9989 --connect=localhost:9988 --connect=localhost:9987 /dev/lircd

```
I'm very happy!! Now my multiseat can run 3 Kodi instances, each one with his own remote!!
Hope this can be useful to somebody!!!

---

### Post by dino99 on 2015-03-22
3 kodi instances, wow 
may i ask how many eyes are lurking at time ???

---

### Post by Fisher on 2015-03-22
Just split my PC in many rooms. Trying to save a little power :-)
I have one monitor for my 4yr old daughter, other TV for my father, that is my neighbour, and other for my use, on a old tube TV.
I'm thinking in trying to connect an HDTV through HDMI, but I'm not sure if I'll be able to pass the remote control commands through CEC...
I'm also thinking on try to control the tube tv with lirc and the same remote I use in Kodi.
Anyway, if I succeed in doing this I'll probably share it here too ;-)

---

