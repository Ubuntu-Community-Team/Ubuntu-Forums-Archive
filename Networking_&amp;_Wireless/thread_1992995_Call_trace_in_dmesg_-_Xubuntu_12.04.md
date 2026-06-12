---
title: "Call trace in dmesg - Xubuntu 12.04"
date: 2012-06-01
forum: Networking &amp; Wireless
---

### Post by artg on 2012-06-01
I've just updated 11.10 Xubuntu to 12.04, and am getting a call trace in the dmesg output.

I don't understand what it means, and whether it matters (I think it's something to do with wireless, but wifi works OK as far as I know).

Hardware is a Dell D620 which has an annoying US wifi card that won't use all the EU channel allocations. I'm not sure if this is relevant - I just mention it because of the stuff about 'regulatory settings'.

I'm also unsure about the reg domain " 'J " which looks like junk - but I don't know where that's set.

[   28.068078] cfg80211: Timeout while waiting for CRDA to reply, restoring regulatory settings
[   28.068083] ------------[ cut here ]------------
[   28.068107] WARNING: at /build/buildd/linux-3.2.0/net/wireless/reg.c:290 is_user_regdom_saved+0x61/0x80 [cfg80211]()
[   28.068110] Hardware name: Latitude D620                   
[   28.068112] Unexpected user alpha2: 'J
[   28.068114] Modules linked in: bnep rfcomm bluetooth binfmt_misc nfsd nfs lockd fscache auth_rpcgss nfs_acl sunrpc snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep snd_pcm dell_wmi ppdev sparse_keymap snd_seq_midi snd_rawmidi dell_laptop dcdbas snd_seq_midi_event pcmcia arc4 snd_seq joydev iwl3945 iwl_legacy mac80211 snd_timer snd_seq_device yenta_socket pcmcia_rsrc option usb_wwan psmouse pcmcia_core usbserial serio_raw cfg80211 snd parport_pc irda crc_ccitt mac_hid i915 drm_kms_helper drm i2c_algo_bit soundcore snd_page_alloc video wmi lp parport usbhid hid tg3
[   28.068163] Pid: 11, comm: kworker/0:1 Not tainted 3.2.0-24-generic #39-Ubuntu
[   28.068165] Call Trace:
[   28.068175]  [<ffffffff8106725f>] warn_slowpath_common+0x7f/0xc0
[   28.068183]  [<ffffffffa0185780>] ? restore_regulatory_settings+0x2f0/0x2f0 [cfg80211]
[   28.068187]  [<ffffffff81067356>] warn_slowpath_fmt+0x46/0x50
[   28.068193]  [<ffffffff811621e4>] ? kfree+0x114/0x140
[   28.068201]  [<ffffffffa0183701>] is_user_regdom_saved+0x61/0x80 [cfg80211]
[   28.068208]  [<ffffffffa018373e>] restore_alpha2+0x1e/0x130 [cfg80211]
[   28.068216]  [<ffffffffa01854e4>] restore_regulatory_settings+0x54/0x2f0 [cfg80211]
[   28.068225]  [<ffffffffa0185780>] ? restore_regulatory_settings+0x2f0/0x2f0 [cfg80211]
[   28.068233]  [<ffffffffa01857a1>] reg_timeout_work+0x21/0x30 [cfg80211]
[   28.068238]  [<ffffffff81084f5a>] process_one_work+0x11a/0x480
[   28.068241]  [<ffffffff81085d04>] worker_thread+0x164/0x370
[   28.068245]  [<ffffffff81085ba0>] ? manage_workers.isra.29+0x130/0x130
[   28.068249]  [<ffffffff8108a55c>] kthread+0x8c/0xa0
[   28.068254]  [<ffffffff81666ef4>] kernel_thread_helper+0x4/0x10
[   28.068258]  [<ffffffff8108a4d0>] ? flush_kthread_worker+0xa0/0xa0
[   28.068262]  [<ffffffff81666ef0>] ? gs_change+0x13/0x13
[   28.068264] ---[ end trace 009754ccbc1e397d ]---
[   28.068266] cfg80211: Keeping preference on module parameter ieee80211_regdom: 'J
[   28.068270] cfg80211: Calling CRDA to update world regulatory domain
[   28.072458] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   28.072463] cfg80211: World regulatory domain updated:

---

### Post by chili555 on 2012-06-01
> Hardware is a Dell D620 which has an annoying US wifi card that won't use all the EU channel allocations. I'm not sure if this is relevant - I just mention it because of the stuff about 'regulatory settings'.

I'm also unsure about the reg domain " 'J " which looks like junk - but I don't know where that's set.> WARNING: at /build/buildd/linux-3.2.0/net/wireless/reg.c:290 is_user_regdom_saved+0x61/0x80 [cfg80211]()I suggest we set the correct regulatory domain and see if the warnings go away. Since your annoying wireless card was made in the USA, I suspect the channels available are etched in silicon and not adjustable by users.

Please find out your two letter country code here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)  I will, for illustration purposes, use XY. Of course, substitute your actual code. Please do:```
sudo gedit /etc/modprobe.d/cfg80211.conf
```Add a single line:```
options cfg80211 ieee80211_regdom=XY
```If you don't have the text editor gedit, use kate, nano, leafpad, vim or any other text editor. Proofread carefully, save and close gedit.

At your next ordinary reboot, check dmesg and see if your regulatory domain XY sticks and if the call trace is fixed.

---

### Post by artg on 2012-06-01
Thanks for the fast response. It didn't immediately fix it, but it did lead me there pretty quickly.

There was no file  /etc/modprobe.d/cfg80211.conf  , so I created one with  only the line

options cfg80211 ieee80211_regdom=GB

This produced the same result as before.

However, there was a file /etc/modprobe.d/options-iwl3945.conf (and the wireless hardware on this machine is Intel(R) PRO/Wireless 3945ABG/BG)

This file contained the line 

options cfg80211 ieee80211_regdom='JP'

So I replaced it with the line above (GB, no quotes) and then got far more reasonable output in dmesg : it reported the value GB and then proceeded to disable certain channels (I'll paste that if useful but I assume it's all correct). There was no call trace, and the wifi still works on my home AP.

So I think that's a fix, thanks.

I confess to being a bit confused about the regulatory domain. I can see an argument for having an AP limited to a smaller number of channels, but isn't the point of a laptop to roam ? Perhaps from country to country ? And then use whatever channels are appropriate there, rather than in the country where it was configured ?

---

### Post by artg on 2012-06-01
That leaves the question of how 'JP' got there. 

I wouldn't assume it's an error in the configuration generation, as I've tried in the past (on 11.04, probably) to get this machine to use GB channels. I may have put that there myself and forgotten it (I tried to find the notes I'd used previously to experiment so that I could ensure it was all at default, but I failed).

---

### Post by artg on 2012-06-01
.. and for anyone else as badly informed as me :

There are notes all over the web describing what may be put in that field. Some use single quotes, some use double quotes, some use no quotes.

Here is a proper explanation as to how it works (it's much easier to find these things when you're starting from the end !)

[http://linuxwireless.org/en/developers/Regulatory](http://linuxwireless.org/en/developers/Regulatory)

---

### Post by chili555 on 2012-06-01
I'm glad it's working as expected. 

I think, and this is educated speculation, that some countries have radio frequencies reserved for some purposes that, perhaps other countries do not. They would like for my US laptop to not interfere when I travel to Switzerland, for example. In an ideal world, the router would only use allowable channels. However, it is perfectly possible to buy a router or a laptop or a wireless device across national borders. After our world leaders resolve the Facebook IPO, Greece and Syria, I really wish they'd fix regulatory domain!

So that the searchers will find your solution, would you please use thread tools to mark Solved?

---

