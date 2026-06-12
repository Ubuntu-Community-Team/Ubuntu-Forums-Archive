---
title: "Mobile broadband problems"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by Moinul Abrar on 2009-12-09
Sub:     
[LEFT]**[COLOR=Red]Failed:[/COLOR]** [COLOR=Red]**Network Manager Ubuntu 9.10 Karmic for mobile broadband**[/COLOR][/LEFT]
  [FONT=&quot]
[/FONT]
[FONT=&quot]Hello Friends,[/FONT]
[FONT=&quot]I have a **Nokia 3110c** mobile set. It support EDGE-Mobile Broadband Internet  via  bluetooth, infra-red & USB. [/FONT]
[FONT=&quot][/FONT] In my office & in residence desktop computers, I used it for internet browsing in Windows-7 Ultimate. I used this same Nokia 3110c set in both office & residence. 
-----------------------------------------------------------

**Office Desktop PC Configuration:**

Processor:        Intel Pentium-4, 2.4GHz, 
Motherboard: Intel D865PERL,
RAM:                 512MB,
32-bit operating system

-----------------------------------------------------------
**Residence Desktop PC Configuration:**
Processor:        Intel Core2 Due, 1.8GHz,
Motherboard: Intel DG965GF,
RAM:                 4GB DDR2,
32-bit operating system.
i686 architecture. 

----------------------------------------------------------
**In Office:**

In my office desktop computer, unfortunately, I can still not connect to the internet in Ubuntu 9.10 Karmic via Network Manager using Nokia 3110c mobile set. I cannot understand why it is not working.


In Windows-7 mode, I can connect to internet within a second using the same Nokia 3110c mobile set via bluetooth. In bluetooth setup window, Nokia 3110c set is indicated as** [COLOR=Red]00:1b:33:cc:9a:d6[/COLOR]. **Computer discovered it as a Network Device.


In Ubuntu 9.10 Karmic mode, my office computer can easily discovered my Nokia 3110c mobile set via bluetooth-USB adapter, then I can easily browse my Nokia 3110c mobile's Folders & files such as sms, .jpg flies, video files, etc. [COLOR=Red]except INTERNET. [/COLOR]


After discovered the mobile set on PC, when click on **Network Manager** icon at the top of the Ububtu desktop, then pop-up windows shows "** No network device available**". So  I can't connect to internet & I have to try many times. I can't update or downloading anything for Ubuntu. 

[COLOR=Red]
[/COLOR]
[COLOR=Red]On-line Ubuntu is far far better than Off-line UBUNTU. So without internet Ubuntu is nothing. [/COLOR]

---------------------------------------------------------------
**In Residence:**
In my residence desktop computer, in both Ubuntu 9.10 Karmic & Windows-7 Ultimate - Internet connection is successful.


In Ubuntu Desktop, Nokia 3110c mobile is discovered  on PC via bluetooth-USB adapter. When click on **Network Manager** icon,  then pop-up windows shows "[COLOR=Red]**00: 1B:33:CC:9A:D6 PANU**[/COLOR]". 



When click on [COLOR=Red]**00: 1B:33:CC:9A:D6 PANU **[COLOR=Black], then within a second internet connection is establish successfully in Ubuntu. Nokia 3110c is designated as [/COLOR][/COLOR][COLOR=Red]**00: 1B:33:CC:9A:D6 PANU **[COLOR=Black]which is a **network device.**[/COLOR][/COLOR]
[COLOR=Red][COLOR=Black]**----------------------------------------**[/COLOR][/COLOR]
[COLOR=Red][COLOR=Black]I can't understand, in Ubuntu desktop, why **Network Manager** failed to establish internet connection in office workplace Desktop computer. I think, there is  bug in [/COLOR][/COLOR][COLOR=Red][COLOR=Black] **Network Manager.**[/COLOR][/COLOR]


[COLOR=Red][COLOR=Black]So, in office, I have been using Windows-7 most of the time because it has been impossible to get a internet connection. Now, I'm stay in online using Windows-7 internet connection.[/COLOR][/COLOR]


[COLOR=Red][COLOR=Black]All the best,[/COLOR][/COLOR]


[COLOR=Red][COLOR=Black]Moinul Abrar[/COLOR][/COLOR]
[COLOR=Red][COLOR=Black]Chittagong, Bangladesh[/COLOR][/COLOR]
[COLOR=Red][COLOR=Black]09 December 2009
[/COLOR][/COLOR]


  [FONT=&quot][/FONT]

  [FONT=&quot][/FONT][COLOR=Red][COLOR=Black][/COLOR][/COLOR]




[COLOR=Red][/COLOR]


  [FONT=&quot] 
[/FONT]






[FONT=&quot] [/FONT]

  
****
  

[COLOR=red][/COLOR]

---

### Post by pdc on 2009-12-09
many have reported problems with mobile broadband in 9.10 whereas in 9.04, many reported happiness

---

### Post by cavh on 2009-12-09
Are you running the same kernel on your office machine as you run on your home machine? You can check by running the following command in a terminal window (Applications -> Accessories -> Terminal):

```
uname -r
```

If there is a difference in the kernel versions, then I would suggest trying the same kernel and seeing if that resolves the issue. You can change kernels by following these steps:  

1. Open Synaptic (System -> Administration -> Synaptic Package Manager)
2. CTRL+R to refresh the list of available packages
3. In the search box, enter the kernel number you discovered by running the *uname-r* command I listed above
4. Select the kernel for installation - the entry you want will be in the format of *linux-image-2.6.xx.xx-generic*
5. Click the green apply tick symbol
6. Reboot once Synaptic has applied the change

---

