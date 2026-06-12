---
title: "New ATI/AMD Drivers"
date: 2011-03-30
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2011-03-30
I received this email this morning:

> Hi all,

A new fglrx driver (2:8.840-0ubuntu1) is now available in Natty and it
finally works with the new xserver. There are still a few issues whose
fixes should land after Beta 1 is released:

1) compiz needs to be updated so that fglrx can work with Unity.
Currently the "Classic Desktop" session works well but the "Ubuntu
Desktop" one doesn't. If you'd like to test Unity with the new driver,
you can use Unity's daily builds from the PPA, as described here:
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityWithFglrxBeta](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityWithFglrxBeta)

2) currently the driver is not offered for installation in Jockey. A fix
is already available in Jockey's development branch though.

In the meantime, if you wish to install the new fglrx driver, you can do
it manually by following these commands:

sudo apt-get install fglrx
sudo update-alternatives --config gl_conf (and select the line with fglrx)
sudo update-initramfs -u

and finally reboot.

No xorg.conf is required as the driver will be automatically loaded.

Note: despite what the relevant article from Phoronix claims, the driver
doesn't support AMD's PowerXpress.

Regards,

-- Alberto Milone Sustaining Engineer (system) Premium Engagements Team Canonical OEM Services 

---

### Post by andrewabc on 2011-03-30
I'm guessing this did not make it in time to be included in Beta release by default?

---

### Post by jfernyhough on 2011-03-30
```
Setting up fglrx (2:8.840-0ubuntu1) ...
**update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.**
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.840 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.38-02063802-generic
Building for architecture x86_64
Building initial module for 2.6.38-02063802-generic
Done.
```
Hmm... looks like I don't need to run update-alternatives manually... :D

Watch me lose X when I reboot. ;)

--edit
Works! Multi-monitor setup is a two-stage process:
1) Use Catalyst Control Centre (CCC) to set the desired layout. This sets the virtual area. Log out and back in.
2) Use Displays to set the desired layout.

It looks as though allowing mipmap creation in ccsm (e.g. in Static Application Switcher) works again - no more frozen desktop.

--edit 2
Woohoo! Full-speed Minecraft. :D

---

### Post by rajeev1204 on 2011-03-30
I tried this with the unity daily ppa as suggested in the wiki to get unity running, but i have neither unity or compiz running in classic mode either.

Then i tried typing unity in terminal and i got a mixture of unity and panel both.

---

### Post by ELD on 2011-03-30
> **rajeev1204 said:**
> I tried this with the unity daily ppa as suggested in the wiki to get unity running, but i have neither unity or compiz running in classic mode either.
 
Then i tried typing unity in terminal and i got a mixture of unity and panel both.
 
That's because by doing that you are loading unity on another session = you will of course get both :P
 
So when can we expect these changed to land in a jockey update so we can do it normally without tinkering and get full speed AMD?

---

### Post by cariboo on 2011-03-30
Jockey is in the development branch already, so I'd assume, it'll should show up fairly quickly.

---

### Post by d2kx on 2011-03-31
Unity works if I type "unity" in a terminal, but does not automatically start with the desktop session. Hopefully it'll get fixed soon.

---

### Post by waspbr on 2011-03-31
worked for me with the latest daily unity.

Compiz is still a little buggy, I had to enter 

```
compiz --replace
```

made a little launcher for this command, but yeah it works, but expect some minor compiz borkage.

---

### Post by mohegan on 2011-03-31
It works very well with the daily ppa but Unity doesn't launch auto.
So, I modify the file /usr/share/gnome-session/sessions/ubuntu.session in order to launch unity without gnome-panel :
```
[GNOME Session]
Name=Ubuntu
Required=windowmanager;filemanager;
Required-windowmanager=compiz
Required-filemanager=nautilus
DefaultApps=gnome-settings-daemon;
FallbackSessionsID=FallbackUnity2d;FallbackClassicGnome
FallbackUnity2d=2d-ubuntu
FallbackClassicGnome=classic-gnome
FallbackClassicGnomeMessage=It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment.
```

---

### Post by d2kx on 2011-03-31
Yeah, just commenting out the "IsRunnableHelper" entry in the "/usr/share/gnome-session/sessions/ubuntu.session" did the trick and is not as ugly as a startup script.

---

### Post by artemeas on 2011-04-05
I've reinstalled natty beta (cuz install+reinstall fglrx broke completely the unity support...)

So after reinstalling the whole system I installed fglrx (8.84.6-110324a)

The only thing I noticed (compared to default mesa driver) is the shadow under the top-bar AND window movement IS VERY SLOW, when I move a window it seams like a 16-24fps on default driver movement is very quick.

Enabling Tear Free does quiet nothing...

Is it a compiz bug or a driver issue?

btw. ```
artem@linux-void:~$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 5800 Series
OpenGL version string: 4.1.10665 Compatibility Profile Context

```

**UPD:** slow windows movement fixed :)
compizconfig settings manager -> OpenGL -> Sync to VBlank (uncheck!)
ati catalyst control center -> Display Options -> Tear Free -> Enable
ati catalyst control center -> 3D -> More Settings -> Wait for vertical refresh? -> Performance (Always off)

---

