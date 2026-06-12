---
title: "AMD/ATI Drive Install Fails"
date: 2012-09-10
forum: Multimedia Software
---

### Post by CarlosinFL on 2012-09-10
I've got a new AMD / ATI R7750 PCI-E video card and I'm not exactly sure the correct way to install the 3rd party / closed source drivers. When I use the GUI tool, it fails for some reason:

```
Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log
```

Then I review the referenced logs:

```
2012-09-10 14:53:36,683 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-09-10 14:53:36,755 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-10 14:53:36,755 DEBUG: fglrx_updates is not the alternative in use
2012-09-10 14:53:36,764 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-10 14:53:36,764 DEBUG: fglrx_updates is not the alternative in use
2012-09-10 14:53:36,785 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-10 14:53:36,785 DEBUG: fglrx_updates is not the alternative in use
2012-09-10 14:53:36,794 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-10 14:53:36,794 DEBUG: fglrx_updates is not the alternative in use
2012-09-10 14:53:36,808 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-09-10 14:53:36,808 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-09-10 14:53:37,834 DEBUG: Shutting down

```

Any ideas what I'm doing wrong or how to correctly get drivers loaded on my Linux system for this video card?

---

### Post by CarlosinFL on 2012-09-11
...anyone? ):P

---

### Post by TenPlus1 on 2012-09-11
Open a Terminal window and type the following commands and wait for prompt to appear after each:

   sudo apt-get install fglrx fglrx-amdcccle

   sudo aticonfig --initial

Now reboot and your Ati graphics should be working fine :)

---

### Post by QIII on 2012-09-11
The graphical installation method simply does not work for everyone.  Why that happens is beyond me.  I don't recommend the use of the "Post release updates" version at all for the time being.  If you tried to install that and it failed, that may be the cause of your current issue.

The suggestion above is correct.  However, I think you should attempt to first purge the driver you attempted to install just to be sure.

In the ATI driver wiki in my signature, please have a look at the section "Using the Ubuntu repositories (alternate command line method)".

Also, to get hardware acceleration (which is, regrettably, not as robust as it is for NVIDIA on Linux), please also see the section "Enabling Video Hardware Acceleration".

Towards a bottom are a few common troubleshooting items.

---

### Post by CarlosinFL on 2012-09-12
> **TenPlus1 said:**
> Open a Terminal window and type the following commands and wait for prompt to appear after each:

   sudo apt-get install fglrx fglrx-amdcccle

   sudo aticonfig --initial

Now reboot and your Ati graphics should be working fine :)

This appeared to have worked fine however when I rebooted, I still see a AMD water mark in the lower right corner of my O.S. that says "Unsupported hardware" with the AMD logo. Is there a way to get rid of this? Seems really odd to me they would do this...

---

### Post by QIII on 2012-09-12
It appears as though the 12.4 driver may be troublesome for the 7750.

You can try uninstalling the driver

```
sudo apt-get purge fglrx fglrx-amdcccle
```

and reinstalling a later version manually, as per the instructions for 12.6 in the wiki.  Change as necessary to get 12.8 if you want it.

If it's any consolation, several solutions I found had links to that part of the wiki.

---

### Post by CarlosinFL on 2012-09-13
Thanks all. Decided to go with Debian and everything appears to be working fine. Thanks for the info!

---

