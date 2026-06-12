---
title: "headphones not disabling onboard speakers"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by m0untainrebel on 2007-05-13
when i plug in headphones or speakers into my speaker jack, sound comes out of the external audio device fine, but it also still comes out of my onboard speakers as well. i've tried adjusting settings in alsamixer, but it changes the volume for both internal and external speakers at the same time. i want it to disable onboard sound when i plug in headphones.

i'm running ubuntu feisty on an averatec 2300 series laptop. this is my soundcard, listed from lspci -v:

```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: TWINHEAD INTERNATIONAL Corp Unknown device a005
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at bded8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

```

any help? thanks!

---

### Post by hartz on 2007-05-14
I believe most motherboards nowadays have a jumper which controls this behavior - have a look in your motherboard manual.

---

### Post by lawr_rawr on 2007-05-29
I have an Averatec 2370, and you can fix the issue by right-clicking on the volume control icon and selecting Open Volume Control. Click the sound icon for Front to mute the speakers. Make sure the volume level for front is pretty high, or else you won't get much volume from your headphones.

Just un-mute Front when you want your speakers back.

---

### Post by mkoehler on 2007-05-29
Lawr_rawr's solution will solve your problem.  Simply mute/unmute the speakers as necessary using the volume control.

---

### Post by m0untainrebel on 2007-05-29
oh sweet, thanks! front actually isn't in my volume control (only front mic is), but front is in alsamixer, and i can mute that and it works fine. thanks!

---

### Post by lawr_rawr on 2007-05-30
I can't remember now, but I think I might've had to enable Front in the Volume Control. Go to Edit --> Preferences, and check the ones you want to add. 

Now, if only there was a way to make the Fn-F8 and F9 keys adjust PCM instead of Front... is that possible?

---

### Post by dhasenan on 2007-06-15
I have the same issue with not getting a separate volume control for headphones. I've gone into Volume Control preferences and have every single channel selected; nothing helps.

I'm on the same system -- Compaq V3000 series, nVidia MCP51, all the latest updates on Feisty (upgraded from Edgy).

I'm trying alsa-1.0.14; it has some changes related to the MCP51. (Can't help but think of Tron whenever I write that.)

---

### Post by corefile on 2007-07-03
I had the same problem in feisty with the computer speaker playing, even though I had my headphones plugged in. I was able to fix it by going into the opening the volume control -> Preferences ->  and select headphone jack sense. That will add a tab to your volume control call "switches", in there I checked "headphone jack sense" and now I get sound out of my headphones not the motherboard speaker.

---

### Post by quixotic-cynic on 2007-09-18
I am using a Toshiba laptop and I still have problems despite reading several pages on the alsa site etc - is there some way I can (permanently, but short of a screwdriver) disable the internal speakers (but not the internal amp)?

Edit: I've given up fixing this for now.

---

### Post by Jere997 on 2007-09-26
I found out, actually its quite simple (Ubuntu 7.04 Feisty):
Right-click on volume control (next to the clock) -> "Open volume control"->"Preferences"->Check "Headphone Jack Sense"
Now there should be a new tab in the controls named "Switches". Go there and activate Jack Sense.
Works on my HP D530cmt.

---

### Post by sem7ex on 2007-09-26
i know i searched quite a bit until i found a solution and this worked for me:

$ sudo echo options snd-hda-intel model=laptop >> /etc/modprobe.d/alsa-base

found here [http://ogolberg.googlepages.com/c502us.html]("http://ogolberg.googlepages.com/c502us.html")

---

### Post by corefile on 2007-11-27
> **Jere997 said:**
> I found out, actually its quite simple (Ubuntu 7.04 Feisty):
Right-click on volume control (next to the clock) -> "Open volume control"->"Preferences"->Check "Headphone Jack Sense"
Now there should be a new tab in the controls named "Switches". Go there and activate Jack Sense.
Works on my HP D530cmt.

hmmm... that looks like exactly what I said 2 post earlier

---

### Post by psamp14 on 2007-11-27
I tried right-clicking the Volume Control (next to clock) and the command posted a post or two above mine, but no avail.

I am using Ubuntu 7.10 on a Sony VAIO SZ650N/C, and the issue I have is that when I plug earphones into the headphones/earphones jack, the sound still comes out of the laptop's speakers.

How do I fix this? Any help will be greatly appreciated.

---

### Post by TorchlightJay on 2007-11-27
alsa-1.0.15 may do the trick. It did for me

---

### Post by albertotapia80 on 2008-03-06
thanks a lot guys, you have really made my day...   :guitar:

---

### Post by Astura on 2008-03-07
I too have this problem.

But for me, 
When I go to Open volume Control -> Preferences -> I get a window that has two check box's one says Master the other says PCM. 

Both the Master and PCM volumes may be adjusted, but both affect both the onboard speaker and the headphone volumes... muting one mutes the other, etc.

New Hp laptop
Fiesty

Help?


..This same problem is for ALSA also. The Master/PCM are all I can adjust.

---

### Post by monkeymind90 on 2008-03-11
Same problem here. I've tried installing alsa 1.0.16rc1 and its didn't do any good (although it did enable the mute touch button on my keyboard) and playing with the alsa mixer. I only have two output channels, PCM and Master, and no headphone jack sense. I also have a new HP (dv6700).

---

### Post by bixejo on 2008-03-11
> **monkeymind90 said:**
> Same problem here. I've tried installing alsa 1.0.16rc1 and its didn't do any good (although it did enable the mute touch button on my keyboard) and playing with the alsa mixer. I only have two output channels, PCM and Master, and no headphone jack sense. I also have a new HP (dv6700).

I also tried with alsa 1.0.16 with no success. Only alsa 1.0.15 solved the issue (don't know why, but looks like an older version is more capable to fix things than the new one).

In my case I also had to add the following line at the end of the file** /etc/modprobe.d/alsa-base**:

> options snd-hda-intel model=toshiba, because I'm using module **snd-hda-intel** in a Toshiba laptop (don't know whether this is your case too, but if so, maybe you should have a look at the section related to module snd-hda-intel in the file** /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz** that comes with package alsa-base. You will find there a list of options that should replace the word "toshiba" in the above quoted line.)

---

### Post by monkeymind90 on 2008-03-11
I tried the 1.0.15rc3 driver (with all the paraphernalia of course) with no luck. Any other ideas?

---

### Post by bixejo on 2008-03-12
> **monkeymind90 said:**
> I tried the 1.0.15rc3 driver (with all the paraphernalia of course) with no luck. Any other ideas?

Why did you use 1.0.15rc3 instead of the final version 1.0.15?

You may download it in the following URL's:

Driver:

> [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)Libs:

> [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)Utils and oss (not strictly necessary, I believe):

> [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
[ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.15.tar.bz2)If this does not work for you, I'm afraid I cannot do anything else for you. Make sure you follow carefully all the installation steps. And one more advice: when compiling, installing, etc., I would suggest you to get a true superuser shell instead of sudoing each step. In the case you don't have got root account enabled, which is the default in Ubuntu, you may still get the superuser shell by typing:

> yourlogin@yourhost$ **sudo bash**Good luck,

P.S.: One more note: check your PATH environment variable and make sure that all building commands (make, gcc, etc.) are taken from the default system installation, instead of some other sw that you may have installed before. I also got a problem with that, and got almost mad till I realized what was happening...

---

### Post by monkeymind90 on 2008-03-15
The 1.0.15 final build didn't seem to help. How do i check the PATH environment. I'm pretty new at this and I've never heard of it.

---

### Post by bixejo on 2008-03-15
> **monkeymind90 said:**
> The 1.0.15 final build didn't seem to help. How do i check the PATH environment. I'm pretty new at this and I've never heard of it.
If you don't know what I'm talking about, you probably shouldn't worry about this, as it's highly unlikely that your shell PATH gets changed unless you explicitly do so by editing the file .bashrc in your home directory.

Anyhow, just try the following in a terminal and check whether you get a similar output:

> 
bixejo@colmena:~$ [COLOR=Blue]**echo $PATH**[/COLOR]
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
bixejo@colmena:~$ [COLOR=Blue]**which make**[/COLOR]
/usr/bin/make
bixejo@colmena:~$ [COLOR=Blue]**which gcc**[/COLOR]
/usr/bin/gcc
bixejo@colmena:~$ 
Also, if you were able to be a bit more descriptive with the kind of problem you're getting now... Is it the same one you began this thread with? Maybe I (or someone else who knows much more than me) would be able to be more helpful.

---

### Post by monkeymind90 on 2008-03-16
The PATH environment was what you described.
And now for my symptoms:
I have a new HP dv6700 laptop. Since I installed Ubuntu I have not been able to get the headphones functioning without the internal speakers also on. There are no seperate controls, front jack/headphone jack doesn't show up in my alsa (all I have is PCM, Master, Digital, and Line In) and I have no option for headphone jack sense. I'm not really sure where to go to figure out more, but everything I have tried has been succesful (including playing with alsa, oss, editing alsa-base, and installing new a new curse program (which was recommended to me). So far my headphone jack is not even recognized. I would really like to be able to listen to music on my headphones. I have no problems with sound. When I plug headphones in I hear sound, but it cannot be adjusted seperately of the master.
If anyone has any ideas I'd love to hear them.
Thanks

---

### Post by bixejo on 2008-03-16
> **monkeymind90 said:**
> ...

In another thread I wrote a post trying to help another user with a problem quite similar to yours. You may have a look at this post [_here_]("http://ubuntuforums.org/showthread.php?p=4513122#post4513122").

Note that the second step described in that post may slightly vary for you if you are using a sound module other than snd-hda-intel. You may check your currently loaded sound modules by typing in a terminal:

> yourlogin@yourhost:~: [COLOR=Blue]lsmod | grep snd[/COLOR]Taking into account what's your sound module and also what's your sound card as reported by the aplay command (see my referenced post), you may find the right options you may set in your file **/etc/modprobe.d/alsa-base**.

Also, in that same thread you may find posts with other advices that may be helpful to you.

Good luck,

---

