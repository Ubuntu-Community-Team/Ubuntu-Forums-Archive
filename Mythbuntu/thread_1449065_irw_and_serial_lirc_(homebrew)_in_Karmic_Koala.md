---
title: "irw and serial lirc (homebrew) in Karmic Koala"
date: 2010-04-07
forum: Mythbuntu
---

### Post by Dubbledex on 2010-04-07
Dear anyone. I have been having a nightmare of a time trying to get serial lirc to work. I have looked at numerous forums, but they are all for older versions gutsy/feisty etc, and things look different/files in different places in Karmic. If anyone has a homebrew serial IR working in Karmic, please please tell me how to do it. :)

The other thing is, I did have the lirc irw working (before I totally corrupted 9.10) I can't find any info anywhere on how to just run it, or what package it is in.

(See my feeble efforts below)


david@david-desktop:~$ 'irw'
connect: No such file or directory
david@david-desktop:~$ irw
connect: No such file or directory


How do I just run irw?!?!? (yes I'm a newbie and am a bit crap at Linux)

Oh yeah, when I reinstalled, I put the new Beta version of Mythbuntu 10.04 just to make things interesting!

Cheers! David

---

### Post by SiHa on 2010-04-07
I have a homebrew serial receiver (The 'More Complicated' version from [[COLOR="Blue"]_lirc.org_[/COLOR]](http://www.lirc.org/receivers.html)) working fine under Karmic. I'm assuming you have either of the two mentioned there.

All I did to get basic functionality (ie, receiving pulses, not necessarily interpreting them) was```
sudo dpkg-reconfigure lirc
``` You will be prompted for the type of reciver - choose the 'Homebrew 16x50 UART compatible'(IIRC) one, not the IGOR variant, and the correct serial port (ttyS0, normally). This should also take care of the 'setserial' operation that is mentioned elsewhere.

You **may** need to reboot, so that the kernel will free up the serial port, not sure if the dpkg-reconfigure does this.

To check the port has been initialised properly, stop lirc and run mode2```
sudo /etc/init.d/lirc stop
sudo mode2 -d /dev/lirc0
```
Press some buttons on the remote, and you should get the raw IR data output to the screen:
> pulse 7846
space545
pulse7846
space545
.
.
.
ctrl+C to exit

If this bit works, your receiver is working, your /etc/lirc/hardware.conf will have been configured correctly, so all you should need to do is get the correct lircd.conf for your remote, or record a new one with irrecord. I just have my lircd.conf in /etc/lirc, and because I used irrecord and was lazy, my remote is called lircd.conf.

Hardware.conf & lircd.conf live in /etc/lirc. the mythtv config is in ~/.lirc.
The files in this directory are linked by an include statement in ~/.lircrc. ('~' is the home directory for the mythtv user, /home/frontend on my machine). I've included them for reference.

With any luck, once you have the correct lircd.conf, and have restarted lirc:```
sudo /etc/init.d/lirc restart
```, irw will now respond with the remote keypresses.

If that works, you just need to edit the mythtv config file, or run mythbuntu-lirc-generator.

Hope this helps some!

The files:

```
frontend@frontend-desktop:/etc/lirc$ cat hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Home-brew (16x50 UART compatible serial port)"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
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

```
frontend@frontend-desktop:/etc/lirc$ cat lircd.conf

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.6(default) on Sun Feb 21 20:49:24 2010
#
# contributed by 
#
# brand:                       digi
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  lircd.conf
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           857   819
  zero          857   819
  plead         883
  gap          107206
  toggle_bit_mask 0x800

      begin codes
          Power                    0x124B
          1                        0x1241
          2                        0x1242
          3                        0x1243
          4                        0x1244
          5                        0x1245
          6                        0x1246
          7                        0x1247
          8                        0x1248
          9                        0x1249
          0                        0x1240
          Menu                     0x125C
          ChUp                     0x1256
          ChDown                   0x1257
          Up                       0x1252
          Down                     0x1253
          Left                     0x1250
          Right                    0x1251
          OK                       0x1272
          Rewind                   0x1268
          Play                     0x126D
          Pause                    0x1269
          FF                       0x126C
          Replay                   0x126B
          Skip                     0x126F
          Stop                     0x126A
          Red                      0x1258
          Green                    0x1259
          Yellow                   0x125B
          Blue                     0x125A
          Guide                    0x125D
          Exit                     0x124D
          PPV                      0x125E
          Subt                     0x124F
          Fav                      0x1270
          Record                   0x126E
          Info                     0x124E
          ?                        0x124C

      end codes

end remote

```

```
frontend@frontend-desktop:~/.lirc$ cat mythtv
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
begin
    remote = lircd.conf
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = ChUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = ChDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Up
    config = Up
    repeat = 1
    delay = 1
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Down
    config = Down
    repeat = 1
    delay = 1
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Left
    config = Left
    repeat = 1
    delay = 1
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Right
    config = Right
    repeat = 1
    delay = 1
end

begin
    remote = lircd.conf
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = FF
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Exit
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Skip
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = mythtv
    button = Replay
    config = Q
    repeat = 0
    delay = 0
end

begin
   remote = lircd.conf
   prog = mythtv
   button = Info
   config = I
   repeat = 0
   delay = 0
end

begin
   remote = lircd.conf
   prog = mythtv
   button = Record
   config = R
   repeat = 0
   delay = 0
end

```

---

### Post by Dubbledex on 2010-04-08
Hi SiHa, Thanks for all that info! At work at the moment, and was not going to try it until lunchtime (lots of work to do!), but seeing as it seemed so easy I gave it a try. Can't see anything when I press the remote buttons, but it could be my homebrew serial ir! Will let you know how I get on 
 
Thanks again!
 
Dubbledex

---

### Post by SiHa on 2010-04-08
Might be that you need to change the I/O or IRQ settings for your COM ports in the BIOS, or pick another port when you reconfigure lirc. I *think* the usual settings for ttyS0 (COM1) are 0x03f8 and IRQ4.

To check the COM port is initialised, you can put a DVM between pin 7 and GND, see if you have a +ve voltage of 10V or so. I must admit I had the advantage of a scope at work to help me get my receivers working. One mistake I made at first was putting an LED across the output to check it was working. Yes, the LED flashes when a signal is received, but the output is clamped to ~2.5V or so which is below the 5V required for RS232 :redface:

Have you tried the receiver outside of the PC? If you don't have a bench PSU handy, you could take the +12V and GND from the yellow and black wires on a spare HDD connector as the regulator input. I found that the simple circuit didn't work for me, so I used the more complicated one, but this is obviously harder to debug when it doesn't work.

---

### Post by Dubbledex on 2010-04-08
Okay! I'm so almost there!
 
Finally got my serial/ir thing to work.. Had not soldered up pin 7.. doh! mistake number 1! The other thing was I had tried to extend the ir on a piece of cat 5 (only about 30cm), but that seemed to break it. As soon as I got rid of it, and soldered the ir directly to my little board, it worked like a dream!
 
Right, I got it working, I can see things in irw.
I downloaded a config file for an LG remote I happened to have and it all seems happy.
 
Only thing I cant do is the mythtv part. 
 
I looked in usr-share-mythtv folder, and I can't find any config file.
I looked in home-mythtv that folder is empty
 
I installed mythbuntu-lirc-generator and ran that.
 
It says:
 
"you should now have a .lircrc file generated in /home/david/.lircrc
All application specific lircrc files are in /home/david/.lirc
"
I do have a remote file in home/david/lirc but that was created when I did the remote download. (it was just part of the code I ran was to make a copy there first).
i removed that and ran it again, but it does not create any files.
 
What do you think I am doing wrong?
 
Cheers, 
 
Dubbledex

---

### Post by Dubbledex on 2010-04-08
Okay, I'm now replying to myself! V Sad!
 
I just tried my remote in mythbuntu and it works!! yey! But I have no idea where the file mythtv-lirc file is hiding, as I would really like to be able to put my pc into hibernation with the standby button. Any ideas??
 
P.s. SiHa. thanks for all the help!

---

### Post by SiHa on 2010-04-08
You'll need to use irexec for that. Now here I had a few issues. It seems that the LIRC init script looks to see if ~/.lircrc exists and fires up irexec for you.
This is good, but every time I've tried using irexec I've ended up with 3 or 4 instances running. In the end I've ened up with a dirty hack of a script in rc.local that kills all irexec processes then starts a fresh one.
I'll be honest, I can't remember the specifics of getting only one instance of irexec running, but apart from that it's quite simple.
My .lircrc is here:
```
frontend@frontend-desktop:~$ cat /home/frontend/.lircrc

begin
    remote = lircd.conf
    prog = irexec
    button = Power
#    config = sudo /usr/sbin/pm-suspend
    config = sudo /sbin/shutdown -h now
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = irexec
    button = Blue
    config = /usr/sbin/Mythrestart
    repeat = 0
    delay = 0
end

```

I did have it suspending, but I prefer to shutdown now. If you change the line above to /usr/sbin/pm-hibernate, this should do the trick.
Now you also need to edit your /etc/sudoers file to that the command will run without asking for a password.
```
sudo visudo
```
You'll probably be asked which editor to use, the default now is nano, I'd stick with that as it's easy enough to use. Much easier than vi.
At the bottom of the file you'll need to add a line like this:
```
# remove sudo password for pm-hibernate
frontend ALL=NOPASSWD: /usr/sbin/pm-hibernate
```
CTRL+O to save (output) the file. You'll be asked to confirm the filename, hit enter, it'll be a random string of characters. Then CTRL+X to exit.

Visudo will check the syntax of this file before saving it. If it's wrong, you're stuck because sudo won't work anymore. If you want to be really safe you can backup before.```
sudo cp /etc/sudoers /etc/sudoers.bak
```You can always restore this in a recovery shell from the GRUB menu.

Now wait >15 mins (so that sudo doesn't remember your password), and type ```
sudo pm-hibernate
```If the PC hibernates without asking for a password, you're well on the way. After restarting, see of irexec will do it for you.

Mythrestart, BTW is a little script I have that kills and restarts the frontend when it's gone screwy.

---

### Post by Dubbledex on 2010-04-08
Nice one, I will definitely give that a try. Work is a bit of a mare at the moment, so probably won't get to try it until some point next week, but I will definitely post and let you know how I get on.

I don't suppose you would have any idea where my myth-lirc file would be hiding. I'm guessing that seeing the remote is working in myth that it must be somewhere.

Cheers ,

Dubbledex

---

### Post by SiHa on 2010-04-09
It should definitely be in /home/david/.lirc, especially if you ran the mythbuntu lirc generator, that's where it puts them.

You did mention that your a bit of a Linux noob, so pardon me if I'm telling you stuff you already know...

A '.' at the beginning of a file /directory in Linux indicates that it is hidden.

To view all files including hidden ones, use the -a (all) switch. I generally use the -l (long) as well to give all info like permissions and filesize, mainly so that I get a single list of files, rather than columns, which I find hard to search by eye.

So if you're in your home directory (/home/david) and type```
ls -al
``` you will get a directory listing, which should have an .lircrc file, and an .lirc folder (the first character in the attribute list (e.g. drwxrw----) shows the directories.

If you look at the .lircrc file:```
cat .lircrc
```...you should see a list of include statements:```
include /home/david/.lirc/mythtv
include /home/david/.lirc/xine
etc...
```

Now change to the .lirc folder and list the contents:```
cd .lirc
ls -al

**or just**

ls -al .lirc
```

You should see all the application-specific lirc files.

---

### Post by Dubbledex on 2010-04-09
Aaaah! That is why I can't see the files! Yes I'm a total Linux noobie, so don't feel bad when you have to tell me totally obvious things, because they are not that obvious to me, and I really appreciate the patience, as I know how frustrating it can be! 
 
Going to have a good crack at all this next week. Managed to get some really good remotes that have lots of spare buttons.
 
Cheers, 
 
Dubbledex

---

### Post by SiHa on 2010-04-09
We all have to learn sometime. In many ways I'm still a noob, I was exactly where you are two years ago...

Enjoy your weekend! Try and get some sun though...

---

### Post by sailor420 on 2010-04-10
SiHa, thank you so much for your thorough writeup. I was pulling my hair out trying to get lirc working on my new 9.10 install, and this got it working immediately. Much appreciated!

---

### Post by Dubbledex on 2010-04-21
Hey SiHa, 
 
Been doing a fair bit on the Mythbuntu front. 
Forgot after the rebuild I would have to sort out my dvd drive, and all the cvschs or whatever it is. So got that working. I cant see attached usb drives without mounting them (weird as there is an option in ubuntu manager to see and open usb drives -  guess that is a question for another thread).
 
I tried to get the power button to switch my machine off, but I can't. 
I did everything you said, but even when I tested it (I just restarted my machine instead of waiting 15min). it still asked me for a password. It is like it is ignoring this bit: # remove sudo password for pm-hibernate
frontend ALL=NOPASSWD: /usr/sbin/pm-hibernate
 
Any ideas?

---

### Post by SiHa on 2010-04-22
Sorry, I should have been clearer, in:```
# remove sudo password for pm-hibernate
[COLOR="Red"]frontend[/COLOR] ALL=NOPASSWD: /usr/sbin/pm-hibernate
```

The 'frontend' in the above statement is the user that you wish to give passwordless sudo access to /usr/sbin/pm-hibernate. On my machine, that user is 'frontend'. Sorry, it's easy to see now how that could be misunderstood.

If you change it to the correct user on your machine (david, going from your 1st post) you should be sorted.
```
# remove sudo password for pm-hibernate
[COLOR="Red"]david[/COLOR] ALL=NOPASSWD: /usr/sbin/pm-hibernate
```

Cheers,

Simon

---

