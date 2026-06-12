---
title: "Help with driver compile (Make Error 127)"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by ryanlhjess on 2009-05-12
I am trying to compile a driver using the instructions listed below.  When i get to step 4, i get an Make: error 127.  
Any idea on what im doing wrong?

```

Build Instructions:  
====================
1> $tar -xvzf RT73_Linux_STA_Drv_x.x.x.x.tar.gz
    go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.
    
2> $cp Makefile.4  ./Makefile       # [kernel 2.4]
    or
   $cp Makefile.6  ./Makefile       # [kernel 2.6]
   
3> [kernel 2.4]
    $chmod 755 Configure
    $make config         # config build linux os version

4> $make all            # compile driver source code

5> $cp rt73.bin /etc/Wireless/RT73STA/	    # copy firmware
 
6>  $dos2unix rt73sta.dat
    $cp rt73sta.dat  /etc/Wireless/RT73STA/rt73sta.dat       
    # !!!check if it is a binary file before loading !!!  
    
7> $load                
    #[kernel 2.4]
    #    $/sbin/insmod rt73.o
    #    $/sbin/ifconfig rausb0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt73.ko
    #    $/sbin/ifconfig rausb0 inet YOUR_IP up

```

---

### Post by Crafty Kisses on 2009-05-12
I guess the most logical question right about now is do you have "build-essential" installed?

---

### Post by cariboo on 2009-05-12
Is there a reason why the RT73 module included with the kernel doesn't work?

---

