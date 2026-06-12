---
title: "Help. Ubuntu is seeing double servers."
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by darthpenguin on 2009-05-30
I use netatalk and avahi on my ubuntu machine to seamlessly serve files to my Macs on my home Network. I could not connect to my afp shares on my macs from Ubuntu and I was not about to fuss with samba. I turned on "Remote Login" on my Macs to experiment with ssh and discovered to my joy that not only could I connect to my macs from Ubuntu, but they show in the network browser in Nautilus. Hooray! Remote shares mount as "sftp on macname.local". So not afp but it works for me. The interesting this is, when I upgraded to 9.04 the network browser shows duplicates of each server. They each work fine and mount the same way so why is Ubuntu seeing double? It is a bit of an eye sore. Any ideas?

[IMG]http://lh3.ggpht.com/_9hZSzbmspo0/SiHF-i-H5wI/AAAAAAAAACQ/sIjpLEaKqOI/s800/Screenshot.png[/IMG]
note that Miracle Max in a LAN lazerjet and Westly is my Apple Time Capsule. Only my Mac Mini and MacBook doing this.

Ultimately I would like Ubuntu to mount mac shares as AFP in the /media directory so they appear as drives on the desktop when mounted just like Leopard works.

---

### Post by darthpenguin on 2009-06-02
::Bump::

I have also noticed that if I unmount (or disconnect) from the sftp share I can not mount it again unless I close my session and log in again. I get an error saying *Could not display "sftp://Indigo.local:22/". The file is of an unknown type* for example.

I don't need to share by sftp. If there is a way to mount afp shares from network:// in Nautilus that would be even better. I refuse to share with samba if for no other reason I hate seeing the ugly BSOD Window's share icons on my Leopard machines. Also if I can conect Ubuntu to my mac servers via afp then all the sftp instantness in network:// must be gone (yet I cannot turn off "Remote Login" on my macs as I need to ssh into them from time to time.)

I know it sounds confusing. If anyone can help me get ubuntu seemlessly integrated into my Apple network I would be forever in your debt.

Thanks,

---

### Post by darthpenguin on 2009-06-02
Update:

I set #enable-dbus=yes to enable-dbus=no in /etc/avahi/avahi-daemon.conf

Now Nautilus doesn't display anything in Network:// Vinagre isn't displaying remote desktops (though I can connect to vnc by typing the host name) and my Ubuntu desktop's vnc is not broadcasting to my Macs. 

This means that the problem is somewhere in avahi-daemon as that is the program finds and broadcasts network services (like bonjour)

so how can I get avahi to find and display only one instance of sftp per server?

---

