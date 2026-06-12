---
title: "Lirc 0.8.6, homebrew receiver and Karmic Koala 9.10"
date: 2009-12-03
forum: Mythbuntu
---

### Post by Flaming_Amarant on 2009-12-03
Hello everyone!

This is my first post, but I'm a very satisfied user of Mythbuntu from some years now. It's a great project and I enjoy it very much.

Some days ago, I finally decided to upgrade my version from 8.04 to 9.10. I'm using now MythTV 0.22.

The problem is that lirc is not working anymore. I remember some years ago it was a major PITA making it work... and now everything is coming back!

So, here's my situation:

homebrew receiver connected to ttyS0.
I have loaded lirc_serial and lirc_dev modules

mode2 -d /dev/lirc0 works perfectly. I can see the codes when I press the buttons.

if I run lircd this way:

/usr/sbin/lircd -n --output=/var/run/lirc/lircd --device=/dev/lirc0 /etc/lirc/lircd.conf

I get:
lircd-0.8.6[27158]: lircd(default) ready, using /var/run/lirc/lircd

then i launch irw like this:

irw /var/run/lircd

and in my lircd I can see this:
lircd-0.8.6[27158]: accepted new client on /var/run/lirc/lircd

anyway, if I press the buttons, nothing happens.

I have an AOpen ea65 remote, and my /etc/lirc/lircd.conf includes its config file:
include "/usr/share/lirc/remotes/ea65/lircd.conf.ea65"

So, by looking at this, I guess that I verified my device is lirc0, the socket is accepting clients and is launched by specifying the device lirc0... where is the problem?

thanks!

---

### Post by OffAxis on 2009-12-03
what does
irsend LIST "" ""

give you?

can you post your /etc/lirc/hardware.conf file?

I recall there used to be something funny about running lircd directly (3 or 4 versions ago since I tried it) instead of lirc from the init.d folder...the references would get screwed up or something...

try running
sudo service lirc restart

or 
sudo /etc/init.d/lirc restart

and see if you get any better result.

---

### Post by Flaming_Amarant on 2009-12-03
thanks for your reply OffAxis,

irsend LIST "" "" gives me this:

irsend: EA65
irsend: EA65

I had already tested it with the service, the behavior is the same.

thanks

---

### Post by OffAxis on 2009-12-03
it listed it twice?

should just be once...

> irw /var/run/lircd

did you just mis-type this? the lircd entry should be in the lirc folder; 
/var/run/lirc/lircd, but I wouldn't use that (it won't throw an error even if there's no device detected; only if the daemon isn't running).
Much better to check the /dev/ folder for an lirc instance.
(I notice you did that on your mode2 check)

Beyond that, do you have the hardware.conf set up?
/etc/lirc/hardware.conf
There's a 
REMOTE_DEVICE=
line that should reference your device path.
```
REMOTE_DEVICE=/dev/lirc0
```

---

### Post by Flaming_Amarant on 2009-12-03
> **OffAxis said:**
> it listed it twice?

should just be once...



strange... got it twice

> **OffAxis said:**
> did you just mis-type this? the lircd entry should be in the lirc folder; 
/var/run/lirc/lircd, but I wouldn't use that (it won't throw an error even if there's no device detected; only if the daemon isn't running).

> **OffAxis said:**
> Sorry, it was a mistype. The path is actually /var/run/lirc/lircd 

Much better to check the /dev/ folder for an lirc instance.
(I notice you did that on your mode2 check)

Exactly, it work doing mode2 /dev/lirc0


> **OffAxis said:**
> Beyond that, do you have the hardware.conf set up?
/etc/lirc/hardware.conf
There's a 
REMOTE_DEVICE=
line that should reference your device path.
```
REMOTE_DEVICE=/dev/lirc0
```

I do... I'm attaching my /etc/lirc/hardware.conf and /etc/modprobe.d/lirc-serial.conf
(I just renamed them to txt so I could upload them)

---

### Post by OffAxis on 2009-12-04
Here's what my hardware.conf reconfigured to when I selected the Aopen remote

```
#Chosen Remote Control
REMOTE="AOpen XC Cube EA65 EA65-II"
REMOTE_MODULES=""
REMOTE_DRIVER="ea65"
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="ea65/lircd.conf.ea65"
REMOTE_LIRCD_ARGS=""

```

Aside from yours being a serial setup and needing a few modules, you're missing the value for REMOTE_LIRCD_CONF and REMOTE_DRIVER.
I know you're specifying on the command line, but I'm not entirely certain how the hardware.conf file plays into things. Information on it is very limited.
So, I'd update the REMOTE_DRIVER and REMOTE_LIRCD_CONF values to those above and try launching irw again (it defaults to watching /var/run/lirc/lircd so you don't need to specify it).

```
sudo service lirc restart
irw
```

---

### Post by OffAxis on 2009-12-04
> strange... got it twice

This thread might help:
[http://ubuntuforums.org/showthread.php?t=1345628](http://ubuntuforums.org/showthread.php?t=1345628)

---

### Post by Flaming_Amarant on 2009-12-04
I tried those modifications, but now this is what I get in the logs, after restarting lirc and launching irw

Dec  4 22:09:29 mce lircd-0.8.6[725]: accepted new client on /var/run/lirc/lircd
Dec  4 22:09:29 mce lircd-0.8.6[725]: EA65: device /dev/lirc0
Dec  4 22:09:29 mce lircd-0.8.6[725]: EA65: could not reset tty
Dec  4 22:09:29 mce lircd-0.8.6[725]: Failed to initialize hardware
Dec  4 22:09:29 mce lircd-0.8.6[725]: caught signal

I tried doing some setserial /dev/ttyS0 uart none, and restarted lirc. The logs:

Dec  4 22:10:47 mce lircd-0.8.6[1971]: accepted new client on /var/run/lirc/lircd
Dec  4 22:10:47 mce lircd-0.8.6[1971]: EA65: device /dev/lirc0
Dec  4 22:10:47 mce lircd-0.8.6[1971]: EA65: could not reset tty
Dec  4 22:10:47 mce lircd-0.8.6[1971]: Failed to initialize hardware
Dec  4 22:10:47 mce lircd-0.8.6[1971]: select() failed
Dec  4 22:10:47 mce lircd-0.8.6[1971]: Bad file descriptor
Dec  4 22:10:47 mce lircd-0.8.6[1971]: removed client

I checked with ps -A |grep lircd, only one instance.

thanks for your help!

---

### Post by Flaming_Amarant on 2009-12-08
A little update.

From the /etc/lirc/hardware.conf file, I changed again this line, which previously had ea65 as value to this:

REMOTE_DRIVER=""

Now if I restart lirc, I can see again this message:

Dec  8 09:12:13 mce lircd-0.8.6[4243]: accepted new client on /var/run/lirc/lircd
Dec  8 09:13:02 mce lircd-0.8.6[4243]: removed client

I also tried adding this to the same file (I saw it in some forum):

#Serial
COM_PORT=/dev/ttyS0
DRIVER_OPTS="irq=4 io=0x3f8"
setserial /dev/ttyS0 uart none

But the thing is that irw doesn't give any output yet... any other ideas?

---

### Post by ffonz on 2010-01-27
Hi Flaming_Amarant,

I have a EA65 running Koala as well. I got lirc running. 
I removed all the default lirc packages of Ubuntu.
Now install the sources from the official lirc homepage.
Install dialog package from the synaptic package manager and run
```
./setup.sh
```Now configure driver (EA65 is listed under 'other') and end with save & run configure.
```
make
make install
```I saw you already included ea65 to lircd.conf, then run
```
sudo lircd /etc/lirc/lircd.conf
irw

```Now irw is returning valid values. At least to me...

But now I have to figure out how get it running automatically at startup. Any ideas?

---

### Post by oneindelijk on 2010-05-26
Hi, 

I have a built in infrared port (HP compaq nx8220)
should Lirc work with this ?
I have been search around and tried numerous stuff, but even this mode2 thing mentioned in the first post yields no results.
Tried this in Karmic and now in Lucid...

---

### Post by ffonz on 2010-05-27
Hoi oneindelijk,

I just googled a little bit, and here I saw someone with the same hardware as you: [http://old.nabble.com/IR-laptop-chip-td21477485.html](http://old.nabble.com/IR-laptop-chip-td21477485.html)
He managed to get it working. Maybe you could get in contact with the writer.

BTW The answer for his question about probing is irw. With irw you can test your remote control.

---

