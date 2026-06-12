---
title: "TP Link TL-WN727N working on Ubuntu 10.11"
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by iComputerSaysNo on 2012-01-02
Hi,

I have never used Linux before and am having great difficulties in setting up a wireless connection with my desktop PC. I have a TP Link TL-WN727N wireless USB adapter 
(the 150Mbps version) but I cannot get it to work as I can't find a driver to let Ubuntu 10.11 use it.

Can anyone help me, as a complete beginner?

Many thanks.

---

### Post by cha0s619 on 2012-01-28
Hi,

I have the same card and I used this to make it work:

> **nickbooker said:**
> Hi there.

That card needs an updated driver for its internal chipset, available  from Ubuntu's repositories, for which you'll need to connect to your  router via a wired network temporarily.

Unplug the wireless card from your machine, and connect your machine to your router with a wired network cable.

Wait a few seconds, and check you can browse to a website (e.g. [www.ubuntu.com]("http://www.ubuntu.com/")), to ensure you have a connection to the Internet.

To install the updated driver, click Applications -> Accessories  -> Terminal, and type the following commands at the $ prompt,  pressing Enter after each one and supplying your password if prompted:

```
sudo apt-get update

sudo apt-get install linux-backports-modules-wireless-generic
```Note  when entering passwords the characters you type are not echoed back to  screen, even as asterisks - this is normal Linux command-line behaviour.

When finished on the command line, type the following to close the terminal:
```
exit
```Unplug your ethernet cable.

Close all your windows and restart the computer.  This will make sure  the older version of the driver gets unloaded from memory, so the new  version can be loaded in its place.

When logged back in, insert your wireless stick.

Wait about 30 seconds.

Left-click the Network Manager icon on the panel at the top of the  screen (it will be near the left-side of the clock) and you should see a  list of available network names to connect to.

Click the one corresponding to your access point and you'll be prompted for any keys required to connect your network.

If you can't see any access points, right-click the network manager icon  and make sure the option Enable Wireless is both present and ticked.

A message will appear briefly in the top-right hand corner of your screen when the connection is established.

Try browsing to a different website to check you have a working route out onto the Internet, and you should be all set.

In future, you should just be able to plug in the device, and if it  doesn't connect to your access point automatically just left-click the  network manager icon and pick the access point from the list.

Hope this helps,

Nick

If that fails try this:

> **anewguy said:**
> Not sure if this is the one or not, but try:

sudo apt-get install linux-backports-modules-wireless-lucid-generic


See if that helps or not, or if it even does the install.

Dave :wink:

---

### Post by ReapingWildOats on 2012-02-06
I have the same card as you, this is what I did.

[http://blog.y3xz.com/post/11811814837/installing-tl-wn722n-on-ubuntu-11-10](http://blog.y3xz.com/post/11811814837/installing-tl-wn722n-on-ubuntu-11-10)

Just download the file to your windows laptop instead of using wget, transfer via usb, then cd to the location of the file and run the rest of the commands!

What's interesting is I had to do that for my older pc.  I built a new computer last week, installed ubuntu, and without even thinking about having to get the drivers, plugged in my tp-link adapter and presto, it worked.  Out of the box.  About to hop on irc and find if anyone knows why.

---

### Post by nito2721 on 2012-02-20
This worked for me. Hopefully it helps others.

[http://ubuntuforums.org/archive/index.php/t-1800178.html]("http://ubuntuforums.org/archive/index.php/t-1800178.html")

Go here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) Download this to your desktop: RT8070/RT3070/RT3370/RT5370/RT5372USB Right-click it and select Extract Here. Rename the file that's extracted to RT5370. Right-click it and select Extract Here.

Open the resulting folder and go to os > linux and use any text editor to edit config.mk. Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close the text editor.

Now, a geek's dream; open a terminal and do:cd Desktop/2011Press Tab and the remainder will fill in. Press Enter. Now do:sudo su
make
make install
modprobe rt5370sta
exit
Is your wireless working?

Props to chili555 for the solution.

---

