---
title: "Wired ethernet connection keeps dropping in 8.10"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by jstorta on 2008-12-08
I recently 'upgraded' from 8.04 to 8.10. 

Everything worked fine under 8.04.  Immediately after upgrading, I noticed that all of my network config was gone and the new Network Manager would not allow me to save configuration changes.  After several trips to the Ubuntu Forums, I finally found a work-around that allowed me to save the configuration.  I cannot recall exactly what the work-around was, but I think I had to delete the contents of a configuration file.

Unfortunately, I now have a problem where my wired network connection will drop every few minutes. It comes back in a matter of seconds, but it is very annoying because streaming video such as You Tube will stop downloading and I have to completely refresh the page to get it to start again.

I looked in the /var/log/messages file and I see the following messages repeated over and over.

Dec  8 19:11:12 gimli kernel: [11150.304353] eth2: Media Link Off
Dec  8 19:11:22 gimli kernel: [11159.988013] eth2: Transmit timeout, status 00000004 00000000 
Dec  8 19:11:22 gimli kernel: [11160.304678] eth2: Media Link On 100mbps full-duplex 
Dec  8 19:18:03 gimli kernel: [11561.304349] eth2: Media Link Off
Dec  8 19:18:13 gimli kernel: [11570.988014] eth2: Transmit timeout, status 00000004 00000000 
Dec  8 19:18:13 gimli kernel: [11571.304682] eth2: Media Link On 100mbps full-duplex 
Dec  8 19:31:09 gimli kernel: [12347.305429] eth2: Media Link Off
Dec  8 19:31:19 gimli kernel: [12356.988017] eth2: Transmit timeout, status 00000004 00000040 
Dec  8 19:31:19 gimli kernel: [12357.304704] eth2: Media Link On 100mbps full-duplex 

I keep hoping that one set of updates will include something that will fix the problem, but the problem persists.  I tried searching the forums for a solution, but everything I find refers to wireless connections.

I am very close to going back to 8.04, but I am hoping someone can point me towards a solution.

I will provide whatever information is needed to help.  Just let me know.

Thanks.

---

### Post by tvtech on 2008-12-08
you might need to try a different module it sounds like the 8.10 module is no good, also check out launchpad see if there are any bugs related to your network interface card and 8.10  be more specific and reference you kernal version in your searches.  

also check out [www.google.com/linux](www.google.com/linux)   it's a linux specific search engine, reference your network card model/ chipset in your searches.

---

