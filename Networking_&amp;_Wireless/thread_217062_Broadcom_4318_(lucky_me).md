---
title: "Broadcom 4318 (lucky me)"
date: 2006-07-16
forum: Networking &amp; Wireless
---

### Post by Twidoom on 2006-07-16
So I just finished installing Ubuntu as a dual boot on my laptop (looks nice so far), but I'm having issues getting my Broadcom to work, and no internet just isn't a realistic alternative ](*,) 

I followed the instructions [here](http://ubuntuforums.org/showthread.php?t=197102) (downloaded the one with network manager and ndiswrapper) but it told me there was an error installing network manager.
I am able to get the message "drivers installed, hardware present" or whatever, but no internet.  And every time I restart the computer I lose the settings that I had fiddled with (making eth1 active, putting in my WEP, etc)

---

### Post by joplass on 2006-07-16
try issuing these commands. they helped me when i had similar issues.
depmod -a
modprobe ndiswrapper

---

### Post by bluecherry on 2006-07-16
Make sure your /etc/network/interfaces contains nothing but entries containing lo (local loop).

I know it's already mentioned in the thread but I overlooked it myself the first time... ;)

---

### Post by Twidoom on 2006-07-16
my interfaces looks like this:


```

auto lo
iface lo inet loopback

```

**depmod - a**
FATAL: could not open lib/modules/2.6.15-23-386/modules.dep.temp for writing: Permission denied
**modprobe ndiswrapper**
no output at all:-k 

I think this is probably the problem:
```

unpackng replacement network-manager...
dpkg: dependency problems prevent configuration of network-manager:
network-manager depends on libnl1-pre6; however:
Package libnl1-pre6 is not installed.
...
same for libnm-util0 and dhcdbd (>=1.10-0ubuntu2)
...
dpkg: error processing network-manager (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
 network manager
Installation completed.

```

BTW: TY for the fast responses!

---

### Post by bluecherry on 2006-07-16
1. Try: "sudo depmod -a"

2. No output is good with modprobe. This means ndiswrapper is loaded, it would've said "FATAL: something..." if it wasn't. ;)

3. Using synaptic, remove the package "network-manager" completely.

When this is done, try installing "network-manager-gnome" and see if synaptic complains about dependencies.

It's very strange that these dependencies are not met and this could well be your problem.

---

### Post by Twidoom on 2006-07-16
sudo depmod -a ran fine, worked for a while, no output
i tried running depmod -a afterwards again but got the same error

removed the package, synaptic said i had one broken package and that ended up being it

where do i find network-manager-gnome?  I did a search for network manager and all i found was the package pcmcia-cs which is already installed on my system.

---

### Post by bluecherry on 2006-07-16
In synaptic:

1. Make sure you've got all the repo's activated.
--> Go to "Settings > Package Sources > First tab.
--> Check every entry in this list en close this window.
--> Click the big "Reload" button and watch how synaptic updates itself ;)

2. Click "Find", enter "network-manager-gnome" and select "name" from the dropbox. Now click "Find". The package should show up now.

NOTE: I've got Ubuntu in Dutch so I've translated everything but "Find" could be "Search" etc...

---

### Post by Twidoom on 2006-07-16
Okay I went to the repo's and would have added them all, but I need to be connected to the internet, is there anywhere I can go to downoad them and then burn em to a CD?

---

### Post by bluecherry on 2006-07-16
These are the packages you need to install (respect this order when installing):

[http://packages.ubuntulinux.org/dapper/admin/dhcdbd](http://packages.ubuntulinux.org/dapper/admin/dhcdbd)
[http://packages.ubuntulinux.org/dapper/libs/libnl1-pre6](http://packages.ubuntulinux.org/dapper/libs/libnl1-pre6)
[http://packages.ubuntulinux.org/dapper/net/libnm-util0](http://packages.ubuntulinux.org/dapper/net/libnm-util0)
[http://packages.ubuntulinux.org/dapper/net/network-manager](http://packages.ubuntulinux.org/dapper/net/network-manager)
[http://packages.ubuntulinux.org/dapper/net/network-manager-gnome](http://packages.ubuntulinux.org/dapper/net/network-manager-gnome)

Scroll down these pages and click on the architecture of your CPU (if you're not sure it will probably be I386). You will be asked to select a mirror (pick one close to you) en you can download the file.

Download every file of the above, burn them on cd and copy them to your ubuntu desktop.

Fire up a terminal and navigate to your desktop (cd ~/Desktop).
Install all the .deb files in the order i listed them above with:
```

sudo dpkg -i name_of_package.deb

```

This should get it working...

---

### Post by Twidoom on 2006-07-16
OK I have all of that done now with no errors or anything.  Now what do I do?  (thanks for all the help so far, I never woulda known what to do!)

---

### Post by Twidoom on 2006-07-16
NM what I've realized is the following...

WEP does not work
I can freeload off my neighbour's network the first time I set it up under network settings but if I fiddle with it, it stops working and I have no internet again :(

---

### Post by Jagot on 2006-07-17
I have a Dell Inspiron 1300 with the BC4318 and this is how I get it working:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

Then it's just a matter of activating and filling in details in network settings.

---

### Post by Twidoom on 2006-07-17
Jagot, whats bcmwl5/bcmwl5.inf?  Do you have a location where I could download it from?  Thanks.

Also do you have WEP?

---

### Post by Jagot on 2006-07-17
bcmwl5.inf is the driver for the card.  You should be able to download the drivers from your computer manufacturers web site.  Although I have a Dell, I downloaded the driver from Acer's web site and it still worked.

And yes I have WEP

---

### Post by Twidoom on 2006-07-17
sigh...still not working :(

the neighbour's unencrypted network works, but mine with WEP doesn't =/

---

### Post by Jagot on 2006-07-17
When your setting up the WEP you do have it set for hexadecimal right?

---

### Post by Twidoom on 2006-07-17
yeap, and I'm positive its right because I tried it on my Windows computer with the same hex code and it worked.

Wireless connection eth1, dhcp

---

### Post by Jagot on 2006-07-17
In Terminal, could you run the command 'iwconfig' and post the output here please?

---

### Post by Twidoom on 2006-07-17
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"default"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:2A:6F:64
          Bit Rate:11 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-75 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

uhh, thats the one that actually works, would you like me to post the other as well?

---

### Post by Jagot on 2006-07-17
Hmm, well there doesn't appear to be anything wrong with that.  All I can suggest is you double-check the name of your access point, your hex code and give it a restart as I can't see any other reason why it shouldn't be working.

---

### Post by Twidoom on 2006-07-17
hmmm....nope everything appears to be right, i've tried putting in the hex code and network name a thousand times :S

---

### Post by Twidoom on 2006-07-17
Hey this may help...I changed the settings to the WEP connection, restarted my computer and then it reverted back to the default...

---

### Post by Twidoom on 2006-07-17
I THINK I KNOW THE PROBLEM!!!

I did 
```
sudo iwlist eth1 scan
```
and it says that my network is a freqency of 2.437ghz (channel 6), I'm not positive but I'm pretty sure I changed it on my router because it was being troublesome.  However its entirely possible my neighbour is still on channel 6.

Now the question is, how do I specificy which frequency ubuntu should be checking?

---

### Post by Twidoom on 2006-07-17
bump, checkd the frequency, guess its not the problem

---

### Post by Twidoom on 2006-07-18
Umm, i figured out something interesting...

Everytime I try to connect to my network (instead of my neighbour's) I end up knocking down my internet somehow.  Could this somehow be related to my problem?  I end up having to reset my cable router.

To clarify, my network doesn't get knocked down, just the internet.  i can still connect to the network with my windows pc's, but there is no internet.

Really confusing....Anybody have any ideas?  Any help would be greatly appreciated!

---

