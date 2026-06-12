---
title: "Nvidia Drivers With Maverick"
date: 2010-05-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zenarcher on 2010-05-20
I'm just curious if anyone has tried the proprietary Nvidia video drivers with Maverick.  I haven't given that a try as of yet, so wondering if anyone has experience with that.

Cheers,
zenarcher

---

### Post by philinux on 2010-05-20
> **zenarcher said:**
> I'm just curious if anyone has tried the proprietary Nvidia video drivers with Maverick.  I haven't given that a try as of yet, so wondering if anyone has experience with that.

Cheers,
zenarcher

Since it's still lucid in disguise it works just fine.

Aha "lucid in disguise with diamonds....."

---

### Post by zenarcher on 2010-05-20
Ah, thanks for that.  I guess I wasn't thinking.:P  I'll go ahead and give it a try on the install.

Thanks,
zenarcher

---

### Post by donniezazen on 2010-05-20
Yep, Nvidia works fine, may be better than Nouveau. The startup screen is not as polished as in Nouveau but other than that it works better than Nouveau.

---

### Post by Merk42 on 2010-05-20
> **philinux said:**
> Since it's still lucid in disguise it works just fine.

Aha "lucid in disguise with diamonds....."

Lucid in disguise with **drivers**

---

### Post by nanog on 2010-05-20
I expect we will see some breakage with the debian sync and 2.6.35.

---

### Post by autocrosser on 2010-05-20
Yes--looks "interesting"---I'm on the outside edge using the edgers PPA--so will make for a fun time............:)

---

### Post by bladerunner6 on 2010-05-21
I wasn't able to get the 173 drivers working, maybe incompatible with 2.6.34 ?

moans about the source not available even though I installed and unpacked it

---

### Post by wojox on 2010-05-21
Yup got 195 drivers running under 2.6.34-2 kernel.

---

### Post by philinux on 2010-05-21
Kernel 2.6.34.-3, 
nVidia current 195.36.15 8600GT

Just booted in and all fine. Compiz smooth as ever.

---

### Post by ronacc on 2010-05-21
> **autocrosser said:**
> Yes--looks "interesting"---I'm on the outside edge using the edgers PPA--so will make for a fun time............:)

oh boy time to get out the seasick pills , my 24" panasonic looks like crap with vesa . :lolflag:

---

### Post by ronacc on 2010-05-24
new nvidia driver out 256.25  not in jockey yet but hand installs with 2.6.34-3 see SS

---

### Post by dino99 on 2010-05-24
how its working ?
only "current" packages are out, miss "common", i'm still waiting for complete updates

---

### Post by xeizo on 2010-05-24
They are working very well; but I use the downloaded drivers from Nvidia. Installing them was a breeze. I run the latest Maverick packages(without client side decorations for gtk+2.0 courtesy of Kjell L.)) , Xorg-edgers, Ricotz unstable, Compiz, Wine daily git etc and have had NO problems with 256.25, even overclocking works fine when adding coolbits. One peculiarity is that it's now possbible to clock the gddr a couple of 100MHz higher than before.  I run Wine with Steam and in example have been running Oblivion GOTY DLE for a couple of hours today at the highest settings. Ultra-stable and very good fps!(and that's on Maverick)  ;)

---

### Post by wojox on 2010-05-24
Ha. I've finally got the 2.6.34-3-generic kernel

---

### Post by dino99 on 2010-05-24
> **xeizo said:**
> They are working very well; but I use the downloaded drivers from Nvidia. Installing them was a breeze. I run the latest Maverick packages(without client side decorations for gtk+2.0 courtesy of Kjell L.)) , Xorg-edgers, Ricotz unstable, Compiz, Wine daily git etc and have had NO problems with 256.25, even overclocking works fine when adding coolbits. One peculiarity is that it's now possbible to clock the gddr a couple of 100MHz higher than before.  I run Wine with Steam and in example have been running Oblivion GOTY DLE for a couple of hours today at the highest settings. Ultra-stable and very good fps!(and that's on Maverick)  ;)

thanks for feedback; i'm still having minor issue with the new gtk2 packages: when a right-click open a sub-windows to choose settings, this sub-windows close if right-click is not hold down (tested with ipblock)

---

### Post by xeizo on 2010-05-24
ipblock works fine here, with right-click ... (have to remember to disable everytime I use Steam, it thinks Steam is suspicious).

---

### Post by bladerunner6 on 2010-05-25
still waiting for 173 drivers to work, i think nvidia need to bring out updated package

---

### Post by dino99 on 2010-05-26
> **bladerunner6 said:**
> still waiting for 173 drivers to work, i think nvidia need to bring out updated package

as i've understood, 256 is the new step for all cards

---

### Post by bladerunner6 on 2010-05-26
only for geforce 6 onwards, i have a geforce 5 series

---

### Post by tad1073 on 2010-05-26
kernel update 2.6.34-4 breaks nvidia; haven't tried to uninstall and reinstall the drivers, didn't feel like fooling with it.

---

### Post by cariboo on 2010-05-26
I've been using the 2.6.34-4 kernel with the 256.25 drivers for the last 6 hours with zero problems. I was having a few problems with yesterdays kernel and the same drivers.

---

### Post by tad1073 on 2010-05-26
> **cariboo907 said:**
> I've been using the 2.6.34-4 kernel with the 256.25 drivers for the last 6 hours with zero problems. I was have a few problems with yesterdays kernel and the same drivers.

guess I should have specified the driver in question, which is 195.36.24

---

### Post by ayates on 2010-05-26
> **bladerunner6 said:**
> still waiting for 173 drivers to work, i think nvidia need to bring out updated package

I'm using the 2.6.34-4-generic kernel and the 173.14.25 proprietary driver with no problems.

---

### Post by jppr on 2010-05-27
i have nvidia-current (195.36.24) driver and system run without problems (2.6.34-4 kernel)

---

### Post by xeizo on 2010-05-27
2.6.34-4 works fine here with nvidia-current(256.25), it even boots fine after installing them without having to edit xorg.conf or anything. With 2.6.34-3 and the Nvidia-driver before I had to install Nvidia manually from Nvidias binary blob. A definite improvement.

---

### Post by bladerunner6 on 2010-05-27
> **ayates said:**
> I'm using the 2.6.34-4-generic kernel and the 173.14.25 proprietary driver with no problems.

well they don't build for me, i assume glxinfo shows the nvidia direct rendering

also your using the manual drivers direct from nvidia? how did you install them

update: i got them working, i think it was blacklisting nouveaufb also.

---

### Post by tad1073 on 2010-05-27
I fixed the problem. When kernel 2.6.34-4 came down with update manager the source and headers did not come down with them.

---

### Post by wayneericgouin on 2010-05-27
Does the xorg-edgers ppa update the Proprietary Nvidia drivers? Jockey didnt report anything new so I guess perhaps im unclear on whats in the ppa.

---

### Post by cariboo on 2010-05-27
The update wouldn't show up in jockey-gtk once the original driver has been installed, just do a regular update using synaptic, or the terminal, and the new drivers will be installed.

---

### Post by LaneLester on 2010-06-12
I sure don't understand what I'm seeing, based on the above experiences.

Today (6/12) I downloaded and installed the Ubuntu Maverick Minimal CD. I then used a script to install the software I use. Finally, I used Synaptic to mark nvidia-current for installation. It informed me that, while it was installing the drivers, it would be deleting xorg and everything with "xorg" in its name.

I decided that would be pointless. Here's hoping for a Maverick I can use with my fairly-new nVidia motherboard chipset.

Lane

---

### Post by cariboo on 2010-06-12
Would your problem have something to do with [this]("http://ubuntuforums.org/showthread.php?t=1503555")?

---

### Post by LaneLester on 2010-06-12
> **cariboo907 said:**
> Would your problem have something to do with [this]("http://ubuntuforums.org/showthread.php?t=1503555")?

Yes, I expect it does, although no one has reported the same symptoms as I got.

Thanks for letting me know about that thread.

Lane

---

### Post by VastOne on 2010-06-14
> **cariboo907 said:**
> The update wouldn't show up in jockey-gtk once the original driver has been installed, just do a regular update using synaptic, or the terminal, and the new drivers will be installed.

I am running 2.6.35 rc3 and have followed all of these instructions and watched every thing from the xorg-edger ppa install.  I did get an error at the end regarding nvidia 173:

Bad return status for module build on kernel: 2.6.34-020634-generic (x86_64)

E: Sub-process /usr/bin/dpkg returned an error code (1)

I cannot get any nVidia drivers to load other than a NVIDIA Accelerated graphics driver, which I have never seen before...

Can anyone give me a point in the right direction on this?

---

### Post by cariboo on 2010-06-14
Which version of xserver-xorg-core are you running?

---

### Post by VastOne on 2010-06-14
> **cariboo907 said:**
> Which version of xserver-xorg-core are you running?

I borked my system to the point of wiping and starting over...

I accomplished what I set out to do in getting my git knowledge up to speed and another way of compiling these kernels

Thanks but I think I will wait till the nVidia dust settles on the latest kernel releases and try again then.

---

### Post by LaneLester on 2010-06-14
After adding the xorg-edger ppa, I succeeded in installing nvidia-current with synaptic to my Ubuntu Minimal CD install: 
```
sudo add-apt-repository ppa:xorg-edgers/ppa
```

This time synaptic didn't want to remove xorg while it was installing the nvidia driver.

In the last day or two there have been updates to xorg and nvidia-current (now at 256-something).

Lane

---

### Post by philinux on 2010-06-14
> **LaneLester said:**
> After adding the xorg-edger ppa, I succeeded in installing nvidia-current with synaptic to my Ubuntu Minimal CD install: 
```
sudo add-apt-repository ppa:xorg-edgers/ppa
```

This time synaptic didn't want to remove xorg while it was installing the nvidia driver.

In the last day or two there have been updates to xorg and nvidia-current (now at 256-something).

Lane

Vanilla install and my xorg is all up to date since I removed nvidia-current. If you use jockey it removes all of xorg without telling you.

I'm checking in synaptic now to see the state of play.

---

### Post by cariboo on 2010-06-14
> **LaneLester said:**
> After adding the xorg-edger ppa, I succeeded in installing nvidia-current with synaptic to my Ubuntu Minimal CD install: 
```
sudo add-apt-repository ppa:xorg-edgers/ppa
```

This time synaptic didn't want to remove xorg while it was installing the nvidia driver.

In the last day or two there have been updates to xorg and nvidia-current (now at 256-something).

Lane

Xorg-edgers would prefer you not post instructions on how to enable the repositories, without linking to the page also.

From the xorg-edgers ppa page:

> ** Please do not publish instructions for how to install from this archive without linking to this page! Anyone using packages from this archive is expected to read this page first and it is recommended to check back occasionally for notice on problems that may arise. **

---

### Post by russianbandit on 2010-06-14
What's the status of the nvidia driver? I want to install the Alpha again, but don't want my video to break like last time when I installed the nvidia driver.

---

### Post by bladerunner6 on 2010-06-14
just use nouveau/gallium till nvidia fix 173x for xorg 1.8

---

### Post by recluce on 2010-06-14
I am currently using NVidia drivers 195.36.24 in Maverick. I can confirm that this driver has been working well in all kernels so far, including 2.6.35.2. 

However, I am still on the old x.org packages. Aptitude safe-upgrade is currently holding back 37 upgrades (all or almost all relating to x.org). Am I assuming correctly that Aptitude is holding back because of the Nvidia drivers in use? In other words: remove NVidia drivers to update x.org?

---

### Post by VastOne on 2010-06-14
> **bladerunner6 said:**
> just use nouveau/gallium till nvidia fix 173x for xorg 1.8

I just rebuilt 2.6.35 rc3 again and this time the nouveau/gallium worked like it should have...

Thanks...

---

### Post by philinux on 2010-06-15
> **russianbandit said:**
> What's the status of the nvidia driver? I want to install the Alpha again, but don't want my video to break like last time when I installed the nvidia driver.

Newly built against the latest X. Installed and working here. Make sure it's available otherwise jocky will remove X. All of it.
[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01557.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01557.html)

---

### Post by uBeer on 2010-06-15
I have all the latest packages installed, but when I move my xorg.conf in place that should load the nvidia drivers it fails.

I have nvidia-settings installed as well, but it doesn't show up in the menu and if I try to start it from the commandline I get this:
```

** (nvidia-settings:3410): CRITICAL **: menu_proxy_module_load: assertion `dbusproxy != NULL' failed
Segmentation fault
```

Does anyone have a clue about how I can try to fix this?

---

### Post by dino99 on 2010-06-15
[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/593474](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/593474)

check "affect me too" if you have the same issue

---

### Post by VastOne on 2010-06-15
New updated X and I now have 195.36.24 nVidia driver moving up from 195.36.15 on 2.6.35-rc3

X 1.7.6

---

### Post by russianbandit on 2010-06-15
> **VastOne said:**
> New updated X and I now have 195.36.24 nVidia driver moving up from 195.36.15 on 2.6.35-rc3

X 1.7.6

Are you using proprietary nvidia drivers? What method did you use to update the driver?

---

### Post by VastOne on 2010-06-15
> **russianbandit said:**
> Are you using proprietary nvidia drivers? What method did you use to update the driver?

Yes. 

I did a clean install yesterday using the .debs from the mainline [_[COLOR="Red"]here[/COLOR]_]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc3-maverick/") which installed the default of 195.36.15 drivers.  

In today's updates I received a new xorg and was bumped up to 195.36.34

I did nothing but standard installs, with a vanilla software source.

I actually do have this software source setup

[http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu)

---

### Post by VastOne on 2010-06-15
Built kernel 2.6.35.999 and the nVidia drivers 195.36.34 held up and running strong.

---

### Post by uBeer on 2010-06-16
> **dino99 said:**
> [https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/593474](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/593474)

check "affect me too" if you have the same issue

Thanks, it's the same issue! Though I'm now happily using the nouveau packages from the xorg-edgers that give me open source wobbly windows! And better playback of full screen flash movies. Now I don't have to explain anymore to my friends that I use open source drivers and thus can't watch YouTube stuff full screen...

I got some weird hang-ups but I believe that was caused by some faults in an ntfs partition... Weird bug as well.

---

### Post by VastOne on 2010-06-16
> **philinux said:**
> Vanilla install and my xorg is all up to date since I removed nvidia-current. If you use jockey it removes all of xorg without telling you.

I'm checking in synaptic now to see the state of play.

If I want to use the edgers ppa, do I remove the nvidia-current before adding the ppa or does that happen during the ppa update?

I have pp-purge ready and want to use the edgers ppa, but I am unsure of the step by step.

Would you mind outlining it?

Thanks

---

### Post by VastOne on 2010-06-16
Was able to get X 1.8.2 RC1 running with kernel 2.6.35.999 and 256.29 nvidia drivers.

Saw that nvidia-config is now nvidia-settings and that threw me a bit...

All appears to be running right, will test some more...

---

### Post by DooDle on 2010-06-23
> **VastOne said:**
> Was able to get X 1.8.2 RC1 running with kernel 2.6.35.999 and 256.29 nvidia drivers.

Saw that nvidia-config is now nvidia-settings and that threw me a bit...

All appears to be running right, will test some more...

As you did manage to do it, could you highlit us..? Please..?
Even with links...
How did you update to X 1.8.2, and the nVidia drivers..?
I'm running 10.10 with 2.6.35 (can't remember which, the r5 I think)

Thanks in advance...

---

### Post by VastOne on 2010-06-23
> **DooDle said:**
> As you did manage to do it, could you highlit us..? Please..?
Even with links...
How did you update to X 1.8.2, and the nVidia drivers..?
I'm running 10.10 with 2.6.35 (can't remember which, the r5 I think)

Thanks in advance...

I am using the xorg-edgers ppa [[COLOR="Blue"]_here_[/COLOR]]("https://launchpad.net/~xorg-edgers/+archive/ppa") and it is handling all the workload for me.  

Currently at X 1.8.1.902 (10801902) nVidia 256.35 on

2.6.35-999-generic #201006151505 SMP Tue Jun 15 14:08:25 UTC 2010 x86_64 GNU/Linux   (Current daily)

---

### Post by cecilpierce on 2010-06-24
I'm using xorg-edgers ppa and nvidia 256.35, does anyone know why the 3 button mouse emu (button 1&2 togeter) does not work?
I have another Maverick install without xorg-edgers and nvidia 195.?? and it works fine.

Thanks, Cecil ;)

I noticed if I hold the mouse wheel down it acts like the 3rd button, but sometimes rolls to the next window, hmmm?

---

### Post by DooDle on 2010-06-24
> **VastOne said:**
> I am using the xorg-edgers ppa [[COLOR="Blue"]_here_[/COLOR]]("https://launchpad.net/~xorg-edgers/+archive/ppa") and it is handling all the workload for me.  

Currently at X 1.8.1.902 (10801902) nVidia 256.35 on

2.6.35-999-generic #201006151505 SMP Tue Jun 15 14:08:25 UTC 2010 x86_64 GNU/Linux   (Current daily)

So, I got the ppa added, OS upgraded... No worry so far.
Question though... How do you install the nVidia 256.35..?
Do you download something somewhere..? Are they coming as well with the ppa source..?
Do I have to do something in the configuration, somewhere, somehow..?

Edit : OK, I got it, found it there : [http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)

I'm puzzled on this one... Any help, please..?

---

### Post by VastOne on 2010-06-24
> **DooDle said:**
> So, I got the ppa added, OS upgraded... No worry so far.
Question though... How do you install the nVidia 256.35..?
Do you download something somewhere..? Are they coming as well with the ppa source..?
Do I have to do something in the configuration, somewhere, somehow..?

I'm puzzled on this one... Any help, please..?

Once you added the ppa, did you do a sudo apt-get update and then a sudo apt-get upgrade  ?

That is all I had to do....

---

### Post by DooDle on 2010-06-24
> **VastOne said:**
> Once you added the ppa, did you do a sudo apt-get update and then a sudo apt-get upgrade  ?

That is all I had to do....

I did, but still booting using nouveau driver...

Edit :
I finally have it to work...
After rebooting, get into a terminal and run :
   sudo nvidia-xconfig
and reboot again... Voila!

---

### Post by blwegrzyn on 2010-09-17
I have Dell Latitude D630 nVidia Quadro NVS 135M

So i updated 10.04 to 10.10
and i have installed the nvidia-current

The driver installs fine and i can see it here:
blwegrzyn@blwegrzyn-laptop:/lib/modules/2.6.35-22-generic/updates/dkms$ ls -l
total 15216
-rw-r--r-- 1 root root 13612216 2010-09-17 10:36 nvidia-current.ko
-rw-r--r-- 1 root root  1914496 2010-09-17 09:14 vboxdrv.ko
-rw-r--r-- 1 root root    13168 2010-09-17 09:14 vboxnetadp.ko
-rw-r--r-- 1 root root    32384 2010-09-17 09:14 vboxnetflt.ko
blwegrzyn@blwegrzyn-laptop:/lib/modules/2.6.35-22-generic/updates/dkms$ 

i noticed that nvidia-xconfig is missing with above? Why?

when i try:
blwegrzyn@blwegrzyn-laptop:/lib/modules/2.6.35-22-generic/updates/dkms$ sudo modprobe nvidia-current 
[sudo] password for blwegrzyn: 
FATAL: Error inserting nvidia_current (/lib/modules/2.6.35-22-generic/updates/dkms/nvidia-current.ko): No such device
blwegrzyn@blwegrzyn-laptop:/lib/modules/2.6.35-22-generic/updates/dkms$ 

so what is the deal with the use of nvidia on 10.10?
something changed i guess?

---

### Post by cariboo on 2010-09-17
The last install I did on a system about a week ago automagically created a /etc/X11/xorg.conf file, the system uses an 8400GS connected to a LG 17" crt. I haven't looked into whether nvidia-xconfig was installed, as everything just worked.

---

### Post by coffeecat on 2010-09-21
> **cariboo907 said:**
> The last install I did on a system about a week ago automagically created a /etc/X11/xorg.conf file, the system uses an 8400GS connected to a LG 17" crt. I haven't looked into whether nvidia-xconfig was installed, as everything just worked.

@cariboo907, I hope you still have this thread subscribed because I'm interested that you have the 8400GS and I have an observation and a question.

My main desktop has (or, rather, had until a little while ago) a nvidia 8400GS card, and very happy I was with it until now. The only issue using the proprietary driver in Lucid was the ugly plymouth splash. All my Maverick testing had been  on my ATI graphics laptop until the other day when I installed it on a spare partition on the desktop, installed the proprietary nvidia driver and found an unexpected issue. I was surfing this forum and, at the same time, I had a  'sudo tar -czvf' of another partition going on in the background. OK, that's an intensive operation, but firefox was extermely laggy and unresponsive, almost to the point of being unusable. The rest of the desktop too, not just firefox. I expect a slight performance hit, but not as extreme as this, and I haven't seen this in earlier releases. I have a Phenom quad-core processor which should cope!

Suspecting that the nvidia driver was the culprit I tried disabling it and tried the same combination of tasks. Things were somewhat better, but even with no tar process going on in the background, the whole desktop felt hesitant.

As an experiment I've removed the Nvidia card and installed an ATI HD 4350. I've got another large tar going on the background even as I type and firefox and the whole desktop feels much more sprightly - not really different from not having a lengthy tar going on. I even get compiz with the ATI open-source driver, **and** an elegant Plymouth as a bonus.

So my question: have you noticed any problem with the 8400GS + proprietary driver compared with Lucid?

I'm going to keep the ATI card in, at least for now. I think history is being made. A Linux user preferring an ATI card over a nvidia one. Whatever next? :-s

---

### Post by realzippy on 2010-09-21
*I'm going to keep the ATI card in, at least for now. I think history is being made....*

...so the ATI Card works better than the 8400 in Lucid did?!

---

### Post by cariboo on 2010-09-21
I've had no problems with the 8400GS, I was using it last week after the last install to rip and encode DVDs while surfing, and I didn't notice any slow downs. I don't use firefox much any more, so I can't comment on that. 

I have two other systems with Nvidia cards and I haven't noticed any slow downs on them either, on the system I'm using right now, I have gnome-shell running, with Chromium in one workspace, Deluge in another, I find that it can be a bit of a pig as far as resources go, Acrobat in a third, and two terminals monitoring jobs on other systems.

The one thing I have to say about the 8400GS is that it takes a licking and keeps on ticking. The fan died on it, and the temps got up to the mid 90's C before I caught it, and it now runs a little warmer 51°C as opposed to low 40°C on the other two Nvidia cards, but other than that I'm happy with it.

All three systems with maverick installed use nvidia current, and except for this system I'm using at the moment, I've haven't had to make any adjustments to /etc/X11/xorg.conf. This system runs through a KVM and has an old 19" crt connected to it, which isn't detected properly, so I have to set the Horizontal and Vertical frequencies by hand.

---

### Post by coffeecat on 2010-09-21
> **cariboo907 said:**
> I have two other systems with Nvidia cards and I haven't noticed any slow downs on them either, on the system I'm using right now,

Thanks for your interest. I suspect it may be because  there's also an onboard nvidia graphics chipset on this machine. It *should* be autodisabled in the BIOS, but.... :? I've had odd issues where there are both onboard and PCIe nvidia cards before.

With the nvidia driver the desktop was all but unusable. I'll put this down to my particular combination of hardware. Thanks

> **realzippy said:**
> *I'm going to keep the ATI card in, at least for now. I think history is being made....*

...so the ATI Card works better than the 8400 in Lucid did?!

Certainly in Maverick it does. I've only run Lucid for a couple of minutes with the ATI card, but it seems OK. For a fair test I must use it for longer and see if any issues come up. But I don't game and if I can enable compiz for a bit of eye-candy, I'm happy. And that's one thing the open source ATI driver can do with this card (and the HD4200 in my laptop), that the nouveau driver can't do with the 8400GS. We might see compiz with nouveau in 11.04, but not in Maverick. Not unless you enable a ppa.

I must say though, it does feel very strange being happy with an ATI card while using Linux. Seems all wrong! :wink:

**Edit:**

> **cariboo907 said:**
> The one thing I have to say about the 8400GS  is that it takes a licking and keeps on ticking. The fan died on it, and  the temps got up to the mid 90's C before I caught it, and it now runs a  little warmer 51°C as opposed to low 40°C on the other two Nvidia  cards, but other than that I'm happy with it.

My 8400GS is passively cooled - no fan at all. I bought it because, at the time, it was the best specced nvidia card with passive cooling that I could find. I have an intolerance for noisy machines, spending a fortune on "silent" fans, CPU coolers and PSUs. The ATI card is passively cooled as well - so I'm happy. :)

---

### Post by cariboo on 2010-09-21
I'd forgotten about the onboard graphics chipset, that particular system has an ati radeon xpress 200 graphics adapter. It doesn't show up using lspci, so I know it's disabled.

---

### Post by coffeecat on 2010-09-22
> **cariboo907 said:**
> I'd forgotten about the onboard graphics chipset, that particular system has an ati radeon xpress 200 graphics adapter. It doesn't show up using lspci, so I know it's disabled.

Yes, the problem I had with another machine with both onboard and PCIe nvidia cards was because the BIOS didn't autodisable the onboard with a PCIe plugged in and I didn't notice. But this machine has; only one card is enabled in BIOS and only the PCIe is showing up in lspci.

Oh well. I'll write this off as an oddity with this particular machine. Thanks for your comments. At least there's one happy ATI user!

---

### Post by Grendelmon on 2010-09-23
> ...but firefox was extermely laggy and unresponsive, almost to the point of being unusable. The rest of the desktop too, not just firefox. I expect a slight performance hit, but not as extreme as this, and I haven't seen this in earlier releases. I have a Phenom quad-core processor which should cope!

I think I might be seeing the same issue. I created this post:

[http://help.ubuntuforums.org/showthread.php?p=9867655#post9867655]("http://help.ubuntuforums.org/showthread.php?p=9867655#post9867655")

I don't have the nvidia driver version in front of me right now. The entire desktop is laggy when the driver is activated. The gnome-system-monitor shows that my dual cores peg at 100%. If I disable the drivers everything is fine.

My motherboard is an Asus P5N32-SLI, which has an nvidia chipset and I'm using dual PCIe 9600GTs.

---

### Post by rasmus91 on 2010-09-23
Hi there.

I have a nvidia GT 330m CUDA (which means i have a button that should make the graphics switch to some intel onboard) but im unable to get the nvidia driver working. I can install the driver fine, and when i then reboot my computer it won't start. it halts at the "checking battery state", when i check on Google a lot of people have trouble with this. but i can't fine something that seems like the same problem as mine. The only thing i actually found that looked interesting was something that proposed wrong ACPI (or something) adressing of the graphic card, which is supposedly why it won't work. but that should be changeable in xorg.conf

I really don't understand this problem, but help is much appreciated. 

one other thing, i don't know if its relevant for the problem. but my computer, before it gets to the ubuntu splash screen, says something like: ```
FATAL: Could not load /lib/modules/2.6.35-22-generic/modules.dep: no such file or directory

FATAL: Could not load /lib/modules/2.6.35-22-generic/modules.dep: no such file or directory

(then something about a intel driver) ispci intel i900
``` 

im not sure about the intel thingie, i don't really get it, why does it try to load a intel graphics driver?

well. thanks for any help. :)

---

### Post by Grendelmon on 2010-09-23
> **Grendelmon said:**
> I think I might be seeing the same issue. I created this post:

[http://help.ubuntuforums.org/showthread.php?p=9867655#post9867655]("http://help.ubuntuforums.org/showthread.php?p=9867655#post9867655")

I don't have the nvidia driver version in front of me right now. The entire desktop is laggy when the driver is activated. The gnome-system-monitor shows that my dual cores peg at 100%. If I disable the drivers everything is fine.

My motherboard is an Asus P5N32-SLI, which has an nvidia chipset and I'm using dual PCIe 9600GTs.


Hmmm... okay, strange. I just re-enabled the Nvidia drivers, which is version 256.53, and now it works fine. My cpu cores are completely idle. Must have been an update or something I wonder.

:P

---

### Post by rasmus91 on 2010-09-23
> 

I think i might have located a part of the problem. I started in Recovery, i overlooked the X log

It looks like this: 

```
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    86.646] X Protocol Version 11, Revision 0
[    86.646] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    86.646] Current Operating System: Linux rasmus-acer 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64
[    86.646] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=6efdd980-ee79-4846-8c24-eb2bfe4afb6e ro quiet splash
[    86.646] Build Date: 16 September 2010  06:18:41PM
[    86.646] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    86.646] Current version of pixman: 0.18.4
[    86.646]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    86.646] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    86.647] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 23 13:38:08 2010
[    86.647] (==) Using config file: "/etc/X11/xorg.conf"
[    86.647] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    86.647] (==) ServerLayout "Layout0"
[    86.647] (**) |-->Screen "Screen0" (0)
[    86.647] (**) |   |-->Monitor "Monitor0"
[    86.647] (**) |   |-->Device "Device0"
[    86.647] (**) |-->Input Device "Keyboard0"
[    86.647] (**) |-->Input Device "Mouse0"
[    86.647] (==) Automatically adding devices
[    86.647] (==) Automatically enabling devices
[    86.647] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    86.647]     Entry deleted from font path.
[    86.647] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    86.647] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    86.647] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    86.647] (WW) Disabling Keyboard0
[    86.647] (WW) Disabling Mouse0
[    86.647] (II) Loader magic: 0x7d0200
[    86.647] (II) Module ABI versions:
[    86.647]     X.Org ANSI C Emulation: 0.4
[    86.647]     X.Org Video Driver: 8.0
[    86.647]     X.Org XInput driver : 11.0
[    86.647]     X.Org Server Extension : 4.0
[    86.648] (--) PCI:*(0:0:2:0) 8086:0046:1025:035b rev 18, Mem @ 0xd1400000/4194304, 0xc0000000/268435456, I/O @ 0x00004050/8
[    86.648] (--) PCI: (0:1:0:0) 10de:0a29:1025:035b rev 162, Mem @ 0xd0000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00003000/128, BIOS @ 0x????????/524288
[    86.648] (II) Open ACPI successful (/var/run/acpid.socket)
[    86.648] (II) LoadModule: "extmod"
[    86.649] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    86.649] (II) Module extmod: vendor="X.Org Foundation"
[    86.649]     compiled for 1.9.0, module version = 1.0.0
[    86.649]     Module class: X.Org Server Extension
[    86.649]     ABI class: X.Org Server Extension, version 4.0
[    86.649] (II) Loading extension MIT-SCREEN-SAVER
[    86.649] (II) Loading extension XFree86-VidModeExtension
[    86.649] (II) Loading extension XFree86-DGA
[    86.649] (II) Loading extension DPMS
[    86.649] (II) Loading extension XVideo
[    86.649] (II) Loading extension XVideo-MotionCompensation
[    86.649] (II) Loading extension X-Resource
[    86.649] (II) LoadModule: "dbe"
[    86.649] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    86.649] (II) Module dbe: vendor="X.Org Foundation"
[    86.649]     compiled for 1.9.0, module version = 1.0.0
[    86.649]     Module class: X.Org Server Extension
[    86.649]     ABI class: X.Org Server Extension, version 4.0
[    86.649] (II) Loading extension DOUBLE-BUFFER
[    86.649] (II) LoadModule: "glx"
[    86.649] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    86.656] (II) Module glx: vendor="NVIDIA Corporation"
[    86.656]     compiled for 4.0.2, module version = 1.0.0
[    86.656]     Module class: X.Org Server Extension
[    86.656] (II) NVIDIA GLX Module  256.53  Fri Aug 27 20:50:26 PDT 2010
[    86.656] (II) Loading extension GLX
[    86.656] (II) LoadModule: "record"
[    86.657] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    86.657] (II) Module record: vendor="X.Org Foundation"
[    86.657]     compiled for 1.9.0, module version = 1.13.0
[    86.657]     Module class: X.Org Server Extension
[    86.657]     ABI class: X.Org Server Extension, version 4.0
[    86.657] (II) Loading extension RECORD
[    86.657] (II) LoadModule: "dri"
[    86.657] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    86.657] (II) Module dri: vendor="X.Org Foundation"
[    86.657]     compiled for 1.9.0, module version = 1.0.0
[    86.657]     ABI class: X.Org Server Extension, version 4.0
[    86.657] (II) Loading extension XFree86-DRI
[    86.657] (II) LoadModule: "dri2"
[    86.658] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    86.658] (II) Module dri2: vendor="X.Org Foundation"
[    86.658]     compiled for 1.9.0, module version = 1.2.0
[    86.658]     ABI class: X.Org Server Extension, version 4.0
[    86.658] (II) Loading extension DRI2
[    86.658] (II) LoadModule: "nvidia"
[    86.658] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    86.658] (II) Module nvidia: vendor="NVIDIA Corporation"
[    86.658]     compiled for 4.0.2, module version = 1.0.0
[    86.658]     Module class: X.Org Video Driver
[    86.658] (II) NVIDIA dlloader X Driver  256.53  Fri Aug 27 20:29:45 PDT 2010
[    86.658] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    86.658] (--) using VT number 7

[    86.662] (EE) No devices detected.
[    86.662] 
Fatal server error:
[    86.662] no screens found
[    86.662] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    86.662] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    86.662] 
```

notice near the bottom where it says:

```
[    86.662] (EE) No devices detected.
[    86.662] 
Fatal server error:
[    86.662] no screens found
[    86.662] 
```

so if my graphics driver can't detect my screen, it will logically not be able to make an output to the screen, which would explain why my computer halts. But its still annoying. Does anyone know how to make sure that is detects my screen? i guess i'd have to change something in the xorg.conf file, right?

---

### Post by Grendelmon on 2010-09-23
> **Grendelmon said:**
> Hmmm... okay, strange. I just re-enabled the Nvidia drivers, which is version 256.53, and now it works fine. My cpu cores are completely idle. Must have been an update or something I wonder.

:P

Okay, I retract my previous statement. The issue happened again but I discovered it's only while xfce4-terminal is running. I have the xfce4 compositor running and I think it's a bug in Xubuntu.

---

### Post by rasmus91 on 2010-09-23
Hi there.

Im having a hell of troubles with this !(/&"!¤ nvidia driver, and its driving me mad, i can't tell you how many hours i've spent on this problem today, but its 4+ i feel like im reaching a dead end, im getting no useful responses, and when i google i can see that for other people with my computer it works out of the box.

Im tired now, and about to go to bed. so i thought to my self: "well, it's probably an incompatibility between the new kernel and the nvidia kernel. i wish. But i need my computer tomorrow, so i'll just reinstall the nouveau driver so i can have my graphic effects enabled.

But guess what?

Alle i get is the; Desktop effects could not be enabled. Im so damn frustrated. i know this is just a beta, but it that with the nvidia driver was the exact same problem on 10.04. I'll be so happy if anyone could just tell me wether it's my xorg.conf file i should look for something in or what, cus even though i've spent a lot of time fixing different problems on Ubuntu this is getting to me, Especially because its forcing me to use windows 7 for which i don't care.

I don't mean to be annoying, but please help me! I need Ubuntu for school, and for that i'd very much like a good graphics driver.

Thanks, and sorry for the whining.

---

### Post by cariboo on 2010-09-23
The Ubuntu Control Center is suppose to have an applet that allows you to switch between graphics chipsets. There is a thread somewhere in this sub-forum, but going [here]("http://www.webupd8.org/2010/06/ubuntu-control-center-brings-simplicity.html") to get it would be much easier.

---

### Post by rasmus91 on 2010-09-24
> The Ubuntu Control Center is suppose to have an applet that allows you to switch between graphics chipsets. There is a thread somewhere in this sub-forum, but going here to get it would be much easier.

Tried, doesn't seem to be such a thing.

Its like ubuntu doesn't recognize my graphic card...

---

### Post by Half-Left on 2010-09-24
> **rasmus91 said:**
> Hi there.

Im having a hell of troubles with this !(/&"!¤ nvidia driver, and its driving me mad, i can't tell you how many hours i've spent on this problem today, but its 4+ i feel like im reaching a dead end, im getting no useful responses, and when i google i can see that for other people with my computer it works out of the box.

Im tired now, and about to go to bed. so i thought to my self: "well, it's probably an incompatibility between the new kernel and the nvidia kernel. i wish. But i need my computer tomorrow, so i'll just reinstall the nouveau driver so i can have my graphic effects enabled.

But guess what?

Alle i get is the; Desktop effects could not be enabled. Im so damn frustrated. i know this is just a beta, but it that with the nvidia driver was the exact same problem on 10.04. I'll be so happy if anyone could just tell me wether it's my xorg.conf file i should look for something in or what, cus even though i've spent a lot of time fixing different problems on Ubuntu this is getting to me, Especially because its forcing me to use windows 7 for which i don't care.

I don't mean to be annoying, but please help me! I need Ubuntu for school, and for that i'd very much like a good graphics driver.

Thanks, and sorry for the whining.

Looks like some confusion between your two graphics. You have an intel and NVIDIA right? If so, can you disable the intel one in the bios?

---

