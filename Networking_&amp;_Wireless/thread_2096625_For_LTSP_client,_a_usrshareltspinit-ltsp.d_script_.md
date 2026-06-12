---
title: "For LTSP client, a /usr/share/ltsp/init-ltsp.d script with sed gives duplicate result"
date: 2012-12-20
forum: Networking &amp; Wireless
---

### Post by JD Hupp on 2012-12-20
[SIZE=-1]I want to use a client boot script at       /usr/share/ltsp/init-ltsp.d/50-apcupsd with sed to modify a       configuration file for apcupsd (APC UPS manager daemon).  The       script:
      
      sed -i \
          -e 's/UPSCABLE usb/UPSCABLE ether/' \
          -e 's/UPSTYPE usb/UPSTYPE net/' \
          -e 's/DEVICE/DEVICE Lubuntu1:3551/' \
          -e 's/TIMEOUT 105/TIMEOUT 60/' \
          -e 's/NETSERVER on/NETSERVER off/' \
          -e 's/NISIP 0.0.0.0/NISIP 127.0.0.1/' \
      /etc/apcupsd/apcupsd.conf
      
      It all works fine except for this substitution:
          -e 's/DEVICE/DEVICE Lubuntu1:3551/'
      
      It takes this line:
          DEVICE
      and replaces it with this:
          DEVICE Lubuntu1:3551 Lubuntu1:3551
      
      However, if I run the same script on the server, it does not       produce the duplicate "Lubuntu1:3551".
      -------------------------------------
      
      Wondering if the colon was a special character that needed to be       escaped (but not sure exactly how to do that), I tested the idea       by simply replacing it with a space.  Effectively:
      
          sed -e 's/DEVICE/DEVICE Lubuntu1 3551/'
      
      Now on the LTSP client, the resulting line is:
      
          DEVICE Lubuntu1:3551 Lubuntu1 3551
      -------------------------------------
      
      I don't know what the syntax means, but someone also suggested the       following:
      
          sed -e 's/DEVICE$/DEVICE Lubuntu1:3551/'
      
      And that had no effect whatsoever.  The result was still "DEVICE       Lubuntu1:3551 Lubuntu1:3551".
      -------------------------------------
       
      Seeking a work-around, I added an /etc/apcupsd/apcupsd_slave.conf       file which was already modified with the parameters I want clients       to boot with.  Then I edited       /usr/share/ltsp/init-ltsp.d/50-apcupsd to remove the sed command       and added:
      
          cp /etc/apcupsd/apcupsd_slave.conf  /etc/apcupsd/apcupsd.conf
      
      But this does not seem to execute.  I also tried:
      
          rm /etc/apcupsd/apcupsd.conf
          cp /etc/apcupsd/apcupsd_slave.conf  /etc/apcupsd/apcupsd.conf
      
      But this does not execute either.  And if on a booted-up client I       open a local session xterminal and run:
      
          $ su root cp /etc/apcupsd/apcupsd_slave.conf        /etc/apcupsd/apcupsd.conf
      
      it returns:
      
          /bin/cp: cannot execute binary file
      
      [Does anyone know why?]
      -------------------------------------
      
      Someone pointed out that with my initial sed command, I would get       the duplicate result I report if the script ran twice.  So one       question might be whether there is some mechanism that would cause       the script to run twice.  For instance, if LTSP is actually built       such that I only need the /usr/share/ltsp/init-ltsp.d/50-apcupsd       script on the server, and not in the client network boot image,       that would cause it to run twice.
      
      But I don't think that is what's going on.  My current thought is       this: I think the LTSP clients use a static, read-only network       boot image + a writable union filesystem overlaying the read-only       image.  I saw a slim mention of that in writing somewhere,       sometime.  (Perhaps I'm not searching with the right terms to find       better documentation.)  But if that overlay has persistence       somehow, or is cached on the server, then perhaps there could be       results like the above.  It would effectively be run multiple       times over succeeding boots and be applied to a persistent       overlay.
      
      Can anyone confirm if LTSP uses something like a writable overlay       filesystem?  If so, can I read more about that somewhere?
      
      Does anyone have a work-around?
    [/SIZE]

---

