---
title: "Lirc + Hauppauge HVR4000"
date: 2010-03-07
forum: Multimedia Software
---

### Post by xCAFEBABE on 2010-03-07
Hi,

I spent over four hours searching into ubuntu forums and blogs about how to configure Lirc with  remote control of hauppauge hvr4000.

I gave up, so ask for help to community...

My configuration is
+ Mythbuntu 9.10 
+ Hauppauge HVR4000
+ Lirc 0.8.6
+ Also already installed inputlirc, lirc-x

There is the content of /etc/lirc/hardware.conf
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge-HVR4000-Remote"
REMOTE_MODULES="lirc_dev"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event6"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/etc/lirc/hvr4000.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
#TRANSMITTER_MODULES=""
#TRANSMITTER_DRIVER=""
#TRANSMITTER_DEVICE=""
#TRANSMITTER_SOCKET=""
#TRANSMITTER_LIRCD_CONF=""
#TRANSMITTER_LIRCD_ARGS=""

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

And there is the content of /etc/lirc/lircd.conf

```

begin remote

  name  		Hauppauge-HVR4000-Remote
  bits           	16
  eps            	30
  aeps		 	100

  one			0     0
  zero			0     0
  pre_data_bits		16
  pre_data		0x8001
  gap			133325
  toggle_bit_mask	0x8001001C

      begin codes
          Power                    0x0074
          Go                       0x0161
          TV                       0x0179
          Video                    0x0189
          Music                    0x0188
          Pictures                 0x016F
          Guide                    0x016D
          Radio                    0x0181
          Up                       0x0067
          Down                     0x006C
          Left                     0x0069
          Right                    0x006A
          OK                       0x001C
          Back/Exit                0x00AE
          Menu                     0x008B
          PrevCh                   0x019C
          Mute                     0x0071
          Vol+                     0x0073
          Vol-                     0x0072
          Ch+                      0x0192
          Ch-                      0x0193
          Rec                      0x00A7
          Stop                     0x0080
          Play                     0x00CF
          Pause                    0x0077
          Rewind                   0x00A8
          Forward                  0x00D0
          Replay                   0x00A5
          Skip                     0x00A3
          1                        0x0002
          2                        0x0003
          3                        0x0004
          4                        0x0005
          5                        0x0006
          6                        0x0007
          7                        0x0008
          8                        0x0009
          9                        0x000A
          0                        0x000B
          Text                     0x0184
          Sub/CC                   0x0172
          Red                      0x018E
          Green                    0x018F
          Yellow                   0x0190
          Blue                     0x0191
      end codes

end remote

```

Input device is /dev/input/event6

Because in /proc/bus/input/devices could see this

```

I: Bus=0001 Vendor=0070 Product=6902 Version=0001
N: Name="cx88 IR (Hauppauge WinTV-HVR400"
P: Phys=pci-0000:04:05.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:14.4/0000:04:05.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=100003
B: KEY=100fc312 214a80200000000 0 18000 41a800004801 9e168000000000 10000ffc

```


When i run this
```

sudo lircd -n -H devinput -d /dev/input/event6 

```

In /var/log/daemon.log could see this

```

lircd-0.8.6[6866]: lircd(default) ready, using /var/run
/lirc/lircd

```

Then if i run this
```

irw

```

In /var/log/daemon.log could see this

```

 lircd-0.8.6[6866]: accepted new client on /var/run/lirc
/lircd
 lircd-0.8.6[6866]: initializing '/dev/input/event6'
```

And then i try to push and hold some button of the remote, nothing happens.....

What im doing wrong??? Some advice??

Need to compile lirc?? Bug of ubuntu?? I dont know... By the way i checked that remote had battery ;)... The hauppauge hvr-4000 works becouse  view dvb-t tv.

---

### Post by xCAFEBABE on 2010-03-12
Anyone ?

---

### Post by xCAFEBABE on 2010-03-16
My gosh!!! 

After many tests, many hours spent, including test it on windows, I find into hauppauge forums the next message: 

"Is the IR Cable fully inserted into the card? you should here a definate click when it's all the way in. Sometimes the PC's case can stop it going all the way in"

That was it!!! So right now it works...

---

### Post by dabubu on 2010-03-18
I have exactly the same configuration as you.

I have spent WEEKS (off and on) looking for a solution and here it is!!!

Push the silly little jack all the way in AND IT WORKS!!

---

### Post by dabubu on 2010-03-18
I was so pleased when I saw your post that I forgot to say thanks.

So, THANK YOU.

I was about to throw it away.

---

### Post by karlrt on 2010-06-15
HAHA, this is crazy :) i am at least the forth who couldnt plug a cable right (cost me 2 days)

---

### Post by karlrt on 2010-06-15
as this is the thread for "my" remote, have you guys configured the first buttons:
```

          Power                    0x0074
          Go                       0x0161
          TV                       0x0179
          Video                    0x0189
          Music                    0x0188
          Pictures                 0x016F
          Guide                    0x016D
          Radio                    0x0181
```
correct? I cant get them to work with mythtv. Everythingelse works fine :) If in mythfrontend i want to configure those keys to anything, it looks like it doesnt get the signal, but thats not true:

```

Event: time 1276620907.479990, type 1 (Key), code 116 (Power), value 1
Event: time 1276620907.480000, -------------- Report Sync ------------
Event: time 1276620907.717398, type 1 (Key), code 116 (Power), value 0
Event: time 1276620907.717406, -------------- Report Sync ------------
Event: time 1276620913.088980, type 1 (Key), code 377 (TV), value 1
Event: time 1276620913.088991, -------------- Report Sync ------------
Event: time 1276620913.326388, type 1 (Key), code 377 (TV), value 0
```

so they are recognized somehow. Any help, or should I open a new thread?

---

