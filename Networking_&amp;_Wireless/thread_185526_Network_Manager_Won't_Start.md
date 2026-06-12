---
title: "Network Manager Won't Start"
date: 2006-05-31
forum: Networking &amp; Wireless
---

### Post by s31523 on 2006-05-31
I just did the upgrade from Breezy to Dapper 6.06 LTS RC last night.  The first thing I wanted to get working was Network Manager.  I went to Synaptic and found Network Manager and installed.  After that it doesn't seem to work.  I have looked on the Wiki page at [https://wiki.ubuntu.com/DapperNetworkManager](https://wiki.ubuntu.com/DapperNetworkManager) and tried everything mentioned, but still no go.
When I invoke nm-applet from terminal I get:
nm-applet: error while loading shared libraries: libdbus-glib-1.so.1: cannot open shared object file: No such file or directory

I tried looking for this in synaptic, but I can't seem to find it.  I am not sure the apt-get install Network-Manage worked right... 

Anyone got an idea?

---

### Post by dyssident on 2006-05-31
try ```
sudo apt-get install network-manager-gnome
```

when i upgraded NetworkManager, i found that nm-applet disappeared. the gui and daemon were apparently split and the gui moved to the network-manager-gnome package.

---

### Post by s31523 on 2006-05-31
Thanks for the info... But I never got a chance to run your suggestion...

On a hunch I figured at some point when I was running Breezy I may have horked up something by trying to install nm-applet/NetworkManager from source code and building the application.  So I did a file search and sure enough I found 2 copys of nm-applet, etc.

nm-applet was in /usr/local/bin and in /usr/bin.  Of course my PATH looks at /usr/local/bin first, which is the wrong bat channel wrong bat time... Anyway, after locating the correct files I renamed the old stuff in /usr/local/bin and created symbolic links to the correct files.  For those of you keeping score, should anyone else have the same weird problem, here is what I did:
sudo -s
cd /usr/local/bin
mv nm-applet nm-applet.old
mv NetworkManager NetworkManager.old
ln -s /usr/bin/nm-applet
ln -s /usr/sbin/NetworkManager 

I don't know if your suggestion in the previous post would have fixed thing auto-magically,  or if what I did was correct, but everything works and it's is sweeeeeet.  Thankfully I have  a IPW2200 card so wireless and WPA is working great.  The only sort-of annoying thing is that the first thing I get prompted with at startup is the password to my keyring.. I'll have to figure that one out, anyone?

---

### Post by s31523 on 2006-05-31
I found this link regarding keyring behavior:
[http://www.ces.clemson.edu/linux/nm.shtml](http://www.ces.clemson.edu/linux/nm.shtml)

---

### Post by dyssident on 2006-05-31
ahh, then its unlikely that my suggestion would have helped.

if i understand correctly, user installs in Ubuntu should be done to /usr, not /usr/local as the latter is reserved for root-only stuff.

that keyring popup is annoying, but nothing is as annoying as having to constantly type 'sudo'. oh the price we pay for security.

---

### Post by s31523 on 2006-06-02
I just contacted the new maintainer of PAM_KEYRING, since I couldn't install it because it needs pam >= 0.99 and he said he is about to release a new version that will be backwards compatible.  Hopefully, this will ease the keyring password prompting.  I beleive it will be secure if you keep your keyring password and login password the same, otherwise I think you need to store the keyring password in the clear, which kinda defeats the purpose of the keyring password...

Anyway, with reagrd to how things got stored on my machine, I have no idea, but I am glad I found it.. what a pain!  thanks again for the help and I will let you know how keyring goes.

---

### Post by s31523 on 2006-06-04
By the way, I got PAM_KEYRING working using the latest version, 0.8.
Check out my post here:
[http://www.ubuntuforums.org/showthread.php?t=187874](http://www.ubuntuforums.org/showthread.php?t=187874)

---

### Post by haani on 2006-06-30
i compiled network manager 0.6.3 i get this error and i dont have nm-applet in /usr/bin and network manager in /usr/sbin i have got only one copy which is in /usr/local/bin wot can i do??

```
** (nm-applet:22661): WARNING **: <WARNING>      nma_dbus_init (): nma_dbus_init() could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.18" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'

```

---

### Post by alecubero on 2006-08-05
to solve the problem posted in the last message you need to add the user who want to use NetworkManager to the group netdev, also the interfase needs to be set as auto in the /etc/network/interfase configuration file.
I solved this problem reading the info in /usr/share/doc/network-manager, there you'll find a complete explication.

---

