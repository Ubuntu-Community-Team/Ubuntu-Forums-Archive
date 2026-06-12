---
title: "Help installing a Ralink device: have terminal commands, but confused/not working"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by bigpimpatl on 2009-09-03
Hello all,

I am trying to install a Tenda W541U USB wifi b/g adapter to my notebook. I found that it is a ralink chipset. I believe I have found the correct drivers on the Ralink website, but the directions to install are confusing to me. If someone can point what to type exactly in the terminal, I would be very thankful. I tried many different combinations but no luck. I am running Ubuntu 9.04 with 2.6 kernel. Here are the instructions: 

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


If someone knows what type after locating the file, I would really appreciate if he or she can help me in this matter. Thanks in advance

---

