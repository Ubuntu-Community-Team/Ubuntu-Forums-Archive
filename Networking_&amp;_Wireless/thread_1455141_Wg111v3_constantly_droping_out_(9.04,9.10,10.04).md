---
title: "Wg111v3 constantly droping out (9.04,9.10,10.04)"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by tarun1793 on 2010-04-15
Hello all,

I am running 10.04 beta right now, on a hp a6740in , I have wireless usb adapter WG111v3 with me for connecting to my home network , It works perfect in windows but i am trying to get working it with Ubuntu since the past year.

In 10.04 beta , It MAY connects for sometime and then drops out,trying to connect again and again, asking me to review the password each time.

I have also filed a bug about the same some 6-7 months month ago, but the ubuntu  community seems busy with many other things. So i decided finally posting on the forum again , hoping to get a working solution this time(previous was when jaunty launched)..

This is the only thing that keeps me away from using ubuntu for my general day work,
I have already searched through ubuntu forums but always end up with ndiswrapper thing which doesnt works.

Any help is Greatly appreciated....

Thanks.............

---

### Post by tarun1793 on 2010-04-30
Bump -anyone pls...

it still remains a problem in 10.04...............

---

### Post by koanhead on 2010-04-30
This is a Linksys adapter, correct?
I think I have one of these at home, as a matter of fact.
This will be much easier to diagnose if you will post the output of lsusb -v with the device plugged in and lit up. lsmod -a output might help too. If you've already done these (or even if you haven't) posting a link to the bug you filed or related posts you've made might also help.

---

### Post by tarun1793 on 2010-04-30
here is the link to the bug filed :

 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459732](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459732)

---

### Post by koanhead on 2010-05-01
Does "rtl8187" show up in the output of lsmod?
AFAICT that is the correct module for the device's chipset. Problems like this can arise from the kernel using *almost* the right module, and wireless cards are especially tricky since two examples of the same make and model can have different chipsets.
Your bug report includes the output of lsmod, but it's easier to be sure with lsmod -v (which is why I asked for that) since that output, while harder to read, contains the numeric chipset ID rather than just the callout- sometimes all "Realtek 8187" or whatever are not created equal!
Of course, it's possible that the module itself might be buggy- but if there are lots of others using the module with the same device you can discount that. It's also possible that the device might be screwed up. They are pretty robust, but there is a wire inside my Linksys unit (same chipset, by the way) attached to the antenna which can become loose.

---

### Post by tarun1793 on 2010-05-01
lsmod output : 

aes_i586                7272  2 
aes_generic            26899  1 aes_i586
snd_hda_codec_atihdmi     2403  1 
snd_hda_codec_realtek   218461  1 
binfmt_misc             6579  1 
snd_hda_intel          24172  2 
snd_hda_codec          88705  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
arc4                    1125  2 
snd_hwdep               5461  1 snd_hda_codec
fbcon                  37011  71 
tileblit                2003  1 fbcon
font                    7593  1 fbcon
bitblit                 4585  1 fbcon
softcursor              1097  1 bitblit
snd_pcm_oss            38260  0 
snd_mixer_oss          15521  1 snd_pcm_oss
ppdev                   5495  0 
snd_pcm                75540  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1500  0 
snd_seq_oss            27514  0 
snd_seq_midi            4722  0 
snd_rawmidi            18747  1 snd_seq_midi
rtl8187                51069  0 
snd_seq_midi_event      5911  2 snd_seq_oss,snd_seq_midi
radeon                754726  3 
mac80211              229336  1 rtl8187
ttm                    50540  1 radeon
led_class               2663  1 rtl8187
snd_seq                47110  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         28834  1 radeon
drm                   166335  5 radeon,ttm,drm_kms_helper
snd_timer              19784  2 snd_pcm,snd_seq
snd_seq_device          5768  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                32718  2 ttm,drm
lp                      7469  0 
cfg80211              148737  2 rtl8187,mac80211
eeprom_93cx6            1682  1 rtl8187
i2c_algo_bit            5126  1 radeon
psmouse                58060  0 
snd                    55233  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_nforce2             5502  0 
soundcore               6697  1 snd
parport                32400  2 ppdev,lp
serio_raw               4086  0 
snd_page_alloc          7344  2 snd_hda_intel,snd_pcm
usb_storage            39873  1 
ohci1394               28313  0 
ieee1394               83866  1 ohci1394
ahci                   35476  1 
pata_amd                8770  0 
forcedeth              52643  0 
----------------------------------------------------------------------

I think the problem is that it chipset is RTL8187B not rtl8187

---

### Post by koanhead on 2010-05-02
AFAICT that module is supposed to be correct for either chipset. Apparently some folks have experienced problems with it. I don't know why or how an upgrade would cause it to break though.

---

### Post by tarun1793 on 2010-05-22
Bump.. i hv also tried with latest kernels available still no luck..

---

### Post by CoolDreamZ on 2010-05-25
I had a similar problem with 10.04, I am using WPA2-Personal security on my wireless router and I am repeatedly asked for the passphrase. I switched to WEP security and the link worked with no problem.

I solved the original WPA2 problem by downloading, compiling and installing the Realtek 8187L kernel module (driver) version 1039 from the Realtek site [here]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")

My conclusion is that there is a bug with WPA2 support in the RTL8187 module included in 10.04

---

