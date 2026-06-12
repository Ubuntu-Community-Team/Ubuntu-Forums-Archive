---
title: "mythbuntu diskless"
date: 2012-04-28
forum: Mythbuntu
---

### Post by kingmoffa on 2012-04-28
Hi , 

When trying to setup a diskless system , on the server I type:

sudo ltsp-build-client --mythbuntu 

and Im getting errors:

/usr/sbin/ltsp-build-client: unrecognized option '--mythbuntu'


If I omit the mythbuntu arg , it builds what I think is a whole ubuntu desktop. 

Any ideas on how to get just mythbuntu?

---

### Post by superm1 on 2012-04-29
It looks like it was dropped.  Here's the changelog entry:

"  * Drop mythbuntu debian/extra-plugins hook as it's now covered by the
    upstream fat client implementation and didn't work anyway.
"

I'm really not sure the right way to resolve it right now.  I'm not up to speed on how the setup is supposed to work with it.  If you can find a way to configure it though, it would be great to fix up documentation for everyone else who wants to do it.

You might be able to get by by requesting it to install the 'mythbuntu-desktop' meta package instead of 'ubuntu-desktop'

---

### Post by kingmoffa on 2012-04-30
Thanks for the reply. 

I've started to construct a new diskless setup , it seems quite different from the old way of doing things. 

When your using ltsp-build-client there are options for fat-client that I've used. 

The main difference Im having trouble is with , is that in the previous way of doing things NFS was used to keep track of any changes by diskless clients from the main root filesystem made by the LTSP commands. 

This doesn't seem to be the case anymore , with home folders now mounted via SSH. Any other changes outside /home seem to be discarded upon shutdown. 

I'm having trouble as my different front ends have different xorg.confs , lirc settings and some other differences in start up scripts. 

Any ideas?

---

### Post by santhony on 2012-05-05
I've been running mythbuntu diskless server for a few years now...
Currently on the previous official release, mythbuntu Oneiric, running mythtv .25  ...

I'm going to give this a try today and post my results...

I did try the beta a month or so ago, and did notice that there is no longer an option of --mythbuntu .....  So I'll see if I come across a work around..

---

### Post by santhony on 2012-05-05
I'm not haveing much luck building the mythbuntu client..

I've tried: 
ltsp-build-client --fat-client-desktop --mythbuntu-desktop
ltsp-build-client --fat-client-desktop --ubuntu-desktop

The main problem is that it just seems to build as the standard LTSP service will build, there seems to be no mythbuntu customization doing anything to the builds....  Also, without the mythbuntu customization... I'll have to read up on the LTSP options, as I cannot modify any of the clients, frontends, seems to be read only file systems.

---

### Post by rlowery on 2012-05-06
This works for me for the most part.
sudo ltsp-build-client --arch i386 --fat-client --fat-client-desktop mythbuntu-desktop --mount-package-cache --keep-packages --accept-unsigned-packages --copy-sourceslist --mirror [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) --late-packages libdvdcss2,w32codecs,mplayer,ntfs-3g --prompt-rootpass

My server has medibuntu configured to get lidbdvdcss3 and w32codecs.  You will also want to change the mirror to suit.

It errors on /usr/share/ltsp/plugins/ltsp-build-client/common/035-update-kernels, but seems to get far enough to get a working system after I run ltsp-update-image

To get it to login automatically on boot and start mythfrontend, I created a /srv/tftp/ltsp/i386/lts.conf file containing 

[default]
LDM_AUTOLOGIN = True
LDM_USERNAME = mythtv
LDM_PASSWORD = <password>
LDM_SESSION = /usr/bin/mythfrontend 

However this does not start irexec so my custom remote command don't work.  Any tips?

---

### Post by santhony on 2012-05-06
Thanks rlowery, I'll give this a try and let you know how it goes..

I'm wondering particularly how these options are working together...

--fat-client --fat-client-desktop mythbuntu-desktop

---

### Post by rlowery on 2012-05-06
I believe --fat-client-desktop overrides --fat-client so the --fat-client is probably not necessary.  It was in an example I followed so I left it in.

---

### Post by rlowery on 2012-05-08
> **kingmoffa said:**
> Thanks for the reply. 

I've started to construct a new diskless setup , it seems quite different from the old way of doing things. 

When your using ltsp-build-client there are options for fat-client that I've used. 

The main difference Im having trouble is with , is that in the previous way of doing things NFS was used to keep track of any changes by diskless clients from the main root filesystem made by the LTSP commands. 

This doesn't seem to be the case anymore , with home folders now mounted via SSH. Any other changes outside /home seem to be discarded upon shutdown. 

I'm having trouble as my different front ends have different xorg.confs , lirc settings and some other differences in start up scripts. 

Any ideas?

lts.conf on the server can be used to point to a different xorg.conf file per client.  The setting is X_CONF, see [http://manpages.ubuntu.com/manpages/lucid/man5/lts.conf.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/lts.conf.5.html) for details.

---

### Post by kingmoffa on 2012-05-08
Hi, 

I've got most of my diskless machines working now. Using the lts.conf file I was able to load separate xorg.conf files. 

What I'm struggling with now is authentication and X authority via SSH. 

I used to be able to SSH into a machine , run export DISPLAY=:0 and run commands with the diskless machines X server. 

This doesn't seem to work , as Im guessing LDM handles authentication? 

I can log in via SSH to the diskless machine as I unlocked the root account password in the chroot earlier.  

When I login via SSH and type: **su - *USER*** , it does change user but with :

su: Authentication failure
(Ignored)

I then run :
export DISPLAY=:0

Running any command that needs X has this error:
 Error, can't open display: ':0'

Any ideas?

---

### Post by santhony on 2012-05-08
ok, Finally... I was able to fully build and boot a diskless tv Frontend, using:


sudo ltsp-build-client --fat-client-desktop mythbuntu-desktop  --mount-package-cache --keep-packages --accept-unsigned-packages --copy-sourceslist --prompt-rootpass

It did complete the build 100% succesfully..

I do see that my overlay is not working which is probrably leaving me to the issue of not being able to exit out of the Mythtv Frontend and getting to the desktop.  It will exit out of Mythtf Frontend, but then bounces back into Mythtv Fronted... As noted, I think this is from my overlay not working, not even showing the MAC address under the overlay directory...

I probrably need to fix my pxe default config. 

It's currently:
****************
default ltsp

label ltsp
kernel vmlinuz
append ro initrd=initrd.img root=/dev/nbd0 init=/sbin/init-ltsp quiet splash plymouth:force-splash vt.handoff=7 nbdroot=:ltsp_amd64 

label memtest86+
kernel memtest86+.bin
*****************

So at this point, I'm unable to customize the frontend.

---

### Post by kingmoffa on 2012-05-08
I've figured out my problem:

X is launched as :7 , not :0

so export DISPLAY=:7 seems to work fine. 

My next job is trying to get VAAPI for my intel G45 working - wish me luck!

---

### Post by rlowery on 2012-05-08
> **santhony said:**
> ok, Finally... I was able to fully build and boot a diskless tv Frontend, using:


sudo ltsp-build-client --fat-client-desktop mythbuntu-desktop  --mount-package-cache --keep-packages --accept-unsigned-packages --copy-sourceslist --prompt-rootpass

It did complete the build 100% succesfully..

I do see that my overlay is not working which is probrably leaving me to the issue of not being able to exit out of the Mythtv Frontend and getting to the desktop.  It will exit out of Mythtf Frontend, but then bounces back into Mythtv Fronted... As noted, I think this is from my overlay not working, not even showing the MAC address under the overlay directory...

I probrably need to fix my pxe default config. 

It's currently:
****************
default ltsp

label ltsp
kernel vmlinuz
append ro initrd=initrd.img root=/dev/nbd0 init=/sbin/init-ltsp quiet splash plymouth:force-splash vt.handoff=7 nbdroot=:ltsp_amd64 

label memtest86+
kernel memtest86+.bin
*****************

So at this point, I'm unable to customize the frontend.

How is mythfrontend being run?

If it is run with the --service argument I think it will restart on close or crash.  Without this argument it will not restart.

---

### Post by santhony on 2012-05-15
I'm still not having any luck making a mythtv diskless client, with overlay working... I'm still hacking away.... 

Anyone else ??

---

### Post by rlowery on 2012-05-16
> **santhony said:**
> I'm still not having any luck making a mythtv diskless client, with overlay working... I'm still hacking away.... 

Anyone else ??

My setup doesn't require overlay so I haven't really been looking further, but I have a few suggestions for per machine configurations in lts.conf (via mac address)
1) Use a different user account via LDM_USERNAME
2) Mount different folders via LOCAL_APPS_EXTRAMOUNTS 

HTH

---

### Post by littleinfinity on 2012-06-17
> **santhony said:**
> I'm still not having any luck making a mythtv diskless client, with overlay working... I'm still hacking away.... 

Anyone else ??
Make sure you are using a unique username for your diskless frontend. I was stuck where you were until I created an account specifically for the diskless frontend in my basement.

---

### Post by nickrout on 2012-06-17
> **littleinfinity said:**
> Make sure you are using a unique username for your diskless frontend. I was stuck where you were until I created an account specifically for the diskless frontend in my basement.

How do you do that?

---

### Post by santhony on 2012-06-18
> **nickrout said:**
> How do you do that?

Where is the lts.conf file ??

---

### Post by littleinfinity on 2012-06-19
> **nickrout said:**
> How do you do that?

From your backend:

```
# adduser <username>
...

# ltsp-chroot

# vi /etc/lts.conf

[Default]
LDM_AUTOLOGIN=True

[<mac address>]
LDM_USERNAME=<username>
LDM_PASSWORD=<password>

# ltsp-update-image


```

---

### Post by santhony on 2012-06-19
Thanks.. I'll give that a try..

---

### Post by raptorjr on 2012-09-05
> **santhony said:**
> Thanks.. I'll give that a try..

Did you get it to work? I cant get the overlay to work.

---

### Post by santhony on 2012-09-05
Nope, not the last time I tried.... 

I haven't tried in a while... Has anything changed, that you know of?

---

### Post by santhony on 2012-09-05
I'm going to try the minimyth.. 

They setup a PXE server with NFS overlay for Mythtv..

[www.minimyth.org](www.minimyth.org)   Give it a try...

I'll let you know how I make out... 

It'll probably take me a few days...

---

### Post by tomoprime on 2012-09-05
Hi all

Is it possible to setup a Mythbuntu diskless backend ? I have my NAS running TFTP and Dnsmasq. 

Or am I stuck at doing a vanilla install on a local hdd and then manually copying / reconfiguring...

Thanks.

---

### Post by nickrout on 2012-09-06
> **tomoprime said:**
> Hi all

Is it possible to setup a Mythbuntu diskless backend ? I have my NAS running TFTP and Dnsmasq. 

Or am I stuck at doing a vanilla install on a local hdd and then manually copying / reconfiguring...

Thanks.

I suppose it is possible, are you saying you want to run the backend in a diskless box with the OS and all storage mounted on the nas?

What architecture is your nas? is it a standard x86 computer set up as a nas, or is it some sort of proprietary thing?

---

### Post by tomoprime on 2012-09-06
My NAS is an old ReadyNas X6 by infrant (NetGear). Pretty hackable - have root. They support updates and plugins on regular basis. I believe it's a non intel chip running debian.

---

### Post by nickrout on 2012-09-06
> **tomoprime said:**
> My NAS is an old ReadyNas X6 by infrant (NetGear). Pretty hackable - have root. They support updates and plugins on regular basis. I believe it's a non intel chip running debian.

I think it would be easier to put a small hard drive in the backend and then mount your storage via nfs or cifs on the nas. 

minimyth will operate as a slave backend but not a master.

---

### Post by 3Slyfpolf on 2013-03-31
I built my diskless frontend by following the instructions [here]("https://help.ubuntu.com/community/DisklessUbuntuHowto"). Once I had a basic Ubuntu diskless setup, I used apt-get to install the xserver and mythtv-frontend.

---

### Post by cncook001 on 2013-12-29
Take a look at this page:

[http://www.mythtv.org/wiki/Diskless_LTSP_Frontend](http://www.mythtv.org/wiki/Diskless_LTSP_Frontend)

Craig

---

