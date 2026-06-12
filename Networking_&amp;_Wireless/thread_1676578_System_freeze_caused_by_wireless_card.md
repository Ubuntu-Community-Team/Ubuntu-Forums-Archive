---
title: "System freeze caused by wireless card?"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by Benic on 2011-01-27
I have a slightly different problem than the usual b43 driver problem installation in maverick. Everything was fine until the last upgrade from 9.10 to 10.10. I've been able to install the b43 driver without big problems. Wireless works just as it did before. But now, the whole system freezes after a moment and I highly suspect this is related to the wireless card, because it doesn't happen when wireless is not in use. 

The symptom is a slow-moving mouse and if I ever dare to touch a key, the system freezes and needs a hard reset.

Here's the wireless chptset:
```
portable@portable1:~$ lspci -vvnn | grep 14e4
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```

Here's a little overview of what I've got in the logs after a crash:

syslog
Jan 26 21:08:34 portable1 kernel: [  830.544142] BUG: scheduling while atomic: irq/11-b43/839/0x00000101
kernlogJan 
26 21:10:23 portable1 kernel: [   46.272107] wlan0: no IPv6 routers present
Jan 26 21:56:27 portable1 kernel: [ 2810.480096] BUG: scheduling while atomic: irq/11-b43/836/0x00000101

This looks like bug #[560409]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBYQFjAA&url=https%3A%2F%2Fbugs.launchpad.net%2Fubuntu%2F%2Bsource%2Flinux%2F%2Bbug%2F560409&rct=j&q=ubuntu%20maverick%20bug%20atomic%20scheduling%20b43&ei=d59BTYTVHYH88Aayvp3hAQ&usg=AFQjCNHYZAVoYFjiCazjg21edFLZiDlyJA&cad=rja"), already present in 10.04 and supposed to be corrected in 10.10.

debug
Jan 26 21:10:09 portable1 modem-manager: (tty/ttyS0): port's parent platform driver is not whitelisted
Jan 26 21:10:09 portable1 modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Jan 26 21:10:09 portable1 modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Jan 26 21:10:09 portable1 modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Jan 26 21:10:12 portable1 kernel: [   36.132930] wlan0: authenticate with 00:14:d1:40:30:0d (try 1)
Jan 26 21:10:12 portable1 kernel: [   36.134357] wlan0: authenticated
Jan 26 21:10:12 portable1 kernel: [   36.134717] wlan0: associate with 00:14:d1:40:30:0d (try 1)
Jan 26 21:10:12 portable1 kernel: [   36.136893] wlan0: RX AssocResp from 00:14:d1:40:30:0d (capab=0x431 status=0 aid=1)
Jan 26 21:10:12 portable1 kernel: [   36.136902] wlan0: associated
Jan 26 21:10:14 portable1 rtkit-daemon[1235]: Successfully called chroot.
Jan 26 21:10:14 portable1 rtkit-daemon[1235]: Successfully dropped privileges.
Jan 26 21:10:14 portable1 rtkit-daemon[1235]: Successfully limited resources.
Jan 26 21:10:14 portable1 rtkit-daemon[1235]: Running.
Jan 26 21:10:14 portable1 rtkit-daemon[1235]: Watchdog thread running.
Jan 26 21:10:14 portable1 rtkit-daemon[1235]: Canary thread running.
Jan 26 21:10:14 portable1 rtkit-daemon[1235]: Supervising 1 threads of 1 processes of 1 users.
Jan 26 21:10:15 portable1 rtkit-daemon[1235]: Supervising 2 threads of 1 processes of 1 users.
Jan 26 21:10:15 portable1 rtkit-daemon[1235]: Supervising 3 threads of 1 processes of 1 users.
Jan 26 21:10:23 portable1 kernel: [   46.272107] wlan0: no IPv6 routers present

You can also take a look at the daemon log attached.

Anyone has an idea of what's going on? I've tried to re-installed the b43 driver and updated the kernel without success.

---

### Post by Benic on 2011-01-28
Bump... Am I the only one experiencing this problem?

---

### Post by SYNchroACK on 2011-01-29
No! I have the same problem since 3 weeks ago in **Fedora 14** and now, with **Ubuntu 10.10**, I dont know what can i do... i dont see anything suspect in 'syslog' file. :S

My laptop is an **Asus K50ID** with a wireless card **Atheros**.

Help please,[I]
Thanks[/I].

SYNchroACK

---

### Post by Benic on 2011-01-29
Hmmm... I thought this problem was only affecting Broadcom chipsets.

I did a clean install of 10.10 yesterday.  The same problem occurs after some time. I'll take a closer look at the logs, to see if there is some pattern I can find.

I also tried ndiswrapper but I couldn't make it work properly.

I'm testing some different power management settings (acpi=off, noapic, nolapic, etc.) to see what happens.

---

### Post by SYNchroACK on 2011-01-29
Whatever, I installed Ubuntu 10.04 (32bit) and works fine. ... :(

---

### Post by Benic on 2011-01-31
It seems to be a power management issue and I have found a solution. I have an old Dell Latitude C840 and I used to have a problem with a pcmcia usb hub. It was constantly crashing after some time when I was using it with an external hd. In a post in ubuntuforums, someone said the solution was to set acpi to off in grub. It did work for me. So I thought that the wireless card problem could be related to the pcmcia problem.
Here's what I did: 

edit /etc/default/grub 
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off"

sudo update-grub

Just reboot and it's done.

EDIT: I thought this would have solved the problem... I've cheered too early! It still happens, but less often than before. Still looking for a definitive solution.

---

### Post by bmwpanda on 2011-02-04
You are not the only one having the issue, I have the same issue with the same card BCM4318 on a Dell Precision M50.  Please let us know if you are able to find a solution.

I am new to ubuntu so I am not able to troubleshoot properly.  Took me over a week to get the card working!

---

### Post by Benic on 2011-02-04
Well, I think I've found a working solution. After a couple of days, the problem is definitively gone. The problem is I don't have any idea why it works! 

As I said, I've tried to install ndiswrapper and use it. It didn't work, so I had to uninstall ndiswrapper and use the b43 driver again. I don't know why, but after that, my wireless card works like a charm! To be sure, I purged b43 and re-installed it. No luck, the same crash happened again. After installing and uninstalling ndiswrapper, no more crash.

Here's what I did

Install ndiswrapper:
```
sudo apt-get install ndisgtk
```

Then I charged the bcmwl5 driver recommended by ndiswrapper.

Check to see if the driver is loaded correctly and apply the setting:
```
ndiswrapper -l
sudo ndiswrapper -m
```

Remove the b43 driver:
```
sudo modprobe -r b43
```

Edit blacklist.conf to add b43;
```
echo "blacklist module_a_backlister"|sudo tee -a /etc/modprobe.d/blacklist.conf
```

Load ndiswrapper:
```
sudo modprobe ndiswrapper 
```

In my case, it didn't work. To revert back to b43, it is better to have direct internet access:
Edit /etc/modprobe.d/blacklist to remove b43
sudo modprobe -r ndiswrapper
sudp apt-get purge ndisgtk

Go back in the menu and activate the proprietary driver again. Then reboot and it's done.

---

### Post by bmwpanda on 2011-02-04
Did you keep acpi off?

---

### Post by Benic on 2011-02-04
Yes, otherwise I can't use my pcmcia usb hub. Yet I don't know if it makes a difference for this specific problem.

---

### Post by bmwpanda on 2011-02-04
Yea, didn't work for me:(

---

### Post by Benic on 2011-02-10
Well, well, after all it's still not working properly. It crashes anytime from 2 minutes to 2 hours.

I will try with another wireless card to see if it fixes the problem. Otherwise, I'll revert back to good old Karmic, which was running flawlessly!

---

### Post by bmwpanda on 2011-02-10
I think this issue may mainly lie with this linksys card :(.  Through my many hours of googling... it seems that a different card would resolve this issue.  Keep us up-to-date!

Thanks

---

### Post by DaveJ1337 on 2011-02-16
This definitely isn't just happening on Broadcom cards, I'm having the same problem and I'm using an Atheros card:

01:07.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

I initially suspected the problem came from the "bleed" repository that I'd enabled a while ago, so I backed everything important up to my Ubuntu One folder and did a clean install of 10.10.

Here's what's interesting:  Vanilla 10.10 worked flawlessly, as did the first barrage of updates.  The second set of updates, however, introduced the problem again which means this is a regression caused by one of the updates.

As of now, I have to kill the power on my machine about three times in a row before I can get it to connect to my wireless network without locking the system up completely.  I have found that if I log in and then CANCEL the prompt to unlock my keyring (and thus connect to the internets) and then let the computer idle for about 5 minutes before I connect it will have a better chance of connecting without freezing the system.

I'm going to look for a bug on this and open one if I don't find any.  Once I do, I'll post a link to it here and we can hopefully get some attention paid to the issue.

----
follow-up: 
The closest bug I found was this:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668498](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668498)
It suggested installing a pre-release kernel, so I tried it and it worked like a charm.  I can't make any promises, and I recommend backing up your files first just in case, but I was able to fix this by downloading the 3 applicable .deb files from:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/)

and, after they're all in one folder, installing them with:

sudo dpkg -i *.deb

---

### Post by Benic on 2011-02-17
Just got a new Intel 2280BG wireless card. So far, so good!

DaveJ1337: You're following an interesting path and a little follow-up would be truly appreciated!

---

