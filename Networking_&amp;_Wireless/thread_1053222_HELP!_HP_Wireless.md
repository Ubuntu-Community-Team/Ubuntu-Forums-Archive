---
title: "HELP! HP Wireless"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by 3mb0 on 2009-01-28
First of all i want to say thank you for looking here, and possibley trying to help me out xD.

I currently have Ubuntu linux 8.10, for about 4 days now, running on a HP Pavilion dv9000.

I have to plug in a wire to my laptop to get any connection at all, which obviously i don't want to do (or i wouldn't be here).

I saw something similar to this, which told me a couple of commands, so i now have the wireless chipset i have. (i'm very new to do this, so please help me in the simplest way possible.)

03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01) 

I go to my drivers panel, and it says the driver is working and in use, but im sitting right next to my router right now (which i get vista connection on) and im having no luck. 

Screenshot of drivers panel: [http://s655.photobucket.com/albums/uu279/3mb0/?action=view&current=NOW.jpg](http://s655.photobucket.com/albums/uu279/3mb0/?action=view&current=NOW.jpg) 

Any help really appreciated!

3mb0

---

### Post by khelben1979 on 2009-01-28
[Check this out!]("http://www.linuxquestions.org/questions/linux-networking-3/slackware-atheros-problem-solved-693626/") Maybe it can help you?

---

### Post by Cope57 on 2009-01-28
Not to tell you what operating system(s) you should use, but I happen to have some good luck with [openSUSE]("http://www.opensuse.org/en/") 11.1 and [CrunchBang Linux]("http://crunchbanglinux.org/") for my HP Pavilion dv6900 laptop and the wireless.

I was impressed enough that the wireless worked from the liveCD's that I am now dual-booting openSUSE and Crunchbang Linux.

Vista *was* the default OS, but no longer...

Hard to believe I actually had Vista pre-installed on it for over a month...

---

### Post by Metaljaz on 2009-01-28
If you left click on the network manager on the top right hand side of the screen do you see the option for wireless connection. If so click on the little circle and you should be connected.

---

### Post by 3mb0 on 2009-01-28
> **Metaljaz said:**
> If you left click on the network manager on the top right hand side of the screen do you see the option for wireless connection. If so click on the little circle and you should be connected.

Thanks for trying, but unfortunatly, i go to the tab named "wireless" and there is nothing there =[

---

### Post by 3mb0 on 2009-01-28
> **khelben1979 said:**
> [Check this out!]("http://www.linuxquestions.org/questions/linux-networking-3/slackware-atheros-problem-solved-693626/") Maybe it can help you?

I'm stuck at the first hurdle. 

I really don't know how to install stuff. So i downloaded the install of madwifi, but i don't know the coding to install it to my computer.

3mb0

---

### Post by khelben1979 on 2009-01-28
To compile it from source you do this:

sudo root
./configure
make
make install

But you can also [try this]("http://rpmfind.net/linux/rpm2html/search.php?query=madwifi&submit=Search+...") which I suspect is much easier, especially when thinking about that compiling source code can sometimes get troublesome.

---

### Post by Metaljaz on 2009-01-29
Please take a look at these post. The instructions posted by Ubuntu Geek can easily be cut and pasted into your terminal so that you don't have to type in all in by hand. It may all sound confusing to do yourself but give it a try. If you need help please post back.

[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

[http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860)

[http://start.ubuntuforums.org/showthread.php?t=902860](http://start.ubuntuforums.org/showthread.php?t=902860)

---

### Post by 3mb0 on 2009-01-29
> **khelben1979 said:**
> To compile it from source you do this:

sudo root
./configure
make
make install

But you can also [try this]("http://rpmfind.net/linux/rpm2html/search.php?query=madwifi&submit=Search+...") which I suspect is much easier, especially when thinking about that compiling source code can sometimes get troublesome.

embo@ubuntu:~$ sudo root
sudo: unable to resolve host ubuntu
sudo: root: command not found

:S

---

### Post by 3mb0 on 2009-01-29
Guys dont worry, i manage to get through it xD, anyone whos now looking at this thread wondering how i did, here is the answer. Type down the following:

sudo aptitude update && sudo aptitude -y install build-essential linux-headers
cd ~
wget -O driver.tar.gz [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)
tar xf driver.tar.gz
cd madwifi-*
make
sudo make install
echo ath_pci | sudo tee -a /etc/modules
sudo modprobe ath_pci

---

