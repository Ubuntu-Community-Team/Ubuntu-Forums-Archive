---
title: "Pinnacle Movie Box Drivers"
date: 2008-08-05
forum: Multimedia Software
---

### Post by Xan63 on 2008-08-05
Hello everybody,

As I bought a Pinnacle Movie box with Pinnacle Studio (you can see it [here]("http://www.pinnaclesys.com/PublicSite/us/Products/Consumer+Products/Home+Video/Studio+Family/Studio+MovieBox+Plus+version+11.htm"), in order to capture old Pal videos on my computer, i'm having some issues about this hardware.

The exact reference: Pinnacle 510 USB Rev: 2.0

The lsusb output:
> 
Bus 006 Device 004: ID 2304:0223 Pinnacle Systems, Inc. [hex] 


- Does somebody has succeeded to use the Movie Box with Ubuntu? Because the only providen driver is a sh***y windows driver :mad:. After many searchs on google and on ubuntuforums, nobody seems having found a solution.

- Is there any driver currently being developped in order to use this hardware?

Thanks by advance for your help!

---

### Post by Xan63 on 2008-08-11
Up please :confused:

---

### Post by Stratok on 2008-08-23
same problem here

---

### Post by 73ckn797 on 2008-11-25
> **Xan63 said:**
> Up please :confused:

I am on the same adventure trying to use Pinnacle Movie Box model 710-USB in Ubuntu 8.10. I cannot even get it to work in Windows with Studio Plus v10. It completely freezes the computer. If I run across anything I will reply back.

---

### Post by Fenris14 on 2008-12-03
I use a MovieBox with windows XP. Let's be honest, it's touchy at best. I had some trouble setting it up on windows. 

This said, I'm trying to get the information to build a driver for Ubuntu. I haven't much time to work on it but I'll see if I can do something to make it work.

---

### Post by 73ckn797 on 2008-12-19
> **Fenris14 said:**
> I use a MovieBox with windows XP. Let's be honest, it's touchy at best. I had some trouble setting it up on windows. 

This said, I'm trying to get the information to build a driver for Ubuntu. I haven't much time to work on it but I'll see if I can do something to make it work.

Hope you can succeed in this.

I did get Movie Box working with Windows and quite well I must say.

---

### Post by 73ckn797 on 2009-11-29
> **Fenris14 said:**
> I use a MovieBox with windows XP. Let's be honest, it's touchy at best. I had some trouble setting it up on windows. 

This said, I'm trying to get the information to build a driver for Ubuntu. I haven't much time to work on it but I'll see if I can do something to make it work.


Any results to build a driver?

---

### Post by carlosm7 on 2010-01-24
Anybody has seen this:

[http://pinnaclembusb.sourceforge.net/](http://pinnaclembusb.sourceforge.net/)

---

### Post by 73ckn797 on 2010-01-24
> **carlosm7 said:**
> Anybody has seen this:

[http://pinnaclembusb.sourceforge.net/](http://pinnaclembusb.sourceforge.net/)

Thanks.
I will look into this. Do you use the Pinnacle device?

---

### Post by uniquegodwin on 2011-06-14
Hello everyone,
How do you use this driver?
When I execute sudo ./pmbpipe, I get this message "Cannot initialize Pinnacle MovieBox device".

Please advice.
I would appreciate any help.
Thanks

---

### Post by rocky_raccoon on 2011-11-28
Any luck with that driver? It looks a bit strange to me.

I recently got a MovieBox HD, so if anyone found out how to make it work under Linux, please help.

---

### Post by 73ckn797 on 2011-11-28
I quit looking several years ago.

---

### Post by G4dget on 2013-01-22
I believe giving up on linux compatibility for any type of Pinnacle device is probably the only solution at this point unless someone knows a lot about taking a windows driver into linux. Which at that point I believe the suggestion is to go buy a dvd recorder with a/v inputs as it will save a whole heap of time.

I have a moviebox usb-b and while ubuntu 10.04 recognizes it via lsusb i have had no success in it working. The "driver" from sourceforge seems to have no documentation of how to get it working at all and seems to be a dead project.

My only success in getting my moviebox to work "as the only driver is for 32 a 32 bit OS" was to install it on an old winxp laptop I had and find a copy of pinnacle studio 9.3 as all the newer versions were reliant on a 64 bit processor. 

I am curious though if anyone knows much about the sourceforge driver or any benefits to these types of cards running in linux. If I had the extra cash I would definitely just go with a dvd recorder option and toss this piece of hardware in the trash.

---

### Post by G4dget on 2013-12-29
NEW UPDATE

So after having my windows install completely crap out on me. I have decided to re-double my efforts to get this device running in ubuntu. I have been unsuccessful as of yet but did make a breakthrough on the sourceforge moviebox driver that has been mention throughout this thread. It is not typical source using```
./configure&&make&&sudo checkinstall
``` but appears to be C source code and firmware for a module. I have no idea where to start in building a custom module from source. 

If anyone that knows a lot about building modules is able to please msg me or respond on this thread. There are 3 <name>.o files in this along with firmware and what appears to be everything needed to just compile them into .ko files ready for the kernal.

Driver Download:
[http://sourceforge.net/projects/pinnaclembusb/](http://sourceforge.net/projects/pinnaclembusb/)

---

### Post by oldos2er on 2013-12-29
Since this thread is incredibly old I'm closing it. Please create a new thread if there are further questions.

---

