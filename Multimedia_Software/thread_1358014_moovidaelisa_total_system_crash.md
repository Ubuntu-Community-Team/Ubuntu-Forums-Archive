---
title: "moovida/elisa total system crash"
date: 2009-12-17
forum: Multimedia Software
---

### Post by bender1234 on 2009-12-17
Hi

I'm setting up an ubuntu karmic 9.10 amd64 desktop-mediacenter-fileserver-dhcp-server.

I decided to give elisa / moovida a go, but after i added movies(stored locally) and then tried to play a movie, the system totally crashed. The system went completely dead, ssh froze and not even ping worked.

When restarting, the system stopped in safemode. Rebooted into old kernel 2.6.31-14, got prompted with that the screenconfiguration was bad, tried to fix the config. All went black, couldn't even open a terminal. Managed to log in remotely with ssh, and then restore the old driver..

Anyone got any ideas what caused this strange and serious crash?
I also recovered the original moovidia.conf, and my only altering to it to begin with was to set the location of my video files, which it found.

elisa:
Launcher core version 1.0.7, Current core 1.0.9, Moovida version 1.0.9. 
other:

kernel 2.6.31-14. the uhm 185 nvidia driver. nv8800 gts, amd athlon X4, 2GB ram, asus M4N78 SE, sb platinum 128 eax.

Lastly, is there any other good, non hostile mediacenter anyone could recomend? Don't think I want to try elisa again.. ;)Looked nice and all, but this was just to big of a bug. Also it took forever to just add those +-80 movies I had.

cheers,
Bender Bending Rodriguez ;)

---

### Post by bender1234 on 2009-12-25
The problem might have been the nv 185 driver.

I haven't dared to test elisa again, but generally the system seems stable since I installed the 190 driver. The freeze also happened when not running elisa, since the upgrade the system haven't crashed. It also seemed that there was a problem with the networking timing deamon. I haven't booted the system in a while, but at some points during bootup the system stops when initing the deamon.

Sometimes it works just pressing enter and the system starts up normally. Other times the system freezes at this point.
A complete freeze, everything stops and it's not even possible to bring up a terminal.

Any pointers here? Unfortunately I didn't save the dmesg etc logs, I know its hard to tell what the problem was, without the logs :)

Can PS3[ps3 os] read ntfs via samba(it really should be able to)? Or is an other package required to get the ps mediacenter to autolocate the shared folders? For some odd reason the windows machines in the network don't find the server by name, I manually have to enter the ip adresses for the server. The server is running on two subnets, one being a wifi lan the other an ethernet lan. I guess there might be conflicts as the server has two ip addresses, and windows doesn't know which address to use? It worked like a charm when it was only running on the 802.11g subnet. All networking configuration is properly setup, but as stated there might be problems with samba.

Have anyone tried to run xbmc on karmic? I tested it on my laptop workstation[acer 6930G, nv9600gt, x64 karmic], but it crashed. Whitescreened, couldn't alt-tab in gnome, and I had to kill the process through a different terminal. Again this might be a problem with the driver, as I'm still running nv185 on this fella. I'm running the patched .15 kernel, as the regular .14, .15 and .16 is bugged and neither lan nor wlan is working on them. Can't get to install the 190/195 driver as the installation crashes(seems dependable on stuff from the new kernels).

---

### Post by Zeik_Tuvai on 2010-01-12
I have used XBMC on Karmic on my laptop, it works fine for me.  However when i try to run moovida, it crashes with an python error.  Something about not being able to load pgm.gtk.  If anyone has any ideas i would appreciate it.

---

