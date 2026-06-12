---
title: "mythtv/lirc question"
date: 2006-12-14
forum: Multimedia &amp; Video
---

### Post by autigers20 on 2006-12-14
i've recently installed mythtv on ubuntu edgy and have gotten the lirc package installed and can see that my remote works by running irw and getting the correct output when buttons are pressed. however, the remote doesn't work at all in mythtv. i'm pretty sure i've got the correct lircrc configuration for my remote, so i'm thinking that maybe the mythtv package did not have the native lirc support compiled in. i just used the "apt-get install mythtv" command to install myth, so is there any way to know if native lirc support is enabled in the build i'm using?

---

### Post by superm1 on 2006-12-15
> **autigers20 said:**
> i've recently installed mythtv on ubuntu edgy and have gotten the lirc package installed and can see that my remote works by running irw and getting the correct output when buttons are pressed. however, the remote doesn't work at all in mythtv. i'm pretty sure i've got the correct lircrc configuration for my remote, so i'm thinking that maybe the mythtv package did not have the native lirc support compiled in. i just used the "apt-get install mythtv" command to install myth, so is there any way to know if native lirc support is enabled in the build i'm using?

Lirc support is included for MythTV in Edgy.

MythTV does something funky though where it doesn't use the userwide lircrc.  It uses its own in ~/.mythtv/lircrc.  If you want to just make it use the user wide one, make a symlink to it.

```
ln -s ~/.lircrc ~/.mythtv/lircrc
```

---

### Post by autigers20 on 2006-12-15
> **superm1 said:**
> Lirc support is included for MythTV in Edgy.

MythTV does something funky though where it doesn't use the userwide lircrc.  It uses its own in ~/.mythtv/lircrc.  If you want to just make it use the user wide one, make a symlink to it.

```
ln -s ~/.lircrc ~/.mythtv/lircrc
```

i've tried the symlink and i've also tried just copying the file there - but still no results. the only other thing i can think of is maybe i have the wrong .lircrc file - i'm using one for the mceusb2 remote because the mceusb2 lirc.conf file works with my remote, but i'm not entirely sure what remote i have. it looks like this: [http://registration.hauppauge.com/webstore/images/pv150_mcekit.jpg](http://registration.hauppauge.com/webstore/images/pv150_mcekit.jpg)

can anyone tell me exactly what remote that is?

---

### Post by majoridiot on 2006-12-15
that's the mce remote.  you are correct.

---

### Post by autigers20 on 2006-12-15
> **majoridiot said:**
> that's the mce remote.  you are correct.

all right. so theoretically i have the correct lirc.conf and .lircrc files, and according to the user above mythtv (install with apt-get) should have native lirc support built-in. anyone else got any suggestions for me?

---

### Post by superm1 on 2006-12-15
> **autigers20 said:**
> all right. so theoretically i have the correct lirc.conf and .lircrc files, and according to the user above mythtv (install with apt-get) should have native lirc support built-in. anyone else got any suggestions for me?
Well the easiest way to track down the problem is with irw.

```
irw
```

with lircd running, irw will listen for remote events when you press buttons.
So if you press up, you will receive whatever you mapped that as in /etc/lirc/lircd.conf.
If irw isn't working for you, the trouble is either lircd not running or a faulty /etc/lirc/lircd.conf.

The next useful app for testing is ircat.  It also requires lircd to be running, but it is used to debug your .lircrc file.

Your run it as 
```
ircat PROGRAM
```

Where PROGRAM is the name of the program that you want to test the mapped buttons in your .lircrc.

Catch my drift here?

---

### Post by jafenske on 2006-12-16
I'm having the same problem, I followed the advice from above, when I run
```
irw
```
I get
```
000000037ff07be1 00 Up mceusb
000000037ff07be1 01 Up mceusb
000000037ff07be1 00 Up mceusb
000000037ff07be1 01 Up mceusb
000000037ff07be1 02 Up mceusb
000000037ff07be1 00 Up mceusb
000000037ff07be1 01 Up mceusb
000000037ff07bf4 00 Enter mceusb
000000037ff07bf4 01 Enter mceusb
000000037ff07bf4 02 Enter mceusb
000000037ff07bf5 00 Clear mceusb
000000037ff07bf5 01 Clear mceusb

``` 
So thats OK
When I run
```
ircat /home/mythtv/.mythtv/.lircrc
```
I don't get any change... So I think my .lircrc is the problem.  Below is that file, can someone look over it and let me know what the problem is? Thanks
```
begin
    prog = mythtv
    button = Off
    config = Esc
end

begin
    prog = mythtv
    button = Go
# Swap the PiP windows
    config = N
end

begin
    prog = mythtv
    button = 1
    config = 1
end

begin
    prog = mythtv
    button = 2
    config = 2
end

begin
    prog = mythtv
    button = 3
    config = 3
end

begin
    prog = mythtv
    button = 4
    config = 4
end

begin
    prog = mythtv
    button = 5
    config = 5
end

begin
    prog = mythtv
    button = 6
    config = 6
end

begin
    prog = mythtv
    button = 7
    config = 7
end

begin
    prog = mythtv
    button = 8
    config = 8
end

begin
    prog = mythtv
    button = 9
    config = 9
end

begin
    prog = mythtv
    button = Back/Exit
    config = Esc
end

begin
    prog = mythtv
    button = 0
    config = 0
end

begin
    prog = mythtv
    button = Menu
    config = M
end

# Below are keys used with the Hauppauge Grey remote

begin
   prog = mythtv
# This is the Red key
# We'll use it for "Delete"
   button = Red
   config = D
end

begin
   prog = mythtv
# This is the Green key
# We'll use it for "Information"
   button = Green
   config = I
end

# Note the "repeat =" strings in the volume and channel.
# This means that if you hold down the key, every nth instance will be
# passed.  This depends on your system, so you may want to increase or
# decrease this and see what happens.  repeat = 1 is probably too
# fast.

begin
  prog = mythtv
# This is the Yellow key
# Use it as a volume key
  button = Yellow
  repeat = 3
  config = F10
end

begin
  prog = mythtv
# This is the Blue key
# Use it as a volume key
  button = Blue
  repeat = 3
  config = F11
end

begin
    prog = mythtv
    button = Ch+
# This is the "up" on the central diamond
    repeat = 3
    config = Up
end

begin
    prog = mythtv
    button = Ch-
# This is the "down" on the central diamond
    repeat = 3
    config = Down
end

begin
    prog = mythtv
    button = Vol-
# This is the "left" on the central diamond
    repeat = 3
    config = Left
end

begin
    prog = mythtv
    button = Vol+
# This is the "right" on the central diamond
    repeat = 3
    config = Right
end

begin
    prog = mythtv
# Middle button on the diamond
    button = Ok
    config = Return
end

begin
    prog = mythtv
    button = Mute
    config = F9
end

begin
   prog = mythtv
# Change focus for PiP (to change channel in the other window)
   button = Blank
   config = B
end

begin
   prog = mythtv
# Toggle PiP on/off
   button = Full
   config = V
end

begin
    prog = mythtv
    button = Rew
    config = Left
end

begin
    prog = mythtv
    button = Play
    config = P
end

begin
    prog = mythtv
    button = FFW
    config = Right
end

begin
  prog = mythtv
  button = Record
  config = R
end

begin
   prog = mythtv
# Teletext
   button = Stop
   config = T
end

begin
    prog = mythtv
    button = pause
    config = P
end

begin
   prog = mythtv
   button = Replay
# Use for backwards commercial skip
    config = Q
end

begin
   prog = mythtv
   button = Skip
# Use for forward commercial skip
    config = Z
end
```

---

### Post by superm1 on 2006-12-16
> **jafenske said:**
> I'm having the same problem, I followed the advice from above, when I run
```
irw
```I get
```
000000037ff07be1 00 Up mceusb
000000037ff07be1 01 Up mceusb
000000037ff07be1 00 Up mceusb
000000037ff07be1 01 Up mceusb
000000037ff07be1 02 Up mceusb
000000037ff07be1 00 Up mceusb
000000037ff07be1 01 Up mceusb
000000037ff07bf4 00 Enter mceusb
000000037ff07bf4 01 Enter mceusb
000000037ff07bf4 02 Enter mceusb
000000037ff07bf5 00 Clear mceusb
000000037ff07bf5 01 Clear mceusb

```So thats OK
When I run
```
ircat /home/mythtv/.mythtv/.lircrc
```I don't get any change... So I think my .lircrc is the problem.  Below is that file, can someone look over it and let me know what the problem is? Thanks
```
begin
    prog = mythtv
    button = Off
    config = Esc
end

begin
    prog = mythtv
    button = Go
# Swap the PiP windows
    config = N
end

begin
    prog = mythtv
    button = 1
    config = 1
end

begin
    prog = mythtv
    button = 2
    config = 2
end

begin
    prog = mythtv
    button = 3
    config = 3
end

begin
    prog = mythtv
    button = 4
    config = 4
end

begin
    prog = mythtv
    button = 5
    config = 5
end

begin
    prog = mythtv
    button = 6
    config = 6
end

begin
    prog = mythtv
    button = 7
    config = 7
end

begin
    prog = mythtv
    button = 8
    config = 8
end

begin
    prog = mythtv
    button = 9
    config = 9
end

begin
    prog = mythtv
    button = Back/Exit
    config = Esc
end

begin
    prog = mythtv
    button = 0
    config = 0
end

begin
    prog = mythtv
    button = Menu
    config = M
end

# Below are keys used with the Hauppauge Grey remote

begin
   prog = mythtv
# This is the Red key
# We'll use it for "Delete"
   button = Red
   config = D
end

begin
   prog = mythtv
# This is the Green key
# We'll use it for "Information"
   button = Green
   config = I
end

# Note the "repeat =" strings in the volume and channel.
# This means that if you hold down the key, every nth instance will be
# passed.  This depends on your system, so you may want to increase or
# decrease this and see what happens.  repeat = 1 is probably too
# fast.

begin
  prog = mythtv
# This is the Yellow key
# Use it as a volume key
  button = Yellow
  repeat = 3
  config = F10
end

begin
  prog = mythtv
# This is the Blue key
# Use it as a volume key
  button = Blue
  repeat = 3
  config = F11
end

begin
    prog = mythtv
    button = Ch+
# This is the "up" on the central diamond
    repeat = 3
    config = Up
end

begin
    prog = mythtv
    button = Ch-
# This is the "down" on the central diamond
    repeat = 3
    config = Down
end

begin
    prog = mythtv
    button = Vol-
# This is the "left" on the central diamond
    repeat = 3
    config = Left
end

begin
    prog = mythtv
    button = Vol+
# This is the "right" on the central diamond
    repeat = 3
    config = Right
end

begin
    prog = mythtv
# Middle button on the diamond
    button = Ok
    config = Return
end

begin
    prog = mythtv
    button = Mute
    config = F9
end

begin
   prog = mythtv
# Change focus for PiP (to change channel in the other window)
   button = Blank
   config = B
end

begin
   prog = mythtv
# Toggle PiP on/off
   button = Full
   config = V
end

begin
    prog = mythtv
    button = Rew
    config = Left
end

begin
    prog = mythtv
    button = Play
    config = P
end

begin
    prog = mythtv
    button = FFW
    config = Right
end

begin
  prog = mythtv
  button = Record
  config = R
end

begin
   prog = mythtv
# Teletext
   button = Stop
   config = T
end

begin
    prog = mythtv
    button = pause
    config = P
end

begin
   prog = mythtv
   button = Replay
# Use for backwards commercial skip
    config = Q
end

begin
   prog = mythtv
   button = Skip
# Use for forward commercial skip
    config = Z
end
```
Well a few things -

ircat is used to show the buttons for PROGRAM, where program is the name in the .lircrc

so it would be 

```
ircat mythtv -c ~/.mythtv/lircrc
```

Also, if you don't have a hauppauge remote defined in your /etc/lirc/lircd.conf, don't use hauppauge buttons.  This is most likely your problem.  Grab a lircrc that is specific for mceusb/mceusb2 remotes.
[https://help.ubuntu.com/community/Install_Lirc_Edgy?action=AttachFile&do=get&target=lircrc.mceusb](https://help.ubuntu.com/community/Install_Lirc_Edgy?action=AttachFile&do=get&target=lircrc.mceusb)

There is the one that I posted to the community help pages.

---

### Post by majoridiot on 2006-12-18
try mario's link.  that's the lircd i started with for the same remote and it works for
the most part.  a few of the buttons have different names, but that's easy to resolve
by using irw to identify the correct names.

---

