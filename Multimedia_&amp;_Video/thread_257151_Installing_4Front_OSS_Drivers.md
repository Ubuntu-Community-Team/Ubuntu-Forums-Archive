---
title: "Installing 4Front OSS Drivers"
date: 2006-09-14
forum: Multimedia &amp; Video
---

### Post by jazzworksweb on 2006-09-14
Good news. No need to recompile your kernel, just install the kernel headers instead. I have the 4Front Open Sound System working on Ubuntu 6.06 Dapper Drake 32 bit version as of now with the following steps taken.

[SIZE="2"]**Install Build Dependencies**[/SIZE] :-|

The oss installer will tell you what dependencies it needs as far as building. To satisfy the basic build dependencies install the following.

```
sudo apt-get install build-essential libncurses-dev
```

[SIZE="2"]**Install Kernel Headers**[/SIZE] :cool:

You'll need to get the header files for the kernel you are running so that oss can build it's module against them so that the module built will fit in the running kernel. If you upgrade your kernel (or if it get's upgraded for you, e.g. by a system update) you will have to do this over again.

```
sudo apt-get install linux-headers-`uname -r`
```

[SIZE="2"]**Install Kernel Compiling Dependencies**[/SIZE] :twisted: 

Get the packages needed for compiling a kernel from scratch. I don't know for sure if this is necessary but I'd recommend it anyway. The command below comes from the [Custom Kernel HOWTO]("https://wiki.ubuntu.com/KernelCustomBuild") on the wiki.

```
sudo apt-get install linux-kernel-devel fakeroot kernel-wedge kernel-package
```

[SIZE="2"]**Install The 4Front OSS Drivers**[/SIZE] :cool: 

Download the NO REGPARM version of the [4Front OSS drivers]("http://www.opensound.com/") and cd into the directory where you saved the oss tarball. in this case i use the desktop as an example.

```
foonuts@servalot:~/Desktop$ ls
oss3994b-linux-x86-v26.tar.gz
foonuts@servalot:~/Desktop$ mkdir 4front && cd 4front && tar vxzf ../oss3994b-linux-x86-v26.tar.gz
foonuts@servalot:~$ sudo ./oss-install
```

The default options should probably be fine but feel free to investigate.

[SIZE="2"]**Pitfalls & Known Limitations**[/SIZE]

You can remove the oss tarball if you wish, but if you do a system upgrade that  installs a new kernel you will need to reinstall the linux headers and 4Front driver again. 

Since ESD relies on ALSA you will not have system sounds in gnome but most apps work fine with OSS anyway. As far as i know you cannot use the ALSA OSS emulation in conjunction with these drivers. 

[SIZE="2"]**Usage**[/SIZE]

Each time you boot, before you can use the drivers you'll need to activate them by running the soundon program.

```
sudo /usr/lib/oss/bin/soundon
```

After that, be sure to turn on your speakers ;) and turn up the volume and try the sound test.

```
/usr/lib/oss/bin/osstest
```

If you want sounds in a program (such as xchat) that has the option to use an external player you can use the ossplay program located in the bin directory of the oss install. By default the standalone sound player is

```
/usr/lib/oss/bin/ossplay
```

You can access the magic utility where you can peform most of these tasks graphically. This will also let you reconfigure your card setup.

```
/usr/lib/oss/bin/soundconf
```

[SIZE="2"]**Sound On During Boot**[/SIZE]

If you want oss to insert itself into the running kernel on startup you must either write your own init script (the one that's supposed to come with it seems to be missing) or edit your /etc/rc.local file and make it look like this:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/lib/oss/bin/soundon

exit 0

```

rock on.

\\:D/

---

