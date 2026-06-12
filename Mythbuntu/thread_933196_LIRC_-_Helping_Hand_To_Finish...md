---
title: "LIRC - Helping Hand To Finish.."
date: 2008-09-29
forum: Mythbuntu
---

### Post by bartoon on 2008-09-29
Hi,

I just installed LIRC (actually it's not Mythbuntu but hardy heron 8.04) but when I run irw nothing happen while pressing on some remote buttons:

```

bart@bart-desktop:~$ irw


```

Here are some outputs :


```

bart@bart-desktop:~$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 

```

sudo mode2 -d /dev/lirc0 :
```

space 16777215
pulse 406
space 263
pulse 2086
space 875
pulse 260
space 583
pulse 633
space 1220
pulse 572
space 842
pulse 1109

```

my config file (generated thanks to irrecord) is located in /home/bart/bench.conf

this is my /etc/lirc/hardware.conf:
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Irman / UIR"
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/home/bart/bench.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_LIRCD_CONF="/home/bart/bench.conf"
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

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Serial Port Receiver"
RECEIVER_VENDOR="Generic"

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="Linux Input Layer compatible Remote"
REMOTE_VENDOR="Generic"

```

(my IR receiver is home made connected to the serial port  and the remote control is a random remote i took in my living room the brand is 'bench')

Any ideas ?

Thank You!

---

### Post by mindoms on 2008-09-29
> **bartoon said:**
> Hi,
my config file (generated thanks to irrecord) is located in /home/bart/bench.conf


that config file should be in /etc/lirc/lircd.conf IIRC
so
```
sudo cp /etc/lirc/lircd.conf /etc/lirc/lircd.conf_save
sudo cp /home/bart/bench.conf /etc/lirc/lircd.conf
sudo /etc/init.d/lirc restart
```

should do the trick, and irw should react on your remote.
If you want to add more remotes later, just append the text from irrecord to that file.

hth, stefan

---

### Post by SiHa on 2008-09-30
The problem, I think may be that you aren't loading any modules for the receiver. I Think you need **lirc_dev** and **lirc_serial** for a homebrew serial.
Anyway, I've found the easiest thing to do to get LIRC working is```
sudo dpkg-reconfigure lirc
```Pick the **Homebrew Serial(6550 compatible UART)** entry for the receiver. 
Copy your configuration to **/etc/lirc/lircd.conf** as in Stefan's post and you should be set.

This approach worked for my homebrew receiver first time.

Cheers,

Simon

---

### Post by bartoon on 2008-09-30
Yep it works now thank you guys!


[ I got one last optionnal & noob question..  Now that irw works.. how do I use LIRC with applications now ? Does SMPlayer supports it ? ]

---

### Post by foxbuntu on 2008-09-30
Check out applications for their support, but simply you need a .lircrc configuration to essentially map the lirc.conf buttons to actions in the applications

lircrc example:
```

begin
    prog = irxevent
    button = channel+
    repeat = 3
    config = Key Up CurrentWindow
end

begin
    prog = irxevent
    button = channel-
    repeat = 3
    config = Key Down CurrentWindow
end

```

---

### Post by SiHa on 2008-10-01
Run:```
mythbuntu-lirc-generator
```

This will generate keymapping lircrc files for about 6 apps (Mythtv, Mplayer, Xine are three).

Don't think it needs 'sudo', as the files are created under your home directory:

```
/home/<mythuser>/.lircrc
```
and
```
/home/<mythuser>/.lirc/Mythtv
/home/<mythuser>/.lirc/Xine
/home/<mythuser>/.lirc/Mplayer
etc...
.
.
.

```

The **.lircrc** file should just consist of include statements pointing to the files in **.lirc**.

One caveat: This generator expects your lircd.conf file to have standard button names (like 'ArrowUp', instead of just 'Up') I think you can use one of the predefined configs in **/usr/share/lirc/remotes/hauppauge** (for example) to get the names right.

Once you have this, restart lirc ```
sudo /etc/init.d/lirc restart
``` then restart whatever apps you want to control with LIRC.

---

