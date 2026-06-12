---
title: "No &quot;enable wireless&quot; option"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by Samzystrange on 2011-05-06
Hi all-
I'm running 11.04 on a Compaq presario CQ56. The network dropdown menu doesn't even show "Enable wireless" as an option, which makes me think that the wireless card's driver and/or firmware isn't installed. 

The network card is a Ralink, but I can't figure out which model/chipset :-P

Here is the relevant output for lspci -vnnk:
02:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]
    Subsystem: Hewlett-Packard Company Device [103c:1636]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at 93500000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

I've tried downloading this driver from Ralink 
[LEFT][RT2860PCI/mPCI/PCIe/CB(RT2760/RT2790/RT2860/RT2890)]("http://www.ralinktech.com.tw/data/drivers/2009_0521_RT2860_Linux_STA_V2.1.2.0.tgz")
[RT2860WebUI]("http://www.ralinktech.com.tw/data/drivers/2009_0521_RT2860_Linux_STA_WebUI_v2.1.2.0.tgz")

but am enough of a noob to know I don't know what the heck to do with it now that I've downloaded it. Also, I'm not 100% sure that's even the right driver.
[/LEFT]

Help would be greatly appreciated!

---

### Post by lytithwyn on 2011-05-06
Welcome to the forums!

That particular device ID isn't listed on the pcidatabase.com website, so I can't verify for you if that's the right chipset or not.

Also the links you posted are giving me 404 errors but I was able to download the one that says "RT2860PCI/mPCI/CB/PCIe(RT2760/RT2790/RT2860/RT2890)" directly from Ralink.

When you get the source for linux drivers like this, all you have to do is compile and install them.  In this case, here are the steps I had to follow (I actually installed this on my machine)

[LIST=1]
[*] First you'll need some packages installed.  You should need build-essential and the linux-headers package for whatever kernel you're running.  If you don't know how to install those, just let me know.  I can help you with that.


[*] Download the file to /home/username or wherever you want.  Note that the compile process failed for me when I ran it from a directory that had spaces in the path (aka, something like /home/username/my drivers/ralink, won't work)


[*] Open a command prompt and enter:
```
cd /home/username
``` where /home/username is where you downloaded the file


[*] Extract the file by running the following.  The file I downloaded was named .bz2, but it was actually a gzip file, so if your familiar with tar I'm doing "z" instead of "j" on purpose.
```
tar -xvzf 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2
``` but sub in the name of the file you downloaded.


[*] Now "cd" into the directory that was created
```
cd 2010_07_16_RT2860_Linux_STA_v2.4.0.0
``` again subbing in whatever directory name you have


[*] Now we compile the drivers by doing
```
make
```This might take a few minutes and you should see a lot of commands and output scroll by.  As long as the last few lines output aren't errors (warnings are ok) then everything is fine.


[*] Now we need to install the drivers by typing
```
sudo make install
```The installation process should go a lot faster than the compile did.  If you ever need to uninstall this driver you can do it by running "sudo make uninstall" in this same directory.


[*] You can now either reboot the computer to get your new driver working, or you might be able to do
```
sudo modprobe rt2860sta
```
[/LIST]


Sorry if I've over-explained the use of the terminal, but I wasn't sure how advanced you were with this being your first post.  Just let me know if something wasn't clear or if I can help you with anything else.  Sometimes I can't get on the computer over the weekend but I'll get back to you as quick as I can.

---

### Post by andre_orwell on 2011-05-06
rt2860sta driver seemed to be included with my install of 11.04.  Try just doing the modprobe command from the above post.  Or lytithwyn, is the included version not the latest?  For me the included driver works fine except for suspend/resume.
Cheers.

---

### Post by Samzystrange on 2011-05-07
Turns out it was a Ralink 5390 card. The solution is now here:
[http://ubuntuforums.org/showthread.php?t=1751685](http://ubuntuforums.org/showthread.php?t=1751685)
Thanks to all who helped!

---

### Post by lytithwyn on 2011-05-07
Great!  Glad you got it solved!

In answer to andre_orwel's question (just in case someone with an rt2860 reads this) I'm not sure whether the driver in 11.04 is the most recent or not, or if the driver on Ralink's site is the same as the one included with the Linux kernel.  I'm actually running a vanilla 2.6.38 kernel on 10.10.

I sort of jumped the gun a bit and just assumed that if his hardware wasn't detected the driver wasn't there.  Not a safe assumption.  :P

---

