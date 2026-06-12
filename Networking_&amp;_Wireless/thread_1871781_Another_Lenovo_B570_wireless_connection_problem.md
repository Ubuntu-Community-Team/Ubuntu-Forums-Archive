---
title: "Another Lenovo B570 wireless connection problem"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by yoyo_58 on 2011-10-29
I have a Lenovo B570 dual boot configuration with Ubuntu 11.04 and cannot get a wireless connection.

The internet connection in the upper right hand corner shows "wireless disabled by hardware switch" and is grayed out.

I provide the following for diagnostic:

bill@bill-Lenovo-B570:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lenovo Device [17aa:30a1]
    Kernel driver in use: ath9k
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169


bill@bill-Lenovo-B570:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


bill@bill-Lenovo-B570:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
joydev                 17322  0 
binfmt_misc            13213  1 
arc4                   12473  2 
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ath9k                 103669  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
i915                  451048  3 
mac80211              257001  1 ath9k
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           13611  1 ath9k
uvcvideo               66851  0 
ath9k_hw              300328  2 ath9k,ath9k_common
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath                    19141  2 ath9k,ath9k_hw
drm_kms_helper         40971  1 i915
videodev               75143  1 uvcvideo
cfg80211              156212  3 ath9k,mac80211,ath
drm                   184164  4 i915,drm_kms_helper
psmouse                59039  0 
serio_raw              12990  0 
ideapad_laptop         13262  0 
sparse_keymap          13666  1 ideapad_laptop
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
r8169                  46630  0 
libahci                25548  1 ahci




bill@bill-Lenovo-B570:~$ dmesg | egrep 'b43|wl'
THIS COMMAND DID NOT RETURN ANYTHING




bill@bill-Lenovo-B570:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off




bill@bill-Lenovo-B570:~$ sudo iwlist scan
[sudo] password for bill: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


I would appreciate any help you can provide - thanks.

ETA - I did search and attempt the solutions I saw in 4 other Lenovo B570 threads including those marked [SOLVED], but I still couldn't get it to work.

---

### Post by yoyo_58 on 2011-10-29
btw, this is fresh install.  it would be no  problem for me to delete the partition and start over, perhaps with a different ubuntu build

---

### Post by yoyo_58 on 2011-10-29
a couple more notes

the wireless connection works fine in win7

i made sure the physical wireless switch in "on" and i also did fn + f5, still nuthin'

---

### Post by yoyo_58 on 2011-10-30
okay, so i found the following solution that worked.  i haven't tried to make it permanent yet.  i will report back after i do.

[COLOR=#404040][FONT=Verdana]**Solution for the Issue**
The following commands will enables wireless till next boot
sudo service network-manager stop
sudo rmmod acer_wmi
sudo modprobe acer_wmi
sudo rfkill unblock all
sudo service network-manager start

After this step the status message in the Network Manager will be &#8220;Wireless is disabled&#8221;
Now Enable wireless from the Network Manager using the following commands
sudo rmmod -f acer_wmi
Wireless networks will be detected and connected.
To make this change permanent use
sudo su
echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf
exit

Now if everything goes well you will have Wireless enabled on your Thinkpad. Thanks to David John for sending us the solution


and here's the link
[/FONT][/COLOR][http://www.zyxware.com/articles/1694/wireless-disabled-by-hardware-switch-issue-on-the-thinkpad-z570-in-ubuntu-solution](http://www.zyxware.com/articles/1694/wireless-disabled-by-hardware-switch-issue-on-the-thinkpad-z570-in-ubuntu-solution)

---

### Post by yoyo_58 on 2011-10-30
tested the permanent fix and it worked - Yay!

---

### Post by i8bugs on 2011-11-02
yoyo thanks for the thread.  Just bought a Lenovo B570 from Best Buy and was crossing my fingers on a fresh install when I ran into this wifi issue.  Back over to Win7, quick search, got your prescription and voilà, wireless works!  Now to reboot and make sure it sticks!  Thank goodness I understood how to use terminal from my early linux days- haven't done code in a couple years.
EDIT- Rebooted and the fix is permanent.  Sweet!  Now, need to look for touchpad preferences...

---

### Post by Dough13 on 2011-11-14
Thank you, this was an awesome find for me. I was worried I wouldn't be able to get a solution for this issue. Cheers.

---

### Post by willgreg21 on 2011-12-28
Thank you! Worked perfectly with my B570 with 11.10 and windows 7.

---

### Post by yoyo_58 on 2012-03-17
glad i could help, but i wasn't the one who figured it out.  believe me, i searched and searched to find this.  :)

---

### Post by droxy on 2012-05-08
Fix confirmed thank you very much

---

