---
title: "Problems with VLC and lirc"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by DjBeck on 2007-05-30
Hi there.

I'm trying to get the remote for my Hauppauge tv card up and running, and it seems that it's somewhat working.

When i start the daemon,
```

sudo /etc/init.d/lirc start
irw

```

I get the following output when i press any of the buttons:
```

00000000000017b5 00 Play Hauppauge_350
0000000000001791 00 Vol- Hauppauge_350
0000000000001790 00 Vol+ Hauppauge_350
0000000000001791 00 Vol- Hauppauge_350
...

```
Wouldn't this be a sign that the lirc module is operating correctly?

I've checked the 'Infrared remote control interface' option in the VLC settings. The problem's that VLC won't respond to any of the commands from the remote.

This is my ~/.lircrc
```

begin
 prog = vlc
 button = play
 config = key-play
end
begin
 prog = vlc
 button = pause
 config = key-pause
end
begin
 prog = vlc
 button = stop
 config = key-stop
end

```

and this is what my /etc/lirc/lircd.conf looks like:
```

#
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Nov 28 20:25:09 2004
#
# contributed by 
#
# brand:   Hauppauge 350
# Created: G.J. Werler (The Netherlands)
# Project: Mythtv Fedora Pundit-R www.mythtvportal.com
# Date:    2004/11/28
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
#

begin remote

  name  Hauppauge_350
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remote


```

Why isn't this working? What have I missed? 

Very thankful for any ideas or suggestions.

Regards,

---

### Post by DjBeck on 2007-05-30
> **DjBeck said:**
> Hi there.

I'm trying to get the remote for my Hauppauge tv card up and running, and it seems that it's somewhat working.

When i start the daemon,
```

sudo /etc/init.d/lirc start
irw

```

I get the following output when i press any of the buttons:
```

00000000000017b5 00 Play Hauppauge_350
0000000000001791 00 Vol- Hauppauge_350
0000000000001790 00 Vol+ Hauppauge_350
0000000000001791 00 Vol- Hauppauge_350
...

```
Wouldn't this be a sign that the lirc module is operating correctly?

I've checked the 'Infrared remote control interface' option in the VLC settings. The problem's that VLC won't respond to any of the commands from the remote.

This is my ~/.lircrc
```

begin
 prog = vlc
 button = play
 config = key-play
end
begin
 prog = vlc
 button = pause
 config = key-pause
end
begin
 prog = vlc
 button = stop
 config = key-stop
end

```

and this is what my /etc/lirc/lircd.conf looks like:
```

#
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Nov 28 20:25:09 2004
#
# contributed by 
#
# brand:   Hauppauge 350
# Created: G.J. Werler (The Netherlands)
# Project: Mythtv Fedora Pundit-R www.mythtvportal.com
# Date:    2004/11/28
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
#

begin remote

  name  Hauppauge_350
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remote


```

Why isn't this working? What have I missed? 

Very thankful for any ideas or suggestions.

Regards,


EDIT:

**Problem solved. I forgot to start VLC with the lirc interface :)**

```

vlc -I lirc

```

---

### Post by mael on 2007-11-04
thanks, i had the same problem :D

---

