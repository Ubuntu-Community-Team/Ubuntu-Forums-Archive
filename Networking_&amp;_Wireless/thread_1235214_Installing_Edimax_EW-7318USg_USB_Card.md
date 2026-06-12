---
title: "Installing Edimax EW-7318USg USB Card"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by linorics on 2009-08-08
The new Edimax Card is not plug in play by default due to some device name changes. So after talking to the community and no thanks to Edimax support I got it working. So here are the steps I took to install it.

FYI:Sorry if the English is bad, I made this after 2hr's of sleep. 
[B]
[COLOR="Red"]First:[/COLOR] Make sure you have the new type of card.[/B]

```
lsusb | 7318
```

You should end up with a line that reads;

```
Bus 002 Device 002: [COLOR="Red"]ID 7392:7318[/COLOR]
```

**[COLOR="Red"]Second:[/COLOR] Downloading the drivers.**

Open a web brower and go to [http://sourceforge.net/projects/rt2400/files/](http://sourceforge.net/projects/rt2400/files/)

click on "rt73-cvs-daily.tar.gz" and save it to your desktop.

**OR**

```
cd Desktop/
wget http://downloads.sourceforge.net/project/rt2400/Final%20software%20release/rt73-legacy-final-cvs/rt73-cvs-daily.tar.gz
```

**[COLOR="Red"]Third:[/COLOR] Extract and edit.**

```
tar -xzvf rt73-cvs-daily.tar.gz
cd rt73-cvs-2009041204/Module
gedit rtmp_def.h
```

press ctrl+f
type in /* Ralink */
add the following line   {USB_DEVICE(0x7392,0x7318)},\
save and close

**[COLOR="Red"]Fourth:[/COLOR] Compile and install**
Make sure you have your build tools installed

```
sudo apt-get install build-essential linux-headers-`uname -r`
sudo make

```

If there were no errors your good to go.
To find out which kernel your using type in uname -r

```
sudo cp rt73.ko /lib/modules/YourKernel/kernel/drivers/net/wireless
sudo depmod
sudo modprobe rt73

```

Reboot your machine then the card will be Plag and play.

---

### Post by breephd on 2009-08-10
i am trying this right now. thank goodness you posted this. i just wasted the full day trying to get this to work. i was in the wrong forum posting. and i got an email with the pdf that doesn't work from edimax HQ. 
 
so far, i am now able to open and run "wifi radar" - i was not able to run that before. and in my device manager - the usb is recognized. only problem is that i tried to connect and everything froze! so now i just have to force quit some things and reboot. and will try again. 
 
thanks for posting all of this. now, if i had only found this post 12 hours ago....
 
ps: i rebooted. and the wifi now works.  thanks for this post.  i have one problem and that is that my "wicd network manager" doesn't see wireless networks.  but my "wifi radar" does.  so i am using wifi radar to connect.  is wicd really just ofr wired connections i wonder?  
 
also note to other newbies...  i was searching for this type of thread in the "installation forum" mistakenly thinking it would be the whole site... so lesson is to search in the forum that corresponds...

---

### Post by carroll.ray on 2009-08-27
I followed the instructions, and was able to get the card up and running.  However, WPA encryption is apparently not supported by this particular setup.  Any suggestions on getting WPA up and running?  Time to search the forums.  <G>

---

