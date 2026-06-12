---
title: "SnapStream FireFly RF Remote with 8.04"
date: 2008-04-28
forum: Mythbuntu
---

### Post by TheQuank on 2008-04-28
Hi All,

Has anyone been successful in getting a SnapStream FireFly R1000-1 RF remote to work with MythTV .21 on Hardy? I have Googled for days without any luck!!  Thanks in advance!!

---

### Post by snsv on 2008-05-11
Is your remote control getting recognized at all? i.e what happens when you type "irw" in the terminal window and press some keys in your remote control?

Type Ctrl C to exit

I had to change some values in hardware.conf to get it working on 7.10.. cannot get it working on 8.04.. IRW is not responding to remote key strokes

---

### Post by TheQuank on 2008-05-11
Same here, I can see the hardware in /dev but nothing in IRW. Still getting configuration errors in MCC despite updates. I guess I'll have to roll that frontend back to 7.10.  I am really surprised that no one else is having this issue.....  Any ideas?

---

### Post by snsv on 2008-05-12
[http://ubuntuforums.org/showthread.php?t=790479](http://ubuntuforums.org/showthread.php?t=790479)

This the thread that I posted on this error.. are you getting something similar?

---

### Post by laga on 2008-05-12
How did you set it up? What settings did you choose?

---

### Post by TheQuank on 2008-05-12
Hi All, 

Sorry for the delay!  In Gutsy was able to configure the remote in the MCC.  During the upgrade to Hardy I didn't install it nor did it keep my previous configuration.  I attempted to reinstall it using the SnapStream X10 RF in the MCC. When this failed I did some Googling and found some reports that it was named slightly different in hardware.conf. After double checking that it still would not work in both mythfronend and irw.  I also attempted to use the ati X10 RF userspace and kernel with the same result.  All three produce an error when attempting to automatically configure. Ubuntu automatically opened bug 224512 which I'm told is a duplicate of 228328.  Sorry I'm not more help, but there isn't much documentation on Hardy yet that I have been able to find regarding this. Any help would be great!

---

### Post by williammanda on 2008-05-16
I had no issues with getting snapstream remote working in Hardy. I have two remotes working on channels 5 and 8. Below are my Hardware.conf and Lircd.conf.

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream X10 RF"
REMOTE_MODULES="lirc_dev lirc_atiusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="atiusb/lircd.conf.atiusb"
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


```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.2(default) on Thu Dec 13 17:47:18 2007
#
# contributed by 
#
# brand:Snapstream Firefly RF Remote
# model no. of remote control:R1000
# devices being controlled by this remote:
# THIS IS SETUP FOR CHANNEL ID 8

begin remote

  name  Snapstream Firefly RF Remote
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x7000
  gap          235995
  toggle_bit_mask 0x80800000

      begin codes
          MAXI                     0xF1AC
          CLOSE                    0x4702
          1                        0xD28D
          2                        0x530E
          3                        0xD48F
          4                        0x5510
          5                        0xD691
          6                        0x5712
          7                        0xD893
          8                        0x5914
          9                        0xDA95
          0                        0x5C17
          BACK                     0xDB96
          ENT                      0x5D18
          VOL+                     0xCE89
          VOL-                     0x4D08
          MUTE                     0xCF8A
          FIREFLY                  0x4500
          CH+                      0xD08B
          CH-                      0x510C
          INFO                     0xF3AE
          OPTION                   0x742F
          UP                       0xDF9A
          DOWN                     0x6722
          LEFT                     0xE29D
          RIGHT                    0x641F
          OK                       0xE39E
          MENU                     0x611C
          EXIT                     0xE5A0
          REC                      0x6C27
          PLAY                     0xEAA5
          STOP                     0x6D28
          REW                      0xE9A4
          FWD                      0x6B26
          PREV                     0xF0AB
          PAUSE                    0x6E29
          NEXT                     0xEFAA
          MUSIC                    0x4B06
          PHOTOS                   0xCA85
          DVD                      0x4904
          TV                       0xC883
          VIDEO                    0x4C07
          HELP                     0xC681
          MOUSE                    0x722D
          A                        0xDE99
          B                        0x601B
          C                        0xE6A1
          D                        0x6823
      end codes

end remote
```

---

### Post by justNiz on 2008-05-28
hi williammanda:

I tried your config files exactly as posted and it doesn't work for me either.

I still get nothing from irw even with your config files installed. I'm guessing the kernel atiusb driver must be borked in Hardy. Did you also happen to modify or install your own atiusb driver by any chance?

Thanks,
Niz.

---

### Post by williammanda on 2008-05-30
I used mythbuntu to install the lirc driver. I selected the Snapstream option. Then copied the following files: .lirc, Lircd.conf and lircmd.conf.
Everything worked.
Thanks

---

### Post by superm1 on 2008-05-30
There was a thread that flew by complaining that the lircd.conf for ati's is a little too big.  That's likely the cause.  Any of the drivers using this will probably run into the issue.  Hopefully we can fix that in a nice way :)

---

### Post by pobski on 2008-06-04
> **williammanda said:**
> I used mythbuntu to install the lirc driver. I selected the Snapstream option. Then copied the following files: .lirc, Lircd.conf and lircmd.conf.
Everything worked.
Thanks

I'm a pretty big noobie to the whole linux "feel" of things and have a really loose grasp as to what is going on with a lot of the general OS and everything.  

[grovel]
Oh lords of mythbuntu save me from myself.
[/grovel]

Anyhoo, I'd really like to know where you found the .lirc, Lircd.conf and lircmd.conf to copy from.  I see them in the directory and I have been doing some research to find out exactly what each files talks about, but I'm curious where you are getting your source for the files in question.

Right now, I'm stuck between learning how to fix this and buying a different remote that's easier to set up >.<.  I'd rather learn how to fix it, but it looks like a rocky road ahead.

edit: i misread what you wrote because of inexperience.  Still trying to fix, but I understand how dumb i sounded.

---

### Post by LsrLine on 2008-08-06
I think I'm fairly close to getting it working... I'm using this as a guide which may help you [http://www.mythtv.org/wiki/index.php/Snapstream_Firefly](http://www.mythtv.org/wiki/index.php/Snapstream_Firefly) and this might help as well [http://bonq.net/flipp/2007/11/06/firefly-remote-mythtv/](http://bonq.net/flipp/2007/11/06/firefly-remote-mythtv/)

---

### Post by ruckstande on 2008-08-12
> **LsrLine said:**
> I think I'm fairly close to getting it working... I'm using this as a guide which may help you [http://www.mythtv.org/wiki/index.php/Snapstream_Firefly](http://www.mythtv.org/wiki/index.php/Snapstream_Firefly) and this might help as well [http://bonq.net/flipp/2007/11/06/firefly-remote-mythtv/](http://bonq.net/flipp/2007/11/06/firefly-remote-mythtv/)
How is it going with the remote? Did you get it resolved?

---

