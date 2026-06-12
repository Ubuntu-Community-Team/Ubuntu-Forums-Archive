---
title: "Can't Uninstall nvidia-glx"
date: 2012-05-19
forum: Multimedia Software
---

### Post by Tk007LwZFJW5ej on 2012-05-19
I'm following the directions here 
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

to update my nvidia video driver. For the "Disable Conflicting Software" step, I type

```
sudo apt-get remove nvidia-glx
```and get the output 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'nvidia-glx' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```How can I fix this?

---

### Post by Tk007LwZFJW5ej on 2012-05-20
Ok, I uninstalled nvidia*, now I can't login to the machine at all! After the boot screen and kernel selection, the screen goes totally black, flashes the xubuntu logo, then goes black and stays that way. I'm accessing the internet through a live CD. Is there a way I can fix my video display? I can't even login through recovery!

---

### Post by 2F4U on 2012-05-20
Did you go through the troubleshooting section of that document

[https://help.ubuntu.com/community/NvidiaManual#Uninstalling_the_Driver](https://help.ubuntu.com/community/NvidiaManual#Uninstalling_the_Driver)

Just because you can't login doesn't necessarily mean you can't access the system. Did you try to open a virtual console, e.g. Ctrl-Alt-F1 (2..) and login?

---

### Post by sikander3786 on 2012-05-20
You probably need to insert the 'nomodeset' parameter. It is described under the heading 'First boot after installation is complete' here:

[http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html)

Once you can get to the desktop, we would need you to post the output of these commands:

```
dpkg -l nvidia*
lshw -c video
cat /etc/X11/xorg.conf
```

---

### Post by Tk007LwZFJW5ej on 2012-05-20
> **2F4U said:**
> Did you go through the troubleshooting section of that document

[https://help.ubuntu.com/community/NvidiaManual#Uninstalling_the_Driver](https://help.ubuntu.com/community/NvidiaManual#Uninstalling_the_Driver)

Just because you can't login doesn't necessarily mean you can't access the system. Did you try to open a virtual console, e.g. Ctrl-Alt-F1 (2..) and login?

I am able to use a virtual console, but nothing in the troubleshooting guide is applicable to me because I never got beyond the Disable Conflicting Software step. I did try to update and upgrade the system to replace the deleted packages, but I keep getting errors like "Can't resolve blahblah.ubuntu.com."

---

### Post by Tk007LwZFJW5ej on 2012-05-20
> **sikander3786 said:**
> You probably need to insert the 'nomodeset' parameter. 

That got me beyond the boot screen, but the system gets stuck after the Checking Battery State step (which apparently checks out ok). The system never makes it to login, so I still can't get to the desktop.

---

### Post by Tk007LwZFJW5ej on 2012-05-20
> **sikander3786 said:**
> 

Once you can get to the desktop, we would need you to post the output of these commands:

```
dpkg -l nvidia*
lshw -c video
cat /etc/X11/xorg.conf
```

Ok, I mounted my ubuntu partition into /media from the liveCD and chrooted into it. I'm still getting errors when I try to update ( a whole lot of "Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)." Upgrade only gives me the option of removing ironhide, then gives me the error

E: Sub-process /usr/bin/dpkg returned an error code (1)

when I select yes.



```
dpkg -l nvidia*
``````
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
un  nvidia-173                        <none>                            (no description available)
un  nvidia-180-modaliases             <none>                            (no description available)
un  nvidia-185-modaliases             <none>                            (no description available)
un  nvidia-96                         <none>                            (no description available)
rc  nvidia-common                     1:0.2.35                          Find obsolete NVIDIA drivers
rc  nvidia-current                    280.13-0ubuntu6.1                 NVIDIA binary Xorg driver, kernel module and VDPAU library
un  nvidia-current-modaliases         <none>                            (no description available)
un  nvidia-glx-ia32                   <none>                            (no description available)
un  nvidia-libvdpau                   <none>                            (no description available)
un  nvidia-libvdpau-ia32              <none>                            (no description available)
un  nvidia-libvdpau1                  <none>                            (no description available)
un  nvidia-libvdpau1-ia32             <none>                            (no description available)
rc  nvidia-settings                   280.13-0ubuntu2                   Tool of configuring the NVIDIA graphics driver
un  nvidia-vdpau-driver               <none>                            (no description available)
un  nvidia-vdpau-driver-ia32          <none>                            (no description available)

``````
lshw -c video
``` had no output

Output of ```
cat /etc/X11/xorg.conf
```:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 280.13  (buildmeister@swio-display-x86-rhel47-03.nvidia.com)  Wed Jul 27 17:15:58 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by sikander3786 on 2012-05-20
You are getting the "something wicked happened" error probably because you didn't copy your Live CD's resolv.conf to the chroot environment for resolving the address.

For now, from the chroot, try these commands:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo dpkg-reconfigure xserver-xorg
```

And reboot to see if anything changed.

---

### Post by Tk007LwZFJW5ej on 2012-05-20
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

gives me

```
sudo: unable to resolve host ubuntu
mv: cannot stat `/etc/X11/xorg.conf': No such file or directory

```

---

### Post by sikander3786 on 2012-05-20
You are still in the chroot? Just make sure. If you were able to 'cat' the file, you should be able to move it as well.

---

### Post by Tk007LwZFJW5ej on 2012-05-20
> **sikander3786 said:**
> You are still in the chroot? Just make sure. If you were able to 'cat' the file, you should be able to move it as well.

Yes, I'm still in. I exited, chrooted back in, and tried it again just to be sure. Same result.

Edit: does it matter that there is already something called xorg.conf.old?

---

### Post by sikander3786 on 2012-05-20
No, if there was an 'xorg.conf.old' file already, the error would have been different.

How does you Terminal prompt look like? 'ubuntu@ubuntu'?

What is the output of this command?:

```
ls /etc/X11/xorg.conf
```

---

### Post by Tk007LwZFJW5ej on 2012-05-20
My prompt is root@ubuntu.

```
ls /etc/X11/xorg.conf
``` gives me

```
ls: cannot access /etc/X11/xorg.conf: No such file or directory
```

I'm looking in /etx/X11, and I there is an xorg.conf.old listed. Also, there is an xorg.conf~, but no xorg.conf.

---

### Post by sikander3786 on 2012-05-20
Ok, try moving all the xorg.conf* files to some other place or rename them and try the other command and reboot:

```
sudo dpkg-reconfigure xserver-xorg
```

We have already done quite a lot of work on this simple command so I hope it works now. :)

---

### Post by Tk007LwZFJW5ej on 2012-05-20
> **sikander3786 said:**
> Ok, try moving all the xorg.conf* files to some other place or rename them and try the other command and reboot:

```
sudo dpkg-reconfigure xserver-xorg
```

Nope. I got

```
sudo: unable to resolve host ubuntu
```

Maybe there is something wrong with the way I used chroot? I don't really know much about it, just got the steps from some blog.

I did

```
sudo mkdir /media/fix
sudo mount /dev/sda1 /media/fix
sudo chroot /media/fix
```

---

### Post by sikander3786 on 2012-05-20
No, that method doesn't sound great. Try this instead:

```
sudo mkdir /mnt/temp 
sudo mount /dev/sda1 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```

Now, you can also try updating or removing any packages in that chroot environment.

Later, for exiting the chroot:

```
exit
for i in /dev/pts /dev /proc /sys ; do sudo umount /mnt/temp$i ; done
```

---

### Post by Tk007LwZFJW5ej on 2012-05-20
Well! I tried the dpkg command without "sudo," rebooted, and now I'm back into my system...but it is offering me a partial upgrade, and I read somewhere that this meant that something was off and that I should not do the partial upgrade. I did a


```
sudo apt-get update
``` and got a bunch of these

```
W: GPG error: http://archive.canonical.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

and ```
sudo apt-get upgrade
``` gives same as before: option to remove ironhide and

```

E: Sub-process /usr/bin/dpkg returned an error code (1)

```

when I select "y."

---

### Post by sikander3786 on 2012-05-20
This is Ubuntu Oneiric or Ubuntu Precise?

In the meantime, try:

```
sudo apt-get -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
```

If successful, run this command and answer 'No' when it asks to upgrade and post the complete output:

```
sudo apt-get upgrade
```

---

### Post by Tk007LwZFJW5ej on 2012-05-20
> **sikander3786 said:**
> 

```
sudo apt-get -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
```

I ran this and I still see the "following signatures were invalid" errors.
I have oneiric.
In a moment of weakness before  saw you last comment, I got fed up and just accepted the partial upgrade.:icon_frown: I looked at the upgrade list and didn's see anything that looked like it would wreak total havoc.
Everything seems back to the way it was,, even after reboot.

---

### Post by sikander3786 on 2012-05-20
For getting rid of the BADSIG error later, try this:

[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

You only needed to see if there are any packages that partial upgrade wants to remove. If it decides to remove ubuntu-desktop, or any other critical package, you'll be back to square one.

It isn't too late. Check if it removed any packages and if they sound important to you, re-install them before rebooting.

Good Luck!

---

### Post by Tk007LwZFJW5ej on 2012-05-20
Ok, that got rid of the error. Thank you. Now I'm back to square one with updating my nvidia driver.

---

