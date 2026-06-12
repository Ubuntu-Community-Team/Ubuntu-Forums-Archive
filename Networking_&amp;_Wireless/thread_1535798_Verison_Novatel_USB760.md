---
title: "Verison Novatel USB760"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by JPman on 2010-07-21
I've been away from Ubuntu since 8.04 because wvdial was axed after that release but am back because now I am using Verison Mobile Broadband and I heard Ubuntu supported it.  Sounds good.:D

So I installed 10.04 and hey it worked as soon as I entered the phone number for it to dial.    I stayed online all day during which I downloaded all the updates and a few programs.   Then I shut it down for the night.   

That was the one and only time I could get online.   All subsequent attempts failed.   No longer would 10.04 respond to the USB modem even though it mounted OK.

Well at least it worked once.   That is one time out of all the flavors I've tried.:(

Does anyone have any idea what the reason is for this?   Will the developers be informed just because I post here?:KS

If anyone suggests any scripting will they please explain how exactly I get the file up in the console in order to edit it?   I do not know how to do this but am willing to try.   Years ago with Basic one simply called a starting line number but now????

Tks

---

### Post by alexfish on 2010-07-21
can you post the results of the following from the terminal: connect the modem after boot then allow the device to settle, approx 30 seconds

code:
lsusb

code
ls -al /dev/serial/by-id/usb*

code:
dmesg | grep -e "modem" -e "tty" 

also which method where you using for the connection , did you install any sofware for the modem , if so which

---

### Post by JPman on 2010-07-21
First off I was wrong.   The USB Modem does not auto-mount.   When I select it where it appears on the "Places" menu I get a window:

"Unable to mount Vzacess Manager
 Dbus error org.gtk.private.remote volume monitor.failed
 Operation already pending"

Could this mean something like a "messy" disconnect from the first session?


The code returns are:

Bus003 dev006 id1410 5030 Novatel Wireless
Cannot access   No such file or dir
irq4 26550a i/o 0x3f8  

tks for the help

---

### Post by alexfish on 2010-07-21
according to to lsusb the device is in an unswitch state and therefore not recognised as a modem IE see below Ox1410 and Ox530

########################################################
# Novatel U760

DefaultVendor= 0x1410
DefaultProduct=0x5030

TargetVendor=  0x1410
TargetProduct= 0x6000

CheckSuccess=20

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"

when the device is correctly switched the device ID's would be Ox1410 and Ox6000

does any device appear on the desktop when it is inserted after boot, if so click on the device and try the eject command and see if there are any changes from the terminal commands mentioned above:

also have a look here, 
[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

maybe try the usb-modeswitch mention in the howto

not sure how the device worked on initial install then fail after update,but still waiting on info of which connection method you where using/ the info entered . and any modem software installed


regards

alexfish

---

### Post by JPman on 2010-07-21
I forgot to tell you that I installed no software but only plugged in the modem the first time when it worked.   In the modem config gui I only entered "#777".    That's all I had to do.

---

### Post by JPman on 2010-07-21
OK I'll check out the reference url.

I want to be clear about when it worked.   I first installed it on an IDE drive and it worked once and then not again.   Later I installed in on a SATA drive and same O.   It worked once only but not after re-boot just like the first time.   The updates I don't think had anything to do with it.

Hint...   I can tell when it is going to work because I left click on the NET icon on the top bar and I then get a drop menu which has "mobile bb" on it.   After re=boots this menu never appears again the same way.   Subsequent menu is smaller without the Mobile BB selection.

Sigh

---

### Post by alexfish on 2010-07-21
thanks

I also note your on cdma ,at  the  howto thread you only need to follow the parts on how to get the device to be recognised as a modem 

post back here if you hit snags

regards

alexfish

---

### Post by JPman on 2010-07-22
OK that gives me some stuff to follow up with.

I'll let you know what happens.    I'm not too worried about it as it did work and quite well so this is just a small glitch compared to "if it never worked at all".

tks:KS

JPS

---

### Post by JPman on 2010-07-22
:D    It works...

I rebooted and then plugged in the modem.   After three minutes or so it auto mounted.  Seems kind of a long time doesn't it?   I then selected "Verison Modem" on the "places" menu and clicked "eject" as you suggested.   A moment or two later I was online again.  

If this is a coding glitch how would I make sure the right people read about it?

On the fresh install when it first worked it connected and dropped 3 or 4 times all by itself before settling down after which it stayed stable all day.   Now it still does that routine but I'm not complaining.

The next challenge is getting my 5 year old IBM thinkpad (T42) to connect.   When I achieve that I can zap XP out of that computer for good.

Thanks for the assist.:KS

JP

---

### Post by alexfish on 2010-07-22
hi

just the way your modem behaves ,it's not a coding hitch or a bug;

most of these devices have there windows drivers onboard . blame that

USB_ModeSwitch is (surprise!) a mode switching tool for controlling  "flip flop" (multiple device) USB gear.
Several new USB devices  (especially high-speed wireless WAN stuff, there seems to be a chipset  from Qualcomm offering that feature) have their MS Windows drivers  onboard; when plugged in for the first time they act like a flash  storage and start installing the driver from there.
After that (and  on every consecutive plugging) this driver switches the mode internally,  the storage device vanishes (in most cases), and a new device (like a  USB modem) shows up. The WWAN gear maker Option calls that feature  "ZeroCD (TM)".
As you may have guessed, hardly anything of  this is documented and Linux support by the better part of the makers is  non-existent.
On the good side, most of the known devices do work in  both modes with the available Linux drivers like "usb-storage" or  "option" (an optimized serial driver for high-speed modems).
That  leaves the problem of the mode switching from storage to modem or  whatever the thing is supposed to do.

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

: since your works by what you have done ; linux is now doing the rest

Enjoy

regards

alexfish

---

### Post by JPman on 2010-07-22
Last note.

On subsequent boot ups, with or without modem plugged in, it goes on line by itself and works as advertised.


Yes I am aware of the inclination of makers to stick to those two, MS and Apple, while paying little mind to Linux.   Also the great variety of new devices which seem to appear monthly without end would seem to overwhelm Linux because of this lack of attention.   But Linux seems to overcome in the end.   

The only thing I miss about windows is that pinball game (Space Cadet Table) but I found it as a .zip so I'll Wine it in...

Heaven.

Tks

---

