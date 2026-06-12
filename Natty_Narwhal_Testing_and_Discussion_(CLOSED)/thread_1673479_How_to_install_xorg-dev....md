---
title: "How to install xorg-dev...?"
date: 2011-01-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zika on 2011-01-22
I need xorg-dev in order to compile FluxBox...
But, I can not install it due to unmet dependencies...
Any ideas...?

```
~$ sudo aptitude install xorg-dev
The following NEW packages will be installed:
  libdmx-dev{a} libdmx1{a} libexpat1-dev{a} libfontconfig1-dev{a} 
  libfontenc-dev{a} libfreetype6-dev{a} libfs-dev{a} libice-dev{a} 
  libpciaccess-dev{ab} libpixman-1-dev{a} libpthread-stubs0{a} 
  libpthread-stubs0-dev{a} libsm-dev{a} libx11-dev{ab} libxau-dev{a} 
  libxaw7-dev{a} libxcb1-dev{a} libxcomposite-dev{a} libxcursor-dev{a} 
  libxdamage-dev{ab} libxdmcp-dev{a} libxext-dev{ab} libxfixes-dev{ab} 
  libxfont-dev{a} libxft-dev{a} libxi-dev{a} libxinerama-dev{a} 
  libxkbfile-dev{a} libxmu-dev{a} libxmu-headers{a} libxmuu-dev{a} 
  libxpm-dev{a} libxrandr-dev{a} libxrender-dev{ab} libxres-dev{a} 
  libxss-dev{a} libxt-dev{a} libxtst-dev{a} libxv-dev{a} libxvmc-dev{a} 
  libxxf86dga-dev{a} libxxf86vm-dev{a} x11proto-bigreqs-dev{a} 
  x11proto-composite-dev{a} x11proto-core-dev{a} x11proto-damage-dev{a} 
  x11proto-dmx-dev{a} x11proto-dri2-dev{a} x11proto-fixes-dev{a} 
  x11proto-fonts-dev{a} x11proto-gl-dev{a} x11proto-input-dev{a} 
  x11proto-kb-dev{a} x11proto-randr-dev{a} x11proto-record-dev{a} 
  x11proto-render-dev{a} x11proto-resource-dev{a} x11proto-scrnsaver-dev{a} 
  x11proto-video-dev{a} x11proto-xcmisc-dev{a} x11proto-xext-dev{a} 
  x11proto-xf86bigfont-dev{a} x11proto-xf86dga-dev{a} 
  x11proto-xf86dri-dev{a} x11proto-xf86vidmode-dev{a} 
  x11proto-xinerama-dev{a} xorg-dev xserver-xorg-dev{a} xtrans-dev{a} 
  zlib1g-dev{a} 
0 packages upgraded, 70 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,395 kB of archives. After unpacking 32.4 MB will be used.
The following packages have unmet dependencies:
  libxdamage-dev: Depends: libxdamage1 (= 1:1.1.3-1) but 1:1.1.3+git20100705.8abc1c8e-0ubuntu0sarvatt is installed.
  libxfixes-dev: Depends: libxfixes3 (= 1:4.0.5-1) but 1:4.0.5+git20100705.01e803ae-0ubuntu0sarvatt is installed.
  libxext-dev: Depends: libxext6 (= 2:1.1.2-1) but 2:1.1.2+git20100705.23643bd1-0ubuntu0sarvatt is installed.
  libxrender-dev: Depends: libxrender1 (= 1:0.9.6-1) but 1:0.9.6+git20100705.d3d20437-0ubuntu0sarvatt is installed.
  libx11-dev: Depends: libx11-6 (= 2:1.3.3-3ubuntu2) but 2:1.3.4+git20100720.554da76e-0ubuntu0sarvatt3 is installed.
  libpciaccess-dev: Depends: libpciaccess0 (= 0.12.0-1ubuntu1) but 0.12.0+git20100720.fa3f1c1e-0ubuntu0sarvatt is installed.
The following actions will resolve these dependencies:

      Keep the following packages at their current version:
1)      libdmx-dev [Not Installed]                         
2)      libpciaccess-dev [Not Installed]                   
3)      libx11-dev [Not Installed]                         
4)      libxaw7-dev [Not Installed]                        
5)      libxcomposite-dev [Not Installed]                  
6)      libxcursor-dev [Not Installed]                     
7)      libxdamage-dev [Not Installed]                     
8)      libxext-dev [Not Installed]                        
9)      libxfixes-dev [Not Installed]                      
10)     libxfont-dev [Not Installed]                       
11)     libxft-dev [Not Installed]                         
12)     libxi-dev [Not Installed]                          
13)     libxinerama-dev [Not Installed]                    
14)     libxkbfile-dev [Not Installed]                     
15)     libxmu-dev [Not Installed]                         
16)     libxmu-headers [Not Installed]                     
17)     libxmuu-dev [Not Installed]                        
18)     libxpm-dev [Not Installed]                         
19)     libxrandr-dev [Not Installed]                      
20)     libxrender-dev [Not Installed]                     
21)     libxres-dev [Not Installed]                        
22)     libxss-dev [Not Installed]                         
23)     libxt-dev [Not Installed]                          
24)     libxtst-dev [Not Installed]                        
25)     libxv-dev [Not Installed]                          
26)     libxvmc-dev [Not Installed]                        
27)     libxxf86dga-dev [Not Installed]                    
28)     libxxf86vm-dev [Not Installed]                     
29)     xorg-dev [Not Installed]                           
30)     xserver-xorg-dev [Not Installed]                   



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
``````
~$ sudo apt-get install xorg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xorg-dev : Depends: libdmx-dev but it is not going to be installed
            Depends: libx11-dev but it is not going to be installed
            Depends: libxaw7-dev but it is not going to be installed
            Depends: libxcomposite-dev but it is not going to be installed
            Depends: libxcursor-dev but it is not going to be installed
            Depends: libxdamage-dev but it is not going to be installed
            Depends: libxext-dev but it is not going to be installed
            Depends: libxfixes-dev but it is not going to be installed
            Depends: libxfont-dev but it is not going to be installed
            Depends: libxft-dev but it is not going to be installed
            Depends: libxi-dev but it is not going to be installed
            Depends: libxinerama-dev but it is not going to be installed
            Depends: libxkbfile-dev but it is not going to be installed
            Depends: libxmu-dev but it is not going to be installed
            Depends: libxmuu-dev but it is not going to be installed
            Depends: libxpm-dev but it is not going to be installed
            Depends: libxrandr-dev but it is not going to be installed
            Depends: libxrender-dev but it is not going to be installed
            Depends: libxres-dev but it is not going to be installed
            Depends: libxss-dev but it is not going to be installed
            Depends: libxt-dev but it is not going to be installed
            Depends: libxtst-dev but it is not going to be installed
            Depends: libxv-dev but it is not going to be installed
            Depends: libxvmc-dev but it is not going to be installed
            Depends: libxxf86dga-dev but it is not going to be installed
            Depends: libxxf86vm-dev but it is not going to be installed
            Depends: xserver-xorg-dev but it is not going to be installed
E: Broken packages
```...
(xorg-edgers is applied, fully up-to-date...)

---

### Post by mc4man on 2011-01-22
never mind for the moment

re-edit

Were you previously using the maverick packages from that ppa and have now switched to natty?

---

### Post by Harry33 on 2011-01-22
> **mc4man said:**
> never mind for the moment
re-edit
Were you previously using the maverick packages from that ppa and have now switched to natty?

Yes it seems this is Natty with xorg-edgers PPA (Maverick packages)
For example the package libdamage1_1.1.3-1 is in Natty repo.
But the xorg-edgers-maverick version is installed.

It is better to downgrade those packages (with unmet dependencies) one by one with synaptic (using Package - Force Version) to Natty version.
And after all that install the xorg-dev (of Natty).

---

### Post by Starks on 2011-01-22
> **Harry33 said:**
> Yes it seems this is Natty with xorg-edgers PPA (Maverick packages)
For example the package libdamage1_1.1.3-1 is in Natty repo.
But the xorg-edgers-maverick version is installed.

It is better to downgrade those packages (with unmet dependencies) one by one with synaptic (using Package - Force Version) to Natty version.
And after all that install the xorg-dev (of Natty).

Just switch to xorg-edgers natty and then ppa-purge if you need to.

---

### Post by mc4man on 2011-01-22
> Just switch to xorg-edgers natty ...

I believe it's quite likely he is currently using that ppa set to natty but had previously used it @maverick and had updated those packages.
Now there are no corresponding devel's (=), avail from the ppa @ natty nor the default natty repo's

---

### Post by zika on 2011-01-22
> **mc4man said:**
> I believe it's quite likely he is currently using that ppa set to natty but had previously used it @maverick and had updated those packages.
Now there are no corresponding devel's (=), avail from the ppa @ natty nor the default natty repo's
I'm on natty(ppa) from the first day it opened for natty. Before that I was up-to-date on maverick(ppa) on xorg-edgers. I'll try with ppa-purge...

After ppa-purge xorg-edgers:```
~$ sudo aptitude install xorg-dev
The following NEW packages will be installed:
  libdmx-dev{a} libdmx1{a} libexpat1-dev{a} libfontconfig1-dev{a} libfontenc-dev{a} libfreetype6-dev{a} libfs-dev{a} libice-dev{a} libpciaccess-dev{ab} libpixman-1-dev{a} libpthread-stubs0{a} libpthread-stubs0-dev{a} libsm-dev{a} libx11-dev{ab} libxau-dev{a} libxaw7-dev{a} 
  libxcb1-dev{a} libxcomposite-dev{a} libxcursor-dev{a} libxdamage-dev{ab} libxdmcp-dev{a} libxext-dev{ab} libxfixes-dev{ab} libxfont-dev{a} libxft-dev{a} libxi-dev{a} libxinerama-dev{a} libxkbfile-dev{a} libxmu-dev{a} libxmu-headers{a} libxmuu-dev{a} libxpm-dev{a} libxrandr-dev{a} 
  libxrender-dev{ab} libxres-dev{a} libxss-dev{a} libxt-dev{a} libxtst-dev{a} libxv-dev{a} libxvmc-dev{a} libxxf86dga-dev{a} libxxf86vm-dev{a} x11proto-bigreqs-dev{a} x11proto-composite-dev{a} x11proto-core-dev{a} x11proto-damage-dev{a} x11proto-dmx-dev{a} x11proto-dri2-dev{a} 
  x11proto-fixes-dev{a} x11proto-fonts-dev{a} x11proto-gl-dev{a} x11proto-input-dev{a} x11proto-kb-dev{a} x11proto-randr-dev{a} x11proto-record-dev{a} x11proto-render-dev{a} x11proto-resource-dev{a} x11proto-scrnsaver-dev{a} x11proto-video-dev{a} x11proto-xcmisc-dev{a} 
  x11proto-xext-dev{a} x11proto-xf86bigfont-dev{a} x11proto-xf86dga-dev{a} x11proto-xf86dri-dev{a} x11proto-xf86vidmode-dev{a} x11proto-xinerama-dev{a} xorg-dev xserver-xorg-dev{a} xtrans-dev{a} zlib1g-dev{a} 
0 packages upgraded, 70 newly installed, 0 to remove and 4 not upgraded.
Need to get 9,288 kB of archives. After unpacking 32.8 MB will be used.
The following packages have unmet dependencies:
  libxdamage-dev: Depends: libxdamage1 (= 1:1.1.3-1) but 1:1.1.3+git20100705.8abc1c8e-0ubuntu0sarvatt is installed.
  libxfixes-dev: Depends: libxfixes3 (= 1:4.0.5-1) but 1:4.0.5+git20100705.01e803ae-0ubuntu0sarvatt is installed.
  libxext-dev: Depends: libxext6 (= 2:1.1.2-1) but 2:1.1.2+git20100705.23643bd1-0ubuntu0sarvatt is installed.
  libxrender-dev: Depends: libxrender1 (= 1:0.9.6-1) but 1:0.9.6+git20100705.d3d20437-0ubuntu0sarvatt is installed.
  libx11-dev: Depends: libx11-6 (= 2:1.3.3-3ubuntu2) but 2:1.3.4+git20100720.554da76e-0ubuntu0sarvatt3 is installed.
  libpciaccess-dev: Depends: libpciaccess0 (= 0.12.0-1ubuntu1) but 0.12.0+git20100720.fa3f1c1e-0ubuntu0sarvatt is installed.
The following actions will resolve these dependencies:

      Keep the following packages at their current version:
1)      libdmx-dev [Not Installed]                         
2)      libpciaccess-dev [Not Installed]                   
3)      libx11-dev [Not Installed]                         
4)      libxaw7-dev [Not Installed]                        
5)      libxcomposite-dev [Not Installed]                  
6)      libxcursor-dev [Not Installed]                     
7)      libxdamage-dev [Not Installed]                     
8)      libxext-dev [Not Installed]                        
9)      libxfixes-dev [Not Installed]                      
10)     libxfont-dev [Not Installed]                       
11)     libxft-dev [Not Installed]                         
12)     libxi-dev [Not Installed]                          
13)     libxinerama-dev [Not Installed]                    
14)     libxkbfile-dev [Not Installed]                     
15)     libxmu-dev [Not Installed]                         
16)     libxmu-headers [Not Installed]                     
17)     libxmuu-dev [Not Installed]                        
18)     libxpm-dev [Not Installed]                         
19)     libxrandr-dev [Not Installed]                      
20)     libxrender-dev [Not Installed]                     
21)     libxres-dev [Not Installed]                        
22)     libxss-dev [Not Installed]                         
23)     libxt-dev [Not Installed]                          
24)     libxtst-dev [Not Installed]                        
25)     libxv-dev [Not Installed]                          
26)     libxvmc-dev [Not Installed]                        
27)     libxxf86dga-dev [Not Installed]                    
28)     libxxf86vm-dev [Not Installed]                     
29)     xorg-dev [Not Installed]                           
30)     xserver-xorg-dev [Not Installed]
``````

~$ sudo apt-get install xorg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xorg-dev : Depends: libdmx-dev but it is not going to be installed
            Depends: libx11-dev but it is not going to be installed
            Depends: libxaw7-dev but it is not going to be installed
            Depends: libxcomposite-dev but it is not going to be installed
            Depends: libxcursor-dev but it is not going to be installed
            Depends: libxdamage-dev but it is not going to be installed
            Depends: libxext-dev but it is not going to be installed
            Depends: libxfixes-dev but it is not going to be installed
            Depends: libxfont-dev but it is not going to be installed
            Depends: libxft-dev but it is not going to be installed
            Depends: libxi-dev but it is not going to be installed
            Depends: libxinerama-dev but it is not going to be installed
            Depends: libxkbfile-dev but it is not going to be installed
            Depends: libxmu-dev but it is not going to be installed
            Depends: libxmuu-dev but it is not going to be installed
            Depends: libxpm-dev but it is not going to be installed
            Depends: libxrandr-dev but it is not going to be installed
            Depends: libxrender-dev but it is not going to be installed
            Depends: libxres-dev but it is not going to be installed
            Depends: libxss-dev but it is not going to be installed
            Depends: libxt-dev but it is not going to be installed
            Depends: libxtst-dev but it is not going to be installed
            Depends: libxv-dev but it is not going to be installed
            Depends: libxvmc-dev but it is not going to be installed
            Depends: libxxf86dga-dev but it is not going to be installed
            Depends: libxxf86vm-dev but it is not going to be installed
            Depends: xserver-xorg-dev but it is not going to be installed
E: Broken packages
```

I'll try with update/upgrade, now on xorg-edgers, but, I think that these packages are not, yet available for natty...

After re-update/upgrade natty(xorg-edgers)```
$ sudo aptitude install xorg-dev
The following NEW packages will be installed:
  libdmx-dev{a} libdmx1{a} libexpat1-dev{a} libfontconfig1-dev{a} libfontenc-dev{a} libfreetype6-dev{a} libfs-dev{a} libice-dev{a} libpciaccess-dev{ab} libpixman-1-dev{a} libpthread-stubs0{a} libpthread-stubs0-dev{a} libsm-dev{a} libx11-dev{ab} libxau-dev{a} libxaw7-dev{a} 
  libxcb1-dev{a} libxcomposite-dev{a} libxcursor-dev{a} libxdamage-dev{ab} libxdmcp-dev{a} libxext-dev{ab} libxfixes-dev{ab} libxfont-dev{a} libxft-dev{a} libxi-dev{a} libxinerama-dev{a} libxkbfile-dev{a} libxmu-dev{a} libxmu-headers{a} libxmuu-dev{a} libxpm-dev{a} libxrandr-dev{a} 
  libxrender-dev{ab} libxres-dev{a} libxss-dev{a} libxt-dev{a} libxtst-dev{a} libxv-dev{a} libxvmc-dev{a} libxxf86dga-dev{a} libxxf86vm-dev{a} x11proto-bigreqs-dev{a} x11proto-composite-dev{a} x11proto-core-dev{a} x11proto-damage-dev{a} x11proto-dmx-dev{a} x11proto-dri2-dev{a} 
  x11proto-fixes-dev{a} x11proto-fonts-dev{a} x11proto-gl-dev{a} x11proto-input-dev{a} x11proto-kb-dev{a} x11proto-randr-dev{a} x11proto-record-dev{a} x11proto-render-dev{a} x11proto-resource-dev{a} x11proto-scrnsaver-dev{a} x11proto-video-dev{a} x11proto-xcmisc-dev{a} 
  x11proto-xext-dev{a} x11proto-xf86bigfont-dev{a} x11proto-xf86dga-dev{a} x11proto-xf86dri-dev{a} x11proto-xf86vidmode-dev{a} x11proto-xinerama-dev{a} xorg-dev xserver-xorg-dev{a} xtrans-dev{a} zlib1g-dev{a} 
0 packages upgraded, 70 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,395 kB of archives. After unpacking 32.4 MB will be used.
The following packages have unmet dependencies:
  libxdamage-dev: Depends: libxdamage1 (= 1:1.1.3-1) but 1:1.1.3+git20100705.8abc1c8e-0ubuntu0sarvatt is installed.
  libxfixes-dev: Depends: libxfixes3 (= 1:4.0.5-1) but 1:4.0.5+git20100705.01e803ae-0ubuntu0sarvatt is installed.
  libxext-dev: Depends: libxext6 (= 2:1.1.2-1) but 2:1.1.2+git20100705.23643bd1-0ubuntu0sarvatt is installed.
  libxrender-dev: Depends: libxrender1 (= 1:0.9.6-1) but 1:0.9.6+git20100705.d3d20437-0ubuntu0sarvatt is installed.
  libx11-dev: Depends: libx11-6 (= 2:1.3.3-3ubuntu2) but 2:1.3.4+git20100720.554da76e-0ubuntu0sarvatt3 is installed.
  libpciaccess-dev: Depends: libpciaccess0 (= 0.12.0-1ubuntu1) but 0.12.0+git20100720.fa3f1c1e-0ubuntu0sarvatt is installed.
The following actions will resolve these dependencies:

      Keep the following packages at their current version:
1)      libdmx-dev [Not Installed]                         
2)      libpciaccess-dev [Not Installed]                   
3)      libx11-dev [Not Installed]                         
4)      libxaw7-dev [Not Installed]                        
5)      libxcomposite-dev [Not Installed]                  
6)      libxcursor-dev [Not Installed]                     
7)      libxdamage-dev [Not Installed]                     
8)      libxext-dev [Not Installed]                        
9)      libxfixes-dev [Not Installed]                      
10)     libxfont-dev [Not Installed]                       
11)     libxft-dev [Not Installed]                         
12)     libxi-dev [Not Installed]                          
13)     libxinerama-dev [Not Installed]                    
14)     libxkbfile-dev [Not Installed]                     
15)     libxmu-dev [Not Installed]                         
16)     libxmu-headers [Not Installed]                     
17)     libxmuu-dev [Not Installed]                        
18)     libxpm-dev [Not Installed]                         
19)     libxrandr-dev [Not Installed]                      
20)     libxrender-dev [Not Installed]                     
21)     libxres-dev [Not Installed]                        
22)     libxss-dev [Not Installed]                         
23)     libxt-dev [Not Installed]                          
24)     libxtst-dev [Not Installed]                        
25)     libxv-dev [Not Installed]                          
26)     libxvmc-dev [Not Installed]                        
27)     libxxf86dga-dev [Not Installed]                    
28)     libxxf86vm-dev [Not Installed]                     
29)     xorg-dev [Not Installed]                           
30)     xserver-xorg-dev [Not Installed]                   



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
$ sudo apt-get install xorg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xorg-dev : Depends: libdmx-dev but it is not going to be installed
            Depends: libx11-dev but it is not going to be installed
            Depends: libxaw7-dev but it is not going to be installed
            Depends: libxcomposite-dev but it is not going to be installed
            Depends: libxcursor-dev but it is not going to be installed
            Depends: libxdamage-dev but it is not going to be installed
            Depends: libxext-dev but it is not going to be installed
            Depends: libxfixes-dev but it is not going to be installed
            Depends: libxfont-dev but it is not going to be installed
            Depends: libxft-dev but it is not going to be installed
            Depends: libxi-dev but it is not going to be installed
            Depends: libxinerama-dev but it is not going to be installed
            Depends: libxkbfile-dev but it is not going to be installed
            Depends: libxmu-dev but it is not going to be installed
            Depends: libxmuu-dev but it is not going to be installed
            Depends: libxpm-dev but it is not going to be installed
            Depends: libxrandr-dev but it is not going to be installed
            Depends: libxrender-dev but it is not going to be installed
            Depends: libxres-dev but it is not going to be installed
            Depends: libxss-dev but it is not going to be installed
            Depends: libxt-dev but it is not going to be installed
            Depends: libxtst-dev but it is not going to be installed
            Depends: libxv-dev but it is not going to be installed
            Depends: libxvmc-dev but it is not going to be installed
            Depends: libxxf86dga-dev but it is not going to be installed
            Depends: libxxf86vm-dev but it is not going to be installed
            Depends: xserver-xorg-dev but it is not going to be installed
E: Broken packages
```

No luck...
Now I see why FB ppa failed in producing FB for Natty and, now, it is closed...

At least I did a good housekeeping cleaning, and now I can wait for xorg-dev and gstreamer-plugins-bad to be ready to be (re)installed...

---

### Post by mc4man on 2011-01-22
> and now I can wait for ..
That's probably the safest/easiest option (assuming they will be built for natty in the ppa) or as harry mentioned you could 'downgrade' those packages to the current natty packages

Ot - just curious - are you intending  to try to run your current install, which you've had for quite a while it seems, all the way thru thru the natty  dev?

---

### Post by zika on 2011-01-22
> **mc4man said:**
> That's probably the safest/easiest option (assuming they will be built for natty in the ppa) or as harry mentioned you could 'downgrade' those packages to the current natty packages

Ot - just curious - are you intending  to try to run your current install, which you've had for quite a while it seems, all the way thru thru the natty  dev?
I do not understand Your question...
This is not a clean-natty-install. It is an upgrade from clean-install made once in Maverick-Testing... Very early in Natty-testing, almost the same day it was possible...
I hope this, kind of, answers Your question...

---

### Post by mc4man on 2011-01-22
> I hope this, kind of, answers Your question... 
Completely..

---

### Post by zika on 2011-01-23
> **mc4man said:**
> Completely..I'm glad...
I understand that You think my effort is fruitless...

---

### Post by zika on 2011-01-23
If I enable both maverick@xorg-edgers and natty@xorg-edgers I get:```
$ sudo aptitude install xorg-dev
The following NEW packages will be installed:
  libdmx-dev{a} libdmx1{a} libexpat1-dev{a} libfontconfig1-dev{a} libfontenc-dev{a} libfreetype6-dev{a} libfs-dev{a} libice-dev{a} libpciaccess-dev{a} libpixman-1-dev{a} libpthread-stubs0{a} libpthread-stubs0-dev{a} libsm-dev{a} libx11-dev{a} libxau-dev{a} libxaw7-dev{a} libxcb1-dev{a} 
  libxcomposite-dev{a} libxcursor-dev{a} libxdamage-dev{a} libxdmcp-dev{a} libxext-dev{a} libxfixes-dev{a} libxfont-dev{a} libxft-dev{a} libxi-dev{a} libxinerama-dev{a} libxkbfile-dev{a} libxmu-dev{a} libxmu-headers{a} libxmuu-dev{a} libxpm-dev{a} libxrandr-dev{a} libxrender-dev{a} 
  libxres-dev{a} libxss-dev{a} libxt-dev{a} libxtst-dev{a} libxv-dev{a} libxvmc-dev{a} libxxf86dga-dev{a} libxxf86vm-dev{a} x11proto-bigreqs-dev{a} x11proto-composite-dev{a} x11proto-core-dev{a} x11proto-damage-dev{a} x11proto-dmx-dev{a} x11proto-dri2-dev{a} x11proto-fixes-dev{a} 
  x11proto-fonts-dev{a} x11proto-gl-dev{a} x11proto-input-dev{a} x11proto-kb-dev{a} x11proto-randr-dev{a} x11proto-record-dev{a} x11proto-render-dev{a} x11proto-resource-dev{a} x11proto-scrnsaver-dev{a} x11proto-video-dev{a} x11proto-xcmisc-dev{a} x11proto-xext-dev{a} 
  x11proto-xf86bigfont-dev{a} x11proto-xf86dga-dev{a} x11proto-xf86dri-dev{a} x11proto-xf86vidmode-dev{a} x11proto-xinerama-dev{a} xorg-dev xserver-xorg-dev{a} xtrans-dev{a} zlib1g-dev{a} 
The following packages will be upgraded:
  libx11-6 
1 packages upgraded, 70 newly installed, 0 to remove and 8 not upgraded.
Need to get 8,787 kB of archives. After unpacking 30.8 MB will be used.
Do you want to continue? [Y/n/?] n
```
That looks to me as a hazardous road...
Any thoughts?
Really, I don need that FB so much, but it became interesting and educational...

---

### Post by Harry33 on 2011-01-23
> **zika said:**
> If I enable both maverick@xorg-edgers and natty@xorg-edgers I get:```
$ sudo aptitude install xorg-dev
The following NEW packages will be installed:
  libdmx-dev{a} libdmx1{a} libexpat1-dev{a} libfontconfig1-dev{a} libfontenc-dev{a} libfreetype6-dev{a} libfs-dev{a} libice-dev{a} libpciaccess-dev{a} libpixman-1-dev{a} libpthread-stubs0{a} libpthread-stubs0-dev{a} libsm-dev{a} libx11-dev{a} libxau-dev{a} libxaw7-dev{a} libxcb1-dev{a} 
  libxcomposite-dev{a} libxcursor-dev{a} libxdamage-dev{a} libxdmcp-dev{a} libxext-dev{a} libxfixes-dev{a} libxfont-dev{a} libxft-dev{a} libxi-dev{a} libxinerama-dev{a} libxkbfile-dev{a} libxmu-dev{a} libxmu-headers{a} libxmuu-dev{a} libxpm-dev{a} libxrandr-dev{a} libxrender-dev{a} 
  libxres-dev{a} libxss-dev{a} libxt-dev{a} libxtst-dev{a} libxv-dev{a} libxvmc-dev{a} libxxf86dga-dev{a} libxxf86vm-dev{a} x11proto-bigreqs-dev{a} x11proto-composite-dev{a} x11proto-core-dev{a} x11proto-damage-dev{a} x11proto-dmx-dev{a} x11proto-dri2-dev{a} x11proto-fixes-dev{a} 
  x11proto-fonts-dev{a} x11proto-gl-dev{a} x11proto-input-dev{a} x11proto-kb-dev{a} x11proto-randr-dev{a} x11proto-record-dev{a} x11proto-render-dev{a} x11proto-resource-dev{a} x11proto-scrnsaver-dev{a} x11proto-video-dev{a} x11proto-xcmisc-dev{a} x11proto-xext-dev{a} 
  x11proto-xf86bigfont-dev{a} x11proto-xf86dga-dev{a} x11proto-xf86dri-dev{a} x11proto-xf86vidmode-dev{a} x11proto-xinerama-dev{a} xorg-dev xserver-xorg-dev{a} xtrans-dev{a} zlib1g-dev{a} 
The following packages will be upgraded:
  libx11-6 
1 packages upgraded, 70 newly installed, 0 to remove and 8 not upgraded.
Need to get 8,787 kB of archives. After unpacking 30.8 MB will be used.
Do you want to continue? [Y/n/?] n
```
That looks to me as a hazardous road...
Any thoughts?
Really, I don need that FB so much, but it became interesting and educational...

You want to experience something new, right (Ubuntu natty-maverick).
You have questions, I think.
Will it boot? Will x start?
Anyway, I suppose you know how to chroot.

BTW. If you use synaptic, you would know what version of xorg-dev you are actually installing there. Is it maverick's or natty's?

I would not want to install packages xorg, xserver-xorg and x11-common from edgers-natty (version 7.5+6ubuntu8~raof2).
This is because those have inconsistent dependencies:
They dependend on virtual packages (xserver-xorg-video-9 and xserver-xorg-input-12), that no input nor video driver provide in the same PPA:
- edgers input drivers provide xserver-xorg-input-11
- edgers video drivers provide xserver-xorg-video-8.

---

### Post by zika on 2011-01-23
> **Harry33 said:**
> You want to experience something new, right (Ubuntu natty-maverick).
You have questions, I think.
Will it boot? Will x start?
Anyway, I suppose you know how to chroot.

BTW. If you use synaptic, you would know what version of xorg-dev you are actually installing there. Is it maverick's or natty's?

I would not want to install packages xorg, xserver-xorg and x11-common from edgers-natty (version 7.5+6ubuntu8~raof2).
This is because those have inconsistent dependencies:
They dependend on virtual packages (xserver-xorg-video-9 and xserver-xorg-input-12), that no input nor video driver provide in the same PPA:
- edgers input drivers provide xserver-xorg-input-11
- edgers video drivers provide xserver-xorg-video-8.

I know how to chroot, at least I did, last time I needed that... :)
No, I do not want Mavetty... :)

---

### Post by mc4man on 2011-01-23
> I understand that You think my effort is fruitless...

Not at all - simply wanted to know how much you had 'invested' in this install (ie. whether a testing install that could be experimented on (abandoned if need be),  or one you wished to keep going in good working condition.

I would be inclined to return it to just natty packages which may happen if you wait it out or could be done thru synaptic or thru dpkg
(my preference would be thru dpkg


Edit:
Though I do think that from a testing perspective one should do a fresh install from time to time. I think possibly  it's more likely to represent the current state than an older install updated

---

### Post by Harry33 on 2011-01-23
> **mc4man said:**
> 
...
Edit:
Though I do think that from a testing perspective one should do a fresh install from time to time. I think possibly  it's more likely to represent the current state than an older install updated

Me, I am not going to fresh install any more. I do testing all the time, because I use Ubuntu as a true rolling release (except that it is a stable release version only until next tool chain is uploaded :D).

I do not use meta packages, because I dislike dependency hell and because I demand freedom of choice. I hate Micro-microsoft, I do not need any Bill tell me what installation and setup I need.
If I remember right, a fresh ubuntu installation contains over 1,100 packages.
After having removed those I do not need, I now have about 800 left.
So it is a too big job to reinstall anyway.

One example of the dependency hell:
Fresh ubuntu install contains like 25 different video drivers (xserver-xorg-video-*).
This is because a meta package xserver-xorg-video-all is installed automatically.
Me, like so many other people here, have only one graphic card installed, and I know what it is (NVidia). So I need 0 xserver-xorg-video-drivers. All I need is nvidia-current.

But that is just me.

---

### Post by Harry33 on 2011-01-23
> **zika said:**
> I need xorg-dev in order to compile FluxBox...
But, I can not install it due to unmet dependencies...
Any ideas...?
...
[code]~$ sudo aptitude install xorg-dev
The following packages have unmet dependencies:
  libxdamage-dev: Depends: libxdamage1 (= 1:1.1.3-1) but 1:1.1.3+git20100705.8abc1c8e-0ubuntu0sarvatt is installed.
  libxfixes-dev: Depends: libxfixes3 (= 1:4.0.5-1) but 1:4.0.5+git20100705.01e803ae-0ubuntu0sarvatt is installed.
  libxext-dev: Depends: libxext6 (= 2:1.1.2-1) but 2:1.1.2+git20100705.23643bd1-0ubuntu0sarvatt is installed.
  libxrender-dev: Depends: libxrender1 (= 1:0.9.6-1) but 1:0.9.6+git20100705.d3d20437-0ubuntu0sarvatt is installed.
  libx11-dev: Depends: libx11-6 (= 2:1.3.3-3ubuntu2) but 2:1.3.4+git20100720.554da76e-0ubuntu0sarvatt3 is installed.
  libpciaccess-dev: Depends: libpciaccess0 (= 0.12.0-1ubuntu1) but 0.12.0+git20100720.fa3f1c1e-0ubuntu0sarvatt is installed.
...


To handle all those 6 unmet dependencies, all you have to do is to open synaptic, and from the menu bar:
- choose Package - Force Version
- choose (natty)
Do this one by one to all those 6 packages and you do not have unmet dependencies any more.
Then see what happens when you try to install xorg-dev, (with synaptic).;)

---

### Post by zika on 2011-01-23
> **mc4man said:**
> Not at all - simply wanted to know how much you had 'invested' in this install (ie. whether a testing install that could be experimented on (abandoned if need be),  or one you wished to keep going in good working condition.

I would be inclined to return it to just natty packages which may happen if you wait it out or could be done thru synaptic or thru dpkg
(my preference would be thru dpkg


Edit:
Though I do think that from a testing perspective one should do a fresh install from time to time. I think possibly  it's more likely to represent the current state than an older install updatedI'll investigate it further. For the time being I'll live a bit on ppa-purge-d system (xorg-edgers turned off)...
At least my gstreamer-plugins-bad is back on duty (for some internet radios (old jazz) I like)... I'm not sure what happened but I do not complain...

---

### Post by zika on 2011-01-23
> **Harry33 said:**
> To handle all those 6 unmet dependencies, all you have to do is to open synaptic, and from the menu bar:
- choose Package - Force Version
- choose (natty)
Do this one by one to all those 6 packages and you do not have unmet dependencies any more.
Then see what happens when you try to install xorg-dev, (with synaptic).;)That is on my to-do list even before I posted my question...
I, kind of, preferred a systematic solution, not my brute intrusion, but...
(I know how to do that, I've done it more than couple of times in the past...)

---

### Post by zika on 2011-01-23
I've found enough time and everything went well.
Except that FluxBox git has a bug with FcMatrixRotate that I'll have to investigate more, once I get another spare window of time...
Thank You all...

---

### Post by mc4man on 2011-01-23
> At least my gstreamer-plugins-bad is back
There was a prev. update to the pre-release of the new gstreamer - the bad plugin needed a little extra work.

Wouldn't be surprised to see an overall update to the new release shortly.

( because you do use ppa(s), you may find the "Origin" tab in synaptic useful or at least informative. - shows packages installed and avail. on an individual source basis

---

### Post by zika on 2011-01-23
> **mc4man said:**
> There was a prev. update to the pre-release of the new gstreamer - the bad plugin needed a little extra work.

Wouldn't be surprised to see an overall update to the new release shortly.

( because you do use ppa(s), you may find the "Origin" tab in synaptic useful or at least informative. - shows packages installed and avail. on an individual source basis
Been there...
Thank You...
As I mentioned earlier, I prefer holistic approach...

---

### Post by zika on 2011-01-23
After reboot I've lost keyboard in X. It works in tty but not in X. It seems that something went wrong...
Backup in progress...
Mouse is working...
Still fighting not to resort to reinstall...
Writing from laptop... :)

It works on LiveCd  (daily natty .iso, today)...

---

### Post by zika on 2011-01-24
First thing, this morning, reinstall (without format)...
First reinstall in quite some time...
Back in the saddle without much of the atavisms from Maverick...
Thank You all...
Pursue to compile FluxBox will continue once I regain time lost this morning...

---

### Post by Harry33 on 2011-01-24
> **Harry33 said:**
> 
...
I would not want to install packages xorg, xserver-xorg and x11-common from edgers-natty (version 7.5+6ubuntu8~raof2).
This is because those have inconsistent dependencies:
They dependend on virtual packages (xserver-xorg-video-9 and xserver-xorg-input-12), that no input nor video driver provide in the same PPA:
- edgers input drivers provide xserver-xorg-input-11
- edgers video drivers provide xserver-xorg-video-8.

Now that I am writing this, xorg-edgers are uploading new git snaphots of all video drivers with correct provided virtual packages (xserver-xorg-video-9).
Next, the input drivers should be updated.

---

### Post by zika on 2011-01-24
> **Harry33 said:**
> Now that I am writing this, xorg-edgers are uploading new git snaphots of all video drivers with correct provided virtual packages (xserver-xorg-video-9).
Next, the input drivers should be updated.For the first time in years, I'm without xorg-edgers in sources.list.d... :)
Two reasons: gathering time and patience to do that, and, heads_up because of the problem with xorg-edgers this morning...
Thank You...

P.S. It seems that this heads_up is for NVidia... As far as I was able to conclude...
(I'm on ATI...)

---

### Post by Sarvatt on 2011-01-24
To fix this, disable xorg-edgers natty, add xorg-edgers maverick to your sources again, sudo apt-get update and then sudo ppa-purge xorg-edgers.

---

### Post by zika on 2011-01-25
> **Sarvatt said:**
> To fix this, disable xorg-edgers natty, add xorg-edgers maverick to your sources again, sudo apt-get update and then sudo ppa-purge xorg-edgers.To fix what? Problem with xorg-dev? Or problem of missing keyboard? I do not have it anymore since I've done re-install, due to non-circumventable loss of keyboard in X, after I ppa-purge-d xorg-edgers and manually downgraded 6 packages in order to make xorg-dev installable... Now, as I wrote in a prevous message, I don have xorg-edgers ppa (yet) enabled, because I'm waiting for problems to resolve, (even though I gather problems are with NVidia and I have ATI)...
If I did get You right, I thought of doing just what You've suggested, as You could read from the thread, above, but, kind of, was afraid I would get "Mavatty" at some point and I was wrong, obviously, not attempting that.
I'm not sorry, now I have clean Natty and I'm marching ahead...
Thank You...
(I'm writing this not to complain or pule, but in order to give a complete report, so that someone else could benefit from this experience...)

(Not to forget: I reckon that You are Robert Hooker a.k.a. Sarvatt from xorg-edgers... If You are, I wish to salute You and thank You for all the good stuff I've used in time behind... I take my hat off to You...)

---

