---
title: "can't find connections tab in network settings"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by leonsaurabh21 on 2010-05-17
I have installed Ubuntu_studio n trying to configure the internet, but i couldn't find the connection tab in network settings.
Can somebody help me please 

thanks

---

### Post by banditthecooldog on 2010-05-20
It appears alot of people who are new to ubuntu studio are having this problem (like myself). I posted a similar thread and got no replies basically.

Turns out that that studio doesn't come with the network manager installed! I've been doing a search on how to install it and got some luck, although it's still not working...

Hope this points you in the right direction maybe to fix it, and if you do let me know how!

---

### Post by banditthecooldog on 2010-05-20
And I just got it to work!

Quoted from my post at: [http://ubuntuforums.org/showthread.php?t=1484277](http://ubuntuforums.org/showthread.php?t=1484277)

---------------------------------
Fixed it! It's fairly unscientific and I'm sure all the people who  actually know what they're doing will laugh at me, but I don't care  cause I got it to work-

Heres what I did:

Put in my installation CD
Went to: pool/main/n/
Installed EVERY file in EVERY folder that started with  "Network_Manager_something something blah blah blah..." You get the  Idea...
Restarted the computer

Then the network icon showed up on the panel and I was able to connect  right away. Because Linux has a native driver for my wireless card I  didn't have to go out finding one, my issue was actually not having the  network manager installed in the first place.

---------------------------------

---

### Post by integralcalculus on 2010-06-06
Thankyou very much!!!

I have been trying to install wireless network for 3 days straight and this was the final piece of the puzzle!!! ... 

I absolutely love Ubuntu studio btw

---

### Post by Darktrax on 2010-06-06
> **banditthecooldog said:**
> And I just got it to work!

Quoted from my post at: [http://ubuntuforums.org/showthread.php?t=1484277](http://ubuntuforums.org/showthread.php?t=1484277)

---------------------------------
Fixed it! It's fairly unscientific and I'm sure all the people who  actually know what they're doing will laugh at me, but I don't care  cause I got it to work-

Heres what I did:

Put in my installation CD
Went to: pool/main/n/
Installed EVERY file in EVERY folder that started with  "Network_Manager_something something blah blah blah..." You get the  Idea...
Restarted the computer

Then the network icon showed up on the panel and I was able to connect  right away. Because Linux has a native driver for my wireless card I  didn't have to go out finding one, my issue was actually not having the  network manager installed in the first place.

---------------------------------

Unscientific is OK by me :)  but, just to be clear..
You put the installation Ubuntu Studio Installation CD in the drive and opened it, and looked for the files ???

... Or you booted from it and went through some kind of "repair" ??

What exactly did you do to "install" these EVERY files? Where did you put them? 

Thanks

---

### Post by Darktrax on 2010-06-06
OK - I have found a shorter, and only slightly more scientific way.

I am also noticing the large number of newbies having network troubles. They need help, as do I. Anyways - what I have found out so far is..

1. Ubuntu Studio does not have a functioning Network Manager.

2. Depending on exactly which install CD you have (eg. AMD64 variety) and depending on if you have available a more than one network socket on the machine, your mileage may vary.

3. Using ***[COLOR="Red"]ifconfig[/COLOR]*** commands can get you working - but only temporarily.

4. A way that WORKS, even through a re-boot, is to edit /etc/network/interfaces. In my case, the cable is using eth1 instead of eth0. My file looks like this..

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
	address 192.168.0.24
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
	# dns-* options are implemented by the resolvconf package, if installed
To alter this to suit your own setup, substitute the gateway address of your own router. The address can be any you choose in the allowed range, in this case 192.168.0.x where x can be anything up to 244, and we have to keep off of the router address.

There is, in another thread, a simpler automatic DHCP command setup which I am still checking out. For now, this works for me on a boot-up.

---

### Post by cchhrriiss121212 on 2010-06-09
> Unscientific is OK by me :smile:  but, just to be clear..
You put the installation Ubuntu Studio Installation CD in the drive and opened it, and looked for the files ???

... Or you booted from it and went through some kind of "repair" ??

What exactly did you do to "install" these EVERY files? Where did you put them? 
You just click on the files to install them as they are .deb packages. This is by far the easiest way to do it. If you have a wired connection present during the install, then dhcp should be fine.

---

### Post by Darktrax on 2010-06-10
OK - I found them on the install CD using the Search for Files Utility

I re-installed everything that was associated with networking, by clicking on the .deb files as you suggest. Unfortunately, the result was not as lucky as your attempt. The "**Connections**" tab that should be in the Network Setup tool is still nowhere to be seen. We now have to abandon the un-scientific approach.

Since this 10.04 is the Ubuntu Studio 10.04-alternate-amd64.iso (Lucid), I guess the network tools default setup is maybe not exactly the same as on regular installs.

What always works is..
In a root terminal by entering [COLOR="Red"]gksu gnome-terminal[/COLOR]
[COLOR="Red"]ifconfig -a[/COLOR]                 ..  To see the state of things.
[COLOR="Red"]ifconfig eth0 down[/COLOR]          ..  Disable eth0, and leave it that way.
[COLOR="Red"]ifconfig eth1 up[/COLOR]            ..  Enable eth1.
[COLOR="Red"]ifconfig eth1 192.168.0.24[/COLOR]  ..  Assign eth1 an ipv4 address
[COLOR="Red"]ping -c 4 192.168.0.1[/COLOR]       ..  Check it can see the router.
[COLOR="Red"]route add default gw 192.168.0.1 eth1[/COLOR] .. Finally, let it know the gateway is the router address.

The commands shown have to be entered at each re-boot.

What I am trawling for now is the instructions for a proper working setup. By this I mean, a complete correct description of what needs to be where. The "Help and Support" texts do not provide this. It simply assumes that if one has DHCP, it is automatically OK, and goes on to describe the way to manually set up a **static** connection. Even if one follows that route, the boxes offered do not match what is described, and do not work anyway.

It would be a great help if someone could post a good example ***/etc/network/interfaces*** copy.

There does not seem to be any **resolve.conf** anywhere. (I tried #locate resolve.conf)
OK - so now, at least, I can get it on the internet. It would be nice to have it set up right, so it gets there automatically.

---

### Post by getack on 2010-08-03
I have exactly the same problem. I used the AMD64 alt install DVD. I abandoned the DHCP config during install as I use a wireless card with static IP's for my networking. I got the card working (Netgear WG311v3) using ndiswrapper just like I did with all my other (working online) ubuntu installs. But I cannot find that freaking "Connections" tab! I will try the above things when I get home. Otherwise I will simply add the DVD as a repository for synaptic in my main Ubuntu, and just add all the cool apps to that. Not elegant, but it should work.

---

### Post by solomoncn on 2011-09-05
thanks

---

