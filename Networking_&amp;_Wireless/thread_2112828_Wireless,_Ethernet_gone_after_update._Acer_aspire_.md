---
title: "Wireless, Ethernet gone after update. Acer aspire one"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by LifeEnemy on 2013-02-05
So I have an Acer aspire one 722 with Ubuntu 12.04. 2 days ago it suddenly stopped connecting to my Wi-Fi network. It showed the loading/connecting symbols but never connected. Windows side of my machine works fine. I tried the solution here:

askubuntu.com/questions/146948/internet-on-ubuntu-12-04-stopped-to-work-after-installing-updates-from-the-updat

That just made it worse. Now the Wi-Fi icon is empty and won't even list any networks. Apt-get check didn't show any dependency problems (there was an error message at first but it was gone once I installed more of the packages). 

I'm right in the middle of a busy week in school and I need internet! Please help! :[

---

### Post by LifeEnemy on 2013-02-05
Well, the icon changed back once, then I tried installing the 4.2 network manager from Ubuntu.com (in the link), and its back to nothing. I assume that the recent update broke the wireless... 

I'm already really behind with my work, this is the last thing I need!

---

### Post by LifeEnemy on 2013-02-05
It started attempting connections again a few minutes after I ran "modprobe b44" in a terminal. No idea what's going on, but any help would be greatly appreciated :)  it hasn't been a very good day for me

---

### Post by LifeEnemy on 2013-02-06
Please? :)

I've tried some of the solutions found about similar problems, but since at least one broke my computer before, I'd like to pinpoint the actual problem before trying again. I don't know much about this kind of thing.

---

### Post by LifeEnemy on 2013-02-06
bump

---

### Post by landersohn on 2013-02-06
I couldn't get my build in wireless card to work after upgrade to 12.04 with the same symptoms.
I bought a Buffalo USB wireless dongle, works like a charm. If you really need to have internet, getting a dongle may be the quickest solution.
I found Buffalo and Dlink work best.

---

### Post by LifeEnemy on 2013-02-06
Thanks for the suggestion, but I'm trying to survive on a meager grad student's budget :P

I've been using 12.04 with no issues (or at least rare issues) since last summer though, and it's only in the past week that my wifi has gone down. There must be a way to revert or something. I just don't want to break my system again trying another "solution" for someone else's problem.

I really don't like using Windows :(

---

### Post by LifeEnemy on 2013-02-07
*One* of the 150 who've looked at this thread have gotta have some advice. c'mon guys! :D

---

### Post by LifeEnemy on 2013-02-07
Hi all, 

About a week ago my wireless stopped working (constantly trying to connect but never does). I've tried some of the solutions here and other places, but nothing has worked. I tried ifconfig today and the only thing listed was "lo" wlan and eth0 were nowhere to be found. 

I'm not sure what to do at this point and I'm worried about breaking my computer even more messing around with incorrect solutions. 

I'm considering reinstalling but would rather not if I don't have to. 

Thanks in advance!

---

### Post by kr651129 on 2013-02-07
Just a shot in the dark but I've run into problems like this in the past where I needed to change the encryption type for the WiFi password.  If you're really out of things you could try you can try this just incase.

---

### Post by varunendra on 2013-02-07
Hi LifeEnemy (nice username btw ;)),

Please run following commands (you may copy-paste them in terminal) -
```
lspci -nnk | grep -iA2 net
lsmod
```
Copy-paste their outputs here.

This will allow us to see which network card you have and the driver loaded for it.

**PS:**
**If** (and only if) that happens to be a BCM4313 chip, this may help -
[http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896](http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896)

---

### Post by LifeEnemy on 2013-02-08
Thanks for the suggestions everyone! I'll try them as soon as I get home.

Varunendra, it's a holdover  from my highschool days. I've been using different names, since I'm supposed to seem more professional, sometimes ;)

---

### Post by LifeEnemy on 2013-02-10
Here are my outputs:

```
paul@paul-AO722:~$ lspci -nnk | grep -iA2 net
06:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: Acer Incorporated [ALI] Device [1025:0598]
	Kernel modules: atl1c
07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0510]
	Kernel driver in use: brcmsmac


paul@paul-AO722:~$ lsmod
Module                  Size  Used by
bcma                   25651  0 
arc4                   12473  2 
brcmsmac              540923  0 
mac80211              436493  1 brcmsmac
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
bluetooth             158479  7 bnep
brcmutil               14675  1 brcmsmac
binfmt_misc            17292  1 
cfg80211              178877  2 brcmsmac,mac80211
crc8                   12781  1 brcmsmac
snd_hda_codec_conexant    52554  1 
cordic                 12518  1 brcmsmac
snd_hda_codec_hdmi     31775  1 
snd_seq_midi           13132  0 
radeon                733824  3 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
psmouse                96718  0 
ttm                    65344  1 radeon
uvcvideo               67203  0 
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              13027  0 
videodev               86588  1 uvcvideo
snd_rawmidi            25424  1 snd_seq_midi
k10temp                12990  0 
drm_kms_helper         45466  1 radeon
drm                   197641  5 radeon,ttm,drm_kms_helper
sp5100_tco             13495  0 
i2c_piix4              13093  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
joydev                 17393  0 
i2c_algo_bit           13199  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  20 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
wmi                    18744  1 acer_wmi
video                  19068  0 
mac_hid                13077  0 
vhba                   17151  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid

```


I have the file from your link, varunendra. I'm going to switch over to ubuntu and try it.

---

### Post by LifeEnemy on 2013-02-10
Var,

I tried the solution you linked, and it seems to have worked! Thanks so much! :D I somehow missed that one.

---

