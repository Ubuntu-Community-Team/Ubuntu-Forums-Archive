---
title: "3D apps stopped working."
date: 2009-02-12
forum: Multimedia Software
---

### Post by Ewan the moomintroll on 2009-02-12
Hi,
recently I've noticed that when I try to open 3D applications like open arena or google earth, nothing happens.
I have an ATI radeon 9550 graphics card and it has been working fine until recently.
What should I do?
Thanks.

---

### Post by ajmorris on 2009-02-13
> **Ewan the moomintroll said:**
> Hi,
recently I've noticed that when I try to open 3D applications like open arena or google earth, nothing happens.
I have an ATI radeon 9550 graphics card and it has been working fine until recently.
What should I do?
Thanks.

hi there,
Is your fglrx driver still active? Please post the output of ```
sudo glxinfo
```
Also, can you please post the complete output when you try to open one of your applications.

AJ

---

### Post by Ewan the moomintroll on 2009-02-14
My out put for sudo glxinfo is:
```
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

---

### Post by ajmorris on 2009-02-15
oh crud, sorry, wasn't thinking straight, you have an ATI card lol. glxinfo is not what you want, could you please post instead, the output of: ```
sudo fglrxinfo
```

Sorry again,

AJ :)

---

### Post by Ewan the moomintroll on 2009-02-15
:lol:
I get the same outcome:

```
~$ sudo fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
```

---

### Post by ajmorris on 2009-02-15
ok, this means your accelerated ati driver is not being used. Try opening the restricted hardware gui tool in the gnome admin menus, to see if it detects the card, and gives you the option of installing the drivers. If not, then try running:
```
sudo apt-get install xorg-driver-fglrx xserver-xorg-video-radeon
```
if apt says that either of them are already installed, uninstall the package first, then install it again.
(remember to restart X after both options)

If neither of these work, have no fear, we can override the automatic detection, and initialisation of the driver, by adding a section for your graphics card to /etc/X11/xorg.conf

AJ

---

### Post by Ewan the moomintroll on 2009-02-15
There is a proprietary driver found, but when I click activate, it doesn't.
The second option doesn't work.
I would like to try the third option but I'm not sure how.
Thanks for the help.

---

### Post by ajmorris on 2009-02-16
> **Ewan the moomintroll said:**
> There is a proprietary driver found, but when I click activate, it doesn't.
The second option doesn't work.
I would like to try the third option but I'm not sure how.
Thanks for the help.

ok, just a couple things you can try before overriding the auto-detection since it wont enable your proprietry drivers. Run: ```
sudo dpkg-reconfigure xserver-xorg
``` Then restart X - if that doesnt enable the driver, then boot into the recovery option from grub, and run ```
xfix
``` at the recovery prompt.

If neither of those methods work, then you can edit your /etc/X11/xorg.conf - First, before doing this, a warning. This could break your xsession (we are creating a backup of your current xorg.conf as well) however, if it breaks, you have to be comfortable using the CLI to restore you backup. You can do this in a TTY terminal session (ctrl+alt+f#  Where # is a number from 0-9) 

Ok, the actual editing. First create the backup:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
```

Now, this is what the default intrepid xorg.conf looks like:
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

I would like you to now open /etc/X11/xorg.conf (which will be a new file) in your favourite text editor (as a super user). The default gnome GUI text editor is 'gedit' you can run this as a super user like this:
```
gksudo gedit /etc/X11/xorg.conf
```

Now i would like you to paste this into that new file (Just the default xorg.conf that i modified the display section, to use the accelerated Xorg driver):
```
Section "Device"
        Identifier      "Configured Video Device"
        VendorName      "ATI"
        BoardName       "ATI Radeon 9550"
        Driver          "fglrx" 
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

that xorg.conf will force X to use the fglrx driver. Now you need to restart X. If restarting X fails, and it spits you out an error saying that X cannot be started, and sends you back to a login prompt, can you please paste the contents of /var/log/Xorg.0.log  so that i can debug the issue.
Since you have no X, the easiest way to do this, would be to use the cli application to upload the file to pastebin [(paste2pastebin.pl)]("http://pastebin.ca/download/paste2pastebin.pl"). Or to save the file to to an external device that you can view on another machine, such as a flash disk. Or to retrieve the file from another machine, that does have X avaliable, using either the ssh or ftp protocols :)



AJ

---

### Post by Ewan the moomintroll on 2009-02-16
Thanks,
I entered ```
sudo dpkg-reconfigure xserver-xorg
```
and then restarted and went into "Low Graphics Mode", this messed up the image and I got a load of garbled diagonal lines and I couldn't do much. 
I've decided this is more trouble than it's worth and have installed an old nvidia card I have and it seems to work fine.
Sorry for being such a noob, thanks for your help.

---

### Post by ajmorris on 2009-02-17
> **Ewan the moomintroll said:**
> Thanks,
I entered ```
sudo dpkg-reconfigure xserver-xorg
```
and then restarted and went into "Low Graphics Mode", this messed up the image and I got a load of garbled diagonal lines and I couldn't do much. 
I've decided this is more trouble than it's worth and have installed an old nvidia card I have and it seems to work fine.
Sorry for being such a noob, thanks for your help.

We can continue to try to get your ATI card working if you like? :) Traditionally ATI cards are somewhat annoying in linux, but no-where near impossible. So if you would like to continue trying to get the ATI card working, we can :)

AJ

---

