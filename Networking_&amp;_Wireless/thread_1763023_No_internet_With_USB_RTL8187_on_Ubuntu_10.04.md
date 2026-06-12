---
title: "No internet With USB RTL8187 on Ubuntu 10.04"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by Bonanzaman on 2011-05-19
OK, after searching several dozen posts I still have no clear answer to a problem connecting to the internet with my Alfa AWUS036H Wireless USB adaptor. (Computer is an Aspire 5516 w/ AMD Athlon 64 processor)The device shows up in the network manager, (with great signal strength on many local AP's)and works well with Aircrack for security testing, which is why I got it in the 1st place. However my onboard Antheros wifi card just does not receive as well, thus I'd like to be able to use the Alfa for internet. Any thoughts here would be appreciated....... I read one post here suggesting giving up on the RTL8187 chipset altogether!

---

### Post by Gelupah on 2011-05-21
Running into the same problems here, sad to say the Alfa USB card RTL8187 works greats when it does (connects fine with windows,sad), but I haven't been able to configure it with Ubuntu 10.10 yet.

When I try connecting to an open AP, the connection icon keeps going around and around (one lightlit up) and eventually gives up, with a nice 'connection failed' message. When I connect with the internal wifi card, all works fine, but signal is awful... I tried disabling the internal card, blacklisting the module on startup etc, but I don't think the internal card is the causeofmy ext one malfunctioning...

Driver problem I guess? Any help would be greatly appreciated!

---

### Post by Bonanzaman on 2011-05-21
I have found several convoluted "work arounds" involving disabling Network manager, or connecting manually at each log on through terminal scripts, but these are 2-3 year old posts, and I was in hopes someone had come up with a little better fix. Alternatly, I'd love to hear of anyone's sucess with another High Power USB unit that works with the aircrack suite as well as connect to the internet smoothly!

---

### Post by Bonanzaman on 2011-05-21
OK, I blacklisted my laptops internal Atheros card driver, rebooted, and now have connectivity, but Veeeeeeery Sloooooow! So we have some progress, now just need to get the speed back up to where the internal card was. Ideas here??

---

### Post by Bonanzaman on 2011-05-23
The struggle continues.....too bad I am alone here...tried installing the Realtek xp driver using ndiswrapper, from this link: [http://quilombo.wordpress.com/2008/03/07/realtek-rtl8187b-working-in-ubuntu-710-using-ndiswrapper/](http://quilombo.wordpress.com/2008/03/07/realtek-rtl8187b-working-in-ubuntu-710-using-ndiswrapper/)
but still still no joy...... I realize there may be differences due to my 10.04 install, but there seems to be no info on this that is not a couple of years old. The x64 driver was tried 1st since that is what my system is, and tried to install the .inf file into ndiswrapper, but it returned "invalid driver", so I tried the 32 bit, which it accepted, however, I am confused by the step 7 instruction to "Extract the USB nic and connect it again"
Is this simply to unplug the card and plug it back in? If so, then I still do not have the correct module loaded.  I continue to hope to eventually sort this out, so the one sided dialogue goes on..........

---

### Post by mockingbird on 2011-05-23
The solution is to disable and blacklist the driver that ships with Ubuntu (It is quite outdated and is no longer being maintained), and to compile and install the driver from Realtek's site.

---

### Post by Bonanzaman on 2011-05-23
Thanks, mockingbird for the reply!!...the downloaded windows driver from Realtek shows as installed on the wireless network driver list, (in System-Administration)but the rtl8187 showing up after running lsmod seems to be the only driver (which I have blacklisted), unless it is mac80211 which is associated with some of the same modules...I wonder if this is  the Ubuntu pre-loaded driver I need to blacklist as well? Also, since the windows driver is not seen in the lsmod list, I assume I need to figure out how to associate it with the correct module.

---

### Post by mockingbird on 2011-05-24
Let me clarify:

Remove ndiswrapper, then blacklist the rtl818x (x denoted the revision.  Mine was rtl8180) module (Which is the native Linux realtek module) via the file /etc/modprobe.d/blacklist.conf.

With my card (RTL8185) the module is "rtl8180", and the module I compiled from Realtek's site is "r8185b", so I have to make sure that they don't conflict, hence the blacklisting.  The default driver like I said was old and buggy, the new one works great.

Don't download the Windows drivers from there, download the _LINUX_ drivers and then compile them yourself.  Read the instructions, it's pretty straightforward.  If you have any problems compiling, reply to this thread.

---

### Post by Bonanzaman on 2011-05-24
Thanks much for the additional info, mockingbird.....we'll give it a try and see..........

---

### Post by Bonanzaman on 2011-05-24
I got the driver downloaded, but have not gotten far..sorry...the 1st step in the readme file is to run the "make" script (it actually is named "Makefile", but when I try to "run in terminal" the terminal opens for a split second and closes, with no response. I know I'm overlooking something out of the chute, but it's been about 3 years since I have worked with any Linux at all.......?

---

### Post by mockingbird on 2011-05-24
Ok, first of all, is this the name of the file you got?

rtl8187L_linux_26.1040.0820.2010.release.tar.gz

This is the correct driver.

Now open up a terminal window.  CD into the directory where you extracted the file, and run

"make"

When it is done (and only if it has completed successfully), type:

"make install"

If you install it without getting rid of the old ndiswrapper driver or without blacklisting the rtl818x driver first, you may have problems.

---

### Post by Bonanzaman on 2011-05-24
That"s the driver...I have extracted it to the desktop. cd'ed to the desktop, cannot get "make" command to run.....

```
mark@mark-laptop:~/Desktop$ make
make: *** No targets specified and no makefile found.  Stop.
mark@mark-laptop:~/Desktop$ make rtl8187L_linux_26.1040.0820.2010.release.tar.gzmake: Nothing to be done for `rtl8187L_linux_26.1040.0820.2010.release.tar.gz'.
mark@mark-laptop:~/Desktop$ /rtl8187L_linux_26.1040.0820.2010.release.tar.gz sudo make
bash: /rtl8187L_linux_26.1040.0820.2010.release.tar.gz: No such file or directory
mark@mark-laptop:~/Desktop$ /rtl8187L_linux_26.1040.0820.2010.release sudo make
bash: /rtl8187L_linux_26.1040.0820.2010.release: No such file or directory
mark@mark-laptop:~/Desktop$ make rtl8187L_linux_26.1040.0820.2010.release
make: Nothing to be done for `rtl8187L_linux_26.1040.0820.2010.release'.
mark@mark-laptop:~/Desktop$ 

```
I should know what's missing here............

---

### Post by dhave-dhave on 2011-05-25
I'm running 11.04 and have very good results with an Alfa USB Realtek 8187 adapter connected to a Thinkpad T420. I'm using a USB wifi adapter since I'm at a long distance from my router, and the built-in wifi adapter on the Thinkpad doesn't pull in the signal as well. My Alfa adapter has a 15" antenna.

I've only been running Ubuntu for a few weeks (my join date is deceptive), but I don't remember doing anything special to get this adapter to work. The relevant module name is rtl8187.

---

### Post by mockingbird on 2011-05-25
> **Bonanzaman said:**
> That"s the driver...I have extracted it to the desktop. cd'ed to the desktop, cannot get "make" command to run.....

Mark,

tar -xzvf rtl8187L_linux_26.1040.0820.2010.release.tar.gz
cd <directory it unzipped to>
make
make install

Good luck.  Come on #ubuntu on freenode, I'll be on.

---

### Post by Bonanzaman on 2011-05-25
yep,.........
```
ark@mark-laptop:~/Desktop$ sudo tar -xzvf rtl8187L_linux_26.1040.0820.2010.release.tar.gz
[sudo] password for mark: 
rtl8187L_linux_26.1040.0820.2010.release/
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/scatterwalk.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/rtl_crypto.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/cipher.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/compress.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_wx.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/kmap_types.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/Makefile
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/digest.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_crypt_tkip.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_crypt_wep.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_softmac.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/scatterwalk.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/license
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_module.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_crypt.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_crypt.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/tags
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/readme
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_softmac_wx.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/api.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_crypt_ccmp.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/michael_mic.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/internal.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/proc.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/aes.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/arc4.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_tx.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_rx.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/autoload.c
rtl8187L_linux_26.1040.0820.2010.release/Makefile
rtl8187L_linux_26.1040.0820.2010.release/wlan0down
rtl8187L_linux_26.1040.0820.2010.release/RadioPower.sh
rtl8187L_linux_26.1040.0820.2010.release/ReadMe
rtl8187L_linux_26.1040.0820.2010.release/wlan0up
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/changes
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_dm.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_wx.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/install
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_pm.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/Makefile
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_dm.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/license
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_hw.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_93cx6.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/readme
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_wx.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/copying
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225z2.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/authors
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_pm.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_93cx6.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225.h
rtl8187L_linux_26.1040.0820.2010.release/release_note
rtl8187L_linux_26.1040.0820.2010.release/wlan0dhcp
rtl8187L_linux_26.1040.0820.2010.release/wpa1.conf
rtl8187L_linux_26.1040.0820.2010.release/wpa_supplicant-0.5.5.zip
rtl8187L_linux_26.1040.0820.2010.release/ifcfg-wlan0
mark@mark-laptop:~/Desktop$ make
make: *** No targets specified and no makefile found.  Stop.
mark@mark-laptop:~/Desktop$ cd Desktop
bash: cd: Desktop: No such file or directory
mark@mark-laptop:~/Desktop$ make install
make: *** No rule to make target `install'.  Stop.
mark@mark-laptop:~/Desktop$ 

```

make command still returns no such file, no targets, etc......

(don't have a clue where "#ubuntu freenode" would be)!

---

### Post by mockingbird on 2011-05-25
I'm on now if you need a hand.

You forgot "cd rtl8187L_linux_26.1040.0820.2010.release/rtl8187/" first.

---

### Post by mockingbird on 2011-05-25
> (don't have a clue where "#ubuntu freenode" would be)!
It's on IRC.

---

### Post by beew on 2011-05-25
It is probably your card. I use a netcore usb wireless card with the rtl8187 and it works out of the box for Lucid, Maverick, Natty, LMDE and Fedora 14 and 15 as well.

Here is the card.[http://www.cty.ca/ProductDetails.asp?pid=3267](http://www.cty.ca/ProductDetails.asp?pid=3267)

Unless you like tinkering, otherwise it may be better just get a different card, costs about $15.

---

### Post by Bonanzaman on 2011-05-25
Still getting soundly thrashed here:

```
mark@mark-laptop:~$ cd Desktop
mark@mark-laptop:~/Desktop$ cd rtl8187L_linux_26.1040.0820.2010.release/rtl8187/bash: cd: rtl8187L_linux_26.1040.0820.2010.release/rtl8187/: Permission denied
mark@mark-laptop:~/Desktop$ sudo cd rtl8187L_linux_26.1040.0820.2010.release/rtl8187/
[sudo] password for mark: 
sudo: cd: command not found
mark@mark-laptop:~/Desktop$ 

```

```
mark@mark-laptop:~/Desktop$ sudo tar -xzvf rtl8187L_linux_26.1040.0820.2010.release.tar.gz
[sudo] password for mark: 
rtl8187L_linux_26.1040.0820.2010.release/
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/scatterwalk.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/rtl_crypto.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/cipher.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/compress.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_wx.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/kmap_types.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/Makefile
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/digest.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_crypt_tkip.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_crypt_wep.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_softmac.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/scatterwalk.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/license
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_module.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_crypt.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_crypt.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/tags
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/readme
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_softmac_wx.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/api.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_crypt_ccmp.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/michael_mic.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/internal.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/proc.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/aes.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/arc4.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_tx.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_rx.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/autoload.c
rtl8187L_linux_26.1040.0820.2010.release/Makefile
rtl8187L_linux_26.1040.0820.2010.release/wlan0down
rtl8187L_linux_26.1040.0820.2010.release/RadioPower.sh
rtl8187L_linux_26.1040.0820.2010.release/ReadMe
rtl8187L_linux_26.1040.0820.2010.release/wlan0up
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/changes
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_dm.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_wx.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/install
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_pm.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/Makefile
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_dm.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/license
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_hw.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_93cx6.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/readme
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_wx.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/copying
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225z2.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/authors
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_pm.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_93cx6.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225.h
rtl8187L_linux_26.1040.0820.2010.release/release_note
rtl8187L_linux_26.1040.0820.2010.release/wlan0dhcp
rtl8187L_linux_26.1040.0820.2010.release/wpa1.conf
rtl8187L_linux_26.1040.0820.2010.release/wpa_supplicant-0.5.5.zip
rtl8187L_linux_26.1040.0820.2010.release/ifcfg-wlan0
mark@mark-laptop:~/Desktop$ cd rtl8187L_linux_26.1040.0820.2010.release/rtl8187/bash: cd: rtl8187L_linux_26.1040.0820.2010.release/rtl8187/: Permission denied
mark@mark-laptop:~/Desktop$ sudo cd rtl8187L_linux_26.1040.0820.2010.release/rtl8187/
sudo: cd: command not found
mark@mark-laptop:~/Desktop$ cd ~
mark@mark-laptop:~$ cd rtl8187L_linux_26.1040.0820.2010.release/rtl8187/
bash: cd: rtl8187L_linux_26.1040.0820.2010.release/rtl8187/: No such file or directory
mark@mark-laptop:~$ 

```

---

### Post by mockingbird on 2011-05-25
> mark@mark-laptop:~$ cd Desktop
mark@mark-laptop:~/Desktop$ cd rtl8187L_linux_26.1040.0820.2010.release/rtl8187/bash: cd: rtl8187L_linux_26.1040.0820.2010.release/rtl8187/: Permission denied
mark@mark-laptop:~/Desktop$ sudo cd rtl8187L_linux_26.1040.0820.2010.release/rtl8187/
[sudo] password for mark: 
sudo: cd: command not found
mark@mark-laptop:~/Desktop$
There's no reason why this directory should be password protected.

Try "sudo chown mark rtl8187L_linux_26.1040.0820.2010.release/rtl8187/"

Thent ry to CD into it.

---

### Post by Bonanzaman on 2011-05-25
OK, so that opened the floodgate of errors below........!



```
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_network’ 
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_network’ 
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_network’ 
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_network’ 
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_network’ 
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3291: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3291: error: ‘IEEE80211_NOLINK’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_commit’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3299: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3308: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3314: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3315: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3316: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘r8180_set_multicast’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3359: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘r8180_set_mac_adr’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3375: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_irq_rx_tasklet’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3502: error: variable ‘stats’ has initializer but incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3503: error: unknown field ‘signal’ specified in initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3503: warning: excess elements in struct initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3503: warning: (near initialization for ‘stats’)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3504: error: unknown field ‘noise’ specified in initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3504: warning: excess elements in struct initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3504: warning: (near initialization for ‘stats’)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3505: error: unknown field ‘rate’ specified in initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3505: warning: excess elements in struct initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3505: warning: (near initialization for ‘stats’)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3506: error: unknown field ‘freq’ specified in initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3506: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3506: warning: excess elements in struct initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3506: warning: (near initialization for ‘stats’)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3502: error: storage size of ‘stats’ isn’t known
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3565: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3573: error: implicit declaration of function ‘ieee80211_rx’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3587: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3502: warning: unused variable ‘stats’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_ioctl’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3606: error: implicit declaration of function ‘ieee80211_wpa_supplicant_ioctl’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: At top level:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3749: error: ‘ieee80211_xmit’ undeclared here (not in a function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8187_usb_probe’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3769: error: implicit declaration of function ‘alloc_ieee80211’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3769: warning: assignment makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3780: warning: assignment makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3842: error: implicit declaration of function ‘free_ieee80211’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8187_usb_disconnect’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3870: warning: assignment makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3875: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_try_wake_queue’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3981: error: implicit declaration of function ‘ieee80211_wake_queue’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘SetZebraRFPowerState8187’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3990: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4071: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4071: error: ‘LED_CTL_POWER_OFF’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4077: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4077: error: ‘LED_CTL_POWER_ON’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘MgntActSet_RF_State’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4188: error: implicit declaration of function ‘ieee80211_disassociate’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘GPIOChangeRFWorkItemCallBack’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4233: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4233: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4233: warning: initialization from incompatible pointer type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4233: error: invalid use of undefined type ‘struct ieee80211_device’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4234: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4235: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4271: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4272: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4275: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4276: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4289: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘gpio_change_polling’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4305: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4308: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4308: error: dereferencing pointer to incomplete type
make[2]: *** [/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.o] Error 1
make[1]: *** [_module_/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-31-generic'
make: *** [modules] Error 2
mark@mark-laptop:~/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187$ tar -xzvf rtl8187L_linux_26.1040.0820.2010.release.tar.gz
tar: rtl8187L_linux_26.1040.0820.2010.release.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
mark@mark-laptop:~/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187$ clear

mark@mark-laptop:~/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187$ make
make -C /lib/modules/2.6.32-31-generic/build M=/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-31-generic'
  CC [M]  /home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.o
In file included from /home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:60:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187.h:62:36: error: /home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/../ieee80211/ieee80211.h: Permission denied
In file included from /home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187.h:64,
                 from /home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:60:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.h:122: error: expected declaration specifiers or ‘...’ before ‘LED_CTL_MODE’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.h:128: error: expected declaration specifiers or ‘...’ before ‘LED_CTL_MODE’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.h:134: error: expected declaration specifiers or ‘...’ before ‘LED_CTL_MODE’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.h:140: error: expected declaration specifiers or ‘...’ before ‘LED_CTL_MODE’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.h:146: error: expected declaration specifiers or ‘...’ before ‘LED_CTL_MODE’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:102: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘DefaultChannelPlan’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘write_nic_byte_E’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:178: error: implicit declaration of function ‘ieee80211_priv’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘check_nic_enought_desc’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:547: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘tx_timeout’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:557: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_update_msr’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:625: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:631: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:631: error: ‘IEEE80211_LINKED’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:631: error: (Each undeclared identifier is reported only once
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:631: error: for each function it appears in.)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:633: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:635: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:637: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8187_set_rxconf’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:736: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:745: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:750: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8187_rx_isr’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1101: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_hard_data_xmit’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1153: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1153: error: ‘IEEE80211_FCTL_MOREFRAGS’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1157: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1165: error: implicit declaration of function ‘ieee80211_stop_queue’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8187_lptx_isr’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1262: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8187_net_update’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1292: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1294: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1297: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1298: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1304: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8187_beacon_tx’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1313: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1319: error: implicit declaration of function ‘ieee80211_get_beacon’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1319: warning: assignment makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1341: error: implicit declaration of function ‘msleep_interruptible_rtl’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1349: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8187_nptx_isr’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1363: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_tx’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1390: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1489: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1489: error: ‘WLAN_CAPABILITY_SHORT_PREAMBLE’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1510: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8187_usb_initendpoints’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1548: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8187_usb_deleteendpoints’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1618: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8187_link_change’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1676: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_hw_wakeup’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1687: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1687: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1687: warning: initialization from incompatible pointer type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1687: error: invalid use of undefined type ‘struct ieee80211_device’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1688: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘timer_hw_wakeup_wq’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1712: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_rq_tx_ack’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1724: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1724: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1724: warning: initialization from incompatible pointer type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1724: error: invalid use of undefined type ‘struct ieee80211_device’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1725: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_hw_sleep’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1737: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1737: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1737: warning: initialization from incompatible pointer type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1737: error: invalid use of undefined type ‘struct ieee80211_device’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1738: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1753: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_is_tx_queue_empty’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1788: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘sta_rateadaptive8187’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1805: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1821: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:1857: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2122: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_rate_adapter’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2132: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2132: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2132: warning: initialization from incompatible pointer type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2132: error: invalid use of undefined type ‘struct ieee80211_device’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2133: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘timer_rate_adaptive’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2146: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2151: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2151: error: ‘IEEE_B’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2152: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2153: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2153: error: ‘IEEE80211_LINKED’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2156: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2156: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2163: error: implicit declaration of function ‘MSECS’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘IPSEnter’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2205: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2206: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2206: error: ‘IEEE80211_LINKED’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_watch_dog_wq’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2236: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2236: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2236: warning: initialization from incompatible pointer type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2236: error: invalid use of undefined type ‘struct ieee80211_device’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2237: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2245: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2252: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2253: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2253: error: ‘IEEE80211_NOLINK’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2253: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2253: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2254: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2255: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘watch_dog_adaptive’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2294: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2295: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2303: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2303: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2314: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2314: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_init’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2341: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2392: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2396: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2397: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2398: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2399: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2399: error: ‘IEEE_G’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2399: error: ‘IEEE_B’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2490: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2495: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2495: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2495: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2495: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2504: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2504: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2504: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2504: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2508: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2508: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2508: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2508: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2509: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2509: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2509: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2509: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2510: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2510: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2510: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2510: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2512: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2512: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2512: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2513: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2513: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2513: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2514: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2514: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2514: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2593: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2594: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2595: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2595: error: ‘IEEE_SOFTMAC_SCAN’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2596: error: ‘IEEE_SOFTMAC_ASSOCIATE’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2596: error: ‘IEEE_SOFTMAC_PROBERQ’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2597: error: ‘IEEE_SOFTMAC_PROBERS’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2597: error: ‘IEEE_SOFTMAC_TX_QUEUE’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2598: error: ‘IEEE_SOFTMAC_BEACONS’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2599: error: ‘IEEE_SOFTMAC_SINGLE_QUEUE’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2601: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2602: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2603: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2604: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2604: error: ‘IEEE80211_CCK_MODULATION’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2604: error: ‘IEEE80211_OFDM_MODULATION’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2605: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2606: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2607: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2608: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2609: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2610: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2611: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2612: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2613: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2614: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2615: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2617: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2826: error: ‘DefaultChannelPlan’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2828: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2840: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2852: error: implicit declaration of function ‘MAC_ARG’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:2852: warning: too few arguments for format
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_adapter_start’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3057: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_stats’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3153: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3155: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘_rtl8180_up’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3161: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3169: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3170: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3170: error: ‘LED_CTL_POWER_ON’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3184: error: implicit declaration of function ‘ieee80211_softmac_start_protocol’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3187: error: implicit declaration of function ‘ieee80211_reset_queue’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_open’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3201: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3204: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_up’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3220: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_close’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3230: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_down’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3247: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3252: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3252: error: ‘LED_CTL_POWER_OFF’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3255: error: implicit declaration of function ‘ieee80211_softmac_stop_protocol’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3260: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3261: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3262: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3263: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3270: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3276: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3277: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3278: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3287: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_network’ 
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_network’ 
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_network’ 
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_network’ 
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_network’ 
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3290: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_network’ 
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3291: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3291: error: ‘IEEE80211_NOLINK’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_commit’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3299: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3308: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3314: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3315: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3316: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘r8180_set_multicast’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3359: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘r8180_set_mac_adr’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3375: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_irq_rx_tasklet’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3502: error: variable ‘stats’ has initializer but incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3503: error: unknown field ‘signal’ specified in initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3503: warning: excess elements in struct initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3503: warning: (near initialization for ‘stats’)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3504: error: unknown field ‘noise’ specified in initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3504: warning: excess elements in struct initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3504: warning: (near initialization for ‘stats’)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3505: error: unknown field ‘rate’ specified in initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3505: warning: excess elements in struct initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3505: warning: (near initialization for ‘stats’)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3506: error: unknown field ‘freq’ specified in initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3506: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3506: warning: excess elements in struct initializer
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3506: warning: (near initialization for ‘stats’)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3502: error: storage size of ‘stats’ isn’t known
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3565: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3573: error: implicit declaration of function ‘ieee80211_rx’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3587: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3502: warning: unused variable ‘stats’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_ioctl’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3606: error: implicit declaration of function ‘ieee80211_wpa_supplicant_ioctl’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: At top level:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3749: error: ‘ieee80211_xmit’ undeclared here (not in a function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8187_usb_probe’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3769: error: implicit declaration of function ‘alloc_ieee80211’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3769: warning: assignment makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3780: warning: assignment makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3842: error: implicit declaration of function ‘free_ieee80211’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8187_usb_disconnect’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3870: warning: assignment makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3875: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_try_wake_queue’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3981: error: implicit declaration of function ‘ieee80211_wake_queue’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘SetZebraRFPowerState8187’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:3990: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4071: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4071: error: ‘LED_CTL_POWER_OFF’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4077: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4077: error: ‘LED_CTL_POWER_ON’ undeclared (first use in this function)
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘MgntActSet_RF_State’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4188: error: implicit declaration of function ‘ieee80211_disassociate’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘GPIOChangeRFWorkItemCallBack’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4233: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4233: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4233: warning: initialization from incompatible pointer type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4233: error: invalid use of undefined type ‘struct ieee80211_device’
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4234: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4235: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4271: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4272: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4275: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4276: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4289: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c: In function ‘gpio_change_polling’:
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4305: warning: initialization makes pointer from integer without a cast
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4308: error: dereferencing pointer to incomplete type
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c:4308: error: dereferencing pointer to incomplete type
make[2]: *** [/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.o] Error 1
make[1]: *** [_module_/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-31-generic'
make: *** [modules] Error 2
mark@mark-laptop:~/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187$
```

---

### Post by mockingbird on 2011-05-25
You're getting a "permission denied" when compiling which is causing the cascaded errors...

Hmmm...

Ok, let's do it like this:
sudo su 
cd /home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/
make

This will run make in superuser mode.  Let's see wha happens.  This would be a lot easier if we could meet on IRC.

---

### Post by Bonanzaman on 2011-05-25
Thanks, that did it ....make install ran fine as well, unfortunately, the behavior with the new driver is the same as before.....AP's show up fine in the Network manager, and connection establish fine as well, but no internet connection possible. I did delete the ndiswrapper package and files, and blacklisted the native realtek driver and my laptop's internal card driver as well......I'll see if I can get signed up to the IRC chat to go on from here....

---

### Post by mockingbird on 2011-05-25
Please confirm new driver is installed.

lsmod > lsmod.txt

and post the lsmod.txt file.

---

### Post by Bonanzaman on 2011-05-25
You're quite right, bird.....I don't see it in lsmod, only my laptop's card, the "ath5k"...which I needed to un-blacklist to get online at all with the laptop I'm trying to get the realtek to work with.

```
mark@mark-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
joydev                  8740  0 
snd_hda_codec_realtek   203408  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                677027  3 
ttm                    49943  1 radeon
ath5k                 121632  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29329  1 radeon
mac80211              205402  1 ath5k
ath                     7611  1 ath5k
video                  17375  0 
drm                   162345  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
snd                    54180  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              126528  3 ath5k,mac80211,ath
output                  1871  1 video
ati_agp                 5094  0 
soundcore               6620  1 snd
psmouse                63245  0 
lp                      7028  0 
k8temp                  3152  0 
serio_raw               3978  0 
i2c_piix4               8335  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
atl1c                  28083  0 
led_class               2864  1 ath5k
agpgart                31724  3 ttm,drm,ati_agp
shpchp                 28835  0 
parport                32635  2 ppdev,lp
pata_atiixp             3148  0 
ahci                   32200  2 
mark@mark-laptop:~$ lsmod > lsmod.txt
mark@mark-laptop:~$ 

```

I'm not getting anything with the lsmod > lsmod.txt command, though.

---

### Post by Wolf9466 on 2011-05-25
I used compat-wireless (although with the aircrack-ng patches) and it works great for me.

---

### Post by mockingbird on 2011-05-25
> **Bonanzaman said:**
> You're quite right, bird.....I don't see it in lsmod, only my laptop's card, the "ath5k"...which I needed to un-blacklist to get online at all with the laptop I'm trying to get the realtek to work with.
I'm not getting anything with the lsmod > lsmod.txt command, though.
Curious then...  How were you able to see the APs if the module is not loaded!?

Anyways...  We need to find the module and load it.  The question is what is the name of the module.

Ok type:
sudo updatedb
When that finishes type:
locate r818
and show me the output.
I'd also like the output of:
locate rtl81

---

### Post by Bonanzaman on 2011-05-25
OK, bird...here you are, and it's ginormous....

```
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_dm.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_dm.h
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_dm.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_hw.h
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_pm.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_pm.h
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_pm.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225.h
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225z2.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225z2.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_wx.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_wx.h
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_wx.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187.h
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.h
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187l.ko
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187l.mod.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187l.mod.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187l.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/.tmp_versions/r8187l.mod
/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/r8187l.ko
mark@mark-laptop:~$ locate rtl81
/etc/ndiswrapper/net8185/rtl8185.sys
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release.tar.gz
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/Makefile
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ReadMe
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ifcfg-wlan0
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/release_note
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/wlan0dhcp
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/wlan0down
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/wlan0up
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/wpa1.conf
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/wpa_supplicant-0.5.5.zip
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/Makefile
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/aes.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/api.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/arc4.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/autoload.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/cipher.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/compress.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/digest.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/ieee80211.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/ieee80211_crypt.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/ieee80211_crypt.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/ieee80211_crypt_ccmp.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/ieee80211_crypt_tkip.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/ieee80211_crypt_wep.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/ieee80211_module.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/ieee80211_rx.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/ieee80211_softmac.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/ieee80211_softmac_wx.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/ieee80211_tx.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/ieee80211_wx.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/internal.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/kmap_types.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/license
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/michael_mic.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/proc.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/readme
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/rtl_crypto.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/scatterwalk.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/scatterwalk.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/all-wcprops
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/entries
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/props
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/tmp
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/Makefile.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/aes.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/api.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/arc4.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/autoload.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/cipher.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/compress.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/digest.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/ieee80211.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/ieee80211_crypt.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/ieee80211_crypt.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/ieee80211_crypt_ccmp.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/ieee80211_crypt_tkip.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/ieee80211_crypt_wep.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/ieee80211_module.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/ieee80211_rx.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/ieee80211_softmac.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/ieee80211_softmac_wx.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/ieee80211_tx.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/ieee80211_wx.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/internal.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/kmap_types.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/license.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/michael_mic.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/proc.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/readme.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/rtl_crypto.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/scatterwalk.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/prop-base/scatterwalk.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/Makefile.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/aes.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/api.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/arc4.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/autoload.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/cipher.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/compress.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/digest.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/ieee80211.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/ieee80211_crypt.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/ieee80211_crypt.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/ieee80211_crypt_ccmp.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/ieee80211_crypt_tkip.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/ieee80211_crypt_wep.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/ieee80211_module.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/ieee80211_rx.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/ieee80211_softmac.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/ieee80211_softmac_wx.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/ieee80211_tx.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/ieee80211_wx.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/internal.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/kmap_types.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/license.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/michael_mic.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/proc.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/readme.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/rtl_crypto.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/scatterwalk.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/text-base/scatterwalk.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/tmp/prop-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/tmp/props
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.svn/tmp/text-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/.svn
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/ieee80211-rtl.mod
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/.svn/all-wcprops
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/.svn/entries
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/.svn/prop-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/.svn/props
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/.svn/text-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/.svn/tmp
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/.svn/text-base/ieee80211-rtl.mod.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/.svn/text-base/ieee80211_crypt-rtl.mod.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/.svn/text-base/ieee80211_crypt_ccmp-rtl.mod.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/.svn/text-base/ieee80211_crypt_tkip-rtl.mod.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/.svn/text-base/ieee80211_crypt_wep-rtl.mod.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/.svn/tmp/prop-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/.svn/tmp/props
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/ieee80211/.tmp_versions/.svn/tmp/text-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/Makefile
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/README.adhoc
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/README.master
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/authors
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/changes
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/copying
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/install
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/license
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_93cx6.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_93cx6.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_gct.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_gct.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_hw.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_max2820.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_max2820.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_pm.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_pm.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_rtl8225.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_rtl8225.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_rtl8225z2.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_rtl8255.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_rtl8255.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_sa2400.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_sa2400.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_wx.c
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_wx.h
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/readme
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/all-wcprops
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/entries
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/props
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/tmp
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/Makefile.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/README.adhoc.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/README.master.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/authors.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/changes.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/copying.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/install.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/license.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_93cx6.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_93cx6.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_core.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_gct.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_gct.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_hw.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_max2820.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_max2820.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_pm.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_pm.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_rtl8225.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_rtl8225.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_rtl8225z2.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_rtl8255.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_rtl8255.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_sa2400.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_sa2400.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_wx.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/r8180_wx.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/prop-base/readme.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/Makefile.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/README.adhoc.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/README.master.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/authors.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/changes.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/copying.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/install.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/license.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_93cx6.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_93cx6.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_core.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_gct.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_gct.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_hw.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_max2820.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_max2820.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_pm.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_pm.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_rtl8225.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_rtl8225.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_rtl8225z2.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_rtl8255.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_rtl8255.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_sa2400.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_sa2400.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_wx.c.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/r8180_wx.h.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/text-base/readme.svn-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/tmp/prop-base
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/tmp/props
/home/mark/.local/share/Trash/files/rtl8185_linux_26.1031.1207.2009.release/rtl8185/.svn/tmp/text-base
/home/mark/.local/share/Trash/info/rtl8185_linux_26.1031.1207.2009.release.tar.gz.trashinfo
/home/mark/.local/share/Trash/info/rtl8185_linux_26.1031.1207.2009.release.trashinfo
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release.tar.gz
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/Makefile
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/RadioPower.sh
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/ReadMe
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/ieee80211
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/ifcfg-wlan0
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/release_note
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/wlan0dhcp
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/wlan0down
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/wlan0up
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/wpa1.conf
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/wpa_supplicant-0.5.5.zip
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/.r8180_93cx6.o.cmd
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/.r8180_dm.o.cmd
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/.r8180_pm.o.cmd
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/.r8180_rtl8225.o.cmd
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/.r8180_rtl8225z2.o.cmd
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/.r8180_wx.o.cmd
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/.r8187_core.o.cmd
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/.r8187_led.o.cmd
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/.r8187l.ko.cmd
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/.r8187l.mod.o.cmd
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/.r8187l.o.cmd
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/.tmp_versions
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/Makefile
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/Module.symvers
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/authors
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/changes
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/copying
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/install
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/license
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/lsmod.txt
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/modules.order
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_93cx6.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_93cx6.h
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_93cx6.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_dm.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_dm.h
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_dm.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_hw.h
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_pm.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_pm.h
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_pm.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225.h
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225z2.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225z2.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_wx.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_wx.h
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_wx.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187.h
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.h
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187l.ko
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187l.mod.c
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187l.mod.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187l.o
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/readme
/home/mark/Desktop/rtl8187L_linux_26.1040.0820.2010.release/rtl8187/.tmp_versions/r8187l.mod
/home/mark/Downloads/rtl8187L_linux_26.1040.0820.2010.release(2).tar.gz
/home/mark/Downloads/WinX64/rtl8185.sys
/home/mark/Downloads/WinX64/WinXP/rtl8185.sys
/lib/firmware/RTL8192SE/rtl8192sfw.bin
/lib/firmware/RTL8192SE/rtl8192sfw492.bin
/lib/firmware/RTL8192SE/rtl8192sfw74.bin
/lib/modules/2.6.31-14-generic/kernel/drivers/net/usb/rtl8150.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rtl818x
/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rtl818x/rtl8180.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rtl818x/rtl8187.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8187se
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8192su
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8187se/rtl8187se.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8192su/ieee80211
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8192su/ieee80211-rsl.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/net/usb/rtl8150.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rtl818x
/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rtl818x/rtl8180.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rtl818x/rtl8187.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8187se
/lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192e
/lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192su
/lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8187se/rtl8187se.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192e/r8192_pci.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
/lib/modules/2.6.32-31-generic/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-31-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/usr/share/doc/aircrack-ng/injection-patches/rtl8180-0.21v2.patch.gz
/usr/share/doc/aircrack-ng/injection-patches/rtl8187-mac80211-injection-speed-2.6.28-rc6.patch
/usr/share/doc/aircrack-ng/injection-patches/rtl8187_2.6.27.patch.gz
/usr/share/doc/aircrack-ng/injection-patches/rtl8187_hw_signal_backport_2.6.28.patch
/usr/share/doc/aircrack-ng/injection-patches/old/rtl8180-0.21.patch
/usr/share/doc/aircrack-ng/injection-patches/old/rtl8187_1010.0622.patch.gz
/usr/share/doc/aircrack-ng/injection-patches/old/rtl8187_1010.0622v2.patch.gz
/usr/share/doc/aircrack-ng/injection-patches/old/rtl8187_1025v2.patch.gz
/usr/share/doc/aircrack-ng/injection-patches/old/rtl8187_2.6.20.patch.gz
/usr/share/doc/aircrack-ng/injection-patches/old/rtl8187_2.6.20v2.patch.gz
/usr/share/doc/aircrack-ng/injection-patches/old/rtl8187_2.6.20v3.patch.gz
/usr/share/doc/aircrack-ng/injection-patches/old/rtl8187_2.6.20v4.patch.gz
/usr/share/doc/aircrack-ng/injection-patches/old/rtl8187_2.6.21v2.patch.gz
/usr/share/doc/aircrack-ng/injection-patches/old/rtl8187_2.6.21v4.patch.gz
/usr/share/doc/aircrack-ng/injection-patches/old/rtl8187_2.6.21v5.patch.gz
/usr/share/doc/aircrack-ng/injection-patches/old/rtl8187_2.6.22.patch.gz
/usr/share/doc/aircrack-ng/injection-patches/old/rtl8187_2.6.24.patch.gz
/usr/share/doc/aircrack-ng/injection-patches/old/rtl8187_2.6.24v2.patch.gz
/usr/share/doc/aircrack-ng/injection-patches/old/rtl8187_2.6.24v3.patch.gz
/usr/src/linux-headers-2.6.32-31/drivers/net/wireless/rtl818x
/usr/src/linux-headers-2.6.32-31/drivers/net/wireless/rtl818x/Makefile
/usr/src/linux-headers-2.6.32-31/drivers/staging/rtl8187se
/usr/src/linux-headers-2.6.32-31/drivers/staging/rtl8192e
/usr/src/linux-headers-2.6.32-31/drivers/staging/rtl8192su
/usr/src/linux-headers-2.6.32-31/drivers/staging/rtl8187se/Kconfig
/usr/src/linux-headers-2.6.32-31/drivers/staging/rtl8187se/Makefile
/usr/src/linux-headers-2.6.32-31/drivers/staging/rtl8192e/Kconfig
/usr/src/linux-headers-2.6.32-31/drivers/staging/rtl8192e/Makefile
/usr/src/linux-headers-2.6.32-31/drivers/staging/rtl8192su/Kconfig
/usr/src/linux-headers-2.6.32-31/drivers/staging/rtl8192su/Makefile
/usr/src/linux-headers-2.6.32-31/drivers/staging/rtl8192su/ieee80211
/usr/src/linux-headers-2.6.32-31/drivers/staging/rtl8192su/ieee80211/Makefile
/usr/src/linux-headers-2.6.32-31/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-31/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-31/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-31/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-31/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-31/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-31/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-31-generic/include/config/rtl8180.h
/usr/src/linux-headers-2.6.32-31-generic/include/config/rtl8187
/usr/src/linux-headers-2.6.32-31-generic/include/config/rtl8187.h
/usr/src/linux-headers-2.6.32-31-generic/include/config/rtl8187se.h
/usr/src/linux-headers-2.6.32-31-generic/include/config/rtl8192e.h
/usr/src/linux-headers-2.6.32-31-generic/include/config/rtl8192se.h
/usr/src/linux-headers-2.6.32-31-generic/include/config/rtl8192su.h
/usr/src/linux-headers-2.6.32-31-generic/include/config/rtl8187/leds.h
/usr/src/linux-headers-2.6.32-31-generic/include/config/usb/rtl8150.h
mark@mark-laptop:~$ cd Desktop


```

---

### Post by mockingbird on 2011-05-25
Ok, can you cd into this directory:
/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rtl818x/

Then type:
modprobe rtl8187.ko

And then type ifconfig -a and see ifthe interface is there, or type lsmod and see if the module is loaded.

Another thing that makes me curious...  I see there a "r8192s_usb.ko" module, which obviously is a different model, but if there's a special USB version, I'm wondering if you might need a special USB module for the 8187.

So do me a favor, type "lsusb" and post it here so I can see the information about your wireless USB stick.

---

### Post by Bonanzaman on 2011-05-26
OK, bird, here it is...........

```
ark@mark-laptop:~$ cd /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rtl818x/
mark@mark-laptop:/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rtl818x$ modprobe rtl8187.ko
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module rtl8187.ko not found.
mark@mark-laptop:/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rtl818x$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:23:5a:dc:99:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:25:56:1d:e4:69  
          inet addr:192.168.0.83  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:56ff:fe1d:e469/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:364915 (364.9 KB)  TX bytes:53941 (53.9 KB)

mark@mark-laptop:/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rtl818x$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_realtek   203408  1 
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                677027  3 
ttm                    49943  1 radeon
ath5k                 121632  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29329  1 radeon
mac80211              205402  1 ath5k
ath                     7611  1 ath5k
drm                   162345  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
snd                    54180  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ati_agp                 5094  0 
video                  17375  0 
cfg80211              126528  3 ath5k,mac80211,ath
output                  1871  1 video
lp                      7028  0 
soundcore               6620  1 snd
psmouse                63245  0 
serio_raw               3978  0 
led_class               2864  1 ath5k
i2c_piix4               8335  0 
atl1c                  28083  0 
k8temp                  3152  0 
agpgart                31724  3 ttm,drm,ati_agp
shpchp                 28835  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
pata_atiixp             3148  0 
ahci                   32200  2 
mark@mark-laptop:/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rtl818x$ cd ~
mark@mark-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mark@mark-laptop:~$ #plugged in card..........
mark@mark-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mark@mark-laptop:~$ 

```

---

### Post by Bonanzaman on 2011-05-26
> **Wolf9466 said:**
> I used compat-wireless (although with the aircrack-ng patches) and it works great for me.

Hey, Wolf, do you have functionality with the aircrack suite as well as full internet access as well?

Bird, trying the compat-wireless my be the easier solution ????

---

### Post by mockingbird on 2011-05-26
What happens if you just type "modprobe rtl8187"?

---

### Post by Bonanzaman on 2011-05-26
Looks like I did not get all the ndiswrapper files removed perhaps?

```
mark@mark-laptop:~$ modprobe rtl8187
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

```

---

### Post by mockingbird on 2011-05-26
I think if it's just a warning, it's ok...

See if rtl8187 is loaded.  lsmod...

If not type "dmesg | grep rtl8187"

To see if there's a kernel message on why it didn't.

---

### Post by Bonanzaman on 2011-05-26
OK, here is the output.....my internal card is now not being connected, so I am copying the code out to a stick from the laptop and copying here!
```
ark@mark-laptop:~$ lsmod 
Module                  Size  Used by 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat 
usb_storage            39841  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon 
font                    7557  1 fbcon 
bitblit                 4707  1 fbcon 
softcursor              1189  1 bitblit 
vga16fb                11385  0 
vgastate                8961  1 vga16fb 
snd_hda_codec_realtek   203408  1 
snd_hda_intel          22069  2 
r8187l                136295  0 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep               5412  1 snd_hda_codec 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
arc4                    1153  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
radeon                677027  3 
snd_timer              19098  2 snd_pcm,snd_seq 
ttm                    49943  1 radeon 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
rtl8187                50680  0 
drm_kms_helper         29329  1 radeon 
mac80211              205402  1 rtl8187 
drm                   162345  5 radeon,ttm,drm_kms_helper 
i2c_algo_bit            5028  1 radeon 
led_class               2864  1 rtl8187 
snd                    54180  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
cfg80211              126528  2 rtl8187,mac80211 
video                  17375  0 
eeprom_93cx6            1333  1 rtl8187 
ati_agp                 5094  0 
output                  1871  1 video 
psmouse                63245  0 
serio_raw               3978  0 
lp                      7028  0 
soundcore               6620  1 snd 
k8temp                  3152  0 
atl1c                  28083  0 
agpgart                31724  3 ttm,drm,ati_agp 
shpchp                 28835  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm 
i2c_piix4               8335  0 
parport                32635  2 ppdev,lp 
ahci                   32200  2 
pata_atiixp             3148  0 
mark@mark-laptop:~$ dmesg | grep rtl8187 
[   15.569205] rtl8187: Customer ID is 0xFF 
[   15.569254] Registered led device: rtl8187-phy0::tx 
[   15.569274] Registered led device: rtl8187-phy0::rx 
[   15.571048] rtl8187: wireless switch is on 
[   15.571091] usbcore: registered new interface driver rtl8187 
[   15.623939] rtl8187L: Initializing module 
[   15.623942] rtl8187L: Wireless extensions version 22 
[   15.623944] rtl8187L: Initializing proc filesystem 
[   15.624081] usbcore: registered new interface driver rtl8187L 
mark@mark-laptop:~$ 
```

---

### Post by mockingbird on 2011-05-26
RTL8187 is loaded!

You should be good to go.  Try and connect with it.

---

### Post by Bonanzaman on 2011-05-26
Unfortunetly as my previous post, I have no connectivity on the new driver, even though the network manager shows connected and good signal strength. The internal card which worked previously although weak in reception, now does not work either.

I believe I'll start over using the compat-wireless program, which others seem to have sucess with, if I can get enough info to pull it off.

Thanks for your time and efforts, mockingbird...I appreciate it!

---

### Post by mockingbird on 2011-05-26
No problem...

If the card is showing connected, then I very strongly think that the problem does not lie with your card but with your router.

---

### Post by chili555 on 2011-05-27
> the network manager shows connected and good signal strength.Please let us see:```
ifconfig
iwconfig
cat /etc/resolv.conf
route -n
ping -c3 74.125.93.104
```Thanks.

---

### Post by Bonanzaman on 2011-05-27
OK, chili:

```
mark@mark-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:23:5a:dc:99:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:c0:ca:4f:5c:17  
          inet addr:192.168.0.84  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:caff:fe4f:5c17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:546981 (546.9 KB)  TX bytes:120171 (120.1 KB)

mark@mark-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"qwest0096"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:75:2B:CC:C0   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1_rename  IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mark@mark-laptop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.0.1
mark@mark-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
mark@mark-laptop:~$ ping -c 74.125.93.104
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination
mark@mark-laptop:~$ 

```
Post to follow with the internal ath5k blacklisted (I can only get on the net with the ath5k)

---

### Post by chili555 on 2011-05-27
> mark@mark-laptop:~$ ping -c 74.125.93.104Actually, it's ```
ping -c[COLOR="Red"]3[/COLOR] 74.125.93.104
```

---

### Post by Bonanzaman on 2011-05-27
OK, Chili:

```
mark@mark-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:23:5a:dc:99:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:c0:ca:4f:5c:17  
          inet addr:192.168.0.84  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:caff:fe4f:5c17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:546981 (546.9 KB)  TX bytes:120171 (120.1 KB)

mark@mark-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"qwest0096"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:75:2B:CC:C0   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1_rename  IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mark@mark-laptop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.0.1
mark@mark-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
mark@mark-laptop:~$ ping -c 74.125.93.104
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination
mark@mark-laptop:~$ 

``` 

Now I'll blacklist the ath5k internal card (that I am online with), and run those again:

mark@mark-laptop:~$ ifconfig 
eth1      Link encap:Ethernet  HWaddr 00:23:5a:dc:99:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B) 

wlan2     Link encap:Ethernet  HWaddr 00:c0:ca:4f:5c:17  
          inet addr:192.168.0.84  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::2c0:caff:fe4f:5c17/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:25383 (25.3 KB)  TX bytes:10078 (10.0 KB) 

mark@mark-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth1      no wireless extensions. 
 
wlan2     IEEE 802.11bg  ESSID:"qwest0096"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:75:2B:CC:C0   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

mark@mark-laptop:~$ cat /etc/resolv.conf 
# Generated by NetworkManager 
nameserver 192.168.0.1 
mark@mark-laptop:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan2 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan2 
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan2 
mark@mark-laptop:~$ ping -c 74.125.93.104 
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline] 
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address] 
            [-M mtu discovery hint] [-S sndbuf] 
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination 
mark@mark-laptop:~$

I think the realtek shows up as wlan2

---

### Post by chili555 on 2011-05-27
> I think the realtek shows up as wlan2I beloieve you are correct.> wlan2 Link encap:Ethernet HWaddr 00:c0:ca:4f:5c:17
inet addr:[COLOR="Red"]192.168.0.84[/COLOR] Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::2c0:caff:fe4f:5c17/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:181 errors:0 dropped:0 overruns:0 frame:0
TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:25383 (25.3 KB) TX bytes:10078 (10.0 KB)
You have an IP address and all the other signs of being connected. Can you please correct the ping command and show us? Please show me:```
cat /etc/resolv.conf
```

---

### Post by mockingbird on 2011-05-27
Bonanzaman, don't get to overeager.  Follow the instructions.  It's:

ping -c3 and **not** ping -c

---

### Post by Bonanzaman on 2011-05-27
Chili.....Sorry about the last command error...1st sign of fatigue in a week! Here it is:

```
mark@mark-laptop:~$ ping -c3 74.125.93.104
PING 74.125.93.104 (74.125.93.104) 56(84) bytes of data.
64 bytes from 74.125.93.104: icmp_seq=1 ttl=55 time=97.1 ms
64 bytes from 74.125.93.104: icmp_seq=2 ttl=55 time=109 ms
64 bytes from 74.125.93.104: icmp_seq=3 ttl=55 time=98.8 ms

--- 74.125.93.104 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 97.169/101.816/109.385/5.398 ms
mark@mark-laptop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.0.1
nameserver 192.168.0.1
mark@mark-laptop:~$ 


```

---

### Post by chili555 on 2011-05-27
> 64 bytes from 74.125.93.104: icmp_seq=1 ttl=55 time=97.1 msThat IP address is Google so you are indeed connected to the internet. Now try:```
ping -c3 192.168.0.1
```^^ That's the router. What happens when you open Firefox and try to get a web page? Everything I see here says yippy-skippy hunky-dory.

---

### Post by Bonanzaman on 2011-05-27
This is a bit akward, because the ping success is due to being connected with the ath5k card in the laptop. As soon as I blacklist that card, the realtek takes over and the ping shows 100% loss...I was in the process of blacklisting/re-booting to copy that return result to post when my cursor/touchpad went dead! I'm on my desktop now, is there a keyboard / function key I can use to open a terminal?](*,)]

---

### Post by Bonanzaman on 2011-05-27
OK, plugged in corded mouse, and we are ok for now..anyway here is the result with the ath5k blacklisted, and connected with the realtek

```
mark@mark-laptop:~$ ping -c3 74.125.93.104 
PING 74.125.93.104 (74.125.93.104) 56(84) bytes of data. 

--- 74.125.93.104 ping statistics --- 
3 packets transmitted, 0 received, 100% packet loss, time 2014ms 

mark@mark-laptop:~$ cat /etc/resolv.conf 
# Generated by NetworkManager 
nameserver 192.168.0.1 
mark@mark-laptop:~$ 
```

---

### Post by chili555 on 2011-05-27
Please leave ath5k blacklisted and run:```
sudo modprobe rtl8187
iwconfig
dmesg | grep 8187

```Thanks.

---

### Post by Bonanzaman on 2011-05-27
Just to clarify a little, here is a shot of NM with the ath5k un-blacklisted...notice that both the atheros card in the laptop & the realtek show connected to qwest0096 (mine). If I disconnect the atheros connection here at NM, the realtek stays connected, but no internet! (note the signal strength difference between the 2...this is why I'd like to be able to use the realtek in the 1st place!)

---

### Post by Bonanzaman on 2011-05-27
OK, bear with me......

```
mark@mark-laptop:~$ sudo modprobe rtl8187
[sudo] password for mark: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
mark@mark-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan2     IEEE 802.11bg  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mark@mark-laptop:~$ dmesg | grep 8187
[   15.222294] phy0: hwaddr 00:c0:ca:4f:5c:17, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   15.240040] rtl8187: Customer ID is 0xFF
[   15.240104] Registered led device: rtl8187-phy0::tx
[   15.240126] Registered led device: rtl8187-phy0::rx
[   15.242002] rtl8187: wireless switch is on
[   15.242050] usbcore: registered new interface driver rtl8187
[   15.304767] Linux kernel driver for RTL8187L based WLAN cards
[   15.304771] rtl8187L: Initializing module
[   15.304773] rtl8187L: Wireless extensions version 22
[   15.304776] rtl8187L: Initializing proc filesystem
[   15.304895] usbcore: registered new interface driver rtl8187L
mark@mark-laptop:~$ 



```

---

### Post by chili555 on 2011-05-27
So do you see networks in Network Manager? How about this?```
sudo iwlist wlan2 scan
```

---

### Post by Bonanzaman on 2011-05-27
```
sudo iwlist wlan2 scan
wlan2   Interface doesn't support scanning : Device or resource busy
```

---

### Post by chili555 on 2011-05-27
This is crazy, but please humor an old driver hacker:```
lsmod | grep ndis
dmesg | grep ndis
lsusb
```Thanks.

---

### Post by mockingbird on 2011-05-27
> **Bonanzaman said:**
> ```
sudo iwlist wlan2 scan
wlan2   Interface doesn't support scanning : Device or resource busy
```
IWCONFIG and IWLIST interfere with the NetworkManager GUI so that's why you see that weird SSID in IWCONFIG.

Bonanzaman:
Something we discounted...

I believe your still loading the old rtl8187 module that came with Ubuntu and NOT the rtl8187 we downloaded from Realtek.  Here's where I don't know how to proceed...  When I downloaded my driver from Realtek, their module name was r8185b, so I had no problem blacklisting the Ubuntu module because the name was different.

In this case, the modules bear the same name, so you will need to find out how to replace that module with th eone from Realtek's site.

I'll show you what I mean:
```


/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/r8187l.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/net/usb/rtl8150.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rtl818x/rtl8180.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rtl818x/rtl8187.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8187se/rtl8187se.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/net/usb/rtl8150.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rtl818x/rtl8180.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rtl818x/rtl8187.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8187se/rtl8187se.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192e/r8192_pci.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
/lib/modules/2.6.32-31-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko

```
Remember when I asked you to locate "rtl", well these are all the Realtek Wireless modules on your PC.  Now I wish I knew which ones were the ones that you compiled and which ones came with the kernel.

Disable the driver (You don't have to blacklist, just rmmod) that's running right now and try each of the 8187 drivers above.

One of them should work for you.

---

### Post by Bonanzaman on 2011-05-27
OK, Chili here is the output you wanted:

```
mark@mark-laptop:~$ lsmod | grep ndis
mark@mark-laptop:~$ dmesg | grep ndis
mark@mark-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mark@mark-laptop:~$ 
```

Bird, I assume that code is output from your system?

How do I identify the driver in use, and which to replace it with?

---

### Post by chili555 on 2011-05-27
These come with the stock Ubuntu kernel:> /lib/modules/2.6.38-8-generic/[COLOR="Red"]kernel/drivers/net/wireless/rtl818x[/COLOR]/rtl8187/rtl8187.koYou can figure out which you have with:```
modinfo rtl8187
```Are you confident you got the downloaded version compiled successfully?

---

### Post by Bonanzaman on 2011-05-27
OK, Chili, output from "modinfo":

```
mark@mark-laptop:~$ modinfo rtl8187 
filename:       /lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rtl818x/rtl8187.ko 
license:        GPL 
description:    RTL8187/RTL8187B USB wireless driver 
author:         Larry Finger <Larry.Finger@lwfinger.net> 
author:         Hin-Tak Leung <htl10@users.sourceforge.net> 
author:         Herton Ronaldo Krzesinski <herton@mandriva.com.br> 
author:         Andrea Merello <andreamrl@tiscali.it> 
author:         Michael Wu <flamingice@sourmilk.net> 
srcversion:     47F87A7CDF8BBC9C79E7F37 
alias:          usb:v1737p0073d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1B75p8187d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v18E8p6232d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v13D1pABE6d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1371p9401d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v114Bp0150d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p0029d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p0028d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p000Dd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v03F0pCA02d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0846p4260d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0846p6A00d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0846p6100d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0789p010Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0769p11F2d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0BDAp8198d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0BDAp8197d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0BDAp8189d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v050Dp705Ed*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0B05p171Dd*dc*dsc*dp*ic*isc*ip* 
depends:        mac80211,eeprom_93cx6,led-class,cfg80211 
vermagic:       2.6.32-31-generic SMP mod_unload modversions 586 
mark@mark-laptop:~$ 
```
Does not appear to be the stock Ubuntu kernel module...?

Also please see code in post #35 this thread....1st time for me, but appeared sucessful....

---

### Post by chili555 on 2011-05-27
> /lib/modules/2.6.32-31-generic/[COLOR="Red"]kernel/drivers/net/wireless/rtl818x[/COLOR]/rtl8187.ko Looks stock to me. To find out what you have loaded, run:```
lsmod
```Here is a snip from a previous lsmod:> snd_hda_codec_realtek   203408  1 
snd_hda_intel          22069  2 
[COLOR="Red"]r8187l[/COLOR]                136295  0 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep               5412  1 snd_hda_codec 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
arc4                    1153  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
radeon                677027  3 
snd_timer              19098  2 snd_pcm,snd_seq 
ttm                    49943  1 radeon 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
[COLOR="Red"]rtl8187[/COLOR]                50680  0 
drm_kms_helper         29329  1 radeon 
mac80211              205402  1 rtl8187 So, do you have rtl8185 loaded or r8187l...or both???

You probably need to blacklist rtl8187.

Please see private messages.

---

### Post by Bonanzaman on 2011-05-27
OK, from lsmod I read...

[COmark@mark-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
vfat                    8933  0 
fat                    47767  1 vfat
usb_storage            39841  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_realtek   203408  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
r8187l                136295  0 
snd_seq_dummy           1338  0 
arc4                    1153  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
radeon                677027  3 
ttm                    49943  1 radeon
rtl8187                50680  0 
snd                    54180  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29329  1 radeon
***mac80211              205402  1 rtl8187***video                  17375  0 
_***led_class               2864  1 rtl8187***_drm                   162345  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
ati_agp                 5094  0 
soundcore               6620  1 snd
[I][B][U]cfg80211              126528  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187[/U][/B][/I]output                  1871  1 video
psmouse                63245  0 
serio_raw               3978  0 
atl1c                  28083  0 
k8temp                  3152  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  3 ttm,drm,ati_agp
shpchp                 28835  0 
i2c_piix4               8335  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67096  1 usbhid
pata_atiixp             3148  0 
ahci                   32200  2 
mark@mark-laptop:~$ DE][/CODE]

---

### Post by chili555 on 2011-05-27
> [COLOR="Red"]r8187l[/COLOR] 136295 0
snd_seq_dummy 1338 0
arc4 1153 0
snd_seq_oss 26722 0
snd_seq_midi 4557 0
snd_rawmidi 19056 1 snd_seq_midi
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 19098 2 snd_pcm,snd_seq
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
radeon 677027 3
ttm 49943 1 radeon
[COLOR="Red"]rtl8187[/COLOR] 50680 0
snd 54180 16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec, snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_se q_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper 29329 1 radeon
mac80211 205402 1 rtl8187video 17375 0
led_class 2864 1 rtl8187drm 162345 5 radeon,ttm,drm_kms_helper
i2c_algo_bit 5028 1 radeon
ati_agp 5094 0
soundcore 6620 1 snd
cfg80211 126528 2 rtl8187,mac80211
eeprom_93cx6 1333 1 rtl8187output 1871 1 video
psmouse 63245 0
serio_raw 3978 0 Isn't r8187l the one you compiled? I think you need to blacklist rtl8187 and reboot. We'll look forward to your report.

---

### Post by Bonanzaman on 2011-05-27
Yes, rtl8187l is the new one, I blacklisted the rtl8187 & the ath5k, re-booted, still no internet....nm keeps trying to connect, asks for key code, etc, but no connection shows at all.....before nm showed connected, BUT no internet....??#-o

---

### Post by chili555 on 2011-05-27
Let's see:```
dmesg | grep 8187
iwconfig
sudo iwlist wlan2 scan
```We're pretty close.

---

### Post by Bonanzaman on 2011-05-27
OK....

[CODE]mark@mark-laptop:~$ dmesg | grep 8187 
[   14.499824] Linux kernel driver for RTL8187L based WLAN cards 
[   14.499828] rtl8187L: Initializing module 
[   14.499830] rtl8187L: Wireless extensions version 22 
[   14.499833] rtl8187L: Initializing proc filesystem 
[   14.534261] rtl8187L: Reported EEPROM chip is a 93c46 (1Kbit) 
[   14.752545] rtl8187L: Card MAC address is 00:c0:ca:4f:5c:18 
[   15.005826] rtl8187L: Card reports RF frontend Realtek 8225 
[   15.005831] rtl8187L: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO Realtek 
[   16.973697] rtl8187L: This seems a new V2 radio: rtl8225_zebra2 
[   16.973838] rtl8187L: PAPE from CONFIG2: 0 
[   16.993222] rtl8187L: EEPROM Customer ID: FF 
[   16.994439] rtl8187L: Driver probe completed 
[   16.994535] usbcore: registered new interface driver rtl8187L 
[   16.996591] rtl8187L: Now Radio On 
[   17.104936] rtl8187L: rtl8180_open process 
[   18.135510] rtl8187L: Card successfully reset 
mark@mark-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth1      no wireless extensions. 

wlan3     802.11bg  ESSID:"denton"  
          Mode:Managed  Channel=13  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

mark@mark-laptop:~$ sudo iwlist wlan2 scan 
[sudo] password for mark: 
wlan2     Interface doesn't support scanning. 

so is the 8187l associated properly?? wlan3?  Have not seen that before???

---

### Post by chili555 on 2011-05-27
Is there a README in the file you extracted?> rtl8187L_linux_26.1040.0820.2010.releaseCan you copy and paste it here? Please try:> sudo iwlist wlan3 scan
lsmod | grep 818Thanks.

---

### Post by Bonanzaman on 2011-05-27
ok....the readme



Release Date: 2008-12-05, ver 1037 
RTL8187L Linux driver version 1037 
 
   --This driver supports RealTek RTL8187L Wireless LAN NIC for 
     2.6 kernel: 
     Fedora Core 2/3/4/5/6/7, Debian 3.1, Mandrake 10.2/Mandriva 2006,  
     SUSE 9.3/10.1/10.2, Gentoo 3.1, etc, Ubuntu8.04/8.10. 
     2.4 kernel: 
     Redhat 9.2, etc 
   - Support Client mode for either infrastructure or adhoc mode 
   - Support WEP, WPAPSK and WPA2PSK connection 
 
======================================================================================
                                Component
======================================================================================
The driver is composed of several parts:
        1. Module source code
           ieee80211
           rtl8187

        2. Script ot build the modules
           Makefile

        3. Script to load/unload modules
           wlan0up
           wlan0down

        4. Script and configuration for DHCP
           wlan0dhcp
           ifcfg-wlan0
 
	5. Supplicant source code: 
	   wpa_supplicant-0.5.5.tar.gz 
 
	6. Example of supplicant configuration file: 
	   wpa1.conf 
 
======================================================================================
                                Installation
======================================================================================
<<Method 1>>
Runing the scripts can finish all operations of building up modules
from the source code, installing driver to the kernel and starting up the nic.
        1. Build up the drivers from the source code
           make

        2. Install the driver to the kernel
           make install
           reboot
	
        3. bring up wlan if nic is not brought up by GUI, such as NetworkManager
           ifconfig wlan0 up
           Note: use ifconfig to check whether wlan0 is brought up and use iwconfig to 
           check your wlan interface name,since it may change wlan0 to wlan1,etc.

<<Method 2>>
Or only load the driver module to kernel and start up nic.
        1. Build up the drivers from the source code
           make

        2. Load driver module to kernel and start up nic.
           ./wlan0up

           Note: when "insmod: error inserting 'xxxx.ko': -1 File exists" comes out
                 after run ./wlan0up, please run ./wlan0down first, then it should
                 be ok..
           Note: If you see the message of "unkown symbol" during ./wlan0up, it
                 is suggested to build driver by <<Method 1>>.
 
======================================================================================
                                Set wireless lan MIBs
======================================================================================
This driver uses Wireless Extension as an interface allowing you to set 
Wireless LAN specific parameters. 
 
Current driver supports "iwlist" to show the device status of nic 
        iwlist wlan0 [parameters] 
where 
        parameter explaination      	[parameters]     
        -----------------------     	-------------    
        Show available chan and freq	freq / channel   
        Show and Scan BSS and IBSS 	scan[ning]           
        Show supported bit-rate         rate / bit[rate]         
        Show Power Management mode      power              
 
For example: 
	iwlist wlan0 channel 
	iwlist wlan0 scan 
	iwlist wlan0 rate 
	iwlist wlan0 power 
 
Driver also supports "iwconfig", manipulate driver private ioctls, to set 
MIBs. 
 
	iwconfig wlan0 [parameters] [val] 
where 
	parameter explaination      [parameters]        [val] constraints 
        -----------------------     -------------        ------------------ 
        Connect to AP by address    ap              	[mac_addr] 
        Set the essid, join (I)BSS  essid             	[essid] 
        Set operation mode          mode                {Managed|Ad-hoc} 
        Set keys and security mode  key/enc[ryption]    {N|open|restricted|off} 
 
For example: 
	iwconfig wlan0 ap XX:XX:XX:XX:XX:XX 
	iwconfig wlan0 essid "ap_name" 
	iwconfig wlan0 mode Ad-hoc 
	iwconfig wlan0 mode essid "name" mode Ad-hoc 
	iwconfig wlan0 key 0123456789 [2] open 
	iwconfig wlan0 key off 
	iwconfig wlan0 key restricted [3] 0123456789 
 
======================================================================================
                                Getting IP address
======================================================================================
After start up the nic, the network needs to obtain an IP address before 
transmit/receive data. 
This can be done by setting the static IP via "ifconfig wlan0 IP_ADDRESS" 
command, or using DHCP. 
 
If using DHCP, setting steps is as below: 
	(1)connect to an AP via "iwconfig" settings 
		iwconfig wlan0 essid [name]	or 
		iwconfig wlan0 ap XX:XX:XX:XX:XX:XX 
 
	(2)run the script which run the dhclient 
		./wlan0dhcp 
           or  
		dhcpcd wlan0 
              	(Some network admins require that you use the 
              	hostname and domainname provided by the DHCP server. 
              	In that case, use  
		dhcpcd -HD wlan0) 
		 
======================================================================================
                        WPAPSK/WPA2PSK
======================================================================================
Wpa_supplicant helps to secure wireless connection with the protection of
WPAPSK/WPA2PSK mechanism.

If the version of Wireless Extension in your system is equal or larger than 18,
WEXT driver interface is recommended. Otherwise, IPW driver interface is advised.

	Note: Wireless Extension is defined us "#define WIRELESS_EXT" in Kernel
	Note: To check the version of wireless extension, please type "iwconfig -v"

If IPW driver interface is used, We suggested to follow the steps from 1 to 6.
If wpa_supplicant has been installed in your system, only steps 5 and 6 are required
to be executed for WEXT driver interface.

To see detailed description for driver interface and wpa_supplicant, please type
"man wpa_supplicant".
	
	(1)Download latetest source code for wpa supplicant or use wpa_supplicant-0.5.5
           attached in this package. (It is suggested to use default package contained
           in the distribution because there should less compilation issue.)

           Unpack source code of WPA supplicant:

           tar -zxvf wpa_supplicant-0.5.5.tar.gz (e.g.)
           cd wpa_supplicant-0.5.5

	(2)Create .config file:

           cp defconfig .config

        (3)Edit .config file, uncomment the following line if ipw driver interface
           will be applied:

           #CONFIG_DRIVER_IPW=y.

        (4)Build and install WPA supplicant:
           
           make
           cp wpa_cli wpa_supplicant /usr/local/bin

           If make error for lack of <include/md5.h>, install the openssl lib(two ways):
           1. Install the openssl lib from corresponding installation disc:
              Fedora Core 2/3/4/5(openssl-0.9.71x-xx),
              Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk),
              Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl),
              Gentoo(dev-libs/openssl), etc.
           2. Download the openssl open source package from [www.openssl.org](www.openssl.org), build and
              install it.

        (5)Edit wpa_supplicant.conf to set up SSID and its passphrase.
           For example, the following setting in "wpa1.conf" means SSID
           to join is "BufAG54_Ch6" and its passphrase is "87654321".

           Example 1: Configuration for WPA-PWK
           network={
                        ssid="BufAG54_Ch6"
                        proto=WPA
                        key_mgmt=WPA-PSK
                        pairwise=CCMP TKIP
                        group=CCMP TKIP WEP104 WEP40
                        psk="87654321"
                        priority=2
                  }

           Example 2: Configuration for LEAP
           network={
                        ssid="BufAG54_Ch6"
                        key_mgmt=IEEE8021X
                        group=WEP40 WEP104
                        eap=LEAP
                        identity="user1"
                        password="1111"
                  }

        Note: 1. proto=WPA for WPA, proto=RSN for WPA2.
              2. If user needs to connect an AP with WPA or WPA2 mixed mode, it is suggested
                 to set the cipher of pairwise and group to both CCMP and TKIP unless you
                 know exactly which cipher type AP is configured.
              3. Low kernel version which is lower than 2.6.18.rc2 may have trouble with
                 TKIP heavy traffic while SMP is configured. Please change your security
                 cipher or update your kernel.
              4. According to documentaion "wpa_supplicant.conf" provided by the package of
                 wpa_supplicant, ap_scan is set to 2 for IBSS connection. If user is trying to
                 associate to AP in Infrastructure mode, please unmark this line us as belowing
                 "#ap_scan=2"

        (6)Execute WPA supplicant (Assume related modules had been loaded):
           wpa_supplicant -D wext -c wpa1.conf -i wlan0 & (recommended)
           wpa_supplicant -D ipw -c wpa1.conf -i wlan0

           Note: At first, user sholud check Wireless Extension by typing "iwconfig -v"
                 on the comment line. If the version of Wireless Extension is equal or
                 larger than 18, the option of "-D wext" is suggested. If the version
                 of Wireless extension is less than 18, the option of "-D ipw" is
                 suggested.
           	 
		 But before you use "wext" or "ipw" command, you sholud check which drivers 
                 wpa_supplicant can support by typing command "wpa_supplicant". after typing the 
                 comment line, you can see some infomations about wpa_supplicant are listed, 
                 example:
		 ---------------------------------------------------------------------------
		 usage:
                      	XXXXXXXXX
                 drivers:
                        wext = Linux wireless extensions (generic)
  			atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  			wired = wpa_supplicant wired Ethernet driver
                 options:
                      	XXXXXXXXX
                 example:
                      	XXXXXXXXX 
		 ---------------------------------------------------------------------------
		 The driver interface wpa_supplicant can support are listed in "drivers", 
                 if "ipw" or "wext" is not listed in it, you can only use the the other interface. 
                 If the interface you want to use is not supported by wpa_supplicant. you can 
                 follow steps (1)-(6), And in step (3) you must let:

                 CONFIG_DRIVER_IPW=y.
                 or
                 CONFIG_DRIVER_WEXT=y.
		 or both 
                 CONFIG_DRIVER_IPW=y.
                 CONFIG_DRIVER_WEXT=y.

======================================================================================
                        GPIO methord for Radio On/Off
======================================================================================
	1. The Change For Deliverring Power State:

           Now we add the RadioPower.sh script in the driver root path.
           When you run ./wlan0up or make install, this script will be copied 
	   to /etc/acpi/events. And the driver can deliver the power 
	   state "RFON" or "RFOFF" into /etc/acpi/events/RadioPower.sh from driver.
           So you can change this script based on the power state RFON or RFOFF.

	2. For Example:

           Now the RadioPower.sh's content is:
           if[ "$1" = ""RFON ]; then
                echo "===================>Now Polling Method Turn RF ON!" > /etc/acpi/events/RadioPowerTest
           else
                echo "===================>Now Polling Method Turn RF OFF!" > /etc/acpi/events/RadioPowerTest
           fi

           So when you turn on RF using Polling Method, you can see "===================>>Now Polling Method Turn RF ON!"
           using command: cat /etc/acpi/events/RadioPowerTest.

           And when you turn off RF using Polling Method, you can see "===================>>Now Polling Method Turn RF OFF!"
           using command: cat /etc/acpi/events/RadioPowerTest.


output:

```
mark@mark-laptop:~$ sudo iwlist wlan3 scan 
[sudo] password for mark: 
wlan3     Scan completed : 
          Cell 01 - Address: 00:19:E4:1F:E1:89 
                    ESSID:"denton" 
                    Protocol:IEEE 802.11bg 
                    Mode:Master 
                    Channel:9 
                    Encryption key:on 
                    Bit Rates:54 Mb/s 
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=45/100  Signal level=-64 dBm  Noise level=-82 dBm 
                    Extra: Last beacon: 549ms ago 

mark@mark-laptop:~$ lsmod | grep 818 
r8187l                136295  0 
mark@mark-laptop:~$ 
```

---

### Post by chili555 on 2011-05-27
So far, so good! It looks like your network, denton has simple WEP encryption. Are you quite sure about the key? Is it 10 or 26 characters? Double double-checked?> Release Date: 2008-12-05, ver 1037 That's an oldie, however, so is your kernel version.> Quality=45/100It is a bit far away, yes?

Well, I'm clocking out for tonight. See ya tomorrow. Get connected while I sleep, would ya?

---

### Post by Bonanzaman on 2011-05-27
Thanks, chili!!!!    "denton" is not my ap, the system keeps scrolling through available ap's to try and connect to...that one happened to be up as I tried the last code lines. I really appreciate your help...I'll be on intul about 1 or 2PM MST tomorrow if you are still up for some more abuse....otherwise it will be Monday for me...much thanks again

---

### Post by Bonanzaman on 2011-05-28
Chili, you were probably awake when I got connected, but you got your request! There was a 3rd driver (rt2800usb)on the blacklist which I saw but paid no attention to it as it was listed there when I loaded 10.4 to the laptop. Took it off the blacklist, and my card works on it.....go figure!

Thanks much for your time and patience...I learned quite a bit about drivers and command line caution to boot....(pun intended!) Thanks goes to mockingbird as well for your time. I intend to continue lurking on the wireless forum, so when my next glitch occurs, I might be equipped to handle things a bit better!

Cheers, Mark

---

