---
title: "Checkpoint VPN with Ubuntu 9.04"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by avphoto on 2009-07-23
Anyone have any advice on trying to connect to a Checkpoint VPN with Ubuntu 9.04 
I've used the following steps so far with no help. I've also tried running firefox from Root after these steps as some others have suggested again with no fix. Any advice on this is greatly appreciated.

1- get the SNX archive on checkpoint, go checkpoint website download section and get “SNX R66 HFA 01 For Linux 800004013 “

2- install the package (#./snx_install.sh)
you will probably get an error message : snx: symbol lookup error: snx: undefined symbol: cerr

3- you need a special library to get the snx client working : libstdc++2.10-glibc2.2.
download

4- install it with dpkg (#dpkg -i libstdc++2.10-glibc2.2)

5- update your env variable : #LD_PRELOAD=/usr/lib/libstdc++-libc6.2-2.so.3 snx

---

### Post by donchichi on 2009-09-03
Need to get this working for work..

When I searched I got this file from checkpoint. Check_Point_SNX_R66_HFA_01_For_Linux_800004013.sh

Different? Or did I look in the wrong place?

regards
Arif

---

### Post by berteh on 2009-10-17
> **avphoto said:**
> Anyone have any advice on trying to connect to a Checkpoint VPN with Ubuntu 9.04

Yes, I got it running (mostly fine) under Kubuntu 9.04, so I guess it might work for you too... please read on and comment.

> 
1- get the SNX archive on checkpoint, go checkpoint website download section and get “SNX R66 HFA 01 For Linux 800004013 “
correct. google works with the above info.  [direct link]("https://supportcenter.checkpoint.com/supportcenter/portal/user/anon/page/default.psml/media-type/html?action=portlets.DCFileAction&eventSubmit_doGetdcdetails=&fileid=8724")

> 3- you need a special library to get the snx client working : libstdc++2.10-glibc2.2.
I actually needed to install manually [libstdc++2.10-glibc2.2]("http://packages.ubuntu.com/dapper/libstdc++2.10-glibc2.2"), [libstdc++5]("http://packages.ubuntu.com/hardy/libstdc%2B%2B5") and [gcc-3.3-base]("http://packages.ubuntu.com/hardy/gcc-3.3-base"). I got them from the Hardy and Dapper repositories (direct links on libs names).

Download all 3 debs in the same directory and, open a console in this directory and run
```
 $sudo dpkg -i *.deb
```

> 2- install the package (#./snx_install.sh)
do it rather with sudo:
```
  $sudo -s
  #export LD_PRELOAD=/usr/lib/libstdc++-libc6.2-2.so.3
  #./Check_Point_SNX_R66_HFA_01_For_Linux_800004013.sh
```

The second line enforces the use of your (old) library.

The message of install should be successful: congratulations!

exit sudo session and run snx to test:
```
  #exit
  $snx -s HOSTNAME -u VPN_LOGIN
```

shutdown vpn with
```
  $snx -d
```

to ease next connection store your session info in ~/.snxrc
```
  server HOSTNAME
  username VPN_LOGIN
  reauth yes
  debug 1
```

This will enable to run the vpn by simply calling
```
  $snx
```

Hope this helps.
I attach the 3 mentionned debs for later references, but preferably get them from the above links as they are mirrored!

Berteh.

---

### Post by Angotull on 2009-11-30
Thank you sir. Worked like a charm on 9.10 as well.

---

### Post by acpreda on 2009-12-05
Berteh,

My Ubuntu is 64 bits. The libstdc++2.10-glibc2.2 package is available only for 32bit so I got all the old packages for i386 arch, installed them forcing the architecture:

dpkg -i --force-architecture gcc-3.3-base_3.3.6-15ubuntu4_i386.deb libstdc++2.10-glibc2.2_2.95.4-24_i386.deb libstdc++5_3.3.6-15ubuntu4_i386.deb

After that, I exported the LD_PRELOAD:

export LD_PRELOAD=/usr/lib/libstdc++-libc6.2-2.so.3

When intalling Check_Point_SNX_R66_HFA_01_For_Linux_800004013.sh I got the following error:

ERROR: ld.so: object '/usr/lib/libstdc++-libc6.2-2.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libstdc++-libc6.2-2.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libstdc++-libc6.2-2.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libstdc++-libc6.2-2.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libstdc++-libc6.2-2.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libstdc++-libc6.2-2.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libstdc++-libc6.2-2.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libstdc++-libc6.2-2.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libstdc++-libc6.2-2.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libstdc++-libc6.2-2.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libstdc++-libc6.2-2.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libstdc++-libc6.2-2.so.3' from LD_PRELOAD cannot be preloaded: ignored.
Installation successfull
ERROR: ld.so: object '/usr/lib/libstdc++-libc6.2-2.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libstdc++-libc6.2-2.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libstdc++-libc6.2-2.so.3' from LD_PRELOAD cannot be preloaded: ignored.

So, while the message "Installation successfull" is present I tried to run snx command and this is the output:

-su: /usr/bin/snx: No such file or directory

Finally, the uname -a command if this helps:
Linux decebal 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

Could you please help me with some advice?

Thanks however.

Regards,

Arturo

---

### Post by liedan on 2010-01-02
I am also struggling to get this working on 64bit Karmic Koala.
This forum helped me a lot: [http://ubuntuforums.org/showthread.php?t=340307&page=6](http://ubuntuforums.org/showthread.php?t=340307&page=6)
Especially  posts #21 and #57 were helpful for me. 

Finally, i think it should work correctly. When i type "snx", I get:

```
a username or a certificate were not supplied
Check Point's Linux SNX
build 700001030
usage: snx -s <server> {-u <user>|-c <certfile>} [-l <ca dir>] [-p <port>] [-r] [-g] [-e <cipher>]
                                run SNX using given arguments
       snx -f <cf>              run the snx using configuration file
       snx                      run the snx using the ~/.snxrc

       snx -d                   disconnect a running SNX daemon

        -s <server>           connect to server <server>
        -u <user>             use the username <user>
        -c <certfile>         use the certificate file <certfile>
        -l <ca dir>           get trusted ca's from <ca dir>
        -p <port>             connect using port <port>
        -g                    enable debugging
        -e <cipher>           SSL cipher to use: RC4 or 3DES


```However, when I try to connect by :

```
sudo snx -s Gateway -u My_username

```The output is the same.:( Any ideas?

---

### Post by liedan on 2010-01-09
Ok, now it´s worknig fine for me. All I needed was reinstallation.

However, I was messing up with so many thing that i am not sure, what was the key for my success. I installed all libraries mentioned by berteh. 
And I commented 4 lines with the trap cleanup in snx_install.sh according to this forum:

[http://ubuntuforums.org/showthread.php?t=340307&page=3](http://ubuntuforums.org/showthread.php?t=340307&page=3)  ,post #21. 

And that was it I think. Hope it helps.

---

### Post by Setya on 2010-03-30
Hi all,

I also need to connect to Checkpoint VPN using Ubuntu 9.04, where to download the client software ?

Please Help.


Regards,

Setya

---

### Post by shaun.husain on 2010-04-21
**THANK YOU THANK YOU THANK YOU**
Also worked for me on 9.10 thanks berteh, very clear instructions and worked like a charm.  Can now simply type snx and I'm VPNed in to work and maven can contact our repository and the world keeps turning yea!  Thanks again, was reading a lot on this last night and was feeling it might have been hopeless.

For the last poster here, looking for an installer, that's what berteh has explained up above.  The installer from Checkpoint won't work outright you need to install a few old dependencies, to allow the Checkpoint client to install correctly. You'll need to download all 4 files in berteh's post
Iff you just needed the link to the checkpoint software and didn't see it above you can get it _**[here]("https://supportcenter.checkpoint.com/supportcenter/portal/user/anon/page/default.psml/media-type/html?action=portlets.DCFileAction&eventSubmit_doGetdcdetails=&fileid=8724")**_ copied the link from above.[FONT=Arial Black]

Generally this is what you're being instructed to do[/FONT]
The three files you get from the repository or by downloading the zip attached to the post above that have an extension of .deb are installers/setup files, you run dpkg to install those first then when they're done installing you type a command to run the script.

[FONT=Arial Black]Specifically this is what I did[/FONT]

Download the files from above to the default location, my home folder /home/shaun/Downloads/

As instructed move the .deb files into a folder I used
Fire up the terminal Alt+F2, gnome-terminal, [Enter]
```

mkdir debs
mv gcc-3.3-base_3.3.6-15ubuntu4_i386.deb
mv libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
mv libstdc++5_3.3.6-15ubuntu4_i386.deb
cd debs
sudo dpkg -i *.deb

```after that just run the checkpoint installer
```

cd ..
sudo -s
export LD_PRELOADER=/usr/lib/libstc++-libc6.2-2.so.3
 ./Check_Point_SNX_R66_HFA_01_For_Linux_800004013.sh

```I was a bit confused because I saw one of the lines that was quoted from a previous post that said ./snx_install.sh (s)he's referencing somebody else's post about this issue instead you want to do whats in the berteh's code block after the quote, essentially moving the prompt into "root mode" (I don't know the terminology for this) then setting an environment variable by using export (this can then be referenced within scripts and must be referenced by the install script, has to be done in root context for it to work) then simply run the install script.  You should have three .deb files and one .sh file.  I hadn't done any other steps previous to this in terms of Checkpoint setup just a pretty fresh 9.10 Ubuntu install, eclipse, flex builder, maven, svn, charles and a few other goodies on here too already.

Since it sounds like you may be a beginner with Linux I'm trying to be as explicit as possible, here's a quick glossary of the commands used in the code shown in this post

mkdir folderToCreate - makes a directory (rmdir removes)

mv - Move/Rename a file (rm removes, cp copies)

cd - change (working) directory

dpkg - debian package management tool, debian is one of quite a few branches of the linux tree all spawning from the kernel released by Linus Torvalds ubuntu is some sort of twig on the debian branch I guess, big-ups (as Ali G would say) to Linus and the whole community though for making it really happen, this OS is sweet.
[http://en.wikipedia.org/wiki/Linus_Torvalds](http://en.wikipedia.org/wiki/Linus_Torvalds)

chmod - change mode bits which are used to determine permissions of who is allowed to do what to a given file or folder I would guess stored in the same section of a file as other attributes like timestamps and stuff.  The argument a+x means for all add execution privileges to the file then the name of the file you want to apply that to comes after the optional arguments.

export - creates or updates the value of a variable for a given session, can set permanent environment variables in /etc/environment a text file that works.

man - see a manual about some other program/command you can run
```

 man (command)
 
```like
 ```

 man chmod
 
```press the q key to quit out of man use the arrows to scroll around or spacebar to jump pages

Eh well, now that I think about it I could write a script to do these steps and just throw wget in there to download the packages, this is only going to work for 32 bit OSes anyway.  Well NEhow hopefully you'll get more understanding out of doing these steps yerself.

ADDITION
just upgraded to 10.04 of Ubuntu and I had a problem where it couldn't find tun after installing, tried to reboot but no change, ultimately found this on another forum and it fixed it although I'm not sure all of what's being done here, looks like it generates a C file makes a makefile for it then executes that... but to be honest VPN is mystifying enough by itself.
```

sudo apt-get install build-essential linux-headers-`uname -r`
mkdir faketun
cd faketun
echo -e "#include <linux/module.h>\nstatic int start__module(void) {return 0;}\nstatic void end__module(void){return;}\nmodule_init(start__module);\nmodule_exit(end__module);">tun.c
echo -e "obj-m += tun.o\nall:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) modules\nclean:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) clean\nclean-files := Module.symvers">Makefile
make
sudo install tun.ko /lib/modules/`uname -r`/kernel/net/tun.ko
sudo depmod -a
sudo modprobe tun

```

If someone else wants to fill me and everyone else in on what exactly this does and why it's needed that'd be great.

---

### Post by nvanevski on 2010-05-10
Hi all,

Thanks for the great instructions - I managed to install SNX client on 10.04.
However, when I run it for the first time, it displays following message:

```

SNX authentication:
Please confirm the connection to gateway: www.sample.dom
Root CA fingerprint: COLT TINT BALD GALE SELF HA SENT OWN FAY HOC DOG BAG
Do you accept? [y]es/[N]o:
y

```

After that, I always get "Authentication failure" response.
I guess the gateway offered is not correct (we have another name for the gateway), and the Windows client gives a totally different fingerprint.

Is there any way to change the gateway name? I did not find anything similar in the options.

Thanks in advance,

/Nikola

---

### Post by zeus.jay on 2010-06-25
Hey Guys is there any way to get this fully working on 10.04 64 bit...


It seems to have installed but when connecting it sticks there for like 10 seconds then does the connection aborted

zeus@Pandion:~/Desktop$ sudo snx -s server -c file.p12 -g
Check Point's Linux SNX
build 800004013
Please enter the certificate's password:

SNX: Connection aborted.


Thanks

---

### Post by freegilyeon on 2010-06-30
> **zeus.jay said:**
> Hey Guys is there any way to get this fully working on 10.04 64 bit...


It seems to have installed but when connecting it sticks there for like 10 seconds then does the connection aborted

zeus@Pandion:~/Desktop$ sudo snx -s server -c file.p12 -g
Check Point's Linux SNX
build 800004013
Please enter the certificate's password:

SNX: Connection aborted.


Thanks

I'm same
> 
$> snx -s xxx.xxx.xxx.xxx -u xxxxxx -g
Check Point's Linux SNX
build 800004013
Please enter your password:

SNX: Connection aborted.
$> cat snx.elg
[ 2449 -147383680]@nahan-note[30 Jun 23:02:18] snx: starting debug - Wed Jun 30 23:02:18 2010

[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] snx_browser::snx_browser(): called
[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] snx_browser::auth: entering
[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] gwinfo:gwinfo: entered!0x963ae58
[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] creating the ssl layer
[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] talkssl::talkssl(): entered with chunk=512, opaque=f7322008, link_established=80d3ab0, link_failure=80d3a90, packet_receive=80d3a60, verify_gw=80d3ad0
[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] talkssl::set_sslalg:  setting ssl alg to 2
[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] connecting
[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] talkssl:: init_ssl_neg: using 3DES
[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] ckpSSLctx_New: prefs = 1a
[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] CkpRegDir: Environment variable CPDIR is not set.
[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] GenerateGlobalEntry: Unable to get registry path
[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] isExist: ProxyEntity didn't initiated yet
[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] talkssl::start_async: Creating a new connection
[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] talkssl::start_async: Connecting to gw: 0x32bbf6cb, port: 443
[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] fwasync_make_connection: cbf6bb32/443: dowait is -1 sock is 5
[ 2449 -147383680]@nahan-note[30 Jun 23:02:25] talkssl::start_async: Connection created successfully
[ 2449 -147383680]@nahan-note[30 Jun 23:02:46] fwasync_connected: 5: getpeername: Transport endpoint is not connected
[ 2449 -147383680]@nahan-note[30 Jun 23:02:46] fwasync_client_handler_wrapper: failed to create conn
[ 2449 -147383680]@nahan-note[30 Jun 23:02:46] fwasync_end_conn: scheduling the end of connection 5
[ 2449 -147383680]@nahan-note[30 Jun 23:02:46] fwasync_do_end_conn: closing connection 5 (conn=9642310)
[ 2449 -147383680]@nahan-note[30 Jun 23:02:46] talkssl::end_handler: ending connection
[ 2449 -147383680]@nahan-note[30 Jun 23:02:46] snx_browser::Failure: entering with code: 1
[ 2449 -147383680]@nahan-note[30 Jun 23:02:46] got link down!- exit
[ 2449 -147383680]@nahan-note[30 Jun 23:02:46] snx: quit.
[ 2449 -147383680]@nahan-note[30 Jun 23:02:46] snx_browser::~snx_browser: called
[ 2449 -147383680]@nahan-note[30 Jun 23:02:46] talkssl::~talkssl: delete link
[ 2449 -147383680]@nahan-note[30 Jun 23:02:46] talkssl::~talkssl: end
[ 2449 -147383680]@nahan-note[30 Jun 23:02:46] done
help me!

PS. I do not speak english.

---

### Post by ozzytrain on 2010-08-30
> **zeus.jay said:**
> Hey Guys is there any way to get this fully working on 10.04 64 bit...


It seems to have installed but when connecting it sticks there for like 10 seconds then does the connection aborted

zeus@Pandion:~/Desktop$ sudo snx -s server -c file.p12 -g
Check Point's Linux SNX
build 800004013
Please enter the certificate's password:

SNX: Connection aborted.


Thanks

Has anybody solved this?

I've got the same message on 10.04 64-bit.

[FONT=Arial]I would be very grateful if you would find a solution, because this problem [/FONT]force me to work on Windows.


Thank in advance, and apologize for my english.

---

### Post by jlfuentes on 2010-09-20
Some progress? I have the same problem

---

### Post by djberndt on 2011-05-24
Bumping this thread.. Ubuntu 10.04 64-bit, same problem.

---

### Post by orduek on 2011-05-29
I'm having same authentication failure problem.
I used the newest snx client 2 weeks ago and it worked perfectly.
after a week it started giving "authentication failure". 
any ideas?

---

### Post by strackerphil on 2011-08-01
Exactly same problem here. I could not find any solution yet.
If anybody can find a way to solve this I would be very grateful for your advice ;-)

---

### Post by dan_bb3 on 2011-08-04
I am having the same issue a zeus.jay:

```
Check Point's Linux SNX
build 800005013
Please enter the certificate's password:

SNX: Connection aborted.
```

The issue has to do with a corrupted or missing registry file that SNX uses ([https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=skI3336](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=skI3336)):

```
[4 Aug 14:41:21] registry_root_reload: registry file corrupted.
[4 Aug 14:41:21] Unable to open Registry (/home/vpn/test/registry/HKLM_registry.data)! Fatal Error (rc=-1)!!
```

I set the environmental variable, CPDIR=/home/vpn/test, hoping that SNX would create the registry if it did not exist, however this did not work.

Does anyone know how to create this registry file?

TIA!

---

### Post by GlenPopata on 2011-09-20
Hi dan_bb3,
Did you get this resolved? I have the same issue:
Unable to open Registry (/home/user/vpn/registry/HKLM_registry.data)! Fatal Error (rc=-14)!!

Glen.

---

### Post by André Fernandes Simões on 2012-03-26
I am facing exactly the same problem but in Ubuntu 10.10.

anyone knows how to solve this CPDIR location and the HKLM_registry.data?

---

