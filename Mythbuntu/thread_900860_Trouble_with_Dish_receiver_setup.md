---
title: "Trouble with Dish receiver setup"
date: 2008-08-25
forum: Mythbuntu
---

### Post by abarber on 2008-08-25
I have been working on my HTPC off and on for a few months now, but have recently hit a snag when it came to connecting it to my set top box.  While I was finally able to get Myth to display the signal coming from the cable box, I still cannot change channels with my USB MCE remote.  I should say that the remote is changing the channel within Myth, but this signal is not being sent to the Dish receiver.  Also, some of the channels are not displaying the correct information in the box at the bottom of the screen.  To properly troubleshoot the problem, here are the specs and scripts for my box:

ECS mobo w/ dual core CPU
PNY nVidia geForce 7600GS video card
Hauppage PVR-150 MCE tuner card
Generic MCE remote and receiver (USB IR)
Combo USB IR blaster/transmitter (from Hauppage PVR-1300?)

I am running Mythbuntu 8.04. Here are the configuration files for my setup:

/etc/lirc/lircd.conf:
```

  GNU nano 2.0.7               File: /etc/lirc/lircd.conf                                     



#This configuration has been automatically generated via 
#the Ubuntu LIRC package maintainer scripts. 
# 
#It includes the default configuration for the remote and/or 
#transmitter that you have selected during package installation. 
# 
#Feel free to add any custom remotes to the configuration 
#via additional include directives or below the existing 
#Ubuntu include directives from your selected remote and/or 
#transmitter. 

#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote: 
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb 

#Configuration for the USB-UIRT2 : Dish Receiver transmitter: 
include /usr/share/lirc/transmitters/dish/general.conf 

Obviously since mythbuntu control center manages my IR devices, it has includes for my remotes and transmitters:

# 
# RC-6 config file 
# 
# source: http://home.hccnet.nl/m.majoor/projects__remote_control.htm 
#         http://home.hccnet.nl/m.majoor/pronto.pdf 
# 
# used by: Philips 
# 
######### 
# 
# Philips Media Center Edition remote control 
# For use with the USB MCE ir receiver 
# 
# Dan Conti  dconti|acm.wwu.edu 
# 
# Updated with codes for MCE 2005 Remote additional buttons 
# *, #, Teletext, Red, Green, Yellow & Blue Buttons 
# Note: TV power button transmits no code until programmed. 
# Updated 12th September 2005 
# Graham Auld - mce|graham.auld.me.uk 
# 
# Radio, Print, RecTV are only available on the HP Media Center remote control 
# 

begin remote 

  name mceusb 
  bits           16 
  flags RC6|CONST_LENGTH 
  eps            30 
  aeps          100 

  header       2667   889 
  one           444   444 
  zero          444   444 
  pre_data_bits 21 
  pre_data      0x37FF0 
  gap          105000 
  toggle_bit     22 
  rc6_mask     0x100000000 


      begin codes 

	Blue	0x00007ba1 
	Yellow	0x00007ba2 
	Green	0x00007ba3 
	Red	0x00007ba4 
	Teletext	0x00007ba5 

# starts at af 
        Radio    0x00007baf 
        Print    0x00007bb1 
        Videos   0x00007bb5 
        Pictures 0x00007bb6 
        RecTV    0x00007bb7 
        Music    0x00007bb8 
        TV       0x00007bb9 
# no ba - d8 

        Guide    0x00007bd9 
        LiveTV   0x00007bda 
        DVD      0x00007bdb 
        Back     0x00007bdc 
        OK       0x00007bdd 
        Right    0x00007bde 
        Left     0x00007bdf 
        Down     0x00007be0 
        Up       0x00007be1 

        Star       0x00007be2 
        Hash       0x00007be3 

        Replay   0x00007be4 
        Skip     0x00007be5 
        Stop     0x00007be6 
        Pause    0x00007be7 
        Record   0x00007be8 
        Play     0x00007be9 
        Rewind   0x00007bea 
        Forward  0x00007beb 
        ChanDown 0x00007bec 
        ChanUp   0x00007bed 
        VolDown  0x00007bee 
        VolUp    0x00007bef 
        More     0x00007bf0 
        Mute     0x00007bf1 
        Home     0x00007bf2 
        Power    0x00007bf3 
        Enter    0x00007bf4 
        Clear    0x00007bf5 
        9        0x00007bf6 
        8        0x00007bf7 
        7        0x00007bf8 
        6        0x00007bf9 
        5        0x00007bfa 
        4        0x00007bfb 
        3        0x00007bfc 
        2        0x00007bfd 
        1        0x00007bfe 
        0        0x00007bff 
      end codes 

end remote




Now for the Transmitter, I am not sure if this is what I should have it set to ... but this is what I currently have in the include (automatically generated from the mythbuntu control center).

# This config file is based on the information posted by Endaf Jones at 
# http://www.gossamer-threads.com/lists/mythtv/users/196566#196566 
# 
# brand:                       JVC/RCA 
# model no. of remote control: 
# supported devices:           Dish Network (Echostar) 
#                                - JVC 2700 receiver 
#                                - JVC 4700 receiver 
#                                - JVC 49xx receiver 
#                                - JVC 50xx receiver 
#                                - RCA 31x receiver 
#                              and several other Dish receivers using the 
#                              "blue button" remotes 
# 
# Unit code selection (1-16) is performed by specifying the appropriate 
# value for post_data 
#  1=0x000             2=0x200             3=0x100             4=0x300 
#  5=0x080             6=0x280             7=0x180             8=0x380 
#  9=0x040            10=0x240            11=0x140            12=0x340 
# 13=0x0C0            14=0x2C0            15=0x1C0            16=0x3C0 
# 
# Each has been implemented in this config file with the remote names "dish#" 
# where the hash/pound/number sign ("#") is a code number from 1 through 16. 
# There is also a remote called "dish" (without a number), for users with only 
# one receiver, that uses remote code 1 (DISH's default). 
# 
# The duty_cycle (the percentage of time during a pulse that infrared light is 
# being sent) is commented because some hardware transmitters don't support its 
# use. 
# 
# The discrete power functions (power_on and power_off) can be used to ensure 
# the power state of the receiver.  However, they probably shouldn't be used in 
# a channel change script as the receiver will require a significant delay 
# after a power_on before it is capable of receiving/responding to additional 
# commands (such as channel numbers).  Instead, assuming most of your recording 
# is during prime-time, you may want to set a cron job to run a "power_on" 
# command for each of your receivers about 5 or 10 minutes before primtetime. 


### Remote definition for remotes using remote code 1 (0x000) 
begin remote 
  name dish 

  flags SPACE_ENC|NO_HEAD_REP 
  eps 30 
  aeps 100 

  frequency 56000 
#  duty_cycle 32 

  one 440 1645 
  zero 440 2780 

  header 525 6045 
  ptrail 450 
  gap 6115 

  min_repeat 6 

  bits 6 
  post_data_bits 10 

  post_data 0x000 

  begin codes 
    info                               0 
    power_on                           1 
    power                              2 
    1                                  4 
    2                                  5 
    3                                  6 
    4                                  8 
    5                                  9 
    6                                  10 
    7                                  12 
    8                                  13 
    9                                  14 
    0                                  17 
    menu                               11 
    select                             16 
    cancel                             18 
    guide                              20 
    view                               22 
    tv_vcr                             23 
    right                              24 
    up                                 26 
    recall                             27 
    left                               28 
    down                               30 
    record                             31 
    pause                              32 
    stop                               33 
    sys_info                           36 
    asterisk                           37 
    pound                              38 
    power_off                          39 
    sat                                41 
    dish_home                          52 
    sys_info2                          54 
    dish_home2                         56 
  end codes 
end remote 

```

I abbreviated this, but this is the code that allows for 16 remotes.


Here is the channel change script I tried (actually second one I tried to no avail)
change-channel-lirc.sh:

```

REMOTE_NAME=mceusb 
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select 
sleep 0.5 
for digit in $(echo $1 | sed -e 's/./& /g'); do 
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME $digit 
sleep 0.5 
done 
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select 

```



Now here is my lircrc found in my home directory:
```

# LIRCRC Auto Generated by Mythbuntu Lirc Generator 
# Author(s): Mario Limonciello, Nick Fox 
# Created for use with Mythbuntu 
begin 
    remote = mceusb 
    prog = mythtv 
    button = Seven 
    config = 7 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Right 
    config = Right 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Mute 
    config = | 
    repeat = 0 
    delay = 0 
end 
 
begin 
    remote = mceusb 
    prog = mythtv 
    button = Skip 
    config = Z 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = One 
    config = 1 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Down 
    config = Down 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Zero 
    config = 0 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Replay 
    config = Q 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Home 
    config = M 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Pause 
    config = P 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Six 
    config = 6 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Two 
    config = 2 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = ChanDown 
    config = Down 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = ChanUp 
    config = Up 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Rewind 
    config = < 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Forward 
    config = > 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Play 
    config = P 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = VolDown 
    config = [ 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Stop 
    config = Escape 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = VolUp 
    config = ] 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Five 
    config = 5 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = More 
    config = I 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Four 
    config = 4 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = OK 
    config = Return 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Up 
    config = Up 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = RecTV 
    config = R 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Nine 
    config = 9 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Three 
    config = 3 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Enter 
    config = Enter 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Eight 
    config = 8 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Guide 
    config = S 
    repeat = 0 
    delay = 0 
end 

begin 
    remote = mceusb 
    prog = mythtv 
    button = Left 
    config = Left 
    repeat = 0 
    delay = 0 
end 

```

I'll be checking this thread frequently, so let me know if I can post anything useful.  I'm REALLY set on getting this working.  Thanks in advance for your help.

---

### Post by LarryJ2 on 2008-08-25
1. So /usr/local/bin/change-channel-lirc.sh is executible?

```
chmod +x /usr/local/bin/change-channel-lirc.sh
```

2.  What happens when you run this in a terminal?

```
/usr/local/bin/change-channel-lirc.sh 200
```

3.  Have you tried the IR Sensitive camera trick? (to see if anything is coming (emitting) from the blaster diode when you send an irsend command)

4. For some reason, my irsend command had to be "/dev/lircd1 SEND_ONCE".  what do you show as a result of "ls -al /dev/lirc*"

---

### Post by abarber on 2008-08-26
> **LarryJ2 said:**
> 1. So /usr/local/bin/change-channel-lirc.sh is executible?

```
chmod +x /usr/local/bin/change-channel-lirc.sh
```

Yes, it is executable.

> 2.  What happens when you run this in a terminal?

```
/usr/local/bin/change-channel-lirc.sh 200
```



```
sudo /usr/local/bin/change-channel-lirc.sh 200
irsend: command failed: SEND_ONCE mceremote select
irsend: unknown remote: "mceremote"
irsend: command failed: SEND_ONCE mceremote 2
irsend: unknown remote: "mceremote"
irsend: command failed: SEND_ONCE mceremote 0
irsend: unknown remote: "mceremote"
irsend: command failed: SEND_ONCE mceremote 0
irsend: unknown remote: "mceremote"
irsend: command failed: SEND_ONCE mceremote select
irsend: unknown remote: "mceremote"


```

> 3.  Have you tried the IR Sensitive camera trick? (to see if anything is coming (emitting) from the blaster diode when you send an irsend command)

I don't know about this trick, but I doubt I am even to that point.

> 4. For some reason, my irsend command had to be "/dev/lircd1 SEND_ONCE".  what do you show as a result of "ls -al /dev/lirc*"

```
ls -al /dev/lirc*
crw-rw---- 1 root root 61, 0 2008-08-25 16:55 /dev/lirc0
crw-rw---- 1 root root 61, 1 2008-08-25 16:55 /dev/lirc1
srw-rw-rw- 1 root root     0 2008-08-25 16:55 /dev/lircd

```

UPDATE: I changed the remote name in the channel change script from "mceremote" to "mceusb" to "dish" and finally received no error messages.  The script did send a signal to the blaster as a result, but did not change the channel on the TV.  Maybe the codes are wrong?

---

### Post by LarryJ2 on 2008-08-27
```
The script did send a signal to the blaster as a result, but did not change the channel on the TV. Maybe the codes are wrong?
``` 
I assume you mean that the blaster didn't change the channel of the dish receiver?

Have you read and followed the sequence that rubrboots posted?  It's here:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=893697](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=893697).  My blaster started working after several trips though his step by step.

When I do "ls -al", I see 

```
lj@mythtv:~$ ls -al /dev/lirc*
crw-rw---- 1 root root 61, 0 2008-08-26 16:02 /dev/lirc0
crw-rw---- 1 root root 61, 1 2008-08-26 16:02 /dev/lirc1
srw-rw-rw- 1 root root     0 2008-08-26 16:02 /dev/lircd
srw-rw-rw- 1 root root     0 2008-08-26 16:02 /dev/lircd1
```

 I'm not certain why I have two /dev/lircd's (lircd and lircd1) and you only have one. I think this is because my mythbox has a KWorld 110 ATSC/NTSC/remote card which I only use it's  DVB portion. So /dev/lircd is associated with the KWorld card and /dev/lircd1 associated with the serial blaster/streamzap setup. And consequently, I had to  show "/dev/lircd1" in the channel-change-lirc.sh script. Quite obviously,  if your ls -al /dev/lirc* is only showing /dev/lircd then that's what should be in the channel-change-lirc.sh script, presumbaly.  But what if the Hauppauge blaster is not being loaded?

I reread your post.  I see your blaster facility is provided from a Hauppauge card.  I don't know what it would take to make this hardware available for mythbuntu's lirc.  Have you done a "lshw" to find the hauppage card model?  Maybe a search for that card plus lirc plus blaster will turn up something.  

Anyway, keep hacking.  It was a week before I finally got mine running.  Maybe someone else with more experience can step in here.

---

### Post by anonymousdog on 2008-08-27
Do you have two IR receiver/blaster units on you machine?  Your hardware list sort of looks like that.  You configuration reflects just the IR unit from the PVR-150 MCE unit though.  I'd be really tempted to unplug the other unit (and reboot).

Otherwise, let's back up just a bit and do some basic TS.  Open a terminal and type```
irw
```That'll return nothing until you hit some buttons on the remote.  Do that and make sure the output from irw reflects the buttons you are pressing on the remote.  You should get output like```
000000037ff07bde 00 Right mceusb
000000037ff07bde 01 Right mceusb
000000037ff07bde 02 Right mceusb
000000037ff07bdf 00 Left mceusb
000000037ff07bdf 01 Left mceusb
000000037ff07be6 00 Stop mceusb
000000037ff07be6 01 Stop mceusb
```Do not be alarmed about the duplicates; that's normal.  Now press Ctrl-C to kill irw.

If that went ok, we should test your blaster setup.  (If at all possible, hook the dish receiver up to a regular TV and watch that during this test; it eliminates the delay and saves frustration.)  In the terminal you still have running, run```
irsend list dish ""
```(Include the two double quotes.)  That should return all the configured codes for your dish receiver.  Next, issue```
irsend send_once dish cancel
```That should run without error, and, on your TV (or in mythfrontend in LiveTV) you should see the basic channel information display come on for a few seconds (like you had hit "cancel" on your Dish remote control).  If that works, try some other dish remote commands like 'irsend send_once dish select' or 'irsend send_once dish info'.

If all those work, your channel change script is the problem.  Try this one:```
#!/bin/sh

REMOTE_NAME=dish
cmd="$1"

# wakeup dish receiver from sleep mode
irsend send_once $REMOTE_NAME select
sleep 0.3

case $cmd in
    [0-9]*)
# send commands that are channels
    for digit in $(echo $1 | sed -e 's/./& /g'); do 
        irsend SEND_ONCE $REMOTE_NAME $digit
        # sleep 1
        # If things work OK with sleep 1, try this for faster channel changes:
        sleep 0.3
    done
# speed the channel change and clear the screen
irsend send_once $REMOTE_NAME select
sleep 0.3
irsend send_once $REMOTE_NAME cancel
sleep 0.3
    ;;

    *)
# send commands that aren't channel numbers
        irsend SEND_ONCE $REMOTE_NAME $cmd
        ;;
esac
```  It works like a dream with my PVR-500 MCE remote/receiver/blaster and Dish 322 receiver.  You may have to play with sleep values (probably between 0.1 and 1.0) to get the fastest, reliable channel change possible with your setup.  I got down to about 0.15 and started seeing reliability problems; so, I doubled that for "fudge factor".  It changes channels about as fast as a human can with the standard dish remote.

---

### Post by LarryJ2 on 2008-09-20
I recently "upgraded" to a dish ViP612 so called HD-DVR receiver so after the installer left, my channel change script no longer worked!  Thanks alot dishnutwork!!

The problem was the installer left the remote control address as #3.  In otherwords if on the dish remote you press the button "menu", select "System setup". select "Installation", select "System info", the  screen titled System Info One shows a section headed with "i".  In that section, the Rem Addr was set to "3" by my hapless installer.   I tried changing my channel-change-lirc.pl script to show reflect the address 3 but that failed showing the an error message "irsend: unknown remote: "dish3" in the terminal.


An additional problem directly caused by this is that my after market IR Phillips remote no longer worked.   Apparently,  the Phillips aftermarket remote only codes "dish"  but not "dish1" or "dish3".

To fix this,  I changed the Remote Address (Rem Addr) to 1(one) which is the same as using "dish1".  For reasons I don't understand, this command doesn't work either. Witness: 
> lj@mythtv:~$ irsend -d /dev/lircd1 SEND_ONCE dish1 info
irsend: command failed: SEND_ONCE dish1 info
irsend: unknown remote: "dish1"

However  "irsend -d /dev/lircd1 SEND_ONCE dish info" runs fine.  I thought dish and dish1 were synonymous.  The comments in the file
/usr/share/lirc/transmitters/dish/general.conf certainly imply that you can use either dish or dish1.

Briefly, here's how to change the remote address to one on the dish receiver and the dish remote:

1.  On the dish Remote,  Press the SAT button and hold it until the top four buttons (SAT, TV, VCR, and AUX) all turn red.  Then release the SAT button.  The SAT button will continue to flash

2.  On the dish Remote, press the button "1".  Then press the button "#" The SAT button led will extinguish then flash three times indicating that the remote address of 1 was acceptible.   Finally,  press the button "RECORD".

3.  Now that the silver dish remote is set to address1, you need to change the receiver so that it is listening on address1.  Open up the front panel, find and press the button marked "SYSTEM INFO".  When the system info screen appears,  aim the remote at the dish black box and press the remote's button "RECORD"

If successful, the System Info One  screen should show Rem Addr 1 in the section labeled "i".

---

### Post by impossibilechecisiaquesto on 2008-09-20
Hi, check this please 
[http://ubuntuforums.org/showthread.php?t=924388](http://ubuntuforums.org/showthread.php?t=924388)

I have similare problem, but my change-channel script work in a terminal, but don't work inside mythbuntu.

When i lanch the script in a terminal the the led of transmitter blink and the sat-box recive the signal, 

when i vhange channel in LiveTv nothing work.

Any ideas, Please help me =) i'm so near to finish the work.

---

