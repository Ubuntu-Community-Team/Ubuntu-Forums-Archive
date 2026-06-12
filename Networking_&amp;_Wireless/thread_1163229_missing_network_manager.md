---
title: "missing network manager"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by jazzen on 2009-05-18
I'm a super n00b with ubuntu in general, so sorry if this a silly question.

I have installed 9.04 a couple of months ago, and everything was running smoothly, except the wireless signal strength wasn't as strong as it was when I was running XP on the same machine from the same location, so I decided to try and fix it.

First I installed the linux-backports-modules-jaunty module, then WICD using apt-get.  After rebooting, the WICD interface reported there were no available wireless connections.  So I uninstalled it using the gui add/remove.

Now, I have no network manager at all.  I'm plugged into a wired port and that isn't working either.

I'm running on a Thinkpad T43 laptop. When I run lshw -C network, it lists my interfaces but reports "*-network DISABLED".  The wired is a Broadcom BCM5751M, the wireless Atheros AR5001X+.

Before I broke things, there was an entry under System > Preferences > Network and now it's gone.

Help? :confused:

---

### Post by darsie on 2009-05-18
The WICD install removes Gnome Network Manager, so maybe a stupid question, but have you tried entering the following in the terminal?

```
sudo apt-get install network-manager network-manager-config
```

---

### Post by jazzen on 2009-05-18
It tries to connect to the internet to install the packages, but I don't currently have any way to connect to the internet from the laptop.

---

### Post by darsie on 2009-05-18
Sorry, should have thought of that.

Assuming you can't plug it in to your router/modem with an ethernet cable. The alternative is to add your Ubuntu installation CD as a source:

1. Insert your installation CD

2. System->Administration->Synaptic Package Manager

3. Settings->Repositories

4. Check the two CD-ROM boxes at the bottom, and uncheck all the other repositories. Close.

5. Press reload at the top left of the window.

After this, try installing again. After you've tried, don't forget to reset your repositories to their original settings.

---

### Post by jazzen on 2009-05-18
Darsie you mentioned 'two CD-Rom boxes'; I only have one "Cdrom with Ubuntu 9.04"

Even though I've unchecked all the sources under "downloadable from the Internet", when I close then click reload I get a bunch of messages 'failed to fetch [http://ca.archive.ubuntu](http://ca.archive.ubuntu)...'.  The ubuntu CD is in the tray.

Then when I try to install with apt-get, it says "Package network-manager is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source"

I have a feeling that installing WICD marked the package as 'obsolete'.

---

### Post by darsie on 2009-05-18
> **jazzen said:**
> 
Then when I try to install with apt-get, it says "Package network-manager is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source"


Try:
```
sudo apt-get install network-manager-gnome
```

---

### Post by jazzen on 2009-05-18
I forgot to put in the last post that both commands result in the same message.

---

### Post by darsie on 2009-05-18
> **jazzen said:**
> I forgot to put in the last post that both commands result in the same message.

Sorry if I'm asking the obvious, but was it definitely *network-manager-gnome* and NOT *network-manager-config* that you tried to install?

---

### Post by jazzen on 2009-05-18
Dont worry about whether suggestions might seem obvious, as I said at the outset I'm a total Linux noob.

Yes, both commands result in the package not found message. I didn't try the network-manager-config command.

---

### Post by jazzen on 2009-05-18
Anyone else have any ideas I can try?

Update: since last night, I decided to back up my data and do a fresh re-install so everything is working again.  But I still have a question: can anyone tell me how I can boost my wireless signal?  I have no problems connecting to my access point, but the signal strength usually reports about 60-65%, where I was getting an 'excellent' connection with my XP installation.

---

