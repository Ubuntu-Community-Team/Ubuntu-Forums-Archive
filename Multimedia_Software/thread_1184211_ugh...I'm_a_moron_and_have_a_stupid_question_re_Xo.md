---
title: "ugh...I'm a moron and have a stupid question re: Xorg version"
date: 2009-06-10
forum: Multimedia Software
---

### Post by velozoom on 2009-06-10
Trying to sort out if I can install the ATI drivers for my Radeon HD 3650 card on my Thinkpad T500 yet.  ATI has drivers for xorg versions up to 7.4  but 

#Xorg -version 

comes back as version 1.6.0???  I did a clean in stall of Jaunty, can't imagine xorg is 6 versions out of date.....so what gives with my version numbers and how do I know for sure which version I am running?  

Thanks!

Full output of #Xorg -version ```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux [hostname] 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 


```

---

### Post by ssri on 2009-06-11
> **velozoom said:**
> Trying to sort out if I can install the ATI drivers for my Radeon HD 3650 card on my Thinkpad T500 yet.  ATI has drivers for xorg versions up to 7.4  but 

#Xorg -version 

comes back as version 1.6.0???  I did a clean in stall of Jaunty, can't imagine xorg is 6 versions out of date.....so what gives with my version numbers and how do I know for sure which version I am running?  

Thanks!

Full output of #Xorg -version ```

X.Org _**X Server**_ 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux [hostname] 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 


```

You are running X.Org 7.5

[http://www.x.org/wiki/Releases/7.5](http://www.x.org/wiki/Releases/7.5)
look under xorg-server

---

### Post by MaindotC on 2009-06-11
removed

---

