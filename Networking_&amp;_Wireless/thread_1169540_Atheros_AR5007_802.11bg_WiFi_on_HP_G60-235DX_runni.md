---
title: "Atheros AR5007 802.11b/g WiFi on HP G60-235DX running Ubuntu 9.04"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by Muki on 2009-05-25
Have searched and skimmed quite a few posts on how to get this wireless card to work, many with conflicting information, or info not valid for my version of Ubuntu or my wireless card model.

If anyone comes up with a way to make this work, I am all ears. Or if a fairly seasoned Ubuntu guy has struggled with this and suggests I throw in the towel and buy a USB wifi card, please say that as well. Grateful for a suggestion on the model I should buy then.

It doesn't show up when I do an lspci, or an ifconfig, or a lshw.

I am running Ubuntu 9.04 through Wubi on Windows 7 RC, in case that matters.

Thanks in advance.

Update: The card shows up in lshw as AR242x 802.11abg PCI Express Adapter, after blacklisting...

---

### Post by t0mppa on 2009-05-25
If it doesn't show up on lspci, then the interface doesn't exist as far as Ubuntu is concerned and thus you can't get it to work.

Are you sure you haven't disabled it with a button on your laptop? My Atheros card tends to disappear from lspci, if I do that.

---

### Post by Muki on 2009-05-26
I don't think so, Tomppa, but I will investigate. Thanks for the suggestion. Kiitos/Tack!

---

### Post by superprash2003 on 2009-05-27
try this [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

### Post by Muki on 2009-05-27
Superprash2003. Thank you! The lshw -C network did not show that the Atheros card was being detected, so I looked for the blacklist file in the /etc/modprobe.d directory. There was none, so I created one and put in the two blacklist lines for the ath_hal and ath_pci. After reboot, the lshw -C network was showing an "unclaimed" network device called AR242x 802.11abg PCI Express Adapter. Hooray! Thanks.

I am, however, unable to access the backports for Intrepid. Would they be available to me, if I am already on 9.04 Jaunty??? From what I have read about the backport concept, this would not be logical. But I am not very versed in Ubuntu -- yet.

What do you think, Babu?

---

### Post by igotnoluck on 2009-05-27
I have the same card (only on a LG laptop)
it worked for me (without any need of madwifi like in 8.10)
the problem was that it didn't want to connect to any WPA Enterprise network (in my campus) so
I went back to 8.10

maybe try to install the madwifi on 9.04.

---

### Post by superprash2003 on 2009-05-27
use jaunty backports instead , just replace intrepid with jaunty

---

### Post by Muki on 2009-05-27
I had already installed the jaunty backports. Am getting the same error as "j" from you own forum:
"j said... @ May 20, 2009 9:30 AM  
I have tried all of this to no avail. The only driver it lists in Hardware Drivers is the madwifi driver and when I activate it it give me an error saying the device was just disabled but is still in use. Any suggestions?"
Any ideas? I am running Ubuntu through wubi, if that matters, on top of Windows 7 RC.
Thanks Babu!

---

### Post by superprash2003 on 2009-05-28
well jaunty backports does exist [http://packages.ubuntu.com/jaunty/linux-backports-modules-jaunty](http://packages.ubuntu.com/jaunty/linux-backports-modules-jaunty) .. i still didnt understand the error you mentioned..

---

### Post by t0mppa on 2009-05-28
So, what driver are you exactly trying to install there?

On 8.10 ath5k was listed in Hardware Drivers as the secondary option. On 9.04 ath5k was made the default driver and the original MadWifi put to secondary status though, since ath5k should be superior by now.

The tutorial superprash is referring to is misleading, because it says that to blacklist ath5k you have to add blacklists for ath_pci and ath_hal, which are modules of the original MadWifi driver. Ath5k_pci is the module used by ath5k. On top of that 9.04 already has /etc/modprobe.d/blacklist-ath_pci.conf file by default which blacklists ath_pci, so it won't conflict with ath5k.

Also, you couldn't find the blacklist file, because on 9.04 all the blacklist files have a .conf extension, as Ubuntu is moving away from the extensionless files. The system will give you a warning each time you use modprobe, if you have files without a .conf extension in the /etc/modprobe.d/ directory.

So, I suggest you run 'lsmod | grep ath' from the terminal to see if you have modules related to either driver loaded. If so, use 'sudo modprobe -r <module_name>' to remove them to start from a clean plate. Then pick either ath5k or the madwifi driver and see if you can get it to work. Notice that if you pick the madwifi one, you'll have to comment out (add # in front of the line) or delete the blacklist entries for ath_pci and ath_hal.

The error you describe from the Hardware Drivers happens sometimes. That's why I prefer to install the madwifi by compiling it manually from the source, when I need to use it (have an AR5007 which shows as AR242x as well and both of these drivers work for it).

---

### Post by Muki on 2009-05-28
--> Superprash: Sorry if I was unclear. I had already enabled the Jaunty backports and downloaded them as part of an earlier update action.

--> T0mppa: Thanks. Very good explanation. I will give it a try. Paljon kiitoksia!

---

