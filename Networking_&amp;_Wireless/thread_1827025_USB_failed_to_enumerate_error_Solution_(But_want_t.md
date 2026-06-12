---
title: "USB failed to enumerate error Solution (But want to make it permanent)"
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by karlw1lk1ns on 2011-08-17
Okay so my background. I have been using Ubuntu a shortwhile I updated to 11.04 recently and I had suddenly lost the ability to use any device with my USB ports. 

Dmesg gave me something along the lines of "hub 1-0:1.0: unable to enumerate USB device on port 4".

After much playing around I thought I'd try 10.4.3 just to see if I have introduced the problem from the update, but the problem was still there. (So for clarity I'm NOW running 10.4.3)

I eventually came across the following solution (It is from this link all credit to the author [http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/](http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/)) :

> [Solved] Unable to enumerate USB device (Disabling ehci_hcd)

Some hardware just don’t work with ehci_hcd on Karmic Koala. My memory stick from transcend refused to work no matter what I did. After plugging the device nothing happened, doing dmesg showed me the following error:

Apr 18 10:59:04 dpac-laptop kernel: [73668.388060] usb 1-2: new high speed USB device using ehci_hcd and address 5
Apr 18 10:59:04 dpac-laptop kernel: [73668.473034] hub 1-0:1.0: unable to enumerate USB device on port 2

After searching a lot, I came to a conclusion that my device doesn’t work with USB 2.0. So I disabled the ehci_hcd to make it work.
Since Karmic doesn’t use ehci_hcd as a module, modprobe -r ehci_hcd no longer works. The module is compiled into kernel. To disable it execute the following commands in terminal:

cd /sys/bus/pci/drivers/ehci_hcd
ls
You will see a file with 0000:00:xx.x format. Execute the following command:
sudo sh -c 'echo -n "0000:00:xx.x" > unbind'
Replace the xx.x with the numbers displayed on your file. It should disable the ehci_hcd.
I plugged in my memory stick, and it worked.
Please note that you’ll have to do all this each time you restart.
UPDATE
You can now use the following script to disable ehci_hcd. It is far more simpler since it just needs you copy pasting the commands instead of a manual action. Here it goes:
cd /sys/bus/pci/drivers/ehci_hcd/
sudo sh -c 'find ./ -name "0000:00:*" -print| sed "s/\.\///">unbind'

This works great but when I restart I have to do this again, is there a way of making it a permanent change?

Also an explanation of what the error actually was and what the cause would be, would make me a wiser person :P

Many thanks in advance for any help :)

---

### Post by karlw1lk1ns on 2011-08-18
Okay I have now got a permanent solution:

Press Alt+F2 or open the Terminal and paste the following:
> 
Type gksu gedit /etc/rc.localNow gedit will open and paste the code that worked before and save it, this will run it for you on each startup:

> 
cd /sys/bus/pci/drivers/ehci_hcd/
sudo sh -c 'find ./ -name "0000:00:*" -print| sed "s/\.\///">unbind' Now when you do a reboot it should still work, hope this helps.

---

