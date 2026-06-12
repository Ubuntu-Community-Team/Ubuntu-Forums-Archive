---
title: "[SOLVED] 8.10 Network Manger, (Help - Online with a live Disk)"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by Orfintain on 2008-12-23
My network manager says it isn't running

I tired to restart it by

kill-all nm-applet 
and  then
nm-applet &#8211;sm-disable 
# the command never finish the cursor just kept blinking

I don't know what sm is. it is the default I copied from the sessions app. 
I have tried without the -sm-disable didn't either 

I ran the following command recently to fix pidgin I don't think it was intended for 8.10 I wonder if that could have done something...?

sudo chmod -x /usr/sbin/NetworkManager

I get the error unable to resolve host a lot, the commands have worked anyway so I haven't given it to too much thought

I had been messing with my interfaces before for virtual box but I had everything extra commented out. Now it's back to the simple default (below) still no luck though

auto lo
iface lo inet loopback

---

### Post by Orfintain on 2008-12-23
If anyone has any ideas I'd love to hear them-

I have a 8.10 alternate install disk, should I try to repair how much will that reset ? (ie would i have to redo alot of the things I did after upgrade codecs nonfree ect?)

---

### Post by pdtpatrick on 2008-12-23
reinstall this package network-manager-gnome or network-manager-kde depending on the window manager you are using.
or you can download and use wicd .. its a GUI very easy to use tool. 

Have fun :)

---

### Post by Orfintain on 2008-12-23
oh duh, that worked of course 
and everything else still works

---

