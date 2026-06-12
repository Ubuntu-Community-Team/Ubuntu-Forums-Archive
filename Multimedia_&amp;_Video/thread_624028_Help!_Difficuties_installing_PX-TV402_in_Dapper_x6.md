---
title: "Help! Difficuties installing PX-TV402 in Dapper x64"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by jsmithy on 2007-11-26
Hello, :)

I'm a new to Linux and Ubuntu but I see a lot of reasons to move from Winblows.

I am trying to install the driver for a Plextor PX-TV402U USB2 PVR.

I went to a site that gives the following instructions in how to do it:

# Install required development packages (this is a big download)
sudo apt-get install linux-kernel-devel linux-headers-generic fxload libncurses5-dev
# Get the driver source
wget [http://nikosapi.org/software/WIS_Go7...atched.tar.bz2](http://nikosapi.org/software/WIS_Go7...atched.tar.bz2)
# Unpack the source
tar -xjvf wis-go7007-linux-0.9.8-patched.tar.bz2
t# Decend into source directory
cd wis-go7007-linux-0.9.8-patched
# Compile the software
make
# Install the software
sudo make install

Because the first instruction included linux-headers-generic, I would get an error stating not to be found. I substituted linux-headers-generic by linux-headers-2.6.15-29-amd64-generic

The process for the first instruction found everything and installed all. I had already installled linux-headers-2.6.15-29-amd64-generic and it so notified.

I downloaded the driver and untar it in my home directory. Changed to the directory that was created and executed:

make

the output was:

***** Using kernel source in /usr/src/linux-headers-2.6.15-29-amd64-generic *****

make modules -C /usr/src/linux-headers-2.6.15-29-amd64-generic M=/home/oem/wis-go7007-linux-0.9.8-patched/kernel
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-29-amd64-generic'
CC [M] /home/oem/wis-go7007-linux-0.9.8-patched/kernel/go7007-usb.o
/home/oem/wis-go7007-linux-0.9.8-patched/kernel/go7007-usb.c:30:27: error: media/tvaudio.h: No such file or directory
/home/oem/wis-go7007-linux-0.9.8-patched/kernel/go7007-usb.c:228: error: ‘TVAUDIO_INPUT_EXTERN’ undeclared here (not in a function)
/home/oem/wis-go7007-linux-0.9.8-patched/kernel/go7007-usb.c:238: error: ‘TVAUDIO_INPUT_TUNER’ undeclared here (not in a function)
make[2]: *** [/home/oem/wis-go7007-linux-0.9.8-patched/kernel/go7007-usb.o] Error 1
make[1]: *** [_module_/home/oem/wis-go7007-linux-0.9.8-patched/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-29-amd64-generic'
make: *** [all] Error 2

Being new to all this, I do not know what went wrong.

Can you help me?

Peace to all :)

---

### Post by jsmithy on 2007-11-27
Hello, :)

A friend of mine always said that the way to find out if you were crazy is not if you talk aloud when there is nobody around but to answer yourself.  But as I'm a newbie, I think this could help others like me.

I sent an email to Nikosapi, the author of the guide I was following in order to install this driver.

He pointed me to a patch that could be applied in reverse to get the patched driver I downloaded from his site to work with my kernel.

He advised to perform the following steps:

wget [http://files.zoeloelip.be/wis-go-0.9.8-2.6.17.patch](http://files.zoeloelip.be/wis-go-0.9.8-2.6.17.patch)
patch -R -p 1 < wis-go-0.9.8-2.6.17.patch
make

My gratitude goes to Nikosapi for his immediate answer and to zoeloelip for the patch used to fix the situation.

I added some repos to my list and installed mplayer. Followed Nikosapi's guide in order to test the setup and it did recorded perfectly in MP4 with no effort from the Dapper x64 box.  I am even more happy after I discovered that audio is louder than in any of the Winblows boxes I tried the TV402U in.  This means I will not have to use external amplifier to be able to watch TV, capture or author video.

Once again, remember this is good for Ubuntu Dapper Drake x64 with 2.6.15-29-amd64-generic kernel.

Good Luck with your setup :)

---

