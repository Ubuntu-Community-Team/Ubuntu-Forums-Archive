---
title: "gphoto2 Canon 400d new error message"
date: 2009-04-10
forum: Multimedia Software
---

### Post by zongpog on 2009-04-10
Dear all,

  Two days ago I downloaded my images from my camera with the command gphoto -P.  It worked then & has always worked.

Today, two days later, after being on holiday and not using my computer, I ran the same command, but got this:


```


output from /var/log/messages from when the Canon 400d was plugged in:
Apr 10 16:00:46 max kernel: [  840.870967] usb 5-1: new high speed USB device using ehci_hcd and address 23
Apr 10 16:00:46 max kernel: [  841.414290] usb 5-1: new high speed USB device using ehci_hcd and address 24
Apr 10 16:00:47 max kernel: [  841.957610] usb 5-1: new high speed USB device using ehci_hcd and address 25
Apr 10 16:00:47 max kernel: [  842.476965] usb 5-1: new high speed USB device using ehci_hcd and address 26

$ gphoto2 -l
                                                                               
*** Error ***              
An error occurred in the io-library ('Bad parameters'): Could not find USB device (vendor 0x4a9, product 0x3110). Make sure this device is connected to the computer.
*** Error (-2: 'Bad parameters') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt -l

Please make sure there is sufficient quoting around the arguments.


```



No changes to the PC, nor to the camera. I have tried another USB port in case there was a problem with it.

  Any ideas?

Regards.

---

