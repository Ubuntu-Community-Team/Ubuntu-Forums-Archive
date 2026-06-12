---
title: "Modem drivers driving me crazy"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by brain frog on 2009-09-13
hello

I am totally new to linux so i might need many aspects explained in detail.

I recently decided to try linux after a bit of deciding i have chosen to use ubuntu. i installed it with no problems but after a small amount of research it turns out that you need to be online to do almost anything.

That is my problem i have a sagem F@st800 USB Modem, i found the linux driver on there site but this is where the trouble began, i have attempted quite a bit to install it but i just dont have the understanding to install it but to have that i need more time using linux but that wont happen if i never get online.

What i have done is, put the Fast8x0_3-0-6.tgz file on linux extracted it to home folder, attempted to install the patch that came in the file but had a problem saying "line 2 patch command not found", after this i just attempted to install the main files i started with what the main guides say but it appears i need kernel, however i could not find a guide that worked i found a reference to using a packet manager to find it off the cd but googling this to find out how was fruitless.

I did all this in terminal 

If it helps i have saved the result of me using ./configure in terminal to see if it helps to explain my problem.

meee@meee-brain-frog:~$ cd eagle-usb/eagle-usb-src
meee@meee-brain-frog:~/eagle-usb/eagle-usb-src$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking for main in -lc... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for uid_t in sys/types.h... yes
checking whether gcc needs -traditional... no
checking return type of signal handlers... void
checking for strftime... yes
checking for gettimeofday... yes
checking for select... yes
checking for socket... yes
checking for strcspn... yes
checking for strdup... yes
checking for strerror... yes
checking for strspn... yes
checking for strtol... yes
checking for ifconfig... yes
checking for route... yes
checking for pidof... yes
checking for dhclient... dhclient
checking for pppd... yes
checking for pppoe... no
checking for doc/man/eagleconfig.8... yes
checking for xsltproc... yes
   *** docbook stylesheets are missing, keeping prebuild version ***
checking for kernel version...  not found 
checking for hotplug... 0
checking for ifup... 1
checking for adictrl... no
checking for eaglectrl... no
checking for showstat... no
checking for eaglestat... no
checking for startadsl... no
checking for stopadsl... no
configure: creating ./config.status
config.status: creating Makefile.common

========================================================================
distribution detected                Debian

dhcp support                    dhclient

pppd support                    yes
  pppoa support                    yes
  pppoe support                    no  (runtime detection)

install eagleconnect (tcl/tk frontend)        yes

generate documentation                no
========================================================================

error: kernel-sources cannot be found!

meee@meee-brain-frog:~/eagle-usb/eagle-usb-src$ 



How can i get the kernel i need as i cant get it by simply going online as i am doing this in order to get online?

sorry about any bad spelling or grammar i am not feeling very well today

any help will be appreciated as this is my last ditch attempt to get this working

---

### Post by brain frog on 2009-09-13
oh  why has it turned into a solid block of text?   It doesn't seem to detect it when return is used how strange, great another problem.

I think i have worked it out it was NOSCRIPT.

---

### Post by Irvine_himself on 2009-09-13
I don't know if I can really help you or not? I have my own problems with this subject at the moment, (that is how I found your post.)

First off:  in terminal "uname -v : print the kernel version" without the quotes will see if the kernel version is visible?

Have you tried contacting their customer support, since they are good enough to offer a Linux driver,  they might be very helpful?

Anyway, I did some research into your modem and the answer is, it seems to be an absolute bitch to get working! (Sorry, but that seems to be a universal opinion.)

The sites below all offer possible solutions?

1/  [http://ubuntuforums.org/showthread.php?t=34278](http://ubuntuforums.org/showthread.php?t=34278)
2/  [http://www.bandstand.org.uk/~adamgray/fast800.html](http://www.bandstand.org.uk/~adamgray/fast800.html)
3/  [http://atm.eagle-usb.org/wakka.php?wiki=PagePrincipaleEn](http://atm.eagle-usb.org/wakka.php?wiki=PagePrincipaleEn)

The last site, (3/) would involve ditching the manufacturers driver and installing the Eagle GNU version, I would only consider that as the very last option after everything else has failed.

---

### Post by brain frog on 2009-09-15
> **Irvine_himself said:**
> I don't know if I can really help you or not? I have my own problems with this subject at the moment, (that is how I found your post.)

First off:  in terminal "uname -v : print the kernel version" without the quotes will see if the kernel version is visible?

Have you tried contacting their customer support, since they are good enough to offer a Linux driver,  they might be very helpful?

Anyway, I did some research into your modem and the answer is, it seems to be an absolute bitch to get working! (Sorry, but that seems to be a universal opinion.)

The sites below all offer possible solutions?

1/  [http://ubuntuforums.org/showthread.php?t=34278](http://ubuntuforums.org/showthread.php?t=34278)
2/  [http://www.bandstand.org.uk/~adamgray/fast800.html]("http://www.bandstand.org.uk/%7Eadamgray/fast800.html")
3/  [http://atm.eagle-usb.org/wakka.php?wiki=PagePrincipaleEn](http://atm.eagle-usb.org/wakka.php?wiki=PagePrincipaleEn)

The last site, (3/) would involve ditching the manufacturers driver and installing the Eagle GNU version, I would only consider that as the very last option after everything else has failed.

Thanks for the response

This is what i got from the kernel command i know and the one you stated

meee@meee-brain-frog:~$ uname -r
2.6.28-11-generic
meee@meee-brain-frog:~$ uname -v
#42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009
meee@meee-brain-frog:~$ 

I am using a fresh install of 9.04 i think

Because of my inexperience i dont know how to get this obscure version of the kernel at least thats what i think it is.

I have spent many hours looking online and found many pages of people asking this and not much use i have attempted everything they say no luck so far.

I have already read the top 2 links i attempted the 3rd one the result and oddly the filenames were the same.

The pc itself is made of old pc parts and i downloaded ubuntu so no tech support there, and tiscali my isp is notoriouse for its poor customer service, i remember when i had a connection problem and i am not wasting my time talking to someone in india who doesnt have a clue what they are doing and barely speaks english again and again and again. ticali need to hire competent staff.

i have attempted many kernels no luck yet maybe i am doing it wrong i followed this exactly but got the same kernel error

[http://atm.eagle-usb.org/wakka.php?wiki=UeagleAtmDoc](http://atm.eagle-usb.org/wakka.php?wiki=UeagleAtmDoc)

any advice would be good and it would be fantastic if someone could tell me exactly how to get the kernels and get them onto my offline system

---

### Post by Irvine_himself on 2009-09-15
I don't think it is a problem with kernels or anything to do with building your own machine. It seems to be a problem with installing the driver for that particular modem. (I have not seen anything complementary said about it)

If you don't mind a suggestion, jumpimg around switching kernels willy nilly is a sure recipe for disaster. Since you haven't really done any thing with the installation yet. I would start off by doing a fresh install, that way if someone more knowledgeable than me decides to help, you are starting from base zero. (Surprises! are never very nice)

What I do know, is that Jaunty seems to have problems with modems, there are lots of patches and fixes for the most common wireless cards in this forum. Me myself, I did my research and installed a PCI p2p modem with drivers, everything looked great, right up until I connected it to the server.I now have a friendly systems engineer tearing his hair out with the beast. Although he is a Linux Evangelist, at the present time he is not saying nice things about Jaunty!

Anyway, it might be an idea rather than installing Jaunty, install Ubuntu 8.04 LTS (Hardy Heron). that is the long term support version. (It is older and had more time to get the kinks ironed out.)

If the Linux driver still does not install, and you have the modems original installation disk, then use ndswrapper to install a wrapped version of the windows driver.

Hopefully by then, a real expert will take over and you will get better quality advice.

---

### Post by Irvine_himself on 2009-09-16
I know you can only get intermittent access to the internet so I am just going to post this before you reply.

I have done some more research and I think I know what the problem is. When you compile a package, it is a multi-step process converting a human readable text source file into a machine readable executable. During this process the compiler  gathers OS and hardware specific information including the location of standard dll's etc. 

I am certain that what it is referring to when it say's it cant find the "kernel headers", (and the patch problem,) is that the human readable source code has a some minor syntax error in its configuration files. I am not an expert in this, but from previous experience with Fedora and talking with other Linux users, it is a regrettably all too common situation when trying to compile packages.

[There is in fact a Forum section here]("http://ubuntuforums.org/forumdisplay.php?f=44"), for this where expert coders would be able to help you out. So, eirther a new post giving full details, including:  Ubuntu version, type of Modem and where you got the source package. Alternatively, ask ther moderator to move this to the packaging and compiling Forum?

Also, when you try to compile/install, packages copy and paste the terminal output into a text file and use USB stick to carry it to a internet connection where you can post it here.

Finally one other link you might find useful is [DialupModemHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/DialupModemHowto")

---

### Post by Whiffle on 2009-09-16
You need the kernel sources, and probably some other stuff for building.

That includes the build-essential package, and its dependencies, and then you need the linux-headers-2.6.28-11 package and its dependencies.

If you can get it connected to the internet or you've got your Ubuntu CD (I think these are on the CD or alternate cd), then:
```

sudo apt-get install build-essential linux-headers-2.6.28-11

```

will get that for you.  Otherwise you'll have to get it all from packages.ubuntu.com one at a time (not recommended...): 
[http://packages.ubuntu.com/jaunty/linux-headers-2.6.28-11](http://packages.ubuntu.com/jaunty/linux-headers-2.6.28-11)
[http://packages.ubuntu.com/jaunty/build-essential](http://packages.ubuntu.com/jaunty/build-essential)

AFter that, you should be able to compile your modem driver.

And while I'm at it, here's a howto on setting up your modem:
[https://help.ubuntu.com/community/UsbAdslModem/EagleUsb](https://help.ubuntu.com/community/UsbAdslModem/EagleUsb)

---

### Post by brain frog on 2009-09-18
I have put quite a bit more time into getting this to work still no luck.

From what i have been able to work out the 2 best drivers are the eagle one that you have to compile. [https://help.ubuntu.com/community/UsbAdslModem/EagleUsb](https://help.ubuntu.com/community/UsbAdslModem/EagleUsb)

Or the ueagle that apears that you simply copy the files into the system set it up and it should work without any checks to see if you have its dependancys. [https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm)

I installed 8.04 and i ended up with identical results to 9.04.

I used the links that were sent and found this guide [https://help.ubuntu.com/community/UsbAdslModem/EagleUsb](https://help.ubuntu.com/community/UsbAdslModem/EagleUsb) , and i attempted to update the drivers however using[FONT=monospace] , [/FONT]sudo apt-get install build-essential linux-headers-$(uname -r) was ineffective it unable to find the linux headers, i used synaptic to try to do it manually, the build essentials allowed the patch to work but i still got the same kernel headers as i could not get the kernel headers it apears i will have to find them online.

It apears that the ueagle is a more modern driver it is good i know this now as previously i thought it was a dependency of the earlier eagle-usb drivers, apparently they conflict.

I used this guide [https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm)  , fustratingly i compleated the instalation however it failed to work.

The problem may be one part that seemed unclear at the point where i must insert[FONT=monospace] [/FONT]"<your username>"  "*"  "<your password>"  "*" into chap and pap secrets, each file contains text aready but i was unsure if i had to put it into a percific part of the text in the file or not but i interprited it as emptying the file and leaving only "<your username>"  "*"  "<your password>"  "*" is this correct?

The modem did have one steady light then the 2nd light is dead then blinks and becomes steady which means that the drivers were installed and the modem is detected.

When i type pon ueagle-atm (the command to tell it to connect) all i get is "plugin pppoatm.so loaded." and find my web brouser cant find a web address.

I will test this again tomorow on a clean install of 9.04 rather than 8.04 to see if it works.

Thankyou for all previous replies and help it has been very helpful.

Any further guidance would be great.

I have been told that i should simply abandon the modem as its more trouble than its worth.

---

### Post by Whiffle on 2009-09-18
Does this modem happen to have an ethernet port?  It might be easier to hook it up that way.

---

### Post by brain frog on 2009-09-19
Sadly no, all it has is a connector that goes from the splitter at the phone connection to the modem and a printer cable going from it to the pc, oh and 2 lights, apart from that nothing.

---

### Post by brain frog on 2009-09-21
Just posting to say thanks and that i have gotten it working.

I have learned a lot about linux in my recent attempts to get it working, i wonder what the next hurdle will be.

Links and tips that helped me a lot were, for anyone who has this problem.


[https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm) at this point ueagle-atm-1.1 is the latest driver and should be used instead of eagle-usb

[http://faq.eagle-usb.org/wakka.php?wiki=ListConfigADSL](http://faq.eagle-usb.org/wakka.php?wiki=ListConfigADSL) in the uk i used 0.38 as the decimal code which is put in <VP>.<VC>  in the guide

[https://bugs.launchpad.net/ubuntu/+bug/278828](https://bugs.launchpad.net/ubuntu/+bug/278828)  for the dip command , i had this problem when attempting to dial you must then restart after using it

also at this point "<your username>"  "*"  "<your password>"  "*"[/code] Dont forget both "*"

i simply removed all existing content in the file and just put that, dont forget to put both "*" and keep the " and dont forget to remove the < > *feels a bit embarrassed*

on ubuntu 9.04 i only needed to add the kernel essentials i did this by searching for it in synaptic and inserting the dvd

also i think i had problems with causing conflicts between my attempts to get it working in previous attempts

also i got it working by installing them in the /lib/firmware/ueagle-atm location as the other mentioned did not work

Good luck to anyone else who is new to linux and isnt quite sure what they are doing.

---

### Post by Whiffle on 2009-09-21
Thanks for the update, it'll help people in the future with the same issue.  It would also be good to mark the thread as Solved.

---

