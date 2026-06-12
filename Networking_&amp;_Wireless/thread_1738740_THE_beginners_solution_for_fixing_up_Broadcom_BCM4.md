---
title: "THE beginners solution for fixing up Broadcom BCM43xx and Wireless Cards"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by jasonmanchu on 2011-04-25
Hi everyone! This is my first post, especially special because i am posting from Ubuntu 11.04 Natty Narwhal.
I am here to post a solution that is so much simpler and with no hassle for Broadcom BCM43xx, [COLOR=Green]with STA drivers.[/COLOR]

Just some system specs:
Dell Latitude XT2
Dual Boot Windows 7 Professional and Ubuntu 11.04
Dell Wireless 1510 WLAN card.

I have been googling everywhere for this solution for at least 4 days, stuff from linuxquestions.org and ubuntuforums.org. It would be very complicated for me to try and explain the time i wasted over the past few days achieving nothing.
Then i found this page:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[COLOR=Red]
[/COLOR]
So I shall try and attempt to compress that page down to a few instructions.
NOTE: No ndiswrapper, b43-cutter etc needed! All that is needed is Ubuntu Software Center and some files on the Ubuntu iso.
__________________________________________________________________________________________________________________________

[COLOR=Red]1. First it is a good idea to check you actually have the Broadcom BCM43xx hardware. So open terminal and type in:
[/COLOR]```
lspci -vvnn | grep 14e4 
```[COLOR=Red]An example of the output should say something like this:
[/COLOR]```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
```[COLOR=Red]
What we are looking for is:
[/COLOR][14e4:432b]
[COLOR=Red][COLOR=Green]14e4 is the code for Broadcom. If the above command comes with [14e4:....] then you have Broadcom hardware
[/COLOR][/COLOR][COLOR=Green]STA - BCM4311, BCM4312, BCM4313, BCM4321, BCM4322, BCM43224, BCM43225, **BCM43227, **BCM43228 [/COLOR][COLOR=Red]
[/COLOR]
[COLOR=Red] 
2. 
Open the Ubuntu Iso in Archive manager or Archive mounter.
Go to these locations below[/COLOR][COLOR=Red] and double click on the debian (.deb) file located there.[/COLOR]
[COLOR=Red]If you are running 11.04 you will only need the first two files[/COLOR]
../pool/main/d/dkms 
../pool/restricted/b/bcmwl 
[COLOR=Gray]../pool/main/p/patch[/COLOR]
[COLOR=Gray]../pool/main/f/fakeroot [/COLOR]

3.
[COLOR=Red]Restart your system
4.
If things don't work try this:
[/COLOR]Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **STA** drivers can be activated for use. 
[COLOR=Red] 
Hopefully this works for beginners to linux like me![/COLOR][COLOR=Red]
[/COLOR]

---

### Post by MasterNetra on 2011-04-27
I have all these files installed from the internet courtesy of my USB Wireless Adapter, while additional drivers windows says STA is working, I still don't get no signals for it at all. And yes I am well in range of my wireless connection. Using a BCM4312.

---

### Post by james_mcl on 2011-04-27
Jason,

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) is divided into two sections. The section describing the procedure for bcmwl-kernel-source and the STA drivers, which you reproduce here, does not apply to every 43XX card - it certainly doesn't apply to my 4318.

It is stated that either procedure can be used for the 4311 and 4312, but for most cards only one procedure is correct.

For:
BCM4313, BCM4321, BCM4322, BCM43224, BCM43225, **BCM43227, and **BCM43228 
the correct procedure is that described in [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)

By contrast, for
BCM4301, BCM4306/2, BCM4306/3, BCM4311, BCM4312, BCM4318, and BCM4320

the procedure at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers) should be followed.

PLEASE reread the WifiDocs page and amend your original post accordingly.

James McLaughlin.

---

### Post by jasonmanchu on 2011-04-28
Sorry about that, i knew there were two parts, i forgot to mention that i only looked at the STA drivers section. As the b43 section requires b43 cutter and other stuff. I am currently fixing my original post and will amend accordingly

---

### Post by Lucky8Media on 2011-04-28
The easiest way we have found to activate BCM 43XX:

[http://ubuntuforums.org/showthread.php?t=1742147](http://ubuntuforums.org/showthread.php?t=1742147)

---

### Post by jasonmanchu on 2011-04-28
Perhaps we should create a list of Wireless cards that work with this BCM43xx method? Or is there a list already?

---

### Post by jingglang on 2011-05-01
My Axioo CNWP-015 has Broadcom 4312 LP-PHY network card. In my case installing firmware-b43-lpphy-installer from synaptic did the trick. In the middle of installation progress, it downloaded the appropriate driver.

---

### Post by Tshann on 2011-08-29
Hi,
  I went through a great deal to try to get this puppy to work in Kubuntu 11.04. The final solution - for my rig (HP DV6233se) was to uninstall the bcmwl-kernel-source. I did confirm that the bcm43xx was blacklisted and removed the blacklist - didn't work. No fix on the broadcom sta driver ever worked. But after installing firmware-b43-installer (which automatically brought in cutter) I could get it to work, but I had to log into a terminal every time @ boot up and type in sudo modprobe b43. It was only after removing the above source file and rebooting that my rig came up with a working wireless for Kubuntu 11.04. Hope this is useful for someone else.

Peace

---

### Post by northd_tech on 2011-08-30
> **jasonmanchu said:**
> Perhaps we should create a list of Wireless  cards that work with this BCM43xx method? Or is there a list  already?
Here are a few 'required reading' references for Broadcom wireless interfaces:

 [https://help.ubuntu.com/community/Wi...Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")
  
Broadcom's proprietary "STA" driver:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Linuxwireless.org "b43" Broadcom page
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

I also found this EXTREMELY helpful diagram at the Fedoraforum:
[http://www.fedoraforum.org/forum/showthread.php?t=239922](http://www.fedoraforum.org/forum/showthread.php?t=239922)
```
                               [COLOR=Red]**lspci -vvnn | grep 14e4**[/COLOR]
                                         |
                                Any of these listed?
                                        4301
                                        4303
                                        4306
                                        4309
                                        4311
                                        4312
                                        4313 
                                        4318
                                       /    \
                                      /      \
                                     /        \
                                    /          \
                                  Yes           No
                                  /              \
                                 /                \
                                /                  \
                             [COLOR=Red]**lsmod **[/COLOR]               4310?
                              /                   /   \
                             /                   /     \
                            /                  Yes      No
                          b43                  /         \
                        loaded?               /           \
                        /    \          [COLOR=Sienna] ndiswrapper[/COLOR]   4321,43224
                       /      No                        4322,43225
                      /        \                         4328,43227
                     /          \                         43XG,43228
                   Yes       b43legacy                      /   \
                   /          loaded?                      /     \
                  /           /     \                    Yes      No
                 /          Yes      No                  /         \
                /           /         \                 /           \
             4306?         /         4311?        [COLOR=Blue]broadcom-wl[/COLOR]      4320?
            4311?      Install        4312?                     (from lsusb
           4318?      version 3        4313?                   or other means)
           /   \      firmware         /   \                        /    \
          /     \                     /     \                      /      \
        Yes      No                 Yes      No                  Yes       No
        /         \                 /         \                  /          \
       /           \               /           \                /            \
b43-openfwwf     Install     [COLOR=Blue]broadcom-wl[/COLOR]   [COLOR=Sienna]ndiswrapper[/COLOR]    b43-openfwwf   [COLOR=Sienna]ndiswrapper[/COLOR]
    or          version 4                                       or
  Install       firmware                                    rndis_wlan
 version 4
 firmware
 -------------------------------------------------------------------------------------
```Although some of the commands might need 'translation' for Ubuntu and Debian Linux, there is an EXCELLENT reference for Broadcom wireless on that page.

EDIT:  Let's not forget the "WiFi" search engine:
[http://www.x11wifi.com/wifi.php?q=Broadcom](http://www.x11wifi.com/wifi.php?q=Broadcom)

---

### Post by northd_tech on 2011-08-30
For links to the Ubuntu .DEB packages for "offline" Broadcom wireless network setup, see here:

"broadcom" packages ("STA" driver & "wl" module)
[http://packages.ubuntu.com/search?searchon=names&keywords=broadcom](http://packages.ubuntu.com/search?searchon=names&keywords=broadcom)

"b43" packages 
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=b43](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=b43)

If you need to see which packages to download, these terminal commands should be helpful:

```
uname -a
cat /etc/lsb-release
cat /etc/issue
```

Of course, you will first need to determine whether to get 32 bit "i386" or 64 bit packages (usually either "amd64" or "ia64" for "PC" architectures- read the results of the **uname -a** terminal command carefully).

---

### Post by michael2009 on 2011-09-11
[HTML]I have been googling everywhere for this solution for at least 4 days, stuff from linuxquestions.org and ubuntuforums.org. It would be very complicated for me to try and explain the time i wasted over the past few days achieving nothing.
Then i found this page:
https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx


So I shall try and attempt to compress that page down to a few instructions.
NOTE: No ndiswrapper, b43-cutter etc needed! All that is needed is Ubuntu Software Center and some files on the Ubuntu iso.[/HTML]I am glad you found a solution for your hardware. I also found the above page helpful initially, in identifying the correct driver and relevant packages for my Compaq Evo n400c, which is using a LINKSYS PCMCIA wireless card that requires the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318], and running lubuntu 11.04. 

According to the documentation, I should install the b43 driver. I followed the installation of both the b43-fwcutter and **[B][FONT=Courier New]firmware-b43-installer[/FONT]** [/B][FONT=Arial]packages.When this did not work, I tried with the 
[FONT=Courier New]firmware-b43-lpphy-installer[/FONT] package, but it still did not work, despite repeated removals and 
reinstallations. Finally, I used the ndiswrapper for the driver on the Linksys installation CD as a last resort, 
and it is now working. 

The strange thing about all this is that the wireless drivers installed automatically on the same hardware 
when completing previous Ubuntu installations i.e. JJ, 10.04 and 10.10.[/FONT] [FONT=Arial]Is this an [/FONT][FONT=Arial]issue with 11.04 Natty Narwhal 
only, and does it mean that the b34 drivers are no longer included in the installation?[/FONT] [FONT=Arial]I ask this because I also tried 
installing 11.04 on my wife's Compaq Presario laptop and was unable to get the built in wireless card to work, yet 
the previous installation of Ubuntu 10.10 had no such problems, installing the drivers automatically. Her wireless is 
now working fine again, running 10.10. So until I find a workable solution on 11.04, I am very wary of 
upgrading from 10.10...

Am I missing something?

[/FONT]

---

### Post by Tri-Booter on 2011-11-07
I have tried all of these and still not working... 
Broadcom BCM4309 802.11a/b/g (rev 02)

---

