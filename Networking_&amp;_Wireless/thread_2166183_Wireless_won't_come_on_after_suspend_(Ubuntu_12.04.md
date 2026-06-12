---
title: "Wireless won't come on after suspend (Ubuntu 12.04, ZaReason Ultralap 430)"
date: 2013-08-08
forum: Networking &amp; Wireless
---

### Post by john40 on 2013-08-08
Hi all,

I just purchased a ZaReason Ultrabook 430 preinstalled with Ubuntu 12.04. I've never used Linux before and am not all that tech-savvy, but I'm really impressed with what I've seen so far, esp. in comparison to the awfulness that is Windows 8. However, I'm runnig into a bug that I take to be common and well-known, but for some reason I can't find a solution anywhere that's suitable for a novice like myself.

Here it is in a nutshell:

- When I suspend the computer (either by choosing that option from the menu, or just closing the screen) and then turn it back on, my wireless connection is gone.
- Not only that, but I don't see any way to turn it back on except by restarting the machine: the "Enable Wireless" option is greyed out in my menu, as are a bunch of other options. (I could take some detailed notes if that would help, but it would involve suspending the machine, which would make this post hard to write.)
- Maybe it would come back on if I waited a few minutes? I've given it a bit of time, but not had the patience.

Help? Please note that in order to be useful to me, any instructions will need to presume almost no technical know-how except the ability to type and move a mouse. But I'm willing to learn.

Thanks.

---

### Post by praseodym on 2013-08-08
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv' 
lsmod
```

---

### Post by john40 on 2013-08-08
Here is what it shows right now, when I am connected:

john@plato:~$ ```
lsmod | grep -iE '80|ndiswr|forced|8139|hci|usb|1394|hid|.tv'
btusb                  17948  2 
usbhid                 41937  0 
hid                    77428  1 usbhid
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rfcomm                 38139  12 
i915                  428056  3 
bluetooth             158447  23 btusb,bnep,rfcomm
mac80211              436493  1 iwlwifi
cfg80211              178877  2 iwlwifi,mac80211
mac_hid                13077  0 
john@plato:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174313  1 
joydev                 17393  0 
btusb                  17948  2 
usbhid                 41937  0 
uvcvideo               67203  0 
arc4                   12473  2 
videodev               86588  1 uvcvideo
hid                    77428  1 usbhid
mxm_wmi                12893  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
bnep                   17830  2 
dm_multipath           22747  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 38139  12 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  428056  3 
bluetooth             158447  23 btusb,bnep,rfcomm
drm_kms_helper         45466  1 i915
psmouse                86520  0 
parport_pc             32114  0 
iwlwifi               366509  0 
drm                   197641  4 i915,drm_kms_helper
serio_raw              13027  0 
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                  12849  0 
mac80211              436493  1 iwlwifi
i2c_algo_bit           13199  1 i915
cfg80211              178877  2 iwlwifi,mac80211
mac_hid                13077  0 
video                  19115  1 i915
soundcore              14635  1 snd
mei                    36570  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  1 mxm_wmi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
r8169                  56396  0 
dm_mirror              21822  0 
dm_region_hash         16100  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638340  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
```

Do you need me also to show what it displays when the wireless is out?

Thanks.

---

### Post by wildmanne39 on 2013-08-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by john40 on 2013-08-08
Sorry, got it -- thanks.

---

### Post by Toz on 2013-08-08
Have a look at the /var/log/pm-suspend.log file and the results of:
```
cat /var/log/syslog | grep PM:
```
...to see if there are any error messages about iwlwifi (your wireless  driver).

You might want to try manually unloading the driver before suspend and reloading after resume. To do so automatically:
1. Create the file /etc/pm/config.d/modules:
```
gksu gedit /etc/pm/config.d/modules
```
...with the following content:
```
SUSPEND_MODULES="iwlwifi"
```
2. Save the file.
3. Retry suspend.

---

### Post by john40 on 2013-08-09
Thanks for your suggestions.

I created the modules file as you said, but it doesn't seem to have made a difference.

Here's what the suspend.log file turned up; nothing about iwlwifi from what I can see:

```
john@plato:~$ cat /var/log/syslog | grep PM:
Aug  8 13:04:24 plato kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Aug  8 13:04:24 plato kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Aug  8 13:04:24 plato kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug  8 13:04:24 plato kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug  8 13:04:24 plato kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Aug  8 13:04:24 plato kernel: [    0.517289] PM: Registering ACPI NVS region at da3c4000 (671744 bytes)
Aug  8 13:04:24 plato kernel: [    0.517302] PM: Registering ACPI NVS region at da918000 (274432 bytes)
Aug  8 13:04:24 plato kernel: [    1.437781] PM: Hibernation image not present or could not be loaded.
Aug  8 21:56:09 plato kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Aug  8 21:56:09 plato kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Aug  8 21:56:09 plato kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug  8 21:56:09 plato kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug  8 21:56:09 plato kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Aug  8 21:56:09 plato kernel: [    0.517344] PM: Registering ACPI NVS region at da3c4000 (671744 bytes)
Aug  8 21:56:09 plato kernel: [    0.517358] PM: Registering ACPI NVS region at da918000 (274432 bytes)
Aug  8 21:56:09 plato kernel: [    1.434722] PM: Hibernation image not present or could not be loaded.
Aug  8 22:56:53 plato kernel: [ 3641.743819] PM: Syncing filesystems ... done.
Aug  8 22:56:53 plato kernel: [ 3641.745995] PM: Preparing system for mem sleep
Aug  9 07:02:22 plato kernel: [ 3642.590205] PM: Entering mem sleep
Aug  9 07:02:22 plato kernel: [ 3642.849876] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 221.212 msecs
Aug  9 07:02:22 plato kernel: [ 3643.084771] PM: suspend of drv:sd dev:1:0:0:0 complete after 494.621 msecs
Aug  9 07:02:22 plato kernel: [ 3643.084807] PM: suspend of drv:scsi dev:target1:0:0 complete after 494.584 msecs
Aug  9 07:02:22 plato kernel: [ 3643.084824] PM: suspend of drv:scsi dev:host1 complete after 456.661 msecs
Aug  9 07:02:22 plato kernel: [ 3643.105556] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 477.238 msecs
Aug  9 07:02:22 plato kernel: [ 3643.105594] PM: suspend of drv: dev:pci0000:00 complete after 477.088 msecs
Aug  9 07:02:22 plato kernel: [ 3643.105618] PM: suspend of devices complete after 515.871 msecs
Aug  9 07:02:22 plato kernel: [ 3643.105621] PM: suspend devices took 0.516 seconds
Aug  9 07:02:22 plato kernel: [ 3643.201480] PM: late suspend of devices complete after 95.969 msecs
Aug  9 07:02:22 plato kernel: [ 3643.214173] PM: Saving platform NVS memory
Aug  9 07:02:22 plato kernel: [ 3643.525717] PM: Restoring platform NVS memory
Aug  9 07:02:22 plato kernel: [ 3644.038521] PM: early resume of devices complete after 1.196 msecs
Aug  9 07:02:22 plato kernel: [ 3644.217041] PM: resume of drv: dev:ep_00 complete after 177.981 msecs
Aug  9 07:02:22 plato kernel: [ 3644.217060] PM: resume of drv:hub dev:1-1:1.0 complete after 178.041 msecs
Aug  9 07:02:22 plato kernel: [ 3644.217072] PM: resume of drv: dev:ep_81 complete after 178.033 msecs
Aug  9 07:02:22 plato kernel: [ 3644.282570] PM: resume of drv:uvcvideo dev:1-1.1:1.1 complete after 243.383 msecs
Aug  9 07:02:22 plato kernel: [ 3644.282575] PM: resume of drv: dev:ep_00 complete after 243.367 msecs
Aug  9 07:02:22 plato kernel: [ 3644.282582] PM: resume of drv:uvcvideo dev:1-1.1:1.0 complete after 243.434 msecs
Aug  9 07:02:22 plato kernel: [ 3644.282650] PM: resume of drv: dev:ep_83 complete after 243.483 msecs
Aug  9 07:02:22 plato kernel: [ 3644.380917] PM: resume of drv:sd dev:1:0:0:0 complete after 342.172 msecs
Aug  9 07:02:22 plato kernel: [ 3644.380936] PM: resume of drv:scsi_device dev:1:0:0:0 complete after 342.150 msecs
Aug  9 07:02:22 plato kernel: [ 3644.380942] PM: resume of drv:scsi_disk dev:1:0:0:0 complete after 309.063 msecs
Aug  9 07:02:22 plato kernel: [ 3644.442893] PM: resume of drv:i915 dev:0000:00:02.0 complete after 404.803 msecs
Aug  9 07:02:22 plato kernel: [ 3644.632722] PM: resume of drv:usb dev:1-1.4:1.1 complete after 593.838 msecs
Aug  9 07:02:22 plato kernel: [ 3644.632726] PM: resume of drv: dev:ep_00 complete after 593.789 msecs
Aug  9 07:02:22 plato kernel: [ 3644.632734] PM: resume of drv:usb dev:1-1.4:1.0 complete after 593.921 msecs
Aug  9 07:02:22 plato kernel: [ 3644.632737] PM: resume of drv: dev:ep_83 complete after 593.818 msecs
Aug  9 07:02:22 plato kernel: [ 3644.632757] PM: resume of drv: dev:ep_82 complete after 593.892 msecs
Aug  9 07:02:22 plato kernel: [ 3644.632761] PM: resume of drv: dev:ep_81 complete after 593.926 msecs
Aug  9 07:02:22 plato kernel: [ 3644.632766] PM: resume of drv:bluetooth dev:hci0 complete after 189.990 msecs
Aug  9 07:02:22 plato kernel: [ 3644.632771] PM: resume of drv: dev:ep_03 complete after 593.863 msecs
Aug  9 07:02:22 plato kernel: [ 3644.632776] PM: resume of drv: dev:ep_02 complete after 593.916 msecs
Aug  9 07:02:22 plato kernel: [ 3644.632805] PM: resume of devices complete after 594.970 msecs
Aug  9 07:02:22 plato kernel: [ 3644.633106] PM: resume devices took 0.596 seconds
Aug  9 07:02:22 plato kernel: [ 3644.633142] PM: Finishing wakeup.
Aug  9 07:04:29 plato kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Aug  9 07:04:29 plato kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Aug  9 07:04:29 plato kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug  9 07:04:29 plato kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug  9 07:04:29 plato kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Aug  9 07:04:29 plato kernel: [    0.517497] PM: Registering ACPI NVS region at da3c4000 (671744 bytes)
Aug  9 07:04:29 plato kernel: [    0.517510] PM: Registering ACPI NVS region at da918000 (274432 bytes)
Aug  9 07:04:29 plato kernel: [    1.434595] PM: Hibernation image not present or could not be loaded.
```

And here's what those lsmod commands suggested in the first reply showed when the wireless was disabled:

```
john@plato:~$ lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv'
btusb                  17948  2 
usbhid                 41937  0 
hid                    77428  1 usbhid
rfcomm                 38139  12 
bluetooth             158447  23 btusb,bnep,rfcomm
mac80211              436493  1 iwlwifi
mac_hid                13077  0 
cfg80211              178877  2 iwlwifi,mac80211
john@plato:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174313  1 
joydev                 17393  0 
btusb                  17948  2 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
arc4                   12473  2 
usbhid                 41937  0 
hid                    77428  1 usbhid
mxm_wmi                12893  0 
dm_multipath           22747  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
bnep                   17830  2 
rfcomm                 38139  12 
parport_pc             32114  0 
bluetooth             158447  23 btusb,bnep,rfcomm
snd_rawmidi            25424  1 snd_seq_midi
ppdev                  12849  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  428056  3 
iwlwifi               366509  0 
mac80211              436493  1 iwlwifi
mac_hid                13077  0 
cfg80211              178877  2 iwlwifi,mac80211
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
psmouse                86520  0 
drm_kms_helper         45466  1 i915
serio_raw              13027  0 
drm                   197641  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
wmi                    18744  1 mxm_wmi
mei                    36570  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56396  0 
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16100  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638340  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
```

Anything of note here?

Thanks.

---

### Post by Toz on 2013-08-09
What does pm-suspend.log say?
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

---

### Post by john40 on 2013-08-09
Thanks, here you go: [http://paste.ubuntu.com/5966525/](http://paste.ubuntu.com/5966525/)

---

### Post by Toz on 2013-08-09
Hmmm. Try this:
1. Delete the /etc/pm/config.d/modules file (since its not working).
2. Disable bluetooth:
```
sudo rfkill block bluetooth
```
3. Check to see that your wireless still works
4. Suspend.
5. On resume, check to see if wireless works.
6. To re-enable bluetooth:
```
sudo rfkill unblock bluetooth
```

---

### Post by john40 on 2013-08-09
Will do, but how do I delete the file?

(Told you I was a novice.)

---

### Post by Toz on 2013-08-09
No worries. Try this command:
```
sudo rm /etc/pm/config.d/modules
```

---

### Post by john40 on 2013-08-09
Thanks, I tried it but still no dice.

By the way, I seem to recall that this is a common problem. There is a proposed solution here that I could try: [http://www.webupd8.org/2013/01/fix-wireless-or-wired-network-not.html](http://www.webupd8.org/2013/01/fix-wireless-or-wired-network-not.html) -- does it seem promising?

---

### Post by Toz on 2013-08-09
> **john40 said:**
> Thanks, I tried it but still no dice.

By the way, I seem to recall that this is a common problem. There is a proposed solution here that I could try: [http://www.webupd8.org/2013/01/fix-wireless-or-wired-network-not.html](http://www.webupd8.org/2013/01/fix-wireless-or-wired-network-not.html) -- does it seem promising?
We tried this earlier, only we used a different filename. Unfortunately, it didn't work for you.

Lets try something a little more heavy-handed.

```
sudo rfkill block all
```
...then suspend/resume, then
```
sudo rfkill unblock all
```
...and test the wireless connection.

---

### Post by john40 on 2013-08-09
Still no dice.

---

### Post by Toz on 2013-08-09
Can you post back your syslog log file? I'd like to see if anything is being logged about the wireless card.
```
pastebinit /var/log/syslog
```
...and past back the link

---

### Post by john40 on 2013-08-09
Here it is: [http://paste.ubuntu.com/5967241/](http://paste.ubuntu.com/5967241/)

---

### Post by Toz on 2013-08-09
How did you configure your network? Did you use Network Manager or some other method?

I'm seeing rfkill statements throughout the file and am not sure if they are the result of the last test you did or something else. Can you do one more suspend/resume without any other commands and post back a link for syslog again?

BTW, [http://ubuntuforums.org/showthread.php?t=2158525](http://ubuntuforums.org/showthread.php?t=2158525) is related similar link, though for another card.

---

### Post by Toz on 2013-08-09
After resume, when the network is greyed out, can you run the following command:
```
sudo rfkill list all
```
...and post back if any are set to yes and which ones?

BTW, I'm just heading out for the weekend and won't have access to the internet. I'll review this thread when I return (don't want you to think I'm ignoring you).

---

### Post by john40 on 2013-08-09
> How did you configure your network? Did you use Network Manager or some other method?

I don't think I did anything at all -- the router was set up by our DSL company, and the computer recognized it right away when I first turned it on.

> I'm seeing rfkill statements throughout the file and am not sure if they are the result of the last test you did or something else. Can you do one more suspend/resume without any other commands and post back a link for syslog again?

Seems impossible b/c of no Internet access, right? At least I keep getting an error when I try to run it. Is there another way I can show you this?

But this:

> After resume, when the network is greyed out, can you run the following command:
Code:

sudo rfkill list all

...and post back if any are set to yes and which ones?

... I can do. The only thing set to yes is Wireless LAN, listed as Hard blocked:

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

Last of all:

> BTW, [http://ubuntuforums.org/showthread.php?t=2158525](http://ubuntuforums.org/showthread.php?t=2158525) is related similar link, though for another card.

Thx, I will take a look while you're away -- and no problem with that, of course; your help has been much appreciated and this is easily worked around.

---

### Post by Toz on 2013-08-09
One last thing as I rush out the door:
> 0: phy0: Wireless LAN
    Soft blocked: no
[COLOR="#FF0000"]**    Hard blocked: yes**[/COLOR]
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
On resume, your wireless device is hard-locked. This, I believe, is your problem. Not sure what is doing this. Do you have a switch or key-combination that turns on/off the wireless? If so, can you try flipping it? Otherwise, I'll research this when I return.

---

