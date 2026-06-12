---
title: "some help please, tired after 5 hrs of looking"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by jcia2006 on 2008-03-30
04:04.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs X-Fi XtremeMusic
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at cce0 [size=32]
        Memory at d9e00000 (64-bit, non-prefetchable) [size=2M]
        Memory at d4000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>


i cant fix this.. want to listen to music etc LOL :-x

im new to ubuntu and already erased XP LOL .. been reading alot lately but cant seem to make the sound card work :(

please help me with this

thanks in advance , much appreciated!

ps. first post ftw, hi community!~

---

### Post by pseudo-random on 2008-03-30
Acces denied...
This says to me the permissions on your soundcard are wrong. You should have access to your own soundcard!
Have a look in the /dev directory for something like snd.
Try owning it with the command:
```
chown (yourname) snd
```
If you get an error then do it again but prefix it with sudo.

---

### Post by jcia2006 on 2008-03-30
erm..

im a total noob with coding and ubuntu... 

i opened the code and it says this

jcia@gsus:~$ chown jcia@gsus snd
chown: `jcia@gsus': invalid user
jcia@gsus:~$ chown jcia snd
chown: cannot access `snd': No such file or directory


now what sorry? :-O

---

### Post by xc3RnbFO8P on 2008-03-30
Here is a thread, see if pseudo-random can help you with it:
[http://ubuntuforums.org/showthread.php?t=731589]("http://ubuntuforums.org/showthread.php?t=731589")

---

### Post by pseudo-random on 2008-03-30
Sorry I pitched that a bit fast.
You need to open your terminal and do as follows:```
cd /dev
```Enter
```
ls
```
Enter. Look for snd
```
chown jcia snd
```
Where yourname seems to be jcia (not @gsus)

---

### Post by jcia2006 on 2008-03-30
got this..

jcia@gsus:~$ 
jcia@gsus:~$ cd /dev
jcia@gsus:/dev$ ls
1-3        ptyc9  ptyr8  ptyw7   sda2      ttya1  ttyp0  ttytb  ttyya
1-3.1      ptyca  ptyr9  ptyw8   sda5      ttya2  ttyp1  ttytc  ttyyb
1-3.2      ptycb  ptyra  ptyw9   sg0       ttya3  ttyp2  ttytd  ttyyc
1-3.4      ptycc  ptyrb  ptywa   sg1       ttya4  ttyp3  ttyte  ttyyd
1-4        ptycd  ptyrc  ptywb   sg2       ttya5  ttyp4  ttytf  ttyye
bus        ptyce  ptyrd  ptywc   shm       ttya6  ttyp5  ttyu0  ttyyf
cdrom      ptycf  ptyre  ptywd   snapshot  ttya7  ttyp6  ttyu1  ttyz0
cdrom1     ptyd0  ptyrf  ptywe   sndstat   ttya8  ttyp7  ttyu2  ttyz1
cdrw       ptyd1  ptys0  ptywf   sr0       ttya9  ttyp8  ttyu3  ttyz2
cdrw1      ptyd2  ptys1  ptyx0   sr1       ttyaa  ttyp9  ttyu4  ttyz3
console    ptyd3  ptys2  ptyx1   stderr    ttyab  ttypa  ttyu5  ttyz4
core       ptyd4  ptys3  ptyx2   stdin     ttyac  ttypb  ttyu6  ttyz5
disk       ptyd5  ptys4  ptyx3   stdout    ttyad  ttypc  ttyu7  ttyz6
dvd        ptyd6  ptys5  ptyx4   tty       ttyae  ttypd  ttyu8  ttyz7
dvd1       ptyd7  ptys6  ptyx5   tty0      ttyaf  ttype  ttyu9  ttyz8
dvdrw      ptyd8  ptys7  ptyx6   tty1      ttyb0  ttypf  ttyua  ttyz9
fd         ptyd9  ptys8  ptyx7   tty10     ttyb1  ttyq0  ttyub  ttyza
full       ptyda  ptys9  ptyx8   tty11     ttyb2  ttyq1  ttyuc  ttyzb
fuse       ptydb  ptysa  ptyx9   tty12     ttyb3  ttyq2  ttyud  ttyzc
hpet       ptydc  ptysb  ptyxa   tty13     ttyb4  ttyq3  ttyue  ttyzd
initctl    ptydd  ptysc  ptyxb   tty14     ttyb5  ttyq4  ttyuf  ttyze
input      ptyde  ptysd  ptyxc   tty15     ttyb6  ttyq5  ttyv0  ttyzf
kmem       ptydf  ptyse  ptyxd   tty16     ttyb7  ttyq6  ttyv1  urandom
kmsg       ptye0  ptysf  ptyxe   tty17     ttyb8  ttyq7  ttyv2  usb
log        ptye1  ptyt0  ptyxf   tty18     ttyb9  ttyq8  ttyv3  usb1
loop0      ptye2  ptyt1  ptyy0   tty19     ttyba  ttyq9  ttyv4  usb2
MAKEDEV    ptye3  ptyt2  ptyy1   tty2      ttybb  ttyqa  ttyv5  usbdev1.1_ep00
mem        ptye4  ptyt3  ptyy2   tty20     ttybc  ttyqb  ttyv6  usbdev1.1_ep81
net        ptye5  ptyt4  ptyy3   tty21     ttybd  ttyqc  ttyv7  usbdev1.2_ep00
null       ptye6  ptyt5  ptyy4   tty22     ttybe  ttyqd  ttyv8  usbdev1.2_ep81
nvidia0    ptye7  ptyt6  ptyy5   tty23     ttybf  ttyqe  ttyv9  usbdev1.3_ep00
nvidiactl  ptye8  ptyt7  ptyy6   tty24     ttyc0  ttyqf  ttyva  usbdev1.3_ep81
oldmem     ptye9  ptyt8  ptyy7   tty25     ttyc1  ttyr0  ttyvb  usbdev1.3_ep82
port       ptyea  ptyt9  ptyy8   tty26     ttyc2  ttyr1  ttyvc  usbdev1.4_ep00
ppp        ptyeb  ptyta  ptyy9   tty27     ttyc3  ttyr2  ttyvd  usbdev1.4_ep81
psaux      ptyec  ptytb  ptyya   tty28     ttyc4  ttyr3  ttyve  usbdev1.4_ep82
ptmx       ptyed  ptytc  ptyyb   tty29     ttyc5  ttyr4  ttyvf  usbdev1.5_ep00
pts        ptyee  ptytd  ptyyc   tty3      ttyc6  ttyr5  ttyw0  usbdev1.5_ep02
ptya0      ptyef  ptyte  ptyyd   tty30     ttyc7  ttyr6  ttyw1  usbdev1.5_ep81
ptya1      ptyp0  ptytf  ptyye   tty31     ttyc8  ttyr7  ttyw2  usbdev1.6_ep00
ptya2      ptyp1  ptyu0  ptyyf   tty32     ttyc9  ttyr8  ttyw3  usbdev1.6_ep01
ptya3      ptyp2  ptyu1  ptyz0   tty33     ttyca  ttyr9  ttyw4  usbdev1.6_ep03
ptya4      ptyp3  ptyu2  ptyz1   tty34     ttycb  ttyra  ttyw5  usbdev1.6_ep07
ptya5      ptyp4  ptyu3  ptyz2   tty35     ttycc  ttyrb  ttyw6  usbdev1.6_ep81
ptya6      ptyp5  ptyu4  ptyz3   tty36     ttycd  ttyrc  ttyw7  usbdev1.6_ep82
ptya7      ptyp6  ptyu5  ptyz4   tty37     ttyce  ttyrd  ttyw8  usbdev1.6_ep83
ptya8      ptyp7  ptyu6  ptyz5   tty38     ttycf  ttyre  ttyw9  usbdev1.6_ep84
ptya9      ptyp8  ptyu7  ptyz6   tty39     ttyd0  ttyrf  ttywa  usbdev1.6_ep87
ptyaa      ptyp9  ptyu8  ptyz7   tty4      ttyd1  ttys0  ttywb  usbdev1.6_ep88
ptyab      ptypa  ptyu9  ptyz8   tty40     ttyd2  ttyS0  ttywc  usbdev2.1_ep00
ptyac      ptypb  ptyua  ptyz9   tty41     ttyd3  ttys1  ttywd  usbdev2.1_ep81
ptyad      ptypc  ptyub  ptyza   tty42     ttyd4  ttyS1  ttywe  vcs
ptyae      ptypd  ptyuc  ptyzb   tty43     ttyd5  ttys2  ttywf  vcs1
ptyaf      ptype  ptyud  ptyzc   tty44     ttyd6  ttyS2  ttyx0  vcs2
ptyb0      ptypf  ptyue  ptyzd   tty45     ttyd7  ttys3  ttyx1  vcs3
ptyb1      ptyq0  ptyuf  ptyze   tty46     ttyd8  ttyS3  ttyx2  vcs4
ptyb2      ptyq1  ptyv0  ptyzf   tty47     ttyd9  ttys4  ttyx3  vcs5
ptyb3      ptyq2  ptyv1  ram0    tty48     ttyda  ttys5  ttyx4  vcs6
ptyb4      ptyq3  ptyv2  ram1    tty49     ttydb  ttys6  ttyx5  vcs7
ptyb5      ptyq4  ptyv3  ram10   tty5      ttydc  ttys7  ttyx6  vcs8
ptyb6      ptyq5  ptyv4  ram11   tty50     ttydd  ttys8  ttyx7  vcsa
ptyb7      ptyq6  ptyv5  ram12   tty51     ttyde  ttys9  ttyx8  vcsa1
ptyb8      ptyq7  ptyv6  ram13   tty52     ttydf  ttysa  ttyx9  vcsa2
ptyb9      ptyq8  ptyv7  ram14   tty53     ttye0  ttysb  ttyxa  vcsa3
ptyba      ptyq9  ptyv8  ram15   tty54     ttye1  ttysc  ttyxb  vcsa4
ptybb      ptyqa  ptyv9  ram2    tty55     ttye2  ttysd  ttyxc  vcsa5
ptybc      ptyqb  ptyva  ram3    tty56     ttye3  ttyse  ttyxd  vcsa6
ptybd      ptyqc  ptyvb  ram4    tty57     ttye4  ttysf  ttyxe  vcsa7
ptybe      ptyqd  ptyvc  ram5    tty58     ttye5  ttyt0  ttyxf  vcsa8
ptybf      ptyqe  ptyvd  ram6    tty59     ttye6  ttyt1  ttyy0  xconsole
ptyc0      ptyqf  ptyve  ram7    tty6      ttye7  ttyt2  ttyy1  zero
ptyc1      ptyr0  ptyvf  ram8    tty60     ttye8  ttyt3  ttyy2
ptyc2      ptyr1  ptyw0  ram9    tty61     ttye9  ttyt4  ttyy3
ptyc3      ptyr2  ptyw1  random  tty62     ttyea  ttyt5  ttyy4
ptyc4      ptyr3  ptyw2  rtc     tty63     ttyeb  ttyt6  ttyy5
ptyc5      ptyr4  ptyw3  scd0    tty7      ttyec  ttyt7  ttyy6
ptyc6      ptyr5  ptyw4  scd1    tty8      ttyed  ttyt8  ttyy7
ptyc7      ptyr6  ptyw5  sda     tty9      ttyee  ttyt9  ttyy8
ptyc8      ptyr7  ptyw6  sda1    ttya0     ttyef  ttyta  ttyy9
jcia@gsus:/dev$ chown jcia snd
chown: cannot access `snd': No such file or directory


which snd? :-X

---

### Post by pseudo-random on 2008-03-30
[http://ubuntuforums.org/showthread.php?t=239981](http://ubuntuforums.org/showthread.php?t=239981)
You'll find the driver in that thread as well as advice on how to install it.

---

### Post by warp99 on 2008-03-30
This is the module for your card according to Creative Labs new open source driver program:

[http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx](http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx)

The module is snd-ca0106 as is an ALSA driver:

[http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106](http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106)

The module is compiled into the kernel so it should be loaded. Please do the following:

```
lsmod |grep snd
```

and post the output to this thread.

Edit:

I found your answer in this thread at alsa-user: \\:D/

[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html)

Read the entire thread since there are some errors in the first post.

---

