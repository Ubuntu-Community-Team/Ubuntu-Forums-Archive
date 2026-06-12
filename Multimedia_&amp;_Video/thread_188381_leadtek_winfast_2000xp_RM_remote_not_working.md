---
title: "leadtek winfast 2000xp RM remote not working"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by Spleenie on 2006-06-04
I have posted about this in response to another thread in a Hoary 5.04 hardware section. I realise that solutions and method may have changed into the Dapper release so I am more or less reposting here.

I have a Winfast 2000 XP RM TV tuner card. I initially had trouble with the tuner but changing the tuner type to 38 rather than 5 in modprobe fixed that particular problem. I now have audio and video through all connections.

Just one other minor detail. Anyone got the remote to work? :)

I have installed lirc and obtained the config file for the Leadtek RM remote control.

I have been unable to get the remote working at all. Has anyone had some success here?

Here is my relevant dmesg output for the tuner card:

```

[4294691.208000] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 5, latency: 32, mmio: 0xe6023000
[4294691.208000] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[4294691.208000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[4294691.208000] bttv0: gpio: en=00000000, out=00000000 in=003ff102 [init]
[4294691.209000] bttv0: using tuner=38
[4294691.209000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[4294691.211000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294691.214000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294691.216000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4294691.230000] sis900.c: v1.08.09 Sep. 19 2005
[4294691.230000] **** SET: Misaligned resource pointer: d85e88c2 Type 07 Len 0
[4294691.230000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294691.230000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294691.232000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[4294691.297000] 0000:00:04.0: Using transceiver found at address 1 as default
[4294691.297000] eth0: SiS 900 PCI Fast Ethernet at 0xe800, IRQ 11, 00:01:6c:a7:8e:7f.
[4294691.392000] i2c-sis96x version 1.0.0
[4294691.392000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x10c0
[4294691.454000] Real Time Clock Driver v1.12
[4294691.459000] FDC 0 is a post-1991 82077
[4294691.488000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[4294691.488000] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[4294691.554000] bttv0: registered device video0
[4294691.554000] bttv0: registered device vbi0
[4294691.554000] bttv0: registered device radio0
[4294691.554000] bttv0: PLL: 28636363 => 35468950 .. ok
[4294691.585000] bttv0: add subdevice "remote0"
[4294691.612000] input: PC Speaker as /class/input/input1
[4294691.648000] bt878: AUDIO driver version 0.0.0 loaded
[4294691.648000] bt878: Bt878 AUDIO function found (0).

```

Here is my /etc/lirc/lircd.conf file

```

#
# this config file was automatically generated
# using WinLIRC 0.6.4 (LIRC 0.6.1pre3) on Sun Nov 03 14:25:14 2002
#
# modified by CB
#
# contributed by Erik Christiansson, aka Sci
# www.alphafish.com
# erik@alphafish.com
#
# brand:             Leadtek
# model:             RM-0010 (bundeled with TV2000 TV-card)
#
# modifications based on the config files from
# Juan Toledo <toledo@users.sourceforge.net> and
# Markus Lischka <mlischka@users.sourceforge.net>
# Reza Naima
#
# Only CH_UP, CH_DOWN, VOL_UP and VOL_DOWN will repeat. This seems to
# be a hardware limitation.
#


begin remote

  name  RM-0010
  bits           16
  flags SPACE_ENC|CONST_LENGTH
  eps            40
  aeps          100

  header       9000  4500
  one           563  1687
  zero          563   562
  ptrail        563
  repeat       9000  2250
  pre_data_bits   16
  pre_data       0xC03F
  gap          108000
  toggle_bit      0

  frequency    38000
  duty_cycle   33

      begin codes
          POWER                    0x00000000000000FF
          TV/FM                    0x00000000000040BF
          SCAN                     0x000000000000A857
          DISPLAY                  0x0000000000006897
          1                        0x000000000000A05F
          2                        0x000000000000609F
          3                        0x000000000000E01F
          4                        0x000000000000906F
          5                        0x00000000000050AF
          6                        0x000000000000D02F
          7                        0x000000000000B04F
          8                        0x000000000000708F
          9                        0x000000000000F00F
          0                        0x00000000000048B7
          RECALL                   0x0000000000008877
          ENTER                    0x000000000000C837
          CC                       0x000000000000F807
          MTS                      0x000000000000D827
          FINE_DOWN                0x0000000000009867
          FINE_UP                  0x00000000000018E7
          VIDEO                    0x0000000000007887
          MUTE                     0x00000000000028D7
          CH_UP                    0x00000000000030CF
          CH_DOWN                  0x00000000000008F7
          VOL_DOWN                 0x00000000000010EF
          VOL_UP                   0x00000000000020DF
          FULLSCREEN               0x000000000000C03F

# The following are only supported by the remote control bundled with
# the WinFast TV 2000 XP Deluxe card.

          SLEEP                    0x00000000000002FD
          BOSS_KEY                 0x000000000000926D
          RED                      0x000000000000D22D
          GREEN                    0x00000000000032CD
          YELLOW                   0x000000000000B24D
          BLUE                     0x000000000000728D
          PIP                      0x00000000000052AD
          .                        0x000000000000827D
          BACK                     0x00000000000042BD
          PLAY                     0x000000000000C23D
          NEXT                     0x00000000000022DD
          TIMESHIFT                0x000000000000A25D
          STOP                     0x000000000000629D
          REC                      0x000000000000E21D
          SNAPSHOT                 0x00000000000012ED

# Only found on CoolCommand remote

          REPEAT                   0x000000000000884B
          TELETEXT                 0x000000000000F807
          TV                       0x0000000000006A95
          FM                       0x000000000000EA15
          DVD                      0x0000000000001AE5
          CLEAR(C)                 0x0000000000000AF5
          MENU                     0x000000000000F20D
          CH_SURF                  0x0000000000008A75
          ENTER                    0x000000000000C837
          AUDIO                    0x000000000000D827
          CC                       0x0000000000004AB5
          REW                      0x0000000000002AD5
          STOP                     0x000000000000629D
          FFW                      0x000000000000AA55
      end codes

end remote

```

Is there anything more I needed to do?

Cheers, Spleenie

---

### Post by teet on 2006-06-04
I have a leadtek winfast tv 2000 xp rm tuner with the cool command remote.

I had the remote sort of working with breezy and I just upgraded to dapper yesterday.  I only really wanted to use the remote with MythTV.  Only about half of the buttons worked right for some reason, but luckily it was the most important buttons (the number buttons, volume +/-, channel +/-, skip ahead/back, pause, etc.). 

Currently I'm trying to sort things out because the method I used to get LIRC up and running under Breezy isn't working.  Here's a link to the guide I made for the leadtek card:  [http://www2.truman.edu/~dat725/htpc_single.html](http://www2.truman.edu/~dat725/htpc_single.html)

When I figure it out I'll update my guide and try to remember to post back here :)

-teet

---

### Post by teet on 2006-06-04
```
alex@htpc:/usr/src/lirc-0.8.0$ sudo modprobe lirc_gpio
WARNING: Error inserting lirc_dev (/lib/modules/2.6.15-23-686/misc/lirc_dev.ko): Invalid module format
FATAL: Error inserting lirc_gpio (/lib/modules/2.6.15-23-686/misc/lirc_gpio.ko): Invalid module format
```

Here's the error I'm getting...

-teet

Update:  here's relevant dmesg output:

```

[4297577.163000] APIC error on CPU0: 00(40)
[4304800.118000] lirc_dev: no version for "struct_module" found: kernel tainted.[4304800.119000] lirc_dev: version magic '2.6.12-10-686 686 gcc-3.4' should be '2.6.15-23-686 SMP preempt 686 gcc-4.0'
[4304800.121000] lirc_gpio: version magic '2.6.12-10-686 686 gcc-3.4' should be '2.6.15-23-686 SMP preempt 686 gcc-4.0'
[4304832.903000] lirc_dev: version magic '2.6.12-10-686 686 gcc-3.4' should be '2.6.15-23-686 SMP preempt 686 gcc-4.0'
[4304832.907000] lirc_dev: version magic '2.6.12-10-686 686 gcc-3.4' should be '2.6.15-23-686 SMP preempt 686 gcc-4.0'
[4304832.909000] lirc_gpio: version magic '2.6.12-10-686 686 gcc-3.4' should be '2.6.15-23-686 SMP preempt 686 gcc-4.0'
[4307060.321000] lirc_dev: version magic '2.6.12-10-686 686 gcc-3.4' should be '2.6.15-23-686 SMP preempt 686 gcc-4.0'
[4307060.323000] lirc_gpio: version magic '2.6.12-10-686 686 gcc-3.4' should be '2.6.15-23-686 SMP preempt 686 gcc-4.0'
[4307806.573000] lirc_dev: version magic '2.6.12-10-686 686 gcc-3.4' should be '2.6.15-23-686 SMP preempt 686 gcc-4.0'
[4307806.575000] lirc_gpio: version magic '2.6.12-10-686 686 gcc-3.4' should be '2.6.15-23-686 SMP preempt 686 gcc-4.0'

```

---

### Post by Spleenie on 2006-06-04
[QUOTE=teet]I have a leadtek winfast tv 2000 xp rm tuner with the cool command remote.

I had the remote sort of working with breezy and I just upgraded to dapper yesterday.  I only really wanted to use the remote with MythTV.  Only about half of the buttons worked right for some reason, but luckily it was the most important buttons (the number buttons, volume +/-, channel +/-, skip ahead/back, pause, etc.). 

Currently I'm trying to sort things out because the method I used to get LIRC up and running under Breezy isn't working.  Here's a link to the guide I made for the leadtek card:  [http://www2.truman.edu/~dat725/htpc_single.html](http://www2.truman.edu/~dat725/htpc_single.html)

When I figure it out I'll update my guide and try to remember to post back here :)

-teet[/QUOTE]


Thanks for the help, however I still havent got it to work.

I installed lirc via apt-get. Was this the appropriate way to do it? Do I still have to download the kernel source and do all that stuff? btw my kernel version (2.6.15-23-386) didn't work when I tried to download the source.

```
sudo apt-get install linux-source-2.6.15-23-386 linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-source-2.6.15-23-386

```

It sounds like our hardware is 100% identical. I would really love to get this to work :) I am also using Dapper, so I suppose I should not expect the guide to apply, and as you say it isn't working for you either. Perhaps it works without all the compiling and we are just missing the next easy step :)

Cheers, Spleenie

---

### Post by teet on 2006-06-04
[QUOTE=Spleenie]Thanks for the help, however I still havent got it to work.

I installed lirc via apt-get. Was this the appropriate way to do it? Do I still have to download the kernel source and do all that stuff? btw my kernel version (2.6.15-23-386) didn't work when I tried to download the source.

```
sudo apt-get install linux-source-2.6.15-23-386 linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-source-2.6.15-23-386

```

It sounds like our hardware is 100% identical. I would really love to get this to work :) I am also using Dapper, so I suppose I should not expect the guide to apply, and as you say it isn't working for you either. Perhaps it works without all the compiling and we are just missing the next easy step :)

Cheers, Spleenie[/QUOTE]

As far as I know, the LIRC via apt-get is broken (there are several threads on this forum that discuss it) and you MUST build your own module.  Here is the contents of my /etc/apt/sources.list file (it should contain the linux-source package that you need):

```

#deb file:///cdrom/ dapper main restricted
#deb cdrom:[Ubuntu 5.10 _dapper Badger_ - Release i386 (20051012)]/ dapper main restricted

deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

I have a lot to do tomorrow so I probably won't get a chance to look into this further for a couple days...I'll get it going eventually :)  If not, I'll just buy a wireless keyboard or something. 

-teet

---

### Post by teet on 2006-06-12
Sorry for the delay in getting back to you but I had a really busy week.

I ended up doing a fresh format and reinstall of Dapper.  This didn't end up being that big of a deal seeing as how I had a seperate /home and /video partition.  After reinstalling, I followed my guide:

[http://www2.truman.edu/~dat725/htpc_single.html](http://www2.truman.edu/~dat725/htpc_single.html)

and was able to get things set up for the most part...but the mythtv packages in the repos and mysql5 don't mix together very well.  First of all, when I was installing apache and all that jazz, I had to also install the following:
```
sudo apt-get install libapache2-mod-php5 
```
This fixes it so you can actually log into phpmyadmin from firefox.  If you follow my guide to the T, you'll get stuck at that step and see what I mean.

Next up, I kept getting these errors when I tried to run mythfilldatabase and I couldn't download the program guide (which makes myth pretty much useless).  The error is outlined here:  

[http://www.ubuntuforums.org/showthread.php?t=125571&highlight=mythfilldatabase](http://www.ubuntuforums.org/showthread.php?t=125571&highlight=mythfilldatabase)

The solution I found was to download the 2 *.deb files listed in the 6th post from the above link and install them.

Okay, now onto your problem...getting the remote to work.  I just followed my own guide and things worked perfectly:

[http://www2.truman.edu/~dat725/htpc_single.html#htpc6](http://www2.truman.edu/~dat725/htpc_single.html#htpc6)

I followed steps 1-9 (NOT STEP 10) and my remote works just as well as it did  under breezy!  I haven't tried configuring my remote to work with an lircrc file yet.  I assume mythtv has some sort of builtin remote support.  In any event, you should be able to follow my guide and get your remote working.  Let me know if you need more help.  I don't know all that much about this stuff, but I'll certainly give it the old college try :)

-teet

EDIT:  I just saw why you were getting an error message in your above post.  The correct code should be:

```
sudo apt-get install linux-source-2.6.15 linux-headers-`uname -r`
```

Note the omission of the "-23-386".  If you read my guide carefully, I think it says that #ker# is shorthand for 2.6.15 only without the -23-386 part.  This will be important to keep in mind for later in my guide.

---

### Post by huwshimi on 2006-06-13
I never quite managed to get my Winfast 2000 XP RM TV tuner card working. Care to write a quick guide to how you guys got yours working. Thanks very much guys (and sorry for hijacking your thread a bit).

Cheers,

Huw

---

### Post by Spleenie on 2006-06-13
[QUOTE=xi0nblue]I never quite managed to get my Winfast 2000 XP RM TV tuner card working. Care to write a quick guide to how you guys got yours working. Thanks very much guys (and sorry for hijacking your thread a bit).

Cheers,

Huw[/QUOTE]

This is how I got mine to work:

Remove bodgy mods that are there:

```
sudo rmmod bt878
sudo rmmod tuner
sudo rmmod bttv
```

Then change the tuner settings thusly (I believe ubuntu automatically and falsly puts the "tuner" at 5)

```
sudo modprobe bttv card=34 tuner=38
```

That should be it.

As for getting the remote to work, which is the purpose of the thread, well, kudos to teet for all his success, but, bloody hell, thats a lot of work to get an IR interface to work. In addition, I am not using mythtv (I am just using lightweights like kdetv) and my FreeBSD days taught me that mucking with the kernel (anyone done the cvsup dance?) can be painful and I am jinxed ever since.

I note that there is a kdelirc, but I have been able to find out very little about it. Has anyone had success with it? If I get desperate (which is not likely) I will follow teets advice. Just a shame that I have been talking people into Ubuntu left right and centre and the one thing that stops them from turning is  stuff like this. The windows software that came with the card sucked to all hell, but the remote worked out of the box. Says it all really.

smooches, Spleenie

---

### Post by huwshimi on 2006-06-13
what about radio? Will this work as well?

---

### Post by Spleenie on 2006-06-13
[QUOTE=xi0nblue]what about radio? Will this work as well?[/QUOTE]

My Winfast 2000xp RM card does not come with FM radio capability. I didn't really need it to anyway. If yours does, then I imagine it will work, just throw gnomeradio or something like that at it and see how you go. Keep in mind that perhaps yours doesnt have FM either. I just know mine doesn't

---

### Post by teet on 2006-06-14
> As for getting the remote to work, which is the purpose of the thread, well, kudos to teet for all his success, but, bloody hell, thats a lot of work to get an IR interface to work. In addition, I am not using mythtv (I am just using lightweights like kdetv) and my FreeBSD days taught me that mucking with the kernel (anyone done the cvsup dance?) can be painful and I am jinxed ever since.

I note that there is a kdelirc, but I have been able to find out very little about it. Has anyone had success with it? If I get desperate (which is not likely) I will follow teets advice. Just a shame that I have been talking people into Ubuntu left right and centre and the one thing that stops them from turning is stuff like this. The windows software that came with the card sucked to all hell, but the remote worked out of the box. Says it all really.


You're not alone...I hate messing around with the kernel too.  However, you really ARE NOT compiling your own kernel with "my" method.  All that you're doing is setting up the kernel source exactly the way it is running now so that you can properly build the lirc module to insert into your current kernel.  After you download the headers and kernel source it's seriously only like 10 minutes (less than that really) to follow my guide.  It's not that big of deal really, just give it a try.

Now, actually getting the remote to work with mplayer or whatever may be a pain, but one problem at a time I always say :)

-teet

---

### Post by ianmac on 2006-06-15
Thought I would add/confirm that the default tuner value that Ubuntu 6.06 picks up is tuner=5.  This is the value for a PAL tuner.  I found many places that said that this should be tuner=2 for US/NTSC (which is the same as where I am, which is Canada).  However, the Leadtek card that I have seems to be a newer revision, and I needed to use tuner=43 (which I think is what you used).

So in summary, if you are in Canada/US (and Mexico?), you need to use a tuner value of either 2 or 43.

Haven't got tvtime to work yet...  xaw works great, myth works ok, but won't do overlay...  still more to figure out...  I have a SiS 661FX onboard video, so I am guessing that is part of the problem.

Ian

---

### Post by Spleenie on 2006-06-21
I can see now that it isn't actually recompiling the kernel. It is actually a pretty reasonable method. Sorry if I came across as ungrateful; I really did appreciate your help.

For the record I did follow the instructions and got the beast working. It was quite a relief to see the little hexes with appropriate keycodes coming up with irw :)

Oh and getting it to work with kdetv was a cinch (once lirc was properly loaded of course)

I use gnome and xfce, not kde, but I found myself in kde one day and noticed in the kcontrolpanel a section under peripherals dealing with remote controls. I decided to run it from gnome

```
kcontrol
```

From there I went to the remote control configuration. My remote control was now there, it was simply a matter of choosing the application I wished to control (they were exclusively kde apps but I wanted to control kdetv anyway) and pressed "autopopulate" which autoloaded the key configurations. Neato! turned on kdetv and presto I was controlling it with the remote.

Thanks again!

[QUOTE=teet]You're not alone...I hate messing around with the kernel too.  However, you really ARE NOT compiling your own kernel with "my" method.  All that you're doing is setting up the kernel source exactly the way it is running now so that you can properly build the lirc module to insert into your current kernel.  After you download the headers and kernel source it's seriously only like 10 minutes (less than that really) to follow my guide.  It's not that big of deal really, just give it a try.

Now, actually getting the remote to work with mplayer or whatever may be a pain, but one problem at a time I always say :)

-teet[/QUOTE]

---

### Post by teet on 2006-06-21
Awesome!  Glad to hear you got it working.  Thanks for posting back with your reply...it may help somebody else out someday.

As a final note, remember that you'll probably have to go through this process everytime you upgrade your kernel.  Once you get it down, it only takes like 10 minutes or so to do, but I still find myself only upgrading my kernel every other version or so.

-teet

---

### Post by tlue on 2006-09-16
> **teet said:**
> I have a leadtek winfast tv 2000 xp rm tuner with the cool command remote.

I had the remote sort of working with breezy and I just upgraded to dapper yesterday.  I only really wanted to use the remote with MythTV.  Only about half of the buttons worked right for some reason, but luckily it was the most important buttons (the number buttons, volume +/-, channel +/-, skip ahead/back, pause, etc.). 

Currently I'm trying to sort things out because the method I used to get LIRC up and running under Breezy isn't working.  Here's a link to the guide I made for the leadtek card:  [http://www2.truman.edu/~dat725/htpc_single.html](http://www2.truman.edu/~dat725/htpc_single.html)

When I figure it out I'll update my guide and try to remember to post back here :)

-teet


I have an older Hauppauge TV-Card (KDETV says ist's a "Video4Linux2: BT878 video (Hauppauge (bt878))").
Your guide worked fine for me. (I have tried with several other guides yet but none of them worked at the end).
The only differences to your steps (for your card) where the following:

step 7: instead of "Driver configuration-->TV Card-->Winfast TV2000/XP (card=34)" I selected the Hauppauge-TV-Card in that menu.
I got a line at the end of that script saying:
"You will have to use the lirc_i2c kernel module."

step 8: I didn't do anything here. etc/modules already had my correct module lirc_i2c

step 9: I did "sudo modprobe lirc_i2c" instead of "sudo modprobe lirc_gpio" (that is quite logical becuase of my different selection in step 7 and the message from the script there.)

So, thanks very much for your help!
=D>

---

### Post by teet on 2006-09-17
> **tlue said:**
> I have an older Hauppauge TV-Card (KDETV says ist's a "Video4Linux2: BT878 video (Hauppauge (bt878))").
Your guide worked fine for me. (I have tried with several other guides yet but none of them worked at the end).
The only differences to your steps (for your card) where the following:

step 7: instead of "Driver configuration-->TV Card-->Winfast TV2000/XP (card=34)" I selected the Hauppauge-TV-Card in that menu.
I got a line at the end of that script saying:
"You will have to use the lirc_i2c kernel module."

step 8: I didn't do anything here. etc/modules already had my correct module lirc_i2c

step 9: I did "sudo modprobe lirc_i2c" instead of "sudo modprobe lirc_gpio" (that is quite logical becuase of my different selection in step 7 and the message from the script there.)

So, thanks very much for your help!
=D>

You're very welcome :D  I'm glad I could help.

For future reference, the link to my mythtv guide is now:  [http://www.missouri.edu/~datcnc/htpc_single.html](http://www.missouri.edu/~datcnc/htpc_single.html)

or you should be able to get to it from:

[http://www.missouri.edu/~datcnc/articles.html](http://www.missouri.edu/~datcnc/articles.html)

(I graduated from Truman and moved on to Mizzou btw :) )

-teet

P.S.  The lirc modules should be fixed in Edgy, so it will be really easy to setup your remote.  Plus, Edgy should have MythTV 0.20 (which was just released a few days ago).

---

### Post by zHyOn on 2007-02-05
Hi everyone, 
   I read this topic for a long time, I have a Winfast TV/Radio tuner 2000XP RM Y0400052, My RM works partially under kubuntu 6.10 (no need for install lirc, etc), searching in google, I found a patch in cx88_input.c that could solves this problem by setting timing for 1 ms as it was in the original driver, but I don't know how to use this patch. Some one would help-me, please?
   Change log of kernel 2.6.19 tells that there's a fix for Winfast 2000 XP RM:  Cx88: fix remote control on WinFast 2000XP Expert fix remote control. Is that true?

This link have a very interesting text about modifications on v4l/dvd about winfast cards and RM.
[http://www.linuxtv.org/downloads/snapshots/v4l-dvb-ChangeLog-20061209]("http://www.linuxtv.org/downloads/snapshots/v4l-dvb-ChangeLog-20061209")

Where I got this information: [http://lkml.org/lkml/2006/11/13/78]("http://lkml.org/lkml/2006/11/13/78")

thanks a lot!!

---

### Post by deadgobby on 2007-02-05
At least some one got that working that way. I have the same card and had problems getting the sucker to capture any type of video. Any one got it to work with Kino or other type of vid capture program.
Gobby

---

### Post by zHyOn on 2007-02-06
I use KDE-TV and MisthTV for capturing, works great, even Better than original windows program. :)

---

### Post by teet on 2007-02-06
> **deadgobby said:**
> At least some one got that working that way. I have the same card and had problems getting the sucker to capture any type of video. Any one got it to work with Kino or other type of vid capture program.
Gobby

My guide should theoretically work.  

[http://www.missouri.edu/~datcnc/htpc_single.html](http://www.missouri.edu/~datcnc/htpc_single.html)

For whatever reason, the card seemed to work best under Breezy Badger.  I never got it working 100% exactly the way I wanted it to in Dapper or Edgy.  Over Christmas I bought myself a cheap hauppauge PVR-150 (it was less than $60 after shipping and everything) so I haven't really messed with the leadtek card since.  I may end up slapping it back in my machine to use to watch live TV.  The live TV quality of the leadtek card is nothing short of excellent.

-teet

---

