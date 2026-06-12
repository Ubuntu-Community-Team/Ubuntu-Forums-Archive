---
title: "No sound after installing Ubuntu 7.04"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by tanveer on 2007-05-08
Hi all:

I just installed new ubuntu7.04 and its great,amazing and most of all the apt-get is mind blowing.
Now the only problem lies for me is I can't hear any sound. Now please tell me what to do to deal with this problem?

---

### Post by mkuutti on 2007-05-08
What is your sound chipset? Run command 'lspci' in terminal and provide output here, maybe we can help you. lspci  belongs to pciutils packate, so you may need to 'apt-get install pciutils'.

---

### Post by tanveer on 2007-05-08
oops. sorry. Let me check this link first which I should have done before posting here.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

if still problem persists I will come back for your help.

---

### Post by tanveer on 2007-05-08
Hi, I couldn't make the sound work. 

this is the Output of lspci.

```

tanveer@Spearhead:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:01.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:03.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
02:04.0 Ethernet controller: MYSON Technology Inc SURECOM EP-320X-S 100/10M Ethernet PCI Adapter

```

Thanks.

---

### Post by lebe0024 on 2007-05-08
I think you have the same problem I had - the linux soundblaster drivers enable digital output by default!  It's easy to switch to analog.  I'm not sure why they enable digital output by default.

[http://ubuntuforums.org/showthread.php?t=434911]("http://ubuntuforums.org/showthread.php?t=434911")

---

### Post by tanveer on 2007-05-08
I go through that link and God thats the same setup as you wrote in your problem. Specially,
 >  the progress bar only gets two bar segments and it stops :)  

I  will give it a try after getting  back home and let u know what happened. 

thank you.

---

### Post by tanveer on 2007-05-09
sorry. It didn't worked for me. 
FYI, when I first installed ubuntu then it played sound at login and logout time. But when I tried to play mp3 through xmms then I didn't hear any sound and then I did some editing on sound preference. may be thats causing the trouble. 
Any idea or do I have to reinstall ubuntu again:(

---

### Post by tanveer on 2007-05-20
Hi,

Now the problem is sometimes I get the sound but sometimes I don't. What is causing that?

---

