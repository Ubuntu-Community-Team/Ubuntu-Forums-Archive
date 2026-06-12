---
title: "Really slow wireless internet on ubuntu 11.10"
date: 2011-11-07
forum: Networking &amp; Wireless
---

### Post by bjarnovikus on 2011-11-07
Hello whoever this reads,

A few days ago I installed Ubuntu 11.10 trough the wubi installer (I didn't feel well to partition my laptop so it seemed to be a good solution). However it seems that my internet connection is terrible slow:

[[IMG]http://www.speedtest.net/result/1578725594.png[/IMG]]("http://www.speedtest.net")

On windows I got a really fast internet connection and it is the same laptop, so the same hardware.

I tried to fix it by googling my problem, but when I rebooted my computer this time, my internet connection was painfull slow (see above) and I lost track of every page.

I don't know where to start, so I'm going to give some basic information:

```
bjarno@ubuntu: sudo iwconfig
[sudo] password for bjarno:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"xxxxxxxxxxxxx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1947  Invalid misc:335   Missed beacon:0


```If I need to enter more information please tell me...

(sorry for any bad English structure, most of the time I'm talking in Dutch ;) )

Thanks,
Bjarnovikus

---

### Post by wildmanne39 on 2011-11-07
Hi, please post the results of:
```
lspci -nnk | grep -iA2 net
```
```
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by bjarnovikus on 2011-11-07
lspci -nnk | grep -iA2 net gives me the following:

```
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave Device [1a3b:1089]
    Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1820]
    Kernel driver in use: atl1c

```

lsmod gives me the following:
```
Module                  Size  Used by
nls_iso8859_1          12713  2 
nls_cp437              16991  2 
vfat                   17585  2 
fat                    61475  1 vfat
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
vesafb                 13809  1 
joydev                 17693  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
snd_hda_intel          33390  7 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72711  1 
videodev               93004  2 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi           13324  0 
psmouse                73882  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
serio_raw              13166  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ath9k                 127538  0 
fglrx                2929009  276 
mac80211              310872  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312866  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              199587  3 ath9k,mac80211,ath
video                  19412  0 
snd                    68266  22 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_laptop            19722  0 
sparse_keymap          13890  1 asus_laptop
mei                    41480  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
usb_storage            57901  2 
uas                    18027  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  1 
libahci                26861  1 ahci
atl1c                  41643  0 

```

---

### Post by wildmanne39 on 2011-11-07
Hi, you can try this please:
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```
Run the commands one at a time and do not restart your computer, if this works we will need to make it permanent.

Also those wireless card's usually do not have good signal strength in linux so try not to get to far from your router.
Thank you

---

### Post by bjarnovikus on 2011-11-07
```
root@ubuntu:~# ifconfig wlan0 down
root@ubuntu:~# rmmod -f ath9k
root@ubuntu:~# sudo modprobe ath9k nohwcrypt=1
WARNING: All config files need .conf: /etc/modprobe.d/bad_list, it will be ignored in a future release.
root@ubuntu:~# ifconfig wlan0 up
root@ubuntu:~# 


```

Executed the commands above and this was the result (one warning, is this a problem?). (I executed "sudo -s" for a root ;) ).

It worked, now my connection speed is A LOT faster.

[[IMG]http://www.speedtest.net/result/1578879651.png[/IMG]](http://www.speedtest.net)

But what precisily did these commands do, I understand the first one and the last one but the other two are one mystery for me.

How to make this permanent?

---

### Post by wildmanne39 on 2011-11-07
Hi, it added a parameter to your driver which switched encryption from hardware to software.

Let's make it permanent:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Add a single line:
```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit then Reboot.

Would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by sparticus2311 on 2011-11-13
Helped me out too, thanks!

---

### Post by wildmanne39 on 2011-11-13
Hi, your welcome!
Enjoy

---

### Post by Hausi on 2011-11-14
Hi, could this be a bug? I have the same situation in 2 laptops. One has an Intel WiFi Link 1000 and the other one an Intel 3945. Unloading/loading the module gives me something like factor 10 of improvement.
Q: can I use this solution (hwcrypt) for the Intel HW too?
thanks _Hans

---

### Post by konstant100 on 2011-12-18
> **wildmanne39 said:**
> Hi, it added a parameter to your driver which switched encryption from hardware to software.

Let's make it permanent:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Add a single line:
```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit then Reboot.

Would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

Hi guys,
I so hoped it would help me too, but my Terminal said it can not find ath9k file/directory on my Sony Vaio VGN-FW180D, when i wanted to apply wildmanne39's code. Could you please help me with this one. I am just new to Ubuntu. It is my first day. Many thanks in advance.:)

---

### Post by wildmanne39 on 2011-12-18
Hi, please post the results of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by konstant100 on 2011-12-18
Hi guys,
I so hoped it would help me too, but my Terminal said it can not find ath9k file/directory on my Sony Vaio VGN-FW180D, when i wanted to apply wildmanne39's code. Could you please help me with this one. I am just new to Ubuntu. It is my first day. Many thanks in advance.

---

### Post by konstant100 on 2011-12-18
Hi guys,
I so hoped it would help me too, but my Terminal said it can not find ath9k file/directory on my Sony Vaio VGN-FW180D, when i wanted to apply wildmanne39's code. Could you please help me with this one. I am just new to Ubuntu. It is my first day. Many thanks in advance.

---

### Post by wildmanne39 on 2011-12-18
Hi, welcome to the forum please read my previous post and do what it says, also please do not post for help more then once in a 24 hour period give people time to answer you.
Thank you

---

### Post by konstant100 on 2011-12-18
Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:B0:BA:43:B9   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5372  Invalid misc:221   Missed beacon:0



0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by konstant100 on 2011-12-18
Module                  Size  Used by
rfcomm                 38408  8 
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          28358  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
snd_timer              28932  2 snd_pcm,snd_seq
uvcvideo               67271  0 
usbhid                 41905  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
hid                    77367  1 usbhid
videodev               85626  1 uvcvideo
radeon                961834  4 
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlagn                273937  0 
ttm                    65224  1 radeon
joydev                 17393  0 
drm_kms_helper         32889  1 radeon
soundcore              12600  1 snd
mac80211              393459  1 iwlagn
drm                   196290  6 radeon,ttm,drm_kms_helper
cfg80211              172392  2 iwlagn,mac80211
btusb                  18160  2 
psmouse                63474  0 
bluetooth             148839  23 rfcomm,bnep,btusb
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
r592                   17808  0 
memstick               15857  1 r592
i2c_algo_bit           13199  1 radeon
serio_raw              12990  0 
sony_laptop            39681  0 
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  0 
uas                    17699  0 
firewire_ohci          35846  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ahci                   21634  2 
libahci                25761  1 ahci
sky2                   49304  0 
konstant@konstant-VGN-FW180D:~$

---

### Post by wildmanne39 on 2011-12-18
Hi, please do the following.
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```
Add a single line:
```
options iwlagn nohwcrypt=1
```
Proofread carefully, save and close gedit then Reboot.
Thank you

---

### Post by konstant100 on 2011-12-18
After restart I can not connect to network at all

---

### Post by wildmanne39 on 2011-12-18
Hi, open the file back up and remove:
```
options iwlagn nohwcrypt=1
```
and add
```
options iwlagn 11n_disable=1
```
poofread and save.

Then unplug wired connection and reboot.
Thank you

---

### Post by konstant100 on 2011-12-18
After saving I always get same message:(gedit:3550):Gtk-WARNING**:Attempting to set the permissions of '/root/.local/share/recently-used.xbel', but failed: No such file or directory

I made changes you asked, no change. Still can not get wireless.

---

### Post by konstant100 on 2011-12-18
Hold on sec, may be I was screwed up with 11 instead of ll

---

### Post by wildmanne39 on 2011-12-18
Hi, you will need to create the directory it tells you too.
```
mkdir /root/.local/share
```
then try the commands again.
Thanks

---

### Post by konstant100 on 2011-12-18
No, all is right, but same results. No wireless

---

### Post by wildmanne39 on 2011-12-18
Hi, did you follow the directions in post 22 yet?
Thanks

---

### Post by konstant100 on 2011-12-18
...permission denied

---

### Post by wildmanne39 on 2011-12-18
HI, my fault, you need to add sudo in front of the command like this.
```
sudo mkdir /root/.local/share
```
Thanks

---

### Post by konstant100 on 2011-12-18
It is asking for password .....?

---

### Post by wildmanne39 on 2011-12-18
Hi, I now enter your user password then open the file and delete that one line and add the other one as stated in the earlier post.
Thanks

---

### Post by konstant100 on 2011-12-18
I removed password before that but system keeps asking me for one. Even though I enter the old one or just nothing, it does not accept

---

### Post by wildmanne39 on 2011-12-18
Hi, how do you login?
Thanks

---

### Post by konstant100 on 2011-12-18
Doing just nothing . I removed password. But when I try to open the file to modify it back, system askin for password.

---

### Post by konstant100 on 2011-12-18
May be there is some default pw like Admin or so?

---

### Post by wildmanne39 on 2011-12-18
Nope just the password you created.

When you type your password it will not show on the screen and if it is right it will just perform the command.

How do you login?

---

### Post by konstant100 on 2011-12-18
I log in without any password

---

### Post by wildmanne39 on 2011-12-18
Hi, how do you install updates then?

---

### Post by konstant100 on 2011-12-18
2 hours ago I used my regular password. Then, during this chat, I removed the password from my account . But the system keeps asking for one. I tried to use the old one but it does not work anymore

---

### Post by wildmanne39 on 2011-12-18
Hi, you will need to create new password without it you will not be able to install updates or anything else that requires a password and when you reboot you might run into trouble, is there any chance your cap locks are on?
Thanks

---

### Post by konstant100 on 2011-12-18
I am reinstalling ubuntu now. 75 % already done. It seems to be fastest way to fix wifi access. Then, let's trty to fix the speed again . Are u ok with it? Thanks a lot

---

### Post by konstant100 on 2011-12-18
I checked all cap locks etc I have no clue what a hek iit is ...!

---

### Post by wildmanne39 on 2011-12-18
Hi, however you want to do it but this would have been quicker.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Thanks

---

### Post by wildmanne39 on 2011-12-18
Hi, I am pretty sure it is just because you removed your password, that is not recommended it makes your system unsecure and as you can see causes other issues as well.
Thanks

---

### Post by konstant100 on 2011-12-18
No argue, but is it going to be always like that frisking me out asiking for password whatever I want to do? Because It is kind of annoying. That is why I cancelled it.

---

### Post by wildmanne39 on 2011-12-18
Hi, when you install something or do something that requires elevated privileges it will, that is what makes ubuntu safe, even windows 7 learned from ubuntu and requires passwords to install programs, it is for your safety.

The issue really is that it takes getting use too just like you had to learn windows you have to learn how ubuntu works and why.
Thanks

---

### Post by konstant100 on 2011-12-18
I see. If it is the worst issue for Ubuntu, it is ok.
...several more minutes left to complete reinstall. I choose that mode which reinstall leaving previous system configuration. That is why it takes so long.

---

### Post by wildmanne39 on 2011-12-18
Hi, I believe that will leave you with the same problem of the password and wireless, you needed to do a clean install and get rid of the configuration files, but you can also use the link I gave you to reset your password.
Thanks

---

### Post by konstant100 on 2011-12-18
Thanks for the attempt, I will try

---

### Post by wildmanne39 on 2011-12-18
Hi, did you have the same problem with password after you reinstalled?
Thanks

---

### Post by konstant100 on 2011-12-18
Now password works well. Where should I start now?

---

### Post by wildmanne39 on 2011-12-18
Hi, start at post 19.

Is your wireless working?
Thanks

---

### Post by konstant100 on 2011-12-18
Yes but very slow

---

### Post by konstant100 on 2011-12-18
I managed to create directory and the file but:

(gedit:2232): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to rename file '/root/.local/share/recently-used.xbel.L8J75V' to '/root/.local/share/recently-used.xbel': g_rename() failed: Is a directory

(gedit:2232): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to rename file '/root/.local/share/recently-used.xbel.NXPI6V' to '/root/.local/share/recently-used.xbel': g_rename() failed: Is a directory

---

### Post by wildmanne39 on 2011-12-18
Hi, did you try what was in post 26? Then tried the previous command again?
Thanks

---

### Post by konstant100 on 2011-12-18
Yes, I created the dir. Then tried 17 ,then 19, but got 51

---

### Post by wildmanne39 on 2011-12-18
Hi, that must be an issue with installing over the old ubuntu, and I am not sure how to fix it, I will have to take a little while to see if I can find an answer.
Thanks

---

### Post by konstant100 on 2011-12-18
Hey, we did it man! I cleaned all after creating the dir, went thru 17 and 19 again and it is just perfect now! Thank s for your support .

---

### Post by wildmanne39 on 2011-12-18
Hi, your welcome!!! I knew it should that is why I was over here scratching my head.

---

### Post by am3 on 2011-12-27
Hi, I'm new guy using ubuntu 11.10

I have problems with slow internet, i had windows on the same laptop (inspiron) and internet speed was pretty ok, but now i must 'wait' for some pages (with pictures, videos and so on) and it's obvious that is slower than before.

I'm reading first post and I don't know how to post any informations about system (what codes I should type in Terminal) ...

---

### Post by am3 on 2011-12-27
I forgot to mention ...  it's about wireless connection on dell inspiron n5010 (ubuntu 11.10)

---

### Post by wildmanne39 on 2011-12-27
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by am3 on 2011-12-27
first command:
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux marin-Inspiron-N5010 3.0.0-14-generic-pae #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 i686 i686 i386 GNU/Linux
marin@marin-Inspiron-N5010:~$ ^C



```

second:
```
12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell XPS 8300 [1028:0010]
    Kernel driver in use: brcmsmac
--
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:0447]
    Kernel driver in use: r8169


```

third:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Roud68"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:04:8A:E0:60   
          Bit Rate=54 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2859   Missed beacon:0

```

fourth:

```
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

fifith:
```
Module                  Size  Used by
rfcomm                 38408  8 
bnep                   17923  2 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251973  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
wl                   2646601  0 
snd_hda_codec_hdmi     31426  1 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
binfmt_misc            17292  1 
snd_hda_codec_idt      60049  1 
uvcvideo               67271  0 
snd_hda_intel          28358  3 
videodev               85626  1 uvcvideo
btusb                  18160  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
bluetooth             148839  23 rfcomm,bnep,btusb
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              393459  1 brcmsmac
mei                    36466  0 
joydev                 17393  0 
fglrx                2756852  123 
cfg80211              172392  2 brcmsmac,mac80211
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
crc_ccitt              12595  1 brcmsmac
wmi                    18744  1 dell_wmi
psmouse                63474  0 
serio_raw              12990  0 
dell_laptop            13519  0 
video                  18908  0 
dcdbas                 14098  1 dell_laptop
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  2 
libahci                25761  1 ahci
r8169                  47200  0 

```

---

### Post by wildmanne39 on 2011-12-27
Hi, I just want to make sure it is your wireless that is slow the same as the topic of this thread?
Thanks

---

### Post by blakm43 on 2011-12-29
1.  marc@blakm43:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux blakm43 3.0.0-15-generic #24-Ubuntu SMP Mon Dec 12 15:25:25 UTC 2011 i686 i686 i386 GNU/Linux


2.  marc@blakm43:~$ lspci -nnk | grep -iA2 net
02:04.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7094]
	Kernel driver in use: ath5k
--
02:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: 8139too


3.   marc@blakm43:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"06B402781151"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:0E:33:05:C0   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:113   Missed beacon:0

4.  marc@blakm43:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
marc@blakm43:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
arc4                   12473  2 
joydev                 17393  0 
snd_hda_codec_realtek   254125  1 
snd_hda_codec_si3054    12864  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
rfcomm                 38408  0 
snd_pcm                80435  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
bluetooth             148839  10 bnep,rfcomm
radeon                925178  2 
ath5k                 145100  0 
ath                    19387  1 ath5k
mac80211              393459  1 ath5k
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39822  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
cfg80211              172427  3 ath5k,ath,mac80211
drm                   192194  4 radeon,ttm,drm_kms_helper
psmouse                73673  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd                    55902  14 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 radeon
binfmt_misc            17292  1 
i2c_piix4              13093  0 
shpchp                 32356  0 
ati_agp                13242  0 
sparse_keymap          13658  0 
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
8139too                23283  0 
8139cp                 22636  0 
pata_atiixp            12967  0 
sata_sil               13278  2

---

### Post by wildmanne39 on 2011-12-29
Hi blakm43, please run the following commands one at a time and do not restart your computer this is for this boot only if it works we will need to make it permanent.
```
sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up

```
Thanks

---

### Post by optima4 on 2011-12-29
Wow, this is a good thread, and thank you wildmanne39 for such excellent support. 

I have a similar question and I hate to ask because there are so many asking these very similar questions, but I need help and I can't seem to figure out how to make it better.

I am using Ubuntu 11.10 on a Gateway LT-27 netbook right now, and if I open a page from google I keep getting, "Page Not Loading". Everyday this happens and the internet is very slow, very frustrating. I also run Windows 7 on a virtual machine and the internet works perfectly every time. We also use wireless. I ran this code 

[SIZE=1][/SIZE]*pics removed for safety*


**cat /etc/lsb-release; uname -a**

AND

**lspci -nnk | grep -iA@ net**

AND 

**iwconfig**

results




**rfkill list all**

AND

**lsmod**

---

### Post by wildmanne39 on 2011-12-29
Hi optima4, please go to this link and do what it says in post 4 and I think it will make it work a lot better, please let me know.
[http://ubuntuforums.org/showthread.php?p=11573134#post11573134](http://ubuntuforums.org/showthread.php?p=11573134#post11573134)
Thanks

---

### Post by optima4 on 2011-12-29
You Sir have brightened my world, so far it looks like the issue has been resolved. Many thanks

Optima4 

´´´´´´´´´´´´´´´´´´´´´´¶¶¶¶¶¶¶¶¶&#8230;&#8230;..
´´´´´´´´´´´´´´´´´´´´¶¶´´´´´´´´´´¶¶&#8230;&#8230;
´´´´´´¶¶¶¶¶´´´´´´´¶¶´´´´´´´´´´´´´´¶¶&#8230;&#8230;&#8230;.
´´´´´¶´´´´´¶´´´´¶¶´´´´´¶¶´´´´¶¶´´´´´¶¶&#8230;&#8230;&#8230;&#8230;..
´´´´´¶´´´´´¶´´´¶¶´´´´´´¶¶´´´´¶¶´´´´´´´¶¶&#8230;..
´´´´´¶´´´´¶´´¶¶´´´´´´´´¶¶´´´´¶¶´´´´´´´´¶¶&#8230;..
´´´´´´¶´´´¶´´´¶´´´´´´´´´´´´´´´´´´´´´´´´´¶¶&#8230;.
´´´´¶¶¶¶¶¶¶¶¶¶¶¶´´´´´´´´´´´´´´´´´´´´´´´´¶¶&#8230;.
´´´¶´´´´´´´´´´´´¶´¶¶´´´´´´´´´´´´´¶¶´´´´´¶¶&#8230;.
´´¶¶´´´´´´´´´´´´¶´´¶¶´´´´´´´´´´´´¶¶´´´´´¶¶&#8230;.
´¶¶´´´¶¶¶¶¶¶¶¶¶¶¶´´´´¶¶´´´´´´´´¶¶´´´´´´´¶¶&#8230;
´¶´´´´´´´´´´´´´´´¶´´´´´¶¶¶¶¶¶¶´´´´´´´´´¶¶&#8230;.
´¶¶´´´´´´´´´´´´´´¶´´´´´´´´´´´´´´´´´´´´¶¶&#8230;..
´´¶´´´¶¶¶¶¶¶¶¶¶¶¶¶´´´´´´´´´´´´´´´´´´´¶¶&#8230;.
´´¶¶´´´´´´´´´´´¶´´¶¶´´´´´´´´´´´´´´´´¶¶&#8230;.
´´´¶¶¶¶¶¶¶¶¶¶¶¶´´´´´¶¶´´´´´´´´´´´´¶¶&#8230;..
´´´´´´´´´´´´´´´´´´´´´´´¶¶¶¶¶¶¶¶¶¶¶&#8230;&#8230;.

---

### Post by wildmanne39 on 2011-12-29
Hi optima4, your welcome! I am glad it is working.
Enjoy

---

### Post by optima4 on 2011-12-29
Hey, sorry to message back again already. Was there any other code to add by chance? Because although it is actually connecting everytime, I notice there is a bit of a lag still just at least connecting eventually. Would there be anything else to try? Otherwise at least I havent gotten a "Page Not Loading" error.

EDIT** hm, seems to be doing OK, not sure if it was just that page or something you know. I really dont mean to sound ungrateful, just better to ask now, you know. And still thank you very much wildmanne39.

---

### Post by blakm43 on 2011-12-30
thxx wildmane it works!! :)

---

### Post by optima4 on 2011-12-30
Sigh well, ya this morning running into some of these issues again. Maybe I need to repost my Terminal results? Well, I am getting some slower loading pages and I already had a "Not Loading" error this morning.


*got copy and paste working*
[B]

cat /etc/lsb-release; uname -a

[/B]```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux plethoraviaoptima-LT27 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux

```

 **lspci -nnk | grep -iA@ net**

```

grep: @: invalid context length argument

 **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:2  Signal level:186  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

 **rfkill list all**

```

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

 **lsmod**

```

Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251973  3 vboxpci,vboxnetadp,vboxnetflt
deflate                12545  0 
zlib_deflate           26622  1 deflate
ctr                    13033  0 
twofish_generic        16579  0 
twofish_i586           12503  0 
twofish_common         20823  2 twofish_generic,twofish_i586
parport_pc             32114  0 
ppdev                  12849  0 
camellia               29212  0 
serpent                29029  0 
blowfish               16674  0 
cast5                  24976  0 
des_generic            21191  0 
xcbc                   12711  0 
rmd160                 16664  0 
sha512_generic         16780  0 
crypto_null            12782  0 
af_key                 31531  2 
snd_hda_codec_realtek   254125  1 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_intel          24262  4 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
joydev                 17393  0 
snd_seq_midi           13132  0 
lib80211_crypt_tkip    17240  0 
snd_rawmidi            25241  1 snd_seq_midi
i915                  505159  2 
snd_seq_midi_event     14475  1 snd_seq_midi
wl                   2646601  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
serio_raw              12990  0 
snd                    55902  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192194  3 i915,drm_kms_helper
lib80211               14570  2 lib80211_crypt_tkip,wl
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
i2c_algo_bit           13199  1 i915
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
wmi                    18744  1 acer_wmi
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  2 
libahci                25727  1 ahci
atl1c                  36638  0 

```

---

### Post by wildmanne39 on 2011-12-30
Hi optima4, try this please:
```
sudo su
echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf
exit
```
Then reboot.
Thanks

---

### Post by optima4 on 2011-12-31
I dont want to speak too soon, but it looks back to normal so far. I know its the Holidays, so I appreciate you taking the time to get back to me on that.

---

### Post by wildmanne39 on 2011-12-31
Hi optima4, I think your wireless will be okay now, keep us informed.
Thanks

---

### Post by optima4 on 2012-01-01
Yep, everything is doing much better now, thank you Wilmanne39 :}

---

### Post by wildmanne39 on 2012-01-01
Your welcome!
Enjoy

---

### Post by blakm43 on 2012-01-01
hey the commands fixed my wireless..but is there a perm fix for this or do i have to do these commands everytime i get on my pc

---

### Post by wildmanne39 on 2012-01-01
Hi blakm43, this is how to make it permanent.
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Add a single line:
```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by xchecker on 2012-01-02
Having the same problem here on my 11.10 desktop with a Linksys wireless USB adapter.  Can someone help?  Here's some info to start:

> crichmond@brichmond-desktop:~$ lspci -nnk | grep -iA2 net
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
	Subsystem: nVidia Corporation Device [10de:0162]
	Kernel driver in use: forcedeth
crichmond@brichmond-desktop:~$ lsmod
Module                  Size  Used by
snd_hrtimer            12648  1 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_realtek   254125  1 
binfmt_misc            17292  1 
nvidia              10390874  40 
arc4                   12473  2 
joydev                 17393  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
usbhid                 41905  0 
hid                    77367  1 usbhid
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rt2500usb              22652  0 
rt2x00usb              20092  1 rt2500usb
rt2x00lib              48114  2 rt2500usb,rt2x00usb
mac80211              393459  2 rt2x00usb,rt2x00lib
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
cfg80211              172392  2 rt2x00lib,mac80211
snd                    55902  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
ndiswrapper           193669  0 
coretemp               13188  0 
w83627ehf              29165  0 
serio_raw              12990  0 
lm78                   19537  0 
hwmon_vid              12658  2 w83627ehf,lm78
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
forcedeth              58103  0 
sata_nv                23379  2 
pata_amd               13753  0 


---

### Post by wildmanne39 on 2012-01-02
Hi, please post:
```
lsusb
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by xchecker on 2012-01-02
```
crichmond@brichmond-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 13b1:000d Linksys WUSB54G v4 802.11g Adapter [Ralink RT2500USB]
Bus 002 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 002 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel

```

---

### Post by wildmanne39 on 2012-01-02
Hi, there are two things that I see we need to get rid of ndiswrapper and we can set a parameter for your wireless driver.

Just copy and paste all commands.

Please run these codes one line at a time:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Then
```
gksudo gedit /etc/modprobe.d/rt2500usb.conf
```
Add a single line:
```
options rt2500usb nohwcrypt=1
```
Proofread carefully, save and close gedit then reboot.
Thanks

---

### Post by xchecker on 2012-01-02
Didn't improve unfortunately.  Got a couple of responses to the commands you provide that may have bearing:

```
crichmond@brichmond-desktop:~$ sudo modprobe -rf ndiswrapper
[sudo] password for crichmond: 
WARNING: All config files need .conf: /etc/modprobe.d/Untitled Document 1, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
```

```
crichmond@brichmond-desktop:~$ sudo rm /etc/modprobe.d/ndiswrapper.conf
rm: cannot remove `/etc/modprobe.d/ndiswrapper.conf': No such file or directory

```

---

### Post by wildmanne39 on 2012-01-02
Hi, did you copy and paste all commands one line at a time then hit enter after each line and type your password, it will not show your password so when you have type it just hit enter.
Thanks

---

### Post by xchecker on 2012-01-02
Yes, each command copy and pasted individually into Terminal and hit enter after each.  Only had to enter my password once.  The other commands seemed to run OK or generated no response in Terminal.

---

### Post by acastroh on 2012-01-02
I just read this thread today.

First, I want to thank wildmanne39, because he/she was so patient and helpful.
Second, I want to share that I followed his/her directions on #19 (you need to read 17 and 18 to understand it) and it works! :D
I have installed Ubuntu Oneiric Ocelot on a **Toshiba Satellite A305-S6872** (see computer description here-> [http://reviews.cnet.com/laptops/toshiba-a305-s6872/1707-3121_7-33309976.html](http://reviews.cnet.com/laptops/toshiba-a305-s6872/1707-3121_7-33309976.html))

---

### Post by wildmanne39 on 2012-01-02
Hi, please copy the contents of this folder 
```
gksudo gedit /etc/modprobe.d/rt2500usb.conf
```
and post the output of:
```
lsmod | grep rt2
```
```
ndiswrapper -l
```
Thanks

---

### Post by wildmanne39 on 2012-01-02
Hi acastroh, your welcome! I am glad I could help.
Enjoy

---

### Post by xchecker on 2012-01-02
Contents of file:
```
options rt2500usb nohwcrypt=1
```

Command output:
```
crichmond@brichmond-desktop:~$ lsmod | grep rt2
rt2500usb              22652  0 
rt2x00usb              20092  1 rt2500usb
rt2x00lib              48114  2 rt2500usb,rt2x00usb
mac80211              393459  2 rt2x00usb,rt2x00lib
cfg80211              172392  2 rt2x00lib,mac80211

```

Command output:
```
crichmond@brichmond-desktop:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
```

---

### Post by wildmanne39 on 2012-01-02
Hi, also make sure your wireless connection looks like mine.

---

### Post by xchecker on 2012-01-02
Rats.  I made the wireless setting changes to ipv4 and ipv6 to match yours, rebooted and now it can't find a any servers.  Ideas?  I really appreciate your patience!

EDIT: I take that back; the servers are now found, but connections are still very, very slow.

---

### Post by wildmanne39 on 2012-01-02
Hi, double check that your settings are like mine and you did not make a typo like in the dns server and make sure auto connect is checked, I notice for some reason it is not in my screenshot but mine auto connects.

Please post the results of:
```
lsmod
nm-tool
iwconfig
rfkill list all

```
```
sudo cat /var/log/syslog | grep -e rt2 -e firmware -e wlan -e wpa -e etork | tail -n55
```
Thanks

---

### Post by xchecker on 2012-01-02
Changed to autoconnect on the IPv4.

Here's the first set of commands:
```
crichmond@brichmond-desktop:~$ lsmod
Module                  Size  Used by
snd_hrtimer            12648  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
binfmt_misc            17292  1 
snd_hda_codec_realtek   254125  1 
arc4                   12473  2 
nvidia              10390874  40 
nv_tco                 13399  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
rt2500usb              22652  0 
rt2x00usb              20092  1 rt2500usb
snd_seq_midi_event     14475  1 snd_seq_midi
rt2x00lib              48114  2 rt2500usb,rt2x00usb
mac80211              393459  2 rt2x00usb,rt2x00lib
ndiswrapper           193669  0 
coretemp               13188  0 
w83627ehf              29165  0 
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
cfg80211              172392  2 rt2x00lib,mac80211
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17393  0 
snd                    55902  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
lm78                   19537  0 
hwmon_vid              12658  2 w83627ehf,lm78
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
pata_amd               13753  0 
forcedeth              58103  0 
sata_nv                23379  2 
crichmond@brichmond-desktop:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Richsys] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2500usb
  State:             connected
  Default:           yes
  HW Address:        00:12:17:72:E9:26

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Richsys:        Infra, BC:AE:C5:C3:04:4F, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:04:4B:07:0F:89

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


crichmond@brichmond-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Richsys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: BC:AE:C5:C3:04:4F   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:71  Invalid misc:3427   Missed beacon:0

crichmond@brichmond-desktop:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

and the last:
```
crichmond@brichmond-desktop:~$ sudo cat /var/log/syslog | grep -e rt2 -e firmware -e wlan -e wpa -e etork | tail -n55
[sudo] password for crichmond: 
Jan  2 23:45:38 brichmond-desktop kernel: [ 3482.368036] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:45:42 brichmond-desktop kernel: [ 3486.204042] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:45:42 brichmond-desktop kernel: [ 3486.204051] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:45:46 brichmond-desktop kernel: [ 3490.044083] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:45:46 brichmond-desktop kernel: [ 3490.044092] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:45:50 brichmond-desktop kernel: [ 3493.884063] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:45:50 brichmond-desktop kernel: [ 3493.884072] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:45:54 brichmond-desktop kernel: [ 3497.720042] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:45:54 brichmond-desktop kernel: [ 3497.720050] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:45:58 brichmond-desktop kernel: [ 3501.564060] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:45:58 brichmond-desktop kernel: [ 3501.564068] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:46:02 brichmond-desktop kernel: [ 3505.400020] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:46:02 brichmond-desktop kernel: [ 3505.400025] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:46:05 brichmond-desktop kernel: [ 3509.240043] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:46:05 brichmond-desktop kernel: [ 3509.240051] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:46:12 brichmond-desktop kernel: [ 3515.760083] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:46:12 brichmond-desktop kernel: [ 3515.760091] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:46:16 brichmond-desktop kernel: [ 3519.604034] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:46:16 brichmond-desktop kernel: [ 3519.604042] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:46:20 brichmond-desktop kernel: [ 3523.444046] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:46:20 brichmond-desktop kernel: [ 3523.444055] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:46:23 brichmond-desktop kernel: [ 3527.284082] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:46:23 brichmond-desktop kernel: [ 3527.284091] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:46:27 brichmond-desktop kernel: [ 3531.128049] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:46:27 brichmond-desktop kernel: [ 3531.128058] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:46:31 brichmond-desktop kernel: [ 3535.328040] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:46:31 brichmond-desktop kernel: [ 3535.328048] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:46:35 brichmond-desktop kernel: [ 3539.172041] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:46:35 brichmond-desktop kernel: [ 3539.172050] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:46:39 brichmond-desktop kernel: [ 3543.236042] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:46:39 brichmond-desktop kernel: [ 3543.236051] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:46:43 brichmond-desktop kernel: [ 3547.172062] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:46:43 brichmond-desktop kernel: [ 3547.172071] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:46:47 brichmond-desktop kernel: [ 3551.116041] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:46:47 brichmond-desktop kernel: [ 3551.116047] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:46:51 brichmond-desktop kernel: [ 3555.060046] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:46:51 brichmond-desktop kernel: [ 3555.060054] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:46:56 brichmond-desktop kernel: [ 3560.320076] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:46:56 brichmond-desktop kernel: [ 3560.320081] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:47:00 brichmond-desktop kernel: [ 3564.160022] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:47:00 brichmond-desktop kernel: [ 3564.160030] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:47:05 brichmond-desktop kernel: [ 3568.880040] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:47:05 brichmond-desktop kernel: [ 3568.880048] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:47:09 brichmond-desktop kernel: [ 3572.836054] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:47:09 brichmond-desktop kernel: [ 3572.836062] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:47:13 brichmond-desktop kernel: [ 3576.672041] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:47:13 brichmond-desktop kernel: [ 3576.672047] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:47:17 brichmond-desktop kernel: [ 3580.516040] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:47:17 brichmond-desktop kernel: [ 3580.516045] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:47:20 brichmond-desktop kernel: [ 3584.352063] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:47:20 brichmond-desktop kernel: [ 3584.352072] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:47:24 brichmond-desktop kernel: [ 3588.300123] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:47:24 brichmond-desktop kernel: [ 3588.300129] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Jan  2 23:47:28 brichmond-desktop kernel: [ 3592.140047] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Jan  2 23:47:28 brichmond-desktop kernel: [ 3592.140055] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
```

---

### Post by wildmanne39 on 2012-01-03
Hi, I think this will work if it does we need to make it permanent. Run the code one line at a time.
```
sudo /etc/init.d/network-manager stop
sudo iwconfig wlan0 power off
sudo service network-manager restart
```
Thanks

---

### Post by sromano88 on 2012-01-03
Hi wildmanne39, this is an excellent post.
I was trying to apply your comments to my configuration but I cannot understand the analogies.
Note: It was woking everything ok till a few days ago. I can't figure it out what has changed (if anything has)

Hope you can help me.
Thanks a lot.
Sergio.

```
user@machine:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux sergio-ubuntu 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```


```
user@machine:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82b3]
	Kernel driver in use: forcedeth

```

```
user@machine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"******"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: F4:EC:38:EC:3F:F8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:36   Missed beacon:0

```

```
user@machine:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
user@machine:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
binfmt_misc            17540  1 
vesafb                 13809  1 
arc4                   12529  2 
rt73usb                31735  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20830  1 rt73usb
rt2x00lib              50325  2 rt73usb,rt2x00usb
mac80211              462092  2 rt2x00usb,rt2x00lib
cfg80211              199587  2 rt2x00lib,mac80211
snd_hda_codec_realtek   330769  1 
ppdev                  17113  0 
nvidia               8107305  34 
psmouse                73882  0 
edac_core              53746  0 
serio_raw              13166  0 
edac_mce_amd           23709  0 
k8temp                 13057  0 
parport_pc             36962  1 
asus_atk0110           18078  0 
wmi                    19256  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
ahci                   26002  4 
libahci                26861  1 ahci
forcedeth              67563  0 
pata_amd               14121  0 

```

---

### Post by xchecker on 2012-01-03
Wildman -

On the last command I got the response 'restart: Unknown instance'.  Is that a problem?

---

### Post by wildmanne39 on 2012-01-03
Hi xchecker, run the commands again and try the last one like this please:
```
sudo /etc/init.d/network-manager start
```
Thanks

---

### Post by wildmanne39 on 2012-01-03
Hi sromano88, the first thing I see is your link quality is low that will slow down internet a lot.

Second you may be having issues power management.

Please post the output of:
```
lsusb
```
Thanks

---

### Post by xchecker on 2012-01-03
Command output from the revised command:
```
crichmond@brichmond-desktop:~$ sudo /etc/init.d/network-manager start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start network-manager
network-manager start/running, process 3148

```

---

### Post by and1script on 2012-01-03
Hi I am new to Ubuntu and my wireless connection is really slow as well.

@wildmanne39 I have a Dell XPS 15 with Ubuntu 11.10 and wanted to ask you first whether I should do the stuff you have suggested the other people to do or if the steps are machine dependent. 

Thanks in advance. You have helped many people on this thread and we all appreciate you patience. :D

---

### Post by Martian1567 on 2012-01-04
I've tried the above steps of disabling IPV6. For some reason, my Ubuntu 11.10 Wireless is still slower than Dial-up. This issue is driving me nuts. I appreciate your support.

---

### Post by kforum on 2012-01-04
> **Martian1567 said:**
> I've tried the above steps of disabling IPV6. For some reason, my Ubuntu 11.10 Wireless is still slower than Dial-up. This issue is driving me nuts. I appreciate your support.

have you tried using the 2.6 kernel?

---

### Post by wildmanne39 on 2012-01-04
Hi xchecker, let's do it this way since it is not working the other way.
```
gksudo gedit /etc/pm/power.d/wireless
```
(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```
Save, exit gedit and reboot.
Thanks

---

### Post by wildmanne39 on 2012-01-04
Hi and1script, yes it is hardware dependent, so please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
lsusb
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by wildmanne39 on 2012-01-04
Hi Martian1567, please do what I said in post 103.
Thanks

---

### Post by and1script on 2012-01-04
Hey wildmanne39 this is what I got when I run the following commands:

cat /etc/lsb-release; uname -a
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux andres-Ubuntu 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```


lspci -nnk | grep -iA2 net
```

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [8086:008a] (rev 34)
	Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]
	Kernel driver in use: iwlagn
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Dell Device [1028:04b6]
	Kernel driver in use: r8169

```


iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"CIA-3"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 1C:7E:E5:35:E7:98   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8226  Invalid misc:275   Missed beacon:0

```


rfkill list all
```

1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
10: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


```


lsmod
```

Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
usb_storage            57901  0 
uas                    18027  0 
acpi_call              12623  0 
bnep                   18436  2 
rfcomm                 47946  8 
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
joydev                 17693  0 
binfmt_misc            17540  1 
arc4                   12529  2 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            13831  0 
dcdbas                 14490  1 dell_laptop
snd                    68266  15 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
iwlagn                314213  0 
psmouse                73882  0 
serio_raw              13166  0 
mei                    41480  0 
mac80211              462092  1 iwlagn
soundcore              12680  1 snd
i915                  566827  3 
cfg80211              199587  2 iwlagn,mac80211
drm_kms_helper         42558  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   236290  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
wmi                    19256  1 dell_wmi
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  3 
libahci                26861  1 ahci
r8169                  52788  0 
xhci_hcd               82820  0 


```


lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 002 Device 003: ID 8086:0189 Intel Corp. 

```

thanks

---

### Post by wildmanne39 on 2012-01-04
Hi and1script, please try:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up
```
if it helps we will need to make it permanent.
Thanks

---

### Post by Martian1567 on 2012-01-05
cat /etc/lsb-release; uname -a: ```
 DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Luke-PC 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```lspci -nnk | grep -iA2 net: ```
 00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
    Subsystem: Intel Corporation Device [8086:201b]
    Kernel driver in use: e1000e

```iwconfig: ```
 lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"phillies2011"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:18:E7:E5:F6:9C   
          Bit Rate:300 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=99/100  Signal level=61/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```rfkill list all: ```
 0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```lsmod: ```
 Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  8 
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
binfmt_misc            17540  1 
r8712u                189049  0 
joydev                 17693  0 
snd_hda_codec_hdmi     32040  4 
nvidia              11713772  40 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  6 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
btusb                  18600  2 
snd_seq_midi           13324  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30547  1 snd_seq_midi
bluetooth             166112  23 bnep,rfcomm,btusb
psmouse                73882  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  3 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
mei                    41480  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
shpchp                 37345  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
usb_storage            57901  1 
uas                    18027  0 
xhci_hcd               82820  0 
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  2 
libahci                26861  1 ahci
e1000e                160582  0 

```lsusb: ```
 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 002: ID 0bc2:50a1 Seagate RSS LLC 
Bus 001 Device 003: ID 045e:0768 Microsoft Corp. 
Bus 001 Device 004: ID 06a3:0cc3 Saitek PLC 
Bus 001 Device 005: ID 07d1:3300 D-Link System DWA-130 802.11n Wireless N Adapter(rev.E) [Realtek RTL8192SU]
Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 004: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 002 Device 006: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 002 Device 007: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 002 Device 008: ID 0a5c:2154 Broadcom Corp.  
```

---

### Post by wildmanne39 on 2012-01-05
Hi Martian1567, please see if this helps:
```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
reboot.
Thanks

---

### Post by xchecker on 2012-01-05
Wildman -

OK, we're getting closer.  I created the configuration file you suggested and rebooted.  Now it takes 15-20 seconds to load a page rather than several minutes.  Still slow, but much improved.  Can we do better?

I really appreciate your efforts here.

Update - Well, maybe not as improved as I thought.  The first time it loads a page it takes maybe 30 secs, but then after that it's taking several minutes again to reload or to follow a link at the same site.  Definitely frustrating.

---

### Post by wildmanne39 on 2012-01-05
Hi xchecker, in post 89 in the screenshot I gave you it showed dns server set manually to several 8's did you change that also to match mine?
Thanks

---

### Post by gillza on 2012-01-06
Dear All,

I guess I will jump in here and complain about my issue :)

I'm a happy owner of Asus G53sx-a1 laptop running 11.04 currently. 
The original ath9k driver that is installed by default craps out on me every 5 minutes or so if I download stuff at max speed. So I have installed compact wireless driver:

```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar -xjvf compat-wireless-2.6.tar.bz2
cd into_folder_that_was_created
./scripts/driver-select ath9k
make
sudo make install
sudo make unload
sudo modprobe ath9k
```

With this the driver wlan is stable BUT the speeds are a half of what they are used to be. Before I installed the compact wireless driver I tried the suggested: 

```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```
[B]
No effect.[/B]

I have tried the same with the new compact-wireless driver with **no improvement as well**. I would appreciate any help or advice. Thank you:

**cat /etc/lsb-release; uname -a**
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux user-asus 2.6.38-13-generic #53-Ubuntu SMP Mon Nov 28 19:23:39 UTC 2011 i686 i686 i386 GNU/Linux
```

**lspci -nnk | grep -iA2 net**
```
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave Device [1a3b:2c37]
	Kernel driver in use: ath9k
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device [1043:13b7]
	Kernel driver in use: r8169

```

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 14:da:e9:36:00:8b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1713 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:232440 (232.4 KB)  TX bytes:232440 (232.4 KB)

wlan0     Link encap:Ethernet  HWaddr 74:2f:68:3a:0a:90  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::762f:68ff:fe3a:a90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22612 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15209831 (15.2 MB)  TX bytes:9417258 (9.4 MB)

```

**rfkill list all**
```
2: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
8: phy3: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

**lsmod**
```
Module                  Size  Used by
ath9k                 115231  0 
mac80211              432443  1 ath9k
compat                 15408  1 mac80211
ath9k_common           13780  1 ath9k
ath9k_hw              389148  2 ath9k,ath9k_common
ath                    19182  3 ath9k,ath9k_common,ath9k_hw
cfg80211              177343  3 ath9k,mac80211,ath
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
pci_stub               12550  1 
vboxpci                22892  0 
vboxnetadp             13348  0 
vboxnetflt             27225  0 
vboxdrv               252051  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_hdmi     27535  4 
joydev                 17322  0 
arc4                   12473  2 
snd_hda_codec_realtek   255882  1 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
asus_nb_wmi            12587  0 
snd_seq_midi_event     14475  1 snd_seq_midi
asus_wmi               19428  1 asus_nb_wmi
sparse_keymap          13666  1 asus_wmi
usbhid                 41704  0 
nvidia              10782581  48 
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
uvcvideo               66851  0 
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
hid                    77084  1 usbhid
videodev               75143  1 uvcvideo
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  3 
xhci_hcd               68062  0 
r8169                  42534  0 
libahci                25548  1 ahci

```

---

### Post by Martian1567 on 2012-01-06
My internet feels even slower. I haven't always had slow internet. My internet has been slow ever since I reinstalled. I've reinstalled another time and, it's still slow. It might be a settings problem? I'm not sure.

---

### Post by wildmanne39 on 2012-01-06
> **Martian1567 said:**
> My internet feels even slower. I haven't always had slow internet. My internet has been slow ever since I reinstalled. I've reinstalled another time and, it's still slow. It might be a settings problem? I'm not sure.
Hi, did you do what I said in post 108 on this new install?
Thanks

---

### Post by and1script on 2012-01-06
Hey wildmanne39, that did the trick, how do i make it permanent?

thanks

---

### Post by wildmanne39 on 2012-01-06
Hi and1script, here is a link, please do the first two commands in post 4.
[http://ubuntuforums.org/showthread.php?t=1905409](http://ubuntuforums.org/showthread.php?t=1905409)
Thanks

---

### Post by wildmanne39 on 2012-01-06
Hi gillza, please try:
```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
Thanks

---

### Post by Martian1567 on 2012-01-06
I don't believe the problem is IPV6. Infact, disabling IPV6 makes the internet slower. It is a different problem. I have tried many different ways of disabling IPV6. They show no improvement. I would imagine that it's related to the CPUFREQ performance mode. Otherwise, I have no clue.

---

### Post by xchecker on 2012-01-06
wildman -

Under IPv4 settings tab I set Method = Auto (DHCP) addresses only, and DNS servers to: 8.8.8.8, 8.8.4.4

Any other thoughts?

---

### Post by gillza on 2012-01-07
> **wildmanne39 said:**
> Hi gillza, please try:
```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
Thanks

Entered the command and rebooted. No change. Sorry.

---

### Post by wildmanne39 on 2012-01-07
Hi, click on the internet icon in the top right corner of the screen and click on edit connections then make sure ipv6 is set to ignore and set your dns server like mine.
Thanks

---

### Post by gillza on 2012-01-07
Hi, 

Thank you for such a quick reply. Unfortunately adding googles public DNS and disabling IPv6 from network manager did not have any positive effect. 

Thank you.


> **wildmanne39 said:**
> Hi, click on the internet icon in the top right corner of the screen and click on edit connections then make sure ipv6 is set to ignore and set your dns server like mine.
Thanks

---

### Post by wildmanne39 on 2012-01-07
Hi, with everything you have tried assuming you made ```
options ath9k nohwcrypt=1
``` permanent I do not have any other idea's, I did research on it but no new answers were found.
Thanks

---

### Post by wildmanne39 on 2012-01-07
Hi Martian1567, right now with the wireless card you have if you have tried everything in this thread then I am out of idea's.
Thanks

---

### Post by gillza on 2012-01-07
> **wildmanne39 said:**
> Hi, with everything you have tried assuming you made ```
options ath9k nohwcrypt=1
``` permanent I do not have any other idea's, I did research on it but no new answers were found.
Thanks

wildmanne39,

Thank you for all your help. I am going to look for more information as well. If I will be able to fix it I'll post it here. 

Thank you!

---

### Post by wildmanne39 on 2012-01-07
Hi gillza, your welcome and yes please let us know it will help many to solve this issue.

---

### Post by Martian1567 on 2012-01-07
Well, I guess I'm stuck here. Thanks for your help.

---

### Post by wildmanne39 on 2012-01-07
Hi, your wqelcome! I am sorry I was not able to find a solution.

---

### Post by Flash__Gordon on 2012-01-08
I just tried Fedora 16 (which is using 3.1 for kernel) and it seems to have NO issues with the wireless as I have with 11.10. I believe this is a kernel issue and really, really hope 12.04 using newer kernel will also solve this as I prefer Ubuntu/Debian based linux. (just a preference) 

Flash

---

### Post by gillza on 2012-01-08
> **wildmanne39 said:**
> Hi gillza, your welcome and yes please let us know it will help many to solve this issue.

I have reverted all the changes suggested because the system started to hang on occasion. Will see if it will become stable again. Wireless still slow.

---

### Post by STUPID USERNAME on 2012-01-08
Hello!
I have a very similar problem.
I just bought a notebook, Aspire 4739-6483, with windows installed on it. On windows, the wireless signal was strong and the speed match my connection. 

But I don't want windows so I replaced it completely with Ubuntu 11.10.
At first, the signal was strong and navigation fast, just like in windows. I could go in any room in my place and navigate without problem. I could see over 60 different networks. But after a few minutes only, the signal got very weak and I couldn't get a somewhat decent signal unless I was very close to the router. Even there, sometime to signal gets so weak that I lose connection... I never see more than 5 networks available now... On my older desktop, running Ubuntu 11.10, I have no problem at all...
I really don't know what to do, and I'm a noob.
Maybe this info will help you help me:


''sudo iwconfig'' gives me this:
```

bern@bern-Aspire-4739:~$ sudo iwconfig
[sudo] password for bern: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"teksavvy"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:F8:F3:F9:FD   
          Bit Rate=24 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:75  Invalid misc:720   Missed beacon:0
```''lspci -nnk | grep -iA2 net'' gives me this:

```
bern@bern-Aspire-4739:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0603]
    Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6617]
    Kernel driver in use: ath9k
```''lsmod'' gives me this:

```
bern@bern-Aspire-4739:~$ lsmod
Module                  Size  Used by
ath9k                 112612  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
joydev                 17393  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          28358  4 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
sparse_keymap          13658  0 
snd_pcm                80435  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12473  2 
snd                    55902  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  0 
psmouse                63474  0 
serio_raw              12990  0 
i915                  509290  8 
intel_ips              17753  0 
mac80211              393459  1 ath9k
drm_kms_helper         32889  1 i915
ath9k_common           13599  1 ath9k
ath9k_hw              293933  2 ath9k,ath9k_common
drm                   196290  4 i915,drm_kms_helper
ath                    19387  2 ath9k,ath9k_hw
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
mei                    36466  0 
cfg80211              172392  3 ath9k,mac80211,ath
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25761  1 ahci
atl1c                  36638  0 
```
Please help me! It would be so much appreciated! The only reason I own a computer is to navigate the internet!

Thank you very much for your time!

Bern

---

### Post by wildmanne39 on 2012-01-08
Hi Flash__Gordon, you can also use that kernel on ubuntu just start a thread in the right section of the forum and ask for help on installing it.
Thanks

---

### Post by wildmanne39 on 2012-01-08
Hi gillza, the changes we made if done properly would not cause any problems I have helped people do them many times and have them same changes on my computer.

I suspect in some of these cases that an update may have caused the slow issues if this is the case hopefully another update will correct some of these issues.
Thanks

---

### Post by wildmanne39 on 2012-01-08
Hi STUPID USERNAME, please do what is in post 6 of this thread.
Thanks

---

### Post by Flash__Gordon on 2012-01-08
> **wildmanne39 said:**
> Hi Flash__Gordon, you can also use that kernel on ubuntu just start a thread in the right section of the forum and ask for help on installing it.
Thanks


Thanks wildmanne39 I will do that in next couple of days. What would be the best section for this to be posted?

Flash

---

### Post by STUPID USERNAME on 2012-01-09
Thank you wildmanne! I did what was on post number 6, carefully, but nothing seems to have changed.

I still have the same problem.
Any other ideas?

Thanks again!

Bern

---

### Post by wildmanne39 on 2012-01-09
Hi STUPID USERNAME, change your settings to match the screen shot except leave yours to auto connect.
Thanks

---

### Post by gillza on 2012-01-09
> **wildmanne39 said:**
> Hi gillza, the changes we made if done properly would not cause any problems I have helped people do them many times and have them same changes on my computer.

I suspect in some of these cases that an update may have caused the slow issues if this is the case hopefully another update will correct some of these issues.
Thanks

I also think it was just a coincidence. Right before (literally) I started messing with the settings and loading unloading modules I updated the system. And the first time the system froze was when I executed: [B]sudo modprobe ath9k nohwcrypt=1
[/B]

It completely hanged, numlock indicator started flashing (kernel panic??) and I could only do a hard shutdown. Now it hangs periodically. I suspect it happens most often when I use **wlan** or **lan** heavily (lan speeds are unaffected by the way).

I know it is a bit off-topic but what logs (and where) could I check to narrow down the issue. I have looked at kern.log and dmesg and did not see anything suspicious. I remember the approximate times of recent hangs so I could correlate log output.

Thank you.

---

### Post by wildmanne39 on 2012-01-09
Hi, you can also look at system logs and xorg logs.
Thanks

---

### Post by STUPID USERNAME on 2012-01-10
> **wildmanne39 said:**
> Hi STUPID USERNAME, change your settings to match the screen shot except leave yours to auto connect.
Thanks

I'm sorry... I feel a bit stupid because I don't get it.
What screen shot?

---

### Post by Optimised on 2012-01-10
At the risk of sounding like a broken record I also have the same problem and have tried everything in this thread and others I have found googling, I am pretty much at my wits end. This all started when I upgraded from 10.04 to 11.10 and my internet had been unbelievably slow since then.

Here is the output of the following commands:

cat /etc/lsb-release; uname -a

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux PC1 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

lspci -nnk | grep -iA2 net

```

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device [1043:81f8]
	Kernel driver in use: sky2

```

iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SomeESSIDName"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C2:3F:C7:34:C3:1B   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:25  Invalid misc:275   Missed beacon:0

```

rfkill list all

```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

lsmod

```

Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
nls_utf8               12557  0 
cifs                  273872  0 
nvidia              11713772  42 
snd_hda_codec_analog    93522  1 
arc4                   12529  2 
uvcvideo               72711  0 
rtl8187                57035  0 
snd_usb_audio         118064  1 
mac80211              462092  1 rtl8187
snd_usbmidi_lib        25371  1 snd_usb_audio
videodev               92992  1 uvcvideo
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_analog,snd_hda_intel
ip6t_LOG               16974  4 
v4l2_compat_ioctl32    17083  1 videodev
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                96714  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
xt_hl                  12521  6 
cfg80211              199587  2 rtl8187,mac80211
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
ip6t_rt                12558  3 
eeprom_93cx6           12725  1 rtl8187
nf_conntrack_ipv6      13906  7 
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
ipt_REJECT             12576  1 
ipt_LOG                12919  5 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
xt_limit               12711  12 
xt_tcpudp              12603  18 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
xt_addrtype            12713  4 
asus_atk0110           18078  0 
xt_state               12578  14 
ip6table_filter        12815  1 
snd                    68266  17 snd_hda_codec_analog,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0 
nf_nat                 25890  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           82342  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13166  0 
ip_tables              27473  1 iptable_filter
x_tables               29846  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_crypt               23199  1 
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
usbhid                 47198  0 
hid                    95463  1 usbhid
crc_itu_t              12707  1 firewire_core
floppy                 70365  0 
sky2                   58674  0 
ahci                   26002  0 
pata_jmicron           12747  2 
libahci                26861  1 ahci

```

lsusb

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 002: ID 046d:08ce Logitech, Inc. QuickCam Pro 5000
Bus 008 Device 002: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 008 Device 003: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 008 Device 004: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 008 Device 005: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD

```

I know you guys are probably sick to death of looking through these things but any help you could give would be much appreciated.

---

### Post by gillza on 2012-01-10
> **STUPID USERNAME said:**
> I'm sorry... I feel a bit stupid because I don't get it.
What screen shot?

I think he meant this post: [http://ubuntuforums.org/showpost.php?p=11592868&postcount=120](http://ubuntuforums.org/showpost.php?p=11592868&postcount=120)

---

### Post by wildmanne39 on 2012-01-10
Hi, yes that is what I meant, I am sorry I thought I linked to it.
Thank you gillza.

I will not be on my today because it is my birthday.
Thanks

---

### Post by gillza on 2012-01-10
> **wildmanne39 said:**
> Hi, yes that is what I meant, I am sorry I thought I linked to it.
Thank you gillza.

I will not be on my today because it is my birthday.
Thanks

Happy Birthday wildmanne39!
Hope you have lots of fun today!

---

### Post by Flash__Gordon on 2012-01-10
> **wildmanne39 said:**
> Hi, yes that is what I meant, I am sorry I thought I linked to it.
Thank you gillza.

I will not be on my today because it is my birthday.
Thanks

Happy Birthday!

---

### Post by STUPID USERNAME on 2012-01-11
Happy birthday wildmanne39!
and thanks again!
I matched my settings to the screen shot. But the problem is still there.
I noticed a little improvement... I can go a bit farther from the router... and I see up to 10 available networks... However, maybe it has nothing to do with what I did, and it's a mystery... Just like it's a mystery why and how it went from being perfectly good after the installation to weak and slow in a few minutes.

Do you think there is still something I could do or I should just reinstall windows or an older version of Ubuntu, which would be a defeat.

Bern

---

### Post by jamesdotca on 2012-01-11
Just wanted to say thanks to wildmanne39. His advice, combined with info from [HERE]("http://blogs.gnome.org/thos/2009/01/30/iwlagn-driver-and-wpa/") allowed me to fix my wireless connection with iwlagn.

---

### Post by wildmanne39 on 2012-01-12
Hi STUPID USERNAME, you can try this:
```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf

```
Also did you compile your driver from an outsidfe source?
Thanks

---

### Post by STUPID USERNAME on 2012-01-12
Hi!
I tried it and it didn't seem to have changed anything.
No I didn't compile the driver from an outside source, right after installation I checked for additional drivers with the "additional drivers" app but there was nothing.
Thanks

---

### Post by wildmanne39 on 2012-01-12
Hi STUPID USERNAME, the file you created for the driver that I asked you too you left it created and did not change it back right?

Also check your router settings and make sure your wireless power is turned all the way up.
Thanks

---

### Post by STUPID USERNAME on 2012-01-12
Hi wildmanne!
No I didn't change it back.
I don't know how to check the router settings.

I have to tell you I just reinstalled Ubuntu 11.10... I thought it might help... After all, the last time I installed it everything was perfect at first. But this time it's not, nothing changed. I must admit I'm desperate. 
I tried the wired connection for the first time. Works fine. I get 100 mb/s.

Before we try to go any further, do you want me to redo everything you asked me to do before I reinstalled it? (right now it's a fresh install, didn't even updated, added or remove anything)

thank you so much wildmanne

---

### Post by wildmanne39 on 2012-01-12
Hi, yes but try them one at a time and see if it helps, start with the very first one I asked you to do with your driver.

There is not much more to try.

I think an update has caused this issue many people are having the same problem but with a couple of different drivers.
Thanks

---

### Post by STUPID USERNAME on 2012-01-13
It still doesn't work. I tried fedora 16 and openSUSE 12.1 from the CD, and it doesn't work either.
Thank you so much for trying to help me for free. I really appreciate that.
I'd like to reinstall Windows, and wait for the next ubuntu release and try it from the CD to see if it got any better. It's either that or no wireless connection... and since I travel a lot I really need it. At least Ubuntu works perfectly on my desktop.

I don't have the windows CD, and the recovery partition is gone. 
Could you help me with reinstalling it? I think I can download the Cd from the web or burn it from my brother's computer (running same windows 7 HP).
But do I need to format my computer completely in any special format before I try to install it?
thanks
Bern

---

### Post by wildmanne39 on 2012-01-13
Hi, we can help with that but you will need to start a new thread in absolute beginners section for that issue, then paste a link to it here.
Thanks

---

### Post by OdiusRex on 2012-01-15
could you help me as well 
lspci -nnk | grep -iA2 net ```
04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
    Subsystem: Intel Corporation Vaio VGN-SZ79SN_C [8086:1100]
    Kernel driver in use: iwl4965
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136]
    Kernel driver in use: r8169
    Kernel modules: r8169

```and lsmod ```
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
binfmt_misc            17292  1 
snd_hda_codec_realtek   254125  1 
joydev                 17393  0 
arc4                   12473  2 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
pcmcia                 39822  0 
snd_timer              28932  2 snd_pcm,snd_seq
i915                  505159  2 
iwl4965               121795  0 
tifm_7xx1              12937  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
iwl_legacy             71499  1 iwl4965
drm_kms_helper         32889  1 i915
mac80211              393459  2 iwl4965,iwl_legacy
drm                   192194  3 i915,drm_kms_helper
tifm_core              15040  1 tifm_7xx1
psmouse                73673  0 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
serio_raw              12990  0 
cfg80211              172392  3 iwl4965,iwl_legacy,mac80211
pcmcia_rsrc            18367  1 yenta_socket
i2c_algo_bit           13199  1 i915
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
sparse_keymap          13658  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
r8169                  43104  0 

```

---

### Post by dezideriu_candid on 2012-01-15
Hello all and happy birth day wildmane!
I have a similar problem with the wireless connection. I can connect to the desired network which is in proximity and I get a very good signal form it. the problem is that I always get the 'problem loading page' error in my browser. I desperately tried various fixes I found on the Internet (some of them from this thread), I installed the compact-wireless drivers, I installed wicd, I even installed an older version of ubuntu (10.04 that is) thinking the problem only occurs with newer versions. Yesterday I got it working with the maximum speed (don't ask me how...) and it worked fine for a while but then suddenly it reverted to the same aforementioned symptoms. 

I have to mention that I also run Windows 7 on this machine and wireless works fine. 

In the end I installed a fresh copy of Ubuntu 11.10 and I figured I shouldn't be clutching at straws anymore but instead get some expert help with my problem. I'd really like to get at the bottom of this! Thanks!

here is the output of: 
cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux bogdan-Inspiron-N5040 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```lspci -nnk | grep -iA2 net
```
12:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Dell Device [1028:0204]
    Kernel driver in use: ath9k
--
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0505]
    Kernel driver in use: r8169
```iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"LinuxApt"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 72:C0:6F:21:26:D8   
          Bit Rate=13.5 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:1   Missed beacon:0

```rfkill list all
```
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```lsmod
```
Module                  Size  Used by
iwlagn                314213  0 
ath9k                 127538  0 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
uvcvideo               72711  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
videodev               92992  1 uvcvideo
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
v4l2_compat_ioctl32    17083  1 videodev
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12529  2 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  566827  3 
mac80211              462092  2 iwlagn,ath9k
drm_kms_helper         42558  1 i915
drm                   236290  4 i915,drm_kms_helper
ath9k_common           13839  1 ath9k
ath9k_hw              312914  2 ath9k,ath9k_common
i2c_algo_bit           13423  1 i915
ath                    24067  2 ath9k,ath9k_hw
soundcore              12680  1 snd
video                  19412  1 i915
dell_laptop            13831  0 
psmouse                73882  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
serio_raw              13166  0 
dcdbas                 14490  1 dell_laptop
mei                    41480  0 
cfg80211              199587  4 iwlagn,ath9k,mac80211,ath
intel_ips              18089  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  1 dell_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            57901  0 
uas                    18027  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
r8169                  52788  0 
ahci                   26002  3 
libahci                26861  1 ahci

```

---

### Post by DR1665 on 2012-01-15
> **wildmanne39 said:**
> 
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Add a single line:
```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit then Reboot.

Thank you for post #6, wildmanne39. Immediate improvement on Dell 1521 running whatever the latest version is as of this post's date. 

Appreciate this community. Love how Ubuntu just works. :D

---

### Post by wildmanne39 on 2012-01-15
Hi OdiusRex, please try this:
```
gksudo gedit /etc/modprobe.d/iwl4965.conf
```
Add a single line:
```
options iwl4965 11n_disable=1
```
Proofread carefully, save and close gedit. Reboot and see if it works. 
Thanks

---

### Post by OdiusRex on 2012-01-16
[wildmanne39,]("http://ubuntuforums.org/member.php?u=508533") you sir, are awesome tyvm!

---

### Post by wildmanne39 on 2012-01-16
Hi, thanks for the kind words and your welcome!
Enjoy

---

### Post by STUPID USERNAME on 2012-01-16
Hi wildmanne!
I started a new thread:

[http://ubuntuforums.org/showthread.php?p=11616156#post11616156](http://ubuntuforums.org/showthread.php?p=11616156#post11616156)

Thanks!

---

### Post by mohammad110 on 2012-01-16
hi
i have been same problem since install 11.10 with wireless...
please order solution.
thanks

lsmod :
```
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
joydev                 17693  0 
binfmt_misc            17540  1 
arc4                   12529  2 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
ir_sony_decoder        12549  0 
ir_jvc_decoder         12546  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
ir_rc6_decoder         12546  0 
serio_raw              13166  0 
ir_rc5_decoder         12546  0 
rc_rc6_mce             12502  0 
i915                  566711  2 
ir_nec_decoder         12546  0 
ite_cir                25775  0 
ideapad_laptop         13871  0 
sparse_keymap          13890  1 ideapad_laptop
rc_core                26963  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ite_cir
iwlagn                314213  0 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms              17646  0 
wmi                    19256  0 
memstick               16569  1 jmb38x_ms
mac80211              310872  1 iwlagn
drm_kms_helper         42558  1 i915
drm                   236330  3 i915,drm_kms_helper
soundcore              12680  1 snd
cfg80211              199587  2 iwlagn,mac80211
i2c_algo_bit           13423  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  3 
libahci                26861  1 ahci
tg3                   147729  0 
firewire_ohci          40722  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core

```

lspci -nnk | grep -iA2 net

```
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
	Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1211]
	Kernel driver in use: iwlagn
--
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
	Subsystem: Lenovo Device [17aa:3878]
	Kernel driver in use: tg3

```

---

### Post by Optimised on 2012-01-17
bump.. lol 
> **Optimised said:**
> 
At the risk of sounding like a broken record I also have the same problem and have tried everything in this thread and others I have found googling, I am pretty much at my wits end. This all started when I upgraded from 10.04 to 11.10 and my internet had been unbelievably slow since then.

Here is the output of the following commands:

cat /etc/lsb-release; uname -a

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux PC1 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

lspci -nnk | grep -iA2 net

```

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device [1043:81f8]
	Kernel driver in use: sky2

```

iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SomeESSIDName"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C2:3F:C7:34:C3:1B   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:25  Invalid misc:275   Missed beacon:0

```

rfkill list all

```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

lsmod

```

Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
nls_utf8               12557  0 
cifs                  273872  0 
nvidia              11713772  42 
snd_hda_codec_analog    93522  1 
arc4                   12529  2 
uvcvideo               72711  0 
rtl8187                57035  0 
snd_usb_audio         118064  1 
mac80211              462092  1 rtl8187
snd_usbmidi_lib        25371  1 snd_usb_audio
videodev               92992  1 uvcvideo
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_analog,snd_hda_intel
ip6t_LOG               16974  4 
v4l2_compat_ioctl32    17083  1 videodev
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                96714  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
xt_hl                  12521  6 
cfg80211              199587  2 rtl8187,mac80211
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
ip6t_rt                12558  3 
eeprom_93cx6           12725  1 rtl8187
nf_conntrack_ipv6      13906  7 
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
ipt_REJECT             12576  1 
ipt_LOG                12919  5 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
xt_limit               12711  12 
xt_tcpudp              12603  18 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
xt_addrtype            12713  4 
asus_atk0110           18078  0 
xt_state               12578  14 
ip6table_filter        12815  1 
snd                    68266  17 snd_hda_codec_analog,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0 
nf_nat                 25890  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           82342  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13166  0 
ip_tables              27473  1 iptable_filter
x_tables               29846  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_crypt               23199  1 
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
usbhid                 47198  0 
hid                    95463  1 usbhid
crc_itu_t              12707  1 firewire_core
floppy                 70365  0 
sky2                   58674  0 
ahci                   26002  0 
pata_jmicron           12747  2 
libahci                26861  1 ahci

```

lsusb

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 002: ID 046d:08ce Logitech, Inc. QuickCam Pro 5000
Bus 008 Device 002: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 008 Device 003: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 008 Device 004: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 008 Device 005: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD

```

I know you guys are probably sick to death of looking through these things but any help you could give would be much appreciated.


---

### Post by wildmanne39 on 2012-01-17
Hi dezideriu_candid, please try this:
```
echo "blacklist iwlagn" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot
Thanks

---

### Post by wildmanne39 on 2012-01-17
Hi mohammad110, please do:
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```
```
Add a single line:
```
```
options iwlagn 11n_disable=1
```
Proofread carefully, save and close gedit. Reboot and see if it works.
Thanks

---

### Post by wildmanne39 on 2012-01-17
Hi Optimised,
Please refer to this link you will need to use ndiswrapper and a winxp driver because the driver your device uses has problems.
[http://ubuntuforums.org/showthread.php?t=1563834&highlight=8187&page=2](http://ubuntuforums.org/showthread.php?t=1563834&highlight=8187&page=2)  post 16 has the directions.
Thanks

---

### Post by IndyGunFreak on 2012-01-17
Seems most of this thread is about Atheros, but if anyone can help me with a Realtek(different device than the one mentioned above) problem, I would really appreciate it.

[http://ubuntuforums.org/showthread.php?p=11619279#post11619279](http://ubuntuforums.org/showthread.php?p=11619279#post11619279)

---

### Post by wildmanne39 on 2012-01-17
Hi, right now there are a lot of people having trouble with Realtek drivers, we are able to get some to improve but right now there is not much of a solution, please post the output of the following commands and we will try.
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
Thanks

---

### Post by IndyGunFreak on 2012-01-17
Thanks for trying... this is very frustrating (timed out 3x during this post, and had to just connect via cable)

lspci -nnk | grep -iA2 net

```
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8182]
	Kernel driver in use: rtl8192ce

```

lsb_release -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ken-Satellite-C655 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

uname -a
```
3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

lspci -nn
```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"MYESSID"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:33:B6:55:28   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-12 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:21891   Missed beacon:0

```
(My laptop is sitting 10ft from my router right now, so I'm not sure why it says Link quality is 70/70)

rfkill list all
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

lsmod
```
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
joydev                 17693  0 
parport_pc             36962  0 
ppdev                  17113  0 
arc4                   12529  2 
snd_hda_codec_conexant    62197  1 
snd_hda_intel          33390  1 
snd_hda_codec         104802  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
uvcvideo               72711  0 
snd_rawmidi            30547  1 snd_seq_midi
psmouse                73882  0 
serio_raw              13166  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi_event     14899  1 snd_seq_midi
rtl8192ce             137433  0 
rtlwifi               118703  1 rtl8192ce
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              310872  2 rtl8192ce,rtlwifi
cfg80211              199587  2 rtlwifi,mac80211
snd_timer              29991  2 snd_pcm,snd_seq
sparse_keymap          13890  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  566711  2 
drm_kms_helper         42558  1 i915
snd                    68266  11 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   236330  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
mei                    41480  0 
video                  19412  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
atl1c                  41643  0 
ahci                   26002  3 
libahci                26861  1 ahci

```

---

### Post by wildmanne39 on 2012-01-17
Hi ,IndyGunFreak try everything that was listed for Flash__Gordon to try one at a time in this thread but leave installing a new driver for last, it may help it may not.
[http://ubuntuforums.org/showthread.php?t=1901422&highlight=flash_gordon](http://ubuntuforums.org/showthread.php?t=1901422&highlight=flash_gordon)

If you need help with the instructions in that thread post exactly what you are having problems with here.
Thanks

---

### Post by dezideriu_candid on 2012-01-18
Thank you wildmanne39 for your reply and your patience! Unfortunately your solution didn't solve my problem. If you have any other suggestions I'd be more than happy to try them.

When I had my wireless up and running a few days ago my father might have worked up some changes in my router configuration (which is WPA-PSK) that seemed to do the trick for a while. But then again on Windows it works fine and I also have a netbook with 11.04 on it that also works perfectly fine. I guess there's a problem with the AR9285 driver as I see a lot of people having troubles with it. Unfortunately I do not have the possibility of connecting my laptop to a different wireless connection to see whether the problem has been caused by the router configuration.

I really wonder if there is a proprietary driver somewhere that might work?
    
Anyway thanks again!

---

### Post by ridhisundar on 2012-01-18
I have same problem of Internet slowness.

 > lspci -nnk | grep -iA2 net
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
    Subsystem: Acer Incorporated [ALI] Aspire 5920G [1025:0121]
    Kernel modules: tg3                                 
> root@Ridhi-Aspire:~# lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  12 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
r8712u                189049  0 
acer_wmi               23948  0 
sparse_keymap          13890  1 acer_wmi
btusb                  18600  2 
r592                   18144  0 
r852                   18277  0 
sm_common              16865  1 r852
nand                   54965  2 r852,sm_common
nand_ids               12723  1 nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
nand_ecc               13230  1 nand
psmouse                73882  0 
memstick               16569  1 r592
bluetooth             166112  23 bnep,rfcomm,btusb
mtd                    33181  2 sm_common,nand
serio_raw              13166  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i915                  566827  4 
snd_timer              29991  2 snd_pcm,snd_seq
wmi                    19256  1 acer_wmi
drm_kms_helper         42558  1 i915
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   236290  5 i915,drm_kms_helper
snd                    68266  13  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,   snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,sn  d_seq_device
i2c_algo_bit           13423  1 i915
soundcore              12680  1 snd
video                  19412  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
root@Ridhi-Aspire:~#                                 

                                           > root@Ridhi-Aspire:~# cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Ridhi-Aspire 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux                                 
Please advise...

---

### Post by wildmanne39 on 2012-01-18
Hi, dezideriu_candid please do:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Add a single line:
```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit. 
Then do:
```
gksudo gedit /etc/pm/power.d/wireless
```
(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off

```
Proofread carefully, save and close gedit.
Reboot
Thanks

---

### Post by wildmanne39 on 2012-01-18
Hi ridhisundar, is this a usb adaptor?
because I do not see a wireless adaptor if it is please post:
```
lsusb
```
Thanks

---

### Post by IndyGunFreak on 2012-01-18
> **wildmanne39 said:**
> Hi ,IndyGunFreak try everything that was listed for Flash__Gordon to try one at a time in this thread but leave installing a new driver for last, it may help it may not.
[http://ubuntuforums.org/showthread.php?t=1901422&highlight=flash_gordon](http://ubuntuforums.org/showthread.php?t=1901422&highlight=flash_gordon)

If you need help with the instructions in that thread post exactly what you are having problems with here.
Thanks

Tried everything there, installed new driver, still no joy.

Very frustrating.

---

### Post by wildmanne39 on 2012-01-18
Hi, did you reboot your computer and reset your router after all those changes?

Options:
If you did the above there is not any more I can do.

There is a problem with the driver and the 3.0 kernel so you could go back to 10.04, or 11.04, or you could install the 11.04 kernel but you will need to start another thread on that or you could try ndiswrpper and here is a link to get help with ndiswrapper if you choose this option.

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
Thanks

---

### Post by amknott on 2012-01-18
Hi, I'm having the same problem with my wireless internet. I have tried rmmod -f ath5k and modprobe ath5k nohwcrypt=1, and it sometimes seems to work, but not always. Executing terminal commands as per Post #59, i get the following:
```
 cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Toshiba 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

```
 lspci -nnk | grep -iA2 net
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: r8169
--
0e:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: AMBIT Microsystem Corp. AR5007EG 802.11bg NIC [1468:042a]
	Kernel driver in use: ath5k
```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Knottnet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: B4:74:9F:2B:FA:60   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

```

```
 rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
lsmod
Module                  Size  Used by
rndis_host             13848  0 
cdc_ether              13536  1 rndis_host
usbnet                 26212  2 rndis_host,cdc_ether
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
joydev                 17693  0 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
binfmt_misc            17540  1 
snd_hda_codec_realtek   330769  1 
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
sp5100_tco             13791  0 
snd_timer              29991  2 snd_pcm,snd_seq
r852                   18277  0 
sm_common              16865  1 r852
nand                   54965  2 r852,sm_common
nand_ids               12723  1 nand
nand_bch               13147  1 nand
r592                   18144  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
bch                    22061  1 nand_bch
nand_ecc               13230  1 nand
mtd                    33181  2 sm_common,nand
memstick               16569  1 r592
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              53746  0 
psmouse                73882  0 
k8temp                 13057  0 
edac_mce_amd           23709  0 
serio_raw              13166  0 
soundcore              12680  1 snd
i2c_piix4              13301  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19412  0 
ath5k                 156371  0 
ath                    24067  1 ath5k
mac80211              462092  1 ath5k
radeon               1016226  3 
sparse_keymap          13890  0 
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236290  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
cfg80211              199587  3 ath5k,ath,mac80211
shpchp                 37345  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
usb_storage            57901  0 
uas                    18027  0 
crc_itu_t              12707  1 firewire_core
sdhci                  32166  1 sdhci_pci
pata_atiixp            13164  0 
ahci                   26002  2 
libahci                26861  1 ahci
r8169                  52788  0 

```

I can use the wired connection, and it performs perfectly, and I can even use my Android mobile phone as a usb modem (with the phone connected to the WiFi network) and that works great too.

Any help will be much appreciated!

Thanks!

---

### Post by wildmanne39 on 2012-01-18
Hi amknott, did you make ath5k nohwcrypt=1 permanent?
Thanks

---

### Post by amknott on 2012-01-19
Hi Wildmanne39,

I tried.  I created the following .conf file:
```

cat /etc/modprobe.d/ath5k.conf
options ath5k nohwcrypt=1

```

But there seems to be no consistency - sometimes it will work great after a reboot, at other times rebooting makes no difference.  Sometime after a reboot I manually enter the rmmod / modprobe commands and it works, other times it doesn't.

Thanks for the quick response!

---

### Post by wildmanne39 on 2012-01-19
Hi, this > cat /etc/modprobe.d/ath5k.confis really ```
/etc/modprobe.d/ath5k.conf
```Right?

Please post the contents of that folder:
Thanks

---

### Post by amknott on 2012-01-19
Yes, that's right.

The contents of /etc/modprobe.d are as follows:
```

alsa-base.conf              blacklist-framebuffer.conf~
ath5k.conf                  blacklist-modem.conf
blacklist-ath_pci.conf      blacklist-oss.conf
blacklist-ath_pci.conf~     blacklist-rare-network.conf
blacklist.conf              blacklist-watchdog.conf
blacklist-cups-usblp.conf   options.conf
blacklist-firewire.conf     options.conf~
blacklist-framebuffer.conf

```

---

### Post by wildmanne39 on 2012-01-19
Hi, this is the name of the file that should have been created when you saved your file unless you changed the name
```
/etc/modprobe.d/ath5k.conf
```
**NOT**
```
/etc/modprobe.d
```

This file ```
/etc/modprobe.d/ath5k.conf
```what does it have in it?
Thanks

---

### Post by amknott on 2012-01-19
Contents of /etc/modprobe.d/ath5k.conf:
```

options ath5k nohwcrypt=1

```

---

### Post by wildmanne39 on 2012-01-19
Hi, please do the following:
```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
Then click on the internet icon in the top right corner of the screen,>Edit connection>wireless and set your settings to match the screen shots, except leave connect automatically checked.

It is getting late here so I am getting off for the night.
Thanks

---

### Post by amknott on 2012-01-19
Thanks again. I'&#314;l post the results tomorrow - it's pretty late here too!

---

### Post by dezideriu_candid on 2012-01-19
Thanks again wildmanne39. Unfortunately the solution you've posted didn't seem to work. If you have anything else in your magic bag of tricks I'm ready ready to try it.

---

### Post by IndyGunFreak on 2012-01-19
> **wildmanne39 said:**
> Hi, did you reboot your computer and reset your router after all those changes?

Options:
If you did the above there is not any more I can do.

There is a problem with the driver and the 3.0 kernel so you could go back to 10.04, or 11.04, or you could install the 11.04 kernel but you will need to start another thread on that or you could try ndiswrpper and here is a link to get help with ndiswrapper if you choose this option.

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
Thanks

Just for grins, I booted a live USB of 11.04, and still have the exact same problem.  Don't really wanna go back to 10.04, but I guess if I have to, I can.

Edit:  I just booted a Live USB of 10.04.3, and it does not pick up my Wired or my Wireless connection.

---

### Post by injur3 on 2012-01-19
Hi,
I'm having the same problem with wireless internet slowness when i upgraded to 11.10. I tired rmmod -f ath5k and modprobe ath5k nohwcrypt=1 with no luck.

Here's some information!

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Ubuntu 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux

```


```
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
	Subsystem: Intel Corporation Vaio VGN-SZ79SN_C [8086:1100]
	Kernel driver in use: iwl4965
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:30cc]
	Kernel driver in use: r8169

```


```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"AnimalHouse"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:B2:8A:0C:54   
          Bit Rate=144.4 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:830  Invalid misc:76   Missed beacon:0

```

```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
Module                  Size  Used by
nls_utf8               12493  1 
udf                    83826  1 
hidp                   22351  1 
hid                    77367  1 hidp
bnep                   17923  2 
rfcomm                 38408  8 
joydev                 17393  0 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13489  1 
nvidia              10390874  43 
arc4                   12473  2 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
uvcvideo               67271  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
videodev               85626  1 uvcvideo
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
snd                    55902  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
video                  18908  0 
nand_ecc               13070  1 nand
iwl4965               121795  0 
mtd                    35852  2 sm_common,nand
btusb                  18160  4 
iwl_legacy             71499  1 iwl4965
mac80211              393459  2 iwl4965,iwl_legacy
r592                   17808  0 
wmi                    18744  1 hp_wmi
memstick               15857  1 r592
psmouse                73673  0 
soundcore              12600  1 snd
cfg80211              172392  3 iwl4965,iwl_legacy,mac80211
serio_raw              12990  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
bluetooth             148839  28 hidp,bnep,rfcomm,btusb
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  3 
libahci                25727  1 ahci
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  2 udf,firewire_core
r8169                  43104  0 

```


Thanks for all of your help in advance!

---

### Post by gillza on 2012-01-19
Um don't you have intel wireless not atheros ?

---

### Post by IndyGunFreak on 2012-01-19
> **injur3 said:**
> Hi,
I'm having the same problem with wireless internet slowness when i upgraded to 11.10. I tired rmmod -f ath5k and modprobe ath5k nohwcrypt=1 with no luck.

You should make sure you have the same hardware as the people that are being helped, when following instructions.  You're using an Intel 4965, so start your search there.

---

### Post by wildmanne39 on 2012-01-19
Hi injur3, please try this:
```
gksu gedit /etc/modprobe.d/iwl4965.conf
```
And add the following to it:
```
options iwl4965 11n_disable=1
```
proof read then save and exit and reboot.
Thanks

---

### Post by wildmanne39 on 2012-01-19
Hi dezideriu_candid, please try what is in post 183 also make sure in your router that your wireless power level is at 100 percent.
Thanks

---

### Post by Flash__Gordon on 2012-01-19
> **IndyGunFreak said:**
> Just for grins, I booted a live USB of 11.04, and still have the exact same problem.  Don't really wanna go back to 10.04, but I guess if I have to, I can.

Edit:  [COLOR="Red"]I just booted a Live USB of 10.04.3, and it does not pick up my Wired or my Wireless connection.[/COLOR]

I found the same thing when I tried 10,04,3. 

Flash__Gordon

---

### Post by wildmanne39 on 2012-01-19
Hi IndyGunFreak, that driver is not included in 10.04 
The funny thing is the driver in 11.10 was suppose to make your device work better.

I ask a friend with a lot more experience then I have to see if he has any idea's.
Thanks

---

### Post by chili555 on 2012-01-19
@IndyGunFreak--

Please see my response on your other thread.

---

### Post by dezideriu_candid on 2012-01-20
Hi wildmanne39! Thanks again for the reply. I haven't tried it yet... because miraculously the wireless connection works fine. I don't know how though?! Yesterday your solution didn't seem to have any effect although I did specifically what you asked. It's getting really weird (it's better weird than wired :p) This happened before and now I doubt it is because of the solutions posted here.

For the moment I'll leave it be and if it stops working I'll give you the details!

Thanks again!

Update: It's not working anymore. I tested the direct download speed by downloading ubuntu from ubuntu.com and it worked really good, maximum speed and all. Then I started deluge and it worked for a couple of minutes and now it stopped. I'm going to try that solution after all...

---

### Post by dezideriu_candid on 2012-01-20
Tried it... but it doesn't seem to help.

Anyway many thanks again!

---

### Post by mohammad110 on 2012-01-20
> **wildmanne39 said:**
> Hi mohammad110, please do:
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```
```
Add a single line:
```
```
options iwlagn 11n_disable=1
```
Proofread carefully, save and close gedit. Reboot and see if it works.
Thanks

hi
thanks for your answer. my internet speed now is better than ago...
but still bandwidth when i download file by chrome in Ubuntu than win7 1/5 !!
thanks

---

### Post by amknott on 2012-01-20
Hi Wildmanne39,

I followed your instructions (post 183) to disable ipv6, but it doesn't seem to have made any difference.  I already had the Google public DNS active, so there was nothing else to change.

I had my laptop at work yesterday, and the wireless worked fine - not sure if it was a fluke, or whether there is some incompatibility with my home router?

I just upgraded to the 3.0.0.15 kernel, so I'll see if that helps after rebooting.

---

### Post by wildmanne39 on 2012-01-20
@ dezideriu_candid and gillza please post the output of:
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n35
```
```
nm-tool
```
```
dmesg | grep ath
```
Thanks

---

### Post by dezideriu_candid on 2012-01-21
Hi, thanks for the reply

sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n35
```
Jan 21 09:36:24 bogdan-Inspiron-N5040 kernel: [   17.246730] wlan0: associate with 72:c0:6f:21:26:d8 (try 1)
Jan 21 09:36:24 bogdan-Inspiron-N5040 NetworkManager[926]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan 21 09:36:24 bogdan-Inspiron-N5040 kernel: [   17.250891] wlan0: RX AssocResp from 72:c0:6f:21:26:d8 (capab=0x431 status=0 aid=1)
Jan 21 09:36:24 bogdan-Inspiron-N5040 kernel: [   17.250898] wlan0: associated
Jan 21 09:36:24 bogdan-Inspiron-N5040 wpa_supplicant[998]: Associated with 72:c0:6f:21:26:d8
Jan 21 09:36:24 bogdan-Inspiron-N5040 kernel: [   17.257774] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan 21 09:36:24 bogdan-Inspiron-N5040 NetworkManager[926]: <info> (wlan0): supplicant interface state: associating -> associated
Jan 21 09:36:25 bogdan-Inspiron-N5040 NetworkManager[926]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jan 21 09:36:26 bogdan-Inspiron-N5040 wpa_supplicant[998]: WPA: Key negotiation completed with 72:c0:6f:21:26:d8 [PTK=CCMP GTK=CCMP]
Jan 21 09:36:26 bogdan-Inspiron-N5040 wpa_supplicant[998]: CTRL-EVENT-CONNECTED - Connection to 72:c0:6f:21:26:d8 completed (auth) [id=0 id_str=]
Jan 21 09:36:26 bogdan-Inspiron-N5040 NetworkManager[926]: <info> (wlan0): supplicant interface state: 4-way handshake -> group handshake
Jan 21 09:36:26 bogdan-Inspiron-N5040 NetworkManager[926]: <info> (wlan0): supplicant interface state: group handshake -> completed
Jan 21 09:36:26 bogdan-Inspiron-N5040 NetworkManager[926]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'LinuxApt'.
Jan 21 09:36:26 bogdan-Inspiron-N5040 NetworkManager[926]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 21 09:36:26 bogdan-Inspiron-N5040 NetworkManager[926]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan 21 09:36:26 bogdan-Inspiron-N5040 NetworkManager[926]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan 21 09:36:26 bogdan-Inspiron-N5040 NetworkManager[926]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 21 09:36:26 bogdan-Inspiron-N5040 NetworkManager[926]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan 21 09:36:26 bogdan-Inspiron-N5040 NetworkManager[926]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan 21 09:36:26 bogdan-Inspiron-N5040 dhclient: Listening on LPF/wlan0/e4:d5:3d:90:dc:5e
Jan 21 09:36:26 bogdan-Inspiron-N5040 dhclient: Sending on   LPF/wlan0/e4:d5:3d:90:dc:5e
Jan 21 09:36:26 bogdan-Inspiron-N5040 dhclient: DHCPREQUEST of 192.168.1.102 on wlan0 to 255.255.255.255 port 67
Jan 21 09:36:26 bogdan-Inspiron-N5040 NetworkManager[926]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jan 21 09:36:26 bogdan-Inspiron-N5040 NetworkManager[926]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 21 09:36:26 bogdan-Inspiron-N5040 NetworkManager[926]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 21 09:36:26 bogdan-Inspiron-N5040 NetworkManager[926]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan 21 09:36:26 bogdan-Inspiron-N5040 avahi-daemon[933]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.102.
Jan 21 09:36:26 bogdan-Inspiron-N5040 avahi-daemon[933]: New relevant interface wlan0.IPv4 for mDNS.
Jan 21 09:36:26 bogdan-Inspiron-N5040 avahi-daemon[933]: Registering new address record for 192.168.1.102 on wlan0.IPv4.
Jan 21 09:36:27 bogdan-Inspiron-N5040 NetworkManager[926]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan 21 09:36:27 bogdan-Inspiron-N5040 NetworkManager[926]: <info> Policy set 'LinuxApt' (wlan0) as default for IPv4 routing and DNS.
Jan 21 09:36:27 bogdan-Inspiron-N5040 NetworkManager[926]: <info> Activation (wlan0) successful, device activated.
Jan 21 09:36:27 bogdan-Inspiron-N5040 NetworkManager[926]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 21 09:36:27 bogdan-Inspiron-N5040 NetworkManager[926]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 21 09:40:42 bogdan-Inspiron-N5040 NetworkManager[926]: <info> Policy set 'LinuxApt' (wlan0) as default for IPv4 routing and DNS.
```nm-tool
```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [LinuxApt] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           no
  HW Address:        E4:D5:3D:90:DC:5E

  Capabilities:
    Speed:           13 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    NewBusiness50:   Infra, 00:19:70:27:E9:4F, Freq 2457 MHz, Rate 54 Mb/s, Strength 20
    RomTelecom-WPA-7821: Infra, 72:C0:6F:20:78:21, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2
    PETRU:           Infra, 72:C0:6F:20:78:20, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WEP
    HG520b:          Infra, 00:24:D2:A6:7D:71, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    NewBusiness10:   Infra, 00:4F:62:17:22:9D, Freq 2432 MHz, Rate 54 Mb/s, Strength 29
    RomTelecom-WEP-C022: Infra, 7A:4C:A9:A5:C0:20, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WEP
    iulian:          Infra, 72:C0:6F:20:B0:18, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WEP
    RomTelecom-WPA-EE58: Infra, 7A:54:99:1F:EE:59, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    lucica66:        Infra, 7A:54:99:1F:EE:58, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA
    RomTelecom-WPA-C022: Infra, 7A:4C:A9:A5:C0:21, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    PAMNET:          Infra, 00:90:D0:E7:34:06, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA
    RomTelecom-WPA-26DB: Infra, 72:C0:6F:21:26:D9, Freq 2447 MHz, Rate 54 Mb/s, Strength 94 WPA2
    *LinuxApt:       Infra, 72:C0:6F:21:26:D8, Freq 2447 MHz, Rate 54 Mb/s, Strength 95 WPA

  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        24:B6:FD:01:9C:EC

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220

```dmesg | grep ath
```
[   11.771143] ath9k 0000:12:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.771159] ath9k 0000:12:00.0: setting latency timer to 64
[   11.822307] ath: EEPROM regdomain: 0x60
[   11.822309] ath: EEPROM indicates we should expect a direct regpair map
[   11.822312] ath: Country alpha2 being used: 00
[   11.822313] ath: Regpair used: 0x60
[   12.134644] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.135198] Registered led device: ath9k-phy0
[   14.096036] type=1400 audit(1327131381.636:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=958 comm="apparmor_parser"

```

---

### Post by JavaQueen on 2012-01-21
This helped me out, too! Thank you so much!

---

### Post by wildmanne39 on 2012-01-21
Hi dezideriu_candid, which network are you connecting too? and when you changed everything and tested for increased speed did you have your wired connection unplugged? 

The reason I asked is that if the wired was plugged in then it would have taken over and not your wireless.
Thanks

---

### Post by xchecker on 2012-01-21
Wildman -

For your info and those reading the thread, my connection has been fixed by replacing the adapter I was using.  I've kept all the other settings you suggested and I'm blazing along now.  For those who care, I got a TP-Link TL-WN722N and it was plug and play - excellent!

Thanks again.

---

### Post by wildmanne39 on 2012-01-21
Hi xchecker, that is good to know and I am glad it is working.

---

### Post by idskot on 2012-01-23
Hey, Wildmanne, I was wondering if you could help me as well!

My internet on Windows 7 is capable of downloading (VIA Torrents / From Servers) at upwards of 1.3 MB/s. Although, on Linux it seems like it caps at 100kB/s. I was wondering if you could help me speed it up a bit.

(New to Linux, btw!)


lspci -nnk | grep -iA2 net results:
```
scott@Scott-Linux:~$ lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Kernel driver in use: r8169
--
05:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Melco Inc Buffalo WLI2-PCI-G54S High Speed Mode Wireless Desktop Adapter [1154:0330]
    Kernel driver in use: b43-pci-bridge

```lsmod results:
```
scott@Scott-Linux:~$ lsmod
Module                  Size  Used by
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83507  0 
hfs                    49479  0 
minix                  31444  0 
ntfs                  100171  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55577  2 vfat,msdos
jfs                   175084  0 
xfs                   746832  0 
reiserfs              230932  0 
dm_crypt               22565  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
nvidia              10390874  40 
snd_hda_codec_hdmi     31426  4 
binfmt_misc            17292  1 
ppdev                  12849  0 
arc4                   12473  2 
uvcvideo               67271  0 
joydev                 17393  0 
snd_usb_audio         100930  1 
snd_usbmidi_lib        24558  1 snd_usb_audio
videodev               85626  1 uvcvideo
b43                   318816  0 
snd_hda_codec_realtek   254125  1 
mac80211              393459  1 b43
snd_hda_intel          24262  5 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_pcm                80435  5 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
cfg80211              172427  2 b43,mac80211
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  23 snd_hda_codec_hdmi,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32114  1 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
vesafb                 13489  1 
ahci                   21634  2 
hid_sony               12667  0 
usbhid                 41905  0 
hid                    77367  2 hid_sony,usbhid
ssb                    50682  1 b43
libahci                25727  1 ahci
r8169                  43104  0 
pata_jmicron           12651  0 

```

---

### Post by dezideriu_candid on 2012-01-24
Hello every one!
Sorry for the slow reply wildmanne. When I tested your solution I had the cable unplugged and still it didn't work. Now I moved from there (that was my parents' house) to someplace else where the only possibility to connect  is wireless (that's why I was so desperate about it, because I knew I needed here). Everything seems to work fine for the moment. I'm thinking there was a problem of compatibility between the driver for my AR9285 and the router configuration. I'm thinking the problem persists with other routers. I'd like to solve it but there's no possibility I can test that now.

Anyway thanks a lot for your patience! If I have any troubles I will probably bug you again. If you need an output of a specific command to check out any differences between the non working wireless and the working one I will gladly post it. Maybe it helps somebody. 

Thank again!

---

### Post by downlink on 2012-01-28
Hey guys, I'm new to Ubuntu but I really like the freedom so I switched over from Windows 7, recently installing Ubuntu 11.10 but I went from having 50Mb/s download speeds to only 20Mb/s. When I plug in to my router I'm back at 50Mb/s speeds so I know its a problem with my wireless card on Ubuntu. I checked the power management settings and it says its off. I've tried most of the solutions given on this thread but I can't quite get it to work. Here's some basic info:



root@downlink:~# lspci -nnk | grep -iA2 net

02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [8086:0091] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6230 AGN [8086:5201]
    Kernel driver in use: iwlagn
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Sony Corporation Device [104d:907b]
    Kernel driver in use: r8169


root@downlink:~# lsmod

Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
btusb                  18600  0 
bluetooth             166112  11 bnep,rfcomm,btusb
joydev                 17693  0 
tpm_infineon           17536  0 
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
snd_seq_midi_event     14899  1 snd_seq_midi
v4l2_compat_ioctl32    17083  1 videodev
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
tpm_tis                18546  0 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                3101196  0 
i915                  566711  2 
sony_laptop            45393  0 
psmouse                73882  0 
serio_raw              13166  0 
iwlagn                314213  0 
drm_kms_helper         42558  1 i915
mac80211              310872  1 iwlagn
drm                   236330  3 i915,drm_kms_helper
rts_pstor             445246  0 
cfg80211              199587  2 iwlagn,mac80211
i2c_algo_bit           13423  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
libahci                26861  1 ahci
xhci_hcd               78641  0 
r8169                  52788  0

---

### Post by dvsarchitect on 2012-01-30
For any noob that has tried this solution to no end, I assure you this solution is real.

However, the sample code that appears several hundred times throughout this thread is just that... sample code. It won't necessarily be the same for each user. Especially in each of Wildeman's posts where he refers to:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
ath9k happened to be the variable I was missing. For my instance it happened to be, **ath5k**.

Be sure to run:
```
lspci -nnk | grep -iA2 net
```
and
```
lsmod
```
Look at the listing for "mac80211" and replace all instances of wildemans' ath9k code fixes with that.

EXAMPLE: My "mac80211" listing = ath5k
SOLUTION:
```
gksudo gedit /etc/modprobe.d/ath5k.conf
```
Add a single line:
```
options ath5k nohwcrypt=1
```

Worked like a charm in Ubtunu 11.10 and Linux Mint 12.

---

### Post by DarrenMeerwald on 2012-01-31
Thanks from me too.It helped get the frustratingly slow internet on my Acer Aspire 8950G  with Ubuntu 11.10 useable again.

---

### Post by wildmanne39 on 2012-02-03
Hi dezideriu_candid, glad you have a good connection at your new home and yes compatibility with routers or the router settings cause many issues but we tried everything that I know of to get around them.
Thanks

---

### Post by wildmanne39 on 2012-02-03
Hi dvsarchitect, thanks for posting your solution > However, the sample code that appears several hundred times throughout this thread is just that... sample code. It won't necessarily be the same for each user. Especially in each of Wildeman's posts where he refers to:
actually is not sample code it is the specific solution to each posters issue based on the information they posted from the commands I gave them.

That is why I always ask for information first so I know what wireless device we are dealing with.
Thanks

---

### Post by wildmanne39 on 2012-02-03
Hi downlink, please try this:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up
```
please do not restart, and if it help we will need to make it permanent.
Thanks

---

### Post by downlink on 2012-02-06
Thanks for the reply but that's what I'd already tried when I said I'd tried the solutions given. It wasn't a matter of power management, I think it actually had to do with the kernel driver I was using. I upgraded to iwlwifi from the compat-wireless release and that seems to have fixed my speed problem. I'm back at 50 Mb/s :)

---

### Post by wildmanne39 on 2012-02-06
Hi downlink, that is good to hear and thanks for sharing your solution.

---

### Post by CrossPlatform on 2012-02-13
I have a Lenovo S205 (perhaps not the wisest choice for a Laptop/Netbook destined to run only Linux).  Most things work fine (after working out that I needed to create a 2GB /dev/sda1 EFI boot partition and replace GRUB2 with Legacy Grub) under Ubuntu 11.10.  The laptop itself is great (and has very good battery life) but the Mini PCI Atheros 9285 WiFi card (which uses the ath9k kernel module) is terrible.  Even worse - the S205 has a Mini PCI whitelist in the UEFI BIOS and hardware blocks any other Mini PCI WiFi cards <sarcasm>'thanks' Lenovo</sarcasm>.  I presume this is an agreement between Atheros and Lenovo?

In order to get the card to work at all I have to run this on boot (rc.local)

```
ifconfig wlan0 down > /dev/null 2>&1
rmmod -f ath9k
rfkill unblock wifi
rfkill unblock all
modprobe -r acer_wmi
modprobe ath9k nohwcrypt=1
ifconfig wlan0 up > /dev/null 2>&1
# Optional following line (does not make any difference)
iwconfig wlan rate 54M
```I have tried putting kernel options in /etc/modprobe.d/ath9k.conf, blacklisting acer_wmi and everything else that I can think of.  Nothing works except the above sequence and even then I rarely get more than 100Kbyte/sec out of the WiFi (when I can easily get 1.5MByte/sec from other cards).

This is NOT solved at all (at least NOT on the S205).  None of the (otherwise very helpful - so thanks) fixes posted on this topic seem to work on the S205 :(

I have downloaded the latest source code for the WiFi kernel drivers and built that and it doesn't make any difference.  If I blacklist ath9k and try the MadWifi drivers then I cannot unblock the hardware.  If I blacklist ath9k and use an external USB WiFi card then it doesn't work UNTIL the ath9k has initialized by the above script (and then been disconnected!)

If only Coreboot ([http://www.coreboot.org/Welcome_to_coreboot](http://www.coreboot.org/Welcome_to_coreboot) ) would work on this laptop!

I have modified kernel drivers before and IF I had SOME pointers would be quite willing to have a go but this driver does seem pretty broken on a number of Atheros cards.

---

### Post by chili555 on 2012-02-13
> BIOS and hardware blocks any other Mini PCI WiFi cards <sarcasm>'thanks' Lenovo</sarcasm>. I presume this is an agreement between Atheros and Lenovo?I think this is a concession to the FCC and Lenovo's nervous lawyers. I believe the intent is to insure that the laptop, shipped from China, will absolutely comply with US regulatory domain requirements; not just channels received and transmitted, but signal strength. I think the FAA would also like to have assurance that the wireless radio is absolutely defeatable with a hardware switch.

Whitelists are very common and not limited to Atheros cards. [http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card](http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card)

My T40 is using an 'unauthorized' card using no-1802 methods.

I think acer-wmi is the culprit here, not the ath9k driver. I'd love to see you blacklist acer-wmi, comment out some rc.local lines like this:```
#ifconfig wlan0 down > /dev/null 2>&1
rmmod -f ath9k
#rfkill unblock wifi
rfkill unblock all
#modprobe -r acer_wmi
modprobe ath9k nohwcrypt=1
#ifconfig wlan0 up > /dev/null 2>&1
# Optional following line (does not make any difference)
#iwconfig wlan rate 54M
```Reboot and show us:```
iwconfig
rfkill list all
```Once we see that result, we can better decide on the next steps, if any.

PS- If you are not in the US, well...never mind!

---

### Post by CrossPlatform on 2012-02-14
Firstly thank you chili555 for your prompt and kind reply.  Is is people like you that make the Ubuntu Community such a wonderful source of help :)

I did follow the instructions to the letter and ended up with a WiFi card that was hard blocked.  Loading/removing the acer_wmi module must unblock the Atheros 9285 card on the S205 for some reason.

iwconfig output

```

lo        no wireless extensions.
eth0      no wireless extensions.

virbr0    no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```rfkill list all output
```

0: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```It isn't VMware Player either by the way - I purged this off my system and tried previously - and it does not make the slightest bit of difference.  As you suspected I live in the 51st State of the USA (aka United Kingdom) so I won't have to mind ;)  If I unblacklist acer_wmi and add the "modprobe -r acer_wmi" line back in then

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

virbr0    no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"wireless guest"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:A9:42:11:71   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:18   Missed beacon:0

```rfkill list all
```

0: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```and I have working but VERY SLOW (< 100KBytes/sec) WiFi!

I suspect that I need SOME of the code from the acer_wmi module to get the S205 working properly but not most of it.

---

### Post by CrossPlatform on 2012-02-14
Oh I forgot to add this - loaded modules list

```
Module                  Size  Used by
ath9k                 134892  0 
bnep                   18139  2 
rfcomm                 46622  8 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
ip6table_filter        12815  0 
ip6_tables             27864  1 ip6table_filter
ipt_MASQUERADE         12759  3 
iptable_nat            13229  1 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  4 iptable_nat,nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_state               12578  1 
nf_conntrack           82342  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT             12576  2 
xt_CHECKSUM            12549  1 
iptable_mangle         12734  1 
xt_tcpudp              12603  5 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 ip6table_filter,ip6_tables,ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_CHECKSUM,iptable_mangle,xt_tcpudp,iptable_filter,ip_tables
bridge                 90905  0 
stp                    12931  1 bridge
dm_crypt               23199  1 
vmnet                  55617  13 
ppdev                  17113  0 
parport_pc             36962  0 
vsock                  52475  0 
joydev                 17693  0 
vmci                   86575  1 vsock
vmmon                  80498  0 
kvm_amd                59832  0 
kvm                   383773  1 kvm_amd
rts5139               351143  0 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
btusb                  18295  2 
bluetooth             185424  23 bnep,rfcomm,btusb
binfmt_misc            17540  1 
arc4                   12529  2 
snd_hda_codec_conexant    62197  1 
mac80211              511030  1 ath9k
snd_hda_codec_hdmi     32040  1 
ath9k_common           14053  1 ath9k
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
ath9k_hw              413407  2 ath9k,ath9k_common
snd_hwdep              13668  1 snd_hda_codec
snd_seq_midi           13324  0 
psmouse                73882  0 
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
nls_iso8859_1          12713  1 
serio_raw              13166  0 
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
nls_cp437              16991  1 
snd_rawmidi            30547  1 snd_seq_midi
vfat                   17585  1 
fat                    61475  1 vfat
k10temp                13166  0 
cfg80211              209841  3 ath9k,mac80211,ath
sp5100_tco             13791  0 
i2c_piix4              13301  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ideapad_laptop         13871  0 
sparse_keymap          13890  1 ideapad_laptop
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
fglrx                2928969  105 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
r8169                  56121  0 
ahci                   26002  4 
libahci                26861  1 ahci
video                  19412  0 

```

---

### Post by chili555 on 2012-02-14
You will not be surprised to know this is an ongoing issue. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775414](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775414)

What kernel version are you running?```
uname -r
```Do you feel adventerous and would you like to try the fix at post #12? At the least, I suggest you register with Launchpad and add to the bug report.

---

### Post by eduloni on 2012-02-14
hello 

lspci -nnk | grep -iA2 net gives me the following:

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8185]
    Kernel driver in use: rtl8192ce
--
08:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Kernel driver in use: atl1c

smod gives me the following:

Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
joydev                 17693  0 
snd_hda_codec_conexant    62197  1 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
radeon               1015995  3 
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236330  5 radeon,ttm,drm_kms_helper
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
i2c_algo_bit           13423  1 radeon
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
serio_raw              13166  0 
sp5100_tco             13791  0 
rtl8192ce              84775  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               110972  1 rtl8192ce
mac80211              310872  3 rtl8192ce,rtl8192c_common,rtlwifi
soundcore              12680  1 snd
edac_core              53746  0 
k10temp                13166  0 
cfg80211              199587  2 rtlwifi,mac80211
edac_mce_amd           23709  0 
shpchp                 37345  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_piix4              13301  0 
wmi                    19256  0 
sparse_keymap          13890  0 
binfmt_misc            17540  1 
video                  19412  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
libahci                26861  1 ahci
atl1c                  41643  0 
ums_realtek            13272  0 
usb_storage            57901  1 ums_realtek
uas                    18027  0


can anyone healp me plz?

---

### Post by CrossPlatform on 2012-02-14
Hi Chilli555 and thanks for the pointers

uname -a
```

Linux tachyon 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

I tried the test-dkms package as suggested but alas it didn't work.  Here are the outputs from iwconfig, rfkill and lsmod

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

virbr0    no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off


```

rfkill list all
```

0: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

Such a shame - hard blocked again!

lsmod
```

Module                  Size  Used by
ath9k                 134892  0 
bnep                   18139  2 
rfcomm                 46622  8 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
ip6table_filter        12815  0 
ip6_tables             27864  1 ip6table_filter
ipt_MASQUERADE         12759  3 
iptable_nat            13229  1 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  4 iptable_nat,nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_state               12578  1 
nf_conntrack           82342  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT             12576  2 
xt_CHECKSUM            12549  1 
iptable_mangle         12734  1 
xt_tcpudp              12603  5 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 ip6table_filter,ip6_tables,ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_CHECKSUM,iptable_mangle,xt_tcpudp,iptable_filter,ip_tables
vmnet                  55617  10 
bridge                 90905  0 
stp                    12931  1 bridge
parport_pc             36962  0 
ppdev                  17113  0 
dm_crypt               23199  1 
vsock                  52475  0 
joydev                 17693  0 
vmci                   86575  1 vsock
vmmon                  80498  0 
kvm_amd                59832  0 
kvm                   383773  1 kvm_amd
test                   28111  0 
rts5139               351143  0 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
btusb                  18295  2 
v4l2_compat_ioctl32    17083  1 videodev
bluetooth             185424  23 bnep,rfcomm,btusb
binfmt_misc            17540  1 
arc4                   12529  2 
mac80211              511030  1 ath9k
psmouse                73882  0 
serio_raw              13166  0 
ath9k_common           14053  1 ath9k
ath9k_hw              413407  2 ath9k,ath9k_common
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
k10temp                13166  0 
cfg80211              209841  3 ath9k,mac80211,ath
nls_iso8859_1          12713  1 
sp5100_tco             13791  0 
nls_cp437              16991  1 
vfat                   17585  1 
i2c_piix4              13301  0 
fat                    61475  1 vfat
ideapad_laptop         13871  0 
sparse_keymap          13890  2 test,ideapad_laptop
snd_hda_codec_conexant    62197  1 
fglrx                2928969  88 
snd_hda_codec_hdmi     32040  1 
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
r8169                  56121  0 
ahci                   26002  4 
libahci                26861  1 ahci
video                  19412  0 
wmi                    19256  1 test

```

Have to remove the test-dkms package, unblacklist acer-wmi and go back to the current WiFi initialization unfortunately.

dmesg (extract)
```

[   26.893837] ath9k 0000:03:00.0: PCI INT A disabled
[   26.893919] ath9k: Driver unloaded
[   26.932296] acer_wmi: Acer Laptop WMI Extras unloaded
[   26.948350] wmi: Mapper unloaded
[   26.967871] ath9k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.967895] ath9k 0000:03:00.0: setting latency timer to 64
[   27.049520] ath: EEPROM regdomain: 0x65
[   27.049529] ath: EEPROM indicates we should expect a direct regpair map
[   27.049536] ath: Country alpha2 being used: 00
[   27.049540] ath: Regpair used: 0x65
[   27.049548] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   27.049555] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.049560] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   27.049566] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.049571] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   27.049577] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.049581] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   27.049587] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.049591] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   27.049597] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.049601] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   27.049607] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.049611] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   27.049617] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.049622] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   27.049627] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.049632] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   27.049637] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.049641] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   27.049647] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.049651] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   27.049657] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.049661] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   27.049667] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.049672] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   27.049677] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.049682] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   27.051968] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   27.058399] ieee80211 phy1: Selected rate control algorithm 'ath9k_rate_control'
[   27.063059] Registered led device: ath9k-phy1
[   27.063082] ieee80211 phy1: Atheros AR9285 Rev:2 mem=0xffffc900030a0000, irq=18

```

Is there anything else I can do to help - debugging-wise (like me actually doing the work rather than someone else parsing long sequences of my own logs!)

---

### Post by CrossPlatform on 2012-02-14
Yeah will add a bug report to Bug #775414
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775414](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775414)

but would like to help rather than generating work for other people!

---

### Post by chili555 on 2012-02-14
You might try to see what acer-wmi is doing under the hood:```
sudo cat /var/log/syslog | grep acer
```If the output is sparse, look in syslog.1.

I notice this:> $ modinfo acer-wmi
filename:       /lib/modules/3.0.0-15-generic/kernel/drivers/platform/x86/acer-wmi.ko
alias:          wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026
alias:          wmi:6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3
alias:          wmi:67C3371D-95A3-4C37-BB61-DD47B491DAAB
license:        GPL
description:    Acer Laptop WMI Extras Driver
author:         Carlos Corbacho
srcversion:     302311E1F70D1B1462328D7
depends:        sparse-keymap,wmi
vermagic:       3.0.0-15-generic SMP mod_unload modversions 686 
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
[COLOR="Red"]parm:           force_series:Force a different laptop series (int)[/COLOR]
parm:           ec_raw_mode:Enable EC raw mode (bool)We might Google for your particular Lenovo and see if there is a 'series' designation. You might also check in dmesg for the series; perhaps something like this from my machine (a Lwenovo T60):> [    0.000000] ACPI: DSDT 7fed195e 0D2D9 (v01 LENOVO TP-7I    00001170 MSFT 0100000E)
<snip>
[    8.996134] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[    8.996139] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[    8.996142] thinkpad_acpi: ThinkPad BIOS 7IET36WW (1.17 ), EC 79HT50WW-1.07
[    8.996145] thinkpad_acpi: Lenovo ThinkPad T60, model 8743CTO
[    8.996885] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[    8.997723] thinkpad_acpi: radio switch found; radios are enabled
<snip>Is there any recognition of the wireless key combination; Fn+Fwhatever?

---

### Post by chili555 on 2012-02-14
I also notice this:> less /usr/src/linux-source-2.6.38/Documentation/laptops/acer-wmi.txt

<snip>
acer-wmi creates /sys/devices/platform/acer-wmi, and fills it with various
files whose usage is detailed below, which enables you to control some of the
following (varies between models):

* the wireless LAN card radio
<snip>Do you have that file? Can you force the correct state? Something like:```
echo 1 > /sys/devices/platform/acer-wmi/wireless
```...or some such.

---

### Post by CrossPlatform on 2012-02-14
I noticed this kernel bug report
[https://bugzilla.kernel.org/show_bug.cgi?id=37892](https://bugzilla.kernel.org/show_bug.cgi?id=37892)

and this diff patch of acer-wmi.c for the Lenovo S205
[http://permalink.gmane.org/gmane.linux.drivers.platform.x86.devel/2349](http://permalink.gmane.org/gmane.linux.drivers.platform.x86.devel/2349)

Might try building a new kernel module and trying to backport the kernel 3.1 changes back to 3.0.  Perhaps it is fixed in 12.04 LTS!  I guess the next thing is to download the latest Alpha of 12.04 and boot from a USB stick and try it!

I can't see /sys/devices/platform/acer-wmi at the moment because (obviously) I unloaded the module!  Will try some more hacks...

From my syslog
```

Feb 14 11:33:31 tachyon kernel: [   18.319980] acer_wmi: Acer Laptop ACPI-WMI Extras
Feb 14 11:33:32 tachyon NetworkManager[1036]: <info> found WiFi radio killswitch rfkill3 (at /sys/devices/platform/acer-wmi/rfkill/rfkill3) (driver acer-wmi)
Feb 14 11:33:39 tachyon kernel: [   26.566289] acer_wmi: Acer Laptop WMI Extras unloaded
Feb 14 11:33:39 tachyon NetworkManager[1036]: <info> radio killswitch /sys/devices/platform/acer-wmi/rfkill/rfkill3 disappeared
Feb 14 14:44:31 tachyon kernel: [   18.093993] acer_wmi: Acer Laptop ACPI-WMI Extras
Feb 14 14:44:31 tachyon NetworkManager[959]: <info> found WiFi radio killswitch rfkill3 (at /sys/devices/platform/acer-wmi/rfkill/rfkill3) (driver acer-wmi)
Feb 14 14:44:40 tachyon NetworkManager[959]: <info> radio killswitch /sys/devices/platform/acer-wmi/rfkill/rfkill3 disappeared
Feb 14 14:44:40 tachyon kernel: [   26.932296] acer_wmi: Acer Laptop WMI Extras unloaded

```

There is no documentation folder within /usr/src/linux-source-3.0.0 and alas I don't have the module options documentation.  Time to hack the module I think :)

---

### Post by chili555 on 2012-02-14
What is here?```
cat /sys/devices/platform/acer-wmi/rfkill/rfkill3
```While acer-wmi is loaded, can you force the opposite state; i.e. if 0 force 1, etc.```
sudo echo 1 > /sys/devices/platform/acer-wmi/rfkill/rfkill3 
```Maybe that's all we need to do in rc.local.> There is no documentation folder within /usr/src/linux-source-3.0.0 and alas I don't have the module options documentation.Here is what I have.

---

### Post by eduloni on 2012-02-14
hi im new in ubuntu. my wifi is very slow, im usin a toshiba sattelite l645-s4056 with ubutu 11.10 
can anyone help me :)????

sory if my english is no good

---

### Post by chili555 on 2012-02-14
> **eduloni said:**
> hi im new in ubuntu. my wifi is very slow, im usin a toshiba sattelite l645-s4056 with ubutu 11.10 
can anyone help me :)????

sory if my english is no goodYour English is fine enough; no worries. Would you please start your own new thread and include:```
lspci -nn | grep 0280
iwconfig
```Leave a link here to the new thread, please.

---

### Post by eduloni on 2012-02-14
[http://ubuntuforums.org/showthread.php?p=11689140#post11689140](http://ubuntuforums.org/showthread.php?p=11689140#post11689140)

---

### Post by littlealmond on 2012-02-14
Hi, my internet was very slow too but I used the following as adviced:

sudo ifconfig wlan0 down sudo rmmod -f ath5k sudo modprobe ath5k nohwcrypt=1 sudo ifconfig wlan0 up

and solved it! however I can't make it permanent I opened

gksudo gedit /etc/modprobe.d/ath9k.conf

but it was an empty document so I just added
options ath9k nohwcrypt=1

saved and left, don't know if I did something wrong 

Thank you!!

---

### Post by wildmanne39 on 2012-02-15
Hi littlealmond, this is what you need to do if your driver is ath5k like you think:
```
gksudo gedit /etc/modprobe.d/ath5k.conf
```
Add a single line:
```
options ath5k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by CrossPlatform on 2012-02-15
Thanks wildmanne39 - but I have been following this thread and the kernel threads about the ath9k/acer-wmi for a while and that was one of the first things I tried.  In my case alas it does not work (either for the ath5k driver or ath9k driver).  I have tried every combination of ath5k, ath9k and MadWiFi driver and options that I can think of and I still have very slow WiFi.  Your kindly suggested modprobe option does not improve the speed in my case.

I have a Belkin F5D8053 USB WiFi dongle and if I disable the Atheros and use that instead - I can get 1.5MByte/sec download rates on the current (admittedly congested) network so it is not the WiFi hub which is at fault.

Others have got the Ath9k driver to work fine so I suspect that it is an artefact of the Lenovo S205 - probably some interaction with the acer-wmi module.  If I don't load/remove the acer-wmi driver then the ath9k module remains hard locked.  If I follow the sequence

```

rmmod -f ath9k
rfkill unblock all
modprobe -r acer_wmi
modprobe ath9k nohwcrypt=1

```after the main kernel initialization (e.g. in /etc/rc.local) then it works BUT at a very slow rate.  If I blacklist acer_wmi then it does NOT work at all.

Tricky huh!  I suspect that I need to modify the acer-wmi  module as per this link
[http://permalink.gmane.org/gmane.linux.drivers.platform.x86.devel/2349](http://permalink.gmane.org/gmane.linux.drivers.platform.x86.devel/2349)

---

### Post by CrossPlatform on 2012-02-15
As an addendum to this - if I miss out the step removing the acer_wmi module then not only does the ath9k based card remain hard blocked but so does the external USB Belkin WiFi dongle (how weird is that!) Must be related to the hard block (switch) functionality and yes the switch is always enabled!

---

### Post by wildmanne39 on 2012-02-15
Hi CrossPlatform, the method I mentioned in post 231 is for littlealmonds issue.

I am going to let chili555 help you he is much more experienced then I am.
Thanks

---

### Post by littlealmond on 2012-02-15
Thank you very much wildmanne39 it's completely solved!!!! I can enjoy my ubuntu now :KS:KS:KS__

---

### Post by wildmanne39 on 2012-02-15
Hi littlealmond, your welcome!
Enjoy

---

### Post by Questionario on 2012-02-21
Hi,

I also have a problem with slow wireless lan on my Zotac AD10 with Atheros 9285 chipset.
I am running Lubuntu 11.10.
Sometimes the speed breaks down to below 100kbyte/s and usually doesn't go above ~700kbyte/s on average. when it gets real tough and the neighbours download something (I am assuming as I can't see a pattern to when this is happening) the WLAN even keeps disconnecting. even my router (Netgear DGN3500B) gets messed up by the linux-wlan and keeps sometimes keeps disconnecting wireless lan and/or the dsl, this does not go away until I pull the power from the router. All this only happens with Linux/Ubuntu (even worse with OpenElec, which is not based on ubuntu). If I use windowsXP with the original drivers from the CD, I get rates over 3mbytes/s (probably the speed limit of my thumbdrive) even with both ends using wireless lan.

Here is the output of some commands you requested from other users before, I did try the nowhcrypt=1 but this didn't fix the issue, I tried installing wicd and uninstalling network-manager but that didnt help either (I undid that one).
I disabled IPv6 (but kept normal DHCP, not just addresses...)

any idea?

```
xbmc@XBMCBuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10 - XBMCbuntu"
Linux XBMCBuntu 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686 athlon i386 GNU/Linux
xbmc@XBMCBuntu:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
        Subsystem: AzureWave Device [1a3b:2c37]
        Kernel driver in use: ath9k
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
        Subsystem: ZOTAC International (MCO) Ltd. Device [19da:a176]
        Kernel driver in use: r8169
xbmc@XBMCBuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [MyWLAN] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        AB:CD:EF:12:34:56

  Capabilities:
    Speed:           108 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *MyWLAN: Infra, 12:34:56:AB:CD:EF, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA2
    FRITZ!Box Fon WLAN 7141: Infra, 00:04:0E:F2:31:4D, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA
    *MyWLAN: Infra, 12:34:56:AB:CD:EF, Freq 2412 MHz, Rate 54 Mb/s, Strength 57
    FRITZ!Box Fon WLAN 7170: Infra, 00:1C:4A:A4:2F:F0, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    zentrum-wg-02:   Infra, 00:1B:2F:55:D4:C4, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    zentrum-wg-01:   Infra, 00:22:3F:2A:8A:DE, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    dlink:           Infra, 00:22:B0:9B:98:0B, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    ASNOTEBOOK:      Infra, 00:23:08:C0:A1:12, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    TP-LINK_1B3641:  Infra, 00:23:CD:1B:36:41, Freq 2432 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.16
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:01:22:33:DD:11

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


xbmc@XBMCBuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"MyWLAN"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 12:34:56:AB:CD:EF
          Bit Rate=108 Mb/s   Tx-Power=15 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=45/70  Signal level=-65 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:58   Missed beacon:0

xbmc@XBMCBuntu:~$ rfkill list all
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
xbmc@XBMCBuntu:~$ lsmod
Module                  Size  Used by
dvb_usb_dib0700        80531  7
dib7000p               34073  2 dvb_usb_dib0700
dib0090                32688  1 dvb_usb_dib0700
dib7000m               22965  1 dvb_usb_dib0700
dib0070                18150  2 dvb_usb_dib0700
dvb_usb                23788  1 dvb_usb_dib0700
dib8000                42094  1 dvb_usb_dib0700
dvb_core               94826  3 dib7000p,dvb_usb,dib8000
dib3000mc              22920  1 dvb_usb_dib0700
dibx000_common         18418  5 dvb_usb_dib0700,dib7000p,dib7000m,dib8000,dib3000mc
ir_lirc_codec          12770  3
lirc_dev               18700  1 ir_lirc_codec
ath3k                  13011  0
arc4                   12473  2
ath9k                 112711  0
mac80211              393421  1 ath9k
ath9k_common           13599  1 ath9k
ath9k_hw              293933  2 ath9k,ath9k_common
ath                    19387  2 ath9k,ath9k_hw
cfg80211              172427  3 ath9k,mac80211,ath
rfcomm                 38408  0
autofs4                27924  1
dm_crypt               22565  0
rc_dib0700_rc5         12460  0
snd_hda_codec_hdmi     31426  1
snd_hda_intel          24262  2
snd_hda_codec          91859  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
btusb                  18160  0
bluetooth             148839  4 rfcomm,btusb
fglrx                2756852  68
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_sony_decoder        12493  0
rc_rc6_mce             12454  0
ir_jvc_decoder         12490  0
psmouse                73673  0
serio_raw              12990  0
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17393  0
ir_rc6_decoder         12490  0
sp5100_tco             13495  0
snd                    55902  12 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_rc5_decoder         12490  0
ir_nec_decoder         12490  0
ite_cir                24743  0
rc_core                25797  13 dvb_usb_dib0700,dvb_usb,ir_lirc_codec,rc_dib0700_rc5,ir_sony_decoder,rc_rc6_mce,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,ite_cir
i2c_piix4              13093  0
k10temp                12990  0
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0
parport                40930  1 lp
dm_raid45              76451  0
xor                    21860  1 dm_raid45
dm_mirror              21822  0
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1
hid_logitech           17405  0
ff_memless             12945  1 hid_logitech
usbhid                 41905  1 hid_logitech
hid                    77367  2 hid_logitech,usbhid
r8169                  43104  0
xhci_hcd               72982  0
pata_atiixp            12967  0
ahci                   21634  5
libahci                25727  1 ahci
xbmc@XBMCBuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 006: ID 14f7:0004 TechniSat Digital GmbH AirStar TeleStick 2
Bus 008 Device 002: ID 046d:0b07 Logitech, Inc.
Bus 008 Device 004: ID 046d:c71e Logitech, Inc.
Bus 008 Device 005: ID 046d:c71f Logitech, Inc. diNovo Mini Wireless Keyboard
Bus 005 Device 006: ID 0cf3:3005 Atheros Communications, Inc.
xbmc@XBMCBuntu:~$ cat /etc/modprobe.d/ath9k.conf
options ath9k nohwcrypt=1
xbmc@XBMCBuntu:~$

```

---

### Post by wildmanne39 on 2012-02-21
Hi, to start with someone else has the same name as your network this will cause issues and both are on the same channel. 

Did you make nowhcrypt=1 permanent? you should and leave it.
```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf . /dev/null

```
```
sudo iwconfig wlan0 power off
sudo iwconfig wlan0 rate auto
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
sudo service network-manager restart
```
That is all I know to do.
Thanks

---

### Post by Questionario on 2012-02-22
Hi,

yes I did leave that active (see second last line in the previous code output).

```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf . /dev/null
tee: .: Is a directory
``````
sudo sh wildmanne.sh
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
network-manager start/running, process 6577

```nameserver I would prefer to not use some external one but the one of my provider/my router if that doesn't give an improvement (I guess it won't as so far I have tested with IP and not something with external dns).


This did not improve the speed of my connection but as far as I can tell from the short time I have been running this computer now... the connection seems to be at least half stable. only one connection drop so far and the speed of the connection varies between 400kbyte/s-1mbyte/s. still a lot slower than with windows and considering that the antenna is like 1m apart from the access point... :-\

The speed doesn't even drop much if I completely disconnect the external omnidirectional antenna ([this one]("http://www.idealo.de/preisvergleich/OffersOfProduct/401988_-wlan-antenne-6-dbi-62770-hama.html")).

Thanks a lot for taking the time to take a look at my problem though!

Questionário

---

### Post by Questionario on 2012-02-22
I have changed the channel to have the least interference from other WLANs. Channel 1,5,6 and 11 all had one or even two access points, no 802.11b APs.
Channel 3 and 8 gave the best performance for me.
WLAN seems to stay stable for three evenings now. 
While I still don't nearly get the speed I get with Windows, I get 10-15Mbit/s which is good enough to stream 720p content.
I guess that's as good as it will get with Linux.
Thanks for the help!

Questionário

---

### Post by wildmanne39 on 2012-02-22
Hi, your welcome! we do the best we can with the drivers and wireless devices we have to work with, I wish I could do more but that is all I know.

I increased my speed a lot just by using googles dns server and it is secure.
Thanks

---

### Post by Questionario on 2012-02-23
Hi,

it was enough to make the speed and connection acceptable :-P
Google's DNS won't make a difference to me as I don't browse the web with that computer.
It is just XBMC running on Lubuntu to make it start fast (installed version of the latest beta xbmc from xbmc.org). The Media Center only needs to stream sometimes and only connect to the internet for small addon downloads or upgrades.

Again thanks for the help, looks like you have helped many people in this thread already :)

Questionário

---

### Post by parth.s on 2012-02-25
Hi I have a dual boot machine with 11.10 and win7. I use internet using wifi at my home.

Now my problem is that internet works just fine in win7. But in Ubuntu its really intermittent. Meaning the websites randomly take time to load. The response time is very slow. Its really annoying, when even Google takes like a min to load sometimes...

need some suggestions...

---

### Post by wildmanne39 on 2012-02-26
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by parth.s on 2012-02-26
@wildmanne39 thanks for the quick reply, I see that you have single evenhandedly taken care of this entire thread, good work man.. 

here it goes...

```
kingpin@kingpin-K53E:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux kingpin-K53E 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

kingpin@kingpin-K53E:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: AzureWave Device [1a3b:1139]
	Kernel driver in use: rtl8192ce
--
03:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
	Kernel driver in use: atl1c

kingpin@kingpin-K53E:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"DragonAge"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: E0:46:9A:50:28:C2   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:58   Missed beacon:0

kingpin@kingpin-K53E:~$ rfkill list all
0: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

kingpin@kingpin-K53E:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
joydev                 17693  0 
arc4                   12529  2 
asus_nb_wmi            12517  0 
asus_wmi               20035  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                73882  0 
serio_raw              13166  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rtl8192ce              84775  0 
wmi                    19256  1 asus_wmi
rtl8192c_common        75767  1 rtl8192ce
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rtlwifi               110972  1 rtl8192ce
mac80211              462046  3 rtl8192ce,rtl8192c_common,rtlwifi
i915                  571221  3 
drm_kms_helper         42558  1 i915
drm                   236290  4 i915,drm_kms_helper
mei                    41480  0 
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
cfg80211              199630  2 rtlwifi,mac80211
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
atl1c                  41643  0 
ahci                   26002  2 
libahci                26861  1 ahci


```

---

### Post by wildmanne39 on 2012-02-26
Hi, the wireless card you have is problematic in 11.10, there are a few things we can try but we have not had much success with your card in 11.10 lately. 

Please do:
```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf . /dev/null
```
then go to the internet icon in the top right of the screen and click on it then click edit connection and ipv6 and set it to ignore, use the screenshot and set yours to look like mine.
Then reboot
Thanks

---

### Post by parth.s on 2012-02-26
I have been facing the same problem with 11.04 too, and the driver that I have installed is not the default driver..I have downloaded and installed it myself as a suggestion from someone.

Regardless Im gonna try what you have suggested and let you know...

---

### Post by parth.s on 2012-02-26
I just did what you said. Right now I don't see much of a change, randomly websites are still taking time to get resolved and open.

Also to try it out, I did speedtest on my connection. I did it for like 6-7 times, the results were totally random from 1/6th to 1/2 my actual speed and only showing me the true speed in the last one...

Thanks a lot for your help, let me know if there is any other way..

---

### Post by wildmanne39 on 2012-02-26
Hi, since you already tried a newer driver there is not much else to try.

I have read that this issue is fixed in 12.04 so I guess it will be best to wait until it comes out in April.
Thanks

---

### Post by parth.s on 2012-02-26
I guess I'll have to wait for 12.04...Thanks for all the help..
Thanks

---

### Post by wildmanne39 on 2012-02-26
Your welcome!

---

### Post by jbobgray on 2012-02-27
Hello. I hope you could help me too.
I'm running ubuntu 11.10 with usb wireless Netgear Wg111v2. The internet is slow. Your help would very much appreciated.

Jay

here are the following details that you might need.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux jjay-GC679AA-ABG-a6160a 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux




00:19.0 Ethernet controller [0200]: Intel Corporation 82566DC-2 Gigabit Network Connection [8086:294c] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:2a5d]
	Kernel driver in use: e1000e



lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"BigPond942CBA"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:44:94:2C:BA   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:4770   Missed beacon:0


1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
jjay@jjay-GC679AA-ABG-a6160a:~$ lsmod
Module                  Size  Used by
rtl8187                56323  0 
eeprom_93cx6           12653  1 rtl8187
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
nvidia              10390874  40 
binfmt_misc            17292  1 
arc4                   12473  2 
rt73usb                27029  0 
rt2x00usb              20092  1 rt73usb
rt2x00lib              48146  2 rt73usb,rt2x00usb
mac80211              393421  3 rtl8187,rt2x00usb,rt2x00lib
cfg80211              172427  3 rtl8187,rt2x00lib,mac80211
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
serio_raw              12990  0 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  1 
uas                    17699  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  2 rt73usb,firewire_core
e1000e                139814  0 
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash


thanks.

---

### Post by wildmanne39 on 2012-02-27
Hi first do what I recommended in post 246 then post the output of:
```
modinfo rt73usb
```
Thanks

---

### Post by jbobgray on 2012-02-27
Hi. Done what was in 246.

He is the putput.

filename:       /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     A934BD4EDD13F40E6D1C5D3
alias:          usb:v0586p3415d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp001Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7167p3840d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v6933p5001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0024d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p4471d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0812p3101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp093Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p7318d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p4600d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0028d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p3701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7318d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v178Dp02BEd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0137d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0119d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0116d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00D9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00D8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08DDp0120d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Bd*dc*dsc*dp*ic*isc*ip*
depends:        rt2x00lib,rt2x00usb,crc-itu-t
vermagic:       3.0.0-16-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

thanks.

---

### Post by wildmanne39 on 2012-02-27
Hi, please do:
```
gksudo gedit /etc/modprobe.d/rt73usb.conf
```
Add a one line:
```
options rt73usb nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.

---

### Post by jbobgray on 2012-02-27
Thank you for your help. I have tested it and all good.
Thanks so much.

---

### Post by wildmanne39 on 2012-02-27
Hi, your welcome! I am glad I could help.
Enjoy

---

### Post by veroslav on 2012-02-29
Hi,

I am having the same problem as OP (slow wireless Internet) and I also have an Atheros AR9285 wireless card. I have tried to run the following four commands, the same ones as the OP was recommended to do:

```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```However, even though running the commands above run without problems, I am still having VERY slow Internet. Could somebody please help me out with this? Below I am attaching the outputs of "lspci -nnk | grep -iA2 net" and "lsmod" after running the above four commands. Thank you in advance.

```
user@user-laptop:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Dell Device [1028:0205]
    Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:04c4]
    Kernel driver in use: r8169
``````
user@user-laptop:~$ lsmod
Module                  Size  Used by
ath9k                 127538  0 
bnep                   18436  2 
rfcomm                 47946  0 
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
nouveau               728677  0 
ttm                    76805  1 nouveau
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104931  2 snd_hda_codec_realtek,snd_hda_intel
uvcvideo               72711  0 
snd_hwdep              13668  1 snd_hda_codec
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
dell_laptop            13831  0 
dcdbas                 14490  1 dell_laptop
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
btusb                  18600  1 
snd_rawmidi            30547  1 snd_seq_midi
bluetooth             166112  13 bnep,rfcomm,btusb
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              462046  1 ath9k
psmouse                73882  0 
serio_raw              13166  0 
ath9k_common           13839  1 ath9k
ath9k_hw              312914  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
i915                  571221  3 
cfg80211              199630  3 ath9k,mac80211,ath
drm_kms_helper         42558  2 nouveau,i915
mei                    41480  0 
drm                   236290  6 nouveau,ttm,i915,drm_kms_helper
soundcore              12680  1 snd
mxm_wmi                12979  1 nouveau
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  2 nouveau,i915
wmi                    19256  2 dell_wmi,mxm_wmi
video                  19412  2 nouveau,i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            13272  0 
usb_storage            57901  1 ums_realtek
uas                    18027  0 
ahci                   26002  2 
libahci                26861  1 ahci
r8169                  52788  0 
xhci_hcd               82820  0 
```

---

### Post by veroslav on 2012-03-01
Actually, after I restarted the computer, the speeds went up again and I was able to reach the max download rate available for my connection!

I don't know yet if this is going to persist on the next reboot or not, but I will keep an eye and post again if the connection speed drops again.

When I noticed the slow speeds, it was the first login I did after I installed Ubuntu 11.10 and directly after I successfully logged in to my wireless connection. Perhaps a restart was needed to get everything up and going at max?

Kind Regards,
Veroslav

---

### Post by shanyman on 2012-03-02
Thanks alot - legend!

---

### Post by wildmanne39 on 2012-03-03
Hi, let us know if you need more help, just know that I am not available much right now so my responses will be slow.
Thanks

---

### Post by jscherer26 on 2012-03-03
I would appreciate some help when you get time.


cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Northfork 3.0.0-16-generic-pae #29-Ubuntu SMP Tue Feb 14 13:56:31 UTC 2012 i686 i686 i386 GNU/Linux

```
lspci -nnk | grep -iA2 net
```
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169
--
06:00.0 Network controller [0280]: Atheros Communications Inc. AR5008 Wireless Network Adapter [168c:0023] (rev 01)
	Subsystem: Atheros Communications Inc. Device [168c:3071]
	Kernel driver in use: ath9k

```

iwconfig
```
lo        no wireless extensions.

eth1      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"xxxxxxx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/70  Signal level=-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:2   Missed beacon:0

```
rfkill list all
```
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
lsmod
```

Module                  Size  Used by
ath9k                 112612  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
vesafb                 13489  1 
binfmt_misc            17292  1 
arc4                   12473  2 
cx18_alsa              13488  1 
mxl5005s               46116  1 
s5h1409                18386  1 
tuner_simple           18151  1 
tuner_types            18998  1 tuner_simple
cs5345                 12927  1 
tda9887                17874  1 
tda8290                22216  0 
tuner                  26836  2 
snd_hda_codec_realtek   254163  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 cx18_alsa,snd_hda_intel,snd_hda_codec
mac80211              393421  1 ath9k
ppdev                  12849  0 
nvidia              10941445  40 
snd_seq_midi           13132  0 
ath9k_common           13599  1 ath9k
cx18                  117669  1 cx18_alsa
dvb_core               94826  1 cx18
cx2341x                27739  1 cx18
i2c_algo_bit           13199  1 cx18
videobuf_vmalloc       13336  1 cx18
ath9k_hw              293933  2 ath9k,ath9k_common
videobuf_core          25409  2 cx18,videobuf_vmalloc
tveeprom               17009  1 cx18
v4l2_common            15793  4 cs5345,tuner,cx18,cx2341x
videodev               85626  5 cs5345,tuner,cx18,cx2341x,v4l2_common
ath                    19387  2 ath9k,ath9k_hw
snd_rawmidi            25241  1 snd_seq_midi
cfg80211              172427  3 ath9k,mac80211,ath
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                63474  0 
serio_raw              12990  0 
parport_pc             32114  1 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 cx18_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
firewire_ohci          35846  0 
firewire_core          56937  1 firewire_ohci
usbhid                 41905  0 
hid                    77367  1 usbhid
crc_itu_t              12627  1 firewire_core
ahci                   21634  0 
libahci                25761  1 ahci
r8169                  47200  0 
pata_jmicron           12651  0 

```

---

### Post by wildmanne39 on 2012-03-04
Hi jscherer26, please do what is in post 6 of this thread and see if that help.

Please just copy and paste the commands.
Thanks

---

### Post by jscherer26 on 2012-03-04
Thanks you wildmanne39. I tried everything I found in the post and didn't have success. I removed and packaged up the card and I'm going to return it. After spending a day messing around I discovered ThinkPenguin.com and ordered their Penguin Wireless N PCIe Card for GNU / Linux. Ubuntu claims it compatible. Hopefully that will be all I need.

---

### Post by PapaSol on 2012-03-18
I recently installed Ubuntu on an old Toshiba Satellite laptop that I have.  I am very happy with Ubuntu, but my internet is painfully slow.  Maybe you can help?

```
solomon@solomon-Satellite-A135:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux solomon-Satellite-A135 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686 i686 i386 GNU/Linux
``````

solomon@solomon-Satellite-A135:~$ lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1040]
    Kernel driver in use: iwl3945
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Toshiba America Info Systems Device [1179:ff00]
    Kernel driver in use: r8169
solomon@solomon-Satellite-A135:~$ 

``````

solomon@solomon-Satellite-A135:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Belkin.3B99"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 94:44:52:11:5B:99   
          Bit Rate=48 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:522   Missed beacon:0

solomon@solomon-Satellite-A135:~$ 

``````

solomon@solomon-Satellite-A135:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
solomon@solomon-Satellite-A135:~$ 

solomon@solomon-Satellite-A135:~$ lsmod
Module                  Size  Used by
parport_pc             32114  1 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_realtek   254163  1 
joydev                 17393  0 
binfmt_misc            17292  1 
pcmcia                 39822  0 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
i915                  509519  3 
snd_seq_midi           13132  0 
tifm_7xx1              12937  0 
snd_rawmidi            25241  1 snd_seq_midi
tifm_core              15040  1 tifm_7xx1
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12473  2 
yenta_socket           27428  0 
psmouse                73673  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
iwl3945                73360  0 
iwl_legacy             71499  1 iwl3945
serio_raw              12990  0 
i2c_algo_bit           13199  1 i915
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              393421  2 iwl3945,iwl_legacy
cfg80211              172427  3 iwl3945,iwl_legacy,mac80211
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
sparse_keymap          13658  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
r8169                  43104  0 
solomon@solomon-Satellite-A135:~$

```

---

### Post by wildmanne39 on 2012-03-20
Hi, change your settings to match the screenshots and see if that helps.

---

### Post by PapaSol on 2012-03-20
That seems to have really helped.  Thanks.

---

### Post by wildmanne39 on 2012-03-20
Your welcome! Glad I could help.

---

### Post by cloyd on 2012-04-04
I have the same card.  I had used another solution in 10.04, but it wouldn't work in 12.04 beta 2.    This did.   Thanks much.

---

### Post by wildmanne39 on 2012-04-04
Your welcome!

---

### Post by atomicpirate on 2012-04-04
First thank you wildmanne39 for all the help.  I was getting 1Mb down before using > options iwlagn nohwcrypt=1 and now am getting about 8Mb down.  However, using the exact same hardware in Windows 7 I get about 19Mb down, so I know there is room for improvement.  Would you mind looking over my system's output to see if there are any obvious tweaks to make?

BTW I am curious why hardware encryption would be slower; it is counterintuitive to me that turning off hardward in favor of software would speed things *up*.

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Kronk 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```
```

00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
	Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:849c]
	Kernel driver in use: e1000e
--
09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178]
	Kernel driver in use: rtl8192ce

```
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Relentless"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 68:A8:6D:62:C5:B9   
          Bit Rate=144.4 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:47   Missed beacon:0


```
```

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
```

Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  4 
bnep                   18436  2 
rfcomm                 47946  8 
binfmt_misc            17540  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
arc4                   12529  2 
snd_hda_codec_realtek   330815  1 
eeepc_wmi              12826  0 
asus_wmi               20035  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
psmouse                73882  0 
serio_raw              13166  0 
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
snd_hda_intel          33390  3 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
nouveau               728722  2 
snd_seq_midi           13324  0 
rtl8192ce              84775  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               110972  1 rtl8192ce
snd_rawmidi            30547  1 snd_seq_midi
mac80211              462046  3 rtl8192ce,rtl8192c_common,rtlwifi
ttm                    76805  1 nouveau
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              199630  2 rtlwifi,mac80211
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
drm_kms_helper         42558  1 nouveau
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mei                    41480  0 
drm                   236290  4 nouveau,ttm,drm_kms_helper
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13423  1 nouveau
soundcore              12680  1 snd
mxm_wmi                12979  1 nouveau
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19412  1 nouveau
wmi                    19256  2 asus_wmi,mxm_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
e1000e                160582  0 
xhci_hcd               82820  0 
ahci                   26002  4 
libahci                26861  1 ahci

```

---

### Post by wildmanne39 on 2012-04-04
Hi, you need to remove this option
```
options iwlagn nohwcrypt=1 
```
it is not right for the card you have.

Then do:
```
sudo modprobe -r rtl8192ce
sudo modprobe rtl8192ce swenc=1
```
do not reboot if it works we will need to make it permanent.
Thanks

---

### Post by atomicpirate on 2012-04-04
That did the trick.  Download speeds are now comparable to Windows 7 on the same hardware.  How do you recommend making this permanent?

Btw your solution for my system seems to be the same in spirit as the solutions you've suggested to many others on this thread: turning off hardware encryption in favor of software.  Do you mind commenting on why that makes such a huge difference?

Thanks again!

---

### Post by wildmanne39 on 2012-04-05
Hi, like this:
```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```
A new empty file will open, paste this one line into the file.
```
options rtl8192ce swenc=1
```
Proofread, save and close gedit, then reboot.

In ubuntu by default encryption is set to be handled by the hardware and sometimes it works better handling encryption with the software as in your case so we set it to do just that.
Thanks

---

### Post by jerkyeights on 2012-04-05
can anyone help me to fix my slow wrless internet . i used ubuntu 12.04 lts p.p ](*,)](*,)

---

### Post by wildmanne39 on 2012-04-05
Hi jerkyeights, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by jerkyeights on 2012-04-05
im new on this haha

```
lsb_release -a
jerkyeights@jerkyeights-Intel-power-rangers:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu precise (development branch)
Release:	12.04
Codename:	precise
jerkyeights@jerkyeights-Intel-power-rangers:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
Linux jerkyeights-Intel-power-rangers 3.2.0-22-generic #35-Ubuntu SMP Tue Apr 3 18:32:42 UTC 2012 i686 i686 i386 GNU/Linux
jerkyeights@jerkyeights-Intel-power-rangers:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Elitegroup Computer Systems Device [1019:9089]
	Kernel driver in use: r8169
jerkyeights@jerkyeights-Intel-power-rangers:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0ac8:c312 Z-Star Microelectronics Corp. 
Bus 001 Device 005: ID 0db0:6877 Micro Star International RT2573
Bus 001 Device 006: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 003 Device 013: ID 0e8f:0016 GreenAsia Inc. 4 port USB 1.1 hub UH-174
Bus 003 Device 003: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse
Bus 003 Device 014: ID 04e8:689e Samsung Electronics Co., Ltd GT-S5670 [Galaxy Fit]
Bus 003 Device 015: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
jerkyeights@jerkyeights-Intel-power-rangers:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"ezah WIFI"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 34:08:04:FD:8B:FD   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0

eth0      no wireless extensions.

jerkyeights@jerkyeights-Intel-power-rangers:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by wildmanne39 on 2012-04-05
Hi, is your wireless an internal card? If so try this command and post the results here.
```
lspci -nn
```
Thanks

---

### Post by jerkyeights on 2012-04-05
i think yes but seriously im new

```
:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GSE Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

```

---

### Post by wildmanne39 on 2012-04-05
Hi, post the output of:
```
lsmod
```
Thanks

---

### Post by jerkyeights on 2012-04-05
```
:~$ lsmod
Module                  Size  Used by
cdc_acm                22306  0 
parport_pc             32114  0 
ppdev                  12849  0 
arc4                   12473  2 
rt73usb                27029  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              20061  1 rt73usb
rt2x00lib              48858  2 rt73usb,rt2x00usb
mac80211              436455  2 rt2x00usb,rt2x00lib
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  5 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
cfg80211              178679  2 rt2x00lib,mac80211
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
psmouse                87140  0 
serio_raw              13027  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  414568  3 
joydev                 17393  0 
tpm_tis                18308  0 
drm_kms_helper         45466  1 i915
rfcomm                 38139  0 
bnep                   17830  2 
snd                    62064  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth             158438  10 rfcomm,bnep
binfmt_misc            17292  1 
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
ums_realtek            17920  0 
usb_storage            39646  1 ums_realtek
uas                    17699  0 
r8169                  56321  0 

```

---

### Post by wildmanne39 on 2012-04-05
Hi, try this please:
```
sudo ifconfig wlan0 down
sudo rmmod -f rt73usb
sudo modprobe rt73usb nohwcrypt=1
sudo ifconfig wlan0 up
```
of that helps and I think it will we will need to make it permanent.
Thanks

---

### Post by jerkyeights on 2012-04-05
nothing happen on terminal but my wifi discnnt and cnnct back .

---

### Post by wildmanne39 on 2012-04-05
Hi, those commands would only show output if there were errors, so just try your internet and see how it works but do not reboot or you will have to run those commands again.
Thanks

---

### Post by jerkyeights on 2012-04-05
thanks a lot ! it work ! :D . If I reboot ?

---

### Post by wildmanne39 on 2012-04-05
Hi, we need to make it permanent.
```
gksudo gedit /etc/modprobe.d/rt73usb.conf
```
Add a single line:
```
options rt73usb nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.

---

### Post by jerkyeights on 2012-04-05
DONE ! btw thanks again wildmanne39

---

### Post by wildmanne39 on 2012-04-05
Your welcome!

---

### Post by atomicpirate on 2012-04-06
Although my stats on speedtest.net have improved with this line:
```
options rtl8192ce swenc=1
```
I am now experiencing frequent "stalls"--downloading will proceed quickly for a couple seconds and then suddenly stop and hang for awhile, sometimes as long as a minute or two before resuming.

Any idea on what might be wrong?

---

### Post by wildmanne39 on 2012-04-06
Hi, do what is in post 266 that should help.

Also it may be where you are downloading from.
Thanks

---

### Post by Perogasus on 2012-04-10
Hi, wildmanne39
I'm new to ubuntu and this slow internet thing is really killing me. I see you've helped a lot of people here so I'm asking you to help me too :) . I tried using the commands you gave to the other guys but none of them seem to work. I figured out it has something to do with our wireless card drivers so I tried to alter the commands according to my wireless card rt2500, again with no luck.
So now I'm desperately asking for your help. These are the outputs I get from the lsmod commands: 

```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: ASRock Incorporation Device [1849:8136]
	Kernel driver in use: r8169
--
03:01.0 Network controller [0280]: Ralink corp. RT2500 802.11g [1814:0201] (rev 01)
	Subsystem: Ralink corp. Device [1814:2560]
	Kernel driver in use: rt2500pci
```

and 

```
Module                  Size  Used by
ath9k                 127538  0 
ath9k_common           13839  1 ath9k
ath9k_hw              312866  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
snd_hda_codec_hdmi     32040  1 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
joydev                 17693  0 
hid_gaff               12643  0 
ff_memless             13097  1 hid_gaff
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
arc4                   12529  2 
ppdev                  17113  0 
snd_seq_midi_event     14899  1 snd_seq_midi
binfmt_misc            17540  1 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
usbhid                 47198  1 hid_gaff
snd_hda_codec_realtek   330769  1 
radeon               1015995  5 
hid                    95463  2 hid_gaff,usbhid
snd_hda_intel          33390  6 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
parport_pc             36962  1 
rt2500pci              27646  0 
rt2x00pci              14578  1 rt2500pci
rt2x00lib              50325  2 rt2500pci,rt2x00pci
mac80211              310872  3 ath9k,rt2x00pci,rt2x00lib
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   236330  7 radeon,ttm,drm_kms_helper
snd_timer              29991  2 snd_seq,snd_pcm
cfg80211              199587  4 ath9k,ath,rt2x00lib,mac80211
i2c_algo_bit           13423  1 radeon
eeprom_93cx6           12725  1 rt2500pci
snd                    68266  22 snd_hda_codec_hdmi,snd_rawmidi,snd_seq,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
r8169                  52788  0 
```

Thanks for your help, you rock :)


edit: Also, the first few minutes after i connect to my wireless, the speed seems fine, then it drops from 1500kb/s to 100kb/s :(

---

### Post by ejeroel on 2012-04-11
Hi, I'm not new to Ubuntu, but I'm having this problem since I've installed it (11.10) on my sony vaio laptop too.
wi-fi works fine with 10.10 on my station.

I have tried what you suggested to the other vaio user in the early replies, but it didn't work

help, please

edit: went through post 17 through 19 and solved the problem
thanks wildmanne39!

---

### Post by wildmanne39 on 2012-04-15
Hi ejeroel, I am glad you found the solution in this thread, I am sorry I did not reply sooner but I was out of town.
Enjoy

---

### Post by MScotth on 2012-05-05
I'm using an old d-link pmcia wireless 802.11b/g card on a toshiba laptop with xubuntu 11.10. Drivers athk5.
This is what it happens.
I turn the computer on in the morning. Everythings works perfectly. I ping the router and I get 1 ms average. Great. I use the PC all day. No problem.  In the evening after a day of use the wifi connection becames very slow. I ping the router and I get 500ms, 1000ms, 30000ms etc..I lose a lot of packets. I've tried to reboot the machine and the router, but it's useless. I'm thinking that maybe some component in the card becames too hot and this affect the reception of the signal? Is it possible? :confused:
I've disabled ipv6 and the hardware crypt as suggested, but it changed nothing.

---

### Post by chili555 on 2012-05-05
> old d-link pmcia wireless> I'm thinking that maybe some component in the card becames too hot and this affect the reception of the signal? Is it possible?I think it is entirely possible. There is a small possibility you could reduce the heat by reducing tx-power:```
sudo iwconfig wlan0 txpower 13
```Get an idea what the current setting is with:```
iwconfig
```> wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:13:10:62:8D:xx   
          Bit Rate=36 Mb/s   [COLOR="Red"]Tx-Power=15 dBm[/COLOR]   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
Not all cards are capable of setting txpower; if yours is, it may help. Of course, it's a balancing act between txpower and the ability to connect with stability. If you can change it, keep walking it down until instability creeps in and go back up one step. 

You might also experiment with power management on and off:```
sudo iwconfig wlan0 power off
```I suspect heat would be less with power management on.

In all cases, substitute your wireless interface if it's not wlan0.

Of course, for US$10-15, you could get a newer device!

---

### Post by MScotth on 2012-05-05
Thanks for the suggestion. I've set the txpower to 11. Let's wait some hours.:popcorn:

---

### Post by sodafan on 2012-05-17
Hi, 
I am having the same trouble too. 
#17-19 didn't solve the problem. 

lspci -nnk | grep -iA2 net gives this

```
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
	Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1301]
	Kernel driver in use: iwlwifi
--
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller [11ab:4380] (rev 10)
	Subsystem: Sony Corporation Device [104d:9072]
	Kernel driver in use: sky2

```

lsmod gives this

```
Module                  Size  Used by
iwlwifi               328352  0 
vesafb                 13844  1 
rfcomm                 47604  0 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  4 
arc4                   12529  2 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  7 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
mac80211              506816  1 iwlwifi
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87692  0 
serio_raw              13211  0 
uvcvideo               72627  0 
nvidia              12319264  44 
videodev               98259  1 uvcvideo
joydev                 17693  0 
v4l2_compat_ioctl32    17128  1 videodev
cfg80211              205544  2 iwlwifi,mac80211
intel_ips              18089  0 
snd                    78855  23 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  18288  0 
bluetooth             180104  11 rfcomm,bnep,btusb
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
sony_laptop            45393  0 
mxm_wmi                12979  0 
wmi                    19256  1 mxm_wmi
video                  19596  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
sky2                   59043  0 
sdhci_pci              18826  0 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci                  33205  1 sdhci_pci

```

---

### Post by wildmanne39 on 2012-05-17
Hi, it would not help you because you have a different driver everywhere you see iwlagn in the changes you made please change iwlagn to iwlwifi then save gedit,close. and reboot.
Thanks

---

### Post by illeatmyhead on 2012-05-21
Hello everyone,

I've followed your instructions as well as I could and read through your posts all the while patiently waiting for the next page to load. i've tried 17 and don't know how to open the file backup to do 19 (17 didn't help).
 I hope you can help. It would be much appreciated!! :D

here are my specs:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux martin-ThinkPad-X61 3.0.0-19-generic #33-Ubuntu SMP Thu Apr 19 19:05:57 UTC 2012 i686 i686 i386 GNU/Linux


00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
    Subsystem: Lenovo Device [17aa:20de]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4230] (rev 61)
    Subsystem: Intel Corporation Lenovo ThinkPad T51 [8086:1110]
    Kernel driver in use: iwl4965

[FONT=monospace]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"MariJo"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:4D:4D:A1:A4   
          Bit Rate=65 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1903  Invalid misc:400   Missed beacon:0


[/FONT]
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_analog    75090  1 
binfmt_misc            17292  1 
arc4                   12473  2 
pcmcia                 39822  0 
snd_hda_intel          24262  2 
snd_hda_codec          91888  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
thinkpad_acpi          73942  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
nvram                  14029  1 thinkpad_acpi
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
tpm_tis                14002  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
iwl4965               121795  0 
iwl_legacy             71499  1 iwl4965
mac80211              393421  2 iwl4965,iwl_legacy
i915                  509559  4 
snd                    55902  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  18160  2 
cfg80211              172427  3 iwl4965,iwl_legacy,mac80211
psmouse                73673  0 
bluetooth             148869  23 bnep,rfcomm,btusb
serio_raw              12990  0 
drm_kms_helper         32889  1 i915
drm                   192194  5 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19069  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
e1000e                139814  0 



I hope this helps.

---

### Post by wildmanne39 on 2012-05-21
Hi illeatmyhead, first that would not work because you do not have the same driver, please do:
```
gksudo gedit /etc/modprobe.d/iwl4965.conf
```
Add one line:

```
options iwl4965 11n_disable=1
```

Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by illeatmyhead on 2012-05-21
wow, it's back to normal and you are amazing!!!

I hope the other commands I entered didn't do any damage?! please advice.

thanks so much.

---

### Post by wildmanne39 on 2012-05-21
Hi, they should be ok since they were under a different driver name and you do not have that driver.
Enjoy

---

### Post by eiriksm on 2012-05-28
Hello.

I have done a lot of googling and actually reading all 31 pages of this thread (and trying appropriate fixes), but still my wifi is most of the time >1Mb, when it should be 10. Sometimes it is as slow as 40Kb, very frustrating. And every time I feel it has improved, it goes back to being unstable after a short time. It felt like it was fixed in 12.04 for a while, but then it went back to slooooow.

The last days it has been worse than usual. If anyone can help me out, I would be very happy.

Some info: cat /etc/lsb-release; uname -a
```


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux eirik-Aspire-7750G 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

``` 

lspci -nnk | grep -iA2 net
```

02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: Acer Incorporated [ALI] Device [1025:050e]
	Kernel driver in use: atl1c
--
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6603]
	Kernel driver in use: ath9k

``` 

iwconfig
```


lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"xxxxxx"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx:xx:xx:xx:xx:xx  
          Bit Rate=54 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:315  Invalid misc:17   Missed beacon:0

eth0      no wireless extensions.

```

---

### Post by wildmanne39 on 2012-05-28
Hi, please do:
```
sudo /etc/init.d/network-manager stop

sudo iwconfig wlan0 power off

sudo iwconfig wlan0 rate auto

sudo /etc/init.d/network-manager start 
```
now post the output of:
```
iwconfig
```
again so I we can see if your tx power has changed.

Also please post the contents of:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```

Please go into network manager, edit connection, wireless and set IPV6 to ignore.
Thanks

---

### Post by eiriksm on 2012-05-28
Hi. Thanks for your quick reply.

new iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"xxxxxx"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=54 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:14   Missed beacon:0

eth0      no wireless extensions.

```

gksudo gedit /etc/modprobe.d/ath9k.conf

file contains:
```
options ath9k nohwcrypt=1
```

Still same speed, though. Is it something with the invalid nwid and that stuff?

Thanks again for being helpful.

---

### Post by wildmanne39 on 2012-05-28
Hi, no it has nothing to do with invalid nwid.

Please set your wireless setting to match the screenshots and see if that helps.
Thanks

---

### Post by eiriksm on 2012-05-28
Hi. Sorry, forgot to add that I also did that previously. Tried both manual DNS and automatic, no difference.

Thanks again for looking at my problem.

---

### Post by wildmanne39 on 2012-05-28
Hi, I recommend that you leave your settings to what the screenshots have and also go into your router settings and see if you can turn your wireless power output all the way up if it is not already.
Thanks

---

### Post by eiriksm on 2012-05-28
I tried tweaking the settings on the router, and no luck. It is an old router, though. But it works perfectly on my ubuntu 11.04 (i think that is ath5k) and windows 7 on the same computer as the ubuntu 12.04. (and also on android, ipad, iphone, Vista, XP, you name it :))

---

### Post by wildmanne39 on 2012-05-28
Hi, the only other thing I can suggest is see if there is a newer driver for your card or install ndiswrapper.
Thanks

---

### Post by wildmanne39 on 2012-05-28
Hi, one more thing you can try:
```
gksudo gedit /etc/rc.local
```
Add a line above exit 0
```
iwconfig wlan0 power off
```
proofread, save and close gedit then reboot.
Thanks

---

### Post by eiriksm on 2012-05-28
Thanks for that tip. I think I just found out an embarrassing fact: The speed seems stable and fast when I am 2 feet away from the router. The tip that made me try it was your suggestion about changing the power output on the router, so thanks for that!

What I think is strange is that this applies only to my ubuntu computer (which is my preferred one). Is there anything setting I can tweak to improve the reception (which now seems to be the problem)?

---

### Post by wildmanne39 on 2012-05-28
Hi, I also suspect it is a factor > Tx-Power=13 dBmmost peoples read 20 and it can be changed in the router settings of most newer routers.

Also I found this you can try:
```
gksudo gedit /etc/sysctl.conf; sudo sysctl -p
```

and add these lines:

```
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1
vm.swappiness = 10

```
Save the new file, close gedit and reboot.
Thanks

---

### Post by shirokoff on 2012-06-11
Hi. I thing I've got the same problem on my 11.10 ubuntu =(

**shirokoff@shirokoff-desktop:~$ cat /etc/lsb-release; uname -a**
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux shirokoff-desktop 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux
shirokoff@shirokoff-desktop:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:529c]
    Kernel driver in use: r8169
--
04:01.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
    Subsystem: D-Link System Inc AirPlus G DWL-G510 Wireless PCI Adapter(rev.B) [1186:3a16]
    Kernel driver in use: ath5k

```**shirokoff@shirokoff-desktop:~$ lspci -nnk | grep -iA2 net**
```

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:529c]
    Kernel driver in use: r8169
--
04:01.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
    Subsystem: D-Link System Inc AirPlus G DWL-G510 Wireless PCI Adapter(rev.B) [1186:3a16]
    Kernel driver in use: ath5k

```**shirokoff@shirokoff-desktop:~$ iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"durden"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:49:A7:4B:26   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:8   Missed beacon:0

```**shirokoff@shirokoff-desktop:~$ rfkill list all**
```
2: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```**shirokoff@shirokoff-desktop:~$ lsmod**
```
Module                  Size  Used by
ath5k                 145100  0 
ipheth                 13307  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
vesafb                 13489  1 
binfmt_misc            17292  1 
joydev                 17393  0 
arc4                   12473  2 
snd_hda_codec_realtek   254163  1 
wacom                  37007  0 
hid_logitech           17405  0 
ff_memless             12945  1 hid_logitech
nvidia              10390874  40 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ath                    19387  1 ath5k
mac80211              393421  1 ath5k
ppdev                  12849  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                73673  0 
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32114  1 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172427  3 ath5k,ath,mac80211
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  1 hid_logitech
hid                    77367  2 hid_logitech,usbhid
usb_storage            44173  0 
uas                    17699  0 
r8169                  43104  0 
```Thanks.

---

### Post by chili555 on 2012-06-11
I believe the Wild Man is out of town. If not, I apologize in advance. 

What do you make of this?> wlan0     IEEE 802.11bg  ESSID:"durden"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:49:A7:4B:26   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          [COLOR="Red"]Link Quality=29/70[/COLOR]  Signal level=-81 dBm Are you in the same *county* with the router? Is there a power setting in the router? Is it dialed up to the maximum? Have you tried different channels in the router to try to get better reception? I have the best luck with 1 and 11.

---

### Post by shirokoff on 2012-06-11
> **chili555 said:**
> I believe the Wild Man is out of town. If not, I apologize in advance. 

What do you make of this?Are you in the same *county* with the router? Is there a power setting in the router? Is it dialed up to the maximum? Have you tried different channels in the router to try to get better reception? I have the best luck with 1 and 11.

Huh. Looks like changing the chanel to 1 solved my problem.
Think the problem specific from my wifi adapter though. 
Cause I didn't have any wifi problems on 10.10. And on windows.

Thank you.

---

### Post by blennox on 2012-06-24
Hi guys,

I'm having the same problem, just installed ubuntu 12.04 64-bit today and the wifi is seriously slow, but is fine on windows. I ran the following in terminal, anyone able to help please?

bill@bill-Aspire-7741:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"SKY04FA3"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 90:01:3B:70:4F:A4   
          Bit Rate=144.4 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:46  Invalid misc:933   Missed beacon:0

eth0      no wireless extensions.




bill@bill-Aspire-7741:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Aspire 7740G [1025:033d]
    Kernel driver in use: tg3
--
05:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
    Subsystem: Foxconn International, Inc. T77H103.00 Wireless Half-size Mini PCIe Card [105b:e021]
    Kernel driver in use: brcmsmac




bill@bill-Aspire-7741:~$ lsmod
Module                  Size  Used by
joydev                 17693  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
snd_hda_codec_hdmi     32474  1 
bcma                   26696  0 
arc4                   12529  2 
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
snd_hda_codec_realtek   223867  1 
ses                    17417  0 
enclosure              15269  1 ses
uvcvideo               72627  0 
snd_seq_midi           13324  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
psmouse                87692  0 
serio_raw              13211  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon                804372  3 
video                  19596  0 
wmi                    19256  1 acer_wmi
mac_hid                13253  0 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
snd_timer              29990  2 snd_seq,snd_pcm
drm                   242038  5 radeon,ttm,drm_kms_helper
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
brcmsmac              570874  0 
i2c_algo_bit           13423  1 radeon
mac80211              506816  1 brcmsmac
brcmutil               15139  1 brcmsmac
mei                    41616  0 
cfg80211              205544  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12535  1 brcmsmac
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
uas                    18180  0 
usb_storage            49198  0 
tg3                   152032  0

---

### Post by wildmanne39 on 2012-06-24
Hi blennox, please do:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
does that help.
Thanks

---

### Post by blennox on 2012-06-24
Hi Wildmanne39,
That seems to have done the trick! Thanks very much for your help  :KS
Bill

---

### Post by wildmanne39 on 2012-06-24
Your welcome!!!

---

### Post by LintWad on 2012-07-11
I'm having similar problems as stated above. I have tried the fix posted to no avail, upon the recommendation of some other threads: [http://ubuntuforums.org/showpost.php?p=11976840&postcount=305](http://ubuntuforums.org/showpost.php?p=11976840&postcount=305)

As well as a couple others. I was able to both kill my internet connection by mucking with the ath9k, and then restore it after returning the settings to normal. In either case, my internet is essentially unusable on that computer due to the slow connection. 

The wireless adaptor is a Netgear USB N150 WNA1100

The output as requested is as follows.

Please advise.

```

  	 	 	 	 	 	   *iwconfig*
 lo        no wireless extensions.  
 

 eth1      no wireless extensions.  
 

 wlan0     IEEE 802.11bgn  ESSID:"wireless"   
           Mode:Managed  Frequency:2.462 GHz  Access Point: 58:6D:8F:6F:95:68    
           Bit Rate=28.9 Mb/s   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
           Link Quality=33/70  Signal level=-77 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:9  Invalid misc:25   Missed beacon:0  
 

 eth0      no wireless extensions. 


```

 

```


 *lspci -nnk | grep -iA2 net * 
 00:0a.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller [11ab:4320] (rev 13)  
 	Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Controller (Asus) [1043:811a]  
 	Kernel driver in use: skge  
 	Kernel modules: skge  
 00:0c.0 Ethernet controller [0200]: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 [8086:1229] (rev 04) 
 	Subsystem: Intel Corporation 82558B PRO/100+ PCI (TP) [8086:0009]  
 	Kernel driver in use: e100 


```

 

```


 *lsmod*
 Module                  Size  Used by  
 arc4                   12529  2  
 snd_via82xx            29734  2  
 snd_via82xx_modem      18825  0  
 gameport               19693  1 snd_via82xx  
 snd_ac97_codec        134826  2 snd_via82xx,snd_via82xx_modem  
 ac97_bus               12730  1 snd_ac97_codec  
 snd_pcm                97188  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec  
 snd_mpu401_uart        14169  1 snd_via82xx  
 snd_seq_midi           13324  0  
 ath9k_htc              92738  0  
 snd_rawmidi            30748  2 snd_mpu401_uart,snd_seq_midi  
 mac80211              506816  1 ath9k_htc  
 snd_seq_midi_event     14899  1 snd_seq_midi  
 ath9k_common           14053  1 ath9k_htc  
 ath9k_hw              411112  2 ath9k_htc,ath9k_common  
 snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event  
 ath                    24067  3 ath9k_htc,ath9k_common,ath9k_hw  
 snd_timer              29990  2 snd_pcm,snd_seq  
 snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq  
 nouveau               774571  2  
 cfg80211              205544  3 ath9k_htc,mac80211,ath  
 snd                    78855  13 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 joydev                 17693  0  
 amd64_edac_mod         24778  0  
 psmouse                87603  0  
 edac_core              53746  3 amd64_edac_mod  
 i2c_viapro             13153  0  
 serio_raw              13211  0  
 k8temp                 13057  0  
 ttm                    76949  1 nouveau 
 snd_page_alloc         18529  3 snd_via82xx,snd_via82xx_modem,snd_pcm  
 edac_mce_amd           23709  1 amd64_edac_mod  
 soundcore              15091  1 snd  
 drm_kms_helper         46978  1 nouveau 
 drm                   242038  4 nouveau,ttm,drm_kms_helper  
 rfcomm                 47604  0  
 bnep                   18281  2  
 i2c_algo_bit           13423  1 nouveau 
 parport_pc             32866  1  
 bluetooth             180104  10 rfcomm,bnep  
 mxm_wmi                12979  1 nouveau 
 wmi                    19256  1 mxm_wmi 
 ppdev                  17113  0  
 video                  19596  1 nouveau 
 mac_hid                13253  0  
 shpchp                 37277  0  
 lp                     17799  0  
 parport                46562  3 parport_pc,ppdev,lp  
 usbhid                 47199  0  
 hid                    99559  1 usbhid  
 floppy                 70365  0  
 firewire_ohci          41000  0  
 firewire_core          63558  1 firewire_ohci  
 pata_via               13701  2  
 sata_via               13799  0  
 e100                   37213  0  
 skge                   49902  0  
 crc_itu_t              12707  1 firewire_core 


```

---

### Post by Tamas7 on 2012-08-27
Hello,

I also have network speed problem and I also would need for help.

My problem is similar, but any of the previous comments helped me out yet.

I have usbnet, with the followings:

**ROUTER PART (2.6.32):**
physic modem, (USB 2.0 full-speed)
OHCI,
usbnet,
and a driver from the modem manufacturer.

**via WiFi**

**MY LAPTOP**

I would like to use all of the above via Wifi connection like a router. 

My problem are the **speed slow** and **asymmetric**, the download  is much more bigger then the upload. I tested the modem and that is right in my laptop. I mean the internet speed is high.

Any idea what I should change?

My idea was to exchange the OHCI to EHCI, but firstly I cannot and secondly I am afraid of this cannot solve my problem.

Sorry for my poor English.

T

---

### Post by ozzyprv on 2012-09-02
[edit] removed post. Problem seems to be fixed. thanks.

---

### Post by waadimch on 2012-09-15
[SIZE=1]hi 

I have a problem with slow speed 
([/SIZE][SIZE=1][SIZE=1]RTL8188CE[/SIZE])
Please help

Module                  Size  Used by
vesafb                 13844  1 
joydev                 17693  0 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
arc4                   12529  2 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_codec_idt      70795  1 
snd_hda_codec_hdmi     32474  1 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                87692  0 
k10temp                13166  0 
serio_raw              13211  0 
uvcvideo               72627  0 
i2c_piix4              13301  0 
videodev               98259  1 uvcvideo
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
v4l2_compat_ioctl32    17128  1 videodev
rtl8192ce             137448  0 
snd_timer              29990  2 snd_pcm,snd_seq
fglrx                3263886  117 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rtlwifi               118718  1 rtl8192ce
mac80211              506816  2 rtl8192ce,rtlwifi
rts_pstor             445196  0 
snd                    78855  20 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
cfg80211              205544  2 rtlwifi,mac80211
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  1 hp_wmi
video                  19596  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

wlan0     IEEE 802.11bgn  ESSID:"danny"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:90:D0:F3:27:10   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3053   Missed beacon:0

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1629]
    Kernel driver in use: rtl8192ce
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:3566]
    Kernel driver in use: r8169




[/SIZE]

---

### Post by chili555 on 2012-09-16
> **waadimch said:**
> [SIZE=1]hi 

I have a problem with slow speed 
([/SIZE][SIZE=1][SIZE=1]RTL8188CE[/SIZE])
Please helpWow! This is a long, old complicated thread! Would you please start your own new thread and PM me the link?

---

### Post by kclindal on 2013-01-27
Deadly! Worked like a charm Ubuntu 12.04 - Ultimate 3.5.

Atta Boy Wild Man, Thanks!  Theres no going to going back to windows for this cowboy,  No matter how buggy ubuntu is for me,

Wish I could wholeheartedly recommend it to windows users tho.  

I love Linux,  why is so buggy tho? Or is it just me and my "fix it till it breaks", kinda personality?

Hmmm...  Oh well, thanks again!

---

### Post by Manowar676 on 2013-03-10
thanks a lot man, really appreciate it. guys dont forget to enter the code in the new document folder not in the terminal as i did the first time!

---

### Post by travelholic on 2013-04-02
Edit: If you read this, I just started a new thread. Thanks!

---

### Post by wildmanne39 on 2013-04-02
Go into your router and change 802.11bgn to just 802.11bg.

Change your wireless setting to match the screenshots.
Then do:
```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```

A new empty file will open, paste this one line into the file.

```
options rtl8192ce swenc=1
```
Proofread, save and close gedit, then reboot.
Thanks

---

### Post by travelholic on 2013-04-02
Sorry I started a new thread with all the same info. I don't have access to the router though. It's the school internet, but it equally doesn't work at home.

---

### Post by wildmanne39 on 2013-04-02
Did you do all the other things listed above except changing the router settings?
Thanks

---

### Post by travelholic on 2013-04-02
> **Wild Man said:**
> Did you do all the other things listed above except changing the router settings?
Thanks
Hey I think that worked! I'll post one more time when I'm home later to make sure it works on that connection.

Thanks much!

---

### Post by Slixt on 2013-04-03
Hey, I'm glad I found this. I've been noticing my wifi seems slower than it should and tried all kinds of things. I did notice I got some improvement by disabling ivp6 in network-manager on my wifi profile. I'll post the needed info for you. It's not terrible speed, just kind of slower than any of the other laptops in the house and noticeable if i'm doing anything that's steady where I can notice the small hangs that get annoying.

lspci -nnk:
```
 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
    Kernel driver in use: rtl8192ce
```

lsmod:
```
Module                  Size  Used by
snd_hda_codec_hdmi     31423  1 
snd_hda_codec_conexant    52202  1 
joydev                 17161  0 
arc4                   12473  2 
rtl8192ce             131812  0 
rtlwifi               116139  1 rtl8192ce
coretemp               13168  0 
mac80211              461161  2 rtl8192ce,rtlwifi
snd_hda_intel          32515  3 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
microcode              18209  0 
i915                  457161  3 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         45271  1 i915
uvcvideo               71277  0 
toshiba_acpi           18238  0 
videobuf2_core         32070  1 uvcvideo
cfg80211              175375  2 rtlwifi,mac80211
drm                   230463  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
snd                    61991  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sparse_keymap          13658  1 toshiba_acpi
psmouse                84843  0 
serio_raw              13031  0 
lpc_ich                16925  0 
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
mei                    35796  0 
wmi                    18590  1 toshiba_acpi
parport_pc             31968  0 
ppdev                  12817  0 
bnep                   17707  2 
rfcomm                 37276  0 
bluetooth             183228  10 bnep,rfcomm
video                  18847  1 i915
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
atl1c                  36175  0 


```
Any advice would be helpful to get it reaching speeds like the others in the house. Thanks in advance guys. :)

---

### Post by wildmanne39 on 2013-04-03
Hi, please do what is in post 329.
Thanks

---

### Post by Slixt on 2013-04-04
Okay, thanks. I must have somehow missed that last page while searching. I followed the steps except the ones dealing with the router. I'm not using the same router it seems and couldn't find ivp6 to disable it on mine. I have it disabled through network manager though.

---

### Post by wildmanne39 on 2013-04-04
Did you do this > Go into your router and change 802.11bgn to just 802.11bg.

Thanks

---

### Post by Slixt on 2013-04-04
Okay, I found it and changed it to b/g mixed (was the only setting for it.) and left b/g protection checked. We'll see how it goes.

---

### Post by wildmanne39 on 2013-04-04
Crossing fingers and toes.

---

### Post by Slixt on 2013-04-04
Well, honestly I'm not noticing anything positive. I ran speedtest.net prior to doing this and the performance seemed to have dropped. I undid the changes and the results didn't increase much. Is that even a reliable site to test with?

---

### Post by Slixt on 2013-04-04
I'll leave it like this for a little bit and see if it's reliable. I had great speed, just unreliable it seemed. Playing games i'd be going fine, super fast.. then stall.. then go again and hit another stall down the line. It makes me wonder since I didn't have that in my windows laptop.

---

### Post by wildmanne39 on 2013-04-04
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by Slixt on 2013-04-04
Sorry for the late reply. I ended up reverting back to how it was because browsing had become noticeably slower. I'll go ahead and post the results of this. If you need me to switch it all back, I can do that too. One thing I did keep was the command to enable software encryption. That did seem to make things seem smoother.

---

### Post by Slixt on 2013-04-04
Sorry, the file exceeded the limit for the forum. I pastebinned it for you instead. Is there a way to clear my messages out at some point?

[http://pastebin.com/JFYNxpfg](http://pastebin.com/JFYNxpfg)

---

### Post by wildmanne39 on 2013-04-05
From what I see your signal strenth and link quality is low that effects speed and being able to connect.

Changing your channel in the router to 1 or 11 is recommended.
Also all the suggestions I mentioned earlier including  changing 802. to 802.11bg.

It would be my guess that when things slowed down more it is because your signal strength dropped and not the settings you changed.

The only other thing you can do is install the driver from the maker of the cards website, which is not real easy.

---

### Post by Slixt on 2013-04-05
Alright, thanks. I wasn't sure what else it could be either. Perhaps the hardware in my older pc is stronger then. It seemed to get a solid connection and maintain it where this one fluctuates. Sucks but, it is operational. It could be the wifi, I'll play around with the settings you recommended when I get some free time. Thanks for all of your help, it's greatly appreciated.

---

### Post by parantonis on 2013-05-10
Hello guys,
I made many tries in order to fix my slow internet (only wifi) problem but finally i cant. Do you think that my problem differs from other users who wrote before? and if no please tell me what i can do in order to fix it because this is the first ti me install ubuntu

lspci -nnk | grep -iA2 net result is:
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:013c]
    Kernel driver in use: tg3
--
04:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
    Kernel driver in use: iwlwifi



and lsmod result is :

Module                  Size  Used by
snd_hda_codec_hdmi     32476  1 
arc4                   12530  2 
coretemp               13642  0 
joydev                 17694  0 
acer_wmi               32845  0 
sparse_keymap          13891  1 acer_wmi
parport_pc             32867  0 
ppdev                  17114  0 
bnep                   18240  2 
rfcomm                 47562  0 
bluetooth             211812  10 bnep,rfcomm
snd_hda_codec_realtek    79756  1 
microcode              23030  0 
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
iwlwifi               399651  0 
psmouse               102075  0 
serio_raw              13216  0 
snd_hda_intel          34117  5 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
mac80211              555198  1 iwlwifi
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon                912794  4 
video                  19598  1 acer_wmi
cfg80211              208382  2 iwlwifi,mac80211
wmi                    19257  1 acer_wmi
mac_hid                13254  0 
snd                    83674  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    88495  1 radeon
drm_kms_helper         49259  1 radeon
drm                   290344  6 radeon,ttm,drm_kms_helper
i2c_algo_bit           13565  1 radeon
lpc_ich                17145  0 
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 47259  0 
tg3                   156594  0 
hid                   100815  2 hid_generic,usbhid

---

### Post by chili555 on 2013-05-10
> Do you think that my problem differs from other users who wrote before? The thread is 346 posts long. Which post and which user?

I suggest you search for iwlwifi and 11n_disable and try the temporary parameter to see if it helps. If not, start a new thread and we'll be happy to help.

---

### Post by Celzo on 2013-05-16
Hi, 
Same problem here.  My upload speed is fine but my download speed is slow as hell. Windows PC's work fine :/ 

Here are details

```
3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/
```

```
Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:0110]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
    Subsystem: Micro-Star International Co., Ltd. MN54G2 / MS-6894 Wireless Mini PCIe Card [1462:6894]
    Kernel driver in use: r8180
```

```
802.11b/g  link  ESSID:"marko"  
          Mode:Managed  Frequency=2.452 GHz  Access Point: 00:78:9E:FA:A8:D6   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=80/100  Signal level=-39 dBm  Noise level=-106 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.
```
```
     Size  Used by
michael_mic            12540  4 
arc4                   12473  2 
coretemp               13168  0 
joydev                 17161  0 
hid_generic            12445  0 
gpio_ich               13159  0 
snd_hda_codec_realtek    63356  1 
microcode              18209  0 
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
btusb                  17950  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  457161  2 
psmouse                84843  0 
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
serio_raw              13031  0 
lpc_ich                16925  0 
rfcomm                 37276  12 
drm_kms_helper         45271  1 i915
parport_pc             31968  0 
bnep                   17707  2 
ppdev                  12817  0 
bluetooth             183228  22 btusb,rfcomm,bnep
drm                   230463  3 i915,drm_kms_helper
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
r8187se               160853  0 
binfmt_misc            17260  1 
eeprom_93cx6           13134  1 r8187se
snd                    61991  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13197  1 i915
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
wmi                    18590  0 
video                  18847  1 i915
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
ums_realtek            17669  0 
uas                    17556  0 
r8169                  55976  0 
usb_storage            39350  1 ums_realtek


```

---

### Post by GeekyGamer14 on 2013-06-17
Same here, bump!

---

### Post by chili555 on 2013-06-17
> **GeekyGamer14 said:**
> Same here, bump!This thread is 350 posts long involving several different users and as many different wireless devices. I really doubt that, other than slow wireless, anything is the 'same here.' I suggest you start your own new thread and post:```
lspci -nn | grep 0280
iwconfig
nm-tool
```

---

### Post by idealistic on 2014-03-13
Hi,

My internet connection was fine yesterday and suddenly went down to really slow.
I read through the thread but don't seem to find anything to make it better, here are my specs :

```
DISTRIB_ID=UbuntuDISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux theo-laptop 2.6.32-57-generic #119-Ubuntu SMP Wed Feb 19 01:04:55 UTC 2014 i686 GNU/Linux
```

```
01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 22)	Kernel driver in use: sky2
	Kernel modules: sky2
02:00.0 Network controller [0280]: Atheros Communications Inc. AR5008 Wireless Network Adapter [168c:0024] (rev 01)
	Kernel driver in use: ath9k
	Kernel modules: ath9k
theo@theo-laptop:~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


usb0      no wireless extensions.


pan0      no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"EMOBILE-GL09P-EB61"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 7A:E8:B6:09:EB:61   
          Bit Rate=104 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

```
0: hci0: Bluetooth	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no



```

```
Module                  Size  Used byaes_i586                7268  1 
aes_generic            26863  1 aes_i586
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_hda_codec_idt      52074  1 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
snd_hda_codec          74297  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
rfcomm                 33547  4 
snd_seq_oss            26722  0 
arc4                    1153  2 
snd_seq_midi            4557  0 
binfmt_misc             6523  1 
uvcvideo               57438  0 
sco                     7949  2 
snd_rawmidi            19056  1 snd_seq_midi
i915                  290772  3 
videodev               34457  1 uvcvideo
ppdev                   5259  0 
v4l1_compat            13251  2 uvcvideo,videodev
drm_kms_helper         29361  1 i915
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ath9k                 306106  0 
bridge                 45710  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30688  16 rfcomm,bnep
drm                   163779  4 i915,drm_kms_helper
snd_seq                47295  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_algo_bit            5028  1 i915
mac80211              205434  1 ath9k
ath                     7611  1 ath9k
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lm75                    4631  0 
btusb                  11085  2 
coretemp                4417  0 
cdc_ether               3541  0 
joydev                  8740  0 
intel_agp              24375  2 i915
isight_firmware         1938  0 
video                  17375  1 i915
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
cfg80211              126528  3 ath9k,mac80211,ath
usbnet                 14975  1 cdc_ether
applesmc               21477  0 
agpgart                31724  2 drm,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
mii                     4381  1 usbnet
led_class               2864  2 ath9k,applesmc
output                  1871  1 video
appletouch              8368  0 
input_polldev           2482  1 applesmc
mbp_nvidia_bl           1867  0 
lp                      7060  0 
parport                32635  2 ppdev,lp
hid_apple               4765  0 
usbhid                 36110  0 
hid                    68263  2 hid_apple,usbhid
usb_storage            40033  0 
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
sky2                   40807  0 



```

Does anybody has a clue ?

thanks

---

### Post by wildmanne39 on 2014-03-13
Hi, please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Make your wireless settings match the screenshots.
Thanks

---

### Post by idealistic on 2014-03-13
Thanks for the quick reply.

I did the code, and my ipv6 setting is setted as "ignored", but actually i can't modify the connection informations, the "apply" button is grey and I can't click on it, is it a permission problem ? how do i get to fix it ?

thanks

---

### Post by idealistic on 2014-03-13
Oh actually I got it by just entering the pw in the "wireless security" thing.

But it doesn't seem to work any faster ...

---

### Post by wildmanne39 on 2014-03-13
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by idealistic on 2014-03-13
Here it is[ATTACH]251120[/ATTACH]

---

### Post by wildmanne39 on 2014-03-13
Do you have a mobile 3g adaptor plugged in? it looks like you do.

You can only use one at a time, that includes ethernet, so if you are using wireless disconnect all other internet devices. 

I suggest you remove the dashes from your network name.

You do know that 10.04 is not support any more, not even security updates?

You did not change your dns servers like I had them in the screenshots, this almost always helps a lot.

You should set your routers encryption to just wpa2 AES not mixed or TKIP.
Thanks

---

### Post by idealistic on 2014-03-14
Yes my internet is a mobile adaptator from EMobile, it works pretty fine normally.

I'm afraid if i upgrade my distribution it will make everything very slower cause it happened to me in the past and i had to reinstall ubuntu after that to Lucid.

I'm sorry I pasted actually the wrong file, it was from an hour ago.

Here is the new file with the changes made :[ATTACH]251121[/ATTACH]

and what do you mean by removing the dashes in the network name ? the "-" in the wireless network name ?

---

### Post by idealistic on 2014-03-14
And (sorry for being very ignorant abotu those things), what is a router encryption and how do i get to change it ?

---

### Post by idealistic on 2014-03-14
Ok i figured out some things, so i changed the router configuration encryption to Wpa2 psk AES, made it a name so there is no dashes anymore, but it doesn't change anything actually ...

---

### Post by idealistic on 2014-03-14
I don't know if it is of any use but anyway i attach the latest file for the specs just in case 
[ATTACH]251123[/ATTACH]

---

### Post by Raafi on 2014-03-20
I have same problem, how about this? Sorry for my bad English, maybe I can't asking well mannered. :-)
```
raafi@raafi-pc:~$ iwconfigeth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"**"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: **   
          Bit Rate=60 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:377   Missed beacon:0


raafi@raafi-pc:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Samsung Electronics Co Ltd Device [144d:4105]
    Kernel driver in use: ath9k
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c680]
    Kernel driver in use: r8169
raafi@raafi-pc:~$ lsmod
Module                  Size  Used by
ath9k                 151173  0 
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101512  3 hid_generic,usbhid
nls_iso8859_1          12713  0 
usb_storage            62062  0 
nvram                  14362  0 
parport_pc             32701  0 
ppdev                  17671  0 
joydev                 17377  0 
rfcomm                 69070  12 
bnep                   19564  2 
uvcvideo               80885  0 
ath3k                  13318  0 
snd_hda_codec_realtek    51465  1 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
btusb                  28267  0 
snd_hda_codec_hdmi     41276  1 
videodev              133390  2 uvcvideo,videobuf2_core
bluetooth             371874  23 bnep,ath3k,btusb,rfcomm
samsung_laptop         14486  0 
binfmt_misc            17468  1 
kvm_amd                59958  0 
kvm                   431315  1 kvm_amd
microcode              23518  0 
psmouse                97626  0 
serio_raw              13413  0 
k10temp                13126  0 
arc4                   12608  2 
dm_multipath           22843  0 
scsi_dh                14882  1 dm_multipath
ath9k_common           13859  1 ath9k
ath9k_hw              444645  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              596969  1 ath9k
snd_hda_intel          48171  10 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq_midi           13324  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              479757  3 ath,ath9k,mac80211
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
i2c_piix4              22106  0 
snd                    69141  31 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
radeon               1402449  4 
ttm                    83995  1 radeon
drm_kms_helper         52651  1 radeon
wmi                    19070  0 
video                  19318  1 samsung_laptop
drm                   296739  6 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
sdhci_pci              18985  0 
sdhci                  42630  1 sdhci_pci
r8169                  67341  0 
mii                    13934  1 r8169
ohci_pci               13561  0 
ahci                   25819  3 
libahci                31898  1 ahci
dm_mirror              22056  0 
dm_region_hash         20784  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
```

---

### Post by wildmanne39 on 2014-03-23
Please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
set your wireless settings in network manager to match the screenshots.
does that help?
Thanks

---

### Post by rohan4 on 2014-05-14
Hello sir @Wild Man
I'm having the same problem
```
rohan@rohan:~/Downloads$ lsmodModule                  Size  Used by
nls_utf8               12557  1 
udf                    89723  1 
crc_itu_t              12707  1 udf
ctr                    13049  2 
ccm                    17773  2 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
nls_iso8859_1          12713  2 
snd_hda_codec_hdmi     46207  1 
arc4                   12608  2 
rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
mac80211              626489  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              484040  2 mac80211,rtlwifi
joydev                 17381  0 
snd_hda_codec_via      27860  1 
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ghash_clmulni_intel    13259  0 
nouveau              1097199  3 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
aesni_intel            55624  4 
snd_timer              29482  2 snd_pcm,snd_seq
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau
ttm                    85115  1 nouveau
snd                    69238  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm_kms_helper         52758  1 nouveau
psmouse               102222  0 
serio_raw              13462  0 
drm                   302817  5 ttm,drm_kms_helper,nouveau
i2c_algo_bit           13413  1 nouveau
soundcore              12680  1 snd
lpc_ich                21080  0 
mei_me                 18627  0 
mei                    82274  1 mei_me
video                  19476  1 nouveau
mac_hid                13205  0 
parport_pc             32701  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18581  0 
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  5 hid_generic,usbhid,hid_logitech_dj
alx                    32452  0 
usb_storage            62209  1 
mdio                   13807  1 alx



```
i have netgear wireless adapter 
i tried manually changing drivers by comparing but got no luck(maybe i did some thing wrong)
using ubuntu 14.04 LTS
thanks!
my iwconfig 
```
rohan@rohan:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"New!!"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: F8:1A:67:A3:C3:DC   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:134   Missed beacon:0

```

---

### Post by wildmanne39 on 2014-05-14
Hi, you have drivers loaded for the usb device and your internal device, that causes conflicts, unplug the usb device, reboot and do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
does that improve your internal cards speed?
also set wireless settings in network manager to match the screenshots.
If you want to use the usb adaptor which I do not recommend you can blacklist the internal driver and that might help but it probably will not, I do not have the time to try to get the usb device working properly it will most likely mean installing a new driver.
Thanks

---

### Post by len4 on 2014-08-22
umm, hi... im new to using Ubuntu, and i have ubuntu 14.04 LTS, my wireless internet connection drops at times and doesnt come back for a while on some occassions. can someone help me? maybe walk me through a way to fix this problem? it would be much appreciated.

---

### Post by chili555 on 2014-08-23
> **len4 said:**
> umm, hi... im new to using Ubuntu, and i have ubuntu 14.04 LTS, my wireless internet connection drops at times and doesnt come back for a while on some occassions. can someone help me? maybe walk me through a way to fix this problem? it would be much appreciated.I suggest that, rather than tack on to a very long and old thread, you start your own new thread and give us details of your wireless device from: ```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my keyboard on the same key with \. Thanks.

---

### Post by len4 on 2014-08-23
thank you, i'll make sure to make a new thread then. :-)

---

