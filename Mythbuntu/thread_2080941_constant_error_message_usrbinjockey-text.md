---
title: "constant error message /usr/bin/jockey-text"
date: 2012-11-05
forum: Mythbuntu
---

### Post by arjay1 on 2012-11-05
I am in the process of installing mythbuntu 12.10 on a spare PC. I have it installed and am going through the setup process.  

I keep getting an error message that references /usr/bin/jockey-text and asks if I want to send a report about it.  It comes up every few minutes and is seriously irritating as it overlays whatever I am working on and I have to take time out to cancel it or resend the report (requires password).  I have googled and searched here but not much turned up.

Anyone help out?

Thnx

---

### Post by 2F4U on 2012-11-05
Well, Ubuntu experienced an error and is trying to tell you about it. If you opt to report, you will get more details about the error. As you may imagine, there are a lot of possible errors, and without more details it will be difficult to help.

---

### Post by arjay1 on 2012-11-05
> **2F4U said:**
> Well, Ubuntu experienced an error and is trying to tell you about it. If you opt to report, you will get more details about the error. As you may imagine, there are a lot of possible errors, and without more details it will be difficult to help.

Thanks for the prompt reply.  Unfortunately this is all the info I get.  I just wondered if anyone else had come across this problem.  Of course, just to be perverse - it has stopped coming up.  If it does again, I'll see what else I can glean.....

---

### Post by 2F4U on 2012-11-05
The error may be totally harmless. Find out if you experience any problems aft the error message comes up. I also had such an annoying error message, telling me that my GPU hung. However, I didn't experience any problems and the GPU worked normal. I ended up disabling the crash report completely by editing /etc/default/apport and changing the line that says enabled=1 to enabled=0. This disables Apport and no more error messages are raised.

---

### Post by nickrout on 2012-11-05
> **arjay1 said:**
> I am in the process of installing mythbuntu 12.10 on a spare PC.No you aren't because there is no mythbuntu for 12.10. 

[http://www.mythbuntu.org/12.10/release](http://www.mythbuntu.org/12.10/release)

At best you are installing the minimal CD and then mythbuntu-desktop.

---

### Post by arjay1 on 2012-11-05
> **nickrout said:**
> No you aren't because there is no mythbuntu for 12.10. 

[http://www.mythbuntu.org/12.10/release](http://www.mythbuntu.org/12.10/release)

At best you are installing the minimal CD and then mythbuntu-desktop.

I stand corrected - my bad. It was Mythbuntu 12.04 of course from the same page you have posted. Is this a substantial issue that affects my problem, or are you just being pedantic?

---

### Post by nickrout on 2012-11-05
> **arjay1 said:**
> I stand corrected - my bad. It was Mythbuntu 12.04 of course from the same page you have posted. Is this a substantial issue that affects my problem, or are you just being pedantic?Perhaps pedantry, but it's hard to help someone who gives the wrong info :) Computers are pedantic!

jockey is the system that loads restricted drivers (ie closed source drivers like nvidia's propprietary drivers). Beyond telling you that, without the exact (pedantic?) error message it's hard to say.

If you send the report, does it stop?

---

### Post by arjay1 on 2012-11-06
> **nickrout said:**
> 
jockey is the system that loads restricted drivers (ie closed source drivers like nvidia's proprietary drivers). 
JFYI - this jockey error message started when the default (nouveau??) driver was running immediately after first install.  

It carried on intermittently after I installed the nvidia drivers using the "install additional drivers" via the menu. This never worked either - possibly because nouveau never got blacklisted properly. Finally I uninstalled all those drivers and used sgfxi to reinstall the nvidia ones.  Since then no further messages.

I then got so irritated with the limitations of the xfce desktop (pathetic file manager for starters) and loads of missing stuff I need that I installed KDE and now I have a proper desktop, Dolphin etc etc and am a happy bunny....

---

### Post by nickrout on 2012-11-06
> **arjay1 said:**
> JFYI - this jockey error message started when the default (nouveau??) driver was running immediately after first install.  

It carried on intermittently after I installed the nvidia drivers using the "install additional drivers" via the menu. This never worked either - possibly because nouveau never got blacklisted properly. Finally I uninstalled all those drivers and used sgfxi to reinstall the nvidia ones.  Since then no further messages.

I then got so irritated with the limitations of the xfce desktop (pathetic file manager for starters) and loads of missing stuff I need that I installed KDE and now I have a proper desktop, Dolphin etc etc and am a happy bunny....And why would you want those things on a mythtv machine?

---

### Post by arjay1 on 2012-11-06
> **nickrout said:**
> And why would you want those things on a mythtv machine?

Because at least during setup I need to do the most basic of things - like communicate with other PCs on my network for frontend and backend and copy files around like xmltv, smb.conf, xorg.conf for starters.  Thunar is absolute cr*p for browsing the network.  

Later, I need to stream music and share images from another PC, same again. I need to burn cds with a decent burner (K3b, beats the socks off Brasero), need access to Gimp 2.8 and a heap of other stuff.  Reckon KDE is superior for most software.  Need I go on??

My first choice would always be Mythdora - much better than mythbuntu IMO but unfortunately it is no longer under active development hence a return to trying mythbuntu again after 3 years.  I am also thinking of trying LinHES as an alternative to Mythbuntu - depends on how this experience goes.

---

### Post by Quazza on 2012-11-15
Hi Guys,

Any resolution on this one as I seem to be getting this one as well but I have the full error in the attachment below.

This seemed to show up after sending the error report, anyway help would be appreciated although as the system is my backend I don't need to be in front of it so ignoring it for time being is ok.

Cheers

Quazza :D

---

### Post by jazzhupal on 2012-11-17
Hi.
I've the same problem but only first line  "/usr/bin/jockey-text/". When I type in terminal full path, the terminal  displays a comment "adding drivers" and problem doesn't show anymore.

Peace :)

PS. Sorry for my English.

---

### Post by superm1 on 2012-11-19
If you are encountering constant crashes with jockey-text, can you please take a look in /var/crash for a crash report?  it should say what's up.

We don't install "whoopsie" by default in mythbuntu, but you could also install that and let it submit these crash reports automatically too.

---

### Post by kuramayoko10 on 2012-12-01
I am also having this problem on a fresh install of Ubuntu 12.04 64-bit.

The first time it happened I was clicking in "Additional Hardware" in the System Settings. It kept showing this error and the window wouldn't open. As suggested by the message I restarted my computer.
Ok, after the reboot I was able to choose the recommended driver for my nvidia card.

Then it occurred again when I tried testing my audio through the Test Audio in the System Settings. I have a Realtek HD Audio card.

So I am guessing this is happening whenthe system tries to fetch the proprietary drivers for those cards.

I tried running the program /var/bin/jockey-text
It searched for additional drivers but didn't report anything. 
I don't know if it installed them or not, but the error is gone for now. And both my video card and audio card are working fine.

---

### Post by mpearrow on 2013-01-02
Same thing happens to me on the 20 Thinkpad W530 systems I've set up by paving over the HD and installing Ubuntu 12.04 64-bit Desktop. As soon as I log in for the first time, and click on the taskbar to launch search (to get a terminal) the error about /usr/bin/jockey-text comes up. 

Not sure if it is relevant, but these laptops have the Nvidia Optimus technology enabled by default; however, before installing Ubuntu, I disable Optimus and the "integrated" graphics, using only the "discrete" graphics. 

These lines look interesting to my untrained eye:

 ```
2013-01-02 12:54:09,309 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
 2013-01-02 12:54:09,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
```

I have attached the contents of the /var/crash logfile. As others have noted, the issue seems to vanish once I install nvidia-current.  And yes, I have submitted the error report.

---

### Post by morinpatmorin on 2013-01-15
I'm having the same problem.  A full crash report is attached.  The kicker comes at the end:

```

   File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 68, in __init__
     self.getData()
   File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 149, in getData
     driver_version = self.__get_value_from_name(stripped_package_name)
   File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 87, in __get_value_from_name
     v = int(name)
 ValueError: invalid literal for int() with base 10: 'experimental-304'
UserGroups: 

```

---

### Post by superm1 on 2013-01-16
Even though it's the 304 version it's the same error.  That's because the 304 version is what's in the APT cache.

The original problem is fixed, so once you update to the newer version of Jockey it won't happen.

---

