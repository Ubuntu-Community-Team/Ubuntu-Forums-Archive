---
title: "Wireless cuts in and out intermittendly"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by davethewave83 on 2012-01-13
I am using the Broadcom STA driver, and everything worked fine seemingly until I enabled WPA2 encryption, then my wi-fi started to act slow, and cut in and out of data transmission. When downloading a file, it will begin download, and then pause for no reason, the progress just stops until I try to open or refresh some windows, then it sort of "kicks it" into gear again for a few seconds. 

I thought it was a DHCP issue, so I set a static IP
192.168.1.9
255.255.255.0
192.168.1.1

208.67.220.220
208.67.222.222

and it still does it. 

uninstalling and re-installing the wi-fi broadcom STA driver does not fix it. 

This is in Ubuntu 10.04 Lucid Lynx but I also experienced it in Oneiric Ocelot (11.10) 

again, this seems to have only happened after enabling WPA2 encryption.

is there a way to diagnose this, some commands to run or logs to check? Thanks!

Router:
Linksys WRT54G/GS/GL
Router interface: Tomato, Version 1.28

---

### Post by doofliet on 2012-01-14
same thing happens with me.... when i connect it stay connected for about 5 minutes then it disconnect ... the wifi seems like connected but its actually not, I have to click disconnect then connect again so its get connected !!!! ... I really hate this !!!!!!!! i have to do it every 5 minutes

---

### Post by davethewave83 on 2012-01-14
> **doofliet said:**
> same thing happens with me.... when i connect it stay connected for about 5 minutes then it disconnect ... the wifi seems like connected but its actually not, I have to click disconnect then connect again so its get connected !!!! ... I really hate this !!!!!!!! i have to do it every 5 minutes

I went into Synaptic Package manager (you may need to install this using the software centre if you are using a newer version of ubuntu) and searched for my drivers (in this case broadcom) and used completely remove on all of it, then reboot. Then I did "aptitude update", and "aptitude upgrade" from the terminal, after that, I reboot again. 

after the upgrade, I went up to System>Administration>Hardware Drivers (this may be different if you're using Unity, search Hardware Drivers in the unity search) 

and it searched for the drivers, I activated them there instead of a synaptic install. 

It has not cut in or out so far, and I've been on about a half hour. I hope this has solved it. Maybe it will help you too, let me know.

it still behaves a tiny bit laggy, during a download it seems to download in chunks, then pauses a second, then downloads another chunk, pauses a second (repeat)  but it's a lot better than it was, so far.

---

### Post by varunendra on 2012-01-15
Hi dave,

I've observed in the forums that many drivers may have problems with WPA/WPA2 mixed mode. So please check in your router if this is the case. If it is, try changing it to WPA or WPA2 only and see if the performance improves.

---

### Post by davethewave83 on 2012-01-15
> **varunendra said:**
> Hi dave,

I've observed in the forums that many drivers may have problems with WPA/WPA2 mixed mode. So please check in your router if this is the case. If it is, try changing it to WPA or WPA2 only and see if the performance improves.

Thanks for the reply, 
in my router, it has been set to WPA2 only mode the entire time, but in Ubuntu there is no WPA2 only mode, there is WPA/WPA2 personal and WPA/WPA2 enterprise. I have it set for personal. 

Is there a way to force it to WPA2 only mode within Ubuntu? 

I haven't had any issues with it since uninstalling completely and re-installing the driver, I could go ahead and mark this as solved but I was just waiting to see if doofliet had any success as well.

---

### Post by varunendra on 2012-01-15
> **davethewave83 said:**
> Is there a way to force it to WPA2 only mode within Ubuntu?
As far as I know, there is no such option in Ubuntu, but is not necessary either. That was meant to be done at the router's end only which is already done.

Some other people have had success with wicd instead of Network Manager - especially with encryption related problems. You may try to install it, then disable or uninstall NM. But do this only if the current performance is too much pain to bear with, as replacing nm with wicd is no guaranty of improved performance and wicd also has no indicator applet as nm has (it is a simpler, less complex app).

---

