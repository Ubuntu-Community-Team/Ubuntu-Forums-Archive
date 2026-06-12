---
title: "Help with an Actisys ACT-IR200L (act200l) IR Blaster"
date: 2008-06-12
forum: Mythbuntu
---

### Post by bblboy54 on 2008-06-12
I have been having nightmare after nightmare since I've decided to go to Dish network and use a set top box....  I have a PVR150 with the IR Blaster which always worked fine with Myth years ago when I used a set top box.  I figured it would be a no brainer to set up on MythBuntu 8.04 but I was apparently very wrong.  I posted a message on the forums here but had no luck on getting responses.  I decided to move on to a home-brew RS232 solution.....  more issues.  I finally broke down and got an Actisys ACT-200L (ACT-IR200L) and you'd think that the third time was a charm?  Wrong :(

Apparently MythBuntu doesn't have a configuration for this device in it's control center.  I haven't found any information to setting this up on MythBuntu so I've done some poking around on Google and I'm even more frustrated than I was before.  From what I gather the ACT-200L uses the lirc_sir module with the act200l driver.  I configured this using MCC and was greeted with a message when trying to (re)start lircd saying that act200l is not a valid driver.

Is it true that MythBuntu has removed support for this device?  I can't understand why they would but I'm at a total loss.

Any advice would be greatly appreciated.

---

### Post by Wayne_V on 2009-01-12
Did you ever get this resolved?   I never could get the Ubuntu 8.10 lirc packages to work with the act200l either.   Finally compiled it myself and now it works.   Basic steps:

1) $ sudo /etc/init.d/lirc stop ;  sudo dpkg --purge lirc lirc-x
2) get rid of lirc modules delivered w/ kernel:
       $ cd /lib/modules/`uname -r`/kernel/ubuntu
       $ sudo tar czf lirc.tgz lirc
       $ sudo rm -fr lirc
       $ lsmod | grep lirc
       $ sudo rmmod (any lirc modules)
       $ rm -f /dev/lirc*
       $ sudo depmod -e
3) install build stuff: $ sudo apt-get install linux-source linux-headers-`uname -r` dialog build-essential
4) get the latest tar ball from lirc.org and untar
5) run setup.sh, select driver config, IrDA h/w, act200l, then the correct serial port
6) save config but don't run configure
7) make sure .setup.config looks good
8) run configure.sh --prefix=/usr
9) sudo make (if it complains about anything missing it's  probably because I missed it in step 3)
10) sudo make install
11) $ setserial /dev/ttySX uart none
12) modprobe lirc_sir   (should now see /dev/lirc* devices again)
13) $ sudo irrecord  remote
        (record all your remotes buttons)
14) $ sudo cp remote /etc/lircd.conf
15) lircd -d /dev/lirc0

Now, you should be able to run:
$ irsend send_once <remote> <key>

where <remote> is the name you gave your remote in step 13 and <key> is one of the key names you recorded.

Steps 11, 12 and 15 are  required on each boot.

Good luck!

And here is a simple changer script that should work ($ changer 231)

```
#!/bin/sh

#REMOTE_NAME=philips
#REMOTE_NAME=blaster
#REMOTE_NAME=directtv
REMOTE_NAME=hrmc5  # from /etc/lircd.conf
for digit in $(echo $1 | sed -e 's/./& /g'); do
    irsend SEND_ONCE $REMOTE_NAME $digit
    sleep 1.8 # note, you may have to tweak the interdigit delay up a bit
done

# if you need to send an enter key after the digits put it her
# irsend SEND_ONCE $REMOTE_NAME K
```

---

