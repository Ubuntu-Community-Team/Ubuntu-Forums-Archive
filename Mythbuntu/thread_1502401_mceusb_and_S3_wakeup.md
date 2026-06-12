---
title: "mceusb and S3 wakeup"
date: 2010-06-05
forum: Mythbuntu
---

### Post by dtaylorl on 2010-06-05
I'm trying to get mceusb working to wakeup my mythtv box from S3 suspend using this guide: 
[[Howto Mythtv] Use a remote to sleep and wakeup a mythtv frontend. - Overclockers Australia Forums](http://forums.overclockers.com.au/showthread.php?t=810214)

I'm stuck on step 3.  The computer does not wakeup from the remote.  A USB mouse wakes the system just fine.  It appears that the usb receiver is not receiving power at all when the computer is sleeping (the red led does not light up when I press buttons on the remote).  Yet if I put a mouse in the same USB port it receives power (optical mouse glows).  Suggestions?

---

### Post by matt06 on 2010-06-07
What is the contents of /proc/acpi/wakeup?  Also check BIOS Power Management settings for "Wakeup" or similar. (though you should be aware it's possible to break your working "sleep" by changing options there)

I remember following a similar guide ([see this thread also!]("http://ubuntuforums.org/showthread.php?t=711747")) and having to force my USB1 port to 'enabled' for resume from S3/USB to work properly. /proc/acpi/wakeup:

```
USB1      S3     enabled   pci:0000:00:10.0
USB2      S3     enabled   pci:0000:00:10.1
USB3      S3     enabled   pci:0000:00:10.2
USB4      S3     enabled   pci:0000:00:10.3
```
My USB1 here was always disabled even with proper BIOS options.

```
matt@mythtv-bs:~/.lirc$ cat /etc/init.d/wakeup-resume.sh
#!/bin/sh
# modify /proc/acpi/wakeup to allow resume from usb
# to test on cmdline use sudo sh -c "echo XXXX > /proc/acpi/wakeup"
echo USB1 > /proc/acpi/wakeup
echo PS2K > /proc/acpi/wakeup
# echo PS2M > /proc/acpi/wakeup
```
I changed permissions for the script as per the link I posted above and also added the NOPASSWD entry for running /usr/sbin/pm-suspend.  Was playing with the PS2 ports also, but only use USB now.  After doing that, USB1 remains enabled in /proc/acpi/wakeup on fresh boot.

Contents of my ~/.lirc/mythtv file if it helps.

```
# add button for remote suspend
begin
    remote = mceusb
    prog = irexec
    button = Power
    config = sudo /usr/sbin/pm-suspend
    repeat = 0
    delay = 10
end
```
(should I have & at the end of the config = command, anyone?)

EDIT:  most of this is from memory so I apologize if any of it is inaccurate.

---

### Post by dtaylorl on 2010-06-07
Thanks for the reply matt06.  That looks pretty much exactly like what I am doing.  I have tested my /proc/acpi/wakeup before using pm-suspend, and all the usb ports are set to enable.  Also, as I mentioned a usb mouse seems to wakeup the system just fine.

The thing I'm noticing is that the USB mouse will glow when the computer is sleeping, but the red LED on the IR Receiver does not blink when I press remote buttons.  Does the computer still reduce power to the USB ports when it is sleeping?  I'm wondering if there is any chance the IR Receiver requires more power to function than a mouse?

---

### Post by matt06 on 2010-06-07
Hi dtaylorl.  I just tested mine and while my frontend is sleeping, the receiver does *not* light up when pushing any remote buttons so that may be normal behavior.  Once I hit the proper 'Power' button, a split second after the system wakes, I can see the red LED lighting for button pushes.

---

### Post by dtaylorl on 2010-06-07
Thanks.  I think I actually *just* figured out the problem.  Apparently it only wakes up when the power button from a microsoft remote is pressed.  The remote I am using is not a microsoft remote.  If I set the device code on my universal remote to the microsoft code it successfully wakes up the machine.  As you said, the receiver does not light up until after the machine is awake.  Unfortunately, I do not want to use the microsoft remote codes, so I will have to find a way to map the power button only.  Unless someone knows another way?

---

