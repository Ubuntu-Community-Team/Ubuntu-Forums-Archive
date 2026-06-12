---
title: "NVIDIA config missing &quot;driver line&quot; in default device section, not booting to gui"
date: 2011-05-04
forum: Multimedia Software
---

### Post by lodecl on 2011-05-04
I've just installed a clean version of 11.04 and I am trying to get the NVIDIA driver to work.

Just after installing I've seen Unity and used it. Then I activated the NVIDIA driver (from the additional drivers dialog) or I just restarted (I don't remember well anymore) and I got a message telling me that Unity didn't want and I got into classic mode.

In the additional drivers dialog it says the NVIDIA driver is "activated but not currently in use". I found out that I should do a ```
sudo nvidia-xconfig
```, which gave back:

> Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'(Exactly as posted earlier by groovomata here: [http://ubuntuforums.org/showthread.php?t=1739269#7](http://ubuntuforums.org/showthread.php?t=1739269#7). I also have the same  version, "nvidia-xconfig:  version 270.41.06".)

After I reboot I can see the Ubuntu logo bith the four dots starting up and then only a console with some starting messages:

> 
* Starting ACPI deamon [ OK ]
.. more of such starting messages ..

modem-manager[778]: <info> ModemManager (version 0.4) starting...
.. and more modem-manager loading plugin messages ..

.. and ending with:
* Stopping Flush boot log to disk [ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
[ OK ]
And then nothing happens anymore. I stay in this console and can't get into a graphical mode in a normal way.

I can reboot in recovery mode and start a classic GUI, replace the xorg.conf with the backuped one and have everything working again. And thus also repeat this whole process over and over again. But the NVIDIA driver is still "not currently in use".

Anyone knowing a next hint to help me further?

---

### Post by wolfen69 on 2011-05-04
Here is my device section which may help. Of course, replace GT 430 with your card.

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 430"
EndSection
```

---

### Post by lightpurpledye on 2011-08-28
I am having exactly the same problem. I'm on a Samsung SF310, with an nVidia 310M graphics card. It was running 11.04 fine previously, (updated from 10.x) but just reinstalled from an 11.04 liveCD (due to an unrelated problem) and got all the same symptoms as the OP.

---

### Post by Mike Buksas on 2011-09-08
I'm having this problem as well on a Latitude e5420 with NVS 2400m. Reverting back to an earlier version of the driver (173) doesn't help.

Anyone know if there's an open bug on this?

Mike

---

### Post by bronzehedwick on 2011-12-05
Having the same issue on 11.10 with an ASUS UL-80.

---

### Post by northd_tech on 2011-12-06
If you are trying to upgrade to the newer/newest NVIDIA Linux drivers (which I recommend from my experience), then you will need to shutdown/exit the X11 window server.  This isn't the easiest thing to do- after all it was designed for 24/7 reliability unlike some OS'es.

There is extensive documentation at NVIDIA's website where the drivers can be found (and elsewhere online):

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

I'm not sure which driver(s) people will want or need there, so I can't link to specific README files at NVIDIA's website.

There is also this Ubuntu Howto:


[LIST]
[*][BinaryDriverHowto]("https://help.ubuntu.com/community/BinaryDriverHowto")
[*][Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?action=fullsearch&context=180&value=linkto%3A%22BinaryDriverHowto%2FNvidia%22")
[/LIST]
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

The most recent (290.10) driver that I downloaded apparently links to an OpenSuSE HOWTO at NVIDIA's website:

[http://www.suse.de/~sndirsch/nvidia-installer-HOWTO.html]("http://www.suse.de/%7Esndirsch/nvidia-installer-HOWTO.html")

This is what I used to very recently install the 290.10 NVIDIA driver on my laptop (needing the init x and init y commands to manipulate the X11 server):

**NVIDIA Accelerated Linux Graphics Driver README and Installation Guide**
[http://us.download.nvidia.com/XFree86/Linux-x86_64/290.10/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/290.10/README/index.html)

I would recommend reading A LOT of the documentation very thoroughly (maybe even multiple times and letting it 'soak in' for a few days before attempting the NVIDIA driver installation/repair(s) ).  Sometimes it can be nearly painless and other times it can (and WILL) 'break' your Linux installation severely.  I suspect that different hardware combinations are a major culprit here.  

If you get a "partial" install or get stuck at a root# (or other username) command line, you might need to configure the X server files by hand:

Editing the configuration file by hand
Prev      Chapter 3. Configuring X for the NVIDIA Driver
[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/chapter-03-section-02.html](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/chapter-03-section-02.html)

My recent install went pretty quick & painless with those two "init" commands and the NVIDIA .run script, but I don't want to post the exact commands and be responsible for 'borking' everyone's Ubuntu.  READING is far preferable to 'blind tinkering' from my experience with NVIDIA Linux drivers (and they seem to have gotten much easier in the last 10 years FWIW).

EDIT:  Let's also take a look at which graphics driver module(s) are running.  Can you copy/pase the results of this terminal command:
```
lsmod | egrep 'nv|nouv'
```It also might be worth issuing a **startx** command from the terminal (or posting the error messages from that here too).

Also, that Appendix J from the NVIDIA website was very useful for me:
[http://us.download.nvidia.com/XFree86/Linux-x86_64/290.10/README/newusertips.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/290.10/README/newusertips.html)

---

