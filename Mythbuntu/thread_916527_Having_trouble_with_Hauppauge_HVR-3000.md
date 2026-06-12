---
title: "Having trouble with Hauppauge HVR-3000"
date: 2008-09-11
forum: Mythbuntu
---

### Post by uMuppet on 2008-09-11
I just got a new HVR-3000 hybrid card installed on my system.  My backend cant find any of the inputs, I have had a good dig around on the net for a fix to this and there doesn't seem to be any concrete ones.

Has anyone got there HVR-3000 going with the latest Mythbuntu build?

---

### Post by KuriKai on 2008-09-11
do you have the module for it installed and the firmware for the card?

---

### Post by uMuppet on 2008-09-11
No, where can I get them?

---

### Post by SATA on 2008-09-12
I followed this link to get mine working. Watching TV on it now.
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000)

Hope this helps


*EDIT* took me a while to work out that sfe.diff is for single frontend and mfe.diff is for multiple frontend. I went with mfe.

---

### Post by uMuppet on 2008-09-15
Whats the difference between SFE and MFE?

---

### Post by SATA on 2008-09-16
Im not too sure, I think its so you can record one channel and watch another (As long as they are on the same multiplex) at the same time.

---

### Post by Bloemetjesgordijn on 2008-11-04
Hope this will work, I have tried several things. Without any success.

Cheerz
Bloemetjesgordijn

---

### Post by saradisn on 2008-11-08
Same problem here. I have the same TV card and followed the guide mentioned above from linuxtv. The card is recognized , but when I open Kaffeine , there is no DVB-S options (and no analogue) , only DVB-T (which here in Patra , Greece still don't have any channels). I'm so desperate that I'll buy a sky star-2  if nothing works.:( :confused:

---

### Post by saradisn on 2008-11-10
to uMuppet and Bloemetjesgordijn:
Any luck?

---

### Post by nicola76b on 2008-11-11
I Have the same problem.
I also downgrade and recompile my kernel.
The problem in dmesg is ths:```

[ 1254.277816] cx22702_readreg: readreg error (ret == -121)
[ 1254.279483] cx22702_writereg: writereg error (reg == 0x0d, val == 0x00, ret == -121)
```
best regards,
    nicola

---

### Post by Bloemetjesgordijn on 2008-11-11
> **saradisn said:**
> to uMuppet and Bloemetjesgordijn:
Any luck?

Havent tried it yet. I was thinking of selling the card and buy a more supported on.

Hauppauge is one of many things I have to fix in Ubuntu:
- LCD / VDF screen
- Bluetooth not reconnecting
- Hauppauge
- Frostwire not exiting
- list keeps on growing... :???:

But I will try to give it a go this evening.

* Wish me luck*

Cheerz
Bloemetjesgordijn

---

### Post by nicola76b on 2008-11-11
> **SATA said:**
> I followed this link to get mine working. Watching TV on it now.
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000)

Hope this helps


*EDIT* took me a while to work out that sfe.diff is for single frontend and mfe.diff is for multiple frontend. I went with mfe.

Which kernel were used?
Do you used Steve Toth's repository ( 22 Sep 2008 ) or kewl.org HVR3000 ( 06 Mar 08 )? In the second case, pardon the dummy question from a newbe, since "/etc/modprobe.conf" does not exist in my ubuntu 8.10, where should I put "options cx88-dvb frontend=1" string?

Thank you very much,
   -nicola

---

### Post by saradisn on 2008-11-11
I not experienced too , so I tried both. With the second way , I created  a new file with the two lines 

options cx88-dvb frontend=0 
options cx88-dvb frontend=1

and name it  modprobe.conf .

Now which is the right one , I don't know. The Steve Toth's repository (22 Sep 2008 ) must be ,  but I haven't read any post with a successful installation.

---

### Post by nicola76b on 2008-11-11
probably you're right, but in this thread it seems (I hope for me..) that SATA make it works!!
This evening, if I have some time I try another test with the last sources (s2-mfe-6b6e9be35963.tar.bz2)..

  -nicola

---

### Post by saradisn on 2008-11-11
Could you give more infomation about that "the last sources (s2-mfe-6b6e9be35963.tar.bz2).." ?

---

### Post by Bloemetjesgordijn on 2008-11-11
Ok Here it is on Ubuntu 8.10 

sudo su

apt-get install mercurial

hg clone -r 7879 [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)  

wget [http://linuxtv.org/hg/~stoth/s2-mfe](http://linuxtv.org/hg/~stoth/s2-mfe)

patch -p1 < *fe-9159.diff                   (9159 is the up to date version)

I get an error: "bash: *fe-9159.diff: File of folder does not exist"

pls advise......

BTW is a patch needed as 9195 is the latest version??

---

### Post by nicola76b on 2008-11-12
in Italy we say: "FUNZIONA!!!!!!!!" :D
Yesterday night (I finished at 3:00 in this morning, and now I'm working..) I installed hauppauge hvr3000 and it works (dvb-t and dvb-s), didn't try other.
To get it work I re-installed ubuntu 8.04, and follow usual guide:
[http://www.i-owns-u.net/~ryan/Hauppauge_WinTV-HVR-3000.html](http://www.i-owns-u.net/~ryan/Hauppauge_WinTV-HVR-3000.html)

tonight I'm planning to reTest ubuntu 8.10, with which I can not made it work.
 
In my life I never had successfully patching nothing, also this time I compile complete v4l-sources available at Steve Toth's repository (on the top you can download bz2 complete file..)

Hope this help someone... I was desperate and I was selling my card, yesterday, instead, the big happening....

Best regards,
 nicola's newbie

---

### Post by nicola76b on 2008-11-12
> **saradisn said:**
> Could you give more infomation about that "the last sources (s2-mfe-6b6e9be35963.tar.bz2).." ?

I'm not expert, but I think it is the last complete v4l-sources available at Steve Toth's repository (on the top page you can download bz2 complete file..)

Hope this helps,
with ubuntu 8.04, and generic kernel "2.6.24-21-generic" I get it work.

PS: remember to reststart pc at the end of process..

---

### Post by nicola76b on 2008-11-14
I try also with clean installation of intrepid hybrid (without kernel recompiling..).

 IT WORKS!

ps: I can get it work with kaffeine under gnome (but I don't like kde..), no lucky with mythtv. If someone can get me some council...

  -nicola

---

### Post by saradisn on 2008-11-14
I'll install 8.10 and try it.

---

### Post by fastie81 on 2008-11-16
Hi Guys

Ok if you guys write a nice how-to you got it working on 8.04 and 8.10(witch I need to get working) I will give you a how to do the LCD in 8.10 and an Imod remote if you have one..
I have been looking to get this working and can't the Steve Toth's to work on my system.. 
If I can get it working I am sure I can try to get it working with mythtv
Please guys
Thanks
C

---

### Post by Bloemetjesgordijn on 2008-11-17
> **fastie81 said:**
> Hi Guys
Ok if you guys write a nice how-to you got it working on 8.04 and 8.10(witch I need to get working) I will give you a how to do the LCD in 8.10 and an Imod remote if you have one..
C

I would love to write a how-to, if for f..k sake I could get it working.

> **Bloemetjesgordijn said:**
>  

patch -p1 < *fe-9159.diff                   (9159 is the up to date version)

I get an error: "bash: *fe-9159.diff: File of folder does not exist"

pls advise......

BTW is a patch needed, as 9195 is the latest version??

BUMP * I hate bumping my own post*

---

### Post by fastie81 on 2008-11-17
Well as far as I know you should not need to patch Steve Toth's repository if you download that one. but for some reason I can get my devices but get no signal. and that is on a roof airial. 
I have been looking at this now for the last 4 weeks with no luck. 
I have see some guys getting it working that is why I ask for a how to.
maybe that will help you to..

Chris

---

### Post by saradisn on 2008-11-21
This site [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000") was updated with this line:

 "Kernels 2.6.28-rc1 and later have a working multiple frontend driver built in."

Does this mean that distros with the kernel reffered, will see the card without any other actions?

---

### Post by Bloemetjesgordijn on 2008-11-21
Well according to your mail it should.

I installed the patch so i cant verify it anymore.

Cheerz 

Bloemetjesgordijn

---

### Post by fastie81 on 2008-11-21
yes I saw that yesterday. So now rather than digging with the driver I am trying to get the new kernel installed.. ubuntu is sort of pissing on my battery. I was hopping there was a switch I can tick to say I want develepment packages but there is not and can get this kernel to compile. any one with some help, I even tried the KernelCheck from here.. no luck.
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

When it comes to kernel and ubuntu I am a nob.. I have done it may of times on fedora and there is a tick in the repos.. makes it easie..
PLease help would love to get this card working..
I can blow this install away, I am running 8.10 now.. 
C

---

### Post by fastie81 on 2008-11-23
Hi Guys

Some good news..
I can confirm that kernel 2.6.28 are working with the HVR3000
I did a clean install of 8.04.1 and just did a update and then installed kernelcheck and let it upgrade the kernel. 
Than I rebooted installed kaffeine and did a scan. it work. no changes just worked..
the current kernel is 2.6.28-rc6 but it is stable enough I think.
This is a big brake for me..
Hope this help you guys. if you need more info just give me a shout. 
Now I just going to see if my remote and LCD still works with the new kernel. 
C

---

### Post by saradisn on 2008-11-24
:lolflag:  I'll try it and tell you what happened.

---

### Post by Bloemetjesgordijn on 2008-11-24
Fastie81

Good for you :-)

I still cannot find any analogue channels....

In Kaffeien how many front ends can you select??
If I am correct there should be three: Analogue, DVB-T and DVB-S, as HVR is a tri card

I am a bit reluctant to do a kernel update....for two simple reasons:
1) if it aint broken don't fix it
2) I dont know how

On the other hand, if it gets my card working...I wil try it tonight.

Cheerz

Bloemetjesgordijn

---

### Post by nicola76b on 2008-11-24
I don't know because I don't tune analog tv, all what I needed was dvb-t and dvb-s..  :-|
bye
   -nicola

---

### Post by saradisn on 2009-02-17
Has anyone tried mythbuntu 9.04 alpha 4? I tried sidux 2009 with kernel 2.6.28 and I could watch analog tv (didn't try dvb-s). Black and white picture and no sound.

---

### Post by uMuppet on 2009-02-17
You can use 8.10 just upgrade the kernel to 2.6.28

---

### Post by saradisn on 2009-02-17
Well , I tried kernelcheck to upgrade the kernel , but I got an error message from it (kernelcheck). Think I 'll wait for the stable 9.04.

---

### Post by uMuppet on 2009-02-17
I had trouble using that program too.  I have upgraded without problem before to test this card so there is an easy way.

I'll have a dig for it soon.

---

### Post by saradisn on 2009-02-27
I installed mythbutnu 9.04 alpha 5. The card is recognized during the setup , found some channels , but when I try to watch , it returns to the menu (analoge). I'll try DVB-S and see what happens. Has anyone else tried?

---

### Post by SATA on 2009-02-27
I used Steve Toth's repository.

Took a little tweaking to get mythtv to work with it, But it all worked fine in the end (I can even use my remote (Even more tweaking!!!))

I did have to write a script to have the kernel module updated everytime a kernel update was released.

***EDIT***
The Script I wrote to automatically rebuild the modules from the latest source can be found here
[http://www.i-owns-u.net/hauppauge.sh](http://www.i-owns-u.net/hauppauge.sh)

This script needs to be put in ***/etc/kernel/postinst.d***

[I]If you would like it to stop deleting the old source files, Comment out these lines:
[/I]> echo Grabbing latest build available from [http://linuxtv.org/hg/~stoth/s2-mfe]("http://linuxtv.org/hg/%7Estoth/s2-mfe")
rm -rf $DRIVER
hg clone [http://linuxtv.org/hg/~stoth/s2-mfe]("http://linuxtv.org/hg/%7Estoth/s2-mfe")

---

### Post by saradisn on 2009-02-28
> Took a little tweaking to get mythtv to work with it, But it all worked fine in the end (I can even use my remote (Even more tweaking!!!))

Could you write a tutorial , how to set up mythtv-backend with this card? I can't do it.:(

---

### Post by SATA on 2009-02-28
> **saradisn said:**
> Could you write a tutorial , how to set up mythtv-backend with this card? I can't do it.:(

I'll try and find the time and i will whip one up.

My Mythbuntu box died last night so im in the process of re-installing it.

Im just stuck on my lirc config again. But the card and the backend are working beautifully.


I assume you'll be viewing via satellite ?
As i havent touched terrestrial or even attempted it.

---

### Post by saradisn on 2009-03-01
Yes , basically satellite .  In Greece , digital tv is not available everywhere. Can we watch analog TV alternatively?

---

### Post by SATA on 2009-03-01
As far as i know, Yes. But with that, your on your own

I can help with your sat setup provided you have all the settings

---

### Post by saradisn on 2009-03-01
Great! :P

---

### Post by SATA on 2009-03-01
> **saradisn said:**
> Great! :P


It may take a day or two before I can post some proper instructions as im currently fighting with my own setup (lirc)

But I'll let you know.

---

### Post by saradisn on 2009-03-01
> My Mythbuntu box died last night so im in the process of re-installing it.

Well , if only [this machine]("http://www.dreambox.org.uk/dreambox-8000.html") didn't cost so much. Don't misunderstand me , setting up a mythtv box , from an old pc and a TV card is a great challenge and I'm learning a lot , but sometimes patience has it limits. Thanks , in advance for you help.

---

### Post by SATA on 2009-03-02
> **saradisn said:**
> Well , if only [this machine]("http://www.dreambox.org.uk/dreambox-8000.html") didn't cost so much. Don't misunderstand me , setting up a mythtv box , from an old pc and a TV card is a great challenge and I'm learning a lot , but sometimes patience has it limits. Thanks , in advance for you help.


Heres the specs for the machine im currently dealing with: [http://wiki.linuxmce.org/index.php/User:IOU](http://wiki.linuxmce.org/index.php/User:IOU)

(Just have a few buttons left to map)

---

### Post by pj7 on 2009-03-11
I recently installed jaunty's kernel and have the card working again in intrepid. I used to use Steve Toth's repository but somehow it stopped working on intrepid kernels.

I use the card in Spain for DVB-T & DVB-S. 
The difference with the new kernel is the remote. I cannot get it to work with lirc any more. But it works fine as input device (keyboard).
All the buttons send keycodes and here is the keymap:
```

0x0000 =  11  # KEY_0
0x0001 =   2  # KEY_1
0x0002 =   3  # KEY_2
0x0003 =   4  # KEY_3
0x0004 =   5  # KEY_4
0x0005 =   6  # KEY_5
0x0006 =   7  # KEY_6
0x0007 =   8  # KEY_7
0x0008 =   9  # KEY_8
0x0009 =  10  # KEY_9
0x000a = 388  # KEY_TEXT
0x000b = 398  # KEY_RED
0x000c = 385  # KEY_RADIO
0x000d = 139  # KEY_MENU
0x000e = 370  # KEY_SUBTITLE
0x000f = 113  # KEY_MIN_INTERESTING
0x0010 = 115  # KEY_VOLUMEUP
0x0011 = 114  # KEY_VOLUMEDOWN
0x0012 = 412  # KEY_PREVIOUS
0x0014 = 103  # KEY_UP
0x0015 = 108  # KEY_DOWN
0x0016 = 105  # KEY_LEFT
0x0017 = 106  # KEY_RIGHT
0x0018 = 393  # KEY_VIDEO
0x0019 = 392  # KEY_AUDIO
0x001a = 367  # KEY_MHP
0x001b = 365  # KEY_EPG
0x001c = 377  # KEY_TV
0x001e = 163  # KEY_NEXTSONG
0x001f = 174  # KEY_EXIT
0x0020 = 402  # KEY_CHANNELUP
0x0021 = 403  # KEY_CHANNELDOWN
0x0022 = 363  # KEY_CHANNEL
0x0024 = 165  # KEY_PREVIOUSSONG
0x0025 =  28  # KEY_ENTER
0x0026 = 142  # KEY_SLEEP
0x0029 = 401  # KEY_BLUE
0x002e = 399  # KEY_GREEN
0x0030 = 119  # KEY_PAUSE
0x0032 = 168  # KEY_REWIND
0x0034 = 208  # KEY_FASTFORWARD
0x0035 = 207  # KEY_PLAY
0x0036 = 128  # KEY_STOP
0x0037 = 167  # KEY_RECORD
0x0038 = 400  # KEY_YELLOW
0x003b = 353  # KEY_SELECT
0x003c = 372  # KEY_ZOOM
0x003d = 116  # KEY_POWER

```

MythTv recognized rare keycodes like KEY_SUBTITLES but others like mplayer & vlc did not. So I modified the keymap of the remote and modified the key shortcuts in the programs that I mostly use (mythtv, mplayer & vlc) so that they are the same.

To see & modify the keymap install the fine little package called "input-utils".
Run "input-kbd" with the event device number of your remote to see the keymap. My remote used /dev/input/event6 so the input-kbd command I used is:
```

sudo input-kbd 6 > hvr3000.keymap

```
That dumped the keycode in hvr3000.keymap file.

To find out what event number your card uses run this code:
```

cat /proc/bus/input/devices |grep HVR300 -A 4 |grep H: | grep H: -n | grep 1 | grep -o event[01123456789] | grep -o [01234567890]

```


When you have the keymap in the file you can modify it:

```

0x003d = 116  # KEY_POWERKEY
0x003b = KEY_F6  # KEY_SELECT "Go" button
0x001c = KEY_F7  # KEY_TV
0x0018 = KEY_F8  # KEY_VIDEO
0x0019 = KEY_F9  # KEY_AUDIO
0x001a = KEY_F10  # KEY_MHP
0x000c = KEY_F11  # KEY_RADIO
0x001b = KEY_S  # KEY_EPG
0x0014 = 103  # KEY_UP
0x0015 = 108  # KEY_DOWN
0x0016 = 105  # KEY_LEFT
0x0017 = 106  # KEY_RIGHT
0x0025 =  28  # KEY_ENTER
0x000d = KEY_M  # KEY_MENU
0x001f = KEY_ESC  # KEY_EXIT
0x0010 = 115  # KEY_VOLUMEUP
0x0011 = 114  # KEY_VOLUMEDOWN
0x000f = 113  # KEY_MIN_INTERESTING  Mute button
0x0020 = KEY_UP  # KEY_CHANNELUP
0x0021 = KEY_DOWN  # KEY_CHANNELDOWN
0x0012 = KEY_I  # KEY_PREVIOUS
0x0035 = KEY_P  # KEY_PLAY
0x0030 = KEY_P  # KEY_PAUSE
0x0036 = KEY_ESC  # KEY_STOP
0x0037 = 167  # KEY_RECORD
0x0032 = 168  # KEY_REWIND
0x0034 = 208  # KEY_FASTFORWARD
0x0024 = 165  # KEY_PREVIOUSSONG
0x001e = 163  # KEY_NEXTSONG
0x0001 =   2  # KEY_1
0x0002 =   3  # KEY_2
0x0003 =   4  # KEY_3
0x0004 =   5  # KEY_4
0x0005 =   6  # KEY_5
0x0006 =   7  # KEY_6
0x0007 =   8  # KEY_7
0x0008 =   9  # KEY_8
0x0009 =  10  # KEY_9
0x0000 =  11  # KEY_0
0x000a = KEY_KPPLUS  # KEY_TEXT
0x000e = KEY_J  # KEY_SUBTITLE
0x000b = KEY_F2  # KEY_RED
0x002e = KEY_F3  # KEY_GREEN
0x0038 = KEY_F4  # KEY_YELLOW
0x0029 = KEY_F5  # KEY_BLUE
0x0022 = KEY_CHANNEL  # KEY_CHANNEL 
0x0026 = KEY_SLEEP  # KEY_SLEEP
0x003c = KEY_ZOOM  # KEY_ZOOM

```

I've changed the keymap so that all the buttons send a widely-recognizable keycode. Notice that I've changed the order of the keys, to group them as they lay physically on the remote. Also the last 3 codes/buttons do not exist on the remote of HVR3000, they are for other Hauppauge models I suppose.

Then with this code I put the new keymap on the remote:
```

sudo input-kbd -f hvr3000.keymap 6

```

Of course this has to be done on every boot, so you have to put it in a startup script.

Hope this helps some people.

---

### Post by daahli on 2009-04-11
Hey, I just got this card and it seems to work in Jaunty out of the box using Kaffeine. Even the remote works!

However, I can't figure out how to set up Mythtv to be able to toggle between DVB-S and DVB-T. Anyone able to point me in the right direction?

Thanks

---

### Post by dm7020s on 2009-05-24
Can the two sites help for you?
[http://www.dreambox7020s.com](http://www.dreambox7020s.com) andy [http://www.dreambox-500s.co.uk](http://www.dreambox-500s.co.uk) ,:p

---

### Post by vivichrist on 2009-07-29
I'm having trouble with this card under Jaunty. DVB-S works fine but DVB-T doesn't exist even though the /dev/dvb entries are all there. the modules are loaded but the DVB-T side is not connected up (looking via lsmod). I guess I'm going to need to install an old kernel.

---

