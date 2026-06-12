---
title: "How to drive my IPW2200 wireless card?"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by haibin on 2009-09-28
My system is Ubuntu 9.04, kernel version is 2.6.28-11-generic.

Now I'm trying to install drivers for a new wireless card Intel Pro/Wiress 2200BG.

I searched the Internet and tried as the following, but it failed.

[COLOR=Red]sudo module-assistant[/COLOR]

and then select "ieee80211" & "ipw2200", and then build them.

Here it seemed there is something wrong with it.

[COLOR=Red]Installation of the ipw2200-source source failed.                  &#8593; 
     &#9474;                                                                    &#9646; 
     &#9474; Ignoring this package. Maybe you need to add something to          &#9618; 
     &#9474; sources.list, maybe the contrib and non-free archives.    

[COLOR=Black]I pressed Ok and then went on. Here came another error.[/COLOR]
[/COLOR]
[COLOR=Red]Build of the package ieee80211-source failed! How do you      &#9474; 
       &#9474; wish to proceed?                                              &#9474; 
       &#9474;                                                               &#9474; 
       &#9474;       VIEW     Examine the build log file                     &#9474; 
       &#9474;       CONTINUE Skip and continue with the next operation      &#9474; 
       &#9474;       STOP     Stop processing the build commands  [/COLOR]

In order to view the log file, I pressed VIEW.

[COLOR=Red]/usr/bin/make clean                                                        &#9618;
 &#9474; make[2]: Entering directory `/usr/src/modules/ieee80211'                   &#9618;
 &#9474; make[2]: *** No rule to make target `clean'.  Stop.                        &#9618;
 &#9474; make[2]: Leaving directory `/usr/src/modules/ieee80211'                    &#9618;
 &#9474; make[1]: [clean] Error 2 (ignored)                                         &#9618;
 &#9474; /usr/bin/make -C driver clean                            
[/COLOR]

Please help me. Right now I really do not know what to do next. Thanks.

---

### Post by haibin on 2009-09-29
Thank you very much.

I tried make menuconfig under Ubuntu. It seemed that ieee80211 & Wireless driver for IPW2200 have been installed and compiled.

The following is the graphs when I run make menuconfig.

<network device support>
<M>   Intel PRO/Wireless 2200BG and 2915ABG Network Connection

<wireless>
<M>   Generic IEEE 802.11 Networking Stack (mac80211) 

Does it mean that these modules have been compiled? How to check it out? And How to know if they are loaded while Ubuntu is running?

Thanks again.

---

