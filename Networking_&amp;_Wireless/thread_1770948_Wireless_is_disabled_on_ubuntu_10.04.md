---
title: "Wireless is disabled on ubuntu 10.04"
date: 2011-05-29
forum: Networking &amp; Wireless
---

### Post by tim042849 on 2011-05-29
I've installed ubuntu 10.04 on a hp mini 110. I've used netbook
remix on this same computer and had no problems with a wireless
connection. In this case, network manager shows **wireless disabled.** 
I have installed the Broadcom B43 Wireless drive from 
Adminstration->Hardware drivers. **No help**! ifconfig does not
show eth1 and lspci tells me that the Broadcom BCM4312 Network
controller is present.
What else do I need to do?
Thanks
Tim

---

### Post by chili555 on 2011-05-29
Let's have a look at:```
dmesg | grep b43
rfkill list all
lsmod | grep wmi
```Thanks.

---

### Post by tim042849 on 2011-05-29
> **chili555 said:**
> Let's have a look at:```
dmesg | grep b43
rfkill list all
lsmod | grep wmi
```Thanks.:popcorn:
I got shrimp on the barbie and my significant other is
giving me the evil eye when I get near the computer. I will
have dumps for that in the morning and if anyone else has
any other diagnostics that they think I should run, speak
up and I will have 'em tomorrow.
thanks for such a timely response.
tim

---

### Post by chili555 on 2011-05-29
> I will have dumps for that in the morning I'll look for you then. Enjoy the shrimp. I'm jealous!

---

### Post by Bucky Ball on 2011-05-29
Have you plugged in a cable and gotten updates and checked any response for your wireless? B43, yes, but you also need b43-fwcutter to install. Plugging in a cable may pick this up automagically and offer it for installation. ;)

---

### Post by tim042849 on 2011-05-30
> **Bucky Ball said:**
> Have you plugged in a cable and gotten updates and checked any response for your wireless? B43, yes, but you also need b43-fwcutter to install. Plugging in a cable may pick this up automagically and offer it for installation. ;)
Yes, I have plugged in a cable. The entire installation was done
with the lan cable connected.
thanks.
Dumps follow:
for dmesg: ```

[    1.347478] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.347508] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[   14.766294] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   15.085293] Registered led device: b43-phy0::tx
[   15.085345] Registered led device: b43-phy0::rx
[   15.085394] Registered led device: b43-phy0::radio
[   16.657131] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   16.756086] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[   16.780593] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[   16.951306] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   17.338025] b43-phy0: Radio hardware status changed to DISABLED
[   17.345158] b43-phy0: Radio turned on by software
[   17.345167] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.

```
For lsmod ```

snd_rawmidi            19056  1 snd_seq_midi
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54180  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```
and for rfkill ```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```
Thanks. 
tim

---

### Post by Bucky Ball on 2011-05-30
System>Administration>Synaptic Package Manager. Search for 'b43-fwcutter'. Is it installed? If not, install. Reboot. Any luck? That card *should *be working out of the box.

---

### Post by chili555 on 2011-05-30
> **Bucky Ball said:**
> System>Administration>Synaptic Package Manager. Search for 'b43-fwcutter'. Is it installed? If not, install. Reboot. Any luck? That card *should *be working out of the box.The firmware is installed and loading:> b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
b43-fwcutter is not going to turn the switch on.

---

### Post by chili555 on 2011-05-30
Tim, here is all you need to do:> The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.

---

### Post by tim042849 on 2011-05-30
> **chili555 said:**
> Tim, here is all you need to do:

:redface:Hey! A meaningful error message! I got this netbook without an owner's manual and just started it by pressing buttons.
FYI: On the front of the unit are two buttons. I have used the
left one to start the unit. I had probably fooled around with
the right one and had shut it off earlier. 
By pressing it leftward, it blinked red and
**lo** I have wireless.
Thanks folks
Your help is greatly appreciated.
cheers
tim

---

