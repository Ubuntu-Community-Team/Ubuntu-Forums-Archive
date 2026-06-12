---
title: "Remote works....but not with mythtv"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by shingalated on 2007-08-10
I needed a remote for mythtv so I purchased a mce1039 (windows media center remote) from newegg...I spent all day trying to get it working.  I finally got linirc installed and the mceusb2 module working correctly, but it will  not work in mythtv.  Works fine in irw:```
chris@Linus:~$ irw
000000037ff07bf2 00 Home mceusb
000000037ff07bf2 01 Home mceusb
000000037ff07bfd 00 Two mceusb
000000037ff07bfd 01 Two mceusb
000000037ff07bfd 02 Two mceusb

```

I have copied the lircrc file to /home/chris/.mythtv/ AND /etc/lirc/ AND /etc/
I run mythtv from my own account "chris" and not from mythtv... Can anyone help?

---

### Post by morgwon on 2007-08-11
I am on the same boat as you. Was about to post a thread. Do you have the lirc modules loaded into /etc/modules?

---

### Post by newlinux on 2007-08-11
can you post your /home/chris/.mythtv/lircrc file for us to look at, as well as your /etc/lirc/lircd.conf file?

---

### Post by morgwon on 2007-08-11
dont mean to hijack your thread Chris but we have the same issue and I don't think we need two threads for the same issue

lircd.conf

```

begin remote
  name            iMON-PAD  
  bits            32  
  eps             30  
  aeps            100  
  one             0     0  
  zero            0     0  
  gap             235965  

  begin codes
       AppExit         0x288195B7
       Standby         0x289115B7
       Record          0x298115B7
       Play            0x2A8115B7
       SlowMotion      0x29B195B7
       Rewind          0x2A8195B7
       Pause           0x2A9115B7
       FastForward     0x2B8115B7
       PrevChapter     0x2B9115B7
       Stop            0x2B9715B7
       NextChapter     0x298195B7
       Esc             0x2BB715B7
       Eject           0x299395B7
       AppLauncher     0x29B715B7
       MultiMon        0x2AB195B7
       TaskSwitcher    0x2A9395B7
       Mute            0x2B9595B7
       Vol+            0x28A395B7
       Vol-            0x28A595B7
       Ch+             0x289395B7
       Ch-             0x288795B7
       Timer           0x2B8395B7
       1               0x28B595B7
       2               0x2BB195B7
       3               0x28B195B7
       4               0x2A8595B7
       5               0x299595B7
       6               0x2AA595B7
       7               0x2B9395B7
       8               0x2A8515B7
       9               0x2AA115B7
       0               0x2BA595B7
       ShiftTab        0x28B515B7
       Tab             0x29A115B7
       MyMovie         0x2B8515B7
       MyMusic         0x299195B7
       MyPhoto         0x2BA115B7
       MyTV            0x28A515B7
       Bookmark        0x288515B7
       Thumbnail       0x2AB715B7
       AspectRatio     0x29A595B7
       FullScreen      0x2AA395B7
       MyDVD           0x29A395B7
       Menu            0x2BA395B7
       Caption         0x298595B7
       Language        0x2B8595B7
       MouseKeyboard   0x299115B7
       SelectSpace     0x2A9315B7
       MouseMenu       0x28B715B7
       MouseRightClick 0x688481B7
       Enter           0x28A195B7
       MouseLeftClick  0x688301B7
       WindowsKey      0x2B8195B7
       Backspace       0x28A115B7
       #               smd: Pad codes added from mode2 codes (Pad is pres
       Up              0x6902C1B7
       Left            0x6AC2A1B7
       Down            0x6AEAF9B7
       Right           0x697AE9B7
                       

  end codes

end remote
```

Lircrc

```
# Record
begin
  prog = mythtv
  remote = iMON-PAD
  button = Record
  repeat = 2
  config = R
end

# Skip Backwards
begin
  prog = mythtv
  remote = iMON-PAD
  button = Rewind
  repeat = 2
  config = PgUp
end

# Pause
begin
  prog = mythtv
  remote = iMON-PAD
  button = Pause
  repeat = 2
  config = P
end

# Skip Forward
begin
  prog = mythtv
  remote = iMON-PAD
  button = FastForward
  repeat = 2
  config = PgDown
end

# Previous Commercial Cut
begin
  prog = mythtv
  remote = iMON-PAD
  button = PrevChapter
  repeat = 2
  config = Q
end

# Stop
begin
  prog = mythtv
  remote = iMON-PAD
  button = Stop
  repeat = 2
  config = T
end

# Next Commercial Cut Forward
begin
  prog = mythtv
  remote = iMON-PAD
  button = NextChapter
  repeat = 2
  config = Z
end

# Cancel / Back
begin
  prog = mythtv
  remote = iMON-PAD
  button = Esc
  repeat = 2
  config = Esc
end

# Change PiP Focus
begin
  prog = mythtv
  remote = iMON-PAD
  button = AppLauncher
  repeat = 2
  config = B
end

# PiP On-Off Toggle
begin
  prog = mythtv
  remote = iMON-PAD
  button = MultiMon
  repeat = 2
  config = V
end

# Swap PIP Windows
begin
  prog = mythtv
  remote = iMON-PAD
  button = TaskSwitcher
  repeat = 2
  config = N
end

# Mute
begin
  prog = mythtv
  remote = iMON-PAD
  button = Mute
  repeat = 2
  config = F9
end

# Volume Down
begin
  prog = mythtv
  remote = iMON-PAD
  button = Vol+
  repeat = 2
  config = F10
end

# Volume Up
begin
  prog = mythtv
  remote = iMON-PAD
  button = Vol-
  repeat = 2
  config = F11
end


begin
  prog = mythtv
  remote = iMON-PAD
  button = 1
  repeat = 2
  config = 1
end


begin
  prog = mythtv
  remote = iMON-PAD
  button = 2
  repeat = 2
  config = 2
end


begin
  prog = mythtv
  remote = iMON-PAD
  button = 3
  repeat = 2
  config = 3
end


begin
  prog = mythtv
  remote = iMON-PAD
  button = 4
  repeat = 2
  config = 4
end


begin
  prog = mythtv
  remote = iMON-PAD
  button = 5
  repeat = 2
  config = 5
end


begin
  prog = mythtv
  remote = iMON-PAD
  button = 6
  repeat = 2
  config = 6
end


begin
  prog = mythtv
  remote = iMON-PAD
  button = 7
  repeat = 2
  config = 7
end


begin
  prog = mythtv
  remote = iMON-PAD
  button = 8
  repeat = 2
  config = 8
end


begin
  prog = mythtv
  remote = iMON-PAD
  button = 9
  repeat = 2
  config = 9
end

# Number Zero
begin
  prog = mythtv
  remote = iMON-PAD
  button = 0 
  repeat = 2
  config = 0
end

# Change Aspect Ratio
begin
  prog = mythtv
  remote = iMON-PAD
  button = AspectRatio
  repeat = 2
  config = W
end

# Menu
begin
  prog = mythtv
  remote = iMON-PAD
  button = Menu
  repeat = 2
  config = M
end


begin
  prog = mythtv
  remote = iMON-PAD
  button = SelectSpace
  repeat = 2
  config = Space
end

# OSD browse
begin
  prog = mythtv
  remote = iMON-PAD
  button = MouseRightClick
  repeat = 2
  config = O
end

# Select
begin
  prog = mythtv
  remote = iMON-PAD
  button = Enter
  repeat = 2
  config = Return
end

# Show OSD
begin
  prog = mythtv
  remote = iMON-PAD
  button = MouseLeftClick
  repeat = 2
  config = I
end

# Delete
begin
  prog = mythtv
  remote = iMON-PAD
  button = Backspace
  repeat = 2
  config = D
end


begin
  prog = mythtv
  remote = iMON-PAD
  button = Up
  repeat = 2
  config = Up
end


begin
  prog = mythtv
  remote = iMON-PAD
  button = Left
  repeat = 2
  config = Left
end


begin
  prog = mythtv
  remote = iMON-PAD
  button = Down
  repeat = 2
  config = Down
end


begin
  prog = mythtv
  remote = iMON-PAD
  button = Right
  repeat = 2
  config = Right
end


```

Here is what is in /etc/modules

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
cx88_dvb
lirc_imon
lirc_dev

```

I have a Silverstone Lascala LC10M with the Soundgraph iMON VFD/IR

output of lsusb

```
Bus 006 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 05af:0408 Jing-Mold Enterprise Co., Ltd
Bus 002 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 004 Device 001: ID 0000:0000

```

output of: ls -l /dev/l*

```
crw-rw---- 1 root root 180, 144 2007-08-11 00:19 /dev/lcd0
crw-rw---- 1 root root  61,   0 2007-08-11 00:19 /dev/lirc0
srw-rw-rw- 1 root root        0 2007-08-11 00:38 /dev/lircd
srw-rw-rw- 1 root root        0 2007-08-11 00:20 /dev/log
brw------- 1 root root   7,   0 2007-05-08 00:52 /dev/loop0
crw-rw---- 1 root lp     6,   0 2007-08-11 00:20 /dev/lp0

```

I am running Feisty with lirc 0.8.1. IRW recognizes everything in my lircd.conf file. Are there any permissions that have to set so mythtv can use my iMON-PAD. This is on a backend/frontend system. I followed the guide from [Ubuntu Documentation]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend"). This is the last piece to my mythtv setup and then I can get rid of the stinking tivo. Any help is appreciated and if I can figure anything out I will post here.

---

### Post by morgwon on 2007-08-13
anybody have any ideas for either Chris or I to try?

---

### Post by praet on 2007-08-14
Take a look at the following:

[http://www.wilsonet.com/mythtv/fcmyth.php#lirc](http://www.wilsonet.com/mythtv/fcmyth.php#lirc)
[http://www.mythtv.org/wiki/index.php/MCE_Remote#Configuring_the_Buttons](http://www.mythtv.org/wiki/index.php/MCE_Remote#Configuring_the_Buttons)
The two example config files are posted here:
[http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib/configfiles/lircrc.native.example.mceusb2](http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib/configfiles/lircrc.native.example.mceusb2)
[http://www.hauppauge.co.uk/board/showthread.php?t=8048](http://www.hauppauge.co.uk/board/showthread.php?t=8048) 
The 


Basically if your irw is showing all your buttons when you press them then you've got the remote working.  Now what you have to do is configure lirc to map the result to buttons.

---

### Post by newlinux on 2007-08-15
Assuming all the files are in the right place these files look good. IRW is reporting output so the Ir receiver is definitely receiving and transmittign signals. Sorry I couldn't be of much more help. Have you tried getting LIRC to work with mplayer or another application to rule out myth as the problem (maybe write a short irexec script  to test with LIRC).

---

### Post by morgwon on 2007-08-15
I don't have any other apps installed in my setup since all it is backend/frontend and I like the internal mythtv player.

I have my lircd.conf in /etc/lirc/ and I have lircrc file in /home/morgwon/.mythtv/ and /home/mythtv/.mythtv/

Here is the output of dmesg | grep -i lirc 

```
[   10.095131] lirc_dev: IR Remote Control driver registered, at major 61
[   10.102619] lirc_imon: no version for "lirc_unregister_plugin" found: kernel tainted.
[   10.103279] /usr/src/modules/lirc/drivers/lirc_imon/lirc_imon.c: Driver for Soundgraph iMON MultiMedian IR/VFD, v0.3
[   10.103282] /usr/src/modules/lirc/drivers/lirc_imon/lirc_imon.c: Venky Raju <dev@venky.ws>
[   10.442519] /usr/src/modules/lirc/drivers/lirc_imon/lirc_imon.c: imon_probe: found IMON device
[   10.442524] lirc_dev: lirc_register_plugin: sample_rate: 0
[   10.442574] /usr/src/modules/lirc/drivers/lirc_imon/lirc_imon.c: imon_probe: Registered iMON plugin (minor:0)
[   10.442604] /usr/src/modules/lirc/drivers/lirc_imon/lirc_imon.c: imon_probe: iMON device on usb<4:2> initialized
[   10.442612] usbcore: registered new interface driver lirc_imon
[   43.332144] /usr/src/modules/lirc/drivers/lirc_imon/lirc_imon.c: IR port opened

```


in case this is needed here are the contents of hardware.conf



```
# /etc/lirc/hardware.conf
#
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
MODULES="lirc_imon"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""

```

Should I insert the path to my lircd.conf file?

---

### Post by morgwon on 2007-08-15
got it working. For some reason linking the file to the one in my home directory was not working

this is what I tried

```
ln -s ~/.lircrc /home/mythtv/lircrc
```

but when I would run

```
ls -l ~/.lircrc
```

I would get

```
-rw-r--r-- 1 root root 2709 2007-08-15 19:26 /home/morgwon/.lircrc
```

so it would not show it linked to anything. I just copied the .lircrc file over to /home/mythtv/.mythtv/lircrc and the remote started working after reboot. Thanks for the help guys and good luck with your Chris.

---

### Post by newlinux on 2007-08-15
```
ln -s ~/.lircrc /home/mythtv/lircrc
```

would create a softlink from /home/mythtv/lircrc to /home/morgwon/.lircrc, meaning that the actual file is expected to be /home/morgwon/.lircrc, and /home/mythtv/lircrc is a link to that file. So the link you actually created with that command is at /home/mythtv/lircrc (type ls -l /home/mythtv/lircrc).

If what you wanted was a link from /home/mythtv/.mythtv/lircrc and the file was at /home/morgwon/.lircrc and you are logged in as morgwon than what you would type to link them is:
```

ln -s ~/.lircrc /home/mythtv/.mythtv/lircrc

```

Which is what you would want to do if you run myth as the mythtv user... 

Also you don't need to reboot when you do this, just restart mythfrontend. This is also all you need to do if you make changes to the lircrc file. Just an FYI.

Glad you got it working. Sounded like a location problem in the first place, since everything else was working. Happy mything.

---

### Post by shingalated on 2007-08-20
Well I am all set now...I had numbers at the beginning of each line that I thought were commented, but apparently they weren't...Had to manually remove all the numbers and now I'm fine, I doubt that will help the rest of you guys though....

---

### Post by eagle63 on 2007-08-20
Hey guys, I just installed Myth on Feisty and am now facing the task of getting my remote working.  (M$ media center remote)  

Looking at the Feisty install section, it states that " Lirc now includes support for mceusb2 and pvr150 IR transmitters from the Ubuntu package". 

Doesn't this mean I can just install lirc from the repository without having to mess with kernel modules and such?  Or is there more to it than that?

---

### Post by newlinux on 2007-08-20
A little more to it from this, unless something's changed... I think that may just be referring to a blaster...

[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

---

### Post by NJHokie on 2007-10-02
Hopefully people are still watching this thread, if not, i'll create a new one.

I am having the same issue here and have tired everything this thread has stated and the information found in others.  

It seems like lirc is not starting when mythtv starts.  Is there a way to force this or check it?  
My remote works fine when i test with irw, and i have cross checked my lircd.conf and .lircrc files to make sure they match up.  

Any help would be greatly appreciated.  Thanks!

---

### Post by NJHokie on 2007-10-02
nm you all.  I got it to work.  it was the wrong file format. 
my lircrc file was in DOS format, not unix, that was the problem.  

now it works!  

Thanks!

---

### Post by uwditto on 2007-10-20
I also am having trouble getting the remote to work in MythTv.  I had everything working fine and then I ended up having to reinstall things when it was time to change to Schedules Direct from the Zap2it server...anywho, I have everything up and working, lirc even recognizes the correct remote inputs (IRW shows me the buttons I'm pressing) but I can't get it to work in mythtv.  I've spent hours scouring forums and trying to get things working, but to no avail.  Any help would be appreciated.

It sounds like it's just a file location/format issue or something because the lirc recognizes the remote, but I can't seem to figure out the issue.

I'm not posting this from the computer mythtv is on, but I'll post the lircrc file I have later.

My lircrc file is located in ~/.lircrc and it is linked to ~/.mythtv/lircrc.

I've checked the the 'buttons' in the lircrc file match that of the lircd.conf file.

Any help would be appreciated.

Thanks!

---

### Post by superm1 on 2007-10-21
> **uwditto said:**
> I also am having trouble getting the remote to work in MythTv.  I had everything working fine and then I ended up having to reinstall things when it was time to change to Schedules Direct from the Zap2it server...anywho, I have everything up and working, lirc even recognizes the correct remote inputs (IRW shows me the buttons I'm pressing) but I can't get it to work in mythtv.  I've spent hours scouring forums and trying to get things working, but to no avail.  Any help would be appreciated.

It sounds like it's just a file location/format issue or something because the lirc recognizes the remote, but I can't seem to figure out the issue.

I'm not posting this from the computer mythtv is on, but I'll post the lircrc file I have later.

My lircrc file is located in ~/.lircrc and it is linked to ~/.mythtv/lircrc.

I've checked the the 'buttons' in the lircrc file match that of the lircd.conf file.

Any help would be appreciated.

Thanks!
You may consider running mythbuntu-lirc-generator.  It will regenerate the button mapping in ~/.lircrc and ~/.mythtv/lircrc for you.  This will then get around issues like extra whitespace at the end of the lines or any other similar annoyances that you are missing.

---

### Post by uwditto on 2007-10-22
that sounds like a good suggestion.  I tried getting the mythbuntu-lircrc-generator, but (probably since I am quite a noob) I'm not sure how to install it on feisty.  I can't find it on the synaptic package manager and when I try downloading it and installing it I get an "error: dendancy is not satisfiable: lirc"...but I have lirc, so I'm not sure what that means.

Thanks for all the help!

---

### Post by superm1 on 2007-10-22
> **uwditto said:**
> that sounds like a good suggestion.  I tried getting the mythbuntu-lircrc-generator, but (probably since I am quite a noob) I'm not sure how to install it on feisty.  I can't find it on the synaptic package manager and when I try downloading it and installing it I get an "error: dendancy is not satisfiable: lirc"...but I have lirc, so I'm not sure what that means.

Thanks for all the help!
Sorry you've got to be on gutsy for it to work :(

---

### Post by uwditto on 2007-10-22
bummer.  would the next best thing be to just write the file from scratch?  The file I'm using is from the site where you enter the buttons you want and it generates the file.  It's just strange that it won't work (not to mention frustrating) no matter what I try.

---

### Post by superm1 on 2007-10-22
Well my vote is personally to upgrade to gutsy.  There are utilities to check your lircrc file though too.

Look at

```
man ircat
```

---

### Post by uwditto on 2007-10-27
Well, somehow it's working now!!!  Thanks for all your suggestions.  I'm not sure what the deciding factor was, but after I ran the code you suggested, everything worked.  I have to say that I'm a noob to ubuntu and mythtv, but although it's sometimes very difficult to learn an new system and have to "compile" things and do things on the command line, I have really come to enjoy the freedom, possibilities and power of things that can be done.  I can see myself using this system for a long time to come.  Thanks!

---

