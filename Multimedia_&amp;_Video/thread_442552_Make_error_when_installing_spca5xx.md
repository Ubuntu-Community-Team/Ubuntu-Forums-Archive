---
title: "Make error when installing spca5xx"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by luckyaba on 2007-05-13
I am trying to get my webcam working and when i try and install the spca5xx module it is failing and i don't know why.

This is the error.

/usr/src/modules/spca5xx/drivers/usb/spca5xx.c:39:26: error:               
 &#9474; linux/config.h: No such file or directory                                  
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c: In function               
 &#9474; &#8216;spca50x_init_isoc&#8217;:                                                       
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:1681: warning: assignment   
 &#9474; from incompatible pointer type                                             
 &#9474; make[4]: *** [/usr/src/modules/spca5xx/drivers/usb/spca5xx.o] Error 1     
 &#9474; make[3]: *** [_module_/usr/src/modules/spca5xx] Error 2                   
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'     
 &#9474; make[2]: *** [default] Error 2                                             
 &#9474; make[2]: Leaving directory `/usr/src/modules/spca5xx'                      
 &#9474; make[1]: *** [binary-modules] Error 2                                      
 &#9474; make[1]: Leaving directory `/usr/src/modules/spca5xx'                
 &#9474; make: *** [kdist_build] Error 2                                            
 &#9474; ^Y

 touch /usr/src/linux/include/linux/config.h

[http://www.linuxquestions.org/questions/showthread.php?t=506363](http://www.linuxquestions.org/questions/showthread.php?t=506363)

---

### Post by josesanders on 2007-05-14
> /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:39:26: error:
&#9474; linux/config.h: No such file or directory 

The problem is here.  It can't find the file 'linux/config.h'.  I found this thread:
[http://www.debianhelp.org/node/6037](http://www.debianhelp.org/node/6037)

According to them, the file name has changed from 'config.h' to 'autoconfig.h'.  The easiest way to fix the problem is to create a symbolic link:

$ ln -s /path/to/real/file /path/to/non-existant/file

In your case, change to the 'linux' directory and run the command:

$ ln -s autoconfig.h config.h

---

### Post by luckyaba on 2007-05-14
nice! that makes more sense that way.

---

