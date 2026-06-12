---
title: "ATI Radeon 9200 + Ubuntu 8.10"
date: 2008-12-23
forum: Multimedia Software
---

### Post by NikolaWeb on 2008-12-23
Hello,

As I noticed "fglrx" doesn't support my graphic card (Radeon 9200) anymore.

So my question is:
Should I install "ATI binary X.Org driver" from "add/remove applications",
or install manually newest ati driver for my card?

Or maybe I should do nothing :)

---

### Post by steefjeqv on 2008-12-23
Hi,

You're card will be perfectly happy (3d, compiz desktop effects, video) with the open-source driver.

Type the following command in terminal :

sudo apt-get install xserver-xorg-video-ati 

Now, be careful because the following step will most likely end with a black (console) screen :

Press the following key combination : ctrl-alt-backspace

If your monitor turns black press ctrl-alt-f1, login with your username and password and type the following command :

sudo dpkg-reconfigure -phigh xserver-xorg

then

sudo reboot

Now you can use desktop effects, play 3d games, play video .... .

If you still have a black screen, press ctr-alt-f1 and type the following :

sudo nano /etc/X11/xorg.conf

Add the following line in your xorg.cong (section device):

Driver "vesa"

press ctrl-o to save
press ctrl-x to quit

sudo reboot and you will have your X back (but no ATI driver).

Now edit your xorg.conf like this :

sudo gedit /etc/X11/xorg.conf

Add the following text (marked in red) to your screen section (underneath the "Generic monitor" line) :

Section "Screen"
        [COLOR="Red"]DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection[/COLOR]
EndSection

Now change "vesa" into "ati".

Save and press ctrl-alt-backspace. If you're login screen appears you'll have a working ati driver.

If you're interested in the latest version of this driver you can check Tormod Volden's launchpad  (always install both the corresponding radeon & ati module from Tormod Volden):

[http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-ati/]("http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-ati/")

Greetings,
Steven

---

### Post by NikolaWeb on 2008-12-23
Thank you very much for fast answer and great explanations.

```

nikola@nikola-desktop:~$ sudo apt-get install xserver-xorg-video-ati
[sudo] password for nikola: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-ati is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nikola@nikola-desktop:~$ 

```

Ubuntu installed newest drivers automatically so I already have fancy 3d window animations and that's great, especially one when you drag window :)

But there is a lot of small bugs that ruin everything... for example when I press keyup it takes screenshot :(

---

