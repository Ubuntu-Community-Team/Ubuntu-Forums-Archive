---
title: "mythzoneminder anyone?"
date: 2009-08-17
forum: Mythbuntu
---

### Post by newlinux on 2009-08-17
Anybody know how to setup mythzoneminder? For this particular machine I'm on hardy running zoneminder 1.23 - which I think is incompatible with the mythzoneminder in hardy repos (think that's expecting 1.22).

Anybody got any experience with this? or know how I can download the source to just mythzoneminder? Not too familiar with downloading myth code...

---

### Post by newlinux on 2009-08-17
I was able to compile and install it with zoneminder 1.23.3 haven't fully tested (heck, I just installed zoneminder, so I know little about that...). Will write up instructions when I have more time and confirm it is working.

---

### Post by newlinux on 2009-08-18
These are instructions for installing ZoneMinder 1.23.3 on Hardy, and then installing mythzoneminder. 


Disclaimers and assumptions

[LIST]
[*]Use at your own risk, I haven't tested these a ton, but they work on two of my systems.
[*]These are based on using zoneminder 1.23.3 on Hardy - which I installed using the instructions here: [http://www.linuxonline.ca/?q=node/8](http://www.linuxonline.ca/?q=node/8) (scroll to near the bottom)
[*]These instructions borrow heavily from google searches.
[*]These assume your want ZoneMinder 1.23.3 installed on Hardy. An older version is in the repos which you can install with apt, and Jaunty comes with 1.23.3
[*]If you already have ZoneMinder 1.23.3 installed, you can skip to the installing mythzoneminder section.
[*]Configuring zoneminder for your hardware is way beyond the scope of this how-to
[*]I'm completely new to zoneminder and mythzoneminder
[/LIST]

Now that that's out of the way here we go
**[SIZE="3"][COLOR="Red"]Install ZoneMinder 1.23.3 on Hardy[/COLOR][/SIZE]**
[list=1]
[*]Install prerequisites for zoneminder 1.23.3 on Hardy (taken from link above)
```

sudo apt-get install g++ mysql
sudo apt-get install binutils cpp fetchmail flex gcc gcc-4.0 libarchive-zip-perl
sudo apt-get install libarchive-tar-perl libmime-perl libstdc++6 libjpeg62 ffmpeg
sudo apt-get install libarchive-zip-perl zlib1g libdate-manip-perl libwww-perl libdevice-serialport-perl

```
[*]Download Gutsy deb, install it, fix missing dependencies, make appropriate symlink for apache config, and reload apache config.

```

wget ftp://www.northern-ridge.com.au/zoneminder/1.23/ubuntu/gutsy/zoneminder_1.23.3-3_i386.deb
sudo dpkg -i zoneminder*.deb
sudo apt-get -f install
sudo ln -s /etc/zm/apache.conf /etc/apache2/conf.d/zoneminder.conf
sudo /etc/init.d/apache2 force-reload

```

You should be able to go to your IP address /zm/ and the GUI will come up.

example [http://192.168.0.100/zm/](http://192.168.0.100/zm/) or [http://hostname/zm/](http://hostname/zm/)

[/list]

**[SIZE="3"][COLOR="Red"]Install MythZoneMinder (for ZoneMinder 1.23.3)[/COLOR][/SIZE]**
You will need to download the mythplugins source code, modify the configure file and one source code file, install dependencies and then compile and install.

[list=1]
[*] Download mythplugins source code tarball from the mythtv site: [http://www.mythtv.org/download](http://www.mythtv.org/download).
[*] Untar it to ~/mythplugins-0.21 (or wherever you'd like - these instructions assume this location)
[*] change line 526 of the ~/mythplugins-0.21/configure to allow compiling for 1.23.3. The line should be changed to: 
```

 if test "$zmversion" != "1.22.2" -a "$zmversion" != "1.23.3" ; then

```
[*]Modify line 216 of the file ~/mythplugins-0.21/mythzoneminder/mythzmserver/main.cpp to allow for zoneminder version 1.23.3. The line should be changed to:
```
if (g_zmversion != "1.23.3")
```
[*]Now install necessary dependencies and links, configure, compile and install.
```

cd ~/mythplugins-0.21
sudo apt-get install libmyth-dev libxv-dev distcc ccache libmysqlclient15-dev
sudo mkdir /usr/local/include/mythtv
sudo ln -s /usr/include/mythtv/libmyth/mythconfig.mak /usr/local/include/mythtv/mythconfig.mak
./configure --disable-all --enable-mythzoneminder --zm-version="1.23.3"
make
sudo make install

```

[*] Follow the mythtv wiki for configuring the plugin or if you need to install mythzmserver on a different machine than is running the plugin: [http://www.mythtv.org/wiki/MythZoneMinder](http://www.mythtv.org/wiki/MythZoneMinder). The main things you will need to do is run:
```

sudo mythzmserver --zmconfig /etc/zm/zm.conf 

```

on the server running zoneminder (you may want to add this to rc.local or create an init script). Then in mythfrontend where you installed the plugin you need to configure the it to connect to the IP address of where zoneminder is installed.
[/list]

Enjoy, and I hope these instructions are close to accurate and help someone...

---

### Post by jhetrick62 on 2009-08-19
I see that you are running this on a x64 machine, are you running with the amd64 kernel installed or the 32-bit kernel?  I'm looking to move to zm 1.23.3 on my 8.04 LTS systems.

I'm currently running zm 1.22.3 out of the repos on (3) separate systems, all 8.04 LTS although without any issues, (2) of them are 32-bit and (1) is 64 bit.

I'm building a new box for someone else with 8.04 LTS, also 64-bit, although zm seems to freeze after 12 hours so I'm in the process of debugging and wondering about moving to 1.23.3 more permanently.

Thanks,
Jeff

---

### Post by newlinux on 2009-08-19
I'm running the 32-bit kernel.

---

