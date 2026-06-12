---
title: "wireless internet not working on ubuntu 11.04 (hp dv6000)"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by mozozo4 on 2011-09-26
Hi, i just recently got ubuntu 11.04 and everything works perfectly. 
The only thing is that the wireless internet does not work because there is only wired connections available.
The wired connections work but the wireless does not and i have been trying to fix it but i can't.
I have an hp dv6000 laptop and im running sta broadcom driver. 
I don't know that much about ubuntu yet, so please someone help me get wireless internet
Thanks

---

### Post by wildmanne39 on 2011-09-26
Hi, welcome to the forum! please open a terminal by hitting ctrl+alt+t then copy and paste these commands into it and then paste the results here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
```
sudo iwlist scan
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by mozozo4 on 2011-09-26
```

```michael@michael-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux michael-laptop 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686 athlon i386 GNU/Linux
michael@michael-laptop:~$ sudo lshw -C network
[sudo] password for michael: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b3200000-b3203fff
michael@michael-laptop:~$ lspci -nn | grep -e 0280 -e 0200
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
michael@michael-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

michael@michael-laptop:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
michael@michael-laptop:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
joydev                 17322  0 
binfmt_misc            13213  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
nvidia               7098106  37 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
hp_wmi                 13418  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13666  1 hp_wmi
wl                   2642531  0 
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
psmouse                73312  0 
k8temp                 12872  0 
serio_raw              12990  0 
nv_tco                 13331  0 
video                  18951  0 
i2c_nforce2            12906  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lib80211               14570  1 wl
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
forcedeth              58190  0 
sata_nv                23176  2 
pata_amd               13762  0 
michael@michael-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

by the way thank you for trying to help me

---

### Post by wildmanne39 on 2011-09-26
Hi, welcome to the forum! Please uninstall the driver you installed then restart your computer then run this command:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
after it is done installing, disconnect your wired connection,and run this command.
```
sudo modprobe b43
```
if it does not come on run this command and post the results here:
```
egrep -e b43 -e ssb  /etc/modprobe.d/*
```
Thank you

---

### Post by chili555 on 2011-09-26
I think the Wild Man is going to refer you to this: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)> CAUTION: This pci.id is also claimed by the Broadcom STA driver provided by bcmwl-kernel-source. Installation blacklists b43 and ssb. The driver bcmwl-kernel-source driver wl doesn't work well and b43 and ssb are preferred. To remove the incorrect driver and blacklist, do:
```
sudo apt-get remove -–purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```And now we return to our regularly scheduled expert!

---

### Post by wildmanne39 on 2011-09-26
Hi, thank you chili555 I suspect that will be the case also.

If it does not connect please run the commands given by chili555.

---

### Post by mozozo4 on 2011-09-27
by uninstalling the driver, do u mean the sta broadcom driver

---

### Post by wildmanne39 on 2011-09-27
Hi, yes that is what I meant, however if you run the commands in post 5 given by chili555 that will take care of uninstalling the driver and the removing of the b43 and ssb driver from being blacklist then it should work after a restart.
Thank you

---

### Post by mozozo4 on 2011-09-27
im sorry but im confused
so i shouldn't do wat u said but i should do wat chili said

---

### Post by wildmanne39 on 2011-09-27
Hi, yes do it the way chill555 said, it is the easiest way to do the same thing I said to do, it is just a different method which is a little quicker.
Thank you

---

### Post by mozozo4 on 2011-09-27
hi, this is wat it said in terminal after i typed in the commands that chili said

```

```michael@michael-laptop:~$ sudo apt-get remove -–purge bcmwl-kernel-source
[sudo] password for michael: 
E: Command line option '&#65533;' [from -–purge] is not known.
michael@michael-laptop:~$ sudo apt-get remove -–purge bcmwl-kernel-source
E: Command line option '&#65533;' [from -–purge] is not known.
michael@michael-laptop:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
michael@michael-laptop:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove `/etc/modprobe.d/blacklist-bcm43.conf': No such file or directory
michael@michael-laptop:~$

---

### Post by wildmanne39 on 2011-09-27
Hi, try it this way then:
```
sudo apt-get --purge remove bcmwl-kernel-source
```
also you can open synaptic and uninstall it from there.
Then restart your computer and run this command to install the b43 driver.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
then disconnect your wired connection after the b43 and firmware is done downloading.

Then 
```
sudo modprobe b43
```
and it should be working.
Thank you

---

### Post by mozozo4 on 2011-09-27
it worked!!!!!!!!!!
thank you [wildmanne39]("http://ubuntuforums.org/member.php?u=508533") and [chili555]("http://ubuntuforums.org/member.php?u=35909") 
i truly appreciate it 

thanks

---

### Post by wildmanne39 on 2011-09-27
Hi, your welcome! I am glad it is working.

---

### Post by mozozo4 on 2011-09-27
im so sorry but i messed up my whole ubuntu and i need help fixing it
i was playing with compiz and i pressed 3d cuber but then it says this will disable unity plugin or something like that

now my unity launcher and side bars aren't visible

also i managed to open terminal and typed in unity --reset
but then it was stuck on something and i pressed closed terminal


wat should i do? is there a way to reset ubuntu 11.04

im so sorry for being stupid enough to being able to mess up my ubuntu

---

### Post by wildmanne39 on 2011-09-27
Hi, its not you it is the way unity was made I did the same thing, and that is why I wrote a guide about it.

I hope you did not crash your system with the hard reboot.

In my signature there is a link that says setup the cube and effects in 11.04 click on it then scroll to the bottom of the page and there are directions for getting to a terminal one way or other, follow those directions and reset unity again this time let it run about three minutes then restart your computer.

Unity will never stop so just reboot by tapping your power button gently it will bring up a window so you can restart, then it should be back to normal.
Thank you

---

### Post by mozozo4 on 2011-09-27
in terminal should it be stuck on indicator added: libsession.so
 do i have to wait?

---

### Post by wildmanne39 on 2011-09-27
Hi, how long have you let it run?

I do not remember which errors it lists, there are so many, just let it run 3 minutes then reboot.
Thank you

---

### Post by mozozo4 on 2011-09-27
thank u so much again
u realy r a lifesaver

just another question: do i have to do anything with compiz or no?

---

### Post by wildmanne39 on 2011-09-27
Hi, no you don't but if you clicked on the link in my signature that is a guide to set the cube and effects up so they will work in unity and not break it if I have been helpful would you click on the red link in my signature and support me for ubuntu membership please? Also would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by mozozo4 on 2011-10-01
sorry dude, but i got another problem

i try to open synaptic package manager, but it gives me an error and it doesn't let me open it


E: Type '“deb' is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

can u please help me

---

