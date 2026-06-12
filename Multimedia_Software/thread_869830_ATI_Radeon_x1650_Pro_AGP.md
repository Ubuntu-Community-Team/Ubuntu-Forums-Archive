---
title: "ATI Radeon x1650 Pro AGP"
date: 2008-07-25
forum: Multimedia Software
---

### Post by daedalas1981 on 2008-07-25
Radeon x1650 Pro AGP 512 MB

The keyword is AGP. Seems to always not be supported.

I've done a fresh install of Hardy from a DVD and had the automatic VESA drivers work. But I can't use compiz or normal desktop effects. If I install the proprietary driver, I get the black screen of Death. If I use eNVY after a clean installation, I get the Login Screen, but then I get the white screen of Death. If I do a fresh install and use the latest driver from AMD's Ati Driver section, I get (3) screen flashes prior to the login screen, a pop-up window that says I have to re select a Video Card and Display, which only leads to low resolution mode.

I've removed Hardy and did a fresh install of Gutsy from a DVD. I can get the proprietary driver working without any screen problems, but I still can't use compiz or normal desktop effects. I've also tried the methods above and failed.

AS I SAID earlier for you fast response people, AGP. I've heard that the PCI-e works, and there are demos on YouTube, But AGP is still out of the loop. I heard there is something you got to do to the AGPgart according to ATI. I don't know what AGPgart is, but it might help???

Sending out a S.O.S.

Please help out ATI AGP issues. Or Atleast help us get Compiz going.

---

### Post by kajillin on 2008-07-25
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) follow those instructions exactly, and your card should work. Not 100% but it should work. And font forget to purge all your old driver files.

---

### Post by daedalas1981 on 2008-07-28
Results in Black Screen. Thanks.

Does anybody know what this means in the installation instructions at ATI's website:

Note:  In order to use the fglrx internal AGP support, you have to make sure that the kernel agpgart support is not active, i.e. it is not compiled into the kernel and the kernel modules are not loaded. If the fglrx kernel module detects that the kernel agpgart support is active, it will automatically use that even if its internal AGP support is requested in order to avoid conflicts that can cause problems under some circumstances.  

Could this be the source of my problem? Thanks.

---

### Post by abanuelosh on 2008-08-27
yep, black screen over here too:

Please someone help us!!!!!!!!!!!!!


x1650 agp doesnt work properly, except with MESA drivers :(

---

### Post by tuxxy on 2008-08-27
It should run with Feisty if thats any use.

---

### Post by MusicallyInspired on 2008-12-01
Bump.

Same problem. Any solutions?

---

### Post by DHCline on 2009-05-26
To remove the drivers that give you the blank screen, do this:
 
Boot to a root prompt from recovery mode at startup. If you don't get the option automatically, then try to press escape at startup time or search around on google til you figure out how to do it, for me it's automatic so I'm not sure how to manually make the options appear. If the below steps don't work, you can try the "Try to fix X server" option from the recovery menu also.
 
Anyways for now try this...
run this:
```
 
sudo dpkg -l | less

```
 
Search for xorg-driver-fglrx in the list. If it's not there you might try looking for other ati drivers in that list. Press q to exit "less". If you found the xorg package, run this command to remove the non-working driver:
```
 
sudo apt-get remove xorg-driver-fglrx

``` 
Now you should be able to reboot your machine and at least get your old display back. 
 
I saw it recommended on several forums to use "envy" to install a good ati driver but I haven't tried that myself yet.
[http://benl.com/node/10](http://benl.com/node/10)
 
I also saw it recommended in another forum to rebuild X before reboot after removing the driver, but I didn't need to do that myself:
```
 
sudo dpkg-reconfigure xserver-xorg

``` 
 
---OR---
If that didn't work you can also try this from the root prompt, a lot of other forums said to do it this way, (I personally don't have an ati directory so this didn't work for me):
```
 
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh

``` 
 
and maybe
```
 
sudo dpkg-reconfigure xserver-xorg

```

---

