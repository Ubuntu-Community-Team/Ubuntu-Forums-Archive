---
title: "[SOLVED] ATI Remote Wonder 5000023600"
date: 2007-11-04
forum: Mythbuntu
---

### Post by a_posse_ad_esse on 2007-11-04
I am using the kernel module (ati_remote, the userspace module is blacklisted) and a fresh install.  The GUI configuration worked pretty well, but it identified the control as the Remote Wonder II, and didn't give the functionality that I wanted (such as the ability to use "escape").  I did some homework and modified my settings as such:

/etc/lirc/lircd.conf
```


begin remote

  name  ati_remote
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          227972
  min_repeat      4
  toggle_bit      0


      begin codes
          1                        0x000000000000920D
          2                        0x000000000000930E
          3                        0x000000000000940F
          4                        0x0000000000009510
          5                        0x0000000000009611
          6                        0x0000000000009712
          7                        0x0000000000009813
          8                        0x0000000000009914
          9                        0x0000000000009A15
          a                        0x0000000000008500
          b                        0x0000000000008601
          power                    0x0000000000008702
          tv                       0x0000000000008803
          dvd                      0x0000000000008904
          web                      0x0000000000008A05
          media_library            0x0000000000008B06
          drag                     0x0000000000008C07
          0                        0x0000000000009C17
          c                        0x0000000000009E19
          d                        0x000000000000A01B
          mute                     0x0000000000008F0A
          tv_on_demand             0x000000000000A11C
          max_window               0x000000000000A520
          e                        0x000000000000A621
          f                        0x000000000000A823
          ok                       0x000000000000A31E
          left                     0x000000000000A21D
          right                    0x000000000000A41F
          up                       0x0000000000009F1A
          down                     0x000000000000A722
          rewind                   0x000000000000A924
          play                     0x000000000000AA25
          forward                  0x000000000000AB26
          record                   0x000000000000AC27
          stop                     0x000000000000AD28
          pause                    0x000000000000AE29
          mouse_button_left        0x000000000000FD78
          mouse_button_right       0x000000000000017C
          vol-down                 0x0000000000008E09
          vol-up                   0x0000000000008D08
          chan-down                0x000000000000910C
          chan-up                  0x000000000000900B
          mouse-up                 0x000000000000F772
          mouse-down               0x000000000000F873
          mouse-left               0x000000000000F570
          mouse-right              0x000000000000F671
          mouse-left_up            0x000000000000F974
          mouse-left_down          0x000000000000FC77
          mouse-right_up           0x000000000000FA75
          mouse-right_down         0x000000000000FB76
          dvd-root_menu            0x0000000000009B16
          launch_setup             0x0000000000009D18
      end codes

end remote

```

lircrc
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="ATI/NVidia X10 RF (kernel)"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES=""

# Default configuration files for your hardware if any
#LIRCD_CONF="atiusb/lircd.conf.atilibusb"
#LIRCMD_CONF=""
LIRCD_CONF="lircd.conf"

```

/home/mythtv/,mythtv/lircrc, /home/user/.mythtv/lircrc (for good measure)
```

begin
prog = mythtv
button = a
config = E
repeat = 2
end

begin
prog = mythtv
button = b
config = O
repeat = 2
end

#begin
#prog = mythtv
#button = tv
#config = Key Alt-T CurrentWindow
#repeat = 2
#end

begin
prog = mythtv
button = stop
config = Esc
repeat = 2
end

begin
prog = mythtv
button = fastforward
config = Right
repeat = 2
end

begin
prog = mythtv
button = rewind
config = Left
repeat = 2
end

begin
prog = mythtv
button = max_window
config = V
repeat = 2
end

begin
prog = mythtv
button = pause
config = P
repeat = 2
end

begin
prog = mythtv
button = play
config = P
repeat = 2
end

begin
prog = mythtv
button = mute
config = F9
repeat = 2
end

begin
prog = mythtv
button = vol-down
config = F10
repeat = 2
end

begin
prog = mythtv
button = vol-up
config = F11
repeat = 2
end

begin
prog = mythtv
button = f
config = PgDown
repeat = 2
end

begin
prog = mythtv
button = d
config = PgUp
repeat = 2
end

begin
prog = mythtv
button = c
config = F4
repeat = 2
end

begin
prog = mythtv
button = e
config = Esc
repeat = 2
end

begin
prog = mythtv
button = cursor-right
config = Right
repeat = 2
end

begin
prog = mythtv
button = cursor-left
config = Left
repeat = 2
end

begin
prog = mythtv
button = cursor-up
config = Up
repeat = 2
end

begin
prog = mythtv
button = cursor-down
config = Down
repeat = 2
end

begin
prog = mythtv
button = chan-up
config = Up
repeat = 2
end

begin
prog = mythtv
button = chan-down
config = Down
repeat = 2
end

begin
prog = mythtv
button = rewind
config = Left
repeat = 2
end

begin
prog = mythtv
button = ok
config = Enter
repeat = 2
end

begin
prog = mythtv
button = 1
config = 1
repeat = 2
end

begin
prog = mythtv
button = 2
config = 2
repeat = 2
end

begin
prog = mythtv
button = 3
config = 3
repeat = 2
end

begin
prog = mythtv
button = 4
config = 4
repeat = 2
end

begin
prog = mythtv
button = 5
config = 5
repeat = 2
end

begin
prog = mythtv
button = 6
config = 6
repeat = 2
end

begin
prog = mythtv
button = 7
config = 7
repeat = 2
end

begin
prog = mythtv
button = 8
config = 8
repeat = 2
end

begin
prog = mythtv
button = 9
config = 9
repeat = 2
end

begin
prog = mythtv
button = 0
config = 0
repeat = 2
end

begin
prog = mythtv
button = record
config = R
repeat = 2
end

begin
prog = mythtv
button = check
config = Enter
repeat = 2
end

### MPlayer lirc setup
#
# Remember to ln -s ./.mythtv/lircrc ../.lircrc for mplayer to work!

# Show OSD
begin
prog = mplayer
button = tv_on_demand
repeat = 3
config = osd
end

# Pause playback
begin
prog = mplayer
button = pause
repeat = 3
config = pause
end

begin
prog = mplayer
button = play
repeat = 3
config = pause
end

# Stop playback and exit
begin
prog = mplayer
button = stop
repeat = 3
config = quit
end

# Mute
begin
prog = mplayer
button = mute
repeat = 3
config = mute
end

# Seek back 10 seconds
begin
prog = mplayer
button = rewind
repeat = 3
config = seek -10
end

# Seek forward 30 seconds
begin
prog = mplayer
button = fastforward
repeat = 3
config = seek +30
end

# Quit
begin
prog = mplayer
button = e
repeat = 3
config = quit
end

```

lircd is running, but when I try to run irw, it will either go back to the command prompt, or will say "connection refused."

The functionality isn't any different from before however...  Why didn't it change?  Any suggestions would be appreciated.  Thanks

---

### Post by a_posse_ad_esse on 2007-11-05
Addendum:

If someone else has the same model with a working configuration, posting the relevant configs would work too.  I'm not tied to the ones above by any means, they just happened to have matched my remote number.

---

### Post by a_posse_ad_esse on 2007-11-17
Sorry, but *bump.*  Any ideas?

---

### Post by road2elysium on 2007-11-17
> **a_posse_ad_esse said:**
> Sorry, but *bump.*  Any ideas?

There's an article on this exact remote in the upstream MythTv wiki:
[http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder]("http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder")

Hope it helps.

---

### Post by a_posse_ad_esse on 2007-11-17
I thought that I had configured the remote according to the article, but I missed copying /home/mythtv/.mythtv/lircrc.  The remote works very well now.  Thank you for the input.

For those who want to configure this remote, this article is the way to go.

---

### Post by frank10 on 2007-12-08
I'm also trying to get this remote to work.  One thing is that I don't have a modprobe.conf file.  Should I just create one?

---

### Post by a_posse_ad_esse on 2007-12-09
Yes.

---

### Post by docdailey on 2007-12-12
> **frank10 said:**
> I'm also trying to get this remote to work.  One thing is that I don't have a modprobe.conf file.  Should I just create one?

I did that and it broke my boot...I had to manually go delete it using a live cd.  Those instructions have me confused.  Are we supposed to follow the fedora or open suse instructions?  I guess I don't have a good enough grasp on the dists to know which uses the same stuff as mythbuntu.

Doc

---

### Post by a_posse_ad_esse on 2007-12-12
Ouch.  I'm sorry about that.

What did you do to configure the remote in mythbuntu?  When was the last time you updated the system?  I know that there was a relatively recent update of the lirc generator.

---

### Post by docdailey on 2007-12-14
I configured it using userspace x-10 ati.  Funny thin is...if I install it stock (no config file changes etc) the remote "works" but I can't get it to escape and the mappings could be better.  does that mean I just have to "learn it" using irrecord?  I update constantly.

I blacklisted it
changed the configs 
tried the modprob.conf thing

worked on it all night the other night (bad for the next day)...huh.. done it before...will do it again...now reverted all changes back to stock so it is "usable" but non ideal



Bill

---

### Post by Joshua on 2007-12-16
I have a remote that, I think, is called the Remote Wonder, but the model number is 5000015900A.  The receiver is 5000015900B.  I've been trying to figure out how to get it to work with the link that was posted above, but so far I haven't had any luck.

If I disable the lirc_atiusb module and enable the ati_remote module, it looks like it works but I don't know how to configure the controls.  Besides, everything seems to say that the ati_remote module is old and has been incorporated into the lirc_atiusb module.  Anyone know what's going on?

---

### Post by Joshua on 2007-12-16
I guess, just to be clear, this is what I did in my attempt.

- First I selected the ATI/NVidia x10 RF (kernel) remote control configuration in Mythbuntu Control Center.  That didn't get everything working.
- added "blacklist ati_remote" to /etc/modprobe.d/blacklist
- added "alias char-major-61 lirc_atiusb" and "alias lirc_dev lirc_atiusb" to /etc/modprobe.d/aliases
- copied lircd.conf from /etc/lirc/lircd.conf to /etc/lircd.conf (is this actually necessary?)
- copied lircrc from /home/joshua/.mythtv/ircrc to /home/mythtv/.mythtv/lircrc (again, is this actually necessary if I use Mythbuntu to install everything?)
- started lircd / restarted the computer several times - the remote never works and irw never works.  irw actually looks like it causes lircd to crash.  "ps -ef | grep lircd" shows it, but then it doesn't if I run it after irw.

---

### Post by Joshua on 2007-12-17
Does anyone even know if the 5000023600 and the 5000015900 are similar enough to discuss in the same thread?

---

### Post by a_posse_ad_esse on 2007-12-17
I had the same problems with the remote out-of-the-box, such as the lack of an "esc" key, etc.  Did you change the settings in /home/user/.mythtv/lircrc?  That is the important one I believe.

You may also need to rmmod the old module.

---

### Post by Joshua on 2007-12-18
What do you mean by change the settings?  What settings need to be changed?

I copied the lircrc file that Mythbuntu created from /home/joshua/.mythtv/lircrc to /home/mythtv/.mythtv/lircrc.

Also, I have done
```
rmmod ati_remote
modpobe lirc_atiusb
lircd
```
but the remote won't work at all then.

I think that should give the idea, but I'm working blind.  There seems to be a bug in mdadm that is preventing me from booting right now.

---

### Post by a_posse_ad_esse on 2007-12-19
I should have been more clear.  The posted configurations on the first page are what got the remote working for me.  The problem with the settings that mythbuntu creates is that, while they work somewhat, they lack some primary functionalities such as the "esc" key.  My recommendation would be to backup your existing copy of lircrc and try the configuration listed in this thread.

---

### Post by LtPitt on 2008-02-24
Hello, everybody!

I've tried to follow accurately all the instructions and now I finally get the irw command fully working and listing me all the buttons of my remote accurately.

Next (and final) step would be to be able to use MythTV with it...

I've copied the lircrc file in many different locations

/home/user

/home

/home/mythtv

/home/user/.mythtv

...
Almost everywhere...
But it's not working...

Another thing is that my fresh install of 7.10 somewhat allowed me to use the remote controller with the basic driver as a "mouse emulator".
Since I installed LIRC and blacklisted the general driver coming with 7.10 I've lost this function...
Anybody has idea about how to restore it? :(

Thanks!

---

### Post by a_posse_ad_esse on 2008-02-25
You need to have mythtv own the file.  It is one of those little things that will get you.

As for the mouse emulation, mine doesn't work either.  I haven't needed it, so I haven't done much looking.  I wouldn't know where to start, but if you have a lead I might be able to help.

---

### Post by LtPitt on 2008-02-25
aw!

Thank you for your accurate and promt answer!
=D

You mean that I have to change permission on the file, right?
Where should I put the file?
Is there any way (sorry I'm a newbie =_= ) to put a linux file on everyone/full control to avoid any further problem?

I've googled a bit for mouse emulation but I've found only bad news:

"You don't have to use lirc for this remote, you can use the ati_usb 
driver ([http://gatos.sf.net](http://gatos.sf.net))... that way you can use the mouse emulation

too (lirc doesn't support the mouse emulation thing...)"

This maybe means that if I take ati_usb out of the blacklist and stop lirc everything should work like when I didn't install lirc?
As soon as I go home (I'm @ work, now) I'll try and write my results...
Thank you once again! =)

---

### Post by LtPitt on 2008-02-25
O_O

hot hot news:

"OK. Got rid of and blacklisted lirc_atiusb. Got the numbers, letters, directionals, "enter" (checkmark at bottom left of controller) and mouse emulation working correctly.

Now, I understand I should use gizmo daemon to get the rest of the keys working. I installed python and gizmod, setup gizmod to run on startup, and here are my symptoms:

1) All keys that work before no longer work
2) Only key on remote that works is the "power" button, which opens up another "mythfrontend"

I'm not really a programmer, so the python configs that came w/ gizmod make no sense to me. How do I configure gizmod to turn the rest of my buttons other than power into keyboard keypresses (which I could then set to functions in mythtv)?"

Maybe this "gizmo" is the final and total solution...

---

### Post by LtPitt on 2008-02-26
This is me being happy!!!

loading this little program:

sudo mythbuntu-lircrc-generator

MY ATI REMOTE IS WOOORRRKIIINGGG!!!!

YAAY!!!!
YIPPEEEE!!!!

In MythTV!!!
I was surely wrong with some path and or permission... 
I'm happy :'(

But some buttons are not working...
Like up down left and right...

Any hints? Also volume doesn't work properly...
I think it's related to the fact that when I try those buttons I'm in the video player, maybe...

ps also the "esc" button works =)

I'm really CLOSE to heaven now thanks

ps
anyone knows about hot use mouse emulation too?

---

### Post by LtPitt on 2008-02-27
Everything just work perfectly =)

I just used the info that we have in this topic just and hopped to:
[http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder](http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder)
for the configuration files

Everything is really perfect!

The key was to write a good .lircrc file and put it in the home folder.

Now my remote works perfectly =)

I'm just trying to find out about mouse emulation and how to load mythtv pressing one button and use another button to shutdown the computer.

But this is more than what I was looking for at the beginning.

Thanks to everybody! =)

If anybody needs help I'm here

---

### Post by Panik on 2008-02-29
For the life of me, I can't seem to be getting this thing to work.

I think I have followed the instructions, but am going about nuts.  The link to the wiki is not specific to mythbuntu.  So neither walk throughs are correct from what I can tell.  

Can someone please step me through this including code.  I'm about losing my mind trying to figure this out.

---

### Post by LtPitt on 2008-02-29
Step 1

Don't panic! :D


Step 2

What have you done and which error do you get?
Is lirc installed and running?
Have you prepared and placed in the right folders the configuration files?

---

### Post by Panik on 2008-03-01
I will do my best to walk through what I did.  Hopefully you will see something.

My install is Mythbuntu 7.10 and clean

First I plugged in the RF receiver.  Oddly enough, the mouse emulator thingy worked but most all the buttons didn't.  So I figured I would attempt to follow this thread and the wiki.

Then I went somewhat in this order (I think)

1) I unplugged the RF receiver then blacklisted the ati_remote in /etc/modprobe.d/blacklist

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

blacklist ati_remote
```

2) Typed in lsmod | grep ati and get:

> lirc_atiusb            19530  1 
lirc_dev               15860  1 lirc_atiusb
usbcore               138632  8 lirc_atiusb,xpad,snd_usb_audio,snd_usb_lib,usbhi

3) Created file /etc/modprobe.conf and pasted the following into it:

> 
alias char-major-61 lirc_atiusb
alias lirc_dev lirc_atiusb

4) I created and copied the contents of the example lircd.conf config file to /etc/lircd.conf

```
# brand: ATI Remote Wonder
# model no. of remote control: 5000023600
# devices being controlled by this remote: ATI USB Receiver
#
# Found on a linpvr.org forum, thanks.

begin remote

  name  ati_remote
  bits           40
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          235966
  toggle_bit      0


      begin codes
          a                        0x00000014D5000000
          b                        0x00000014D6010000
          power                    0x00000014D7020000
          tv                       0x00000014D8030000
          dvd                      0x00000014D9040000
          web                      0x00000014DA050000
          media_library            0x00000014DB060000
          drag                     0x00000014DC070000
          mouse-button_left        0x000000144D780000
          mouse-button_right       0x00000014517C0000
          mouse-up                 0x0000001447720000
          mouse-down               0x0000001448730000
          mouse-left               0x0000001445700000
          mouse-right              0x0000001446710000
          mouse-left_up            0x0000001449740000
          mouse-right_up           0x000000144A750000
          mouse-left_down          0x000000144C770000
          mouse-right_down         0x000000144B760000
          vol-up                   0x00000014DD080000
          vol-down                 0x00000014DE090000
          mute                     0x00000014DF0A0000
          chan-up                  0x00000014E00B0000
          chan-down                0x00000014E10C0000
          1                        0x00000014E20D0000
          2                        0x00000014E30E0000
          3                        0x00000014E40F0000
          4                        0x00000014E5100000
          5                        0x00000014E6110000
          6                        0x00000014E7120000
          7                        0x00000014E8130000
          8                        0x00000014E9140000
          9                        0x00000014EA150000
          0                        0x00000014EC170000
          dvd-root_menu            0x00000014EB160000
          launch_setup             0x00000014ED180000
          c                        0x00000014EE190000
          d                        0x00000014F01B0000
          tv_on_demand             0x00000014F11C0000
          max_window               0x00000014F5200000
          cursor-up                0x00000014EF1A0000
          cursor-down              0x00000014F7220000
          cursor-left              0x00000014F21D0000
          cursor-right             0x00000014F41F0000
          ok                       0x00000014F31E0000
          e                        0x00000014F6210000
          f                        0x00000014F8230000
          rewind                   0x00000014F9240000
          play                     0x00000014FA250000
          fastforward              0x00000014FB260000
          record                   0x00000014FC270000
          stop                     0x00000014FD280000
          pause                    0x00000014FE290000
      end codes

end remote
```


5) I saved the following to /home/mythtv/.mythtv/lircrc and /home/jim/.mythtv/lircrc

```
#
# MythTV native LIRC config file for
# the ATI-Wonder Remote
# using lirc_atiusb driver
#

begin
prog = mythtv
button = a
config = E
repeat = 2
end

begin
prog = mythtv
button = b
config = O
repeat = 2
end

#begin
#prog = mythtv
#button = tv
#config = Key Alt-T CurrentWindow
#repeat = 2
#end

begin
prog = mythtv
button = stop
config = Esc
repeat = 2
end

begin
prog = mythtv
button = fastforward
config = Right
repeat = 2
end

begin
prog = mythtv
button = rewind
config = Left
repeat = 2
end

begin
prog = mythtv
button = max_window
config = V
repeat = 2
end

begin
prog = mythtv
button = pause
config = P
repeat = 2
end

begin
prog = mythtv
button = play
config = P
repeat = 2
end

begin
prog = mythtv
button = mute
config = F9
repeat = 2
end

begin
prog = mythtv
button = vol-down
config = F10
repeat = 2
end

begin
prog = mythtv
button = vol-up
config = F11
repeat = 2
end

begin
prog = mythtv
button = f
config = PgDown
repeat = 2
end

begin
prog = mythtv
button = d
config = PgUp
repeat = 2
end

begin
prog = mythtv
button = c
config = F4
repeat = 2
end

begin
prog = mythtv
button = e
config = Esc
repeat = 2
end

begin
prog = mythtv
button = cursor-right
config = Right
repeat = 2
end

begin
prog = mythtv
button = cursor-left
config = Left
repeat = 2
end

begin
prog = mythtv
button = cursor-up
config = Up
repeat = 2
end

begin
prog = mythtv
button = cursor-down
config = Down
repeat = 2
end

begin
prog = mythtv
button = chan-up
config = Up
repeat = 2
end

begin
prog = mythtv
button = chan-down
config = Down
repeat = 2
end

begin
prog = mythtv
button = rewind
config = Left
repeat = 2
end

begin
prog = mythtv
button = ok
config = Enter
repeat = 2
end

begin
prog = mythtv
button = 1
config = 1
repeat = 2
end

begin
prog = mythtv
button = 2
config = 2
repeat = 2
end

begin
prog = mythtv
button = 3
config = 3
repeat = 2
end

begin
prog = mythtv
button = 4
config = 4
repeat = 2
end

begin
prog = mythtv
button = 5
config = 5
repeat = 2
end

begin
prog = mythtv
button = 6
config = 6
repeat = 2
end

begin
prog = mythtv
button = 7
config = 7
repeat = 2
end

begin
prog = mythtv
button = 8
config = 8
repeat = 2
end

begin
prog = mythtv
button = 9
config = 9
repeat = 2
end

begin
prog = mythtv
button = 0
config = 0
repeat = 2
end

begin
prog = mythtv
button = record
config = R
repeat = 2
end

begin
prog = mythtv
button = check
config = Enter
repeat = 2
end

### MPlayer lirc setup
#
# Remember to ln -s ./.mythtv/lircrc ../.lircrc for mplayer to work!

# Show OSD
begin
prog = mplayer
button = tv_on_demand
repeat = 3
config = osd
end

# Pause playback
begin
prog = mplayer
button = pause
repeat = 3
config = pause
end

begin
prog = mplayer
button = play
repeat = 3
config = pause
end

# Stop playback and exit
begin
prog = mplayer
button = stop
repeat = 3
config = quit
end

# Mute
begin
prog = mplayer
button = mute
repeat = 3
config = mute
end

# Seek back 10 seconds
begin
prog = mplayer
button = rewind
repeat = 3
config = seek -10
end

# Seek forward 30 seconds
begin
prog = mplayer
button = fastforward
repeat = 3
config = seek +30
end

# Quit
begin
prog = mplayer
button = e
repeat = 3
config = quit
end
```

6) I changed ownership from root to jim with group users (no mythtv user) for both versions of lircrc

7) I start lircd (I must start with sudo or I get an Permission Denied response)

8) I verified it was running with ps -ef | grep lircd

> root      8920     1  0 22:33 ?        00:00:00 lircd
jim       9061  9043  0 22:54 pts/0    00:00:00 grep lircd

9) I type "irw" with no response (eg, seems to accept, but I don't think irw is running)

10) I type "irw" again and get 
> 
connect: Connection refused

Couple of things I noted:

When I boot my system with the RF remote, it locks up in the beggining of the boot.  If I remove from the USB port, it boots fine.

When I start lircd (via sudo) and look in the /var/run folder, the file lircd.pid exists.  Then, when I run irw Once, while looking at the lircd.pid file in Thunar, it vanishes.  Then I get the "Connection refused" response when I type irw again.  

I must be missing the obvious, but please help.  I'm such a linux newb it's crazy.

Thanks.

---

### Post by LtPitt on 2008-03-01
It's true! :D

I went crazy in the same way!

I think you did fine the only problem is that the DAMN .lircrc file (look exactly at the name: it includes the "dot" at the beginning) goes in the

/home/user folder.

so, for me it's in

/home/pitto/.lircrc

:D

---

### Post by LtPitt on 2008-03-01
ps

I blacklisted the wrong module like you but to run the right module on each startup I added to /etc/rc.local this:

modprobe lirc_atiusb


it went pefect!

Now I'm trying to shut the system down from the remote but the shutdown command's quite a bitch :/

---

### Post by Panik on 2008-03-01
> **LtPitt said:**
> ps

I blacklisted the wrong module like you but to run the right module on each startup I added to /etc/rc.local this:

modprobe lirc_atiusb


it went pefect!

Now I'm trying to shut the system down from the remote but the shutdown command's quite a bitch :/

OK, i put the .lircrc in /home/jim/.lircrc and modded the ownership to jim:users

I included the DOT

Still acting the same.  Not sure I understand your above statement.  "Blacklisted the wrong module".  It is still blacklisted like I posted.  How exactly should I do it differently?  I'm a bit confused.

Thanks for the help!!!

---

### Post by LtPitt on 2008-03-01
Sorry: I meant to blacklist the standard ati module =)

One more information:
when you run irw in terminal and use the remote wonder you get any output?

I upload my lircd folder (/etc/lirc/)

I hope you find it useful... =)


(if you don't find this post attachment you can download it from [http://www.lucidaebbrezza.it/lirc.zip](http://www.lucidaebbrezza.it/lirc.zip)

:)

---

