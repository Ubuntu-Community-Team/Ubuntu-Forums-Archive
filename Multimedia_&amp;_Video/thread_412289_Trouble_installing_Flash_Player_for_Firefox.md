---
title: "Trouble installing Flash Player for Firefox"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by Thrasonic on 2007-04-17
So I'm following the instructions on the web site to install the Flash Player plugin for Firefox.  The first few steps are below:

cd ~/Desktop
tar -xzvf install_flash_player_9_linux.tar.gz
sudo mv -f ~/Desktop/install_flash_player_9_linux/libflashplayer.so /usr/lib32/firefox32/plugins
sudo mv -f ~/Desktop/install_flash_player_9_linux/flashplayer.xpt /usr/lib32/firefox32/plugins

The first two lines work in Terminal, but I get stuck on the third line.  I'm pretty certain it's because my path to the firefox directory is different from the path in that line, only I don't know how to find the correct path for my install seeing as how I'm a newbie and all.  How can I find the correct path?

---

### Post by mrreality13 on 2007-04-17
i too have issues but mine are this,

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.
 
any ideas?
thanx..

---

### Post by Thrasonic on 2007-05-01
bump

---

### Post by NeoLithium on 2007-05-01
You can get the flashplayer plugin for firefox through the repositories with 
```

sudo aptitude install flashplugin-nonfree

```

---

### Post by Thrasonic on 2007-05-01
Here's what I got when I tried that:

bubba@kubuntu:~$ sudo aptitude install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for flashplugin-nonfree
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
bubba@kubuntu:~$  

Any thoughts?  It doesn't seem to be working.

---

### Post by Thrasonic on 2007-05-02
bump

---

### Post by Thrasonic on 2007-05-02
bump

---

### Post by lahook on 2007-05-02
> **Thrasonic said:**
> So I'm following the instructions on the web site to install the Flash Player plugin for Firefox.  The first few steps are below:

cd ~/Desktop
tar -xzvf install_flash_player_9_linux.tar.gz
sudo mv -f ~/Desktop/install_flash_player_9_linux/libflashplayer.so /usr/lib32/firefox32/plugins
sudo mv -f ~/Desktop/install_flash_player_9_linux/flashplayer.xpt /usr/lib32/firefox32/plugins

The first two lines work in Terminal, but I get stuck on the third line.  I'm pretty certain it's because my path to the firefox directory is different from the path in that line, only I don't know how to find the correct path for my install seeing as how I'm a newbie and all.  How can I find the correct path?



did you run "./flashplayer-installer" in the directory you created by untaring in the terminal?
when you do that it should ask where you want to install the plugins

tar -xzvf install_flash_player_9_linux.tar.gz
cd to new directory
./flashplayer-installer
probably install in /usr/lib/firefox/plugins

---

### Post by jargoman on 2007-05-05
flashplugin-nonfree is not in the repositories?
same with sun-java6-plugin

---

### Post by jargoman on 2007-05-05
you can test your flash here
[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

does anyone know how to get Adobe Shockwave working

---

### Post by Jeff_From_Hell on 2007-05-05
which version of ubuntu are you on?
if your using feisty, do this:
Applications>Add/Remove Then go to the drop down menu and select "All Available Applications" and search Restricted.  Then check the package that shows up. got flash working for me.

---

### Post by ggaaron on 2007-05-06
Edit your /etc/apt/sources.list or use synaptic and enable all repositories, add medibuntu repositories and flash plug-in is somewhere there.

---

### Post by dislocated on 2007-05-06
I'm running Feisty 64 bit mode.

Does anyone know when (if) there will be a 64 bit flash plug-in? Or do I need to re-install at 32 bits to watch YouTube?

---

### Post by jargoman on 2007-05-24
There are no 64 bit pluggins that I know of. 
I got this to work by installing automatx
[www.getautomatix.com](www.getautomatix.com)

---

