---
title: "Can't turn on bluetooth module on my latptop"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by amrbekhit on 2009-05-01
Hello all,

I'm using Ubuntu 9.04 on my Compaq TC4200 tablet. The tablet has a built in bluetooth adapter, which I have had successfully working under Windows. However, I am unable to get it to switch on in Ubuntu.

The Wifi module and the bluetooth adapter seem to be integrated into one wireless module. There is a button at the side of my laptop that allows me to turn on/off the wireless module. In Windows, the Wifi and bluetooth drivers were installed separately and then there was a third program which allowed me to individually turn on/off the bluetooth and wireless modules. I usually had the wireless module always on and turned the bluetooth module on only when needed.

In Ubuntu, the wireless module worked straight out of the box, which was great. However, I just cannot get the bluetooth module to be switch on. I suspect that this is because before I removed Windows and installed Ubuntu, I had turned the bluetooth module off using the aforementioned software. However, I have since completely removed Windows and it's going to be a hassle to reinstall it again, just so that I can turn on my bluetooth module then remove it.

I have done some google searched around the matter and have tried a couple of command line tests without any luck.

[LIST]
[*]**sudo /etc/init.d/bluetooth status** indicates that bluetooth is running
[*]**sudo /etc/init.d/bluetooth restart/force-reload** do not solve the problem
[*]bluez is installed
[*]**lspci, lshw, lsusb** do not seem to show anything related to bluetooth, but maybe that is not unexpected as I think that by turning off bluetooth in the software, the module was literally being turned off and disconnected from whatever bus it is on.
[/LIST]

I think that the issue lies in activating the bluetooth 'killswitch'.

I've attached the output of my lspci,lsusb and lshw tests to this post.

Any ideas?

Thanks,

--Amr

---

### Post by amrbekhit on 2009-05-05
Any ideas?

---

### Post by Favux on 2009-05-08
Hi amrbekhit,

Maybe you should see if HAL sees your bluetooth.  You can install gnome-device manager-manager from Synaptics.  It's the HAL front-end gui.  It should install in Applications>System Tools.  Be sure to click on properties in View once you've started it.

Or you could look at lshal.
```
lshal>lshal.txt
```
Search lshal.txt on your desktop with gedit for bluetooth or whatever.

It's possible there is a .fdi file that is suppose to handle blue tooth.  It may not be configured to handle your blue tooth correctly.  If you find the blue tooth section(s) in lshal you may be able to fix it.  I don't know anything about blue tooth so I'm just guessing about there being a .fdi.

---

### Post by amrbekhit on 2009-05-14
Thanks for your reply Favux,

The output of lshal doesn't contain anything that directly points to bluetooth. The only thing which I think is related is the Intel PRO/Wireless WLAN Switch, but I'm not sure how to go about trying to take advantage of that.

As I mentioned in my previous post, I think that the bluetooth and wifi modules are integrated into one module. The hardware switch on the side of the laptop turns on/off both the wifi and bluetooth modules and you can individually turn each one on/off using a software driver downloaded from the HP website.

I've attached the contents of my lshal output to this post.

--Amr

---

### Post by chunky bacon! on 2011-01-29
I made the apparent mistake of turning off bluetooth once, and now I can't turn it back on, either.  

Dell Vostro V130 laptop that came preinstalled with 10.04. There is no Windows install for me to fall back on, unfortunately.  Everything was fine out of the box until I made the silly mistake of not knowing I was going to break everything simply by trying to save power.  Up until then, I had been bragging to so many friends on how nice it was for new linux distros to have everything working like it should, right out of the box.

I've installed blueman.

I've done the edit of /etc/bluetooth/main.conf RememberedPower = false

uninstalled everything bluetooth related and reinstalled.
sudo /etc/init.d/bluetooth restart
sudo /etc/init.d/bluetooth start
sudo /etc/init.d/bluetooth stop


nothing, zilch, nada.  i get the indicator, but it will forever say "bluetooth needs to be enabled." you click "enable," and get "the connection timed out."

and every bug I see that deals with it says "yes, its broken."

I guess bluetooth is just a no-go for most folks in linux.

That being said, since Ubuntu is so user friendly, there should be a huge gigantic warning the first time you try to turn bluetooth off.  Something like "YOU WILL NEVER GET IT BACK NO MATTER WHAT YOU DO.  ARE YOU SURE YOU WANT TO DO THIS?"

---

