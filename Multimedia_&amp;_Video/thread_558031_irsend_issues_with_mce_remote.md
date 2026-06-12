---
title: "irsend issues with mce remote"
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by tafkamk on 2007-09-23
Im currently using a mce remote with ubuntu no problem, however I've been trying to setup lirc to control the volume of my Harmon Kardon Receiver. I setup my lircd.conf with two devices one for my remote and one for my receiver. When testing with IRW everything appears as it should

$ irw
00000000010ee31c 00 vol+ AVR320
00000000010ee31c 01 vol+ AVR320
00000000010ee31c 02 vol+ AVR320
00000000010e13ec 00 vol- AVR320
00000000010ef906 00 off AVR320
00000000010e03fc 00 on AVR320
00000000010e03fc 01 on AVR320

however upon issuing "irsend SEND_START AVR320" on, my receiver does not turn off or on. My ir blaster extension from the mce receiver flashes and the red light on the mce receiver is on, so it seems to be trying to work. I've tried moving the ir blaster to pretty much every possible location on the front of the Harmon Kardon with no luck. Here is the Receiver portion of my lircd.conf, ive omitted the mceusb section as everything there is working ok.(can control amarok, vlc and others no problem).

begin remote

  name  AVR320
  bits           32
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       9140  4495
  one           594  1650
  zero          594   528
  ptrail        586
  repeat       9142  2211
  gap          108216
  toggle_bit      0


      begin codes
          on                       0x00000000010E03FC
          off                      0x00000000010EF906
          mute                     0x00000000010E837C
          avr                      0x00000000010E03FC
          dvd                      0x00000000010E0BF4
          cd                       0x00000000010E23DC
          tape                     0x00000000010E33CC
          vid1                     0x00000000010E53AC
          vid2                     0x00000000010ED32C
          vid3                     0x00000000010E738C
          vid4                     0x00000000010E8B74
          am/fm                    0x00000000010E817E
          6/8ch                    0x00000000414EDB24
          sleep                    0x00000000010EDB24
          surr                     0x00000000414E1AE5
          test                     0x00000000414E31CE
          night                    0x00000000414E6996
          mroom                    0x00000000414EFB04
          vol+                     0x00000000010EE31C
          vol-                     0x00000000010E13EC
          ch                       0x00000000414EBA45
          spkr                     0x00000000414ECA35
          digital                  0x00000000414E2AD5
          delay                    0x00000000414E4AB5
          ^                        0x00000000414E51AE
          v                        0x00000000414ED12E
          <                        0x00000000414E837C
          >                        0x00000000414E43BC
          set                      0x00000000414E21DE
          1                        0x00000000010EE11E
          2                        0x00000000010E11EE
          3                        0x00000000010E916E
          4                        0x00000000010E51AE
          5                        0x00000000010EC936
          6                        0x00000000010E31CE
          7                        0x00000000010EB14E
          8                        0x00000000010E718E
          9                        0x00000000010EB946
          0                        0x00000000010E7986
          tun-m                    0x00000000010EC936
          mem                      0x00000000010E619E
          tuning+                  0x00000000010E21DE
          tuning-                  0x00000000010EA15E
          direct                   0x00000000010ED926
          osd                      0x00000000414E3AC5
          clear                    0x00000000414E9B64
          d.skip                   0x00000000414EBB44
          preset+                  0x00000000414E0BF4
          preset-                  0x00000000414E8B74
          dolby                    0x00000000414E0AF5
          dts_surr                 0x00000000414E05FA
          dts_neo:6                0x00000000414E857A
          logic_7                  0x00000000414E45BA
          stereo                   0x00000000414ED926
      end codes

end remote


Any help would definitely be appreciated.

---

