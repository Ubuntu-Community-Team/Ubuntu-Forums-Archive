---
title: "Acer one aspire, Wifi problems"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by Oyb on 2009-01-07
Hi,

Installed Linux Mint 6.0 without any problems today. Updated and thought everything was going smoothly. (guessing it doesn't matter really if I installed ubuntu or Mint, since they are very similar) 
But when I tested out the wifi, I couldn't get a signal.. Guessing the wlan card isnt working correctly with the driver. So I tried what said on the Ubuntu 8.10 guide. 
[https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L)
Both options actually.. Doesn't work :( 

Didn't get any error messages on the athk5 option, but didn't work after restart. 

When I tried the Madwifi option, I got an error on the last command line. Something about error

wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/
make
sudo make install
modprobe ath_pci

Anyone who could help me out? Thanks

---

### Post by gettinoriginal on 2009-01-07
Both of these are wireless threads, I don't have wireless, so have not tried them. I know the 2nd says intrepid Ibex, but maybe something will be helpful  :confused:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
[http://beginlinux.wordpress.com/2008/11/01/solving-wireless-issues-with-ubuntu-810-intrepid-ibex/](http://beginlinux.wordpress.com/2008/11/01/solving-wireless-issues-with-ubuntu-810-intrepid-ibex/)

This one is about Aspire One install, but there is a section on wirless:

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by Oyb on 2009-01-07
I'm quite new on linux distros, and the first link got destroyed already at the beginning, since the wifi connection wouldnt even show when i typed the command 
lshw -C network

---

### Post by gettinoriginal on 2009-01-07
Sorry, that should be run as 
```
sudo lshw -C network
```

And don't worry about being new, we all were at one time  LOL

---

### Post by Oyb on 2009-01-07
Well I figured that out, but still didnt stand anything about wireless network. 

Though I now installed a windows driver through the mint windows wireless driver program. Now I can see the wireless network, and type in the password, but wont let me connect. Just stands there and trying to connect, and freezes up the netbook.

---

### Post by Oyb on 2009-01-07
I disabled the windows driver and tried this guide:
[http://www.linuxmint.com/forum/viewtopic.php?f=53&t=18566](http://www.linuxmint.com/forum/viewtopic.php?f=53&t=18566)

Got the same problem, can see and find the network, but can't connect to it.

---

### Post by gettinoriginal on 2009-01-07
Well, my next suggestion is to check here for [Solved] entries:
[http://ubuntuforums.org/search.php?searchid=54182541](http://ubuntuforums.org/search.php?searchid=54182541)

---

### Post by wthornhill on 2009-01-07
Oyb,

I have an aspire one running Mint 6 and followed roughly the same route as you and couldn't get wifi to work until I found this thread last night [http://ubuntuforums.org/showthread.php?t=943189&highlight=ASPIRE+ONE+WIFI]("http://ubuntuforums.org/showthread.php?t=943189&highlight=ASPIRE+ONE+WIFI")

So not too sure if I had screwed anything up trying the different drivers I did a fresh install of Mint 6, followed Nothingspecials instructions and connected first time!

Couple of things to note:

The link to Snapshots did not work for me so I googled for driver madwifi-hal-0.10.5.6-current.tar.gz  

Once your download is finished, click the tar file and Mint gives you the option to extract the file, once you have done this, open a terminal and navigate to the extracted file.

From here follow Nothingspecials instructions to compile and install the driver (last three instructions)

Hope this helps, good luck!

---

### Post by 1numchucks on 2009-03-09
I also had this problem with getting wireless on my acer laptop.  I had tried mint & other distros. I went back to Ubuntu 8.04. I had to hook up with a hard wire cable. Then I went to system--Administration--Synaptic Package Manager--then hit the reload button. On left top side of page scroll down to Meta Packages. Download     linux&#8208;backports&#8208;modules&#8208;hardy.
Reboot. I found this information in the Ubuntu pocket guide. All the work had already been done for me. 
I hope this helps for someone.

---

### Post by jarvik on 2009-03-09
Hi! I did this and work for me:

$wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz)
$tar -xzvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
$cd madwifi-hal-0.10.5.6-r3835-20080801
$sudo apt-get install build-essential linux-headers-$(uname -r)

$make
$make install
$modprobe ath_pci


not upgrade the version of the kernel, but does not work;)

bye!

---

