---
title: "Can't install b43 fwcutter in Jaunty"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by Asterio on 2009-04-25
My Broadcom wireless card needs this tool to work, but I can't install it. On 8.10, I could install it through the Hardware Drivers window, but now that doesn't work. 

I found the package on Launchpad, but what do I do with a tar.gz, and where would I put it?

---

### Post by thewolfman on 2009-04-25
> **Asterio said:**
> My Broadcom wireless card needs this tool to work, but I can't install it. On 8.10, I could install it through the Hardware Drivers window, but now that doesn't work. 

I found the package on Launchpad, but what do I do with a tar.gz, and where would I put it?

The simplest way to deal with the Broadcom wlan is to go to:

[www.ubuntu.cafuego.net](www.ubuntu.cafuego.net) and download it from there, you will need to add the url's to your repository manager in synaptic.

Just go to the cafuego page and follow the link to Broadcom then add the 2 url's to your repo, then using synaptic install them both, you will also need ndiswrapper package (3 in total) and the windows driver disk with the Broadcom driver file which ends in INF.

The ndiswrapper is used to install windows wireless drivers which will show up in your admin applications list.

Hope this helps.

thewolfman

---

### Post by Asterio on 2009-04-25
> **thewolfman said:**
> The simplest way to deal with the Broadcom wlan is to go to:

[www.ubuntu.cafuego.net](www.ubuntu.cafuego.net) and download it from there, you will need to add the url's to your repository manager in synaptic.

Just go to the cafuego page and follow the link to Broadcom then add the 2 url's to your repo, then using synaptic install them both, you will also need ndiswrapper package (3 in total) and the windows driver disk with the Broadcom driver file which ends in INF.

The ndiswrapper is used to install windows wireless drivers which will show up in your admin applications list.

Hope this helps.

thewolfman

I can't find the Broadcom section.

---

### Post by thewolfman on 2009-04-25
> **Asterio said:**
> I can't find the Broadcom section.

[http://ubuntu.cafuego.net/dists/intrepid-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/intrepid-cafuego/broadcom/)

Go to the link I just posted, it is for intrepid but works for me.

Sorry mate to have misguided you a little.

thewolfman

---

### Post by snowpine on 2009-04-25
Actually, the simplest way to install it is to open a terminal and:

```
sudo apt-get install b43-fwcutter
```

Installing it from the official Ubuntu repository using apt-get is safer than installing random downloads from the internet.

---

### Post by sidewinder12s on 2009-04-25
Cant you do it through terminal?

---

### Post by Asterio on 2009-04-25
> **snowpine said:**
> Actually, the simplest way to install it is to open a terminal and:

```
sudo apt-get install b43-fwcutter
```

Installing it from the official Ubuntu repository using apt-get is safer than installing random downloads from the internet.

I've tried that at least ten times; I'm not stupid.

---

### Post by thewolfman on 2009-04-25
> **Asterio said:**
> I've tried that at least ten times; I'm not stupid.

Trust me on this, I have a Broadcom myself and it works just fine.

thewolfman

---

### Post by snowpine on 2009-04-25
> **Asterio said:**
> I've tried that at least ten times; I'm not stupid.

Nobody called you stupid. :) Just trying to help. What errors did you get the ten times you tried?

---

### Post by Asterio on 2009-04-25
LOL, now it works! I did the exact same thing before, and it didn't work.

---

### Post by snowpine on 2009-04-25
> **Asterio said:**
> LOL, now it works! I did the exact same thing before, and it didn't work.

Sometimes I think the Ubuntu Forums are magic. :) 
Glad you got it working.

---

### Post by Asterio on 2009-04-25
> **snowpine said:**
> Sometimes I think the Ubuntu Forums are magic. :) 
Glad you got it working.

Magic forums :D 

Thanks for all the help. 

Now I can enjoy Jaunty without worrying about the frigging wireless.

---

### Post by sidewinder12s on 2009-04-25
Could someone help me with mine?
[http://ubuntuforums.org/showthread.php?t=1136474](http://ubuntuforums.org/showthread.php?t=1136474)

I tired doing this and it tells me that i already have it installed, but my wireless still doesnt work. Ive got a lot of info about my set-up. put a lot of effort into it and any help would be great

---

### Post by marbss on 2009-04-26
thanks for posting this thread.  here's what worked for me on x40 with broadcom b4318 wireless adapter.

added 
    deb     [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) jaunty-cafuego all
    deb-src [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) jaunty-cafuego all
to the software third party source list.  closed out of the software sources pop window.

then went to terminal 
typed

sudo aptitude update
(it gave me pubkey message near the end)

then typed
sudo apt-get install b43-fwcutter 
let it install and download what it needed to... rebooted and i'm working.  
cheers,

---

### Post by SeePU on 2009-04-26
> **thewolfman said:**
> Trust me on this, I have a Broadcom myself and it works just fine.

thewolfman
No, it doesn't!

Is there a bug in Ubuntu's 'Hardware Drivers' utility?   Because, it totally sucks.

I click to activate the bcm43 driver and it is ignored.  Then I found out, I have to press 'enter' with the cursor beside the selected text.  But, nothing happens after it's activated.  

So, once again, it doesn't work.

I'm looking into replacing my wifi card.  How could Ubuntu not care about properly configuring such a common wifi card?!? :(

---

### Post by SeePU on 2009-04-26
> **marbss said:**
> thanks for posting this thread.  here's what worked for me on x40 with broadcom b4318 wireless adapter.

added 
    deb     [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) jaunty-cafuego all
    deb-src [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) jaunty-cafuego all
to the software third party source list.  closed out of the software sources pop window.

then went to terminal 
typed

sudo aptitude update
(it gave me pubkey message near the end)

then typed
sudo apt-get install b43-fwcutter 
let it install and download what it needed to... rebooted and i'm working.  
cheers,
Sounds good if it works.  Do you have to reboot after it installs?

I am wondering if I can do it via LiveCD.  Right now, my laptop only has a 40GB drive and I don't want to install a new distro on top yet if I can't get wireless working.

I have it working in another Debian-based distro but I'm used to Kubuntu on my desktop and would like to use the same OS.

Cheers.  Thanks for some ideas.

---

### Post by thewolfman on 2009-04-26
> **SeePU said:**
> No, it doesn't!

Is there a bug in Ubuntu's 'Hardware Drivers' utility?   Because, it totally sucks.

I click to activate the bcm43 driver and it is ignored.  Then I found out, I have to press 'enter' with the cursor beside the selected text.  But, nothing happens after it's activated.  

So, once again, it doesn't work.

I'm looking into replacing my wifi card.  How could Ubuntu not care about properly configuring such a common wifi card?!? :(

Well you had better come and tell my PC that because I am using it right now!

---

### Post by SeePU on 2009-04-26
> **thewolfman said:**
> Well you had better come and tell my PC that because I am using it right now!
That's good.  But, as far as I'm concerned, it doesn't work.

Not in Ubuntu, not in Kubuntu.  'Doesn't matter.

Installing using 'Hardware Drivers' does the same thing.  The firmware, b43-fwcutter, can be installed but it doesn't matter.  You can't scan wireless networks and nothing is showing in 'wireless connections.'

---

### Post by IceBadger on 2009-04-26
Hey guys, this thread is great if you already have an internet connection on your computer.

If you are like me and have a laptop with a broken ethernet port, you may be caught in a Catch 22 (if I had wireless, I could fix my wireless).  Here is how I got my card working:

You ***WILL*** need internet access to get the following files (for i386):

```

http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-5_i386.deb
http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```

Place these in your home directory.  Next run the .deb file.  It will crash, because you do not have internet access, but it is important that you run this to let your package manager know you have this package installed.

```

sudo dpkg -i b43-fwcutter_011-5_i386.deb
```

To actually install the driver:
```

sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
``` 

I needed to perform a hard reset, but my wireless is now working in 9.04.

---

### Post by thewolfman on 2009-04-27
> **SeePU said:**
> That's good.  But, as far as I'm concerned, it doesn't work.

Not in Ubuntu, not in Kubuntu.  'Doesn't matter.

Installing using 'Hardware Drivers' does the same thing.  The firmware, b43-fwcutter, can be installed but it doesn't matter.  You can't scan wireless networks and nothing is showing in 'wireless connections.'

Did you also install ndiswrapper (3 packages) for the windows wireless drivers and also have the windows driver cd for your wlan card with the INF file which is also needed to get it running.

---

### Post by kevdog on 2009-04-27
Try not using ndiswrapper if you can avoid it.  b43 is much better in terms or performance and capabilities and a native linux driver.

---

### Post by IceBadger on 2009-04-27
> **SeePU said:**
> That's good.  But, as far as I'm concerned, it doesn't work.

Not in Ubuntu, not in Kubuntu.  'Doesn't matter.

Installing using 'Hardware Drivers' does the same thing.  The firmware, b43-fwcutter, can be installed but it doesn't matter.  You can't scan wireless networks and nothing is showing in 'wireless connections.'

**@SeePU:**  I was having the same issue.  It looked like I had the drivers installed, but I could not scan/list any connections.  Do you have any Internet connection on this computer?

It turns out that the b43-fwcutter package does not contain any firmware.  It needs to download them from an external source.  If it cannot connect, nothing is installed but your package manager will think that it is installed and working.

---

### Post by SeePU on 2009-05-01
> **IceBadger said:**
> **@SeePU:**  I was having the same issue.  It looked like I had the drivers installed, but I could not scan/list any connections.  Do you have any Internet connection on this computer?

It turns out that the b43-fwcutter package does not contain any firmware.  It needs to download them from an external source.  If it cannot connect, nothing is installed but your package manager will think that it is installed and working.
Yes, I had to use a wired connection to install but nothing worked anyway.  Bad.

---

### Post by terinjokes on 2009-05-08
> **IceBadger said:**
> You ***WILL*** need internet access to get the following files (for i386):


And for those of us running on PowerPC chips? I can't find the right file anywhere!

Can you point me in the right direction?

---

### Post by zrzhu on 2009-08-12
> **IceBadger said:**
> Hey guys, this thread is great if you already have an internet connection on your computer.

If you are like me and have a laptop with a broken ethernet port, you may be caught in a Catch 22 (if I had wireless, I could fix my wireless).  Here is how I got my card working:

You ***WILL*** need internet access to get the following files (for i386):

```

http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-5_i386.deb
http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```Place these in your home directory.  Next run the .deb file.  It will crash, because you do not have internet access, but it is important that you run this to let your package manager know you have this package installed.

```

sudo dpkg -i b43-fwcutter_011-5_i386.deb
```To actually install the driver:
```

sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
```I needed to perform a hard reset, but my wireless is now working in 9.04.

This method worked for me. I downloaded all the file on XP, and then go to Ubuntu to install the driver.

---

### Post by tinman6700 on 2012-09-18
ok, so it looks like I'm reviving an ancient thread, lol,  but I have been slamming my head against a brick wall for days now, and just running in circles. There has got to be a way to get this working. first off, im trying to fire up an ancient laptop, for a friend. It's a dell inspiron 600m, and the newest distro that I can get to install properly is Jaunty. Ive finally found the list of repo's for older distros, but it would appear that the firmware , and legacy drivers are not available for my distro. I was going to go the route of fw cutter, or ndiswrapper, but cant find a version of the driver, for download, anywhere but Dell. It's zipped, and all of my systems run linux exclusively. I do not have a system that can deal with a zip file, so I am kind of stuck on the .inf part. There has got to be a way to make this work, as my friend has only wireless access, and the laptop is useles to her, if I can't make the wireless work. Any help would be greatly appreciated, thanks

---

