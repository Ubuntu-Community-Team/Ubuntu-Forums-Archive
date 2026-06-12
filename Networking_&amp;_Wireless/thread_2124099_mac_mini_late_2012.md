---
title: "mac mini late 2012"
date: 2013-03-09
forum: Networking &amp; Wireless
---

### Post by sparklyballs on 2013-03-09
hi, i've just within the last hour or so installed 12.10 on my late 2012 mac mini. 

i'm looking to utilise it for xbmc and a tv server (possibly with myth), however i am failing at the very first hurdle it would seem. 

i can't get wireless or ethernet working, i read some posts about it not having a driver, all the posts i have read the fixes all start with installing dkms 

i've tried sudo apt-get install dkms and it says unable to locate package, then i found another post about there being a dkms package on the installation disk under pool/d/dkms.

i clicked it and the package manager thing opened up, but the install button is greyed out and won't let me press it. 

so my question is, how can i get either wireless or wired internet access (or local lan access for that matter) with my mac mini running 12.10 ?

---

### Post by varunendra on 2013-03-11
Hi,

Please let us see the card and related drivers in use -
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
```
Enter the above commands in a terminal (Ctrl+Alt+T) and post back the outputs here.
Make sure to use 'Code' tags to preserve formatting of the output (follow the example link in my signature to see how to)

---

### Post by sparklyballs on 2013-03-11
> **varunendra said:**
> Hi,

Please let us see the card and related drivers in use -
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
```
Enter the above commands in a terminal (Ctrl+Alt+T) and post back the outputs here.
Make sure to use 'Code' tags to preserve formatting of the output (follow the example link in my signature to see how to)


right at this moment i am in the process of restoring the mac mini to a one partition install of mac osx, i've one more try at this before i give up with linux as a lost cause. 

what led me down this path was xbmc of all things, on the mac mini apple won't release api's (i think that's what they're called) to allow the intel hd4000 to pass hd-audio to my surround sound system. so i tried windows 7 and it worked very well for that, but then i decided on pvr tv functions and was less than impressed with the options for windows 7.

so i find myself with what seems to be the only operating system that can do a little of everything or maybe more ?, i can get the ethernet drivers working info from this post, [http://bharath.lohray.com/weblog/installing-mint-on-a-late-2012-macmini/](http://bharath.lohray.com/weblog/installing-mint-on-a-late-2012-macmini/)  

i've also found some kernel patches and an alsa lib patch that supposedly cures the intel on linux hd-audio situation, but i've no information on how to apply them. 

how does one apply patches to a kernel and alsa and how do i stop the software centre thing from "upgrading" my kernel and borxing the ethernet drivers and just updating things like openlibre etc .... ?

---

### Post by sparklyballs on 2013-03-11
ps. i can also get wireless working and it seems to survive kernel updates, using information from the same post about the ethernet, but wireless unfortunately doesn't have the umph to play my movies and service mysql requests.

---

### Post by varunendra on 2013-03-11
> **sparklyballs said:**
> right at this moment i am in the process of restoring the mac mini to a one partition install of mac osx, i've one more try at this before i give up with linux as a lost cause. 
IMO, unless there is some good reason drop or pick an OS, it is a good idea to just go with the one that satisfies our needs.
Different OS have different advantages/disadvantages and similarly different are the needs of different users. No one can be perfect for everyone.

If you like the advantages of Linux/Ubuntu, then it's entirely up to you how much you weight them against the possible hassles of making it work for your specific needs.

> how does one apply patches to a kernel and alsa and how do i stop the software centre thing from "upgrading" my kernel and borxing the ethernet drivers and just updating things like openlibre etc .... ?
I have no idea about applying patches to a kernel, although a quick search suggests it is not something too difficult or too uncommon, but I just never needed it, so...

As for stopping SC from auto updating, go to -
**Ubuntu Software Center > Edit > Software Center > Updates** tab > change the settings to suit your choice.

---

### Post by mastablasta on 2013-03-11
you could create a script that would do all the things you have in that post. so once you would install  and update you would only need to run the script.

another option is as suggested to also give 13.04 beta a try. a newer version of kernel might have propper drivers or solutions already built in. another option are bleeding edge distros such as Fedora and Arch. they both have much newer kernels.

patching the kernel can be done via script if it was provided or sometimes via PPA. what you did to get the ethernet driver working is that basically you patched kernel with your new drivers. on update this wasn't done (sicne you did it manually before) and you would just have to do it again manually. this is sort of the same if you needed proprietary graphics drivers. only there solution is usually provided via system tool and that one perform the patching on upgrade.

you can get to older kernel by holding shift before grub appears.

intel audio HD is a hit and miss it seems. i am still having porblems with it occasionally. othertimes it works perfectly. 

everything works very well and out of the box if the hardware is compatible or if manufacturers provided propper drivers for it.

---

