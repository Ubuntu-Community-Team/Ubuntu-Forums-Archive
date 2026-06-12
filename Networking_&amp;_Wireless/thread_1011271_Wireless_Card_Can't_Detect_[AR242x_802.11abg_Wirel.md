---
title: "Wireless Card Can't Detect [AR242x 802.11abg Wireless PCI Express Adapter]"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by brandon89 on 2008-12-14
hey guys, so im pretty new to ubuntu (ive used it before, but still wouldnt consider myself anywhere near an experience user) and i'm having some wireless problems.  i have an hp dv5-1002nr laptop with an  Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) wireless card.  ive tried a couple things such as madwifi and ndiswrapper but unless im following the instructions wrong (theres a good chance of that lol), im still without wireless internet.  so hopefully you guys can help me out a little.  thanks

here's some output from terminal commands:


lscpi
> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

sudo lshw -C network
>   *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:98:b2:62
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=128.138.57.236 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1e:43:6f:39:dd:25
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


---

### Post by Sup3rkirby on 2008-12-14
I am having a problem too.  I tried Ubuntu already and I'm installing Kubuntu right now.

The adapter is detected with the restricted drivers app, but even with the driver active and the firmware(using fwcutter) downloaded and extracted, the laptop does not even register a wireless device(using iwconfig, everything says no wireless devices found).


I have the same wireless card as well, Atheros AR242x (rev 01).  I have tried several solutions which are the various firmware downloads, wicd and madwifi, but no wireless networks are detected, as the computer thinks there are no wireless devices(so it can't scan).

---

### Post by JPorter on 2008-12-14
Same issue here.  Most of the references to this card being a problem are on Macbooks.  I'm trying to set up a Thinkpad R500 for a friend and have hit a wall with the wireless card.  What gives?

---

### Post by brandon89 on 2008-12-14
i dont know, its frustrating though lol.  so whats the plan of attack?  just try a bunch of random stuff? haha

---

### Post by JPorter on 2008-12-14
SOLVED!


You need to install the latest kernel wireless drivers, they have changed somewhat compared to the currently-supported drivers in Ubuntu.

Following the instructions at [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) directs the following:

1. Download the latest kernel wireless drivers for kernels 2.6.27+ from [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

2. Untar onto the desktop.

3. Navigate to the extracted directory and run the following:
```
make
sudo make install
sudo make unload
sudo make load
```

4. reboot and run iwconfig to check wireless status

5. if the card is still not visible, run[FONT="Courier New"] sudo modprobe ath5k[/FONT]

If manually loading the driver works, run[FONT="Courier New"] echo ath5k | sudo tee -a /etc/modules [/FONT]to add the module automatically at startup



This worked for me... though the current version of the ath5k driver is rather slow.

---

### Post by 67GTA on 2008-12-14
If you are using 8.04 or earlier, you will have to use ndiswrapper and the Windows version of your wireless driver. For 8.10, put in your live CD, add it as a repo through synaptic and install linux-backports-modules-intrepid-generic. Ndiswrapper is also installable from the install CD.

---

### Post by Sup3rkirby on 2008-12-14
I found a solution guys.  It is a long one(but not really that bad).  Just follow the instructions STEP-BY-STEP.  I will really post every single thing I did, including getting up to wait.

I first will give credit to an article on madberry.org.  My version here will be a bit different, and will make things easier for those searching on this forum(sorry that I don't know the guy's name).


This was done on a clean install, but as long as you haven't done anything major(as far as these drivers go), everything should be fine.  It would be best to use a clean install, but in any case, give it a try.

Also, I must note you will sadly need to connect the computer to the internet, via ethernet. If you cannot connect via ethernet, then you will need to download the file specified and transfer it to that computer(usb flash drive works). Also, the build-essential package can be installed from the ubuntu disk, so no internet should be needed there.

-------------------------------------------------------------
Open up the terminal, as we will be using this to type a bunch of commands.

Ubuntu uses the resricted drivers by default, but they don't seem to work for the Atheros cards, so use this command to disable/remove them:
```
sudo update-rc.d -f linux-restricted-modules-common remove
```

Next, as simple confimation, use this command below:
```
lspci | grep Atheros
```
That is not an 'l' but a bar. Hold shift and press the backslash.
You should get something either very close to, or the same thing as below.  Really, we are just making sure you have the Atheros AR242x (rev 01) wireless card.
```
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

Now for set up, we change the directory to the desktop. We are about to download the driver and this is where it should be saved by default.  If not and you changed it, please simply change the directory to your downloads folder:
```
cd ~/Desktop
```

I'll just bundle these next commands because essentially, you type the command, hit enter and wait until it has completed, then move on to the next one:
```
wget -c http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
```
```
tar xvf compat*.tar.bz2
```
```
cd compat*
```

Now you have the driver downloaded, extracted and you are in that folder. Next we just need to build and install the driver.  Everything should work as I said this was on a fresh install, so the driver shouldn't bring up any errors.

First make sure you have the compiling functions:
```
sudo apt-get update && sudo apt-get install build-essential
```
Just type 'y' and hit enter when the question of installing it comes up. Once the package has been installed(and downloaded if needed), you are all set for the final set of steps.

Now we are going to create the driver from the source code we downloaded and finally, install it. Just execute these last few steps one after the other. Wait til one is done, then move on. BUT PLEASE NOTE this first step(make) takes a very long time. Please be patient. I left to room and got online on a different computer for a while. It probably takes 6-12 minutes straight, so find something to do:
```
make
```
```
sudo make install
```
```
sudo make unload
```
```
sudo make load
```

Now everything should be ready. Simply restart your computer and when you load back in to Ubuntu, you should be able to connect to wireless networks.

use 'iwconfig' to verify once you have restarted.

Also, I seem to be having a bit of trouble with WPA2 Personal(AES & TKIP). I use this for my home network, simply because it is the best security I can get. I can't seem to connect though, but I did connect to an unencrypted network already.


Hope I helped you guys.

---

### Post by brandon89 on 2008-12-14
sweet!  ok, so i followed all the steps and when i run iwconfig i get this output

> 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


is this right?
and then from here how do i connect to wireless networks?

---

### Post by Sup3rkirby on 2008-12-14
That appears to be correct.  What you really want is wlan0 to be a registered wireless device.  It appears that it has not picked up any networks, but is working.  Try using the network manager and scaning for wireless networks(unless it is hidden).

---

### Post by brandon89 on 2008-12-14
ok, ill see if i can get it to detect the networks....

[EDIT]
sweet, i got it to work guys, thanks a lot

---

### Post by Sup3rkirby on 2008-12-14
Glad I could help.  Looks like WPA can be tricky though if you have any of those networks. I'm still having trouble connecting to my own network.  I tried in Kubuntu and Ubuntu, both fail. I'm not sure if it is the network manager app or just the wireless device being unable to use the protocol when running under linux...

Either way, wireless does indeed work after a little bit of work, but it doesn't seem like it works to its full extent still...

I'm running under Wubi though, don't think it matters. Seems like it is still running as if it were installed to my hard drive.

[EDIT]
Looked it up and it is a common problem. Changing the wireless channel or using a different network management app seems to fix the problem, for anyone wondering.

---

### Post by brandon89 on 2008-12-15
hm ok so im having some trouble connecting to my roommates wireless network.  im pretty sure its wpa protected (and hidden as well) so i tried a different network application (widc) but thats not working.  i guess i can try changing the channel, but what channel should i change it to?

EDIT:
well i switched the channel to 11 since thats what most people have done, but still no luck....

---

### Post by john0boy on 2008-12-22
i found that the best result was sup3rkirby's answer to it but i cam across a problem. as i get through it all i suddenly comes up saying - [sudo] password required andwhen i try to enter my password it does not allow me to type my password in and suddenly it just wont let me do it anymore and i ends the terminal installation how can i put in my password?
thanks

---

### Post by Sup3rkirby on 2009-04-05
It appears you are a new user to the linux world, and I appologize for being months behind on this.

When using the terminal, you use the 'sudo' command to run something with full adminstrative rights. Thus, allowing those functions to actually be run. But when the terminal ask for your password, it will not show the characters, or even a mask while typing.  So it will appear as if you have typed nothing in.  Just continue and type your entire password, then press the 'Enter' or 'Return' key.  If you typed in your password correctly, everything will work. If not, then try again.

And brandon89, have you tried any other channels? You said you changed to 11, as it would be the most common solution, but perhaps in your situation, another number would work best. If not, then because the network is hidden, you might want to find a good network manager. I honestly can't recommend anything at the time, as I've been off linux for a while.

I hate to post back in such an old topic, but after I had a number of problems with my linux boot(it seems using the auto-update ruins the work done here with the wireless driver, thus the steps must be redone after updating). I had completely forgotten how to fix the driver issue, and had to come back to this topic, that's all. Figured I'd continue the help.

---

### Post by warpasylum on 2009-04-08
Awesome!  Thanks man.  I've had this laptop Acer Aspire 5050 for 2 years and this is the first time my wireless has ever worked under Ubuntu.  I followed your steps to a t n' it works great.  Thanks again.:p

---

