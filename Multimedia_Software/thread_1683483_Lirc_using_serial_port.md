---
title: "Lirc using serial port"
date: 2011-02-07
forum: Multimedia Software
---

### Post by gregmcc on 2011-02-07
Running Ubuntu 10.10 and trying to get lirc working with a TSO4848 using the serial port.

I've tried Winlirc and it work fine under XP so I dont think its a hardware problem.

I've followed a ton of posts and dont seem to be getting anywhere.

I've disabled the serial port:

```
sudo setserial /dev/ttyS0 uart none
```

in the kernel and if I view dmesg:

```
[   36.628971] lirc_dev: IR Remote Control driver registered, major 251
[   37.435904] IR LIRC bridge handler initialized

``` 

I also dont have a file called /dev/lirc0 that all the posts refer to,  but I do have a /dev/lird

Anyone with a serial receiver post their hardware.conf file? Where am I going wrong?


Here is my hardware.conf

```
#Chosen Remote Control
REMOTE="Home Brew"
REMOTE_MODULES="lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"


```

---

### Post by gregmcc on 2011-02-08
Anyone?

---

### Post by Ceyx on 2011-02-08
I am working on getting lirc going with an old IBM receiver. Some progress so far, but not quite there so I cannot speak with any authority.

I'd be interested in your progress...

Ciao !

---

### Post by gregmcc on 2011-02-09
So far none yet. :( I"ll let you know if I get anywhere.

---

### Post by Ceyx on 2011-02-12
Hey....I found a solution that works for me.  Turns out that I have a Logitech/AST receiver which I could only find out about by searching on the FCC ID.

Just about to throw in the towel on this one when I found :

[http://azug.minpet.unibas.ch/~lukas/linux_recipes/lirc_logitech-AST.html](http://azug.minpet.unibas.ch/~lukas/linux_recipes/lirc_logitech-AST.html)

The long and short of my (our?) solution : The Lirc code in the repositories was compiled to NOT use /dev but to use /var/run/lirc/lircd.  Fine with me !  No recompiling the kernel or fooling with permissions....

Hope this provides some light....my remote is working now using 
/var/run/lirc/lircd

So below is a note to myself and hopefully others for the future.

Setting up lircd

To get the lirc daemon up and running with the Logitech AST IR RC, move the configuration file for the remote control model to /etc:

ln -s /usr/share/lirc/remotes/logitech/lircd.conf.logitech /etc/lircd.conf

Then start the lirc daemon by specifying the logitech driver, the serial device where the receiver is connected and eventually the name of the unix domain socket where clients can connect and read depressed keys.

lircd --driver=logitech --device=/dev/ttyS0 --nodaemon

Run

irw /var/run/lirc/lircd

and press some keys on the remote to check if everything works ok.

Be aware of the fact that lirc by default creates it's socket and fifo at non-standard places i.e. in /dev/. On Ubuntu the place is /var/run/lirc/. 

Thanks to Lukas Zimmerman for his OpenSuse post which I shamelessly copied and edited.

---

