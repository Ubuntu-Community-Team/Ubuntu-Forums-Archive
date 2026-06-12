---
title: "Laptop speaker and headphones work at the same time"
date: 2009-10-23
forum: Multimedia Software
---

### Post by dineshbabumm on 2009-10-23
Hi friends,

I recently installed Ubuntu 64 bit OS in my laptop. I am having a problem with my speakers. They are working fine. But when I insert the headphones, only the headphone should work and the speakers in the laptop should be disabled isn't it? But it is not happening. Both the headphone speakers as well as laptop speakers are on at the same time. It is very irritating as it disturbs people around me and doesn't allow me to listen to songs as and when I want. So please help me out with some solution.

Thank you very much in advance.

- Dinesh

---

### Post by Ulysses361 on 2009-10-24
Please execute step 1, then reboot and send us output from step 3 and step 4 in this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Please also specify the exact model and make of pc you are using.

---

### Post by AutoStatic on 2009-10-24
> **Ulysses361 said:**
> Please also specify the exact model and make of pc you are using.Please do so first, together with the output of **aplay -l**, **lspci | grep -i audio** and **cat /proc/asound/card*/codec#* | grep -i codec** in a terminal.
I would really, really, really  discourage upgrading Alsa, big chance it will break your soundstack.

---

### Post by dineshbabumm on 2009-11-03
Thank you very much friends. I installed Ubuntu 9.10 and the problem vanished! Thank you very much for your time. :-)

---

### Post by Chewy2 on 2009-11-03
I'm having the same problem...  Should I try upgrading Alsa?  

Here's some info about my sound devices/drivers: 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ryan@ryan-laptop:~$ grep -i audio

Codec: IDT 92HD75B3X5
Codec: LSI ID 1040
Codec: Intel G45 DEVCTG

---

### Post by Bunnybugs on 2009-11-03
You kan set a switch at the soundsettings menu... had the same problem with Jaunty...

but it didn come back after rebooting with karmic...

---

### Post by Chewy2 on 2009-11-03
In the sound preferences the only output displayed is Internal Audio Analog Stereo, no headphones show up.

---

### Post by Bunnybugs on 2009-11-04
> **Chewy2 said:**
> In the sound preferences the only output displayed is Internal Audio Analog Stereo, no headphones show up.


Maybe you should check out alsa... Or you have the wrong driver for your soundcard;)

[LEFT][SIZE=2]**(1)** Go to a shell and type:      Code:
     aplay -l 
[/SIZE][/LEFT]

[LIST]
[*]**You See Your Soundcard Listed Here, c**
[*][LEFT][SIZE=2]Move on to step 2.[/SIZE][/LEFT]
[/LIST]
[LEFT][SIZE=2]**(2)** Type this into the shell:      Code:
     lspci -v 
[/SIZE][/LEFT]

[LIST]
[*][LEFT][SIZE=2][COLOR=green]**Success**[/COLOR] - At this point, you should see your sound card listed. This is a positive sign because it means that **Ubuntu **is detecting the presence of your soundcard, but the drivers are not installed/running. Leave your shell running since you will need it.[/SIZE][/LEFT]
[/LIST]

[LIST]
[*][LEFT][SIZE=2]**[COLOR=red]Failure[/COLOR]** - If it is not listed, then there are a few things that you can do.[/SIZE][/LEFT]

[LIST]
[*][LEFT][SIZE=2]If your soundcard is an onboard sound card, then it might be disabled in the system's BIOS. You will have to reboot and hit the key that lets you enter into the BIOS (usually Delete, F2, or F:cool:.[/SIZE][/LEFT]
[*][LEFT][SIZE=2]If your soundcard is not onboard, make sure that it is properly seated in the PCI slot. If your card is working under Windows then this is not a problem.[/SIZE][/LEFT]
[/LIST]
 
[/LIST]
[SIZE=2]**(3)** Check to see if the ALSA driver for your sound card exists. Go to [/SIZE][[SIZE=2]http://www.alsa-project.org/alsa-doc/[/SIZE]]("http://www.alsa-project.org/alsa-doc/")[SIZE=2] and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver([COLOR=seagreen]green hyperlink text[/COLOR]).[/SIZE]
[LIST]
[*][SIZE=2][COLOR=green]**Success**[/COLOR] - You will have found the driver for your soundcard's chipset.[/SIZE]
[/LIST]

[LIST]
[*][LEFT][SIZE=2]**[COLOR=red]Failure[/COLOR]** - You will have not found the driver for your soundcard chipset. (at the moment I cannot help you, but stay tuned!)[/SIZE][/LEFT]
[/LIST]
[LEFT][SIZE=2]**(4)** Now go back to the shell and type      Code:
     sudo modprobe snd- 
 Now, press the **TAB** key **BEFORE** pressing the **ENTER** key to see a list of modules. Try to find the module that matches the driver you found in step 3.[/SIZE][/LEFT]
      

[LEFT][SIZE=2]For example, my driver is a via82xx so I would type, sudo modprobe snd-via82xx.[/SIZE]
[LIST]
[*][LEFT]**[SIZE=2][COLOR=green]Success [/COLOR][/SIZE]**[/LEFT]

[LIST]
[*][LEFT][SIZE=2]A success here means that your soundcard was installed, but it was not being loaded. Now you have loaded it for the current session.[/SIZE][/LEFT]
[/LIST]

[LIST]
[*][LEFT][SIZE=2]To load it for all sessions (you will probably want to do this) you will have to edit /etc/modules (I think this is the file, I'll check once I get to my Dapper PC).[/SIZE][/LEFT]
[/LIST]

[LIST]
[*][LEFT][SIZE=2]Type this into the shell      Code:
      sudo nano /etc/modules 
[/SIZE][/LEFT]
[/LIST]

[LIST]
[*][LEFT][SIZE=2]Add only the name of the module to be loaded at the end of the file. In my case, the via82xx module gave me sound so I added "snd-via82xx" to the end of the file.(iii) Make sure that you have all channels unmuted in alsamixer[/SIZE][/LEFT]
[/LIST]

[LIST]
[*][LEFT][SIZE=2]See the **alsamixer** section[/SIZE][/LEFT]
[/LIST]

[LIST]
[*][LEFT][SIZE=2]Play media using your favorite media player. Set your audio engine to alsa. In some cases, you have to configure your audio engine within another (media engine) like in Kaffiene in Kubuntu. If you hear sound, hurray![/SIZE][/LEFT]
[*][LEFT][SIZE=2]One final step. Go onto **Saving Sound Settings**[/SIZE][/LEFT]
[/LIST]
 
[/LIST]

[LIST]
[*][SIZE=2][COLOR=red]**Failure**[/COLOR] -You have two options[/SIZE]
[/LIST]
[/LEFT]

[LIST]
[*][SIZE=2]Move on to **Getting the ALSA drivers from a *fresh* kernel**. This step is easier and is recommended to users who might have been tinkering with their sound settings and want to revert back to the way it was just after installing **Ubuntu **(without reinstalling Ubuntu of course :wink: )[/SIZE]
[/LIST]

[LIST]
[*][LEFT][SIZE=2]Move on to **ALSA driver Compilation**, if you have not done so already. If you have, please post a new thread with your problem.[/SIZE]
[/LEFT]
[/LIST]
[U][B][SIZE=3]
Getting the ALSA drivers from a *fresh* kernel[/SIZE][/B][/U][SIZE=2]

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall **Ubuntu**. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.[/SIZE][SIZE=2]

A faster way, is to just remove the problematic packages and reinstall them cleanly.[/SIZE] [SIZE=2]

(1) Remove these packages     Code:
     sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils 
 [/SIZE][SIZE=2]
(2) Reinstall those same packages[/SIZE][SIZE=2]
     Code:
     sudo apt-get install linux-sound-base alsa-base alsa-utils 
 [/SIZE]
[list]
[*][LEFT][LEFT] [SIZE=2]**VERY IMPORTANT NOTE: **Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following[/SIZE]
[SIZE=2]     Code:
     sudo apt-get install gdm ubuntu-desktop 
 [/SIZE]
[SIZE=2](3) Reboot[/SIZE][/LEFT]
[/LEFT]
[*][left][LEFT] [SIZE=2]**VERY IMPORTANT NOTE: **Xubuntu (XFCE) users have reported that packages 'gdm' and 'xubuntu-desktop' are removed after removing the [/SIZE][SIZE=2]linux-sound-base[/SIZE][SIZE=2] packages. If this happens, then do the following[/SIZE]
[SIZE=2]     Code:
     sudo apt-get install gdm xubuntu-desktop 
 [/SIZE]
[SIZE=2](3) Reboot[/SIZE]
[SIZE=2]Now you may ask "I already had the packages, so why did I go through the trouble of removing them, then installing them". The answer lies in the --purge option which removes all the extra information that accumulated from tinkering and upgrading. After doing a purge then install, the packages are unpackaged as if it they are brand new.[/SIZE]
[SIZE=2](4) At this point, try using      Code:
      aplay -l 
 you should get your soundcard listed.[/SIZE]
[LIST]
[*][SIZE=2][COLOR=green]**Success**[/COLOR] - Your soundcard is detected. Go onto the **Using alsamixer **section, then try playing something on your music or media player.[/SIZE]
[*][SIZE=2]**[COLOR=red]Failure[/COLOR] -** Your card was not detected. You should try compiling your driver, so go onto **ALSA drive Compilation**.[/SIZE]
[/LIST]
[LEFT]**_[SIZE=3]ALSA driver Compilation[/SIZE]_**[/LEFT]

[LIST]
[*][LEFT][SIZE=2]If you are here, then either your soundcard driver could not be loaded with modprobe, or you want to compile the drivers yourself from scratch. Good luck to you![/SIZE][/LEFT]
[*][LEFT][SIZE=2]There are two main ways the sources of alsa-drivers are made available to you. One is though the apt-get system. Using this system would be the recommended system since most of the heavy lifting is done for you.[/SIZE][/LEFT]
[*][LEFT][SIZE=2]The other way, is getting the latest drivers from alsa-project.org. This page has the latest drivers available, which you might want to fix problems with. However, these have not been tested with Ubuntu and therefore should be used with caution.[/SIZE][/LEFT]
[/LIST]
[LEFT]**_[SIZE=2]Using alsa-source[/SIZE]_**[/LEFT]

[LIST=1]
[*][LEFT][SIZE=2]Type the following to shell: (note: module-assistant is optional, it will compile the package for you)     Code:
     sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source 
[/SIZE][/LEFT]
[*][LEFT][SIZE=2]     Code:
     sudo dpkg-reconfigure alsa-source 
[/SIZE][/LEFT]
[*][LEFT][SIZE=2]You now have a big blue dialog box (left and right keys to choose 'Yes' and 'No', Enter key proceed). Answer yes (for ISA-PNP - recommended by package maintainers), then yes again (for debugging - recommended by package maintainers).[/SIZE][/LEFT]
[*][LEFT][SIZE=2]Now you must pick which driver you want to install. Use space to select and deselect modules, and up and down to navigate.[/SIZE][/LEFT]
[*][LEFT][SIZE=2]From **General Help step 3**, you should know the name of your driver. Deselect 'all' (the * will go away), and select your driver. In my case, I deselected 'all' then selected 'via82xx'. Hit Enter. Almost home free![/SIZE][/LEFT]
[*]
[LIST]
[*][LEFT][SIZE=2]**If you chose module-assistant**      Code:
     sudo module-assistant a-i   alsa-source 
 If the progress bar reaches 100% with no errors, you will have installed the drivers successfully. Resume this guide from **General Help step 4**.[/SIZE][/LEFT]
[*][LEFT][SIZE=2]**If you did not choose module-assistant - **Remember the name of your soundcard driver and use it place of the [COLOR=blue]blue text[/COLOR] below.

     Code:
      cd /usr/src sudo tar xjvf alsa-driver.tar.bz2 cd modules/alsa-driver 
[/SIZE][/LEFT]
     Code:
     [SIZE=2]sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=[COLOR=blue]<enter driver name here e.g. via82xx> [/COLOR][COLOR=blue][COLOR=black]--with-oss=yes[/COLOR][/COLOR] [/SIZE]
[SIZE=2]sudo make  [/SIZE]
[SIZE=2]sudo make install[/SIZE]
[/LIST]
 
[/LIST]
[/LEFT]

[LIST=1]
[*]
[LIST]
[*]     Code:
[/LIST]
 
[/LIST]
     
           [LEFT][SIZE=2]If you get no error messages, you will have installed the drivers successfully.[/SIZE]
[LIST]
[*][SIZE=2][COLOR=green]**Success**[/COLOR] - Resume this guide from **General Help step 4**.[/SIZE]
[/LIST]

[LIST]
[*][LEFT][SIZE=2]**[COLOR=red]Failure - [/COLOR]**Start a new thread in this thread of the forum. Paste the error message that you get and state that you were following instructions on this page.[/SIZE][/LEFT]
[/LIST]
[LEFT][SIZE=2]**_Using drivers from alsa-project_** - **update **I now recommend using the stable version 1.0.12[/SIZE][/LEFT]

[LIST]
[*][LEFT][SIZE=2]The alsa-project route is very similar to the alsa-source route without the module-assistant.[/SIZE][/LEFT]
[*][LEFT][SIZE=2]First you would have to get the alsa-driver tar from alsa-project then pretty much do configure, make and make install again.[/SIZE][/LEFT]
[*][LEFT][SIZE=2]However, I do recommend that you make a specific directory when you compile something from source. Remember the name of your soundcard driver and use it place of the [COLOR=blue]blue text[/COLOR] below.[/SIZE][/LEFT]
[/LIST]
     Code:
      
[LEFT][SIZE=2]mkdir src[/SIZE]
[SIZE=2]cd src[/SIZE] [/LEFT]
      
[LEFT][SIZE=2]mkdir alsa[/SIZE] [/LEFT]
      
[LEFT][SIZE=2]cd alsa[/SIZE] [/LEFT]
      
[LEFT][SIZE=2]sudo apt-get install build-essential linux-headers-$(uname -r)[/SIZE][/LEFT]
                [SIZE=2]wget [ftp://ftp.alsa-project.org/pub/drive....12rc2.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.12rc2.tar.bz2")[/SIZE]
[LEFT][SIZE=2]tar xvjf alsa-driver-1.0.12rc2.tar.bz2[/SIZE]
[SIZE=2]cd alsa-driver-1.0.12rc1[/SIZE]
[SIZE=2]sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=[COLOR=blue]<enter driver name here e.g. via82xx> [COLOR=black]--with-oss=yes[/COLOR][/COLOR][/SIZE]
[SIZE=2]sudo make[/SIZE]
[SIZE=2]sudo make install[/SIZE][/LEFT]
 
[LEFT][SIZE=2]If you get no errors from doing the above then you have successfully compiled alsa-drivers from source. Resume this guide from **General Help step 4**.[/SIZE][/LEFT]
      
 
[LEFT]_**[SIZE=3]Using alsamixer[/SIZE]**_[/LEFT]

[LIST]
[*][SIZE=2]Type this into a shell      Code:
     alsamixer 
[/SIZE]
[/LIST]
[SIZE=2]You will now see what appears to be a graphical equalizer. It is more like ten different volume controls in the sample place.[/SIZE]
[LIST]
[*][SIZE=2]To navigate around:[/SIZE]
[LIST]
[*][SIZE=2]Left and Right Arrow Keys - Move left and right (if you move long enough in one direction you will get back to where you started - you will not fall off the screen :lol:)[/SIZE]
[*][LEFT][SIZE=2]Up and Down Arrow Keys - Increase and decrease volume respectively.[/SIZE][/LEFT]
[*][LEFT][SIZE=2]Letter M Key - Mutes/unmutes. If a channel is unmuted, then there is a [COLOR=seagreen]**green box**[/COLOR] underneath the volume slider. If the channel is muted, the **[COLOR=gray]box is grey[/COLOR]**.[/SIZE][/LEFT]
[/LIST]
 
[/LIST]
_**[SIZE=3]Saving Sound Settings[/SIZE]**_
[SIZE=2]Do this step to ensure that your alsamixer settings are reloaded with each boot. First make sure you have your settings just the way you like them in alsamixer. Then do      Code:
     sudo alsactl store [COLOR=blue]0[/COLOR] 
 or if this is your nth sound card (where n is the number of soundcards in your computer) replace [COLOR=blue]0[/COLOR] with [COLOR=blue]n-1[/COLOR][COLOR=black]. Many thanks to xpix for trying this out.-[/COLOR][/SIZE] 
 
[LEFT]_**[SIZE=3]Getting more than one application to use the soundcard at the same time[/SIZE]**_
[/LEFT]

[LIST]
[*][SIZE=2]You might want to play a game and listen to music on your favorite music player at the same time. To do this successfully, you will have to use ALSA since it supports this feature the best. On all the music players I know of, you can configure the sound engine, to any module that is available.[/SIZE]
[/LIST]
[/LEFT]

[LIST]
[*][LEFT][SIZE=2]The setting is usually found under something like Tools >>> Configure >>> Player Engines.[/SIZE][/LEFT]
[/LIST]

[LIST]
[*][LEFT][SIZE=2]For games, it is a bit more tricky since there is not always a way to configure the player engine directly. Most games, however, do support the OSS. ALSA has an OSS module that allows OSS applications to use the ALSA driver.[/SIZE][/LEFT]
[/LIST]

[LIST]
[*][LEFT][SIZE=2]To do this you will need the alsa-oss package     Code:
     sudo apt-get install alsa-oss 
 [/SIZE][/LEFT]
[*][LEFT][SIZE=2]After doing this step, it is very easy to use alsa-oss. In the shell, you can type 'aoss' then the name of the program name you want to use with alsa-oss.[/SIZE][/LEFT]
[/LIST]

---

### Post by Chewy2 on 2009-11-04
Well I went through the first 4 steps successfully, my sound card was there and everything(snd-intel-hda I think), so I added that to /etc/modules. Still no luck. Sound works fine and everything, it just doesn't get muted when headphones are plugged in(even if two sets are plugged in).

EDIT: I just noticed in my sound preferences, that if I change the hardware to anything but Analogue Stereo Duplex or output, sound does not work. The item for it in alsa settings (IEC958) is muted by default, but even when un-muting setting my hardware to digital does not work.

I've also noticed that the headphones are considered the "front" output in alsa. I can't hear from the headphones at all unless that is set about 64.

---

### Post by Chewy2 on 2009-11-04
I tried to upgrade alsa, and it seemed to do so successfully, but my sound no longer works...

So I'm gonna have to try and fix that now...


That is what comes up when I try to enter sudo modprobe snd-hda-intel...
WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

---

### Post by jewely on 2009-11-24
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.

I get the same thing when i do this: sudo modprobe snd-hda-intel.

---

### Post by theflanman on 2009-12-12
I have the same problem with my tx2120us. it's a pre-fab, with 9.10 unstalled.

---

