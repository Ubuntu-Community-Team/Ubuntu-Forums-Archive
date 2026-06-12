---
title: "ATI Remote Wonder II Configuration Guide."
date: 2009-07-22
forum: Mythbuntu
---

### Post by pombe on 2009-07-22
[edited: was a mistake somewhere...  guide should work now I think...]

Every time I upgrade my mythbox or do something stupid and re-install I have to spend a few hours trying to figure out how to get my ATI RWII to work with LIRC again.  

The remote is detected by default, but only like 5 of the buttons work in mythtv and nothing with mplayer or any other program. The remote configuration through mythbuntu doesnt do any better. Neither the "kernel" or "userspace" drivers seem to make any difference.  mythbuntu-lirc-generator makes a bunch of files, but none of them are read.  

Anyway, here is how I get this thing to work, and all my configuration files will be included for posterity (useful since I seem to break my mythbox every 6 months or so and need to reinstall).  There are three files that need to be edited and a symbolic link.  Its actually pretty easy, its just that these files are so damned esoteric and the info online is so patchy that you end up having to do trial and error for hours to get the thing working properly.   

**1) Need a proper lircd.conf file for the remote. ** 
Displays which buttons correspond to which output.
```
sudo nano /etc/lirc/lircd.conf 
```
If the file is present you can get rid of the info which is there and replace with the text which will be attached below.

**2). Need a sensible .lircrc file** 
This goes in the home directory of the user who logs into mythtv.  
```
nano /home/user/.lircrc 
```
Copy in the text from the appropriate file below

Next, get rid of the lircrc in the .mythtv 
```
rm /home/user/.mythtv/lircrc
```

Make a symbolic link between the lircrc file we've edited and /home/user/.mythtv/lircrc
```
ln -s /home/user/.lircrc /home/user/.mythtv/lircrc
```
I generated this at [http://lircconfig.commandir.com/](http://lircconfig.commandir.com/) 

3). **hardware.conf **  
This was the hardest one to get right...  this works though.
```
sudo nano /etc/lirc/hardware.conf
```
Should look like the file below.  This assumes that you've put the lircd.conf file in the same directory.  By default it directed lirc to look somewhere else.

**4). Making sure that correct kernel modules are loaded.**
```
sudo modprobe lirc_i2c lirc_dev lirc_atiusb
```
Next edit lirc-blackist
```
sudo nano /etc/modprobe.d/lirc-blacklist
```
should read
```
#blacklist lirc_atiusb
blacklist ati_remote
blacklist ati_remote2

```

6). restart your computer.  There should now be a listing for "lirc0" in "/dev" and a whole bunch more buttons should work.

7). **Optional**  
The mythbuntu configuration program makes a bunch of files in the /home/user/.lirc directory.  These are theoretically program specific .lircrc files, but they're not needed now since the commands for all your programs can just be stored in a single .lircrc file in /home/user/   I removed these, probably not a big deal if they stay.

**_Files:_**

**lircd.conf**

```
begin remote
  name            ATI_Remote_Wonder_II
  bits            24
  eps             30
  aeps            100
  one             0     0
  zero            0     0
  gap             203970

  begin codes
       stop            0x000231
       pause           0x000230
       fforward        0x000228
       rec             0x000237
       rewind          0x000229
       play            0x00022C
       d               0x00027B
       c               0x00027A
       e               0x00027C
       f               0x00027D
       right           0x00025B
       left            0x00025A
       up              0x000258
       down            0x000259
       ok              0x00025C
       info            0x0002F9
       timer           0x000296
       menu            0x000254
       check           0x000282
       0               0x000200
       1               0x000201
       2               0x000202
       3               0x000203
       4               0x000204
       5               0x000205
       6               0x000206
       7               0x000207
       8               0x000208
       9               0x000209
       volup           0x000210
       voldown         0x000211
       mute            0x00020D
       chup            0x000220
       chdown          0x000221
       mouse_up        0x0001FF
       mouse_down      0x0002FF
       mouse_left      0x0020FF
       mouse_right     0x0010FF
       mouse_up_right  0x0011FF
       mouse_down_right 0x0012FF
       mouse_up_left   0x0021FF
       mouse_down_left 0x0022FF
       right_click     0x0002AA
       left_click      0x0002A9
       hand            0x0002D0
       shrink_resize   0x0002D5
       ?               0x0002BE
       dvd             0x000238
       tv              0x000239
       a               0x000278
       b               0x000279
       power           0x00020C

  end codes

end remote
```

**.lircrc**

```
# Stop
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = stop
  repeat = 2
  config = T
end

# Pause
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = pause
  repeat = 2
  config = P
end

# Skip Forward
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = fforward
  repeat = 2
  config = PgDown
end

# Record
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = rec
  repeat = 2
  config = R
end

# Skip Backwards
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = rewind
  repeat = 2
  config = PgUp
end

# Swap PIP Windows
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = d
  repeat = 2
  config = N
end

# PiP On-Off Toggle
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = c
  repeat = 2
  config = V
end

# Previous Commercial Cut
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = e
  repeat = 2
  config = Q
end

# Next Commercial Cut Forward
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = f
  repeat = 2
  config = Z
end


begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = right
  repeat = 2
  config = Right
end


begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = left
  repeat = 2
  config = Left
end


begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = up
  repeat = 2
  config = Up
end


begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = down
  repeat = 2
  config = Down
end

# Select
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = ok
  repeat = 2
  config = Return
end

# Show OSD
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = timer
  repeat = 2
  config = I
end

# Menu
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = menu
  repeat = 2
  config = M
end

# Number Zero
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = 0 
  repeat = 2
  config = 0
end


begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = 1
  repeat = 2
  config = 1
end


begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = 2
  repeat = 2
  config = 2
end


begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = 3
  repeat = 2
  config = 3
end


begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = 4
  repeat = 2
  config = 4
end


begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = 5
  repeat = 2
  config = 5
end


begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = 6
  repeat = 2
  config = 6
end


begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = 7
  repeat = 2
  config = 7
end


begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = 8
  repeat = 2
  config = 8
end


begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = 9
  repeat = 2
  config = 9
end

# Volume Up
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = volup
  repeat = 2
  config = F11
end

# Volume Down
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = voldown
  repeat = 2
  config = F10
end

# Mute
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = mute
  repeat = 2
  config = F9
end

# Cancel / Back
begin
  prog = mythtv
  remote = ATI_Remote_Wonder_II
  button = power
  repeat = 2
  config = Esc
end


begin
  prog = mplayer
  remote = ATI_Remote_Wonder_II
  button = stop
  repeat = 2
  config = quit
end


begin
  prog = mplayer
  remote = ATI_Remote_Wonder_II
  button = pause
  repeat = 2
  config = pause
end


begin
  prog = mplayer
  remote = ATI_Remote_Wonder_II
  button = right
  repeat = 2
  config = seek +10
end


begin
  prog = mplayer
  remote = ATI_Remote_Wonder_II
  button = left
  repeat = 2
  config = seek -10
end


begin
  prog = mplayer
  remote = ATI_Remote_Wonder_II
  button = up
  repeat = 2
  config = seek +60
end


begin
  prog = mplayer
  remote = ATI_Remote_Wonder_II
  button = down
  repeat = 2
  config = seek -60
end


begin
  prog = mplayer
  remote = ATI_Remote_Wonder_II
  button = timer
  repeat = 2
  config = osd
end


begin
  prog = mplayer
  remote = ATI_Remote_Wonder_II
  button = volup
  repeat = 2
  config = volume +1
end


begin
  prog = mplayer
  remote = ATI_Remote_Wonder_II
  button = voldown
  repeat = 2
  config = volume -1
end


begin
  prog = mplayer
  remote = ATI_Remote_Wonder_II
  button = mute
  repeat = 2
  config = mute
end


begin
  prog = mplayer
  remote = ATI_Remote_Wonder_II
  button = chup
  repeat = 2
  config = audio_delay +0.1
end


begin
  prog = mplayer
  remote = ATI_Remote_Wonder_II
  button = chdown
  repeat = 2
  config = audio_delay -0.1
end

begin
  prog = mplayer
  remote = ATI_Remote_Wonder_II
  button = f
  repeat = 2
  config = sub_visibility
end

```

**hardware.conf**

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE=""
REMOTE_MODULES="lirc_i2c lirc_dev"
REMOTE_DRIVER="default"
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

---

### Post by usmcstitch on 2009-10-10
<snip> nevermind, sorry to have asked </snip>

---

### Post by guiwegian on 2009-11-14
Hey I m using a ati remote wonder, and for me it works out of the box, I just plugged in and its works, I m not using lirc, my question is where is the configuration file????
How can I use my oen settings on it?

bigman@bigman-desktop:~$ lsmod | grep ati
lirc_atiusb            16284  0 
lirc_dev               10804  1 lirc_atiusb
ati_remote             10084  0 

bigman@bigman-desktop:~$ lsusb
Bus 004 Device 002: ID 0bc7:0004 X10 Wireless Technology, Inc. X10 Receiver

---

### Post by pombe on 2009-12-03
> **guiwegian said:**
> Hey I m using a ati remote wonder, and for me it works out of the box, I just plugged in and its works, I m not using lirc, my question is where is the configuration file????
How can I use my oen settings on it?

bigman@bigman-desktop:~$ lsmod | grep ati
lirc_atiusb            16284  0 
lirc_dev               10804  1 lirc_atiusb
ati_remote             10084  0 

bigman@bigman-desktop:~$ lsusb
Bus 004 Device 002: ID 0bc7:0004 X10 Wireless Technology, Inc. X10 Receiver

Thats the problem I tried to address above.  it does "work" out of the box, in that a couple of buttons do things, but to actually map them out decently you need lirc.   

I'm currently unbreaking my Mythbox, and have discovered that that the instructions above arent completely accurate.  I'm trying to figure out what is wrong...

---

