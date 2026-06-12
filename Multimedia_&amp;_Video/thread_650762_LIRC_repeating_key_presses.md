---
title: "LIRC: repeating key presses"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by rich86 on 2007-12-26
Hi,
I have a MSI Mega Sky 580 usb DVBTV dongle that i have now manged to pretty much totally set up. I just have a few remote problems, all actions are repeated when using LIRC. Using irw it seems that when a button is pressed on the remote the signal is sent twice but i can't get LIRC to ignore the second one. Any ideas?
I have tried changing repeat and delay in the .lircrc file in my home directory but to no avail so far.

Here is irw outpu for one key presst:
richard@richards:~$ irw
0000000000010077 00 Play MSI
0000000000010077 00 Play MSI

I tried using evtest on the input and got this:
Event: time 1198713352.330956, type 1 (Key), code 119 (Pause), value 1
Event: time 1198713352.330961, type 1 (Key), code 119 (Pause), value 0
Event: time 1198713352.330962, type 0 (Reset), code 0 (Reset), value 0

So this confirms each time a key is pressed 2 pulses are sent.

Here is my lircd.conf:
```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.2(dev/input) on Wed Dec 26 22:12:22 2007
#
# contributed by 
#
# brand: MSI                       
# model no. of remote control: MegaSky 580
# devices being controlled by this remote:
#
#
#
#found using: sudo irrecord -H dev/input -d /dev/input/event4 -f file.conf
#
#Run prog using: sudo lircd -H dev/input -d /dev/input/event4
##gap 199979


begin remote

  name  MSI
  bits           16 
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x1
  gap          199979
  toggle_bit_mask 0x80000000

      begin codes
          Play		               0x0077
          FFWD	                   0x00D0
          Rewind                   0x00A8
          ChUp                     0x0192
          ChDown                   0x0193
          VolUp                    0x0073
          VolDown                   0x0072
          Mute                     0x0071
          Fullscreen               0x009A
          T-shift                  0x0160
          Stop                     0x0080
          Reload                   0x008B
          Record                   0x00A7
          Screenshot               0x00D4
          MTS                      0x0098
          Power                    0x0074
      end codes

end remote


```


 and .lircrc: (just the vlc bit for now)
```
begin
    remote = MSI
    prog = vlc
    button = Play
    config = key-play-pause
    repeat = 0
    delay = 0
end

begin
    remote = MSI
    prog = vlc
    button = Mute
    config = key-vol-mute
    repeat = 0
    delay = 0
end

begin
    remote = MSI
    prog = vlc
    button = Stop
    config = key-quit
    repeat = 0
    delay = 0
end

begin
    remote = MSI
    prog = vlc
    button = VolUp
    config = key-vol-up
    repeat = 0
    delay = 0
end

begin
    remote = MSI
    prog = vlc
    button = VolDown
    config = key-vol-down
    repeat = 0
    delay = 0
end

begin
    remote = MSI
    prog = vlc
    button = ChDown
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = MSI
    prog = vlc
    button = ChUp
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = MSI
    prog = vlc
    button = Rewind
    config = key-slower
    repeat = 0
    delay = 0
end

begin
    remote = MSI
    prog = vlc
    button = FFWD
    config = key-faster
    repeat = 0
    delay = 0
end

```

Thanks in advance

Richard

---

### Post by rich86 on 2007-12-28
Any ideas?? i have continued playing with different combinations but still to no avail.
Anyone else had the same problem? or know or a workaround?

---

### Post by AusIV4 on 2007-12-28
Higher values in the "repeat" variable means it will take longer for a button to repeat. I used to have everything set to 1, and it took forever to navigate through a menu because it would jump two or three items at a time. Now I have everything set to 10, so I have to hold down the button for close to a second before it repeats.

---

### Post by rich86 on 2007-12-28
Thanks for the reply i tried varying the repeat variable but it doesn't seem to have any affect (i am restarting lirc after each time!) i think the problem is more than that as the remote transmits a double pulse.

---

