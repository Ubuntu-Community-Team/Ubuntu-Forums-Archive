---
title: "Help plz with my sound and my beryl"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by ddoong91 on 2007-07-08
Help plz with my sound and my beryl
Hi im a new comer and everything worked out great except
for my sound and the beryl

looking in the forum i've found that korea91 has had the same problem because I have the exact same computer as he does, and all the answers and guides that are left on his post i have tried.
with very little success if anything i have had to uninstall and reinstall ubuntu a couple of times.
I'm really not sure wat to do.

the sound itself does not work at all. the volume master tells me that nothing is muted

my lspci info is

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
02:0b.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:0b.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:0d.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)


and where is the digital to analogue?

well in any case thats the bulk of the info i no about my sound

and hopefully this extra info helps as well
$ lsmod | grep snd
snd_hda_intel 21912 1
snd_hda_codec 205056 1 snd_hda_intel
snd_pcm_oss 44544 0
snd_mixer_oss 17408 1 snd_pcm_oss
snd_pcm 79876 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy 4740 0
snd_seq_oss 32896 0
snd_seq_midi 9600 0
snd_rawmidi 25472 1 snd_seq_midi
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi
snd_seq 52592 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 23684 2 snd_pcm,snd_seq
snd_seq_device 9100 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
snd 54020 12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_ oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_ti mer,snd_seq_device
soundcore 8672 1 snd
snd_page_alloc 10888 2 snd_hda_intel,snd_pcm


i think its the snd_hda_intel
yet even with this info not sure wat to do

look guys im gonna hit the hay hoping for answers ill repost this tommorow

thanks for all the help u give to newcomers like myself

P.S. someone said

I have integrated intel sound, and there is a bug that affects these sound cards. Mine is intel ICH6.

The workaround is to set your master chanel to PCM, that way your master volume controll can will actually controll something. You can do this by right clicking the speaker icon on the gnome panel, and clicking on select master chanel.
__________________
-- I only bricked my box once this week!

how do u do this because i do not have a option that says select master chanel


plz if u no any other method plz do help
oh and for my beryl i do not no wats wrong if u tell me the code i must put in to extract the info u need to no about it tell me

thank you i wont check this until tonight

---

