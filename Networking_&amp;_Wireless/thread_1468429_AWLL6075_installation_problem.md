---
title: "AWLL6075 installation problem"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by Megazeroxuxm on 2010-05-01
Hi, for people who are about to help me, let me warn you that this is my first ubuntu or really linux experience, so just want to let you know what you are getting into. 

ok disclaimers aside, I need help with my wireless mini usb adapter, AWLL6075, I have tried following other's successful attempts of installing this, but I have so far unable to duplicate such success. The problem is that I could not place anything that i wanted anywhere because it keep saying that I do not have permission, and so far, i have been denied from copying anything to any place. Plus even if I were to make through all of the permission issues, I still do not understand what the rest of the instructions said, maybe they were informal enough for others, but for me it was very vague. So please help me. I am using ubuntu 10.04, and just had a nice clean install. 

thank you.

---

### Post by djgperu on 2010-05-01
dude... we are on the same boat.. i was just about to post the same problem..
im not that familiar with Ubuntu yet.. so if anyone can help us I will really appreciate it..
im trying to copy a file to lib/firmware folder... but it says i do not have permissions...
how can i do it in terminal?
im a complete newbie as well but i really want my Airlink 101 Wireless-n USB dongle to work!

---

### Post by mothdragon on 2010-05-02
okay I personally have not been able to get my AWLL6075 working on 10.04 yet either, but I haven't tried too hard... 

Now, I don't know what instructions you've had, but if you get it working I'd love to know how you did it, so I can do it also... 

As far as getting past permissions is concerned, there's this cool command called sudo which gives you root access to the filesystem. This is something which should be used with some degree of caution, because some files naturally or not meant to be manipulated and doing so can break your system entirely. I don't want to scare you though. Most times, as long as you're following someone elses instructions you can be generally certain that you'll be safe to follow those instructions. Of course if the system gives you a message which makes you nervous, always feel free to come back here and ask if it's safe.

I myself am still relatively new to Ubuntu, but I can still help a bit... 

In order to use the command sudo, you need to be in the "terminal window" some would call this the command prompt, others might call it bash, or shell. In order to get to the terminal window, go to the Applications menu>Accessories>terminal. Once there you can use terminal based commands like sudo. For copying files, I've found that the most useful command is:

sudo nautilus

you will be prompted for your user password, not the root user password. This is the same password that you use when you log on in the first place.

nautilus is the file browser in ubuntu, and is normally opened when you click any of the items from the Places menu. By using sudo nautilus though, you open the file browser with root user access, and thus don't have to worry about permissions. If you ever find that you need to change permissions of a file for whatever reason ( and this should be done with caution, only change permissions of files that you know are safe, like files that you have made for instance ) then you can change permissions from this sudo nautilus window as well, by right clicking on a file and clicking Properties from the pop up menu. Many Linux die hards of course would recommend the command line alternative to this, which can be faster, and more efficient when you know what you're doing.

Hope I've helped! Good luck!

(Oh by the way, the instructions that I know of for getting AWLL6075 to work in 9.04 are different than those in 9.10, and again these are different for 10.04. That's the reason that I haven't got it working yet myself. )

---

### Post by djgperu on 2010-05-02
i noticed that the compiling and installation of drivers differ for each version of ubuntu (in this case).. i got the permissions part right away... but i cant install the drivers as i too have no knowledge of how to modify  the instructions from 9.04 to make it work in LUCID

hope someone knowledgeable can help us

---

### Post by mothdragon on 2010-05-02
The major difference from 9.04 to 9.10(Karmic) was that as of 9.10 required a firmware update in order to get this wireless adapter to work... I haven't yet figured out whether this firmware update is still required in LUCID.... When I get more info I will be sure to share it here though.

Take care!

---

### Post by mothdragon on 2010-05-03
Okay, so I got a reply back from Airlink, and they inform me that Realtek is now the company supporting this device. The AWLL6075 adapter is running the RTL8191SU chipset and a driver for linux kernel 2.6.x can be found here:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

I haven't yet tested this to see if it works or not, but will be doing so shortly. The last package of this nature that I downloaded had instructions as to how to build the module and install it. The instructions run from the command line. I hope this helps you guys, I'm going to quickly go test it now, and will let you guys know when I have more info!

---

### Post by Megazeroxuxm on 2010-05-04
holy sh*t, this must be the best community i have ever encountered with! please excuse my language but 5 comments in 2 days is ***king amazing! and everyone is so nice! please let me know if the realtek driver works, and please give me instruction on how to. I currently do not have time right now, so i will try out the drivers myself this coming weekend, but in the meantime, please post any tip or, again, instruction or precautions i should take in my attempt of installing this. Thank you. And another question, will it be better to run HD videos on ubuntu through xbmc or will it be better on win 7?

---

### Post by mothdragon on 2010-05-04
Alas the realtek driver did not work... When I try to "make" it then I get the following output:
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.32-21-generic/build M=/home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/cmd/rtl871x_cmd.o
In file included from /home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/cmd/rtl871x_cmd.c:21:
/home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h: In function ‘thread_enter’:
/home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:361: error: implicit declaration of function ‘daemonize’
/home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:362: error: implicit declaration of function ‘allow_signal’
/home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:362: error: ‘SIGTERM’ undeclared (first use in this function)
/home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:362: error: (Each undeclared identifier is reported only once
/home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:362: error: for each function it appears in.)
/home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h: In function ‘flush_signals_thread’:
/home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:369: error: implicit declaration of function ‘signal_pending’
/home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:371: error: implicit declaration of function ‘flush_signals’
In file included from include/linux/usb.h:21,
                 from /home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_intf.h:13,
                 from /home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/rtl871x_io.h:7,
                 from /home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/drv_types.h:58,
                 from /home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/cmd/rtl871x_cmd.c:22:
include/linux/sched.h: At top level:
include/linux/sched.h:2037: warning: conflicting types for ‘flush_signals’
/home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:371: note: previous implicit declaration of ‘flush_signals’ was here
include/linux/sched.h:2151: warning: conflicting types for ‘daemonize’
/home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:361: note: previous implicit declaration of ‘daemonize’ was here
include/linux/sched.h:2349: error: static declaration of ‘signal_pending’ follows non-static declaration
/home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:369: note: previous implicit declaration of ‘signal_pending’ was here
make[2]: *** [/home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/charlie/Documents/Drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [modules] Error 2



I have the firmware update that was needed in 9.10 at: 
/lib/firmware/RTL8192SE/rtl8192sfw.bin

So far I don't know whether I even need the firmware update yet...

I tried deactivating the driver in the Hardware Drivers menu before making it, but the result I get is the same either way...

.
.
.

As far as HD in Win7 vs Ubuntu, I'm not qualified to say in that regard sorry... (But of course, you should do everything in Ubuntu, because it's the best :) )

---

### Post by Megazeroxuxm on 2010-05-05
hmm, i'm sorry, but to be realistic and incredibly blunt, i have no idea what that post meant, i'm sure ubuntu pro would find it useful though :) and btw i'm using win 7 right now cause i cant use the internet on ubuntu :/ so yah... not the best for my htpc, it was quite good for my laptop tho.

---

### Post by Megazeroxuxm on 2010-05-07
hmm, no one knows then? man i was planning to use xbmc :\

---

### Post by mothdragon on 2010-05-07
At this point my best suggestion is to revert to 9.04 or 9.10 until either Ubuntu or Realtek gets on these drivers. That's my plan. And everything works in those :)

---

### Post by Megazeroxuxm on 2010-05-08
i guess so :)

---

### Post by Megazeroxuxm on 2010-05-10
> **mothdragon said:**
> At this point my best suggestion is to revert to 9.04 or 9.10 until either Ubuntu or Realtek gets on these drivers. That's my plan. And everything works in those :)

hey, it seems that you have no problems with installing it on ubuntu 9.10, can you show me step by step how to do it? thanks.

---

### Post by djgperu on 2010-05-14
for now i installed the ndiswrapper and also downloaded the WIndows XP drivers for the adapter and it is working fine...
the only thing is that once in a while when it hibernates/sleeps i have to plug it out and in to get it to connect againl..

---

### Post by jamesbond07 on 2010-05-16
I also have a AWLL6075 (Golden N Wireless Mini USB Adapter). After I searched for 2 hours for solutions on the Internet, I managed to make it work under Ubuntu 10.04 (kernel 2.6.32-21-generic).

I tried a lot of combinations with ndiswrapper, but couldn't make it work. Then I did the following:

1. I plugged in the Wireless USB Adapter and ran "dmesg". I looked at the message saying: 
"usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
  rtl819xU:request firmware fail!
"
2. I extracted the contents of the file attached ( "gunzip rtl8192sfw.bin.gz")

3. I then used "sudo mkdir /lib/firmware/`uname -r`/RTL8192SU"

4. And "sudo cp rtl8192swf.bin /lib/firmware/`uname -r`/RTL8192SU"

5. I unplugged the  Wireless USB Adapterand then plugged it in again in the same USB port.

6. I ran "dmesg" again and saw that my wireless was working! (the SSIDs of wifi networks appeared in the Network Manager)

I hope this will help others too.

---

### Post by dahubbard on 2010-05-17
James! You're my hero!  I've been trying to get the AWLL6075 working for 2-3 days now, even with that same firmware and methods but for some reason, from a clean run and following just those steps I got it to work..  The only part I had to change was to strip the " `uname -r' bit, because it just created a file named RTL8192SU and not a folder.

Thanks man!!!!

---

### Post by ilukester on 2010-05-25
@jamesbond07 I also thank you very much. This post should be saved and/or added to the tutorials. One thing that does need to be changed in your guide is:
> 4. And "sudo cp rtl8192swf.bin /lib/firmware/`uname -r`/RTL8192SU"
It should read: 
```
4. And "sudo cp rtl8192sfw.bin /lib/firmware/`uname -r`/RTL8192SU"
```
Other than that.. Thank you very much :)

Ilukester

---

### Post by darco on 2010-06-04
> **jamesbond07 said:**
> I also have a AWLL6075 (Golden N Wireless Mini USB Adapter). After I searched for 2 hours for solutions on the Internet, I managed to make it work under Ubuntu 10.04 (kernel 2.6.32-21-generic).

I tried a lot of combinations with ndiswrapper, but couldn't make it work. Then I did the following:

1. I plugged in the Wireless USB Adapter and ran "dmesg". I looked at the message saying: 
"usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
  rtl819xU:request firmware fail!
"
2. I extracted the contents of the file attached ( "gunzip rtl8192sfw.bin.gz")

3. I then used "sudo mkdir /lib/firmware/`uname -r`/RTL8192SU"

4. And "sudo cp rtl8192swf.bin /lib/firmware/`uname -r`/RTL8192SU"

5. I unplugged the  Wireless USB Adapterand then plugged it in again in the same USB port.

6. I ran "dmesg" again and saw that my wireless was working! (the SSIDs of wifi networks appeared in the Network Manager)

I hope this will help others too.

Thanks this worked for me too..except I had too upgrade to the .34 kernel and dmesg reports the device is found..
How do I disable the previous wl driver (iwl3945)?

thxs

---

### Post by taylorbarclay on 2010-07-10
Oh crap!

I got this to work with my AZiO AWU212N Wireless USB Adapter using the generic Ubuntu 10.04.  I'll update my post to link to the instructions that jamesbond posted!

---

### Post by Brejcha on 2010-07-26
> **jamesbond07 said:**
> I also have a AWLL6075 (Golden N Wireless Mini USB Adapter). After I searched for 2 hours for solutions on the Internet, I managed to make it work under Ubuntu 10.04 (kernel 2.6.32-21-generic).

I tried a lot of combinations with ndiswrapper, but couldn't make it work. Then I did the following:

1. I plugged in the Wireless USB Adapter and ran "dmesg". I looked at the message saying: 
"usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
  rtl819xU:request firmware fail!
"
2. I extracted the contents of the file attached ( "gunzip rtl8192sfw.bin.gz")

3. I then used "sudo mkdir /lib/firmware/`uname -r`/RTL8192SU"

4. And "sudo cp rtl8192swf.bin /lib/firmware/`uname -r`/RTL8192SU"

5. I unplugged the  Wireless USB Adapterand then plugged it in again in the same USB port.

6. I ran "dmesg" again and saw that my wireless was working! (the SSIDs of wifi networks appeared in the Network Manager)

I hope this will help others too.



The part that did not work for me was the sudo cp rtl8192swf.bin /lib/firmware part....

What I did to fix the problem. 

I ran sudo nautilus

Went to the newly created folder under lib/firmware/RTL8192SU  and just manually placed the rtl8192sfw.b9in file in there...

disconnected the usb card....reconnected and ran dmesh and it looked like it found everything that it needed. Now I just got to try and connect to a network

---

### Post by ichekryg on 2010-08-07
> **jamesbond07 said:**
> I also have a AWLL6075 (Golden N Wireless Mini USB Adapter)...

James! Worked like a char! Thanks

---

### Post by modelck on 2010-08-08
Using the directions below, I was able to get it working flawlessly in Kubuntu 10.04. Perfection. Thanks man. 

> **jamesbond07 said:**
> I also have a AWLL6075 (Golden N Wireless Mini USB Adapter). After I searched for 2 hours for solutions on the Internet, I managed to make it work under Ubuntu 10.04 (kernel 2.6.32-21-generic).

I tried a lot of combinations with ndiswrapper, but couldn't make it work. Then I did the following:

1. I plugged in the Wireless USB Adapter and ran "dmesg". I looked at the message saying: 
"usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
  rtl819xU:request firmware fail!
"
2. I extracted the contents of the file attached ( "gunzip rtl8192sfw.bin.gz")

3. I then used "sudo mkdir /lib/firmware/`uname -r`/RTL8192SU"

4. And "sudo cp rtl8192swf.bin /lib/firmware/`uname -r`/RTL8192SU"

5. I unplugged the  Wireless USB Adapterand then plugged it in again in the same USB port.

6. I ran "dmesg" again and saw that my wireless was working! (the SSIDs of wifi networks appeared in the Network Manager)

I hope this will help others too.

---

### Post by shinasha on 2010-08-15
this also worked for the AZiO AWU212N. very nice jamesbond07, thank you.

> **jamesbond07 said:**
> I also have a AWLL6075 (Golden N Wireless Mini USB Adapter). After I searched for 2 hours for solutions on the Internet, I managed to make it work under Ubuntu 10.04 (kernel 2.6.32-21-generic).

I tried a lot of combinations with ndiswrapper, but couldn't make it work. Then I did the following:

1. I plugged in the Wireless USB Adapter and ran "dmesg". I looked at the message saying: 
"usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
  rtl819xU:request firmware fail!
"
2. I extracted the contents of the file attached ( "gunzip rtl8192sfw.bin.gz")

3. I then used "sudo mkdir /lib/firmware/`uname -r`/RTL8192SU"

4. And "sudo cp rtl8192swf.bin /lib/firmware/`uname -r`/RTL8192SU"

5. I unplugged the  Wireless USB Adapterand then plugged it in again in the same USB port.

6. I ran "dmesg" again and saw that my wireless was working! (the SSIDs of wifi networks appeared in the Network Manager)

I hope this will help others too.

---

### Post by lawonderland on 2010-09-07
> **jamesbond07 said:**
> I also have a AWLL6075 (Golden N Wireless Mini USB Adapter). After I searched for 2 hours for solutions on the Internet, I managed to make it work under Ubuntu 10.04 (kernel 2.6.32-21-generic).

I tried a lot of combinations with ndiswrapper, but couldn't make it work. Then I did the following:

1. I plugged in the Wireless USB Adapter and ran "dmesg". I looked at the message saying: 
"usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
  rtl819xU:request firmware fail!
"
2. I extracted the contents of the file attached ( "gunzip rtl8192sfw.bin.gz")

3. I then used "sudo mkdir /lib/firmware/`uname -r`/RTL8192SU"

4. And "sudo cp rtl8192swf.bin /lib/firmware/`uname -r`/RTL8192SU"

5. I unplugged the  Wireless USB Adapterand then plugged it in again in the same USB port.

6. I ran "dmesg" again and saw that my wireless was working! (the SSIDs of wifi networks appeared in the Network Manager)

I hope this will help others too.

i downloaded the provided .gz file but do NOT download through Safari because everytime you download it, it will unpack it and you don't want to unpack the .gz file.

What i did (and this is for future reference for myself also) is:
1. download provided file

2. I plugged in the Wireless USB Adapter and ran "dmesg". I looked at the message saying: 
"usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
  rtl819xU:request firmware fail!"

3. I extracted the contents of the file attached ( "gunzip rtl8192sfw.bin.gz")

4. I then used "sudo mkdir /lib/firmware/RTL8192SU"

5. then type in "sudo nautilus"

6. it will open up another window.  Navigate to lib/firmware/RTL8192SU and place the RTL8192sfw.bin (which is the unpacked .gz file) directly into that folder.

7. disconnected the airlink101 then re connected it in the same port.  Open terminal and run "dmesg" and it should be able to find all your wireless networks.

ENJOY!

---

### Post by tlois on 2010-09-14
All right!  Now can use it without ndiswrapper.  One thing for anyone else who has been using this device with ndiswrapper and wants to get that wireless N only working....completely uninstall ndiswrapper.  Then I had to sudo nautilus into etc modprobe.d and delete that last ndiswrapper file hanging on there.  It was trying to use it and so the above (great!) instructions were not working for me.  Wireless N only now set on the router and we're good.  

Thanks!!!

---

### Post by yebot on 2010-09-20
nice. just got one of these airlink101 golden n wireless (rtl8192) doohickies working on an ubuntu dell mini 9.

thanks all.

---

### Post by tribescout on 2010-09-30
That's the same nic I've been struggling with, and now it works ! Thank you very much James !!! :)

> **yebot said:**
> nice. just got one of these airlink101 golden n wireless (rtl8192) doohickies working on an ubuntu dell mini 9.

thanks all.

---

### Post by komputerfreek on 2010-10-01
> **jamesbond07 said:**
> I also have a AWLL6075 (Golden N Wireless Mini USB Adapter). After I searched for 2 hours for solutions on the Internet, I managed to make it work under Ubuntu 10.04 (kernel 2.6.32-21-generic).

I tried a lot of combinations with ndiswrapper, but couldn't make it work. Then I did the following:

1. I plugged in the Wireless USB Adapter and ran "dmesg". I looked at the message saying: 
"usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
  rtl819xU:request firmware fail!
"
2. I extracted the contents of the file attached ( "gunzip rtl8192sfw.bin.gz")

3. I then used "sudo mkdir /lib/firmware/`uname -r`/RTL8192SU"

4. And "sudo cp rtl8192swf.bin /lib/firmware/`uname -r`/RTL8192SU"

5. I unplugged the  Wireless USB Adapterand then plugged it in again in the same USB port.

6. I ran "dmesg" again and saw that my wireless was working! (the SSIDs of wifi networks appeared in the Network Manager)

I hope this will help others too.


This seems to be working for everyone but not for me, I tried everything exactly as you said (I noticed you mistyped swf instead of sfw, I changed it and everything seem to go through, no errors) unplugged and replugged and still did not work. I am actually on the computer right now using my laptops wireless/ethernet port to hardwire this computer. I am using the latest Xubuntu so I do not know if the instructions would be different or not.

Also just want to add when I type nm-tool in Terminal I get this 

"- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xU
  State:             unavailable
  Default:           no
  HW Address:        00:21:2F:34:B3:F1

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
"

It show unavailable but shows that I have a wireless adapter... How strange.

Another Edit, Don't know which one did the trick but I did updates (about 200mb worth) and also digged around in my lib and noticed that instead of the folder being RTL8192SU it was RTL8192SE which was wierd because I checked through my commands in terminal and not once did I type SE, what is the reason for this out of curiousity? Anyway, rebooted, and wireless is working :D.

---

### Post by shah_vm on 2010-10-01
> **jamesbond07 said:**
> I also have a AWLL6075 (Golden N Wireless Mini USB Adapter). After I searched for 2 hours for solutions on the Internet, I managed to make it work under Ubuntu 10.04 (kernel 2.6.32-21-generic).

I tried a lot of combinations with ndiswrapper, but couldn't make it work. Then I did the following:

1. I plugged in the Wireless USB Adapter and ran "dmesg". I looked at the message saying: 
"usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
  rtl819xU:request firmware fail!
"
2. I extracted the contents of the file attached ( "gunzip rtl8192sfw.bin.gz")

3. I then used "sudo mkdir /lib/firmware/`uname -r`/RTL8192SU"

4. And "sudo cp rtl8192swf.bin /lib/firmware/`uname -r`/RTL8192SU"

5. I unplugged the  Wireless USB Adapterand then plugged it in again in the same USB port.

6. I ran "dmesg" again and saw that my wireless was working! (the SSIDs of wifi networks appeared in the Network Manager)

I hope this will help others too.

thank you james.

---

### Post by shah_vm on 2010-10-05
> **shah_vm said:**
> thank you james.

I am having strange issue after upgrading to ubuntu 10.10. it detects my access point (wpa/wpa2 personal) sometimes it gets connected and sometimes it just wont connect, it keeps prompting me to enter the correct key phrase.   any idea where is the problem?

---

### Post by nparasu on 2010-10-12
Worked for me. Thanks a bunch, 07!

> **jamesbond07 said:**
> I also have a AWLL6075 (Golden N Wireless Mini USB Adapter). After I searched for 2 hours for solutions on the Internet, I managed to make it work under Ubuntu 10.04 (kernel 2.6.32-21-generic).

I tried a lot of combinations with ndiswrapper, but couldn't make it work. Then I did the following:

1. I plugged in the Wireless USB Adapter and ran "dmesg". I looked at the message saying: 
"usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
  rtl819xU:request firmware fail!
"
2. I extracted the contents of the file attached ( "gunzip rtl8192sfw.bin.gz")

3. I then used "sudo mkdir /lib/firmware/`uname -r`/RTL8192SU"

4. And "sudo cp rtl8192swf.bin /lib/firmware/`uname -r`/RTL8192SU"

5. I unplugged the  Wireless USB Adapterand then plugged it in again in the same USB port.

6. I ran "dmesg" again and saw that my wireless was working! (the SSIDs of wifi networks appeared in the Network Manager)

I hope this will help others too.

---

### Post by Raghuveer Kanneganti on 2010-10-15
Thankyou very much. It worked like charm.

---

### Post by oscarlevin on 2010-11-21
:KS Worked perfectly, even for my Azio awu212n!  Thank you so much.

---

### Post by komputerfreek on 2010-11-24
I do not know how these instructions worked for people. I typed them word for word and even copy and pasted and got countless errors. So I just unzipped it and placed the bin in the folder and it worked.

---

### Post by r_avital on 2010-12-04
Why, '007, I'll sign you a chit for that!

THANKS SO MUCH.  2 minutes of work, after an entire evening of looking up info.  Connected instantly.

Megazeroxuxm, since you started the thread, you're the only one who can mark it "SOLVED" so if you don't mind, please do so at your convenience :)

Best regards to all

---

### Post by sambonedd on 2011-01-06
AWESOME!!!!!! Just omitted the ' uname -r' part and it worked like a charm! THANKS!:p

---

### Post by Nexutt on 2011-03-06
Thank you very much, 007  :cool:
I've been having trouble with this device for a while.
In Ubuntu 10.10, when not using the 'uname -r' part, it works perfectly!

---

### Post by jechill on 2011-08-23
ok like im new to ubuntu
why oh why is there so much command line crap.
I have no idea what any of it means. 
how do you change directories to get the command to run the file you want it to run. opening a terminal window and copy and paste from here to there doesnt help.
it says sudo then owners password but the keyboard is locked out of the terminal window and wont let me type the password.
is it too much to ask that a simple script be written to put the driver where its supposed to be- like in windows 
i mean my god its just a wireless card im not trying to build anything here it should be less than 30 seconds to install not a whole 2 hour bs adventure.
 
well ill be damned the thing just started working all on its own and i have no idea why.

---

### Post by praseodym on 2011-08-23
Hello jechill,

there is no ***** or xxxxxx if you type in your password while using "sudo" commands.

Edit: Just type it in and press return

---

### Post by jechill on 2011-08-24
oh well thanks for that i did not know\
guess thats why im here

---

### Post by jechill on 2011-08-24
ok i did everthing as instructed but i copied and pasted and now its working using the realtek drivers and all is well
thanks

---

### Post by jechill on 2011-08-26
ok i got the wireless adapter to work but i cant browse for a network.
the wireless networks part is greyed out.
any suggestion on how i can get this to work because when i take the computer to another location it will not connect to any other wireless router and it will not show any other wireless connections as being available
thanks in advance

---

### Post by praseodym on 2011-08-27
Checkbox any user rights in "Users&Groups" and login again. Then try:

```
gksudo nm-connection-editor
```

---

### Post by jm2 on 2012-09-03
I had an old dell latitude d600 laptop. I used these instructions and my dwa-131 worked on ubuntu 10.4
2.6.32-42-generic 
#15 download file, and follow instructions

---

### Post by ravensfan55222 on 2012-12-30
Could anyone give me some advice on how to make the adapter work on Ubuntu 12.04.1?

I just bought it a few days ago, and have tried googling things. 

I am new to Ubuntu but have used terminal a few times. 


I can't find any instructions for version 12.04.1 through google , so should would anyone recommend following the instructions on this post??

---

### Post by praseodym on 2012-12-31
Hi,

please open the terminal and show the outputs of the commands:
```

lsusb
lsmod
iwconfig
rfkill list
```
with the stick plugged in.

---

### Post by ravensfan55222 on 2012-12-31
1.
daniel@daniel-Dimension-4600i:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
daniel@daniel-Dimension-4600i:~$ 

2.
daniel@daniel-Dimension-4600i:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
udf                    84576  1 
crc_itu_t              12627  1 udf
snd_intel8x0           33455  2 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
dcdbas                 14098  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
r8712u                163880  0 
snd                    62218  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                86520  0 
soundcore              14635  1 snd
nouveau               712674  2 
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
serio_raw              13027  0 
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197641  4 nouveau,ttm,drm_kms_helper
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158479  10 rfcomm,bnep
ppdev                  12849  0 
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12893  1 nouveau
wmi                    18744  1 mxm_wmi
video                  19068  1 nouveau
parport_pc             32114  1 
mac_hid                13077  0 
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
e100                   36289  0 
floppy                 60184  0 

3.
daniel@daniel-Dimension-4600i:~$ iwconfig
lo        no wireless extensions.

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

4.
daniel@daniel-Dimension-4600i:~$ rfkill list
daniel@daniel-Dimension-4600i:~$ rfkill list
daniel@daniel-Dimension-4600i:~$ 

The stick was plugged in.. I have the cd that came with it but I cant figure out how to install the cd because it was made for windows/mac

---

### Post by praseodym on 2012-12-31
The driver **r8712u** is shown. Which channel do you want to use? It only works wich chanels 1-13.

---

### Post by ravensfan55222 on 2012-12-31
I'm sorry I don't understand what that means. But it doesn't matter to me.

Would the channel have to do with my router?

---

### Post by ivan16 on 2013-09-29
Thank you so much this post was very useful for me, after 2 days trying here I found very easy way to fix it. THANKX

---

