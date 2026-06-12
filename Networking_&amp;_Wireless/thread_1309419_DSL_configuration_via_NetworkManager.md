---
title: "DSL configuration via NetworkManager"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by abhilash82 on 2009-11-01
I am currently trying out ubuntu 9.10 KK using Wubi and everything works great inclunding the boot-up speed even though the installation is using Wubi.

The only problem I have as of now is my DSL configuration via the NetworkManager applet which does not work the way I had configured in 9.04. Having said that I am able to connect to the internet by running pppoeconf everytime from the terminal. I do not prefer using this method and would like to use the Network Manager to connect to the internet.

I have attached the --no-daemon log of NetworkManager along with its configuration file. I have also attached the interfaces file.

---

### Post by Iowan on 2009-11-01
Do a quick SEARCH for "DSL". There are several threads... [some]("http://ubuntuforums.org/showthread.php?p=8213343#post8213343") are showing workarounds - and an update has reportedly been released. Since I upgraded to DSL not long ago, it would certainly be a disappointment if Karmic couldn't use it.

---

### Post by p1977p on 2009-11-27
[SIZE=5][COLOR=Red]Problem solved using this launchpad [Network Manager]("https://launchpad.net/%7Enetwork-manager/+archive/trunk") trunk !!!!!  :p[/COLOR][/SIZE]

---

