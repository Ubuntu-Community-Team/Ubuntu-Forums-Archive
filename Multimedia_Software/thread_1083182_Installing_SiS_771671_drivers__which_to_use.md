---
title: "Installing SiS 771/671 drivers / which to use"
date: 2009-02-28
forum: Multimedia Software
---

### Post by Vainone on 2009-02-28
I have an emachines laptop (unheard of i know)
EDIT: the model number is 1212
I have been working to get ubuntu to work smoothly on it for about 4 days now lol. Yes i am a ubuntu No0b.

I have fixed my wireless card with ndiswrapper, i found the solution on this site ^^

It's just i can't seem to figure out how to sort this graphics problem out.

It will only display at 800-600 

The chipset is SiS mirage or M672. On ubuntu it says im running sis 771/671

Also i found out by looking at my xorg.log that it will only start up in fail-safe

Finally i get an error on start up saying something like pnpbios failed run as option pnpbios = off... Would that affect anything and if so how would i change it ? 

If you need any documentation just tell me the command and ill be happy to reply as fast as i can.

Thanks in advance


Another Edit: Im currently running hardy heron
Final Edit: ok i've upgraded to intrepid and used the .run file for this kernel... logged out, logged back in.. nothing happened. Same as ever

---

### Post by Vainone on 2009-02-28
Bump ?

---

### Post by overdrank on 2009-02-28
Hi and I have no experience with the SIS graphics but you may look here
[SiS 771/671]("http://ubuntuforums.org/showthread.php?t=886463&highlight=SiS+771%2F671")
For some help. 
Have you tried using the xfix option when booting into recovery mode?
Recovery mode is usually the second choice from the grub when booting. Then you will be given 4 choices and the last is xfix. When xfix is complete you will be given the 4 choices again and you may choose to boot normally.

---

### Post by Vainone on 2009-03-01
Ok thankyou, i will try it and get back to you. 

:P

---

### Post by Vainone on 2009-03-01
Ok tried xfix but nothing seemed to happen. I didn't get the error box come up saying run as low graphics mode. 
Or the error message 
"error parsing config file"
"problem parsing config file"

But im still running as 800x600 and it's giving me a headache lol

I got the driver from here [http://ncc-1701a.homelinux.net/~linux-sis/](http://ncc-1701a.homelinux.net/~linux-sis/)

the 8.10 driver ran it as told and changed the config file so that driver "sis" 

When i rebooted i got that error.

For some reason it always starts as xorg.failsafe

Edit: Thanks again for your help. Sorry, i have checked that thread and to no avail =/ i can't find anything on there that helps :S

---

### Post by Vainone on 2009-03-01
Solved ! 
When i ran xfix it cleaned up my horribly distorted xorg.conf file lol

So i reinstalled the driver again.

Edit: then added in 
Section "device"

Driver "sis" 

<ctrl><alt><backspace>

And Bob's Your Uncle ^^

---

