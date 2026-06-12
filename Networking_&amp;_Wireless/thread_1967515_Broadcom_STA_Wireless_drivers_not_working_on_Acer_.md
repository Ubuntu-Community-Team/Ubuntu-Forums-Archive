---
title: "Broadcom STA Wireless drivers not working on Acer aspire 5750G, Ubuntu 12.04"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by sidewayssammich on 2012-04-28
Hi, I'm new to linux, I've only been using it for a short period of time. I just upgraded to Ubuntu 12.04, and stupidly didn't check if everything would work before upgrading. I am now stuck without working wifi. I'm not positive what my wireless card is, but the Broadcom STA wireless drivers seemed to work without any problems. My laptop is an acer aspire 5750G, running Ubuntu 12.04. When I go into the additional drivers section of system settings, the drivers show up, but when i click activate, it comes up with this error: 

"Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

I have no clue what this means. Help me Ubuntu forums, you're my only hope!

---

### Post by chili555 on 2012-04-28
A known issue is that jockey; also known as Additional Drivers, suggests the wrong driver for a few Broadcom cards. Let's find out what you have and solve it. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by sidewayssammich on 2012-04-28
here's what i got

> 03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]

is that any help?

---

### Post by chili555 on 2012-04-28
> Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [[COLOR="Red"]14e4:4358[/COLOR]] Perfect!

With a temporary ethernet connection, please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```After it's done, do:```
sudo modprobe wl
```If there is no error or warning, your wireless should be working.

---

### Post by sidewayssammich on 2012-04-28
here's what i got

code:
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
is that any help?
sorry, repost. i'm a noob and don't know where to go to delete posts

---

### Post by sidewayssammich on 2012-04-28
thank you so much! wifi is now up and running!

---

### Post by chili555 on 2012-04-28
> **sidewayssammich said:**
> thank you so much! wifi is now up and running!Awesome! Glad it's working. So that the searchers with a similar problem will find the solution, please use thread tools at the top to Mark Solved.

Note to searchers: If your pci.id is *not* 14e4:4358, then this may not work for you. Start a new thread or search for your specific pci.id.

---

### Post by snookpup on 2012-04-29
Thank You chili555, I have a Samsung Core i5 portable pc, and I recently upgraded to 12.04 from 11.10, and had this exact same problem.  This pc also had a similar situation with/Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n.  U opened up a terminal and used your fix as well, and BINGO, it worked.  Thanks!  :)

---

### Post by chili555 on 2012-04-29
Glad it's working.

**Note to searchers**: If your pci.id is *not* 14e4:4358, then this may not work for you. Start a new thread or search for your specific pci.id.

---

### Post by hamiltonjlc on 2012-04-30
Used this fix for pci.id [14e4:4727] and it worked flawlessly.

---

### Post by DodgeX on 2012-05-01
Worked fine for me in Lenovo G560 with Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01):guitar:

---

### Post by WVPARN on 2012-05-01
I'm having a fair amount of difficulty even with the above tips. I, too, have [14e4:4727]. 

I performed the steps including the modprobe that returned no errors, but I get the following symptoms.

The wireless detects the network, but seems to get stuck on the password step.
The wireless can at times connect, but then the computer won't shut down properly.
The most frequent behavior is that the computer hangs when trying to shake hands with the router. Again, I can see that the computer can see the wireless network and I know it has the password embedded already. The computer hangs and needs a cold shut-off with the power button.

I also tried going into settings, drivers, and removing the Broadcom wireless driver, and then performing the above-mentioned steps again (reinstall etc.)

This pertains to an Aspire One 722.

On my 1001PXD, no problems at all with 11 or 12 Ubuntu, wireless or otherwise.

---

### Post by chili555 on 2012-05-01
Please try:```
sudo modprobe -r wl
sudo modprobe -r bcma
sudo modprobe brcmsmac
```How does it work now? If it improves, we'll tweak a couple of files and make it persistent.> I, too, have [14e4:4727]. Did you see above where I said:> Note to searchers: If your pci.id is not 14e4:[COLOR="Red"]4358[/COLOR], then this may not work for you. Start a new thread or search for your specific pci.id. I guess the gremlin bit your nose!

---

### Post by WVPARN on 2012-05-01
:) Someone mentioned 4727, so I thought I'd mention my trouble there.

I did the steps you suggested just above, and immediately it found the network even though I had the ethernet in, so I thought I'd tempt fate (or gremlins) and try for a shutdown, but it has hanged again. Three red dots, two white, no-go.

Now I'm rebooting after a cold power-off. As an experiment, I have the ethernet unplugged. Let's see what it does.

The triangle is blank, it's not searching out the wireless. I click the triangle, and go to edit connections. Under wireless, I see my wireless network named there. I try the function-wireless-on-off button, no change.

Now I delete the wireless network from the AO722. (I'm using the PXD for this post.) Now under system settings and drivers, I see that the Broadcom STA wireless driver is not activated.

sudo modprobe wl = no answer. So there seems to be a driver working, correct?

Now I do these three again:
sudo modprobe -r wl
sudo modprobe -r bcma
sudo modprobe brcmsmac

No evident response. Under settings and network, I see that it considers that there is no wireless network available. The wireless has a hardware address, but it says that wireless is unavailable.

The AO722 is able to shutdown and reboot normally at this time.

---

### Post by chili555 on 2012-05-01
As soon as you reboot, the changes I suggested go away. We are trying to find a working driver and suspect a driver conflict, so I don't understand why, after you removed wl here:> sudo modprobe [COLOR="Red"]-r[/COLOR] wl...then the first thing you do is load it up again:> sudo modprobe wl = no answer.Please do the following and no more:```
sudo su
echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
echo brcmsmac >> /etc/modules
exit
```Detach the ethernet cable and reboot without ethernet. When the computer comes up, run:```
lsmod | grep -e wl -e bcma -e brcmsmac
```We hope that all we see is brcmsmac. If you see anything else, report it here.

I suspect this hanging behavior is symptomatic of a bigger problem. Many posters here have missing or conflicting drivers and no hangs; their wireless simply doesn't work.

---

### Post by WVPARN on 2012-05-01
Thanks for your help! Let's see, I did the steps involving echo, and removed the ethernet cable, rebooted. At the moment there is no apparent connection, and no attempt to find one. 

the lsmod command yields five lines of output.

```
brcmsmac  540875  0
mac80211  436455  1  brcmsmac
brcmutil  14675  1  brcmsmac
cfg80211  178679  2  brcmsmac,mac80211
crc8  12781  1  brcmsmac
cordic  12487  1  brcmsmac
```

---

### Post by chili555 on 2012-05-01
Excellent so far. Let's see:```
dmesg | grep -e brcm -e wlan
iwconfig
rfkill list all
```Thanks.

---

### Post by WVPARN on 2012-05-01
I had shut the computer off. I'll leave it on now, for the rest of our experiments. Sorry.

I just turned it on, without the ethernet cable. The desktop showed a balloon saying, "Wireless Networks Available", and now the computer is hanging. No mouse movement, tab and enter do nothing. Cold shut-off, and I'll reboot with ethernet.

Rebooted, everything normal. Open terminal. I'll go back a few steps.

sudo su
echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
echo brcmsmac >> /etc/modules
exit

Then

lsmod | grep -e wl -e bcma -e brcmsmac

gives the identical readout from before. At this juncture, "System settings" "additional drivers" shows that the Broadcom STA wireless driver is not activated. "System settings" "network" shows "Wireless" "disconnected" and a hardware address. Airplane mode is off, Wireless is on. Under the drop-down menu I see the computer has detected two wireless networks that I recognize.

Here is the next readout.

```

dmesg | grep -e brcm -e wlan
[   13.266731] brcmsmac 0000:07:00.0: bus 7 slot 0 func 0 irq 11
[   13.266830] brcmsmac 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.266845] brcmsmac 0000:07:00.0: setting latency timer to 64
[   14.880146] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   14.880216] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   14.881291] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   14.881921] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.882963] ADDRCONF(NETDEV_UP): wlan0: link is not ready



iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.



rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

I'll leave the computer on now. Ethernet is plugged in for this whole experiment. Thank you very much. :KS

---

### Post by chili555 on 2012-05-01
> sudo su
echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
echo brcmsmac >> /etc/modules
exitThese steps needn't be done more than once. Once it's done, it's done. Those are permanent modifications to a system file.> "additional drivers" shows that the Broadcom STA wireless driver is not activated. I believe we've already established that the STA driver doesn't effectively drive your wireless card.

As I said, I think your freeze is unrelated to wireless. You might look in the system logs for errors or warnings:```
sudo cat /var/log/syslog | grep -i error
sudo cat /var/log/syslog | grep -i warn
```You can Google the message and get some clues as to its origin.

---

### Post by WVPARN on 2012-05-01
The grep -i error gives many entries stating

real_update_permament_hw_address(): (eth1): unable to read permanent MAC address (error 0)

Later there are some that state

error adding interface: wpa_supplicant couldn't grab this interface

relating to NetworkManager.

The grep -i warn gives entries from NetworkManager. About 2/3 of these are "failed to allocate link cache". Some say "Trying to remove a non-existant call id." There are a couple from dnsmasq stating "warning: no upstream servers configured"

---

### Post by WVPARN on 2012-05-01
By the way, it never hangs when the ethernet cord is plugged in. So I think the hanging seems related exclusively to the wireless. And it seems especially connected with actually handshaking with the router. But anyway, something to do with the wireless adapter, or driver... :)

---

### Post by WVPARN on 2012-05-02
I don't want you to waste time on my case if not necessary, so I'll mention that I tried the Mint distro, and it works fine, it finds the wireless, connects to it, shuts down and starts back up again normally. I'm not sure which Mint but it would be the latest I suppose, since I used Unetbootin to find it, and I have the sense that Unetbootin tries to stay up to date about versions.

I don't actually like the AO722, it is someone else's. I prefer the PXD, where I'm still using Ubuntu.

Thanks for your help. :KS

---

### Post by chili555 on 2012-05-02
Yikes! Those are some scary errors. You might check:```
cat /etc/NetworkManager/NetworkManager.conf 
```Does it exist? Is there a line managed=false in there? Also check:```
cat /etc/network/interfaces
```Hopefully, there are only lines in there related to lo or loopback. If there are others, they need to be removed so that the end result is:> auto lo
iface lo inet loopbackYou might also reinstall Network Manager:```
sudo apt-get install --reinstall network-manager
```Are all these connection attempts *without* the ethernet attached? Network Manager will not activate wireless if wired is available.

---

### Post by WVPARN on 2012-05-02
In the Mint Julia forum, there is a discussion about this problem.

[http://forums.linuxmint.com/viewtopic.php?f=53&t=82747&p=529851&hilit=AO722#p529851](http://forums.linuxmint.com/viewtopic.php?f=53&t=82747&p=529851&hilit=AO722#p529851)

> The AO522 and AO722 have been known to  behave terribly (freezing) in Ubuntu due to an interaction between the  wireless card and the wired network driver.  The solution there has been  to enter BIOS (F2 @ boot) and make the Network Boot option the first  priority among boot devices.  This might help with running Mint 11 or  12.  Reference: [https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)

Apparently they will upgrade Mint soon with the newer Ubuntu, so my problem may recur. Anyway I thought this would be a helpful lead for anyone with an Aspire.

---

### Post by WVPARN on 2012-05-02
I thought it might be helpful to mention that when I ran Mint 12 from a USB, I got the same problems. After the wireless spends a few seconds trying to connect, the computer stops being usable.

Mint 10 works fine. Mint 12 has the same problem on the AO722. Isn't Mint based on Ubuntu to some extent? So I thought it might be a helpful observation.

---

### Post by chili555 on 2012-05-02
Reading the link above makes me wonder if things might improve if you made the BIOS change mentioned and blacklisted the ethernet driver. Do you use wireless exclusively?

---

### Post by WVPARN on 2012-05-03
It seems to be solved in my case.


The topic is getting the wireless to work on an AO722, an Acer Aspire One 722. The wireless card is a Broadcom. I use Ubuntu on all my other computers, but found problems in this case. I tried Mint Julia, or Mint 10, but I set Mint aside, because I didn't like it as well, and it didn't solve the problem.

Previously I did a bunch of things to try to get wireless to work on the Acer running Ubuntu 12, but now I'm trying to start from scratch, fresh install.

Fresh install begins:

download updates while installing
install this third-party software
erase disk, use whole disk
noticed a brief message about something not being ready, or mounted, swap or something.
boot with ethernet plugged in
notice the 'restricted drivers available' icon and balloon in top left area
I do not yet check for updated software, in case doing so causes problems
unplug ethernet, tap connection triangle, choose my wireless network
it asks for passphrase, I enter it
wireless connects

After the above, various diagnostic command output, including:

lspci command.
lsmod command.
dmesg command.
cat commands to syslog.
cat to NetworkManager.conf.

```

lspci -nn | grep 0280
07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)


lsmod | grep -e wl -e bcma -e brcmsmac
wl                   2646601  0 
lib80211               14040  1 wl
bcma                   25651  0 
brcmsmac              540875  0 
mac80211              436455  1 brcmsmac
brcmutil               14675  1 brcmsmac
cfg80211              178679  2 brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12487  1 brcmsmac



dmesg | grep -e brcm -e wlan
[   14.887388] brcmsmac 0000:07:00.0: bus 7 slot 0 func 0 irq 11
[   14.887516] brcmsmac 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.887530] brcmsmac 0000:07:00.0: setting latency timer to 64
[   25.026114] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   25.026130] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   25.027779] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   25.028669] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.030023] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  243.810470] wlan0: authenticate with 00:13:46:cf:85:e8 (try 1)
[  243.816076] wlan0: authenticated
[  243.822941] wlan0: associate with 00:13:46:cf:85:e8 (try 1)
[  243.826124] wlan0: RX AssocResp from 00:13:46:cf:85:e8 (capab=0x431 status=0 aid=3)
[  243.826136] wlan0: associated
[  243.827400] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  243.827414] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  243.827434] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  243.827967] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  245.954629] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[  256.160307] wlan0: no IPv6 routers present




cat /var/log/syslog | grep -i error
May  3 03:44:16 aopup-AO722 kernel: [   13.651499] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
May  3 03:47:59 aopup-AO722 NetworkManager[998]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed




cat /var/log/syslog | grep -i warn
May  3 03:44:21 aopup-AO722 NetworkManager[998]: <warn> failed to allocate link cache: (-10) Operation not supported
May  3 03:44:22 aopup-AO722 NetworkManager[998]: <warn> Trying to remove a non-existant call id.
May  3 03:45:47 aopup-AO722 kernel: [  110.318091] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
May  3 03:47:42 aopup-AO722 dnsmasq[2510]: warning: no upstream servers configured

```I have made no changes to BIOS. 
I would like to use both ethernet and wireless, due to unpredictability of circumstances.

At this point, ethernet unplugged, wireless connected, I tell the computer to shutdown. It shuts down normally. On previous experiments it would hang while shutting down with wireless connected.

I will now turn it on, ethernet cable unplugged. Recall that at this point I have not sought any restricted drivers or new software. Everything boots, no freezing, it has found the wireless connection and connected. I see it wants me to download some packages. I will reboot first. It shuts down normally, starts normally, connects to the wireless. Now I try a Fn-Zz experiment. Press power button then, and everything seems normal.

Okay, is it time to fetch some packages? By the way that message I can never quite read on bootup is approximately "the disk drive for cryptswap is not ready yet".

Click on updates manager. There are 47. I click "install updates". Update manager asks me to restart. I click the restart button. Shuts down normally, starts normally, finds the network, no freezing.

Until further notice, I guess that's it. Solved! Unless you have comments. Thank you very kindly for your help. I guess my impression is that not getting the restricted drivers made the difference. Dare I peek in the restricted drivers settings area?? Might tempt fate to do that.

---

### Post by chili555 on 2012-05-03
> Dare I peek in the restricted drivers settings area??NO! For Broadcom cards, it is broken. Whatever it suggests is wrong.> lsmod | grep -e wl -e bcma -e brcmsmac
wl                   2646601  0 
lib80211               14040  1 wl
bcma                   25651  0 
brcmsmac              540875  0 
mac80211              436455  1 brcmsmac
brcmutil               14675  1 brcmsmac
cfg80211              178679  2 brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12487  1 brcmsmacYou have every driver there is for your device and they will, no doubt inhibit performance. I'd blacklist bcma and wl. You can check that your device works first by temporarily unloading them:```
sudo modprobe -r wl
sudo modprobe -r bcma
```If it works well, connects, pulls web pages, is fast enough, etc., then I'd proceed with the blacklist.

I'm glad it's solved, by whatever means.

---

### Post by WVPARN on 2012-05-03
When I did the first, the connection ended.

```
sudo modprobe -r wl 
sudo modprobe -r bcma
```

When I did the second, there seemed to be no ill effect. Does this imply a benefit to blacklisting the second?

---

### Post by chili555 on 2012-05-03
It implies that wl is the correct driver for your device; a wholly unexpected result! Please try this:```
sudo modprobe wl
sudo modprobe -r bcma
sudo modprobe -r brcmsmac
```Now do you have a stable connection? If so, we'll blacklist bcma and brcmsmac and leave wl to run the show.

I learn something new about 14e4:4727 just about hourly!

---

### Post by WVPARN on 2012-05-04
I'll try it. But a question. If I have rebooted, wouldn't wl already be loaded? Wouldn't it be better to do just
```

sudo modprobe -r bcma
sudo modprobe -r brcmsmac
```

Also if I make a mistake, how do I unblacklist something?

---

### Post by b1gag3 on 2012-05-04
If you used 
```
sudo modprobe -r bcma
```to blacklist something, you can simply reboot ubuntu or do
```
sudo modprobe bcma
```If you blacklisted it by a file, take a look in the directory "/etc/modprobe.d/" and delete the file you're looking for and reboot or use the command above.

---

### Post by chili555 on 2012-05-04
> Wouldn't it be better to do just
Code:

sudo modprobe -r bcma
sudo modprobe -r brcmsmac

Is that really what you want to do every morning when you turn on your computer? *Every* day?? Wouldn't you rather turn on your computer and have it start and run perfectly without human intervention?

Blacklisting involves using a text editor such as gedit to add a few words to a text file.```
blacklist bcma
blacklist brcmsmac
``` If it doesn't work, we edit the file again and correct the mistake. We can also add a comment to the file:```
#added 5-4-2012: see forum posts. is wl the best driver for my wireless?
```Comments are preceded with #; the system ignores anything following # in /etc files.

One of the wonderful things about Linux is that users can easily make changes to suit their needs or even preferences.

---

### Post by WVPARN on 2012-05-04
Okay, thanks for your help again. I did

```
sudo modprobe -r bcma
sudo modprobe -r brcmsmac
```

The connection continues to be great. But when I tried

```
sudo echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
```

it said, permission denied.

---

### Post by WVPARN on 2012-05-05
Sorry, I just remembered to use "sudo su" first. Now it's done.

Many thanks!

---

### Post by gabor111 on 2012-05-05
> **chili555 said:**
> Yikes! Those are some scary errors. You might check:```
cat /etc/NetworkManager/NetworkManager.conf 
```Does it exist? Is there a line managed=false in there? Also check:```
cat /etc/network/interfaces
```Hopefully, there are only lines in there related to lo or loopback. If there are others, they need to be removed so that the end result is:You might also reinstall Network Manager:```
sudo apt-get install --reinstall network-manager
```Are all these connection attempts *without* the ethernet attached? Network Manager will not activate wireless if wired is available.

I had the same problem with Dell Inspirion N7010 with BCM4313.
After a fresh install of 12.04, my wireless worked fine, but after installing the automated updates, splash frized... ](*,)
After solved the freezing, there was no way to start wireless. In the network settings, wireless still always off. :-k
I tried many propositions from many posts without succes, :-k but the reinstall of Network Manager solved my problem; wireless is working fine now. [-o<
Thank you

---

### Post by WVPARN on 2012-05-05
It's back. I rebooted this morning, and the current behavior is:

Without ethernet plugged in, the wireless freezes the computer after a minute of trying.
With ethernet plugged in, the wireless locates the wireless network, while the computer also uses the wire. If I unplug the ethernet, the wireless works briefly before freezing.

I un-blacklisted bcma and brcmsmac from that /etc file. Rebooted, still having the problem.

```
wl                   2646601  0 
lib80211               14040  2 lib80211_crypt_tkip,wl



0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no



lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:193  Noise level:160
          Rx invalid nwid:0  invalid crypt:1  invalid misc:0

eth0      no wireless extensions.


May  5 05:17:44 aopup-AO722 postfix/smtp[15694]: BFBD841D7A: to=<creimann@radix.net>, relay=none, delay=21327, delays=21326/0.23/0.01/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=radix.net type=MX: Host not found, try again)
May  5 06:07:55 aopup-AO722 kernel: [21638.716226] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
May  5 12:48:49 aopup-AO722 kernel: [   18.775583] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
May  5 12:48:50 aopup-AO722 NetworkManager[648]: <error> [1336236530.24395] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
May  5 12:48:54 aopup-AO722 postfix/smtp[1330]: BFBD841D7A: to=<creimann@radix.net>, relay=none, delay=48397, delays=48396/0.65/0/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=radix.net type=MX: Host not found, try again)
May  5 12:50:53 aopup-AO722 kernel: [   20.881760] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
May  5 12:50:53 aopup-AO722 NetworkManager[614]: <error> [1336236653.759071] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
May  5 12:54:25 aopup-AO722 kernel: [   22.161930] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
May  5 12:54:26 aopup-AO722 NetworkManager[629]: <error> [1336236866.83531] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
May  5 12:56:21 aopup-AO722 kernel: [   20.580730] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
May  5 12:56:26 aopup-AO722 NetworkManager[606]: <error> [1336236986.23510] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
May  5 13:02:45 aopup-AO722 kernel: [   21.514291] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
May  5 13:02:46 aopup-AO722 NetworkManager[615]: <error> [1336237366.621172] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
May  5 13:04:47 aopup-AO722 kernel: [   20.278906] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
May  5 13:04:52 aopup-AO722 NetworkManager[615]: <error> [1336237492.264877] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
May  5 05:17:43 aopup-AO722 dnsmasq[15569]: warning: no upstream servers configured

May  5 06:07:59 aopup-AO722 NetworkManager[942]: <warn> Trying to remove a non-existant call id.
May  5 12:48:49 aopup-AO722 NetworkManager[648]: <warn> failed to allocate link cache: (-10) Operation not supported
May  5 12:48:50 aopup-AO722 NetworkManager[648]: <warn> failed to allocate link cache: (-10) Operation not supported
May  5 12:48:50 aopup-AO722 NetworkManager[648]: <warn> Trying to remove a non-existant call id.
May  5 12:50:53 aopup-AO722 NetworkManager[614]: <warn> failed to allocate link cache: (-10) Operation not supported
May  5 12:50:53 aopup-AO722 NetworkManager[614]: <warn> failed to allocate link cache: (-10) Operation not supported
May  5 12:50:54 aopup-AO722 NetworkManager[614]: <warn> Trying to remove a non-existant call id.
May  5 12:54:25 aopup-AO722 NetworkManager[629]: <warn> failed to allocate link cache: (-10) Operation not supported
May  5 12:54:26 aopup-AO722 NetworkManager[629]: <warn> failed to allocate link cache: (-10) Operation not supported
May  5 12:54:26 aopup-AO722 NetworkManager[629]: <warn> Trying to remove a non-existant call id.
May  5 12:56:22 aopup-AO722 NetworkManager[606]: <warn> failed to allocate link cache: (-10) Operation not supported
May  5 12:56:25 aopup-AO722 NetworkManager[606]: <warn> failed to allocate link cache: (-10) Operation not supported
May  5 12:56:26 aopup-AO722 NetworkManager[606]: <warn> Trying to remove a non-existant call id.
May  5 13:02:46 aopup-AO722 NetworkManager[615]: <warn> failed to allocate link cache: (-10) Operation not supported
May  5 13:02:46 aopup-AO722 NetworkManager[615]: <warn> failed to allocate link cache: (-10) Operation not supported
May  5 13:02:46 aopup-AO722 NetworkManager[615]: <warn> Trying to remove a non-existant call id.
May  5 13:04:47 aopup-AO722 NetworkManager[615]: <warn> failed to allocate link cache: (-10) Operation not supported
May  5 13:04:52 aopup-AO722 NetworkManager[615]: <warn> failed to allocate link cache: (-10) Operation not supported
May  5 13:04:52 aopup-AO722 NetworkManager[615]: <warn> Trying to remove a non-existant call id.

```

---

### Post by chili555 on 2012-05-05
> I un-blacklisted bcma and brcmsmac from that /etc file. Rebooted, still having the problem.I'm not even sure how to respond. Haven't we established previously that these are incorrect for your device? Why did you *un*-blacklist them? Is it surprising that Network Manager throws out errors when it's trying to juggle three drivers; two of which are incorrect?

I really can't hit an ever-changing, ever-moving target.

---

### Post by WVPARN on 2012-05-05
I meant, after noticing a return of the main problem, I unblacklisted those two, to see if they might do something useful after all. But I can re-blacklist them.

Which I have now done.

---

### Post by WVPARN on 2012-05-05
Just now I did a reinstall of network-manager, and the behavior remained unchanged. For example, the computer froze when rebooting without the ethernet cable.

So I think we are right where we left off. We've ruled out a problematic upgrade, because I did a full install of 12.04. It's neither bcma nor brcmsmac because they are blacklisted (I put them back only after noticing the problem again, and then I re-blacklisted them, which they are now). I haven't sought out any restricted drivers. I haven't even opened that section of system settings, in case just looking there would make it retrieve something.

One funny thing happened last night. I let the computer play a stream as I went to sleep. I set the power option to suspend after ten minutes. When I got up in the morning, the computer was in a state to reboot, not to wake up from suspend. That was unexpected. So I don't know what it did when I wasn't looking.

The other point I can think of is that Mint 10 / Ubuntu 10 seem to be able to drive the wireless. I used Mint 10 for a day or so but tired of its bad rendering of the monitor, plus the fact that it will be phased out made it seem a bad bet.

Do you want me to run a diagnostic command?

---

### Post by johnnyzee on 2012-05-05
Thanks CHILI555 I had the same problem with a Dell 630 after upgrade from v.11 to 12.04 and your suggestion worked for my machine as well.

---

### Post by chili555 on 2012-05-05
> **johnnyzee said:**
> Thanks CHILI555 I had the same problem with a Dell 630 after upgrade from v.11 to 12.04 and your suggestion worked for my machine as well.Glad it helped and I'm glad it's working.

---

### Post by WVPARN on 2012-05-06
Thanks anyway for your help, and I apologize for offending you. I'm not familiar enough with this kind of thing to know whether or not step XYZ is worthwhile, or irrelevant, or what.

I guess 14e4:4727 is still something of a mystery. This page ( [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) ) lists it as not supported, and suggests [http://linuxwireless.org/en/users/Drivers/brcm80211](http://linuxwireless.org/en/users/Drivers/brcm80211) as an alternative. But we've been ruling that one out in the case of my AO722.

---

### Post by chili555 on 2012-05-06
@WVPARN--

Please see Private Messages at the top.

---

### Post by gabor111 on 2012-05-07
My problem is not solved too.
After a reboot, the wireless is not working.

I had the 64-bit version of ubuntu, and I tried to make a fresh install with the 32 bit version.

The result was the same. The wifi worked fine untill I enabled a restricted driver for ATI video... After the reboot this blocked my wireless...

The only way to make working my wireless was to disable all restricted drivers, even the STA broadcom driver too.
After this my wireless is working stable.

I hope this informations will be helpfull.

---

### Post by chili555 on 2012-05-07
> **gabor111 said:**
> My problem is not solved too.
After a reboot, the wireless is not working.

I had the 64-bit version of ubuntu, and I tried to make a fresh install with the 32 bit version.

The result was the same. The wifi worked fine untill I enabled a restricted driver for ATI video... After the reboot this blocked my wireless...

The only way to make working my wireless was to disable all restricted drivers, even the STA broadcom driver too.
After this my wireless is working stable.

I hope this informations will be helpfull.When it *is* running correctly, please open a terminal and run and post:```
lsmod | grep -e wl -e b43 -e brcmsmac
lspci -nn | grep 0280
```Thanks.

---

### Post by gabor111 on 2012-05-07
> **chili555 said:**
> When it *is* running correctly, please open a terminal and run and post:```
lsmod | grep -e wl -e b43 -e brcmsmac
lspci -nn | grep 0280
```Thanks.

Please find it below:

```

....:~$ lsmod | grep -e wl -e b43 -e brcmsmac
brcmsmac              540875  0 
mac80211              436455  1 brcmsmac
brcmutil               14675  1 brcmsmac
cfg80211              178679  2 brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12487  1 brcmsmac
....:~$ lspci -nn | grep 0280
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

Please ask me if you need additional info for solving this issue.

---

### Post by chili555 on 2012-05-07
The more I read about your device 14e4:4727, the less I understand!!

Please try this:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo su
echo brcmsmac >> /etc/modules
exit
```Now does it work correctly?

---

### Post by cardiffman28 on 2012-05-07
Hi Chili555,

I tried your solution to speedwayssammich on page 1 (as at base here).  I have a Dell Inspirion 6400 running 12.04 on dual boot with Vista and have a Broadcom BCM4311 802.11bg wlan (rev 01).  The Broadcom driver is now activated in Sys Settings/Add Drivers HOWEVER in sys settings/Network the Wireless tab has now disappeared (!) so I only have wired showing in Network and the wifi light on my Dell is still out....help please!

With a temporary ethernet connection, please do: 	Code:
 	sudo apt-get install --reinstall bcmwl-kernel-source 
After it's done, do: 	Code:
 	sudo modprobe wl

---

### Post by chili555 on 2012-05-07
> **cardiffman28 said:**
> Hi Chili555,

I tried your solution to speedwayssammich on page 1 (as at base here).  I have a Dell Inspirion 6400 running 12.04 on dual boot with Vista and have a Broadcom BCM4311 802.11bg wlan (rev 01).  The Broadcom driver is now activated in Sys Settings/Add Drivers HOWEVER in sys settings/Network the Wireless tab has now disappeared (!) so I only have wired showing in Network and the wifi light on my Dell is still out....help please!

With a temporary ethernet connection, please do: 	Code:
 	sudo apt-get install --reinstall bcmwl-kernel-source 
After it's done, do: 	Code:
 	sudo modprobe wlLet's see:```
lspci -nn | grep 0280
```Thanks.

I don't know why you would expect the same fix to work; you have a different device.

---

### Post by cardiffman28 on 2012-05-07
> **chili555 said:**
> Let's see:```
lspci -nn | grep 0280
```Thanks.

I don't know why you would expect the same fix to work; you have a different device.
I am very new so thank you for your patience.  I entered the code you gave in your reply and got:

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Don't know if this helps?

Thanks again.

---

### Post by chili555 on 2012-05-07
Please hook up the ethernet and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```Detach the ethernet and tell us if it's working.

---

### Post by cardiffman28 on 2012-05-07
> **chili555 said:**
> Please hook up the ethernet and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```Detach the ethernet and tell us if it's working.
Just tried it and yup it works!  Thank you very much Chili555!  I'm so impressed with Ubuntu (and its support such as through your good self) after trying to run through the quick sand of Vista.

---

### Post by chili555 on 2012-05-07
Glad it's working and I appreciate your kind words. Welcome to the fun world of Ubuntu.

---

### Post by cardiffman28 on 2012-05-07
> **chili555 said:**
> Glad it's working and I appreciate your kind words. Welcome to the fun world of Ubuntu.
This is a very reluctant rejoinder but...I am losing wifi every time I shut down and start up again.  Your code works every time I try it (and thanks again for it!) but the effects of it seem to be lost every time on reboot (ie back to no wireless tab and no wifi light).  Is there any way of making it "stick" through a reboot please?  Thank you (and yes it's all lots of fun!)

---

### Post by chili555 on 2012-05-07
Sometimes, the b43 module fails to load on boot. Let's try to fix that:```
sudo su
echo b43 >> /etc/modules
exit
```Is it working now?

---

### Post by cardiffman28 on 2012-05-08
> **chili555 said:**
> Sometimes, the b43 module fails to load on boot. Let's try to fix that:```
sudo su
echo b43 >> /etc/modules
exit
```Is it working now?
It is indeed working now through a reboot.  Thank you very much once again Chili5555.  Nice working with you :-)

---

### Post by TheAscended on 2012-05-08
chili 555: "If your pci.id is *not* 14e4:4358, then this may not work for you."

My pci.id is 14e4:4358, I tried the solution you proposed, but i don't think it worked. what do you recommend?

---

### Post by chili555 on 2012-05-08
> but i don't think it worked.Let's see what happened. Please run and post:```
sudo modprobe wl
dmesg | grep wl
rfkill list all
iwconfig
```When you reply, please try to be more specific about what didn't work. Thanks.

---

### Post by bp1 on 2012-05-08
Hi,

I have effectively the same problem as the first post (upgraded to  12.04, can't activate broadcom driver) but I have no option to connect  to the internet using an ethernet cable. Can I download the file using  another machine and install it from a pen drive?

Thanks for any help you can offer

---

### Post by chili555 on 2012-05-08
> **bp1 said:**
> Hi,

I have effectively the same problem as the first post (upgraded to  12.04, can't activate broadcom driver) but I have no option to connect  to the internet using an ethernet cable. Can I download the file using  another machine and install it from a pen drive?

Thanks for any help you can offerMy response is the same in *every* case. Before we install the wrong driver and chase an error for 153 posts, let's be sure what you have. Please post:```
lspci -nn | grep 0280
```

---

### Post by bp1 on 2012-05-08
Thank you. I get:

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY
 [14e4:4315] (rev 01)

And rather than an Acer aspire as with the first poster, it's a Dell Inspiron 1545.

---

### Post by bp1 on 2012-05-08
[I just wanted to delete this extra post to avoid clutter, but couldn't. I moved what I said into the previous post]

---

### Post by chili555 on 2012-05-08
> **bp1 said:**
> Thank you. I get:

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY
 [14e4:4315] (rev 01)

And rather than an Acer aspire as with the first poster, it's a Dell Inspiron 1545.You need the Broadcom STA driver, also known as bcmwl-kernel source. This describes how to get it without internet access. Scroll down to here: **STA - No Internet access**. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Feel free to post back if you get stuck.

---

### Post by bp1 on 2012-05-08
Thank you. I found the instructions a bit confusing, so repeat what I did here in case it's useful to anyone else who doesn't have an ethernet connection. First, I went into the Ubuntu Software Centre and searched for bcmwl-kernel-source. It was already installed. I "removed" it.

Then, on another machine (with a network connection) I went to:

[http://www.ubuntuupdates.org/package/core/precise/restricted/updates/bcmwl-kernel-source](http://www.ubuntuupdates.org/package/core/precise/restricted/updates/bcmwl-kernel-source)

and downloaded the 32-bit deb package. I transferred this via a USB pen drive, and installed it by right-clicking and opening with GDebi Package Installer. Now I could see that the broadcom driver was activated, but no sign of any wireless connection. I rebooted. It worked.

Many thanks for your help chili555

---

### Post by TheAscended on 2012-05-08
> **chili555 said:**
> Let's see what happened. Please run and post:```
sudo modprobe wl
dmesg | grep wl
rfkill list all
iwconfig
```

That worked! I am now sending this wirelessly. Thank you very much! :D

---

### Post by silverkitsune27 on 2012-05-09
I'm also having trouble installing the Broadcom STA Wireless Driver (directs me to the /var/log/jockey.log file). 

My output to "lspci -nn | grep 0280" is:

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Which set of solutions above should I follow? Thanks in advance for any help!

---

### Post by chili555 on 2012-05-09
> **silverkitsune27 said:**
> I'm also having trouble installing the Broadcom STA Wireless Driver (directs me to the /var/log/jockey.log file). 

My output to "lspci -nn | grep 0280" is:

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Which set of solutions above should I follow? Thanks in advance for any help!You do not need the STA driver; instead, you need:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```Post back if it doesn't spring to life.

---

### Post by silverkitsune27 on 2012-05-10
Ah! Worked like a charm. Thank you!

---

### Post by CortonaJ on 2012-05-10
> **chili555 said:**
> Perfect!

With a temporary ethernet connection, please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```After it's done, do:```
sudo modprobe wl
```If there is no error or warning, your wireless should be working.

I tried this for my Aspire one 722 with a BCM4313 802.11b/g/n Wireless lAN Controller [14e4:4727] (rev 01)but with no luck.
I'm new to using Terminal so it could be "Pilot Error"

---

### Post by bkratz on 2012-05-10
@CortonaJ


I believe you want to look around the area of posts 27 to 33 or so of this same thread, to look at the blacklistings described.

---

### Post by CortonaJ on 2012-05-10
I tried 

sudo modprobe -r wl
sudo modprobe -r bcma

but wl could not be found, so I did


sudo modprobe -r bcma
sudo modprobe -r brcmsmac
sudo apt-get install wl

it was installed but still doesn't work

---

### Post by chili555 on 2012-05-10
> I tried this for my Aspire one 722 with a BCM4313 802.11b/g/n Wireless lAN Controller [14e4:[COLOR="Red"]4727[/COLOR]] (rev 01)but with no luck.There is doubt as to the correct driver for this device. I have seen posts claiming that wl works; others claim brcmsmac is correct. Let's find out. First, we'll remove everything but wl:```
sudo modprobe -r bcma
sudo modprobe -r brcmsmac
sudo modprobe wl
iwconfig
```Do you have any errors or warnings to report? Do you have a wireless interface eth1? Can you connect? If so, stop and we'll make it permanent.

Now let's try brcmsmac:```
sudo modprobe -r bcma
sudo modprobe -r wl
sudo modprobe brcmsmac
iwconfig
```Do you have any errors or warnings to report? Do you have a wireless interface wlan0 or eth1? Can you connect?

---

### Post by CortonaJ on 2012-05-10
great, now working

---

### Post by chili555 on 2012-05-10
Great, now working *with which driver?* Would you like to tweak a file or two so it works after a reboot??

---

### Post by CortonaJ on 2012-05-11
Yes certainly, it is working with brcmsmac

---

### Post by chili555 on 2012-05-11
In order to get it to be persistent, so that you don't have to issue terminal commands every time you start the computer, please do:```
sudo su
echo brcmsmac >> /etc/modules
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
apt-get remove --purge bcmwl-kernel-source
exit
```The searchers and I appreciate the confirmation.

---

### Post by CortonaJ on 2012-05-11
Did all of that, restarted and all is working fine.
Thank you very much, not only for solving the problem but for giving me confidence to approach these things.

---

### Post by chili555 on 2012-05-11
> **CortonaJ said:**
> Did all of that, restarted and all is working fine.
Thank you very much, not only for solving the problem but for giving me confidence to approach these things.I'm glad it's working and I'm glad to have had a part in your relatively painless introduction to Ubuntu Linux. Have fun and post back if we can help you again.

---

### Post by ArjenR on 2012-05-13
> **chili555 said:**
> Perfect!

With a temporary ethernet connection, please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```After it's done, do:```
sudo modprobe wl
```If there is no error or warning, your wireless should be working.


This worked for me on an HP Mininote 5101. After upgrading to 12.04 from 11.10, which succeeded otherwise even though the upgrade process totally crashed at some point (mouse pointer locked up), the wireless connection didn't work. The STA driver wouldn't install, either.
I did try different things before I ran the above commands, but it's a fact that after following chili555's advice, the wireless connection started working.
The HP5101's wl card has a Broadcomm 43224 chip.
It worked on earlier distributions, but never without somewhat of a fight, except perhaps after my first Ubuntu installation ... likely 8.04.
Under 11.10 I had installed a kernel much newer than the one in Pangolin (testing if a problem with the use channel 13 had perhaps been solved in anewer kernel), but I kicked that out at one point when trying to get the wireless to work again.

---

### Post by chili555 on 2012-05-13
> This worked for me on an HP Mininote 5101. Excellent! Glad it's working. Post back if we can help you further.

---

### Post by WVPARN on 2012-05-14
> **CortonaJ said:**
> I tried this for my Aspire one 722 with a BCM4313 802.11b/g/n Wireless lAN Controller [14e4:4727] (rev 01)but with no luck.
I'm new to using Terminal so it could be "Pilot Error"

I found my answer here:

[http://bernaerts.dyndns.org/linux/202-ubuntu-acer-ao722](http://bernaerts.dyndns.org/linux/202-ubuntu-acer-ao722)

Changing the boot order seems to resolve the AO722 conflict between the ethernet and wireless adapters.

---

### Post by xingguo on 2012-05-22
hi chili555,

I got Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01), can you tell me what I should do? Thanks. mine is dell vostro 1088.

---

### Post by xingguo on 2012-05-22
> **chili555 said:**
> A known issue is that jockey; also known as Additional Drivers, suggests the wrong driver for a few Broadcom cards. Let's find out what you have and solve it. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.
hi chili555,

I got 
Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
can you tell me what I should do? Thanks. mine is dell vostro 1088.

---

### Post by chili555 on 2012-05-22
> **xingguo said:**
> hi chili555,

I got 
Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
can you tell me what I should do? Thanks. mine is dell vostro 1088.Please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```You should be all set but post back if you need more help.

---

### Post by Tucma on 2012-06-03
Hello Chili

Thank you very much for your help, but unfortunately I didn't arrive to activate my WiFi card. Is it maybe because the answer given by the computer is different to the one indicated by you?

04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [[SIZE=3][COLOR=Red]14e4:4311[/COLOR][/SIZE]] (rev 01)

Thank you very much in advance

---

### Post by Tucma on 2012-06-03
Just in case, my computer is Acer Aspire 5100.

---

### Post by chili555 on 2012-06-03
> unfortunately I didn't arrive to activate my WiFi card. Is it maybe because the answer given by the computer is different to the one indicated by you?Correct. A different card requires a different solution. Please make sure you have a wired ethernet connection and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```Please do not follow instructions for cards different that yours; they will most likely not work.

---

### Post by wizard_karan on 2012-06-05
> **chili555 said:**
> Perfect!

With a temporary ethernet connection, please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```After it's done, do:```
sudo modprobe wl
```If there is no error or warning, your wireless should be working.

Awesome! This solution worked for me too :D Thanks and Cheers to chili555

---

### Post by Tucma on 2012-06-05
Chili, I got the connexion! 

Thank you very much for your great help!

---

### Post by hansson_14 on 2012-06-07
Thanks, this solved it for me as well.
Laptop: Samsung 305-U1A
My pci.id is [14e4:4727] and it works.

---

### Post by chili555 on 2012-06-07
> **hansson_14 said:**
> Thanks, this solved it for me as well.
Laptop: Samsung 305-U1A
My pci.id is [[COLOR="Red"]14e4:4727[/COLOR]] and it works.Which of the several solutions worked for you? Please show us:```
lsmod | grep -e b43 -e wl -e brcm
```Thanks.

---

### Post by tarsofagundes on 2012-06-18
OK!!! thanks!!! in my Dell inspiron 1428 works fine!

---

### Post by Possum63 on 2012-07-04
> **chili555 said:**
> Please hook up the ethernet and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```Detach the ethernet and tell us if it's working.

Wow.  After a day and a half of internet research and forum reading, this fixed my issue.  Thank you so much.  :)

Edit:  Ok, it does fix the issue.  But it doesn't persist through reboot.  Had to do the second two commands again after rebooting.

I'm a complete Linux/Ubuntu noob.  So I appreciate your patience.  How do I make this persistent through reboot?

---

### Post by newbiedev on 2012-08-01
Hi I'm new to ubunto. I'm having the same problem trying to install the WiFi drivers. 
My information is 0b:00.0 network controller [0280]: broadcom corporation bcm4311 802.11b/g WLAN [14e4:4311] (rev 01]

My laptop is a Dell e1505 and I have no other form of internet other than the WiFi. So no Ethernet. I'm running ubuntu 10.04 lucid lynx
Any help would be much appreciated. Thanks.

---

### Post by bkratz on 2012-08-01
> **newbiedev said:**
> Hi I'm new to ubunto. I'm having the same problem trying to install the WiFi drivers. 
My information is 0b:00.0 network controller [0280]: broadcom corporation bcm4311 802.11b/g WLAN [14e4:4311] (rev 01]

My laptop is a Dell e1505 and I have no other form of internet other than the WiFi. So no Ethernet. I'm running ubuntu 10.04 lucid lynx
Any help would be much appreciated. Thanks.




This should take care of you

[http://ubuntuforums.org/showpost.php?p=12094989&postcount=12](http://ubuntuforums.org/showpost.php?p=12094989&postcount=12)


[COLOR=Red]Ignore the above,  just noticed that you are using 10.04 not 12.04![/COLOR]

---

### Post by chili555 on 2012-08-01
> **newbiedev said:**
> Hi I'm new to ubunto. I'm having the same problem trying to install the WiFi drivers. 
My information is 0b:00.0 network controller [0280]: broadcom corporation bcm4311 802.11b/g WLAN [14e4:4311] (rev 01]

My laptop is a Dell e1505 and I have no other form of internet other than the WiFi. So no Ethernet. I'm running ubuntu 10.04 lucid lynx
Any help would be much appreciated. Thanks.Please download the file I've attached and transfer it on a USB drive or similar. Drag and drop it to the desktop of the Dell. Right-click it and select Extract Here. Now open a terminal and do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo modprobe -r b43
sudo modprobe b43
```Is it working now?

---

### Post by newbiedev on 2012-08-01
> **chili555 said:**
> Please download the file I've attached and transfer it on a USB drive or similar. Drag and drop it to the desktop of the Dell. Right-click it and select Extract Here. Now open a terminal and do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo modprobe -r b43
sudo modprobe b43
```Is it working now?


im to do this in with linux loaded right?
also can i do this on a later version (12.04) of linux or it has to be (10.04)
update
sorry ignore the last question, i read your reply above. this is for 10.04

---

### Post by chili555 on 2012-08-01
> also can i do this on a later version (12.04) of linux or it has to be (10.04)
update
sorry ignore the last question, i read your reply above. this is for 10.04The firmware will be required in *both*.

---

### Post by newbiedev on 2012-08-01
> **chili555 said:**
> The firmware will be required in *both*.
 
ok im on 10.04 and i downloaded the zip. i just need to know if i should be doing this on the ubuntu os or windows os. im thinking the ubuntu. ill reply in a bit with the results.


again, thanks for the time to reply and help.

---

### Post by newbiedev on 2012-08-01
> **chili555 said:**
> Please download the file I've attached and transfer it on a USB drive or similar. Drag and drop it to the desktop of the Dell. Right-click it and select Extract Here. Now open a terminal and do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo modprobe -r b43
sudo modprobe b43
```Is it working now?

Thanks you very much, this worked...Oh I tried it on the 12.04 and it worked. Do I need to this on every boot or its permanent?

---

### Post by chili555 on 2012-08-02
> Do I need to this on every boot or its permanent?It's permanent. You should be all set, but if you have a problem, please post back and we'll be glad to help you.

---

### Post by chunnel on 2012-08-15
> **chili555 said:**
> A known issue is that jockey; also known as Additional Drivers, suggests the wrong driver for a few Broadcom cards. Let's find out what you have and solve it. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

I have the same problem, I ran that code above and got Broadcom Corporation BCM4313 802.11b/g/n Wirelesss LAN Controller [14e4:4727] (rev01).

By the way, how do you copy and paste in Ubuntu?  Ctrl C and Ctrl V do not seem to have any effect.  Nor do I see a menu bar to select copy or paste in the terminal.

---

### Post by chili555 on 2012-08-15
> **chunnel said:**
> I have the same problem, I ran that code above and got Broadcom Corporation BCM4313 802.11b/g/n Wirelesss LAN Controller [14e4:4727] (rev01).

By the way, how do you copy and paste in Ubuntu?  Ctrl C and Ctrl V do not seem to have any effect.  Nor do I see a menu bar to select copy or paste in the terminal.Please start a new thread; this one is getting old.

You simply highlight the text and right-click then select Copy. Please see attached.

---

### Post by sankalp84 on 2012-08-15
hi , i am also facing same problem , but in my side ethernet connection is also not working.
please help me out this.

Thanks

---

### Post by chili555 on 2012-08-15
> **sankalp84 said:**
> hi , i am also facing same problem , but in my side ethernet connection is also not working.
please help me out this.

ThanksPlease start a new thread; this one is getting old.

---

### Post by chunnel on 2012-08-15
> **chili555 said:**
> Please start a new thread; this one is getting old.

You simply highlight the text and right-click then select Copy. Please see attached.
Right click won't work in Ubuntu on my mousepad.  I see no settings to change in Mousepad under System settings that could make it work.

---

### Post by chili555 on 2012-08-15
> Right click won't work in Ubuntu on my mousepad.What sort of device is it? How do you paste then?

:confused:

---

### Post by kinzel on 2012-08-16
> **chili555 said:**
> Perfect!

With a temporary ethernet connection, please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```After it's done, do:```
sudo modprobe wl
```If there is no error or warning, your wireless should be working.

Thanks! :D:D:D

---

### Post by Guinness37 on 2012-08-21
I also am new to Ubuntu.  This post helped me fix the same issue, so thank you for sharing this!

---

### Post by martinkorlu on 2012-09-12
its not working for me... i get the result...

Module wl not found.

---

### Post by chili555 on 2012-09-12
> **martinkorlu said:**
> its not working for me... i get the result...

Module wl not found.Please see post #106.

---

### Post by thesheckies on 2012-09-12
Please help,- recently upgraded daughters Qimo to Ubuntu 12.04- i think.   Wireless not working.  Wireless required for her to do school work away from my office.  

says i have the broadcom sta wireless driver

tried uninstalling and resintalling the driver,- found one website that suggested blacklisting something- cant remember what it was i blacklisted- found website here- 
[http://ubuntuforums.org/showthread.php?t=1859668](http://ubuntuforums.org/showthread.php?t=1859668)

came on your thread from finding the pci.id to be 14e4:4311.  

the terminal says 

Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)


tried some commands from this thread,- nothing worked. still no wireless networks found.

maybe i need to unblacklist something?  i have Dell inspiron E1505

Thanks for your help

---

### Post by chili555 on 2012-09-12
> **thesheckies said:**
> Please help,- recently upgraded daughters Qimo to Ubuntu 12.04- i think.   Wireless not working.  Wireless required for her to do school work away from my office.  


Thanks for your helpPlease see post #106.

---

### Post by Cowcharge on 2012-09-15
> **chili555 said:**
> Please hook up the ethernet and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```Detach the ethernet and tell us if it's working.

My hero! This is my first time using Linux, and after a week of trying ](*,) to get my wireless working I found this thread, then found the same 4311 ID, did the above and it worked! Through 2 reboots as well. Thank you! \\:D/:guitar:):P

---

### Post by matspitz0 on 2012-09-25
WOW THANKS chili555. Broadcom wifi working on a GATEWAY mx6453!!

:P

---

### Post by rubyalma on 2012-09-26
I put the first code and got 0:400.0 network controller [0280]: Broadcom corporation bcm4312 802.11b/g LO-PHY [14e4:4315] (rev 01)

---

### Post by chili555 on 2012-09-27
> **rubyalma said:**
> I put the first code and got 0:400.0 network controller [0280]: Broadcom corporation bcm4312 802.11b/g LO-PHY [[COLOR="Red"]14e4:4315[/COLOR]] (rev 01)You need the Broadcom STA driver. Please hook up the ethernet and do:```
sudo apt-get install bcmwl-kernel-source
```Reboot and it should be working.

---

### Post by dlr2986 on 2012-10-02
> **chili555 said:**
> 
With a temporary ethernet connection, please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```After it's done, do:```
sudo modprobe wl
```If there is no error or warning, your wireless should be working.

Thank you!

This worked for me after ubuntu 12.04 updates somehow killed the wireless connection!

It was not fun to drag my entire system across the house in order to plug into a ethernet cable.

---

### Post by chili555 on 2012-10-02
> **dlr2986 said:**
> It was not fun to drag my entire system across the house in order to plug into a ethernet cable.I'm sure. Hopefully, now it's fixed and you will have smooth sailing!

---

### Post by Vitex2011 on 2012-10-09
Just to say thank you: I had a similar problem on my Dell Inspiron 1525 upgrading from 11.10 to 12.04 and a Broadcom BCM4312 - your solution worked perfectly.

---

### Post by nutpants on 2012-10-19
this fixed my wifi with a bcm43227 card on my acer timeline 1830tz

but modprobe wl  will not stick
i have to issue the command every time i boot..

is there a way around this other that adding it to rc.local???

---

### Post by chili555 on 2012-10-19
> **nutpants said:**
> this fixed my wifi with a bcm43227 card on my acer timeline 1830tz

but modprobe wl  will not stick
i have to issue the command every time i boot..

is there a way around this other that adding it to rc.local???Certainly!```
sudo su
echo wl >> /etc/modules
exit
```

---

### Post by umfunix on 2012-10-21
> **chili555 said:**
>  
With a temporary ethernet connection, please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```After it's done, do:```
sudo modprobe wl
```If there is no error or warning, your wireless should be working.
 
Hi
 
I DO NOT have a temporary connection on the laptop as the nethernet adapter is broke. I can however download the driver package from anouter computer onto a flash drive.
 
How do I do that?
 
Thanks

---

### Post by chili555 on 2012-10-21
> **umfunix said:**
> Hi
 
I DO NOT have a temporary connection on the laptop as the nethernet adapter is broke. I can however download the driver package from anouter computer onto a flash drive.
 
How do I do that?
 
ThanksYou can get it here: [http://packages.ubuntu.com/precise/bcmwl-kernel-source](http://packages.ubuntu.com/precise/bcmwl-kernel-source)

Be sure to get the correct architecture; either 32- or 64-bit and be sure to get all the dependencies indicated by the red dots. If you have it mis-installed now, first remove it:```
sudo apt-get remove --purce bcmwl-kernel-source
```If you do have it, you probably have the dependencies already, too; check:```
sudo dpkg -s some_dependency
```For example:```
chili@LAPTOP410:~$ sudo dpkg -s dkms
[sudo] password for chili: 
Package: dkms
Status: [COLOR="Red"]install ok installed[/COLOR]
Priority: optional
<snip>
```Once you have the packages downloaded, drag and drop them to your desktop. Then install with:```
cd Desktop
sudo dpkg -i *.deb
```The wildcard * means install *all* the deb packages.

Before you go to all this trouble, please verify you have the *exact* same device by matching the pci.id:```
lspci -nn | grep 0280
```Different devices require different fixes.

---

### Post by cloti on 2012-10-29
It also worked for me with this code [14e4:4315]

---

### Post by RHogskin on 2012-11-08
> **chili555 said:**
> A known issue is that jockey; also known as Additional Drivers, suggests the wrong driver for a few Broadcom cards. Let's find out what you have and solve it. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.
I have this same problem. I haven't been able to figure out how to get in on the conversation. Here are the results of "lspci -nn | grep 0280"

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)0

My computer is a Dell D620; I am running Ubuntu 12.10.

---

### Post by philipy1219 on 2012-11-09
I followed this but got
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found.
FATAL: Error running install command for wl

---

### Post by chili555 on 2012-11-09
> **philipy1219 said:**
> I followed this but got
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found.
FATAL: Error running install command for wlIn order to be sure you are installing the correct driver, please post:```
lspci -nn | grep 0280
```

---

### Post by chili555 on 2012-11-09
> **RHogskin said:**
> I have this same problem. I haven't been able to figure out how to get in on the conversation. Here are the results of "lspci -nn | grep 0280"

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [[COLOR="Red"]14e4:4311[/COLOR]] (rev 01)0

My computer is a Dell D620; I am running Ubuntu 12.10.Your device needs this and not the STA driver:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```You should be all set.

---

### Post by philipy1219 on 2012-11-09
Here is 
> 03:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)

---

### Post by chili555 on 2012-11-09
Excellent. Let's fix this and then try again:> Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.Kernel source in Ubuntu world is linux headers, so please do:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Are we there yet?

---

### Post by philipy1219 on 2012-11-10
Thank you! My wifi is working now.

---

### Post by kapad on 2012-11-11
hey, 

I am having the same problem as philipy1219.

The output to sudo apt-get-install bcmwl-kernel-source is

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 69 not upgraded.
Need to get 0 B/1,181 kB of archives.
After this operation, 3,609 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 165716 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb) ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-17-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
```


I have tried `sudo apt-get install -reinstall bcmwl-kernel-source` and purging and then installing. still the same output each times

Have also tried chilli555's solution of installing linux-headers-generic and then installing bcmwl-kernel-source. Still no luck

Please let me know if you want any other hardware information. Help appreciated.

---

### Post by chili555 on 2012-11-11
> Have also tried chilli555's solution of installing linux-headers-generic and then installing bcmwl-kernel-source. Still no luckPlease show me the results in *exact* order:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```

---

### Post by iwanttoknow2012 on 2012-11-18
hi,my card is also bcm43227 . i have only wifi, i have no Ethernet. how can i install the driver without An Internet Connection...how ,give me detail step and download link.thinks

---

### Post by chili555 on 2012-11-18
> **iwanttoknow2012 said:**
> hi,my card is also bcm43227 . i have only wifi, i have no Ethernet. how can i install the driver without An Internet Connection...how ,give me detail step and download link.thinksPlease see my reply on your thread.

---

### Post by ysk099 on 2012-11-23
same problem...
my pc.icp is [14e4:4328]

---

### Post by ysk099 on 2012-11-23
my thing is 14e4 4328 bcm 4321

can u please help me

---

### Post by ysk099 on 2012-11-23
plus I have no Internet connection

---

### Post by 555|STi on 2012-11-26
> **chili555 said:**
> Your device needs this and not the STA driver:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```You should be all set.

Hey man, just logged in to say thanks. You just saved me. =D>

---

### Post by raux87 on 2012-12-17
Hello, my names is giorgio and i write from italy near naples..sorry for my horrible english but i can't speak wery well..
i have a problem whith wi fi connection on my acer 5750g..
i have ubuntu 12.10..
i tryed some solution without a good results...in italian forum i don't find a solution..

 pci-id 4358,  broadcom...
help my please!


ps.: write a simple english for me..tanks;)

---

### Post by chili555 on 2012-12-17
> **raux87 said:**
> Hello, my names is giorgio and i write from italy near naples..sorry for my horrible english but i can't speak wery well..
i have a problem whith wi fi connection on my acer 5750g..
i have ubuntu 12.10..
i tryed some solution without a good results...in italian forum i don't find a solution..

 pci-id 4358,  broadcom...
help my please!


ps.: write a simple english for me..tanks;)Your English is just fine. I understand you well. With a temporary ethernet connection, please open a terminal and do:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Your wireless should now be working.

---

### Post by raux87 on 2012-12-18
> **chili555 said:**
> Your English is just fine. I understand you well. With a temporary ethernet connection, please open a terminal and do:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Your wireless should now be working.

hello, tanks for the guide...
unfortunly my pc doesn't work...i think there is a problem with a ethernet connection because ubuntu tell me: unable to download some packages. may be useful to "atp-get update" or try "--fix-missing"...


help me!!;)

---

### Post by chili555 on 2012-12-18
I suggest you do exactly that:```
sudo apt-get update
sudo apt-get --fix-missing
```If that all goes without errors, then proceed:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```If there are any errors, please post them and I'll be happy to help.

---

### Post by raux87 on 2012-12-18
> **chili555 said:**
> I suggest you do exactly that:```
sudo apt-get update
sudo apt-get --fix-missing
```If that all goes without errors, then proceed:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```If there are any errors, please post them and I'll be happy to help.

ubuntu work..him download a some packages..it's a slow download, but work!
i hope....

no, same error... unable to download some packages. may be useful to "atp-get update" or try "--fix-missing"...
hmhm...

---

### Post by chili555 on 2012-12-18
Are there any errors or messages after this:```
sudo apt-get --fix-missing
```Or this?```
sudo apt-get install -f
```

---

### Post by manojfdo on 2012-12-31
i tried to fix it with the instruction you gave... but still it wont workout

here's what i'm getting

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  efibootmgr
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 220 not upgraded.
Need to get 0 B/1,181 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 142079 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.112+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
Building only for 3.5.0-17-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
manojfdo@manojfdo-Aspire-4752:~$ sudo modprobe wl
FATAL: Module wl not found.

---

### Post by chili555 on 2012-12-31
> Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.But now we know *why* it didn't work and a method to fix it!```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo apt-get autoremove
sudo modprobe wl
```Now is it working?

---

### Post by manojfdo on 2013-01-01
> **chili555 said:**
> But now we know *why* it didn't work and a method to fix it!```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo apt-get autoremove
sudo modprobe wl
```Now is it working?

i'm still getting an error

manojfdo@manojfdo-Aspire-4752:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 220 not upgraded.
manojfdo@manojfdo-Aspire-4752:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 220 not upgraded.
Need to get 0 B/1,181 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 164822 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.112+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
Building only for 3.5.0-17-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic

---

### Post by manojfdo on 2013-01-01
I update the ubuntu now it;s ok thx brother

---

### Post by chili555 on 2013-01-01
> Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.Same error...if old Chili were inclined to curse, this might be a time to start. linux-headers-generic is supposed to also install the needed headers for your running kernel version. Obviously, it did not. I notice you have a few updates pending. I suggest you get those done first:```
sudo apt-get update && sudo apt-get upgrade
sudo reboot
```After the reboot, do:```
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Those backticks are on the left side of my US keyboard on the same key with ~.

---

### Post by chili555 on 2013-01-01
> **manojfdo said:**
> I update the ubuntu now it;s ok thx brotherGreat news. Glad it's working!

---

### Post by Harco02 on 2013-01-09
> **chili555 said:**
> Perfect!

With a temporary ethernet connection, please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```After it's done, do:```
sudo modprobe wl
```If there is no error or warning, your wireless should be working.

hello i'm new in ububtu, i have the same problem and found this solution, i try this but i get that:

root@bt:~# sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.39.4
Building for architecture x86_64
Building initial module for 2.6.39.4

Error! Bad return status for module build on kernel: 2.6.39.4 (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by chili555 on 2013-01-09
> Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.I suggest you do just that:```
cat /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/make.log
```If you can see more specific information about the error, please post it here. If you can't determine what it is, post the whole log here.

---

### Post by Decaffeination on 2013-01-13
Hi! I am quite new with Linux and have this problem. I'd really appreciate some help. 

Info about the system:
Ubuntu 12.04 LTS
Wireless card Broadcom 4358

Problem:
Claims to have the network disabled, although it's enabled. Therefore doesn't see the available networks as well.

I read your recommendations on this thread and applied them. Executed commands and results:

lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]

Connected via Ethernet and executed the guys below. 
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
It didn't complain, everything looked fine. It even started to see the available networks. However, it doesn't connect. I 

enter the password, it tries to connect, then it asks the password again. 

Then I tried this:
sudo modprobe -r wl
sudo modprobe -r bcma
sudo modprobe brcmsmac
It got back to its initial status. (claiming the wlan to be disabled)

I did
sudo modprobe wl
Back to the second status (seeing the networks but not being able to connect)

Then I did the blacklisting things
sudo su
echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
echo brcmsmac >> /etc/modules
exit
Didn't change much. Still pending between two status depending on modprobe -r wl / modprobe wl

Btw. I rebooted a couple of times.

When I run 
lsmod | grep -e wl -e bcma -e brcmsmac
I get
(after modprobe -r wl)
brcmsmac	570874	0
mac80211	506816	1 brcmsmac
brcmutil	 15139	1 brcmsmac
cfg80211	205544	2 brcmsmac,mac80211
crc8		 12893	1 brcmsmac
cordic		 12535	1 brcmsmac
if I do a modprobe wl before I run lsmod | grep -e wl -e bcma -e brcmsmac I get two additional lines
wl		2568210	0
lib80211	  14381	2 lib80211_crypt_tkip,wl
The rest remains the same.

When I run this commands after modprobe -r wl
dmesg | grep -e brcm -e wlan
iwconfig
lo	no wireless extensions.

eth0	no wireless extensions.

rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no

When I run the same commands after modprobe wl
dmesg | grep -e brcm -e wlan
iwconfig
lo	no wireless extensions.

eth1	IEEE 802.11  Access Point: Not-Associated
	Link Quality:5  Signal level:0  Noise level:0
	Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0	no wireless extensions.

rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Sorry if the message was too long, but I figured you ask this stuff everytime. Thank you in advance!

Regards

---

### Post by chili555 on 2013-01-13
> Broadcom Corporation BCM43227 802.11b/g/n [[COLOR="Red"]14e4:4358[/COLOR]]I believe *wl*, the STA driver is correct for your device. Let's get it and only it loading and troubleshoot from there.```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Make sure the blacklist for* wl* is removed and the following appear:```
blacklist bcma
blacklist brcmsmac
blacklist b43
blacklist ssb
```Proofread carefully, save and close gedit. Now do:```
gksudo gedit /etc/modules
```Make sure *wl* appears and not any other Broadcom driver. Proofread carefully, save and close gedit.

Reboot and post:```
iwconfig
dmesg | grep eth1
sudo iwlist eth1 scan
```Thanks.

---

### Post by Decaffeination on 2013-01-13
First of all, thank you for taking time to reply!

In blacklist.conf: I deleted wl, b43 and ssb weren't there, I appended them.

In modules: It was brcmsmac, now it is wl.

Done the last part. Its reaction:

pi@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:212  Noise level:187
          Rx invalid nwid:0  invalid crypt:12  invalid misc:0

eth0      no wireless extensions.

pi@ubuntu:~$ dmesg | grep eth1
[   26.494604] eth1: Broadcom BCM4358 802.11 Hybrid Wireless Controller 5.100.82.38

pi@ubuntu:~$ sudo iwlist eth1 scan
[sudo] password for pi: 
eth1      Scan completed :
    Cell 01 - Address: ...
                    ESSID:"..."
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-46 dBm  Noise level:-89 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDAC0050F204104A0001101044000102103B0001031047001083989299473954BB2649E64539DC9243102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000752542D4E3636551042001133303A38353A41393A36423A34453A35301054000800060050F20400011011000752542D4E363655100800022008103C0001031049000600372A000120
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

12 other cells like that.

It finally worked. Turns out I had to reboot again.

Thank you very much! You saved me hours of anger and disappointment.

---

### Post by chili555 on 2013-01-13
> It finally worked. Turns out I had to reboot again.Awesome! Glad it's working.

---

### Post by stryk9 on 2013-01-29
Hi Chilli, I was hoping you could help me out as well as you seem to be the godly man of knowledge fixing everybody's issue! :)

I am running an Acer Aspire 5560. This is the output of the inxi -i command

Network:   Card-1: Broadcom BCM43227 802.11b/g/n driver: wl 
           IF: eth1 state: up mac: 64:27:37:32:c3:80
           Card-2: Broadcom NetLink BCM57785 Gigabit Ethernet PCIe driver: tg3 
           IF: eth0 state: down mac: 20:6a:8a:6a:f6:d8
           WAN IP: 108.162.151.209 IF: eth0 ip: N/A IF: eth1 ip: 192.168.0.107


I ran the command 

"sudo apt-get install --reinstall bcmwl-kernel-source"

and the command seems to somewhat go well? I mean, I'm currently using the wireless as of now, but as soon as I reboot, it disappears. Another thing to take note of though is at the end of running the above command, I get this...

bruce@bruce-Aspire-5560 ~ $ sudo apt-get install --reinstall bcmwl-kernel-source 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  apport-hooks-medibuntu
Use 'apt-get autoremove' to remove it.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 0 B/1,181 kB of archives.
After this operation, 3,609 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 166120 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb) ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-17-generic
Building for architecture x86_64
Building initial module for 3.5.0-17-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-17-generic/updates/

depmod....

DKMS: install completed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
Warning: No support for locale: en_US.utf8

on top of that, attempting to run the command:

sudo modprobe w1

returns an error as well stating "FATAL: Module w1 not found." I'm clueless what to do at this point as I've been able to get it to work on my own prior to coming to this forum but with the same issue of my wifi disappearing right after reboot. Really hope you  can help me out. Thank you.

---

### Post by chili555 on 2013-01-29
> **stryk9 said:**
> 
on top of that, attempting to run the command:

sudo modprobe w1

returns an error as well stating "FATAL: Module w1 not found." I'm clueless what to do at this point as I've been able to get it to work on my own prior to coming to this forum but with the same issue of my wifi disappearing right after reboot. Really hope you  can help me out. Thank you.First, the name of the module is wl with an L, not w1 with a one. Please try:```
sudo modprobe wl 
```Does your wireless spring to life? If so, let's get it to load automatically on boot:```
sudo su
echo wl >> /etc/modules
exit
```If there are other warnings or errors, post back; I'll be happy to help.

---

### Post by stryk9 on 2013-01-29
LoL! Can't believe I didn't notice the l vs 1 haha... Well, afterall, they do look pretty damn the same! Everything seems fine ! sudo modprobe wl functioned with no errors, and also entered your commands to make it automatically run at startup. Wow, you're amazing! Thank you so much! You're the guru!

---

### Post by chili555 on 2013-01-29
> **stryk9 said:**
> LoL! Can't believe I didn't notice the l vs 1 haha... Well, afterall, they do look pretty damn the same! Everything seems fine ! sudo modprobe wl functioned with no errors, and also entered your commands to make it automatically run at startup. Wow, you're amazing! Thank you so much! You're the guru!Glad it's working and thanks for your kind comments.

---

### Post by sausi007 on 2013-02-24
I am very new to ubuntu and the wireless is not working. I tried the sudo modprobe wl command.  But nothing happens after I run it.  The terminal just sort of hangs. I have ubuntu 12.04.1 LTS and a very old hp compaq laptop. I am sorry but I have no idea which wireless adapter is in this system. 

Next step - blacklisted.

Command: lsmod | grep -e wl -e bcma -e brcmsmac
Output:
brcmsmac   540923  0
mac80211   436493  1 brcmsmac
brcmutil    14675  1 brcmsmac
cfg80211   178877  2 brcmsmac, mac80211
crc8        12781  1 brcmsmac
cordic      12518  1 brcmsmac

Next step
dmesg | grep -e brcm -e wlan
iwconfig

Output
lo   no wireless extensions

Next:
rfkill list all

Output:
0: hp-wifi: Wireless LAN
     Soft blocked: no
     Hard blocked: no
1: hp-bluetooth: Bluetooth
     Soft blocked: yes
     Hard blocked: no

What should be my next steps?

---

### Post by chili555 on 2013-02-24
> **sausi007 said:**
> I am very new to ubuntu and the wireless is not working. 

What should be my next steps?Would you please start your own new thread instead of adding on to this moldy oldy? Please add this information from the terminal:```
lspci -nn | grep 0280
```Thanks.

---

### Post by sureshvv on 2013-03-30
modprobe wl says

FATAL: module wl not found

---

### Post by chili555 on 2013-03-30
> **sureshvv said:**
> modprobe wl says

FATAL: module wl not foundWould you please start your own new thread instead of adding on to this moldy oldy? Please add this information from the terminal:


```
lspci -nn | grep 0280
```

In a 160+ post thread going back almost a year, that is my answer.

---

### Post by Nerph on 2013-04-29
Hello

chill555, I have the exact same laptop as the person who created this thread, and I followed your steps, however after doing the reinstall of bcmwl-kernel-source I get the following error:

```
ERROR (dkms apport): kernel package linux-headers-3.5.0-23-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-23-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
```

and when doing the sudo modprobe wl command I get the following error:

```
FATAL: Module wl not found.
```

Any idea what the problem could be? All the information matches that of the topic creator, yet for some reason your solution doesn't work for me :(

---

### Post by chili555 on 2013-04-30
> ERROR (dkms apport): kernel package linux-headers-3.5.0-23-generic is not supportedPlease try this:```
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall linux-headers-`uname -r`
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

Any improvement?

---

### Post by Nerph on 2013-04-30
> **chili555 said:**
> Please try this:```
sudo apt-get install --reinstall linux-headers-`uname -r`
```

After doing that part of the commands you advised, I get this error:

```
Reinstallation of linux-headers-3.5.0-23-generic is not possible, it cannot be downloaded.
```

Carrying on with the rest, will update my post with how it goes.

edit: It hasn't seemed to work, still the same previous errors, pasted below:

```
ERROR (dkms apport): kernel package linux-headers-3.5.0-23-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-23-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
```

and 

```
FATAL: Module wl not found.
```

So no improvements :(

---

### Post by tusharmilan on 2013-05-15
is connection via ethernet cable absolutely necessary for fixing wireless problem? i have pci:id (14e4:4727) and same wireless problem. without ethernet not possible?

---

### Post by chili555 on 2013-05-16
> **tusharmilan said:**
> is connection via ethernet cable absolutely necessary for fixing wireless problem? i have pci:id (14e4:4727) and same wireless problem. without ethernet not possible?It is possible. Please run and post:```
lsmod | grep -e wl -e brcmsmac
sudo dpkg -s bcmwl-kernel-source
```We'll figure out a way.

Do you have your original Ubuntu install disk?

---

### Post by johnnycatt on 2013-06-12
this thread worked for me!!  I was WIFI by the 5th panel on page 1 of this thread!

Acer Aspire D250
Broadcom BCM4312

---

### Post by dheerajmarda on 2013-07-10
I have the same proble with my brocom wireless driver , i followed the above steps and i got following reply for 

sudo apt-get install --reinstall bcmwl-kernel-source 


dheerajmarda@ubuntu:~$ lspci -nn | grep 0280
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
dheerajmarda@ubuntu:~$ sudo apt-get install --reinstall bcmwl-kernel-source
[sudo] password for dheerajmarda: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,151 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 165012 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 3.5.0-23-generic
Building for architecture x86_64
Building initial module for 3.5.0-23-generic
ERROR (dkms apport): kernel package linux-headers-3.5.0-23-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-23-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic
Warning: No support for locale: en_US.utf8
dheerajmarda@ubuntu:~$ sudo modprobe wl
FATAL: Module wl not found.
dheerajmarda@ubuntu:~$ sudo apt-get install --reinstall bcmwl-kernel-source
[sudo] password for dheerajmarda: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,151 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 165012 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 3.5.0-23-generic
Building for architecture x86_64
Building initial module for 3.5.0-23-generic
ERROR (dkms apport): kernel package linux-headers-3.5.0-23-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-23-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic
Warning: No support for locale: en_US.utf8
dheerajmarda@ubuntu:~$ clear

dheerajmarda@ubuntu:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,151 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 165012 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 3.5.0-23-generic
Building for architecture x86_64
Building initial module for 3.5.0-23-generic
ERROR (dkms apport): kernel package linux-headers-3.5.0-23-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-23-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic
Warning: No support for locale: en_US.utf8
dheerajmarda@ubuntu:~$

---

### Post by chili555 on 2013-07-11
> ERROR (dkms apport): kernel package linux-headers-3.5.0-23-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-[COLOR="#FF0000"]23[/COLOR]-generic (x86_64)I expect what that means is that it would like for you to update your kernel, also known as linux-image, to the latest and try again. Please run Update manager, let it update your linux-image and linux-headers to the latest, reboot and try again.

---

### Post by ngoviettien on 2013-09-15
Hi Chili555,
I'm new in Ubuntu and i got the same problem with installing Broadcom STA Wireless. I've run
```
lspci -nn | grep 0280
```
and this is the result:
```
02:00.0 Network controller [0280]: Broadcom Corporation [COLOR=#ff0000]BCM4312[/COLOR] 802.11b/g LP-PHY [[COLOR=#ff0000]14e4:4315[/COLOR]] (rev 01)
```
I tryed exactly all solutions that you gave:
```
sudo apt-get update && sudo apt-get upgrade
sudo reboot
```
and
```
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
or 
```
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall linux-headers-`uname -r`
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
but i still cannot install Broadcom Wireless driver. Every command is OK, except:
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
and with this command, i got error:
```
tien@tien-HP-ProBook-4410s:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,301 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 195224 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu0.0.1 (using .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.8.0-30-generic
Building for architecture i686
Building initial module for 3.8.0-30-generic
[COLOR=#ff0000]Error! Bad return status for module build on kernel: 3.8.0-30-generic (i686)
Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.[/COLOR]
FATAL: Module wl not found.
FATAL: Error running install command for wl
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-30-generic


```
This is my log file:
```
tien@tien-HP-ProBook-4410s:~$ more /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log
DKMS make.log for bcmwl-6.20.155.1+bdcom for kernel 3.8.0-30-generic (i686)
Sun Sep 15 13:25:13 ICT 2013
make: Entering directory `/usr/src/linux-headers-3.8.0-30-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.o
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c: In function
 &#8216;wl_cfg80211_join_ibss&#8217;:
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:705:26: erro
r: &#8216;struct cfg80211_ibss_params&#8217; has no member named &#8216;channel&#8217;
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c: At top leve
l:
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1560:2: warn
ing: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1560:2: warn
ing: (near initialization for &#8216;wl_cfg80211_ops.scan&#8217;) [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1565:2: warn
ing: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1565:2: warn
ing: (near initialization for &#8216;wl_cfg80211_ops.set_tx_power&#8217;) [enabled by defaul
t]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1566:2: warn
ing: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1566:2: warn
ing: (near initialization for &#8216;wl_cfg80211_ops.get_tx_power&#8217;) [enabled by defaul
t]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c: In function
 &#8216;wl_update_bss_info&#8217;:
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1991:11: err
or: &#8216;struct cfg80211_bss&#8217; has no member named &#8216;information_elements&#8217;
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1992:15: err
or: &#8216;struct cfg80211_bss&#8217; has no member named &#8216;len_information_elements&#8217;
make[1]: *** [/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.
o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-30-generic'


```
Please, help me. I'm tired to looking for solution.
P/S: i install Ubuntu 12.04 LTS on HP Probook 4410s.

---

### Post by varunendra on 2013-09-15
Welcome to the forums ngoviettien! :)

> **ngoviettien said:**
> 
```

[COLOR=#ff0000]Error! Bad return status for module build on kernel: 3.8.0-30-generic (i686)
Consult /var/lib/dkms/bcmwl/**6.20.155.1+bdcom**/build/make.log for more information.[/COLOR]
FATAL: Module wl not found.
FATAL: Error running install command for wl

```

That version ^^ currently available in the repositories is broken. Things like this should immediately get fixed, but evidently this one hasn't been for quite a few days now.

Anyway, a fixed, working [newer version]("https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504") is available at launchpad, but it is meant for 64 bit and I can't say if it'll work on 32 bit also, which you have.

But you shouldn't need the sta driver at all. The native b43 driver should work better for you. Please try -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
Wireless good now?

---

### Post by ngoviettien on 2013-09-15
I really appreciate your help. I've just found another solution for my problem shown in this page:
```
http://www.broadcom.com/support/802.11/linux_sta.php
```
So, which is the best way? Can you or anyone give me some advices? Thanks in advance. :)

---

### Post by varunendra on 2013-09-15
It is a newer version of the sta driver (slightly newer than the one I linked to, thank God they finally cared to provide an updated one !). You may try it but you'll have to purge the currently installed one anyway.

So I suggest you try what I suggested in my previous post first. If it doesn't work, we may try the one you found above.

---

### Post by alexmat on 2014-03-06
Hallo,

I followed the discussion. 
Having exactly this: 
Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4: 4358] 

I reinstalled: 
sudo apt-get install - reinstall kernel-source-bcmwl 

But it does not solve anything. After a while the PC Freezing (freezes the screen and all keys are usable).
Thanks for help-me

Alex

---

### Post by varunendra on 2014-03-06
Welcome to the forums Alex! :)

Is this a typo or did you run exactly this code ? -
> **alexmat said:**
> 
sudo apt-get install **[COLOR="#FF0000"]- reinstall kernel-source-bcmwl[/COLOR]**
Error #1 : there is a gap between hyphen (-) and reinstall, there shouldn't be any,
Error #2 : there is no such package as "kernel-source-bcmwl". Instead, it is "bcmwl-kernel-source".

If these corrections don't solve your problem, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by alexmat on 2014-03-06
1)  exactly  my command  wos :
sudo apt-get install --reinstall bcmwl-kernel-source.



I post  the output.

```

*************** info trace ***************

***** uname -a *****

Linux Aspire-5755G 3.2.0-59-generic #90-Ubuntu SMP Tue Jan 7 22:43:51 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0504]
    Kernel driver in use: tg3
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
    Subsystem: Foxconn International, Inc. Device [105b:e040]
    Kernel driver in use: wl

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b2dc Chicony Electronics Co., Ltd 

***** PCMCIA Card Info *****


***** iwconfig *****

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

***** rfkill *****

0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

***** iw reg get *****

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

***** route -n *****

Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

***** lsmod *****

wl                   3074895  0 
cfg80211              205774  1 wl
lib80211               14381  2 lib80211_crypt_tkip,wl

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Ethernet automatica] ------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

  IPv6 Settings:
    Address:         fd00:664b:b3e0:a100:6d80:d04b:b310:477b
    Prefix:          64
    Gateway:         ::

    Address:         fd00:664b:b3e0:a100:de0e:a1ff:fe5c:4b49
    Prefix:          64
    Gateway:         ::

    Address:         fe80::de0e:a1ff:fe5c:4b49
    Prefix:          64
    Gateway:         ::




***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
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

[/etc/modprobe.d/bumblebee.conf]
blacklist nouveau
blacklist nvidia
blacklist nvidia-current
blacklist nvidia-current-updates
blacklist nvidia-304
blacklist nvidia-304-updates
blacklist nvidia-experimental-304
blacklist nvidia-310
blacklist nvidia-310-updates
blacklist nvidia-experimental-310
blacklist nvidia-313
blacklist nvidia-313-updates
blacklist nvidia-experimental-313
blacklist nvidia-319
blacklist nvidia-319-updates
blacklist nvidia-experimental-319
blacklist nvidia-325
blacklist nvidia-325-updates
blacklist nvidia-experimental-325
blacklist nvidia-331
blacklist nvidia-331-updates
blacklist nvidia-experimental-331

***** modinfo *****

filename:       /lib/modules/3.2.0-59-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     CBEDDD2D4888AAD1517D3C9
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.2.0-59-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

***** dmesg *****

[   29.052891] wl: module license 'MIXED/Proprietary' taints kernel.
[   29.056837] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   29.056847] wl 0000:03:00.0: setting latency timer to 64
[   29.084634] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   29.230086] eth1: Broadcom BCM4358 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   29.444714] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f01)
[   29.897210] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  696.422273] ERROR @wl_dev_intvar_get : error (-1)
[  696.422277] ERROR @wl_cfg80211_get_tx_power : error (-1)

****************** done ******************

```

many thanks
Alex

---

### Post by varunendra on 2014-03-06
You seem to have not enabled Wireless in Network Manager menu. Please make sure there is a Tick mark before "Enable Wireless" option in Network Manager menu (click it to enable it).

---

### Post by alexmat on 2014-03-06
i repost  the  report file  with  wireless  connection "on"

```

*************** info trace ***************

***** uname -a *****

Linux Aspire-5755G 3.2.0-59-generic #90-Ubuntu SMP Tue Jan 7 22:43:51 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0504]
    Kernel driver in use: tg3
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
    Subsystem: Foxconn International, Inc. Device [105b:e040]
    Kernel driver in use: wl

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b2dc Chicony Electronics Co., Ltd 

***** PCMCIA Card Info *****


***** iwconfig *****

eth1      IEEE 802.11abg  ESSID:"InfostradaWiFi-404264"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

***** rfkill *****

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****

country IT:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS

***** route -n *****

Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1

***** lsmod *****

wl                   3074895  0 
cfg80211              205774  1 wl
lib80211               14381  2 lib80211_crypt_tkip,wl

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth1  [InfostradaWiFi-404264] ----------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           104 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    AP_LEV02:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Vodafone-26528627: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2
    NETGEAR53:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    FASTWEB-1-0021964425CC: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA
    *InfostradaWiFi-404264: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             8.8.8.8


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"InfostradaWiFi-404264"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 0015496E666F737472616461576946692D343034323634
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000007127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706495420010D10
                    IE: Unknown: DDA70050F204104A0001101044000102103B00010310470010BC329E001DD811B2860100664BB3E0A81021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B41505310080002210C103C0001001049000600372A000120
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Vodafone-26528627"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 0011566F6461666F6E652D3236353238363237
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR53"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 00094E4554474541523533
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B0F0A00000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B0F0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: DD2C0050F204104A0001101044000101105700010010470010565AA94967C14C0EAA8FF349E6F59311103C000103


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
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

[/etc/modprobe.d/bumblebee.conf]
blacklist nouveau
blacklist nvidia
blacklist nvidia-current
blacklist nvidia-current-updates
blacklist nvidia-304
blacklist nvidia-304-updates
blacklist nvidia-experimental-304
blacklist nvidia-310
blacklist nvidia-310-updates
blacklist nvidia-experimental-310
blacklist nvidia-313
blacklist nvidia-313-updates
blacklist nvidia-experimental-313
blacklist nvidia-319
blacklist nvidia-319-updates
blacklist nvidia-experimental-319
blacklist nvidia-325
blacklist nvidia-325-updates
blacklist nvidia-experimental-325
blacklist nvidia-331
blacklist nvidia-331-updates
blacklist nvidia-experimental-331

***** modinfo *****

filename:       /lib/modules/3.2.0-59-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     CBEDDD2D4888AAD1517D3C9
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.2.0-59-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

***** dmesg *****

```

Alex

---

### Post by chili555 on 2014-03-06
> **alexmat said:**
> Hallo,

I followed the discussion. 
Having exactly this: 
Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4: 4358] 

I reinstalled: 
sudo apt-get install - reinstall kernel-source-bcmwl 

But it does not solve anything. After a while the PC Freezing (freezes the screen and all keys are usable).
Thanks for help-me

AlexI believe that bcmwl-kernel-source is correct. However, I am not at all sure that it is causing the freezing. Let's have a look at:```
lsmod
cat  /etc/modules
dmesg | grep -i -e warn -e error
```

---

### Post by alexmat on 2014-03-06
To  Chili555

I post

```
alessandro@Aspire-5755G:~$ lsmod
Module                  Size  Used by
michael_mic            12612  4 
arc4                   12529  2 
bbswitch               13611  0 
bnep                   18281  2 
parport_pc             32866  0 
snd_hda_codec_hdmi     32530  1 
joydev                 17693  0 
snd_hda_codec_realtek   224173  1 
rfcomm                 47604  0 
bluetooth             180113  10 bnep,rfcomm
ppdev                  17113  0 
binfmt_misc            17540  1 
lib80211_crypt_tkip    17390  0 
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
wl                   3074895  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                97519  0 
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
dm_multipath           23275  0 
uvcvideo               72627  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
cfg80211              205774  1 wl
lib80211               14381  2 lib80211_crypt_tkip,wl
mei                    41616  0 
serio_raw              13211  0 
acer_wmi               28418  0 
mxm_wmi                13021  0 
sparse_keymap          13890  1 acer_wmi
mac_hid                13253  0 
wmi                    19256  2 acer_wmi,mxm_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20961  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 653116  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
vesafb                 13844  0 
i915                  478556  3 
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
tg3                   152144  0 
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
zram                   18642  1 
alessandro@Aspire-5755G:~$ 

```


```
alessandro@Aspire-5755G:~$ cat  /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
lp
rtc
lp
rtc
alessandro@Aspire-5755G:~$ 

```



```
alessandro@Aspire-5755G:~$ dmesg | grep -i -e warn -e error
[    0.844601]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    2.142495] zram: module is from the staging directory, the quality is unknown, you have been warned.
[    2.609169] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
[   28.371434] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   28.569478] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[   30.347884] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a000000, was 12060000
[   60.574652] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a0d0000, was 1a000000
[  326.457633] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 000d0000, was 1a0d0000
[  696.422273] ERROR @wl_dev_intvar_get : error (-1)
[  696.422277] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 2529.822853] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a000000, was 12060000
[ 2552.368218] unity-panel-ser[1886] general protection ip:4063bd sp:7fff8663e220 error:0 in unity-panel-service[400000+f000]
[ 2656.864446] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a0d0000, was 1a000000
[ 2715.168152] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a0d0000, was 1a000000
[ 2761.633983] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 000d0000, was 1a0d0000
[ 2774.623212] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 2774.623215] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 2774.623220] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 2774.623221] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 2774.623225] ERROR @wl_dev_intvar_get : error (-1)
[ 2774.623226] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 4317.190629] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a000000, was 12060000
[ 4401.012472] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a0d0000, was 1a000000
[ 4413.566358] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a0d0000, was 1a000000
[ 4422.829841] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 000d0000, was 1a0d0000
alessandro@Aspire-5755G:~$ 

```

Alex

---

### Post by chili555 on 2014-03-06
> [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy:Please see here: [http://ubuntuforums.org/showthread.php?t=2142892](http://ubuntuforums.org/showthread.php?t=2142892)>  My guess is you all have an Intel video card. Another hint are the words 'drm' which indicate the kernel video management subsystem. So, I think it's your videocard protesting against whatever the kernel is throwing at him.

You could try to run a more recent kernel. And this: [https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/1168467](https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/1168467)> I installed the Quantal stack that updated me to kernel 3.5.0-27-generic. This resolved the error.So it appears the freeze is a video problem. I suggest you address it first and then let's return to the wireless.

---

### Post by alexmat on 2014-03-06
Why the defect occurs only with a wireless connection? 

I have no problems with ethernet connections, or when i am not connected to the internet. 

if it is a video problem the fault should also occur at other times !

Alex

---

### Post by chili555 on 2014-03-06
> **alexmat said:**
> Why the defect occurs only with a wireless connection? 

I have no problems with ethernet connections, or when i am not connected to the internet. 

if it is a video problem the fault should also occur at other times !

AlexI haven't any idea. I'm just telling you what Google tells me. I don't know much about video. I actually have two machines that use the same video driver i915 and neither has any problem; however, neither has a Broadcom card. 

FYI:```
$ modinfo i915
filename:       /lib/modules/3.13.0-14-generic/kernel/drivers/gpu/drm/i915/i915.ko
license:        GPL and additional rights
description:    [COLOR="#FF0000"]Intel Graphics[/COLOR]

```

---

### Post by varunendra on 2014-03-06
@alexmat,

The "Blacklist" part of the script shows that you might have installed or tried to install the nvidia driver "Bumblebee", while your lsmod shows i915 and vesafb drivers. The vesafb is a fallback generic video driver that provides a 'usable' graphics when no suitable graphics drivers are found for the video card.

So, is your system the one that offers an Intel+Nvidia Hybrid crossfire graphics? If so, I have read that it is problematic in Linux.

In any case, your native Nvidia driver 'nouveau', the proprietary one proposed by default 'nvidia-current' are blacklisted, so can't load, and the one which has blacklisted them doesn't seem to be loaded either (bumblebee - I'm not sure if that is the name of the driver as well). As such, I believe you have not achieved what you wanted to achieve by installing bumblebee, and so you should sort out you graphics issues first. I don't know what that fix maybe - perhaps disable hybrid graphics and prefer only the Intel one in BIOS, or remove the blacklist file so that the native one may load (may be more problematic in case of hybrid graphics.

As a sidenote, regarding the wifi, you may wish to change the encryption type in the router to pure **WPA2-AES**. Currently it is using WPA/WPA2 mixed mode with TKIP. Avoid the mixed mode and TKIP at all costs. It may also help to _disable the N-channel in the router_ if it allows that setting (b/g-only mode). The "wl" driver can't use N-channel anyway, it only supports a/b/g modes, which means your router will (should) fall back to those modes when your this particular card is connected to it. If it doesn't do so *(as apparent from the nm-tool section, which is showing a link speed of 104 Mbps, whereas it should have been 54 Mbps or less)*, I *think* it may be problematic.

---

### Post by chili555 on 2014-03-06
Ahh! Thanks for the help, Varun. It's great to have the additional information.

Myself, I don't know which end of the video card to hit with the hammer!

---

### Post by varunendra on 2014-03-06
> **chili555 said:**
> Myself, I don't know which end of the video card to hit with the hammer!

Usually the center of the card is a good spot, but the hammer should be at least 2.5 Kg or more, from a height of no less than 1 meter, full force..

:lolflag:

---

### Post by alexmat on 2014-03-08
_To Varun_


```
So, is your system the one that offers an Intel+Nvidia Hybrid crossfire  graphics? If so, I have read that it is problematic in Linux.

In any case, your native Nvidia driver 'nouveau', the proprietary one  proposed by default 'nvidia-current' are blacklisted, so can't load, and  the one which has blacklisted them doesn't seem to be loaded either  (bumblebee - I'm not sure if that is the name of the driver as well). As  such, I believe you have not achieved what you wanted to achieve by  installing bumblebee, and so you should sort out you graphics issues  first. I don't know what that fix maybe - perhaps disable hybrid  graphics and prefer only the Intel one in BIOS, or remove the blacklist  file so that the native one may load (may be more problematic in case of  hybrid graphics.
```

Yes I have an Intel+Nvidia Hybrid crossfire  graphics.
 two days ago I started using the nvidia graphisc card (with dirver bumblebee) to load firefox. everything works fine and there are no freeze. 
I'll try a few more days, if everything is ok I will make a transition to kernel 3.5, 3.8 or 3.11. 
I'll let you know how it works .........

Alex

---

### Post by varunendra on 2014-03-08
> **alexmat said:**
> 
Yes I have an Intel+Nvidia Hybrid crossfire  graphics.
 two days ago I started using the nvidia graphisc card (with dirver bumblebee) to load firefox. everything works fine and there are no freeze.

I'll wait with curiosity to see your report/feedback, hopefully the final one. :)

In the meanwhile, can you also post the output of "lsmod" again please? Just curious to see if there is a difference now.

---

### Post by alexmat on 2014-03-09
Varun,  here my  lsmo with  nvidia
 
```
alessandro@Aspire-5755G:~$  lsmod
Module                  Size  Used by
nvidia              11334527  32 
michael_mic            12612  4 
arc4                   12529  2 
bbswitch               13611  0 
snd_hda_codec_hdmi     32530  1 
bnep                   18281  2 
joydev                 17693  0 
snd_hda_codec_realtek   224173  1 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bluetooth             180113  10 bnep,rfcomm
binfmt_misc            17540  1 
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip    17390  0 
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   3074895  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              205774  1 wl
psmouse                97519  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
serio_raw              13211  0 
dm_multipath           23275  0 
mei                    41616  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
v4l2_compat_ioctl32    17128  1 videodev
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
mxm_wmi                13021  0 
mac_hid                13253  0 
wmi                    19256  2 acer_wmi,mxm_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20961  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 653116  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
vesafb                 13844  0 
i915                  478556  3 
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
tg3                   152144  0 
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
zram                   18642  1 
alessandro@Aspire-5755G:~$ 

```

---

### Post by varunendra on 2014-03-09
Yup, the "difference" is on the top!

Hope it remains stable, which would remove another doubt I have about that "mxm_wmi" driver.

Thank you for taking time to provide us your feedback, it's very much appreciated. :)

---

### Post by alexmat on 2014-03-10
now  i changed  kernel  i  have 3.8.0-37-generic kernel. 
i post the   desmeg  output :

```
dmesg | grep -i -e warn -e error
[    1.689549] zram: module is from the staging directory, the quality is unknown, you have been warned.
[   30.201635] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[   30.392531] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   30.392544] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   30.392548] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20121018/utaddress-251)
[   30.392554] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   30.392557] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20121018/utaddress-251)
[   30.392562] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   30.392565] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20121018/utaddress-251)
```

as you can see is different from the previous one (kernel 3.2). 

Now I will test the connection wi.fi ........ 

I'll give you information

Alex ):P

---

### Post by wepbep on 2014-03-28
> **chili555 said:**
> Perfect!

With a temporary ethernet connection, please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```After it's done, do:```
sudo modprobe wl
```If there is no error or warning, your wireless should be working.

[I][SIZE=4]Thank you so much !!! :D[FONT=Arial][FONT=Arial Black][FONT=Verdana][FONT=Arial Black]

Acer Aspire R7-571-53336G50ass and Ubuntu 14.04 beta[/FONT][/FONT][/FONT][/FONT]
[/SIZE][/I]

---

### Post by taha2 on 2014-04-25
Hi,
i have recently installed Ubuntu, i have the same device and the same Hardware, when i tried the two instructions, i received two error :


> **chili555 said:**
>  please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```

for This i have received the error : [COLOR=#ff0000]**Package bcmwl-kernel-source can **[/COLOR][COLOR=#ff0000]**not be found**[/COLOR].

> **chili555 said:**
>  After it's done, do:```
sudo modprobe wl
```If there is no error or warning, your wireless should be working.

for This i have received the error : [COLOR=#ff0000]**E: Module wl not found.**[/COLOR][COLOR=#ff0000][/COLOR]

Thank you for the help.

---

### Post by chili555 on 2014-04-25
> for This i have received the error : Package bcmwl-kernel-source can not be found.Are you hooked to the internet so the package can be found and downloaded? Have you built an index of available packages?```
sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source
```

---

### Post by Christopher_Turner on 2014-10-04
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)

also worked perfectly with ubuntu 14.04 and the above pci.id on an Acer Aspire E15 ES-511-C619

---

### Post by maryam3 on 2015-03-04
hi. i installed ubuntu14 for the first time, i have the same problem with Acer 5750, i did as you said
but got error :roll::-?

sudo apt-get install --reinstall bcmwl-kernel-source
E: unable to locate package bcmwl-kernel-source

---

### Post by jeremy31 on 2015-03-04
> **maryam3 said:**
> hi. i installed ubuntu14 for the first time, i have the same problem with Acer 5750, i did as you said
but got error :roll::-?

sudo apt-get install --reinstall bcmwl-kernel-source
E: unable to locate package bcmwl-kernel-source

If you still have the DVD/USB that you installed Ubuntu from, you can find bcmwl-kernel-source on it in /pool/restricted/b/bcmwl/

---

### Post by kartheek3 on 2015-03-07
same problem.. acer aspire one 756

03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
im using ubuntu 12.04 lts

---

### Post by chili555 on 2015-03-07
> **kartheek3 said:**
> same problem.. acer aspire one 756

03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
im using ubuntu 12.04 ltsWhich problem? It's hard to figure out in a thread that's 205 posts and 2 1/2 years old. Please start your own new thread and include the information from the wireless_script in the sticky at the top of the forum. I'll be glad to help.

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by rahul_gawade on 2015-07-06
Hi Chill555 , 
this commands not working for me . Here is what i am getting,

02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

plzplz help

---

### Post by chili555 on 2015-07-06
> **rahul_gawade said:**
> Hi Chill555 , 
this commands not working for me . Here is what i am getting,

02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

plzplz helpPlease see the post right above yours.

---

### Post by rahul_gawade on 2015-07-06
worked thanks , but now i am getting new error while opening Ubantu Software Center or Update manager . 
PFB image,
[http://tinypic.com/r/eiqzyw/8](http://tinypic.com/r/eiqzyw/8)    
 (FYI i tried installing Google chrome stable package before this happen)
Please help.

---

### Post by chili555 on 2015-07-06
> **rahul_gawade said:**
> worked thanks , but now i am getting new error while opening Ubantu Software Center or Update manager . 
PFB image,
[http://tinypic.com/r/eiqzyw/8](http://tinypic.com/r/eiqzyw/8)    
 (FYI i tried installing Google chrome stable package before this happen)
Please help.That's a question for General Help, please: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by Raj_Nayan on 2015-12-24
i got this after doing the steps u asked for, what should i do now?

modprobe: FATAL: Module wl not found.

---

### Post by huy5 on 2016-02-19
Hi. 
Please help on wireless card 14e4.4315

thank you.
huy

---

### Post by chili555 on 2016-02-19
> **huy5 said:**
> Hi. 
Please help on wireless card 14e4.4315

thank you.
huyPlease check here: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by tmittelstaedt on 2016-03-19
Please refer to the following:

[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

---

### Post by jeremy31 on 2016-03-19
> **tmittelstaedt said:**
> Please refer to the following:

[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)
You do realize that answer is based on info from chili555

---

