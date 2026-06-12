---
title: "Ubuntu 11.04 ATI Driver Installation"
date: 2012-05-01
forum: Multimedia Software
---

### Post by kaniko on 2012-05-01
Hello,

$ uname -a
Linux MyCOmputer 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


$lspci -nn | grep VGA 

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] [1002:5b60]

I follow this thread 
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

but when I arrive here

sudo amdconfig --initial -f
amdconfig: No supported adapters detected

$ fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV370
OpenGL version string: 1.4 (2.1 Mesa 7.10.2)


Does anybody could help me?

Thanks in advance

---

### Post by The Rnegade on 2012-05-02
> **kaniko said:**
> Hello,

$ uname -a
Linux MyCOmputer 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


$lspci -nn | grep VGA 

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] [1002:5b60]

I follow this thread 
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

but when I arrive here

sudo amdconfig --initial -f
amdconfig: No supported adapters detected

$ fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV370
OpenGL version string: 1.4 (2.1 Mesa 7.10.2)


Does anybody could help me?

Thanks in advance

Okay, well did you install it from the ubuntu repo, or did you manually install it via a .run file?
if you installed from the ubuntu repos you dont need to run sudo amdconfig --initial -f

oh yeah also the terminal command you issue is

sudo aticonfig --initial

a better tutorial for this is 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

