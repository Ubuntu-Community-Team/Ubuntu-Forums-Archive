---
title: "Snapstream Firefly in Myth 9.04"
date: 2009-05-17
forum: Mythbuntu
---

### Post by lightning9 on 2009-05-17
Hello,

I can't get my Firefly to work in 9.04 at all whether I follow [my own guide for 8.04/8.10]("http://ubuntuforums.org/showthread.php?t=884972") or the suggestions made by phroman or superm1 in [this thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7161629").

Here's what I did:

Started with a clean slate (blank hard drive).
Selected the Snapstream X10 RF remote during installation of 9.04.
No buttons worked.
Performed the steps of my instructions.
No buttons worked.
Backed out my mods and followed superm1's instructions.
No buttons work.

syslog says it sees the remote and accepts the mythtv client when it loads.

```
May 17 08:03:26 m0 kernel: [  894.666753] lirc_atiusb: USB remote driver for LIRC $Revision: 1.69 $
May 17 08:03:26 m0 kernel: [  894.666755] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
May 17 08:03:26 m0 kernel: [  894.668786] lirc_dev: lirc_register_plugin: sample_rate: 0
May 17 08:03:26 m0 kernel: [  894.684017] lirc_atiusb[2]: X10 WTI RF receiver on usb8:2
May 17 08:03:26 m0 lircd-0.8.4a[5844]: garbage after 'name' token in line 1941 ignored
May 17 08:03:26 m0 lircd-0.8.4a[5847]: lircd(default) ready
May 17 08:03:26 m0 kernel: [  894.693734] usbcore: registered new interface driver lirc_atiusb
May 17 08:04:01 m0 lircd-0.8.4a[5847]: accepted new client on /dev/lircd

```

It also accepts the new client when I play a video. However, nothing works!

If I do get this working, there is another large concern of mine. I have two Fireflies in my home and need to configure each machine to only respond to a specific channel. While trying to follow [this guide]("http://ubuntuforums.org/showthread.php?t=639123"),
I can no longer find /etc/modprobe.d/aliases to modify. How does one go about making these changes in 9.04?

But again, this will only apply once I get the remote working so, any suggestions?

Thanks,
lightning9

---

### Post by lightning9 on 2009-05-17
I tried so many different things that I am not quite sure what made the difference, but it now works!  \\:D/

If I am correct, I believe the fact that it didn't work at all was related to the fact that I couldn't figure out how to configure lirc to only listen to a specific channel since /etc/modprobe.d/aliases no longer exists.

Once I finally discovered the lirc_atiusb kernel module options could go into an arbitrarily named conf file in /etc/modprobe.d (thanks to [this thread]("http://ubuntuforums.org/showthread.php?t=1147741")), it started working. So, for anybody for anybody who wants lirc to respond to unique channels of the Firefly remote, instead of [these instructions (which work great for 8.04/8.10)]("http://ubuntuforums.org/showthread.php?t=639123"), simply put the options into /etc/modprobe.d/lirc_atiusb.conf.

Here's what my working /etc/modprobe.d/lirc_atiusb.conf contains:

```
# /etc/modprobe.d/lirc_atiusb.conf
# options to enable/disable various features of the
# lirc_atiusb kernel module.
# To see which options are available, run "modinfo lirc_atiusb | grep parm".
#
# My output:
#   parm:           debug:Debug enabled or not (default: 0) (bool)
#   parm:           mask:Set channel acceptance bit mask (default: 0xFFFF) (int)
#   parm:           unique:Enable channel-specific codes (default: 0) (bool)
#   parm:           repeat:Repeat timeout (1/100 sec) (default: 10) (int)
#   parm:           mdeadzone:rw2 mouse sensitivity threshold (default: 0) (int)
#   parm:           emit_updown:emit press/release codes (rw2): 0:don't (default), 1:emit 2 codes only, 2:code for each button (int)
#   parm:           emit_modekeys:emit keycodes for aux1-aux4, pc, and mouse (rw2): 0:don't (default), 1:emit translated codes: one for mode switch, one for same mode, 2:raw codes (int)
#   parm:           mgradient:rw2 mouse: 1000*gradient from E to NE (default: 500 => .5 => ~27 degrees) (int)
#
# Mask values can be:
# Channel Mask
#       1 0x0001
#       2 0x0002
#       3 0x0004
#       4 0x0008
#       5 0x0010
#       6 0x0020
#       7 0x0040
#       8 0x0080
#       9 0x0100
#      10 0x0200
#      11 0x0400
#      12 0x0800
#      13 0x1000
#      14 0x2000
#      15 0x4000
#      16 0x8000
#
# Accept only channel 9
options lirc_atiusb unique=1 mask=0x0100

```

The rest of [my Firefly instructions for 8.04/8.10]("http://ubuntuforums.org/showthread.php?t=884972") still apply.


<aside_0> 
This fix doesn't make sense to me right now because the file that obscurely pointed me in the right direction (/usr/share/lirc/remotes/atiusb/lircd.conf.atiusb) says:

```
# NOTE!! The lirc_atiusb driver now removes the channel code
# from key-codes (by default).  This effectively outputs codes
# for remote channel 1.  You can change this behavior by
# loading the module with unique=1.  Type `modinfo lirc_atiusb`
# for details.
```
Which leads me to believe it should have worked OOTB regardless of which channel my Firefly was programmed to emit since the default value of the unique parm is 0. (And, yes, I tried programming channel 1 on my remote. Didn't work.) :confused:
</aside_0>


<aside_1>
Setting the kernel module options in this new way is soooo much better than having to modify a monolithic /etc/modprobe.d/aliases! Thanks Ubuntu developers!
</aside_1>


Hope this helps,
lightning9

---

### Post by Dragonflyoh on 2009-06-05
I am having problems with my Firefly remote and after sorting through the steps in the above post I have the remote working for about half of the keys. I just upgraded to 9.04 and before the upgrade the remote worked fine. Any ideas would be appreciated.

---

### Post by lightning9 on 2009-06-06
> **Dragonflyoh said:**
> I am having problems with my Firefly remote and after sorting through the steps in the above post I have the remote working for about half of the keys. I just upgraded to 9.04 and before the upgrade the remote worked fine. Any ideas would be appreciated.
Hello Dragonflyoh,

I am happy to try and help but you didn't supply enough info. Half the keys work how/where? In the Myth frontend or mplayer or ... ? What does your /etc/lircd.conf contain/point to? What are the contents of your ~/.lirc/mplayer and ~/.lirc/mythtv files? etc.

lightning9

---

### Post by Dragonflyoh on 2009-06-07
The main keys that are not working are for Mythtv are OK, Exit, Info and Menu. I went back over the setup again and more keys are now working. The close key will shut down Mythtv but I never used it for anything before.
My lircd.conf is:
# /etc/lirc/lircd.conf
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.7.0(any) on Fri Mar 11 08:51:45 2005
#
# contributed by
#
# brand: Snapstream Firefly Remote
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name Snapstream
    bits 40
    eps 30
    aeps 100
    one 0 0
    zero 0 0
    gap 219964
    toggle_bit 0

    begin codes
      MAXI 0x0000001481AC0000
      MAXI 0x00000014012C0000
      CLOSE 0x00000014D7020000
      CLOSE 0x0000001457820000
      1 0x00000014628D0000
      1 0x00000014E20D0000
      2 0x00000014E30E0000
      2 0x00000014638E0000
      3 0x00000014648F0000
      3 0x00000014E40F0000
      4 0x00000014E5100000
      4 0x0000001465900000
      5 0x0000001466910000
      5 0x00000014E6110000
      6 0x00000014E7120000
      6 0x0000001467920000
      7 0x0000001468930000
      7 0x00000014E8130000
      8 0x00000014E9140000
      8 0x0000001469940000
      9 0x000000146A950000
      9 0x00000014EA150000
      0 0x00000014EC170000
      0 0x000000146C970000
      BACK 0x000000146B960000
      BACK 0x00000014EB160000
      ENT 0x00000014ED180000
      ENT 0x000000146D980000
      VOL+ 0x000000145E890000
      VOL+ 0x00000014DE090000
      VOL- 0x000000145D880000
      VOL- 0x00000014DD080000
      MUTE 0x000000145F8A0000
      MUTE 0x00000014DF0A0000
      FIREFLY 0x0000001455800000
      FIREFLY 0x00000014D5000000
      CH+ 0x00000014608B0000
      CH+ 0x00000014E00B0000
      CH- 0x00000014618C0000
      CH- 0x00000014E10C0000
      INFO 0x0000001483AE0000
      INFO 0x00000014032E0000
      OPTION 0x0000001484AF0000
      OPTION 0x00000014042F0000
      UP 0x000000146F9A0000
      UP 0x00000014EF1A0000
      LEFT 0x00000014729D0000
      LEFT 0x00000014F21D0000
      DOWN 0x0000001477A20000
      DOWN 0x00000014F7220000
      RIGHT 0x00000014749F0000
      RIGHT 0x00000014F41F0000
      OK 0x00000014739E0000
      OK 0x00000014F31E0000
      MENU 0x00000014719C0000
      MENU 0x00000014F11C0000
      EXIT 0x0000001475A00000
      EXIT 0x00000014F5200000
      REC 0x00000014FC270000
      REC 0x000000147CA70000
      PLAY 0x00000014FA250000
      PLAY 0x000000147AA50000
      STOP 0x00000014FD280000
      STOP 0x000000147DA80000
      REW 0x00000014F9240000
      REW 0x0000001479A40000
      FWD 0x00000014FB260000
      FWD 0x000000147BA60000
      PREV 0x00000014002B0000
      PREV 0x0000001480AB0000
      PAUSE 0x00000014FE290000
      PAUSE 0x000000147EA90000
      NEXT 0x00000014FF2A0000
      NEXT 0x000000147FAA0000
      MUSIC 0x00000014DB060000
      MUSIC 0x000000145B860000
      PHOTOS 0x00000014DA050000
      PHOTOS 0x000000145A850000
      DVD 0x00000014D9040000
      DVD 0x0000001459840000
      TV 0x00000014D8030000
      TV 0x0000001458830000
      VIDEO 0x00000014DC070000
      VIDEO 0x000000145C870000
      HELP 0x00000014D6010000
      HELP 0x0000001456810000
      MOUSE 0x00000014022D0000
      MOUSE 0x0000001482AD0000
      A 0x00000014EE190000
      A 0x000000146E990000
      B 0x00000014F01B0000
      B 0x00000014709B0000
      C 0x00000014F6210000
      C 0x0000001476A10000
      D 0x00000014F8230000
      D 0x0000001478A30000

  end codes

end remote
And my home/myname/.lirc/mythtv is:
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
begin
    remote = Snapstream
    prog = mythtv
    button = PLAY
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = RIGHT
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = MUTE
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = VOL-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = STOP
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = VOL+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = DOWN
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = INFO
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = PAUSE
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = ENT
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = MENU
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = UP
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = CH-
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = REC
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = CLOSE
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = CH+
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = ENT
    config = Enter
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = FWD
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream
    prog = mythtv
    button = LEFT
    config = Left
    repeat = 0
    delay = 0
end

---

### Post by lightning9 on 2009-06-07
You are aware the mappings you supplied (~/.lirc/mythtv) are only used while in the frontend (the myth menu system), right? ~/.lirc/mplayer is used for buttons while playing a video via mplayer, ~/.lirc/xine is used while playing a video via xine, etc. 

That being said, your Menu and Info keys are mapped correctly (at least they are the same as mine) for the frontend. Your OK and Exit keys aren't mapped to anything in your listing below.

How about trying my lircd.conf and ~/.lirc/mythtv (and ~/.lirc/mplayer ?) files from here:
[http://ubuntuforums.org/showpost.php?p=5650075&postcount=4](http://ubuntuforums.org/showpost.php?p=5650075&postcount=4)

Or, perhaps there is a misconception as to how the different keys should work?

Guess I still need more info...

---

### Post by Dragonflyoh on 2009-06-08
Thank you for the help. I copied your files and all of the remote keys are working as they were before I update to 9.04.

---

