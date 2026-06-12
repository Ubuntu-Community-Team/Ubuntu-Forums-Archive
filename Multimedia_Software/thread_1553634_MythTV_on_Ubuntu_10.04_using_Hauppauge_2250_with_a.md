---
title: "MythTV on Ubuntu 10.04 using Hauppauge 2250 with analog firmware and drivers"
date: 2010-08-15
forum: Multimedia Software
---

### Post by joama on 2010-08-15
Hello everyone, this is our first post.  My wife and I are trying to get  MythTV working with the hauppauge 2250. We have gotten the digital  channels working previously but most of our cable channels are still  analog so we're trying to use new analog drivers and firmware from  Steven Toth. So far, a week of working on it and still no luck. Any help  would be greatly appreciated. Below we've documented our latest attempt  starting with a clean install in the hopes that it would evolve into a  guide to help anyone else with the similar problems. It is already written like  a guide out of optimism :smile: but be warned, it doesn't end well.   
[LIST=1]
[*]Start with a CD install of Ubuntu     Desktop 10.04 here:
     [http://www.ubuntulinux.org/desktop](http://www.ubuntulinux.org/desktop)
     we used the Ubuntu 10.04 Desktop     amd64.
[LIST=1]
[*]Partitioning as follows:
/boot 1GB primary ext4
swap 4GB primary
/ 995GB logical ext4
[*]This is just what we did, it has         nothing to do with getting the hardware working.
[/LIST]
 
[*]Update the Kernel to 2.6.34
[LIST=1]
[*]Go to here :         [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/")
[LIST]
[*] If             you have amd64 (like we do) download and install in this order:[URL="file:///home/jam/Desktop/Install%20MythTV5.html"]
[/URL]linux-headers-2.6.34-020634_2.6.34-020634_all.deb
linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb
linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb[URL="file:///home/jam/Desktop/Install%20MythTV5.html"]
  [/URL]
[*]If             you have intel download:
linux-headers-2.6.34-020634_2.6.34-020634_all.deb
linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb
linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
[/LIST]
 
[*]Install in order using
[LIST]
[*]sudo dpkg -i filename
[/LIST]
 
[*]reboot.
[/LIST]
 
[*]Install updates using update     manager or
[LIST=1]
[*]sudo apt-get update
sudo apt-get upgrade
sudo reboot
[/LIST]
 
[*]Install 2250 firmwares
[LIST=1]
[*]In a terminal type :
[LIST]
[*]wget             [http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw)
[/LIST]
 
[*]Type:
[/LIST]
 
[/LIST]
 
[LIST=1]
[*]
[LIST=1]
[*]
[LIST]
[*]sudo cp *fw /lib/firmware
[/LIST]
 
[/LIST]
 
[/LIST]
 
[LIST=1]
[*]Compile and Install saa7164-v4l     drivers
[LIST=1]
[*]Type:
[/LIST]
 
[/LIST]
 
[LIST=1]
[*]
[LIST=1]
[*]
[LIST]
[*]hg clone             [http://kernellabs.com/hg/~stoth/saa7164-v4l]("http://kernellabs.com/hg/%7Estoth/saa7164-v4l")
[/LIST]
 
[/LIST]
 
[/LIST]
 
[LIST=1]
[*]
[LIST=1]
[*]Type:
[LIST]
[*]cd saa7164-v4l
[/LIST]
 
[*]Type: (this is to get some         applications that will be needed)
[LIST]
[*]sudo apt-get install mercurial             libncurses5-dev
[/LIST]
 
[*]Type: (note: this will take a         while do not panic!)
[LIST]
[*]make CONFIG_DVB_FIREDTV:=n
[/LIST]
 
[*]Type:
[LIST]
[*]sudo make install
[/LIST]
 
[*]Type:
[LIST]
[*]sudo reboot
[/LIST]
 
[*]You can check if the driver is         working by typing in the terminal:
[LIST]
[*]dmesg | grep saa7164_
[/LIST]
     
[/LIST]
 
[*]Installing MythTV:
     This will install MythTV pakage and     the backend master
[LIST=1]
[*]In a terminal type:
[LIST]
[*]sudo apt-get install pwgen
[/LIST]
     
[/LIST]
 
[/LIST]
 
[LIST=1]
[*]
[LIST=1]
[*]
[LIST]
[*]sudo apt-get install             mythtv-backend-master mythtv
[/LIST]
 
[/LIST]
 
[/LIST]
 
[LIST=1]
[*]Update MythTV:
     Update by going to :     [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)     and clicking on Activate Auto builds. Follow the instructions there.
[*]MythTV Setup:
[LIST=1]
[*]In a terminal type:
[LIST]
[*]mythtv-setup
[/LIST]
 
[*]Go to General and set the         frequency table to us-cable. Hit next until finish.
[*]Go to Capture card setup choose         the Analog V4L capture card for the card type and don't change         anything else then press finish.
[*]Go to capture card setup again to         add the second tuner, here we have to change the video device to         /dev/video1 then press finish.
[*]If you don't have an account with         SchedulesDirect.org already we advise you to make one, they have a 1         week free trail.
[*]Go to video sources, type what         ever you like in video source name. We choose SD Analog. Type in         your user ID and password and then choose your lineup (more on that         later). Change channel frequency table to us-cable.
[*]Go to input connections. Start         with choosing the first connection that says (tuner). Choose a         display name, we used Tuner1, choose your video source in our case         SD Analog. Then finally press “Fetch Channels from listing         source”. You will now that it worked when starting channel         changes from (please inter a channel number) to 2. Click through to         finish
[*]Do the same for the 2nd         tuner, this time you will not need to press the fetch channel         button.
[*]Hit Esc twice to exit the backend         setup.
[*]Click yes on running the         mythfilldatabase this will take a little bit of time to populate         the guid.
[/LIST]
 
[*]Start up MythTV front end.
[*]Go to Watch TV. This is where it     crashes and after a while shows the following message:
     Could not connect to the master     backend server -- is it running? Is the IP address set for it in the     setup program correct?
[/LIST]


PS. The IP is set correctly to localhost, and user mythtv can connect to mysql using the password. Also the backend status in mythweb looks fine, so we know it is connecting to the database as well.

PPS. Sorry about the formatting and numbering problems, this was pasted in from an odt

---

### Post by dnobes on 2010-10-20
Several of us are having this same issue...  But there is a more active/up-to-date thread going on here:
[http://ubuntuforums.org/showthread.php?p=10003300#post10003300](http://ubuntuforums.org/showthread.php?p=10003300#post10003300)

---

