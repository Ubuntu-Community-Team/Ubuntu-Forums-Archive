---
title: "Is there a way to get breezy to detect/install a different NIC after installation?"
date: 2006-01-25
forum: Networking &amp; Wireless
---

### Post by jbus on 2006-01-25
Ok guys I have a odd problem here...

I did a fresh install of kubuntu breezy on my sisters computer... She had been using Mepis and all the hardware worked fine but she wanted to try kubuntu instead.

She brought her PC to my place so I could take my time with getting it up and running. At home she has it hooked up to a cable modem via a switch and about 40-50 feet of cat 5 UTP that is hard wired in her home. At my place, during the installation, I had it hooked up with a 4 foot crossover cable to my switch/router. Her 3com Etherlink XL PCI refused to pull an IP from my router with it hooked up like this. So I just replaced it with an extra kingston NIC I had lying around. This worked great, it got an IP and the install process completed. I got her system all set up the way she wanted and everything worked great.

Here's the problem... Now that the PC is back at her place the kingston NIC refuses to pull an IP from her router... The wiring is fine, the router is fine, the switch is fine and it's NOT a MAC address filtering/security issue either. Unfortunately I now remember having similar trouble with that kingston NIC before, but I never got rid of it for some reason :oops:  

So now I have a good working customized kubuntu install that I don't want to trash, but I need to install another NIC in it instead (probably the 3com Etherlink XL PCI). I'm not sure how to do this... I tried pulling the kingston out and replacing it with the 3com hoping that it when it booted it would recognize the 3com but it didn't and the eth0 interface will no longer come up, so I really need some help.

Is there a simple way to get kubuntu to detect the new 3com NIC? Or do I have to manually install a 3com driver?

Any suggestions would be appreciated.

---

### Post by tokyovigilante on 2006-01-25
You should be able to get it to recognise the 3com card by finding what kernel module it needs to load, then sudo modprobe <name of module>.

adding it to /etc/modules will allow it to come up each boot.

---

### Post by jbus on 2006-01-26
[QUOTE=tokyovigilante]You should be able to get it to recognise the 3com card by finding what kernel module it needs to load, then sudo modprobe <name of module>.

adding it to /etc/modules will allow it to come up each boot.[/QUOTE]

Thank you tokyovigilante...

I tested the 3c509 module with modprobe to make sure it worked, then I added it to /etc/modules and used Network Settings to configure it. Everything works great now :D

---

### Post by tokyovigilante on 2006-01-26
That's great, glad to help.

---

