---
title: "rosegarden 1.4.0"
date: 2006-09-20
forum: Multimedia &amp; Video
---

### Post by damu on 2006-09-20
[Rosegarden 1.4.0 now available!]("http://www.rosegardenmusic.com/")

This exciting release includes a number of significant new features, including true multitrack MIDI recording, ramped tempos, cut and paste of time ranges across all segments, better Lilypond output, better support for transposing instruments, and a database of acoustic instrument ranges, transpositions, and clefs.

---

### Post by dolson on 2006-09-20
Awesome, just in time to not be in Edgy.

---

### Post by raydar on 2006-11-10
No kidding--I was hoping it'd solve my "sequencer failed to initialize" startup error; dunno whether it'd do the trick, but I'd like to be able to  try it.

---

### Post by damu on 2006-11-11
The timing of developpement for applications is not always "Ubuntu centered"... ;) 

But [Rosegarden 1.4.0]("http://archive.ubuntulinux.org/ubuntu/pool/universe/r/rosegarden4/") is available and works on Ubuntu

Have fun!

---

### Post by dolson on 2006-11-11
> **damu said:**
> The timing of developpement for applications is not always "Ubuntu centered"... ;) 

But [Rosegarden 1.4.0]("http://archive.ubuntulinux.org/ubuntu/pool/universe/r/rosegarden4/") is available and works on Ubuntu

Have fun!

All I see in there is Rosegarden 0.9.8 and 1.0..?

---

### Post by CadetD on 2006-11-13
> **dolson said:**
> All I see in there is Rosegarden 0.9.8 and 1.0..?

Just download the 1.4 directly and compile. 
You'll be better off. And quite painless... I promise.

---

### Post by dolson on 2006-11-13
I don't actually want to use Rosegarden (I am a seq24 kinda guy). The point is that damu linked to a repo and said that 1.4.0 was there, but it's not, so I said as much.

---

### Post by asmok on 2006-11-16
Yes, it is easy to compile. But you can do it with alien too.

I have made (finnish) howto for that. Just grab a Mandrake rpm-package and turn it to the deb-package. Easy.

[http://forum.ubuntu-fi.org/index.php?topic=6510.0](http://forum.ubuntu-fi.org/index.php?topic=6510.0)

It just works.

Best Regards Asmo Koskinen.

---

### Post by rytmisk on 2006-11-16
Could you post the deb here? Would be fantastic!!

Ketil

---

### Post by asmok on 2006-11-16
> **rytmisk said:**
> Could you post the deb here?

You can try and download it form here:

[www.arkki.info/howto/rosegarden_1.4.0-2_i386.deb](www.arkki.info/howto/rosegarden_1.4.0-2_i386.deb)

Just remenber make those few symlinks:

sudo ln -s /usr/lib/liblrdf.so /usr/lib/liblrdf.so.2
sudo ln -s /usr/lib/libjack.so /usr/lib/libjack.so.0

And you must also lock that version on the Synaptic.

Synaptic | Package | Lock Version

Best Regards Asmo Koskinen.

---

### Post by asmok on 2006-11-16
My bad. Please notice this.

Rosegarden4 (1.4.0) depends on KDE-libs etc. I did try put that my own deb-package on other machine and run to this:

ltsp2@eduwks6-120:~/bin$ sudo dpkg -i rosegarden*
(Reading database ... 87918 files and directories currently installed.)
Unpacking rosegarden (from rosegarden_1.4.0-2_i386.deb) ...
dpkg: dependency problems prevent configuration of rosegarden:
 rosegarden depends on kdelibs4c2a (>= 4:3.5.3-1); however:
  Version of kdelibs4c2a on system is 4:3.5.2-0ubuntu18.1.

So please do it with alien - just download rpm-package and alien it and make some symlinks. Then it works whatever is your KDE-libs etc versions in your machine.

Best Regards Asmo Koskinen.

---

### Post by asmok on 2006-11-29
I have just install (clone) whole classroom with dual-boot pc's. XP and Ubuntu Dapper. We use Jack and Rosegarden 1.4 with M-Audio 49e midi-usb-keyboards. Installing (cloning) works great with g4u (netBSD-based live-disc).

Some pictures:

[http://www.arkki.info/howto/LTSP_Pikiruukki/Pikiruukki_20.png](http://www.arkki.info/howto/LTSP_Pikiruukki/Pikiruukki_20.png)
[http://www.arkki.info/howto/LTSP_Pikiruukki/Pikiruukki_21.png](http://www.arkki.info/howto/LTSP_Pikiruukki/Pikiruukki_21.png)

Best Regards Asmo Koskinen.

---

### Post by Unterseeboot_234 on 2006-12-01
Hello Asmo, your install makes me think I can get Rosegarden running on my machine. I have the AMD64. I have uninstalled / installed a few times. It is real important to:
> Applications / Add-Remove / Advance / (search) Rosegarden
select it, Menu-Package, lock the install.

ubuntu updates thinks 1.4.0 is older than rosegarden 2.0

I'm down to the links. Here is what I've got:
```
libjack-0.100.0.so.0.0.23
libjack-0.100.0.so.0 [link to shared library]

liblrdf.so.0 [link to shared library]
liblrdf.so.0.0.0

```

the links that are there are installed by deb. jack is a download from jack-audio.com

From the terminal: 
```
user@user-desktop:~$ rosegarden --nosequencer
rosegarden: error while loading shared libraries: libjack.so.0: cannot open shared object file: No such file or directory
```

---

### Post by asmok on 2006-12-02
I have these symlinks:

1.

koskias@ubuntu:/usr/lib$ ls -l libjack*
lrwxrwxrwx 1 root root    25 2006-11-30 18:54 libjack-0.100.0.so.0 -> libjack-0.100.0.so.0.0.23
-rw-r--r-- 1 root root 56676 2005-11-09 20:03 libjack-0.100.0.so.0.0.23
lrwxrwxrwx 1 root root    25 2006-11-30 19:52 libjack.so.0 -> libjack-0.100.0.so.0.0.23

2.

koskias@ubuntu:/usr/lib$ ls -l liblrdf*
lrwxrwxrwx 1 root root    16 2006-11-30 18:54 liblrdf.so.0 -> liblrdf.so.0.0.0
-rw-r--r-- 1 root root 25040 2004-12-21 11:12 liblrdf.so.0.0.0
lrwxrwxrwx 1 root root    16 2006-11-30 19:57 liblrdf.so.2 -> liblrdf.so.0.0.0

New ones are (as you can see from date):

libjack.so.0 -> libjack-0.100.0.so.0.0.23 and
liblrdf.so.2 -> liblrdf.so.0.0.0

Symlinks commands are like this kind of:

sudo ln -s libjack-0.100.0.so.0.0.23 libjack.so.0
sudo ln -s liblrdf.so.0.0.0 liblrdf.so.2

I hope this helps.

Asmo.

---

### Post by Unterseeboot_234 on 2006-12-03
No, it still does not work. I think because you have a input/output board in your Linux box that Jack configures. Of interest, Java JRE 1.5+ (the plug-in) does configure automatically. Wished rosegarden/jack would. I do not have a i/o board for sound. I am using the onboard Itel chip.

On the ALSA website is a link for my chip. The install patch for ./config is for Redhat or SuSe. [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Nvidia&card=.&chip=nForce&module=intel8x0]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Nvidia&card=.&chip=nForce&module=intel8x0")

I will have to study up on the ubuntu way to default the intel chip as a card. My machine gives...

```
modinfo soundcore
filename:       /lib/modules/2.6.15-27-amd64-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
...

is the amd-64 ubuntu module
```

ALSA instructions call for ...
```
modinfo soundcore
# description: "Intel 82801AA,82901AB,i810,i820,i830,i840,i845,MX440; SiS 7012; Ali 5455"
# author: "Jaroslav Kysela "
# license: "GPL"
# parm: index int array (min = 1, max = 8), description "Index value for Intel i8x0 soundcard."
# parm: id string array (min = 1, max = 8), description "ID string for Intel i8x0 soundcard."
# parm: enable int array (min = 1, max = 8), description "Enable Intel i8x0 soundcard."
# parm: ac97_clock int array (min = 1, max = 8), description "AC'97 codec clock (0 = auto-detect)."
# parm: joystick_port int array (min = 1, max = 8), description "Joystick port address for Intel i8x0 soundcard. (0 = disabled)"
# parm: mpu_port int array (min = 1, max = 8), description "MPU401 port # for Intel i8x0 driver." 

```
and, they show the RedHat way to make this change.

If you have any more suggestions -- great! Or, if the ubuntu forum is not the way to get this done, I will post to this thread if I ever get rosegarden/jack working.

---

### Post by damu on 2006-12-05
thanks Asmok for the info. I found different debs of rosegarden 1.4.0, but always had dependencies  problem to install them (either libc6 or another lib). I remembered it to be the default version in feisty when I tested it.
I followed your instructions and manage to install Rosegarden now, but it wouldn't start even after another attempt to create the needed link :
> damu@ubuntu:~$ rosegarden
rosegarden: error while loading shared libraries: liblrdf.so.2: cannot open shared object file: No such file or directory
damu@ubuntu:~$ 
damu@ubuntu:~$ sudo ln -s /usr/lib/liblrdf.so /usr/lib/liblrdf.so.2
Password:
ln: creating symbolic link `/usr/lib/liblrdf.so.2' to `/usr/lib/liblrdf.so': File exists
damu@ubuntu:~$ rosegarden
rosegarden: error while loading shared libraries: liblrdf.so.2: cannot open shared object file: No such file or directory


Any idea how to solve this problem?

---

