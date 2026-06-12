---
title: "FF 7.04 tells me I DONT HAVE permission to play TOTEM MOVIE PLAYER!"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by intricate on 2007-06-27
I use FF 7.04. I went to a web site that streams traffic video and TOTEM MOVIE PLAYER launched. Good so far. Then I got a screen message saying I DID NOT have rights/permission to use the player! What the? Its my own laptop and I am the only user. 

How can I get around this "warning message" telling me I don't have rights to my own movie player?

Thanks Friends!

---

### Post by RTrev on 2007-06-30
> **intricate said:**
> I use FF 7.04. I went to a web site that streams traffic video and TOTEM MOVIE PLAYER launched. Good so far. Then I got a screen message saying I DID NOT have rights/permission to use the player! What the? Its my own laptop and I am the only user. 

How can I get around this "warning message" telling me I don't have rights to my own movie player?

Thanks Friends!

Are you sure you're qualified to use Totem, and have the appropriate training and credentials?  :-)

What I would do is check file permissions.. something must have gotten set incorrectly in terms of file permissions.  I had the same problem with VMware Server.  It told me I didn't have permission to change the settings.  Ran it as root, it then let me change the settings, but from then on I couldn't run it at all if I wasn't root.

Browse around and see if any of the Totem related files are set to not allow any access to normal users.

Bob

---

### Post by eggdeng on 2007-06-30
Make sure your user is a member of the audio and video groups, System->Users and Groups tab. Double-click on audio and make sure your user is listed, then on video & the same.
Find the Totem player ```
which totem
``` it's probably in the /usr/bin directory
then do a long listing to see the permissions
```
ls -l/usr/bin/totem
``` You should get
```
-rwxr-xr-x 1 root root 
```
If any of the x are missing do
```
sudo chmod /usr/bin/totem 751
```
If you still have problems and are using xine as a backend, go through the same procedure with xine.

---

### Post by intricate on 2007-07-02
Here is the streaming video site I am trying to view:

video.dot.ca.gov. Right now i get a "black display" when I click on any of the highway links.

Ive got bigger problems here I think.

using your commands,  I get the following:

bobo@bobo-laptop:~$ which totem
/usr/bin/totem


then, I get:

bobo@bobo-laptop:~$ ls-1/usr/bin/totem
bash: ls-1/usr/bin/totem: No such file or directory

Also, there is no VIDEO DEVICES field under USER PRIVILEGES for bobo or root, just USE AUDIO DEVICES for user bobo.


Guess I am royally stupid here. Any ideas?

Thanks.

---

### Post by eggdeng on 2007-07-02
> bobo@bobo-laptop:~$ ls-1/usr/bin/totem
bash: ls-1/usr/bin/totem: No such file or directory

You got no output because you typed the command wrong: the shell is very picky about spaces. Also you typed a 1 instead of a lowercase L. Copy and paste to a terminal. ```
ls -l /usr/bin/totem
```
Similarly, with the users and groups applet, you really want to go to the groups tab rather than the users tab. On a different note, congratulations on being the first person I have ever seen  spell the word 'privileges' correctly on any forum!

---

### Post by intricate on 2007-07-04
you were right and here is the output I got:

bobo@bobo-laptop:~$ ls -l /usr/bin/totem
-rwxr-xr-x 1 root root 311008 2007-04-05 09:13 /usr/bin/totem


Still cant play the streaming video from that web site. Should I use another player? By the way, never have been able to get sound either from FF 7.04.

Thanks.

---

### Post by intricate on 2007-07-04
Now TOTEM doesnt respond and just locks up.

---

### Post by eggdeng on 2007-07-04
There are a few different interrelated issues here.
1) The drivers for your soundcard are not installed or not working properly. Post the output of ```
lspci 
```and ```
aplay -l
``` to enable people to help you with this.
2) You do not have the codecs / plugins for some types of multimedia files properly installed. As you are using ubuntu 7.04, which has a menu option to install these codecs, it would be best if someone using the same version as you helped you with this.
2) You have some kind of permissions problem with the version of totem you are using. I would recommend using the Synaptic Package Manager (in the administration menu) to uninstall it, as well as the coresponding firefox-plugins package. Then, in the package manager, locate and install gxine and gxine-plugins to replace it. (This should also go some way towards helping with the codecs issue.)

---

### Post by intricate on 2007-07-05
lspci

bobo@bobo-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
09:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
bobo@bobo-laptop:~$ 

aplay -l

bobo@bobo-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
bobo@bobo-laptop:~$ 


Hope these output postings help.

Kind regards with Lots of gratitude.
I know my system is messed up.
Thank you-I wish i could be 1/4th as smart as you!

---

### Post by eggdeng on 2007-07-05
It's not so much a question of smart as of my having messed up four times as many installs as you have. If this is your first linux install, you will be learning all the time by experimenting and breaking things. Just make sure all your data files are safely backed up and the most you will lose is the 40 mins or so that it takes to reinstall (no CD key or product activation required).

lspci (list devices on the PCI bus, ie the motherboard) lists your audio device as an ATI SB450 HDA Audio. A lot of users have had problems with this card on ubuntu 7.04 (Fiesty Fawn) although many seem to have solved it just by typing the following commands in a terminal.

```
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto
```

See [http://ubuntuforums.org/showthread.php?t=415821&highlight=ATI+SB450+HDA]("http://ubuntuforums.org/showthread.php?t=415821&highlight=ATI+SB450+HDA") for more details. You will probably need to reboot to see if the fix works. If it doesn't, you may have to edit a configuration file but we'll cross that one if & when we come to it. The worst case scenario is a reinstall with a slightly earlier ubuntu version (6.10) which seems to work perfectly with this card. Try to sort out the soundcard first as multimedia players aren't much use without sound.

---

### Post by intricate on 2007-07-07
Here is the output in FF 7.04 after running those commands in Terminal:

bobo@bobo-laptop:~$ sudo rmmod snd-hda-intel
Password:
ERROR: Module snd_hda_intel is in use
bobo@bobo-laptop:~$ sudo modprobe snd-hda-intel probe_mask=8 model=auto
bobo@bobo-laptop:~$ 

Where to go from here?

Thank you for your patiience.

---

### Post by eggdeng on 2007-07-07
Reboot in recovery mode and try again. (If your computer doesn't give you the option to do this when you restart, watch the bottom of the screen carefully for a message which says press escape to enter menu and you will find the option there.) 
Run the two commands. While you are at it, run ```
gedit /etc/modprobe.d/alsa-base
``` add the line ```
sudo modprobe snd-hda-intel probe_mask=8 model=auto
``` to this file, save and reboot. If you still have problems, try going through the whole rigmarole again but this time using ```
model=3stack
``` in place of model=auto.
No guarantees that it will work but you may get lucky.

---

