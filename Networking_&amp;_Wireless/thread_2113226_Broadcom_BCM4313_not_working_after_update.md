---
title: "Broadcom BCM4313 not working after update"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by Tacuabe on 2013-02-06
Hi!

I've been using Ubuntu and, lately Lubuntu, for about seven years.

On my HP Mini netbook there's Lubuntu 12.04.2 LTS with Kernel 3.2.0-37 generic i686. Wireless is Broadcom Corp. BCM4313 802.11 b/g/n and the PCI-ID is [14e4:4727] (rev 01). Installed driver is wl and I use Wicd.

Everything worked flawlessly (including my wireless HP printer) until a couple of days ago. At that time I was notified that an update was available. Using the Update Manager I proceeded to update my system, as I usually do in this case.

After updating I noted a erratical behaviour of the wireless. It would not work on a first login, but it will work normally after rebooting. Sometimes it will work OK without rebooting. The printer stopped working altogether in all cases.

I usually take a look at what the update is about. In this case I recall that the Kernel was updated and the Broadcom drivers too. Unfortunately I do not know how to check again the contents of this last update.

It seems obvious that updating somehow scrambled my settings producing the described behaviour. I tried reading similar posts, but most refer to a complete installation from scratch failing to work. This is not my case, as everything worked OK before updating.

Any help with this issue will be much appreciated.

---

### Post by DuckHook on 2013-02-06
The broadcom chipsets are simply ongoing headaches in Ubuntu, and Linux in general. I am not surprised that a kernel update or driver updates hosed your wireless; they routinely hose mine too. Since you've provided exceptionally and admirably detailed info about your BCM chipset, this shouldn't be too hard:

The main Ubuntu help page for the bcm43xx chipset is [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx").

Specifically, the instructions relevant to your chipset involve installing either *bcmwl-kernel-source* or* broadcom-sta*. More generally, the solution to your wonky behaviour will be to ```
sudo apt-get remove --purge
``` all of your existing drivers, delete the kernel modules, and reinstall them from the linked sources on the above-cited web page in order to "reset" them to proper working order. Be sure to use the --purge switch. You want to get rid of all your old config files that may be causing conflicts/problems.

The referenced help page gives excellent instructions. Read it through first to be confident of exactly what steps you will be taking and you should be good to go. If you have questions about any part of it, post back here and many of us will be glad to help. Let us know how it goes!

---

### Post by Tacuabe on 2013-02-07
Hi DuckHook!

Thanks for the quick turn-around and a comprehensive reply. 

I had previously visited the official page. That should explain why I was cautious to provide complete info on my setup.

There are some questions I do have before I plunge into the matter. I'd hate to mess it up even more!

From a more detailed analysis of the options, I'm inclined to use the bcmwl-kernel-source. However, there are yet two additional options for 12.04 to download: 5.100.82.38+bdcom-0ubuntu6 OR 6.20.155.1+bdcom-0ubuntu0.0.1 Which one should I use?

Additionally, the page lists instructions for 10.04 and 11.10 but none for 12.04. Could you guide me with this?

I use the terminal whenever I need to, but this is only occasionally. Could you expand a bit about the code you suggest? I'm not sure where the driver's name should be inserted or if more parameters are needed in order to carry out the cleanup you mention.

Many thanks again for your kind help.

---

### Post by DuckHook on 2013-02-07
I did not at first understand where you found the references to "5.100.82.38+bdcom-0ubuntu6 OR 6.20.155.1+bdcom-0ubuntu0.0.1", but now I see. I suspect that you've drilled down a little too far into the instructions: those instructions are for people who have no wired connection and therefore cannot access the internet from the problem machine at all. In this case, they have to download the driver another way, transfer it to their machine likely via USB stick, and install the driver with no network connection. If you have a wired connection, then you don't need to download the driver this way, and it is far better to make use of the driver already resident in the repositories.

Let me lay out the steps I would use. These are largely modelled on the instructions referenced in previous post, specifically:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A11.10_.28Oneiric_Ocelot.29_-_12.10_.28Quantal_Quetzal.29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A11.10_.28Oneiric_Ocelot.29_-_12.10_.28Quantal_Quetzal.29)

but with additional steps that I recommend in the spirit of both belts and suspenders:

1. Make sure that your wired connection works and the repositories are available,
2. Do: ```
sudo apt-get update
```3. Then: ```
sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
``` This removes all possible conflicting modules from your system RAM.
4. ```
sudo apt-get remove --purge bcmwl-kernel-source
``` This completely removes any old bcmwl-kernel-source and their config files.
5. ```
sudo shutdown -r now
``` ...to reboot.
6. ```
lsmod | egrep -i 'b43|ssb|wl|brcm|bcma'
``` ...which should return nothing. We are making sure that no possibly conflicting modules remain in memory.
7. ```
sudo apt-get install bcmwl-kernel-source
``` to install the proper driver.
8. Either reboot again, or: ```
sudo modprobe wl
```9. Wait one minute, then: ```
lsmod | grep wl
``` which should return "wl"
10. Test your connection by unplugging your wired connection. To be real anal about things, you can shutdown, then unplug, then boot back up, then test.

It is possible that we may need to load one of the alternate drivers after all. However, the above steps are still correct in principle: unload and delete all conflicting drivers, load up the one we want, then test. Let's start with the easiest one first.

Please let us know how it goes.

---

### Post by Tacuabe on 2013-02-08
Hi DuckHook!

Thanks for the help. I was able to follow your instructions to the letter. Since I had wireless Internet access anyhow, I did not use the wired connection. Nonetheless, every step executed correctly AFAIK.

Upon shutting down and restarting several times the connection was established immediately. No need for rebooting as before!

However, the wireless HP printer still fails to operate. I'm using HPLIP as recommended. Should I reinstall it or check for an update?
Make it work and it will clinch the whole issue. Please let me know your views on this.

Thanks again. Great job!

---

### Post by Tacuabe on 2013-02-08
I decided to try and update/reinstall HPLIP. Current was 3.12.09 and updated to 3.12.11 uninstalling previous version. No luck, still fails to print.

---

### Post by DuckHook on 2013-02-08
> **Tacuabe said:**
> However, the wireless HP printer still fails to operate.Solving this one will require more info:

1. Make and model.
2. Are you connected to a router? If so, by ethernet cable or wireless?
3. Is it assigned its address by DHCP, BOOTP or have you configured it with static IP? (This last can usually be read by forcing a printer (not OS) test page).
4. Try pinging this address. If you can ping, then it is likely a driver issue. If you cannot ping, then likely a communication issue.
5. Are you using the hplip graphical front-end? It is possible to configure hplip with the command line (actually it's more powerful that way) but this is not for beginners. Need a few callouses to tackle it that way.

Anyway, follow the instructions in [this]("http://ubuntuforums.org/showthread.php?p=12492401#post12492401") prior post, which dealt with somewhat the same matter. If it works, no need to go further. If not, then post back all observations and above info.

> Current was 3.12.09 and updated to 3.12.11General-purpose users should try to stick to the repository apps because they go through extensive testing to be stable with your version of OS. I realize there are times when this is not possible. A few years ago, I had to source-build a newer version of hplip because my brand new printer was too new to be supported by the binary in the repository, but if your printer is supported, it is generally best to stick to repository offerings.

As things now stand, we don't know if the new version you've downloaded is choking on older libraries. Too many variables to juggle. But try linked instructions above first, and we can go further if they don't work.

---

### Post by Tacuabe on 2013-02-09
I'm sorry to report that after after a few hours "rest", the following morning the wireless connection exhibited again the same failure symptoms. Once more rebooting is required to make it work as expected.

Since we are back to square one, I'm afraid the printer issue will have to be postponed until the main problem is solved. Anyway, thanks for providing a lot of information on same.

I wonder if using this "dude" wireless connection to repair itself could have affected the application of your detailed instructions. If you think this has any bearing please advise and I'll try a wired connection and redo all steps.

---

### Post by Hadaka on 2013-02-09
Hi, see if this resolves your problem

```
sudo modprobe wl
sudo su
echo wl >> /etc/modules
exit
 
```

---

### Post by DuckHook on 2013-02-10
> **Hadaka said:**
> Hi, see if this resolves your problem

```
sudo modprobe wl
sudo su
echo wl >> /etc/modules
exit
 
```

+1
Excellent suggestion. Try @Hadaka's suggestion first. If it doesn't solve your problem, then next time problem occurs, do ***not*** reboot. We want to see what is ***not*** working. Instead, post results of:

```
lsmod | grep wl
``````
dmesg | grep -i 'wl\|wlan'
``````
cat /var/log/kern.log | grep -i 'wl\|wlan'
``````
ifconfig
```for privacy x out all IP addresses (called "inet address") and MAC addresses (called "HWaddr") before posting
```
iwconfig
```for privacy x out ESSID and Access Point before posting.

Repeat: we do ***not*** want above from a working connection. Rather we want them generated from a ***non-working*** connection. Some output will be lengthy. Highlight output and tag as "code" by using the hash (#) button in posting box. This makes for much easier reading.

---

### Post by hemesh on 2013-02-10
Thanks a lot for your help DuckHook. I use HP g6-1201TX and faced problems similar to Tacuabe, however my wifi started working immediately after removing/purging bcmwl-kernel-source (step 5) and reinstalling it caused the problem to occur again.

Thanks a lot again.

Regards.
Hemesh.

---

### Post by DuckHook on 2013-02-10
> **hemesh said:**
> Thanks a lot for your help DuckHook. I use HP g6-1201TX and faced problems similar to Tacuabe, however my wifi started working immediately after removing/purging bcmwl-kernel-source (step 5) and reinstalling it caused the problem to occur again.

Thanks a lot again.

Regards.
Hemesh.

I don't understand if your problem is solved. If reinstalling causes problem whereas it worked without *bcmwl-kernel-source*, then problem is almost certainly conflicting drivers.

I gave bad instructions in my earlier posting (I'm still learning too) and the form of *grep* that I used won't work to see what modules are in memory. Instead do:```
lsmod | grep -i 'b43\|ssb\|wl\|brcm\|bcma'
```You should never see any more than one of those drivers resident at any one time. If there are two, it means they are fighting each other over control of your WIFI and neither will work. One has to be uninstalled.

---

### Post by Tacuabe on 2013-02-10
Hi both of you!

Thanks Hadaka for your suggestion. It appeared to work at first, but after some time it stopped working. For your guidance, once the code was applied, I turned of my computer several times and connection was automatically restored. I then left it alone for the night and the following morning it wasn't working anymore.

DuckHook, here's the info you requested taken from a NON-WORKING connection:

```
wl                   2906597  0 
cfg80211              178877  1 wl
lib80211               14040  2 lib80211_crypt_tkip,wl
```

```
[    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
[   17.345794] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.450812] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.450836] wl 0000:01:00.0: setting latency timer to 64
[   17.528762] INFO @wl_cfg80211_attach : Registered CFG80211 phy
```

```
Feb  7 10:31:23 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  7 10:31:23 hector-HP kernel: [   17.701585] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  7 10:31:23 hector-HP kernel: [   17.822573] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  7 10:31:23 hector-HP kernel: [   17.822596] wl 0000:01:00.0: setting latency timer to 64
Feb  7 10:31:23 hector-HP kernel: [   17.873884] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  7 15:28:04 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  7 15:28:04 hector-HP kernel: [   10.417526] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  7 15:28:04 hector-HP kernel: [   10.492818] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  7 15:28:04 hector-HP kernel: [   10.492836] wl 0000:01:00.0: setting latency timer to 64
Feb  7 15:28:04 hector-HP kernel: [   10.534794] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  7 15:29:39 hector-HP kernel: [  109.253585] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
Feb  7 22:08:30 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  7 22:08:30 hector-HP kernel: [   17.298931] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  7 22:08:30 hector-HP kernel: [   17.425814] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  7 22:08:30 hector-HP kernel: [   17.425835] wl 0000:01:00.0: setting latency timer to 64
Feb  7 22:08:30 hector-HP kernel: [   17.508132] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  7 22:10:28 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  7 22:10:28 hector-HP kernel: [   17.283854] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  7 22:10:28 hector-HP kernel: [   17.426956] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  7 22:10:28 hector-HP kernel: [   17.426979] wl 0000:01:00.0: setting latency timer to 64
Feb  7 22:10:28 hector-HP kernel: [   17.507678] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  8 15:24:38 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  8 15:24:38 hector-HP kernel: [   17.406771] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  8 15:24:38 hector-HP kernel: [   17.541337] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 15:24:38 hector-HP kernel: [   17.541361] wl 0000:01:00.0: setting latency timer to 64
Feb  8 15:24:38 hector-HP kernel: [   17.589206] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  8 15:25:44 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  8 15:25:44 hector-HP kernel: [   18.064833] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  8 15:25:44 hector-HP kernel: [   18.166288] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 15:25:44 hector-HP kernel: [   18.166313] wl 0000:01:00.0: setting latency timer to 64
Feb  8 15:25:44 hector-HP kernel: [   18.252125] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  8 23:39:18 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  8 23:39:18 hector-HP kernel: [   17.406963] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  8 23:39:18 hector-HP kernel: [   17.529779] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 23:39:18 hector-HP kernel: [   17.529804] wl 0000:01:00.0: setting latency timer to 64
Feb  8 23:39:18 hector-HP kernel: [   17.627697] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  8 23:41:47 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  8 23:41:47 hector-HP kernel: [   17.307578] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  8 23:41:47 hector-HP kernel: [   17.418871] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 23:41:47 hector-HP kernel: [   17.418895] wl 0000:01:00.0: setting latency timer to 64
Feb  8 23:41:47 hector-HP kernel: [   17.473182] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  8 23:56:03 hector-HP kernel: [  876.508509] wlc_lcnphy_rx_gain_tbl_free_entry = 5
Feb  8 23:56:03 hector-HP kernel: [  876.508602] wl 0000:01:00.0: PCI INT A disabled
Feb  8 23:59:26 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  8 23:59:26 hector-HP kernel: [   20.625556] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb  8 23:59:26 hector-HP kernel: [   20.627294] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb  8 23:59:28 hector-HP kernel: [   23.039884] wlan0: authenticate with 00:27:19:e8:0f:70 (try 1)
Feb  8 23:59:29 hector-HP kernel: [   23.041639] wlan0: authenticated
Feb  8 23:59:29 hector-HP kernel: [   23.045505] wlan0: associate with 00:27:19:e8:0f:70 (try 1)
Feb  8 23:59:29 hector-HP kernel: [   23.049828] wlan0: RX AssocResp from 00:27:19:e8:0f:70 (capab=0x431 status=0 aid=1)
Feb  8 23:59:29 hector-HP kernel: [   23.049842] wlan0: associated
Feb  8 23:59:29 hector-HP kernel: [   23.052101] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb  8 23:59:39 hector-HP kernel: [   33.496072] wlan0: no IPv6 routers present
Feb  9 00:01:42 hector-HP kernel: [  156.158272] wlan0: deauthenticating from 00:27:19:e8:0f:70 by local choice (reason=3)
Feb  9 00:01:42 hector-HP kernel: [  156.379359] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 00:01:42 hector-HP kernel: [  156.460929] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 00:01:42 hector-HP kernel: [  156.460957] wl 0000:01:00.0: setting latency timer to 64
Feb  9 00:01:42 hector-HP kernel: [  156.501593] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  9 00:04:06 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  9 00:04:06 hector-HP kernel: [   17.340633] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 00:04:06 hector-HP kernel: [   17.456316] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 00:04:06 hector-HP kernel: [   17.456338] wl 0000:01:00.0: setting latency timer to 64
Feb  9 00:04:06 hector-HP kernel: [   17.504335] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  9 00:09:15 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  9 00:09:15 hector-HP kernel: [   17.327015] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 00:09:15 hector-HP kernel: [   17.439629] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 00:09:15 hector-HP kernel: [   17.439650] wl 0000:01:00.0: setting latency timer to 64
Feb  9 00:09:15 hector-HP kernel: [   17.500101] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  9 00:14:12 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  9 00:14:12 hector-HP kernel: [   17.431009] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 00:14:12 hector-HP kernel: [   17.567787] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 00:14:12 hector-HP kernel: [   17.567810] wl 0000:01:00.0: setting latency timer to 64
Feb  9 00:14:12 hector-HP kernel: [   17.646426] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  9 00:54:21 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  9 00:54:21 hector-HP kernel: [   17.484909] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 00:54:21 hector-HP kernel: [   17.585320] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 00:54:21 hector-HP kernel: [   17.585344] wl 0000:01:00.0: setting latency timer to 64
Feb  9 00:54:21 hector-HP kernel: [   17.643813] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  9 08:48:35 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  9 08:48:35 hector-HP kernel: [   17.681283] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 08:48:35 hector-HP kernel: [   17.801706] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 08:48:35 hector-HP kernel: [   17.801730] wl 0000:01:00.0: setting latency timer to 64
Feb  9 08:48:35 hector-HP kernel: [   17.875302] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  9 08:50:28 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  9 08:50:28 hector-HP kernel: [   17.766829] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 08:50:28 hector-HP kernel: [   17.927953] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 08:50:28 hector-HP kernel: [   17.927975] wl 0000:01:00.0: setting latency timer to 64
Feb  9 08:50:28 hector-HP kernel: [   17.984344] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  9 09:45:59 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  9 09:45:59 hector-HP kernel: [   17.359985] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 09:45:59 hector-HP kernel: [   17.488508] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 09:45:59 hector-HP kernel: [   17.488531] wl 0000:01:00.0: setting latency timer to 64
Feb  9 09:45:59 hector-HP kernel: [   17.560097] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  9 09:49:08 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  9 09:49:08 hector-HP kernel: [   17.532557] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 09:49:08 hector-HP kernel: [   17.661859] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 09:49:08 hector-HP kernel: [   17.661879] wl 0000:01:00.0: setting latency timer to 64
Feb  9 09:49:08 hector-HP kernel: [   17.724585] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  9 19:00:07 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  9 19:00:07 hector-HP kernel: [   17.459350] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 19:00:07 hector-HP kernel: [   17.626837] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 19:00:07 hector-HP kernel: [   17.626861] wl 0000:01:00.0: setting latency timer to 64
Feb  9 19:00:07 hector-HP kernel: [   17.674724] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  9 19:02:57 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  9 19:02:57 hector-HP kernel: [   17.770017] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 19:02:57 hector-HP kernel: [   17.889291] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 19:02:57 hector-HP kernel: [   17.889312] wl 0000:01:00.0: setting latency timer to 64
Feb  9 19:02:57 hector-HP kernel: [   17.937684] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  9 21:27:15 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  9 21:27:15 hector-HP kernel: [   17.689840] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 21:27:15 hector-HP kernel: [   17.799542] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 21:27:15 hector-HP kernel: [   17.799567] wl 0000:01:00.0: setting latency timer to 64
Feb  9 21:27:15 hector-HP kernel: [   17.848184] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  9 21:28:20 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  9 21:28:20 hector-HP kernel: [   17.478875] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 21:28:20 hector-HP kernel: [   17.638638] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 21:28:20 hector-HP kernel: [   17.638660] wl 0000:01:00.0: setting latency timer to 64
Feb  9 21:28:20 hector-HP kernel: [   17.739998] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  9 22:29:15 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  9 22:29:15 hector-HP kernel: [   17.482984] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 22:29:15 hector-HP kernel: [   17.611591] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 22:29:15 hector-HP kernel: [   17.611612] wl 0000:01:00.0: setting latency timer to 64
Feb  9 22:29:15 hector-HP kernel: [   17.673121] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  9 22:30:15 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  9 22:30:15 hector-HP kernel: [   17.492386] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 22:30:15 hector-HP kernel: [   17.610141] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 22:30:15 hector-HP kernel: [   17.610163] wl 0000:01:00.0: setting latency timer to 64
Feb  9 22:30:15 hector-HP kernel: [   17.665981] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb  9 23:52:38 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb  9 23:52:38 hector-HP kernel: [   17.375033] wl: module license 'MIXED/Proprietary' taints kernel.
Feb  9 23:52:38 hector-HP kernel: [   17.476200] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  9 23:52:38 hector-HP kernel: [   17.476223] wl 0000:01:00.0: setting latency timer to 64
Feb  9 23:52:38 hector-HP kernel: [   17.527497] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb 10 00:06:37 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb 10 00:06:37 hector-HP kernel: [   17.263921] wl: module license 'MIXED/Proprietary' taints kernel.
Feb 10 00:06:37 hector-HP kernel: [   17.365152] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 10 00:06:37 hector-HP kernel: [   17.365174] wl 0000:01:00.0: setting latency timer to 64
Feb 10 00:06:37 hector-HP kernel: [   17.415725] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb 10 09:01:16 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb 10 09:01:16 hector-HP kernel: [   17.354322] wl: module license 'MIXED/Proprietary' taints kernel.
Feb 10 09:01:16 hector-HP kernel: [   17.464545] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 10 09:01:16 hector-HP kernel: [   17.464567] wl 0000:01:00.0: setting latency timer to 64
Feb 10 09:01:16 hector-HP kernel: [   17.519387] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb 10 09:02:43 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb 10 09:02:43 hector-HP kernel: [   17.247869] wl: module license 'MIXED/Proprietary' taints kernel.
Feb 10 09:02:43 hector-HP kernel: [   17.347515] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 10 09:02:43 hector-HP kernel: [   17.347538] wl 0000:01:00.0: setting latency timer to 64
Feb 10 09:02:43 hector-HP kernel: [   17.408518] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb 10 20:30:46 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb 10 20:30:46 hector-HP kernel: [   17.381609] wl: module license 'MIXED/Proprietary' taints kernel.
Feb 10 20:30:46 hector-HP kernel: [   17.491357] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 10 20:30:46 hector-HP kernel: [   17.491380] wl 0000:01:00.0: setting latency timer to 64
Feb 10 20:30:46 hector-HP kernel: [   17.538393] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb 10 20:31:48 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb 10 20:31:48 hector-HP kernel: [   17.471365] wl: module license 'MIXED/Proprietary' taints kernel.
Feb 10 20:31:48 hector-HP kernel: [   17.573994] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 10 20:31:48 hector-HP kernel: [   17.574017] wl 0000:01:00.0: setting latency timer to 64
Feb 10 20:31:48 hector-HP kernel: [   17.623784] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb 10 21:03:36 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb 10 21:03:36 hector-HP kernel: [   17.471415] wl: module license 'MIXED/Proprietary' taints kernel.
Feb 10 21:03:36 hector-HP kernel: [   17.576227] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 10 21:03:36 hector-HP kernel: [   17.576251] wl 0000:01:00.0: setting latency timer to 64
Feb 10 21:03:36 hector-HP kernel: [   17.622553] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb 10 23:35:47 hector-HP kernel: [    0.000000] DMI: Hewlett-Packard HP Mini 110-3500                /1584, BIOS F.14 11/30/2010
Feb 10 23:35:47 hector-HP kernel: [   17.345794] wl: module license 'MIXED/Proprietary' taints kernel.
Feb 10 23:35:47 hector-HP kernel: [   17.450812] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 10 23:35:47 hector-HP kernel: [   17.450836] wl 0000:01:00.0: setting latency timer to 64
Feb 10 23:35:47 hector-HP kernel: [   17.528762] INFO @wl_cfg80211_attach : Registered CFG80211 phy
```

```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:xxx.xxx.x.xxx  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: xxxx::xxxx:xxxx:xxxx:xxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:1 dropped:0 overruns:0 frame:4764
          TX packets:354 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1906 (1.9 KB)  TX bytes:35810 (35.8 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:xxx.x.x.x  Mask:255.0.0.0
          inet6 addr: ::x/xxx Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:548 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39132 (39.1 KB)  TX bytes:39132 (39.1 KB)
```

```
lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"xxxxxxx"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.
```

Hope this will provide enough data to track the problem.

Thanks again for your kind efforts.

---

### Post by Hadaka on 2013-02-10
Hi, please post

```
cat /etc/modules
lsmod | egrep 'b43|ssb|wl|brcm|bcma'
grep blacklist /etc/modprobe.d/blacklist.conf 
```
thanks.

---

### Post by DuckHook on 2013-02-10
Let me explain some of the output: *wl* is loading at boot and creating a network object (eth1) and a wireless object (eth1) although the wireless object is inactive. I'm scratching my head because the wireless object should be recognized as wlan0. @Hadaka is now asking for a list of all modules loaded at boot, ascertaining if any conflicting modules reside in memory and seeing what modules (if any) are blacklisted so as not to ever load. This will be very useful info.

---

### Post by Tacuabe on 2013-02-11
Here's the required output, taken from a NON working connection.

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wl
```

```
wl                   2906597  0 
cfg80211              178877  1 wl
lib80211               14040  2 lib80211_crypt_tkip,wl
```

```
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
```

I also did the same for a working connection. There were no differences.

---

### Post by Hadaka on 2013-02-11
Hi, the eth1 output is interesting, it "may" be part of the problem
please post
```
grep wlan0 /etc/udev/rules.d/70-persistent-net.rules
```
and
```
grep eth1 /etc/udev/rules.d/70-persistent-net.rules 
```

---

### Post by bkratz on 2013-02-11
> **Hadaka said:**
> Hi, the eth1 output is interesting, it "may" be part of the problem
please post
```
grep wlan0 /etc/udev/rules.d/70-persistent-net.rules
```and
```
grep eth1 /etc/udev/rules.d/70-persistent-net.rules 
```


@Hakaka,

The STA driver often makes an eth1 with the wired called eth0,  the b43 driver makes a Wlanx.

---

### Post by Hadaka on 2013-02-11
Thanks, I wasn;t aware of that. the only other suggestion i have is to
try this post. different machine, but same brcm 4313 and [14e4:4727]

[http://ubuntuforums.org/showthread.php?t=2111181](http://ubuntuforums.org/showthread.php?t=2111181)

post #4..as suggested copy and paste the commands.

sure glad i have the simple b43 driver...

---

### Post by bkratz on 2013-02-11
> **Hadaka said:**
> Thanks, I wasn;t aware of that. the only other suggestion i have is to
try this post. different machine, but same brcm 4313 and [14e4:4727]

[http://ubuntuforums.org/showthread.php?t=2111181](http://ubuntuforums.org/showthread.php?t=2111181)

post #4..as suggested copy and paste the commands.

sure glad i have the simple b43 driver...




@hadaka

From his original statement " Thanks a lot for your help DuckHook. I use HP g6-1201TX and faced  problems similar to Tacuabe, however my wifi started working immediately  after removing/purging bcmwl-kernel-source (step 5) and reinstalling it  caused the problem to occur again."   I am not sure why he is changing the drivers. If he is using 12.10 the kernel contains  brcmsmac which often works with the BCM4313.

If he trys post four commands make sure he changes the "precise" backports statement to whatever version he is using.  i think I would just purge the driver again and try

sudo modprobe -v brcmsmac


and see if it works.  just a suggestion though.

Will see how it is going later.

---

### Post by Tacuabe on 2013-02-11
Hi Hadaka!

Here are the outputs you requested. I took them with a WORKING connection. If you need them with a NON WORKING connection, then I'll have to shut down and wait until the connection goes down.

```
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="cc:52:af:13:4b:a3", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

```
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="cc:52:af:13:4b:a3", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

```

I'm answering posts step by step, otherwise I'm afraid things may get out of control. Will tackle the other suggestions in due time.

---

### Post by Hadaka on 2013-02-11
Hi, ok so you have eth1 and wlan0 both with the same mac address
in dev rules. so..try this..copy the dev rules
```
sudo cp /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.rules.old  
```
then..```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules 
```
and delete the wlan0 entry.
save,close,boot and see what happens.
*please verify you have copied the file before any deletion.

---

### Post by Tacuabe on 2013-02-11
Hi Hadaka!

Followed your steps to the letter. It worked first time, but after shutting down and waiting about an hour, the problem reappeared without change. Sorry!

---

### Post by Hadaka on 2013-02-11
Hi, the wlan0 most likely got created when you loaded the b43 is my guess,
anyway give post #4 a try, if it doesnt work out, its easy enough to reload
what you currently have.
[http://ubuntuforums.org/showthread.php?t=2111181](http://ubuntuforums.org/showthread.php?t=2111181)
thanks.

---

### Post by chili555 on 2013-02-11
First of all eth1 is the proper wireless interface for the Broadcom STA driver. There is no need to fix what isn't broken. 

Second, this looks like an awesome, working interface to me:> eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:xxx.xxx.x.xxx  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: xxxx::xxxx:xxxx:xxxx:xxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:1 dropped:0 overruns:0 frame:4764
          TX packets:354 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1906 (1.9 KB)  TX bytes:35810 (35.8 KB)
          Interrupt:16 You have a proper interface, it has an IP address and it's sending and receiving packets, at least to the router. So what about this is not working? Can you ping the router?```
ping -c3 192.168.1.1
```Google's DNS nameserver?```
ping -c3 8.8.8.8
```Google itself?```
ping -c3 www.google.com
```When you left the computer over-night, did it suspend? Is this perhaps actually a 'wireless won't come back from suspend' problem?

---

### Post by DuckHook on 2013-02-11
Please beware that we are now getting into highly conjectural territory, so suggestions are very dicey and can get you into trouble as much as getting you out. Basically, we are guessing at what the problem is, and floating solutions rather than the slower but safer diagnose/process-of-elimination method.

That said, there are some broadcom chips that don't handle power management very well. The various 'buntus all try to power manager the WIFI chip so that laptops don't waste limited battery power broadcasting when network is actually quiet. This trips up some broadcom chips. We don't really know if this is the problem in your case. It is possible, but it's just an educated guess. If you want to try turning off power management, follow *@Wild Man's* steps in [this]("http://ubuntuforums.org/showthread.php?t=1943701") thread. If this solves your problem then you will just have to be aware that your battery will drain faster because your WIFI will be "on" all the time. If it does *not* solve your problem then reverse the steps to bring power management back on.

---

### Post by ere109 on 2013-02-12
I've also got a 4313 card that stopped working after recent updates.  Several people have reported similar problems, so let's just keep searching and sharing.

---

### Post by ere109 on 2013-02-12
I was able to get wifi back tonight by completely removing all traces of the STA drivers, removing some blacklists, and doing a restart.  There's a lot of extra information here, but post #5 is how I ended up working it out (about 10 steps more than you actually need - focus on removing and purging all bcmwl drivers, files, sources, and then making sure brcmsmac isn't blacklisted anywhere in /etc/modprobe.d directory.

[http://ubuntuforums.org/showthread.php?p=12505627#post12505627](http://ubuntuforums.org/showthread.php?p=12505627#post12505627)

---

### Post by Tacuabe on 2013-02-12
Happy to report SUCCESS! 

As Hadaka suggested, I applied the instructions of Post #4 and that did the trick. To boot, my HP D110 PhotoSmart wireless printer was revived and works flawlessly.

Many thanks to DuckHook and others who were kind enough to lend a much needed hand.

Cheers!

Tacuabe

---

### Post by Tacuabe on 2013-02-12
I'd like to mark this as Solved. How do you do that?

---

### Post by bkratz on 2013-02-12
> **Tacuabe said:**
> I'd like to mark this as Solved. How do you do that?




If you go to the thread tools at the top of the page, there is a selection for mark as solved.

---

### Post by Hadaka on 2013-02-12
Hi, awesome, glad that worked for you,hopefully others with the 4713 [14e4:4727]
having like problems will find this thread.

---

