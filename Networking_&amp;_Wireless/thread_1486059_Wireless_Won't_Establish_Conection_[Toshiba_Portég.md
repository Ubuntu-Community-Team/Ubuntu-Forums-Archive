---
title: "Wireless Won't Establish Conection [Toshiba Portégé 3505]"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by SlidingHorn on 2010-05-17
Ok...so I've been searching around and I haven't found a solution to why my wireless card won't establish a connection.  It sees available networks, attempts to connect, but fails.  I have attached results of lspci, lsusb, and (what I believe is the relevant info from...) dmesg for reference.  

This has been a problem for a while, and until I'm able to connect via wireless, I won't be able to use *buntu exclusively on this system, which is my ultimate goal here.

Any help you guys could provide would be GREATLY appreciated.

**Edit:** I forgot to mention, I'm running 10.04 LTS

---

### Post by SlidingHorn on 2010-05-19
*bump*

---

### Post by portentum on 2010-05-19
There's a lot to wade through, but [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498336") bug report may help. They start making progress around [comment 86]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498336/comments/86").

---

### Post by SlidingHorn on 2010-05-20
*bump*

> **portentum said:**
> There's a lot to wade through, but [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498336") bug report may help. They start making progress around [comment 86]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498336/comments/86").

I know it's a lot of info to sift through.  Checked out the bug report, but no luck.  

Any other suggestions, anyone? :)

---

### Post by SlidingHorn on 2010-05-21
Still no luck here :(

*Bump*

---

### Post by SlidingHorn on 2010-05-22
*bump*

Is there any more information I can provide to help someone figure this out?

---

### Post by ztrange on 2010-05-23
Well, you can find info to see if your adapter is supported here:

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

There you'll probably find compatibility info and comments about the driver needed.

Hope it helps

By the way, your lspci and lsusb don't mention any wireless adapter, are you sure it exists? Check also if it's enabled in the BIOS menu

---

### Post by SlidingHorn on 2010-05-23
> **ztrange said:**
> By the way, your lspci and lsusb don't mention any wireless adapter, are you sure it exists? Check also if it's enabled in the BIOS menu

Well, I had not noticed that...however, I ran 

```
sudo lshw -C network
```

and it did find a wireless card...maybe this could get the ball rolling:

```
*-network
[INDENT]description: Wireless LAN Card
product: Version 01.01
vendor: TOSHIBA
physical id: 0
slot: socket 0
resources: irq:11[/INDENT]
*-network
[INDENT]description: Wireless interface
physical id: 2
logical name: eth1
serial: 00:02:2d:7e:37:44
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=orinco driverversion=0.15 firmware=Lucent/Agere 9.48 link=yes wireless=IEEE 802.11b[/INDENT]
```

sudo pccardctl ident 0 shows:

```
product info: "TOSHIBA", "Wireless LAN Card", "Version 01.01", ""
manfid: 0x0156, 020002
function: 6 (network)
```

Hope this helps...will knock down yet one more small barrier to me completely ditching XP on that laptop.

**P.S.** Thanks for taking a look @ this, everyone.  I was beginning to lose hope :)

---

### Post by Rubi1200 on 2010-05-23
This may seem a bit obvious, but have you tried installing and using the ndiswrapper package?

---

### Post by SlidingHorn on 2010-05-23
> **Rubi1200 said:**
> This may seem a bit obvious, but have you tried installing and using the ndiswrapper package?

After my last post, I did some more looking and found that I'd have to try with ndiswrapper.  

I went to Toshiba's website and looked for the Windows drivers, and there were a few different options.  I hate to be such a newb, but I don't know which one to use (I don't know where the driver is on my Windows partition to pull it over).  I've looked in the drivers, driver cache, system, system32 directories, but don't see any matching files from the self-extracting archives offered on Toshiba's site.

I'm pretty bad when it comes to networking stuff, so any additional help determining where the actual driver is would be greatly appreciated...

---

### Post by linuxonbute on 2010-05-24
> **SlidingHorn said:**
> After my last post, I did some more looking and found that I'd have to try with ndiswrapper.  

I went to Toshiba's website and looked for the Windows drivers, and there were a few different options.  I hate to be such a newb, but I don't know which one to use (I don't know where the driver is on my Windows partition to pull it over).  I've looked in the drivers, driver cache, system, system32 directories, but don't see any matching files from the self-extracting archives offered on Toshiba's site.

I'm pretty bad when it comes to networking stuff, so any additional help determining where the actual driver is would be greatly appreciated...
Well I don't use Windows but I think you can get information from control panel. If I remember correctly you look under devices and look for the wireless device.
Norm

---

### Post by SlidingHorn on 2010-05-24
I'll take a look when I get home...that is, if I can convince my gf to quit complaining about the mess in my apartment.  It's a bachelor pad...it's supposed to be messy. ;)

---

### Post by SlidingHorn on 2010-05-24
Ok, so I've finally determined (kinda) the driver Windows XP is using, but it only shows a .sys file (wlluc48.sys) -- no .inf file.  Do I need both?  If so, how do I find the .inf file?

---

### Post by MiGsBPR on 2010-05-24
Hello friends, I'm having similar wireless issues aswell with my Portege 3500, along with a screen resolution issue, but that got fixed. Here is my tale.

Yesterday, did a netboot install of 10.04 Xubuntu which took forever, wireless was semi working for the install, tried accessing the mirrors but it failed each time. So I installed over ethernet. After it installed I tried apt-get to find some interfaces, doing this over wireless, I was able to get the package list back and it would give me a file size of the package, but when I tried to download and install it, it would say it failed to retrieve the package. So I was finally able to get it to download the package by rebooting with the wireless switch in the off position then when it was booted up, I turned the wireless card on, and was able to download the xubutnu desktop package over wireless and install that way.

Jump to today... I freshly installed regular Ubuntu desktop on the hdd from another laptop (the 3500 doesn't have a CD drive) and ofcourse wireless didn't work, so I'm in the same position you're in, with the same wireless product info and such that you listed aswell.

Also, I'm just trying out ubuntu on this laptop because I got it without a hdd, and without recovery CD's and I've been unsuccessful in installing windows on it for awhile (failing network install, hdd swap, and I have no supported cd-rom drive), so if you have any pointers on installing windows on here, then please shoot me over a PM or something.

---

### Post by linuxonbute on 2010-05-25
> **SlidingHorn said:**
> Ok, so I've finally determined (kinda) the driver Windows XP is using, but it only shows a .sys file (wlluc48.sys) -- no .inf file.  Do I need both?  If so, how do I find the .inf file?

Again not a windows user but 2 things you could do.

1/ search the whole of the windows C: drive for .inf files and see if one matches your .sys file.

2/ Search Toshiba site and see if you can find it there

---

### Post by SlidingHorn on 2010-05-25
@linuxonbute - I'll give it a shot when I get home.

@migsbpr - well best of luck...we'll get this nailed down eventually, lol.

---

### Post by SlidingHorn on 2010-05-25
Ok...so I searched my system, and there is no matching .inf file.  Also, I downloaded all of the available archives from Toshiba's website...and (just my luck) none of them had the wlluc48.sys file within them.  Assuming I *must* not have the correct driver, I told Windows to update the driver.  It told me that there was not a better match for my card...

Just so you all know I'm not entirely crazy, I'm attaching a screen shot showing that Windows is only using the one .sys file without an .inf file to accompany it.  I'm really at a loss as to what do do here :confused:



I'm really sorry to keep dragging this out, guys.  Just really want to get this laptop working so I can ditch XP and use it for work.

---

### Post by SlidingHorn on 2010-05-25
deleted the shot, as it was huge...gonna try to get a thumbnail if I can figure out how

**Edit:** Ok..got the thumbnail...

---

### Post by MiGsBPR on 2010-05-25
You can try uninstalling the device all together and try to let windows install it again... which could work, but is risky, windows might not find any driver at all haha. Anyways, I found this on the internets [http://members.driverguide.com/driver/detail.php?driverid=133876&action=filfo](http://members.driverguide.com/driver/detail.php?driverid=133876&action=filfo) , look in win xp>pc card, and check the timestamp of that wlluc48.sys with the one you have on your system, see if its the same thing. I'm pretty sure you've seen that page before, but not sure, and it might be helpful.

---

### Post by SlidingHorn on 2010-05-25
My drivers are dated 2004 (those are 2001)...maybe I'll just have to use the older ones with ndiswrapper and give that a try.  Will let y'all know afterward

**Edit: ** My *driver*

---

### Post by SlidingHorn on 2010-05-25
even bigger edit....the exe file installs the .inf file.  not too bright tonight am i?  lol

I'll give this a shot tomorrow

---

### Post by matias.moreno on 2010-05-26
I'm really surprised this thread last post is 13 hours ago, I'm having exactly the same problem with the same tablet.

I'll give the ndiswrapper alternative a shot too.

---

### Post by SlidingHorn on 2010-05-26
Ok...well the story is, ndiswrapper is not compatible (as far as I could tell from researching online & @ the ndiswrapper sourceforge wiki) with the driver for my on-board wireless card.  I gave it a try anyway and did troubleshooting from [this post]("http://ubuntuforums.org/showthread.php?t=885847") to no avail.

In a fit of rage, I decided to step away and clean my apartment - because if I couldn't be happy, I might as well make sure my gf wasn't bitching about the place being a mess.

While cleaning, I came across an old Z-Com USB adapter.  I turned the on-board card's switch off, plugged in the USB, ran my lsusb, and was given:

```
Bus 001 Device 002: ID 0cde:0008 Z-com Sitecom Wireless Network Adapter 100G+ WL-125
```

Ran the ID through ndiswrapper's wiki to find it IS COMPATIBLE!  I downloaded the Windows driver (WlanUIG.inf) and installed w/ ndiswrapper & checked the install

```
sudo ndiswrapper -i WlanUIG.inf
ndiswrapper -l
wlanuig : driver installed
[INDENT]device (0CDE:0008) present (alternate driver: p54usb)[/INDENT]
```

Blacklisted the alternative driver in /etc/modprobe.d/blacklist.conf, ran

```
sudo update-initramfs -k all -u
```

and restarted.  There were a couple other small steps that I could not remember at this time, but it wasn't anything major.  

Basically the lesson to learn here is that **if you have this laptop, the factory wireless card is not compatible**.  Go out, spend $10 (or dig through your mess of an apartment) and grab a USB adapter that is already known to work.

---

### Post by MiGsBPR on 2010-05-26
What the, this can't be marked "solved" if you solved it by using something else :confused:.... I guess this wifi card is unsupported, and the only solution is to get it supported.. how do we got about doing that?

---

### Post by matias.moreno on 2010-05-27
Good news, I got mine partially working. :)

With native linux drivers, no ndiswrapper.

This is what I did:

- Edit /etc/network/interfaces file and add an entry for the wireless card. Mine looks like this:

auto eth1
iface eth1 inet dhcp

- Click on wireless icon and setup a wireless connection as usual: SSID, 
WEP password if applies, etc...
- Click on icon again and disable (YES, DISABLE) wireless networks.
- Shutdown, then power on with power key (didn't try rebooting yet).

Sometimes it shows the wireless icon with red exclamation sign, sometimes it just doesn't show the icon, but anyway the wireless connects successfuly. So... it seems the Ubuntu (or Gnome?) applet is not working properly with this card.

I have unplugged the ethernet cable, just to be sure, and ping'ed [www.google.com](www.google.com) and it pings ok all the way.

Here is iwconfig output:

...

Ok, I'll connect to this forum again from the tablet (I'm typing at my desktop computer now, hehehe)

---

### Post by matias.moreno on 2010-05-27
Ok, lshw relevant output:

        *-pcmcia:0
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=64
             resources: irq:11 memory:38102000-38102fff ioport:1400(size=256) ioport:1800(size=256) memory:20000000-23ffffff(prefetchable) memory:24000000-27ffffff
           *-network
                description: Wireless LAN Card
                product: Version 01.01
                vendor: TOSHIBA
                physical id: 0
                slot: Socket 0
                resources: irq:11

...further down...

  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:87:0d:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b

iwconfig eth1 output:

eth1      IEEE 802.11b  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:29:63:40:99   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr: off   Fragment thr: off
          Encryption key: off
          Power Management: off
          Link Quality=29/70  Signal level=-73 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:1
          Tx excessive retries:2  Invalid misc:0   Missed beacon:0

Oops, it is connecting to my neighboor's unprotected network :P, whatever... in previous iwconfig runs I saw it connected to my WEP-128 bit protected network too, pings ok to google, ethernet cable disconnected, etc...

What shall I do next? It works fine via command-line, but Ubuntu is about human beings after all, so where should I bug report this one? (sorry I'm a real noob at this)

EDIT: forum replaced : o with :o on iwconfig output hehe

---

### Post by matias.moreno on 2010-05-27
Ok, I just tried this:

ifdown eth1
iwconfig eth1 essid "Lamadr...
iwconfig eth1 key s:Mat...
ifup eth1

Then it got IP through DHCP, pings google, etc... and can see the tablet just connected, at my router's status page.

I guess something is really wrong with the applet, or with whatever the applet uses. :S

---

### Post by MiGsBPR on 2010-05-27
Good work there Matias, this looks like its halfway there to finding a fix!

Update:
So I installed openSUSE 11.2, wireless still giving the same problem, but its also give a description saying. "Lucent/Agere firmware doesn't support manual roaming."

---

### Post by matias.moreno on 2010-06-02
Ok, the problem is network-manager.

Connecting from command line works just fine. Do this:

Edit /etc/network/interfaces

Add these lines:

# The loopback network interface
auto lo
iface lo inet loopback

# The cable network interface
auto eth0
iface eth0 inet dhcp

# The wireless network interface
auto eth1
iface eth1 inet dhcp

Now you need to connect manually to the network.
For example, to connect to JohnSmithAP, with WEP 128-bit key yawontpass123:

iwconfig eth1 ESSID JohnSmithAP
iwconfig eth1 KEY s:yawontpass123

Then bring up the wireless interface:

ifup eth1

Of course this is all too tedious, so I wrote a PHP script to be run from inetd/xinetd to manage all that. It also stores keys so you don't have to enter them twice, and can be called as this:

/usr/bin/wget -O - 'http://127.0.0.1:8080/startup/'

From an init script to make it connect to the last known network at startup.

I did this for a friend of mine (the Portégé's owner), the script works fine.

If someone is interested in my script, please don't doubt to reply or PM me and I'll upload it somewhere and customize it if you need it (not for strange/bizarre/commercial purposes, sorry... ok, maybe if you pay me :tongue:).

---

### Post by matias.moreno on 2010-06-03
Ok, I'm trying other network managers:

- wicd: didn't work
- wifi-radar: [s]testing...[/s] didn't work

I'd prefer to use a network manager instead of my script. 8-[

If anyone has suggestions please reply.

---

### Post by Shmitty08 on 2011-06-28
I know that this is a little late, by almost a year, sorry :). I was actually able to get mine to work. I had to blacklist the driver that Network Manager uses by default, and unblacklist the Atheros driver. Granted this doesn't work under the network manager, but I was atleast able to use the essid command to connect to the network. I am working on writing a script to do some stuff automatically for me, will post that later. So to start open terminal, sign into root, then one line at a time enter:

# gedit /etc/modprobe.d/blacklist.conf 
     (In GEdit, add the line) blacklist bcm43xx  (and remove the line) blacklist ath9k (Save and close GEdit)
# reboot

Once you have rebooted your machine, you will be able to use the terminal to connect to wireless networks. Only issue with this is that you need to enter it every time you try to connect to a network. Open root terminal:

# ifconfig eth1 up (ETH1 is mine on this machine will prolly be the same on yours)
# iwlist eth1 scan 
# iwconfig eth1 essid network-SSID key yourkeyhere
# dhclient eth1

Once you have done that, you should be able to get online. Every once in a while, you will have to do the iwconfig, and dhclient over again, but it is rare that happens. My real question from this post though was, is there any way to make the ath9k driver work under Network Manager so that we can use the GUI instead of BASH? I would have thought that taking it off the blacklist would have done the trick, but Network Manager isn't grabbing it for use.

---

