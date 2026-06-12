---
title: "Error - &quot;Could not claim the USB device&quot;"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by bananabob on 2007-03-12
My camera has been able to connect to my Edgy system several times. Today, however, I attached it to my a USB port, and received the following message from gthumb

> 
An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.


I searched the forums and came up with this post 

[http://ubuntuforums.org/showthread.php?t=358518](http://ubuntuforums.org/showthread.php?t=358518)
which point to this entry:
[http://www.ubuntuforums.org/showthread.php?t=340271](http://www.ubuntuforums.org/showthread.php?t=340271)
This describes my problem, but.....

When I do the lsusb command I get the following returned:

> 
Bus 005 Device 012: ID 040a:0130 Kodak Co. DC-280
Bus 005 Device 002: ID 04b8:0103 Seiko Epson Corp. Perfection 610
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 08bb:2702 Texas Instruments Japan 
Bus 001 Device 004: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 003: ID 046d:c30f Logitech, Inc. 
Bus 001 Device 005: ID 04f9:001a Brother Industries, Ltd HL-1430 Laser Printer
Bus 001 Device 001: ID 0000:0000  


Then when I did the gedit of /etc/udev/rules.d/45-libgphoto2.rules the line that I should be adding, according to the post, is already present

> 
# udev rules file for libgphoto2 devices (udev < 0.98)
#
BUS!="usb*", GOTO="libgphoto2_rules_end"
ACTION!="add", GOTO="libgphoto2_rules_end"

<snip>

SYSFS{idVendor}=="040a", SYSFS{idProduct}=="057e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="058a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="058c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="058d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0589", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="059a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="05a2", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="05ba", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="05a7", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="059c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0560", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0560", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0535", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0566", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0566", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0574", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0573", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0571", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0584", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0579", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0578", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0578", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="057a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="057b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0586", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="057c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0121", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0110", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0111", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0130", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0112", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0132", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0160", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0131", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0525", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0500", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0510", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0530", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0170", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0555", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0576", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0550", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0570", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0572", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0575", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="057d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="057f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0577", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0300", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0540", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0568", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0569", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0565", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0567", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0400", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0592", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="058e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="058f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="059d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="059e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0587", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0580", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0588", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0403", MODE="0660", GROUP="plugdev"

<snip>

LABEL="libgphoto2_rules_end"



I presume that some update I have applied has caused this problem because, as I said, it used to work fine.


Can someone tell me what I can do to fix the problem please?

---

### Post by Forseti on 2007-03-14
Hi!
I've got the same error with my Kodak EasyShare i530 camera. However it occured only after I upgraded **libgphoto2-2** and **libgphoto2-port0** from version **2.2.1-ubuntu4** to [B]2.3.0-ubuntu3-edgy2.

[/B]The solution was obvious: I've just downgraded mentioned files in Synaptic. Now everything works fine as before.

Should I report it somewhere?

-- 
Regards
Forseti

---

### Post by WStephens on 2007-03-14
Hello,

Same thing here, Kodak easy share and updated to the backports version and it broke. 2.2.1-2ubuntu4 got things going good.

W. Stephens

---

### Post by bananabob on 2007-03-14
Great that works like a charm.

I guess this needs reporting as a bug. Will you do it or shall I?

Also do you know how to stop the update manager telling me I need to update these modules, I get the icon in the panel all the time?

Cheers
Bb

---

### Post by clean97gti on 2007-03-14
Downgrade worked for me too.
Camera is a Canon S3 IS.

---

### Post by WStephens on 2007-03-14
I did a quick search and found:

[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)

I used the line in the description in the bug and now the backport versions work as expected.

To stop the versions from telling you there is an update you can go to synaptic>repositories>internet updates and uncheck the update from backports line.

__________
W. Stephens

---

### Post by bananabob on 2007-03-14
OK - So we can assume that a fix is forthcoming.

If i do the business with synaptic, what would happen to other backport updates. I assume I would get no notification of those, and I may need to have an update?

---

### Post by WStephens on 2007-03-14
That would stop all backports from being updated maybe in synaptic highlight the package click packages>lock version is what your looking for.

---

### Post by bananabob on 2007-03-14
Perhaps it would help if I understood what "backports" really means.

I assume that it is the repository where older versions of software resides, so that it can be used if required.

What worries me is if I  do synaptic>repositories>internet updates and uncheck the update from backports line I will not receive any notification of updates to backported software.

This seems like a bad idea because I would want to know that updates to backported software, at least, these libgphoto modules, so I can get the fix when it comes out. 

Maybe I don't need to update the libgphoto modules at all because they work for me.

I guess what I am saying is I am unsure of what I have done to my system by backporting these libgphoto modules, and would like to understand more about the consequences before I add to any problems that may arise in the future by doing the synaptic>repositories>internet updates thing.

Can anyone explain?

---

### Post by WStephens on 2007-03-14
Backports are where package maintainers recompile testing or unstable packages so that we can have the newest and greatest packages without having the long wait for newer and greater libraries.  For example, in edgy there was a newer version of gstreamer plugins that fixed alot of bugs and those running dapper for the long term support can get the new gstreamer plugins backported so they get the bugs fixed without upgrading to edgy.

---

### Post by alanjackson on 2007-03-15
> **WStephens said:**
> I did a quick search and found:

[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)

I used the line in the description in the bug and now the backport versions work as expected.

To stop the versions from telling you there is an update you can go to synaptic>repositories>internet updates and uncheck the update from backports line.

__________
W. Stephens

The latest backport Edgy update broke mine as well. This fixed it perfectly. Thanks!

---

### Post by gilgongo on 2007-03-17
> **Forseti said:**
> Hi!
I've got the same error with my Kodak EasyShare i530 camera. However it occured only after I upgraded **libgphoto2-2** and **libgphoto2-port0** from version **2.2.1-ubuntu4** to [B]2.3.0-ubuntu3-edgy2.

[/B]The solution was obvious: I've just downgraded mentioned files in Synaptic. Now everything works fine as before.



**[SIZE="4"]For anyone reading this that doesn't know how to downgrade with Synaptec:[/SIZE]**

1. Go to System > Administration > Synaptic Package Manager

2. Hit the Search button and find "libgphoto2"

3. Select libgphoto2-2 and libgphoto2-port0, and for each go to Package > Force Version

4. There will be a drop-down menu letting you choose the previous version (in this case 2.2.1-ubuntu4) for each package. 

5. Hit the "Apply" button. Your camera should now work and you can stop screaming.

Note that this means you will get an annoying message that "2 updated packaged are available" now. Not sure how best to deal with this for the moment, but perhaps wait until a new version of libgphoto2 is released that is higher than 2.3.0-ubuntu3-edgy2?

---

### Post by Artemis3 on 2007-03-18
Oh, just make sure you downgrade libgphoto2-2 first, lock its version and then libgphoto2-port0 and lock its version.

If you select both at the same time synaptic will want to uninstall various important packages such as gthumb, ubuntu-desktop f-spot, and only god knows why, wine...

And while you are at it, lock xchat and xchat-common versions (to 2.6.6); as the 2.6.8 upgrade wants you to upgrade the distro... It seems some of these backports belong to feisty already; which makes me wonder how come these packages ended in the backports edgy repository...

---

### Post by tonywhelan on 2007-03-18
> **WStephens said:**
> I did a quick search and found:

[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)

I used the line in the description in the bug and now the backport versions work as expected.

(snip)
__________
W. Stephens

This edit of the libgphoto2.rules file fixed problem for my Canon A700, thanks.

Tony

---

### Post by tpbarnabas on 2007-03-20
I didn't change the version back, editing of the libgphoto2.rules file fixed the problem for my Canon Powershot A85. 

I've changed 
the 3rd line in /etc/udev/rules.d/45-libgphoto2.rules
from 

BUS!="usb*", GOTO="libgphoto2_rules_end"

to

SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

and everything works fine.

---

### Post by Toadmund on 2007-03-31
Thanks gilgongo, downgrading got my Kodak easyshare DX6340 uploads back to working order!
:)

---

### Post by msolorzano on 2007-03-31
Thank God for your posts on this!

I just bought my Cannon PowerShot S3 IS yesterday ... when I plugged it in - ERROR!
The same error "Could not claim the USB device" being discussed here.
I'm going on a year w/ Linux and so far it's great!
Thanks again ... the downgrade worked for me too (Edgy user).

One thing I did not see mentioned here was the howto "force" the downgrade ... for other noo-b's like me "Synaptic menu>Package>Force Version" and select the downgrade version.

-M

---

### Post by flipkick on 2007-04-17
Another sigh of relief. Thanks.

---

### Post by otakuj462 on 2007-04-19
Same problem, Canon Powershot A520. This fixed it completely.

-Jake

---

### Post by Jetcollins on 2007-11-17
Hello. I have Feisty as well. I change the line in the conf file:

SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

And the issue is still unfixed. When I try to downgrade libgphoto2-2, the Force Package option is greyed out in the dropdown menu. 

In the repositories menu, under Updates tab, I have checked everything.

So, I cannot downgrade, it seems, and cannot get pictures from my Kodak Z740, which does show up in lsusb.

What next, please?

thanks in advance!

Peter

---

