---
title: "Installing netgear wireless drivers running from liveUSB"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kelean on 2011-04-02
I am trying to test out Beta1 from a liveUSB drive.  I have not been able to figure out how to install the drivers for my usb wireless dongle.

It is a Netgear WPN111 dongle.  I have the drivers for it.  How do I install the drivers and get ndiswrappers working.

Thanks Kelean.

---

### Post by cariboo on 2011-04-02
Isn't there a native linux driver for your device? Does it work when you run the latest release?

---

### Post by kelean on 2011-04-02
I am not currently running Ubuntu but I am running Linux Mint 10.  I have it working with Mint using ndiswrappers.  

I do not know of a linux driver for my device and would not know where to look.  I am interested in Unity and want to give it a try before I install it.

---

### Post by bennachie on 2011-04-02
Have you tried just plugging the device in and seeing whether Ubuntu recognises it? You might be pleasantly surprised.

---

### Post by RJ12 on 2011-04-02
What I had to do (I require NDISwrapper too) is to install Ubuntu, go back into Windows, and go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and download all of the NDISwrapper / ndisgtk packages.

Then I went back into Ubuntu, found the files and did a 

```
sudo dpkg -i *.deb
```
in the directory I had all of my deb files. Then I got my wireless drivers, and installed them, and restarted the computer and the wireless was working :)

It was a little advanced, but actually quite easy.

---

### Post by cariboo on 2011-04-02
I'd suggest once you are at the Natty desktop, plug in your device, then open a terminal and type:

```
dmesg
```

The output from the above command should tell you if your device has been detected properly.

---

### Post by kelean on 2011-04-02
bennachie, I tried just plugging it in and nothing happened.

cariboo907, I ran dmesg and read through it twice.  I found nothing about the wireless dongle.  I then ran lsusb and it was listed there correctly but it had no firmware installed in parentheses.

Ndiswrapper is not installed on the live cd.

Can I install Ubuntu to my computer without beining connected to the internet.  If so then I dowmload the needed ndis packeges on my Mint install and pull them over and install them with dpkg?

Thanks Kelean.

---

### Post by bennachie on 2011-04-02
Yes, you certainly can install Ubuntu without being connected to the Internet - in fact, that's often a good idea. You should then be able to transfer the requisite packages from your Mint installation as you suggest.

---

### Post by kelean on 2011-04-03
I installed Natty to my hard drive.  Downloaded ndiswrapper packages needed on Mint install.  Copied to natty and installed.  I had to reboot a couple of times but all is working fine now.

Not sure if I should mark solved or not as I could not get it to work from the liveusb.

Thanks for all of the help, Kelean.

---

### Post by bennachie on 2011-04-03
Well, I'm very glad to hear that you've been able to get around the problem, but it looks as if omitting ndiswrapper from the default installation may have been a step too far.

To some extent, this may be a result of an understandable wish to keep the size of the basic installation within the limits of a CD for those with computers unable to read DVDs. The fact that such computers probably can't run Ubuntu 11.04 anyway is less important. 

The issue, of course, becomes moot for those who want to use a live USB for installation. I doubt that you can actually buy anything less than a 2GB stick any longer, and the bargain bins tend to be full of 4GB versions. I think that Linux Mint has got the balance just right.

---

