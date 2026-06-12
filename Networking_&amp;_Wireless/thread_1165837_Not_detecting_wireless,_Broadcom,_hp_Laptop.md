---
title: "Not detecting wireless, Broadcom, hp Laptop"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by Hybird on 2009-05-21
I just installed **Ubuntu 9.04** onto a separate partition and looking at the top corner I see 3 vertical signal bars with an 'x' over them. I've been reading I have to install the firmware from my Broadcom wireless adapter to make Ubuntu see the networks available if I'm correct? If so, here are my questions.

**1.)** I have the driver downloaded using my vista partition and placed it in ubuntu. It is BCMWL6.sys. Now I need to steal the firmware using bcm43xx-fwcutter. I can't connect to the net and use ubuntu to get the **bcm43xx-fwcutter** pacakge so I downloaded the i386 **deb** file from Ubuntu Jaunty utities site. Then I tried to use "sudo dpkg -i PackageName.deb to install and it fails. So how can I get bcm43xx-fwcutter? And do I need other packages installed first to make it work?

**2.)** Is my wireless card even usable under the Jaunty OS? (*See specs below*)

**Specs:**

My comp.
HP Pavilion dv9000 32-bit Os (Vista) AMD turion 64 X2 
Nvidia Graphics
Broadcom Wireless Adapter: **4321AG 802.11a/b/g/draft-n Wi-Fi Adapter**

Anything else needed just ask, and if possible list the Terminal command to get info.

**3.) **Also, if my CPU's are "AMD turion 64 X2" does this mean I could install a 64-bit version of ubuntu? I don't know which I installed.

Thanks for the help in advance, this has kept me up two nights in a row!
-Jordan

---

### Post by t0mppa on 2009-05-21
**1.)** Bcm43xx is deprecated, you should use b43. Thus you need the b43-fwcutter package. However, using these drivers you won't get draft-n working, so I suggest you try the new STA driver instead. See [here]("http://www.broadcom.com/support/802.11/linux_sta.php") for info & download.

**2.)** It should be. At the very least, I haven't seen anything that'd suggest it's not.

**3.)** That it does. Myself, I'm still running 32bit though, since I only have 4Gb RAM and never seen Ubuntu use more than 1.5Gb of it anyway. If you need heavy computing power, like scientific or graphical work, then it comes in handy, but it won't make mundane tasks (web browsing, word processing, etc.) any quicker.

---

### Post by Hybird on 2009-05-24
(Subscribing to Thread)

But I still have to download that .deb file and install it in ubuntu. That's when I get an error, I will try it again later tonight and post my results.

---

### Post by Ayuthia on 2009-05-24
The draft-n cards are not currently supported by the b43 modules at this time.  You will be better off trying to use the wl module (Broadcom STA).  You should be able to find this under System->Administration->Hardware Drivers.  The good news about this is that you do not need an internet connection to make this one work.  The only problems that you might encounter is if the b43 module is enabled or loaded, it will cause conflicts with the wl module.

---

### Post by Hybird on 2009-05-28
> **Ayuthia said:**
> The draft-n cards are not currently supported by the b43 modules at this time.  You will be better off trying to use the wl module (Broadcom STA).  You should be able to find this under System->Administration->Hardware Drivers.  The good news about this is that you do not need an internet connection to make this one work.  The only problems that you might encounter is if the b43 module is enabled or loaded, it will cause conflicts with the wl module.

Is there any chance you could elaborate on how to make this work. I checked the Sys/Admin/hardware driver and it says:

"No proprietary drivers are in use on this system"

And under the Broadcom STA which is the only listed module it says:

"This driver is activated but not currently in use"

I'm very new to Linux, so I need a lot of explanation. I really just want the internet to work so I can play around with manipulating things and not have to switch back and forth between partitions every time I need to ask a question.


Also, apparently I am running 32-bit ubuntu, because I got the i686 GNU/Linux response to "uname -a" command.

---

### Post by Hybird on 2009-05-28
Also, when I type in the "sudo iwconfig" I get the following:

lo          no network extensions
eth0      no network extensions
pan0     no network extensions

---

### Post by t0mppa on 2009-05-28
Why don't you begin by running **lshw -C network** from the terminal. If it lists your wireless with UNCLAIMED, then you have no drivers trying to associate with it and can proceed to the next step. If it's not unclaimed, but says "driver=b43-pci-bridge module=ssb" instead for instance, then run **sudo modprobe -r <module_name>** to get that module unloaded. Then make sure the interface is unclaimed, if not repeat the unload command. That way you make sure you don't have any other drivers loaded and possibly creating conflicts with the STA before enabling it.

The activated but not in use part likely refers to the driver files having been installed on the system, but not being currently loaded on the kernel. To load it, you can run **sudo modprobe wl** from the terminal. Then run **lshw -C network** again and see if the interface has the STA driver associated with it. If it is, the connection should now work properly.

If this works, you'll have to add the module(s) you possibly removed before loading wl to blacklist with **echo blacklist <module_name> | sudo tee -a /etc/modprobe.d/blacklist.conf** (*) and add wl to the list of modules automatically loaded during boot with **echo wl | sudo tee -a /etc/modules**, so you don't have to manually enable it after each reboot or shutdown.

If it doesn't, you'll have to wait for Ayuthia to reply, since the STA doesn't support my broadcom card and thus I haven't played around with it to know all its ins and outs.

*) Since you asked for a lot of explanations, here comes. The echo just outputs whatever is typed afterwards. The tee command with option -a appends the file in question by adding a line with the output given to it. The |, also known as the pipe, makes the tee command take the output from the echo command to work its magic with.

---

### Post by Hybird on 2009-05-28
Thank-you very much, I will give this a shot tonight after I get back from work. And thanks for the break down of the commands, also very helpful.

EDIT: IT WORKS!!! I'm on the interweb via my Linux partition! Thank you so much! But I still have one more question.

I saw the driver listed as the b43-pci-bridge and so deleted the module named "ssb" then installed the "wl" module, so I'm sure I did that right. Now what's this business about adding the modules I possiblely deleted? I just typed the following two lines:

[B]echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf

echo wl | sudo tee -a /etc/modules[/B]

Does this mean that in the first line I tell it to put the ssb module on a "this module is unwanted list" and the second line places the wl module in the directory with all the other modules to be loaded onto the kernel?

---

### Post by Hybird on 2009-05-31
--BUMP--

What modules do I have to load back before I blacklist the ssb module??

---

### Post by Ayuthia on 2009-05-31
You only need to make sure that the wl module is loaded (in /etc/modules) and that b43 and ssb are blacklisted.

---

### Post by t0mppa on 2009-05-31
Sorry, edits don't show up as being changed on this board, so missed that completely.

What I wrote earlier might've been slightly confusing, but the idea was: "add to blacklist all the modules you removed, so they don't conflict with wl". Like Ayuthia already stated, these would be ssb & b43, if you had b43 installed.

---

### Post by Hybird on 2009-05-31
Thanks for the help, its finally working stably.

---

### Post by reese.mitchell on 2009-06-25
Thanks so much for the help! I am running a hp pavilion dv2000 notebook it work great the only problem is my router is using wpa2 and i had to switch to wpa in order to get the wireless to work.:KS:KS:KS 

Thank you so much

Reese.Mitchell

---

### Post by stevie1989 on 2009-06-25
l'm running Kubuntu and followed the steps, running HP DV2620ca and still having issues and read up tons of tutorials and trouble shooting through Google:(
l have Broadcom's drivers for my driver and used the .exe in Windows drivers l downloaded on HP Canada website, allowed the driver too install my thumbdrive. Any help would be sweet

---

### Post by Ayuthia on 2009-06-25
> **stevie1989 said:**
> l'm running Kubuntu and followed the steps, running HP DV2620ca and still having issues and read up tons of tutorials and trouble shooting through Google:(
l have Broadcom's drivers for my driver and used the .exe in Windows drivers l downloaded on HP Canada website, allowed the driver too install my thumbdrive. Any help would be sweet
Can you help provide some information about your wireless card and which which version of Kubuntu you are using?  There are currently three different types of wireless drivers for Broadcom and some are only compatible with certain cards.  Please provide the following:
```
lspci -nn
lshw -C network
```

If you have not already done so, you might also check System->Hardware Drivers and see if you have a Broadcom option.

---

### Post by Hybird on 2009-06-26
Well it was working for a while.. then the internet went down. Now when I go to disable the ssb module and then load the wl module nothing ends up loading. And help? Maybe I blacklisted the wl module some how? I don't know.. damn Ubuntu. I was so happy with it.

---

### Post by Ayuthia on 2009-06-26
> **Hybird said:**
> Well it was working for a while.. then the internet went down. Now when I go to disable the ssb module and then load the wl module nothing ends up loading. And help? Maybe I blacklisted the wl module some how? I don't know.. damn Ubuntu. I was so happy with it.

What do you mean by nothing ends up loading?  Does an error message come up about the wl.ko is missing or is it loading and nothing is happening?

Can you post the results of:
```
lsmod|grep -e ssb -e wl -e b43
```

---

### Post by Hybird on 2009-06-26
When I first start ubuntu the ssb is still loaded. 

when I type:
lshw -s network 

I get the following in the config area of the Network Controller:
driver=b43-pci-bridge latency=0 module=ssb

So then I have to remove the ssb by typing:
sudo modprobe -r ssb

This makes it go away, then when I list the hardware again I get "UNCLAIMED" for the Network Controller. I then proceed to type:
sudo modprobe wl

And then I check out the Network Controller again and get the same "UNCLAIMED". After that I typed in the command that you gave me and I get this:

wl                        1496016      0
ieee80211_crypt       14596  1 wl

P.S. I may not respond until sunday night. Gotta leave town, thanks for the help again though.

---

### Post by Ayuthia on 2009-06-26
> **Hybird said:**
> When I first start ubuntu the ssb is still loaded. 

when I type:
lshw -s network 

I get the following in the config area of the Network Controller:
driver=b43-pci-bridge latency=0 module=ssb

So then I have to remove the ssb by typing:
sudo modprobe -r ssb

This makes it go away, then when I list the hardware again I get "UNCLAIMED" for the Network Controller. I then proceed to type:
sudo modprobe wl

And then I check out the Network Controller again and get the same "UNCLAIMED". After that I typed in the command that you gave me and I get this:

wl                        1496016      0
ieee80211_crypt       14596  1 wl

P.S. I may not respond until sunday night. Gotta leave town, thanks for the help again though.

It looks like the you were missing one step try:
```
sudo modprobe -r ssb wl
sudo modprobe wl
```If that works, before you reboot do the following:
```
sudo update-initramfs -u
```and that will update the initramfs file (it is used when the system is starting up) and add the ssb blacklist during startup.

---

### Post by Hybird on 2009-07-02
Ok, it seems to be working, hopefully indefinitely. Thanks for taking the time once again.

---

### Post by reese.mitchell on 2009-10-12
the update-initramfs -u does work in ubuntu 9.04  Thanks once again.  Has anyone tried to see if we have to do the update-initramfs for ubuntu 9.10

---

