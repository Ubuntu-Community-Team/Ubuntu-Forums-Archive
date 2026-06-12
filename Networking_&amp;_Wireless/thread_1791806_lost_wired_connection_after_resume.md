---
title: "lost wired connection after resume"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by fiacobelli on 2011-06-27
Hi,
So, when I booted up, the wired connection was automatically detected and in use. Whenever I suspend my computer and then resume it later I lose the wired connection. It is detected (seen) by Networkmanager, but I can never connect.
I found a way to restore the connection, but it is manual and I was wondering if I could automate this process every time I resume. Details follow:

Laptop: HP dm1z, Natty 64bit. ethernet card: 
```

#lspci|grep Ethernet
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```
Likely culprit (according to dmesg)
```

#dmesg|grep r8169
r8169 0000:03:00.0: PME# disabled

```
No matter how many times I tried to restart my network services, it wouldn't work. Finally I saw clues to solve this [here]("https://bugzilla.redhat.com/show_bug.cgi?id=711197") and [here]("https://bugs.archlinux.org/task/22957") and it may help [here]("http://ubuntuforums.org/showthread.php?t=1790234&highlight=modprobe+r8169").
basically I had to 
```

#sudo rmmod r8169
#sudo modprobe r8169

```
Is there a way that I can either: enable the module on resume, or execute an automatic script after resume that will remove the module (rmmod) and re-install it (modprobe)?

Thanks!

---

### Post by chili555 on 2011-06-27
You might try this. ```
sudo gedit /etc/pm/config.d/config
```
Add one line:```
SUSPEND_MODULES="r8169"
```I have no idea if it will work; some report it's working, some not. Nothing ventured, nothing gained.

---

