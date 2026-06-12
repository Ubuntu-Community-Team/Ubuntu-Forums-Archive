---
title: "Wireless Internet Solution for 9.10 (with Nokia CS-10 usb stick and not only...)"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by Menestrello on 2009-11-02
[SIZE=3][COLOR=Lime][B]EDIT: the bug has been solved.
Install again the latest version of network-manager and network-manager-gnome and manually fix the bug (see [https://bugs.launchpad.net/modemmanager/+bug/470728](https://bugs.launchpad.net/modemmanager/+bug/470728) and [https://wiki.ubuntu.com/DebuggingModemmanager](https://wiki.ubuntu.com/DebuggingModemmanager) for the patch and info about how to apply it).
_Remember to Lock the edited modemmanager version in your Synaptic Package manager._
Ty a lot Mr. beniwtv and BEmanuel.PE[/B][/COLOR][/SIZE]

---------------------------------- Original post ---------------------------------
Hi to everybody,
I just started to use Ubuntu since three weeks ago (9.04 & everything working) and I switched to the new 9.10.
Everything was almost ok, but my wireless connection (Nokia CS-10 usb stick)  was not working... after a lot of time spent around forums to search some solution, I found a (bad) way to make it working... and atm I'm surfing the web with it ;)

I'm reporting what I discovered and what I've done, hoping this could help some of those having my same problems:


[LIST]
[*]I made a clean install of Ubuntu 9.10
[*]Since my usb stick wasn't automatically recognized and mounted, I opened **System -> Administration -> Disk utility** and discovered it was recognized as device, but with unknown filesystem... so I just selected it and pressed the command button **Eject media from the device** (At this point the stick red led started blinking)
[*] I went in **System -> Preferences -> Network Connections **and I created the connection in the same way I did for Ubuntu 9.04 (_[COLOR=Red]ATTENTION: be sure to do this step before perfoming the next ones... I'll describe why later[/COLOR]_)
[*][COLOR=Black]I rebooted the system and used the Ubuntu 9.04 installation cd to run the Live 9.04: in this way Ubuntu was recognizing my usb stick and I was able to open it and to copy/paste all the files into a folder located in my /home.[/COLOR]
[*][COLOR=Black]I rebooted the system (removing the 9.04 cd) and ran Ubuntu 9.10 again. Once inside I went to the folder created in the previous step and used the *install.sh* file to install the Nokia CS-10 usb stick (as I did for Ubuntu 9.04, but running the files from the system instead that from the stick memory)[/COLOR]
[/LIST]
[COLOR=Black]Ok... so now the device is installed, but still just recognized and not mounted, and even the connection is not working. I was mad and was going to go back to the safe 9.04... when I found this post onto the Ubuntu Italian Forum: [B][http://forum.ubuntu-it.org/index.php/topic,332110.0.html](http://forum.ubuntu-it.org/index.php/topic,332110.0.html)
[/B]Since I had nothing to loose, I tried it and it is working (**[COLOR=Red]but with some bad effect[/COLOR]**).

I'm reporting here a (resumed) translation for the English speakers.

[/COLOR]> After trying all the workaround proposed on the web, I just started thinking the problem could be in the Network Manager, since I even know the Karmic is using a new method to manage the usb sticks (modem Manager) that could be bugged. So tried to remove the new Network Manager and to use the old one, downloading it from the Jaunty repositories.
These are the steps on a 9.10 clean installation:

[LIST=1]
[*]download the 3 packages *network-manager*, *network-manager-gnome* and *libnm-glib0* from jaunty repositories ```
libnm-glib0: http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager/libnm-glib0_0.7.1~rc4.1.cf199a964-0ubuntu2_i386.deb
network-manager-gnome: http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.7.1~rc4.1-0ubuntu2_i386.deb
network-manager: http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager/network-manager_0.7.1~rc4.1.cf199a964-0ubuntu2_i386.deb
```
[*]sudo apt-get --purge remove network-manager
[*]Install them and then go to System -> Administration -> Synaptic Package Manager and *lock* them, so that Ubuntu won't try to update them again to the new version.
[/LIST]
These instruction are for the i386, if you have a 64bit Ubuntu, go on **packages.ubuntu.com** and download the right packages from there.
After these steps, reboot your computer, *eject media from the device* and use your usb stick wireless connection as you were used with Ubuntu 9.04.

[COLOR=Red][B]BAD EFFECTS:
[/B][/COLOR]
[LIST=1]
[*][COLOR=Red]**  it seems I'm no more able to edit my connections... System-> Preferences->Network Connections is not launching anything... and since I'm a newbie I dunno how to launch it from the command line... or if it is something related to the old version of the package *network-manager-gnome. *That's why it's really important that I setted up the connection parameters before running the quoted steps**[/COLOR]
[*][COLOR=Red][B]when you try to disconnect from the gui, sometimes it dosn't work;
[/B][/COLOR]
[/LIST]
[COLOR=Red][B] Any input or help about how to solve this problem is appreciated.
[/B]
[COLOR=Black]Ps: if you are using a different usb stick, the first steps are of course different for you. Just try to install your wireless connection as you were used with 9.04 and then perform the quoted steps.[/COLOR] [/COLOR] [COLOR=Black]

[/COLOR]

---

### Post by beniwtv on 2009-11-02
Well, you don't need to necessarily use "install.sh", a simple "eject /dev/sr1" (may be different number on your system) will also do the trick.

As for the acutal problem, I found out that the AT+CGDCONT command is issued incorrectly for this modem, so I filed a bug:

[https://bugs.launchpad.net/modemmanager/+bug/470728](https://bugs.launchpad.net/modemmanager/+bug/470728)

---

### Post by Menestrello on 2009-11-02
Oh, that seems a very simple error. What a bad luck... let's hope it will be fixed soon.

Ty for the feedback :p

---

### Post by martin.walton on 2009-11-02
> **beniwtv said:**
> Well, you don't need to necessarily use "install.sh", a simple "eject /dev/sr1" (may be different number on your system) will also do the trick.

As for the acutal problem, I found out that the AT+CGDCONT command is issued incorrectly for this modem, so I filed a bug:

[https://bugs.launchpad.net/modemmanager/+bug/470728](https://bugs.launchpad.net/modemmanager/+bug/470728)


Is there a work around for this bug? I really need to get the cs-10 to work in Karmic for me to work on the move. I'm starting to wish I'd looked in forums before I upgraded from Jaunty.

---

### Post by Menestrello on 2009-11-03
I'm afraid that, while waiting for a fix, we need to use the old version of the Network Manager (from 9.04) or the command line program [wvdial]("http://alumnit.ca/wiki/index.php?page=WvDial").

---

### Post by Menestrello on 2009-11-03
I tried wicd but I wasn't able to make it recognize the usb stick... tried to setup *wlan0* and */dev/ttyACM0* or */dev/ttyACM1* or just *ACM0*, *ACM1* but it wasn't showing any wireless device.

---

### Post by Placidia on 2009-11-03
Menestrello,

You mention using the old network manager from 9.04. I am a newbie; could you explain how to do that? Can we get it back without going back to a full 9.04 install?

Background: I started using Ubuntu 9.04 6 months ago with a ZTE MF636 USB broadband stick. It worked fine until I upgraded to 9.10. Disaster! I set up a connection in the NM, but nothing showed when the stick was plugged in.

---

### Post by Menestrello on 2009-11-03
> **Placidia said:**
> could you explain how to do that? Can we get it back without going back to a full 9.04 install?

If I understood your question, you can easily keep your 9.10 Karmik Koala Ubuntu and just replace the **network-manager** and **network-manager-gnome** with their previous version (the one you were using in 9.04 Jaunty Jackalope ubuntu).

Everything you need is written in the first post, step by step (totally 3 steps) into the quoted selection :D

---

### Post by Menestrello on 2009-11-07
Any news?
The workaround is doing his job...but it's also pretty annoying.

:(

---

### Post by Menestrello on 2009-11-18
It has been fixed!!!!

Check [https://bugs.launchpad.net/modemmanager/+bug/470728](https://bugs.launchpad.net/modemmanager/+bug/470728) for the patch and [https://wiki.ubuntu.com/DebuggingModemmanager](https://wiki.ubuntu.com/DebuggingModemmanager) for info about how to apply it!

PS: at the end remember to lock the edited version of modemmanager in your Synaptic Package Manager.

Ty a lot Mr. beniwtv and BEmanuel.PE

---

### Post by beniwtv on 2009-11-18
> **Menestrello said:**
> It has been fixed!!!!
Ty a lot Mr. beniwtv and BEmanuel.PE

Indeed, once problems have been identified correctly we have a _very_ quick community! 

Enjoy! :popcorn:

---

