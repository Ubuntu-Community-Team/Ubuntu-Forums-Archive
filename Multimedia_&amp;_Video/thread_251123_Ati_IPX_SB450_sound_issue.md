---
title: "Ati IPX SB450 sound issue"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by zyris on 2006-09-05
I have recently purchased a Foxconn RC4107MA-RS2 motherboard.
as at the current moment i can not get the sound to work.

as far as i can see the sound card has been detected as it shows up in the device manager. Using lspci -v the sound card shows up

0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
        Subsystem: Foxconn International, Inc.: Unknown device 0c81
        Flags: 66MHz, slow devsel, IRQ 209
        Memory at fdff8000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-


following the sticky post on sound cards i loaded up the snd-atiixp module.
but alsamixer is still telling me that theres no sound card.

i also tried loading module that was recomended for the SB450 chipset. and that failed as well.
i also stuck in a knoppix 5.0 live cd to see if it was just an ubuntu related issue. but no sound from there either :(

i do have windows installed (dual boot) so i know that the sound card does work.

---

### Post by HoneyGutClusters on 2006-09-25
I have ATI IXP SB400 sound as well, getting this to work was simple, even though I fought for hours to get it up. Here's what you need to do:

Open a console, then run "alsamixer" (without the quotes). Use the right arrow to highlight IEC958, then hit the "m" key to mute it. tap escape twice to exit, then try your sound again.

---

### Post by jubilee33 on 2006-09-25
I also have an ATI IXP SB400 card and I kept IEC958 muted the whole time (in fact this was the default in my system).  I still have no sound.

Zyris, you should check the output of "lsmod | grep snd" and "dmesg | grep snd".  See whether the module is loaded in lsmod.

---

### Post by pharmd24 on 2006-09-25
I'm having the same issue with a DFI Infinity RS482

When I try alsamixer I get:

alsamixer: function snd_ctl_open failed for default: No such device



pharmd24@rs482u:~$ lsmod | grep snd
snd_atiixp             20364  0
snd_ac97_codec         92832  1 snd_atiixp
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            61728  0
snd_mixer_oss          19456  1 snd_pcm_oss
snd_pcm                99080  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              26500  1 snd_pcm
snd                    62956  6 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         11272  2 snd_atiixp,snd_pcm
pharmd24@rs482u:~$ dmesg | grep snd

dmesg | grep snd returns nothing.

I have loaded the snd-atiixp module as you can see

TIA for any help here.

---

### Post by pharmd24 on 2006-11-02
> **zyris said:**
> I have recently purchased a Foxconn RC4107MA-RS2 motherboard.
as at the current moment i can not get the sound to work.

as far as i can see the sound card has been detected as it shows up in the device manager. Using lspci -v the sound card shows up

0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
        Subsystem: Foxconn International, Inc.: Unknown device 0c81
        Flags: 66MHz, slow devsel, IRQ 209
        Memory at fdff8000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-


following the sticky post on sound cards i loaded up the snd-atiixp module.
but alsamixer is still telling me that theres no sound card.

i also tried loading module that was recomended for the SB450 chipset. and that failed as well.
i also stuck in a knoppix 5.0 live cd to see if it was just an ubuntu related issue. but no sound from there either :(

i do have windows installed (dual boot) so i know that the sound card does work.
I just noticed what you were saying!

The motherboards we have have got a sb450 southbridge that should use a the hda-intel module but ubuntu and other linux distros are detecting it as a sb400 that would use atiixp module!!!!

Help anyone!  Please...

---

### Post by dr777099 on 2006-12-06
No sound on the DFI RS482 Infinity mobo. (!)

I doubt I would ever have noticed Ubuntu's mis-identification of the sb450... good catch guys!

Anybody working on a solution?  

How can we raise the awareness level of this issue?

---

### Post by TL1000S on 2006-12-11
I also have tried "some hours" with my DFI RS482 board (X2 3800+). ](*,) 

Followed the "Comprehensive Sound problem guide". Tried rebuilding drivers - both atiixp and hda-intel..
No success.. :( 

Really frustrating as it was easy to set up Ubuntu on my Asrock 775Twins-HDTV (intel i945G. Running SMP kernel with E6300).

---

### Post by voisine on 2007-03-04
I have the same issue with 6.10 on a DFI Infinity RS482. It's been 6 months. Has any progress been made with this yet? Fixes, workarounds, patches?

To clarify, the RS482 has onboard Realtek ACL850 sound chip controlled by an SB450 southbridge. If you run lspci -v, it does not show up, however the nonexistant IXP SB400 AC'97 Audio Controller does.

---

### Post by eode on 2007-03-09
I'm having the same issue, I think..  ..any way to prevent the atiixp module from loading?


-b

---

### Post by petergun on 2007-03-11
Solution I found :

See bug report : [http://bugzilla.kernel.org/show_bug.cgi?id=7467](http://bugzilla.kernel.org/show_bug.cgi?id=7467)

Grab last patch : [http://bugzilla.kernel.org/attachment.cgi?id=9515&action=view](http://bugzilla.kernel.org/attachment.cgi?id=9515&action=view)

Apply patch, rebuild kernel, reboot.

Dmesg cut-n-paste:

   41.129764] Atiixp quirk for DFI RS482.  Forcing codec 0

Success for analog sound, will test digital at a later time.

---

### Post by numb3r5ev3n on 2007-04-18
> **petergun said:**
> Solution I found :

See bug report : [http://bugzilla.kernel.org/show_bug.cgi?id=7467](http://bugzilla.kernel.org/show_bug.cgi?id=7467)

Grab last patch : [http://bugzilla.kernel.org/attachment.cgi?id=9515&action=view](http://bugzilla.kernel.org/attachment.cgi?id=9515&action=view)

Apply patch, rebuild kernel, reboot.

Dmesg cut-n-paste:

   41.129764] Atiixp quirk for DFI RS482.  Forcing codec 0

Success for analog sound, will test digital at a later time.

I'm pretty much a n00b...I only made the switch from Windows a few months ago. I'm not sure how to do this. I was just going to throw in a PCI sound card until I found this thread. I'd like to get the onboard sound working if I can, but I don't have much experience with editing kernels. If anyone could give me any pointers, I'd be much obliged!

---

### Post by szinestv on 2007-04-21
I have Toshiba Satelite L30-134 laptop with SB450.

There is no sound.  That's the same problem. If the kernel patch can resolve this problem I would be very happy. But how can I patch the kernel? :confused: 

You can see the technical info here:
[http://pastebin.ca/451400](http://pastebin.ca/451400)

Please somebody help. Thank you in advance.

My email: [email]szinestv@gmail.com[/email]

---

### Post by lonewolf_timberwolf on 2007-04-26
I'd have to say I'm a complete noob as well. When you say 'apply the patch' I'm going back to my winblows days and expect an executable patch. And the thought of rebuilding the kernel scares the living beejeebees out of me!

---

### Post by abstractism on 2007-09-06
hey, I have this problem as well. would anyone care to provide some more detailed ways to fix this problem? I'm not sure how to apply a patch such as this, and my fortune is not shining brightly due to the fact that I've had this RS482 mobo for like 6 months or so already, just sitting in the box. 
someone help, please :(

---

### Post by eode on 2007-09-06
What works for me:

Go to [http://www.alsa-project.org](http://www.alsa-project.org) .  Get the current version of:

alsa-driver
alsa-lib
alsa-utils

(1.0.14, at time of this writing).

Uncompress each into their own directory.

In each directory, do:

```
./configure
make
sudo make install
```

..if it fails on the "./configure" step, then you may need to install some other packages to get it to work.  It should say what library is missing, or what blah blah is missing.  Find it in the package manager, and install it.

The above alsa packages may also need to be done in a certain order -- try driver, then lib, then utils, I think that works.

..also -- since this is not preinstalled in the ubuntu kernel, you will need to do the ./configure; make; sudo make install; again whenever there's a kernel update (you should be running the kernel you want it to compile for)

Once each of the three have compiled and installed without complaint, you should be able to either reboot, or do a 'sudo /etc/init.d/alsa<something> restart' (where '<something>' is 'sound' and "-utils".

---

### Post by numb3r5ev3n on 2007-09-06
> **eode said:**
> What works for me:

Go to [http://www.alsa-project.org](http://www.alsa-project.org) .  Get the current version of:

alsa-driver
alsa-lib
alsa-utils

(1.0.14, at time of this writing).



Thanks! I'll try this. I'll let everyone know if I'm successful...I was just going to hold out for Harmonius Heron, since I was told the driver issue would be fixed in that release. :)

---

### Post by apparle on 2007-09-13
Hello does anyody know how to apply the patch

---

### Post by aquavitae on 2007-09-13
Here's aguide for compiling the kernel: [http://ubuntuforums.org/showthread.php?t=56835]("http://ubuntuforums.org/showthread.php?t=56835") and here's instructions for applying patches: [http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")

---

### Post by apparle on 2007-09-13
Stay online I will check the guide

---

### Post by apparle on 2007-09-13
i donot have internet at my home I am using it in college.
please tell me how to do it without net

---

### Post by apparle on 2007-09-13
The guide seems too confusing can u tell me a step wise procedure
For eg;
i have ATI graphics card which needs proprietary driver but i have not installed it what ot do.
tell me what all should I download to compile kernel without net

---

### Post by numb3r5ev3n on 2007-09-13
> **eode said:**
> What works for me:

Go to [http://www.alsa-project.org](http://www.alsa-project.org) .  Get the current version of:

alsa-driver
alsa-lib
alsa-utils

(1.0.14, at time of this writing).

Uncompress each into their own directory.

In each directory, do:

```
./configure
make
sudo make install
```

..if it fails on the "./configure" step, then you may need to install some other packages to get it to work.  It should say what library is missing, or what blah blah is missing.  Find it in the package manager, and install it.

...Actually, the error I get is, "bash: ./configure: No such file or directory" when I type ./configure.

---

### Post by apparle on 2007-09-13
I have installed the latest alsa
which directory are you in ?

---

### Post by aquavitae on 2007-09-13
> **apparle said:**
> The guide seems too confusing can u tell me a step wise procedure
For eg;
i have ATI graphics card which needs proprietary driver but i have not installed it what ot do.
tell me what all should I download to compile kernel without netIf you have ati then there is not need to compile the kernel - I thought you had realtek...  Here's a howto on ati - its really easy, just follow the instructions: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by numb3r5ev3n on 2007-09-13
> **apparle said:**
> I have installed the latest alsa
which directory are you in ?

I made a directory for each file and extracted them there. Is there anything else I should do?

---

### Post by numb3r5ev3n on 2007-09-13
> **numb3r5ev3n said:**
> I made a directory for each file and extracted them there. Is there anything else I should do?

I made the directories in my hope directory...should I have put them somewhere else?

---

### Post by apparle on 2007-09-16
I want to install drivers for the sound card not the display drivers.
Are the sound card drivers also there in restricted drivers.
Another thing , my sound card is Realtek RTL8100C with ATI IXP SB450 south bridge controller

---

### Post by numb3r5ev3n on 2007-09-18
> **numb3r5ev3n said:**
> I made the directories in my hope directory...should I have put them somewhere else?

Whoops, that was "home directory." And it's working now that I installed a bunch of updates...I'll let everyone know if this works.

---

### Post by numb3r5ev3n on 2007-09-18
> **numb3r5ev3n said:**
> Whoops, that was "home directory." And it's working now that I installed a bunch of updates...I'll let everyone know if this works.

Ok, no...should these be in another directory?

---

