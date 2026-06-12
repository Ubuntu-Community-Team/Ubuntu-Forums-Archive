---
title: "lirc, Disable pressing power button on remote to shutdown computer."
date: 2009-08-15
forum: Multimedia Software
---

### Post by samcan on 2009-08-15
On my Ubuntu 9.04 box, I've been configuring MythTV, and I wanted to get the power button on my remote control to turn on Mythfrontend. Thus, I tried using the following for my .lircrc:

```

begin
    prog = irexec
    button = TurnOn
    config = mythfrontend &;
end

```

My /etc/lirc/lircd.conf looks like this:

```


begin remote
  name            PinnaclePCTV800i
  bits            16
  eps             30
  aeps            100
  one             0     0
  zero            0     0
  gap             135975
  pre_data_bits   16
  pre_data        0x8001

  begin codes
       TurnOn          0x0074
       Ok              0x001C
       VolumeUp        0x0073
       VolumeDown      0x0072
       Up              0x0192
       Down            0x0193
       Left            0x00A8
       Right           0x00D0
       Guide           0x016D
       Menu            0x0174
       Mute            0x0071
       Play            0x00A4
       Record          0x00A7
       Stop            0x0080
       1               0x0002
       2               0x0003
       3               0x0004
       4               0x0005
       5               0x0006
       6               0x0007
       7               0x0008
       8               0x0009
       9               0x000A
       0               0x000B
       Dot             0x0172
  end codes
end remote


```

From what it looks like, I believe it should work. However, whenever I press the power button (what TurnOn is assigned to), it pulls up GNOME's shutdown computer menu.

Is there anyway to disable GNOME's built-in lirc events, if that's even the problem? Thanks!

---

### Post by guyrichie@hotmail.com on 2011-12-04
Hello All,

Please see my reply within this thread:

[http://ubuntuforums.org/showthread.php?p=11512006#post11512006](http://ubuntuforums.org/showthread.php?p=11512006#post11512006) 

Cheers.

---

