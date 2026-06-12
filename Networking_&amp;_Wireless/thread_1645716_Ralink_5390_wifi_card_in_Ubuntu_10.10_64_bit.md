---
title: "Ralink 5390 wifi card in Ubuntu 10.10 64 bit"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by akshay.guleria@gmail.com on 2010-12-14
**Problem**: 
Got a brand new HP laptop - HP g62x. Installed ubuntu 10.10 and found that I do not have a wlan interface as one would expect with an active wireless connection.

**Thanks to** 
Great discussion on similar work here @ [http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498). Just a different card.

**Solution:**
I used the above thread to do my work - banged my head against the wall a couple of times but it was fun :). I am listing down steps that finally worked for me. But before that, my configurations:
[LIST]
[*]Ubuntu 10.10
[*]64 bit
[*]WPA2 wireless network
[*]OS was freshly installed and there was no specific customization prior to this
[*]RaLink Device 5390. (use lspci to see your model number)
[/LIST]


[LIST=1]
[*]Download the driver from ralinktech.com --> Software --> Linux
[*]Unzip the download zip file anywhere. I did it in the default Downloads directory
[*]cd to the 2010_xxx extracted directory
[*]cd os/linux/
[*]Edit the config.mk file as below:
HAS_ATE=y (no change, it was originally as is)
HAS_WPA_SUPPLICANT=y (no change, it was originally as is)
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y (no change, it was originally as is)
HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n -- this was the only thing I modified) 
[*]Go back to the 2010_xx directory
[*]run command 'make'
[*]Make sure 'make compile' exists without errors. I got an error "too many arguments to format" towards the end of the compile but it did compile successfully eventually. And so I ignored the errors. You would see ***errors*** if the compile is not successful. In which, something went wrong and you may need to tweak the makefile or config.mk files before compile is successful.
[*]run command 'make install' as root. This is not listed in the README_STA_pci file that comes with downloaded driver zip file. This takes of copying the file to /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rt5390sta.ko. running depmod, creating /etc/Wireless/... folder.
[*]Edit the /etc/modules and add the line  at the end of this file
rt5390sta
[*]Edit the file /etc/modprobe.d/blacklist.conf and add the below line to it...
blacklist rt2800pci
[*]Reboot and you should see an ra0 interface when you run the command 'ifconfig'
[*]You may have to run '/etc/init.d/network-manager restart' command to have it show in the first go.
[*]Once, the wireless icon shows up, look for your wireless SSID and there you go surfing :)
[/LIST]

---

### Post by waseemriyaz on 2010-12-18
Thanks a lot man.

How to edit the /etc/modprobe   to add the line      rt5390sta ???   

I am waiting for your answer

Thanks..

---

### Post by akshay.guleria@gmail.com on 2010-12-18
> **waseemriyaz said:**
> Thanks a lot man.

How to edit the /etc/modprobe   to add the line      rt5390sta ???   

I am waiting for your answer

Thanks..

Sorry, that should be modules - typo :)
sudo gedit /etc/modules

---

### Post by waseemriyaz on 2010-12-18
I actually skipped step 9 and it worked fine for me. Thanks a lot. I thought I could never use ubuntu on hp g62x without wireless... 

the only change I made was , for make file to successfully compile without errors, you need to login to root then run make file.... then it will compile without errors..

[]("http://ubuntuforums.org/showpost.php?p=10240071&postcount=1")

---

### Post by akshay.guleria@gmail.com on 2010-12-18
glad my post helped. The "make install" generally does the whole trick so i guess after some more feedback, i could be confident that this is actually optional. I also have it disabled for me and it still works :)

---

### Post by rogermore on 2010-12-18
Thanks for this!

Just did a fresh install 10.04 and followed the steps, worked great....then when I updated to the latest kernel it stopped working and had to redo make/make install.  So it may have to be done every time?

---

### Post by akshay.guleria@gmail.com on 2010-12-18
Yes. i guess. thats the sad part :(. However, no other configurations. just do 
make
and
sudo make install

---

### Post by waseemriyaz on 2010-12-18
My sound is not working . Can any1 suggest me .. Mine is same hp G62x...

---

### Post by akshay.guleria@gmail.com on 2010-12-18
My sound card on Hp-G62x works out of box on 10.10. Is your sound card the same? 

#:~$ lshw -C sound
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-multimedia            
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:45 memory:d4400000-d4403fff
#:~$ 

BTW, you might get better responses on the Multimedia forum.

---

### Post by rogermore on 2010-12-19
I am having connection issues....will randomly loose the connection and then the only way to reconnect is close the screen and then once opened it is instantly connected again.  Any one have this issue or how to fix?

---

### Post by saber850 on 2010-12-20
Thanks for this info!  I also worried that I wouldn't be able to put linux on this laptop for my wife.

A couple things:

[LIST=1]
[*]Everyone who wants linux on this laptop should ask Ralink to incorporate their drivers into the mainline kernel so things will "just work" rather than have to manually setup the driver (and repeat the process for each kernel upgrade).
[*]I also have Ubuntu 10.10 on this laptop.  Whenever I reboot, the laptop's wireless is disabled (as indicated by a red light on the F12 key).  I don't know if this is a hardware or software default (or both).  Does anyone else's work this way?  Is there a way to have the laptop's wireless automatically enabled upon reboot?
[*]I use WPA2 to secure my network, and I do not broadcast my SSID.  Ubuntu 10.10 does not seem to automatically connect to (or even list) my wireless network in Network Manager upon reboot.  Each time, I have to go back and forth between enabling/disabling the laptop's wireless (Fn + F12) and instructing Ubuntu to connect to my network (Network Manager -> Connect to hidden wireless network).
Basically, does anyone's linux install on this laptop "just work" w/ regards to wireless connectivity?
[/LIST]

Thanks again for your help.

Nick

---

### Post by saber850 on 2010-12-20
> **akshay.guleria@gmail.com said:**
> My sound card on Hp-G62x works out of box on 10.10. Is your sound card the same? 


Sound output also worked out of the box for me (also using Ubuntu 10.10).  But my built-in microphone does not seem to work.

---

### Post by akshay.guleria@gmail.com on 2010-12-27
@nick

> 
[*]Everyone who wants linux on this laptop should ask Ralink to incorporate their drivers into the mainline kernel so things will "just work" rather than have to manually setup the driver (and repeat the process for each kernel upgrade).


Sure. or perhaps publish to multiverse repository or a repository of their own. Part of the problem being the support of "N" specifications for wireless which is new for all wireless vendors and so have not gotten mainstream into linux yet. But i am glad ralink has source code available so we can at least get it up and running somehow :)

> 
[*]I also have Ubuntu 10.10 on this laptop.  Whenever I reboot, the laptop's wireless is disabled (as indicated by a red light on the F12 key).  I don't know if this is a hardware or software default (or both).  Does anyone else's work this way?  Is there a way to have the laptop's wireless automatically enabled upon reboot?


For me, it connects to network automatically. I am on 11.04 beta. I remember on 10.10, i had a similar issue. However, it still keeps getting disconnected at times. However, it gets connected back instantly. Not sure if you too are facing the same problem.

> 
[*]I use WPA2 to secure my network, and I do not broadcast my SSID.  Ubuntu 10.10 does not seem to automatically connect to (or even list) my wireless network in Network Manager upon reboot.  Each time, I have to go back and forth between enabling/disabling the laptop's wireless (Fn + F12) and instructing Ubuntu to connect to my network (Network Manager -> Connect to hidden wireless network).
Basically, does anyone's linux install on this laptop "just work" w/ regards to wireless connectivity?


I have WPA2 and have it set to broadcast. Connection to network is automatic for me.  Other than it getting disconnected at times, i just works for me as of now :)

---

### Post by akshay.guleria@gmail.com on 2010-12-27
Haven't tried my microphone yet. Will let you know once i get there. 

> **saber850 said:**
> Sound output also worked out of the box for me (also using Ubuntu 10.10).  But my built-in microphone does not seem to work.

---

### Post by saber850 on 2010-12-30
> **akshay.guleria@gmail.com said:**
> 
Sure. or perhaps publish to multiverse repository or a repository of their own. Part of the problem being the support of "N" specifications for wireless which is new for all wireless vendors and so have not gotten mainstream into linux yet. But i am glad ralink has source code available so we can at least get it up and running somehow :)

Absolutely--source code is much better than nothing or binary-only drivers.

> 
For me, it connects to network automatically. I am on 11.04 beta. I remember on 10.10, i had a similar issue.
I'm not sure what changed (if anything), but now the laptop usually starts w/ the hardware's wireless enabled.  So that saves from having to enable it va Fn+F12.
But it does not connect automatically after reboot/resume/etc.  And it does not even list my network in the list--I have to choose "Connect to hidden wireless network" and then select my network from the drop-down list.  Only then is my network listed in the list, but it's till not connected (though it looks like it's trying and will eventually fail)! To connect, I then have to select my network from the list. Once I do that, it says I've been disconnected (which is incorrect because I was never connected in the first place) and then it connects.

> 
However, it still keeps  getting disconnected at times. However, it gets connected back  instantly. Not sure if you too are facing the same problem.
Unfortunately, my laptop also drops the connection periodically.  I have no idea what causes it.  Even worse, it does not automatically reconnect for me.  This is probably inline with Ubuntu not automatically connecting when I reboot/resume/etc.  I have to restart networking and Network Manager, then repeat the process above.  The drop out is frustrating my wife.

> 
I have WPA2 and have it set to broadcast. Connection to network is automatic for me.  Other than it getting disconnected at times, i just works for me as of now :)I can try enabling broadcast on my router to see if that helps.  But I'd really like to know the culprit(s) for this.  An older version of Ubuntu on another (older) laptop worked perfectly--it automatically connected after reboot/resume/etc and never dropped the connection.  I'd be very disappointed if any of these problems are Ubuntu 10.10's fault--that's supposed to be a stable release, right?

---

### Post by saber850 on 2010-12-30
> **akshay.guleria@gmail.com said:**
> Haven't tried my microphone yet. Will let you know once i get there.
I found that my audio's input was muted, so that may have been the problem.  I haven't checked yet.

---

### Post by saber850 on 2010-12-30
I confirmed that if I configure my router to broadcast the SSID, Ubuntu 10.10 automatically connects.

---

### Post by akshay.guleria@gmail.com on 2010-12-30
> **saber850 said:**
> I confirmed that if I configure my router to broadcast the SSID, Ubuntu 10.10 automatically connects.

Kind of interesting. Broadcast or hidden, if it in the profile, it should connect. Looks like Ubuntu network-manager needs some revamp :)

Good to know your problem is solved - at least - it is not frustrating for you anymore.

---

### Post by akshay.guleria@gmail.com on 2010-12-30
BTW, ralink seems to have a new version of the driver on their website for ra5390 card. I could not compile it but perhaps that will eliminate rest of the pain with this card.

---

### Post by saber850 on 2011-01-02
> **saber850 said:**
> I found that my audio's input was muted, so that may have been the problem.  I haven't checked yet.
I've confirmed that the problem w/ the built-in microphone was due to the input being muted--once I unmuted it, the mic worked.
Incidentally, Skype and this laptop w/ Ubuntu work out of the box (audio + video).

---

### Post by saber850 on 2011-01-02
> **akshay.guleria@gmail.com said:**
> BTW, ralink seems to have a new version of the driver on their website for ra5390 card. I could not compile it but perhaps that will eliminate rest of the pain with this card.
I'm not sure which version you're referring to, but I've been using what seems to be their latest (v2.4.0.4 released on 12/17/2010) since the beginning.  Unfortunately the connection still drops out, but fortunately if the SSID is broadcast, the connection is automatically restored shortly after.

---

### Post by akshay.guleria@gmail.com on 2011-01-02
i am using 2.4.0.2_Beta. Could not compile v2.4.0.4

> **saber850 said:**
> I'm not sure which version you're referring to, but I've been using what seems to be their latest (v2.4.0.4 released on 12/17/2010) since the beginning.  Unfortunately the connection still drops out, but fortunately if the SSID is broadcast, the connection is automatically restored shortly after.

---

### Post by saber850 on 2011-01-02
> **akshay.guleria@gmail.com said:**
> i am using 2.4.0.2_Beta. Could not compile v2.4.0.4
Interesting.  2.4.0.4 built for me w/out a problem by following your instructions.

I downloaded and installed Ubuntu 10.10, but System->About Ubuntu says I have 11.04, released (note the past tense) in April of 2011!  I just checked the downloaded ISO and at least the file name reports 10.10.  Whatever my version is, 2.4.0.4 built and installed fine.

---

### Post by StarGater93 on 2011-01-11
> **akshay.guleria@gmail.com said:**
> i am using 2.4.0.2_Beta. Could not compile v2.4.0.4

Can you still get 2.4.0.2_Beta / Anything other than 2.4.0.4 anywhere? because I am attempting this on a friends laptop running Kubuntu 10.10 and it cannot compile, not that I have much experience with compiling things besides Arch Makepkg commands - which don't count at all really... the PKGBUILDS do all the heavy lifting....

Anyhow -- If I am to be successful in yet another conversion to Linux, This laptop needs WiFi.

EDIT : I just noticed the Title of this thread states "64bit" and I installed 32bit on the comp in question btw... Usually 32bit is less of a pain than that of 64bit I would imagine so yeah....

---

### Post by StarGater93 on 2011-01-13
BUMP -- When you have over 9000 threads being created a second its not hard for a thread thats 2 min old to be buried....

---

### Post by saber850 on 2011-01-15
> **StarGater93 said:**
> Can you still get 2.4.0.2_Beta / Anything other than 2.4.0.4 anywhere? because I am attempting this on a friends laptop running Kubuntu 10.10 and it cannot compile, not that I have much experience with compiling things besides Arch Makepkg commands - which don't count at all really... the PKGBUILDS do all the heavy lifting....

Anyhow -- If I am to be successful in yet another conversion to Linux, This laptop needs WiFi.

EDIT : I just noticed the Title of this thread states "64bit" and I installed 32bit on the comp in question btw... Usually 32bit is less of a pain than that of 64bit I would imagine so yeah....
My laptop is also running the 32-bit build.  I didn't have any problems compiling 2.4.0.4.  What compiler errors are you getting?

---

### Post by rebeltaz on 2011-02-04
I downloaded the drivers from RaLink and installed them as described. When I activate the wireless card (F12 on my Compaq CQ56) the card comes on and the network connections are shown. However out of three routers, I can only connect to one. I have tried with and without WEP security, and all of the settings SEEM the same on the different routers. When trying to connect to two of the three routers, it just sits there trying, but never connects...

Can someone help with this problem? Any ideas?

---

### Post by ogretone on 2011-02-04
I have the G62x too.

lspci reports:
        02:00.0 Network controller: RaLink Device 5390

I'm having problems with version 2.4.0.4.  It compiles without errors.  I followed the steps as outlined in the first post.

NetworkManager shows all of the access points available.  When I select mine, it prompts for the key...  After I give it my password, it just never connects.  It keeps trying but never connects.

dmesg reports this (constantly):
Feb  4 20:29:43 mybox2 kernel: [   63.148834] AsicAdjustTxPower 1314 -> aaaa6666.
Feb  4 20:29:43 mybox2 kernel: [   63.148841] AsicAdjustTxPower 1318 -> aaaa6688.
Feb  4 20:29:43 mybox2 kernel: [   63.148861] AsicAdjustTxPower 131c -> aaaa6688.
Feb  4 20:29:43 mybox2 kernel: [   63.148864] AsicAdjustTxPower 1320 -> aaaa6688.
Feb  4 20:29:43 mybox2 kernel: [   63.148868] AsicAdjustTxPower 1324 -> cccc6688.
Feb  4 20:29:44 mybox2 kernel: [   64.146338] AsicAdjustTxPower 1314 -> aaaa6666.
Feb  4 20:29:44 mybox2 kernel: [   64.146345] AsicAdjustTxPower 1318 -> aaaa6688.
Feb  4 20:29:44 mybox2 kernel: [   64.146364] AsicAdjustTxPower 131c -> aaaa6688.
Feb  4 20:29:44 mybox2 kernel: [   64.146368] AsicAdjustTxPower 1320 -> aaaa6688.
Feb  4 20:29:44 mybox2 kernel: [   64.146372] AsicAdjustTxPower 1324 -> cccc6688.

I would appreciate any advice and direction on this.

Does anybody have the older driver source?  Maybe there is a problem with 2.4.0.4?

---

### Post by emoric on 2011-02-05
> **ogretone said:**
> I have the G62x too.

lspci reports:
        02:00.0 Network controller: RaLink Device 5390

I'm having problems with version 2.4.0.4.  It compiles without errors.  I followed the steps as outlined in the first post.

NetworkManager shows all of the access points available.  When I select mine, it prompts for the key...  After I give it my password, it just never connects.  It keeps trying but never connects.

dmesg reports this (constantly):
Feb  4 20:29:43 mybox2 kernel: [   63.148834] AsicAdjustTxPower 1314 -> aaaa6666.
Feb  4 20:29:43 mybox2 kernel: [   63.148841] AsicAdjustTxPower 1318 -> aaaa6688.
Feb  4 20:29:43 mybox2 kernel: [   63.148861] AsicAdjustTxPower 131c -> aaaa6688.
Feb  4 20:29:43 mybox2 kernel: [   63.148864] AsicAdjustTxPower 1320 -> aaaa6688.
Feb  4 20:29:43 mybox2 kernel: [   63.148868] AsicAdjustTxPower 1324 -> cccc6688.
Feb  4 20:29:44 mybox2 kernel: [   64.146338] AsicAdjustTxPower 1314 -> aaaa6666.
Feb  4 20:29:44 mybox2 kernel: [   64.146345] AsicAdjustTxPower 1318 -> aaaa6688.
Feb  4 20:29:44 mybox2 kernel: [   64.146364] AsicAdjustTxPower 131c -> aaaa6688.
Feb  4 20:29:44 mybox2 kernel: [   64.146368] AsicAdjustTxPower 1320 -> aaaa6688.
Feb  4 20:29:44 mybox2 kernel: [   64.146372] AsicAdjustTxPower 1324 -> cccc6688.

I would appreciate any advice and direction on this.

Does anybody have the older driver source?  Maybe there is a problem with 2.4.0.4?

+1

Bump for the exact problem.

---

### Post by mr_roboto on 2011-02-06
Hey everyone I have a hp dm1z series laptop and lspci tells me I have a 539f instead of 5390. Official specs tell me it has a 5390.

I followed the OP's instructions from beginning to end but here is the problem.

It can scan and look for network SSID's but the moment I enter the WPA2 password to try and connect, I see the network icon moving  and then it hard crashes.
Can't move mouse and no keyboard commands work.

Does anyone else with a hp dm1z have this problem , or anyone else have any insight?

Thanks

---

### Post by shoaibi on 2011-02-06
+1 for mr_roboto

Scenario:
- I have 593f instead of 5930. On Ralink site 5930 is the only one with ^5930* in it.
- I have tried using the manual provided in first post, succeeded upto where i could see ra0 in ifconfig, see scan results on commandline and network manager.

Problem:
a. when trying to connect to a network, as soon as i provide key, there is an error which hangs system, i can't move mouse, or change to ttys using keyboard, ssh to hanged box doesn't work either, boxes starts to act as brick. Possibly related log entries in syslog:

```

  6 14:28:25 eagle kernel: [   47.799814] Call Trace:
Feb  6 14:28:25 eagle kernel: [   47.799820]  [<ffffffff81084bcf>] ? up+0x2f/0x50
Feb  6 14:28:25 eagle kernel: [   47.799823]  [<ffffffff81061250>] ? release_console_sem+0x1c0/0x210
Feb  6 14:28:25 eagle kernel: [   47.799833]  [<ffffffffa068ad05>] CntlIdleProc+0xb5/0x170 [rt5390sta]
Feb  6 14:28:25 eagle kernel: [   47.799842]  [<ffffffffa068aed0>] MlmeCntlMachinePerformAction+0x110/0x1a0 [rt5390sta]
Feb  6 14:28:25 eagle kernel: [   47.799850]  [<ffffffffa0611e6c>] MlmeHandler+0x19c/0x2e0 [rt5390sta]
Feb  6 14:28:25 eagle kernel: [   47.799859]  [<ffffffffa0692436>] Set_SSID_Proc+0x1b6/0x2d0 [rt5390sta]
Feb  6 14:28:25 eagle kernel: [   47.799869]  [<ffffffffa069b1e3>] rt_ioctl_siwessid+0x113/0x150 [rt5390sta]
Feb  6 14:28:25 eagle kernel: [   47.799873]  [<ffffffff81564ec0>] ioctl_standard_iw_point+0x1d0/0x3e0
Feb  6 14:28:25 eagle kernel: [   47.799882]  [<ffffffffa069b0d0>] ? rt_ioctl_siwessid+0x0/0x150 [rt5390sta]
Feb  6 14:28:25 eagle kernel: [   47.799891]  [<ffffffffa0699d0b>] ? rt_ioctl_siwap+0x12b/0x160 [rt5390sta]
Feb  6 14:28:25 eagle kernel: [   47.799894]  [<ffffffff815650d0>] ? ioctl_standard_call+0x0/0xd0
Feb  6 14:28:25 eagle kernel: [   47.799896]  [<ffffffff81565c60>] ? ioctl_private_call+0x0/0xa0
Feb  6 14:28:25 eagle kernel: [   47.799899]  [<ffffffff81565171>] ioctl_standard_call+0xa1/0xd0
Feb  6 14:28:25 eagle kernel: [   47.799902]  [<ffffffff8149cbf0>] ? __dev_get_by_name+0xb0/0xd0
Feb  6 14:28:25 eagle kernel: [   47.799904]  [<ffffffff815650d0>] ? ioctl_standard_call+0x0/0xd0
Feb  6 14:28:25 eagle kernel: [   47.799907]  [<ffffffff8156445c>] wireless_process_ioctl+0x19c/0x1b0
Feb  6 14:28:25 eagle kernel: [   47.799909]  [<ffffffff815650d0>] ? ioctl_standard_call+0x0/0xd0
Feb  6 14:28:25 eagle kernel: [   47.799912]  [<ffffffff815644e1>] wext_ioctl_dispatch+0x71/0xb0
Feb  6 14:28:25 eagle kernel: [   47.799914]  [<ffffffff81565c60>] ? ioctl_private_call+0x0/0xa0
Feb  6 14:28:25 eagle kernel: [   47.799916]  [<ffffffff815645c6>] wext_handle_ioctl+0x46/0xa0
Feb  6 14:28:25 eagle kernel: [   47.799919]  [<ffffffff814899d0>] ? sys_sendmsg+0x240/0x3a0
Feb  6 14:28:25 eagle kernel: [   47.799921]  [<ffffffff8149f97f>] dev_ioctl+0x4df/0x4f0
Feb  6 14:28:25 eagle kernel: [   47.799925]  [<ffffffff8111e489>] ? __do_fault+0x479/0x560
Feb  6 14:28:25 eagle kernel: [   47.799927]  [<ffffffff81486bea>] sock_ioctl+0xea/0x2b0
Feb  6 14:28:25 eagle kernel: [   47.799930]  [<ffffffff811630fd>] vfs_ioctl+0x3d/0xd0
Feb  6 14:28:25 eagle kernel: [   47.799932]  [<ffffffff811639d1>] do_vfs_ioctl+0x81/0x340
Feb  6 14:28:25 eagle kernel: [   47.799935]  [<ffffffff8158e5ae>] ? do_page_fault+0x15e/0x350
Feb  6 14:28:25 eagle kernel: [   47.799937]  [<ffffffff81163d11>] sys_ioctl+0x81/0xa0
Feb  6 14:28:25 eagle kernel: [   47.799940]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
Feb  6 14:28:25 eagle kernel: [   47.799942] Code: 00 00 88 87 b0 ba 01 00 4c 89 ef e8 da 3d f8 ff 80 bb 89 aa 00 00 00 0f 88 6d 01 00 00 48 69 f0 b8 06 00 00 0f b6 8b d1 ba 01 00 <3a> 8c 33 fc 1a 05 00 0f 84 62 03 00 00 b9 ff ff ff ff 8b 93 80 
Feb  6 14:28:25 eagle kernel: [   47.799962] RIP  [<ffffffffa068a101>] CntlOidRTBssidProc+0xb1/0x570 [rt5390sta]
Feb  6 14:28:25 eagle kernel: [   47.799971]  RSP <ffff880242c0f9c8>
Feb  6 14:28:25 eagle kernel: [   47.799972] CR2: ffffcfb811a63444
Feb  6 14:28:25 eagle kernel: [   47.799974] ---[ end trace e812a409e00ad8ab ]---



```

b. when i create a network it just keeps showing same message again and again in log:
```


Feb  6 15:55:21 eagle kernel: [  347.049103] AsicAdjustTxPower 1324 -> cccc6688.
Feb  6 15:55:22 eagle kernel: [  348.056386] AsicAdjustTxPower 1314 -> aaaa6666.
Feb  6 15:55:22 eagle kernel: [  348.056416] AsicAdjustTxPower 1318 -> aaaa6688.
Feb  6 15:55:22 eagle kernel: [  348.056423] AsicAdjustTxPower 131c -> aaaa6688.
Feb  6 15:55:22 eagle kernel: [  348.056430] AsicAdjustTxPower 1320 -> aaaa6688.
Feb  6 15:55:22 eagle kernel: [  348.056437] AsicAdjustTxPower 1324 -> cccc6688.
Feb  6 15:55:23 eagle kernel: [  349.056489] AsicAdjustTxPower 1314 -> aaaa6666.
Feb  6 15:55:23 eagle kernel: [  349.056519] AsicAdjustTxPower 1318 -> aaaa6688.
Feb  6 15:55:23 eagle kernel: [  349.056526] AsicAdjustTxPower 131c -> aaaa6688.
Feb  6 15:55:23 eagle kernel: [  349.056533] AsicAdjustTxPower 1320 -> aaaa6688.
Feb  6 15:55:23 eagle kernel: [  349.056539] AsicAdjustTxPower 1324 -> cccc6688.
Feb  6 15:55:24 eagle kernel: [  350.064451] AsicAdjustTxPower 1314 -> aaaa6666.
Feb  6 15:55:24 eagle kernel: [  350.064481] AsicAdjustTxPower 1318 -> aaaa6688.
Feb  6 15:55:24 eagle kernel: [  350.064489] AsicAdjustTxPower 131c -> aaaa6688.
Feb  6 15:55:24 eagle kernel: [  350.064495] AsicAdjustTxPower 1320 -> aaaa6688.
Feb  6 15:55:24 eagle kernel: [  350.064502] AsicAdjustTxPower 1324 -> cccc6688.
Feb  6 15:55:25 eagle kernel: [  351.063451] GetDesiredTssiAndCurrentTssi: BBP TSSI INFO is not ready. (BbpR47 = 0x94)
Feb  6 15:55:25 eagle kernel: [  351.063459] AsicAdjustTxPower: Incorrect desired TSSI or current TSSI
Feb  6 15:55:25 eagle kernel: [  351.064587] AsicAdjustTxPower 1314 -> aaaa6666.
Feb  6 15:55:25 eagle kernel: [  351.064595] AsicAdjustTxPower 1318 -> aaaa6688.
Feb  6 15:55:25 eagle kernel: [  351.064617] AsicAdjustTxPower 131c -> aaaa6688.
Feb  6 15:55:25 eagle kernel: [  351.064623] AsicAdjustTxPower 1320 -> aaaa6688.
Feb  6 15:55:25 eagle kernel: [  351.064630] AsicAdjustTxPower 1324 -> cccc6688.
Feb  6 15:55:26 eagle kernel: [  352.071313] AsicAdjustTxPower 1314 -> aaaa6666.
Feb  6 15:55:26 eagle kernel: [  352.071343] AsicAdjustTxPower 1318 -> aaaa6688.
Feb  6 15:55:26 eagle kernel: [  352.071351] AsicAdjustTxPower 131c -> aaaa6688.
Feb  6 15:55:26 eagle kernel: [  352.071357] AsicAdjustTxPower 1320 -> aaaa6688.
Feb  6 15:55:26 eagle kernel: [  352.071364] AsicAdjustTxPower 1324 -> cccc6688.
Feb  6 15:55:27 eagle kernel: [  353.061929] AsicAdjustTxPower 1314 -> aaaa6666.
Feb  6 15:55:27 eagle kernel: [  353.061958] AsicAdjustTxPower 1318 -> aaaa6688.
Feb  6 15:55:27 eagle kernel: [  353.061966] AsicAdjustTxPower 131c -> aaaa6688.
Feb  6 15:55:27 eagle kernel: [  353.061973] AsicAdjustTxPower 1320 -> aaaa6688.
Feb  6 15:55:27 eagle kernel: [  353.061980] AsicAdjustTxPower 1324 -> cccc6688.
Feb  6 15:55:28 eagle kernel: [  354.060657] AsicAdjustTxPower 1314 -> aaaa6666.
Feb  6 15:55:28 eagle kernel: [  354.060688] AsicAdjustTxPower 1318 -> aaaa6688.
Feb  6 15:55:28 eagle kernel: [  354.060695] AsicAdjustTxPower 131c -> aaaa6688.
Feb  6 15:55:28 eagle kernel: [  354.060702] AsicAdjustTxPower 1320 -> aaaa6688.
Feb  6 15:55:28 eagle kernel: [  354.060709] AsicAdjustTxPower 1324 -> cccc6688.
Feb  6 15:55:29 eagle kernel: [  355.060735] GetDesiredTssiAndCurrentTssi: BBP TSSI INFO is not ready. (BbpR47 = 0x94)
Feb  6 15:55:29 eagle kernel: [  355.060744] AsicAdjustTxPower: Incorrect desired TSSI or current TSSI



```

System Details:
```


Linux eagle 2.6.35-26-generic #46-Ubuntu SMP Sun Jan 30 06:59:07 UTC 2011 x86_64 GNU/Linux


No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick


```


Attached detailed lspci, lshw, lsmod, dmesg and syslog.

[edit]:
( -My earlier post: [http://ubuntuforums.org/showthread.php?t=1681956](http://ubuntuforums.org/showthread.php?t=1681956) )
(HP Support Forum: [http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/HP-Pavilion-Dv6-4001tx-and-Multiple-Issues/td-p/511921](http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/HP-Pavilion-Dv6-4001tx-and-Multiple-Issues/td-p/511921) )

---

### Post by rebeltaz on 2011-02-06
I'm glad to see that I am not the only one with this problem. In my case, I may have to disable the built in wireless and use a USB wireless if no one can shed some light on this problem... :(

---

### Post by cherryred714 on 2011-02-06
):P[B]
my computer-toshiba satellite currently running on ubuntu 10.10 i cant connect to wireless except when im at my parents house not to sure why it was working now all of a sudden it stopped while i was using 10.04 figure when i upgraded to 10.10 it would fix it self ..didnt happen so im stumped when i right click on the satelite it the top right of my screen it shows-
-enable networking-(witch is checked) 
-enable wireless-(witch willnot allow me to click it) 
-enable notifications-(witch is checked) 
-connection information- (wont allow) 
-edit connections..- 
-about- 
dont know why it wont allow me to enable the wireless but am kinda desprate for answers now anyone ???.....[/B] :confused:

---

### Post by spaceharrier on 2011-02-06
> **mr_roboto said:**
> Hey everyone I have a hp dm1z series laptop and lspci tells me I have a 539f instead of 5390. Official specs tell me it has a 5390.

I followed the OP's instructions from beginning to end but here is the problem.

It can scan and look for network SSID's but the moment I enter the WPA2 password to try and connect, I see the network icon moving  and then it hard crashes.
Can't move mouse and no keyboard commands work.

Does anyone else with a hp dm1z have this problem , or anyone else have any insight?


Yep, same laptop, same reported wireless card, same problem. Symptoms are similar/the same as ogretone reported above. This happens on both 2.6.35-22 and -25. 

(I've tried a few different driver versions and the steps reported in various successful threads.)

---

### Post by edwin_aldrin on 2011-02-08
I have the same problem. It just sits there trying to connect and never connects. Pops up the prompt for the SSID and the password.

---

### Post by stubbsPY on 2011-02-08
> **spaceharrier said:**
> Yep, same laptop, same reported wireless card, same problem. Symptoms are similar/the same as ogretone reported above. This happens on both 2.6.35-22 and -25. 

(I've tried a few different driver versions and the steps reported in various successful threads.)

Same here. HP dm1z-3000 (the new AMD Fusion version). Last night I got desperate and tried the Natty alpha 2, hoping that the new kernel would cooperate better w/ the Ralink wireless driver. No such luck. Driver compiles and installs fine, but then output looks like what's posted above; system hangs as soon as Network Manager tries to connect.

---

### Post by mrmagos on 2011-02-08
> **stubbsPY said:**
> Same here. HP dm1z-3000 (the new AMD Fusion version). Last night I got desperate and tried the Natty alpha 2, hoping that the new kernel would cooperate better w/ the Ralink wireless driver. No such luck. Driver compiles and installs fine, but then output looks like what's posted above; system hangs as soon as Network Manager tries to connect.

I have the same system as you, but I've yet to get the module to compile. I figured it had to do with Natty's kernel, but if you got it to work, I'll go back and check the options. Sounds as if the endeavor is moot, since it still doesn't work.

I'm thinking we should probably start a new thread instead of hijacking this one.

---

### Post by rebeltaz on 2011-02-08
> **mrmagos said:**
> I'm thinking we should probably start a new thread instead of hijacking this one.

I tried that already - [http://ubuntuforums.org/showthread.php?t=1681297](http://ubuntuforums.org/showthread.php?t=1681297) - with absolutely no response...

---

### Post by mrmagos on 2011-02-08
> **rebeltaz said:**
> I tried that already - [http://ubuntuforums.org/showthread.php?t=1681297](http://ubuntuforums.org/showthread.php?t=1681297) - with absolutely no response...

At least on your system the card shows up as a 5930. On mine it comes up as a 593f - those of us with a different card should probably start a new thread.

---

### Post by spaceharrier on 2011-02-10
I've emailed Ralink tech support asking if there's anything we can adjust to make the current driver work with the "549f" or, if not, if they're expecting an upcoming Linux driver to support it.

We'll see if they say anything.

---

### Post by stubbsPY on 2011-02-10
I created a new thread for all of us dm1z'ers, as this one is marked solved and isn't likely to see any attention.

Go post there so we can get the help we need!

[http://ubuntuforums.org/showthread.php?t=1685430]("http://ubuntuforums.org/showthread.php?t=1685430")

---

### Post by ricardon on 2011-02-12
Hi,

I had the same problem with my HP G62 with Ralink 5390 network adapter. I could compile the driver by downloading the source code from Ralink but after installing it tried to connect forever without success. I also saw the "3.061929] AsicAdjustTxPower 1314 -> aaaa6666" in dmesg over and over. I did some research and I found that OpenSUSE includes this driver in their releases and does some modifications to it. I took their code, which is the same you can get from Ralink website. Basically, I followed the same steps as described at the top of this thread, but with the additional SUSE patches. Here are the steps that I followed:

1. Download code from here
[https://build.opensuse.org/package/binary?arch=x86_64&filename=rt5390sta-2.4.0.4-6.2.src.rpm&package=rt5390sta&project=driver%3Awireless&repository=11.3-update](https://build.opensuse.org/package/binary?arch=x86_64&filename=rt5390sta-2.4.0.4-6.2.src.rpm&package=rt5390sta&project=driver%3Awireless&repository=11.3-update)

In the future, more recent releases could be used. I used 11.3-update.

2. Apply the patches contained in the RPM. I left out rt5390sta-2.4.0.4-gcc-warnings-x86_64.patch as I am using 10.10 32-bit.

3. Rename RT2860STA.dat  as RT5390STA.dat

5. Build as shown at the beginning of this thread: make

6. make install will fail as the .dat file was renamed. Hence, copy manually
   sudo mkdir /etc/Wireless/RT5390STA
   sudo cp /etc/Wireless/RTA5390STA/RTA5390STA.dat

7. Copy manually the kernel module to your modules directory.
     sudo cp ./os/linux/rt5390sta.ko /lib/modules/2.6.35-25-generic/kernel/drivers/net/wireless/

8. Edit /etc/modules to add the line 'rt5390sta'

9. Reboot and find your network SSID. It may be possible that you need to restart the network manager with 'sudo restart network-manager'

Now I can connect to my wireless network. I have tried with WEP and WPA2.

I know this is for 32-bit but as I saw the same problems discussed here, this could also help in the 64-bit version.

---

### Post by edwin_aldrin on 2011-02-13
How do I apply certain patches (and leave out certain others) from rpm package? Please pardon my ignorance but I never had to deal with rpms in the Ubuntu environment.

---

### Post by ricardon on 2011-02-13
Hi edwin_aldrin,

To open an RPM package, just download it then double-click on it as you would do with any TAR or ZIP. It will be opened and you will see the contents. You will see a TAR with the driver code from Ralink and a set of patches. Just extract the contents of the RPM to some directory of your choice. Then, extract the driver code TAR in that directory and your directory should look like

#cd myDir
#ls
driverCodeDir
patch1.patch
patch2.patch
...
patchN.patch

then change to the driver code directory and apply the patches as follows
#cd driverCodeDir
#patch -p0 <../patch1.patch
#patch -p0 <../patch2.patch
..
#patch -p0 <../patchN.patch

To know the order in which you need to apply the patches, look at the rt5390sta.spec file lines 38-44. If you are using 10.10 32-bit apply all patches except rt5390sta-2.4.0.4-gcc-warnings-x86_64.patch. For 10.10 64-bit, apply all patches.

---

### Post by spaceharrier on 2011-02-14
> **ricardon said:**
> Hi,

I had the same problem with my HP G62 with Ralink 5390 network adapter. I could compile the driver by downloading the source code from Ralink but after installing it tried to connect forever without success. I also saw the "3.061929] AsicAdjustTxPower 1314 -> aaaa6666" in dmesg over and over. I did some research and I found that OpenSUSE includes this driver in their releases and does some modifications to it. I took their code, which is the same you can get from Ralink website. Basically, I followed the same steps as described at the top of this thread, but with the additional SUSE patches. Here are the steps that I followed:

1. Download code from here
[https://build.opensuse.org/package/binary?arch=x86_64&filename=rt5390sta-2.4.0.4-6.2.src.rpm&package=rt5390sta&project=driver%3Awireless&repository=11.3-update](https://build.opensuse.org/package/binary?arch=x86_64&filename=rt5390sta-2.4.0.4-6.2.src.rpm&package=rt5390sta&project=driver%3Awireless&repository=11.3-update)

In the future, more recent releases could be used. I used 11.3-update.

2. Apply the patches contained in the RPM. I left out rt5390sta-2.4.0.4-gcc-warnings-x86_64.patch as I am using 10.10 32-bit.

3. Rename RT2860STA.dat  as RT5390STA.dat

5. Build as shown at the beginning of this thread: make

6. make install will fail as the .dat file was renamed. Hence, copy manually
   sudo mkdir /etc/Wireless/RT5390STA
   sudo cp /etc/Wireless/RTA5390STA/RTA5390STA.dat

7. Copy manually the kernel module to your modules directory.
     sudo cp ./os/linux/rt5390sta.ko /lib/modules/2.6.35-25-generic/kernel/drivers/net/wireless/

8. Edit /etc/modules to add the line 'rt5390sta'

9. Reboot and find your network SSID. It may be possible that you need to restart the network manager with 'sudo restart network-manager'

Now I can connect to my wireless network. I have tried with WEP and WPA2.

I know this is for 32-bit but as I saw the same problems discussed here, this could also help in the 64-bit version.

Confirmed working on dm1z, Kernel 2.6.35-25 on 10.10 64-bit. Let's hope that turns into out-of-box support soon.

---

### Post by mr_roboto on 2011-02-14
Since some of you guys got it working, can you guys tell me what I am doing wrong?

First I patch in the order of the .spec file. (all patches as i am 64bit)
Rename RT5390STA.dat
sudo make
sudo make install
sudo mkdir -p /etc/Wireless/RT5390STA
sudo cp RT5390STA.dat /etc/Wireless/RTA5390STA/
sudo cp ./os/linux/rt5390sta.ko /lib/modules/2.6.35-25-generic/kernel/drivers/net/wireless/
Edit /etc/modules to add the line 'rt5390sta'
reboot
then sudo restart network-manager

I have a feeling I am forgetting something simple or stupid :/

---

### Post by adamhooper on 2011-02-15
> **ricardon said:**
> Hi,

I had the same problem with my HP G62 with Ralink 5390 network adapter. I could compile the driver by downloading the source code from Ralink but after installing it tried to connect forever without success. I also saw the "3.061929] AsicAdjustTxPower 1314 -> aaaa6666" in dmesg over and over. I did some research and I found that OpenSUSE includes this driver in their releases and does some modifications to it. I took their code, which is the same you can get from Ralink website. Basically, I followed the same steps as described at the top of this thread, but with the additional SUSE patches. Here are the steps that I followed:

1. Download code from here
[https://build.opensuse.org/package/binary?arch=x86_64&filename=rt5390sta-2.4.0.4-6.2.src.rpm&package=rt5390sta&project=driver%3Awireless&repository=11.3-update](https://build.opensuse.org/package/binary?arch=x86_64&filename=rt5390sta-2.4.0.4-6.2.src.rpm&package=rt5390sta&project=driver%3Awireless&repository=11.3-update)

In the future, more recent releases could be used. I used 11.3-update.

2. Apply the patches contained in the RPM. I left out rt5390sta-2.4.0.4-gcc-warnings-x86_64.patch as I am using 10.10 32-bit.

3. Rename RT2860STA.dat  as RT5390STA.dat

5. Build as shown at the beginning of this thread: make

6. make install will fail as the .dat file was renamed. Hence, copy manually
   sudo mkdir /etc/Wireless/RT5390STA
   sudo cp /etc/Wireless/RTA5390STA/RTA5390STA.dat

7. Copy manually the kernel module to your modules directory.
     sudo cp ./os/linux/rt5390sta.ko /lib/modules/2.6.35-25-generic/kernel/drivers/net/wireless/

8. Edit /etc/modules to add the line 'rt5390sta'

9. Reboot and find your network SSID. It may be possible that you need to restart the network manager with 'sudo restart network-manager'

Now I can connect to my wireless network. I have tried with WEP and WPA2.

I know this is for 32-bit but as I saw the same problems discussed here, this could also help in the 64-bit version.

Confirming this works (for at least 15 minutes) on a dm1z-3000 with 64-bit Natty (11.04) connecting to a WPA network. No need to add anything to /etc/modules, but I did need to run "sudo depmod -a", turn on the wireless card and then reboot. (I think that might be because I'd previously been tinkering with the non-RPM version.)

---

### Post by edwin_aldrin on 2011-02-15
Worked for me. I am also on a 32-bit version. The patches rock and roll. I am loving this.

mr_roboto, did u blacklist 2860? You might want to look at the steps described at the beginning of the thread, on page 1.

---

### Post by mrmagos on 2011-02-15
> **mr_roboto said:**
> Since some of you guys got it working, can you guys tell me what I am doing wrong?

First I patch in the order of the .spec file. (all patches as i am 64bit)
Rename RT5390STA.dat
sudo make
sudo make install
sudo mkdir -p /etc/Wireless/RT5390STA
sudo cp RT5390STA.dat /etc/Wireless/RTA5390STA/
sudo cp ./os/linux/rt5390sta.ko /lib/modules/2.6.35-25-generic/kernel/drivers/net/wireless/
Edit /etc/modules to add the line 'rt5390sta'
reboot
then sudo restart network-manager

I have a feeling I am forgetting something simple or stupid :/

You either need to wait and rename the .dat until after your run 'make install' or you need to run 'sudo depmod -a'

---

### Post by mr_roboto on 2011-02-16
> **mrmagos said:**
> You either need to wait and rename the .dat until after your run 'make install' or you need to run 'sudo depmod -a'

Yep that did it, I moved the .dat after the make and make install. Thanks everyone, working great on my hp dm1z maverick 64bit

---

### Post by edwin_aldrin on 2011-02-19
I noticed that sometimes I lose connection. I see "Connecting" state for about 40 sec. and most of the times it reconnects. Has anyone else observed these intermittent problems? I am running 32 bit OS and followed the steps for the 32 bit installation. I also changed the property of the wireless network to be "Available to all users" so it does not keep asking me for the keyring password.

---

### Post by san000 on 2011-02-21
I followed the steps and my wifi connection is working now, but Im having regular desconnections too and no matter how long I wait or try, I have to reboot to be able to connect again.


Anyone having the same problem? Any solution?

---

### Post by t0adman on 2011-03-03
I'm awaiting my dm1z and intend to load 10.10 64-bit in dual boot initially, then remove Win7 entirely if enough functionality exists.  

For those of you dm1z owners running Ubuntu, what are the most significant missing pieces?

---

### Post by Quwartz on 2011-03-08
Hello.

Been lurking on this thread for a while. I have to say thanks to all for helping me getting my dm1z with 10.10 64 on-line wirelessly. I had another problem though... after updating the kernel wireless quit working once again. What files would I have to move to get WiFi working again, or would I have to redo it all for this kernel?

---

### Post by mrmagos on 2011-03-09
> **Quwartz said:**
> Hello.

Been lurking on this thread for a while. I have to say thanks to all for helping me getting my dm1z with 10.10 64 on-line wirelessly. I had another problem though... after updating the kernel wireless quit working once again. What files would I have to move to get WiFi working again, or would I have to redo it all for this kernel?

You will have to run 'make' and 'make install' again for the new kernel.

As an aside, has anyone had success with bluetooth with this card? Syslog shows that it goes into discovery mode, but it doesn't seem to be able to pick up any devices.

---

### Post by Walpy on 2011-03-10
High five!

Thanks, it is working for me now on my Ubuntu 10.04

---

### Post by Walpy on 2011-03-14
> **waseemriyaz said:**
> My sound is not working . Can any1 suggest me .. Mine is same hp G62x...

Move to this tread for sound fix on HP-G62. This did the thing for me...
[http://ubuntuforums.org/showthread.php?t=1570060](http://ubuntuforums.org/showthread.php?t=1570060)

---

### Post by jackharvest on 2011-03-20
> **t0adman said:**
> I'm awaiting my dm1z and intend to load 10.10 64-bit in dual boot initially, then remove Win7 entirely if enough functionality exists.  

For those of you dm1z owners running Ubuntu, what are the most significant missing pieces?

The biggest piece missing on the DM1 is the touchpad. The damn thing doesn't support multitouch, so drag and drop with two fingers causes major mouse jumping. Not sure if anyone has a fix for it yet - hoping for a link once there's a fix, as I'm sure you are.

---

### Post by jackharvest on 2011-03-20
> **ricardon said:**
> Hi edwin_aldrin,

To open an RPM package, just download it then double-click on it as you would do with any TAR or ZIP. It will be opened and you will see the contents. You will see a TAR with the driver code from Ralink and a set of patches. Just extract the contents of the RPM to some directory of your choice. Then, extract the driver code TAR in that directory and your directory should look like

#cd myDir
#ls
driverCodeDir
patch1.patch
patch2.patch
...
patchN.patch

then change to the driver code directory and apply the patches as follows
#cd driverCodeDir
#patch -p0 <../patch1.patch
#patch -p0 <../patch2.patch
..
#patch -p0 <../patchN.patch

To know the order in which you need to apply the patches, look at the rt5390sta.spec file lines 38-44. If you are using 10.10 32-bit apply all patches except rt5390sta-2.4.0.4-gcc-warnings-x86_64.patch. For 10.10 64-bit, apply all patches.

O_o Can somebody turn this into a file that an Ubuntu noob can just run? I love Ubuntu, but sometimes us dumbass folk need some slack. If not, I guess I'll have to wait for official support. -_-

---

### Post by palimmo on 2011-03-20
Hi guys!

Can someone resume the trick to solve (more or less) this problem with Ralink 5390?

If it isn't solved, can someone open a "real" bug in Launchpad?
[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)
Maybe Ubuntu experts can save us!

Thank you!!!

---

### Post by Walpy on 2011-03-20
> **palimmo said:**
> Hi guys!

Can someone resume the trick to solve (more or less) this problem with Ralink 5390?

If itsn't solved, can someone open a "real" bug in Launchpad?
[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)
Maybe Ubuntu experts can save us!

Thank you!!!

See first post

---

### Post by saber850 on 2011-03-27
FYI for those who asked me about my status on this issue.  The networking problem on this laptop gradually got worse, and I was not getting any support from Ralink.  So I ended up returning the laptop and getting a different make & model (thank goodness for COSTCO's return policy!).

Good luck w/ this.

---

### Post by en4ian on 2011-04-03
> **ricardon said:**
> Hi,

I had the same problem with my HP G62 with Ralink 5390 network adapter. I could compile the driver by downloading the source code from Ralink but after installing it tried to connect forever without success. I also saw the "3.061929] AsicAdjustTxPower 1314 -> aaaa6666" in dmesg over and over. I did some research and I found that OpenSUSE includes this driver in their releases and does some modifications to it. I took their code, which is the same you can get from Ralink website. Basically, I followed the same steps as described at the top of this thread, but with the additional SUSE patches. Here are the steps that I followed:

1. Download code from here
[https://build.opensuse.org/package/binary?arch=x86_64&filename=rt5390sta-2.4.0.4-6.2.src.rpm&package=rt5390sta&project=driver%3Awireless&repository=11.3-update](https://build.opensuse.org/package/binary?arch=x86_64&filename=rt5390sta-2.4.0.4-6.2.src.rpm&package=rt5390sta&project=driver%3Awireless&repository=11.3-update)

In the future, more recent releases could be used. I used 11.3-update.

2. Apply the patches contained in the RPM. I left out rt5390sta-2.4.0.4-gcc-warnings-x86_64.patch as I am using 10.10 32-bit.

3. Rename RT2860STA.dat  as RT5390STA.dat

5. Build as shown at the beginning of this thread: make

6. make install will fail as the .dat file was renamed. Hence, copy manually
   sudo mkdir /etc/Wireless/RT5390STA
   sudo cp /etc/Wireless/RTA5390STA/RTA5390STA.dat

7. Copy manually the kernel module to your modules directory.
     sudo cp ./os/linux/rt5390sta.ko /lib/modules/2.6.35-25-generic/kernel/drivers/net/wireless/

8. Edit /etc/modules to add the line 'rt5390sta'

9. Reboot and find your network SSID. It may be possible that you need to restart the network manager with 'sudo restart network-manager'

Now I can connect to my wireless network. I have tried with WEP and WPA2.

I know this is for 32-bit but as I saw the same problems discussed here, this could also help in the 64-bit version.

The link for that download no longer works. I downloaded a slightly newer version (I think): [https://build.opensuse.org/package/binary?arch=x86_64&filename=rt5390sta-2.4.0.4-6.3.src.rpm&package=rt5390sta&project=driver%3Awireless&repository=11.3-update](https://build.opensuse.org/package/binary?arch=x86_64&filename=rt5390sta-2.4.0.4-6.3.src.rpm&package=rt5390sta&project=driver%3Awireless&repository=11.3-update)

However, I didn't see any patches when I was trying to follow your instructions. So I tried skipping that and just going straight to doing make. That didn't work either and I recieved the error that the command wasn't found.

Any help?

---

### Post by tatxo on 2011-04-08
I've installed the new version available at [OpenSuse]("https://build.opensuse.org/package/binaries?nextstatus=404&package=rt5390sta&project=driver%3Awireless&repository=11.3-update") with the patches without any problem. Just still having frequent disconnections, solved by disabling and enabling wireless from Network Manager.

Any suggestion on the disconnection field would be very appreciated.

---

### Post by en4ian on 2011-04-08
How did you install it? Did you have to patch it? I tried the instructions once and got to the point where my computer hardlocks whenever I try to connect. I then downloaded the other guy's patched files since I have no clue how that patching process works and put it into the needed directory and that didn't work either. 

I also tried using my USB wireless adapter but that frequently disconnects as well. It's a ralink2--- something. I'm beginning very much not to like ralink.

---

### Post by jivanyatra on 2011-04-08
Hey all,
I'm a lurker more than a poster, and I'd like to change that whenever I can. This time, though, I'm the one in need of help.

I'm an HP DM1z user (with the AMD Zacate APU). I've been fiddling with Natty (64-bit) from alpha on. I followed the instructions to compile and install the driver and this worked fine on kernel 2.6.35... I didn't get the dropped signal issues or anything.

I borked my install, and I reinstalled the beta (again, 64-bit), with kernel 2.6.38-7. I can compile correctly, without a problem. I manually copy all of the files to their appropriate places including the proper kernel directory. After a restart, it still doesn't seem to detect my card.

network-manager doesn't show any wireless networks.
ifconfig shows just my eth0 and lo.
It used to show up under the Restricted Drivers box when it worked on my previous install. If I look there now, I still don't see it.

Not sure what I'm doing wrong, or if I'm just unlucky. 
I've been incessantly searching the forums and launchpad for any solutions to this issue. I thought the proper 5390 drivers were supposed to be included in the mainline 2.6.38 kernel?

Any help is appreciated.

---

### Post by jivanyatra on 2011-04-08
> **jackharvest said:**
> The biggest piece missing on the DM1 is the touchpad. The damn thing doesn't support multitouch, so drag and drop with two fingers causes major mouse jumping. Not sure if anyone has a fix for it yet - hoping for a link once there's a fix, as I'm sure you are.

Have you looked at Touchegg?
[http://code.google.com/p/touchegg/wiki/ConfigureDevices](http://code.google.com/p/touchegg/wiki/ConfigureDevices)

Installation instructions here: [http://www.chromeoslounge.com/cr-48-chrome-notebook/1507-touchegg-finger-gestures-ubuntu.html](http://www.chromeoslounge.com/cr-48-chrome-notebook/1507-touchegg-finger-gestures-ubuntu.html)

In natty beta and in maverick, I have hscroll and vscroll working with 2 fingers, and 2-finger right-click by default (out of box).

---

### Post by jivanyatra on 2011-04-08
> **mrmagos said:**
> You will have to run 'make' and 'make install' again for the new kernel.

As an aside, has anyone had success with bluetooth with this card? Syslog shows that it goes into discovery mode, but it doesn't seem to be able to pick up any devices.

My phone and wiiremote both connected fine in Maverick. Haven't tried it in Natty Beta yet.

---

### Post by devguy on 2011-04-09
> **jivanyatra said:**
> Hey all,
I'm a lurker more than a poster, and I'd like to change that whenever I can. This time, though, I'm the one in need of help.

I'm an HP DM1z user (with the AMD Zacate APU). I've been fiddling with Natty (64-bit) from alpha on. I followed the instructions to compile and install the driver and this worked fine on kernel 2.6.35... I didn't get the dropped signal issues or anything.

I borked my install, and I reinstalled the beta (again, 64-bit), with kernel 2.6.38-7. I can compile correctly, without a problem. I manually copy all of the files to their appropriate places including the proper kernel directory. After a restart, it still doesn't seem to detect my card.

network-manager doesn't show any wireless networks.
ifconfig shows just my eth0 and lo.
It used to show up under the Restricted Drivers box when it worked on my previous install. If I look there now, I still don't see it.

Not sure what I'm doing wrong, or if I'm just unlucky. 
I've been incessantly searching the forums and launchpad for any solutions to this issue. I thought the proper 5390 drivers were supposed to be included in the mainline 2.6.38 kernel?

Any help is appreciated.

Same thing here; it worked fine in Maverick, doesn't work in Natty Beta 1.  Also interesting is that Bluetooth works out of the box in Natty, but trying to install these drivers kills it (it worked fine in Maverick).

There won't be RT5390 support in kernel 2.6.38, but it should make 2.6.39.  Unfortunately, while I really suggest Canonical backport these drivers, I doubt they will, as it's very late in the development cycle.

---

### Post by rvfh on 2011-04-12
I just wanted to confirm that it works fine in 64-bit Natty Beta too.

For those who are lost compiling this stuff, this is what I did:

```
rpm -i rt5390sta-2.4.0.4-6.3.src.rpm 
cd ~/rpmbuild/
tar xf SOURCES/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO.tar.bz2 
cd 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/
patch -p0 < ../SOURCES/rt5390sta-2.4.0.4-config.patch 
patch -p0 < ../SOURCES/rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
patch -p0 < ../SOURCES/rt5390sta-2.4.0.4-gcc-warnings-x86_64.patch 
patch -p0 < ../SOURCES/rt5390sta-2.4.0.4-reduce_debug_output.patch 
patch -p0 < ../SOURCES/rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
patch -p0 < ../SOURCES/rt5390sta-2.4.0.4-return_nonvoid_function.patch 
patch -p0 < ../SOURCES/rt5390sta-2.4.0.4-WPA-mixed.patch 
mv RT2860STA.dat RT5390STA.dat
sudo mkdir -p /etc/Wireless/RT5390STA
sudo cp RT5390STA.dat /etc/Wireless/RT5390STA
make
sudo cp os/linux/rt5390sta.ko /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
sudo depmod
sudo modprobe rt5390sta
```

Then just use your network icon to connect to your WiFi network. No reboot needed.

---

### Post by jivanyatra on 2011-04-12
rvfh: Thank you! It works!

Looking over your instructions, I couldn't find any changes from what I was doing before. Nevertheless, I followed your process using the updated 11.4 source available from:

[https://build.opensuse.org/package/binaries?package=rt5390sta&project=driver%3Awireless&repository=11.4-update]("https://build.opensuse.org/package/binaries?package=rt5390sta&project=driver%3Awireless&repository=11.4-update")

No idea where I went wrong earlier, but it definitely works.

---

### Post by jrierab on 2011-04-20
> **akshay.guleria@gmail.com said:**
> **Problem**: 


[LIST=1]
[*]Download the driver from ralinktech.com --> Software --> Linux
[*]Unzip the download zip file anywhere. I did it in the default Downloads directory
[*]cd to the 2010_xxx extracted directory
[*]cd os/linux/
[*]Edit the config.mk file as below:
HAS_ATE=y (no change, it was originally as is)
HAS_WPA_SUPPLICANT=y (no change, it was originally as is)
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y (no change, it was originally as is)
HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n -- this was the only thing I modified)
[*]Go back to the 2010_xx directory
[/LIST]


Thank you for your detailed instructions !!! You've saved my life :popcorn:

I have changed them slightly, however:

7. sudo make
8 sudo make install

Reboot, and voilà, surfing !!!

---

### Post by insanekat on 2011-04-27
Still have issues, no change in my wireless connection other than that r5390 shows up in my Additional Drivers area. Not sure where I went wrong as I'm not incredibly savvy with the terminal. Everything appeared fine as I was doing it, that's probably not the case though.

---

### Post by port86 on 2011-04-29
> **akshay.guleria@gmail.com said:**
> **Problem**: 
Got a brand new HP laptop - HP g62x. Installed ubuntu 10.10 and found that I do not have a wlan interface as one would expect with an active wireless connection.

**Thanks to** 
Great discussion on similar work here @ [http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498). Just a different card.

**Solution:**
I used the above thread to do my work - banged my head against the wall a couple of times but it was fun :). I am listing down steps that finally worked for me. But before that, my configurations:
[LIST]
[*]Ubuntu 10.10
[*]64 bit
[*]WPA2 wireless network
[*]OS was freshly installed and there was no specific customization prior to this
[*]RaLink Device 5390. (use lspci to see your model number)
[/LIST]


[LIST=1]
[*]Download the driver from ralinktech.com --> Software --> Linux
[*]Unzip the download zip file anywhere. I did it in the default Downloads directory
[*]cd to the 2010_xxx extracted directory
[*]cd os/linux/
[*]Edit the config.mk file as below:
HAS_ATE=y (no change, it was originally as is)
HAS_WPA_SUPPLICANT=y (no change, it was originally as is)
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y (no change, it was originally as is)
HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n -- this was the only thing I modified)
[*]Go back to the 2010_xx directory
[*]run command 'make'
[*]Make sure 'make compile' exists without errors. I got an error "too many arguments to format" towards the end of the compile but it did compile successfully eventually. And so I ignored the errors. You would see ***errors*** if the compile is not successful. In which, something went wrong and you may need to tweak the makefile or config.mk files before compile is successful.
[*]run command 'make install' as root. This is not listed in the README_STA_pci file that comes with downloaded driver zip file. This takes of copying the file to /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rt5390sta.ko. running depmod, creating /etc/Wireless/... folder.
[*]Edit the /etc/modules and add the line  at the end of this file
rt5390sta
[*]Edit the file /etc/modprobe.d/blacklist.conf and add the below line to it...
blacklist rt2800pci
[*]Reboot and you should see an ra0 interface when you run the command 'ifconfig'
[*]You may have to run '/etc/init.d/network-manager restart' command to have it show in the first go.
[*]Once, the wireless icon shows up, look for your wireless SSID and there you go surfing :)
[/LIST]


Hello, thanks for the info. 

I have been able to follow this guide up until number 7, the make command. Each time I run it, I receive the following error:

make[2]: *** [/home/donald/Downloads/wireless/os/linux/../../os/linux/cfg80211.o] Error 1
make[1]: *** [_module_/home/donald/Downloads/wireless/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [LINUX] Error 2

You mention that I should perhaps modify my config.mk or makefile - I am new to Linux, so perhaps you could shed some light on what I should look out for?

I am trying this on 11.04, could this be the cause of my problems?

Thanks.

---

### Post by chili555 on 2011-04-29
> You mention that I should perhaps modify my config.mk or makefile - I am new to Linux, so perhaps you could shed some light on what I should look out for?

I am trying this on 11.04, could this be the cause of my problems?

Thanks.Please see your other thread. You need to make the patches I referred you to.

---

### Post by port86 on 2011-04-29
I do apologise, I clicked the link on that thread rather than following it, my mistake. The info in the other thread solved the problem. You sir are a genius. Thank you!!!

---

### Post by palimmo on 2011-04-30
Hi guys!

I thought I solved the problem with this solution on my Ubuntu 11.04 but...
Sometimes  the connection goes down... in particular during skype videochat... and this is very annoying.

Do you have any idea?

Thank you very much!

> **adamis said:**
> The instructions listed in the link from earlier posts I found have typos. Below are some corrected instructions that hopefully should get you on your way... 

1. Download the file contained at this link: [http://barkmunchers.com/dm1z/RT.tar.gz](http://barkmunchers.com/dm1z/RT.tar.gz)

2. Extract the files to a directory. Then open a console, navigate to the directory that you extracted the files to then run the following commands:

[PHP]sudo make
sudo make install
sudo mkdir -p /etc/Wireless/RT5390STA
sudo cp RT5390STA.dat /etc/Wireless/RT5390STA/RT5390STA.dat
sudo cp ./os/linux/rt5390sta.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt5390sta.ko[/PHP]

Note that for the last command above I used the option <uname -r>. This will copy the files to the current running kernel version. Make sure you are running the kernel that you wish to get the wireless running on...

Now edit /etc/modules to add the line 'rt5390sta' at the end

Then run:

[PHP]sudo depmod -a
reboot[/PHP]

That should get you on your way. Hopefully that I didn't add in any typos myself.

**Edit** fixed the <uname -r> with `uname -r`, Thanks frospeh for catching the error!

---

### Post by howellb3383 on 2011-04-30
Hi, I have done all the directions given in this forum. I have updated from opensuse, gone step by step to both directions (main and the one after that says to include an update) and yet my computer still doesn't recognize my wireless card.  I have a Compaq Presario 56Q with a 64 bit intel celeron and install alongside Windows 7. Thank you for reading.

---

### Post by howellb3383 on 2011-05-01
Never mind, I did what post #77 said to do again, and everything is working like a charm. Not sure why it didn't work the first time....Anyway, I want thank all the people that make this forum so great. I too apologize for un-needed post. Hope I can learn enough to give back!

---

### Post by Brumbinhd on 2011-05-01
> **akshay.guleria@gmail.com said:**
> **Problem**: 
Got a brand new HP laptop - HP g62x. Installed ubuntu 10.10 and found that I do not have a wlan interface as one would expect with an active wireless connection.

**Thanks to** 
Great discussion on similar work here @ [http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498). Just a different card.

**Solution:**
I used the above thread to do my work - banged my head against the wall a couple of times but it was fun :). I am listing down steps that finally worked for me. But before that, my configurations:
[LIST]
[*]Ubuntu 10.10
[*]64 bit
[*]WPA2 wireless network
[*]OS was freshly installed and there was no specific customization prior to this
[*]RaLink Device 5390. (use lspci to see your model number)
[/LIST]


[LIST=1]
[*]Download the driver from ralinktech.com --> Software --> Linux
[*]Unzip the download zip file anywhere. I did it in the default Downloads directory
[*]cd to the 2010_xxx extracted directory
[*]cd os/linux/
[*]Edit the config.mk file as below:
HAS_ATE=y (no change, it was originally as is)
HAS_WPA_SUPPLICANT=y (no change, it was originally as is)
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y (no change, it was originally as is)
HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n -- this was the only thing I modified) 
[*]Go back to the 2010_xx directory
[*]run command 'make'
[*]Make sure 'make compile' exists without errors. I got an error "too many arguments to format" towards the end of the compile but it did compile successfully eventually. And so I ignored the errors. You would see ***errors*** if the compile is not successful. In which, something went wrong and you may need to tweak the makefile or config.mk files before compile is successful.
[*]run command 'make install' as root. This is not listed in the README_STA_pci file that comes with downloaded driver zip file. This takes of copying the file to /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rt5390sta.ko. running depmod, creating /etc/Wireless/... folder.
[*]Edit the /etc/modules and add the line  at the end of this file
rt5390sta
[*]Edit the file /etc/modprobe.d/blacklist.conf and add the below line to it...
blacklist rt2800pci
[*]Reboot and you should see an ra0 interface when you run the command 'ifconfig'
[*]You may have to run '/etc/init.d/network-manager restart' command to have it show in the first go.
[*]Once, the wireless icon shows up, look for your wireless SSID and there you go surfing :)
[/LIST]
  

Any idea what can be done different? I got an error 2 message while trying to compile. I'm really new at this and any lamens type explanation or idea would help.. I've been working through the forums like crazy trying to get this working and you have the exact same setup I do. Thanks in advance.

---

### Post by howellb3383 on 2011-05-02
I had the same problem Brumbinhd. All you have to do is go to post #77, install from the link, then extract it in your Downloads folder. (Any folder will do, but, we will say Downloads to make it easier.) Open your terminal, then type in ->cd Downloads. This should bring you to the Downloads folder within the terminal. Then type -> cd RT. Now you are in the downloaded content folder that you just extracted to this destination. Once there, follow the steps in post #77. (I will copy and paste it down below this) Tell me if it worked for you also. 

                     Originally Posted by **adamis**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10661914#post10661914")                 
                 [I]The instructions listed in the link  from earlier posts I found have typos. Below are some corrected  instructions that hopefully should get you on your way... 

1. Download the file contained at this link: [http://barkmunchers.com/dm1z/RT.tar.gz](http://barkmunchers.com/dm1z/RT.tar.gz)

2. Extract the files to a directory. Then open a console, navigate to  the directory that you extracted the files to then run the following  commands:

     PHP Code:
     [LEFT]                      [COLOR=#000000] [COLOR=#0000BB]sudo make 
sudo make install 
sudo mkdir [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]p [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]etc[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]Wireless[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]RT5390STA 
sudo cp RT5390STA[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]dat [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]etc[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]Wireless[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]RT5390STA[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]RT5390STA[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]dat 
sudo cp [/COLOR][COLOR=#007700]./[/COLOR][COLOR=#0000BB]os[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]linux[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]rt5390sta[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]ko [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]lib[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]modules[/COLOR][COLOR=#007700]/`[/COLOR][COLOR=#0000BB]uname -r[/COLOR][COLOR=#007700]`/[/COLOR][COLOR=#0000BB]kernel[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]drivers[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]net[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]wireless[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]rt5390sta[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]ko  
[/COLOR] [/COLOR]               [/LEFT]
 
Note that for the last command above I used the option <uname  -r>. This will copy the files to the current running kernel version.  Make sure you are running the kernel that you wish to get the wireless  running on...

Now edit /etc/modules to add the line 'rt5390sta' at the end

Then run:

     PHP Code:
     [LEFT]                      [COLOR=#000000] [COLOR=#0000BB]sudo depmod [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]a 
reboot  
[/COLOR] [/COLOR]               [/LEFT]
 
That should get you on your way. Hopefully that I didn't add in any typos myself.

**Edit** fixed the <uname -r> with `uname -r`, Thanks frospeh for catching the error![/I]

---

### Post by nefan on 2011-05-02
Does anybody have working bluetooth with ralink 5390? The btusb driver loads on my HP dm1, I get no errors when scanning for new devices, but, as mentioned previously in the thread, no devices show up..

Stefan

---

### Post by theprintingplace on 2011-05-02
I have achieved some headway, thankfully. After following the steps in this link, I am seeing wlan0 after iwconfig but I sill do not have wireless networks listed when  I click on the icon. Any ideas. I also see the Ralink 5390 listed in the additional drivers dialog.

Thanks for everyone's help.

---

### Post by Brumbinhd on 2011-05-02
hi howellb3383, i did just as you said and i got this back with the make install command:
~/Downloads/RT$ sudo make install
make -C /home/brumbinhd/Downloads/RT/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/brumbinhd/Downloads/RT/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/brumbinhd/Downloads/RT/RT2860STA.dat /etc/Wireless/RT2860STA/.
cp: cannot stat `/home/brumbinhd/Downloads/RT/RT2860STA.dat': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/brumbinhd/Downloads/RT/os/linux'
make: *** [install] Error 2

now what i think is somehow i need to erase the folder /etc/Wireless and start over... is that right? and if so how do i change the permissions? it seems like a silly question but when i go into properties it tells me that im not the owner so i can't change them. also if i try to run the reboot command, it tells me that "needs to be root". thanks for your help im farther than ive been!

---

### Post by howellb3383 on 2011-05-03
I know this sounds silly, but did you type "sudo" before each command? I was looking over what was in your terminal, and it appears you haven't. Ignore the errors for now, because you are directly putting them in the Wireless folder. So, there is no need to delete it. Also, you will need to go to your modules and edit them. (it is a text file) so to get there type in -> cd /etc/ then type -> sudo gedit modules. At the end of everything, below the last line, type -> rt5390sta 

So a quick summery:
-Type -> sudo  Before every command in the previous post that I cut and pasted. (ps you can cut and paste everything. Just do not put the periods at the end of each line in the terminal.)
- Make sure to a add rt5390sta to the end of your "modules" document list.
-Once you have typed in the previous step make sure to save it!
- Then finally hit restart.

On a final note, if you want to make a new root password, so that you can access root in the terminal, do this:

Type -> sudo passwd
Type your current password
Type the new root password
Retype the new root password

You will see you are then in root. To go back to just being a normal terminal user, type -> exit.

After doing all of this, please then type -> ifconfig and tell us what you get. (if you do not automatically get wifi.) Oh! Before I forget, make sure your wifi is on after doing all of this.

---

### Post by Brumbinhd on 2011-05-03
DUDE! so i had just ignored the errors and followed through with the rest of that post from you, and then i posted my reply.. in a spat of frustration i shut down my computer and left the house for a bit.. i came back and booted back up and.. PRESTO! connection established! Thank you for your help! I really appreciate it!

---

### Post by howellb3383 on 2011-05-03
Glad to hear. Did you see where I responded to changing your password?

---

### Post by palimmo on 2011-05-03
Hi!

Is your connection steady (for example during a Videochat session on Skype)? :(

---

### Post by theprintingplace on 2011-05-03
Did any of you add anything to the rfkill list? Mine is showing up in iwconfig but I still show no wireless networks listed and can't connect to any.

---

### Post by Brumbinhd on 2011-05-03
yes I did. i was able to change that password and get into root. it was a little slow at first (wifi) and web pages in chrome would take forever to load. after work today however everything seemed to be working as if the computer came out of the box with ubuntu. i havent yet used a video chat service yet but the way everything else is running i would imagine it would be stable. thanks again for the help, i learned a lot about how linux runs/works from those posts!

Oh and I am on 11.04, so those steps from post 81 definitely works for that version

---

### Post by Samzystrange on 2011-05-06
> **akshay.guleria@gmail.com said:**
> **Problem**: 
Got a brand new HP laptop - HP g62x. Installed ubuntu 10.10 and found that I do not have a wlan interface as one would expect with an active wireless connection.

**Thanks to** 
Great discussion on similar work here @ [http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498). Just a different card.

**Solution:**
I used the above thread to do my work - banged my head against the wall a couple of times but it was fun :). I am listing down steps that finally worked for me. But before that, my configurations:
[LIST]
[*]Ubuntu 10.10
[*]64 bit
[*]WPA2 wireless network
[*]OS was freshly installed and there was no specific customization prior to this
[*]RaLink Device 5390. (use lspci to see your model number)
[/LIST]


[LIST=1]
[*]Download the driver from ralinktech.com --> Software --> Linux
[*]Unzip the download zip file anywhere. I did it in the default Downloads directory
[*]cd to the 2010_xxx extracted directory
[*]cd os/linux/
[*]Edit the config.mk file as below:
HAS_ATE=y (no change, it was originally as is)
HAS_WPA_SUPPLICANT=y (no change, it was originally as is)
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y (no change, it was originally as is)
HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n -- this was the only thing I modified)
[*]Go back to the 2010_xx directory
[*]run command 'make'
[*]Make sure 'make compile' exists without errors. I got an error "too many arguments to format" towards the end of the compile but it did compile successfully eventually. And so I ignored the errors. You would see ***errors*** if the compile is not successful. In which, something went wrong and you may need to tweak the makefile or config.mk files before compile is successful.
[*]run command 'make install' as root. This is not listed in the README_STA_pci file that comes with downloaded driver zip file. This takes of copying the file to /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rt5390sta.ko. running depmod, creating /etc/Wireless/... folder.
[*]Edit the /etc/modules and add the line  at the end of this file
rt5390sta
[*]Edit the file /etc/modprobe.d/blacklist.conf and add the below line to it...
blacklist rt2800pci
[*]Reboot and you should see an ra0 interface when you run the command 'ifconfig'
[*]You may have to run '/etc/init.d/network-manager restart' command to have it show in the first go.
[*]Once, the wireless icon shows up, look for your wireless SSID and there you go surfing :)
[/LIST]


Hi, thanks for the thread! Sorry to reopen it after so many months, but I'm having the same issue, and when I ran the make command, I got *** errors ***.
I'm running 11.04 on a compaq presario CQ56, I have the Ralink 5390 card. I don't really know how to tweak the Makefile or config.mk file to get it to complete successfully. 


Here is the error message I got:

/home/samz/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:2594:2: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217;
make[2]: *** [/home/samz/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.o] Error 1
make[1]: *** [_module_/home/samz/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [LINUX] Error 2



For whatever it's worth, this is the relevant output of lspci -v:

02:00.0 Network controller: Ralink corp. Device 5390
    Subsystem: Hewlett-Packard Company Device 1636
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at 93500000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>


Any help on this would really be appreciated!

---

### Post by dr.s on 2011-05-07
> **Samzystrange said:**
> Hi, thanks for the thread! Sorry to reopen it after so many months, but I'm having the same issue, and when I ran the make command, I got *** errors ***.
I'm running 11.04 on a compaq presario CQ56, I have the Ralink 5390 card. I don't really know how to tweak the Makefile or config.mk file to get it to complete successfully. 


Here is the error message I got:

/home/samz/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:2594:2: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
make[2]: *** [/home/samz/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.o] Error 1
make[1]: *** [_module_/home/samz/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [LINUX] Error 2



For whatever it's worth, this is the relevant output of lspci -v:

02:00.0 Network controller: Ralink corp. Device 5390
    Subsystem: Hewlett-Packard Company Device 1636
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at 93500000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>


Any help on this would really be appreciated!

Had a similar error on an HP laptop with Ralink 5390, try this:
-edit config.mk (should be under ..../os/linux
-look for this line:
 HAS_CFG80211_SUPPORT=y
-change "y" to "n" then recompile and run make install.

---

### Post by Mac Jingles on 2011-05-09
> **Samzystrange said:**
> Hi, thanks for the thread! Sorry to reopen it after so many months, but I'm having the same issue, and when I ran the make command, I got *** errors ***.
I'm running 11.04 on a compaq presario CQ56, I have the Ralink 5390 card. I don't really know how to tweak the Makefile or config.mk file to get it to complete successfully. 


Here is the error message I got:

/home/samz/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:2594:2: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
make[2]: *** [/home/samz/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.o] Error 1
make[1]: *** [_module_/home/samz/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [LINUX] Error 2


I was getting a similar error when trying to compile using Ubuntu 11.04.

My Computer: HP Compaq Presario CQ56

However, I decided to burn the 10.04 LTS, and I installed that on the laptop, and then the instructions posted in this thread worked perfectly! However, I upgraded to 10.10 and some of the finicky connection problems that others have described are happening to me now.

---

### Post by guest5 on 2011-05-15
I need to reopen this as well, please please.

I have a hp dm-1, ralink 5390.

Followed all instructions. Get the following error on 'sudo make install':

studio4@TinyUbuntu:~/RT$ sudo make install
make -C /home/studio4/RT/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/studio4/RT/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/studio4/RT/RT2860STA.dat /etc/Wireless/RT2860STA/.
cp: cannot stat `/home/studio4/RT/RT2860STA.dat': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/studio4/RT/os/linux'
make: *** [install] Error 2
studio4@TinyUbuntu:~/RT$ 


I continued, including edit /etc/modules to add the line 'rt5390sta' at the end.

I see the wireless now, and I can see my router, but cannot connect to it, although it keeps trying it just never connects.

---

### Post by chili555 on 2011-05-15
This is the kwik 'n durty solution:```
sudo gedit /home/studio4/RT/RT2860STA.dat
```Add one line:```
Default
```Proofread, save and close gedit. Next do:```
make clean
make
```Continue the instructions as before.

---

### Post by guest5 on 2011-05-15
That was a fast response.  Thank you for it.  It got rid of the error but I still cannot connect. I am in an endless loop of trying to connect.

One thing, I errorred on the reboot command so I manually rebooted.  Don't know if that is pertinent but thought I'd better mention it.

Thanks again for all the help.

---

### Post by acghi on 2011-05-16
Hello,

While trying the solution given (on Ubuntu 10.10 32 bits), in step 7 ("make"), I get the following error message:

...
cp -f /home/agonzalez/drivers/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/rt5390sta.ko /tftpboot
cp: could not create regular file «/tftpboot»: Permission denied

I'm surprised that the Makefile apparently is trying to write a file in / directory. Why? How could I complete this step?

---

### Post by chili555 on 2011-05-16
> I'm surprised that the Makefile apparently is trying to write a file in / directory. Why? How could I complete this step?Run as super-user:```
sudo su
make clean
make 
make install
modprobe rt5390sta
exit
```

---

### Post by chili555 on 2011-05-16
> **guest5 said:**
> That was a fast response.  Thank you for it.  It got rid of the error but I still cannot connect. I am in an endless loop of trying to connect.

One thing, I errorred on the reboot command so I manually rebooted.  Don't know if that is pertinent but thought I'd better mention it.

Thanks again for all the help.Any interesting messages here?```
dmesg | grep -e 539 -e wlan -e ra0
```

---

### Post by guest5 on 2011-05-16
> Any interesting messages here?
Code:

dmesg | grep -e 539 -e wlan -e ra0



studio4@TinyUbuntu:~$ dmesg | grep -e 539 -e wlan -e ra0 
[    0.000000] Memory: 2666900k/2735104k available (5189k kernel code, 62924k reserved, 2539k data, 700k init, 1820972k highmem)
[    0.000000]       .data : 0xc15116e1 - 0xc178c4c0   (2539 kB)
[    0.004539] mce: CPU supports 6 MCE banks
[    0.332227] pci 0000:02:00.0: [1814:539f] type 0 class 0x000280
[    0.539772] ACPI: Lid Switch [LID]
[    0.539910] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.539919] ACPI: Power Button [PWRF]
[    1.236539] hub 5-0:1.0: USB hub found
[    1.583539] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 1 ports 6 Gbps 0x1 impl SATA mode
[   16.958851] rt5390 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.958927] rt5390 0000:02:00.0: setting latency timer to 64
[   28.496214] wlan0: no IPv6 routers present
studio4@TinyUbuntu:~$

Please note: This pc is running 11.04, 32 bit (I think)

---

### Post by chili555 on 2011-05-16
Nothing helpful there. How about:```
sudo cat /var/log/syslog | grep -i network | tail -n20
```If this is sparse, try:```
sudo cat /var/log/syslog.1 | grep -i network | tail -n20
```I hope we can see why it fails to connect.

Is your router set to WPA or WPA2 or the tricky and difficult mixed wpa *AND *wpa2 mode?

---

### Post by guest5 on 2011-05-16
We are using wpa personal

studio4@TinyUbuntu:~$ sudo cat /var/log/syslog | grep -i network | tail -n20
[sudo] password for studio4: 
May 16 08:50:47 TinyUbuntu NetworkManager[579]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
May 16 08:50:50 TinyUbuntu NetworkManager[579]: <info> (wlan0): supplicant connection state:  4-way handshake -> disconnected
May 16 08:50:50 TinyUbuntu NetworkManager[579]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
May 16 08:50:52 TinyUbuntu NetworkManager[579]: <info> (wlan0): supplicant connection state:  scanning -> associating
May 16 08:50:52 TinyUbuntu NetworkManager[579]: <info> (wlan0): supplicant connection state:  associating -> associated
May 16 08:50:52 TinyUbuntu NetworkManager[579]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
May 16 08:50:55 TinyUbuntu NetworkManager[579]: <info> (wlan0): supplicant connection state:  4-way handshake -> disconnected
May 16 08:50:55 TinyUbuntu NetworkManager[579]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
May 16 08:50:57 TinyUbuntu NetworkManager[579]: <info> (wlan0): supplicant connection state:  scanning -> associating
May 16 08:50:57 TinyUbuntu NetworkManager[579]: <info> (wlan0): supplicant connection state:  associating -> associated
May 16 08:50:57 TinyUbuntu NetworkManager[579]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
May 16 08:50:58 TinyUbuntu NetworkManager[579]: <warn> Activation (wlan0/wireless): association took too long.
May 16 08:50:58 TinyUbuntu NetworkManager[579]: <info> (wlan0): device state change: 5 -> 9 (reason 7)
May 16 08:50:58 TinyUbuntu NetworkManager[579]: <warn> Activation (wlan0) failed for access point (U.S.Gov HackerTrap)
May 16 08:50:58 TinyUbuntu NetworkManager[579]: <info> Marking connection 'Auto U.S.Gov HackerTrap' invalid.
May 16 08:50:58 TinyUbuntu NetworkManager[579]: <warn> Activation (wlan0) failed.
May 16 08:50:58 TinyUbuntu NetworkManager[579]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
May 16 08:50:58 TinyUbuntu NetworkManager[579]: <info> (wlan0): deactivating device (reason: 0).
May 16 08:50:58 TinyUbuntu NetworkManager[579]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
May 16 08:50:58 TinyUbuntu NetworkManager[579]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
studio4@TinyUbuntu:~$


should I be actively trying to connect when running any of these commands, or merely have the wireless switched to 'on'?

---

### Post by chili555 on 2011-05-16
Can you confirm you made the changes to config.mk as outlined in the README?> 3> In os/linux/config.mk 
        ......
        modify to meet your need.
        ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
           Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.May I see:```
ls /home/studio4/RT/
```Thanks.

---

### Post by guest5 on 2011-05-16
Yes, I can confirm:
# Support Wpa_Supplicant

HAS_WPA_SUPPLICANT=y


Dir List:

studio4@TinyUbuntu:~$ ls /home/studio4/RT/
1.patch  4.patch  7.patch  include           os                 RT2860STA.dat  sta_ate_iwpriv_usage.txt
2.patch  5.patch  chips    iwpriv_usage.txt  README_STA_pci     RT5390STA.dat  tools
3.patch  6.patch  common   Makefile          RT2860STACard.dat  sta
studio4@TinyUbuntu:~$ 


Thank you so very much for putting your mind on this problem!

---

### Post by guest5 on 2011-05-16
Forgot to confirm the other request, here it is:

# Support Native WpaSupplicant for Network Maganger

HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

---

### Post by chili555 on 2011-05-16
Let's try something:```
sudo rmmod -f rt5390sta
sudo cp studio4/RT/RT5390STA.dat /etc/Wireless/RT2860STA/RT2860STA.dat
sudo modprbe rt5390sta
```Is yours a 64-bit system? Did you do all the patches, including the 64-bit patch?

Any improvement in your ability to connect?

---

### Post by guest5 on 2011-05-16
I believe this to be the 32 bit version - Linux i686

Got some odd responses to the input requests:

studio4@TinyUbuntu:~$ sudo rmmod -f rt5390sta
[sudo] password for studio4: 
ERROR: Removing 'rt5390sta': Resource temporarily unavailable


studio4@TinyUbuntu:~$ sudo cp studio4/RT/RT5390STA.dat /etc/Wireless/RT2860STA/RT2860STA.dat
cp: cannot stat `studio4/RT/RT5390STA.dat': No such file or directory

studio4@TinyUbuntu:~$ sudo modprbe rt5390sta
sudo: modprbe: command not found

The connection attempt is still always in process, then times out after a few minutes.

---

### Post by chili555 on 2011-05-16
Let's correct a couple of things and hit it again!```
sudo ifconfig wlan0 down
sudo rmmod -f rt5390sta
sudo cp /home/studio4/RT/RT5390STA.dat /etc/Wireless/RT2860STA/RT2860STA.dat
sudo modpr[COLOR="Red"]o[/COLOR]be rt5390sta
sudo ifconfig wlan0 up
```

---

### Post by guest5 on 2011-05-16
Not yet.  I rebooted as well.

---

### Post by guest5 on 2011-05-17
Please laugh, Anyways, I changed my password and was using the old one.  I would expect it to tell me the password is rejected, whatever, it's working fine.  

Thank You.  I got to learn allot more about Ubuntu. Thank YOU.

---

### Post by chili555 on 2011-05-17
Glad it's working by whatever means. I admit you had me worried for a while!

---

### Post by guest5 on 2011-05-17
I had to confess it you know. I couldn't leave you hanging. I don't make many errors, but every once in a while...  Oh well.

---

### Post by thegrooviest1 on 2011-06-08
> **akshay.guleria@gmail.com said:**
> **Problem**: 
Got a brand new HP laptop - HP g62x. Installed ubuntu 10.10 and found that I do not have a wlan interface as one would expect with an active wireless connection.

**Thanks to** 
Great discussion on similar work here @ [http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498). Just a different card.

**Solution:**
I used the above thread to do my work - banged my head against the wall a couple of times but it was fun :). I am listing down steps that finally worked for me. But before that, my configurations:
[LIST]
[*]Ubuntu 10.10
[*]64 bit
[*]WPA2 wireless network
[*]OS was freshly installed and there was no specific customization prior to this
[*]RaLink Device 5390. (use lspci to see your model number)
[/LIST]


[LIST=1]
[*]Download the driver from ralinktech.com --> Software --> Linux
[*]Unzip the download zip file anywhere. I did it in the default Downloads directory
[*]cd to the 2010_xxx extracted directory
[*]cd os/linux/
[*]Edit the config.mk file as below:
HAS_ATE=y (no change, it was originally as is)
HAS_WPA_SUPPLICANT=y (no change, it was originally as is)
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y (no change, it was originally as is)
HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n -- this was the only thing I modified) 
[*]Go back to the 2010_xx directory
[*]run command 'make'
[*]Make sure 'make compile' exists without errors. I got an error "too many arguments to format" towards the end of the compile but it did compile successfully eventually. And so I ignored the errors. You would see ***errors*** if the compile is not successful. In which, something went wrong and you may need to tweak the makefile or config.mk files before compile is successful.
[*]run command 'make install' as root. This is not listed in the README_STA_pci file that comes with downloaded driver zip file. This takes of copying the file to /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rt5390sta.ko. running depmod, creating /etc/Wireless/... folder.
[*]Edit the /etc/modules and add the line  at the end of this file
rt5390sta
[*]Edit the file /etc/modprobe.d/blacklist.conf and add the below line to it...
blacklist rt2800pci
[*]Reboot and you should see an ra0 interface when you run the command 'ifconfig'
[*]You may have to run '/etc/init.d/network-manager restart' command to have it show in the first go.
[*]Once, the wireless icon shows up, look for your wireless SSID and there you go surfing :)
[/LIST]
I am totally new I just installed ubuntu 11.04 today, I studied this issue before I installed. I've downloaded the driver, unzipped it into a folder and I just don"t know how to install it from there. Like I said I'm brand new to this and I really want to learn. I am a little overwehlmed with what to do with Linux. I like it and this really might sound like a very stupid question but I am lost. Everthing else works but my wireless card. I have a HP g62x with windows 7. I would appreciate any help with pointing me in the right direction of maybe a website that could explain in detail how to install drivers and software. I'm sorry if this is the wrong place to ask this question. 

[LIST]
[*]Ubuntu 11.04
[*]64 bit
[*]WPA2 wireless network
[*]RaLink  5390
[/LIST]

---

### Post by chili555 on 2011-06-09
> **thegrooviest1 said:**
> I am totally new I just installed ubuntu 11.04 today, I studied this issue before I installed. I've downloaded the driver, unzipped it into a folder and I just don"t know how to install it from there. Like I said I'm brand new to this and I really want to learn. I am a little overwehlmed with what to do with Linux. I like it and this really might sound like a very stupid question but I am lost. Everthing else works but my wireless card. I have a HP g62x with windows 7. I would appreciate any help with pointing me in the right direction of maybe a website that could explain in detail how to install drivers and software. I'm sorry if this is the wrong place to ask this question. 

[LIST]
[*]Ubuntu 11.04
[*]64 bit
[*]WPA2 wireless network
[*]RaLink  5390
[/LIST]

Ubuntu 11.04 and 64-bit are a whole other issue. It's a slight bit more complicated than above but not, as my drinking buddy says, rocket surgery. Please start your own new thread and I'll be right there to help. If I don't catch it right away, send me a private message by clicking my user-name. In your new thread, tell us how far you've gotten with the process.

---

### Post by chareen on 2011-06-28
Hi,

I have just got a G62 456TU and am facing this problem. I have tried your suggestions right up to step 12. how do I run step 13?

Thanks
chareen

> **akshay.guleria@gmail.com said:**
> **Problem**: 
Got a brand new HP laptop - HP g62x. Installed ubuntu 10.10 and found that I do not have a wlan interface as one would expect with an active wireless connection.

**Thanks to** 
Great discussion on similar work here @ [http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498). Just a different card.

**Solution:**
I used the above thread to do my work - banged my head against the wall a couple of times but it was fun :). I am listing down steps that finally worked for me. But before that, my configurations:
[LIST]
[*]Ubuntu 10.10
[*]64 bit
[*]WPA2 wireless network
[*]OS was freshly installed and there was no specific customization prior to this
[*]RaLink Device 5390. (use lspci to see your model number)
[/LIST]


[LIST=1]
[*]Download the driver from ralinktech.com --> Software --> Linux
[*]Unzip the download zip file anywhere. I did it in the default Downloads directory
[*]cd to the 2010_xxx extracted directory
[*]cd os/linux/
[*]Edit the config.mk file as below:
HAS_ATE=y (no change, it was originally as is)
HAS_WPA_SUPPLICANT=y (no change, it was originally as is)
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y (no change, it was originally as is)
HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n -- this was the only thing I modified)
[*]Go back to the 2010_xx directory
[*]run command 'make'
[*]Make sure 'make compile' exists without errors. I got an error "too many arguments to format" towards the end of the compile but it did compile successfully eventually. And so I ignored the errors. You would see ***errors*** if the compile is not successful. In which, something went wrong and you may need to tweak the makefile or config.mk files before compile is successful.
[*]run command 'make install' as root. This is not listed in the README_STA_pci file that comes with downloaded driver zip file. This takes of copying the file to /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rt5390sta.ko. running depmod, creating /etc/Wireless/... folder.
[*]Edit the /etc/modules and add the line  at the end of this file
rt5390sta
[*]Edit the file /etc/modprobe.d/blacklist.conf and add the below line to it...
blacklist rt2800pci
[*]Reboot and you should see an ra0 interface when you run the command 'ifconfig'
[*]You may have to run '/etc/init.d/network-manager restart' command to have it show in the first go.
[*]Once, the wireless icon shows up, look for your wireless SSID and there you go surfing :)
[/LIST]


---

### Post by frederickSweet on 2011-07-28
I am having some problems getting the wifi to turn on it is being hard blocked and I have no idea how to enable it.  I am trying to get this done so I can get this laptop out of my house.  running fresh install of 10.10 I have the Compaq Presario CQ56 with the celeron processor

---

### Post by chili555 on 2011-07-28
> **frederickSweet said:**
> I am having some problems getting the wifi to turn on it is being hard blocked and I have no idea how to enable it.  I am trying to get this done so I can get this laptop out of my house.  running fresh install of 10.10 I have the Compaq Presario CQ56 with the celeron processorI think that's a different issue than how to compile the driver. Please start a new thread and post:> rfkill list all
lsmod | grep wmiThen leave a link here to the new thread and I'll be there.

---

### Post by thmsmorrow on 2011-08-08
Thanks to everyone who updated these instruction so quickly! Brand new dm1 up thanks to you.

---

### Post by n9jfg on 2011-08-18
Can someone tell where I can find the RA5390 driver? Seems to be a well hidden secret. Needed for a hp pavillion dv7-6157cl

Thanks

n9jfg

---

### Post by chili555 on 2011-08-18
> **n9jfg said:**
> Can someone tell where I can find the RA5390 driver? Seems to be a well hidden secret. Needed for a hp pavillion dv7-6157cl

Thanks

n9jfgHere ya go! It's now called RT539xPCIe.

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

---

### Post by n9jfg on 2011-08-20
> **chili555 said:**
> Here ya go! It's now called RT539xPCIe.

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
Thanks Chili555 it is working as we speak rather write. I installed it using the process listed by Grooviest and also Chareen.

Great thanks to all  !!!!

---

### Post by beelzebufo on 2011-08-25
wow, thank you man, great tutorial works perfect :)

---

### Post by eerjay on 2011-09-27
what does it mean when stated on step 3 cd to 2010_directory....

---

### Post by XxionxX on 2011-10-05
I don't know what I am doing wrong, none of these links to the desired binary seem to be working. This one 
[http://barkmunchers.com/dm1z/RT.tar.gz](http://barkmunchers.com/dm1z/RT.tar.gz) gives me this error message: "/tmp/PRcwAI+I.part could not be saved, because the source file could not be read.Try again later, or contact the server administrator" And when I visit this address: [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)  and visit the link for the RT539x PCIe to try and download the binary I get is this error message "/tmp/3RNzuVL8.bin.part could not be saved, because the source file could not be read.Try again later, or contact the server administrator."

What am I missing here? I don't really want to try and get this driver from a third party website or somewhere I don't trust :/ I am totally willing to go through all of the aforementioned steps, but I can't seem to get the binary :(

Am I just having some bad luck with links breaking?

Edit: @:eerjay    cd is a command that stands for Current Directory. So lets say you are in a terminal window and the prompt looks like this 

```
 yourusername@ubuntu:~$ 
```If you enter:

```
 yourusername@ubuntu:~$ cd /home 
```You will get: [email]akshay.guleria@gmail.com[/email]

```
 yourusername@ubuntu:/home$ 
```Which means you are in that particular folder when you are executing commands. I hope that at least gives you the general idea! :)

Edit2: Never mind, after an update and a reboot the links work fine -_- * turns into Loony Toons donkey/@** *

Edit3: Totally worked for me when I followed [email]akshay.guleria@gmail.com[/email]'s instructions. Although I did encounter that in the newest version of the driver that the makefile was different. This is what I found for step 5:Edit the config.mk file as below:
HAS_ATE=y (Changed it as per the instructions was originaly n)
HAS_WPA_SUPPLICANT=y (Changed it as per the instructions was originaly n)
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y (Changed it as per the instructions was originaly n)
[STRIKE]]HAS_ANTENNA_DIVERSITY_SUPPORT=y[/STRIKE] (This line was nowhere to be found, but I did not encounter any problems with the make install when i just left it alone besides the above changes)

Also, I am using Wicd as my network manager and by pure luck I figured out what to do after the reboot.
Open the Wicd network manager and click on the preferances button. On the general settings tab there is a field for 'Wireless Interface:' In that field put ra0 and hit ok. If it does not work, try rebooting, but it worked great for me!

Thanks for all your help guys!

---

### Post by elpanaqute on 2011-10-20
I got a CQ1 Compaq All in one computer with the mentioned wireless network card 5390 and after about 15 minutes searching i found this threat and then i did all the steps in the tutorial and WORK PERFECT!! THANK YOU man i love this forum!

PD: sorry bad english, but just want to confirm to everyone that really works.

---

### Post by chareen on 2011-11-10
Hi,

Have been following this thread for a while now. The problem I am facing is the connection drops very frequently.

Each time that happens I have to disable the wi-fi, then enable it again. After that it connects.

Anyone know how to overcome this. It's really annoying me that the connection drops all the time.

cheers

---

### Post by chareen on 2011-11-10
oowh forgot to mention, the wifi does not work after i perform the system updates. had to reinstall the driver. 

this too is annoying and it's great if there's a way to overcome it.

cheers

---

### Post by rukiaEnix on 2011-11-11
hello, I just did all the steps but I'm still having an error during compilation:

missing arguments for function ieee80211_channel_to_frequency

at file cfg80211.c

What could be wrong?

I'm trying to install the vendor driver from ralink because right now the laptop can connect just to some wireless access points we have at work, but it can't to others.
So I thought maybe trying the drivers at ralink website might work but I'm having this problem.
The laptop has Ubuntu 11.10

---

