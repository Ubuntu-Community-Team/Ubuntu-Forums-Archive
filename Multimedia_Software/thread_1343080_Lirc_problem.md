---
title: "Lirc problem"
date: 2009-12-01
forum: Multimedia Software
---

### Post by GuruMadMat on 2009-12-01
Hello,

I installed lirc and chose from the list my remote.
It is an Medion as seen [here]("http://www.vdr-wiki.de/wiki/images/a/a8/Fernbedienung_Medion_X10.jpg")

I got it working in irw, but some keys don't work.
I wanted to add them with irrecord so i used:
```

irrecord -H atilibusb test.conf

```

But after doing so nothing was changed in the file.
irrecord runs fine, no errors at all.

I'm on Ubuntu 8.10 with lircd 0.8.3pre1.
my current lirc config file:

```

begin remote
  name  medion
  bits           16
  eps            30
  aeps          100
  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          219967
  toggle_bit_mask 0x80800000

      begin codes
          1                        0xE20D
          2                        0x638E
          3                        0xE40F
          4                        0x6590
          5                        0xE611
          6                        0x6792
          7                        0xE813
          8                        0x6994
          9                        0xEA15
          0                        0x6C97
          Play                     0xFA25
          Pause                    0x7EA9
          Stop                     0xFD28
          Record                   0x7CA7
          SkipNext                 0xF823
          SkipPrior                0x76A1
          Forward                  0xFB26
          Rewind                   0x79A4
          snapshot                 0xED18
          red                      0x87B2
          yellow                   0x0934
          blue                     0x8AB5
          green                    0x0833
          Mute                     0x5580
          return                   0xF11C
          VolUp                    0x5E89
          VolDown                  0xDD08
          ChanUp                   0x608B
          ChanDown                 0xE10C
          menu                     0x6E99
          back                     0xF520
          Left                     0x729D
          Right                    0xF41F
          Up                       0xCDF8
          Down                     0x4570
          tv                       0x81AC
          Videos                   0x022D
          DVD                      0x5984
          Guide                    0xEB16
          Music                    0x5B86
          Radio                    0x032E
          book                     0x86B1
          Pictures                 0xDA05
          info                     0x84AF
          Power                    0xD702
          ok                       0x709B
          enter                    0xF31E
      end codes

end remote

```

The Up and Down buttons are defined but not working.

---

### Post by GuruMadMat on 2009-12-02
Solved, irrecord added .conf to config file!

---

