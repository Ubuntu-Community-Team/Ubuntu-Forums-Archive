---
title: "Ibex: Mixman dm2"
date: 2008-11-16
forum: Multimedia Software
---

### Post by guggi on 2008-11-16
successfully compiled the driver!
```
$ modinfo dm2
filename:       /lib/modules/2.6.27-7-generic/kernel/sound/drivers/dm2.ko
license:        GPL
srcversion:     01D00948C6266BF88C11FAA
alias:          usb:v0665p0301d*dc*dsc*dp*ic*isc*ip*
depends:        usbcore,snd-rawmidi,snd
vermagic:       2.6.27-7-generic SMP mod_unload modversions 
parm:           index:Index value for DM2 MIDI controller. (int)
parm:           id:ID string for DM2 MIDI controller. (charp)

```

but when i try to modrobe the module dmesg spits the following:
```
[CFATAL: Error inserting dm2 (/lib/modules/2.6.27-7-generic/kernel/sound/drivers/dm2.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
```
dmesg
[ 9609.799212] dm2: disagrees about version of symbol snd_rawmidi_receive
[ 9609.799224] dm2: Unknown symbol snd_rawmidi_receive
[ 9609.799393] dm2: disagrees about version of symbol snd_card_register
[ 9609.799395] dm2: Unknown symbol snd_card_register
[ 9609.799478] dm2: disagrees about version of symbol snd_card_free
[ 9609.799480] dm2: Unknown symbol snd_card_free
[ 9609.799794] dm2: disagrees about version of symbol snd_rawmidi_transmit_ack
[ 9609.799797] dm2: Unknown symbol snd_rawmidi_transmit_ack
[ 9609.800151] dm2: disagrees about version of symbol snd_card_new
[ 9609.800154] dm2: Unknown symbol snd_card_new
[ 9609.800261] dm2: disagrees about version of symbol snd_rawmidi_transmit_peek
[ 9609.800263] dm2: Unknown symbol snd_rawmidi_transmit_peek
[ 9609.800451] dm2: disagrees about version of symbol snd_rawmidi_new
[ 9609.800453] dm2: Unknown symbol snd_rawmidi_new
[ 9609.800530] dm2: disagrees about version of symbol snd_rawmidi_set_ops
[ 9609.800532] dm2: Unknown symbol snd_rawmidi_set_ops

```
any help would be appreciated!

cheers guggi

---

