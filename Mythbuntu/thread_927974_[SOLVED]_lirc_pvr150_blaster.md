---
title: "[SOLVED] lirc pvr150 blaster"
date: 2008-09-23
forum: Mythbuntu
---

### Post by RoyalPro on 2008-09-23
I can't get my blaster to work on my haupuage pvr150.  I had it working before with ubuntu, but don't remember the the exact settings.  I have the remote part working, but when I try to add the "blaster" remote to the .conf I get the error "Segmentation fault".  I have messed around with the .conf(s) putting the "lirc_pvr150" in the transmitters and verious other things.  Can some one help me by showing me working .conf(s) and/or what I have to do to get it working  I have haup*.bin in /lib/firmware

Here is what my hardware.conf looks like
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES="lirc_dev lirc_pvr150"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/mycustom.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="none"
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
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""
```

Here is what my lircd.conf looks like
```
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

#Configuration for the Custom remote:
#include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge

include /usr/share/lirc/remotes/mycustom.conf
```

---

### Post by RoyalPro on 2008-09-23
[SOLUTION] I changed the blaster so that it was before the other remote in the mycustom.conf and now it works.
```
# My Custom configuration

# my attempt at blaster

begin remote
	name blaster
		bits 32
		flags RAW_CODES
		eps 0
		aeps 0
		plead 0
		gap 333333
		repeat_bit 0
		begin raw_codes
		    name 0
		    6029312
		    name 1
		    6029313
		    name 2
		    6029314
		    name 3
		    6029315
		    name 4
		    6029316
		    name 5
		    6029317
		    name 6
		    6029318
		    name 7
		    6029319
		    name 8
		    6029320
		    name 9
		    6029321
		    name POWER
		    6029322
		    name OK
		    6029335
		    name EXIT
		    6029336
		end raw_codes
end remote

begin remote

  name  Hauppauge_pvr150
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remote
```

---

### Post by bpowell2005 on 2008-11-03
> **RoyalPro said:**
> changed the blaster so that it was before the other remote in the mycustom.conf and now it works.

I'm struggling to get my PVR150 to work as well...can you please post your mycustom.conf file?

Right now, I'm running mythbuntu 8.10...I can get the remote to work, but when I un-remark the "include transmitter" section, I can no longer get IRW to report remote button presses.

Thanks!

---

### Post by RoyalPro on 2008-11-04
Here is mycustom.conf.  If there is anything else I can help with let me know, I know how frustrating it can be.  With this conf and the above and the haup*.bin in the firmware directory, mine is working.

```
# My Custom configuration

# my attempt at blaster

begin remote
	name blaster
		bits 32
		flags RAW_CODES
		eps 0
		aeps 0
		plead 0
		gap 333333
		repeat_bit 0
		begin raw_codes
		    name 0
		    6029312
		    name 1
		    6029313
		    name 2
		    6029314
		    name 3
		    6029315
		    name 4
		    6029316
		    name 5
		    6029317
		    name 6
		    6029318
		    name 7
		    6029319
		    name 8
		    6029320
		    name 9
		    6029321
		    name POWER
		    6029322
		    name OK
		    6029335
		    name EXIT
		    6029336
		end raw_codes
end remote

begin remote

  name  Hauppauge_pvr150
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remote
```

---

### Post by bpowell2005 on 2008-11-05
RoyalPro,

Here is a link to a thread where I've posted details about my errors: [http://ubuntuforums.org/showthread.php?p=6110234#post6110234](http://ubuntuforums.org/showthread.php?p=6110234#post6110234)

I can see some big differences in your hardware.conf from mine...namely, you transmitter section is not populated. I may look at changing my hardware.conf to match yours and try again. I got a little closer, but as you can see from the link above, I'm still getting "transmission failed"....

This is very frustrating...I feel like I'm close...but not there yet! ](*,)

Thanks for your help and for posting your .conf files...I'll copy liberally and see what happens!

---

### Post by ed3120 on 2008-12-03
How is this solved when there is no solution listed?

---

### Post by RoyalPro on 2008-12-03
> **ed3120 said:**
> How is this solved when there is no solution listed?

Sorry that I didn't make it more clear in my second post in it I said I listed the "blaster" before the other remote "Hauppauge_pvr150" in mycustom.conf.  I had the haup listed first and it didn't work then with the blaster listed first it did.  Thats all.  My solution was that simple.

---

### Post by bblboy54 on 2009-01-06
I'm really stressed with this whole ordeal.  I have been fighting with getting my IR Blaster working for months now and I just now decided to install the latest alpha because, well, it couldn't be worse than where I'm at now.  I actually got A LOT further than before but right now I keep getting this:
```

root@mythbuntu-master:/etc/lirc# irsend SEND_ONCE blaster POWER
irsend: command failed: SEND_ONCE blaster POWER
irsend: unknown remote: "blaster"
root@mythbuntu-master:/etc/lirc# 

```
:confused:

I've tried many different layouts of the config files including what you have listed but I keep ending up with the same thing.  I also tried putting my remote config in lircd.conf it's self but that doesn't seem to work either.

```

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

#Configuration for the Hauppauge TV card remote:
#include "/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"

#Configuration for the Hauppauge PVR-150 (pci) : Dish Receiver transmitter:
#include "/usr/share/lirc/transmitters/dish/general.conf"

begin remote

name blaster
bits 32
flags RAW_CODES
eps 0
aeps 0
plead 0
gap 333333
repeat_bit 0

begin raw_codes
name 0
2149318656
name 1
2149318657
name 2
2149318658
name 3
2149318659
name 4
2149318660
name 5
2149318661
name 6
2149318662
name 7
2149318663
name 8
2149318664
name 9
2149318665
name POWER
2149318666
name CH_UP
2149318671
name CH_DOWN
2149318672
name MUTE
2149318673
name VOL_DOWN
2149318674
name CH_PREVIOUS
2149318675
name VOL_UP
2149318676
name DISPLAY
2149318677
name EXIT
2149318680
name GUIDE
2149318683
name SELECT
2149318686
name AV
2149318697
name ENTER
2149318699
name MENU
2149318703
name MUP
2149318704
name MDOWN
2149318705
name MLEFT
2149318706
name MRIGHT
2149318707
end raw_codes

end remote

```

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES="lirc_dev lirc_pvr150"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/blaster.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Custom"
TRANSMITTER_MODULES="lirc_dev lirc_pvr150"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_LIRCD_CONF="/usr/share/lirc/remotes/blaster.conf"
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

Those are my current files.....  any advice would be greatly appreciated.

Thanks

---

### Post by bblboy54 on 2009-01-06
Just found this.....

```

root@mythbuntu-master:/var/log# tail syslog 
Jan  6 20:03:47 mythbuntu-master kernel: [ 4178.993103] lirc_dev: lirc_register_plugin: sample_rate: 0
Jan  6 20:03:47 mythbuntu-master kernel: [ 4178.993242] i2c ir driver 3-0070: firmware: requesting haup-ir-blaster.bin
Jan  6 20:03:47 mythbuntu-master kernel: [ 4179.003020] lirc_pvr150: firmware of size 302355 loaded
Jan  6 20:03:47 mythbuntu-master kernel: [ 4179.003619] lirc_pvr150: 743 codesets loaded
Jan  6 20:03:47 mythbuntu-master lircd-0.8.4a[10449]: error in configfile line 62:
Jan  6 20:03:47 mythbuntu-master lircd-0.8.4a[10449]: "2147549184": must be a valid (lirc_t) number
Jan  6 20:03:47 mythbuntu-master lircd-0.8.4a[10449]: reading of file '/etc/lirc//lircd.conf' failed
Jan  6 20:03:47 mythbuntu-master lircd-0.8.4a[10449]: reading of config file failed
Jan  6 20:03:47 mythbuntu-master lircd-0.8.4a[10450]: lircd(default) ready
Jan  6 20:03:47 mythbuntu-master kernel: [ 4179.041960] lirc_pvr150: Hauppauge PVR-150 IR blaster: firmware version 1.3.0
root@mythbuntu-master:/var/log# 

```

It looks like lircd doesn't like the raw codes?

---

### Post by bblboy54 on 2009-01-06
I found the issue to my problem but no total solution.  Apparently when you are running on an AMD64 platform the raw codes don't work because you're working with a different base number set.  I reloaded with the i386 version and everything is working perfectly now.
:popcorn:

---

### Post by RoyalPro on 2009-01-07
> **bblboy54 said:**
> I found the issue to my problem but no total solution.  Apparently when you are running on an AMD64 platform the raw codes don't work because you're working with a different base number set.  I reloaded with the i386 version and everything is working perfectly now.
:popcorn:

Maybe something else got fixed in the reload, because I am using the 64 bit version.  Also if you look at mine above I have nothing in the transmitters section.

---

