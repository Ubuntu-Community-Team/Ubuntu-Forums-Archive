---
title: "beginner netgear question"
date: 2006-01-13
forum: Networking &amp; Wireless
---

### Post by lolacaust on 2006-01-13
hey i'm just starting out in linux and i'd like to hook my computer running ubuntu(5.10) up to my wireless router using a NETGEAR wg111t wireless usb adapter.

i've looked around online and checked out some tutorials for using ndiswrapper to install the .inf drivers from cd and website. i've done this a few times in a few different ways making sure the .sys files were in the same directory. however when i do a 'sudo ndiswrapper -l' to check on the drivers they say the following:

athfmwdl driver installed, hardware present
netgear11t driver installed

nothing...

i'm assuming that the process isnt working because there is no "hardware present" next to the netgear11t driver but i have no idea on how to make it happen.

i've heard something about ndisgtk and how you can get it from synaptic.
would this help me? and if it would, how do i get it onto my computer and installed if there is no way to hook the computer up to the internet any other way than wirelessly? i know that it would probly be cake to get it off synaptic if i had an existing internet connection but i don't.

please help! thanks.

---

### Post by spd106 on 2006-01-13
To get ndisgtk, navigate a browser to [http://archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/](http://archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/)
then download the ndisgtk.deb file.

Transfer this to your machine and open a terminal.
cd to the directory where the file is and run **sudo dpkg -i filename.deb**.

It only depends on python and python-gnome2, which should already be installed I think. You might want to get those as well to save an extra journey.

---

### Post by irw on 2006-01-13
Have a look [here]("http://ubuntuforums.org/showthread.php?t=98709&") - this got me going with the same usb adaptor. :D 

My problem is now that I can connect without encryption, but if I try to run with WEP, it won't connect. :confused:  I'm still searching the fora to find a solution to that one.

Ian

---

### Post by lolacaust on 2006-01-13
thx for the links guys. :) i'll try'em right away.

---

### Post by IanM39 on 2006-01-13
Hi all,

I have the same problem connecting with my netgear wg111v2 usb adaptor.

I followed all your instructions installing ndiswrapper and ndisgtk and have installed my xp drivers.

When I type in the sudo ndiswrapper -l command I get an output of:
net111v2  driver installed  hardware present.

Hwever, when I go to system - admin - networking, it doesn't show a wireless connection, just ethernet eth1, ethernet eth0 and modem.

How can I get it to show wireless connection?

I really appreciate the help as I've been trying to get internet connected for a week without success.

Many thanks

---

### Post by lolacaust on 2006-01-13
well i tried and was at least successful in getting ndisgtk started

this made the installation process for the drivers easier but i still get the same end result.

the athfmwdl driver is present with hardware detected but the netwg11t driver can't detect the hardware and it doesn't show a wlan0 anywhere.:( 

i tried a dmesg|tail and it looked to me like it wasnt loading the drivers correctly. i dont know what more to do. :sigh:

---

### Post by trubblemaker on 2006-01-13
[QUOTE=IanM39]Hi all,
When I type in the sudo ndiswrapper -l command I get an output of:
net111v2  driver installed  hardware present.

Hwever, when I go to system - admin - networking, it doesn't show a wireless connection, just ethernet eth1, ethernet eth0 and modem.

[/QUOTE]

do you have 2 network cards and a wireless card?  my computer has my wireless card as eth1.

did you try ```
modprobe ndiswrapper
```

look over the [trouble shooting howto]("http://www.ubuntuforums.org/showthread.php?t=87643") it might help

---

### Post by ORF1000 on 2006-07-29
I found the WG111T needs ndiswrapper 1.10 or higher.  That means download and install the latest stable from source, not synaptic and the Ubuntu repositories.  [I got great results following these instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").  It's not that hard.  Go to step 4. Also, you need both drivers; athfmwdl.inf and netwg11t.inf.  Install with the command line (per instructions) not gtk.  Even with everything working, it will show hardware installed for only one driver, not both.

---

