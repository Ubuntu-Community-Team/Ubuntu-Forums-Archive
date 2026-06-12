---
title: "No Wifi, No Other OS"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by seniorPantaloons on 2011-06-10
Hey, UbuntuForums.
     I've been lurking around theses forums and I can't find a solution to this problem, nor can I find anyone else who is suffering from the same problem. 
     A little while ago, I accidentally uninstalled Windows Vista from my HP G60-117US laptop, the HP location of which can be found here: 

[http://search.hp.com/query.html?charset=iso-8859-1&lk=1&la=en&nh=10&st=1&rf=0&qs=&tridion=0&hpvc=sitewide&uf=1&qt=HP+G60-117US+Notebook+PC+us-117&ocoldqt=HP+G60+US-117&oc=3808697](http://search.hp.com/query.html?charset=iso-8859-1&lk=1&la=en&nh=10&st=1&rf=0&qs=&tridion=0&hpvc=sitewide&uf=1&qt=HP+G60-117US+Notebook+PC+us-117&ocoldqt=HP+G60+US-117&oc=3808697). 

When my Windows Vista went to the dogs, so did my HP wireless assistant. Now I don't know what to do, and I haven't had wi-fi for about a month, except for a brief 2 or 3 hour stint when wifi miraculously worked for me. Then I updated to 10.10, and wifi didn't work anymore, and then I updated to 11.04, and wifi still doesn't work. I have absolutely no idea what to do, being a general newbie to Ubuntu. Thanks for any help.

---

### Post by chili555 on 2011-06-10
> uninstalled Windows Vista You made a very wise decision, my friend; you shall never hear 'virus' again! Please open a terminal and run and post:```
rfkill list all
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```Some of these commands may say nothing; that's OK, it means, "Command executed with no errors to report, sir!"

---

### Post by seniorPantaloons on 2011-06-13
Hello, chili. Thanks for responding so quickly. I posted the code in the terminal, and I have the following end results:
```

1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

I am still unable to connect to connect to a wireless network, but I appreciate how far you've gotten me in my wifi hunt so far.

> **chili555 said:**
> You made a very wise decision, my friend; you shall never hear 'virus' again!
You know what they say. The day Microsoft makes something that doesn't suck is the day Microsoft makes a vacuum cleaner.

---

### Post by mazz on 2011-06-13
what driver are you using?
I have the opposite of your problem. 
soft blocked: yes
hard block : no

EDIT: Also I have to enable wireless every time I restart laptop.

I have a : HP G60-249WM

---

### Post by chili555 on 2011-06-13
> Hard blocked: yesThis strongly suggests that the actual hardware switch has the wireless turned to 'Off.' Can you please check and move it to 'On?'

---

### Post by seniorPantaloons on 2011-06-13
My hardware switch is a button that lies next to the power button at the top of the keyboard. No matter how many times I press it, wireless remains deactivated, and my Wireless LAN remains hard blocked. 

I did a quick google search and this page came up: 

[http://linuxtrap.wordpress.com/2009/11/25/hard-blocked-wireless-kill-switch-on-dell-laptop/](http://linuxtrap.wordpress.com/2009/11/25/hard-blocked-wireless-kill-switch-on-dell-laptop/)

Do you think that page would be able to help me at all?

---

### Post by mazz on 2011-06-13
Ok got mine to work. This is what I did:

```
sudo rfkill unblock all
```
```
sudo ifconfig wlan0 up
```

This fixed my **soft block **being yes. It should fix the **hard block **too.

My Laptop is  HP G60-249WM, but it should work for your laptop too, as it uses the same HP Driver.

---

### Post by seniorPantaloons on 2011-06-14
Hi, mazz.
I tried the code you recommended, and I got the following:
```

SIOCSIFFLAGS: Operation not possible due to RF-kill

```

---

### Post by chili555 on 2011-06-14
> **seniorPantaloons said:**
> My hardware switch is a button that lies next to the power button at the top of the keyboard. No matter how many times I press it, wireless remains deactivated, and my Wireless LAN remains hard blocked. 

I did a quick google search and this page came up: 

[http://linuxtrap.wordpress.com/2009/11/25/hard-blocked-wireless-kill-switch-on-dell-laptop/](http://linuxtrap.wordpress.com/2009/11/25/hard-blocked-wireless-kill-switch-on-dell-laptop/)

Do you think that page would be able to help me at all?That page deals with dell-laptop. Don't you have an HP?

Let's see all of your listing:```
lsmod
```

---

### Post by seniorPantaloons on 2011-06-14
Yes, I *do* have an HP laptop, but I thought "eh...well, I'll try just about anything."

Here are my results from lsmod:
```

else@else-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_conexant    43782  1 
binfmt_misc            13213  1 
nvidia               9766978  46 
joydev                 17322  0 
arc4                   12473  2 
ath9k                 103633  0 
mac80211              257001  1 ath9k
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
sparse_keymap          13666  0 
ath9k_common           13611  1 ath9k
snd_rawmidi            25269  1 snd_seq_midi
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              156212  3 ath9k,mac80211,ath
psmouse                73312  0 
video                  18951  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
k10temp                12951  0 
serio_raw              12990  0 
shpchp                 32345  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  1 
uas                    17676  0 
ahci                   21591  2 
libahci                25548  1 ahci
forcedeth              58190  0 
pata_amd               13762  0 

```

---

### Post by chili555 on 2011-06-14
As we sometimes say in the south, "I'm corn fused." Did you take some steps to remove or blacklist hp-wmi? I thought it was routinely loaded in HP laptops. When, a few posts ago, I asked you to remove (not blacklist) the module, there was no complaint that it wasn't present to be rmmodded. As well, the module sparse-keymap *is* loaded and it's a dependency of hp-wmi.

Dr. Chili is all like :confused::confused::confused:

---

### Post by seniorPantaloons on 2011-07-01
Sorry I haven't responded for two weeks. I've been pretty busy. Ubuntu stopped working for me, so I was stuck with a completely dead computer, until I re-installed Ubuntu using my flash drive on which I had already created a live install using Unetbootin. My wifi seems to work when I have Ubtunu 10.04 installed, but doesn't work at 10.10 or 11.04. Thanks for all your help, though.

---

