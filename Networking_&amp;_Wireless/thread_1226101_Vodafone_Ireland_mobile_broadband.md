---
title: "Vodafone Ireland mobile broadband"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by AlanRyan on 2009-07-29
I have just bought a Dell Inspiron mini with ubunto. Dell have just told me that Ubunto does not support Vodafone mobile broadband as it wont load the software.
 
Is there any solution to this or do I have to get windows?

---

### Post by Grenage on 2009-07-29
I'd give it a whirl anyhow, see what happens.  While I can't speak for Vodafone, I plugged my girlfriend's '3' dongle in, and it works perfectly.  The Ubuntu prompts took care of it all.

---

### Post by AlanRyan on 2009-07-29
Cheers, yea unfortunately I have tried it and it wont run the setup.exe file

---

### Post by RikoW on 2009-07-29
Hi :)

if network manager cannot deal with it automatically (which it did for my vodafone UMTS modem), try the connector software for Linux from here:

[https://forge.betavine.net/frs/?group_id=12]("https://forge.betavine.net/frs/?group_id=12")

In fact, at first NM would not recognize the dongle, but after installing the above software it did. I assume, it has to do with the fact, that this sticks are usually switching devices, which need to be switched to the modem mode.

Cheers,

                 Riko

---

### Post by AlanRyan on 2009-07-29
Thanks Riko, do I need to download all of those files? I'll have to find a wireless hotpsot to do so.

---

### Post by RikoW on 2009-07-29
I'd install the lasted svn deb package for your machine, for example:

  vodafone-mobile-connect_svn20090615_all.deb

and the latest usb-modeswitch package which actually switches the stick into modem mode as I mentioned earlier. 

Probably, the vodofone-mobile-connect installation will request to install a bunch of python dependencies in addition.

Good luck and let us know, if you were successful.

           - Riko

---

### Post by AlanRyan on 2009-07-29
Thanks a Mil Riko. I'll that and let you know. Pint of Guiness on its way to you :D

---

### Post by AlanRyan on 2009-08-11
Hi Riko...tks for the prompts so far...I think I'm nearly there....I've downloaded the .deb files and tried to install them as packages...hovever, it quckly threw up some error messages "libxcb -shape0 is missing final newline"...I tried installing the prvious version of the .deb file but same error appears....also happens to the second .deb file...I tried continuing with the install process but the laptop doesn't initiate the setup.exe file ...any ideas what I should do next/

Thanks.....Alan

---

### Post by RikoW on 2009-08-11
Hi Alan,

I already thought you gave up on that project ... :)

Can you post exactly which deb files you tried install and what dpkg spit out when it failed? Just copy&paste the terminal content.

Cheers,

             Riko

---

### Post by craptree on 2009-08-30
Works perfectly under jaunty after some updating!

see [http://ubuntuforums.org/showthread.php?t=961334&highlight=vodafone+dell+mini](http://ubuntuforums.org/showthread.php?t=961334&highlight=vodafone+dell+mini)

Riz

---

