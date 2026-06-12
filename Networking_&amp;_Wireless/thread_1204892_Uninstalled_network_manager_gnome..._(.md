---
title: "Uninstalled network manager gnome... :("
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by potterbond007 on 2009-07-05
My network manager gnome wasn't getting any wireless networks.. it used to do it fine and it suddenly stops showing any wireless networks after i manually put in names of wireless networks.. following the advice of somebody i uninstalled network manager gnome by the command sudo apt-get purge network manager gnome.. now i cant get it back as i dont have an internet connection.. :( 
made a huge mistake.. cant install it from the synaptic package manager too without the internet connection. it shows that the network manager is still there but the gnome is uninstalled in the synaptic package manager.. Somebody please guide me with the link of a network manager gnome installation package so that i could transfer it to my computer from this one with a pen drive and install it that way.. I use Ubuntu Hardy version 8.04.2

---

### Post by computer13137 on 2009-07-05
The best thing I can think of is to add a Ubuntu Desktop CD as a source on aptitude.  If you installed from a CD it may still be a source. Unfortunately, I always remove it the first chance I get so I can use the Internet source, lol.

What you need to do is find a Ubuntu CD matching your version, then add the CD as a source. ** Insert this CD in the drive**, then do the following:

1) Open Synaptic Package Manager from the System > Administration menu.
2) Go to Preferences > Repositories.
3) The default tab will be "Ubuntu Software".  On the bottom there's an option for a CD, which is probably unchecked.  Check it.
4) Then hit close.  You will get a message that you need to reload your repositories.  Just hit close on that too.
5) Now press the Reload button toward the top left of the Snaptic window. 
6) Now try installing network-manager-gnome again.  It should install off the CD.

I never really use the CD resources, so I'm not sure this will work as expected.  (But there should almost definitely be a way to do this from the CD).  You may have to remove all the Internet sources from the list, then reload it again.  I'm also not 100% sure that network-manager-gnome  is on the CD.  I am currently on my eeePC which has no CD drive, and I have to be going now.  I'll check this thread later... either try what I've said - or could someone who knows more about the CD resources confirm\deny my solution will work?

Cheers,
Kirk

---

### Post by potterbond007 on 2009-07-05
> **computer13137 said:**
> The best thing I can think of is to add a Ubuntu Desktop CD as a source on aptitude.  If you installed from a CD it may still be a source. Unfortunately, I always remove it the first chance I get so I can use the Internet source, lol.

What you need to do is find a Ubuntu CD matching your version, then add the CD as a source. ** Insert this CD in the drive**, then do the following:

1) Open Synaptic Package Manager from the System > Administration menu.
2) Go to Preferences > Repositories.
3) The default tab will be "Ubuntu Software".  On the bottom there's an option for a CD, which is probably unchecked.  Check it.
4) Then hit close.  You will get a message that you need to reload your repositories.  Just hit close on that too.
5) Now press the Reload button toward the top left of the Snaptic window. 
6) Now try installing network-manager-gnome again.  It should install off the CD.

I never really use the CD resources, so I'm not sure this will work as expected.  (But there should almost definitely be a way to do this from the CD).  You may have to remove all the Internet sources from the list, then reload it again.  I'm also not 100% sure that network-manager-gnome  is on the CD.  I am currently on my eeePC which has no CD drive, and I have to be going now.  I'll check this thread later... either try what I've said - or could someone who knows more about the CD resources confirm\deny my solution will work?

Cheers,
Kirk

I dont have the ubuntu cd with me... :(

---

### Post by computer13137 on 2009-07-05
Dunno what to tell you.  We can't make it appear on your system, got to get it on there somehow. 

The other option I can think of is to download the .deb file from the Ubuntu repository, and throw it on a flash drive or something.   However, there may be a few dependencies that need to be installed.  I could see it quickly becoming a pain.

[i386 Package]
[http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.7.1-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.7.1-0ubuntu1_i386.deb)
[x64 Package]
[http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.7.1-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.7.1-0ubuntu1_amd64.deb)

Then try installing it by running a command such as...
```
dpkg -i network-manager-gnome_0.7.1-0ubuntu1_i386.deb
```

However, it'll probably error and say it needs like 5 more programs.  That being the case, you may still be able to get the .deb files for them from the repository manually, and do the same thing.

If you don't have a USB flash drive either, I don't know what to tell you.  We can't use willpower to make the software appear on your computer, lol.

Cheers,
Kirk

---

### Post by f.constantino on 2009-07-05
Hello,

I may have misunderstood your problem but if all you did was uninstall network manager, you can just get it back using apt-get. If you can make a wired connection to your router/modem/switch through an ethernet cable, you can still have internet without the use of network-manager. Just open the terminal and type the following:

```
sudo dhclient eth0
```

and use this connection to download network manager using apt-get.

If, however, you cannot make a wired connection and can only connect trough wireless, I believe the best aproach for a newbie in networking (don't know if you are) would be exactly what you are suggesting (cd, pen, etc.) with the required packages for the installation. If, on the other hand, you do know your way around networks, try reading this: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) to manually setup a wireless connection.

Cheers,
Fábio Constantino

---

### Post by potterbond007 on 2009-07-06
I am a bit of a newbie in networking.. :) Can somebody guide me on the packages in synaptic manager that is needed for the network gnome to be installed.. I get the error dependency is not satisfiable: libdbus-glib-1-2 when i try to install the package for network-manager-gnome_0.7.1~rc4.1-oubuntu2_i386.deb.. That is the file that synaptic manager said was the gnome package for my particular laptop.. i download this file and tranferred it to my laptop but I am getting the error.. 

I have got the network manager, netwrok manager-dev and network manager-kde and networkstatus packages already installed.. the other files needed to be installed look like network-manager-openvpn, network-manager-pptp, network-manager-vpnc and networkstatus-dev.. which among these packages should i install to take out that dependancy error being shown for network-manager-gnome???? I am an ubuntu hardy 8.04 user.. Please help!!!!!!

---

