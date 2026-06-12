---
title: "Getting Alfa WUS036NHR to Work"
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by Victor99 on 2013-04-07
HI! I just got an Alfa WUS035NHR afdapter. I  dual boot with xp and ubuntu 12.04. I'm new at linux and I'm learning  ubuntu. I plugged the card in, and put the cd in in xp. No problems. I  noticed during installation that it had a linux option. Rebooted went to  ubuntu, put in disk, and nothing. So I accessed the disk in file  manager and clicked in autorun and received a meaage from the archive  manager that it couldn't unzip the file(s). It's then that I realized exe files don't work in linux. So I went to this site
      [http://store.rokland.com/blogs/featured ... 36nhr-is-b]("http://store.rokland.com/blogs/featured-stories/6347758-alfa-awus036nhr-is-b")
and  tried to install it from the directions. I unzipped the downloaded  file, started a terminal, and tried to navigate to the file. I attached a screnshot of what I dud in the terminal. Here's a list of the file.

       Alfa
         RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20010715 which contains:
                   android_refernce_codes
                   document
                   driver
                   wpa_supplicant_hostapd
                   install.sh
                   readme.txt 
                  ReleaseNotes.doc
I opened the driver directory and evtracted rtl8192_8188CU_linux_v3.0.2164.20010715 .tar.gz into the same directory.
          rtl8192_8188CU_linux_v3.0.2164.20010715 
                   core
                   hal
                   include 
                   os_dep
                   autoconf_rtl8192c_lusb_linux.h
                   clean
                   ifcfg_wlan0
                   Kconfig
                   MakeFile
                   runwpa
                   wlan0dhcp
What  am I missing? I think I've tried every variation of typing in the path.  Should I have not extracted rtl8192_8188CU_linux_v3.0.2164.20010715  .tar.gz? Any and all responses will be greatly appreciated. Thanks.

---

### Post by chili555 on 2013-04-07
Generally, the files included on the accompanying CD are too old by the time it's manufactured, shipped, sold and opened by the consumer. However, Ubuntu 12.04 is a bit older as well, so let's give it a try.

What did the readme.txt say to do??

I suspect you will need to install the prerequisites:```
sudo apt-get install linux-headers-generic build-essential
```Then navigate in the terminal to the location of the driver:```
cd Alfa
sudo su
sh install.sh
exit
```Either it will install perfectly or an error that we can use to troubleshoot will be thrown. Post it, if any, and we'll proceed.> I'm new at linux and I'm learning ubuntu.You are doing very well so far!

---

### Post by Victor99 on 2013-04-09
Thanks for the response. I had to change to a directory below Alfa to get to the install.sh command. I did the header  build essential command then ran the install.sh command from the above lower directory. I got an error message at the end of 4 pages of terminal. Here's the results in the attached files. I sse that they uploaded in reverse order---the 4th has the error message.  Thanks.

---

### Post by chili555 on 2013-04-09
I suspected the driver was too old to compile correctly against your 3.2.xx kernel. I suggest you try the compat-wireless package, built for Ubuntu:```
sudo apt-get install linux-backports-modules-cw-3.6-precise-generic
```Reboot and let us hear your report.

---

### Post by Victor99 on 2013-04-10
Thanks for the response. Nada. I did ifconfig, and no wireless. I did iwconfig and no wireless extensions. I looked in network in system settings, and there's no tab for wireless. The drivers I used are from the webpage link in the first post. Thanks.

---

### Post by chili555 on 2013-04-10
> **Victor99 said:**
> Thanks for the response. Nada. I did ifconfig, and no wireless. I did iwconfig and no wireless extensions. I looked in network in system settings, and there's no tab for wireless. The drivers I used are from the webpage link in the first post. Thanks.
Are there any informative clues here?```
sudo modprobe rtl8192cu
dmesg | grep rtl
rfkill list all
```

---

### Post by Victor99 on 2013-04-11
Thanks for the response. There's a lot of errors showing up. I'm sending more screenshots, but I might have to start another reply to show them all as the dmesg command went to 6 pages. Thanks.

---

### Post by Victor99 on 2013-04-11
Here are the other 2 screenshots.

---

### Post by chili555 on 2013-04-11
> **Victor99 said:**
> Here are the other 2 screenshots.And this is after installing backports and a reboot? Or no reboot? If not, please do so and try again:```
sudo modprobe rtl8192cu
```If there are massive errors, there is no need to post them all here, just the last three lines or so.

---

### Post by Victor99 on 2013-04-11
Thanks for the response. Disregard the above 2 replies. I noticed as I closed firefox that I had updates to install. After the updates, I rebooted, and Voila! I had wireless network. I just glanced at the updates as I hit install and saw a couple of compat updates. So which commands worked? Thanks.

---

### Post by chili555 on 2013-04-11
> **Victor99 said:**
> Thanks for the response. Disregard the above 2 replies. I noticed as I closed firefox that I had updates to install. After the updates, I rebooted, and Voila! I had wireless network. I just glanced at the updates as I hit install and saw a couple of compat updates. So which commands worked? Thanks.Awesome! Glad it's working. I suspect the installation of the compat-wireless suite was what did it.

Have fun.

---

### Post by Victor99 on 2013-04-21
Hi! I'm back again. I had connected the wired connection when I switched to XP, so I didn't notice until now that the wireless connection is no more. I remember from earlier searching about this problem an article describing an install of, I'm not sure if it was this device or a different version of alfa, that you had to edit some config file, or all the settings are lost the next time you boot. I don't remember which file, but I do remember something about adding to the file info on the adapter, and als something about WPA Supplicant. I thought I had bookmarked thIs page, but apparently not. Can somebody help me on this? I assume that i'd have to follow all of the abive steps, then edit the file. Any and all responses will be greatly appreciated. Thanks.

---

### Post by chili555 on 2013-04-21
Please try this:```
sudo modprobe rtl8192cu
```Did that bring your wireless to life? If so, let's get it to load automatically:```
sudo su
echo rtl8192cu >> /etc/modules
exit
```

---

### Post by Victor99 on 2013-04-21
Thanks for the response. I tried the code you posted, but nothing happened. I looked at network under system settings and there's nothing there for wireless. Ifconfig shows eth0 and lo, and iwconfig shows no wireless extensions.

---

### Post by chili555 on 2013-04-21
> **Victor99 said:**
> Thanks for the response. I tried the code you posted, but nothing happened. I looked at network under system settings and there's nothing there for wireless. Ifconfig shows eth0 and lo, and iwconfig shows no wireless extensions.Let's go back to basics; please run and post:```
lsusb
lsmod | grep rtl
rfkill list all

```

---

### Post by Victor99 on 2013-04-21
Thanks for the response. I've attached a screenshot of the 3 commands. rfkill just put up another prompt.

---

### Post by chili555 on 2013-04-21
Isn't the Alfa a USB device or am I corn-fuzed? *lsusb* doesn't show it. It probably won't work if it's not inserted.

Please post:```
lspci -nn | grep 0280
```

---

### Post by Victor99 on 2013-04-22
Thanks for the response. I think the adapter is kaput! I jusr sent an e-mail to rokland to see about resolving the issue. I went back to XP ---I dual boot, and it didn't show up there either. I removed the drivers, unplugged the adapter, replugged it in, and XP doesn't even come up with a found new hardware message. So I'm guessing it died. I had left it in the computer with a wired connection also attached, but I can't see how that would effect it. When I get the replacement, or my money back if they want me to pay postage, I'll get back to you. If they do want me to pay postage, then I'll probably be looking for another card. Thanks.

---

### Post by chili555 on 2013-04-22
> **Victor99 said:**
> Thanks for the response. I think the adapter is kaput! I jusr sent an e-mail to rokland to see about resolving the issue. I went back to XP ---I dual boot, and it didn't show up there either. I removed the drivers, unplugged the adapter, replugged it in, and XP doesn't even come up with a found new hardware message. So I'm guessing it died. I had left it in the computer with a wired connection also attached, but I can't see how that would effect it. When I get the replacement, or my money back if they want me to pay postage, I'll get back to you. If they do want me to pay postage, then I'll probably be looking for another card. Thanks.I will look forward to your report and I'll be very happy to help.

---

### Post by Victor99 on 2013-05-11
Hi! I'm back again. Finally received the replacement adapter. I installed it in XP, and it works fine. I haven't tried the Ubuntu instructions you gave me yet, as I want to find out how to edit the config file so I don't lose the install when I reboot. Thanks.

---

### Post by chili555 on 2013-05-11
I am not sure you need to do anything at all. What file did you think you might need to change?

---

### Post by Victor99 on 2013-05-12
Thanks for the response. You're right. I plugged it in, and it was detected, and it works. Thanks.

---

### Post by chili555 on 2013-05-12
Woo hoo! Glad it's working. Have fun!

---

