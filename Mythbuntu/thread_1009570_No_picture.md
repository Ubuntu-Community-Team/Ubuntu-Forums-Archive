---
title: "No picture"
date: 2008-12-12
forum: Mythbuntu
---

### Post by olddave on 2008-12-12
Hi all just installed Mythbuntu 8.04 on to a spare computer specs are 2.8 processor, 1 gig ram, ati graphics card, 500gig hd, Hauppauge win tv nova 500. The install was the best of any linux distro that i have used. The only problem is when i connect it up to the tv (LG 42in LCD hi def) It will display the xfce desktop and the Mythbuntu start screen but when i select watch tv option i get just a black screen no picture/or sound.
It is connected via a DVI to HDMI cable.
Hope someone can help
Thanks olddave

---

### Post by olddave on 2008-12-12
Hi Me Again got the picture working but no sound does anyone no if the dvi/hdmi cable can pass sound through it if so how or where can i change this in the mythbuntu setup page..
Thanks olddave

---

### Post by SiHa on 2008-12-13
Although HDMI supports both Audio & Video in the same interface, DVI doesn't, it's video only. If you're lucky your TV will have separate audio inputs (red & white RCA connectors, most likely) on one or all of the HDMI inputs. You'll need a Stereo Jack -> RCA lead to take the sound from your PC to the TV.

If you're unlucky the TV will only support Audio-over-HDMI. In this case, your best bet is to use the VGA or component inputs, and whatever audio input that takes.

You can get HDMI graphics cards that will output audio as well, but support of these in Linux is flaky - check this forum.

---

### Post by olddave on 2008-12-13
Thanks for the info SiHai got it working by going through my hometheater system. The picture seems to be a little jerk but that could be the graphics card once again thanks..
Olddave

---

### Post by olddave on 2008-12-13
hi SiHa do you no how to get the remote working i have tried here [http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php) and herehttp://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI
But still no go have used Google but still cannot get it to work.
Anybody can help..
Thanks olddave

---

### Post by hardyn on 2008-12-14
** solved ** major brain cramp

> **olddave said:**
> Hi Me Again got the picture working but no sound does anyone no if the dvi/hdmi cable can pass sound through it if so how or where can i change this in the mythbuntu setup page..
Thanks olddave

I have same issue, how did you get the TV working?

---

### Post by uMuppet on 2008-12-14
Those guides are for MythTV, if you are using Mythbuntu then things are just a little different.  Check the prefixes in your /etc/lirc/hardware.conf file.  The guides tell you to use something else but when Mythbuntu control panel automatically changes things to setup your remote it uses a different prefix.  See mine below,

See [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI) for adding a static input event.

here is my /etc/lirc/hardware.conf

```

REMOTE="Custom"
REMOTE_MODULES=""
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/irremote"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/hauppauge/novat.conf"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```

I have adjusted the lirc file in my home directory to make all the buttons on the remote work.  You can view the 3 files you need on my website [here]("http://mythkiwi.com/index.php/remository?func=select&id=5")

---

### Post by olddave on 2008-12-16
uMuppet
 Thanks for that, at the moment i have not got time Family over for xmas will have a look as soon as i can. Will post here if i have problems..
Once again thanks to all..
Olddave..

hardyn
I have same issue, how did you get the TV working?
What do you mean picture or sound not working or remote.
If it is the sound like i said i got it working with my home theater system..
Give more info and we can try to help..
Olddave

---

### Post by olddave on 2008-12-20
umuppit had a look today at the link [http://www.mythtv.org/wiki/index.php...Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php...Nova-T_500_PCI) for adding a static input event..
i cannot find anything to do with static input event. can you give more info please if it is not a problem..
Thanks again olddave

---

### Post by olddave on 2009-02-05
Hi again back from holiday now so going to have a go at setting up the remote can some one help me with "adding a static input event".
uMuppet i will go to your website and get those files and have ago with those first..
Thanks again
olddave

---

### Post by uMuppet on 2009-02-05
Nice one, let me know how it goes.  I'm making up a program that will set up an IR blaster and it needs to be able to setup a static event so I'll be looking into this soon.

---

### Post by olddave on 2009-02-06
uMuppet got the three files hardware_conf i put this one in /etc/lirc/hardware.conf
The file named novat_conf i put it in /usr/share/lirc/remotes/hauppauge/novat.conf is this right if so all is good but where do i put lirc on your website it says to put it in HOME/.mythtv/ folder
But on my system i have this home/mythtv/.mythtv so where does it go also any help this "adding a static input event" would be great..
olddave

---

