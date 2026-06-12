---
title: "nVidia driver installation help."
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by Jimit87 on 2006-09-10
483916]Ok so from one forum i found out that to install nVidia 3D driver i must do the following.

1.: ctrl+alt+f1
2.: login as root
3.: init 3
4.: chmod +x /home/your-linux-username/NVIDIA-Linux-x86-1.0-8774-pkg1.run
5.: /home/your-linux-username/NVIDIA-Linux-x86-1.0-8774-pkg1.run
6.: now the installer is loaded just keep pressing next next next next next... at the end of driver isntall it will ask you if the installer should automaticly update your Xorg config file, choose yes. the installer will exit now.
7.: init 5

is that right?

this is what i did.
1) opened terminal
2) typed in
> sudo su
3) it asked me to type in my password and so i did.
4) the thing changed from "gates@gates-desktop:~$" to "root@gates-desktop:/home/gates#"
5) i typed in init 3 next to that and pressed enter
6) nothing happend and i got that [email]root@...gate[/email]s#" back so then i typed in c> chmod +x /home/gates/NVIDIA-Linux-x86-1.0-8774-pkg1.run and pressed enter.
7) nothing happend and i got that [email]root@.....gate[/email]s# back so then i typed in > /home/gates/NVIDIA-Linux-x86-1.0-8774-pkg1.run and pressed enter.
8 ) and i get

"Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 1.0-8774......................................................................................................................................................................................................................................................................................."

and new blue screen appears in term and this is the error mess. i get.

"NVIDIA Software Installer for Unix/Linux





ERROR: Unable to find the system utility `ld`; please make sure you have the
package 'binutils' installed. If you do have binutils installed,
then please check that `ld` is in your PATH.

OK"

my nvidia driver is in the /home/my username forlder.

what am i doing wrong?

btw, from "Linux IA32
Latest Version: 1.0-8774
Latest Legacy GPU version: 1.0-7184"

which one should i use? i have nVidia MX 420 64MB AGP 4X. and did i do those things correctly?

posted in the right section.* 

Thank you.
:)

---

### Post by tseliot on 2006-09-10
You're trying to perform what I call Method 2.

That is not necessary.

Try Method 1 of my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by Jimit87 on 2006-09-10
umm, ok.

edit: check your pm.

---

