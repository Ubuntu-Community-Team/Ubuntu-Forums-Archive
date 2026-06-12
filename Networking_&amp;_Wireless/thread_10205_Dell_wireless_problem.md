---
title: "Dell wireless problem"
date: 2005-01-05
forum: Networking &amp; Wireless
---

### Post by ovrundr on 2005-01-05
Have a problem with my dell laptop wireless. I have it working with the ndiswrapper and windows driver. In fact, I'm using it now. The problem is after reboot I have to reset the network with the following commands.

1> bring up the Network Setting app and Deactivate the wlan0 interface
2> go to a root window and run:
   iwconfig wlan0 key open xxxxxxxxxxxxxxxxxxxxxxABCD
3> go back to the Network Settings app and activate the wlan0 interface

After this the network works fine.

I think the problem has to do with the restricted/open option, but I don't know 
how to set it to open by default. Can someone tell how to do this or how
to deactivate/activate the interface and I'll just run a script at boot.

Not sure if it related, but it takes about 2 minutes to configure the network 
at boot up. I have the hard wire interface set to not activate when computer 
starts.

Thanks for any help.
Rick

---

### Post by celtic_saint on 2005-01-06
Check your /etc/network/interfaces file. It has the config settings for your wireless adapter (at least my config is that way). You'll see your essid, wep key, and other settings. I am now researching what the config description is for that file so I might configure multiple boot options to connect any WAP instead of having to reconfigure manually whereever I go.

---

### Post by ovrundr on 2005-01-06
Well here is what is in my interfaces file.

#######################
# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp
name Ethernet LAN card

iface wlan0 inet dhcp
name Wireless LAN card
wireless_essid linksysWLan
wireless_key xxxxxxxxxxxxxxxxxxxxxabcde

auto wlan0
########################

not sure what I can add. Where can I find the documentation for
this so I can try adding other config options?

Thanks

---

