---
title: "One lircd.conf for two remotes?"
date: 2008-06-27
forum: Mythbuntu
---

### Post by larsolav on 2008-06-27
I currently have a Mythbuntu machine with a Streamzap remote control. Recently got a new TV which includes a universal remote which can be programmed to emulate the media center pc remote and a hauppauge remote (at least the manual listed "media center pc" and hauppauge under Setup code for video accessories).

I guess I could change my remote settings in Mythbuntu to the windows remote or hauppauge and use only the universal remote, but I think that may confuse my user group slightly. 

Can I edit my current Streamzap lircd.conf ( [http://lirc.sourceforge.net/remotes/streamzap/lircd.conf.streamzap](http://lirc.sourceforge.net/remotes/streamzap/lircd.conf.streamzap)) to include the hauppauge information ( [http://lirc.sourceforge.net/remotes/hauppauge/lircd.conf.hauppauge.irman](http://lirc.sourceforge.net/remotes/hauppauge/lircd.conf.hauppauge.irman) ) so that my lircd.conf would look  like:

> begin remote

  name  Streamzap_PC_Remote
  bits            6
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           889  889
  zero          889  889
  plead         889
  pre_data_bits   8
  pre_data       0xA3
  gap          108344
  toggle_bit      2


      begin codes
          0                        0x00
          1                        0x01
          2                        0x02
          3                        0x03
          4                        0x04
          5                        0x05
          6                        0x06
          7                        0x07
          8                        0x08
          9                        0x09
          POWER                    0x0A
          MUTE                     0x0B
          CH_UP                    0x0C
          VOL_UP                   0x0D
          CH_DOWN                  0x0E
          VOL_DOWN                 0x0F
          UP                       0x10
          LEFT                     0x11
          OK                       0x12
          RIGHT                    0x13
          DOWN                     0x14
          MENU                     0x15
          EXIT                     0x16
          PLAY                     0x17
          PAUSE                    0x18
          STOP                     0x19
          |<<                      0x1A
          >>|                      0x1B
          RECORD                   0x1C
          <<                       0x1D
          >>                       0x1E
          RED                      0x20
          GREEN                    0x21
          YELLOW                   0x22
          BLUE                     0x23
      end codes

end remote

begin remote

  name  hauppauge
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0xFFFF
  post_data_bits  32
  post_data      0x0
  gap          213188
  min_repeat      8
  toggle_bit      0


      begin codes
          POWER                    0x0000000000002A80
          GO                       0x0000000000002AE0
          1                        0x0000000000002940
          2                        0x0000000000002970
          3                        0x0000000000002960
          4                        0x0000000000002910
          5                        0x0000000000002900
          6                        0x0000000000002930
          7                        0x0000000000002920
          8                        0x00000000000029D0
          9                        0x00000000000029C0
          EXIT                     0x00000000000028A0
          0                        0x0000000000002950
          MENU                     0x0000000000002980
          RED                      0x00000000000029E0
          GREEN                    0x0000000000002BB0
          YELLOW                   0x0000000000002AD0
          BLUE                     0x0000000000002BC0
          UP                       0x0000000000002B50
          DOWN                     0x0000000000002B40
          LEFT                     0x0000000000002840
          RIGHT                    0x0000000000002850
          OK                       0x0000000000002B00
          MUTE                     0x00000000000029A0
          _BLANK                   0x0000000000002990
          FULL                     0x0000000000002A90
          REW                      0x0000000000002A70
          PLAY                     0x0000000000002A00
          FWD                      0x0000000000002A10
          REC                      0x0000000000002A20
          STOP                     0x0000000000002A30
          PAUSE                    0x0000000000002A50
          REPLAY                   0x0000000000002B10
          SKIP                     0x00000000000028B0
      end codes

end remote

I may have to change FWD to >> etc to coordinate with the Streamzap info.

Would this work? I may try this after work today... Can it screw things up by doing this?

Thanks,

Lars

---

### Post by bah1976 on 2008-06-27
I've gone a slightly different method, based on what I found in my lircd.conf.  I had quite a time getting lirc to work for me - I tried with a non standard iR receiver first, so I don't know if my files are stock anymore.  That said, I don't use MCC to manage my remotes at all.  My /etc/lirc/lircd.conf looks like this:
```

#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb
include /usr/share/lirc/remotes/bruce/urc-1068.conf
include /usr/share/lirc/remotes/bruce/rs-15-1994.conf

```

And the 3 included files are a single remote config.  For you, you could have two of them.  The urc-1068 & rs-15-1994 remotes I had to train via irrecord.

I'm doing it this way for easy maintenance of a single remote - but I think you could put both begin/end remote sections in the same file - that's all that the "include" is doing.  Once you have it setup the way you want, use "irw" to make sure it's receiving the right commands.  Just run irw and then press buttons on the remote - it should echo which remote and what button you pushed.
After LIRC is receiving the signal correctly you'll have to add the corresponding sections to your myth setup so Myth knows what to do with the buttons.  Mine is in ~/.lirc/ in two files - "mythtv" and "mplayer".  If you run mythbuntu-lirc-generator, it'll make the files for you based on what I believe to be standard button configs.  In my case, I'm editing them manually to make sure they do exactly what i want them to.  Make sure you make copies of the existing files before you do anything - you're concern about messing things up is easily fixed by restoring your copies and restarting lirc (sudo /etc/init.d/lirc restart) and restarting the front-end (I think it reads the remote config files at startup)

---

### Post by larsolav on 2008-06-27
Thanks a bunch!
I will definetly try this evening!
Cheers

---

