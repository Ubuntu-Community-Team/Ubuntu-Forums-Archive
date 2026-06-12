---
title: "Mythtv-frontend : Schema is 18 versions behind"
date: 2014-04-23
forum: Mythbuntu
---

### Post by martin90 on 2014-04-23
Last september, I installed Mythbuntu 12.04.3 on a Dell computer (Pentium 4, 3 GHz, made circa 2004) with 1 Gb of RAM as Mythtv-backend (0.25-3.49) only, working with HDHomeRun. Basically, the Dell machine is used only to record shows, but it's not good enough for playback.

My main machine used to be a Pentium 4, 3.4 GHz with 2 GB of RAM running Windows XP. I was using XBMC for playback until I installed Ubuntu 12.04 on it, back in november, with mythtv-frontend only. Output in HDMI to the TV set, had a few dropped frames but result was acceptable.

I brought a used motherboard/CPU/Memory (Core 2 Quad CPU Q6600), installed Ubuntu 14.04 LTS, the 64-bit version. then installed mythtv-frontend (0.27) from the Ubuntu Software Center. After I enter the IP/port/MySQL infos, I get the following error message :
```
This version of MythTV requires an updated database.
 (schema is 18 versions behind)

Please run mythtv-setup or mythbackend to update your database.
```
(When I click OK, I get a notice that it crashed and restarted... I have to kill -9 PID from Terminal... *sigh*)

After some googling, I figured out that the backend and frontend must run the same version.

Question : How come newest frontend version is not backwards compatible with previous versions of mythtv-backend ?

This is where it gets frustrating.

- The mythbuntu.org website, download section, Upgrade Older Mythbuntu Install just links to the Ubuntu Network Upgrade Guide. Hey, I have 40+ unwatched recorded shows on the HDD, but the only tip I've been given is to backup my files. I can't fit all those shows on an USB drive and I have no informations whatsoever on how to upgrade mythbuntu without affecting my recorded shows. I downloaded mythbuntu 14.04, put it on a USB key and rebooted... but I was only given "Install" as an option. I stopped as there was no guarantee.

- I installed XBMC on this Ubuntu machine, but PVR Service has been taken away. Out of the scope for this forum, I'll just let it be.

- I decided to instead install the 0.25 version of mythtv-frontend. From the Software Center, older versions ain't a solution. Some googling hinted Synaptic Package Manager, select package, Force Version, but only 0.27 is part of the choices. I've been hinted to perform this : "sudo add-apt-repository ppa:mythbuntu/0.25", but after performing "sudo apt-get update", I get this message at the bottom :

W: Failed to fetch [http://ppa.launchpad.net/mythbuntu/0.25/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/mythbuntu/0.25/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/mythbuntu/0.25/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/mythbuntu/0.25/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

Consequently, the 0.25 version still ain't part of Force Version list from the Synaptic Package Manager.

I downloaded the 0.25.3 file from the mythtv.org website, released 2 tears ago, but I don't know how to compile...

Is there an easier solution or a workaround this error message ?

---

### Post by blm-ubunet on 2014-04-23
Don't install 14.04 on the FE.
AFAIK There is no 0.25 for mythbuntu 14.04.

Use same mythbuntu repositories on both..the old packages should still be there for 12.04.
You can get (the recommended) 0.27+fixes for mythbuntu 12.04LTS.

Or use the same ubuntu version & stock ubuntu versions of mythtv.

XBMC (myth plugin) is always a bit delayed (your packages at least) in matching the mythtv schema updates.

Your recordings a just files in a folder.
The database details for your recordings is located with the master BE so should be safe.

---

### Post by aelfric55 on 2014-04-23
Having installed plain vanilla Ubuntu 14.04, you might try installing the necessary debs from old mythtv 0.25 to see whether they will install and whether they will run on the current OS. They may or may not. 

Uninstall all of the mythtv 0.27 detritus you may have put on this frontend machine. The debs for mythtv 0.25 may be directly downloaded from here: [http://packages.ubuntu.com/precise/graphics/](http://packages.ubuntu.com/precise/graphics/) libmyth-0.25-0 is at [http://packages.ubuntu.com/precise/libs/](http://packages.ubuntu.com/precise/libs/)

For a frontend-only installation of myth 0.25, you should likely only require the packages libmyth-0.25-0, mythtv-common and  mythtv-frontend. Install the three debfiles using the simple gdebi package installer or similar. If the installer complains of a missing dependency, you may need to go back to the packages page and get the package for it. 

If the three packages install successfully, run mythfrontend from a terminal to see whether it launches, and then configure it to access your remote backend. If this mythfrontend 0.25  installation can be configured successfully, and you're happy with the result, lock the package version so that the machine won't try to upgrade the packages to mythtv 0.27 every time you do an update.

---

### Post by bullwinkle2 on 2014-04-23
> **martin90 said:**
> Question : How come newest frontend version is not backwards compatible with previous versions of mythtv-backend ?

That's something I think a lot of users would like to know.  It makes updating the version difficult because you have to do it on all your machines at once.  It would be nice if the newer frontends at least had a limited degree of backward compatibility with older backends.  That way you could update your frontends one at a time and then upgrade the backend after all the frontends have been updated.

> **martin90 said:**
> - I installed XBMC on this Ubuntu machine, but PVR Service has been taken away. Out of the scope for this forum, I'll just let it be.

If you are running XBMC Frodo or Gotham, there should not be any reason the PVR won't work, and unlike the MythTV frontends, XBMC will work with a wider range of MythTV backend versions.  The thing to make sure of is that the cMyth PVR addon is installed and configured.  Often on a new install of XBMC, it is not enabled by default so you have to go into the PVR addons and enable it.  I have XBMC Gotham running on an OS X Mavericks machine and it works great with a MythTV 0.25 backend, but when I installed the Gotham beta I did have to re-enable the cMyth plugin.  The fact that Gotham actually works well with the MythTV backend is a welcome surprise, since this functionality was broken in later versions of Frodo under OX X.

---

### Post by martin90 on 2014-04-23
mythtv-frontend 0.25 depends on libmyth 0.25 which depends on a specific version of libx264, in the case of precise, it's -120. Once those two packages installed, mythtv-frontend errors with message "cannot install 'gksu:i386' ".
I already have "gksu" installed, but not "gksu:i386"... Oh, turns out I downloaded the i386 version instead of amd64... Ooops.

Since it requires gksu 2.0.2-6ubuntu1, but gksu...untu2 is already installed on my system, I decided to pick the "quantal" version (mythtv 0.25.2) and re-download the 3 above files and let Software Center do its magic... Came with errors and it decided by itself to install the 0.27 version instead. Oh, for crying out loud !!!

---

### Post by aelfric55 on 2014-04-23
That's why you don't use the Software Center for unsupported things like this. Rely on a nice brain-dead installer like gdebi. Over-automation is not necessarily your friend.

But if the latest 0.25 debfiles end up requiring dependencies that are earlier than the files/libs already installed on your system, and will not install with the later versions of the files/libs your system has, then this method will not work.  Ubuntu dependency hell. Your choices in this case will be either to use XBMC as your frontend (even though its PVR interface is clunky and buggy), or to compile your own 0.25 from the tarball, based on the particulars of your current system (not particularly difficult), or to upgrade the backend to 0.27, which would be the only currently supported configuration among the three possibilities.

---

### Post by martin90 on 2014-04-24
Along the way yesterday, I installed fglrx in order to have some kind of AMD/ATI drivers ("lspci | grep VGA" says I have RV710 Radeon HD, but fglrx software says I don't have a compatible card. Huh?), shut down the computer for the night. This morning, while booting, I saw a stretch violet Ubuntu logo, then blank screen for 5 minutes, no mouse reaction... I had it !
So, I started up my old system running Windows XP (where the ubuntu ISO file is still located) to make a bootable USB key with Ubuntu 12.04 and re-installed Precise on this machine from scratch, then installed mythtv-frontend (0.25-2).

Problem worked-around with an OS downgrade, but not solved. After the TV season is over mid-may and the Mythtv-backend library will be empty, I'll re-install mythbuntu from scratch and then re-install this machine to Ubuntu 14.04.

Could have been much easier if mythtv-frontend was backwards compatible. The way the above-mentionned error message was formulated (schema X versions behind) makes me wonder if the programmers just tested mythtv with backend and frontend on the same machine and released it as-is.

---

### Post by aelfric55 on 2014-04-24
The incompatibility of differing versions of mythfrontend and mythbackend was a feature built in by the myth devs from nearly the very beginning a decade ago, and one I wouldn't think they'd change. Not really a problem from their standpoint, since all they issue are the tarballs for the various releases and revisions. It's just as easy for a user to compile and install a mythtv 0.23 installation on, say, a 3.14-kernel-up-to-the-minute machine as it is to compile and install a mythtv 0.27 version on that kernel or the same 0.27 version on a 2.6.33 kernel from four years ago. It all works. At least until the version is so old that it ceases to be compilable against modern libraries.

A problem only arises when the user has to rely on precompiled binaries supplied with a distribution, since they've been compiled against a fixed set of libraries supplied with a particular OS version. There's only a small leeway for installing precompiled binaries up and down versions before something breaks. Dependency checking (without a --force --nodeps option like rpm has) makes the range smaller still, because it blocks some installations that, if allowed to complete, might actually function.

So there's probably no easy solution except to be prepared, in a pinch, to compile from source and install what you need that way on occasion. Heck, if it could still compile against modern libraries, I'd probably still be running Mythtv 0.21, which was the last version I was entirely happy with.

---

### Post by tgm4883 on 2014-04-25
> **aelfric55 said:**
> The incompatibility of differing versions of mythfrontend and mythbackend was a feature built in by the myth devs from nearly the very beginning a decade ago, and one I wouldn't think they'd change. Not really a problem from their standpoint, since all they issue are the tarballs for the various releases and revisions. It's just as easy for a user to compile and install a mythtv 0.23 installation on, say, a 3.14-kernel-up-to-the-minute machine as it is to compile and install a mythtv 0.27 version on that kernel or the same 0.27 version on a 2.6.33 kernel from four years ago. It all works. At least until the version is so old that it ceases to be compilable against modern libraries.

A problem only arises when the user has to rely on precompiled binaries supplied with a distribution, since they've been compiled against a fixed set of libraries supplied with a particular OS version. There's only a small leeway for installing precompiled binaries up and down versions before something breaks. Dependency checking (without a --force --nodeps option like rpm has) makes the range smaller still, because it blocks some installations that, if allowed to complete, might actually function.

So there's probably no easy solution except to be prepared, in a pinch, to compile from source and install what you need that way on occasion. Heck, if it could still compile against modern libraries, I'd probably still be running Mythtv 0.21, which was the last version I was entirely happy with.

It's worth noting that the Mythbuntu team provides packages for a wide range of MythTV and Ubuntu releases to alleviate some of the hassles of distro upgrading (see [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) ). You can upgrade a 12.04 system to 0.27 which would be compatible with the 14.04 version (since it ships with 0.27). It's also worth noting that this version compatibility requirement is in the 14.04 release notes [http://www.mythbuntu.org/home/news/mythbuntu1404releasedbetterlatethanneveredition](http://www.mythbuntu.org/home/news/mythbuntu1404releasedbetterlatethanneveredition)

---

### Post by martin90 on 2014-04-25
> **tgm4883 said:**
> It's worth noting that the Mythbuntu team provides packages for a wide range of MythTV and Ubuntu releases to alleviate some of the hassles of distro upgrading (see [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) ). You can upgrade a 12.04 system to 0.27 which would be compatible with the 14.04 version (since it ships with 0.27).
Already tried it. In the Repositories tab, there's a drop-down menu, and when I select 0.27, it defaults back to 0.25. I received a few updates but I disabled it right after, not sure if I would be getting experimental codes and get stuck with a re-install from scratch.

---

### Post by tgm4883 on 2014-04-28
> **martin90 said:**
> Already tried it. In the Repositories tab, there's a drop-down menu, and when I select 0.27, it defaults back to 0.25. I received a few updates but I disabled it right after, not sure if I would be getting experimental codes and get stuck with a re-install from scratch.

If you select 0.27 and hit apply, it should save that. I'd try opening mythbuntu-control-centre from the command line, trying that again and seeing what error message you are getting.

---

### Post by dannyboy79 on 2014-04-28
compatibility between frontend and backend is crucial because some times they change the mysql table layout and or add or remove something so the schema check makes sure you're running the same version frontend as your backend.

if you wanted to stick with your mythtv 0.25 backend and wanted to be able to watch those shows from a 14.04 install of ubuntu you could've just installed xbmc frodo or gotham beta 4 and the pvr addon should've been able to interface with your mythtv backend.

my main backend is still running xubuntu 12.04 with mythtv 0.26+fixes and I have been waiting to upgrade it to xubuntu 14.04 and mythtv 0.27 when i have time since i am also upgrading the server hardware. my frontend i use for viewing is an original apple tv running crystalbuntu 2.0 which is ubuntu 12.04 base but boots directly into xbmc frodo.

another solution could've been to stay with your ubuntu 14.04 install and use mythrename or whatever the script is called these days but what it does it creates human readable filenames of your recordings and then you would share that directory of symlinks over samba which then you could use ubuntu 14.04 to watch them over samba. you wouldn't get the commercial flagging but that's not a big deal to me. then when you're done watching that episode you could use your backend to delete that show OR use mythweb to delete that episode.

---

### Post by martin90 on 2014-06-04
Just wanted to give an update to my adventure.

I had a few shows left, which was acceptable if I mess up and lost them, so I decided to upgrade both machines.

- Copy /var/lib/mythtv/recordings/* to an external HDD.
- Mythtv Control Center, Backup & Restore, click next, pickup the resulting file and save it to external HDD.
- Boot from USB Key, fresh install of Mythbuntu 14.04 64-bit, without the updates, as backend and frontend. -- Oddly enough, "Where Are You?" auto-detects Toronto. If I select Montreal, I can't continue.
- Perform system updates. -- Went to screensaver. When I woke it up, the system updates window was stuck. A reboot and it finished installing updates. Tried to Enable MySQL from the Mythbuntu Control Center, it stuck...
Not satisfied, I decided to re-install the OS again from scratch as primary backend. Disabled screensaver, then perform system updates. It stuck at "samba-common". Reboot, system updates completes.
- Mythbuntu Control Center, Restore database, then copied the recordings to /var/lib/mythtv/recordings.
- Ubuntu Software Center, install mythtv-frontend.
Everything seems to be working, except the channel logos ain't displaying.

On my Ubuntu machine
- Saved data to USB Key, install Ubuntu 14.04 64-bit from scratch. -- Again, can't continue if I select Montreal.
- install mythtv-frontend. Same mysql password as previous installation.

Vermont PBS station changed its PSIP name, so I went to Mythtv Backend Setup, Channel Editor, delete the channel and its subchannels, rescan, restore most channel logos, exit and restart backend.
The channel's PSIP was updated, but the channel logo aren't appearing in both frontend (the Myth server and the Ubuntu machine).

---

