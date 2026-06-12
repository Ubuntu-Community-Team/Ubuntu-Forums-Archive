---
title: "Connecting PS3 to Ubuntu"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by Funkydonut5000 on 2009-04-14
Does anyone know how to properly connect a Playstation 3 to Ubuntu?  For those with PS3's, you'll notice an icon in the XMB labeled "search for media server".  As expected, when I clicked on this options, no server was found.

I would like to able to share music and pictures (pictures so I can bore people to death with modern day slide shows).

Does anyone know what needs to be done in Ubuntu to make this possible?  I'm still fairly new to Ubuntu.

Thanks.

---

### Post by madmaxo on 2009-04-14
quick google search reveals:

[http://www.freesoftwaremagazine.com/columns/upnp_mediatomb_ps3_and_me](http://www.freesoftwaremagazine.com/columns/upnp_mediatomb_ps3_and_me)

[http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04](http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04)

first link looks better

---

### Post by Funkydonut5000 on 2009-04-14
Eeeexxxxcellent.  Cheers bro.

---

### Post by static0verdrive on 2009-04-16
OK Here's what I use: uShare

```
sudo apt-get install ushare
```

Then you edit /etc/ushare.conf (or) dpkg-reconfigure ushare

Last but not least, if you want it to be running any time your ubuntu/kubuntu box is up, you need to do the following (otherwise login and type "ushare -D"):

```
sudo update-rc.d -f ushare remove
sudo mv /etc/init.d/ushare /etc/init.d/ushare.sh
sudo update-rc.d ushare.sh defaults 50
```

More details and Special thanks (Merci!!) to [http://doc.ubuntu-fr.org/ushare](http://doc.ubuntu-fr.org/ushare)

---

### Post by Funkydonut5000 on 2009-04-17
I setup Mediatomb, made a few small tweaks to the xml file and it works like a charm.  Thanks everybody.

---

### Post by static0verdrive on 2009-04-24
I'm now trying mediatomb and was curious: Anyone get it to be running on bootup without having to log into a user and run the command?

---

### Post by Keithhed on 2009-04-25
I'm fairly new to using Ubuntu, but from what I gather you need to be logged in to access data on the computer.  When you log in it is granting access.  No log in, no sharing.

---

### Post by Drenhead on 2009-04-25
Ushare and Mediatomb work, but I found ps3mediaserver to be the easiest to set up and the one that works best.

[http://code.google.com/p/ps3mediaserver/](http://code.google.com/p/ps3mediaserver/)

---

