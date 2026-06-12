---
title: "rt73 wireless chip in dwl-g122"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by peterthewolf on 2006-07-04
I am trying to get this working using a download from ralink and the instructions are a follows

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


Everything  goes  fine until step 5. Now the instructions are for redhat and my problem is what the ubuntu equivalent of /etc/wireless is. I have tried setting that directory up but nothing seems to take notice.

---

