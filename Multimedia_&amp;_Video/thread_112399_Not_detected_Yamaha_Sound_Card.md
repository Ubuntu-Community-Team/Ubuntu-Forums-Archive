---
title: "Not detected Yamaha Sound Card"
date: 2006-01-04
forum: Multimedia &amp; Video
---

### Post by antubis on 2006-01-04
My Ubuntu 5.10 Breezy Badger system did not found my Yamaha OPL sound card.
How can I configured it so I can use it?

Thanks to all!

P.S.
I fixed the problem by typing:

sudo modprobe opl3sa2

Now I have a crystal sound :)

---

### Post by az on 2006-01-04
add the module name to the end of /etc/modules so that it gets loaded at boot time, every time.

---

### Post by antubis on 2006-01-04
10x azz
This is a good sugestion!

---

### Post by Pnut on 2006-01-06
Hello to all the people that prefer to use linux instead of windows.  this is my 3rd day using a linux os and i think that i love it compared to windows.  on my first 2 days of playing with Ubuntu 5.10 BreezyBadger, I over came the hurdle of getting this os on my laptop and getting my laptop up on my wireless network.  The next hurdle to overcome is my sound drivers and i think that may have just happend.  I will repost if i was successful at making it work.  In the mean time 

OMGthisOSWTFPWNZWINDOWS

Pnut
the noob

---

### Post by FarEast on 2006-01-08
I am not sure, but have a try;) 
Describe the following (in 1 line) in /etc/modprobe.d/sound .

```
options snd-opl3sa2 snd_index=1 snd_id=OPL3
snd_port=0x370 snd_sb_port=0x370 snd_wss_port=0x530
snd_midi_port=0x330 snd_fm_port=0x388 snd_irq=5 snd_dma1=1
snd_dma1_size=32 snd_dma2=0 snd_dma2_size=32
```

Then, do the following:

```
$ sudo update-modules
$ sudo modprobe snd-opl3sa2
$ alsamixer
```

Good luck!

---

### Post by Pnut on 2006-01-09
i appreciate the help guyz but im still having no luck.  i think that im just fresh fish when it comes to linux.  i have a gateway solo 9100 laptop. the sound chipset in this model laptop is a yamaha 715/704.  It has two altec-lansing a2524 stereo speakers built into the palm-rest.  I'm currently running Ubuntu breezy badger updated.  Im new to linux and have only been running it for about 5 days.  I have successfully over come the wireless networking issues that linux has with linksys hardware,  yet im not able to over come this sound device issue.  all the help possible is very appreciated

Pnut
The ChickEnMcNo0bLet

---

### Post by FarEast on 2006-01-10
Hi Pnut,

Please try my suggestion again and paste the output of the
command below;) .

```
$ cat /proc/asound/card[COLOR="Red"]s[/COLOR]
```

---

### Post by Pnut on 2006-01-10
hey fareast heres were im at right now in this process.  i have created the folder sound.  and in it i have a file with all the information that u have listed above.  i placed it in the /etc/modprobe.d folder.  i have done the sudo update-modules with no problems.  then i did the sudo modprobe snd-opl3sa2 and i got fatal: error inserting snd_opl3sa2 (/lib/modules/2.6.12-10-386/kernel/sound/isa/snd-opl3sa2.ko):unknown sysbol in module, or unkown parameter (see dmesg).   Then i typed cat /proc/asound/cards and the os replied ---no soundcard---

root@pnut:/etc/modprobe.d#

Pnut

---

### Post by FarEast on 2006-01-10
Hi,

> i have created the folder sound. 
> and in it i have a file with all the information that u have listed above.
> i placed it in the /etc/modprobe.d folder.

My explanation might be wrong:???: 

/etc/modprobe.d/sound is *not* a folder but a file, which (usually) exists
already in /etc/modprobe.d .
What has to be described is:

```
options snd-opl3sa2 snd_index=1 snd_id=OPL3 snd_port=0x370 snd_sb_port=0x370 snd_wss_port=0x530 snd_midi_port=0x330 snd_fm_port=0x388 snd_irq=5 snd_dma1=1 snd_dma1_size=32 snd_dma2=0 snd_dma2_size=32
```

Regards

---

### Post by Pnut on 2006-01-10
it doesnt exist in my modprobe.d folder

---

### Post by Pnut on 2006-01-10
so i put it there..i will let ya know how it goes

---

### Post by FarEast on 2006-01-10
Hmm...:confused: 

OK:p 
Please paste the output from the commands below:

```
$ uname -r
$ ls /lib/modules/$(uname -r)/kernel/
$ cat /proc/interrupts
```

---

### Post by Pnut on 2006-01-10
ok.  my /etc/modprobe.d/sound wasnt there to begin with....but now it is containing the infomation that you placed here on the forums.  I created the file using gedit then named it sound and saved it to my desktop.  I then opened terminal and logged on as root.  I switched to /etc/modprobe.d# then typed cp -Rf /home/pnut/Desktop/sound ./  After asuring that the sound file was in its correct place, I then typed sudo update-modules with no error, then sudo modprobe snd-opl3sa2 with no errors and finished with alsamixer and i got alsamixer: function snd_ctl_open failed for default: No such file or directory.  Am i totally No0buLar or what? :P

Pnut
Silent N Seattle

---

### Post by FarEast on 2006-01-10
Thanks, Pnut, for the report:) .

Restart the system, load snd-opl3sa2 again and type in a command line:

```
$ cat /proc/asound/oss/sndstat
```
Paste the output, please.

---

### Post by Pnut on 2006-01-10
uname -r-----2.6.12-10-386
ls /lib/modules/2.6.12-10-386/kernel/----No such file or directory
cat /proc/interrupts
cpu0

0: 5096665          xt-pic    timer
1: 3260               xt-pic    i8042
2: 0                    xt-pic    cascade
7: 1                    xt-pic    parport0
8: 1                    xt-pic    rtc
9: 1                    xt-pic    MS Sound System
10: 135747          xt-pic     uhci_hcd:usbl, yenta, yenta, ndiswrapper
12: 576542          xt-pic    i8042
14: 23749            xt-pic    ide0
15: 44800            xt-pic    ide1
NMI: 0
LOC: 0
ERR: 0
MIS: 0

---

### Post by Pnut on 2006-01-10
[QUOTE=FarEast]Thanks, Pnut, for the report:) .

Restart the system, load snd-opl3sa2 again and type in a command line:

```
$ cat /proc/asound/oss/sndstat
```
Paste the output, please.[/QUOTE]
card config
---no soundcards---

audio devices: not enabled in config

synth devices: not enabled in config

midi devices:  not enabled in config

timers:
7: system timer

Mixers: not enabled in config

root@pnut~#

---

### Post by Pnut on 2006-01-10
[QUOTE=Pnut]card config
---no soundcards---

audio devices: not enabled in config

synth devices: not enabled in config

midi devices:  not enabled in config

timers:
7: system timer

Mixers: not enabled in config

root@pnut~#[/QUOTE]
before the card config just after the input command it states...

sound driver: 3.8.la-980706 (alsa v1.0.9 emulation code) Kernel: Linux Pnut 2.6.12-10-386 #1 Thu Dec 22 11:37:10 UTC 2005 i 686
config options : 0

---

### Post by FarEast on 2006-01-10
I read your report with surprise.

> ls /lib/modules/2.6.12-10-386/kernel/----No such file or directory

It is odd... If so, how can 'snd-opl[COLOR="red"]3[/COLOR]sa[COLOR="red"]2[/COLOR]' be loaded with no errors?
For 'snd-opl[COLOR="Red"]3[/COLOR]sa[COLOR="red"]2[/COLOR]' is placed in /lib/modules/2.6.12-10-386/kernel/sound/isa .

What does your system have under /lib/modules/2.6.12-10-386?
I wonder if it is set up properly...

---

### Post by Pnut on 2006-01-11
ok im confused now.  ive been following instructions using snd-opl3sa2.  but in your last post now i see snd-opl2sa3.  which is it?

---

### Post by FarEast on 2006-01-11
Hi,

> but in your last post now i see snd-opl2sa3. which is it?
Sorry#-o  It is 'snd-0pl3sa2'.

cf. To know names for your sound cards, visit the ALSA website.
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

---

### Post by Pnut on 2006-01-11
ok with the hardware that is currently in my laptop i definitly fall under the opl3sa2 catagory.  i cant belive its this tricky to get my sound working for this laptop using breezy badger.  technically i can live without the sound...but it would be nice to have...adding on to my ubuntu experience.  so i continue in my pursuit of a functional driver/module to make it work.

Pnut
The silence only makes me push harder for a fix :)

---

### Post by Pnut on 2006-01-11
oh yea using that site that u posted for alsa....i found that i have 1 pnp card being found.  dmesg says that this card Found opl3sa3 (ymf715e or ymf719e) then its saying theres an unkown parameter 'snd-id'

---

### Post by Pnut on 2006-01-11
ok in /lib/modules/2.6.12-10-386/kernel i have 9 blue directories.  they are listed as follows....arch, cluster, crypto, drivers, fs, lib, net, security, sound.

---

### Post by FarEast on 2006-01-12
Hi,

> ok in /lib/modules/2.6.12-10-386/kernel i have 9 blue directories.

OK!

> i found that i have 1 pnp card being found.
> dmesg says that this card Found opl3sa3 (ymf715e or ymf719e)
> then its saying theres an unkown parameter 'snd-id'

I think that an important clue exists in the third line of the quotation above.
It shows that the system was trying to load the module 'snd-oopl3sa2' but
the options described in /etc/modprobe.d/sound was unknown.

How about making another try;)? 
Alter the description in /etc/modprobe.d/sound as Martin says.

[http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html](http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html)

```
options snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530
```

Then, execute 'sudo update-modules' and restart the system.
What will happen?
----------
BTW Have you tried 'alsaconf' I sent to you?

---

### Post by Pnut on 2006-01-12
im alwayz up for another try.  i have a question tho.  that alsa.conf that u sent me...i dont know were to place it....does it go in the /etc/modprobe.d or does it go into /etc/alsa. ?

Pnut

---

### Post by FarEast on 2006-01-12
Hi,
'alsaconf' can be run wherever it is placed.
If it is in your home dir., then you have to type
```
$ cd
$ [COLOR="Red"]sudo[/COLOR] ./alsaconf
```
If you put it in /usr/local/bin , just type
```
$ [COLOR="Red"]sudo[/COLOR] alsaconf
```

Good luck;)

---

### Post by Pnut on 2006-01-13
ok i put alsaconf in usr/local/bin then i typed alsaconf and it would not execute it.  i extracted it to my desktop then i used terminal to copy it to /usr/local/bin.  did i do something wrong?

---

### Post by FarEast on 2006-01-13
Hi,

> did i do something wrong?

Not at all;) .
Sorry, my explanation was wrong;  I should write:
```
$ sudo alsaconf
```

---

### Post by Pnut on 2006-01-15
still no luck....

:(


Pnut

---

### Post by FarEast on 2006-01-16
Let's continue with working around, Pnut;) 

What we have to do is to specify options which the system
needs to probes 'snd-opl3sa2' correctly.

I have searched on the net for information once more and
come across several success stories.  I am going to evaluate
them.

BTW What kind of error messages come out when you try to
execute 'alsaconf'?

-----------------------

Examples of **/etc/modprobe.d/sound** in success stories:
(Note: they are originally described in [COLOR="Red"]one line[/COLOR].)

---------- 1 ----------
options snd-opl3sa2
index=1
id=OPL3
midi_port=0x330
port=0x370
sb_port=0x370
fm_port=0x388
wss_port=0x530
irq=5
dma1=1
dma1_size=32
dma2=0
dma2_size=32

---------- 2 ----------
options snd-opl3sa2 
sb_port=0x220
midi_port=0x330
fm_port=0x388
wss_port=0x530
irq=5
dma1=1
dma2=0
isapnp=0

---------- 3 ----------
options snd-opl3sa2
index=0
id=CARD_0
port=0x370
sb_port=0x220
wss_port=0x530
midi_port=-1
fm_port=-1
irq=5
dma1=0
dma2=1
isapnp=0

---------- 4 ----------
options snd-opl3sa2
port=0x370
sb_port=0x220
wss_port=0x530
midi_port=-1
fm_port=-1
irq=5
dma1=0
dma2=-1
isapnp=0

---------- 5 ----------
options snd-opl3sa2
index=1
id=CARD_0
port=0x370
midi_port=0x330
fm_port=0x388
sb_port=0x370
wss_port=0x530
irq=5
dma1=1
dma2=0

---------- 6 ----------
(line 1.)
options opl3sa2
io=0x370
mss_io=0x530
mpu_io=0x330
irq=5
dma=1
dma2=0

(line 2.)
options opl3
io=0x388 

--------- END ---------

---

### Post by Pnut on 2006-01-17
ok im gonna give all of these methods a try...im still having no luck yet...but i will keep ya posted on how it goes...after i try all of these sound types.


Pnut

---

### Post by Pnut on 2006-01-23
sory for the long time since the last reply.  since my last reply i have had problems with fat-fingering in root.  i had to re-install my breezy badger in order to over come the issues i had after rm -Rf a wrong directory.  im still having the problem with my sound.  i dont know what else to do.  ive jumped thru so many hoops trying to get this working but to no avail.  im kinda at the point were i dont mind the silence,  altho it would contribute greatly to my initial ubuntu linux experience.

Pnut

---

### Post by FarEast on 2006-01-23
Hi Pnut,
I have not been able to access the forum for 2 days, either
(due to system trouble or something).

I started the topic below.  How do you like the solution?
[http://ubuntuforums.org/showthread.php?t=119348](http://ubuntuforums.org/showthread.php?t=119348)

---

### Post by Pnut on 2006-02-09
FarEast Long time no hear from ya...i bet that your saying the same thing about me too lol.....anyways just wanted to pop in and let ya know that i finally got my audio working on the laptop.  I couldnt have done it without your help man...so i thank you sincerely.

Pnut 
the happiest ubuntu noob on the globe :)

---

### Post by FarEast on 2006-02-09
> i finally got my audio working on the laptop.

Congratulations!
Please share your experience with your fellows.

---

### Post by Pnut on 2006-02-15
i will thank you again for your help.  it was tedious but i got it done. :)

---

### Post by Canellas on 2006-02-25
Hi Pnut,

Would you please tell us how you managed to get the sound working correctly?

Thanks a lot,
   Canellas

---

### Post by Pnut on 2006-02-25
[QUOTE=Canellas]Hi Pnut,

Would you please tell us how you managed to get the sound working correctly?

Thanks a lot,
   Canellas[/QUOTE]
I have been running ubuntu breezy for about 2 months now. I have been experiencing a major sound issue on my laptop since i have installed breezy on it. I have been working with people kind enough to have the patience to deal with nooby issues and I really like the community atmosphere. FarEast, has provided me with most of the resources I needed to resolve this issue. FarEast also asked that I share my resolution with the forums.

My laptop is a Gateway Solo 9100. it has a yamaha sound card as its onboard multimedia controller for audio. It is the YM715 model.

This is what made it work:

1) I had to create a config file for the sound device. I named the file "sound". The line that worked is posted here---options snd-opl3sa2 index=0 id=CARD_0 port=0x370 sb_port=0x220 wss_port=0x530 midi_port=-1 fm_port=-1 irq=5 dma1=0 dma2=1 isapnp=0---(this line was written as one line) I used Gedit to create this file.

2) I then saved the file to my desktop and opened terminal. As root user i copied the file from my desktop to its proper destination, which is /etc/modprobe.d - using the commands as following.

root@pnut~$cd /etc/modprobe.d (enter)
cp -Rf /home/pnut/Desktop/sound ./ (enter)
sudo update-modules (enter)
sudo modprobe snd-opl3sa2 (enter)
alsamixer (enter)

Once alsa mixer was open i could control my sound hardware listen to music ect.

Thanks to all the people that helped me, and i hope that this helps someone else

---

### Post by Canellas on 2006-02-25
Thanks Pnut and FarEast!

Unfourtunately, I still did not get my sound board to work on my Toshiba 4025CDT

I tried these 6 configurations of '/etc/modprobe.d/sound':

"
options snd-opl3sa2 index=0 id=CARD_0 port=0x370 sb_port=0x220 wss_port=0x530 midi_port=-1 fm_port=-1 irq=5 dma1=0 dma2=1 isapnp=0
"

"
options snd-opl3sa2 index=1 id=OPL3 midi_port=0x330 port=0x370 sb_port=0x370 fm_port=0x388 wss_port=0x530 irq=5 dma1=1 dma1_size=32 dma2=0 dma2_size=32
"

"
options snd-opl3sa2 sb_port=0x220 midi_port=0x330 fm_port=0x388 wss_port=0x530 irq=5 dma1=1 dma2=0 isapnp=0
"

"
options snd-opl3sa2 index=0 id=CARD_0 port=0x370 sb_port=0x220 wss_port=0x530 midi_port=-1 fm_port=-1 irq=5 dma1=0 dma2=1 isapnp=0
"

"
options snd-opl3sa2 port=0x370 sb_port=0x220 wss_port=0x530 midi_port=-1 fm_port=-1 irq=5 dma1=0 dma2=-1 isapnp=0
"

"
options snd-opl3sa2 index=1  id=CARD_0 port=0x370 midi_port=0x330 fm_port=0x388 sb_port=0x370 wss_port=0x530 irq=5 dma1=1 dma2=0
"

"
options opl3sa2 io=0x370 mss_io=0x530 mpu_io=0x330 irq=5 dma=1 dma2=0
options opl3 io=0x388
"

An in all of then, when I tried to 'sudo modprobe snd-opl3sa2', I got:

"
FATAL: Error inserting snd_opl3sa2 (/lib/modules/2.6.12-10-386/kernel/sound/isa/snd-opl3sa2.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_opl3sa2
"

At the end of 'dmesg' appears:
"
snd_opl3sa2: Unknown parameter `dma1_size'
"

Where does this 'dma1_size' parameter comes from?

[]s

---

### Post by Pnut on 2006-03-01
ok type 

lspnp and then post your output here

pnut

also, are you using the sudo update-modules command before trying to modprobe it?

---

### Post by FarEast on 2006-03-03
Hi Pnut;) ,
I am glad that you are helping your fellow.
Thanks for the infomation of the command 'lspnp' which I have not known.

BTW:
Now I am busy to prepare for the removal at the end of this month.  I have already laid off the ISP.  When I have time again in April, I will come to the forums as often as I did;) .

---

### Post by Pnut on 2006-03-04
Hi FarEast,  
I'm glad to be able to provide help to someone, just like someone was able to provide help for me.  Hopefully he gets the sound device working.  I will still be around here and there using U-linux.  At the moment I am building a custome case for my new system.  I will send ya some pics of it when its done :) 

Hope to see you back in April :)


Pnut

---

### Post by fparri on 2006-07-04
Any of you guys succeeded in using Ubuntu Dapper and having an OPL3SA2 chip working?

---

