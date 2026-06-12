---
title: "Strange wifi problem"
date: 2013-08-05
forum: Networking &amp; Wireless
---

### Post by mbeltoft on 2013-08-05
Im having a strange problem with my wifi. Its very slow when ever my laptop running ubuntu 13.04 is connected to it. 

My setup: asus n16 router running asuswrt-merlin fw (have also tried with dd-wrt), wifi is secured with wpa2 personal. 
Server is running ubuntu 13.04 and is connected to the router by cable. 

When I'm copying a file from the server to my android tablet via wifi im getting speeds between 20 and 40 kb/s when my laptop is connected to the same network.  As soon i disconnect the laptop the transfer speed to the tablet goes up to about 3mb/s.
When i reconnect the laptop the speed drops again. 

Any ideas why this is happening?

---

### Post by chili555 on 2013-08-05
There is a driver that is known to hog the bandwidth. Let's see if you have it. Please open a terminal and run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by mbeltoft on 2013-08-05
Here you go

```
12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```

---

### Post by chili555 on 2013-08-05
There are two drivers that drive this device, each with varying degrees of success. Let's see which you have:```
lsmod | grep -e wl -e brcmsmac
```

------

EDIT: Note to chili: [http://ubuntuforums.org/showthread.php?t=2131244](http://ubuntuforums.org/showthread.php?t=2131244) (Wrong way to do it, but use brcmsmac instead of wl???)

---

### Post by mbeltoft on 2013-08-05
```

 lsmod | grep -e wl -e brcmsmac
wl                   3074449  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
cfg80211              510937  1 wl

```

---

### Post by chili555 on 2013-08-05
> **mbeltoft said:**
> ```

 lsmod | grep -e wl -e brcmsmac
wl                   3074449  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
cfg80211              510937  1 wl

```Let's try the other driver.```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -r wl
sudo modprobe brcmsmac
```Any improvement? It may take a reboot.

---

### Post by mbeltoft on 2013-08-05
got at error on the second commando:

 sudo modprobe -r wl
FATAL: Module wl not found.

and the last one don't give me any output so don't know if it was working or not.

rebooting now to check if its working


EDIT: it looks like its working. I can get the expected speed on a file transfer while the laptop is connected. :D

thanks for the help

---

### Post by Chet Hardin on 2013-10-04
Hey Chili555. 

I had the same problem as mbeltoft. My wifi was working great, but it was a bandwidth hog. I followed your instructions, and got the other driver working. But now, I am creeping along with seriously slow speeds, or it just disconnects. 

Got any ideas?

Thanks

---

### Post by chili555 on 2013-10-04
> **Chet Hardin said:**
> Hey Chili555. 

I had the same problem as mbeltoft. My wifi was working great, but it was a bandwidth hog. I followed your instructions, and got the other driver working. But now, I am creeping along with seriously slow speeds, or it just disconnects. 

Got any ideas?

ThanksWhich Ubuntu version do you have?```
lsb_release -d
arch
```

---

### Post by Chet Hardin on 2013-10-04
Hey. 

13.04 and x86 64

Thanks.

---

### Post by chili555 on 2013-10-05
Your problem is strange, indeed. It's probably a lot deeper than most Ubuntu users understand, actually. Have a look at the mess here: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1097519](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1097519) 

I participated in a fix, albeit for Ubuntu 12.04, here: [http://askubuntu.com/questions/337643/problem-with-ubuntu-12-04-and-ideapad-n581-broadcom/337658#337658](http://askubuntu.com/questions/337643/problem-with-ubuntu-12-04-and-ideapad-n581-broadcom/337658#337658)

Frankly, I am not totally sure what the best solution is for 13.04; I don't have the device. So, I'm asking you to help us out and test my proposed solution from askubuntu.com:```
wget http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb
sudo dpkg -i bcmwl*.deb
```If there are errors, please capture and post them here. If there are no errors (fingers crossed!), reboot and let us have your report.

---

### Post by Chet Hardin on 2013-10-05
Hey Chili.

The wifi seems to be running better, although Connection Information says that I am running at 19 mb/s.

Here are the errors I encountered: 

```
DKMS: install completed.
Error: Module b43 is not currently loaded
Error: Module b43legacy is not currently loaded
Error: Module ssb is not currently loaded
Error: Module bcm43xx is not currently loaded
Error: Module brcm80211 is not currently loaded
Error: Module brcmfmac is not currently loaded
Error: Module brcmsmac is not currently loaded
Error: Module bcma is not currently loaded
```

---

### Post by Chet Hardin on 2013-10-05
OK, now connection information says that I am running at 72 mb/s. And I am streaming Netflix from my iPad right next to the ubuntu machine, which I couldn't do before these changes. So, I am tentatively optimistic that all is well. 

Thanks Chili!

---

### Post by chili555 on 2013-10-05
> **Chet Hardin said:**
> OK, now connection information says that I am running at 72 mb/s. And I am streaming Netflix from my iPad right next to the ubuntu machine, which I couldn't do before these changes. So, I am tentatively optimistic that all is well. 

Thanks Chili!Awesome! I look forward to your further report. By golly, I think we may have solved it!

---

### Post by Chet Hardin on 2013-10-27
Hey Chili555. Here's the update. The wifi is still working, but it seems to be hogging the bandwidth again. Got any ideas?

Thanks

---

### Post by chili555 on 2013-10-27
Please let us see:```
sudo dpkg -s bcmwl-kernel-source
```

---

