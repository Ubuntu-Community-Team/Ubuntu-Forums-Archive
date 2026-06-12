---
title: "Youtube+Flash: Pink-Red youtube videos on Chrome 10"
date: 2011-03-15
forum: Multimedia Software
---

### Post by konstant@mail.ntua.gr on 2011-03-15
After trying several suggestions on the web, I am writing the following that applies to my Ubuntu 10.04:

1. Go to [http://www.youtube.com/html5](http://www.youtube.com/html5)
   Click "Enter trial of html5"
Pros: easy, nicer clearer videos
Cons: lots of CPU resources, full screen buggy (cannot return it to normal size...)

2. 

a) Downgrade to flash 10.1.85

   32bit
   >wget [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_i386.deb)
   >sudo dpkg -i flashplugin-installer_10.1.85.3ubuntu1_i386.deb

   64bit
   >wget [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_amd64.deb)
   >sudo dpkg -i flashplugin-installer_10.1.85.3ubuntu1_amd64.deb
b) remove flash plugin of chrome (libgcflashplayer.so). In my (default) configuration
   >  cd /opt/google/chrome
   > mv libgcflashplayer.so ~
   (just in case you want it back)

c)
   Start chrome with the  --allow-outdated-plugins option. E.g.
   > /opt/google/chrome/google-chrome --allow-outdated-plugins [https://mail.google.com/mail](https://mail.google.com/mail)



Pros: works as before, slightly lighter
Cons: a bit more involved (but not hard), use downgraded flash and have to call chrome using the above mentioned flag


The reason I wrote the thread was that I could not find the libgcflashplayer.so effect anywhere mentioned. I apologize if I repeat already known information.

References:
[http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html](http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html)

---

### Post by ChipOManiac on 2011-03-15
Disabling hardware accleration fixed the problem for me:

1. go to a flash website (miniclip.com) 
2. right click on a flash content and select "Settings"
3. in the dialog uncheck "hardware accleration" under the hardware tab.

---

### Post by konstant@mail.ntua.gr on 2011-03-15
For me it did not work. Please also note that I am referring specifically for the google chrome. This could be due to its own flash plugin (it seems they incorporated flash 10.2).

---

### Post by kirtley on 2011-03-16
My solution for a working flash/chromium setup on ubuntu 10.10 i386
[LIST=1]
[*]Install Chromium Stable and Flash 10.1
```

# Install Chromium stable
sudo add-apt-repository ppa:chromium-daily/stable && sudo apt-get update
sudo apt-get install -y chromium-browser
# install flash 10.1
cd /tmp/
wget "http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_i386.deb"
sudo dpkg -i flashplugin-installer_10.1.85.3ubuntu1_i386.deb

```
[*]set Chromium to use outdated plugins (I wasn't able to get sed to work for some reason, anybody know why?)
```

sudo vi /usr/share/applications/chromium-browser.desktop

```
Scroll down to the bottom and change
```
Exec=/usr/bin/chromium-browser %U
```
to
```
Exec=/usr/bin/chromium-browser --allow-outdated-plugins %U
```
save and quit
[*]Upgrade your system without upgrading flash
```

sudo apt-get update && sudo apt-get upgrade -yd
sudo rm /var/cache/apt/archives/flashplugin-installer*
sudo apt-get upgrade -y --no-download --ignore-missing

```
[/LIST]

---

### Post by johntaylor1887 on 2011-03-16
> **konstant@mail.ntua.gr said:**
> For me it did not work. Please also note that I am referring specifically for the google chrome. This could be due to its own flash plugin (it seems they incorporated flash 10.2).

Chrome does not have "its own" flash. It uses Firefox's flash if installed.

---

### Post by konstant@mail.ntua.gr on 2011-03-21
So what is the file  libgcflashplayer.so in
/opt/google/chrome ? And why if I have this file in place then downgrading flash does not work?

---

