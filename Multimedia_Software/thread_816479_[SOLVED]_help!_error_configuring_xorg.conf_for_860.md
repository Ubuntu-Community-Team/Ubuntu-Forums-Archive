---
title: "[SOLVED] help! error configuring xorg.conf for 8600gts in hardy"
date: 2008-06-02
forum: Multimedia Software
---

### Post by conphuzed on 2008-06-02
i followed [this](http://www.funnestra.org/ubuntu/hardy/#nvidia-driver) guide trying to install nvidia drivers correctly. upon booting back into the desktop and trying to configure nvidia settings, here are the results:

sudo nvidia-settings

result:
```
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
```

so i tried:
sudo nvidia-xconfig

result:
```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

what to do?

---

### Post by wolfen69 on 2008-06-02
try:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Xiong Chiamiov on 2008-06-03
and/or [this]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329")

---

### Post by conphuzed on 2008-06-06
okay thanks for the help so far. unfortunately, no luck. 

_wolfen:_ when i follow your advice and type

```
sudo dpkg-reconfigure xserver-xorg
```

it lets me configure something, but it's all about keyboard stuff (what does this have to do with nvidia drivers?). so i go thru and select US keyboard layout and all that but then when i'm done and back at the terminal i try sudo nvidia-settings again and it gives me the same error as before.

_Xiong Chiamiov_: when i follow that guide and type the following:

```
sudo apt-get remove --purge nvidia*
cd ~
sudo chmod +x NVIDIA[press tab to autocomplete]
sudo /etc/init.d/gdm stop
sudo ./NVID[tab]
startx
```

after entering the 2nd last line, it enters what appears to be the nvidia driver config tool (which is good) but then it says there's no kernel interface, so it tries to compile one but then i get the error that [COLOR="Red"]libc header files are not installed[/COLOR] (and it says "please install your distribution's libc development pckg.)

so i press ok and i guess it tried to install that pckg. but failed, so it says installation failed, [COLOR="Red"]please see file '/var/log/nvidia-installer.log' for details.[/COLOR]

any ideas?

---

### Post by conphuzed on 2008-06-13
okay, xiong i ended up using that guide (which has now been modified to account for the problem i encountered above).

thx for the help guys

---

