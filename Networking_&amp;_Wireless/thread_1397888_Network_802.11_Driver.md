---
title: "Network 802.11 Driver"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by ShadowMosesGreen on 2010-02-03
For those suggesting any sudo apt-get install command, please don't.  I have no internet.  That's the problem I'm having in the first place.

I have been trying to gain access to the internet using Ubuntu and I just started to use Ubunutu so I'm still a complete novice at this.  I tried making sense of the URL that the DMESG gave me.  This was part of DMESG thing I typed in the terminal.

[ 16.240049] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[ 16.242681] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[ 16.247491] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 16.247496] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 16.247499] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

Can anyone help make sense of what the URL is trying to say?  And if so, how will I know which driver to download?

I looked at the following URL and don't know how to figure out which one to download by reading the previous URL.  How do I know which one to download.

[http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/)

Also, how would I go about installing those wireless kernels once I get them?  And I do mean step by step.  Don't just tell me to open up the terminal.  Tell me applications>accessories>terminal.  Assume I know nothing.

---

### Post by chili555 on 2010-02-03
Please walk your laptop over to the router or modem. Disconnect your bf/gf/life partner. Tell them to chill. Hook an ethernet cable to your laptop and connect to the WWW.

Go to Applications -> Accessories -> Terminal. Type in:```
sudo apt-get install b43-fwcutter
```Press Enter. You will be asked to automatically fetch and install the firmware into the right location. When that's all done, reboot, disconnect the ethernet cable, hook up the bf/gf/life partner and tell them thanks. Bring them a brew.

Upon reboot, your wireless will most likely work.

I hope you are a good sport. I have just been having a bit of fun.

---

### Post by ShadowMosesGreen on 2010-02-04
> **chili555 said:**
> Please walk your laptop over to the router or modem. Disconnect your bf/gf/life partner. Tell them to chill. Hook an ethernet cable to your laptop and connect to the WWW.

Go to Applications -> Accessories -> Terminal. Type in:```
sudo apt-get install b43-fwcutter
```Press Enter. You will be asked to automatically fetch and install the firmware into the right location. When that's all done, reboot, disconnect the ethernet cable, hook up the bf/gf/life partner and tell them thanks. Bring them a brew.

Upon reboot, your wireless will most likely work.

I hope you are a good sport. I have just been having a bit of fun.

1. I don't have a laptop
2. I am hooked up wirelessly
3. Hooking the computer up directly to a cable did nothing
4. I have no internet to do ANY sudo get-apt install command

---

### Post by chili555 on 2010-02-04
Well, that will make it harder, won't it, but not impossible.

May I assume you have a USB drive or similar that you can use to grab files from the internet and then transfer to your Ubuntu machine? Here is a post that describes the method:

[http://ubuntuforums.org/showpost.php?p=7698202&postcount=14](http://ubuntuforums.org/showpost.php?p=7698202&postcount=14)

---

### Post by ShadowMosesGreen on 2010-02-04
> **chili555 said:**
> Well, that will make it harder, won't it, but not impossible.
 
May I assume you have a USB drive or similar that you can use to grab files from the internet and then transfer to your Ubuntu machine? Here is a post that describes the method:
 
[http://ubuntuforums.org/showpost.php?p=7698202&postcount=14](http://ubuntuforums.org/showpost.php?p=7698202&postcount=14)
 
I truly hope it works.  You're one of the few that hasn't suggested a sudo get-apt install command.  I'm in classes right now and won't be home until later.  I'll try it then.

---

### Post by bkratz on 2010-02-04
Also you can do it from the installation CD. See the following thread for instructions.  See about halfway down for instructions with no wired connection  available.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by ShadowMosesGreen on 2010-02-04
> **chili555 said:**
> Well, that will make it harder, won't it, but not impossible.

May I assume you have a USB drive or similar that you can use to grab files from the internet and then transfer to your Ubuntu machine? Here is a post that describes the method:

[http://ubuntuforums.org/showpost.php?p=7698202&postcount=14](http://ubuntuforums.org/showpost.php?p=7698202&postcount=14)
I wish I could say that it works, but not even close.  I just get a bunch of "unkown. . . " stuff.  Error, non, no, un, in, just about every negative possible shows up in the terminal.

---

### Post by ShadowMosesGreen on 2010-02-04
> **bkratz said:**
> Also you can do it from the installation CD. See the following thread for instructions.  See about halfway down for instructions with no wired connection  available.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)
The only thing that shows up when I use Synaptic is "Mark for deletion."  I can never get past step 1 with all of these questions that i've asked.

---

### Post by chili555 on 2010-02-04
Please elaborate which one of these steps fails and what happens:>    1. Open Sytem -> Admin -> Synaptic Package Mgr
   2. Ensure 9.10 LiveCD is in the drive
   3. In Synaptic Package Mgr, open Settings -> Repositories -> Ubuntu Software
   4. Check "Installable from CD-ROM/DVD" and close
   5. Reload (disregard connectivity errors)
   6. Search for "b43-fwcutter"
   7. Right-click and mark for installation
   8. Apply changes (answer yes when asked "Fetch and install firmware?")
   9. Reboot
  10. Repeat steps 1.3 thru 1.4.2
Thanks.

---

