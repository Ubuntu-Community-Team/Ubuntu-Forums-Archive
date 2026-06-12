---
title: "gspca and intel 82801db in ibex giving me problems with skype"
date: 2008-10-30
forum: Multimedia Software
---

### Post by nagolchi on 2008-10-30
Just upgraded to ibex.  Looked as if everything was working.  However, when I opened up skype, I noticed that neither my webcam nor my sound was working.  While I am able to hear correct audio from rhythmbox, youtube, etc, when I go to test my sound in system > preferences >sound, i get nothing but a long system beep.  I tried changing the audio playback to ALSA, PulseAudio, and everything else available.  I'm using the Intel 82801DB audio drivers.


When I open up skype through the terminal, I receive these error messages
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)

Also, I noticed my webcam wasn't working.  There are no video devices listed in /dev. When I tried to do a sudo modprobe gspca, I receive a dreaded FATAL: Module gspca not found. 

Any help is appreciated.  I live in Europe and I desperately need Skype working so I can tell my parents I'm still alive.

---

### Post by jblackhall on 2008-10-31
have you added the new medibuntu repos and updated your skype software?

---

### Post by nagolchi on 2008-10-31
indeed I have.  I can still get sound out of most programs. but when i test my audio in my panel I get just a constant system beep sound and when I run skype, I can't get any audio to play. 

Also, gspca is still nowhere to be found.  I was under the impression that it was included in the kernel 2.6.27

---

### Post by leshiySKH on 2008-10-31
same problems. but i am missing sound throughout the system ( no sound any where). got an old ibm thinkpad t22, if it helps.

i guess will have to wait till more people have this problem :) 
otherwise i'll have to go back to 8.04.

---

### Post by leshiySKH on 2008-10-31
this helped me: 


[https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/274124](https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/274124)



Hm.. to all OSS users, (Realtek etc) - and to all those who just don't know, but want to try and make it work, try execute this command:

sudo apt-get install --reinstall oss-preserve psemu-sound-oss oss-compat alsa-oss alsa-tools alsa-firmware-loaders alsa-base alsa-utils
sudo adduser $USER audio
sudo adduser $USER pulse
sudo adduser $USER pulse-access
sudo adduser $USER pulse-rt

(One of the above packages made it work for me, I don't know which one or ones)
- When it's done installing/reinstalling, log out and log back in
- Go to System > Preferences > Sound, you should see new "ALSA ... Analog (OSS)" in the drop down lists - choose the last analog (oss) item mentioned in each list.
- For "Device:" choose the "Alsa mixer"

Now press Close and reboot your machine (yes, restart!).

Log in again, and execute this command to open the volume control:
gnome-volume-control

Choose in the device "Alsa mixer"
If you see a PCM section in the volume control, raise its volume.
If you don't see it, click "Preferences" and make sure "PCM" is checked there.

This should hopefully enable you to listen to flash movies audio and local audio until pulseaudio is fixed :)

---

### Post by nagolchi on 2008-10-31
didn't work for me, but it's reassuring to find out that these audio problems are widespread.   However, on a whim, i killed the pulseaudio process.  now audio in skype works, even if I keep getting the error messages.  i suppose it's just a temporary fix until they address this bug. 

now if i could get the darn gspca module to compile correctly...

---

### Post by nagolchi on 2008-11-01
Still cannot get this darn gspca module to compile.  This is the output with error messages that I get.  Any ideas?  

make -C /lib/modules/`uname -r`/build SUBDIRS=/home/name/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/name/gspcav1-20071224/gspca_core.o
/home/name/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/name/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/name/gspcav1-20071224/gspca_core.c:2466: error: implicit declaration of function ‘video_usercopy’
/home/name/gspcav1-20071224/gspca_core.c: At top level:
/home/name/gspcav1-20071224/gspca_core.c:2612: error: unknown field ‘owner’ specified in initializer
/home/name/gspcav1-20071224/gspca_core.c:2612: warning: initialization from incompatible pointer type
/home/name/gspcav1-20071224/gspca_core.c:2614: error: unknown field ‘type’ specified in initializer
/home/name/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/name/gspcav1-20071224/gspca_core.c:2772: error: implicit declaration of function ‘video_device_create_file’
/home/name/gspcav1-20071224/gspca_core.c:2783: error: implicit declaration of function ‘video_device_remove_file’
/home/name/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/name/gspcav1-20071224/gspca_core.c:4314: error: incompatible types in assignment
make[2]: *** [/home/name/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/name/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2
name@name-laptop:~/gspcav1-20071224$ sudo make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/name/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/name/gspcav1-20071224/gspca_core.o
/home/name/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/name/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/name/gspcav1-20071224/gspca_core.c:2466: error: implicit declaration of function ‘video_usercopy’
/home/name/gspcav1-20071224/gspca_core.c: At top level:
/home/name/gspcav1-20071224/gspca_core.c:2612: error: unknown field ‘owner’ specified in initializer
/home/name/gspcav1-20071224/gspca_core.c:2612: warning: initialization from incompatible pointer type
/home/name/gspcav1-20071224/gspca_core.c:2614: error: unknown field ‘type’ specified in initializer
/home/name/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/name/gspcav1-20071224/gspca_core.c:2772: error: implicit declaration of function ‘video_device_create_file’
/home/name/gspcav1-20071224/gspca_core.c:2783: error: implicit declaration of function ‘video_device_remove_file’
/home/name/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/name/gspcav1-20071224/gspca_core.c:4314: error: incompatible types in assignment
make[2]: *** [/home/name/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/name/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2

---

### Post by joanvup on 2008-11-06
change #include <asm/semaphore.h> for #include </usr/include/semaphore.h> in /home/name/gspcav1-20071224/gspca_core.c file and try again

> **nagolchi said:**
> Still cannot get this darn gspca module to compile.  This is the output with error messages that I get.  Any ideas?  

make -C /lib/modules/`uname -r`/build SUBDIRS=/home/name/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/name/gspcav1-20071224/gspca_core.o
/home/name/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/name/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/name/gspcav1-20071224/gspca_core.c:2466: error: implicit declaration of function ‘video_usercopy’
/home/name/gspcav1-20071224/gspca_core.c: At top level:
/home/name/gspcav1-20071224/gspca_core.c:2612: error: unknown field ‘owner’ specified in initializer
/home/name/gspcav1-20071224/gspca_core.c:2612: warning: initialization from incompatible pointer type
/home/name/gspcav1-20071224/gspca_core.c:2614: error: unknown field ‘type’ specified in initializer
/home/name/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/name/gspcav1-20071224/gspca_core.c:2772: error: implicit declaration of function ‘video_device_create_file’
/home/name/gspcav1-20071224/gspca_core.c:2783: error: implicit declaration of function ‘video_device_remove_file’
/home/name/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/name/gspcav1-20071224/gspca_core.c:4314: error: incompatible types in assignment
make[2]: *** [/home/name/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/name/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2
name@name-laptop:~/gspcav1-20071224$ sudo make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/name/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/name/gspcav1-20071224/gspca_core.o
/home/name/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/name/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/name/gspcav1-20071224/gspca_core.c:2466: error: implicit declaration of function ‘video_usercopy’
/home/name/gspcav1-20071224/gspca_core.c: At top level:
/home/name/gspcav1-20071224/gspca_core.c:2612: error: unknown field ‘owner’ specified in initializer
/home/name/gspcav1-20071224/gspca_core.c:2612: warning: initialization from incompatible pointer type
/home/name/gspcav1-20071224/gspca_core.c:2614: error: unknown field ‘type’ specified in initializer
/home/name/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/name/gspcav1-20071224/gspca_core.c:2772: error: implicit declaration of function ‘video_device_create_file’
/home/name/gspcav1-20071224/gspca_core.c:2783: error: implicit declaration of function ‘video_device_remove_file’
/home/name/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/name/gspcav1-20071224/gspca_core.c:4314: error: incompatible types in assignment
make[2]: *** [/home/name/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/name/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2

---

### Post by nagolchi on 2008-11-09
no luck.  gotta wait for some fix for this webcam.  logitech e2500.

---

### Post by Servechilled on 2008-11-10
> **nagolchi said:**
> no luck.  gotta wait for some fix for this webcam.  logitech e2500.

The gspca driver is included in 8.10. 
```
sudo modprobe gspca_main
``` should get you up and running :guitar:

---

### Post by 081103jk on 2008-11-10
1&#12289;[**&#30095;&#36890;&#39532;&#26742;**](http://www.bjbtgdst.com.cn/stmt.htm)&#19987;&#19994;&#30095;&#36890;&#21508;&#31181;&#22411;&#21495;&#39532;&#26742;&#65288;&#25273;&#24067;&#12289;&#22609;&#26009;&#65289;&#31561;&#21508;&#31181;&#36719;&#30828;&#29289;&#36136;&#25152;&#36896;&#25104;&#30340;&#22581;&#22622;&#12290;2&#12289;[**&#30095;&#36890;&#22320;&#28431;**](http://www.bjbtgdst.com.cn/stdl.htm)&#65306;&#19987;&#19994;&#30095;&#36890;&#21508;&#31181;v&#22411;&#12289;S&#22411;&#25296;&#24367;&#30340;&#22320;&#28431;&#65292;&#65288;&#22240;&#20026;&#35013;&#20462;&#25481;&#36827;&#27700;&#27877;&#12289;&#27801;&#23376;&#25110;&#22836;&#21457;&#31561;&#31181;&#21407;&#22240;&#25152;&#12288;&#12288;&#12288;&#12288;&#12288;&#36896;&#25104;&#30340;&#22581;&#22622;&#65289;&#12290; 3&#12289;&#22699;&#12288;&#22353;&#65306;&#22240;&#20026;&#22699;&#22353;&#24180;&#25104;&#20037;&#20102;&#65292;&#31649;&#36947;&#24367;&#22836;&#20135;&#29983;&#20102;&#19968;&#23618;&#21402;&#21402;&#30340;&#23615;&#30897;&#65292;[**&#39640;&#21387;&#28165;&#27927;**](http://www.bjbtgdst.com.cn/gyqx.htm)&#30001;100MM&#24930;&#24930;&#30340;&#21464;&#25104;&#20102;50MM&#29978;&#12288;&#12288;&#12288;&#12288;&#12288;&#33267;10MM&#29978;&#33267;&#36824;&#20250;&#22581;&#27515;,&#25152;&#20197;&#36896;&#25104;&#22699;&#22353;&#19979;&#27700;&#24930;&#12289;&#26131;&#22581;&#65292;&#26412;&#37096;&#26681;&#25454;&#22810;&#24180;&#25152;&#31215;&#32047;&#32463;&#39564;&#37319;&#29992;&#26368;&#12288;&#12288;&#12288;&#12288;&#12288;&#20339;&#25216;&#26415;&#21644;&#26041;&#26696;&#12289;&#24443;&#24213;&#30095;&#36890;&#21508;&#31181;&#24773;&#20917;&#25152;&#36896;&#25104;&#30340;&#22581;&#22622;&#12290;4&#12289;&#38754;&#12288;&#30406;&#65306;&#19987;&#19994;&#30095;&#36890;&#21508;&#31181;&#38754;&#30406;&#65292;&#21253;&#25324;&#65288;V&#22411;&#12289;S&#22411;)&#31561;&#30340;&#31649;&#36947;&#12290;5&#12289;&#20027;&#31649;&#36947;&#65306;&#26412;&#37096;&#22791;&#26377;&#22823;&#20013;&#23567;&#22411; &#26426;&#26800;&#21644;&#39640;&#21387;&#28165;&#27927;&#26426;&#65292;&#19987;&#19994;[**&#31649;&#36947;&#30095;&#36890;**](http://www.bjbtgdst.com.cn/gdst.htm)&#12290;&#12288;&#12288;&#12288;&#21271;&#20140;&#20445;&#36890;&#31649;&#36947;&#30095;&#36890;&#26381;&#21153;&#37096;&#26412;&#30528;&#20197;&#20449;&#35465;&#27714;&#21457;&#23637;&#65292;1)&#26426;&#26800;&#30095;&#36890;&#21508;&#31181;&#24066;&#25919;&#31649;&#36947;&#65292;[**&#19978;&#19979;&#27700;&#32500;&#20462;**](http://www.bjbtgdst.com.cn/sxswx.htm)&#20027;&#31649;&#36947;&#21644;&#20854;&#20182;&#22823;&#22411;&#22320;&#19979;&#31649;&#36947;&#30340;&#22581;&#22622;&#12290;

---

### Post by nagolchi on 2008-11-14
gspca_main doesn't work.  any ideas anyone?

---

### Post by nagolchi on 2008-11-14
Ok. Finally got the camera working!  Thanks to the post in here:

[http://ubuntuforums.org/showthread.php?t=966932&highlight=e2500](http://ubuntuforums.org/showthread.php?t=966932&highlight=e2500)

I removed all other gspca modules I had loaded (gspca_main, etc).  Used the gspca source from here:

wget [http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz)

and patched using the file posted in the forum link above.  make sure to remove all other gspca modules before running the gspca_build script included in the gspca tar file.  my logitech quickcam e2500 is now working in skype!

---

