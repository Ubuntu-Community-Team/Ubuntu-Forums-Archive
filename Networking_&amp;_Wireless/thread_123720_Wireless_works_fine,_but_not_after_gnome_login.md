---
title: "Wireless works fine, but not after gnome login"
date: 2006-01-30
forum: Networking &amp; Wireless
---

### Post by cjaferre on 2006-01-30
I managed to configure my HP Pavillion 5330US to connect to my wireless AP.
Everything works fine.

When booting, the network is configured automatically and the clock is set with NTP normaly. 

The problem is when loggin in Gnome. I have to manually enter the Administration/Network utility and deactivate and activate the wireless connection to get it working.

Why is that? How can I configure it to connect automaticaly?

Thank 

Cassio

---

### Post by byen on 2006-01-30
just a suggestion off the top of my head..
Do you have your Connection Configuration to DHCP or a static IP address? If you are using a router why dont you try and set a static IP address and see if that helps..
Also how about installing the program "Network Manager" or "GTK WIFI applet" ? using this program gives you a small wifi applet on the taskbar (ala windows) and its pretty handy if the problem persists.
See if that helps. I see this is your first post...welcome to Ubuntu!

---

### Post by Titus A Duxass on 2006-01-31
Read the wiki about ndiswrapper, there is a section about modifying your /etc/network/interfaces files so that wlan0 is auto.

---

### Post by metalheart on 2006-01-31
I had same behaviour after installing above mentioned Network Manager application.

---

### Post by bscbrit on 2006-01-31
I have had similar problems ([http://ubuntuforums.org/showthread.php?t=122382](http://ubuntuforums.org/showthread.php?t=122382)) but all seems to be resolved now.  I agree that the network seems to be working before Gnome starts but not after if you simply use either /etc/network/interfaces or the GUI to set up your wireless NIC.  I have had to use a script (automatically invoked by /etc/network/interfaces!) but it seems reliable now.  I do not understand the mechanisms that are coming into play here but, for the time being, I seem to have a working system.

---

### Post by cjaferre on 2006-01-31
I'm avoiding the use of a "after login script".
I know I'm missing something.

I think I didn't make myself clear...
When booting, if I remember well, first, the network is configured, later on, the clock is syncronized with an internet machine. To both messages I get an OK.

Then I'm prompted to login in Gnome. As of this moment, logging in or not, the network is down.
There must be something inbetween the clock sync and the login that's messing up the connection.
To get it working again I simply have to do a "/etc/init.d/networking restart" and everything runs smooth (I supose my "interfaces" is correct, right?).

Any sugestions??

I really don't want to create a script to "reconnect" but I'm afraid that'll be the way.

Thanks to everybody,

Cassio

---

### Post by bscbrit on 2006-02-01
No, I did understand _exactly_ what you are seeing - I have precisely the same problem. I am trying to determine what is happening between the ntp syncronisation (which works fine and proves the network) and the start of GDM by which time the network can be down.

I have overcome this by using a script - but it is run by my interfaces file and by the time I log on everything is working fine.  HOWEVER, I do not understand the mechanism that is causing this fault.  There should be no difference between the effect of commands being run directly by /etc/network/interfaces or by a script invoked by /etc/network/interfaces - but there is, I just don't know why.

Secondly, my network is OK if started from a reboot but, when I have a working network if I then type 'sudo ifdown wlan0' followed by 'sudo ifup wlan0' my network never recovers.  It should, but it doesn't.  The network can only be started during the reboot sequence.  So that suggests that something that is being invoked by the ifdown command is changing a setting that is not be corrected by the ifup command.  I'm still puzzling over this.

I'm stripping down a spare box of all unnecessary software (I have had problems disappear when I removed dhcp-client for example, despite the fact that I am not using dhcp!).  I am currently transferring the commands from my script to the interfaces file one by one to identify which one is causing the hiccup.  This is a slow business because I have to reboot between each change - remember I cannot get the network to kick into life by using ifup or networking restart.

When (If!) I find out anything that is of significance / interest I will come back to this thread to let you know about it!

[Windows might be plug and play and use, but I learn so much more by using linux! :D ]

---

### Post by cjaferre on 2006-03-02
bscbrit, I'm  having trouble even using a script.

As you mentioned you have "partialy" solved the problem, would you mind in posting here your solution?

I can't figure out how to make things work!

Thanks a lot!

Cássio

---

