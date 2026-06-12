---
title: "Can't get Remote Controller to work (LIRC) - Soundgraph iMON Antec Veris"
date: 2010-10-30
forum: Mythbuntu
---

### Post by chrismurf2900 on 2010-10-30
I currently have installed **Mythbuntu 10.10**.  I have an Antec Case which has a **Soundgraph **LCD Screen and IR (Device ID: **15c2:0038**).

I've been looking all around trying to get my remote to properly work, but haven't had any luck.  Let me explain more of my setup.

I went through the "Mythbuntu control center" and enabled the remote control for "**Soundgraph iMON Antec Veris**" (the remote that came with my case is a Veris **RM200**).
Only a few of the buttons work for the controller.  The Channel Up and Channel Down are like Direction Up and Direction Down, and then the Enter buttons work.

What I would really like to do is setup my Mythbuntu system to allow for my Harmony One Universal Remote to work with it, instead of the RM200 controller.  However, I can't even get the RM200 controller to work, and I'm assuming that is where I have to start.
I've tried changing to different types of the "iMON remote" configure files, but nothing helped.

I have read around and found out that Mythbuntu 10.10 kernel has its own LIRC now, so maybe that has to do with the conflict.

If anyone can assist me with getting my controller working, I would greatly appreciate.  It would be even more awesome to get my Harmony One Universal remote working, but somewhere to start is just as good.

Please let me know if I can provide any more information.

Thanks so much!

Results from:* lsmod |grep ir*
```
ir_lirc_codec           3888  0 
lirc_dev               11209  1 ir_lirc_codec
ir_sony_decoder         2381  0 
ir_jvc_decoder          2442  0 
ir_rc6_decoder          3018  0 
ir_rc5_decoder          2474  0 
ir_nec_decoder          2442  0 
ir_core                16906  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_imon_pad,ir_nec_decoder,imon
```

---

### Post by chrismurf2900 on 2010-10-31
No response from *irw* command.  However, I'm thinking that has something to do with the new kernel.

Any suggestions on where I should go from here?

---

### Post by rhpot1991 on 2010-11-01
You can find information on this bug here:
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/635192](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/635192)

Long story short, you don't really need lirc any longer, but there will be some buttons that don't work until we get the latest imon driver into Maverick.  For the time being you may want to try to re-configure lirc as a devinput.

---

### Post by chrismurf2900 on 2010-11-01
Thanks for the reply rhpot1991!

Any idea when the latest imon driver would be put into Maverick?

Do you happen to have a link to directions on how to re-configure lirc as a devinput?  Or maybe you could direct me?

Thanks again!

---

### Post by rhpot1991 on 2010-11-01
Not sure when it will be in yet.

Should be pretty easy to reconfigure lirc.  If you are using mythbuntu-control-centre, just go to the IR tab and choose something along the lines of 'linux input layer (/dev/input)'.  Then check the checkbox to generate the button mappings and apply.  If you care about any of your current configurations then backup the files in /etc/lirc and ~/.lirc

Post back here as to how it goes so others know how this approach works.

---

### Post by chrismurf2900 on 2010-11-01
I get the same responses after changing to "Linux input layer (/dev/input/eventX)" via the "Mythbuntu Control Centre" [with the "Generate dynamic button mappings" checked]

Mouse moves via controller, but when on MythTV Frontend, only the up and down channel changing buttons work (as up and down arrows on keyboard would).  Enter and exit then are the only other buttons working.  No numbers, etc.

---

### Post by rhpot1991 on 2010-11-01
Use irw to check that the keystrokes are coming through.  Also some of those have keyboard and mouse modes, try to toggle that.  It sounds like you are still seeing the same keystrokes from the kernel module and nothing new.

---

### Post by chrismurf2900 on 2010-11-03
Nothing coming back from irw when I press anything.  

How do you toggle mouse and keyboard modes?

Thanks for the help!

---

### Post by rhpot1991 on 2010-11-03
> **chrismurf2900 said:**
> Nothing coming back from irw when I press anything.  

How do you toggle mouse and keyboard modes?

Thanks for the help!

Not entirely sure, I don't actually have one, mine uses a MCE remote.

Verify its using the correct input device in /etc/lirc/hardware.conf

You can look at /dev/input/by-id to get an idea of what input you should be using.

---

### Post by chrismurf2900 on 2010-11-03
Here is what I have in my /dev/input/by-id folder:

```
usb-0461_USB_Optical_Mouse-event-mouse
usb-0461_USB_Optical_Mouse-mouse
usb-15c2_0038-event-mouse
usb-15c2_0038-mouse
usb-Dell_Dell_USB_Keyboard-event-kbd
```

I don't even see what appears to be the controller in there.  The only one that might be it is the 0038-event-mouse and 0038-mouse, but their is no accompanying keyboard for it.

The hardware.conf file was initially using /dev/lirc0 (I believe), and I've tried changing it to /dev/input/event0, /dev/input/event1, /dev/input/event2, /dev/input/event3 with no luck (after restarting lirc service, and also the operating system).
No effect upon changing.  The same keys as mentioned above are the only ones to work.
No codes coming back from irw.

---

### Post by rhpot1991 on 2010-11-03
> **chrismurf2900 said:**
> Here is what I have in my /dev/input/by-id folder:

```
usb-0461_USB_Optical_Mouse-event-mouse
usb-0461_USB_Optical_Mouse-mouse
usb-15c2_0038-event-mouse
usb-15c2_0038-mouse
usb-Dell_Dell_USB_Keyboard-event-kbd
```

I don't even see what appears to be the controller in there.  The only one that might be it is the 0038-event-mouse and 0038-mouse, but their is no accompanying keyboard for it.

The hardware.conf file was initially using /dev/lirc0 (I believe), and I've tried changing it to /dev/input/event0, /dev/input/event1, /dev/input/event2, /dev/input/event3 with no luck (after restarting lirc service, and also the operating system).
No effect upon changing.  The same keys as mentioned above are the only ones to work.
No codes coming back from irw.

If you reconfigured it to use devinput then it should have been using /dev/input/eventX by default.  Might want to fire up MCC and make sure you actually applied the change.

As far as which one to use, if you run lsusb, you should see an ID that matches with one of those, most likely the 15c2_0038.  Map it to those and give it a try.

---

### Post by chrismurf2900 on 2010-11-03
> **rhpot1991 said:**
> If you reconfigured it to use devinput then it should have been using /dev/input/eventX by default.  Might want to fire up MCC and make sure you actually applied the change.

As far as which one to use, if you run lsusb, you should see an ID that matches with one of those, most likely the 15c2_0038.  Map it to those and give it a try.

I re-ran MCC with the Linux input layer as the option again, to just make sure it did work properly.  Upon running it, and looking at the hardware.conf file (/etc/lirc/hardware.conf), it changes the "REMOTE_DEVICE" back to "/dev/lirc0".  (See file below)

Changing the "REMOTE_DEVICE" value still seems to do nothing (I run "/etc/init.d/lirc restart" to make sure it utilizes the hardware.conf).
Nothing seems to change.  I did figure out how to toggle between the mouse and keyboard mode, however, most keys still don't work (numbers don't work, pause, play, rewind, etc. don't work still).


```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
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

---

### Post by chrismurf2900 on 2010-11-03
I used the following to make sure that I am attaching the right device to lircd.

```
/usr/sbin/lircd -H devinput -d /dev/input/by-id/usb-15c2_0038-event-mouse
```

Still same results.

---

### Post by chrismurf2900 on 2010-11-05
Thanks for all your assistance rhpot1991. I got it to work now.

Here is what I did so if anyone else also experiences the problem.

I had to un-install lirc.  You can do this like so:

```
sudo apt-get purge lirc
```

I then re-installed lirc, like so:

```
sudo apt-get install lirc
```

This is where you'll have to configure LIRC correctly.  Perform the following:

First, select the linux devinput option:

```
Linux input layer (/dev/input/eventX)
```

I had no IR transmitter, so I selected "None" for the next screen.

Then, in another terminal window, perform the following to find out what event your remote is on:

```
cat /proc/bus/input/devices
```

Mine was "event4," so I selected that on the last screen.

Now run "irw" from your terminal, press the mouse/keyboard toggle button on your controller (mine was right below the stop button), and then start pressing buttons.

If all goes well, you should be seeing key presses output.

Now, go to:

```
MythTV Frontend -> Utilities/Setup -> Setup -> General
```

Under the "Remote Control" screen, change the LIRC daemon socket to "/dev/lircd"

Restart your computer.

You should now have most of your buttons working within MythTV now.  Please note, upon restart, you'll have to press the toggle button every time so that you can utilize the other keys on your remote.

I'm currently working on getting the other buttons to work on the remote control, and will post back later on how I went about customizing the buttons (I'll attach the full file, which is located at ~/.lirc/mythtv  once I have everything running smoothly.)

---

### Post by chrismurf2900 on 2010-11-05
See frmatc's version of the ~/.lirc/mythtv file.

---

### Post by frmatc on 2010-11-06
I have the same hardware and those steps worked for me. Here's my config with every button working. My starting point was based on the [MythTV Wiki]("http://www.mythtv.org/wiki/Antec_Fusion/Everything_Working").

A few key differences compared to the wiki and yours, either from necessity or my own preferences:
[LIST]
[*]The knob sends the same codes for volume up/down as the remote on devinput, so that part was dropped.
[*]Videos, Music, Pictures, TV, and DVD are configured for JumpPoints. You probably need to setup the frontend to understand them if you want to use them. Instructions are at the [MythTV Wiki]("http://www.mythtv.org/wiki/Antec_Fusion/Everything_Working#MythTV_Keys").
[*]Menu Up (KEY_CONTEXT_MENU) and Menu Down (KEY_COMPOSE), the buttons to the left and right of the joystick, are commercial skip backward (Q) and forward (Z), respectively.
[*]App Launcher (KEY_DASHBOARD) is the on-screen guide, and Task Switcher (KEY_CYCLEWINDOWS) is info.
[*]Star (toggles channel favorites and hash (#) is Delete (D)
[/LIST]

I tried to keep the config in the general order of the buttons on the remote. The only exception is the irexec block, which I kept as a seperate file ~/.lirc/irexec. Instructions and support scripts for the irexec config are in the [MythTV Wiki]("http://www.mythtv.org/wiki/Antec_Fusion/Everything_Working#irexec") and did not change. The config itself is in a separate code block below my mythtv config.

```
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox, John Baab
# Created for use with Mythbuntu
begin
    remote = devinput
    prog = mythtv
    button = KEY_EXIT
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_RECORD
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_PLAY
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_REWIND
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_PAUSE
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_FASTFORWARD
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_PREVIOUS
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_STOP
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NEXT
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NEXT
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_BACKSPACE
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_SELECT
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_CONTEXT_MENU
    config = Q
    repeat = 0
    delay = 0
end 

begin
    remote = devinput
    prog = mythtv
    button = KEY_COMPOSE
    config = Z
    repeat = 0
    delay = 0
end 

begin
    remote = devinput
    prog = mythtv
    button = KEY_ENTER
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_UP
    config = Up
    repeat = 3
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_DOWN
    config = Down
    repeat = 3
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_LEFT
    config = Left
    repeat = 3
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_RIGHT
    config = Right
    repeat = 3
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_ESC
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_DASHBOARD
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_PROG1
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_CYCLEWINDOWS
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_MUTE
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_VOLUMEUP
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_VOLUMEDOWN
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_CHANNELUP
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_CHANNELDOWN
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_TIME
    config = F8
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_POUND
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_STAR
    config = ?
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_BOOKMARKS
    config = C
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_MEDIA
    config = O
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_ZOOM
    config = W
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_SCREEN
    config = F
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_MENU
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_SUBTITLE
    config = T
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_LANGUAGE
    config = +
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_VIDEO
    config = \U
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_AUDIO
    config = \M
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_CAMERA
    config = \I
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_TV
    config = \T
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_DVD
    config = \D
    repeat = 0
    delay = 0
end

```

```
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox, John Baab
# Created for use with Mythbuntu

begin
    remote = devinput
    prog = irexec
    button = KEY_POWER
    config = /home/user/Scripts/runmyth.sh &
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = irexec
    button = KEY_EJECTCD
    config = /home/user/Scripts/eject.sh &
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = irexec
    button = KEY_EJECTCLOSECD
    config = /home/user/Scripts/eject.sh &
    repeat = 0
    delay = 0
end

```

---

### Post by chrismurf2900 on 2010-11-06
> **frmatc said:**
>  Here's my config with every button working.

Thanks so much for the contribution frmatc!

That worked for me.

For everyone else who is interested in detailed instructions on this and also how to get a Harmony One Universal Remote working with this setup, I've put together a wiki page on mythtv's wiki to describe what was discussed here as well as other added details I've come up with.

Here's the wiki page: [http://www.mythtv.org/wiki/Soundgraph_iMON_Antec_Veris_Mythbuntu_10.10](http://www.mythtv.org/wiki/Soundgraph_iMON_Antec_Veris_Mythbuntu_10.10)

---

### Post by drumz on 2010-11-22
Thank you all so much, between this post and a few others I was able to get my upgraded 10.10 mythfrontend box operational again.

Is there a reason why we now have to hit the 'keyboard/mouse' button to get it to work correctly after every reboot?  It's quite annoying and I'd like to do something so that it defaults on startup to the correct mode - makes it simpler for the kids/wife when they want to use it.

Thanks!

---

### Post by greggler on 2010-11-26
i'm using a philips rc6 remote and i dont see any kind of mouse keyboard toggle button.
is there no terminal command equivalent?

---

### Post by rhpot1991 on 2010-11-26
> **greggler said:**
> i'm using a philips rc6 remote and i dont see any kind of mouse keyboard toggle button.
is there no terminal command equivalent?

The solution in this thread wont work for you, its for the newer imon hardware, not the mce version.

---

### Post by HelLios on 2010-11-30
Hi chrismurf2900, could you show your hardware.conf file?

Thanks,

Steven

---

### Post by smi402 on 2010-12-11
I have the Antec case with the **SoundGraph iMon 15c2:ffdc** device rather than the **0038** device. Does this solution work with the **ffdc** device or does anyone know of a procedure to get the **ffdc** device working with Maverick 10.10. I have had it working with earlier versions of Mythbuntu using a Logitech Harmony 525 remote.

---

### Post by smi402 on 2010-12-13
I tried this procedure with the **IMON ffdc** device in my **Antec 430** case and cannot get it to work so I guess the procedure is only for the newer **IMON 0038 ** devices. So, the appeal is for a procedure for getting **lirc** to work on Maverick 10.10 with the **IMON ffdc** device and a **Logitech Harmony 525 Universal Remote**. As I indicated earlier, **lirc** worked quite well with these devices in previous releases of Mythbuntu. Can anyone assist with this problem, or at least offer some thoughts on where the problems may have arisen with Mythbuntu 10.10? :(

---

### Post by mike_perth on 2011-08-13
> **smi402 said:**
> I tried this procedure with the **IMON ffdc** device in my **Antec 430** case and cannot get it to work so I guess the procedure is only for the newer **IMON 0038 ** devices. So, the appeal is for a procedure for getting **lirc** to work on Maverick 10.10 with the **IMON ffdc** device and a **Logitech Harmony 525 Universal Remote**. As I indicated earlier, **lirc** worked quite well with these devices in previous releases of Mythbuntu. Can anyone assist with this problem, or at least offer some thoughts on where the problems may have arisen with Mythbuntu 10.10? :(

i know this was a long time ago, but smi402 have you tried downloading the latest v4l bundle and compiling and installing that? i think that's where the new imon module comes from. no idea if it will change your situation for sure though...

[http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

---

