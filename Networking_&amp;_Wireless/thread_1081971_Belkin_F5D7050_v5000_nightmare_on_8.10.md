---
title: "Belkin F5D7050 v5000 nightmare on 8.10"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by opensourcederry on 2009-02-27
Hi all,

Kubuntu 8.10

I had a working Belkin F5D7050 usb wireless dongle on Kubuntu 8.10 and gave it to a relative who has just installed Ubuntu 8.10

So I buy myself a new Belkin F5D7050 usb wireless dongle and the system recognises it ok and it gets an ip address from my router, but that is about it.

I cannot perform no other network activity whatsoever.  I cannot ping the router.

After digging about it seems that the latest batch of Belkin F5D7050 are actually Belkin F5D7050 **v5000** and are based on a **Ralink RTL8187b** chipset which is different from earlier version of the dongle.

I understand the 8.10 kernel has rtl8187 suppport built in whic is why it can see the dongle  but it does not really recognise the rtl8187b which is why it is likely I cannot do anything.

Has anyone got successfully got this dongle/chipset working on 8.10 and if so what's the process?

Cheers,

osd

---

### Post by Mordac85 on 2009-02-27
I think you could modprobe rt73usb, but there's already a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108264") for that so I don't know if it would resolve your issue.  Worst case, you could fall back to ndiswrapper until it gets cleared up.  Is there a bug report for this driver?  I didn't find one, but that's (usually) the only way the developer's know where the problems are.

---

### Post by opensourcederry on 2009-02-27
Hi all,

Got this working eventually.  Followed this thead but with a few changes ie the other post was for xbuntu and mousepad etc, changed it for Kate etc.

Thanks to James_vanb

[http://ubuntuforums.org/showthread.php?t=745655](http://ubuntuforums.org/showthread.php?t=745655)



Here's the steps for 8.10

As 8.10 recognizes the dongle, config as normal as if it's going to work.

Reboot but Unplug adapter before you re boot.

Create a folder, ie on your desktop and call it whatever you want ie thedrivers, this is just a temp location.

Get your belkin driver cd and navigate to section (varies by cd) that contains drivers, mines was among lines of systemfiles/drivers/xp

In there there should be a .inf and .sys file, mines where called BLKWGU.inf and BLKWGU.sys  Copy these to the folder you created. 



Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands 

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb


Blacklist rt2500usb and rt73usb by opening text editor ie Kate or gedit

sudo kate /etc/modprobe.d/blacklist -- for Kubuntu
sudo gedit /etc/modprobe.d/blacklist -- for Ubuntu


add the following to end of list:

blacklist rt2500usb
blacklist rt73usb

Save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

Open terminal and navigate to folder you created earlier  ie /home/mickymouse/Desktop/thedrivers

Now install the driver you just copied with the following :

sudo ndiswrapper -i thefilenamewhateveritis.inf (whatever it is named on cd, the .inf maybe .INF uppercase)

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo kate /etc/modules  (for kubuntu)
sudo gedit /etc/modules  (for ubuntu)


Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot


Dongle should work, mines just did, I think the key is to config outside of ndiswrapper all the wep stuff etc and ndiswrapper just picks this up.

Any problems or new findings etc please post on this thread.

cheers.

osd

---

