---
title: "Wireless problems"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by brick2 on 2013-07-08
I m truly sorry to bother you again with pretty much the same problem, but it would seam that when I create a virtual machine using virtualbox I somehow mess up my wirelss. Could you pleae help me.

This is What I have done so far:

Dell laptop

Ubuntu 12.4

Device: 08:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)


**ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:26:b9:ed:cf:3a  
          inet addr:77.77.237.161  Bcast:77.77.239.255  Mask:255.255.252.0
          inet6 addr: fe80::226:b9ff:feed:cf3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5420276 (5.4 MB)  TX bytes:345175 (345.1 KB)

eth2      Link encap:Ethernet  HWaddr 78:e4:00:b3:88:3d  
          inet6 addr: fe80::7ae4:ff:feb3:883d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33294 (33.2 KB)  TX bytes:33294 (33.2 KB)


 **sudo apt-get install linux-headers-generic bcmwl-kernel-source **
Nothing new was installed

**iwconfig**

eth0      no wireless extensions.

eth2      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


**rfkill list all**

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**dmesg | grep wl**

[    7.865640] wl: module license 'MIXED/Proprietary' taints kernel.
[    7.902935] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[    8.581292] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[    9.135778] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   29.128161] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   40.208825] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   40.208998] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   60.116390] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   90.104041] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  130.084733] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  180.065668] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  240.040893] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  300.013209] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  359.989691] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  419.964536] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  479.939019] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  504.228489] ERROR @wl_dev_intvar_get : error (-1)
[  504.228495] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  539.913693] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)

[B]sudo apt-get update sudo apt-get -y upgrade sudo apt-get install --reinstall bcmwl-kernel-source


[/B]
**dmesg | grep wl**

[    7.865640] wl: module license 'MIXED/Proprietary' taints kernel.
[    7.902935] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[    8.581292] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[    9.135778] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   29.128161] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   40.208825] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   40.208998] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   60.116390] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   90.104041] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  130.084733] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  180.065668] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  240.040893] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  300.013209] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  359.989691] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  419.964536] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  479.939019] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  504.228489] ERROR @wl_dev_intvar_get : error (-1)
[  504.228495] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  539.913693] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  599.888161] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  659.862461] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  719.837360] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)


[B]sudo apt-get purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer


[/B]As opposed to before this didnt fix it now.

Thank you for your time.

---

### Post by wildmanne39 on 2013-07-08
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

This is on the host machine right? because the guest internet works off of the hosts connection.
Thanks

---

### Post by brick2 on 2013-07-08
Yes is it a host machine

---

### Post by brick2 on 2013-07-08
I m sorry I did not know how to do exatly what you wanted me to do in terms of a tar to zip but it s only 9kb.

---

### Post by wildmanne39 on 2013-07-08
It looks like an update probably broke your wireless, let's try the b43 and if it does not connect post the wireless script again for that driver but b43 is usually solid.
```
sudo apt-get purge --remove bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Make sure that wireless in network manager is enabled and unplug your wired connection.
Thanks

---

### Post by brick2 on 2013-07-08
It changed nothing, as I ran both commands the output was simply that nothing new was removed or installed.

---

### Post by wildmanne39 on 2013-07-08
The first command should have removed the wl driver and the second installed b43 driver and firmware.

What happens when you do:
```
sudo modprobe -r wl
sudo modprobe b43
```
Thanks

---

### Post by brick2 on 2013-07-08
It was very wierd to me as well it didnt find anything to remove but than it didnt install anything new because it was arleady installed, or that is the way I see it anyway.

Here is one to cheer you up:

A dying man says to the doctor: "Could you please write down in the death certificat that I died of AIDS"
Doctor: Why on earth would you wish me to do that?
Dying man: So that noone would have sex with my wife after I die, and so that those who already did would be terrified.


**sudo modprobe b43**
FATAL: Module wl not found.

**sudo modprobe b43**
No output was given.

---

### Post by wildmanne39 on 2013-07-08
Run the purge command and the install for the b43 again, please copy and paste the commands for accurracy, then post all the output here using code tags.
Thanks

---

### Post by brick2 on 2013-07-08
[B]sudo apt-get purge --remove bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
[/B]
```
mmon broadcom-sta-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package broadcom-sta-common is not installed, so not removed
Package broadcom-sta-source is not installed, so not removed
Package bcmwl-kernel-source is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-23-generic linux-headers-3.5.0-23
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

[B]sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer

[/B]
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-lpphy-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-23-generic linux-headers-3.5.0-23
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by wildmanne39 on 2013-07-08
Please post the output of: ```
lsmod 
```
Thanks

---

### Post by brick2 on 2013-07-08
[B]lsmod

[/B]> b43                   379088  0 
mac80211              555272  1 b43
ssb                    53131  1 b43
bcma                   35762  1 b43
pci_stub               12623  1 
vboxpci                23237  0 
vboxnetadp             13383  0 
vboxnetflt             23479  0 
vboxdrv               287105  4 vboxpci,vboxnetadp,vboxnetflt
snd_hda_codec_hdmi     32476  1 
parport_pc             32867  0 
ppdev                  17114  0 
rfcomm                 47562  0 
bnep                   18240  2 
bluetooth             211812  10 rfcomm,bnep
coretemp               13642  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
joydev                 17694  0 
hid_generic            12541  0 
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
dell_wmi               12682  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
sparse_keymap          13891  1 dell_wmi
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
snd_hda_codec_idt      70774  1 
microcode              23030  0 
lib80211_crypt_tkip    17391  0 
snd_seq_midi           13325  0 
snd_hda_intel          34063  8 
snd_rawmidi            30750  1 snd_seq_midi
intel_ips              18332  0 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse               102506  0 
serio_raw              13216  0 
snd_seq_midi_event     14900  1 snd_seq_midi
i7core_edac            23910  0 
edac_core              53053  1 i7core_edac
radeon                917823  3 
wl                   3074942  0 
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
lpc_ich                17145  0 
snd_timer              29990  2 snd_pcm,snd_seq
ttm                    88495  1 radeon
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              208382  3 b43,mac80211,wl
drm_kms_helper         49259  1 radeon
lib80211               14382  2 lib80211_crypt_tkip,wl
snd                    83674  24 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_rawmidi,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
drm                   290595  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13565  1 radeon
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
wmi                    19257  1 dell_wmi
video                  19653  0 
mac_hid                13254  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
r8169                  62705  0 
ahci                   25869  4 
libahci                27338  1 ahci

---

### Post by wildmanne39 on 2013-07-08
Both drivers are loaded so let's try this one more time:
```
sudo modprobe -rfv wl
sudo modprobe -v b43
```
Thanks

---

### Post by brick2 on 2013-07-08
**sudo modprobe -rfv wl**
FATAL: Module wl not found.

 **sudo modprobe -v b43**
No output not even with -v.

---

### Post by brick2 on 2013-07-08
Ok perhaps there is another thing my virtualbox is up and running I do not know does that make any diffrence to you.

---

### Post by wildmanne39 on 2013-07-08
Please post the output of:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e eht1 -e etwork | tail -n45
```
It should not matter but go ahead and shut it down.

Did you change any settings in your hosts wireless settings?
How did you install the wl driver?
Thanks

---

### Post by brick2 on 2013-07-08
No I changed noting.
Installed the drivers via additional drivers.[B]





sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e eht1 -e etwork | tail -n45

```
[/B]Jul  8 23:40:04 brick NetworkManager[961]: <info> WiFi now enabled by radio killswitch
Jul  8 23:40:04 brick NetworkManager[961]: <info> (eth2): bringing up device.
Jul  8 23:40:04 brick NetworkManager[961]: <info> (eth2): supplicant interface state: starting -> ready
Jul  8 23:40:04 brick NetworkManager[961]: <info> (eth2): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul  8 23:40:04 brick NetworkManager[961]: <info> (eth2): supplicant interface state: ready -> inactive
Jul  8 23:40:04 brick NetworkManager[961]: <warn> Trying to remove a non-existant call id.
Jul  8 23:48:12 brick NetworkManager[961]: <info> (eth2): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
Jul  8 23:48:12 brick NetworkManager[961]: <info> (eth2): deactivating device (reason 'none') [0]
Jul  8 23:48:12 brick NetworkManager[961]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jul  8 23:48:12 brick NetworkManager[961]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jul  8 23:48:12 brick NetworkManager[961]: <info> (eth2): taking down device.
Jul  8 23:48:12 brick NetworkManager[961]: <info> WiFi hardware radio set disabled
Jul  8 23:48:12 brick NetworkManager[961]: <info> WiFi now disabled by radio killswitch
Jul  8 23:48:13 brick NetworkManager[961]: <info> (eth2): bringing up device.
Jul  8 23:48:13 brick NetworkManager[961]: <info> WiFi hardware radio set enabled
Jul  8 23:48:13 brick NetworkManager[961]: <info> WiFi now enabled by radio killswitch
Jul  8 23:48:13 brick NetworkManager[961]: <info> (eth2): bringing up device.
Jul  8 23:48:14 brick NetworkManager[961]: <info> (eth2): supplicant interface state: starting -> ready
Jul  8 23:48:14 brick NetworkManager[961]: <info> (eth2): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul  8 23:48:14 brick NetworkManager[961]: <info> (eth2): supplicant interface state: ready -> inactive
Jul  8 23:48:14 brick NetworkManager[961]: <warn> Trying to remove a non-existant call id.
Jul  8 23:50:04 brick NetworkManager[961]: <info> (eth0): DHCPv4 state changed reboot -> renew
Jul  8 23:50:04 brick NetworkManager[961]: <info>   address 77.77.237.161
Jul  8 23:50:04 brick NetworkManager[961]: <info>   prefix 22 (255.255.252.0)
Jul  8 23:50:04 brick NetworkManager[961]: <info>   gateway 77.77.236.1
Jul  8 23:50:04 brick NetworkManager[961]: <info>   hostname 'brick'
Jul  8 23:50:04 brick NetworkManager[961]: <info>   nameserver '77.77.192.10'
Jul  8 23:50:04 brick NetworkManager[961]: <info>   nameserver '77.78.192.10'
Jul  8 23:50:04 brick NetworkManager[961]: <info>   nameserver '94.140.66.194'
Jul  8 23:50:04 brick NetworkManager[961]: <info>   domain name 'telemach.ba'
Jul  9 00:09:23 brick NetworkManager[961]: <info> (eth2): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
Jul  9 00:09:23 brick NetworkManager[961]: <info> (eth2): deactivating device (reason 'none') [0]
Jul  9 00:09:23 brick NetworkManager[961]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jul  9 00:09:23 brick NetworkManager[961]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jul  9 00:09:23 brick NetworkManager[961]: <info> (eth2): taking down device.
Jul  9 00:09:23 brick NetworkManager[961]: <info> WiFi hardware radio set disabled
Jul  9 00:09:23 brick NetworkManager[961]: <info> WiFi now disabled by radio killswitch
Jul  9 00:09:24 brick NetworkManager[961]: <info> (eth2): bringing up device.
Jul  9 00:09:24 brick NetworkManager[961]: <info> WiFi hardware radio set enabled
Jul  9 00:09:24 brick NetworkManager[961]: <info> WiFi now enabled by radio killswitch
Jul  9 00:09:24 brick NetworkManager[961]: <info> (eth2): bringing up device.
Jul  9 00:09:24 brick NetworkManager[961]: <info> (eth2): supplicant interface state: starting -> ready
Jul  9 00:09:24 brick NetworkManager[961]: <info> (eth2): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul  9 00:09:24 brick NetworkManager[961]: <info> (eth2): supplicant interface state: ready -> inactive
Jul  9 00:09:24 brick NetworkManager[961]: <warn> Trying to remove a non-existant call id.
```

---

### Post by wildmanne39 on 2013-07-08
There was actually a lot of change in the error messages.

Please run the wireless script again so we can see everything that is going on using the b43 driver.

Please do not reboot because that will most likely make the wl driver load again.

This > <warn> Trying to remove a non-existant call idlooks like a bug in network manager.
Thanks

---

### Post by brick2 on 2013-07-08
[B]wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script

  
[/B]

---

### Post by brick2 on 2013-07-08
Ok jsut another thing, I did mess around with an openssh-server a bit as well if that makes a diffrence to you but I dont think I ve done anything of any importance.

---

### Post by wildmanne39 on 2013-07-08
Please delete all the wireless-info.txt files in your home folder I believe you are posting the same file and not a new one.

Look and see if there was a tar file created for wireless one will be automatically created when it is to large to attach to the forum and I think it should have been to large.
Thanks

---

### Post by brick2 on 2013-07-08
i delete it every time and wait for a new one to be created and that is the one I post but hold on let me chek

---

### Post by brick2 on 2013-07-08
ok how about now.

---

### Post by wildmanne39 on 2013-07-08
Both drivers are loaded, please do:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf
 sudo modprobe -rfv wl
 sudo modprobe -rfv b43
 sudo modprobe -v b43
```
Thanks

---

### Post by brick2 on 2013-07-08
**echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf**
blacklist wl

**sudo modprobe -rfv wl**
FATAL: Module wl not found.


**sudo modprobe -rfv b43**

```
rmmod /lib/modules/3.5.0-36-generic/kernel/drivers/net/wireless/b43/b43.ko
rmmod /lib/modules/3.5.0-36-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.5.0-36-generic/kernel/drivers/ssb/ssb.ko
rmmod /lib/modules/3.5.0-36-generic/kernel/drivers/bcma/bcma.ko
```

**sudo modprobe -v b43**

```
insmod /lib/modules/3.5.0-36-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.5.0-36-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.5.0-36-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-36-generic/kernel/drivers/net/wireless/b43/b43.ko
```

---

### Post by brick2 on 2013-07-08
It is very likly that I shall have to reinstall it all.

---

### Post by wildmanne39 on 2013-07-08
I think network manager is the issue as long as we use the b43 driver, the wl driver also has an issue, that happens with updates sometimes.

You can see if there is an update to network manager or install an older version.

Or install wicd and remove network manager.
Thanks

---

### Post by brick2 on 2013-07-08
Well I thank you for all your time and effort in any case.

---

### Post by wildmanne39 on 2013-07-08
If you want to try wicd install it using software center then use these commands to remove network manger but it has to be done in this order.
```
sudo apt-get purge network-manager network-manager-gnome
```

Wicd does not put a notification in the top panel.
Thanks

---

### Post by brick2 on 2013-07-09
Yes this seams to have solved the problem and I thank you trully for all your effort.

I m just wondering what could be the cause of the problem, as this seams to happen every once in a while. I reinstall Ubuntu and thanh somethimes everything is ok somethimes minor fixes are required and sometimes something like this happens. The strange thing is that all of this is happening on the same machine and I install it from the same CD. The installation procedure is fairly simple and is prety much aways the same and I m always conected to the internet while im doing it. If you could shed some ligh on this matter thank you if not o well I m just glad the problem was fixed.

---

### Post by wildmanne39 on 2013-07-09
When you installed updates an update to the wl driver and network manager it broke your wireless.

You could have downgraded or upgraded just those packages and fixed it I believe.

I suggest you lock those two packages so they can not be updated, I am not sure how you do it if you are only using software center but google should tell you.

I myself use synaptic and it is very easy using it to lock a package.
Thanks

---

