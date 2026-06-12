---
title: "Atheros AR5007EG Wireless issues"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by areamike on 2009-02-13
I am trying to get my wireless integrated adapter to work on Ubuntu Linux 8.10.

I have tried madwifi and ndiswrapper on a previous install of Linux and totally hosed everything. I reinstalled last night and decided to start fresh and come here for help.

#iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

Also, there is no information in /etc/network/interfaces about ath0.

When I go to System>>Administration>>Hardware Drivers, I see:
Support for Atheros 802.11 Wireless LAN card activated

I can post any additional info as requested.

---

### Post by areamike on 2009-02-13
mike@ubuntu:~$ lsmod | grep ath
ath_pci                99096  0 
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci

---

### Post by sanemanmad on 2009-02-13
Is this a laptop?

---

### Post by sanemanmad on 2009-02-13
Two possible scenarios I can think of.

1. The built-in HAL is toying with your drivers, untick that and reboot; Otherwise you'll need to reinstall the drivers... Here is a decent guide 
[Atheros wireless configure and install]("http://hamzakc.wordpress.com/2006/12/11/atheros-wireless-setup-ubuntu/")

2. There is a switch on the laptop and thus needs to be enabled.

---

### Post by areamike on 2009-02-13
> **sanemanmad said:**
> Two possible scenarios I can think of.

1. The built-in HAL is toying with your drivers, untick that and reboot; Otherwise you'll need to reinstall the drivers... Here is a decent guide 
[Atheros wireless configure and install]("http://hamzakc.wordpress.com/2006/12/11/atheros-wireless-setup-ubuntu/")

2. There is a switch on the laptop and thus needs to be enabled.

It's a Toshiba L355D-S7825.

The wireless switch on front is on. I dual boot to Vista(ugh, trying to get away from Windows) and it works there.

I tried looking in System>>Preferences>>Sessions and cannot find any info on disabling HAL. Man I am such a newb..

---

### Post by areamike on 2009-02-13
I had found that link Atheros wireless configure and install
during my previous quest to get this wlan working.

I am trying it now yet am running into problems already.
This is as far as I have ever gotten

# Get the g++ compiler : sudo apt-get install build-essential
# Download subversion : sudo apt-get install subversion
# Create directory to store the drivers and navigate to it.
# Download latest madwifi drivers using subversion : subversion svn checkout [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) madwifi

subversion command not found.

I am running Kernel 2.6.27-11-generic, but that does not tell me what drivers to use from madwifi.

---

### Post by RealG187 on 2009-02-13
I have this one and got it working.

[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)
Try downloading the file there (I uploaded the one I used [here]("http://www.megaupload.com/?d=G3C1GQHJ"))

Extract it to a folder in your home folder.

Open terminal

type "cd madwifi..." (I just type "cd mad" without pressing enter then push tab and it types the rest, this is called tab completion and since I found out about it it makes things in the terminal a lot easier)

then  type "make"

then type "sudo make install" (this has to be ran as root, I was going insane because it wasns't workng, then I figured it out and it was just simple thing.

finally type " modprobe ath_pci" and restart.

that last command shouldn't have to be ran as root, when I did it I didn't have to, but when my [wireless stopped working]("http://ubuntuforums.org/showthread.php?t=1065954") and I had to do it for the second time just now, I ran it as root...

EDIT: Oh yeah you need [Build Essential]("http://www.megaupload.com/?d=73Q7P6WR").

---

### Post by areamike on 2009-02-13
Thanks RealG187 - followed your steps to the letter.

Seems we are getting somewhere. I now see Enable Wireless checked under Network. However, still no connection and still no info in /etc/network/interfaces about ath0.

Wireless Networks
Device is unmanaged.

---

### Post by Ketara on 2009-02-13
Did you disable the HAL driver in system>administration>hardware drivers?

The madwifi driver won't run unless you disable the HAL driver.

If that doesn't work, you might try the stuff in here: [http://ubuntuforums.org/showthread.php?t=964836&highlight=atheros+5007+backports](http://ubuntuforums.org/showthread.php?t=964836&highlight=atheros+5007+backports)

If that doesn't work, I got this card working with ndiswrapper.

---

### Post by areamike on 2009-02-13
Well I'll be a monkey's uncle.

I checked my /etc/network/interface file after I had manually added info into it hoping it would take which it did not.
I then simply erased EVERYTHING in that file except:

auto lo
iface lo inet loopback

I then rebooted and BAM!...Network notification icon in systray pops up and says Wireless networks detected. I click on it, it asked for my WEP key, I input it and BAM. Wireless working!!!

Thanks RealG187. Your method seemed to work for me.

---

### Post by MRRT on 2009-02-13
Hello.
I have the same problem decribed. Followed the steps described by realG187 and it worked. But when I restart my system it doesen't work. I have to modprobe again and then it work.
Can you help me?
Thanks.

---

### Post by areamike on 2009-02-13
I think there is a way to *** modprobe command to startup.

I'll check.

---

### Post by waj1122 on 2009-02-13
modprobe ath_pci should do it

I followed the instructions here
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)
and used the madwifi method to get my AR5007EG working.

ath5k worked but the connection speed was all over the place on my Toshiba laptop 1M then 54M and everywhere in between and I'm only about 10 feet from the router

---

### Post by RealG187 on 2009-02-13
I don't have to modprobe every time, in fact when I do it I typed it and it didn't work until I restarted. But the second time I did it (after I had [this problem]("http://ubuntuforums.org/showthread.php?t=1065954")) it wokred without restart.

A possible solution is adding "modprobe ath_pci" to startup, I beleive this can be done from System --> Preferecnes --> Sessions...

---

### Post by areamike on 2009-02-13
> **RealG187 said:**
> I don't have to modprobe every time, in fact when I do it I typed it and it didn't work until I restarted. But the second time I did it (after I had [this problem]("http://ubuntuforums.org/showthread.php?t=1065954")) it wokred without restart.

A possible solution is adding "modprobe ath_pci" to startup, I beleive this can be done from System --> Preferecnes --> Sessions...

I don't need it either. I have rebooted and or shutdown 4 times now and each time the Wireless connection automatically connects. Pretty awesome.

---

### Post by sanemanmad on 2009-02-13
> **RealG187 said:**
> A possible solution is adding "modprobe ath_pci" to startup, I beleive this can be done from System --> Preferecnes --> Sessions...

otherwise simply add the line to rc.local file and that will solve the problem where the module isn't loaded during boot

I use *vi* for everything, but go ahead and use *nano*

sudo nano /etc/rc.local

add the line "modprobe ath_pci"

You will have to update the rc.local file

"sudo update-rc.d rc.local defaults"

---

### Post by RealG187 on 2009-02-13
Now I think I have to do it everytime I boot.... WTF :?

---

### Post by areamike on 2009-02-14
> **RealG187 said:**
> Now I think I have to do it everytime I boot.... WTF :?

weird. I have not had to "yet" [knocks on wood]

---

### Post by Aped on 2009-02-14
Will the steps described herein work on my [http://ubuntuforums.org/showthread.php?t=1069947AR5008]("http://ubuntuforums.org/showthread.php?t=1069947")? 

Because that would be sweet, except the 5008 is a Draft-N card.

---

### Post by RealG187 on 2009-02-15
> **areamike said:**
> weird. I have not had to "yet" [knocks on wood]

I didn't have to, but then once my wireless stopped working and I got it working again I do...

---

### Post by RealG187 on 2009-05-20
Does this device work on 9.04?

---

### Post by areamike on 2009-05-28
> **RealG187 said:**
> Does this device work on 9.04?

I don't know. I have not tried. I am still using Ubuntu 8

---

### Post by RealG187 on 2009-05-28
It does and out of the box (I read in another thread I asked and from experience)

The internet might be slow, but I am not entirly sure...

And this is my 1000th post!

[IMG]http://eddsworld.co.uk/pages/stuff/itsatank.gif[/IMG]

---

### Post by wilbz08 on 2009-05-31
mine same card mini pci atheros 5007eg it works auto on ubuntu 8/9 on 32bit/64 and on live cd and installed dont see ur problem

---

### Post by RealG187 on 2009-06-01
It didn't work for me in 8.04 or 8.10, in fact part of the reason I installed 9.04 was at the time my 8.10 installation had the wireless not work (for this device, I plugged in my WUSB54G and it worked but that was only a temporary fix) and instead of fixing the driver (I was moving files, but I dont think I touched the driver, but it stopped working regardless) I just installed 9.04

---

