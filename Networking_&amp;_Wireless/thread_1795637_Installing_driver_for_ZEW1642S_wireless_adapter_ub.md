---
title: "Installing driver for ZEW1642S wireless adapter ubuntu 10.04"
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by bobbert4ever on 2011-07-03
I have a desktop and I just installed ubuntu 10.04 as a dual boot with windows 7. My desktop has a wireless ZEW1642S card. I don't have access to a wired internet connection, but I can use the wireless on my windows 7 fine. It seems like there is no driver for it to work on ubuntu, and since I don't have an internet connection while in ubuntu, it seems I can't update it of course because I need internet to update. I am brand new to the whole linux thing. Can someone give me some step by step instructions on how to get the driver? Thank you so much!

EDIT: My wireless network does NOT have a password if that even means anything for this.

EDIT 2: I have the exe installer for the driver for it but I don't know how I'm supposed to get the INF file or whatever.

---

### Post by MaindotC on 2011-07-03
The first place to start is the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  In order for your device to work properly you need the physical connectivity (plugged in all the way and/or turned on via your machine's BIOS), a driver to communicate between the device and the operating system, and then the proper configuration of the device which typically is via DHCP.  Please follow the guide and indicate at what point you are having difficulty.

---

### Post by bobbert4ever on 2011-07-03
Well the problem is it is plugged in physically and is working 100 percent on this machine in windows 7, but when I started ubuntu there is a wireless icon at the top that is greyed out with a red explanation point by it. I try and look at the wireless internet list but there is none shown. Does this mean that I don't have the drive or something else? If so please tell me but I thought it has to do with the driver. I have the install disk for it but it's an exe install so of course I can't use that. The website that shows this card even says it supports linux/mac/windows. But how do I get (download) AND install that driver for ubuntu?

EDIT: Nevermind the page doesn't say it supports linux.

---

### Post by MaindotC on 2011-07-03
> **bobbert4ever said:**
> Well the problem is it is plugged in physically and is working 100 percent on this machine in windows 7,This is irrelevant

>  but when I started ubuntu there is a wireless icon at the top that is greyed out with a red explanation point by it.

From what I have been able to determine it is NetworkManager, or something affecting NetworkManager, not the driver for the device.  If it was a driver issue then you would not see a driver issue listed in lshw -c network and I'm sure you'll see a driver listed there.  I suggest you try installing Wicd and get on with your life.

---

### Post by bobbert4ever on 2011-07-03
> **MaindotC said:**
> From what I have been able to determine it is NetworkManager, or something affecting NetworkManager, not the driver for the device.  If it was a driver issue then you would not see a driver issue listed in lshw -c network and I'm sure you'll see a driver listed there.  I suggest you try installing Wicd and get on with your life.

How do I install wicd?

---

### Post by chili555 on 2011-07-03
Before you decide that Network Manager isn't doing its job and that you need Wicd, let'a ascertain that you actually have funtioning drivers in place for the device. We are going to use the terminal (Applications > Accessories > Terminal) because it is fast, accurate and sometimes the only way to get data from your computer. First, let's list your PCI devices and filter down to your wireless device. In the terminal, run and post:```
lspci -nn | grep 0280
```You can copy and paste from the terminal to a text document (Applications > Accessories > Text Editor) and drag and drop the text document to a USB key or similar to post it here. Next, let's list running modules and see if any are in place related to your adapter:```
lsmod | grep rt2
```Now, let's see if you have a wireless interface:```
iwconfig
```Post these items and we'll have a better idea about how to proceed.


---------------

Note to Chili: RT3062? Compile? Fun??

---

### Post by bobbert4ever on 2011-07-03
With lspci -nn | grep 0280 I got the following

```
lspci -nn | grep 0280
06:00.0 Network controller [0280]: RaLink Device [1814:3062]

```

With lsmod | grep rt2 I got nothing (is the supposed to happen?)

With iwconfig I got

```
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by chili555 on 2011-07-03
Congratulations, my friend, your geek-o-meter is about to peg! Your device is a rare device that requires the download of a driver from the chipset manufacturer Ralink and then needs to be compiled. Start with post #30 here: [http://ubuntuforums.org/showthread.php?p=10990552](http://ubuntuforums.org/showthread.php?p=10990552)

Notice you have the same pci.id 1814:3062. Therefor, you have the same chipset and require the same driver. Note this:> Please note that you need build tools and headers:
```
sudo apt-get install build-essential linux-headers-generic

```We will go about getting these packages installed a slightly different way. Please drop the install CD in the tray and open System > Administration > Synaptic Package Manager. Open Settings > Repositories and select CD/DVD-ROM. Press reload and let Synaptic index all the packages on the install CD. Look for build-essential and then linux-headers-generic and install them. A few other packages will be installed, too.

Now we go to post #13 here: [http://ubuntuforums.org/showthread.php?t=1790271&page=2](http://ubuntuforums.org/showthread.php?t=1790271&page=2)

You can download the package on your Windows partition and transfer it on a USB stick to Ubuntu and then proceed as I outlined there.

It looks a bit daunting, but go slow and follow the instructions exactly. Most important, stop and ask if you get stuck or don't understand. The doctor is in and I'm ready to help any way I can.> With lsmod | grep rt2 I got nothing (is the supposed to happen?)That's perfect! That means no conflicting driver is loaded. Sometimes, "I have nothing to report" is a great answer.

---

### Post by bobbert4ever on 2011-07-04
I have decided I'm just going to wait to get a wired internet connection and use windows for now.

---

### Post by MaindotC on 2011-07-04
> **bobbert4ever said:**
> I have decided I'm just going to wait to get a wired internet connection and use windows for now.

When you do, you may want to get finallyfastpc.com and/or spysherriff to prevent these types of issues.

---

### Post by bobbert4ever on 2011-07-05
> **MaindotC said:**
> When you do, you may want to get finallyfastpc.com and/or spysherriff to prevent these types of issues.

Is that a joke I hope?

---

### Post by chili555 on 2011-07-05
> **bobbert4ever said:**
> Is that a joke I hope?I hope it was. Not every post on these forums is relevant or helpful.

---

### Post by ajpulley on 2011-08-19
Regarding post #6, the first Terminal command that was being asked to enter was:

lspci -nn | grep 0280

What character is the vertical line between "nn" and "grep" is that?  

I'm having the same issue, but I don't know how to enter the vertical line in Terminal.  I wanted to see if the same post would apply to me based on the results in post #7.

I was able to enter:
iwconfig

and this is what I got (I have to type it manually to reproduce it here):

lo          no wireless extensions.

eth0      no wireless extensions.

wlan0    IEEE 802.11bgn  ESSID:off/any
            Mode:Managed  Access Point: Not-Associated    Tx-Power=20 dBm
            Retry long limit:7     RTS thr:off     Fragment thr: off
            Power Management:off

I haven't a clue what any of that means.

---

### Post by ajpulley on 2011-08-19
Further reading led me to post [#13]("http://ubuntuforums.org/showpost.php?p=10988338&postcount=13").  

I had previously downloaded that folder... and hadn't a clue what to do with it, or how.

---

### Post by chili555 on 2011-08-19
So, did you get the module built? Is it all working now?

---

### Post by ajpulley on 2011-08-20
No.  After entering:

cd Desktop/2010

The following is displayed:

Bash:  cd:  Desktop/2010:  No such file or directory

On my desktop is the folder "DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1)20101217"

Is that file supposed to be renamed 2010?  I'm missing something here, but can't put two and two together.

---

### Post by chili555 on 2011-08-20
Then type:```
cd Desktop/DPO
```Press Tab and the remainder of the file name will fill in automatically. Press Enter. Proceed with the instructions as before.

---

### Post by ajpulley on 2011-08-20
Renamed the folder on the desktop to "2010".  Then, the commands with the " >> ", I entered the whole command together with no spaces.  That seemed to work because as a result, the wireless is now running, and my Update Manager is downloading.

I would like to know why removing all the spaces in the command line worked.  Was is supposed to?  

And, what exactly, in layman's terms, did I just do?

I figured out by using the sudo su command, and subsequently entering my password, I was allowed to administer commands as a root, I think it's called, user.  But, beyond that, I haven't a clue.

I think next time I'm at a book store, I'll head over to the foreign language section and look for an english-to-commandline dictionary.

---

### Post by chili555 on 2011-08-20
> I would like to know why removing all the spaces in the command line worked. Was is supposed to?I think it works just as well with or without spaces.```
echo some_parameter >> /etc/some_file.conf
```I use spaces because it's more readable both on the forum and in the terminal. I don't understand why you felt you needed to modify what I suggested you do by removing spaces. Are you saying what I've attached didn't work for you?> I figured out by using the sudo su command, and subsequently entering my password, I was allowed to administer commands as a root, I think it's called, user.Correct.

You compiled from source the correct, working driver for your wireless. You blacklisted, so it wouldn't load and interfer, the incorrect, not working driver.

Whenever a newer kernel version, or linux-image as it's called in Ubuntu, gets installed by Update Manager, you'll need to recompile the driver against the newer kernel. Add one step:```
cd Desktop/2010
sudo su
make clean
make
make install
modprobe rt3562sta
exit
```If you have more questions, please post back.

---

### Post by ajpulley on 2011-08-20
After Update Manager completed, rebooted and lost wireless capabilities.  However, completed the process I did above, rebooted, and it is enabled again... for the time being.

---

### Post by ajpulley on 2011-08-20
> **chili555 said:**
> I think it works just as well with or without spaces.```
echo some_parameter >> /etc/some_file.conf
```I use spaces because it's more readable both on the forum and in the terminal. I don't understand why you felt you needed to modify what I suggested you do by removing spaces. Are you saying what I've attached didn't work for you?Correct.

You compiled from source the correct, working driver for your wireless. You blacklisted, so it wouldn't load and interfer, the incorrect, not working driver.

Whenever a newer kernel version, or linux-image as it's called in Ubuntu, gets installed by Update Manager, you'll need to recompile the driver against the newer kernel. Add one step:```
cd Desktop/2010
sudo su
make clean
make
make install
modprobe rt3562sta
exit
```If you have more questions, please post back.

Sorry, I didn't see this when I just posted.  Yes, entering the (2) command lines with the ">>", and only those two, would not work.  But, removing the space just before and just after the ">>" allowed the process to complete.  

And, yes, you were right, I had to do it again after the update manager completed.  Next time, I will try the additional step you listed above.

Can you explain why I must update the driver this way, whereas my NVIDIA driver shows up in the driver update utility? (Obviously, I'm glad I can update it this way so I can first establish a connection due to the inability to use a 100/1000 Base-T connection.)

---

### Post by chili555 on 2011-08-20
I wonder if you'd use thread tools at the top and Mark Solved.

---

### Post by ajpulley on 2011-08-20
> **chili555 said:**
> I wonder if you'd use thread tools at the top and Mark Solved.
Looking for thread tools now...

Edit:  Not finding "Solved".

---

### Post by chili555 on 2011-08-20
> **ajpulley said:**
> Looking for thread tools now...

Edit:  Not finding "Solved".Sorry. You won't find it, because you weren't the original poster. Sorry, I just noticed.> entering the (2) command lines with the ">>", and only those two, would not work.What was the error?

---

