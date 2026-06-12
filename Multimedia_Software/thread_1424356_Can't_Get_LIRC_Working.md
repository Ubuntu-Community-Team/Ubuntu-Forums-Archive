---
title: "Can't Get LIRC Working"
date: 2010-03-07
forum: Multimedia Software
---

### Post by MiniVanMan on 2010-03-07
I'm fairly new to Ubuntu, but haven't found something I couldn't get to work until now.  

LIRC is absolutely NOT working in any way. I've tried every tutorial I could find all to no avail.

I recently just tried this one.

> > **epitaph said:**
> I, too, found the most easily discovered documentation on LIRC to be somewhat cryptic.

First, I would plug in a keyboard and mouse to simplify this whole experience until you get your remote working properly.

This is what I ended up doing to use my MCE remote on my HTPC.

(Most of the following is from [http://www.mythtv.org/wiki/Ubuntu_lirc_install](http://www.mythtv.org/wiki/Ubuntu_lirc_install) which is for a much older release of Ubuntu and MythTV, but don't worry)

First:

```
sudo apt-get install lirc lirc-modules-source module-assistant
sudo dpkg-reconfigure lirc-modules-source 

```Select the Windows MCE Remote option when it prompts.

```
sudo m-a update,prepare
sudo rm /usr/src/lirc*deb
sudo m-a clean lirc
sudo m-a a-i -f lirc
sudo depmod -a

``````
sudo modprobe lirc_mceusb2

```This may just end up being lirc_mceusb instead of mceusb2 since I believe they were consolidated at some point. Try to see which module is listed in:

```
sudo nano /etc/lirc/hardware.conf
```If you're new to nano, use ctrl+x to exit. The module should be listed where it says MODULES="".

After starting the module:

```
sudo /etc/init.d/lirc restart
```You may have to use start or stop to replace restart.

At this point, test the receiver+remote:

```
irw

```Press some buttons, it should respond. If it does, congratulations, it's "working".

Next, generate some baseline configuration files:

```
sudo apt-get install mythbuntu-lirc-generator
mythbuntu-lirc-generator

```This will give you some pretty cut-and-dry configuration files. MPlayer should work by default, and VLC requires you to enable the IR remote module. You can find this in your home directory in a folder called ".lirc". I personally use XBMC on the media center which had no quarrels with the remote.

I have some of this stuff documented in a posting on my site [(click)]("http://www.trishock.com/talky/archives/101"), but it's mostly a rehash of things I have already said.

Good luck, hope this helps.

This didn't work either.

From the second step (sudo dpkg-reconfigure lirc-modules-source) I don't get what I'm supposed to get.  I get no selection window for any kind of remote.

I've installed, and reinstalled LIRC over an over.  I've even completed a fresh new OS load.  I've tried it through the Gnome GUI, etc, etc.  

This is the first thing that has brought me to my knees so far with Ubuntu.  I'm not a quitter, but I'm really at the point of giving up on getting a remote to work.

This is the receiver I'm using.

 Bus 003 Device 002: ID 0471:0815 Philips eHome Infrared Receiver

I'm trying to get this to work with an old Tivo remote I have lying around.  Mode2 works.  The remote does communicate with the receiver.  I can't get IRW to work at all.  But then again, I can't compile any modules.    

What am I doing wrong?

---

### Post by molder on 2010-06-19
Did you get this fixed?  I am having the same problem.  I was under the impression the the MCE remotes were plug and play.  This remote is about 4 years old.  You think that it would work by now.

---

