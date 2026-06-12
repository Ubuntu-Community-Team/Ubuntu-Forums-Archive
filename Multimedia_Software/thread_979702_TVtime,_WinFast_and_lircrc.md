---
title: "TVtime, WinFast and lircrc"
date: 2008-11-12
forum: Multimedia Software
---

### Post by nedmar on 2008-11-12
Hi all,

I'm using Ubuntu 8.0.4 LTS 
I managed to install lirc and make it work after few hours of trying different guides without any results, just by using the synaptic and installing almost every package containing the word "lirc" in it (not the most accurate way to do it, i know.it just worked...) 

The problem is that i have no ideea how to make/generate an lircrc and where to put that file so it controls the TVtime.

$cat /proc/bus/input/devices
returns ( pasted only the tvtuner part)
```

I: Bus=0001 Vendor=107d Product=6611 Version=0001
N: Name="cx88 IR (Leadtek Winfast 2000XP"
P: Phys=pci-0000:01:08.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:09.0/0000:01:08.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=100003
B: KEY=10afc336 2150a48 0 0 0 404 80010000 190 4801 1e0000 4400 100000 10000ffc


```

the /etc/lirc/hardware.conf looks like
```

REMOTE="Winfast TV2000/XP (card 34)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-path/pci-0000:01:08.0--event-ir"
REMOTE_LIRCD_CONF="leadtek/lircd.conf.RM-0010"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES="lirc_dev"
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```

the $dmesg | grep -i lirc returns
```
~$ dmesg | grep -i lirc
[ 3684.316363] lirc_dev: IR Remote Control driver registered, major 61 
[ 3684.343246] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[ 2096.130261] lirc_dev: IR Remote Control driver registered, major 61 
[ 4345.015532] lirc_dev: IR Remote Control driver registered, major 61 
[ 4940.715395] lirc_dev: IR Remote Control driver registered, major 61 
[ 2872.581048] lirc_dev: IR Remote Control driver registered, major 61 
[ 5764.706023] lirc_dev: IR Remote Control driver registered, major 61 

```
 (the lirc_i2c appeared because i followed at a certain point a guide for hauptage, trying to adapt it to my tvtuner.. )

the $ lsmod | grep -i lirc
 returns [COLOR="Red"]nothing[/COLOR]
the  /etc/udev/rules.d/85-lirc.rules looks like 
```
ACTION=="add", KERNEL=="lirc[0-9]", RUN="/etc/init.d/lirc restart udev"
ACTION=="remove", KERNEL=="lirc[0-9]", RUN="/etc/init.d/lirc stop udev"

```
and the output for $irw
```
:~$ irw
74 0 KEY_POWER event6
179 0 KEY_TV event6
181 0 KEY_RADIO event6
185 0 KEY_DVD event6
18e 0 KEY_RED event6
18f 0 KEY_GREEN event6
190 0 KEY_YELLOW event6

``` looks fine .

So, on my opinion the lirc is fine.. is working, the tvtime works as well with my tvtuner even if i had to add in the ~/.tvtime/tvtime.xml the following line
```
<option name="MixerDevice" value="/dev/mixer:cd"/>
``` so i can control the sound, but this has nothing to do with the subject..

[COLOR="DarkRed"]I just need to know how do i setup the lircrc and where to put the .lircrc (or where it should be located) .. what files to edit so that they point to the lircrc and make tvtime start when i press.. for example the TV button on the remote..[/COLOR]

Sorry if my questions seems stupid to some of you, but i'm a total newbie when it comes to lirc and linux in general.

Thank You all in advance.

```
~$ uname -r
2.6.24-21-generic

```

---

### Post by lovinglinux on 2008-11-12
Unfortunately, I'm not going to help, but ask for it.

I forgot about lirc because it was driving me crazy. I'm using the same Ubuntu version as yours and I followed several tutorials without luck.

So, after you installed all packages containing the word lirc what did you do? Is there a lirc icon in the menus or how else do you know it was installed correctly?

Did you manually changed any files suggested by some of the tutorials?

---

### Post by nedmar on 2008-11-12
> 
Did you manually changed any files suggested by some of the tutorials? 

i did manually edit the /etc/lirc/hardwaware.conf changing the line:

LOAD_MODULES=""
with 
LOAD_MODULES="lirc_dev"

saved and ~$sudo /etc/init.d/lirc restart
then ~$irw 
witch, when pressed the remote keys, returned
```
:~$ irw
74 0 KEY_POWER event6
179 0 KEY_TV event6
181 0 KEY_RADIO event6
185 0 KEY_DVD event6
18e 0 KEY_RED event6
18f 0 KEY_GREEN event6
190 0 KEY_YELLOW event6

```

[Edited (i forgot about this question)]
> So, after you installed all packages containing the word lirc what did you do? Is there a lirc icon in the menus or how else do you know it was installed correctly?
I supose the fact ~$irw gives some output means lirc was installed correctly.. or at least is working.I'm not completelly sure about that, so please correct me if i'm not right. 

so.. this is all i did.
i have to mention that even if i didn't manage to understand and configure the lircrc ... the remote somehow works if i manually start tvtime.
i have sound control.. and i can change channels by pressing the 0 to 9 keys.. anyway this is not the way it supposed to make it work.. plus that i have to remember the position of too many channels..

---

### Post by lovinglinux on 2008-11-12
Thanks for the quick reply. My problem was that I wasn't able to install lirc. After a lot of tests I finally managed to install and configure it.

This is my hardware.conf

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="PinnacleSysPCTVRemote"
REMOTE_MODULES="false"
REMOTE_DRIVER="pinsys"
REMOTE_DEVICE="/dev/ttyS0"
REMOTE_LIRCD_CONF="pinnacle_systems/lircd.conf.pctv"
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
LOAD_MODULES="lirc_dev"

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

Anyway, I guess you have to put the lircrc in the home directory, as mentioned in the quote below from [http://ubuntuforums.org/showthread.php?t=221299](http://ubuntuforums.org/showthread.php?t=221299)

> **Rilson Raposo said:**
> [FONT="Arial Black"][SIZE="4"]Totem[/SIZE][/FONT]

I use totem as my movie player. To make it work with your remote control, create a file named .lircd in your home folder

```

# gedit ~/.lircrc

```

To create a lircrc for TVTime check [[COLOR="Red"]**this page**[/COLOR]]("http://tvtime.sourceforge.net/lirc.html")

---

### Post by lovinglinux on 2008-11-12
I have confirmed. It is working here.

create the lircrc file

```
gedit ~/.lircrc
```

then add the following code:

```

    begin
      prog = irexec
      button = POWER
      config = tvtime &
      config = tvtime-command QUIT
    end
```

then run in terminal 
```

irexec --daemon
```

Hit the power button on your remote an TVTime should be launched.

---

### Post by nedmar on 2008-11-12
> I have confirmed. It is working here.



Worked here too( so basically this problem was solved for me)... till i rebooted the PC. Now the ~$irw output is blank.. 
Well, at least i know it can be done.. i'll see what i do next. 
Probabbly i'll purge lirc and start all over ..

Ty for the help lovinglinux.

---

### Post by lovinglinux on 2008-11-12
> **nedmar said:**
> Worked here too( so basically this problem was solved for me)... till i rebooted the PC. Now the ~$irw output is blank.. 
Well, at least i know it can be done.. i'll see what i do next. 
Probabbly i'll purge lirc and start all over ..

Weird. I don't have the same issue.

> **nedmar said:**
> Ty for the help lovinglinux.

I should thank you, because if you didn't start this thread I wouldn't bother trying to install lirc again anytime soon. The time I have spent searching for solutions today is nothing compared to what I have lost with this before. Now I have a working remote \\:D/

---

### Post by nedmar on 2008-11-13
OK.. now.. last night reinstalled the system... 
Reinstalled lirc.. just as related previously .. all worked fine till again.. rebooted.
For some reason, after reboot my /dev/lirc no longer exist.
Tryed ~$sudo lircd --nodaemon and ~$irw in a second terminal.The output was:
```
~$ sudo lircd --nodaemon
lircd-0.8.3pre1[13438]: lircd(userspace) ready
lircd-0.8.3pre1[13438]: accepted new client on /dev/lircd
lircd-0.8.3pre1[13438]: could not get file information for /dev/lirc
lircd-0.8.3pre1[13438]: default_init(): No such file or directory
lircd-0.8.3pre1[13438]: caught signal
Terminated
```

Googled a lot for some solutions.. but everything i found is very OUT of date.

So.. is there someone knowing for some tutorial that actually gives a working solution for lirc in Ubuntu Hardy or Intrepid ?

---

