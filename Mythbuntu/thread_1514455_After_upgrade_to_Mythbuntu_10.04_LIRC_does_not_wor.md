---
title: "After upgrade to Mythbuntu 10.04 LIRC does not work as expected"
date: 2010-06-21
forum: Mythbuntu
---

### Post by mmarre on 2010-06-21
Hello all,

I have an strange issue which I can't resolve by myself. I already searched for a solution many hours.

History:
I used Mythbuntu before and it worked (!!!) well. So I am NOT a complete newbe with MythTV on Ubuntu. Last week I upgraded my system via automatic update. The update process completed without any error and I can use mythtv as before with one exception:

LIRC doen't work correct in mythfrontend. Only (!) the left button on the remote works. But ircat does return the correct key codes when they are pressed on the remote:

```

root@vdr:/home/mmarre/.lirc# ircat --config=mythtv mythtv
Left
Up
Down
Right
9
8
1
2
3
5
4
7
M
I
Escape

```

irw also returns the korrect key codes if pressed on the remote:

```

root@vdr:/home/mmarre/.lirc# irw
00000000800100ad 00 MUTE lirc
00000000800100a7 00 EXT lirc
0000000080010172 00 AB lirc
000000008001000b 00 POWER lirc
0000000080010074 00 1 lirc
0000000080010002 00 2 lirc
0000000080010003 00 3 lirc
000000008001006a 00 TVRADIO lirc
0000000080010004 00 4 lirc
0000000080010007 00 7 lirc
0000000080010009 00 9 lirc
0000000080010160 00 MENU lirc
0000000080010069 00 LEFT lirc
0000000080010077 00 UP lirc
0000000080010067 00 RIGHT lirc
0000000080010066 00 DOWN lirc
000000008001008b 00 BACK lirc
0000000080010177 00 RED lirc
00000000800100cf 00 GREEN lirc
000000008001009e 00 YELLOW lirc
00000000800100a8 00 BLUE lirc
0000000080010197 00 TXT lirc
0000000080010189 00 STOP lirc
000000008001016d 00 HELP lirc

```

Also, mythfrontend.log reports that the lircrc file is successfully initialized:

```

2010-06-21 07:21:54.810 LIRC: Successfully initialized '/dev/lircd' using '/home/mmarre/.mythtv/lircrc' config

```

Why does mythfrontend only accept the code for the LEFT button? The buttons of course are correct linked in the config file:

```

<snipped>
begin
    remote = lirc
    prog = mythtv
    button = LEFT
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = lirc
    prog = mythtv
    button = RIGHT
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = lirc
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = lirc
    prog = mythtv
    button = BACK
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = lirc
    prog = mythtv
    button = STOP
    config = Escape
    repeat = 0
    delay = 0
end
</snipped>

```

Any hints? Is there any other way to trace the arriving key codes in mythfrontend?
I found some hints with LIRC and the 2.6.32 Kernel and IOCTL but I am not sure if that this is the issue. 

If I kill the lircd service and press a remote key number i see the number in the console window.

Please let me know if you need further info.

Regards,
Michael

---

### Post by ehaus on 2010-06-29
I had a ton of trouble with LIRC after upgrading to 10.04, and tried many suggestions from the message boards, none that worked for me.

Turns out my LIRC kernel modules were not updated.  I needed to compile my kernel modules (in my case, lircd_dev and lirc_i2c among others).

I followed the instructions here:
[http://www.mythtv.org/wiki/ubuntu_lirc_install](http://www.mythtv.org/wiki/ubuntu_lirc_install)

The above example is meant for the Windows Media Center remote, so I had to change this for me (I use the Hauppauge 350 remote and it's IR receiver, so I had to load/unload lircd_dev and lirc_i2c).  

However, this fixed my problem, and have LIRC with MythTV (and Boxee) working again.

I don't remember having to build kernel modules when I upgraded to 9.10, so not sure what caused this to break.  But, now fixed.

---

