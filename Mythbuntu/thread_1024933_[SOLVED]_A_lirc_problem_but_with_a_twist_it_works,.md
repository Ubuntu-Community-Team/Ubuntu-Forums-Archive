---
title: "[SOLVED] A lirc problem but with a twist: it works, sort of."
date: 2008-12-29
forum: Mythbuntu
---

### Post by Blonddeeni on 2008-12-29
Oh no, yet another problem with lirc. Sorry all. But hey, this one is pretty cool, I've not seen this type of problem posted anywhere. :D

I've been trying to install Mythbuntu_8.10 for the last month now, but to very limited success. I have 7.10 running at the moment, and thought that I would have a go at doing a clean install of 8.10 on a seperate hard drive.
But after fighting my way through grub, ip addresses and so forth, lirc has finally convinced me to call it quits and call for help.


But here is the kicker: lirc sort of works, I think.
 I have limited use of the remote on a mythfrontend, (up down, left right, enter; and that's it), and when I push a button on the remote when I have a terminal screen running, I get that button appearing on the command line.
EG: Button "1" gives a "1" 
Button "Ok" is the same as "Enter" 
Button "Exit" gives "f".
Just as if I was typing on a keyboard.

Here are my machine's spec's.

MB Asus m2npv-vm
CPU 5200+ amd64
2 x 1G ram
2x 500G sata drives
1 80G drive.
remote Technisat TTS35AI
DVB-S card Skystar2
DVB-S card Techno Trend S-1401

And here are the rsults of various commands I've been playing with:

"sudo irw" gives the same result as typing on the command line, but no code to show what that button is assigned to, and irrecord fails to recognise any gap.

IE: "sudo irrecord -H dev/input -d /dev/input/event2 technisat_amd64"
    fails to recognise any gap and indeed, when the remote's button is pressed, that key is displayed just as on the command line.

sudo ps aux |grep lirc
root      7233  0.0  0.0   3072   548 ?        Ss   08:41   0:00 /usr/sbin/lircd --driver=dev/input --device=phys=usb-0000:00:0b.0-2/input0
root      7339  0.0  0.0   3236   800 pts/1    S+   08:45   0:00 grep lirc

sudo ps aux |grep irexec
root      7393  0.0  0.0   3236   796 pts/1    R+   08:56   0:00 grep irexec

sudo etc/init.d/lirc restart 
 * Stopping remote control daemon(s): LIRC     [ OK ] 
 * Loading LIRC modules                        [ OK ] 
 * Starting remote control daemon(s) : LIRC    [ OK ] 

sudo cat /proc/bus/input/devices gives the following for the remote:
I: Bus=0003 Vendor=147a Product=e02d Version=0110
N: Name="Formosa21 USB IR Receiver"
P: Phys=usb-0000:00:0b.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb1/1-2/1-2:1.0/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=10001b
B: KEY=e080ffdf 1cfffff ffffffff fffffffe
B: ABS=300 0
B: MSC=10


I copied the remote's keypress file across from the 7.10 system, and placed it in /usr/share/lirc/remotes/technisat and called it technisat_7.10
I then changed /etc/lirc/lircd.conf to show that file:
IE: "cat /etc/lirc/lircd.conf" (I've left out the bumpf at the beginning of the file for this post)
#Configuration for the Technisat MediaFocus I remote:
#include /usr/share/lirc/remotes/technisat/lircd.conf.mediafocusI
include /usr/share/lirc/remotes/technisat/technisat_7.10

I modified ~.lirc/mythtv so that the remote was technisat_7.10 for all buttons.
EG:  begin
    remote = technisat_7.10
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end


Here are my two hardware.conf files.

First the "Hardy" which doesn't work. :(
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="technisat_7.10"
#REMOTE="Custom"
REMOTE_MODULES=""
#REMOTE_DRIVER=""
#REMOTE_DRIVER="/dev/lircd"
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="phys=usb-0000:00:0b.0-2/input0"
REMOTE_LIRCD_CONF="technisat/technisat_7.10"
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
#LOAD_MODULES=""

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
#FORCE_NONINTERACTIVE_RECONFIGURATION="true"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""


Second "Gutsy" which works. :)

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
#REMOTE="technisat"
REMOTE="technisat"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
#DEVICE="dev/input"

#Note To Self: - this is the bottom left usb port on the rear panel, looking from
#the rear. Won't work if you later change where it's plugged in. Note the lowercase
# 'p'. Doesn't work with a capital 'P'.
# DEVICE="/dev/input/event2"
DEVICE="phys=usb-0000:00:0b.0-2/input0"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""


There you have it.
Lirc is running, but the keypress's appear on the command line, and yet do not go through to mythtv. 
irrecord produces "gap not found, can't continue" and while I am pressing the remote's key, it comes up on the screen as if I was typing on a keyboard.
irw just shows the key presses as if I was typing on a keyboard, but no code.
Running a terminal screen under Fiesty 7.10 does not give that result with the remote.

So I am at a complete loss now as to how to get lirc running. Seems a lot more complicated than from 7.10, which wasn't exactly easy either. 
Oh, and although I'm using these commands, ps aux, dmesg, and others, I'm not actually sure what they mean. The same with things like de/input and /dev/lircd (I've only been using computers since jan 2008)

Cheerio and here's hoping [-o<


PS: Does anyone know where the gui for configuring the network can be found? I've taken to "sudo nano /etc/network/interfaces"  and "/etc/hosts" whenever I want to connect to other computers or the interweb. (Being on dial-up and all I have to keep changing things around. Long story.).

---

### Post by newlinux on 2008-12-29
sounds like your remote/receiver is being recognized as a keyboard, and not by LIRC. I don't have much experience with that, but hopefully that will give you something else to look into.

---

### Post by Geurrilla on 2008-12-30
You'll need to edit /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi ->

Mine looks like this:

```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="saa7134 ir">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="IR-receiver inside an USB DVB receiver">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
  </device>
</deviceinfo>
```

---

### Post by maxim99 on 2008-12-30
Network is tricky depending on what you're looking to accomplish. If you want to use /etc/network/interfaces, then you can't use Network Manager. There are two services available to control your network interfaces. /etc/init.d/networking and /etc/init.d/NetworkManager

I'm not sure what files NetworkManager uses, but it doesn't use /etc/network/interfaces.

I would suggest disabling Network Manager from ever loading in any runlevel. I don't know how to do this from the GUI, but deleting the S files for it in /etc/rc*.d will do just the same.

I believe /etc/network/interfaces can do PPP connections, but i'm not familiar with it.

If you choose to disable Network Manager then also remove the applet from starting up automatically with each login. This can be done through the GUI on a settings window somewhere. I'm sorry I can't recall the exact location currently. It'll be called auto started apps or something similar. You can also delete the appropriate .desktop file from /home/user/.config/autostart/.

Sorry I don't know about LIRC.

---

### Post by Addanc on 2008-12-30
Same bug as mentioned [here]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/204960"); you need to adapt the solution mentioned [here]("http://ubuntuforums.org/showthread.php?t=985311") to your hardware.

---

### Post by Blonddeeni on 2009-01-01
Wow.
Thanks everybody.
I'll have a session with the beast and see if those fixes work.
Just have to make time away from work itself.

Cheers

---

### Post by Blonddeeni on 2009-01-01
WHOOOOOOO HOOOOOOO and BIG CHEESEY GRINS :biggrin:

It's all working now on the remote front.
The thing is, I'm not exactly sure which of the many changes I did to get it going, so I'll be slowly removing one change after another to see what the minimum fiddling around is needed.
Here are the web links I used, thanks everyone for these.

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/204960](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/204960)
[http://ubuntuforums.org/showthread.php?t=985311](http://ubuntuforums.org/showthread.php?t=985311)

In the meantime here are all the changes I did.

In order of commands they are:

lshal > lshal.txt	to give a list of the Hardware Abstract Layer, and then edit lshal.txt to find the name of the IR receiver and the event associated with it.

lshal |grep IR to just show the Infrared Remote information.

I would regularly check with a terminal screen to see if my remote's key presses were coming up on it, which would indicate that "hal" was still getting in the way.
When this finally stopped, I ran "irw".
When it just failed I knew I was making progress, and it was time to look at the hardware.conf file.
Once irw gave the code associated with the remote's key, then it was time to check the remote config file under /usr/share/lirc/remote/technisat/. Once done, check the ./lirc files.

Also I would use "ps aux |grep hal" or "grep event" or "grep lirc" to see what processes were going on. 

Regularly doing a reboot after each change made going a bit slow, but worked in the end.

The files I modified were:

 Modified /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi to the following:

```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="saa7134 ir">
        <merge key="info.ignore" type="bool">true</merge>
           </match>
      <match key="linux.device_file" contains_ncase="/dev/input/event2">
        <merge key="info.ignore" type="bool">true</merge>     
           </match>
      <match key="info.product" contains_ncase="info.product = Formosa21 USB IR Receiver">
        <merge key="info.ignore" type="bool">true</merge>
           </match>
  </device>
</deviceinfo>
```

This is to stop "hal" grabbing the event and the IR Receiver, so that lirc can use it instead.

Then modified /etc/udev/rules.d/60-symlinks.rules, which I found in the novaT fix in one of the above web links above, and added the following line:
[HTML]
# Create /dev/input/irremote symlink for Nova-T 500
KERNEL=="event*", ATTRS{name}=="IR-receiver inside an USB DVB receiver", SYMLINK+="input/irremote"[/HTML]

But I replaced the string "IR-receiverxxxx" with my "Formosa21xxx" (Found from "lshal |grep IR")

To quote from the post this came from:
 "This creates a symlink for the IR event, which avoids the annoyance of the event number moving around if you power-up with other periherals plugged in (e.g. a USB mouse)."
End quote.
So in other words, as the allocation of events can change from boot-up to boot-up, this locks event2 to my IR Reciever. At least that what **I** think it's doing. ;)

Next to be modified / checked was my hardware.conf.

Made sure my /etc/lirc/hardware.conf file's REMOTE_DEVICE= was pointing at the correct usb port on my motherboard. (IE:REMOTE_DEVICE="phys=usb-0000:00:0b.0-2/input0")
I used the command:
"sudo cat /proc/bus/input/devices" to find this physical device. 

I Made sure that I had the a lowercase "p" on that line. Although reported as an uppercase "P", my machine needs the lowercase.
(I didn't make it clear on my first post that my DVB-S card doesn't come with a port for the IR Receiver, but instead you just plug the receiver into a USB port on the motherboard).

Checked that my lircd.conf was pointing to the correct file. (technisat_7.10)
Made sure that that file had the correct header of "technisat_7.10" in it.
Made sure that my ~./lirc/mythtv had all the correct "remote = technisat_7.10" for the button presses.
Made sure that those button presses matched up with the names of the buttons in my technisat_710 file I  had generated.

IE:
[HTML]
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.2(dev/input) on Thu Feb  7 20:39:30 2008
#
# contributed by 
#
# brand:                       /tmp/lircd_test2.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  technisat_7.10
  bits           32
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          107984
  toggle_bit_mask 0x0

      begin codes
          Up                       0x80010067
          Right                    0x8001006A
          Down                     0x8001006C
          Left                     0x80010069
          Ok                       0x8001001C
          Red                      0x8001003F
          Green                    0x80010040
          Yellow                   0x80010041
          Blue                     0x80010042
          Sfi                      0x80010012
          Exit                     0x80010021
          Info                     0x80010017
          Vol+                     0x8001006A
          Vol-                     0x80010069
          CH+                      0x80010067
          CH-                      0x8001006C
          Tv                       0x80010043
          Menu                     0x8001003C
          1                        0x80010002
          2                        0x80010003
          3                        0x80010004
          4                        0x80010005
          5                        0x80010006
          6                        0x80010007
          7                        0x80010008
          8                        0x80010009
          9                        0x8001000A
          0                        0x8001000B
          Mute                     0x80010032
          Check                    0x80010017
          -/--                     0x13
          A/B                      0x1F
      end codes

end remote
[/HTML]
 


Example from my  ~./lirc/mythtv
[HTML]begin
    remote = technisat_7.10
    prog = mythtv
    button = Exit
    config = Escape
    repeat = 0
    delay = 0
end[/HTML]

And that all seems to have fixed the remote. It now works on mythtv no worries. A bit more fiddling with the other files in ~./lirc to make them match my "technisat_7.10" keys and hopefully I can move on to the next challenge

Cheers and Happy New Year to you all. Mine has started well:D

PS:  Hi maxim99. The Gui I was after at the end of my first post is the one that sits under System > Administration and is simply "Network". My bad for not being clear about that. It's on the Ubuntu desktop and the Feisty Mythbuntu.
Thanks for the ideas on where to dig though. I'll get my shovel out on that one once my brain clears later. cheers :D

---

