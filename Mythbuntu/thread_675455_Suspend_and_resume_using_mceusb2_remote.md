---
title: "Suspend and resume using mceusb2 remote"
date: 2008-01-22
forum: Mythbuntu
---

### Post by not4us on 2008-01-22
Getting closer now to have my perfect HTPC setup.
My Frontend/backend box is on all the time, but I have a frontend on my bedroom being controlled by a Windows MCE remote (using lirc_mceusb2).

I now need to configure mythtv and lirc so that I can use the "PC" power button in the remote to suspend and resume the box from bed.

I got suspend working on the box (had to tweak around my xorg.conf for my Geforce 6200 to work on resume) but not using the remote.
Tried to use irexec on my .lircrc to call /etc/acpi/sleep.sh but a permission issue would stop me from getting the machine to suspend using the remote.
Used visudo to change permissions to sleep.sh but still no go.
Any other way to go about this?
I recall reading somwhere that you can change the frontend settings to execute commands when you select "Yes, and Shutdown" from the close menu but I don't know how to go about this.

If I could get the suspend working that would so me for now as I don't want to get out of bed to power of or suspend the box.

Then I'd like to get resuem working from the remote. I've tried by enabling all the USB ports in /proc/acpi/wakeup and I can see the light on the receiver flashing when the machine is suspended and I press the PC button on the remote but nothing happens.
It doesn't even wake up when I press the buttons on my keyboard (USB) or move the mouse (USB), the only way to do it is by pressing the power button.
The BIOS is setup to S3 and to wake up on USB devices and I had it working on Windows XP previously so I know the hardware can do it.

Any help???

---

### Post by not4us on 2008-01-23
Replying to myself here...

Got standby to work by pressing the PC button on the MCE remote.
This is what I did (based on this thread ):
[LIST=1]
[*]Create a folder for the script
**$ mkdir ~/.mythtv/mythscripts**
[*]Create a script that runs "sudo /etc/acpi/sleep.sh" as follows:
**$ sudo nano ~/.mythtv/mythscript/suspend.sh**
[COLOR="Gray"]# ! /bin/bash

# This script will be used to suspend the computer
# from within MythTV when the myth user selects
# the "PC" button on the MCE remote

# Suspend
sudo /etc/acpi/sleep.sh

exit[/COLOR]
[*]Get into root using:
**$ sudo -i**
[*]Add permission using visudo:
**$ visudo**
[*]Add this line at the end of the suoders.tmp:
[COLOR="Gray"]%*username* ALL= NOPASSWD: /etc/acpi/*[/COLOR]
[*]Make the script executable:
**$ sudo chmod g+x ~/.mythtv/mythscript/shutdown.sh**
[*] Start the irexec daemon on boot by adding this to /etc/rc.local:
[COLOR="Gray"]/usr/bin/irexec -d ~/.mythtv/.lircrc[/COLOR]
[*]Add this to your .lircrc file:
[COLOR="Gray"]begin
    prog = irexec
    button = Power *(or wahetver the PC button is named on your lirc hardware config)*
    config = /home/*username*/.mythtv/mythscript/suspend.sh
end[/COLOR]
[*]Restart Lirc
**$ sudo /etc/init.d/lirc restart**
[*]Now use the PC button on the remote to put the computer to sleep!
[/LIST]

Now all I've left to do is to get the wakeup from the remote working.
I'm pretty sure it's somethig to do with the ACPI settigns as I can see the lght blinking on the receiver when the computer is sleeping.
I think I'm going to have a play with /etc/defaults/acpi-support tonight and see how that goes.

---

### Post by yankcrime on 2008-02-06
Hey there not4us.  I am currently in the process of doing the same as you.  I am in the same boat as you, in as much as I have sleep working (I needed to use s2both for the sleep, but same diff I think).  At one point, I had the resume on pc button working by allowing the USB device to wake in acpi.  This is done by the following (use sudo if necessary):
```
echo USB0 > /proc/acpi/wakeup
```
You can check whether this works by catting /proc/acpi/wakeup:
```

myuser@myth-masterbed:/etc/acpi$ cat /proc/acpi/wakeup 
Device  S-state   Status   Sysfs node
P0P2      S4     disabled  pci:0000:00:01.0
P0P1      S4     disabled  pci:0000:00:1e.0
UAR1      S4     disabled  pnp:00:06
PS2K      S4     disabled  pnp:00:0d
PS2M      S4     disabled  pnp:00:0e
EUSB      S4     disabled  pci:0000:00:1d.7
USBE      S4     disabled  pci:0000:00:1a.7
P0P5      S4     disabled  
P0P6      S4     disabled  
P0P7      S4     disabled  
P0P8      S4     disabled  pci:0000:00:1c.4
P0P9      S4     disabled  pci:0000:00:1c.5
USB0      S4     enabled   pci:0000:00:1d.0
USB1      S4     disabled  pci:0000:00:1d.1
USB2      S4     disabled  pci:0000:00:1d.2
USB3      S4     disabled  
USB4      S4     disabled  pci:0000:00:1a.0
USB5      S4     disabled  pci:0000:00:1a.1
P0P4      S4     disabled  pci:0000:00:1c.0
```
Note that there is an "enabled" next to USB0.

You have to do this everytime you reboot (but not when you suspend/resume).  I put it in **rc.local**

Unfortunately, it isn't working again, and I am not sure why.  I am convinced the solution is to make sure the correct modules are not unloaded upon suspend.

A bigger problem for me is that upon reboot (right now not from remote), the remote does not work in MythTV.  irw confirms it is getting commands.  Again, I suspect it is because lirc is being unloaded, and therefore MythTV forgets how to jive with the remote.


I think my wake on remote is not working because I am trying to wake from a suspend to ram (S3) not a suspend to disk (S4).  Also perhaps s2both isn't acpi compatible.

---

