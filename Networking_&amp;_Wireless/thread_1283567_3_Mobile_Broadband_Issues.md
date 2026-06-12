---
title: "3 Mobile Broadband Issues"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by daveycakes on 2009-10-05
Hi there.
 
So recently I bought a 3 mobile broadband dongle/contract. I have ubuntu 9.04 installed. However I have problems getting it to work so I was wondering if somebody could please help me. 
 
When the dongle loaded up there was a .tar file which i extracted and ran the install.sh in terminal view. It hasnt worked and now im out of options =[
 
Here is what appeared:
 
..................start install.................
cp: cannot create directory `/opt/3UK': Permission denied
....installing driver
/media/USB DISK/LinuxUI/install.sh: line 90: cd: /opt/3UK/bin/linuxdriver: No such file or directory
chmod: cannot access `/usr/bin/wvdial': No such file or directory
chmod: changing permissions of `/usr/sbin/pppd': Operation not permitted
chmod: cannot access `/opt/3UK/pppd/ip-up.local': No such file or directory
chmod: cannot access `/opt/3UK/pppd/ip-down.local': No such file or directory
cp: cannot stat `/opt/3UK/pppd/ip-up.local': No such file or directory
cp: cannot stat `/opt/3UK/pppd/ip-down.local': No such file or directory
chmod: cannot access `/opt/3UK/usr/share/applications/3UK.desktop': No such file or directory
cp: cannot stat `/opt/3UK/usr/share/applications/3UK.desktop': No such file or directory
cp: cannot stat `/opt/3UK/usr/share/pixmaps/3UK.png': No such file or directory
chmod: cannot access `/opt/3UK/bin/3UK': No such file or directory
cp: cannot stat `/opt/3UK/bin/3UK': No such file or directory
cp: cannot stat `/opt/3UK/Data/etc/wvdial.conf': No such file or directory
chmod: cannot access `/etc/wvdial.conf': No such file or directory
chmod: changing permissions of `/etc/ppp/options': Operation not permitted
cp: cannot stat `/opt/3UK/Data/etc/ppp/resolv.conf': No such file or directory
chmod: cannot access `/etc/ppp/resolv.conf': No such file or directory
chmod: changing permissions of `/etc/resolv.conf': Operation not permitted
cp: accessing `/etc/ppp/peers/wvdial': Permission denied
chmod: cannot access `/etc/ppp/peers/wvdial': Permission denied
cp: cannot stat `/opt/3UK/Data/etc/udev/rules.d/999-zte.rules': No such file or directory
chmod: cannot access `/etc/udev/rules.d/999-zte.rules': No such file or directory
/media/USB DISK/LinuxUI/install.sh: line 191: udevcontrol: command not found
chmod: cannot access `/opt/3UK/3UK.desktop': No such file or directory
chown: cannot access `/opt/3UK/3UK': No such file or directory
chmod: cannot access `/opt/3UK/3UK': No such file or directory
chmod: cannot access `/opt/3UK/3UK': No such file or directory
chmod: cannot access `/opt/3UK/uninstall.sh': No such file or directory
/media/USB DISK/LinuxUI/install.sh: line 208: cd: /media/USB: No such file or directory
/media/USB DISK/LinuxUI/install.sh: line 212: cd: /media/USB: No such file or directory
/media/USB DISK/LinuxUI/install.sh: line 223: rpm: command not found
..................install completed!!!..................
/media/USB DISK/LinuxUI/install.sh: line 227: cd: /media/USB: No such file or directory
....If you install 3UK for the first time,please re-plug the device!
....After setup, you will find the 3UK in "Applications->Internet->3UK". Click the 3UK and the application will run
press any key to continue.... 
 
If someone could help me getting working i would be very greatful.
 
Thank you :D
 
[COLOR=red]EDIT:[/COLOR]
[COLOR=#ff0000][/COLOR] 
[COLOR=black]So basically i edited the install.sh so all the important things were available for the installer. [/COLOR]
 
Now all those existing issues are gone. However now the error occurs:
 
error: failed dependencies:
 
(huge list of things) is needed by qt3-3.x.xx.-xx.xxx.i386 (i replaced the numbers and letters with x's, not sure if im supposed to show them :P) anyway im stuck now! not sure what to do now.
 
Please help :)

---

