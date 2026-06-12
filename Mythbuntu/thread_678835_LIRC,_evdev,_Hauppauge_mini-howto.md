---
title: "LIRC, evdev, Hauppauge mini-howto"
date: 2008-01-26
forum: Mythbuntu
---

### Post by stdPikachu on 2008-01-26
Not sure how many people this will help, but I've been finding inbuilt Mythbuntu's LIRC support somewhat lacking so thought I would add a mini-howto for configuring a remote using the evdev driver (known as dev/input to LIRC). IIRC the evdev kernel module is always loaded by default in Ubuntu and variants, as it's the standard interface for the kernel to talk to input hardware. I've always found it more reliable and flexible than any other method, YMMV of course!

Hardware here is a Hauppauge Nova-T DVB-T card with the grey remote but the basic rules should be applicable to any remote that works under evdev.

First step is to determine which is your IR device, easiest way to do this is via the dev tree:
```
banquo@banquo:~$ ls -lah /dev/input/by-path/
total 0
drwxr-xr-x 2 root root 140 2008-01-26 14:51 .
drwxr-xr-x 4 root root 280 2008-01-26 14:51 ..
lrwxrwxrwx 1 root root   9 2008-01-26 14:51 pci-0000:00:0b.0-usb-0:3:1.0-event-kbd -> ../event1
lrwxrwxrwx 1 root root   9 2008-01-26 14:51 pci-0000:00:0b.0-usb-0:3:1.1-event-mouse -> ../event2
lrwxrwxrwx 1 root root   9 2008-01-26 14:51 pci-0000:00:0b.0-usb-0:3:1.1-mouse -> ../mouse1
lrwxrwxrwx 1 root root   9 2008-01-26 14:51 pci-0000:04:09.0--event-ir -> ../event4
lrwxrwxrwx 1 root root   9 2008-01-26 14:51 platform-pcspkr-event-spkr -> ../event3
```
NB: the Nova-T has an inbuilt IR sensor so it's visible on the PCI bus. Those of you with USB or serial connections I'm not sure about as I've never used hardware like that via LIRC, so there's a possibility you won't have an evdev/input device node you can use.
udev is kind enough to class one of these nodes as --event-ir and points it at /dev/input/event4, so now we have a device node to point irrecord at. We're now ready to run irrecord to generate our lircd config file. You'll need to twizzle the options to suit your setup but the general command line will look like this:
```
sudo irrecord -d /dev/input/event4 -H dev/input lirc.out
```
Ensure that LIRC isn't running. The -H option is essential otherwise irrecord will grumble that eventX isn't and LIRC device node. Run that command and the wizard will start; that bit is fairly self explanatory - you type in what you want a particular button to be called, you hold down the button and that's pretty much it. Hit enter to stop recording once you've gone through all your buttons and you could end up with a file like this (note that I've edited the remote name to hauppauge_nova_t):
```
banquo@banquo:~$ cat lirc.out

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.2(dev/input) on Sat Jan 26 15:37:11 2008
#
# contributed by
#
# brand:                       lirc.out
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name  hauppauge_nova_t
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          135990
  toggle_bit_mask 0x800100CF

      begin codes
          go                       0x0161
          power                    0x0074
          tv                       0x0179
          videos                   0x0189
          music                    0x0188
          pictures                 0x016F
          guide                    0x016D
          radio                    0x0181
          ok                       0x001C
          up                       0x0067
          down                     0x006C
          left                     0x0069
          right                    0x006A
          back                     0x00AE
          menu                     0x008B
          vol+                     0x0073
          vol-                     0x0072
          ch+                      0x0192
          ch-                      0x0193
          prev                     0x019C
          mute                     0x0071
          record                   0x00A7
          stop                     0x0080
          rew                      0x00A8
          ffw                      0x00D0
          play                     0x00CF
          pause                    0x0077
          skipback                 0x00A5
          skipfwd                  0x00A3
          1                        0x0002
          2                        0x0003
          3                        0x0004
          4                        0x0005
          5                        0x0006
          6                        0x0007
          7                        0x0008
          8                        0x0009
          9                        0x000A
          0                        0x000B
          star                     0x0184
          hash                     0x0172
          red                      0x018E
          green                    0x018F
          yellow                   0x0190
          blue                     0x0191
      end codes

end remote
```
This will be the replacement for /etc/lirc/lircd.conf.
```
sudo cp /etc/lirc/lircd.conf /etc/lirc/lircd.conf.deprecated && sudo cp lirc.out /etc/lirc/lircd.conf
```
Now we just need to tweak the hardware.conf with these lines:
```
/etc/lirc/hardware.conf
DRIVER="dev/input"
DEVICE="/dev/input/event4"
```
It's always a good idea to comment out the old DRIVER and DEVICE lines rather than delete or edit them so it's easy to roll back to a previous config if need be.

Once that's done, we need to edit the Mythbuntu-provided .lircrc file to use the new button names we defined when we made our remote. Cleverer people than me would have used the same names but I have a penchant for keeping things in config files all lower case :)
Tip: if you're a vim user, you can use a command like:
:%s/hauppauge_pvr/hauppauge_nova_t/g
to do a search'n'replace within the file
Edit: just posted my completed .lircrc configured for my remote (watch out for C&P errors!), using myth and xine only (mPlayer = ARGH IMHO :)). If you need a dump of every key/event xine supports, do a `xine --keymap lirc > xine_keymap` and look in that file for every keypress xine has, nicely .lircrc formatted, and just use the events it gives in your lircrc. If you're lazy you can just `xine --keymap lirc >> ~/.lircrc` and fill in the xxxx values yourself.
```
.lircrc
begin
        remote = hauppauge_nova_t
        prog = mythtv
        button = go
        config =
        repeat = 1
        delay = 0
end

begin
        remote = hauppauge_nova_t
        prog = mythtv
        button = power
        config =
        repeat = 1
        delay = 0
end

begin
        remote = hauppauge_nova_t
        prog = mythtv
        button = tv
        config = @
        repeat = 1
        delay = 0
end

begin
        remote = hauppauge_nova_t
        prog = mythtv
        button = videos
        config = *
        repeat = 1
        delay = 0
end

begin
        remote = hauppauge_nova_t
        prog = mythtv
        button = music
        config = &
        repeat = 1
        delay = 0
end

begin
        remote = hauppauge_nova_t
        prog = mythtv
        button = pictures
        config =
        repeat = 1
        delay = 0
end

begin
        remote = hauppauge_nova_t
        prog = mythtv
        button = guide
        config =
        repeat = 1
        delay = 0
end

begin
        remote = hauppauge_nova_t
        prog = mythtv
        button = radio
        config = £
        repeat = 1
        delay = 0
end

begin
        remote = hauppauge_nova_t
        prog = mythtv
        button = up
        config = Up
        repeat = 1
        delay = 0
end

begin
        remote = hauppauge_nova_t
        prog = mythtv
        button = down
        config = Down
        repeat = 1
        delay = 0
end

begin
        remote = hauppauge_nova_t
        prog = mythtv
        button = left
        config = Left
        repeat = 1
        delay = 0
end

begin
        remote = hauppauge_nova_t
        prog = mythtv
        button = right
        config = Right
        repeat = 1
        delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = ok
    config = Return
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = back
    config = Escape
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = menu
    config = M
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = vol+
    config = ]
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = vol-
    config = [
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = prev
    config = Z
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = mute
    config = |
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = ch+
    config = +
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = ch-
    config = -
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = record
    config = R
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = stop
    config = O
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = play
    config = P
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = pause
    config = P
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = rew
    config = <
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = ffw
    config = >
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = skipback
    config = PgDown
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = skipfwd
    config = PgUp
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 1
    config = 1
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 2
    config = 2
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 3
    config = 3
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 4
    config = 4
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 5
    config = 5
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 6
    config = 6
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 7
    config = 7
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 8
    config = 8
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 9
    config = 9
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = star
    config =
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = hash
    config =
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = red
    config = F2
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = green
    config = F3
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = yellow
    config = F4
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = blue
    config = F5
    repeat = 1
    delay = 0
end


begin
    remote = hauppauge_nova_t
    prog = xine
    button = go
    config = Eject
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = tv
    config =
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = videos
    config = AddMediaMark
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = music
    config =
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = pictures
    config = Snapshot
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = guide
    config =
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = radio
    config =
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = up
    config = EventUp
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = down
    config = EventDown
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = left
    config = EventLeft
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = right
    config = EventRight
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = ok
    config = EventSelect
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = back
    config = Quit
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = menu
    config =
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = vol+
    config = Volume+
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = vol-
    config = Volume-
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = ch+
    config = EventNext
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = ch-
    config = EventPrior
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = prev
    config =
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = mute
    config = Mute
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = record
    config =
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = stop
    config = Stop
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = rew
    config = SeekRelative-15
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = ffw
    config = SeekRelative+15
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = skipback
    config = SeekRelative-60
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = skipfwd
    config = SeekRelative+60
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = play
    config = Play
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = pause
    config = Pause
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = 1
    config = SetPosition10%
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = 2
    config = SetPosition20%
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = 3
    config = SetPosition30%
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = 4
    config = SetPosition40%
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = 5
    config = SetPosition50%
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = 6
    config = SetPosition60%
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = 7
    config = SetPosition70%
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = 8
    config = SetPosition80%
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = 9
    config = SetPosition90%
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = 0
    config = SetPosition0%
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = star
    config =
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = hash
    config =
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = red
    config = AudioChannelPrior
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = green
    config = AudioChannelNext
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = yellow
    config = SpuPrior
    repeat = 1
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = blue
    config = SpuNext
    repeat = 1
    delay = 0
end
```
For the sake of simplicity I've only put in entries pertienent to my remote and MythTV. For those of you unfamiliar with lircrc syntax:
"remote" corresponds with the remote named in your lircd.conf config file
"prog" is the the name of the program that wil receive the events
"button" is one of the buttons named in your lircd.conf config
"config" is the name of the event that will be sent to the program defined in "prog"
"repeat" is the amount of time you keep the button held down before it registers a repeat keypress - if your remote seems too sensitive try setting delay to 1 or 2. I don't like the default of repeat set to zero because that way repeat button presses aren't registered at all - annoying if you want to skip through a video by holding down the ffwd button
"delay" is the amount of time between lirc registering a repeat keypress. For example, a delay of "1" will ignore every other keypress for the purposes of detecting repeats
As you're probably aware, it's possible to set up different configs for any program. If you have a play with mythcontrols, you can add your own button entries for setting up things like shortcuts to the video menu (which I set up as F4) for instance:
```
begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = videos
    config = F4
    repeat = 0
    delay = 0
end
```

Once that's all done, restart LIRC and mythfrontend and you should be good to go. You can test the new config is working by running irw and pressing a few buttons (Ctrl-C to exit);
```
banquo@banquo:~$ irw
0000000080010067 00 up hauppauge_nova_t
000000008001006c 00 down hauppauge_nova_t
0000000080010069 00 left hauppauge_nova_t
000000008001006a 00 right hauppauge_nova_t
000000008001001c 00 ok hauppauge_nova_t
00000000800100ae 00 back hauppauge_nova_t
000000008001008b 00 menu hauppauge_nova_t
^C
```

If you have multiple frontends you can copy the same .lircrc file to each machine and edit to your hearts content; don't forget to change the names of the remote you're using to match your lircd.conf! This has the advantage that you can keep the configs the same throughout your house (assuming you can keep the database changes to your input in sync, but that's another thread ;)) and thus the controls will remain the same.

Caveats: I've not done enough testing yet to see whether the device node for the IR remote is likely to change on reboot - if it does all that's required is a custom udev rule to either keep the device node static or (better still) create a symlink to it. Will post that with instructions when I get around to it :)

Edit: Meh, here we go anyway. You can grab udev attributes using the udevinfo tool in conjunction with your input device node:
```
banquo@banquo:~$ udevinfo -a -p $(udevinfo -q path -n /dev/input/event4)

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/class/input/input4/event4':
    KERNEL=="event4"
    SUBSYSTEM=="input"
    DRIVER==""
    ATTR{dev}=="13:68"

  looking at parent device '/class/input/input4':
    KERNELS=="input4"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{modalias}=="input:b0001v0070p9002e0001-e0,1,14,k71,72,73,74,77,80,8B,8E,A3,A5,A7,A8,AE,CF,D0,161,16B,16D,16F,172,174,179,181,184,188,189,18E,18F,190,191,192,193,19C,ramlsfw"
    ATTRS{uniq}==""
    ATTRS{phys}=="pci-0000:04:09.0/ir0"
    ATTRS{name}=="cx88 IR _Hauppauge Nova-T DVB-T"

  looking at parent device '/devices/pci0000:00/0000:00:10.0/0000:04:09.0':
    KERNELS=="0000:04:09.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="cx8800"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{modalias}=="pci:v000014F1d00008800sv00000070sd00009002bc04sc00i00"
    ATTRS{local_cpus}=="ff"
    ATTRS{irq}=="22"
    ATTRS{class}=="0x040000"
    ATTRS{subsystem_device}=="0x9002"
    ATTRS{subsystem_vendor}=="0x0070"
    ATTRS{device}=="0x8800"
    ATTRS{vendor}=="0x14f1"

  looking at parent device '/devices/pci0000:00/0000:00:10.0':
    KERNELS=="0000:00:10.0"
    SUBSYSTEMS=="pci"
    DRIVERS==""
    ATTRS{msi_bus}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{modalias}=="pci:v000010DEd0000026Fsv00000000sd00000000bc06sc04i01"
    ATTRS{local_cpus}=="ff"
    ATTRS{irq}=="0"
    ATTRS{class}=="0x060401"
    ATTRS{subsystem_device}=="0x0000"
    ATTRS{subsystem_vendor}=="0x0000"
    ATTRS{device}=="0x026f"
    ATTRS{vendor}=="0x10de"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""
```
It all looks very confusing; just bear in mind we're looking for an attribute that's going to remain unique for the IR receiver throughout hardware changes - attributes with names or vendor ID's are the best, whereas things like PCI ID's are subject to change. With that in mind, ATTRS{name}=="cx88 IR _Hauppauge Nova-T DVB-T" looks like the best option - this is the name of the parent device (which is still part of the input subsystem - don't use a name further up the device tree than the event subsystem as you'll no longer be pointed at the node for your IR receiver) and should be the same for any Hauppauge Nova-T device (although this can change depending on the card revision). Once we have this creating the rule is pretty simple. I can't find any docs on where custom rules should live in Ubuntu, so I'm going with my usual default of /etc/udev/rules.d/25-custom.rules:
```
ATTRS{name}=="cx88 IR (Hauppauge Nova-T DVB-T", SYMLINK+="input/hauppauge_nova_t input/dvb_remote"
```
That rule basically says "look for the device with this name and then create two additional symlinks in /dev named input/name1 and input/name2". Once you've written the file, run "sudo udevtrigger" to reload udev and the new symlinks should be created.
```
banquo@banquo:~$ ls -l /dev/input/
total 0
drwxr-xr-x 2 root root    100 2008-01-26 14:51 by-id
drwxr-xr-x 2 root root    140 2008-01-26 14:51 by-path
lrwxrwxrwx 1 root root      6 2008-01-26 17:36 dvb_remote -> event4
crw-rw---- 1 root root 13, 64 2008-01-26 14:51 event0
crw-rw---- 1 root root 13, 65 2008-01-26 14:51 event1
crw-rw---- 1 root root 13, 66 2008-01-26 14:51 event2
crw-rw---- 1 root root 13, 67 2008-01-26 14:51 event3
crw-rw---- 1 root root 13, 68 2008-01-26 14:51 event4
crw-rw---- 1 root root 13, 69 2008-01-26 14:51 event5
crw-rw---- 1 root root 13, 70 2008-01-26 14:51 event6
lrwxrwxrwx 1 root root      6 2008-01-26 17:38 hauppauge_nova_t -> event4
crw-rw---- 1 root root 13, 63 2008-01-26 14:51 mice
crw-rw---- 1 root root 13, 32 2008-01-26 14:51 mouse0
crw-rw---- 1 root root 13, 33 2008-01-26 14:51 mouse1
```
This will give you a more reliable device node to use in your lircd.conf:
```
DEVICE="/dev/input/dvb_remote"
```

Note that I've run into a udev bug here where the naming convention of certain characters is mis-reported by udevinfo, notice the brackets (which udevinfo represented as underscores) so if your rule doesn't seem to be working try changing _ for (. You can find the exact value udev "sees" by looking in sys; using the above example:
```
banquo@banquo:$ cat /sys/class/input/input4/name
cx88 IR (Hauppauge Nova-T DVB-T
```
Come to think of it that's a much faster and easier way to grab the name attribute than udevinfo :)

One minor gotcha I ran into, no idea how it happened, was that something had removed the symlink from ~/.mythtv/lircrc to ~/.lircrc so that Myth was running from a different LIRC config to everyone else.
```
banquo@banquo:~/.mythtv$ ls -l
total 48
-rw-r--r-- 1 banquo banquo     0 2008-01-25 11:52 backend_configured
-rw-r--r-- 1 banquo banquo 11912 2008-01-26 15:22 lircrc
-rw-r--r-- 1 banquo banquo 11912 2008-01-26 15:21 lircrc.mythbuntu-old
-rw-r--r-- 1 banquo banquo 11912 2008-01-26 15:04 lircrc.old
drwxr-xr-x 4 banquo banquo  4096 2008-01-25 11:54 MythPhone
drwxr-xr-x 2 banquo banquo  4096 2008-01-25 12:51 osdcache
drwxr-xr-x 3 banquo banquo  4096 2008-01-25 11:55 themecache
```
Recreating the original symlink is easy:
```
banquo@banquo:~$ cd .mythtv/
banquo@banquo:~/.mythtv$ rm lircrc
banquo@banquo:~/.mythtv$ ln -s ../.lircrc lircrc
banquo@banquo:~/.mythtv$ ls -l
total 36
-rw-r--r-- 1 banquo banquo     0 2008-01-25 11:52 backend_configured
lrwxrwxrwx 1 banquo banquo    10 2008-01-26 16:51 lircrc -> ../.lircrc
-rw-r--r-- 1 banquo banquo 11912 2008-01-26 15:21 lircrc.mythbuntu-old
-rw-r--r-- 1 banquo banquo 11912 2008-01-26 15:04 lircrc.old
drwxr-xr-x 4 banquo banquo  4096 2008-01-25 11:54 MythPhone
drwxr-xr-x 2 banquo banquo  4096 2008-01-25 12:51 osdcache
drwxr-xr-x 3 banquo banquo  4096 2008-01-25 11:55 themecache
```
Further caveats: I accept no responsibility if these changes to your system b0rk your myth setup, turn your dog into an ornamental tea urn or burn down your house - just because it hasn't happened before doesn't mean it can't ;) As ever, make sure you have a fair idea what you're doing before you run any commands from the net, especially ones with "sudo" in them!

Hope someone finds that all useful!

Edit again:
Crikey, must be the fifty billionth edit. Nothing really do to with the subject, was just a little put out that Mythbuntu didn't come with the superb MythTVMediaCentre OSD theme by default. To install it just run the following:
```
wget http://files.radixpub.com/MythTVMediaCenterOSD.0.20.tar.bz2
tar xvfj MythTVMediaCenter.OSD.0.20.tar.bz2
sudo cp -r MythTVMediaCenterOSD/ /usr/share/mythtv/themes/
```
This ISD theme should now be available to you under mythfrontend; if you're using the default menu setup: Utilities/Setup > Setup > TV Settings > Playback > Next x8 > OSD theme: MythTVMediaCentreOSD. It really benefits from setting the OSD font (on the same screen) to FreeSans.

For the record, been using Myth under Gentoo for about 5 years now but have jumped ship to Ubuntu after I got fed up of things breaking all the time, and am going through my Mythbuntu install to try and get everything "just so" :). Happy configuring!

---

### Post by superm1 on 2008-01-26
FWIW:

There are some modest improvements to evdev handling in Hardy.

Here's some screenshots:
[http://mythbuntu.org/image/tid/8](http://mythbuntu.org/image/tid/8)

---

### Post by stdPikachu on 2008-01-26
Heh, typical :D I hadn't seen those, nice to see that LIRC configuration is being worked on. Would be nice if a) a GUI configurator could be done (Python frontend for irrecord?) and if Myth had slightly saner keybinding configuration... wish it supported config files or at least SQLite for local settings.

Thanks for the info anyhow :)

---

### Post by superm1 on 2008-01-26
> **stdPikachu said:**
> Heh, typical :D I hadn't seen those, nice to see that LIRC configuration is being worked on. Would be nice if a) a GUI configurator could be done (Python frontend for irrecord?) and if Myth had slightly saner keybinding configuration... wish it supported config files or at least SQLite for local settings.

Thanks for the info anyhow :)
Well something else that we've changed for Hardy (in the direction of a GUI configurator) is "include" support in your lircrc's.  This will mean that the myth lircrc is stored in ~/.lirc/mythtv and the xine one is ~/.lirc/xine.  This should make it a bit easier to customize an apps buttons (and will make it easier to read the currently set settings too).

---

### Post by stdPikachu on 2008-01-27
Include support is definitely a good idea, one of the things that made me want to roll my own was support for all the apps (most of which I don't use) bundled in there which cluttered things up immensely. Is this an upstream change or are you maintaining your own patchsets to LIRC?

Another thing I'd love to add to my wishlist would be to make edits to the Myth keymaps available globally (perhaps a copy-config-to-all-hostnames/make-config-global option in mythcontrols?); do you know if there's anything like this in the works? At the moment I just do it manually via MySQL which is a bit of a PITA.

Anyway, now that I've got almost everything set up dunky-hory, I'd like to extend a big thanks to the Mythbuntu devs, it's certainly a helluva lot less work than Gentoo :D

---

### Post by agnesdavies on 2008-01-27
stdPikachu's post has been a great help to me in understanding the LIRC subsystem and finally getting to the point where I can fire up irw, prod keys on my remote, and get the right answers back!

However (there's always a "however" :) ), I'm no further towards getting mythfrontend to recognise most keystrokes.

What is very strange is that a number of the remote's keystrokes do seem to work - rather better than they should, as hitting the number keys in the remote will produce keystrokes even in terminal shells, OK produces an enter, but that's it. This seems to prevail in mythfrontend, too, with the result that I can select the menu entry I'm on, and bash channel numbers, but that's it.

The girls are getting impatient to use the remote, and I don't much like having a keyboard attached anyway, because the Small One keeps firing up terminal sessions and experimenting in the shell, which is something of a hassle!

I've symlinked the .lircrc in .mythtv to the one in my user home directory, to no avail. And, significantly, having just put in a stanza to the .lircrc to run a script to shut the monitor down when I press the Power button,  that doesn't work either, and yes I've restarted the lircd daemon!

Help!

---

### Post by stdPikachu on 2008-01-27
Edit: doh, actually read your post this time, you have checked with irw.

Can you post your /etc/lirc/lircd.conf and ~/.lircrc?

As an aside, if you have far too much money the Logitech DiNovo Edge is superb for HTPC use, much better than any other wireless keyboard I've used.

IIRC getting buttons on the remote to do exotic things like shut off the monitor (i.e. accessing programs that don't have LIRC support) you need to use irexec; not actually used it myself yet but I'll have a stab at it soon (looking to use the remote "power" button to suspend the machine).

---

### Post by agnesdavies on 2008-01-27
/etc/lirc/hardware.conf
> # /etc/lirc/hardware.conf
#
#Chosen Remote Control
#REMOTE="Hauppauge DVB-s card (ver. 2.1)"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/input/event3"
#MODULES="lirc_dev"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lircd/lircd.conf"
LIRCMD_CONF=""


/etc/lirc/lircd.conf
```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.2(dev/input) on Sun Jan 27 18:43:37 2008
#
# contributed by 
#
# brand:                       lirc.out
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  hauppauge_nova_t
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          135989
  toggle_bit_mask 0x80010002

      begin codes
          Power                    0x0074
          Go                       0x0161
          1                        0x0002
          2                        0x0003
          3                        0x0004
          4                        0x0005
          5                        0x0006
          6                        0x0007
          7                        0x0008
          8                        0x0009
          9                        0x000A
          0                        0x000B
          BackExit                 0x00AE
          Menu                     0x008B
          Red                      0x018E
          Green                    0x018F
          Yellow                   0x0190
          Blue                     0x0191
          ChannelUp                0x0192
          ChannelDn                0x0193
          VolumeUp                 0x0073
          VolumeDn                 0x0072
          OK                       0x001C
          Mute                     0x0071
          Middle                   0x0181
          Full                     0x0174
          Rewind                   0x00A8
          Play                     0x00CF
          FFwd                     0x00D0
          Record                   0x00A7
          Stop                     0x0080
          Pause                    0x0077
          Replay                   0x00A5
          Skip                     0x00A3
      end codes

end remote


```

~/.lircrc (linked to ~/.mythtv/.lircrc)
```
# Power Button
begin
	remote = hauppauge_nova_t
	prog = irexec
	button = Power
	repeat = 4
	config = /usr/local/bin/monitorpowerbutton.sh
end


begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = VolumeUp
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = Middle
    config = C
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = Replay
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = ChannelDn
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = ChannelDn
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = BackExit
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = ChannelUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = FFwd
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = VolumeDn
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = VolumeUp
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = ChannelUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = Menu
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = VolumeDn
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mplayer
    button = Play
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mplayer
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mplayer
    button = OK
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mplayer
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mplayer
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mplayer
    button = VolumeDn
    config = volume -1
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mplayer
    button = SkipBack
    config = seek +15 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mplayer
    button = Stop
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mplayer
    button = ChannelUp
    config = seek +60 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mplayer
    button = VolumeUp
    config = volume +1
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mplayer
    button = ChannelDn
    config = seek -60 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mplayer
    button = VolumeUp
    config = seek +6 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mplayer
    button = Rewind
    config = seek -30 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mplayer
    button = FFwd
    config = seek +30 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = mplayer
    button = VolumeDn
    config = seek -6 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = Play
    config = Play
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = Pause
    config = Pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = OK
    config = EventSelect
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = Mute
    config = Mute
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = VolumeDn
    config = Volume-
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = SkipBack
    config = EventNext
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = Stop
    config = Quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = ChannelUp
    config = EventUp
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = VolumeUp
    config = Volume+
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = ChannelDn
    config = EventDown
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = VolumeUp
    config = EventRight
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = Rewind
    config = SeekRelative-15
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = FFwd
    config = SeekRelative+15
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = xine
    button = VolumeDn
    config = EventLeft
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = ChannelDn
    config = key-nav-down
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = Play
    config = key-play
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = Pause
    config = key-pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = OK
    config = key-nav-activate
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = Mute
    config = key-vol-mute
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = VolumeDn
    config = key-vol-down
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = Stop
    config = key-quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = ChannelUp
    config = key-nav-up
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = VolumeUp
    config = key-vol-up
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = ChannelDn
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = VolumeUp
    config = key-nav-right
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = SkipBack
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = ChannelUp
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = Rewind
    config = key-slower
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = FFwd
    config = key-faster
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_nova_t
    prog = vlc
    button = VolumeDn
    config = key-nav-left
    repeat = 0
    delay = 0
end


```

---

### Post by stdPikachu on 2008-01-27
Do you know which events aren't working?

Is lircd definitely running? My initial problem was that LIRC was dying (I think because /dev/lirc0 or whatever wasn't being created) as soon as mythfrontend started in the default config;
```
banquo@banquo:~$ ps aux | grep lirc
root      5519  0.0  0.0   2920   548 ?        Ss   17:31   0:00 /usr/sbin/lircd --driver=dev/input --device=/dev/input/dvb_remote
banquo   21709  0.0  0.0   2976   764 pts/1    R+   21:15   0:00 grep lirc
```
Even when it wasn't running, some remote events appeared to cause things to work in mythfrontend; mainly, I think, because some events register as standard keyboard input.

As an aside, some of your myth events are non-standard (for example, in the default config volume up/down is mapped to [/]) - I take it you're aware of this? You can check all of your current button mappings in mythcontrols or mythweb (settings > mythtv key bindings > select host > set host).

---

### Post by agnesdavies on 2008-01-27
I'll have a look at mythcontrols/mythweb and see what they say, though this was an out-of-the-box mythbuntu install, and I can't believe I've randomly fiddled enough to b0rk it to that extent!!

But I'll follow up on those comments you've made about non-standard events/keystrokes.

lircd is running - I've checked it via ps. I did have a lot of problems testing that in the beginning because it insisted everything was /dev/lirc0 and the server crashed every time I tried to connect to that port. I fixed that by switching over to the dev/event thing.

And I'm assuming that irw wouldn't work if lircd wasn't going?

Forgive me if I sound confused, trying to make sense of this is causing my brain to trickle out of my ears - I mean, just as an example, what is the mechanism that is causing the button presses on the remote to appear as keystrokes? I'm pretty sure that ps -ef|grep ircmd doesn't yield anything...!

---

### Post by stdPikachu on 2008-01-27
> **agnesdavies said:**
> I'll have a look at mythcontrols/mythweb and see what they say, though this was an out-of-the-box mythbuntu install, and I can't believe I've randomly fiddled enough to b0rk it to that extent!!

I think the problem is that it's very difficult for mythbuntu to figure out exactly which remote you have and ocnfigure accordingly; there are a zillion possible configurations and if you have an edited setup it only gets worse, and you reach the stage where you eventually either need to know exactly what  you're doing, or start from scratch ;) I'd like to see a nice LIRC GUI frontend at some point in the future for the purposes of "training" your system to use the remote, but my coding skills aren't up to that just yet. I envisaged something like a GUI that a) would run irrecord for you and b) would pull your keymapping config from Myth/MySQL and then create a .lircrc file based on your irrecord/lircd.conf data and your defined key mappings.

> **agnesdavies said:**
> lircd is running - I've checked it via ps. I did have a lot of problems testing that in the beginning because it insisted everything was /dev/lirc0 and the server crashed every time I tried to connect to that port. I fixed that by switching over to the dev/event thing.

Yup, had the same problem here, hence this thread.

> **agnesdavies said:**
> And I'm assuming that irw wouldn't work if lircd wasn't going?

Correct. It sounds like your lircd and remote are configured fine but you just need to fiddle things about with myth and your lircrc. My advice would be to setup your myth keymappings first (I generally stick with the defaults and only add things like jump points, most of which aren't configured by default) and then edit your .lircrc file accordingly. Don't know if you saw the edit but I've posted my completed .lircrc in my original post which might be handy for you as a starting point, if you have the default for most of the myth key events you should just need to edit it to use your own button names.

> **agnesdavies said:**
> Forgive me if I sound confused, trying to make sense of this is causing my brain to trickle out of my ears - I mean, just as an example, what is the mechanism that is causing the button presses on the remote to appear as keystrokes? I'm pretty sure that ps -ef|grep ircmd doesn't yield anything...!

Don' worry about it, it took me forever to get my remote running to what I'd call an adequate degree when I first started using Linux. As to events happening in the terminal, IIRC this is due to the fact we're going through the event layer - things like up, down, enter, etc get registered as kb events.

As an example, I'd expect your entry for volume up events to be changed from this:
```
begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = VolumeUp
    config = Right
    repeat = 0
    delay = 0
end
```
to this:
```
begin
    remote = hauppauge_nova_t
    prog = mythtv
    button = VolumeUp
    config = ]
    repeat = 0
    delay = 0
end
```
Can you try that and confirm it works?

Re: irexec, a quick search of the forums shows that a fair few people are having problems with it. Will investigate further once I find out what the cmdline for "hibernate" is ;)

---

### Post by agnesdavies on 2008-01-27
OK, made some headway!

I'd called the file in ~/.mythtv .lircrc, but something you mentioned made me check up on that - it should be lircrc sans dot.

Now mythtv is responding to the remote. In fact, it's responding rather TOO well - Down has it jumping two items down the menu, not one - but that's a problem I can happily fiddle with over the next couple of days.

Thanks very much for the howto, stdPikachu, and thanks for the advice subsequently. I think I am now within sight of getting this working!

---

### Post by stdPikachu on 2008-01-27
Ah yes, I remember getting caught out by that one the first time I set one up. Anyhoo, glad you got it sorted! Apologies for not noticing that error earlier.

As I said above, managing the sensitivity is generally just a matter of fiddling with your repeat and delay lines in .lircrc. A quick search'n'replace will sort that out for you in no time.

---

### Post by stdPikachu on 2008-01-27
For the record I've decided to have a stab at doing some GUI stuff with Python; if anyone has any pointers on making a python backend that'll work with GTK and Qt I'd be much obliged as I've only ever worked Qt before, and I can't see it being much use to mythbuntu unless it'll work with both.

---

### Post by superm1 on 2008-01-27
> **stdPikachu said:**
> Include support is definitely a good idea, one of the things that made me want to roll my own was support for all the apps (most of which I don't use) bundled in there which cluttered things up immensely. Is this an upstream change or are you maintaining your own patchsets to LIRC?

Another thing I'd love to add to my wishlist would be to make edits to the Myth keymaps available globally (perhaps a copy-config-to-all-hostnames/make-config-global option in mythcontrols?); do you know if there's anything like this in the works? At the moment I just do it manually via MySQL which is a bit of a PITA.

Anyway, now that I've got almost everything set up dunky-hory, I'd like to extend a big thanks to the Mythbuntu devs, it's certainly a helluva lot less work than Gentoo :D
Well the include support in the lircrc is available upstream.  The include support for lircd.conf however is a local patch.  I submitted it upstream, but they don't like it in its current form.  Time permitting it will be adjusted and then sent back up to them.

---

### Post by superm1 on 2008-01-27
> **stdPikachu said:**
> For the record I've decided to have a stag at doing some GUI stuff with Python; if anyone has any pointers on making a python backend that'll work with GTK and Qt I'd be much obliged as I've only ever worked Qt before, and I can't see it being much use to mythbuntu unless it'll work with both.
If you want to pop in #ubuntu-mythtv-dev for a bit we can chat a little more in depth there.  I'm around most of the time, and if not ping me and i'll respond when i'm back.

All mythbuntu stuff is being done in python (particularly python + gtk [pyGTK]).  So currently if you write it for pyGTK, it can always be expanded later to have a Qt frontend instead.  The important part is the coding style to make this available.

Also: as of Hardy, I wrote a library that a lot of mythbuntu apps are using now: mythbuntu-common.  You can depend upon it and some of the already present LIRC functionality can be directly used then.  So if say you want to read in the present remote configuration, you can do that from there, sort out whats a transmitter and whats a remote etc.

This would be great to see happen though.   Look forward to seeing you pop in.

---

### Post by stdPikachu on 2008-01-28
Well, I shall see what I can come up with, it's been a pretty eventful weekend Myth-wise for me :) but i'll be ahile before I get another free one.

My GUI programming experience has definitely been all Qt-based, and they're just generally a dumb frontend for one of my hackish scripts for people I work with who call themselves sysadmins but are afraid of command lines ;) with the bare minimum of callback functions. However, always happy to learn and it's so nice to use a distro that's got itself a firm idea of where it's going and that can take contructive criticism that it sounds like a good thing to get stuck into, what with the whole mutually beneficial nature of FOSS an' all. Do you have a "wishlist" of stuff you'd like to see happen in Mythbuntu or anything like that? And what do I need to apt-get for GTK UI's? Is Glade still used or is there something better?

Time to dust off an IRC client...

As an aside, most of my impetus comes from making things easier for the end user (mostly due to some of my many previous frustrations with Myth); I'm keen to see it used but aware that, despite the best efforts of distros like Mythbuntu, there's still alot of pitfalls for the average user compared to things like MCE (which is easy to set up and about as flexible as a cast iron RSJ in a vat of liquid hydrogen ;)).</preach>

---

### Post by superm1 on 2008-01-28
> **stdPikachu said:**
> Well, I shall see what I can come up with, it's been a pretty eventful weekend Myth-wise for me :) but i'll be ahile before I get another free one.

My GUI programming experience has definitely been all Qt-based, and they're just generally a dumb frontend for one of my hackish scripts for people I work with who call themselves sysadmins but are afraid of command lines ;) with the bare minimum of callback functions. However, always happy to learn and it's so nice to use a distro that's got itself a firm idea of where it's going and that can take contructive criticism that it sounds like a good thing to get stuck into, what with the whole mutually beneficial nature of FOSS an' all. Do you have a "wishlist" of stuff you'd like to see happen in Mythbuntu or anything like that? And what do I need to apt-get for GTK UI's? Is Glade still used or is there something better?

Time to dust off an IRC client...

As an aside, most of my impetus comes from making things easier for the end user (mostly due to some of my many previous frustrations with Myth); I'm keen to see it used but aware that, despite the best efforts of distros like Mythbuntu, there's still alot of pitfalls for the average user compared to things like MCE (which is easy to set up and about as flexible as a cast iron RSJ in a vat of liquid hydrogen ;)).</preach>
Well it's good to see you have a common vision and/or sense of sanity that we won't be perfect off the bat.  Eventually the goal is to make the non upstream stuff glued together really well.

Here is a list of the blueprints that we have assembled:

Note, we haven't updated the list in some time as per activity going on, but some of these might have been finished already or in progress.  If you want to take a stab at one, just ask about it and I could let you know whats going on with it.

[https://blueprints.edge.launchpad.net/mythbuntu/](https://blueprints.edge.launchpad.net/mythbuntu/)

As for getting started doing pyGTK development, I like to use geany for my editor.  It's really lightweight and has an in app compilation button that will check your source for errors.  It also cleans up the end of line spaces and replaces tabs by spaces if you want (something i've failed to find another easy to use editor to do).

For the GUI parts, install glade-3.  It is in apt, but takes a little getting used to.  It doesn't have nearly as many features as the Qt designer, but it's functional.

---

### Post by stdPikachu on 2008-01-28
Wicked, I'll give that all a read, thanks, some very good ideas there for starters. Still getting to grips with launchpad, is bzr the equivalent of SVN/git? Never used a version control system for anything other than config files yet... and a quick browse of the code reveals that I'll have to up my coding practices, coding nothing but hackish shell scripts to do a single job on a single system teaches you alot of bad habits :D

---

### Post by superm1 on 2008-01-28
> **stdPikachu said:**
> Wicked, I'll give that all a read, thanks, some very good ideas there for starters. Still getting to grips with launchpad, is bzr the equivalent of SVN/git? Never used a version control system for anything other than config files yet... and a quick browse of the code reveals that I'll have to up my coding practices, coding nothing but hackish shell scripts to do a single job on a single system teaches you alot of bad habits :D
Some of our code is a bit hackish too i'll admit.  I rushed to write mcc in about 2 days, and the code for it shows.  Slowly I've been improving its code, and that's the biggest change for it in hardy (other than stability).

Bzr is just like svn/git.  The nice thing is that its a decentralized system.  You can make a branch anywhere, and merge any two branches.  So if you have a code project that you want to improve, you can 'bzr branch URL' and then you have a local copy.  When you want us to merge it, you would 'bzr push bzr+ssh://LPUSER@bazaar.launchpad.net/~LPUSER/PROJECT/BRANCHNAME'

We would then merge that into the main branch using 'bzr merge URL'.  The whole system takes some getting used to, but is incredibly efficient the way it operates.   Easier than git, and smarter than svn is the way I see it.

---

### Post by agnesdavies on 2008-01-29
Well, since getting some excellent assistance on this thread, I've been forging ahead with sorting out my remote control woes on Mythbuntu, and I think I'm just about there.

But I'm not posting to turn this into some kind of blog of my Mythbuntu trials, but to share a couple of other thoughts which might help anyone else who's getting stuck.

I found that, for some strange reason, when I tried to scroll through the menus in Mythtv, the cursor would (nearly) always jump down two items. I fiddled with delay settings, to no avail...then discovered I had TWO stanzas in my .lircrc file telling mythtv what to do when a down arrow was pressed. Sure enough, taking one out has now given me a down button that behaves as it should.

irexec - as has (on here, I think) been pointed out, irexec entries in .lircrc won't work if the irexec daemon isn't running. I'm trying to use the power button to switch off the monitor using DPMS, and got nowhere until I realised that daemon needed to run. I don't know why it doesn't, but perhaps a good place to put a startup line for it would be in the /etc/init.d/lirc startup file?

One thing I did discover you'll need is the DISPLAY environment variable - without it, xset gives up and goes home. I haven't quite solved the issue completely yet, but hope that these pointers are a help.

My next impossible challenge will be to try and find a way of getting the remote to control the room lights via LIRC and the "heyu" X10 command line tool. Wish me luck :)

---

### Post by stdPikachu on 2008-01-29
Was the duplicate entry a relic of your tinkering or there by default?

I did get irexec running, but I'm still finding it rather problematic. Think I'll similarly modify the lircd init file to launch it as running it via XFCE has brought me no end of problems so far.

Good luck with X10, hope you don't fry your mains in the process :D

SuperM1, cheers for all the info, I've been gandering through the code on launchpad, especially the stuff WRT to lirc internals (parsing output of lirc = nightmare :)), much simpler. Are the LIRC hwdb files part of the official upstream packages or are they [myth|u]buntu-specific? The classes you've built will certainly make everything a million miles easier - I think the pertinent phrase is "mad props" but I've never really understood what it meant (Mad propellers? Propositions? The internet makes you mad). Actually, just found out that pylirc is scheduled for inclusion in Hardy, that might make things alot easier, they've even got sample code for receiving input from irrecord.

As per bzr, is the URL just the launchpad URL for the code in question? I'll get around to reading the man page eventually :D

Actually, just tried the command and answered by own question; that was easy!

---

### Post by superm1 on 2008-01-29
> **stdPikachu said:**
> Was the duplicate entry a relic of your tinkering or there by default?

I did get irexec running, but I'm still finding it rather problematic. Think I'll similarly modify the lircd init file to launch it as running it via XFCE has brought me no end of problems so far.

Good luck with X10, hope you don't fry your mains in the process :D

SuperM1, cheers for all the info, I've been gandering through the code on launchpad, especially the stuff WRT to lirc internals (parsing output of lirc = nightmare :)), much simpler. Are the LIRC hwdb files part of the official upstream packages or are they [myth|u]buntu-specific? The classes you've built will certainly make everything a million miles easier - I think the pertinent phrase is "mad props" but I've never really understood what it meant (Mad propellers? Propositions? The internet makes you mad). Actually, just found out that pylirc is scheduled for inclusion in Hardy, that might make things alot easier, they've even got sample code for receiving input from irrecord.

As per bzr, is the URL just the launchpad URL for the code in question? I'll get around to reading the man page eventually :D

Actually, just tried the command and answered by own question; that was easy!

The lirc hwdb files come from upstream, but we hack on them a bit via patches to make them cleaner to operate on.  

It does look like python-pylirc is in apt for hardy.  Worked with this at all?  Any ideas how functional it is?

Let me know if you come up with any questions :)

---

### Post by stdPikachu on 2008-01-29
No idea what pylirc is like, owing to my problems parsing output I decided to have a google regarding python bindings for LIRC which then led me to pylirc; never used it, no. Sounds like it might be useful for piping LIRC events into a GUI at any rate.

As an aside, was the error I ran into regarding the deletion of the .mythtv/lircrc > ~/.lircrc symlink a result of the LIRC generator? I notice there's symlink code in the BZR tree but not the installed version...?

I seem to be derailing threads left, right and centre recently. Whoops!

---

### Post by superm1 on 2008-01-29
> **stdPikachu said:**
> No idea what pylirc is like, owing to my problems parsing output I decided to have a google regarding python bindings for LIRC which then led me to pylirc; never used it, no. Sounds like it might be useful for piping LIRC events into a GUI at any rate.

As an aside, was the error I ran into regarding the deletion of the .mythtv/lircrc > ~/.lircrc symlink a result of the LIRC generator? I notice there's symlink code in the BZR tree but not the installed version...?

I seem to be derailing threads left, right and centre recently. Whoops!
The behavior has changed from gutsy to hardy on this.  In hardy, that file should be a symlink to ~/.lirc/mythtv which is included from ~/.lircrc

---

### Post by agnesdavies on 2008-01-30
> **stdPikachu said:**
> Was the duplicate entry a relic of your tinkering or there by default?
Not sure. I'm pretty sure I didn't put it there, but there have been a few red-wine-fuelled desperate attempts to get it working over the last couple of months, so who knows what I might have done? :)

> **stdPikachu said:**
> Good luck with X10, hope you don't fry your mains in the process :D
Heh, sadly, the problem tends to be the other way around: the mains quite regularly seems to fry my X10 modules :(

I'm more anxious about the idea of tinkering with C++ after a six year hiatus!

> **stdPikachu said:**
> I think the pertinent phrase is "mad props" but I've never really understood what it meant (Mad propellers? Propositions? The internet makes you mad). 
m8d props. The 8 is important *deadpan*

---

### Post by lytke on 2008-02-02
Hi 

Thanks for posting your Mini-howto, it helped me get my Hauppauge remote up and running.
My setup is Mythbuntu 7.10 with a Hauppauge Nova-t and the remote that comes in the box.

I choose the NovaT-500 remote in setup and worked from there.
At first it was only the arrows and OK that worked.

Then a started reading your howto and ended up with the biggest progress when I discovered that the IR was not configured in hardware.conf

**My ultra short howto**
1.    Discover inputdevice
               ls -lah /dev/input/by-path/
2.    edit /etc/lirc/hardware.conf 
               DEVICE="/dev/input/event2"         (the number was two in my case)

3.   fix the buttons that did not work (9-10 pcs.)
      edit  /etc/lirc/lircd.conf  with correct values for each button
      - took the values from your example => bingo it is working :-D

Hopes this helps others in same situation !

Regards
lytke.

---

### Post by agnesdavies on 2008-02-03
I'm back again!

I've battled with udev on a number of occasions, and always retired somewhat worse off, so I generally end up abandoning it and hoping for the best.

But the changing-event-numbers problem is a complete pain, especially as I have two Hauppauge Nova cards (one terrestrial, one satellite) and they regularly seem to swap device numbers.

I've followed all the various HOWTOs and FAQs, using all kinds of identifiers for the devices (though in practice, only the name actually seems to be any use): here's an example (one of many) of an attempt at a udev rule...

```
BUS=="pci", SYSFS{vendor}=="0x14f1",ATTRS{name}=="*Nova-S-Plus*", \
        SYMLINK="input/irremote"

```

I've tried everything, just using the ATTRS{name}, with and without wildcards, with and without vendor IDs, bus, the whole bit.

The upshot is that I get a symlink in /dev/input...but it points at apparently completely random devices. If I do 'ls -l" at it once, I'll get 

```
lrwxrwxrwx 1 root root      6 2008-02-03 18:28 irremote -> ../2-2
```
then the next time I do it, I'm getting
```
lrwxrwxrwx 1 root root      8 2008-02-03 18:40 irremote -> ../ptybd

```

(just to show Murphy's Law is alive and well, I just did it and got the same result 3 times :rolleyes: ).

I'm at me wits' end on this one now - while I accept I'm not that au fait with the whole udev thing, I can't fathom out why on earth it's randomly directing that symlink to strange devices...

---

### Post by lytke on 2008-02-03
How about using double ir-receivers

If you have a receiver on both cards, wouldn't you be home free....?

I also have a spare Hauppauge Nova-s in a box somewhere, I will try an fit into my pc next to the nova-t - and come back with the results

/lytke

---

### Post by Chunder on 2008-08-25
Hi all - long time lurker but just found this seemingly unresolved issue, and since I've recently (just!) figures out how to fix the problem, I thought I'd join up and try to start repaying the debt that I owe this forum :)

I've been hitting the same problems with the Nova-S card IR receiver being allocated a completely different Eventx upon reboot, usually depending whether there is a USB keyboard/mouse plugged in or not.

I've played around with all manner of settings, read virtually every relevant article on the web that I could find, and I'm not too sure what it was that finally made it click...

My system is in an Antec Fusion case, so I've already had to play around with Udev in order to split off the MCE_USB device and the Volume_Wheel device. These two created symlinks perfectly (although I haven't used them yet) but the Hauppauge IR one just wouldn't work - and it turns out it was due to the designation in the ATTRS{phys} section.
I've edited the rules in /etc/udev/rules.d/85-lirc.rules - not sure if this is the best place for them, but it appears to work...

```
KERNELS=="2-6", SUBSYSTEMS=="usb", ATTRS{idVendor}=="15c2", ATTRS{idProduct}=="ffdc", SYMLINK+="lirc_mceusb2_antec_ir"
KERNELS=="2-6:1.0", SUBSYSTEMS=="usb", DRIVERS=="lirc_imon", ATTRS{bInterfaceNumber}=="00", SYMLINK+="lirc_imon_antec_wheel"
KERNELS=="input[0-9]*", SUBSYSTEMS=="input", ATTRS{phys}=="pci-0000:04:08.0/ir0", SYMLINK+="lirc_hauppauge_ir"
```

Various places I looked (either udevinfo, cat /proc/bus/input/devices, or whatever) would list the address of the IR device as e.g. pci-0000:04:08.2/ir0 or pci-0000:04:08.0/--event-ir, it was all very confusing!

Obviously other systems will have a different address here, as it relates to the PCI slot that the card is inserted into...

Next, in the /etc/lirc/hardware.conf I made the following change:

```
REMOTE_DEVICE="/dev/lirc_hauppauge_ir"
```

Now the remote control always works, even after a reboot, and even if I boot with a USB keyboard or mouse attached... huzzah!

Don't know if this has already been resolved in another thread over the last 6 months, but hopefully this will be useful for someone.

---

### Post by TaTaE on 2008-09-22
Superm1, could you help me with configuring my remote control, please ?
   I am running Intrepid Ibex and I have a Winfast TV2000 XP working like a keyboard (!), that means it only has digits and enter working.
   I have a /dev/lirc0 and a /dev/lircd, and I checked the remote this way: I stopped gdm and I ran irw and irexec, and the remote runs ok. But if xorg is running, it seems it is taking over my remote events, and irexec gets nothing.
   These are my config files:
lircd.conf:
```

$ cat /etc/lircd.conf 

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3(devinput) on Sun Sep 21 23:25:20 2008
#
# contributed by Claudiu Vlad
#
# brand: Leadtek
# model no. of remote control: Y04G0044 
# devices being controlled by this remote: Winfast TV2000 Expert
#

begin remote

  name     Y04G0044
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          263992
  toggle_bit_mask 0x80010179

      begin codes
          POWER                    0x0074
          TV                       0x0179
          FM                       0x0181
          DVD                      0x0185
          RED                      0x018E
          GREEN                    0x018F
          YELLOW                   0x0190
          BLUE                     0x0191
          TELETEXT                 0x0184
          SLEEP                    0x008E
          MUTE                     0x0071
          BOSSKEY                  0x0163
          CHANNELUP                0x0192
          RECALL                   0x00DF
          CHANELLDOWN              0x0193
          ENTER                    0x001C
          VOLDOWN                  0x0072
          VOLUP                    0x0073
          FULLSCREEN               0x0174
          MENU                     0x008B
          CHSURF                   0x016B
          PREVIOUS                 0x019C
          NEXT                     0x0197
          PLAYPAUSE                0x00A4
          INFO                     0x0172
          REWIND                   0x00A8
          STOP                     0x0080
          FFORWARD                 0x00D0
          EPG                      0x0189
          LANGUAGE                 0x0170
          ONE                      0x0002
          TWO                      0x0003
          THREE                    0x0004
          FOUR                     0x0005
          FIVE                     0x0006
          SIX                      0x0007
          SEVEN                    0x0008
          EIGHT                    0x0009
          NINE                     0x000A
          ZERO                     0x000B
          VIDEO                    0x0188
          AUDIO                    0x0166
          DISPLAY                  0x00EA
          SNAPSHOT                 0x0169
          TIMESHIFTING             0x00C2
          RECORD                   0x00A7
          RECORDSTOP               0x0080
          PIP                      0x00E2
          DOT                      0x0034
          DELETE                   0x0195
          UNUSED1                  0x00BF
          UNUSED2                  0x00C0
          UNUSED3                  0x00C1
      end codes

end remote

```
 and hardware.conf :
```

$ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Winfast TV2000/XP (card=34)"
REMOTE_MODULES="lirc_dev lirc_i2c lirc_bt829 lirc_sir"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

```

and .lircrc

```

]$ cat .lircrc 
# This is an example config file for your LIRC remote.  All buttons
# depend on what you have configured in your lircd.conf file.  Please
# refer to this and adjust the labels below accordingly.
#
# tvtime is controlled through a separate program called tvtime-command.
# For a list of commands, see 'man tvtime-command'.  Key events can
# be 'faked' using the command KEY_EVENT, which allows for mapping a
# single remote control button to both a menu mode command and a normal
# mode command.
#
# begin
#    prog = irexec
#    button = DISPLAY
#    config = tvtime-command DISPLAY_INFO
# end


# This section includes two configs, what this does is that it allows
# you to open tvtime and close tvtime with one button.  If your remote
# has seperate buttons for this, then you can break it apart.
begin
    prog = irexec
    button = POWER
    config = tvtime &
    config = tvtime-command QUIT
end


# The following defines most of the common buttons found on a remote and
# what commads they would map to inside tvtime.
begin
    prog = irexec
    button = source
    config = tvtime-command TOGGLE_INPUT
end
begin
    prog = irexec
    button = DISPLAY
    config = tvtime-command DISPLAY_INFO
    repeat = 1
end
begin
    prog = irexec
    button = FULLSCREEN
    config = tvtime-command TOGGLE_FULLSCREEN
end
begin
    prog = irexec
    button = CC
    config = tvtime-command TOGGLE_CC
end

begin
    prog = irexec
    button = MUTE
    config = tvtime-command TOGGLE_MUTE
end

# Menu navigation.
begin
    prog = irexec
    button = CH+
    config = tvtime-command UP
    repeat = 1
end
begin
    prog = irexec
    button = CH-
    config = tvtime-command DOWN
    repeat = 1
end
begin
    prog = irexec
    button = VOL+
    config = tvtime-command RIGHT
    repeat = 2
end
begin
    prog = irexec
    button = VOL-
    config = tvtime-command LEFT
    repeat = 2
end

begin
    prog = irexec
    button = RECALL
    config = tvtime-command CHANNEL_JUMP
    repeat = 1
end

begin
    prog   = irexec
    button = 1
    config = tvtime-command CHANNEL_1
end
begin
    prog   = irexec
    button = 2
    config = tvtime-command CHANNEL_2
end
begin
    prog   = irexec
    button = 3
    config = tvtime-command CHANNEL_3
end
begin
    prog   = irexec
    button = 4
    config = tvtime-command CHANNEL_4
end
begin
    prog   = irexec
    button = 5
    config = tvtime-command CHANNEL_5
end
begin
    prog   = irexec
    button = 6
    config = tvtime-command CHANNEL_6
end
begin
    prog   = irexec
    button = 7
    config = tvtime-command CHANNEL_7
end
begin
    prog   = irexec
    button = 8
    config = tvtime-command CHANNEL_8
end
begin
    prog   = irexec
    button = 9
    config = tvtime-command CHANNEL_9
end
begin
    prog   = irexec
    button = 0
    config = tvtime-command CHANNEL_0
end
begin
    prog = irexec
    button = ENTER
    config = tvtime-command ENTER
end

```

dmesg say this:
```

[   32.844928] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   35.784170] ACPI: \_SB_.PCI0.IDE1.CHN1.DRV0: found ejectable bay
[   35.784179] ACPI: \_SB_.PCI0.IDE1.CHN1.DRV0: Adding notify handler
[   35.784214] ACPI: Error installing bay notify handler
[   36.088525] ACPI: WMI: Mapper loaded
[   36.744150] lirc_dev: IR Remote Control driver registered, major 61 
[   36.933357] bttv: driver version 0.9.17 loaded
[   36.933362] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   37.236947] ivtv:  Start initialization, version 1.4.0
[   37.236993] ivtv:  End initialization
[   37.358066] ATIR: pci_prob failed
[   37.358073] sys_init_module: 'lirc_bt829'->init suspiciously returned 1, it should follow 0/-E convention
[   37.358075] sys_init_module: loading module anyway...
[   37.358081] Pid: 4945, comm: modprobe Tainted: P          2.6.27-3-generic #1
[   37.358089]  [<c03926e6>] ? printk+0x1d/0x1f
[   37.358110]  [<c015bfd7>] sys_init_module+0x1a7/0x1b0
[   37.358122]  [<c0103f6b>] sysenter_do_call+0x12/0x2f
[   37.358131]  =======================
[   37.473193] lirc_dev: lirc_register_plugin: sample_rate: 0
[   37.473325] lirc_sir: I/O port 0x03e8, IRQ 4.
[   37.473336] lirc_sir: Installed.
[   39.834813] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   42.010868] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   42.010876] apm: disabled - APM is not SMP safe.
[   44.104083] ppdev: user-space parallel port driver
[   46.973138] QEMU Accelerator Module version 1.3.0, Copyright (c) 2005-2007 Fabrice Bellard
[   46.974288] KQEMU installed, max_locked_mem=516312kB.

```

lsmod says:
```

$ lsmod | grep lirc
lirc_sir               23684  0 
lirc_bt829             12288  0 
lirc_i2c               17156  0 
lirc_dev               20020  3 lirc_sir,lirc_bt829,lirc_i2c
i2c_core               31892  15 ivtv,bttv,lirc_i2c,lm85,i2c_i801,tuner_simple,tea5767,tda9887,tda8290,tuner,nvidia,cx88xx,i2c_algo_bit,tveeprom,v4l2_common

```

---

### Post by mac-duff on 2009-04-30
Hi,
last time I got a Hauppauge WinTV MiniStick but I am already stucking by the first point. I do not find the IR device. When I do a dmesg I get following output:

root@mdl:/home/stephan/Desktop# dmesg |grep dv
[   67.447631] usb 2-4: firmware: requesting sms1xxx-hcw-55xxx-dvbt-02.fw
[   68.184452] smscore_set_device_mode: firmware download success: sms1xxx-hcw-55xxx-dvbt-02.fw


I can someone give me a hint?

Thx
Stephan

---

### Post by TaTaE on 2009-05-02
> **mac-duff said:**
> Hi,
last time I got a Hauppauge WinTV MiniStick but I am already stucking by the first point. I do not find the IR device. When I do a dmesg I get following output:

root@mdl:/home/stephan/Desktop# dmesg |grep dv
[   67.447631] usb 2-4: firmware: requesting sms1xxx-hcw-55xxx-dvbt-02.fw
[   68.184452] smscore_set_device_mode: firmware download success: sms1xxx-hcw-55xxx-dvbt-02.fw


I can someone give me a hint?

Thx
Stephan


Enter this into terminal :

lshal | grep --color -n10 IR

It should show you something similar to :

blablabla
1175:  input.product = 'cx88 IR (Leadtek Winfast 2000XP'  (string)
1176-  linux.device_file = '/dev/input/event5'  (string)
blablabla

the '/dev/input/event5' must be your IR device

---

### Post by CoolDreamZ on 2009-11-30
Firstly, thank-you very much for this thread. Getting a remote control to work is incredibly difficult!

I have the remote working OK, my problem is getting the udev rule to work to cope with moving devices.

Here is my (current) udev rule (have also tried using the name attibute, with and without SUBSYSTEM="input" to no avail).

```
ATTRS{phys}=="pci-0000:01:06.0/ir0", SYMLINK+="input/HVR400"
```

Here is the output of udevinfo:

```
udevadm info -a -p $(udevadm info -q path -n /dev/input/event6)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:08.0/0000:01:06.0/input/input6/event6':
    KERNEL=="event6"
    SUBSYSTEM=="input"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:08.0/0000:01:06.0/input/input6':
    KERNELS=="input6"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{name}=="cx88 IR (Hauppauge WinTV-HVR400"
    ATTRS{phys}=="pci-0000:01:06.0/ir0"
    ATTRS{uniq}==""
    ATTRS{modalias}=="input:b0001v0070p6902e0001-e0,1,14,k71,72,73,74,77,80,8B,8E,A3,A5,A7,A8,AE,CF,D0,161,16B,16D,16F,172,174,179,181,184,188,189,18E,18F,190,191,192,193,19C,ramlsfw"

  looking at parent device '/devices/pci0000:00/0000:00:08.0/0000:01:06.0':
    KERNELS=="0000:01:06.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="cx8800"
    ATTRS{vendor}=="0x14f1"
    ATTRS{device}=="0x8800"
    ATTRS{subsystem_vendor}=="0x0070"
    ATTRS{subsystem_device}=="0x6902"
    ATTRS{class}=="0x040000"
    ATTRS{irq}=="18"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v000014F1d00008800sv00000070sd00006902bc04sc00i00"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00/0000:00:08.0':
    KERNELS=="0000:00:08.0"
    SUBSYSTEMS=="pci"
    DRIVERS==""
    ATTRS{vendor}=="0x10de"
    ATTRS{device}=="0x006c"
    ATTRS{subsystem_vendor}=="0x0000"
    ATTRS{subsystem_device}=="0x0000"
    ATTRS{class}=="0x060400"
    ATTRS{irq}=="0"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v000010DEd0000006Csv00000000sd00000000bc06sc04i00"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```

Here is the output of udevtest:
```

udevadm test /class/input/input6
[sudo] password for chris:
run_command: calling: test
udevadm_test: version 147
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/etc/udev/rules.d/25-custom.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-gnupg.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ia64.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-infiniband.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-isdn.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libgphoto2-2.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-pilot-links.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ppc.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-xserver-xorg-input-wacom.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-zaptel.rules' as rules file
parse_file: reading '/lib/udev/rules.d/41-mythtv-permissions.rules' as rules file
parse_file: reading '/lib/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/lib/udev/rules.d/50-firmware.rules' as rules file
parse_file: reading '/lib/udev/rules.d/50-udev-default.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-cdrom_id.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-alsa.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-input.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-serial.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage-tape.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-v4l.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-gnome-bluetooth-rfkill.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-mobile-action.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-option-modem-modeswitch.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-persistent-storage-edd.rules' as rules file
parse_file: reading '/lib/udev/rules.d/64-device-mapper.rules' as rules file
parse_file: reading '/lib/udev/rules.d/65-dmsetup.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-acl.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-hid2hci.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-cd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-net.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-cd-aliases-generator.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-net-description.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-persistent-net-generator.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-tty-description.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-ericsson-mbm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-zte-port-types.rules' as rules file
parse_file: reading '/lib/udev/rules.d/78-sound-card.rules' as rules file
parse_file: reading '/lib/udev/rules.d/79-fstab_import.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-alsa.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-drivers.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-lirc.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-regulatory.rules' as rules file
parse_file: reading '/lib/udev/rules.d/90-hal.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-disks.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-battery-recall-dell.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-battery-recall-fujitsu.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-battery-recall-gateway.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-battery-recall-ibm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-battery-recall-lenovo.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-battery-recall-toshiba.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-csr.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-hid.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-wup.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-keymap.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-udev-late.rules' as rules file
parse_file: reading '/lib/udev/rules.d/97-bluetooth.rules' as rules file
udev_rules_new: rules use 119460 bytes tokens (9955 * 12 bytes), 22387 bytes buffer
udev_rules_new: temporary index used 36360 bytes (1818 * 20 bytes)
udev_device_new_from_syspath: device 0x1f68dc8 has devpath '/devices/pci0000:00/0000:00:08.0/0000:01:06.0/input/input6'
udev_rules_apply_to_event: RUN '/sbin/modprobe -b $env{MODALIAS}' /lib/udev/rules.d/80-drivers.rules:5
udev_rules_apply_to_event: RUN 'socket:@/org/freedesktop/hal/udev_event' /lib/udev/rules.d/90-hal.rules:2
udevadm_test: UDEV_LOG=6
udevadm_test: DEVPATH=/devices/pci0000:00/0000:00:08.0/0000:01:06.0/input/input6
udevadm_test: PRODUCT=1/70/6902/1
udevadm_test: NAME="cx88 IR (Hauppauge WinTV-HVR400"
udevadm_test: PHYS="pci-0000:01:06.0/ir0"
udevadm_test: EV==100003
udevadm_test: KEY==100fc312 214a802 0 0 0 0 18000 41a8 4801 9e1680 0 0 10000ffc
udevadm_test: MODALIAS=input:b0001v0070p6902e0001-e0,1,14,k71,72,73,74,77,80,8B,8E,A3,A5,A7,A8,AE,CF,D0,161,16B,16D,16F,172,174,179,181,184,188,189,18E,18F,190,191,192,193,19C,ramlsfw
udevadm_test: ACTION=add
udevadm_test: SUBSYSTEM=input
udevadm_test: run: '/sbin/modprobe -b input:b0001v0070p6902e0001-e0,1,14,k71,72,73,74,77,80,8B,8E,A3,A5,A7,A8,AE,CF,D0,161,16B,16D,16F,172,174,179,181,184,188,189,18E,18F,190,191,192,193,19C,ramlsfw'
udevadm_test: run: 'socket:@/org/freedesktop/hal/udev_event'
```

---

### Post by TaTaE on 2009-11-30
Why dont you use simply this
ATTRS{name}=="cx88 IR (Hauppauge WinTV-HVR400", followed by SYMLINK blabla

This is what I'm using:

$ cat /etc/udev/rules.d/telecomanda.rules 
# stable device for cx88 IR
KERNEL=="event*", ATTRS{name}=="cx88 IR*", NAME="input/%k", SYMLINK="input/irremote"

---

### Post by CoolDreamZ on 2009-12-01
Thanks for the quick reply. My initial (failed) attempt was based on the very first post in this thread like this:

```
ATTRS{name}=="cx88 IR (Hauppauge WinTV-HVR400", SYMLINK+="input/irremote"
```

I will try expanding the rule as you suggest, including > NAME="input/%k", SYMLINK="input/irremote" when I next have access to the machine (this coming weekend) and report back.

Fingers crossed....

---

### Post by CoolDreamZ on 2009-12-07
Went back to the machine over the weekend, powered it on and all is working fine with my current rule (the machine had been rebooted).

So it seems that > Once you've written the file, run "sudo udevtrigger" to reload udev and the new symlinks should be created. from the original post did not work for me (a reboot was required - wish I had thought of that - duh!)

Thanks for your help

---

### Post by scotty64 on 2010-08-28
I am using a WinTV-HVR900 as IR receiver to control various applications (VLC / OpenOffice Impress, etc.). I wanted a lirc / udev configuration that is hotpluggable. Here is how I did it:

1. Check the path of your IR receiver by plugging in the receiver and:
ls /dev/input/by-path
In my case the device is called "pci-0000:00:1d.7-event-ir"

2. Use this path/devicename in your hardware.conf. The first lines should read:
```

#Chosen Remote Control
REMOTE="Hauppauge"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-path/pci-0000:00:1d.7-event-ir"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"

```

3. Now we make lirc hotpluggable by creating a new udev rule in /etc/udev/rules.d. I called the file 97-lirc-hotplug.rules
This file contains the following two lines:

```

SUBSYSTEM=="input", ENV{DEVLINKS}=="*dev/input/by-path/pci-0000:00:1d.7-event-ir", RUN+="/etc/init.d/lirc start"
SUBSYSTEM=="input", ENV{DEVLINKS}=="*dev/input/by-path/pci-0000:00:1d.7-event-ir", ACTION=="remove", RUN+="/etc/init.d/lirc stop"

```

Thes two lines tell udev to start lirc when the device is plugged in and to stop it when we remove it. Be aware that ENV{DEVLINKS} represents a list of all udev links to the device. For correct pattern matching we replace the starting slash of the path with an asterisk to match against all other possible links in the output.

4. sudo /etc/init.d/udev restart

5. remove the autostart links for lirc from the runlevels:

sudo mv /etc/rc2.d/S19lirc /etc/rc2.d/K19lirc
sudo mv /etc/rc3.d/S19lirc /etc/rc3.d/K19lirc

That should do it.

---

