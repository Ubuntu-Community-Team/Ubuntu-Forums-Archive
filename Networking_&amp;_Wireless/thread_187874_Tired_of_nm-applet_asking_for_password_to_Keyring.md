---
title: "Tired of nm-applet asking for password to Keyring?"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by s31523 on 2006-06-03
I contacted the new owner of PAM_KEYRING because the version on the net only supported PAM >= 0.99 and he rebuilt version 0.8 of PAM_Keyring that is backwards compatible with older PAM. (For the noobs PAM=Pluggable Authentication Module).  Anyway here is the link:
[http://www.hekanetworks.com/opensource/pam_keyring/](http://www.hekanetworks.com/opensource/pam_keyring/)

Download version 0.8 and GO!  After installing I am :-D about not having to enter my default keyring password after login anymore.

Here are my steps:
1.) Download
2.) Unzip to folder (i.e. ~/install_tmp)
3.) In Terminal:
cd ~/install_tmp
./configure --prefix=/usr --libdir=/lib
make
sudo make install
cd /etc/pam.d
sudo gedit gdm
Mine looks like:
```
#%PAM-1.0
auth	requisite	pam_nologin.so
auth	required	pam_env.so
@include common-auth
@include common-account
session	required	pam_limits.so
@include common-session
@include common-password
## Added so that NetworkManager doesn't keep asking for Keyring password.
## relies on having same password to keyring as login password.
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so

```

IT IS VERY IMPORTANT TO ADD THE ABOVE LINES TO THE END OF THE GDM FILE

After that, reboot, and no password.  BIG Thanks Jon Nettleton for getting this out!

As I mentioned in the comments in gdm file, this relies on having the password of the default keyring the same as your login password.  ENJOY!

---

### Post by mr.lamp on 2006-06-03
Hi, i am really tired of nm-applet asking for the keyring passw. 

But i got different passwords for login and keyring and i don't know how to change the keyring-password :-/

---

### Post by s31523 on 2006-06-03
Not sure if there is a way to change the keyring password, you can try:
[http://www.linuxquestions.org/questions/showthread.php?t=410266](http://www.linuxquestions.org/questions/showthread.php?t=410266)

Best bet would be to change you login password to your keyring password.

Here is the website for PAM_KEYRING, try the suggestions in the testing suggestion.  I have an email out to Jon (new maintainer/owner) so we will see what he says...

[http://www.hekanetworks.com/index.php/publisher/articleview/frmArticleID/25/staticId/31/](http://www.hekanetworks.com/index.php/publisher/articleview/frmArticleID/25/staticId/31/)

---

### Post by Buell on 2006-06-04
This might be obvious to Linux developers but it wasn't to me.

I needed to get a few packages in addition to build-essential to complete the build. 

Using Synaptic get:

libpam0g-dev
libgnome-keyring-dev
libglib2.0-dev
autotools-dev 
libtool 

Also, I got some error messages when the install tried to make links (ln -s) in the /lib/security directory. I fixed it by removing the old links, pam_keyring_auth.so and pam_keyring_session.so, and running the install again.

Now nm-applet starts without asking for a password.   

Thanks s31523 and Jon Nettleton.

---

### Post by dngpng on 2006-06-05
i guess the second problem you encountered is because you had make install once (unsuccessfully) before and left those symbol links in the folder /lib/security/ .

---

### Post by s31523 on 2006-06-05
Jon's response to my question:
> What if my default Key Ring password is different from my login password?  Do I just change what pam_keyring uses my using the pam-keyring-tool?

was:

> In theory yes.  My patches to support changing a keyring's password just got accepted into gnome-cvs.  If you go to the pam_keyring site, you
will see some experimental packages I have that support changing a
password.

So please give it a try and report back to us!

---

### Post by KiLLeR_WoMBaT on 2006-06-05
I get as far as issuing the command 'make' and i get this:

bash: make: command not found

make used to work as a command.  What now?

---

### Post by s31523 on 2006-06-06
Probably need to issue:
```
sudo apt-get install build-essential
```

---

### Post by s31523 on 2006-06-06
Update on PAM_KEYRING, looks like the website has updated support different key ring passwords! Jon emailed me this morning with:
>  I have tarballs for pam_keyring, gnome-keyring, and
gnome-keyring-manager from cvs.  These versions all support changing a
keyring's password.

---

### Post by KiLLeR_WoMBaT on 2006-06-06
[QUOTE=s31523]Probably need to issue:
```
sudo apt-get install build-essential
```[/QUOTE]


Got it...thanx!

---

### Post by ububug on 2006-06-07
This didn't work at all for me. I still get the dialog asking for the default keyring password everytime I start up. I had no errors compiling and building, and i have the gdm file as shown. What could be the problem?

---

### Post by popkid on 2006-06-07
[QUOTE=s31523]Not sure if there is a way to change the keyring password, you can try:
[http://www.linuxquestions.org/questions/showthread.php?t=410266](http://www.linuxquestions.org/questions/showthread.php?t=410266)

Best bet would be to change you login password to your keyring password.

Here is the website for PAM_KEYRING, try the suggestions in the testing suggestion.  I have an email out to Jon (new maintainer/owner) so we will see what he says...

[http://www.hekanetworks.com/index.php/publisher/articleview/frmArticleID/25/staticId/31/](http://www.hekanetworks.com/index.php/publisher/articleview/frmArticleID/25/staticId/31/)[/QUOTE]

To change your PAM keyring, all you need to do is delete the folder 'keyring-blah' from your /tmp/ directory, keyring will then prompt for a new one the next time it fires up

pK

---

### Post by Kawayanan on 2006-06-08
> This looks very nice.  I started through you instructions, but have three soft links from the pam_keyring that are pointing to the wrong place:

config.guess -> /usr/share/libtool/config.guess
config.sub -> /usr/share/libtool/config.sub
ltmain.sh -> /usr/share/libtool/ltmain.sh

I can't find these files anywhere to just fix the links, is there a package I need to install?
Edit:  Ok, I got the above figured out.  I had to try the running configure about 5 or 6 times to find all the packages I needed to install (mostly dev packages).  I got everything though and the install seemed to work.

On another note, is there any reason this should not be added to universe?  It would make it a lot more straight forward for people to install if it could be done using synaptic to determine all the dependancies.  Does it just need someone to make the packages and submit it? (not sure of the procedure...will look into it)

Kawayanan

Thanks again to everyone here.  I put together a howto from this and it should be posted in the howto and tips forum soon.

---

### Post by HunterPro on 2006-06-10
I too would prefer a package for this one. Compiling it has somehow been somewhat of a bitch, had to manually apt-get loads of stuff. And now, it tells me I need 'gnome-keyring-1' which isnt in the repositories and not on disk, too.

> checking for gnome-keyring-1... Package gnome-keyring-1 was not found in the pkg-config search path. Perhaps you should add the directory containing `gnome-keyring-1.pc' to the PKG_CONFIG_PATH environment variable No package 'gnome-keyring-1' found
configure: error: Library requirements (gnome-keyring-1) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


Anybody got any ideas on that part? Usually i dont really have problems with a bit more hacking and slashing, but this just doesn't make any sense. :)

---

### Post by freddo on 2006-06-10
This is one of the reasons why people don't bother to go for linux, should be some easy click in gnome imho...

---

### Post by ToneDispenser on 2006-06-11
I get the same error HunterPro gets.
Has anyone figured out where to get that package?

---

### Post by ToneDispenser on 2006-06-11
arrr... found it :)

```
apt-get install libgnome-keyring-dev
```

after installing, everything worked as described
in the first post of this Thread!

thanks :)

---

### Post by ToneDispenser on 2006-06-11
I'm still being asked for the password.
The applet says it has to ask since the defualt keyring file is locked.

i tried the following
sudo chmod 0666 .gnome2/keyrings/default.keyring

but i had no success...
any ideas?

---

### Post by joe_bling on 2006-06-11
I've installed all of the packages, yet I get this every time I run ./configure:

checking security/pam_modules.h usability... no
checking security/pam_modules.h presence... no
checking for security/pam_modules.h... no
configure: error: You are missing security/pam_modules.h

......and the configure bombs out.

pam_modules.h is not on my system. What package provides this?

---

### Post by roboguy on 2006-06-12
Just wanted to say thanks very much to s31523. The continual prompting was driving me insane!

Cheers!
Roboguy

---

### Post by s31523 on 2006-06-13
No problem.  Just sharing what I found.

In response to:
> This is one of the reasons why people don't bother to go for linux, should be some easy click in gnome imho...
True, but its forums like these that will get Linux to the "it just works" stage.  I have said this before I will say it again, Linux, especially Ubuntu, is in a state now that Windows 95 was in way back when it was brought out, that is, for the most part things worked out of the box but more often than not you had to play around in DOS and edit congi files and mess around.  With communities like this we will take Linux to a whole new level. Plus, have you ever gotten this kind of support for M$?  I tried calling them once a few years back, and man it was like ](*,)

---

### Post by ububug on 2006-06-14
I still cannot seem to get this to work for me. I have gdm set to autologin could this be the problem? Is there any way around it?

---

### Post by ububug on 2006-06-17
Can anyone help me?

---

### Post by yopnono on 2006-06-26
File removed it don't work anymore...

---

### Post by taj on 2006-06-27
yopnono, thanks for your deb file. I suggest that for the less experienced an updated and complete deb package will be put into the dapper repositories.
General problem: network-manager is not configurable enough. It easily connects to unwanted networks as well. Indeed, as said: this is the first linux programme I know that can hardly be configured.

I really like the ease of use of network-manager, but, as previously said as well: software with such behaviour puts people off.

---

### Post by sbc25a on 2006-07-03
[QUOTE=yopnono]I have created a .DEB file, please try it. You still need to add the.
cd /etc/pam.d
sudo gedit gdm

```

## Added so that NetworkManager doesn't keep asking for Keyring password.
## relies on having same password to keyring as login password. 
auth optional pam_keyring.so try_first_pass 
session optional pam_keyring.so

```
IT IS VERY IMPORTANT TO ADD THE ABOVE LINES TO THE END OF THE GDM FILE[/QUOTE]


I've done this (using Dapper) but I am still being asked for the keyring password.  Any ideas?  I also am periodically asked to re-enter my passphrase.

---

### Post by smpeck on 2006-07-05
[QUOTE=sbc25a]I've done this (using Dapper) but I am still being asked for the keyring password.  Any ideas?  I also am periodically asked to re-enter my passphrase.[/QUOTE]

Same issue here - I'm still being prompted for the password. Will this work if GDM is set to auto-login? This is for a kiosk application and the prompt for a login is not acceptable for our usage...

---

### Post by EuphoricaL on 2006-07-06
excellent, the deb worked great.
thanks, no more three annoying password dialogs on login

---

### Post by juan_suave on 2006-07-07
That .deb worked perfectly.  Thank you so much!  This problem has bugged me for the last 3 minutes, as I just got my wireless working.  Finally an answer. :D

---

### Post by hyapadi on 2006-07-09
It works very well. I guess you should ask the thread starter to update his guide with this .deb file. Thank you very much.

---

### Post by hyapadi on 2006-07-12
Today I updated the linux kernel when I performed apt-get update & upgrade.

Since then, the keyring prompt started to occurs again during start up. Any ideas? thx

* updated *
I did another reboot and the prompt is not appearing again. I'll report the progress after trying several reboots.

---

### Post by summetone on 2006-07-12
That happened to me as well, but I just removed the pam-keyring package and reinstalled it. Might have resolved itself with a reboot, but I didn't have that much patience.

---

### Post by mech7 on 2006-07-13
I get this error..

> 
chris@acerChris:~/keyring$ ./configure --prefix=/usr --libdir=/lib
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
configure: error: cannot run /bin/sh ./config.sub


---

### Post by mech7 on 2006-07-13
mmm i cant edit gdm file :(
also with right click open as root in gedit it hangs :(
when i just click on it it loads normally but is read only ?

---

### Post by AlphaMack on 2006-07-14
Tried the instructions to the letter on two up-to-date Dapper machines without success.  I still keep on getting (often multiple) dialogs. ](*,)

---

### Post by mech7 on 2006-07-15
ok now i reinstalled and it worked.. but i still have to enter the password?

---

### Post by nrayever on 2006-07-17
holy cow!! that's a great solution! easy to install and very handy!:-D :-D

---

### Post by wile_e8 on 2006-07-20
I seem to be getting the same problems as a lot of people on this thread (ububug, sbc25a, smpeck, alphasubzero949) in which everything seems to install fine, but it won't authorize and still asks me for the keyring password.  I also get multiple password boxes occasionally.  I do use autologin to my account, but it still wouldn't authorize even after I switched back to regular login.  Is there any way to check if there are errors occuring with PAM?  I mean, can I see if it's attempting to authorize nm-applet but getting errors, or if it's not even trying for some reason?  I know a few of us are stuck on this.

---

### Post by kronepils on 2006-07-30
It does seem like gdm with autologin is the problem.
It works great for me when I login from gdm, but with autologin the login is really "used".
I tried adding the lines in /etc/pam.d/gdm-autologin, but then X wouldn't start....

Any ideas on autologin??

---

### Post by mssever on 2006-08-06
> **yopnono said:**
> I have created a .DEB file, please try it. You still need to add the.
cd /etc/pam.d
sudo gedit gdm

```

## Added so that NetworkManager doesn't keep asking for Keyring password.
## relies on having same password to keyring as login password. 
auth optional pam_keyring.so try_first_pass 
session optional pam_keyring.so

```
IT IS VERY IMPORTANT TO ADD THE ABOVE LINES TO THE END OF THE GDM FILE

Thanks a bunch!

---

### Post by skirkpatrick on 2006-08-06
Well, I found that you DON'T want to add those lines to gdm-autologin!

---

### Post by helmut_hed on 2006-08-10
What if you don't want to use the keyring, or PAM?

I just want network manager to prompt me for the key for the network, once each time I connect to it, and I don't want it to try to use the keyring at all.  I've just been hitting "deny" each time, but it's annoying.  Is there a simple configuration change to tell nm-applet "don't bother with the keyring"?

Thanks,
Jeff

---

### Post by gannic on 2006-08-19
Can anyone help?...I get this when installing and I get password requests exactly as before...

Making install in src
make[1]: Entering directory `/home/myuser/Desktop/pam/src'
/bin/sh ../libtool --tag=CC --mode=link gcc -g -Werror -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/gnome-keyring-1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2   -o pam-keyring-tool  pam-keyring-tool.o  -lgnome-keyring
gcc -g -Werror -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -o pam-keyring-tool pam-keyring-tool.o  /usr/lib/libgnome-keyring.so /usr/lib/libglib-2.0.so
pam-keyring-tool.o: In function `main':/home/myuser/Desktop/pam/src/pam-keyring-tool.c:205: undefined reference to `gnome_keyring_change_password_sync'
collect2: ld returned 1 exit status
make[1]: *** [pam-keyring-tool] Error 1
make[1]: Leaving directory `/home/myuser/Desktop/pam/src'
make: *** [install-recursive] Error 1

---

### Post by orb9220 on 2006-08-19
I would also like an answer to this problem. Why should I be prompted for keyring password when I am connecting to an open connection?

Is there a way to disable the keyring all together?
It should work like helmut_hed above has stated?

---

### Post by stevieb on 2006-08-26
This howto worked perfectly for me using the .deb file and adding the lines to the gdm file.  I have a Lenovo 3000 C100 running Dapper and FiOS wireless.

I agree that this should be in the repositories.

thanks,
-steve

---

### Post by Anthem on 2006-08-28
Before I install this, can anyone confirm that they've gotten it working with autologin?

---

### Post by eg-maverick on 2006-08-28
Thanks for the straightforward instructions. It worked for me. Thanks.
Craig

---

### Post by skirkpatrick on 2006-08-29
> **Anthem said:**
> Before I install this, can anyone confirm that they've gotten it working with autologin?

I don't think anybody has yet.

---

### Post by Anthem on 2006-08-30
> **skirkpatrick said:**
> I don't think anybody has yet.
Yeah, that's what it sounded like.

---

### Post by oke on 2006-09-11
> **popkid said:**
> To change your PAM keyring, all you need to do is delete the folder 'keyring-blah' from your /tmp/ directory, keyring will then prompt for a new one the next time it fires up

pK

This didn't work for me.  However, removing 'default.keyring' from ~/.gnome2/keyrings/ did the job.

---

### Post by andrewski on 2006-09-11
> **oke said:**
> This didn't work for me.  However, removing 'default.keyring' from ~/.gnome2/keyrings/ did the job.
Does this delete all presently stored passwords in the keyring?

---

### Post by TheRedge on 2006-09-11
Heh, here's something funny for you, help please.

I have a broadcom 4318 wireless pci card, and i had some problems installing the drivers. I got it installed though with ndiswrapper, but for some reason this nm-applet keeps screwing it up. I can't connect a wireless lan becouse of this.
I know it's the nm-applet cuz when i delete keyring and reboot it works, but only for that seession. :confused:

Why is this happening? ](*,)

---

### Post by eg-maverick on 2006-09-11
> **oke said:**
> This didn't work for me.  However, removing 'default.keyring' from ~/.gnome2/keyrings/ did the job.

This seemed to work for me as well. Thanks.

---

### Post by canarsie on 2006-09-12
I was following s31523's instructions in the first post, but when I enter the make command, I get the error:

make: *** No targets specified and no makefile found.  Stop.

How do I specify the file and which file should I be specifying?

---

### Post by mssever on 2006-09-12
> **canarsie said:**
> I was following s31523's instructions in the first post, but when I enter the make command, I get the error:

make: *** No targets specified and no makefile found.  Stop.

How do I specify the file and which file should I be specifying?

Did you forget the ./configure step? When ./configure finishes--and only if there were no errors encountered--./configure automatically generates the Makefile. Use the configure command provided by s31523. If configure reports any errors--such as missing dependencies--you must fix them and re-run configure before continuing.

---

### Post by canarsie on 2006-09-12
thanks.

---

### Post by andrewski on 2006-09-12
> **yopnono said:**
> I have created a .DEB file, please try it. You still need to add the.
cd /etc/pam.d
sudo gedit gdm

```

## Added so that NetworkManager doesn't keep asking for Keyring password.
## relies on having same password to keyring as login password. 
auth optional pam_keyring.so try_first_pass 
session optional pam_keyring.so

``` IT IS VERY IMPORTANT TO ADD THE ABOVE LINES TO THE END OF THE GDM FILE
Just a reminder: you don't need to wrangle with configuring/compiling pam-keyring, because **there's a package**.  Much easier, eh? :-\"

---

### Post by oke on 2006-09-12
> **andrewski said:**
> Does this delete all presently stored passwords in the keyring?

Yes, it does. But again you are prompted for a new to set password and that is where it was all about :D .

---

### Post by andrewski on 2006-09-12
> **oke said:**
> Yes, it does. But again you are prompted for a new to set password and that is where it was all about :D .
Yes, this is true.  However, I just wanted to know ahead of time before I do this.  Thanks. :)

---

### Post by yopnono on 2006-09-15
deleted

---

### Post by spiral out on 2006-09-15
> **yopnono said:**
> Ok. have a new pam-keyring.deb that setup the gdm file as well during install.

Please test and tell me if it works.
All it does is installing the files and also makes a backup of the gdm files and then it adds the entry to the gdm file.



Ok, I tried it but it's not working for me (as the same with manual install), still asking for the password... 
Hoped that the deb fixed something i forgot... :roll:

I'm using a XFCE desktop but that can't be the problem, i assume?

---

### Post by yopnono on 2006-09-15
> **spiral out said:**
> Ok, I tried it but it's not working for me (as the same with manual install), still asking for the password... 
Hoped that the deb fixed something i forgot... :roll:

I'm using a XFCE desktop but that can't be the problem, i assume?

Did you shutdown and and tried.

---

### Post by spiral out on 2006-09-15
> **yopnono said:**
> Did you shutdown and and tried.

Yes, it's like the Win95 old days :D
I reboot a lot!

Removed all the previous installs from pam-keyring and tried it again with the deb, it's still not working... 

I also killed the gnome-keyring-deamon and the nm-apllet before install.

---

### Post by yopnono on 2006-09-15
:) Arghh well ok thanks anyway.

---

### Post by andrewski on 2006-09-16
> **yopnono said:**
> Ok. have a new pam-keyring.deb that setup the gdm file as well during install.

Please test and tell me if it works.
All it does is installing the files and also makes a backup of the gdm files and then it adds the entry to the gdm file.
```
## Added so that NetworkManager doesn't keep asking for Keyring password.
## relies on having same password to keyring as login password. 
auth optional pam_keyring.so try_first_pass 
session optional pam_keyring.so
``` 
If you uninstall it will restore the backup file and remove the modified file and also the old backup.

(I have not tried it on networkmanager don't have it, but it don't ask for the keyring when opening the network folders. And have not tried it if it works with autologin.)
By the way, this package complains if the files /etc/pam.d/gdm_bak and /etc/pam.d/gdm-autologin_bak don't exist.  Creating them before installing seems to be enough.

---

### Post by yopnono on 2006-09-16
> **andrewski said:**
> By the way, this package complains if the files /etc/pam.d/gdm_bak and /etc/pam.d/gdm-autologin_bak don't exist.  Creating them before installing seems to be enough.

Just ignore this .DEB I will delete it. It don't work.

EDIT:
File deleted.

---

### Post by spiral out on 2006-09-16
> **yopnono said:**
> Just ignore this .DEB I will delete it. It don't work.

EDIT:
File deleted.

It worked for me! I did a fresh install with Gnome desktop, installed my wireless nic, removed everything from /etc/network/interfaces (except the settings for lo), installed network-manager, connected to wpa-wireless-network, used login password for Keyring. 
Then i installed the deb, it's working!

Cheers!


ps: I think pam-keyring doesn't work with Xfce-desktop...

---

### Post by dtux on 2006-09-21
> **smpeck said:**
> Same issue here - I'm still being prompted for the password. Will this work if GDM is set to auto-login? This is for a kiosk application and the prompt for a login is not acceptable for our usage...

I also have auto-login set on my laptop with Dapper and I'm still being prompted for Keyring password.

Any work around for this? I'm sure I've got everything else setup as described in previous posts.

cheers

---

### Post by skirkpatrick on 2006-09-21
I don't think anybody's got a solution yet.  If you disable auto-login, you won't get the keyring password but you have to login at the boot screen.

---

### Post by jwal on 2006-09-23
The purpose of a keyring is to allow you to store multiple pieces of highly confidential information (such as passwords) as cyphertext on your hard disc and access them with a minimum number of password prompts.  This minimum number is 1.

To connect to the encrypted network without supplying even one password it is necessary to store the network passphrase on the disc as plain text (unencrypted).  This is exactly what a keyring agent is trying to avoid.

In order to connect to an encrypted network without any password prompts (not even from PAM/gdm) you must somehow tell NetworkManager not to use a keyring.  I don't use NetworkManager so I do not know if this is possible -- all I know is that using a keyring to store a secret which you want to "unlock" without a password is the wrong approach.

Unfortunately I do not know the best way to solve this problem.  I am still using a manually configured [FONT="Courier New"]/etc/wpa_supplicant.conf[/FONT] file that includes a line holding my WPA pre-shared key.

---

### Post by foureight84 on 2006-09-28
i can't get this thing to work. does my log in password have to be the same as my access point password? anyway... i'm gonna remove this. even after trying on a fresh install it still won't work. the keyring dialog is soooooo annoying.

---

### Post by zenwhen on 2006-09-28
Threads like this are why I love these forums. The instructions in the original post are perfect, along with the post a few posts down describing the needed dependencies.

---

### Post by eg-maverick on 2006-09-29
> **zenwhen said:**
> Threads like this are why I love these forums. The instructions in the original post are perfect, along with the post a few posts down describing the needed dependencies.

Unfortunately this post isn't completely correct. The first post did in fact work until a system update broke it. Now it doesn't work - guaranteed.

---

### Post by compmodder26 on 2006-09-30
This hasn't worked for me either.  The pam_keyring module is installed properly and the gdm file is edited properly.  I'm not using autologin and my login password is the same as my keyring password.  But I'm still being prompted for my keyring password.

---

### Post by falkenberg_cph on 2006-10-03
> **mech7 said:**
> I get this error..

Quote:
chris@acerChris:~/keyring$ ./configure --prefix=/usr --libdir=/lib
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
configure: error: cannot run /bin/sh ./config.sub
Reply With Quote

You have missed installing LIBTOOL. Worked for me

Thanks :D

---

### Post by zordon on 2006-10-07
> **compmodder26 said:**
> This hasn't worked for me either.  The pam_keyring module is installed properly and the gdm file is edited properly.  I'm not using autologin and my login password is the same as my keyring password.  But I'm still being prompted for my keyring password.

got into same situation; so is now the only way out of multiple-password entry installing unstable NM7 from CVS?

---

### Post by valnar on 2006-10-29
> **compmodder26 said:**
> This hasn't worked for me either.  The pam_keyring module is installed properly and the gdm file is edited properly.  I'm not using autologin and my login password is the same as my keyring password.  But I'm still being prompted for my keyring password.

Same here.  Is there a new HowTo to make this work on Dapper with all the current updates?

Robert

---

### Post by loko on 2006-10-31
is there any progress on this problem?

---

### Post by foureight84 on 2006-11-02
well to get it working, just read the first 4 threads. it works correctly given that you have libpam0g-dev libgnome-keyring-dev libglib2.0-dev autotools-dev libtool installed.

so here's how to do it:
download pam-keyring 0.80 like it was said in the first thread [http://www.hekanetworks.com/opensource/pam_keyring/](http://www.hekanetworks.com/opensource/pam_keyring/)

then install all the dependent packages:
```
sudo apt-get install libpam0g-dev libgnome-keyring-dev libglib2.0-dev autotools-dev libtool
```

install checkinstall also (this creates a deb package so you can remove it)
```
sudo apt-get install checkinstall
```

tar the pam-keyring, cd into the directory then 
```
sudo make && sudo checkinstall -D make install
```

after it finishes installing, you should change your login password to the same as your keyring password.
```
sudo passwd yourusername
```

don't use autologin, you will be prompted to input the nm-applet password. in either case you will need to enter a password atleast once.

---

### Post by andrewski on 2006-11-02
> **foureight84 said:**
> well to get it working, just read the first 4 threads.
Could the howto be updated so that people don't have to sift through the subsequent posts?

---

### Post by pwaller on 2006-11-06
So is the current consensus that the pam_keyring module doesn't have any effect on the latest edgy? I followed the instructions word for word and it had no effect.

Is there any way around this other than NM7, and does NM7 not asking for a password still depend on pam_keyring ?

 - Pete

---

### Post by skirkpatrick on 2006-11-06
It works under Edgy for me but this machine was upgraded from Dapper.  I had it working in Dapper.

---

### Post by pwaller on 2006-11-06
I just did a fresh install from scratch. I previously upgraded from dapper but the network manager didn't work.

Currently pam_keyring doesn't provide a solution.

- Pete

---

### Post by SuperProg27 on 2006-11-11
hi, i would like to hear you guys opinion about the security of this, if somene stoll the computer, how hard would it be te retreive the login password from  /etc/shadow ? 
is it harder than cracking the keyring file?
what encryption level  uses the keyring file?

---

### Post by BlaY0 on 2006-11-14
For all you guys with gdm autologin...

It doesn't work and it won't work, period! At least not in this kind of design. The reason why is in how this thingie works. When you log in it grabs your password you typed and hand it over to keyring-daemon so it could seamlessly unlock the default keyring (thatswhy both passwords have to be the same). When U log in via autologin... there are actually no credentials being checked for this session. Why's that? Because in autologin mode there is another pam modul being used (pam_permit) which lets U in without entering the password. So, if there was no password being typed then there is nothing for pam_keyring to be done.

Besides try_firs_pass pam_keyring also accepts use_first_pass, keyring= and debug options. At least debug can be handy in searching for the clues why your inplementation isn't working as it should.

One possibility just poped up in my mind (while I'm typing) for you autologin guys. Try to set blank password for your default keyring. I know there's no point of doing this in terms of security but then again autologin isn't really secure either.

Regards,

B

---

### Post by BlaY0 on 2006-11-14
> **SuperProg27 said:**
> hi, i would like to hear you guys opinion about the security of this, if somene stoll the computer, how hard would it be te retreive the login password from  /etc/shadow ? 
is it harder than cracking the keyring file?
what encryption level  uses the keyring file?

Security is stron as its weakest link is. In this case it depends on your system password hash and length of your password. In your case I believe it is md5 hash. For gnome keyring I'm not sure... I will have to look in to the code but right now I don't have the time for doing this.

---

### Post by noxxle on 2006-11-30
My network manager automatically connects me to wireless even if a wired connection is present. Is there a way to change that? I would prefer it choose wired over wireless, in fact i would prefer my computer boot up with wireless disabled unless i turn it on.

---

### Post by msmarino on 2007-01-03
> **BlaY0 said:**
> For all you guys with gdm autologin...

It doesn't work and it won't work, period! At least not in this kind of design.

Ok.  So attempting a different tack (sorry if somebody's already suggested this):

Is there any way to change the keyring nm-applet uses? I run edgy in Spanish and it has two keyrings open (default & sesión) the point being that the session seems to unlock the second, so if nm-applet could be redirected to use that one it may not ask for a password even on auto-login?

Oh, and pam-keyring-0.8.0 works ok for me (except auto-login, of course!) so a big thanks for that.

---

### Post by s31523 on 2007-01-10
Update!

Just installed on a fresh Edgy install.  In addition to the noted things above that need to be gotten there are two more: libtool and libpam0g-dev.

Just thought I'd update things.  I used the GUI for synaptic, so search for the above two things.

---

### Post by pveijden on 2007-02-04
Making pam_keyring work for me on a fresh edgy required the following additional modules installed:

sudo apt-get install build-essential
sudo apt-get install libtool
sudo apt-get install libpam-dev
sudo apt-get install libgnome-keyring-dev
sudo apt-get install libglib2.0-dev

Without the above you will get strange errors like:
configure: error: cannot run /bin/bash ./config.sub

This is because config.sub is a symlink to libtool and without libtool installed the config.sub doesn't resolve.

Now it works like a charm!

---

### Post by valnar on 2007-02-04
Instead of starting a new thread, does anyone know if all this is resolved in Feisty?

Robert

---

### Post by andrewski on 2007-02-12
> **valnar said:**
> Instead of starting a new thread, does anyone know if all this is resolved in Feisty?

Robert
It is; libpam-keyring was just added today. However, I can't get the  friggin' pam-keyring package to remove.

---

### Post by andrewski on 2007-02-12
> **andrewski said:**
> By the way, this package complains if the files /etc/pam.d/gdm_bak and /etc/pam.d/gdm-autologin_bak don't exist.  Creating them before installing seems to be enough.
OK, I got the package to delete; I had to `touch` these files again. The output from apt-get/dpkg wasn't helpful at all. BLARGH

---

### Post by nicktrik on 2007-02-14
I've switched to wifi-radar which is stable and does not ask for any passwords at log in. The only password required is when accessing the wireless network initially.

---

### Post by wile_e8 on 2007-02-14
Are there any instructions on how to switch from network-manager to wifi-radar?  Or do I just install the package and remove nm-applet from the startup programs?

---

### Post by valnar on 2007-02-14
Unless WiFi Radar got better since I last looked at it, it didn't have all the functionality of Network Manager.  If you need advanced WPA support like EAP and 802.1x, stick with Network Manager.

Robert

---

### Post by unite07 on 2007-02-18
at some point pam-keyring was taking care of unlocking the keyring. sence upgrading to edgy, it does not. Instead two password promts apear after login.

I also tried the script to call pam-keyring-tools after autologin, but that opens "i swear" opens three password promts

I have deleted and recreated my default.keyring, i have reinstalled pam-keyring-0.0.8. and have rebooted too many times

the functionality of easy startup is very important for my specific project 

any help is greatly appreciated

---

### Post by valnar on 2007-02-18
Have you tried the latest Feisty Alpha?

---

### Post by unite07 on 2007-02-18
no i am trying to stay stable.  I did however get it to work on a fresh install. so i must have screwed some other config file up?

---

### Post by nzruss on 2007-02-18
Well, I followed the instructions and installed all the bits needed for compiling. 

It all installed fine.  Perfect for the traveler with the laptop.  

However, I'm in the same situation with a WPA network (which I understand rules out wi-fi radar), and need auto-login as this will be my main Mythtv HTPC. 

I understand wi-fi manager doesn't offer wpa support - i did some searching and it looks like it does, but there is discussion there about using Pam for authentication so dont know if i'll end up back where i am, but with wi-fi radar /Pam instead. 

Would really like to get this resolved. Am interested in any other approach/hack to get through this. I dont mind the wireless key being stored in the clear, (you'd need to already be inside my network to get it anyway, so i'd have bigger problems than someone then finding my house and stealing my wi-fi)

[added 8:02pm 18 Feb]
I found the answer here. 
[http://www.ubuntuforums.org/showthread.php?t=316927](http://www.ubuntuforums.org/showthread.php?t=316927)
I followed those instructions and it got me going. (note my post at the end with the "chown" of a folder)

---

### Post by pbunyan on 2007-02-23
Bah! i cant get this working either :(

im running a fresh install of Edgy Eft 64 bit, ive installed the it as per the guide using the pam_keyring-0.0.8-1.fc5.x86_64.rpm file from [http://www.hekanetworks.com/opensource/pam_keyring/](http://www.hekanetworks.com/opensource/pam_keyring/), and also using the normal 32bit version, and niether work. they install correctly, but i still get asked for my keyring password. my keyring password and my login password are the same. and ive edited the gdm file, restarted and tried installing all the libraries listed in this thread, but it still wont work :(

ive tried to uninstal it and try again, but i cant figure out how to uninstall it either

if you can't tell in a newbie ;)

---

### Post by hyapadi on 2007-04-21
I'm using ubuntu 7.04 and it still asking about the keyring everytime the computer start.

Is the package can be used for feisty?

Thanks

---

### Post by Rinzwind on 2007-04-21
Me too.

I have the same pwd for login and keyring.
I also added the lines in bold:

> $ more /etc/pam.d/gdm
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so
@include common-auth
@include common-account
session required        pam_limits.so
@include common-session
@include common-password
[b]auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so[/b]

To no avail. 
Deleting the keyring from System/Administration/Keyring manager also doens't work. 

Acc. to my changes to edgy adding those 2 lines was enough :(

---

### Post by andrewski on 2007-04-21
> **hyapadi said:**
> Is the package can be used for feisty?
 
The package in Feisty is libpam-keyring, included (IIRC) in the Universe repository. This package should be uninstalled. (However, as I mentioned earlier in the thread, I've been unable to completely remove it.)

---

### Post by seeklinux on 2007-04-21
Worked fine for me. I have a fresh feisty installation. I had to install some of the extra packages mentioned in Buell's post (4th one down I believe), but once I had those, I was able to build things fine.

Of course I had to change my keyring password to match my login password, which I did by removing the default keyring file. The next time I booted up it asked first for the WPA passphrase again and then a keyring password.

After that I set up the /etc/pam.d/gdm file as instructed, rebooted, and it didn't ask for the keyring password any more and I got connected to my wireless.

---

### Post by hyapadi on 2007-04-22
> **seeklinux said:**
> Worked fine for me. I have a fresh feisty installation. I had to install some of the extra packages mentioned in Buell's post (4th one down I believe), but once I had those, I was able to build things fine.

Of course I had to change my keyring password to match my login password, which I did by removing the default keyring file. The next time I booted up it asked first for the WPA passphrase again and then a keyring password.

After that I set up the /etc/pam.d/gdm file as instructed, rebooted, and it didn't ask for the keyring password any more and I got connected to my wireless.

Could you update the step by step guide to do that?

Thanks

---

### Post by seeklinux on 2007-04-23
OK, as was stated elsewhere you need the following packages to compile successfully:

libpam0g-dev
libgnome-keyring-dev
libglib2.0-dev
autotools-dev
libtool 

So go to System->Administration->Synaptic Package Manager

and search for these.  Some I had already, some I did not. So install the ones you don't have already.

Next download the [fixed keyring package]("http://www.hekanetworks.com/opensource/pam_keyring/pam_keyring-0.0.8.tar.gz"). I would suggest downloading it either to your home directory or /tmp.  Then open a terminal, **cd** to the directory where you downloaded the file, and execute the command:

tar -xzf pam_keyring-0.0.8.tar.gz

This will create a subdirectory named **pam_keyring-0.0.8**.  Use the **cd** command to go into that directory and do the steps from the original post starting with:

./configure --prefix=/usr --libdir=/lib

but if you need to change your keyring password, don't bother to reboot yet. If you do not already have your keyring password matching your login password and need to change it, the only way is apparently to remove your keyring file and start over. If you are willing to do that then:

cd ~/.gnome2/keyrings
/bin/rm default.keyring

So at this point you should reboot. If you deleted your default keyring so you could change the file, you will need to enter your WPA passphrase or whatever again in the Network Manager and then it will ask you for your new keyring password. This time make it the same as you login password.

At this point you should be all set.  The next time you login it should not ask for the keyring password.

---

### Post by h6w on 2007-04-24
Beware, this won't work if "Enable Automatic Login" is checked in gdm setup (System->Administration->Login Window->Security(tab)"

Tested with Feisty.

---

### Post by hammedhaaret on 2007-05-12
love you guys... thx

---

### Post by Dfects on 2007-05-18
I love you guys long time :) <3

---

### Post by cornelius2 on 2007-07-05
Very useful tip you have here. The thing that I most hated on ubuntu was the need to enter a second password for wireless. I'm wondering why such an obvious "feature" is not still in gutsy. And it's really ok to use the same password for gnome keyring by default. I mean who on earth would want to type another password every time he/she logs in? Users will be pissed if you make them have to type an extra password every time for no apparent reason. Come on Ubuntu developers/packagers, wasn't this obvious? This is a serious usability flaw and also a regression from a user point of view, when they switch from another os. It's things like this that keep people from switching (plus hardware problems and lack of some commercial software of course). Thus, including this by default should be considered a step in fixing Bug #1.

Is there a place on the forum to post this feature as a suggestion for inclusion by default? I couldn't see it on the main page.

Thanks.

---

### Post by mssever on 2007-07-05
> **cornelius2 said:**
> Is there a place on the forum to post this feature as a suggestion for inclusion by default? I couldn't see it on the main page.
Posting bug reports or feature requests on the forum doesn't do much good since the developers don't frequent the forum. The place to do it is the appropriate bug tracker. Ubuntu's bug tracker is at [https://bugs.launchpad.net]("https://bugs.launchpad.net"). The Gnome bug tracker is [http://bugzilla.gnome.org](http://bugzilla.gnome.org).

This issue is a network manager issue, not an Ubuntu issue, so it should be reported on network manager's bug tracker (they're part of Gnome).

Here's a bug that I filed: [http://bugzilla.gnome.org/show_bug.cgi?id=444607](http://bugzilla.gnome.org/show_bug.cgi?id=444607). They say that they're working on this bug.

---

### Post by Goliath! on 2007-07-07
Thanks! thanks! thanks!

***Note: ***You must completely remove default.keyring from ~/gnome2/keyrings.  Just renaming the file doesn't work.

I don't trust myself to go around deleting files will-nilly.  Instead, I rename them so the program using them won't find them.  So I renamed default.keyring to default.keyring.old.  And the fix did not work.

I rm'd the file altogether, rebooted, and all was peachy!!

---

### Post by johnnydough69 on 2007-07-09
Thanks.  It worked well for me.

With one small hitch to be mindful of.

Prior to my install I had checked "Enable Automatic Login" on the "Security" tab of the "Login Window Preferences" dialog.

I couldn't get "Network Manager" to start without prompting for password. I checked and rechecked everything on the pam_keyring install and everything appeared right.

Curious, I disabled automatic login and rebooted.

Lo, I logged in with my password and network manager started without prompting for my password again.

Thought this might save the unwary later.

And thank you Buell for the heads up on the dependencies.

---

### Post by rackoon on 2007-08-11
Just a short note before you start compiling from the sources: Meantime there exists a package libpam-keyring [http://packages.ubuntu.com/feisty/admin/libpam-keyring](http://packages.ubuntu.com/feisty/admin/libpam-keyring)
As stated in /usr/share/doc/libpam-keyring/README.Debian you have to add "@include common-pamkeyring" at the end of your /etc/pam.d/gdm. It might not work with different passwords for login and keystore, but since I use Ihe same for both, works well for me.

---

### Post by porcorosso on 2007-08-16
I was really annoyed by network-manager's behavior with respect to the keyring manager, too. I find both applications to be appallingly badly done -- from an end user's perspective. Being unable to change the primary password on the keyring manager is, unless I'm missing something incredibly obvious, stupid beyond belief. If you could do that (without shutting down the daemon, deleting the hidden file, restarting the daemon, and creating a new keyring just to change passwords) then at least you could keep it synchronized with your logon password. I mean -- DANG! As it is, you have to compromise the security they were trying to ensure in order not to be driven nuts by the thing.

I go to 3-4 different locations (besides home) every danged day! This is just dumb.

But I stumbled upon what looks to me to be an easier solution earlier today. It's at [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/"). Did any of you take a look at that? What do you think of it vs. the PAM keyring solution?

I installed it, and it works VERY well for me. Lets me switch among my hard connected and wireless networks from one location. And no more annoying keyring password popup.

I change my logon password every 30 days. I'm not going to create a new keyring every darned month. Not happening.

Forgot to mention: If you follow the instructions on the download page you get the download through the Synaptic package manager and set up the repository for automatic updates. It automatically uninstalls the network-manager stuff when it installs Wicd. And the addition of the tray applet just puts icing on the cake.

---

### Post by mssever on 2007-08-16
> **porcorosso said:**
> But I stumbled upon what looks to me to be an easier solution earlier today. It's at [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/). Did any of you take a look at that? What do you think of it vs. the PAM keyring solution?

I installed it, and it works VERY well for me. Lets me switch among my hard connected and wireless networks from one location. And no more annoying keyring password popup.

I change my logon password every 30 days. I'm not going to create a new keyring every darned month. Not happening.

Forgot to mention: If you follow the instructions on the download page you get the download through the Synaptic package manager and set up the repository for automatic updates. It automatically uninstalls the network-manager stuff when it installs Wicd. And the addition of the tray applet just puts icing on the cake.

Thanks for mentioning wicd. I think that there are a few other options, too. I agree that nm-applet and gnome-keyring-manager are dumb (although the g-k-m devs are working on some fixes). Unfortunately, I'm stuck with nm-applet as it's the only one that both works with my hardware and supports WPA (and I'm not about to use WEP). All this to say that there are options for many people, but some of us are stuck.

---

### Post by porcorosso on 2007-08-16
I wonder if we're talking about the same software? It appears that the wicd I installed does do WPA 1/2. At least it's working for me here. New version, perhaps?

Anyway, it lets me switch between wired and wireless connections, or create new connection profiles, very easily. Just click on the tray icon, and the applet pops up. The interface is very clean and logical. It lets you set a different set of parameters (fixed IP addresses, DHCP, whatever) for each profile.

I'm curious about it not working with your hardware. I didn't know there could be anything hardware-specific about an application with this function. Oh, unless it has to do with how it ties in with the driver's support for WPA. Is that it?

---

### Post by imdano on 2007-08-16
There is some dependence on the driver you're using, but I've never heard of anyone being unable to use wicd when NetworkManager is working (unless of course that really is the case for mssever).

---

### Post by mssever on 2007-08-16
It's been a while since I tried wicd, along with MadWiFi and I think something else, too, so I don't remember what my problem was with wicd (and it may have been due to an old version).  But my wireless card is weird. It's a Broadcom 4306 (IIRC) and it only works at 11M with the bcm43xx driver. Supposedly, it works with ndiswrapper, but I've never gotten ndis working. So, either I've been doing something wrong, or my card is weird.

At any rate, since my wireless is working, I'm not messing with it.

---

### Post by imdano on 2007-08-16
Oh alright, I think a few people have used wicd with that card/driver without a problem.  Development has been moving pretty quickly so odds are whatever was giving you trouble back when you tried it has since been fixed.

---

### Post by porcorosso on 2007-08-16
> **mssever said:**
> It's been a while since I tried wicd, along with MadWiFi and I think something else, too, so I don't remember what my problem was with wicd (and it may have been due to an old version).  But my wireless card is weird. It's a Broadcom 4306 (IIRC) and it only works at 11M with the bcm43xx driver. Supposedly, it works with ndiswrapper, but I've never gotten ndis working. So, either I've been doing something wrong, or my card is weird.

At any rate, since my wireless is working, I'm not messing with it.

Heh-heh. I can sympathize with that stance!

I decided to give this PAM keyring thing a try. Uninstalled wicd and reinstalled network-manager, network-manager-dev, and network-manager-gnome. I installed libpam-keyring, added the common password line to its configuration file, blew away the old keyring, and reconnected to my wireless connection by providing the WPA2 passkey. I got asked for a new password for the keyring and provided my logon password, and voila! So I'll have to do this again for each of my wireless connections?

Okay, it works. But in 27 days when I change my logon password, I have to do the song and dance (blow away the keyring and create a new one) with the keyring manager again, right? Which means I'll have to go through all of it (except for the installations, of course) again. Eh, it might ALMOST be worth it just to stick with the standard packages instead of replacing them, but I don't know...

Have I got this right, or did I misunderstand something?

---

### Post by olliecampbell on 2007-08-22
Well I've just managed to get through the install, a few dependencies required and had to remove a couple of symbolic links too....time for a reboot....

---

### Post by hyapadi on 2007-08-26
I wonder when will this be fixed. In the next version? =(

It will be very nice if this can be integrated nicely in the official Ubuntu.

---

### Post by dopple on 2007-08-27
Installed and set up very nicely. Used Synaptic PM to download and install, deleted previous default keyring and after the quick gedit and reboot it worked a treat.
Thanks.

---

### Post by 00110000 on 2007-08-27
> **porcorosso said:**
>  I stumbled upon what looks to me to be an easier solution earlier today. It's at [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/"). Did any of you take a look at that? What do you think of it vs. the PAM keyring solution?

I installed it, and it works VERY well for me. Lets me switch among my hard connected and wireless networks from one location. And no more annoying keyring password popup.

I change my logon password every 30 days. I'm not going to create a new keyring every darned month. Not happening.

Forgot to mention: If you follow the instructions on the download page you get the download through the Synaptic package manager and set up the repository for automatic updates. It automatically uninstalls the network-manager stuff when it installs Wicd. And the addition of the tray applet just puts icing on the cake.

Wicd also works fine for me in Feisty. 
I followed the instructions on the download page, pretty easy stuff, configured it, did a reboot and everething is working fine. I am now with automatic connect on WPA network and no more keyring stuff to worry about.

Thanks for the suggestion porcorosso.

---

### Post by porcorosso on 2007-08-29
You're welcome.

I'll probably go with Wicd, too -- after I remove the smoking ruin that was my Ubuntu hard drive and replace it.

:(

---

### Post by vikrant82 on 2007-09-22
Wiith WICD :popcorn:
Works Perfect..

---

### Post by buffalo2001 on 2007-10-04
I was able to successfully use alien to convert the rmp's and install that way...but i could not get it to work after that...do i really have to install from source?

---

### Post by porcorosso on 2007-10-04
> I was able to successfully use alien to convert the rmp's and install that way...but i could not get it to work after that...do i really have to install from source?

Sorry, I'm missing something here. What is it that you're trying to install? Did you download an RPM for something and try to use it in Ubuntu?

---

### Post by Muhahahahaz on 2007-10-11
I recently set up a Dynamic DNS so that I can access my machine remotely.  What if I need to reboot remotely?  Either way, a password will be required before the wireless connection is up.

I can ssh to the computers at my college whether anyone has logged in or not because they have a wired connection.  Shouldn't it be possible to get the wireless connection up before anyone has logged in?  This would be very desirable for me.

Thanks!

---

### Post by Muhahahahaz on 2007-10-12
Ok, so I installed Wicd instead, but it doesn't work properly.  If I set the task bar applet as a startup program, it won't let me click on it and it doens't connect.  If I turn it off and launch it myself, it helps some.  Eventually the Wicd Manager comes up and lets me select my connection.

The thing is, it has all of my connection settings stored and "connect automatically" is checked, but it still refuses to connect unless I tell it to, which sucks because the applet isn't even working properly. :(

---

### Post by Muhahahahaz on 2007-10-12
Well, it turns out that Wicd appears in my Applications menu, which is great because now I can lauch the manager without having to use the applet.  I had looked through the Wicd directory, but I couldn't seem to find the command for lauching the manager... oh well.

Anyways, any idea how to make it connect automatically?

---

### Post by olliecampbell on 2007-10-13
Under each of the networks theres an 'automatically connect' tick box....
to get it to start every time have a look under System -> Preferences -> Sessions (from memory!)

---

### Post by Muhahahahaz on 2007-10-14
> **Muhahahahaz said:**
> The thing is, it has all of my connection settings stored **and "connect automatically" is checked**, but it still refuses to connect unless I tell it to, which sucks because the applet isn't even working properly. :(

It doesn't work. :(

---

### Post by PartisanEntity on 2007-10-14
How do I get rid of pam-keyring completely? I have to access a different router with a different password and I don't get a password prompt while connecting? (I'm assuming this has something to do with pam-keyring)

---

### Post by MadCatMk2 on 2007-10-20
I get

```
make: *** No targets specified and no makefile found.  Stop.
```

when I try to use "make"..

---

### Post by jw5801 on 2007-10-20
Had you cd'd to the folder you extracted the tar you downloaded to before you ran make?

---

### Post by hyapadi on 2007-10-24
how about the 7.10? is it still asking for keyring?

---

### Post by PartisanEntity on 2007-10-24
> **hyapadi said:**
> how about the 7.10? is it still asking for keyring?

Nope,no longer doing so :)

---

### Post by zordon on 2007-10-24
well...when I upgraded I was quite shocked that it asked, but next time I noticed small checkbox "do not ask next time" what a relief!

---

### Post by luts on 2007-10-24
Well it keeps on asking the password and there is **no checkbox at all** on that dialog.

I had libpam_keyring on feisty but it no longer works.

any help appreciated.

---

### Post by NilsE on 2007-10-24
> **luts said:**
> Well it keeps on asking the password and there is **no checkbox at all** on that dialog.

I had libpam_keyring on feisty but it no longer works.

any help appreciated.
On Ubuntu it is now gnome-keyring-manager but I am not sure what it is on the other flavors of Ubuntu (X, K, etc.)

---

### Post by hyapadi on 2007-10-25
> **zordon said:**
> well...when I upgraded I was quite shocked that it asked, but next time I noticed small checkbox "do not ask next time" what a relief!

are u using additional patch or the checkbox is there by default?

What a relief :D

---

### Post by luts on 2007-10-25
> **NilsE said:**
> On Ubuntu it is now gnome-keyring-manager but I am not sure what it is on the other flavors of Ubuntu (X, K, etc.)

euh... I was on Ubuntu Feisty and upgraded to Gutsy.

If they changed keyring manager, they should have upgraded it, not leave it in the irritating state it is now :(

---

### Post by Hairy_Palms on 2007-10-25
ive figured out what the problem is in gutsy! the problem is that gnome-keyring-daemon isnt starting at boot, if you add it to the gnome sessions then nm stops asking for your password and also it stopped the nm keep disconnecting problem that i had!

---

### Post by luts on 2007-10-25
> **Hairy_Palms said:**
> ive figured out what the problem is in gutsy! the problem is that gnome-keyring-daemon isnt starting at boot, if you add it to the gnome sessions then nm stops asking for your password and also it stopped the nm keep disconnecting problem that i had!

nice... any more details on how to do this for a newbie?

---

### Post by rulsky on 2007-10-25
That&#347; great Hairy_Palms that you were able to figure out....but I a NOOB like Luts.....Do you mind giving the details on how to get rid of this annoying password?[-o<

---

### Post by mjitkop on 2007-10-25
Yes, please, what are the steps to follow to stop the keyring prompt at login? I have Gutsy and no check box in the dialog box. :(

---

### Post by luts on 2007-10-26
gnome-keyring-daemon is certainly running here....

I get the feeling something hasn't been upgraded correctly - namely the part that features the dialog with the (missing) checkbox.

---

### Post by luts on 2007-10-27
another thing I tried but didn't help: deleted the keyring and strated from scratch. Still asks the password every time :(

Keyring manager says it is version 2.20.0 but when asking the password after logon, there is _no_ checkbox on the dialog to make it shut up for ever...

Do I really need to downgrade back to Feisty to get rid of this? Or file a bugreport?

---

### Post by Dirkomatic on 2007-10-31
I was experiencing the same thing (no checkbox) after upgrading.

Here's what I did to fix it.

```
cd /etc/pam.d
sudo mv gdm gdm.fiesty
sudo cp -p gdm.dpkg-dist gdm
gksudo gedit gdm
```

Then add:```
@include common-pamkeyring
``` after the last line and save.

Restart and you should get the checkbox which allows you to automatically login to the keyring the next time.

---

### Post by mjitkop on 2007-10-31
Thanks, Dirkomatic. I will give it a try as soon as I get a chance at home. :)

---

### Post by luts on 2007-10-31
Yup, that did it! Thanks a lot!

:)

Am I correct in concluding that the upgrade failed to replace that binary?

---

### Post by Dirkomatic on 2007-10-31
I'm glad it worked for you...

The upgrade didn't replace the gdm file, but luckily it put the gdm.dpkg-dist file out there, which I suppose are the default settings.

I haven't really spent the time investigating the differences between my old gdm and the new one, but I'm sure there's something in the old one that the new package doesn't like.

---

### Post by mjitkop on 2007-10-31
That did not work for me. Maybe because I did a clean install of Gutsy so I do not have any leftovers from Fiesty?

```
<my name>:~$ cd /etc/pam.d
<my name>:/etc/pam.d$ sudo mv gdm gdm.fiesty
[sudo] password for <my name>:
<my name>:/etc/pam.d$ sudo cp -p gdm.dpkg-dist gdm
cp: cannot stat `gdm.dpkg-dist': No such file or directory
<my name>:/etc/pam.d$
```Maybe somebody will be kind enough to show the full content of that `gdm.dpkg-dist' file so I can just copy-and-paste it? :mrgreen:

---

### Post by jhw on 2007-11-01
I did an upgrade from Feisty, and I get the same as mjitkop.

---

### Post by Dirkomatic on 2007-11-01
I've got a lot of stuff going on tonight, but I'll try to get it posted at some point.

---

### Post by djoser on 2007-11-02
I would also love to see a gutsy solution for this!

---

### Post by luts on 2007-11-03
Post 152 contains a solution that works for me...

---

### Post by jhw on 2007-11-03
Yes but I don't have file gdm.dpkg-dist - please could you post its contents?

---

### Post by luts on 2007-11-04
here's mine....

---

### Post by jhw on 2007-11-04
Thanks for that. Unfortunately it still doesn't work for me. I get a pop up saying "Authentication failed" on the login screen and I can't login unless I boot into recovery mode and comment out the last line.

There seems to be something odd going on with nm-applet and/or the keyring.

---

### Post by Leed on 2007-11-04
I'm really put off by this stupid Keyring Manager, it already caused problems in Feisty, needed workarounds to stop ist asking for the keyring password on every boot...

Then in the Gutsy pre-release, at last it worked out of the box as it should work. I even got the checkbox for automatic use of keyring on login.

But as the Gutsy official release appeared, problems came back. Now it's not the Keyring Password that is needed, the Keyring Manager says it needs the WLAN Network password... ON EVERY BOOT!! 
Upon checking the settings in the Keyring Manager, the password is set (yes I replaced it several times, still no good). 

That just leaves me with two choices, either I type in the password for the WLAN or I press cancel and then tell Network Manager to connect to my network... wich it then does without asking for the network password. Why can't it just do this automaticly?

I wonder if anyone knows a workaround... other than reinstalling everything, that's not an option.

---

### Post by Dirkomatic on 2007-11-04
Here are my files that were installed, if they help...

---

### Post by jhw on 2007-11-05
luts  and Dirkomatic - thanks for the files. It still asks for the pasphrase, but if I press cancel and select my network, it connects without me supplying it.

Hopefully there will be an update to fixt this soon.

---

### Post by jhw on 2007-11-07
Something odd:

If I do
> iwlist eth1 scan
I get (excerpt)
> 
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
which is odd because I am using AES encrytion.

If I change the router to use TKIP encryption, I get
> 
IE: WPA Version 1
Group Cipher : WEP-40
Pairwise Ciphers (1) : WEP-40
Authentication Suites (1) : PSK
Which is also odd.

I don't think there is anything wrong with the router - XP on the same machine recognises AES.

---

### Post by mjitkop on 2007-11-07
> **jhw said:**
> luts  and Dirkomatic - thanks for the files. It still asks for the pasphrase, but if I press cancel and select my network, it connects without me supplying it.

Hopefully there will be an update to fixt this soon.

It still asks for the password in my case too. Oh well, I'll live with it until it's fixed.

---

### Post by jhw on 2007-11-09
I solved the problem by replacing Network Manager with WICD
I followed the instructions for manual install and it worked out of the box. The only downside seems to be no VPN support yet, but there should be soon.

[http://ubuntuforums.org/showthread.php?t=527488](http://ubuntuforums.org/showthread.php?t=527488)

---

### Post by hooah212002 on 2007-11-16
I have tried everything I have found and it all seemed like it SHOULD have worked, but it didnt. Could someone show me EXACTLY what the file is suppose to look like? I have already tried adding 
"auth optional pam_keyring.so try_first_pass"
"session optional pam_keyring.so"        to the end of the file, but to no avail. I have tried inserting it in different places but still nothing. Please help!

---

### Post by holizz on 2007-11-17
I worked out why none of these solutions are working for me. Following a trail of bugreports lead me to some comments stating that libpam-gnome-keyring is effectively useless when you're using autologin.

As far as I can tell libpam is copying the password that you used to login into the keyring manager, and apparently it fails if you change your password. According to some comment made in March 2006 the next major version of NetworkManager (0.7 - latest release is 0.6.5, same as Gutsy) will have a checkbox to say "just remember my bleeding passwords without all this keyring rubbish".

The GNOME keyring developers have no intent of fixing it either, because they think PAM will somehow solve it.

In summary, aside from not using NetworkManager, it is currently impossible (as far as I can tell) to use autologin _and_ not have the keyring manager prompt you for a password.

[https://bugs.launchpad.net/ubuntu/+source/pam-keyring/+bug/137247](https://bugs.launchpad.net/ubuntu/+source/pam-keyring/+bug/137247)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/34898](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/34898)
[https://bugs.launchpad.net/gnome-keyring/+bug/108993](https://bugs.launchpad.net/gnome-keyring/+bug/108993)

---

### Post by teddy1977 on 2007-12-15
i have tried alot of solutions. but it still doesnt work for me:-(

---

### Post by Ripfox on 2007-12-15
I have a solution...use wicd like mentioned before. Never gave me any grief... :lolflag:

---

### Post by teddy1977 on 2007-12-16
> **ripfox said:**
> I have a solution...use wicd like mentioned before. Never gave me any grief... :lolflag:

what page is it from??

or can you explain me how??

---

### Post by Palmyra on 2007-12-16
> **teddy1977 said:**
> what page is it from??

or can you explain me how??

Here you go:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by teddy1977 on 2007-12-16
> **Palmyra said:**
> Here you go:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

can you only use this with static ip??

i cant get it to connect to my wireless

---

### Post by Naosedna on 2008-01-19
This worked for me. It DOES NOT work for fresh installs, I have no idea why.  (Credit goes to post #152, I just tweaked it a little)

cd /etc/pam.d
sudo cp -p gdm gdm.backup
gksudo gedit gdm

Paste this at the end and save

@include common-pamkeyring

---

### Post by Juninho1 on 2008-01-29
This is driving me insane as well!! I have tried so many combinations including some suggested like disabling the remote connection settings (and trying the checkbox that should appear) but everywhere I hit a wall.

For the remote settings - if I try and manually configure my network it jsut does not connect.

Is there anywhere / anyway someone can come up with a clever script to just provide the pwd to gnome keyring?

I am the only one who uses my PC and I have thigns set up to just start up automatically (and go to the correct workplaces thanks to devilspie - fantastic app) ... ! BUT I have to still enter my pwd (in spite of auto login).

heeelllppp!!! 

> **holizz said:**
> I worked out why none of these solutions are working for me. Following a trail of bugreports lead me to some comments stating that libpam-gnome-keyring is effectively useless when you're using autologin.

As far as I can tell libpam is copying the password that you used to login into the keyring manager, and apparently it fails if you change your password. According to some comment made in March 2006 the next major version of NetworkManager (0.7 - latest release is 0.6.5, same as Gutsy) will have a checkbox to say "just remember my bleeding passwords without all this keyring rubbish".

The GNOME keyring developers have no intent of fixing it either, because they think PAM will somehow solve it.

In summary, aside from not using NetworkManager, it is currently impossible (as far as I can tell) to use autologin _and_ not have the keyring manager prompt you for a password.

[https://bugs.launchpad.net/ubuntu/+source/pam-keyring/+bug/137247](https://bugs.launchpad.net/ubuntu/+source/pam-keyring/+bug/137247)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/34898](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/34898)
[https://bugs.launchpad.net/gnome-keyring/+bug/108993](https://bugs.launchpad.net/gnome-keyring/+bug/108993)

---

### Post by orbital on 2008-01-30
When I do

```
./configure --prefix=/usr --libdir=/lib
```

I get:

```
checking for GNOME_KEYRING... configure: error: Package requirements (gnome-keyring-1) were not met:

No package 'gnome-keyring-1' found

```
 
What to do?

---

### Post by mexpolk on 2008-02-06
Here is, a solution to change default Keyring Manager password:

[URL="http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html"]
http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html[/URL]

best,
Ivan Torres

---

### Post by imclumzy on 2008-02-07
> **Dirkomatic said:**
> I was experiencing the same thing (no checkbox) after upgrading.

Here's what I did to fix it.

```
cd /etc/pam.d
sudo mv gdm gdm.fiesty
sudo cp -p gdm.dpkg-dist gdm
gksudo gedit gdm
```

Then add:```
@include common-pamkeyring
``` after the last line and save.

Restart and you should get the checkbox which allows you to automatically login to the keyring the next time.

Thanks for this suggestion and the file that you provided a few posts after this.  However, now when the login screen comes up I get a pop-up box that says "Authentication failed" with an OK button.  No matter how many times I hit that button the window spawns again.  I have to switch consoles and remove the line from gdm.  Anyone else experience this problem?

---

### Post by jw5801 on 2008-02-07
That suggestion is for those that use autologin! If you're logging in normally and it's not working for you, then you can try adding the same line to the very bottom of /etc/pam.d/login. I just had the same issue (got to gdm and was told authentication had failed... alot), so I commented out the line in /etc/pam.d/gdm and instead included it in /etc/pam.d/login and once I logged in, no annoying prompt!

---

### Post by orbital on 2008-02-08
How do I get rid of keyring asking the password every time I login? I've been trying to get rid of it but with no success :(

---

### Post by mexpolk on 2008-02-08
Orbital,

Did you tried this howto?

[http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html]("http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html")

---

### Post by jw5801 on 2008-02-08
Did you try [this](http://ubuntuforums.org/showthread.php?t=187874) howto? What went wrong when you did?

---

### Post by orbital on 2008-02-09
> **jw5801 said:**
> Did you try [this](http://ubuntuforums.org/showthread.php?t=187874) howto? What went wrong when you did?

When I run configure I get:

```
checking for GNOME_KEYRING... configure: error: Package requirements (gnome-keyring-1) were not met:

No package 'gnome-keyring-1' found
```

---

### Post by jw5801 on 2008-02-09
Did you try: ```
sudo apt-get install gnome-keyring
```
And if you don't have gnome keyring installed, how is nm-applet asking for a password to it? Are you using gnome or kde? (Ubuntu or Kubuntu).

---

### Post by reidman on 2008-02-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/pam-keyring/+bug/137247](https://bugs.launchpad.net/ubuntu/+source/pam-keyring/+bug/137247) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
After two days of hair-pulling, I've finally found a working solution for those of us trying to auto-login without any passwords prompts (security is for the weak|intelligent|able!)

In a bug report concerning this issue, [Troels Faber decided to be completely awesome and post his  solution to this convoluted problem]("https://bugs.launchpad.net/ubuntu/+source/pam-keyring/+bug/137247/comments/16"). I was able to get it working on my machine, so I thought I'd share it with those of you who are as clueless as I was a few days ago. For the record, I'm doing this on a fresh install of Gutsy.
[LIST=1]
[*]Download the file attached to this post (pammy.tar.gz)
[*]Extract the archive and put the files in your home directory. They should be located at [FONT="Courier New"]~/pam-keyring-tool[/FONT] and [FONT="Courier New"]~/pammy.sh[/FONT]
[*]Edit the pammy.sh file -- change YOUR_PASSWORD_HERE to your password (keep the quotes, though).
[*]Go to System > Preferences > Sessions and click '+ Add'
[*]Name it whatever you want (I personally find 'pammy' to be a flattering and shape-enhancing name)
[*]In the command box, enter the path to [FONT="Courier New"]pammy.sh[/FONT] (i.e. [FONT="Courier New"]/home/username/pammy.sh[/FONT])
[*]Restart your computer and cross your fingers!
[/LIST]
Hope this works for everyone else as well as it worked for me! If you have problems, you might check the permissions on your files -- one or both of them may need to be executable, which you can apply with chmod +x filename. But I don't think that's necessary in this case.

[COLOR="Red"][SIZE="4"]SECURITY NOTE:[/SIZE][/COLOR]
This is a pretty wildly insecure solution. Your password is going to be sitting in plaintext in your home directory. If someone can suggest a more secure way to handle this, I'd be really glad to hear it. But for now, if you're not worried about security, this is a good way to get things rolling :)

---

### Post by Stewie Griffin on 2008-02-15
thanks, i don't really care bout the password being in plain text the wireless key is the only thing in the keyring anyway.  If only the keyring allowed blank passwords like the kde wallet.

also the files could be hidden by renaming then with a full stop at the start, the sh file and the start-up command will have to be altered to point to the hidden files.

---

### Post by orbital on 2008-02-20
> **jw5801 said:**
> Did you try: ```
sudo apt-get install gnome-keyring
```
And if you don't have gnome keyring installed, how is nm-applet asking for a password to it? Are you using gnome or kde? (Ubuntu or Kubuntu).

Gnome-keyring is already installed and is the newest version. I'm using Gnome. Everytime I boot into Gnome nm-applet asks for the password. It's getting annoying.

---

### Post by magicrobotmonkey on 2008-02-21
I found a *really* easy way to fix the problem of changing your login password and then gnome keyring starts asking you for a password. You dont have to patch anything or install anything weird or custom. Check it here: [http://magicrobotmonkey.blogspot.com/2008/02/chaging-your-password-on-gnome-keyring.html](http://magicrobotmonkey.blogspot.com/2008/02/chaging-your-password-on-gnome-keyring.html)


Edit: er, woops, just noticed mexpolk already posted the same solution

---

### Post by Marlo_nl on 2008-03-09
Thanks for the link.

Can you please inform us if this link solved your problem in an Ubuntu 7.04 or Ubuntu 7.10 environment?

I tried the link in Ubuntu 7.04 but without success.

The package "Seahorse" in Ubuntu 7.04 does not have the tab "GNOME Keyring" available.

Hence, I don't think this link provides a solution for Ubuntu 7.04. 
Please correct me if I'm wrong.


p.s. For me, an "upgrade" to Ubuntu 7.10 is no solution because Ubuntu 7.10 is not compatible (extremely slow) with my Toshiba Portege 7200 Notebook (Ubuntu 7.04 is working just fine).
 

Regards, Marlo.

---

### Post by GordonFreeman on 2008-03-24
I'm using Xubuntu 7.10 and I tried the howto in #1 and after quite some time I got everything installed, but not working (I'm using regular login and I altered my gdm file accordingly to the solution in #1).

The only thing I changed: I used the 0.9 version of pam keyring, but when it is working in 0.8, 0.9 should support the try_first_pass, too right?

---

### Post by jw5801 on 2008-03-24
> **GordonFreeman said:**
> I'm using Xubuntu 7.10 and I tried the howto in #1 and after quite some time I got everything installed, but not working (I'm using regular login and I altered my gdm file accordingly to the solution in #1).

The only thing I changed: I used the 0.9 version of pam keyring, but when it is working in 0.8, 0.9 should support the try_first_pass, too right?

pam keyring has a non-explicit gnome dependency. I'm not sure what it is, but I know that I had the same issue as you until the day I decided to install ubuntu-desktop so I could have a play in Gnome to see what it's like nowadays. Lo and behold, when I went back to Xfce, no annoying pop-up. Haven't had one since either! The other option is to use something like wifi-radar or wicd instead of network-manager. I use wifi-radar nowadays which has been much more stable that network-manager and has never once bugged me with annoying passwords. I need to be root to run the GUI, but I don't mind that since I don't often have any reason to run the GUI.

---

### Post by black_zerg on 2008-06-13
I tried everything without luck . 

so my solution is just :
application->accessories->password and...->edit->reference
change unlock password as a blank.

hope it helps!

---

