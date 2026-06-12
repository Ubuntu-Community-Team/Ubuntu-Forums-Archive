---
title: "Wifi in Ubuntu Studio 10.04"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by wbm on 2010-05-31
Hello, I can't seem to get my wifi connection working on my Compaq laptop using Ubuntu Studio 10.04.

The Wifi is working as I can connect from my Mac laptop.

Using Wifi Radar on my Compaq laptop I can see all my neighborhood wifi routers. I take this to mean that my wifi modem works fine and I just don't use correct settings.

My home router is "hidden", meaning broadcast SSID is off. Again, on the Mac laptop I enter my network name, password and it works.

How do I do that in Ubuntu Studio? Where do I start? Wifi Radar seems to have lot's of options and under Network connections/Wireless I am not sure what to put.
I have it so far:

SSID: name of my home network
Mode: ??? Ad hoc or infrastructure?

BSSID: what is that?
MAC address: do I need to put something there? Should't it autofill?
MTU: ?

Wireless Security"
I chose WPA & WPA2 Personal (as on the Mac)
Password: I put my Wifi password


I don't even see in my panel an option to choose a network connection like e.g. in Ubuntu (non studio) version.

---

### Post by PetteriP on 2010-07-18
In my Ubuntu Studio 10.04 installation the Network Manager was also missing from the panel and I could not set up wireless connections - I couldn't even see any wireless connections in Network tools or, well, anywhere. Laptop wireless seemed to be on, judging by the lighted icon on keyboard. 

NetMan got set up with the following terminal commandeering:
1. apt-get install network-manager-gnome
2. /etc/init.d/dbus restart
3. Open the file
/etc/NetworkManager/nm-system-setting.conf
and set
managed=true
4. NetworkManager --no-daemon

Network Manager appeared on panel with these steps - essentially a compilation of related info from a few sources - and then I could proceed setting up the wireless like "e.g. in Ubuntu (non studio) version".

Hope that does it for you, too, mate!

Sources:
[http://ubuntuforums.org/showthread.php?t=1054662](http://ubuntuforums.org/showthread.php?t=1054662)
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)
[http://ubuntuforums.org/showthread.php?t=1098921](http://ubuntuforums.org/showthread.php?t=1098921)

PS: Sorry for the late answer, I just recently upgraded to Studio 10.04...

---

### Post by wbm on 2010-07-19
Thank you for the follow up. Much appreciated.

---

### Post by ytsurk on 2010-08-02
great help .. thx

moved to studiooh too, lovely  :-({|=

just .. a lil thingy ..,
the nm needs to be started everytime manually,
what is wanted .. - regarding the mentioned conflicts with audio,
i guess there's a reason for not automatically installing it ..

i added now a application in terminal to the panel
with the command
> sudo NetworkManager --no-daemon
and a nice icon ..

is there a nicer way ?

---

### Post by PetteriP on 2010-08-02
Hi,

Mine starts automatically now so I haven't had the need to wiggle it much further.
I'm a kind of not-so-expert on core Ubuntu manipulation but there is an easy way for you to add that command line to the start-up scripts and vóila - NM is on from the get-go! Check elsewhere on the forum how to accomplish that, it's a file somewhere where you just add that line.

But hey!
What are these > mentioned conflicts with audio ???
I got some probs now with Jack being all jacked up but guess I need to go to other topic on that...

---

### Post by ytsurk on 2010-08-03
hmm ..

for wireless it now started at its own too, this morning ...
wired i dunno so far ;)


here more info about the leave out, OR bug ..:
[http://www.mail-archive.com/ubuntu-studio-devel@lists.ubuntu.com/msg02286.html](http://www.mail-archive.com/ubuntu-studio-devel@lists.ubuntu.com/msg02286.html)

taken from here:
[http://ubuntuforums.org/showthread.php?t=1525705](http://ubuntuforums.org/showthread.php?t=1525705)

---

