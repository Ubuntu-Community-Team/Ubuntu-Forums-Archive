---
title: "Getting lirc to work with ASUS MyCinema P7131-remote??"
date: 2008-05-18
forum: Multimedia Software
---

### Post by bve on 2008-05-18
I had responded to [this post]("http://ubuntuforums.org/showthread.php?p=4984072#post4984072"), however after I posted I realized it was in the forum archives...

> **doubledouce said:**
> Hi!

I'm setting up a freevo system to use with my TV. Everything is working, but I'm having a really hard time with the remote. I've google'd and searched for many, many, maaaany hours now, but I can't find a solution.

The driver for the card is listed when I "lsmod" so it seems to be working. I've looked at the remote using my camera and I can see the ir-light so the remote is working too. I also have "lirc_serial" and "lirc_dev" started. But if I try to test the remote using "sudo irrecord -d /dev/lirc0 /tmp/my_remote" it doesn't register any signals and end up saying 
"irrecord: no data for 10 secs, aborting
irrecord: gap not found, can't continue"

It's driving me crasy not being able to get this up and running. :(

Have anyone here successfully managed to use the remote that comes with the ASUS MyCinema P7131?? And could you please post how you did it?? :)



I'm in the same boat with the ASUS MyCinema P7131 remote.

What I am finding is lirc doesn't like the code for the enter button.

When I try irw it just dies with no output and lircd crashes, I know this because /etc/init.d/lirc restart fails when stopping.
```

burke@orion:~$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s):LIRC [fail] 
 * Loading LIRC modules [ OK ] 
 * Starting remote control daemon(s) :LIRC [ OK ] 
burke@orion:~$ 

```

This shows up in the syslog
```

May 17 20:36:56 orion lircd-0.8.3pre1[7400]: invalid code found for lirc.conf: Enter
May 17 20:36:56 orion lircd-0.8.3pre1[7401]: lircd(userspace) ready
May 17 20:39:51 orion lircd-0.8.3pre1[7401]: accepted new client on /dev/lircd
May 17 20:39:51 orion lircd-0.8.3pre1[7401]: initializing '/dev/lirc0'
May 17 20:39:51 orion lircd-0.8.3pre1[7401]: unable to open '/dev/lirc0'
May 17 20:39:51 orion lircd-0.8.3pre1[7401]: caught signal

```

The enter code in the config file is:
```

Enter                    0x8001001C

```

Anyone know what it should be? For now I have just removed it to test,  I still need to deal with the below error.

Also there is obviously a problem with my /dev/lirc0 - it doesn't exist
```

May 17 21:53:20 orion lircd-0.8.3pre1[5306]: accepted new client on /dev/lircd
May 17 21:53:20 orion lircd-0.8.3pre1[5306]: initializing '/dev/lirc0'
May 17 21:53:20 orion lircd-0.8.3pre1[5306]: unable to open '/dev/lirc0'
May 17 21:53:20 orion lircd-0.8.3pre1[5306]: caught signal

```

Any help is appreciated.

Thanks in advance
Burke

---

### Post by bve on 2008-05-28
bump...

So does anyone have any ideas here?

---

### Post by bve on 2008-06-02
Well this is disappointing, I bought the ASUS MyCinema P7131 because it is supposedly supported by lirc yet I can't get it to work and apparently nobody else has either :(

Anyone care to point me in the right direction to even try to get it functioning?

---

### Post by bve on 2008-06-15
in order to get my remote working I had to do the following:
download the latest video4linux source from [http://linuxtv.org/hg/v4l-dvb/](http://linuxtv.org/hg/v4l-dvb/)

patch /linux/drivers/media/video/saa7134/saa7134-cards.c file
by adding this line
       case SAA7134_BOARD_ASUSTeK_TVFM7135:
right below this line
        case SAA7134_BOARD_ENCORE_ENLTV_FM:
it is on about line 4330

patch /linux/drivers/media/video/saa7134/saa7134-input.c
by adding this line
       case SAA7134_BOARD_ASUSTeK_TVFM7135:
right below this line
        case SAA7134_BOARD_ASUSTeK_P7131_HYBRID_LNA:
it is on about line 323

compile and install
and now the remote works

---

### Post by mehturt on 2010-01-22
does the lircd start for you? because the remote sort-of works for me (some buttons work) but in order to get the others working I think I need to start up lircd

---

### Post by bve on 2010-01-25
> **mehturt said:**
> does the lircd start for you? because the remote sort-of works for me (some buttons work) but in order to get the others working I think I need to start up lircd

I no longer have the box I had this card in, however I did have problems with lircd until I found the solutions above.

AFAIK v4l still doesn't have support for this card in it, there are a couple cards with similar names - mine was analog tuner only - if that sounds like your card you will probably have to patch/recompile as above(with each kernel release).

Another problem I ran into was the fact the remote is treated as a usb device, so it changed assignment on each reboot. There are ways to 'pin' usb devices, however off hand I am not aware and I followed a howto/sample found somewhere on the net - sorry I don't recall where.

---

### Post by mehturt on 2010-01-26
thanks a lot. my card is P7131 dual and the remote acts sort of like a keyboard, without even lircd started

---

