---
title: "Pro/Wireless 3945 ABG  Ubuntu 10.10 Wireless not working"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by tadthebuilder on 2011-02-16
I have a compaq nc6400 with the intel  Pro/Wireless 3945 ABG card. 
It fails to find any wireless networks.
the IWL3945 driver was installed automatically
But when searching for networks none are found, even though on any other computer in the house the network is found.

According to [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel#miniPCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel#miniPCI)

this should work, or at least it did on previous versions.

any ideas?

---

### Post by chili555 on 2011-02-16
It does work perfectly; I am answering this post with my Intel 3945ABG. Please open a terminal and post:```
rfkill list all
dmesg | grep iwl
```Thanks.

---

### Post by tadthebuilder on 2011-02-16
> **chili555 said:**
> It does work perfectly; I am answering this post with my Intel 3945ABG. Please open a terminal and post:```
rfkill list all
dmesg | grep iwl
```Thanks.
rfkill list all puts out
```
 0: hp-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
1: hp-bluetooth: Bluetooth
        Soft blocked: yes
        Hard blocked: yes
2: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes

```and dmesg | grep iwl puts out
```
[   13.865318] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   13.865321] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   13.865397] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.865412] iwl3945 0000:10:00.0: setting latency timer to 64
[   13.919212] iwl3945 0000:10:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.919216] iwl3945 0000:10:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   13.919369] iwl3945 0000:10:00.0: irq 45 for MSI/MSI-X

```Thanks for your help.

---

### Post by chili555 on 2011-02-16
> phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: yesTypically, this means that the hardware switch on your laptop is in the 'Off' position. Can you please switch it on?

---

### Post by tadthebuilder on 2011-02-16
> **chili555 said:**
> Typically, this means that the hardware switch on your laptop is in the 'Off' position. Can you please switch it on?
I was afraid of this.
There is a button and I press it and nothing happens.
I just bought this laptop for like $160 so what should I expect when the button does nothing. Is there any way to "over rule" the hardware switch?
There is a led light on the button that does not come on either.
And there are volume switches near the wireless button which work fine, and light up when pressed.

so it seems to be that specific button not working.

---

### Post by chili555 on 2011-02-16
Do you have a screwdriver? Please see: [http://madwifi-project.org/wiki/UserDocs/MiniPCI](http://madwifi-project.org/wiki/UserDocs/MiniPCI)> Masking Pin 13 ¶

If this does not work for you, you could try masking off pin 13; sellotape is ideal for this. To find pin 13, hold the card so that the pins, (contacts) are facing you and the key (a little cut in the card) in on the left. Pins are counted up-to-down and left-to-right:

1  key  3  5  7  9 11 13 15 ...
2  key  4  6  8 10 12 14 16 ...

Pin 13 will be thus the seventh pin from the left edge or the sixths pin from the key on the upper side of the card. This picture shows the correct pin to cover, but incorrectly calls is pin 7: [http://www.minipci.biz/pin7.jpg](http://www.minipci.biz/pin7.jpg)

Once you have found pin 13, mask it with a piece of tape, reinstall the card and test.`
Users' Laptops confirmed as needing workarounds ¶
Fujitsu S2020 ¶

    * Sellotape over pin 13 causes radio to work. - Switch on back had no effect. Before you try this, you might try (but I am skeptical it will work):```
sudo rfkill unblock all
rfkill list all
```

---

### Post by tadthebuilder on 2011-02-16
> **chili555 said:**
> Do you have a screwdriver? Please see: [http://madwifi-project.org/wiki/UserDocs/MiniPCI](http://madwifi-project.org/wiki/UserDocs/MiniPCI)Before you try this, you might try (but I am skeptical it will work):```
sudo rfkill unblock all
rfkill list all
```

rfkill unblock all worked!!!!
I am connected. Thank you very much. You have been a big help to me.
Have a wonderful day!
Thank you very much.

---

### Post by chili555 on 2011-02-16
I will have a wonderful day until you suddenly think, "How can I get this to work automagically on boot? I better ask Chili."

I will brew a cuppa tea while I await the inevitable question...

---

### Post by tadthebuilder on 2011-02-16
> **chili555 said:**
> I will have a wonderful day until you suddenly think, "How can I get this to work automagically on boot? I better ask Chili."

I will brew a cuppa tea while I await the inevitable question...
I was actually just going to live with opening the terminal and running that command every time I booted, but you seem to be offering to give me this piece of information...
so how would I go about doing this?

---

### Post by chili555 on 2011-02-16
Let's just add the command to rc.local:```
sudo gedit /etc/rc.local
```Add a line above exit 0:```
rfkill unblock all

```Proofread, save and close gedit. You should be all set.

Please post back so the rfkill seachers will find out how it worked.

---

### Post by tadthebuilder on 2011-02-16
> **chili555 said:**
> Let's just add the command to rc.local:```
sudo gedit /etc/rc.local
```Add a line above exit 0:```
rfkill unblock all

```Proofread, save and close gedit. You should be all set.

Please post back so the rfkill seachers will find out how it worked.
It worked great. boots up and wireless is activated.
Even the LED light is on.

Thank you once again, you made this cheap used laptop worth the money I spent on it.

---

### Post by erez001 on 2011-04-08
Thanks,

now my wifi works again

---

### Post by 3D-TiMi on 2011-05-26
I also having this wireless card on my old laptop Benq Joybook R55.
I always need to manually enable hardware switch (Fn+F2) to enable wireless.
I was trying all this solutions but no luck.

With ```
rfkill list all
```

I have this:

```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```


And with ```
dmesg | grep iwl
```

I have this:

```
[    7.412529] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[    7.412536] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[    7.412627] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.412643] iwl3945 0000:02:00.0: setting latency timer to 64
[    7.452901] iwl3945 0000:02:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[    7.452906] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    7.453063] iwl3945 0000:02:00.0: irq 45 for MSI/MSI-X
[    8.575063] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[  144.902444] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9
[  418.673768] iwl3945 0000:02:00.0: Card state received: HW:Kill SW:On
[  418.673919] iwl3945 0000:02:00.0: Not sending command - RF KILL
[  418.673928] iwl3945 0000:02:00.0: Error sending REPLY_QOS_PARAM: enqueue_hcmd failed: -5
[  418.673947] iwl3945 0000:02:00.0: Not sending command - RF KILL
[  418.673956] iwl3945 0000:02:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  418.673964] iwl3945 0000:02:00.0: Error setting new configuration (-5).
[  418.673971] iwl3945 0000:02:00.0: Not sending command - RF KILL
[  418.673978] iwl3945 0000:02:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[  418.688286] iwl3945 0000:02:00.0: Not sending command - RF KILL
[  418.688299] iwl3945 0000:02:00.0: Error sending REPLY_REMOVE_STA: enqueue_hcmd failed: -5
[  418.688309] iwl3945 0000:02:00.0: Error removing station 00:02:cf:82:0e:30
[  418.693404] iwl3945 0000:02:00.0: Not sending command - RF KILL
[  418.693417] iwl3945 0000:02:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[  418.693433] iwl3945 0000:02:00.0: Not sending command - RF KILL
[  418.693440] iwl3945 0000:02:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  418.693448] iwl3945 0000:02:00.0: Error setting new configuration (-5).
[  418.724178] iwl3945 0000:02:00.0: Not sending command - RF KILL
[  418.724191] iwl3945 0000:02:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  418.724201] iwl3945 0000:02:00.0: Error setting new configuration (-5).
[  418.728119] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x040003DD
[  700.312830] iwl3945 0000:02:00.0: Card state received: HW:Kill SW:On
[  700.312978] iwl3945 0000:02:00.0: Not sending command - RF KILL
[  700.312987] iwl3945 0000:02:00.0: Error sending REPLY_QOS_PARAM: enqueue_hcmd failed: -5
[  700.313005] iwl3945 0000:02:00.0: Not sending command - RF KILL
[  700.313014] iwl3945 0000:02:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  700.313022] iwl3945 0000:02:00.0: Error setting new configuration (-5).
[  700.313030] iwl3945 0000:02:00.0: Not sending command - RF KILL
[  700.313037] iwl3945 0000:02:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[  700.328284] iwl3945 0000:02:00.0: Not sending command - RF KILL
[  700.328296] iwl3945 0000:02:00.0: Error sending REPLY_REMOVE_STA: enqueue_hcmd failed: -5
[  700.328306] iwl3945 0000:02:00.0: Error removing station 00:02:cf:82:0e:30
[  700.333439] iwl3945 0000:02:00.0: Not sending command - RF KILL
[  700.333449] iwl3945 0000:02:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[  700.333464] iwl3945 0000:02:00.0: Not sending command - RF KILL
[  700.333471] iwl3945 0000:02:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  700.333479] iwl3945 0000:02:00.0: Error setting new configuration (-5).
[  700.356182] iwl3945 0000:02:00.0: Not sending command - RF KILL
[  700.356196] iwl3945 0000:02:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  700.356207] iwl3945 0000:02:00.0: Error setting new configuration (-5).
[  700.360116] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x040003DD

```

---

### Post by chili555 on 2011-05-26
> I always need to manually enable hardware switch (Fn+F2) to enable wireless.When you press the Fn+F2 keys, does it change Hard blocked=yes to Hard blocked=no? May we see:```
lsmod
```Thanks.

---

### Post by 3D-TiMi on 2011-05-26
Yes it changes to "Hard blocked: no" when I'm press Fn+F2.

```
lsmod
```

```
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
binfmt_misc            13213  1 
rfcomm                 38125  8 
parport_pc             32111  0 
ppdev                  12849  0 
sco                    17779  2 
bnep                   17785  2 
vesafb                 13449  1 
l2cap                  48656  16 rfcomm,bnep
nvidia               7098106  57 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24140  2 
pcmcia                 39671  0 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27230  0 
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
btusb                  18160  2 
tifm_7xx1              12898  0 
joydev                 17322  0 
serio_raw              12990  0 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
tifm_core              15040  1 tifm_7xx1
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
video                  18951  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
arc4                   12473  2 
iwl3945               130113  0 
iwlcore               148965  1 iwl3945
mac80211              257001  2 iwl3945,iwlcore
cfg80211              156212  3 iwl3945,iwlcore,mac80211
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  2 
uas                    17676  0 
firewire_ohci          31504  0 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
firewire_core          56138  1 firewire_ohci
sky2                   49172  0 
crc_itu_t              12627  1 firewire_core

```

So there's no way to automatically enable hardware switch?

---

### Post by chili555 on 2011-05-26
> So there's no way to automatically enable hardware switch?Let's just add the command to rc.local:
```
sudo gedit /etc/rc.local
```Add a line above exit 0:
```
rfkill unblock all
```
Proofread, save and close gedit. You should be all set.

I don't see any modules in *lsmod* that we can amend or remove to make rfkill happen. I am fairly confident the rc.local method will work. If it doesn't work, I'm afraid the keys are the only way I know of.

---

### Post by 3D-TiMi on 2011-05-26
Nope that didn't work for me.
Does It need to look like in the picture?

---

### Post by chili555 on 2011-05-26
Yes, exactly like the picture. If it doesn't work, then the Fn+F2 keys are the only way I know of. I'm sorry I can't be of more help.

---

### Post by 3D-TiMi on 2011-05-26
Thank's anyway chili555 :)

---

### Post by Ultra Cronic on 2012-08-16
> **chili555 said:**
> Do you have a screwdriver? Please see: [http://madwifi-project.org/wiki/UserDocs/MiniPCI](http://madwifi-project.org/wiki/UserDocs/MiniPCI)Before you try this, you might try (but I am skeptical it will work):```
sudo rfkill unblock all
rfkill list all
```
----In refrence to: Masking Pin 13 ¶

If this does not work for you, you could try masking off pin 13;  sellotape is ideal for this. To find pin 13, hold the card so that the  pins, (contacts) are facing you and the key (a little cut in the card)  in on the left. Pins are counted up-to-down and left-to-right:

1  key  3  5  7  9 11 13 15 ...
2  key  4  6  8 10 12 14 16 ...

Pin 13 will be thus the seventh pin from the left edge or the sixths pin  from the key on the upper side of the card. This picture shows the  correct pin to cover, but incorrectly calls is pin 7: [http://www.minipci.biz/pin7.jpg](http://www.minipci.biz/pin7.jpg)

Once you have found pin 13, mask it with a piece of tape, reinstall the card and test.`
Users' Laptops confirmed as needing workarounds ¶
Fujitsu S2020 ¶

    * Sellotape over pin 13 causes radio to work. - Switch on back had no effect.--end refrence.

This picture in the link is NOT the same chip. 
I have the wm3945ABG  and it has 7 more pins after the slot shown.

---

