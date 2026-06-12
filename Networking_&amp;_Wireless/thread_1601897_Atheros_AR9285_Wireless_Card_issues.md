---
title: "Atheros AR9285 Wireless Card issues"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by Dead ChexMix on 2010-10-20
**SOLUTION? KINDA, I FOUND NO CONCRETE SOLUTION (THIS IS AN EDIT 2 YEARS LATER IN AN ATTEMPT TO HELP THOSE THAT STUMBLE UPON THIS THREAD)** **TRY THE ONES BELOW TOO... THE ONLY SOLOUTION I FOUND WAS USING NATTY NARWHAL (UBUNTU 11.04 I THINK) GOOD LUCK!**
(EDIT MAY 15, 2012)



Okay, I have a Atheros AR9285 wireless card and I can't seem to get ubuntu to reconize it. I've *_attempted _*to install and use the Ndswrapper thing (Sorry, forgot the exact name) it wont install it says that my perl directory is unsattisfactory and I've attempetted to solve this by installing everything it asked for yet in vain. So I need to know is there a ubuntu (Linux) driver for my Wireless card or SOme other soloution to my problem. 
 
Now, I'm sorry guys but I'm a NEWBIE to the Linux system, so any soloutions you give me, can you please please put them in human language?
 
MANY MANY thanks in advanced
 
It seems like my card ***kinda ***works. (After trying out CompShrink's solution, Although I belive it does this by default with no moddifications) It will reconize my network when feed the details..and after asking for the padsword several times over it connects..but not fully, i still have no internet connections.
 
 
 
My card does not show **ANY** wireless networks in my network manager. I'm more than sure my network is discoverable. My Windows computer will see it. 
It will not scan for networks (although I'm not sure how to make it do that. Any help?)
 
It will (I think) connect to my home network but it begs for the password multiple times (I always give it the same password. It takes a couple of tries to get it to say "Connected)
 
I have no internet connection. Firefox doesn't show a think nethir does the software center (when trying to download and install)
 
 
PS Compshrink, Your solotuion worked to no avail

---

### Post by bigfootnmd on 2010-10-21
Please confirm what version of Ubuntu you are using.
The fact that you mention the NDSWRAPPER might indicate that you are using 10.04.  Have you tried downloading 10.10 and making a USB Startup disk?  Ubuntu 10.10 has native drivers for the Atheros cards.

---

### Post by CompShrink on 2010-10-23
I have the same AR9285 card, and I got it working with the method below, which is just slightly complicated. I am using Ubuntu 10.10. I think there is more than one revision of the AR9285, so it may not work for you.

This will need to use the terminal (aka command line, aka dos prompt). It is under Applications > Accessories > Terminal.

First, make sure none of the software installation programs are still open. Then copy & paste the following and hit enter:

```
sudo apt-get install build-essential
```

Then, download [http://www.orbit-lab.org/kernel/compat-wireless-2.6/2010/09/compat-wireless-2010-09-12.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2010/09/compat-wireless-2010-09-12.tar.bz2) to your Downloads folder (which is the default location).

Extract it, which you can do by opening up the folder in the file manager (nautilus) and then right clicking on compat-wireless-2010-09-12.tar.bz2 and selecting Extract Here.

Now again in the Terminal copy & paste the following and hit enter:

```

cd ~/Downloads/compat-wireless-2010-09-12
./scripts/driver-select ath9k

```

It may give you the error:

> Hunk #1 FAILED at 25.
1 out of 1 hunk FAILED -- saving rejects to file config.mk.rej
patching file scripts/gen-compat-autoconf.sh
Reversed (or previously applied) patch detected!  Assume -R? [n] 

If so, just hit enter once. Then type Y and hit enter when it asks:

> Apply anyway? [n]

Finally, copy & paste the following and hit enter:

```

make
sudo make install
sudo make wlunload
sudo modprobe ath9k

```

And now you should be able to connect to the wirless network with the Network Manager icon in the upper right corner of the screen.

Let me know if it doesn't work or if any part of the process is confusing.

---

### Post by stead21 on 2010-10-24
> **CompShrink said:**
> I have the same AR9285 card, and I got it working with the method below, which is just slightly complicated. I am using Ubuntu 10.10. I think there is more than one revision of the AR9285, so it may not work for you.

This will need to use the terminal (aka command line, aka dos prompt). It is under Applications > Accessories > Terminal.

First, make sure none of the software installation programs are still open. Then copy & paste the following and hit enter:

```
sudo apt-get install build-essentials
```

Then, download [http://www.orbit-lab.org/kernel/compat-wireless-2.6/2010/09/compat-wireless-2010-09-12.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2010/09/compat-wireless-2010-09-12.tar.bz2) to your Downloads folder (which is the default location).

Extract it, which you can do by opening up the folder in the file manager (nautilus) and then right clicking on compat-wireless-2010-09-12.tar.bz2 and selecting Extract Here.

Now again in the Terminal copy & paste the following and hit enter:

```

cd ~/Downloads/compat-wireless-2010-09-12
./scripts/driver-select ath9k

```

It may give you the error:



If so, just hit enter once. Then type Y and hit enter when it asks:



Finally, copy & paste the following and hit enter:

```

make
sudo make install
sudo make wlunload
sudo modprobe ath9k

```

And now you should be able to connect to the wirless network with the Network Manager icon in the upper right corner of the screen.

Let me know if it doesn't work or if any part of the process is confusing.

Is this 64 bit or 32 bit?

---

### Post by CompShrink on 2010-10-24
> **stead21 said:**
> Is this 64 bit or 32 bit?

It's compiling from source code, so it should work on either one. But I've only tested on 32-bit.

---

### Post by moore.bryan on 2010-10-24
Jumping-in on this thread because @CompShrink helped-out in another thread.

Make sure to install build-essential and *not* build-essential**s**; one exists, the other doesn't.

In my case (on an Asus 1005HA with the AR9285, running Maverick), the 2010-09-12 ath9k driver doesn't offer a permanent solution. I've downloaded and installed the bleeding-edge compat-wireless and am running it now... let's keep our collective fingers crossed.

P.S.: this is considered "fixed" by the developers, as per the Launchpad bug for it.

---

### Post by stead21 on 2010-10-24
> **CompShrink said:**
> It's compiling from source code, so it should work on either one. But I've only tested on 32-bit.

I just wanted to confirm this fix works. I ran the test on Ubuntu 64-bit. I have a Lenovo G560 Laptop (Core i5 Processor). Internet has been stable all day even coming back from suspend and hibernate. Under connection Information, speed is now between 125-150MB/s.

---

### Post by walt.smith1960 on 2010-10-24
Is this a PCI, PCMCIA or USB?  I recently bought a Netgear WNA1100 USB adapter that I think uses the same chipset.  From memory the output of lsusb is 0846:9030.  For Lucid I installed this .deb file from sourceforge:

[http://sourceforge.net/projects/ath9k-htc/files/](http://sourceforge.net/projects/ath9k-htc/files/)

It extracted and installed without issue.  I couldn't get it to install in Maverick but I see there is supposed to be a fix for Maverick posted.  I was able to get NDISwrapper to install 32 bit WinXP drivers in Maverick.  The only problem I've had with the ath9k-htc is the adapter will infrequently not unsuspend.  Infrequently is perhaps once every 20-30 suspend/unsuspend cycles.  A restart fixes it.

---

### Post by stead21 on 2010-10-25
> **walt.smith1960 said:**
> Is this a PCI, PCMCIA or USB?  I recently bought a Netgear WNA1100 USB adapter that I think uses the same chipset.  From memory the output of lsusb is 0846:9030.  For Lucid I installed this .deb file from sourceforge:

[http://sourceforge.net/projects/ath9k-htc/files/](http://sourceforge.net/projects/ath9k-htc/files/)

It extracted and installed without issue.  I couldn't get it to install in Maverick but I see there is supposed to be a fix for Maverick posted.  I was able to get NDISwrapper to install 32 bit WinXP drivers in Maverick.  The only problem I've had with the ath9k-htc is the adapter will infrequently not unsuspend.  Infrequently is perhaps once every 20-30 suspend/unsuspend cycles.  A restart fixes it.

This is internal to my laptop motherboard so i would assume this is PCI.

---

### Post by walt.smith1960 on 2010-10-25
Internal would be PCI or PCIe so that .deb would not work for you.  Doh, I just checked and my Asus eee1005HA has this:

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01). 

This has had native support since Karmic and has been flawless on this machine.  I wonder what's different on yours?

---

### Post by Dead ChexMix on 2010-10-25
Thanks guys for the solutiuons...Im running Ubuntu 10.10 64 bit...im gona try the soloution lets hope it works
 
Will write back if worked
 
No work

---

### Post by stead21 on 2010-10-25
> **Dead ChexMix said:**
> Thanks guys for the solutiuons...Im running Ubuntu 10.10 64 bit...im gona try the soloution lets hope it works
 
Will write back if worked
 
No work

Ok, this didn't work for me until I actually did a fresh install and I plugged my laptop into a wired connection and did all of my updates via wired, then I ran the solution from CompShrink.

---

### Post by Dead ChexMix on 2010-10-25
> **stead21 said:**
> Ok, this didn't work for me until I actually did a fresh install and I plugged my laptop into a wired connection and did all of my updates via wired, then I ran the solution from CompShrink.
 
 
Ahh...Okay Ill try that (Hopefully my ehthernet wkill work -.-)

---

### Post by moore.bryan on 2010-10-26
It's been a couple days now and I *finally* have a stable connection. I had to download and compile the compat-wireless bleeding-edge stuff from the [kernel.org]("http://wireless.kernel.org/en/users/Download#Requirements_for_bleeding_edge") website.

---

### Post by tstngry on 2010-10-26
I don't have a atheros card, but if you install "ndisgtk" from synaptic it gives you a nice gui that allowed me to install my windows drivers without any problem. These drivers actually worked better then the ones that were there already (B43 & STA for me). The only problem i have is that wpa_supplicant does not support ndiswrapper driver unless you compile it specifically to do so (which is what im working one now). Hope you get it working, good luck.

---

### Post by Dead ChexMix on 2010-10-26
> **tstngry said:**
> I don't have a atheros card, but if you install "ndisgtk" from synaptic it gives you a nice gui that allowed me to install my windows drivers without any problem. These drivers actually worked better then the ones that were there already (B43 & STA for me). The only problem i have is that wpa_supplicant does not support ndiswrapper driver unless you compile it specifically to do so (which is what im working one now). Hope you get it working, good luck.
 
 
I've tried to install The wrapper. But there is no .inf drvier present for my card. Using the Windows hardware manger to find info about the DriverS there all .sys.
 
So here are the soloutions im going to try in the order i will try them...
 
1. Hooking up to my network Via ethernet (sorry if I spelled that wrong) and updating then retrying CompShriks soloution.
 
2. Trying the Bleeding edge drivers
 
3. Attempting to find the .inf driver for my card (The Atheros website it selfish and doesnt let you get drivers from them) and then using the ndisgtk set to run it
 
4. Punt

---

### Post by MYHEADHURTS on 2011-03-06
Hello,
 I have the same card ,(the ethonet works),I installed the ath9k driver but it still won't work and says wirelrss disabled,Iv done a lot of reading about this I'v postedmy own question with no reply
  I tried the compshrink solution and it did not,work it just took of the driver, so I put it back and still nothing,I would be very great fullfor any corospondents at all.,,,MHH

(on Maverick) I have the phisical switch on.
this is wer I got the ath9k,I didn't build it

[http://apt.ubuntu.com/p/linux-backports-modules-wireless-maverick-generic](http://apt.ubuntu.com/p/linux-backports-modules-wireless-maverick-generic)
I also came across this
**Enabling ath9k**

 To enable ath9k, you must first enable mac80211: 

Networking  --->
  Wireless  --->
    <M> Improved wireless configuration API
    <M> Generic IEEE 802.11 Networking Stack (mac80211)You can then enable ath9k in the kernel configuration under 

Device Drivers  --->
  
[*] Network device support  --->
        Wireless LAN  --->

          <M>   Atheros 802.11n wireless cards support

at [http://linuxwireless.org/en/users/Drivers/ath9k#Enabling_ath9k](http://linuxwireless.org/en/users/Drivers/ath9k#Enabling_ath9k)
The above makes no sense because threr is no networking,ther is network,under places,I can't find Device Drivers,,,ther is,,Aditional Drivers under Adminasteration, that says ther are no proprietary drivers in use.

I want to upgrade to Studio Ubuntu ,it says you get no wireless with it,I thought I'd work out how to get it working first, I mite aswell do that now as I am getting no wer with the wireless, 
 My details are hear,,
 
[http://ubuntuforums.org/showthread.php?t=1687259&highlight=AR9285+Wireless](http://ubuntuforums.org/showthread.php?t=1687259&highlight=AR9285+Wireless)
 thanks. J

---

### Post by moore.bryan on 2011-03-07
I know it sounds silly, but have you made sure your lappie/netbook doesn't have it's wireless turned-off by a physical switch or something?

Did you build the ath9k from compat-wireless; i.e., how did you install it?

---

### Post by BkkBonanza on 2011-03-07
I have this card and it works fine with the proper Ath9k drivers. They should be available native since around 2.6.30 or so (not sure exact release). I don't think you should need to use Ndis drivers at all unless you are using some very old release. Even many old releases worked with Ath9k when using the compat-wireless back ports.

The nice thing about the Ath9k drivers is they support master mode allowing use as an access point (which I've done). On recent versions my card was detected and available at boot so I'd be sure to check your wifi card isn't set physically power off.

See this page: [http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k)
They say 2.6.32 is recommended but 2.6.27 was first native kernel.

---

### Post by arrimapirate on 2011-06-12
I have the same card, AR9285, and the only issue i have is that of the 15 wireless networks around my house it cant see any of them except the one created by my android phone.

Running Ubuntu 10.10, nm-tool output:

- Device: wlan0 -------------------------------------------------  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        xxxxxxxxxxxx

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

---

### Post by PlsNoAbreviations on 2012-01-06
Did anyone find the solution to this? I just got errors when trying the first solution.  Using Ubuntu 10.10 Maverick Meerkat installed via Wubi and have the Atheros AR9285 Wireless Card and can not connect.  It worked on Ubuntu 11.11 and I'd like to learn to do this so I can check out older versions too.

---

