---
title: "linux nightmare"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by sniperdude on 2010-09-12
Hi I am totally new to Linux haven't a clue what am doing TBH

but I have a dell 510m laptop I want to install ubuntu couldn't get any of the later versions past the logo for install (have tried fixes posted never worked) 


in the end i went to 9.10 installed fine added the recommend wireless driver from the hardware update 

connect to wifi and the connection is uber slow 1mb 

I have seen posts to disable ipv6 but that dont help any advice would be welcome as I have spent 2 days reading trying to get a working ubuntu install on this laptop and nothing has worked and i am about to give up  


wired connection works fine btw

---

### Post by bryanfblareunion on 2010-09-12
Are you installing via live CD or live USB? My suggestion would be to try the other one if your computer has the option to boot from either. If you need a good USB disc creator LinuxLive is great. I've used it before and love it. Hope this helps. :)

---

### Post by DrMelon on 2010-09-12
> **bryanfblareunion said:**
> Are you installing via live CD or live USB? My suggestion would be to try the other one if your computer has the option to boot from either. If you need a good USB disc creator LinuxLive is great. I've used it before and love it. Hope this helps. :)

Somehow I doubt this will improve the speed of his wireless adapter.

By the connection being "uber slow 1mb" do you mean that it's going at 1MB/s, or that it should be at 1MB but it's going slowly?

---

### Post by wojox on 2010-09-12
What driver did you say you installed ?

---

### Post by sniperdude on 2010-09-12
> **DrMelon said:**
> Somehow I doubt this will improve the speed of his wireless adapter.

By the connection being "uber slow 1mb" do you mean that it's going at 1MB/s, or that it should be at 1MB but it's going slowly?

it says in the information part of network connections my connection speed is 
1Mb/s it should be 54 as i have a with a windows based connection in the same room



> **wojox said:**
> What driver did you say you installed ?

its the boardcom b43legacy driver that the system recommended i use when i use the hardware driver scan

---

### Post by PRC09 on 2010-09-12
You may try just a reboot of the router and the laptop and check again.....

---

### Post by DjSesso on 2010-09-12
> **sniperdude said:**
> it says in the information part of network connections my connection speed is 
1Mb/s it should be 54 as i have a with a windows based connection in the same room





its the boardcom b43legacy driver that the system recommended i use when i use the hardware driver scan

ew I hate that driver. see if it works with the broadcom-wl driver.

#apt-get install broadcom-wl

---

### Post by MaindotC on 2010-09-12
> **DjSesso said:**
> ew I hate that driver. see if it works with the broadcom-wl driver.

#apt-get install broadcom-wl

How did you install this because there is no package called broadcom-wl!

---

### Post by sniperdude on 2010-09-12
> **DjSesso said:**
> ew I hate that driver. see if it works with the broadcom-wl driver.

#apt-get install broadcom-wl

total noob here no good telling me to do something without telling me how




EDIT 

infact no forget it am going back to XP save all the messing about, all well and good that ubuntu is free but don't matter how free somthing is if it dont work 
or its that complicated that you would need to goggle for 2 days to install a wireless card


thanks to the people that replied but linux beat me haha

---

