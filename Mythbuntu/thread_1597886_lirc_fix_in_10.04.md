---
title: "lirc fix in 10.04"
date: 2010-10-15
forum: Mythbuntu
---

### Post by sudanmas on 2010-10-15
Any solid  fix for the lirc bug in 10.04 as yet?  I did a fresh install of 10.04 and as many have reported, their remote doesn't function.  I'm running a Hauppage 250 w/ the old gray remote.  irw from the command prompt produces no output at all with remote button presses  And the standard _**dmesg | grep lirc**_ shows the expected leadtek IR loaded.

Module versions;

lirc_dev 2.6.32-25-generic
lirc_i2c 2.6.32-25-generic

Unfortunately I'm just dipping my foot into the the ubuntu pool, so I know just enough to be dangerous.  Any cut and paste solutions around?  Should i upgrade to 10.10?

Any advice would be great - operating Mybuntu with my keyboard is fun, but the novelty is starting to wear off :-)

Rob

---

### Post by IceCap on 2010-10-15
Supposedly there is a bug in lirc that has been fixed in lirc 0.8.7.  Incidentally, lirc 0.8.7 is supplied with 10.10 but not 10.04 (I'm in the same boat as you with a PVR-350 card).
  If you Google "lirc 0.8.7" you can find the lirc website and they have directions on how to install 0.8.7.  However, unless you are fairly experienced with Linux those directions are going to be a bit long in the tooth to follow (they are for me).
  I'm holding off on upgrading to 10.10 until some of the (inevitable) bugs have been fixed.  I did upgrade from 9.10 (or maybe it was 9.04) to 10.04 and it went amazingly well.  I haven't heard much about upgrade problems here on the list though so it is promising ....

  IC

---

### Post by joama on 2010-10-16
Just want to add that lirc is not working for us in 10.04 either. This is the first time we've tried to use it so we thought we were just being noobs.  We're trying to use a homebrew IR blaster to control our set top box. We installed lirc using Synaptic and pasted the config file from [here]("http://lirc.sourceforge.net/remotes/comcast/3067BC2-R") into /etc/lirc/lircd.conf. We are testing our IR blaster using
```
irsend send_start Comcast_3067BC2-R KEY_1
```So far nothing is coming out of the serial port. From our understanding, DTR (pin 4) should change after issuing that command but it stays at a steady -11.32 V.

```
dmesg | grep lirc
[   19.186435] lirc_dev: IR Remote Control driver registered, major 61 
[   20.310032] lirc_serial: auto-detected active low receiver
[   20.310036] lirc_dev: lirc_register_driver: sample_rate: 0
[   20.310098] lirc_serial $Revision: 5.104 $ registered
```

We're hoping to see a solution for 10.04 instead of having to upgrade to 10.10. If nothing else, does anybody know if lirc 0.8.7 will be available for 10.04 without us having to compile it?

---

### Post by sr_guy on 2010-10-20
I tried a fresh install of 10.10 and unfortunately there is not an easy solution for the lirc problem that I can see. This seems to be kernel related, because if 10.04 upgrades to kernel 2.6.32-25 lirc breaks.

The easiest solution I found was:

cd /boot/grub

cp grub.cfg grub.cfg.bak (backup grub config, so it can be restored just in case)

comment out or remove:

```

}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd1,1)'
        search --no-floppy --fs-uuid --set 35fdb7b7-3389-4a6c-90ae-1e884679a12d
        linux   /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=35fdb7b7-3389-4a6c-90ae-1e884679a12d ro   crashkernel=384M-2G64M,$
        initrd  /boot/initrd.img-2.6.32-25

```


Use the next kernel in the list, in my case, 2.6.32-25-generic-pae. After a reboot, lirc worked fine. Make sure you keep the same formating in grub.cfg otherwise ubuntu won't boot (see example above).

---

### Post by ahood on 2010-10-20
I have several Hauppauge PVR cards (150, 350, and 500) and been using the silver A415 silver remote with Mythbuntu 8.04.

After upgarding to 10.04, this Hauppauge remote does not work. No response by irw. Searching for a fix. If I find one, I will post it here.

---

### Post by klc5555 on 2010-10-20
> **IceCap said:**
> Supposedly there is a bug in lirc that has been fixed in lirc 0.8.7.  Incidentally, lirc 0.8.7 is supplied with 10.10 but not 10.04 (I'm in the same boat as you with a PVR-350 card).
  If you Google "lirc 0.8.7" you can find the lirc website and they have directions on how to install 0.8.7.  However, unless you are fairly experienced with Linux those directions are going to be a bit long in the tooth to follow (they are for me).
  I'm holding off on upgrading to 10.10 until some of the (inevitable) bugs have been fixed.  I did upgrade from 9.10 (or maybe it was 9.04) to 10.04 and it went amazingly well.  I haven't heard much about upgrade problems here on the list though so it is promising ....

  IC

I hesitate to mention this, but lirc is a fairly benign little package, and there is leeway in which versions of lirc will run on which Ubuntu. If you're reasonably sure that 0.8.7 will fix your issues and don't want to compile it --the lirc.org source's "make_install" tends to put things in the wrong directories from the standpoint of Debian/Ubuntu systems --then there's a good chance that the 10.10 .deb for lirc 0.8.7 (from packages.ubuntu.com) will install and run on 10.04. This has worked in other circumstances: when I needed XMP support in lirc in Ubuntu 9.04, I replaced its included lirc 0.8.4a with 0.8.6 from Ubuntu 9.10, and things were fine.

There are a couple of caveats: once the lirc version was changed, all further configuration of lirc had to be done from the ncurses comand-line menu that appears after "sudo dpkg-reconfigure lirc", rather than from, say, the Mythbuntu control center.

Also, if the later version proves unsatisfactory for whatever reason, backing the version down to the earlier one is not completely trivial on Mythbuntu the way it is on some other distros. The later version of lirc has to be uninstalled prior to the earlier one being reinstalled; and in this the .deb package manager will likely insist on also ripping out most of Mythtv, for which lirc is a dependency. These packages would need to be reinstalled along with the older lirc version.

---

### Post by IceCap on 2010-10-20
> **klc5555 said:**
> I hesitate to mention this, but lirc is a fairly benign little package, and there is leeway in which versions of lirc will run on which Ubuntu. If you're reasonably sure that 0.8.7 will fix your issues and don't want to compile it --the lirc.org source's "make_install" tends to put things in the wrong directories from the standpoint of Debian/Ubuntu systems --then there's a good chance that the 10.10 .deb for lirc 0.8.7 (from packages.ubuntu.com) will install and run on 10.04. This has worked in other circumstances: when I needed XMP support in lirc in Ubuntu 9.04, I replaced its included lirc 0.8.4a with 0.8.6 from Ubuntu 9.10, and things were fine.

There are a couple of caveats: once the lirc version was changed, all further configuration of lirc had to be done from the ncurses comand-line menu that appears after "sudo dpkg-reconfigure lirc", rather than from, say, the Mythbuntu control center.

Also, if the later version proves unsatisfactory for whatever reason, backing the version down to the earlier one is not completely trivial on Mythbuntu the way it is on some other distros. The later version of lirc has to be uninstalled prior to the earlier one being reinstalled; and in this the .deb package manager will likely insist on also ripping out most of Mythtv, for which lirc is a dependency. These packages would need to be reinstalled along with the older lirc version.

  Yeah, that's pretty much what I figured after reading the info on the lirc website.  Looks like they moved things around so the files aren't located in the same places.  So I think I'm going to pass on trying this.  Either just use my wireless keyboard or wait for 10.10 bugs (are there any?) to be ironed out.


  IC

---

### Post by klc5555 on 2010-10-21
> **IceCap said:**
> Yeah, that's pretty much what I figured after reading the info on the lirc website.  Looks like they moved things around so the files aren't located in the same places.  So I think I'm going to pass on trying this.  Either just use my wireless keyboard or wait for 10.10 bugs (are there any?) to be ironed out.


  IC

Sorry, my current motley assembly of Xubuntu-ish  machines are all floating around among 9.04, 9.10, and 10.04. No 10.10 yet to directly address your question. 

But there are always bugs. The best you can hope for with perpetual cutting edge upgrades is that fixage >= breakage. Not always the case.

---

### Post by sudanmas on 2010-10-25
I did a fresh 10.04 install and yesterday when perusing the latest available10.04 updates.  I saw lirc 0.8.7 listed and seeing as it's been mentioned in many threads as a possible fix for getting the haupage grey remote working I decided to give it a go.

I installed the 0.8.7 update and still a no go.  IRW still produces no output with key presses on the remote. 

Also:

dmesg | grep lirc
[   16.546283] lirc_dev: IR Remote Control driver registered, major 61 
[   17.437953] lirc_i2c: chip 0x0 found @ 0x18 (Leadtek IR)
[   17.437959] lirc_dev: lirc_register_driver: sample_rate: 10

As above Leadtek is still referenced.  Any thoughts from the Ubuntu Collective on other options.

----

I'm not sure if it's worth mentioning also that lirc_d and lirc_dev are running as processes

I tried updating to 10.10 and it still didn't work unfortunately (I wound up reinstalling 10.04 after major issues with support with my video card).

Thanks muchly for any advice.

---

### Post by tubaman on 2010-10-31
I'm running a WinPVR 350 on mythbuntu 10.04.  I wasn't getting anything from the remote using "cat /dev/lirc0" or irw.  Compiling the 0.8.7 module from maverick worked for me.  On my 10.04 mythbuntu install, I grabbed the source package from here: [http://packages.ubuntu.com/maverick/all/lirc-modules-source/download](http://packages.ubuntu.com/maverick/all/lirc-modules-source/download)
...and installed it(dpkg -i).  That caused dkms to compile it.  Rebooted and the remote started working.  Note: I'm still using the lircd(0.8.6) that comes with 10.04.

---

### Post by sudanmas on 2010-11-04
Tubaman - that worked!

Thanks :-)

---

### Post by IceCap on 2010-12-27
Same here.  Worked right away (after reboot).

  Thanks

  IC

---

### Post by ahood on 2011-01-01
> **tubaman said:**
> I'm running a WinPVR 350 on mythbuntu 10.04.  I wasn't getting anything from the remote using "cat /dev/lirc0" or irw.  Compiling the 0.8.7 module from maverick worked for me.  On my 10.04 mythbuntu install, I grabbed the source package from here: [http://packages.ubuntu.com/maverick/all/lirc-modules-source/download](http://packages.ubuntu.com/maverick/all/lirc-modules-source/download)
...and installed it(dpkg -i).  That caused dkms to compile it.  Rebooted and the remote started working.  Note: I'm still using the lircd(0.8.6) that comes with 10.04.

Thanks tubaman!

This worked for me too. I am using the Hauppauge gray remote (A415-HPG) that came with a PVR 350 TV card.

I downloaded and installed the 0.8.7 lirc-modules-source gdeb file from the link above.  A warning message appeared, which I disregarded.

Note:
lirc 0.8.6 and mythbuntu-lirc-generator were not uninstalled.
I checked synaptic to ensure 0.8.6 lirc-modules-source was not installed
I did not need to reboot.

DrH

---

### Post by BicyclerBoy on 2011-01-02
There is a 3rd party ppa pre-compiled binaries for lucid...

deb [http://ppa.launchpad.net/janvitus/ppa/ubuntu](http://ppa.launchpad.net/janvitus/ppa/ubuntu) lucid main

---

