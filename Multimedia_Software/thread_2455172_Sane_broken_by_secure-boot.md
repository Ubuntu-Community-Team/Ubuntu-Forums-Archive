---
title: "Sane broken by secure-boot"
date: 2020-12-14
forum: Multimedia Software
---

### Post by raoul-markus on 2020-12-14
Hi, 

I recently upgraded my print/scanserver to Ubunut 20.04 server. Already I think the installation of the sane utils in 20.04 is a bit broken: usb port belongs to "lp", but saned is in the group "scanner". This could be fixed by me just by some cumbersome work. 
But then, when everything was tidied up, the scanner came and went. sane-find-scanner showed it ok, but scanimage -L only after fresh reboot. It stopped after some activities. Finally I found in the syslog lines like
```
kernel: [27767.598418] Lockdown: scanimage: /dev/mem,kmem,port is restricted; see man kernel_lockdown.7
```

This lead me to here:
[https://bugzilla.redhat.com/show_bug.cgi?id=1599197](https://bugzilla.redhat.com/show_bug.cgi?id=1599197)

and finally to here:
[http://itadminguide.com/disable-secure-boot-in-ubuntu/](http://itadminguide.com/disable-secure-boot-in-ubuntu/)

Now the scanning works again and is reliable. 

Just want to share the experience, took me around 4 hours to fix this, which I consider as a straight forward installation task of a scanner.  

I'll also report a bug for sane, I feel it should also work on securebooted boxes.

---

### Post by raoul-markus on 2020-12-16
That was too quick. Seems that when I print on the same printer/scanner (Samsung SCX-4623), the usb connection to the scanner is lost. 
Surpising: a first attemt of scaniamge -L after printing something still discovers the scanner, but a second and all subsequent do not find the attached Scanner any more. A usbreset does not help, only reboot.

So after some debugging with ```
SANE_DEBUG_XEROX_MFP=255 SANE_DEBUG_SANEI_USB=255 scanimage -L
```
 I found a variable SANE_USB_WORKAROUND which somehow looked promising. I checked in 

[http://www.sane-project.org/man/sane-usb.5.html](http://www.sane-project.org/man/sane-usb.5.html)

and included SANE_USB_WORKAROUND=1 in my /etc/init.d/saned script as well as in the startup of the scanserv-js

```
 docker run -d -p 8080:8080  -e SANE_USB_WORKAROUND=1 -v /var/run/dbus:/var/run/dbus --restart unless-stopped --name scanservjs-container --privileged sbs20/scanservjs:latest
```

Now finally the scanner works reliably.:)

---

