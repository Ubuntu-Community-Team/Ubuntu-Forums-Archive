---
title: "HowTo  HP DV2000 compile alsa to resolve all issues (mic, jack, AC-power,auto mute)"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by lexarrow on 2007-05-26
I am currently running Ubuntu Studio on a HP Pavilion dv2025nr.

After this install you should have all sound features enabled.

This is a compile of alsa drivers 1.0.15rc3

1.Check your kernel version - in terminal window type:

```
`uname -r'
```

mine is 2.6.10-16-generic

2.Install these packages:

```
sudo apt-get install linux-headers-$(uname -r) build-essential libncurses5-dev libncursesw5-dev ncurses-term alsa-tools-gui gettext po-debconf debhelper quilt alsa-base libc6-dev
```  

and uninstall these ones:
```
 sudo apt-get remove --purge alsa-base alsa-tools

```

be sure not to uninstall alsa-utils as it will uninstall your gdm  too

3.Back-up your current configuration:

```
tar -zcvf original-drivers.tgz /lib/modules/`uname -r`/kernel/sound
```

4.Make a directory for alsa packages:

```
mkdir /home/user/alsa
cd /home/user/alsa

```

5. Get alsa packages:
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc3.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.15rc1.tar.bz2

```


6.Unpack archives:

```
tar xvf alsa-driver-1.0.15rc3.tar.bz2
tar xvf alsa-lib-1.0.15rc3.tar.bz2
tar xvf alsa-utils-1.0.15rc1.tar.bz2
tar xvf alsa-firmware-1.0.15rc1.tar.bz2
```

7.Install driver:
Note: 'sudo make clean' and sudo make mrproper are to clean out your previous drivers. If you are doing a fresh install, you don't need them.

```

cd alsa-driver-1.0.15rc3/
sudo make clean
sudo make mrproper
./configure --with-oss=yes --with-cards=hda-intel 
sudo make
sudo make install
```

9.Install alsa-lib:

```
cd alsa-lib-1.0.15rc3
sudo make clean
./configure
sudo make
sudo make install
```

10.Install alsa-utils:

```
cd alsa-utils-1.0.15rc1
./configure
sudo make clean
sudo make 
sudo make install

```

11.Install alsa-firmware:

```
cd alsa-firmware-1.0.15rc1
./configure
sudo make clean
sudo make 
sudo make install

```

12.double-click Volume control (the speaker next to the clock), then Edit->Preferences and check all the boxes (you should have 8 boxes : Master, PCM, LineIn, IEC958, Digital, Ext Mic, Int Mic, Int Mic (yes 2 times Int Mic). Close Preferences.

13.Go to Switches tab and check LineIn

14.Go to Recording tab and be sure both mic and speakers are not muted. 

15. Go to Playback tab and be sure Master,PCM, and Ext Mic are not muted and BE SURE IntMic IS MUTED!

16. In a terminal, login as root and type:
```
 /etc/init.d/alsa-utils stop

```

17. Type the following command:
```
/usr/sbin/alsaconf
```
When it asks you, choose the 'hda-intel' card and then to save the changes to the files

18.Type:
```
 /etc/init.d/alsa-utils start

```

You should be done! If yo still don't have sound restart and it will be ok !

Note: 1. Every time you update the kernel, you have to recompile the driver
          2. There is still an issue unresolved, the 'no sound after a windows session ' and can be fixed by unplugging the power cord before booting Ubuntu. If it doesn't work, reboot again with no power cord. 

There's no solution for the 'no sound after Windows yet, but:

2.1 If you are in Windows unplug the AC cable and plug it back after you logged into Ubuntu.
2.2 If you are already on Linux after a Windows session and you didn't follow point 1.1estat, Unplug the AC cable, then SHUTDOWN , not restart the computer. Start it again manually and plug the cable back after you logged into Ubuntu 

This way you should have sound every time you follow one of these 2 steps

Special thanks to these 2 articles: [1]("http://www.pixelmonkey.org/2007/03/18/dv2000-alsa-patches/") and [2]("https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard?highlight=%28alsa%29/")

Hope it works for you too!

---

### Post by defyingthenorm on 2007-05-26
When installing the firmware, you listed the code as "cd alsa-lib-1.0.14rc4" instead of "cd alsa-firmware-1.0.14rc4".

Other than that, great guide!

Fixed my headphone problem like that!

---

### Post by lexarrow on 2007-05-26
Updated. Thanks!

---

### Post by brunomfs on 2007-05-26
Thanks very much, this guide worked great in my hp 2125us!

Just a note: when installing alsa-utils, the instalation can complain about "t-ja.gmo" or something like this as pointed out here:
[http://www.linuxquestions.org/questions/showthread.php?t=294058](http://www.linuxquestions.org/questions/showthread.php?t=294058)

Just run:

$sudo apt-get install gettext

And it should do ok!

Thanks again! :D

---

### Post by lexarrow on 2007-05-26
Thanks! Updated the point 2 of the install.

---

### Post by loupy on 2007-05-26
Thank you so much for this how-to.  It worked perfectly!

---

### Post by brandenw on 2007-05-26
OK,  I have an HP DV 2120us.... and everything worked (as far as no errors during that process)

However i still have no sound. when i use the volume monitor it doesnt even register that the sound is playing, if i use rhythmbox.. the file "plays" but no sound. ive tried muting, unmuting, adjusting the sound, headphones, no headphones. i still cant get it to work. I am new to this i can set up a webserver and do php and thats about it, so what do you need from me? or where do i go next?

---

### Post by lexarrow on 2007-05-27
I had also had this kind of problems. Try 2 thinngs:

1. In volume manager File-Change device-HDA Nvidia. Then go to Edit-Preferences and check master, pcm, ext mic, int mic and after that go back to volume control-switches and check only int-mic. Now restart and you should have sound. If this doesn't work please post a snapshot of your volume control-preferences.

2. Install alsamixergui
```
sudo apt-get install alsamixergui
```
Go to Applications-Sound and video-Alsamixergui
You should see from left to right on top of the application Card, Chip and Alsa. Click Alsa-Proc info.
List back here Card, Chip and Proc Info (maybe you have another kind of hardware)

---

### Post by brandenw on 2007-05-27
Thanks for the help! that didnt work, but here i believe is all the information you asked for.

/proc/asound/version:
====================
Advanced Linux Sound Architecture Driver Version 1.0.14rc4.
Compiled on May 26 2007 for kernel 2.6.20-15-generic (SMP).

/proc/asound/cards:
=================
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xc0000000 irq 22

/proc/asound/devices:
====================
  0: [ 0]   : control
  1:        : sequencer
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 33:        : timer

/proc/asound/oss-devices:
========================
No information available

/proc/asound/timers:
===================
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE

/proc/asound/pcm:
================
00-01: Conexant Digital : Conexant Digital : playback 1
00-00: CONEXANT Analog : CONEXANT Analog : playback 1 : capture 1

---

### Post by lexarrow on 2007-05-27
It looks exactly like mine. First off, don't change anything! I had that problem too. I have a few questions:

1.Do you also have windows installed?It happened to me to reboot after a windows session and not have sound. So I rebooted again without the AC cable in the laptop and it worked.
2.what options do you have enabled in Volume control-Switches? Please post a snapshot with Volume control-Switches

---

### Post by brandenw on 2007-05-27
Yes, i have windows, i have tried rebooting over and over, i always have the AC cable in...
ill get u a snapshot later when im back at home.

---

### Post by brandenw on 2007-05-27
here is the screenshot...

---

### Post by hiazle on 2007-05-27
> **lexarrow said:**
> So I rebooted again without the AC cable in the laptop and it worked.

Hi good people, I'd like to voice my gratitude for all those who are working hard to ensure that a solution to this HDA nVidia problem is found. THANK YOU VERY MUCH!! YOU ARE APPRECIATED. Unfortunately, I haven't been able to get my sound card working. However, I also noticed that after I reboot without the AC cable, the sound works. Anyone have an idea what this relates to? I also tried to add "**[COLOR="Red"]acpi=off[/COLOR]**" boot option but that did not solve my problem.

I am using the alsa driver that comes with Feisty, but I added the following line to **/etc/modprobe.d/alsa-base**
```
options snd-hda-intel index=0 model=3stack-dig
```

In case anyone is interested, here is my terminal output:
```
hiazle@hiazle-laptop-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


```
hiazle@hiazle-laptop-ubuntu:~$ lsmod | grep snd
snd_hda_intel          24224  4 
snd_hda_codec         262912  1 snd_hda_intel
snd_pcm_oss            49536  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  3 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    68904  16 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm

```

BTW: My laptop is a Pavilion dv2120ca
Any help will be appreciated.

---

### Post by brandenw on 2007-05-27
when i reboot with OUT the AC Cable it makes no difference... still no sound

 (separate issue.. although possibly related, my wireless doesnt work either, but my ethernet does... Possibly related?)

NEW UPDATE:

I put my laptop to hibernate earlier, and when i came back to turn it back on, it would not boot - it crashed. So i killed it, and brought it back up with a normal boot.. after  i did that my sound worked Without AC Cable.

---

### Post by hiazle on 2007-05-28
> **brandenw said:**
> when i reboot with OUT the AC Cable it makes no difference... still no sound


I noticed that if I have been in Windows, I have to reboot again WITHOUT THE CABLE (sometimes twice), and eventually my sound works. I believe that it has something to do with ACPI, since yours works after hibernate too.

---

### Post by brandenw on 2007-05-28
maybe someone here can help me find it...
earlier while i was searching on the forum i had found a different thread inwhich it mentioned adding parameters to the grub boot..
 NOAPCI NOIRQPOLL  

those were 2 of the 4 i dont even remember what the thread was exactly about other then it was a dv6000(i was researching it for my other laptop), but it was having problems as well.. possibly this could be an attribution to  a solution.

---

### Post by lexarrow on 2007-05-28
I found it [here]("http://ubuntuforums.org/showthread.php?t=448596&highlight=NOAPCI+NOIRQPOLL") and tried it but it doesn't work.

I propose all of you dv2000 users 2 things:

1. The AC problem is probably a bug (ubuntu or alsa bug)  so let's all look for the bug and a solution to fix it.
2. It seems that we have all sorts of problems in getting all the functionality from our laptops so I propose to unify our efforts into a thread, forum or whatever form you think it's best. This way we could post out our problems/solutions in a more efficient way. The final goal of this would be to create an Ubuntu  distribution just for dv2000 with full functionality.

What do you think?

---

### Post by lexarrow on 2007-05-28
Quick note: If you update to kernel 2.6.20-16 you have to recompile the drivers again

Also updated the first post.

---

### Post by lexarrow on 2007-05-28
I found a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108392") thanks to [this]("http://ubuntuforums.org/showthread.php?t=450694&highlight=sound+after+windows") post but a fix is yet to be found

---

### Post by hiazle on 2007-05-28
Thanx lexarrow, I guess we can just track this bug,  and hope for a solution to it.

---

### Post by hiazle on 2007-05-28
On lauchpad, they suggest reinstalling Feisty. Is there a way to just reinstall without necessarily re-formatting? Or something like re-detect hardware so that the kernel reconfigures itself?

---

### Post by lexarrow on 2007-05-28
> **hiazle said:**
> On lauchpad, they suggest reinstalling Feisty. Is there a way to just reinstall without necessarily re-formatting? Or something like re-detect hardware so that the kernel reconfigures itself?

I don't know if a reinstall would work. I made a fresh install of Ubuntu Studio 4 days ago and it doesn't change anything

---

### Post by lexarrow on 2007-05-28
I have submitted the 'no sound after windows' [bug]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3121") to alsa

---

### Post by hiazle on 2007-05-28
> **lexarrow said:**
> I have submitted the 'no sound after windows' [bug]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3121") to alsa

Thanx. let's hope that brings us some results.

---

### Post by Acglaphotis on 2007-05-28
OMG, Thankyou so much!!!!!(insert excesives exclamations symbols).

I've trying to fix this since day 1!.

-Acgla

EDIT: The no sound after windows can be fixed by unplugging the power cord before booting ubuntu.

---

### Post by brandenw on 2007-05-28
OK.. well i think i have a permanent fix... for absolutely no reason. but it worked for me.

1. Boot up Ubuntu WITHOUT power cable.
  a. upgrade kernel if you would like.
  b.  edit /etc/modprobe.d/alsa-base: options snd-hda-intel index=0 model=3stack-dig
2. play some sound or something (make sure it works)
3. Rather than restart send it into hibernate.
4. after hibernation is complete, bring it back up.
    it should crash.upon crashing,  alt+ctrl+del
    reboot into ubuntu.

5. everything should work, you can now reboot with or without the cable and your sound will work.
you can also reboot into windows and your sound will work.

This worked for me on a dv2120us

---

### Post by lexarrow on 2007-05-29
> **brandenw said:**
> OK.. well i think i have a permanent fix... for absolutely no reason. but it worked for me.

1. Boot up Ubuntu WITHOUT power cable.
  a. upgrade kernel if you would like.
  b.  edit /etc/modprobe.d/alsa-base: options snd-hda-intel index=0 model=3stack-dig
2. play some sound or something (make sure it works)
3. Rather than restart send it into hibernate.
4. after hibernation is complete, bring it back up.
    it should crash.upon crashing,  alt+ctrl+del
    reboot into ubuntu.

5. everything should work, you can now reboot with or without the cable and your sound will work.
you can also reboot into windows and your sound will work.

This worked for me on a dv2120us

It doesn't work for me because it doesn't go into hibernation. It tries to, but can't finish the process and shows me the login screen as it were put to sleep.

After this, I have another problem: When I plug in the AC power, the ac power light is still off and it doesn't show me the power status.

---

### Post by lexarrow on 2007-05-29
I found that you can't go into hibernation if you don't have a swap partition (which seems logical, but I didn't know that).

The battery status is solved after a restart.

Still, no sound after windows.

---

### Post by lexarrow on 2007-05-29
> **Acglaphotis said:**
> OMG, Thankyou so much!!!!!(insert excesives exclamations symbols).

I've trying to fix this since day 1!.

-Acgla

EDIT: The no sound after windows can be fixed by unplugging the power cord before booting ubuntu.

Thanks Acglaphotis, edited the first post with your comment.

---

### Post by Poweruser20 on 2007-05-29
Hi thank you very much for the solution to the sound problem.however i accidentally stumbled upon a simpler way for automute to work without patching the alsa drivers,or might have been prepatched,i dont know but here,s what i did.for connexant venice with nvidia chpset
i downloaded the SUSE alsa snapshot driver from 
 [ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver)
 i downloaded the package 
alsa-driver-hg20070526.tar.bz2     dated 05/26/2007
renamed it to alsa-driver.tar.bz2 for ease of installation.
then executed the following commands in the terminal
$tar xvf alsa-driver.tar.bz2
$./configure
$sudo make
$sudo make install

then rebooted the system,sound worked automute worked,sound was clear and loud,but i have not still tested the internal mic.Please make sure that the proper build libraries are installed,i am new to linux so i might not be able to help if u run into any trouble but i will try my best to help out.thank you

---

### Post by hiazle on 2007-05-29
> **brandenw said:**
> OK.. well i think i have a permanent fix... for absolutely no reason. but it worked for me.

1. Boot up Ubuntu WITHOUT power cable.
  a. upgrade kernel if you would like.
  b.  edit /etc/modprobe.d/alsa-base: options snd-hda-intel index=0 model=3stack-dig
2. play some sound or something (make sure it works)
3. Rather than restart send it into hibernate.
4. after hibernation is complete, bring it back up.
    it should crash.upon crashing,  alt+ctrl+del
    reboot into ubuntu.

5. everything should work, you can now reboot with or without the cable and your sound will work.
you can also reboot into windows and your sound will work.

This worked for me on a dv2120us

That did not work for me. I always  have to reboot a second time WITHOUT CABLE for the sound to work. It doesn't matter whether my first boot (after windows) was with cable or not.

---

### Post by hiazle on 2007-05-29
> **Poweruser20 said:**
> Hi thank you very much for the solution to the sound problem.however i accidentally stumbled upon a simpler way for automute to work without patching the alsa drivers,or might have been prepatched,i dont know but here,s what i did.for connexant venice with nvidia chpset
i downloaded the SUSE alsa snapshot driver from 
 [ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver)
 i downloaded the package 
alsa-driver-hg20070526.tar.bz2     dated 05/26/2007
renamed it to alsa-driver.tar.bz2 for ease of installation.
then executed the following commands in the terminal
$tar xvf alsa-driver.tar.bz2
$./configure
$sudo make
$sudo make install

then rebooted the system,sound worked automute worked,sound was clear and loud,but i have not still tested the internal mic.Please make sure that the proper build libraries are installed,i am new to linux so i might not be able to help if u run into any trouble but i will try my best to help out.thank you

Thank u Poweruser20, thanx again Lexarrow. This method worked for me! especially the AUTO MUTE! No need to switch to Windows now.

EDIT:
Actually, the Dual boot/Power cable issue is still not yet resolved. I still have to reboot without cable to get sound back. Headphone jack sense works and the sound quality is superb.

---

### Post by fjgaude on 2007-05-30
> **lexarrow said:**
> I have submitted the 'no sound after windows' [bug]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3121") to alsa

Thanks for putting in a bug report. I tell you, Feisty is sure feisty when it comes to sound. I've followed all the advise given in this thread and sound works but not reliably, and the volume is low, much lower than when in Vista.

Now I'll be afraid to upgrade to a new kernel. The WiFi works with 2.6.20.16 but it didn't with 2.6.20.15.

By reading all the forums it is amazing how things change when there is a "simple" upgrade in the kernel. Things that worked before don't and vice versa.

Regarding sound, Edgy was much better. Can't say about WiFi, as I just got this HP dv2000, for my road work. Home computers work fine with Edgy, but no sound on one of them with Feisty. Ah, well...

Thanks again, to all, and let's do get a special issue of Feisty for HP laptops. Let me know, lexarrow, when it is ready after you created the CD ISO. <smile>

frank

---

### Post by lexarrow on 2007-05-30
the only problem with the ISO is the sound. I got WiFi, webcam, lightscribe, beryl, auto mute, mic, ntfs r&w working...only this AC power, sound after windows bug still left standing.

---

### Post by hiazle on 2007-05-30
> **lexarrow said:**
> the only problem with the ISO is the sound. I got WiFi, webcam, lightscribe, beryl, auto mute, mic, ntfs r&w working...only this AC power, sound after windows bug still left standing.

Hey lexarrow, can you point me in the right direction for WiFi, and webcam. Is it just the wiki? I haven't bothered trying to get these to work as I'm waiting on this sound issue to get resolved. My internal mic works very well with Skype 1.4 (When the sound is working).

---

### Post by Poweruser20 on 2007-05-30
i used ndiswrapper v 1.42 to get broadcom wifi to work.the performance is very good compared to windows and i experienced no crashes so far.there are many guides on ubuntu forums on how to get this working.if you want i can post a link to the guide.

---

### Post by lexarrow on 2007-05-31
> **hiazle said:**
> Hey lexarrow, can you point me in the right direction for WiFi, and webcam. Is it just the wiki? I haven't bothered trying to get these to work as I'm waiting on this sound issue to get resolved. My internal mic works very well with Skype 1.4 (When the sound is working).

hiazle, try [this]("http://ubuntuforums.org/showthread.php?t=405990&highlight=dell+broadcom") thread for WiFi

---

### Post by Poweruser20 on 2007-06-01
> **hiazle said:**
> Thank u Poweruser20, thanx again Lexarrow. This method worked for me! especially the AUTO MUTE! No need to switch to Windows now.

EDIT:
Actually, the Dual boot/Power cable issue is still not yet resolved. I still have to reboot without cable to get sound back. Headphone jack sense works and the sound quality is superb.

If you have upgraded to the latest kernel,the automute problem reapperas,it can be fixed by downloading and installing the latest snapshot driver 05/31/2007.from the above source.using the same procedure above.I have tested it.sound works properly without any issues with respect to automute and clarity.thank you.

---

### Post by dadde on 2007-06-01
It has worked for me too on a hp dv2164eu and Ubuntu Edgy!:p
I found the patch here: [http://article.gmane.org/gmane.linux.alsa.devel/46265](http://article.gmane.org/gmane.linux.alsa.devel/46265)

Thanks!

---

### Post by lexarrow on 2007-06-01
> **dadde said:**
> It has worked for me too on a hp dv2164eu and Ubuntu Edgy!:p
I found the patch here: [http://article.gmane.org/gmane.linux.alsa.devel/46265](http://article.gmane.org/gmane.linux.alsa.devel/46265)

Thanks!

This patch doesn't solve the 'no sound after windows' bug, at least for me.everything else is working normally.

---

### Post by hiazle on 2007-06-01
> **lexarrow said:**
> hiazle, try [this]("http://ubuntuforums.org/showthread.php?t=405990&highlight=dell+broadcom") thread for WiFi

Thanx Lexarrow, I think I'm going to have to go with ndiswrapper. I am familiar with the ndiswrapper method (since dapper, and when I was using Mandriva)  but I'd have prefered using the bcm43xx driver since it appears more intergrated into the kernel. recently I tried fwcutter on my windows driver and it complained, so I set that aside. The threads seem to suggest ndiswrapper as a better choice since I use WPA -- so I'll just use that.

How about the built-in webcam? on my system it is detected as "USB 2.0 webcam", but I'm not sure if that means its usable. I tried opening it in VLC using /dev/video and /dev/video0 but that did not work..

EDIT:
My webcam works with Ekiga! :)  I had to use V4L2.

---

### Post by lexarrow on 2007-06-02
> **hiazle said:**
> Thanx Lexarrow, I think I'm going to have to go with ndiswrapper. I am familiar with the ndiswrapper method (since dapper, and when I was using Mandriva) but I'd have prefered using the bcm43xx driver since it appears more intergrated into the kernel. recently I tried fwcutter on my windows driver and it complained, so I set that aside. The threads seem to suggest ndiswrapper as a better choice since I use WPA -- so I'll just use that.

How about the built-in webcam? on my system it is detected as "USB 2.0 webcam", but I'm not sure if that means its usable. I tried opening it in VLC using /dev/video and /dev/video0 but that did not work..

EDIT:
My webcam works with Ekiga!  I had to use V4L2.


Hiazle, I use [these]("http://www.arakhne.org/spip.php?article50") dirvers. They seem to be specially made for Ricoh webcams and the best thing about it: it's a .deb file. Read [here]("http://lsb.blogdns.net/ry5u870/") more info on what programs work/don't work with these drivers and why.

Anyway, I don't feel the difference between these drivers and the berilos drivers, but they are much easier to install. I haven't used VLC but I've read there are a lot of applications out there that don't have the capability to support the new types othe webcams. Personally, I don't yet have video conferencing software that I can use behind my University's firewall: skype doesn't have video capabilities yet, open wengo is not advanced enough to support my webcam. aMSN I can use only from work.

About the WiFi drivers, it doesn't matter what you use as long as you get it working. 

Hope this helps!

---

### Post by drklepto on 2007-06-05
Same problem..
Tried reinstalling 6 times.. Sometimes it works, sometimes it doesn't..
(even on Kubuntu) And I can't understand how..

So reinstallation is absolutely not a good solution..

In this moment the sound is working, after a combination of randomly plug an aunplug, boot and reboot.. Can't reproduce the procedure.. I hope that it will last for a while..

I'll keep looking this thread to see if there are some good news..

(My Laptop: HP Pavilion dv2164eu)

---

### Post by hiazle on 2007-06-08
> **drklepto said:**
> Same problem..
In this moment the sound is working, after a combination of randomly plug an aunplug, boot and reboot.. 


I found out on my system that I have to unplug power before shutting down/rebooting windows. If ubuntu boots while the power is already unplugged, the sound works. I believe its related to the QuickPlay feature that most of these laptops have, because I noticed that the MUTE led changes status if the laptop boots on battery.

---

### Post by Chappy7777 on 2007-06-08
I just typed "Ubuntu Studio" into Synaptic and it seems to have installed. What I got was something called Ubuntu Studio Launcher. In it's window is a list that includes all of the audio programs listed under Sound and Video under Applications. To their left is a column called Run with boxes to click. Is this what it should look like?

Thnx, Chappy

---

### Post by ElEdwards on 2007-06-08
I was able to go through the steps and had success..... but I noticed that the 'patch' bin file is no longer available, so I did everything without being able to patch the file(s).

Thoughts? :)

---

### Post by prowdtobebrown on 2007-06-09
I just installed ubuntu yesterday and am a first time user so please bear with me with what may be dumb mistakes

I'm trying to follow the initial steps that were outlined but I can't unpack the archives the moment i enter "tar xvf alsa-alsa-driver-1.0.14rc4.tar.bz2" it returns with this error: 

Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

Can someone help? thank you

---

### Post by dancavs on 2007-06-09
> I'm trying to follow the initial steps that were outlined but I can't unpack the archives the moment i enter "tar xvf alsa-alsa-driver-1.0.14rc4.tar.bz2" it returns with this error:

Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


hi try this: 

```
tar xvf alsa-driver-1.0.14rc4.tar.bz2
```

also make sure you are in the directory where your files have been downloaded to.

i too am having trouble with sound (i have none), have tried this how to - unfortunately no success as yet. my laptop is an hp pavillion dv2000.

strangely though i now have 2 new shortcuts on my sound and video menu, HDSP conf and HDSP mixer. ?? neither of these launch anything either ... i am dual booting vista as well and also have my quickplay mute button doing strange things.

will keep plugging away ...

---

### Post by prowdtobebrown on 2007-06-09
i got past that error but i can't input the next line.

patch -p1 < /"path_to_patch"/46265-001.bin

it gives me the same error "no such file or directory" the bin file is in my usr folder?
thanks again

---

### Post by dancavs on 2007-06-09
> i got past that error but i can't input the next line.

patch -p1 < /"path_to_patch"/46265-001.bin

hi replace "path_to_patch" with the directory in which 46265-001.bin lives.

---

### Post by JuhaK on 2007-06-09
I had lot of troubles with sound on my DV2104, everything seemed to detect just fine, but no sound. So I put laptop to hibernate and then booted. Of course, Linux did not start, I had to do reset (ctrl+alt+del). After second boot sound worked! :D

---

### Post by nautical34 on 2007-06-10
I was reading some things elsewhere and I managed to fix the no sound after reboot by doing 

sudo alsaconf ( choosing the HDA one, then choose the default for the questions)

then,

sudo /etc/init.d/alsasound reload


Still haven't gotten the speakers to mute when I plug my headphones in, tried everything.


Hope this works for others.

---

### Post by robeko on 2007-06-10
New notebook, new linux and ubuntu user... and works excellent!!!
Thnx,  great guide!

PS my notebook is a HP dv2315nr

---

### Post by ronbrooks on 2007-06-10
Can't down load the patch.  This is what I get. 

ronbrooks@ronbrooks-desktop:~$ wget [http://cache.gmane.org//gmane/linux/alsa/devel/46265-001.bin](http://cache.gmane.org//gmane/linux/alsa/devel/46265-001.bin)
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.

---

### Post by ronbrooks on 2007-06-10
Now I have no sound at all.  I get a message that no sound card was detected. I did all the steps in the how to so I don't know what went wrong. 

So where do I go from here.

---

### Post by lexarrow on 2007-06-11
> **ronbrooks said:**
> Now I have no sound at all.  I get a message that no sound card was detected. I did all the steps in the how to so I don't know what went wrong. 

So where do I go from here.

The stable version of alsa 1.0.14 is out, so recompile the drivers without the patch.

EDIT.  I updated the first post with the latest version

---

### Post by ronbrooks on 2007-06-11
sudo make clean and sudo make sudo make mrproper not working this is what I get. 

ronbrooks@ronbrooks-desktop:~/alsa-driver-1.0.14$ sudo make clean
rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
make[1]: Entering directory `/home/ronbrooks/alsa-driver-1.0.14/acore'
Makefile:6: /home/ronbrooks/alsa-driver-1.0.14/Makefile.conf: No such file or directory
/home/ronbrooks/alsa-driver-1.0.14/Rules.make:75: /Rules.make1: No such file or directory
make[1]: *** No rule to make target `/Rules.make1'.  Stop.
make[1]: Leaving directory `/home/ronbrooks/alsa-driver-1.0.14/acore'
make: *** [clean] Error 1

I also have an on board audio driver and no audio card in this system.  It is a VIA 8237 my question is do I need to change any of the commands for this type of setup.
and this

ronbrooks@ronbrooks-desktop:~/alsa-driver-1.0.14$ sudo make mrproper
rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
make[1]: Entering directory `/home/ronbrooks/alsa-driver-1.0.14/acore'
Makefile:6: /home/ronbrooks/alsa-driver-1.0.14/Makefile.conf: No such file or directory
/home/ronbrooks/alsa-driver-1.0.14/Rules.make:75: /Rules.make1: No such file or directory
make[1]: *** No rule to make target `/Rules.make1'.  Stop.
make[1]: Leaving directory `/home/ronbrooks/alsa-driver-1.0.14/acore'
make: *** [mrproper] Error 1

---

### Post by dancavs on 2007-06-11
update: i now have sound working ... the last thing i did (after pretty much trying everything mentioned in this post and thankyou lexarrow) was from terminal:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

then added the following to this file: 

```
options snd-hda-intel index=0 model=laptop-hp
```

---

### Post by CrankyFilipino on 2007-06-13
well i'm a new linux and ubuntu user.. and i've tried a few of the things in this thread to make it work.. after a windows session on a restart then ubuntu has no sound.. which really was sucking.. however i didnt see this elsewhere in the thread and i'm surprised. but what works every time for me when this happens is this.. i just shutdown the computer.. not restart.. just complete shutdown.. then when i turn it back on and pick ubuntu to load the sound is all good.. now i know this isn't perfect.. but considering the infrequency of switching back and forth so much.. seems to be a nice way to get sound back lol

and I also have a new hp pavillion dv2000

---

### Post by jpyanowski on 2007-06-18
I want to thank this thread for giving me sound on my HP Pavillion dv2120us.

---

### Post by Niomi on 2007-06-20
I tried this for my Pavilion dv2313cl. No errors came up while executing these commands, but I still have no sound.
Thanks for all the effort put into this, however.

---

### Post by Niomi on 2007-06-20
> **lexarrow said:**
> 3.Back-up your current configuration:

```
tar -zcvf original-drivers.tgz /lib/modules/`uname -r`/kernel/sound
```

How can I restore the backup I made with this command?

---

### Post by greybit on 2007-06-29
Thanks lexarrow!  These steps got my headphone jack working.

---

### Post by bogdan.veringioiu on 2007-07-11
Hi.
I have the same sound chip (ConexantCX20549), using snd_hda_intel driver, on a HP 530 laptop.
I installed Feisty, and everything works with the sound, except for the auto-mute functionality.
If i plug in the headphones, the laptop speakers are not muted. Also there is no option to do this in the sound preferences panel.
I tried to compile alsa drivers like suggested in this thread, but with no success. Nothing changed.
Can anyone help?
Thanks.

---

### Post by fusionisthefuture on 2007-07-12
thanks dude, this fixed my headphone auto mute issue on my dv2200 cto notebook! thanks a ton.
-arne

---

### Post by sparks0548 on 2007-07-15
Man thanks for this forum.  I was seriously debating pulling my hair out.  The instructions were great, very concise and more importantly to me, they worked.  I can finally listen with my headphones on and not have everything playing through the speakers.:guitar:

---

### Post by oootheoneooo on 2007-07-16
First of all, I would like to thank you all for this forum. I finally got the auto-mute working on my laptop. The only thing is... the integrated mics that come with my HP dv2020us laptop stopped working. I was able to use them with Skype and twinkle, but unfortunately after compiling alsa, it stopped working. Any ideas on how to fix this?

---

### Post by godzillak on 2007-07-17
Hi,

I have the same no-sound problem on my dv2386ea notebook. No sound and the powerplug-trick doesn't work at all on my system. But a strange thing happened. My gnome gives no sound at all, but if I play an mp3 in console (using mpg123) everything works fine, I can even adjust and mute/unmute volume using my quickplay buttons. Any ideas why gnome refuses to play sound?

---

### Post by oootheoneooo on 2007-07-17
Ok, today I actually tried using Twinkle and it does in fact work. For some strange reason, the only app that doesn't work with the Internal mics is Skype and Ekiga. Ekiga sound is awful and I can't here people at the other end.  Anyone have a clue why this might be happening? Has anyone else encountered this same problem? If so, please let me know, would appreciate any help you might give.

---

### Post by alef13 on 2007-07-20
> **hiazle said:**
> Hey lexarrow, can you point me in the right direction for WiFi, and webcam. Is it just the wiki? I haven't bothered trying to get these to work as I'm waiting on this sound issue to get resolved. My internal mic works very well with Skype 1.4 (When the sound is working).


for the wifi, just run: apt-get install bcm43xx-fwcutter
reboot, and you'll get it working perfect.

---

### Post by alef13 on 2007-07-20
I followed all the steps in the first post of this forum and I got the sound working, but, only when I boot the laptop without the AC cord.

Even with the sound working with the latest alsa 1.0.14rc2, I was having these issues:

1. Needed to boot ubuntu without the AC cord, or else the sound didn't work - with no changes in /etc/modprobe.d/alsa-base;
2. When working with external USB HD (for example, find /media/disk) I was getting a lot of noise in the headphones, only when the AC cord as plugged in. After unplugging the AC cord the noises stopped;
3. Auto-mute wasn't working;
4. When playing mp3 with totem (using totem-xine) the whole system was hanging for seconds, but kept working after that.

But I fixed everything after installing the latest snapshot of SUSE's driver:
[ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/)
(I downloaded alsa-driver-hg20070721.tar.bz2)

Without rebooting, I removed the mixer applet from the panel, and removed all modules related with sound (as root):
# lsmod|grep snd|cut -d \  -f1|xargs modprobe -r     (note: two spaces after \)

After that, I compiled alsa-driver:
$ tar jxvf alsa-driver-hg20070721.tar.bz2
$ cd alsa-driver-hg20070721
$ ./configure --with-oss=yes --with-cards=hda-intel
$ make
$ sudo make install

Added the following to /etc/modprobe.d/alsa-base (in the first line, not the last - if you do that, don't forget to leave a blank line at EOF):
options snd-hda-intel index=0 model=3stack-dig

Loaded the module:
$ sudo modprobe snd-hda-intel

Loaded the mixer (Volume Control) applet in the panel again.

Everything is working perfect. Clear sound, auto-mute, no noises, no hangs, etc.
By the way, before I found this forum, I installed the latest version of ubuntu, gutsy 7.10, but it didn't worked either.

Good luck!

---

### Post by lexarrow on 2007-07-21
For all those who have sound but can't use the mic:

1.After having compiled the drivers double-click Volume control (the speaker next to the clock), then Edit->Preferences and check all the boxes (you should have 8 boxes : Master, PCM, LineIn, IEC958, Digital, Ext Mic, Int Mic, Int Mic (yes 2 times Int Mic). Close Preferences.

2.Go to Switches tab and check LineIn

3.Go to Recording tab and be sure both mic and speakers are not muted. 

4. Go to Playback tab and be sure Master,PCM, and Ext Mic are not muted and BE SURE IntMic IS MUTED!

5. In a terminal, login as root and type:
```
 /etc/init.d/alsa-utils stop

```
6. Type the following command:
```
/usr/sbin/alsaconf
```
When it asks you, choose the 'hda-intel' card and then to save the changes to the files
7.Type:
```
 /etc/init.d/alsa-utils start

```
and try out your mic (I tested it with Skype)

I this doesn't work uninstall the following packages and recompile the dirvers:
```
 sudo apt-get remove --purge alsa-base alsa-tools

```

There's no solution for the 'no soud after Windows yet, but:

1.1 If you are in Windows unplug the AC cable and plug it back after you logged into Ubuntu.
1.2 If you are already on Linux after a Windows session and you didn't follow point 1.1estat, Unplug the AC cable, then SHUTDOWN , not restart the computer. Start it again manually and plug the cable back after you logged into Ubuntu 

This way you should have sound every time you follow one of these 2 steps

Also edited the first post

---

### Post by acorey on 2007-07-23
"been prepatched,i dont know but here,s what i did.for connexant venice with nvidia chpset
i downloaded the SUSE alsa snapshot driver from 
[ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver)
i downloaded the package 
alsa-driver-hg20070526.tar.bz2 dated 05/26/2007
renamed it to alsa-driver.tar.bz2 for ease of installation.
then executed the following commands in the terminal
$tar xvf alsa-driver.tar.bz2
$./configure
$sudo make
$sudo make install

then rebooted the system,sound worked automute worked,sound was clear and loud,but i have not still tested the internal mic.Please make sure that the proper build libraries are installed,i am new to linux so i might not be able to help if u run into any trouble but i will try my best to help out.thank you"

I have an HP dv2031us and this worked for me after compiling latest drivers in Feisty.

Thanks

---

### Post by GeoMX on 2007-08-11
> **alef13 said:**
> 
But I fixed everything after installing the latest snapshot of SUSE's driver:
[ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/)
(I downloaded alsa-driver-hg20070721.tar.bz2)

Thanks a lot for your comments, finally I could make sound work :) (HP dv2150).

Steps I followed:

- couldn't stop snd-hda-intel module, continued anyway
- downloaded latest SUSE's driver snapshot
- compiled and installed
- added **options snd-hda-intel index=0 model=3stackdig** to /etc/modprobe.d/alsa-base
- rebooted, voilá!

Agan, thank you so much :).

---

### Post by fusionisthefuture on 2007-08-22
just wanted to say:

i followed this HOWTO to the "t" and it worked perfectly, and i think its the only howto i can say that for.  very good job, i just had to use it for the second time, and it worked perfectly again.  

thanks alot
-arne
p.s. i have a dv2200 cto, or something, the stickers say different things.

---

### Post by n0ctem on 2007-08-24
I need a little help with the auto mute fix. When I run the commands in Terminal I always get the same error; "./configure: No such file or directory". Anyone know what I'm doing wrong?

---

### Post by lexarrow on 2007-08-25
> **n0ctem said:**
> I need a little help with the auto mute fix. When I run the commands in Terminal I always get the same error; "./configure: No such file or directory". Anyone know what I'm doing wrong?

Be sure you are in the right directory. At which of the ./configure are you?

---

### Post by n0ctem on 2007-08-26
> **lexarrow said:**
> Be sure you are in the right directory. At which of the ./configure are you?
Ah, never mind, I figured it out. I was unaware that I had to manually change directories. I'm just starting out with linux, and I'm not too familiar with the Terminal. Thanks, though.

---

### Post by fusionisthefuture on 2007-09-05
hi everybody, id like to say once again how much of an awesome howto this is, but i thought it could use one thing...  because it needs to be recompiled with every kernel update, i thought the process could be made easier with a script.

```


#!/bin/sh

echo "preparing"
sudo apt-get remove --purge alsa-base alsa-tools

sudo apt-get install linux-headers-$(uname -r) build-essential libncurses5-dev libncursesw5-dev ncurses-term alsa-tools-gui gettext po-debconf debhelper quilt alsa-base libc6-dev
	echo "getting packages"
sudo aptitude install linux-headers-$(uname -r) build-essential libncurses5-dev libncursesw5-dev ncurses-term alsa-tools-gui gettext
	echo "removing packages"
sudo aptitude remove --purge alsa-base alsa-tools
	echo "backing up current drivers"
tar -zcvf original-drivers.tgz /lib/modules/`uname -r`/kernel/sound

mkdir /home/user/alsa
	echo "made /home/user/alsa dir"
cd /home/user/alsa
	echo "getting alsa packages"
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.14.tar.bz2
	echo "alsa packages gotten"
	echo "unpacking packages"
tar xvf alsa-driver-1.0.14.tar.bz2
tar xvf alsa-lib-1.0.14a.tar.bz2
tar xvf alsa-utils-1.0.14.tar.bz2
tar xvf alsa-firmware-1.0.14.tar.bz2
	echo "packages unpacked"
	echo "installing alsa-driver"
cd alsa-driver-1.0.14/
sudo make clean
sudo make mrproper
./configure --with-oss=yes --with-cards=hda-intel 
sudo make
sudo make install
	echo "installing alsa-lib"
cd alsa-lib-1.0.14a
sudo make clean
./configure
sudo make
sudo make install
	echo "installing alsa-utils"
cd alsa-utils-1.0.14
./configure
sudo make clean
sudo make 
sudo make install
	echo "installing alsa-firmware"
cd alsa-firmware-1.0.14
./configure
sudo make clean
sudo make 
sudo make install
	echo "all installed"
exit 0

```

this just worked flawlessly for me today, but first of all, you must note that this is just the majority of the work for installing the packages, it does not complete the installation, so you have to pick up the original howto, after its done with all the make, installing.  

to make this into something you can run, create a new file in /usr/local/bin/whatever-you-want, (i think, im new to scripts) and paste this into the new file.  then close the file, and in a terminal type 

```
sudo chmod +x /path/to/file/you/just/made/whatever-you-want
```

this makes that file executable, and to execute it just type the name you gave the file in the terminal, like you would with any program that you execute from the terminal.  e.g.  mine is /usr/local/bin/install-alsa

so in the terminal i type

```
sudo whatever-you-want
```

and off it goes.

---

### Post by zdarova on 2007-09-13
my notebook: dv2008ea, Amd turion x2, 6150 video,card audio nvidia, chipset: conexant,
thanks to lexarrow

i installed clean 7.04 ubuntu,
after i restarted without AC adapter, and sound worked...but not auto-mute, followed the lexarrow  guide from the first page and voilà ...after a restart was working and the jack auto-mute too.
for wireless bcm43xx and for the webcam i followed again the lexarrow links and the webcam is working but the wifi adapter only can see the ssid...but is not conecting....maybe because i have WPA and mac filter...but it's ok for now....still remains the problem of reboot after windows with AC adapter...
I sow a new update for QuickPlay(is the program that can be used without an OS) on HP.com support&driver site.

Some geek can try...because i am tired to reinstall my Ubuntu :lolflag:
i am a noob...using ubuntu for few days...i like't :guitar:

i have some problem with the berill desktop effects and the cube...last time i was unable to start the x server, even with startx from line command when is starting Ubuntu
and how i can install the app for music editing...it is name Studio ..or something similar

---

### Post by Dan334477 on 2007-09-15
Hi.

The HowTo didn't work for me, but that's not what I'm writing about.  I just want to know how to reset my sound drivers using the backup that's made in the howto.  I replaced the files and directories in /lib/modules/2.6.20-16-generic/kernel/sound with the sound directory from the backup.   Now, when I load, I get an error from the volume control panel that says "no volume control GStreamer plugins and/or devices found."  Suggestions, please?  Before doing the HowTO, my speakers and headphones worked, the external and internal mics did not work, and I'm not sure about the other features because I didn't test them.  I just want to re-establish my pre-howto functionality, and then I'll worry about the external mic, which is the feature I had hoped this howto would enable.

Thanks.

---

### Post by Dan334477 on 2007-09-15
Nevermind.  I got it to mostly work by doing the howto again and testing the sound after each step.

---

### Post by Mitch_Arsenal on 2007-09-16
Lexarrow,

Thank you so much for your how to. I followed it step by step and now both headphones and digital out are working. Wohoo!

---

### Post by bolero1966 on 2007-09-21
> **lexarrow said:**
> I am currently running Ubuntu Studio on a HP Pavilion dv2025nr.

After this install you should have all sound features enabled.

This is a compile of alsa drivers 1.0.14

1.Check your kernel version - in terminal window type:

```
`uname -r'
```

mine is 2.6.10-16-generic

2.Install these packages:

```
sudo apt-get install linux-headers-$(uname -r) build-essential libncurses5-dev libncursesw5-dev ncurses-term alsa-tools-gui gettext
```  

and uninstall these ones:
```
 sudo apt-get remove --purge alsa-base alsa-tools

```

be sure not to uninstall alsa-utils as it will uninstall your gdm  too

3.Back-up your current configuration:

```
tar -zcvf original-drivers.tgz /lib/modules/`uname -r`/kernel/sound
```

4.Make a directory for alsa packages:

```
mkdir /home/user/alsa
cd /home/user/alsa

```

5. Get alsa packages:
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.14.tar.bz2

```


6.Unpack archives:

```
tar xvf alsa-driver-1.0.14.tar.bz2
tar xvf alsa-lib-1.0.14a.tar.bz2
tar xvf alsa-utils-1.0.14.tar.bz2
tar xvf alsa-firmware-1.0.14.tar.bz2
```

7.Install driver:
Note: 'sudo make clean' and sudo make mrproper are to clean out your previous drivers. If you are doing a fresh install, you don't need them.

```

cd alsa-driver-1.0.14/
sudo make clean
sudo make mrproper
./configure --with-oss=yes --with-cards=hda-intel 
sudo make
sudo make install
```

9.Install alsa-lib:

```
cd alsa-lib-1.0.14a
sudo make clean
./configure
sudo make
sudo make install
```

10.Install alsa-utils:

```
cd alsa-utils-1.0.14
./configure
sudo make clean
sudo make 
sudo make install

```

11.Install alsa-firmware:

```
cd alsa-firmware-1.0.14
./configure
sudo make clean
sudo make 
sudo make install

```

12.double-click Volume control (the speaker next to the clock), then Edit->Preferences and check all the boxes (you should have 8 boxes : Master, PCM, LineIn, IEC958, Digital, Ext Mic, Int Mic, Int Mic (yes 2 times Int Mic). Close Preferences.

13.Go to Switches tab and check LineIn

14.Go to Recording tab and be sure both mic and speakers are not muted. 

15. Go to Playback tab and be sure Master,PCM, and Ext Mic are not muted and BE SURE IntMic IS MUTED!

16. In a terminal, login as root and type:
```
 /etc/init.d/alsa-utils stop

```

17. Type the following command:
```
/usr/sbin/alsaconf
```
When it asks you, choose the 'hda-intel' card and then to save the changes to the files

18.Type:
```
 /etc/init.d/alsa-utils start

```

You should be done! If yo still don't have sound restart and it will be ok !

Note: 1. Every time you update the kernel, you have to recompile the driver
          2. There is still an issue unresolved, the 'no sound after a windows session ' and can be fixed by unplugging the power cord before booting Ubuntu. If it doesn't work, reboot again with no power cord. 

There's no solution for the 'no sound after Windows yet, but:

2.1 If you are in Windows unplug the AC cable and plug it back after you logged into Ubuntu.
2.2 If you are already on Linux after a Windows session and you didn't follow point 1.1estat, Unplug the AC cable, then SHUTDOWN , not restart the computer. Start it again manually and plug the cable back after you logged into Ubuntu 

This way you should have sound every time you follow one of these 2 steps

Special thanks to these 2 articles: [1]("http://www.pixelmonkey.org/2007/03/18/dv2000-alsa-patches/") and [2]("https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard?highlight=%28alsa%29/")

Hope it works for you too!

After 3 days of compiling and lots of coffee, good thing I found this thread, I finally fixed the problem thanks to you. I have a HP DV2422.

---

### Post by fusionisthefuture on 2007-09-21
theres no need to quote the entire original post... we would understand what youre talking about, theres only one HOWTO in this thread.

---

### Post by kaurxxl on 2007-09-26
I decided to try linux again and after searching for awhile I found this guide ... and I got everything working ... now yesterday there were some updates witch I downloaded.
Now I don't have sound anymore and I do get that "no volume control GStreamer plugins and/or devices found" error. I followed that guide again and I still get that same error. Tryed that about 3 times.

So does anyone know's how to get sound working ?

My laptop is hp paviion dv2208ea.

And one off-topic question: does anyone know or has some link for a guide to get hp remote working ?

---

### Post by fusionisthefuture on 2007-09-26
you most likely need to recompile the alsa drivers again...  the update you downloaded was probably a linux-kernel-header update, and whenever you download one of these, it makes you redo some things, one being this particular way of doing your sound driver.  

good luck,
-arne

---

### Post by kaurxxl on 2007-09-27
Got sound back :) ... but with puting previous kernel back or something like that ... one freind suggested to do that.

---

### Post by amirseg on 2007-10-01
greate guide!!!!

fixed my annoying problem of very low sound on speakers.

Thanks!!

---

### Post by ashinshanghai on 2007-10-29
Help! Newbie here.

I got through step 12, and then I did not have these options available in my Volume Control Preferences. I rebooted, and then tried opening Volume Control Again. But I received this error message: 

No volume control GStreamer plugins and/or devices found.

What should I do now?!?!?

I am on an HP dv1000t using Gutsy (though I was having the same sound problems with Feisty).

```
~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

---

### Post by MidasTouchBR on 2007-11-10
Guys

I've done every step of the HOWTO. The result was that now my system complains that no sound card is found. I'm running Ubuntu 7.10 in a HP DV2125. My kernel version is 2.6.22-14. My alsa version is 1.0.15.

Here is what "aplay -l" says:

> aplay: device_list:205: nenhuma placa de som encontrada... 

My system is in portuguese, so that message can be translated as "no sound card was found".

I've got the same message about the "gstreamer" thing, so, I've taken a look at my modules by doing a lsmod and noticed that snd-hda-intel was not loaded. I tried to load it with modprobe. The result was:

> guilherme@guilherme-laptop:~/alsa$ sudo modprobe snd-hda-intel
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
 

Then, I've taken a look at what "dmesg" had to tell me. That's what I've found:

> [  216.614577] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[  216.614590] snd_hda_intel: Unknown symbol snd_ctl_add
[  216.614638] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[  216.614641] snd_hda_intel: Unknown symbol snd_pcm_new
[  216.614689] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[  216.614692] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  216.614734] snd_hda_intel: disagrees about version of symbol snd_card_register
[  216.614737] snd_hda_intel: Unknown symbol snd_card_register
[  216.614774] snd_hda_intel: disagrees about version of symbol snd_card_free
[  216.614777] snd_hda_intel: Unknown symbol snd_card_free
[  216.614815] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  216.614819] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  216.614857] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[  216.614861] snd_hda_intel: Unknown symbol snd_card_proc_new
[  216.614972] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[  216.614976] snd_hda_intel: Unknown symbol snd_ctl_find_id
[  216.615070] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[  216.615073] snd_hda_intel: Unknown symbol snd_ctl_new1
[  216.615148] snd_hda_intel: disagrees about version of symbol snd_component_add
[  216.615151] snd_hda_intel: Unknown symbol snd_component_add
[  216.615195] snd_hda_intel: disagrees about version of symbol snd_card_new
[  216.615198] snd_hda_intel: Unknown symbol snd_card_new
[  216.615277] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  216.615280] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  216.615328] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[  216.615331] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  216.615371] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[  216.615374] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  216.615459] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[  216.615510] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[  216.615546] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[  216.615549] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  216.615594] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[  216.615597] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[  216.615644] snd_hda_intel: disagrees about version of symbol snd_device_new
[  216.615647] snd_hda_intel: Unknown symbol snd_device_new
[  216.615699] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[  216.615702] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  216.615751] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[  216.615754] snd_hda_intel: Unknown symbol snd_card_disconnect
[  216.615790] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  216.615793] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  216.615960] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[  216.615964] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  216.615999] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[  216.616002] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[  517.440765] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[  517.440774] snd_hda_intel: Unknown symbol snd_ctl_add
[  517.440821] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[  517.440824] snd_hda_intel: Unknown symbol snd_pcm_new
[  517.440870] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[  517.440873] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  517.440913] snd_hda_intel: disagrees about version of symbol snd_card_register
[  517.440916] snd_hda_intel: Unknown symbol snd_card_register
[  517.440953] snd_hda_intel: disagrees about version of symbol snd_card_free
[  517.440955] snd_hda_intel: Unknown symbol snd_card_free
[  517.440993] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  517.440996] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  517.441033] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[  517.441036] snd_hda_intel: Unknown symbol snd_card_proc_new
[  517.441146] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[  517.441148] snd_hda_intel: Unknown symbol snd_ctl_find_id
[  517.444763] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[  517.444769] snd_hda_intel: Unknown symbol snd_ctl_new1
[  517.444844] snd_hda_intel: disagrees about version of symbol snd_component_add
[  517.444846] snd_hda_intel: Unknown symbol snd_component_add
[  517.444890] snd_hda_intel: disagrees about version of symbol snd_card_new
[  517.444892] snd_hda_intel: Unknown symbol snd_card_new
[  517.446032] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  517.446036] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  517.446083] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[  517.446085] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  517.446126] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[  517.446128] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  517.446231] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[  517.446281] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[  517.446318] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[  517.446320] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  517.446365] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[  517.446367] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[  517.446414] snd_hda_intel: disagrees about version of symbol snd_device_new
[  517.446416] snd_hda_intel: Unknown symbol snd_device_new
[  517.446468] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[  517.446470] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  517.446522] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[  517.446525] snd_hda_intel: Unknown symbol snd_card_disconnect
[  517.446561] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  517.446563] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  517.446727] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[  517.446730] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  517.446765] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[  517.446768] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step


Does anyone have an idea of what is happening? I haven't updated anything. Except for the alsa packages that I've downloaded to try the HOWTO, my system is the same...

---

### Post by geminianguy101 on 2007-11-14
have  a sony vaio Fz140e   could get my headset working.!! Thanks for the wonderful post!!

---

### Post by lduperval on 2007-12-10
I did all this with 1.0.15 and the sound works (it working with a standard install of Feisty also) on a dv2000. My issue is that the speakers don't turn off when plugging the headphones. I thought 1.0.15 would take car of that, but nothing yet. What am I missing (I don't have the Digital control in the cvolume control).

L

---

### Post by Watchtow3r on 2007-12-21
In the first step, what are the apostrophes for around 'uname -r'? Do you need them, or should you not use them?

---

### Post by Xiong Chiamiov on 2007-12-21
Apostrophes are usually used when you have space in something but want the shell to recognize it's all together.  It doesn't seem to make a difference in this case.

---

### Post by Watchtow3r on 2007-12-21
> **Xiong Chiamiov said:**
> Apostrophes are usually used when you have space in something but want the shell to recognize it's all together.  It doesn't seem to make a difference in this case.

do you use them in the terminal though? Because whenever I do, my @ubuntu:~$ thing on the left side turns into a > sign and won't accept any commands I type in.

---

### Post by Xiong Chiamiov on 2007-12-21
> **Watchtow3r said:**
> do you use them in the terminal though? Because whenever I do, my @ubuntu:~$ thing on the left side turns into a > sign and won't accept any commands I type in.
Hmm, that's interesting.  I get the same thing whether I use single, double, or no quotes at all.

---

### Post by apache2020 on 2007-12-21
thanks a million - worked on the hp dv6000 as well

dave

---

### Post by Mamono on 2007-12-27
> **Xiong Chiamiov said:**
> Hmm, that's interesting.  I get the same thing whether I use single, double, or no quotes at all.

Those are not quotes, they are backticks.  On my keyboard the backtick is located in the upper left underneath the ~.  What they do is replace the section inside the backticks with the stdout of the command within them.  If you type "uname -r" at a prompt it will spit out the kernel version.  Essentialy, that is all the command is asking for.  if you were to replace the backticks and everything inside them with that information it would accomplish the same thing.

For example, let's say you want to kill process_x by using it's pid file.  You could either do this:

# cat /var/run/process_x.pid
2544
# kill -15 2544

Or you could do this:

# kill -15 `cat /var/run/process_x.pid`

The latter version is useful for scripts as the process ID would be different everytime the process starts.

---

### Post by redonisc on 2007-12-28
> **MidasTouchBR said:**
> Guys

I've done every step of the HOWTO. The result was that now my system complains that no sound card is found. I'm running Ubuntu 7.10 in a HP DV2125. My kernel version is 2.6.22-14. My alsa version is 1.0.15.

Here is what "aplay -l" says:



My system is in portuguese, so that message can be translated as "no sound card was found".

I've got the same message about the "gstreamer" thing, so, I've taken a look at my modules by doing a lsmod and noticed that snd-hda-intel was not loaded. I tried to load it with modprobe. The result was:



Then, I've taken a look at what "dmesg" had to tell me. That's what I've found:



Does anyone have an idea of what is happening? I haven't updated anything. Except for the alsa packages that I've downloaded to try the HOWTO, my system is the same...

It has a fix ... [http://ubuntuforums.org/showthread.php?t=577699](http://ubuntuforums.org/showthread.php?t=577699) :guitar:

---

### Post by Watchtow3r on 2007-12-30
step 4 isn't working for me... when I enter in "mkdir /home/user/alsa" I get a message saying "mkdir: cannot create directory `/home/user/alsa': No such file or directory".

how can I fix this? Please note that I just loaded ubuntu on my USB drive, and so the user still just says Live Session User (in the upper right hand corner of the screen next to the time and date). Thanks.

---

### Post by Watchtow3r on 2007-12-30
bump

---

### Post by pavicnat on 2007-12-30
> **lexarrow said:**
> 

7.Install driver:
Note: 'sudo make clean' and sudo make mrproper are to clean out your previous drivers. If you are doing a fresh install, you don't need them.

```

cd alsa-driver-1.0.15rc3/
sudo make clean
sudo make mrproper
./configure --with-oss=yes --with-cards=hda-intel 
sudo make
sudo make install
```


How do I know that I have an hda-intel card? My computer is an amd, so I should think that part of the code should be different for me.

---

### Post by quik366 on 2008-01-02
Just thought I would share my experience with this exhausting issue, I loooove ubuntu but never could get sound to work tried everything (So I thought) finally I stop being so hard headed and decided to try unplugging the computer and removed battery, booted into ubuntu and works great, I have been trying to weeks and never thought that unlugging would work so I never tried it ...how stupid was I?! Anyway huge thanks to everything posting on this topic couldnt have done it without you!!!!!

btw I have the HP Pavillion dv2225nr if anybody has any questions on exact steps please feel free to contact me I know how it feels to be stuck without sound!

---

### Post by Arthur Archnix on 2008-01-09
Very nice how-to. Before I gave up on Windows completely I had the same no sound after windows issue. Unplugging didn't do it for me, but going into bios, saving and exiting, then doing a hard power down (pressing and holding the power button) then restarting into Ubuntu worked. Not exactly healthy for the hard-drive, but if you use windows infrequently perhaps it will help someone.

---

### Post by lexarrow on 2008-01-26
I'm pleased to see that in Hardy Heron (Ubuntu 8.06LTS) the "no sound after windows" bug is fixed.

THANKS UBUNTU TEAM!

---

### Post by blerinab on 2008-01-30
Thanks a lot. This worked great for my HP pavillion dv6631a.

---

### Post by Big G on 2008-01-31
Hi Guys
I have a DV2000. I have got to stage 12 of the 'how to' mentioned earlier in the forum. However in the edit->preferences dialogue I do not get 8 boxes. In change device menu I get a choice of HDA Intel (Alsa) or conexant id 5051 (oss). In HDA I  only get master and PCM. In conexant I get volume and in-gain. Audio playback works ok and the in built mic works fine in Skype. Speakers work ok but inserting headphone jack doesn't mute speakers.
I am running a clean install of ubuntu gustsy.

Any ideas gratefully received.

Cheers

G

---

### Post by s3raphim on 2008-02-23
So I followed the HowTo, hoping that it would get the headphone sensing to work.  It didn't.  Also, not my volume keys do not work when they did before.  How do you completely roll back these changes to the original configuration?  Expanding the backed up directory back into .../kernel/sound didn't do it, so obviously it is a little more complicated than that.

Thanks!

---

### Post by jpconard on 2008-03-03
HP dv2313cl here, went through it and still nothing.  Running Xubuntu 7.10.

But thanks to post above above shut down and remove battery - SUCCESS, finally.

Still not sure everything is quite right, but at least I have sound.

Can the above instructions be run with the latest alsa versions 1.0.16, I think?  Anybody tried that.  I don't really care, but while I'm at it why not setup the latest?

---

### Post by myddewji13 on 2008-03-03
Hey i got the same prob as big G... im pretty sure this is a seperate problem as all fixes ive tried havent really worked...hopin the next release will fix it ...until then im living without headphones  :(. ...thnk god for ipods

---

### Post by lduperval on 2008-03-04
For the "No sound after Windows" bug, I don't do all that battery stuff. I just do a suspend, unplug the battery, then restart and voila! Instant sound. Much quicker than a complete reboot.

L

---

### Post by Tonsil Romancer on 2008-03-19
Toshiba users can find the solve [here](http://ubuntuforums.org/showthread.php?t=568463#1).

---

### Post by bbddnn07 on 2008-03-22
Hey lexarrow,
I followed your instructions up to Step 11, but I still get the message "No volume control GStreamer plugins and/or devices found." when I double click the volume icon.  What do you think I should do?

---

### Post by myddewji13 on 2008-03-22
Hey...upgraded to the beta ..PROBLEM IS FIXED!!!! ..unfortunately...now my internet is gone..<insert profanity here> broadcom...

---

### Post by zdarova on 2008-03-26
> **myddewji13 said:**
> Hey...upgraded to the beta ..PROBLEM IS FIXED!!!! ..unfortunately...now my internet is gone..<insert profanity here> broadcom...

that BETA? about ubuntu or alsa drivers?

---

### Post by myddewji13 on 2008-03-26
lets see... i upgraded to the beta (Ubuntu HardyHeron 8.04) ...the only problem I had was my wireless...so i clean installed gutsy... set up ndiswrapper and then upgraded to hardy... now everything works...headphones, mic, webcam, wpa authentication, suspend/hibernate, network auto refresh...you name it ...no probs at alll (ok i lied...the card reader still doesnt work...but i've read that it only works w/ sd cards which i havent tried yet)...hell even the remote works... I LOVE U UBUNTU!!!

---

### Post by zdarova on 2008-03-27
so i did the upgrade to 8.04 beta, now audio is working...i like new software that they added ekiga, gps and bluetooth manager.
the problem is the quality of my audio is not so good, how do i procced?
recompile alsa drivers...? can i follow the lexx guide?

---

### Post by brinkofacomplex on 2008-04-07
Okay, I got everything to install, but when I try to edit the sound preferences, I can't - "No volume control GStreamer plugins and/or devices found."

---

### Post by D0R1AN on 2008-04-15
CURSES

I'm cursing like crazy right now, because I can't find a solution on here that doesn't give me errors that don't make sense to me, in this case having to do with the "make clean" command, which wouldn't work in any of these instances. I've already uninstalled and reinstalled every bit of ALSA software I can find and still can't get any sound out of my bloody headphones.

Here's the problems I ran into:

E: Couldn't find package libncurses5-dev

So I'm guessing I don't have the proper repositories listed in my software sources, right? Because I don't find libncurses5-dev anywhere.

So, could somebody please tell me how to add a software source PROPERLY? I can never find their addresses listed or the proper format for adding them to the software sources thing. EVERY SINGLE repository I've tried to add has failed. Not one has ever, ever worked except the ones that are already listed by default. I have spent close to six hours looking for a proper explanation of this on the forums ----- this is such a simple function, why is it completely destroying my life????? Please, somebody just give me a straight answer as to what to enter in the address field when adding a repository. PLEASE. THIS INFORMATION IS RIDICULOUSLY HARD TO FIND.

Thanks so much to anybody who can help me out. I'm the most frustrated Noob ever. I just want my headphone jack to work... please... god...

Okay the other relevant info here is that it totally worked under hardy heron - what does that mean and how can it help me???

---

### Post by brinkofacomplex on 2008-04-16
I did it!
One simple command: sudo apt-get install linux-backports-modules
from [http://aldeby.org/blog/?page_id=87#audio](http://aldeby.org/blog/?page_id=87#audio)
I rebooted and now I have sound! Media touch-buttons work, even! Hopefully it will stay.
Before this, I followed instructions 1 - 11 from this thread, and installed all "ALSA" search results in Synaptic Package Manager that had the Ubuntu symbol beside them (stupid, maybe, but lack of music makes me crazy).

---

### Post by Yellow Pasque on 2008-04-16
D0R1AN, go to System -> Administration -> Software Sources and check the first four boxes. Uncheck the CD unless you have a slow internet connection and want to use the older package versions on the CD. Here are some scripts to make the ALSA build easy:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

