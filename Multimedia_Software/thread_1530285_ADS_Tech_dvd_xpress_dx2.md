---
title: "ADS Tech dvd xpress dx2"
date: 2010-07-13
forum: Multimedia Software
---

### Post by pdrift on 2010-07-13
Hello, I have this old usb capture card thats been sitting around that I used in windows in the past but i've been using ubuntu and xubuntu lately and I would love to get it working in linux to get some use out of it.
After searching google and these forums I found that some people managed to get it to work. So I gave it a shot but i'm having trouble.

My system is an old dell dimension 4100 with a 1ghz pentium 3 and 512mb of ram running xubuntu 10.04.

I tried using these instructions I found through google on this page:
[http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Dapper.2FEdgy.2FFeisty.2FGutsy](http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Dapper.2FEdgy.2FFeisty.2FGutsy)

[COLOR="Blue"]# Install required development packages (this is a big download)
sudo apt-get install linux-headers-generic fxload libncurses5-dev
# Get the driver source
wget [http://nikosapi.org/software/WIS_Go7007/wis-go7007-linux-0.9.8-2.tar.bz2](http://nikosapi.org/software/WIS_Go7007/wis-go7007-linux-0.9.8-2.tar.bz2)
# Unpack the source
tar -xjvf wis-go7007-linux-0.9.8-2.tar.bz2
# Decend into source directory
cd wis-go7007-linux-0.9.8-2
# Compile the software
make
# Install the software
sudo make install[/COLOR]


before starting, lsusb showed the device was being recognized, but now after trying those set of instructions it doesn't show up anymore. I think those instructions might be wrong since i'm running lucid.

So do I need to undo what those instructions did and try a different method? When I run gorecord from a terminal this is the error I get:

[COLOR="Blue"]Unable to read /sys/bus/usb/drivers/go7007: No such file or directory
Is the go7007-usb kernel module loaded?[/COLOR]

I'm guessing that the driver isn't loaded, I would really appreciate some help getting this to work. I'm not afraid of the terminal but i'm still learning how to use it and I don't understand the technical stuff yet.

---

