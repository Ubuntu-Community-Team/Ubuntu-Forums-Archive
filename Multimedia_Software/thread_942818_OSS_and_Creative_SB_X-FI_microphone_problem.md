---
title: "OSS and Creative SB X-FI microphone problem"
date: 2008-10-09
forum: Multimedia Software
---

### Post by teust on 2008-10-09
Hi,

I have creative sound blaster X-FI, after a lot of work I have sound, this meant installing OSS.  However my mic is not working, when testing with skype it was getting input but it is garbled and very quiet.  Tried it on windows and it was fine.  I can't see any settings to help with this, the mixer is up full.  Anyone any help with this, below are the results from ossmix and ossinfo.

Any help greatly appreciated.

[HTML]
Selected mixer 0/Sound Blaster X-Fi
Known controls are:
play <both/leftvol>[:<rightvol>] (currently 14.4:14.4 dB)
rec <both/leftvol>[:<rightvol>] (currently 14.4:14.4 dB)
recsrc <mic|line|video|aux|none> (currently mic)
vmix0-src <Fast|Low|Medium|High|High+|Production|OFF> (currently Fast)
vmix0-vol <monovol> (currently 25.0 dB)
vmix0-out1 <leftVU>:<rightVU>] (currently 0:0)
vmix0-out.pcm2 <both/leftvol>[:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out2 <leftVU>:<rightVU>] (currently 0:0)
vmix0-out.pcm3 <both/leftvol>[:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out3 <leftVU>:<rightVU>] (currently 0:0)
vmix0-out.pcm4 <both/leftvol>[:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out4 <leftVU>:<rightVU>] (currently 0:0)
vmix0-out.pcm5 <both/leftvol>[:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out5 <leftVU>:<rightVU>] (currently 0:0)
vmix0-out.pcm6 <both/leftvol>[:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out6 <leftVU>:<rightVU>] (currently 0:0)
vmix0-out.pcm7 <both/leftvol>[:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out7 <leftVU>:<rightVU>] (currently 0:0)
vmix0-out.pcm8 <both/leftvol>[:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out8 <leftVU>:<rightVU>] (currently 0:0)
vmix0-out.pcm9 <both/leftvol>[:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out9 <leftVU>:<rightVU>] (currently 0:0)
vmix0-in <leftVU>:<rightVU>] (currently 0:0)

[/HTML]

[HTML]
Version info: OSS 4.0 (b1015/200803231646) (0x00040003) 
Platform: Linux/i686 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 (tom-desktop)

Number of audio devices:	2
Number of audio engines:	10
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: sbxfi0 Sound Blaster X-Fi interrupts=987271 (987271)
    PCI device 1102:0005, subdevice 1102:1003
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual mixer


Mixer devices
 0: Sound Blaster X-Fi (Mixer 0 of device object 1)

Audio devices
Sound Blaster X-Fi output         /dev/oss/sbxfi0/pcm0  (device index 0)
Sound Blaster X-Fi input          /dev/oss/sbxfi0/pcmin0  (device index 1)

[/HTML]

Thanks
Tom

---

### Post by Yellow Pasque on 2008-10-09
I think you'd have better luck posting to the OpenSound Linux forums.
Also, I just noticed you were using OSS 4.0 1015. You should probably try the latest OSS (4.1rc2). [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by teust on 2008-10-11
Thanks for the reply, I created a new thread [http://www.4front-tech.com/forum/viewtopic.php?t=2896](http://www.4front-tech.com/forum/viewtopic.php?t=2896) as suggested, so if people have the same issue they can follow.  Not feeling much love there yet though.  I upgraded OSS using the link you provided, I still have sound but now skype won't make test calls which it would before!!

---

### Post by H4ck3rz on 2008-10-11
hi you got sb X-Fi to work by any chance did you get this problem iv got the oss4 installed & on the ossxmix it shows audio playing but i cnt hear anything hope you did get this problem & can help me here is my ossinfo ```
h4ck3rz@h4ck3rz-desktop:~$ ossinfo
Version info: OSS 4.1 (b rc2/200810091939) (0x00040090) 
Hg revision: changeset: 473:d79ebde9987e, tag: tip, date: Tue Oct 07 17:50:26 2008 +0300, summary: Suported rate fix for envy24
Platform: Linux/x86_64 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 (h4ck3rz-desktop)

Number of audio devices:	2
Number of audio engines:	6
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_sbxfi0 Sound Blaster X-Fi (UAA) interrupts=35591 (35591)
    PCI device 1102:0005, subdevice 1102:6002
 2: oss_usb0 USB audio core services


Mixer devices
 0: Sound Blaster X-Fi (UAA) (Mixer 0 of device object 1)

Audio devices
Sound Blaster X-Fi (UAA) output   /dev/oss/oss_sbxfi0/pcm0  (device index 0)
Sound Blaster X-Fi (UAA) input    /dev/oss/oss_sbxfi0/pcmin0  (device index 1)
h4ck3rz@h4ck3rz-desktop:~$ 

```

---

### Post by teust on 2008-10-12
Skype makes test calls now, but still have the problem with the mic.  H4ck3rz I didn't have sound after installing OSS, for me my problem was the onboard sound was being used by default, so I disabled it in the BIOS and I got sound :)  Try osstest and see if that does anything.

---

### Post by bluestix on 2009-08-31
I got Skype working with an X-Fi on 9.04 x64.


I used the Creative Beta Driver though.


Here is how I did it. The explanation assumes you already have working sound with the Creative Beta driver.


[http://ubuntuforums.org/showpost.php?p=7878068&postcount=3]("http://ubuntuforums.org/showpost.php?p=7878068&postcount=3")

---

