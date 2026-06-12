---
title: "Xserver 1.10 Final is now released"
date: 2011-02-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-02-26
And here is the announcement for xserver 1.10 final release.

[http://lists.freedesktop.org/archives/xorg-announce/2011-February/001612.html](http://lists.freedesktop.org/archives/xorg-announce/2011-February/001612.html)

---

### Post by ratcheer on 2011-02-26
> **Harry33 said:**
> And here is the announcement for xserver 1.10 final release.

[http://lists.freedesktop.org/archives/xorg-announce/2011-February/001612.html](http://lists.freedesktop.org/archives/xorg-announce/2011-February/001612.html)

That is great news. Is it compatible with the latest (.29) nVidia driver, or does a newer driver still need to be released?

Tim

---

### Post by Harry33 on 2011-02-26
> **ratcheer said:**
> That is great news. Is it compatible with the latest (.29) nVidia driver, or does a newer driver still need to be released?
Tim

Hmm, the fun goes on and on ...
No, unfortunately it isn't compatible. Not even installable on earlier systems.
Xserver 1.10 final brings a new ABI (xorg-video-abi-10).
All recent video drivers, including nvidia-current (but not fglrx) depend on xorg-video-abi-9.
Also input drivers need to be rebuilt against this final version.

---

### Post by terry_gardener on 2011-02-26
so they have released yet another abi for final 1.10, so we are back to square one.

why release one for between rc1 and rc2 and then another for final.

---

### Post by Harry33 on 2011-02-26
> **terry_gardener said:**
> so they have released yet another abi for final 1.10, so we are back to square one.

why release one for between rc1 and rc2 and then another for final.

I think it was because they had to remove the new RandR 1.4 (the resize and rotate extension) from the 1.10 server.
That was a last minute change.

---

### Post by DougieFresh4U on 2011-02-26
So is this why it has been wanting to remove these packages for a few days now?

```
      Remove the following packages:              
1)      ubuntu-desktop                            
2)      xorg                                      
3)      xserver-xorg                              
4)      xserver-xorg-input-all                    
5)      xserver-xorg-input-evdev                  
6)      xserver-xorg-input-mouse                  
7)      xserver-xorg-input-vmmouse                
8)      xserver-xorg-video-all                    
9)      xserver-xorg-video-apm                    
10)     xserver-xorg-video-ark                    
11)     xserver-xorg-video-ati                    
12)     xserver-xorg-video-chips                  
13)     xserver-xorg-video-cirrus                 
14)     xserver-xorg-video-fbdev                  
15)     xserver-xorg-video-i128                   
16)     xserver-xorg-video-intel                  
17)     xserver-xorg-video-mach64                 
18)     xserver-xorg-video-neomagic               
19)     xserver-xorg-video-nouveau                
20)     xserver-xorg-video-r128                   
21)     xserver-xorg-video-radeon                 
22)     xserver-xorg-video-rendition              
23)     xserver-xorg-video-s3                     
24)     xserver-xorg-video-s3virge                
25)     xserver-xorg-video-savage                 
26)     xserver-xorg-video-siliconmotion          
27)     xserver-xorg-video-sis                    
28)     xserver-xorg-video-sisusb                 
29)     xserver-xorg-video-tdfx                   
30)     xserver-xorg-video-trident                
31)     xserver-xorg-video-tseng                  
32)     xserver-xorg-video-vesa                   
33)     xserver-xorg-video-vmware                 
34)     xserver-xorg-video-voodoo                 

      Leave the following dependencies unresolved:
35)     gdm recommends xserver-xorg               
36)     xinit recommends xserver-xorg | xserver 
```

---

### Post by Anduu on 2011-02-27
> **DougieFresh4U said:**
> So is this why it has been wanting to remove these packages for a few days now?

```
      Remove the following packages:              
1)      ubuntu-desktop                            
2)      xorg                                      
3)      xserver-xorg                              
4)      xserver-xorg-input-all                    
5)      xserver-xorg-input-evdev                  
6)      xserver-xorg-input-mouse                  
7)      xserver-xorg-input-vmmouse                
8)      xserver-xorg-video-all                    
9)      xserver-xorg-video-apm                    
10)     xserver-xorg-video-ark                    
11)     xserver-xorg-video-ati                    
12)     xserver-xorg-video-chips                  
13)     xserver-xorg-video-cirrus                 
14)     xserver-xorg-video-fbdev                  
15)     xserver-xorg-video-i128                   
16)     xserver-xorg-video-intel                  
17)     xserver-xorg-video-mach64                 
18)     xserver-xorg-video-neomagic               
19)     xserver-xorg-video-nouveau                
20)     xserver-xorg-video-r128                   
21)     xserver-xorg-video-radeon                 
22)     xserver-xorg-video-rendition              
23)     xserver-xorg-video-s3                     
24)     xserver-xorg-video-s3virge                
25)     xserver-xorg-video-savage                 
26)     xserver-xorg-video-siliconmotion          
27)     xserver-xorg-video-sis                    
28)     xserver-xorg-video-sisusb                 
29)     xserver-xorg-video-tdfx                   
30)     xserver-xorg-video-trident                
31)     xserver-xorg-video-tseng                  
32)     xserver-xorg-video-vesa                   
33)     xserver-xorg-video-vmware                 
34)     xserver-xorg-video-voodoo                 

      Leave the following dependencies unresolved:
35)     gdm recommends xserver-xorg               
36)     xinit recommends xserver-xorg | xserver 
```

I was having the same issues...I tracked mine down to my use of the xorg-edgers ppa.I purged the ppa and ran a dist-upgrade again.Conflicts solved.

---

### Post by Harry33 on 2011-02-27
> **DougieFresh4U said:**
> So is this why it has been wanting to remove these packages for a few days now?

```
      Remove the following packages:              
1)      ubuntu-desktop                            
2)      xorg                                      
...

```

This thread is about the final release version of xserver 1.10.
That has not been built and pulled into Natty repos yet.
The version (rc2) in repos does not cause this and there currently are no problems like this.

You obviously have dependency problems in your system.
It would greatly help if you would let us know:
- what were you trying to install to get this list?
- do you have any additional PPA's in use?
- what is you graphics card model?
- what driver are you using now?

---

### Post by Harry33 on 2011-02-27
> **Anduu said:**
> I was having the same issues...I tracked mine down to my use of the xorg-edgers ppa.I purged the ppa and ran a dist-upgrade again.Conflicts solved.

This was a good idea.
Xorg-edgers PPA should not be used right now with Natty at its current state.
Please also note that the xserver version in xorg-edgers PPA is not rc2, but rc1.

---

### Post by DougieFresh4U on 2011-02-27
> **Harry33 said:**
> 

You obviously have dependency problems in your system.
It would greatly help if you would let us know:

- do you have any additional PPA's in use?
- what is you graphics card model?

Just normal daily updates
Xorg-edgers
ATI Radeon HD3200

> **Harry33 said:**
> This was a good idea.
Xorg-edgers PPA should not be used right now with Natty at its current state.

Removed said PPA and all is good again
Sorry for 'butting in on thread'
Dougie

---

### Post by petersonja on 2011-02-27
My Natty is broken because I upgraded the xserver last week. So now I can install it again and it is now works with the Nvidia properity driver?

---

### Post by Harry33 on 2011-02-27
> **petersonja said:**
> My Natty is broken because I upgraded the xserver last week. So now I can install it again and it is now works with the Nvidia properity driver?

Yes it works fine now fully upgraded/updated and also with the latest nvidia-current_270.29.

---

