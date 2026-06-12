---
title: "No Sound! Urgent!"
date: 2008-04-26
forum: Multimedia Software
---

### Post by Glucklich on 2008-04-26
I've read a lot of posts, on how to fix sound problems on laptops, but none of them did anything to my situation. Can anybody help me? I'm a first time Ubuntu user, version 8.40. Like i said, it's a Toshiba laptop. Intel sound card I think. Anybody have the time and the patience to help a newbie get out of this situation? I really miss my music.

---

### Post by Glucklich on 2008-04-27
Oh, c'mon. Nobody?
Please, somebody help me.

I've tried the comprehensible sound thing, but nothing. The system detects my sound card, but no sound at all! Please, somebody?
Oh, and it's not muted or anything of that stuff. All values are up and loud.

---

### Post by DukeNuke2 on 2008-04-27
can you give ssh access to your laptop? i just fixed my sound yesterday...

if no ssh access:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://wiki.ubuntuusers.de/Soundkarten_installieren/HDA](http://wiki.ubuntuusers.de/Soundkarten_installieren/HDA)

---

### Post by Glucklich on 2008-04-27
Oh yeah! Great suggestion. Check it out.

ayatollah@Etienne:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GS (rev a1)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

I don't see my soundcard listed. How do I get it back?

---

### Post by Glucklich on 2008-04-27
Oops, talked too soon. It's there.

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by unbuntued on 2008-04-27
> **Glucklich said:**
> I've read a lot of posts, on how to fix sound problems on laptops, but none of them did anything to my situation. Can anybody help me? I'm a first time Ubuntu user, version 8.40. Like i said, it's a Toshiba laptop. Intel sound card I think. Anybody have the time and the patience to help a newbie get out of this situation? I really miss my music.

I fixed a problem with my sound yesterday. Assuming your're using Hardy 8.04, the best solution I found is to compile alsa for your machine.

First make sure you have the alsa components installed, run the folowing in the terminal:
```
sudo apt-get install alsa-base alsa-utils gstreamer0.10-alsa
```

Execute the following to compile the alsa component:
```
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
```

Now run ```
sudo module-assistant
```
Follow the instructions. When you're over logout and then back in (or reboot).
This should do it for you.

---

### Post by Glucklich on 2008-04-27
When i do the last step, the "module-assistant" he gives this mensage.
   
 &#9474; You are not root and no replacement directory (the -u option) is   &#8593; 
     &#9474; specified. Unable to continue.   

Any guess?

---

### Post by DukeNuke2 on 2008-04-27
"sudo module-assistant" might do the trick...

---

### Post by ThinkDave on 2008-04-27
sudo module-assistant

---

### Post by Glucklich on 2008-04-27
Now it appears some menu. Do I need to do anything else?

---

### Post by DukeNuke2 on 2008-04-27
> **Glucklich said:**
> Now it appears some menu. Do I need to do anything else?

yes...

---

### Post by Glucklich on 2008-04-27
No, this is not the answer for my problem. I'm still soundless as a mule.
You think I should take all the steps again?

---

### Post by Glucklich on 2008-04-27
What do I need to do on the menu? I just rebooted. But? What do I have to do there?

---

### Post by Glucklich on 2008-04-27
Hello? Anybody out there? Please, help me. I am getting desperate. I am thankful for the previous suggestions, but it doesn't have seem to work. I still don't hear a thing.

---

### Post by Glucklich on 2008-04-27
ayatollah@Etienne:~$ aplay -l
**** Lista de Dispositivos de Hardware PLAYBACK ****
placa 0: Intel [HDA Intel], dispositivo 0: CONEXANT Analog [CONEXANT Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
placa 0: Intel [HDA Intel], dispositivo 1: Conexant Digital [Conexant Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
ayatollah@Etienne:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
ayatollah@Etienne:~$ amixer info
Card default 'Intel'/'HDA Intel at 0xb0000000 irq 21'
  Mixer name	: 'Conexant CX20551 (Waikiki)'
  Components	: 'HDA:14f15047'
  Controls      : 16
  Simple ctrls  : 9
ayatollah@Etienne:~$ 

It's all working fine, why don't I have sound?

---

### Post by DukeNuke2 on 2008-04-27
you never answered to my first reply...

---

### Post by Glucklich on 2008-04-27
I don't know what is ssh, or how I see if it is accessing my laptop or not. Can you help me with that?

---

### Post by ThinkDave on 2008-04-27
Gonna sound stupid but just gonna check... you have run alsamixer and checked that the main channels aren't muted? 
Also check the gnome sound preferences and test the drivers ie test alsa or oss. (System->Preferences->Audio)
Basic things but it may be a simple problem.

---

### Post by DukeNuke2 on 2008-04-27
> **Glucklich said:**
> I don't know what is ssh, or how I see if it is accessing my laptop or not. Can you help me with that?

so if you don't know about ssh, did you read the links i've provided?

---

### Post by Glucklich on 2008-04-27
Thanks Dave, but I've thought of that and the test thing, I've tested every stuff in every way. ALSA, OSS, Conexant, Auto-detect. No sound. There are no muted things, all volumes are in the maximum.
Any advise?

---

### Post by Patsoe on 2008-04-27
> **ThinkDave said:**
> Gonna sound stupid but just gonna check... you have run alsamixer and checked that the main channels aren't muted? 
Also check the gnome sound preferences and test the drivers ie test alsa or oss. (System->Preferences->Audio)
Basic things but it may be a simple problem.

^^ good points.

While I'm sure DukeNuke2 has all the best intentions, it's generally not a good idea to give people you don't know ssh access to your laptop...

---

### Post by DukeNuke2 on 2008-04-27
> **Patsoe said:**
> ^^ good points.

While I'm sure DukeNuke2 has all the best intentions, it's generally not a good idea to give people you don't know ssh access to your laptop...

but it's sometimes easier to do it by your own than to explain the thing... but he don't know ssh so there would be no remote work... but you are right! ssh for people you don't know isn't a good idea. but afaik this is a new installation and there should not be "secret" data on it yet...

---

### Post by Glucklich on 2008-04-27
The first one is the comprehensive sound trouble thing, but i didn't understood the second one since it is in German. But my Toshiba model is a Satellite P100-195. Does this information helps in any way?

---

### Post by jeffreyldavidson on 2008-04-27
I have a Dell 1420N with 7.10 preinstalled. When I upgraded to Hardy I also lost all sound. The hardware was not recognized. So I downloaded the Hardy ISO and did a complete fresh install wiping all else and when doing this the sound now now works fine. For some reason the upgrade removed the sound settings but a fresh install did the trick.

I will though do a reinstall when Dell provides its own ISO. The media buttons do not work now.

---

### Post by Glucklich on 2008-04-27
So what should i do? Reinstall everything again?

---

### Post by Glucklich on 2008-04-27
Please, somebody help me. Music plays an important role in my life. I owe to it so much... that it's absence is really making me nervous.
I installed yesterday Ubuntu, I like it very much. I've been thinking this through for a very long time, and finally did it. I'm very happy with it, but this sound thing, it is just unthinkable. I can't concentrate on my work without my music. I don't get anything about codes or that stuff, so please, can somebody help me?

As I said, nothing is muted on alsa in the console, it's none of that. In the system/sound, I've tryed every combination possible. The system detects the sound card. I've done the module-assistant thing. Nothing in the comprehensive list was any good. What's happening? I like Ubuntu, and I don't wanna give up on it.

---

### Post by Joshua Netterfield on 2008-04-27
The best way I have found to fix this problem is just to run alsaconf. Ubuntu doesn't include it, because it has a way cooler system which always works except for when it doesn't. Nice. We will need to install it ourselves.

1. Open up a terminal. (Applications->Accessories->Terminal)
2. Type "gedit ./alsaconf.sh" (without the quotes)
3. Go to [http://www.schugy.de/forenlinks/alsaconf](http://www.schugy.de/forenlinks/alsaconf), select everything (ctrl+a) and copy it (ctrl+c)
4. Go to the gedit window. Paste what you copied (ctrl+v)
5. Save it.
6. Go back to the terminal and run:
```
chmod +x ./alsaconf.sh
sudo ./alsaconf.sh
```
7. Follow the instructions
8. It should work. But it still might not...


"Chmod +x" makes the program runnable, and "sudo ./alsaconf.sh" runs it.
The script detects the sound cards that you have and gets them ready for use.

Good luck!

Edit: Oh ya. Source is [http://www.ubuntux.org/sound-card-not-detected](http://www.ubuntux.org/sound-card-not-detected) . You should thank them if it works (;

---

### Post by rjmdomingo2003 on 2008-04-27
Try this:

1. Open synaptic.

2. Choose linux-386 for installation.

3. Reboot.

Good luck! This worked for me.

---

### Post by Glucklich on 2008-04-27
Before i try Joshua's solution. RJ, where can I find the Synaptic thing?
Thank you in advance for both solutions, no matter what happens. It means a lot to me that people are trying to figure this thing out.

Edit: Nevermind, i found it. Going to install the thing. Let you know later.

---

### Post by Glucklich on 2008-04-27
RJ's solution didn't worked. Moving to Joshua's solution. Let's see...

---

### Post by Glucklich on 2008-04-27
No, still no sound at all. Thank you for your shot's at the problem.
But I dunno what is happening, but this is very weird.

---

### Post by Glucklich on 2008-04-27
Please, any more suggestions I can use? I got AutoCAD to work, Photoshop. Just missing the sound part, it would be a shame changing to windows just because of the sound.

Btw, is there any possibility that previous things could now be the problem? Just checking...

---

### Post by MaindotC on 2008-04-27
Did you try rebooting your computer?

---

### Post by Glucklich on 2008-04-27
Of course, after every procedure I've made. But just to be sure...

---

### Post by Glucklich on 2008-04-27
No, still no sound. Help? Please?

---

### Post by MaindotC on 2008-04-27
I'm not really in the position to advise this but if you just want to shoot from the hip you can try locating audio drivers and support in the repositories and adding them.  I can't imagine it would hurt your system to have more drivers than you need, but this is purely experimental.  Also, if you see an audio driver that is being used by your system, check out the add-ons associated with that driver.  For example, if you're using ALSA, do a sudo apt-cache search alsa and see if there are any additions you could add.

---

### Post by Glucklich on 2008-04-27
I must confess I'm not very comfortable with that procedure since I'm a newbie and I have no idea which could be a solution and which could be dangerous. In the forum is different, since you have other people looking out and if it could be a threat, they will advise you like it happened before.
But I don't know, I'm being left out of options. And it's a shame, I'm really enjoying Ubuntu.

---

### Post by MaindotC on 2008-04-27
Did you try all sound interfaces?  Sometimes there's a headphone interface as well as an audio-out interface.

---

### Post by Glucklich on 2008-04-27
In the System/Preferences/Sound? Yeah, tried every combination. Nothing. I'm curious about what I'm supposed to hear in the test thing. It certainly will be glorious!

---

### Post by steve8track on 2008-04-27
You should try googling your make and model of laptop to find out more specifics about the kind of soundcard it uses.   For example, mine says intel in lspci as well, but I have realtek sound, which only works with the latest alsa drivers.  When I was running 7.10, that meant I had to download and install them manually, but with 8.04 they came with the correct drivers.

Earlier when someone said to try "apt-cache search alsa" that is the same thing as:

System->Administration->Synaptic Package Manager
Then click search and search for alsa.

That software helps you automatically install in a list fashion.  Using "apt-cache search <search term here>" is to help you search for the software from the command line instead.  You can install in this software by checking the boxes and hitting apply, or from the command line type: "sudo apt-get install <name of software (package)>"

Also, "apt-cache search" doesn't need a sudo in front.  It's a good rule of thumb to not use sudo when not necessary, as it makes you have super user priveleges.  "sudo apt-get install" however requires the "sudo" to install software.

Also, ssh is to let someone remotely connect to your computer, which is only a good idea if you really trust the person or have the computer secured VERY well, since it give them access to your machine.

I hope this helps,

Steve

---

### Post by guj4_n3b3sk4 on 2008-04-27
And check this. Type:

```
alsamixer
```

to shell and check if any of lines is muted. Unmute them all, rise them to maximum and then check the sound.

---

### Post by Glucklich on 2008-04-27
Ok, I'll try to find more info about the soundcard. And about the "alsamixer" thing, I came across that in a couple of other posts and it's all up and not muted, so the problem is not there. Well, et you know when I have more info about the soundcard.

---

### Post by Glucklich on 2008-04-27
This was all I could find, and it's not much. It has almost 2 years old, so it's not easy to find good info about it. But I think it's an Intel On Board. Because on the audio section they only talk about the speakers. But here's the site:
[Toshiba Portuguese Site, Information about the Satellite P100-195]("http://pt.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=PT&toshibaShop=false&com.broadvision.session.new=Yes&PRODUCT_ID=116623")
(If you put it to Babel Fish, altifalantes means speakers.)

Any good?

---

### Post by Glucklich on 2008-04-27
Please? Can anybody help me?

---

### Post by Glucklich on 2008-04-28
C'mon people, please don't give up on this.

---

### Post by jet200 on 2008-04-28
Mate Im also in the same situation as you :(, but the only difference is that my laptop ia ASUS f3sg.

---

### Post by presston on 2008-04-28
i have the same problem too, and post it in 4(!!!) forums in english or russian. no answer, no resolve. nothing. no people who can help.

and it after 5 times of compilation and installing alsa from different resources and etc. sad :(

---

### Post by Cannaregio on 2008-04-28
For what it is worth, here is how I solved my own sound problems on a sony vaio with a INTEL 82801DB. 
Sound disappeared totally when updating to Hardy from Gutsy.
Tried many modifications (adding a line at the end of /etc/modprobe.d/alsa-base along the lines of options snd-hda-intel model=xyz etcetera), didn't work.
What worked was adding users (and myself) to the pulse groups. (and restarting !!)

So go to System --> Administration --> Users and groups
Manage groups, unlock and choose properties for each pulse group.
Then add all the users that should have sound.
Then restart/reboot.

Hope it helps. It helped me!

Why the installation did not add users by default beats me.

---

### Post by Glucklich on 2008-04-28
It's good to know that it's not an isolated case, and sad that it is happening. We need to keep this topic alive so we can get some attention of the experts for the tracking and solution of the problem. So, I would like to ask you to keep an eye on this. Share your experiences as new solutions are brought up and help where ever we can.
There must be some common ground between our cases for this to be happening. I'm not an expert in computing, so I'm gonna stick to a conceptual level, trying to help the more experienced people to track something or maybe give ideas for a possible solution.

Can this be a problem in the way this particular motherboard interacts with the sound card? I dunno, like I said, I don't know anything on the subject. I just want to start an constructive discussion on the subject so that we can develop Ubuntu and minimize this kind of problems, seen that this until now is an old problem coming in a new way.

---

### Post by presston on 2008-04-28
maybe some linux-man after our posts will write resl comlete HOWTO solution for this problem (not like it are now)

---

### Post by presston on 2008-04-28
YYEEEEAAAAAAAH. i've done it.  

1. compiling fresh alsa from sources
2. edit files (by hands :) ):
*/etc/modules.conf
*/etc/asound.conf 
*/etc/modprobe.d/alsa-base

[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0)

can give listing of those files

---

### Post by Glucklich on 2008-04-28
Can you explain in more detail what you've done? Please, I didn't understood what you've done.

---

### Post by presston on 2008-04-28
yeah) 
1. go here  [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)    
do ALL steps before line
> **Manually Specify Module Parameters**
2. in terminal
> sudo bash
that give root rights
3. in terminal
> gedit /etc/modules.conf
if it not exists - it will be create
in this file i wrote

> fuse
lp
snd-intel8x0
snd-pcm-oss
snd-mixer-oss
snd-seq-oss

 # ALSA portion
       alias snd-card-0 snd-hda-intel
       alias snd-card-1 snd-cmipci
       options snd-cmipci id="first" mpu_port=0x330
       
       # OSS/Free portion
       alias sound-slot-0 snd-card-0
       alias sound-slot-1 snd-card-1

# OSS/Free portion - card #1
       alias sound-slot-0 snd-card-0
       alias sound-service-0-0 snd-mixer-oss
       alias sound-service-0-1 snd-seq-oss
       alias sound-service-0-3 snd-pcm-oss
       alias sound-service-0-8 snd-seq-oss
       alias sound-service-0-12 snd-pcm-oss
       
       # OSS/Free portion - card #2 (cmipci)
       alias sound-slot-1 snd-card-1
       alias sound-service-1-0 snd-mixer-oss
       alias sound-service-1-3 snd-pcm-oss
       alias sound-service-1-12 snd-pcm-oss

this is for my card AD1985, but i think it will be apply for you too. save it.
4.in terminal
> gedit /etc/asound.conf

text:
> pcm.intel8x0 {
          type hw
          card 0
       }
       
       ctl.intel8x0 {
          type hw
          card 0
       }

save it.

5. in terminal 
> /etc/modprobe.d/alsa-base

in the end add lines
> options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=**asus**

in this case you must select bolt parameter from 
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)
or
[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0)

save it
6.reboot
7.in system - preference - sound
in all select alsa
8.in all your players and application you must select alsa for sound output

---

### Post by Glucklich on 2008-04-28
Dude, I can't wait to try this. This is our sound card. Awesome!

---

### Post by mormor on 2008-04-28
Saved my day: )

---

### Post by gavinjb on 2008-04-28
Hi,

Not sure if anyone can help as I am having a similar problem, I have a Dell Inspiron 1525 and I have gone onto Dells website and followed there how to to get sound to work after upgrading to 8.04, but that didn't work ([http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade)) I have also tried various things form this forum, and have so far managed to get my sound card recorgnized, but get the following errors when trying to test the card:

```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect stream: Invalid argument

```

Also this is the details I get from lspci | grep -i audio
```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```

and this from running aplay -l
```

**** List of PLAYBACK Hardware Devices ****

```

I did try some of the examples on this topic to do with module-assistant but it didn't have much success (I did manage to kill grub, not sure how and that gave me a heart attack until I worked out how to restore with live CD)

I have also just tried using the HdaIntelSoundHowTo but when I get to sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)

I get the following error:

```
checking for which soundcards to compile driver for... Unknown soundcard hda-intel, exiting!

```

Can anyone help.

Thanks,

---

### Post by Glucklich on 2008-04-28
root@Etienne:~# /etc/modprobe.d/alsa-base
bash: /etc/modprobe.d/alsa-base: Permissão negada

"Permissão negada" means "Permission denied". What happened? Did I do something wrong?

---

### Post by Glucklich on 2008-04-28
Gav, I have a link that can be more useful for your sound card. I don't know if it will help, but... here it goes:

[https://bugs.launchpad.net/ubuntu/+bug/122560]("https://bugs.launchpad.net/ubuntu/+bug/122560")


Edit: It really is helpful for your case, check the end of the page. A guy has a similar laptop to yours. According to him he worked it out by doing something like this:


 Mario Carrión wrote on 2008-03-20: (permalink)

I've fixed the sound problem on my Dell Inspiron 1420 running Hardy and adding the following to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=dell-m26


Hope this helps you, since I find no end for my situation.

---

### Post by Glucklich on 2008-04-28
Please, help me. Why does this message appears?


root@Etienne:~# /etc/modprobe.d/alsa-base
bash: /etc/modprobe.d/alsa-base: Permissão negada

"Permissão negada" means "Permission denied".

---

### Post by salvador_luna on 2008-04-28
Well, I'm not an expert but maybe you must write "sudo gedit" before /etc/modprobe.d/alsa-base (i think this is a file), so the comand in terminal shoud look like this:

sudo gedit /etc/modprobe.d/alsa-base

Sorry abaout my english, my native language is spanish :D

---

### Post by Glucklich on 2008-04-28
Thank you very much Salvador. That was it :P

Now, I have a doubt. Which "formula" must I use for this sound card:

[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel")

and for this one:

[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0]("http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0")

One of this two has got to be.

The end of my present "/etc/modprobe.d/alsa-base" looks something like this right now:
> options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=auto
And by the way, it doesn't work.

---

### Post by Glucklich on 2008-04-28
C'mon people, just a little more patience please. I'll be settled for life with this, I got Autocad working, Photoshop working... Gee, what else do I need besides a good old fashion freeware render program? 
I promise I won't be bothering anymore, with all the newbie stuff.

What are the alternative endings for the "/etc/modprobe.d/alsa-base" for that two soundcard possibilities I said in the previous post? 
Or which one is more likely my soundcard?

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by Apocalypse on 2008-04-28
Try "laptop"

My Toshiba Satellite L45 finally worked "well" with that value.

BTW, a very sincere THANK YOU to Presston. Without your guide, I'd still be using a venerable walkman with fm and external speakers...=)

---

### Post by novus721 on 2008-04-28
Hey all - I have a weird problem, I have been trying to get my sound working, and I have had no success.

Here's the thing - when I originally boot into ubuntu at the login screen, I hear the drums beat. However, my load hangs for awhile before it fully loads, and then I have no sound in my computer after the login screen. 

The weird part is, when I go System>Prefs>Sound I hear the beeps from all the test sounds with all options put to ALSA. I hear the tests, but I dont hear anything when I play normal files!

Any ideas? Thank you in advance!!:confused:

---

### Post by Glucklich on 2008-04-28
After trying Presston's solution, and what appeared to be another failed solution, in a random act of desperation, I laid my head very near to the speakers. And I hear it, MUSIC! Almost inaudible, but it was there. Could it be that the problem was never the sound card but the fact that it is on a very veeeery low level and I never heard it? Well, anyway... I'm glad that this topic helped a lot of people to get their sound back.

But now I've got another problem, how to bring my sound up. I've done a little research and tried the "options snd-hda-intel model=3stack" thing, but it did nothing. What can be wrong? What should I do?

Edit: Novus, can it be your player's output? It's just an idea, as you've might notice I'm not the best person to give advises.

---

### Post by salvador_luna on 2008-04-28
Glucklich: about your doubt, let me do a little research (i did not have this problem so i'm not use to this commands). It's the only way i can help you right now.

Novus721: What do you mean with "normal files"?

---

### Post by laser_in_your_eye on 2008-04-28
Hey Glucklich,

I had the same problem and tried the suggestion to add myself to the pulse groups (in users and groups).  After reboot I thought my audio was still not working, but then I noticed that there was something faint coming out of my speakers.  I then opened the volume control and increased the PCM volume and master volume and...I finally have sound.

Don't know if this will help, but I feel your pain.

---

### Post by tuskpc on 2008-04-28
I have had more issues with this topic than I care to recall.  On a positive note, I learned it was not Ubuntu's fault, but instead the blame goes to shoddy coding done by my laptop manufacturers (1).  

Anyway, have you tried something as simple as typing this:
<terminal>$ sudo alsaconf

I tried this and it fixed the strange sounds.  On the other hand, I upgraded my laptop so the config files where already working.  I'm curious if that will work for you though?



(1) Toshiba Satellite P105-S6147

---

### Post by novus721 on 2008-04-29
> **salvador_luna said:**
> 

Novus721: What do you mean with "normal files"?

I mean any normal video or audio file, regardless of file type. I just dont understand how the test sounds can give me a "beep" while normal files don't work at all. Thanks for the help.

---

### Post by Cannaregio on 2008-04-29
I'll repeat what I already stated, maybe you could try it:

> **Cannaregio said:**
> 
What worked was adding users (and myself) to the pulse groups. (and restarting !!)

So go to System --> Administration --> Users and groups
Manage groups, unlock and choose properties for each pulse group.
Then add all the users that should have sound.
Then restart/reboot.

Adding that [COLOR="Blue"]you need to check your volume[/COLOR] after restarting or rebooting: I found my new settings extremely low :-)

Again, why on earth users are not automatically adedd to the pulse groups during hardy installation totally beats me

---

### Post by novus721 on 2008-04-29
I already tried the pulse thing, I have both my username and root selected under the properties.

Again, I have sound at my login screen, but I do not have it after - so something has to load in the meantime, but what could be loading?

---

### Post by novus721 on 2008-04-29
Just found this out - I can get audio from anything played through firefox, but no files off of my computer! (mp3, avi, etc) Any ideas?!?!

---

### Post by presston on 2008-04-29
> **Glucklich said:**
> Thank you very much Salvador. That was it :P

Now, I have a doubt. Which "formula" must I use for this sound card:

[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel")

and for this one:

[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0]("http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0")

One of this two has got to be.

The end of my present "/etc/modprobe.d/alsa-base" looks something like this right now:
...
And by the way, it doesn't work.

hey :)

**auto** parametr did not work for me to. the same was with 3stack, 4stack etc.

and i tried ASUS (for motherboard) manufacturer. and it works!! try differenr variants. all other my solutions was right for intel8x0 - 100%

---

### Post by Glucklich on 2008-04-29
I'm very thankful for all your help and for trying to figure this thing out, it really means a lot for me, but none of the suggestions worked out.
I added myself and root for all the pulse groups, I've tried in the alsa-base config "laptop", "toshiba", "auto", and all the values are up, including PCM and all on that part, and all the volumes in alsamixer are up and unmuted. I've tried the alsaconf one too. The sound stills very very low.
Man, am I getting to a dead end or what? If it wasn't for my discman I had gone mental in the first two days.
What can be the problem here? How can I fix this?

---

### Post by presston on 2008-04-29
when i setuped ubuntu first time i knew than i'll have a loooooot of problems. and it is:)  but i knew what are waiting for me)

be stubborn :)

about you&#1082; sound. only 3 variants in can be:
1.alsa-base config
2.modules config
3.asound config

thats all. no others. i think that problem is in alsa-base. IMHO.

try asus, basic , dell .. try try  .. there are a lot of variants of that parametr

---

### Post by presston on 2008-04-29
by the way

[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

FULL list of sound cards and their parametrs

---

### Post by Glucklich on 2008-04-29
Well... If that is my only option right now, that's what I'll do. I'll begin trying every code for the Intel HD Audio. By the way, thats mine isn't it? That's the line I should be trying isn't it?
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Meanwhile, I would like to keep this open for everybody who has a suggestion that hasn't been used yet. Please, if you have any suggestion that hasn't been tried yet let me know. Thank you very much for all your support.

---

### Post by gavinjb on 2008-04-29
> **Glucklich said:**
> Gav, I have a link that can be more useful for your sound card. I don't know if it will help, but... here it goes:

[https://bugs.launchpad.net/ubuntu/+bug/122560]("https://bugs.launchpad.net/ubuntu/+bug/122560")


Edit: It really is helpful for your case, check the end of the page. A guy has a similar laptop to yours. According to him he worked it out by doing something like this:


 Mario Carrión wrote on 2008-03-20: (permalink)

I've fixed the sound problem on my Dell Inspiron 1420 running Hardy and adding the following to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=dell-m26


Hope this helps you, since I find no end for my situation.

Hi, thanks for the link unfortunately it didn't work, the one thing I have noticed is that when I log into Live CD I get sound (it doesn't seem as loud as with 7.10, but that might just be me) and that the volume Control gives me sliders for Master, PCM & Front while booting from HD I only get a PCM control, I had looked at the settings on control panel and the other options are not there.  This makes me think that it is trying to use the wrong driver

I have even copied the alsa-base from the live CD to a memory stick and compared and it doesn't use any of the options snd-hda-intel model=dell-m26 type settings for this card.

It seems that there is an issue with the upgrade tool for 8.04 as a clean install seems to fix these issues, but I am reluctant to do this, as dell have my Pc configured to work with the extras buttons etc... plus I get LinDVD on the image.

Gavin,

---

### Post by presston on 2008-04-29
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

that is commom name of this audio cards. what is it model particularly?

AC'97 or AD1986 etc

---

### Post by Glucklich on 2008-04-29
I don't know Presston. How can I get that info? I already tried to get more info on the board but I can't find it. The only site that could give me this info was Toshiba Portugal, but it has no info about the soundcard, just the usual salesmen crap-talk.

---

### Post by RossAndGarfunkel on 2008-04-29
> **Glucklich said:**
> I don't know Presston. How can I get that info? I already tried to get more info on the board but I can't find it. The only site that could give me this info was Toshiba Portugal, but it has no info about the soundcard, just the usual salesmen crap-talk.

I still haven't found a fix either. :/

---

### Post by presston on 2008-04-29
> **Glucklich said:**
> I don't know Presston. How can I get that info? I already tried to get more info on the board but I can't find it. The only site that could give me this info was Toshiba Portugal, but it has no info about the soundcard, just the usual salesmen crap-talk.


give my full name of your notebook

---

### Post by Glucklich on 2008-04-29
It's a Toshiba Satellite P100-195. Any luck finding the specifics of the soundcard?
Here's the site I was talking about.
[Toshiba Portuguese Site, Information about the Satellite P100-195]("http://pt.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=PT&toshibaShop=false&com.broadvision.session.new=Yes&PRODUCT_ID=116623")
If the online translators don't work very well and need translation on a word, I can help you with that.

---

### Post by novus721 on 2008-04-29
Just out of curiosity, does anyone else have a SBLive! CT4871 card that had this problem?

My card is listed, but all I get now for sound is loud static.

---

### Post by presston on 2008-04-29
[http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_P100](http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_P100)

---

### Post by Glucklich on 2008-04-29
So, the problem could be my BIOS?
Gee, I wish I had seen that site before I installed Ubuntu. Express Media Player blown away.

---

### Post by Glucklich on 2008-04-29
It doesn't make any sense. He says that he's using 2.40 BIOS with 2.6.24 Kernel. Wait a minute, how do I know my kernel version? Since my ALSA is the latest one.

---

### Post by free2useemail on 2008-04-29
DO YOU HAVE EVERYTHING HOOKED UP!! It might be a sound driver. Run the update manager, it might download a sound driver. Otherwise, you need to search for a sound driver for ubuntu. This is odd though, sound should just work right out of the box.

---

### Post by presston on 2008-04-29
besides, did you all turn up to maximum in alsamixer?

---

### Post by Glucklich on 2008-04-29
Of course I did, that was the third thing I did. And just for the doubt, I've checked it again and it's in the max. Alsamixer, all maximum, none muted.

Free, run the update manager in the Synaptic? I've done that today in the morning. Nothing. Still the same.

I'm going to pursue the BIOS theory.

---

### Post by presston on 2008-04-29
i dont not what to advice to you now ... sorry:)

---

### Post by Glucklich on 2008-04-29
Stupid question time:
How do I know if my OS is a 32 or a 64 Bit? I used to go to the preferences in windows whenever I had this silly doubt... but, I can't find it in Ubuntu. How can I know this little detail that I need to upgrade my BIOS.

---

### Post by austin1030 on 2008-04-29
> **rjmdomingo2003 said:**
> Try this:

1. Open synaptic.

2. Choose linux-386 for installation.

3. Reboot.

Good luck! This worked for me.

Oh yeah! this one got my problem solved.

thanks for tip

---

### Post by Gunman1982 on 2008-04-29
> **Glucklich said:**
> Stupid question time:
How do I know if my OS is a 32 or a 64 Bit? I used to go to the preferences in windows whenever I had this silly doubt... but, I can't find it in Ubuntu. How can I know this little detail that I need to upgrade my BIOS.

I would say the easiest way is to open a console and execute
cat /proc/version
that tells you what kernel you are running. If its a 64bit kernel it should tell you somehwere in the text.

---

### Post by smokedByGlasnost on 2008-04-29
> **Glucklich said:**
> I added myself and root for all the pulse groups, I've tried in the alsa-base config "laptop", "toshiba", "auto", and all the values are up, including PCM and all on that part, and all the volumes in alsamixer are up and unmuted. I've tried the alsaconf one too. The sound stills very very low.
...
What can be the problem here? How can I fix this?

I had the same problem after upgrading one of my computers to Hardy Heron. Since the issue was very low volume, I opened alsamixer to see if any of the lines had been set unreasonably low. Sure enough, alsamixer showed the bar for 'PCM' was set almost to zero. I raised it, and enjoyed glorious, audible sound.

Take a look. If not PCM, maybe it's something else.

Edit: Just noticed you mentioned your alsamixer settings in a later post. Sorry, guess this isn't it.

---

### Post by MaindotC on 2008-04-30
> **Glucklich said:**
> It doesn't make any sense. He says that he's using 2.40 BIOS with 2.6.24 Kernel. Wait a minute, how do I know my kernel version? Since my ALSA is the latest one.

When you start the computer, it usually shows a screen called the GRUB bootloader and should prompt you to select the operating system unless Ubuntu is the default and it will boot into Ubuntu automatically.  On this screen, it will say the kernel version.

You can also type in a command prompt (and here's my output):

```

mamour@45fdss43sastr43:~$ uname -r
2.6.24-16-generic
mamour@45fdss43sastr43:~$

```

Keep after it man - we're rooting for you!

---

### Post by novus721 on 2008-04-30
I just fixed (I think) my own problem, and I am posting it for everyone else.

I had loud static sound coming from my speakers, and it finally went away when I went to System>Prefs>Volume Control>Switches(tab) and unchecked my output jack. Ever since then everything has worked fine, and I can play multiple sound files off different platforms at the same time. 

Also, my sound prefs are all under PulseAudio, I don't know how much that impacts it.

Hope this helps someone.

---

### Post by salvador_luna on 2008-04-30
I wonder if you tried this

[http://ubuntuforums.org/showthread.php?t=205449&highlight=82801G+Sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=82801G+Sound)

and this

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Look at this section in the first one:


Miscellaneous Tips and Tricks

Here are a few things that other people have dug up over the course of this guide. Not all tips are meant to work for all hardware (believe me hda-intel will probably have like a mini guide of it's own one day).

    * shaviro found the following from this post [http://www.ubuntuforums.org/showthread.php?t=153752](http://www.ubuntuforums.org/showthread.php?t=153752)

Quote:
I wasn't getting any sound out of my Sony Vaio PCG-4B1L ...
Quote:
The crucial thing is to enable everything in alsamixer EXCEPT "external amplifier." (I had to turn off microphone too, to stop feedback).

---

### Post by Glucklich on 2008-04-30
Time for a "not so stupid, but still a bit stupid" question:
How do I install the BIOS .exe file I got from Toshiba's site? It gave me an error while using wine. Any other way to go around it?

---

### Post by presston on 2008-04-30
at my opinion you must have (or get)  MS DOS bootable dissket (3.5").

or this bios.exe make such himself

---

### Post by Glucklich on 2008-04-30
Presston, it's a laptop. Ain't no diskette thing. 
What was the other solution you were talking about?
Wait... I had an idea. This .exe should be on windows xp, so... could any of that things like VistualBox could work? i don't know how to work it out, but... could that work?

---

### Post by MaindotC on 2008-04-30
Yeah it's  a laptop - you DO have a cd-rom drive don't you?

---

### Post by Glucklich on 2008-04-30
So I could update the BIOS by burning the .exe into a CD and boot from it? Cool. That's what I'm going to try now. Or it doesn't work taht way?

---

### Post by Glucklich on 2008-05-01
Will it work if I burn a CD with the .exe in it and boot from the disk?

---

### Post by Glucklich on 2008-05-01
Wow, I am f*cked now? I can't upgrade the BIOS!
I burned the disc, but it didn't boot from the disc, how do I do it? Please, I really miss my music.

---

### Post by presston on 2008-05-01
execute EXE on hard drive. he must unpack himself

---

### Post by DukeNuke2 on 2008-05-01
you have absolutly no knowledge on computer hard- and software, didn't you? better get some help from a friend or a dealer next to you before anything get damaged... you can't burn an *.exe file and boot from that. you need a bootimage AND the *.exe file to make a bottable cdrom and execute the file after booting.
and you should start using a search engine... this is the first hit from google after searching for: "how to create a bootcd"

[http://www.hardwaresecrets.com/article/75](http://www.hardwaresecrets.com/article/75)

after enter "linux" as search word also, you get a step-by-step howto for building a motherboard flash cd on linux.

[http://www.nenie.org/misc/flashbootcd.html](http://www.nenie.org/misc/flashbootcd.html)

start searching the web on your own. if you want get things done... just do it!

some small help to point you in the right direction is ok, but hey, it seems you've done nothing on your own.

---

### Post by MaindotC on 2008-05-01
I'm sorry for advising you to burn it to a cd - if you do it from a windoze environment that should be perfectly fine.  For some reason I thought you couldn't even boot up your machine.  Just run the .exe while you're in windoze.

---

### Post by Glucklich on 2008-05-01
Duke, if I had any experience, I wouldn't be asking for help, won't you think? Maybe I've dedicated most of the time in my life in another subjects, subjects that you might not be as comfortable as you are in computers. And if you had any interest or doubt about them I would be very glad to help you. That's why the sharing of information is so important, and that's why the internet is a powerful source of information.
I've searched every where on a way to solve this problem, but like every outsider on computer issues, I have a problem in knowing what is pertinent and non-pertinent. With Presston and StrAlan's help I came to conclusion that the problem could be in my BIOS, since I never updated it and it's a relatively old laptop. But, I don't know how to do it, and yes, I'm very afraid of messing it up. That's why I'm being extra careful about the sources and posting more posts that any other users would ever do, because I have to be sure that what I'm doing is the right way to do it.
I'm very thankful for you tip, but if I had a friend I could ask for help, I would, but I don't have cause none of them uses Linux. All are passive computer users, just like me. But the reason I decided to take this way is because I've read a few things that convince me going on Linux. The main one being freedom, one of the values I most treasure on this World, not just for me but for all computer users. That's why I've stepped out of my windows passive conformity and joined your cause. And most important of all, the reason I've not yet uninstalled Linux, it's because I really believe in this cause. So, if you are open to help me without any judgment on my personality or experience on this issue, I would appreciate it very much. But if you are going to start playing the newbie card on me, just keep it to yourself please.

---

### Post by MaindotC on 2008-05-01
Glucklich - you'll have this arguement with everyone on a Linux forum - either don't waste your time or keep your post as a template.  It's just how Linux is.

However, it is very important to lay a foundation for developing a methodology to solving problems and although I think Duke's initial comment in the previous post may be a little harsh, I believe we all have your best interests in mind.

I'm actually of a different philosophy - people can ask me the same question or an obvious question a million times and I'll just keep answering it or if I can't I'll at least give them a direction to start - but that's just me.  I feel it will help people better embrace Ubuntu (moreso Linux) which arguably may be better for humanity (like the above reasons you mentioned).

Were you able to upgrade the BIOS ?

---

### Post by DukeNuke2 on 2008-05-01
Glucklich - Yes. i'm deep in the IT... I can see from your replies that you are not. But i would never call you names... Not noob or something like that! But it's allways the same thing. People buy IT products and try to work with the new thing. in most households the computer is the most complex thing around and the people try to work it out on their own. Nobody would to something like that with the tv or the stereo unless they know what to do! Why isn't it the same with a computer?
My problem with that is:
every time you explain something to someone you need some basics to do the taks. And everytime these basics are missing. So we need to go deeper and deeper and deeper... And we won't come near to solve your "no sound" problem.
I allredy offered the SSH remote admin option to you and wouldn't mind to take a look at your laptop from remote... Sure, this is an security problem if i'm into something nasty. But something like this IS my job and i'm also glad to help. So you need to trust the remote guy or fix the problem on your own (or with the help of the other guys around here).

EOF

@strAlan:
Yes, it was a bit harsh ;)

---

### Post by MaindotC on 2008-05-01
He knows he's noob - I think he's cool w/ that :-p  I am too for f's sakes but I do what I can.  Waiting to see if the flash worked alright...

---

### Post by qgfreire on 2008-05-01
See [http://ubuntuforums.org/showthread.php?t=773613&page=2](http://ubuntuforums.org/showthread.php?t=773613&page=2) #20
Perhaps is the same prob.

;-)

---

### Post by Glucklich on 2008-05-01
Thanks for all your support guys, I'm very grateful for what y'all have been doing.
I only now got VirtualBox to work, it's installed XP right now. And well, here's a thing I didn't missed at all.
But, I have a doubt, when I install the BIOS update on XP, it will be available for all my system, right? Not for only the partition I've created., right? Just to be sure.

---

### Post by MaindotC on 2008-05-01
Yes the BIOS is something dealing with the hardware and not the operating system controlling the hardware.  In this instance, I will speculate that the manufacturer only made a BIOS upgrade program that is executable from Windows because they assume the only people that will need to upgrade the BIOS will be users of a Windows system OR it would cost them too much money to figure out how to compile the source code into a Linux binary.  It's pretty common for companies that release BIOS upgrades.

Also, typically BIOS upgrade packages usually come with a version of DOS so when you put in the CD or floopy and boot the computer, assuming you tell the computer to boot from the CD or floppy first, it will check the CD for the presence of an operating and it will find DOS and begin to run whatever commands are on the disk.  Keep us updated!

---

### Post by guildofghostwriters on 2008-05-01
Did you manage to solve this? I had a no sound problem when I first installed and although it took a while to find a solution, in the end it was really simple. I notice that you mention you've used alsamixer and that you have everything unmuted and turned up to full. In the end my solution was to make sure the control called "Analog/Digital Output Jack" was muted - it wasn't a volume slider, just a mute control. As soon as I muted that I had sound. Sorry if that doesn't help, or if you've encountered that on one of the many other pages linked to (no time to read them all), best of luck finding a solution!

---

### Post by Glucklich on 2008-05-02
I can't seem to get Shared Files between Ubuntu and the VirtualBox's XP. Despite I've done everything like it was on the manual. When I do "net use x: \\vboxsvr\pasta" it just shows me a crazy thing, like "error 53". 
Yeah, I really missed the good old windows.
Any idea of what it could be? Never really understood how networking works in Windows, despite I by mistake, got my Internet connections right.

---

### Post by Glucklich on 2008-05-02
Oh, sorry. What it says is: "An error has occurred in system 53" or something like that. I'm translating it from Portuguese to English so the words might not be exactly like this, but that's the general idea.

---

### Post by spsk11india on 2008-05-02
The following suggestion at [https://answers.launchpad.net/ubuntu/+question/20748](https://answers.launchpad.net/ubuntu/+question/20748) 
worked for my 7.10 Ubuntu. You can try it:

sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.bak
This is just to keep backup, in case sumthng goes wrong.

sudo gedit /etc/modprobe.d/alsa-base
This will open up a file in the text editor.
Append to the end of this file the following line:
options snd-hda-intel position_fix=1 model=3stack

Save and exit. Restart and retry.
:popcorn:

---

### Post by Glucklich on 2008-05-02
Thanks for the suggestion spsk. I'm very glad it worked out for me but I really can't say the same about me. The sound is still very low.
I'm betting on this BIOS thing, and I find it very probable. But right now I need to transfer files from my system into the VirtualBox's XP. It gave that strange error I reported earlier, do you have any thoughts on that? Or alternative ways do get the files through so I can install the BIOS update?
Once again, thanks for your try. It means a lot to me.

Edit: Got my solution here, for anyone following the steps on this and had the same problem. 
[http://ubuntuforums.org/showthread.php?t=616605&highlight=virtualbox+sharing+files+problem]("http://ubuntuforums.org/showthread.php?t=616605&highlight=virtualbox+sharing+files+problem")

---

### Post by Glucklich on 2008-05-02
Now I realize why it is giving me that error.
Check this out when I try to install the Guest Modules on VirtualBox:

FATAL: Error inserting vboxadd (lib/modules/2.6.24-16-386/misc/vboxadd.ko) : No such device

What does this mean?

---

### Post by Glucklich on 2008-05-02
Oh, I forgot. The error happens when I try to install:
virtualbox-ose-guest-modules- 24

Any suggestions on what this could be? Please.

---

### Post by MaindotC on 2008-05-02
First of all, did you do the BIOS update/

---

### Post by Glucklich on 2008-05-02
I didn't, I needed to get to a windows environment so I could update the BIOS. Wasn't that what you tried to tell me?
For I to get the .exe file to the VirtualBox's XP, I needed to get the Sharing thing working. And now I got it. 
Next step, update the BIOS :P

Edit: Did I got it all wrong?

---

### Post by MaindotC on 2008-05-02
I would have just burned the .exe to disk with an installation of a DOS environment, but if you want to do the virtualbox thing then I guess so.  You see, updating the BIOS shouldn't require a hard drive.  Oh well however you do it just please get it done and tell us the results.  I updated the BIOS on my ABIT AV8 motherboard and it has been crippled ever since so hopefully it won't turn out that way for you.

---

### Post by Glucklich on 2008-05-02
The .exe file seems not to be working. Is it normal or it's just taking it's time?
Maybe I'll follow the bootcd path. I just didn't want to f*ck anything up, and with this way, I thought I had a BIOS back up. Well, here goes nothing.

Edit: Well, it's a Toshiba BIOS upgrade they had on their site. In case of any trouble I'll just go to the store and rant with them, I think it's still on warranty period :P

---

### Post by Glucklich on 2008-05-02
New developments on this story of epic proportions to the greatest newbie of all times.
The good news is that the BIOS is in version 1.70. Not bad hum? This really might be the problem we were looking for. Still in the good news, bootcd taken care of. With Duke's lead, I was able to make a bootcd and add the .exe provided by the manufacturer.
The not so good news, when I boot from it. It does what it is supposed to. Get me to DOS. It shows me the presence of an A: and R: drives, and took me to the A: one. It does something and asks me to press a key. I press it and then it comes alone with the A: thing. Now, I remembered an old command from the time I owned an Armstrong that was 'dir' and it showed me all the files. Those were:
COMMAND COM; CD1 SYS; AUTOEXEC BAT; CONFIG SYS; MSCDEX EXE.
I give him the order to execture the mscdex.exe, and he says that it's already being executed, but nothing is really happening. What should I do or what did I do wrong? Should I look for files whiting the manufacturer's .exe?

---

### Post by Glucklich on 2008-05-02
Here's the manufacturer's BIOS update file.
[Toshiba Portugal, BIOS Update for the P100-195]("http://pt.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/download_drivers_bios.jsp?service=PT")
If someone has the patience to check what I should do with it, please let me know. Because when I'm in the OS it opens an app called WinPhlash. Was that the reason I could not get the bootcd to update my BIOS?

---

### Post by pandorazboxx on 2008-05-02
I think I am having similar issues with my sound card. I have a Creative Labs Audigy Soundblaster LS. and the device name is sb0312. but that driver is not on the list that was referenced in the sound troubleshooting website from the first page. Has anyone found a driver for this card?

---

### Post by MaindotC on 2008-05-03
Dude the toshiba site you gave me is all in a non-english language :( Sec while I try and figure it out.

Some BIOS updates can be run from the operating system, as I mentioned earlier it seems the .exe was written for windows, and the WihPhlash utility may be able to do that.  If you have Award Bios it's usually a program called awflash.exe, and Phoenix Bios has some other utility.  If you are able to access the windoze environment from virtualbox, try running the WinPhlash.exe.

However, I'm not sure how virtual machines work but I'm thinking that will flash the virtual bios, not the real one.  Is that so?

---

### Post by MaindotC on 2008-05-03
I'm having trouble finding your model.  Tell me what options you are selecting.  I'm using the same url you posted but I replaced the beginning "pt" with a "uk" so I can get engrish.  Here is what I chose so tell me if I'm close:

Product Type: Notebooks
Family: Satellite
Series: Satellite P Series

And from there I had difficulty finding anything that said P100-195.

---

### Post by roma2 on 2008-05-03
> **Glucklich said:**
> Time for a "not so stupid, but still a bit stupid" question:
How do I install the BIOS .exe file I got from Toshiba's site? It gave me an error while using wine. Any other way to go around it?

the bios.exe file will usually make a bootable floppy for you. I don't think you can use wine for it (maybe use DOSemu?) -- if all else fails, just find a win box with a floppy drive and use it.

---

### Post by presston on 2008-05-03
he has no floppy .. this is laptop :) and i dont think that installimg new BIOS in dosbox - is a good idea. may crach ALL

---

### Post by lkraemer on 2008-05-03
Glucklich,
In the process of trying to install Alsa 1.0.16 on my Gateway MT6840,
I got something messed up and had no sound.  The speaker in my top right toolbar had a red circle
with slash through it.  I used the following information to get my drivers re-installed.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
which you have already been given......  and:
[https://help.ubuntu.com/community/SoundTroubleshooting#head-c3f7aee989384b55354da086f03f15a2898a7aec](https://help.ubuntu.com/community/SoundTroubleshooting#head-c3f7aee989384b55354da086f03f15a2898a7aec)

Then under the section:
Using drivers from alsa-project
update I now recommend using the stable version 1.0.16

I followed the information at:
[http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

or
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Download
libc6-dev_2.6.1-1ubuntu10_i386.deb
linux-libc-dev_2.6.22-14.52_i386.deb
and install with:
sudo dpkg -i libc6-dev_2.6.1-1ubuntu10_i386.deb linux-libc-dev_2.6.22-14.52_i386.deb


Here is a script that will do it for you.....slightly modified from the above site.....assuming you have ethernet or dialup available....

#!/bin/sh 
# add  -x to the end of the above line for more DEBUG information ie. sh -x
# add  -i to have the script INTERACTIVE
#
#Now you may ask "I already had the packages, so why did I go through the trouble of removing them, then installing them".
#The answer lies in the --purge option which removes all the extra information that accumulated from tinkering and upgrading.
#After doing a purge then install, the packages are unpackaged as if it they are brand new.
#
#[https://help.ubuntu.com/community/SoundTroubleshooting#head-c3f7aee989384b55354da086f03f15a2898a7aec](https://help.ubuntu.com/community/SoundTroubleshooting#head-c3f7aee989384b55354da086f03f15a2898a7aec)
#
#Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working.   
#One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary
#since you are reinstalling everything because of one thing.
#
#A faster way, is to just remove the problematic packages and reinstall them cleanly.
#    *
#      Remove these packages sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
#    *
#      Reinstall those same packages sudo apt-get install linux-sound-base alsa-base alsa-utils 
#    *
#      VERY IMPORTANT NOTE - Ubuntu (GNOME): users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after
#      removing the linux-sound-base packages. If this happens, then do the following sudo apt-get install gdm ubuntu-desktop
#    *
#      VERY IMPORTANT NOTE - Xubuntu (XFCE): users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after
#      removing the linux-sound-base. If this happens, then do the following sudo apt-get install gdm xubuntu-desktop
#    *
#      Reboot
#    *
#      At this point, try using aplay -l you should get your soundcard listed.
#    *
#      Success - Your soundcard is detected. Go onto the Using alsamixer section, then try playing something on your music or media player.
#    *
#      Failure - Your card was not detected. You should try compiling your driver, so go onto ALSA drive Compilation.
#
#
#Just copy the first block of text to a text file and save as alsa_1.sh, and then the second block to alsa_2.sh
#Then make sure both the scripts have execute privileges. (by typing "chmod a+x alsa_1.sh" & same for alsa_2)
#Now cd to the subdirectory in a terminal window and type "sudo sh alsa_1.sh"
#Reboot, and then type "sudo sh alsa_2.sh"

#install necessary stuff
sudo apt-get install build-essential linux-headers-$(uname -r)

echo "creating the source subdirectories......"
cd /
mkdir -p /usr/src/alsa
cd /usr/src/alsa

echo "downloading alsa packages..."
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2)

echo "extracting alsa packages..."
tar -xjf alsa-driver*.tar.bz2
tar -xjf alsa-lib*.tar.bz2
tar -xjf alsa-utils*.tar.bz2
rm alsa*.tar.bz2

#alsa-driver
make clean
#uncomment above line if on second/third compile
#sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<enter driver name here e.g. via82xx> --with-oss=yes
cd /usr/src/alsa/alsa-driver*
#change the information below to match your machine's information
sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=snd-hda-intel --with-oss=yes
sudo make
sudo make install

#alsa-lib
make clean
#uncomment above line if on second/third compile
cd /usr/src/alsa/alsa-lib*
./configure
make
make install

#alsa-utils
make clean
#uncomment above line if on second/third compile
cd /usr/src/alsa/alsa-utils*
./configure
make
make install

echo "now reboot your machine, and run alsa_2"
#end of alsa_1


#alsa_2

#!/bin/sh
#for after reboot
cp -v /lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.22-*/kernel/sound/
depmod -a
#end of alsa_2

Before running script alsa_2 do the following:

$ find /lib/modules -name snd-hda-intel.ko
I suspect you will find two places with the above file.....

then check which drivers are loaded:
$ lsmod | grep snd
I expect you won't find snd-hda-intel loaded

Now run script alsa_2 
And if the driver wasn't loaded above:

$ sudo modprobe snd-hda-intel
will load the driver.

I had sound.......Viola!

LK

---

### Post by Glucklich on 2008-05-03
Sorry Alan, forgot about that detail.
What matters is just the BIOS update file, so I'll just say what you need to input on those options so it will be left only one option. And the plus side, you'll be learning a bit Portuguese! ;)

Tipo de Produto (Product Type): Portáteis (Laptops)
Familia (Family): Satellite
Séries de Produto (Product Series): Satellite P Series
Modelo (Model): Satellite P100 (PSPA6)
Short Model No: PSPA6E
Sistema Operativo (Operating System): OS Independent
Tipo de Driver (Driver Type): Bios Update
País (Country): Portugal
Idioma (Language) : Portuguese

Then enter the 'Pesquisa'(Search) option and in the end of the page, the red table it will be only one option left.

If this option is a bit dificult, there is another way.
Go to this link:
[Toshiba Portugal, Satellite P100-195]("http://pt.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=PT&tab=1&DISC_MODEL=0&highlightOption=119299&BV_UseBVCookie=yes&PRODUCT_ID=116623")
On the 'Outros Produtos' (Other Products' menu, select the 'drivers' option. That will take you to the page that you are already familiar, but this way you'll only have to complete this options:
 
Sistema Operativo (Operating System): OS Independent
Tipo de Driver (Driver Type): Bios Update

It's a faster way and the way I should have said the first time, sorry for my mistake.
The reason I think your search wasn't successful in the UK site it's because I'm guessing that they have updated it, or this particular product was only available on some markets, I don't know.

I took the liberty of opening the .exe file of the manufacturer on Wine's WinRAR, but I don't know what I'm supposed to be looking for.
The files it shows me are: 
BD13C37.WPH; bios.dat; bios.cmd; mfc42.dll; msvcp60.dll; msvcrt.dll; PHLASH.INI; PHLASH.INI.bak; PHLASH.LOG; Phlash9X.vxd; PhlashLc.dll; PhlashNT.sys; winhlp32.exe; WinPhlash.exe; WINPHLASH.HLP
Any files in here are helpful or there is no way in going around this WinPhlash thing?

---

### Post by presston on 2008-05-03
i have no idea how to upgrade bios without floppy

---

### Post by Glucklich on 2008-05-03
Roma2: The problem is that I can get WinPhlash thing to create an BIOS update file that I can boot from and update it. Because WinPhlash is clearly a program made for windows environment, and doesn't work with Wine or VirtualBox.
What I was trying to do is getting the necessary file from the .exe given by the manufacturer.

lkraemer: I do have sound, but it is very low (almost inaudible actually), that's why I'm following the BIOS thing. I read anywhere that the minimum requirement was to have a 2.40 BIOS, I now have a 1.70. But after the BIOS tip the sound is still in the same, I'll follow your lead.

Thanks for all your continuous support.

---

### Post by MaindotC on 2008-05-03
WinPhlash is a windoze program but as mentioned a few posts above if you burn it to floppy (or in your case CD) it typically make the CD bootable just like an operating system CD is bootable.  The problem is that you booted into this cd and you tried to execute the program but you received a message stating it was already running, correct?

When you boot up the machine do you see any messages like "For AWD Flash Utility Press Alt + F2" or can you try entering the BIOS and seeing if there is a BIOS update utility if you haven't done so already?

I'm looking at the page where you downloaded the BIOS file because I'm trying to see if there are any directions that accompany it.  But I just woke up so first I gotta have some of my leftover chips + salsa con queso or I'll get nauseous.

---

### Post by roma2 on 2008-05-03
> **presston said:**
> he has no floppy .. this is laptop :) and i dont think that installimg new BIOS in dosbox - is a good idea. may crach ALL

Wasn't insinuating he install a flash bios from the dosbox, just make the floppy there.

---

### Post by Glucklich on 2008-05-03
The message I told you about goes something like this:

"The bootfiles are in drive letter A:
Your bios utilities are in drive letter R:"

And then he tells me to press any key.
Could be something about the way I did the bootcd?
I got the bootcd .iso from here [http://www.bootdisk.com/]("http://www.bootdisk.com/") where it says "Bootable CD". Then I just opened UtraISO and added the .exe given by the manufacturer. Saved as .iso and burned the CD.
I also went to the BIOS, to see if I saw anything there to update it. Didn't saw nothing.

Eheheh, enjoy your chips with salsa and cheese ;)

---

### Post by Glucklich on 2008-05-04
Any guess on what I could have done wrong on the bootcd? Or is it the manufacturer's file who's not doing what it is supposed to?

---

### Post by Glucklich on 2008-05-04
Hello? Can anybody help me please? What have i done wrong with the bootcd?

---

### Post by presston on 2008-05-04
is there any solution on manufacturer's site?

---

### Post by Glucklich on 2008-05-04
In terms of files for the BIOS update, no. We are stuck with this crappy "WinPhlash" dependent file. In terms of any documentation that could possibly provide any help on upgrading the BIOS in any alternative way, the answer is once again, no.
Probably I'm going to do a stupid question, but could the answer be in the R: drive the message was talking about or it was referring to the computer's hard drive?

---

### Post by Glucklich on 2008-05-04
Will I have to install XP again, Install the new BIOS from there and come back to Linux? Maybe it's the only chance I've got, or the safest.

---

### Post by presston on 2008-05-04
may be from XP it will fastes and most easy way for you (i think, you don't want to have trouble with mainboard manufacturer's stupid :))

---

### Post by Glucklich on 2008-05-04
Did it. New BIOS successfully upload. But now I'm in deep sh*t since Windows deleted the controllers for my devices and now it can't find them. I had to format all the disc since it would not install XP otherwise. That's in times like these I'm glad to always keep a backup of my work.

---

### Post by MaindotC on 2008-05-04
Hey, Gluck - sorry I've been afk but I had to work Fri and Sat night and I've been bushed - also working on installing a fully-functional Request Tracker system.

The BIOS should have nothing to do with the operating system other than it provides the interface for the operating system to manipulate the hardware on an electrical basis.

You said it deleted all of your "controllers".  Do you mean when you go into the BIOS setup screen it doesn't show the devices you have attached to the system, like say for example, the hard drive?  I'll be up a bit tonight but for the most part I'll be busy the next few days - exams are coming up :(

---

### Post by presston on 2008-05-05
i think that when he setup windows, nt loader erased grub's boot sector.

if it is - there is no big problem and can quickly recover it

---

### Post by Glucklich on 2008-05-05
No, the BIOS shows all the hardware but Windows doesn't detect all the devises on the system. Sorry for my inaccuracy in describing the situation. As I only have with me an old XP version, and not the one that came with the laptop (and it doesn't detect the Wireless thing, so I can search on the internet for them), I must check if Vista has all the drivers I need. Because if I got this right, I must have all the devises working properly on Windows before going to Ubuntu, isn't it? I think I've read it somewhere in the "Pre-installation process" on the Ubuntu manual.

---

### Post by presston on 2008-05-05
so, don't work only wi-fi?

---

### Post by DaveBG on 2008-05-05
Hi. I have 5.1 sound but cannot get sound from the back speakers, the center and sub. Only have stereo from the front 2.

I have ASUS P5ND2-SLI Deluxe mainboard with Realtek sound card that is 7.1.
Since i have nForce4 chip i tried the suggestion in the 10th post in this thread:
[http://ubuntuforums.org/showthread.php?t=187541](http://ubuntuforums.org/showthread.php?t=187541)

but still have no go.

---

### Post by presston on 2008-05-05
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)  try this

---

### Post by DaveBG on 2008-05-06
> **presston said:**
> [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)  try this

I think there is something broken since when i enter:

speaker-test -c6 -Dplug:surround51

```
dave@dave-desktop:~$ speaker-test -c6 -Dplug:surround51

speaker-test 1.0.15

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Playback open error: -16,Device or resource busy
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Playback open error: -16,Device or resource busy
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Playback open error: -16,Device or resource busy
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Playback open error: -16,Device or resource busy
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Playback open error: -16,Device or resource busy
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Playback open error: -16,Device or resource busy
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Playback open error: -16,Device or resource busy
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Playback open error: -16,Device or resource busy
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Playback open error: -16,Device or resource busy
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Playback open error: -16,Device or resource busy
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Playback open error: -16,Device or resource busy
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Playback open error: -16,Device or resource busy

```

Very strange. I will no install driver from Realtek to see...

---

### Post by presston on 2008-05-06
> Device or resource busy

close up ALL applications, which use (or can use) sound. disable pusle audio (before it add yourself to pulse group in users)

---

### Post by MaindotC on 2008-05-06
> **Glucklich said:**
> No, the BIOS shows all the hardware but Windows doesn't detect all the devises on the system. Sorry for my inaccuracy in describing the situation. As I only have with me an old XP version, and not the one that came with the laptop (and it doesn't detect the Wireless thing, so I can search on the internet for them), I must check if Vista has all the drivers I need. Because if I got this right, I must have all the devises working properly on Windows before going to Ubuntu, isn't it? I think I've read it somewhere in the "Pre-installation process" on the Ubuntu manual.

Dude, you don't need anything working in Windoze before going to Ubuntu.  The BIOS thing was written to be executed in a Windoze environment, but that was the decision of the manufacturer.  Think of it this way: Suppose you do get everything working in Windoze - hardware is all detected and so forth.  You take out the hard drive and put in a hard drive that has Ubuntu installed on it.  Nothing you did in Windoze transfers to the Ubuntu hard drive and the Ubuntu hard drive runs independently (except the BIOS upgrade which is a hardware function and stays with the motherboard).

Ok since the BIOS upgrade, what is the status of your sound?

---

### Post by Glucklich on 2008-05-08
Well, been very busy at work. 
I though I needed all the controllers working on windows before going back to Ubuntu. Since it's not like that, I'm going to install Ubuntu immediately and let you know in a sec.

---

### Post by Glucklich on 2008-05-08
IT WORKED!!! The problem was the BIOS!!! Thank you everybody for your support!!! And a very special thanks to Alan and Press... thank you so very much for sticking with me trying to figure this out. A very special thank you for both of you! It means a lot to me. Thank you so much! I hope one day I can be as helpful toward others as you were for me, and hope one day I can be there for you guys if you have any problem in which I can help. Thank you very much!

---

### Post by MaindotC on 2008-05-08
Star for me :)  Hey gluck, there are a lot of systems built especially for ubuntu - completely independent of Windoze or any other o/s.  Check out system76 sometime :)

---

### Post by MaindotC on 2008-05-08
> **RossAndGarfunkel said:**
> I still haven't found a fix either. :/

> **gavinjb said:**
> Hi, thanks for the link unfortunately it didn't work

Gavin,

Have you guys been able to fix your stuff?

---

### Post by presston on 2008-05-08
Gluch, ubuntu is such .. it helps us to help others .. with our best wishes))

don't dissapear :)  tnx for star)))

---

### Post by MaindotC on 2008-05-08
> **presston said:**
> Gluch, ubuntu is such .. it helps us to help others .. with our best wishes))

don't dissapear :)  tnx for star)))

Move 'Zig'. For great justice.

---

### Post by Glucklich on 2008-05-09
Wow, Alan. System76 looks so cool. Great laptops with very nice prices. And they are not even converted to Euros.
What's a 'Zig'? Ziggy Marley? :P
Now I'm reeeeeally enjoying Ubuntu... 
Who haven't seen their sound problems solved yet?

---

### Post by MaindotC on 2008-05-09
System76 and there's another retailer that was pretty sweet - something that begins with a Z.  Also, I'm currently helping [this guy]("http://ubuntuforums.org/showthread.php?t=787484") with his sound issue.

---

### Post by shugs on 2008-05-09
I have the loss of sound after suspend/hibernation that was experienced during the testing... However I have installed the final release, clean install on a toshiba satelite a200-iyo with an intel soundcard...

[https://bugs.launchpad.net/ubuntu/+bug/198218](https://bugs.launchpad.net/ubuntu/+bug/198218)

Any help?

---

### Post by RobbieRob on 2008-05-09
I guess this looks like the best place to put a sound problem.

I have sound in totem and in firefox but not in Internet DJ Console, DJplay, WINE or Ardour GTK2...

What could the problem be?

What kind of diagnostics can I run?

---

### Post by MaindotC on 2008-05-09
Robbie you're being helped on another thread so we'll leave it at that.  Shugs I advise you start your own thread and my first bit of advice would be to install the latest video driver depending on your model because the suspend problems usually originate from video issues.

---

### Post by brinux on 2008-05-09
Dukenuke2, you fixed my issue - thank you. :)

I had no sound and didn't know where to begin troubleshooting and your link 
( [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) ) fixed my problem in two commands.

awesome!
thanx

---

### Post by presston on 2008-05-09
RobbieRob, each program must be configured to work with aslsa mixer or alsa-oss. if they have default config to simple oss - you could not have sound

---

### Post by Dartma on 2008-05-11
SOUND!
I have a toshiba satellite p105 s6204, tried many fixes from many forums...then found this:
[http://www.linlap.com/wiki/Toshiba+Satellite+P105#Audiosolved]("http://www.linlap.com/wiki/Toshiba+Satellite+P105#Audiosolved")
It said to update my bios, I did, after reboot, sound!
I didn't have to follow any of the other dsdt stuff, just worked.  
Hope this helps!

---

### Post by GhettoYhetti on 2008-07-13
> **brinux said:**
> Dukenuke2, you fixed my issue - thank you. :)

I had no sound and didn't know where to begin troubleshooting and your link 
( [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) ) fixed my problem in two commands.

awesome!
thanx
Brinux . . . Doood!!!

The link you reference in #169 ([https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)) solved my issue . . . 

Thanks man!

---

### Post by ebazz on 2008-07-14
I'm a newbie and I'm using Ubunto 7.10 and have tried ver 8.04.
After three installs the sound works one day and not the next.

I'm using an IBM pc clone, nothing dramatic.

Sound has been around for years now. You would thing something as mundane as sound events would be second nature? What is the problem? 
Anyone have a plain language answer to this? Compiling code is something I'm not comfortable with right now.

Any help would be appreciated.
Thank you in advance.

ebazz.

---

