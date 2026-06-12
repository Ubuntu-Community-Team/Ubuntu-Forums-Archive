---
title: "WIFI performance degraded after upgrade to 10.10"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by TooTechy on 2011-01-12
I would like to re-raise this topic that I have seen on other discussion boards but seems to be going no where. Please correct me if I am wrong.

I have been using Ubuntu for many years now having switched from other distributions. All my machines ran some version of Ubuntu, until just recently.

I upgraded my personal HP TX2500 from 9.04 to 10.04. No problems. After 10.10 had been out for a while I upgraded again. The wireless would drop when busy/(signal slightly weakened) etc. It would not function again unless the wifi module was reloaded.

Then I installed 10.10 on my HP NC6400 the same thing occured. I installed Ubuntu 10.04 instead. It seemed no better. After some Googling, it seemed I was not alone. I tried all the suggestions I could find and none of them worked. One suggestion was to install Fedora 14. This works perfectly on the nc6400.

The HP TX2500 has been reinstalled back with 10.04 where the wireless seems ok and I assume I am stuck there for a while.

Now my question is why would the networking behave this way for Ubuntu 10.10 (10.04 as well on the NC6400) but wireless on Fedora 14 is perfect (I mean really good! Better than either Ubuntu 10.04 or 10.10 on any of my laptops) on the NC6400.

I am hoping that we can find a way to fix this, otherwise I will likely have to drop Ubuntu completely because I do not have an upgrade path for laptops. There must be many other users in the same position who are not discussing it and just rebooting each time this occurs. This must give a negative perception of otherwise great software.

Systems running Linux
Dell D610
HP TX2500
HP NC6400
IBM T20
Gigabyte P35C DS3r
Soyo SY-K7V Dragon Plus
plus others now retired.

---

### Post by Zookalicious on 2011-03-30
Same problem. If I find anything out I'll let you know. Broadcom 4322 here.

---

### Post by TBABill on 2011-03-30
Some people have found when they look in lsmod that there is more than one driver trying to claim the device, usually causing no performance at all and other times allowing very degraded performance. Others face other issues. I can't say what could be the problem because you did not list a device, but merely the symptoms. if you can list your hardware, drivers in use, anything blacklisted, lshw, etc., maybe it can be diagnosed to a fix since it works in Fedora well.
 
Edit: that was to the OP
 
To Zookalicious, what have you done so far to troubleshoot, which driver are you using, etc? Further symptoms?

---

### Post by Zookalicious on 2011-03-30
Thanks for your interest TBABill.

I'm using the proprietary Broadcom STA Driver that is recommended in System > Administration > Additional Drivers. 

The card is Broadcom 4322. Generally, my wireless works perfectly at home, friends houses, relatives, the problem is when I am on my University campus. There is no password, it's an open network, and at random intervals, the wireless will suddenly disconnect. At this point it usually reconnects after a few seconds. However sometimes it will disconnect, struggle to reconnect, and then fail after a minute or so. This seems to have only occurred recently, either from an update or from updating to 10.10, I'm not quite sure.

This identical problem also happens to friends whom I have installed 10.10 for on a fresh installation.

I have tried several things such as uninstalling and redownloading / installing the driver, disabling bluetooth, disabling wireless power management, and I have attempted to search through log files, but I am not too knowledgeable of them yet or where to look / what to look for. 

```

Module                  Size  Used by
nls_iso8859_1           4657  0 
nls_cp437               6375  0 
vfat                   10954  0 
fat                    56244  1 vfat
usb_storage            50436  0 
rfcomm                 40787  4 
binfmt_misc             7984  1 
sco                     9986  2 
bnep                   11985  2 
l2cap                  42304  16 rfcomm,bnep
vboxnetadp              5267  0 
vboxnetflt             14966  0 
vboxdrv              1792856  2 vboxnetadp,vboxnetflt
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_realtek   300173  1 
nls_utf8                1453  1 
hfsplus                78159  1 
nvidia              10221046  50 
lib80211_crypt_tkip     8732  0 
snd_hda_intel          26147  2 
snd_hda_codec         100951  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia_bl               9232  0 
joydev                 11395  0 
btusb                  12929  2 
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
bcm5974                 8925  0 
v4l1_compat            15519  2 uvcvideo,videodev
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_compat_ioctl32    12614  1 videodev
applesmc               37104  0 
soundcore               1240  1 snd
shpchp                 34910  0 
wl                   1965231  0 
led_class               3393  1 applesmc
i2c_nforce2             6155  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lib80211                6175  2 lib80211_crypt_tkip,wl
input_polldev           4527  1 applesmc
coretemp                6442  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
hid_apple               5695  0 
usbhid                 42030  0 
hid                    82949  2 hid_apple,usbhid
uvesafb                25058  1 
ahci                   22210  4 
forcedeth              55649  0 
libahci                26148  1 ahci

```

The following is output from lsmod, I can provide any other output if you think it will give any more information. I haven't had much luck with this so far. 

Thank you again for your help.

---

### Post by TBABill on 2011-03-30
In that environment could it be possible that conflicting traffic within close distances could be disrupting the connection? I'm not sure how Ubuntu manages traffice and frequencies of wireless compared to Windows, but many users with similar frequencies in close proximity can be an issue. From the sounds of it your configuration is correct but perhaps someone like Chilli555 can provide thoughts on the subject of interference and controlling channels or frequencies? He's the guru of wireless and may (hopefully) not mind if you PM directly to ask.

---

### Post by Zookalicious on 2011-03-30
Hmm I've always been too worried that I'll be bothering one of the staff or experienced volunteers by PMing them, but I guess it couldn't hurt to try. 

That's a theory I've been considering too. It's a fairly busy campus, so I've noticed that there are a lot of routers in the main lecture halls. I hypothesised that the rapid disconnects / reconnects could actually be Ubuntu switching from one router to another with the same name. Network-Manager applet shows that there is only one "school-wifi" SSID, but WiCD shows many of them. (I also tried WiCD, but I found it to be worse then nm-applet). Just a thought. 

Also my OS X and Windows partitions both handle the campus situation fine for what it's worth, however I loathe using them, I'd much rather deal with disconnects then have to boot into one of those even if it's only on campus.

---

### Post by phoenix1/4 on 2011-05-21
Thought I'd just jump into the mix here too.

I've noticed since I upgraded from 8.04 that I've been having more and more trouble connecting to my Uni's network, I would also support the theory above as it seems I can get a decent connection when I am very close to a router, but it flakes out if its between two or three.

I think for now it's just a case of grin and bear it. I just my phone for an internet connection at uni now.

---

### Post by Zookalicious on 2011-05-22
For anyone curious, I did a full wipe of my hard drive a couple weeks ago (windows did atrocious things to my partition table), and installed 11.04 in place of 10.10 which completely solved all of my wireless problems! (also unity is much nicer than I had previously anticipated, so that's an added bonus). I know not everyone is ready to upgrade yet, but that's my two cents.

---

