---
title: "Dial Up problem"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by hok00age on 2010-05-22
I have USB CDMA Modem with "flip flop" mode (USB CDROM and USB CDMA Modem).
Here the method I use to connect:
1. Plug device
2. run eject /dev/srx (x is number of my USB CDROM usually /dev/sr1)
3. run sudo modprobe usbserial vendor=<my USB CDMA vendorid> product=<my USB CDMA productid>
4. run sudo wvdial or sudo pon
It works, but sometimes (or often) wvdial or pon disconnected suddenly, then I can't redial because my modem is no longer exist. To solve this problem, I must reboot my computer or unplug the device, plug it again and run the method that was mentioned above.
Question:
**Is there any command to "re-detect" my device instead of reboot or "re-plug", may be by restarting kernel module that control USB device?**
Any suggestions will be appreciated
Sorry for my bad English. I'm Indonesian.

---

### Post by alexfish on 2010-05-22
Hi

you can try this

Open /etc/modules by

Code:

gksudo gedit /etc/modules

and add the string


usbserial vendor=<my USB CDMA vendorid> product=<my USB CDMA productid>

Save and exit

But not sure if this would solve the problem , but should no longer have to modprobe every time the device is plugged in

can you have a look at the log files to see if there are any reason for the disconnection

or to monitor what is happening in real time from the terminal

Code:

tail -f /var/log/syslog

regards

alexfish

---

### Post by hok00age on 2010-05-22
> **alexfish said:**
> Hi

you can try this

Open /etc/modules by

Code:

gksudo gedit /etc/modules

and add the string


usbserial vendor=<my USB CDMA vendorid> product=<my USB CDMA productid>

Save and exit

But not sure if this would solve the problem , but should no longer have to modprobe every time the device is plugged in

can you have a look at the log files to see if there are any reason for the disconnection

or to monitor what is happening in real time from the terminal

Code:

tail -f /var/log/syslog

regards

alexfish

No luck.
Thank's for the reply but remember that my USB device is flip flop mode, and it won't be in CDMA mode until eject /dev/sr1 command executed, I meant that when I plugged my device it was in USB CDROM mode and then I executed eject /dev/sr1 command to have it in USB CDMA mode, but I can't get it back to USB CDROM mode except I must reboot or re-plug it. Is there any command instead of rebooting and re-plugging to get my device back to USB CDROM mode?

---

### Post by hok00age on 2010-05-23
No suggestions?? :(

---

### Post by alexfish on 2010-05-23
[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

regards

alexfish

---

### Post by hok00age on 2010-05-23
> **alexfish said:**
> [How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

regards

alexfish

Not works

I have no problem but getting my USB CDMA back to USB CDROM without replugging or rebooting. I want to create some automation script if my connection is down, I can reconnect with the script, of course without human interference. usb_modeswitch -R doesn't work.
Please guys **how to get my USB CDMA back to USB CDROM via command line**?
Sorry for my bad English.

---

### Post by alexfish on 2010-05-23
Hi

look at man eject

Code:

man eject

---

### Post by hok00age on 2010-05-24
> **alexfish said:**
> Hi

look at man eject

Code:

man eject

Thank's for replying

But, eject command is for storage (in my case usb-storage) -- correct me if I'm wrong--. And I used it to change USB CDROM mode to USB CDMA mode. My question is how to get my device back to USB CD ROM mode?

A brief explanation:
1. Plug the device (detected as USB CDROM)
2. run eject /dev/sr1
3. Get USB CDMA mode

Well, how to get it back to USB CDROM when it was in USB CDMA mode without replugging or rebooting?

Sorry for my bad English

---

### Post by alexfish on 2010-05-24
Hi

Observe and read the Man page relative 

AUTHOR
       Eject was written by Jeff Tranter (tranter@pobox.com) and  is  released
       under  the  conditions  of the GNU General Public License. See the file
       COPYING and notes in the source code for details.

       The    -x    option    was     added     by     Nobuyuki     Tsuchimura
       (tutimura@nn.iij4u.or.jp),   with   thanks  to  Roland  Krivanek  (kri&#8208;
       [EMAIL="vanek@fmph.uniba.sk"]vanek@fmph.uniba.sk[/EMAIL]) and his cdrom_speed command.

       The -T option was added by Sybren Stuvel (sybren@thirdtower.com),  with
       big thanks to Benjamin Schwenk (benjaminschwenk@yahoo.de).

       The -X option was added by Eric Piel (Eric.Piel@tremplin-utc.net).

[COLOR=Blue]**SEE ALSO**[/COLOR]
      [B] [COLOR=Blue]mount(2), umount(2), mount(8 ) , umount(8 )
       /usr/src/linux/Documentation/cdrom/[/COLOR][/B]

---

### Post by hok00age on 2010-05-24
I've read the man page and tried after your third post but it doesn't work. I'm n00b here bro, so if you know something please let me know.
Below is the output of My CDMA modem using lsusb command (probed as USB serial):

```
Bus 005 Device 002: ID 1d09:4306 TechFaith Wireless Technology Limited 
```

I've tried
```
usb_modeswitch -R
```
to reset into storage mode but not works.
Thank's

---

### Post by alexfish on 2010-05-24
hi

is this model externally powered 

also some techfaiths have specific AT commands , did a post where the only solution was to switch it off and then back on , may be the best solution would be to ask your ISP which AT commands are used to disable the cdrom feature , or a set of init codes specific to the model  also from data sheets some models have a GPIO  to hold the power on . + possibly others , look at the GPIO value or may have to write a GPIO value ,
Most modem have a register for error reporting , so maybe look at this side of things as well , best done from a serial terminal.

---

### Post by hok00age on 2010-05-25
It's internally powered.

You're right, it doesn't work with default wvdial.conf provided via "sudo wvdialconf". I must do some trick to get it works, fortunately I'm done with this. My big problem is wvdial (or pppd) often terminated suddenly with error code = 16. When wvdial try to redial, it gives me error:
"/dev/ttyUSB0: no such file or directory" or something like that.

The only solution now is re-plugging the device to get it works back.

I think, there is a command to solve my problem without human interference (I meant re-plugging), because I want create some automation scripts if wvdial (or pppd) terminated.
The last method I've tried was:
```
usb_modeswitch -d -R -v 1d09 -p 4306
```
but there was no luck.

Anyway thank's for your answer mate. Hope you can help me solve my problem.

---

### Post by alexfish on 2010-05-25
looks like the wrong entry for the modem

to find the ports been used from the terminal

Code:

dmesg | grep -e "modem" -e "tty" 

then make an entry in the "wvdial.conf file"

like

[FONT=monospace][FONT=monospace]Modem = /dev/tty[FONT=Verdana]XXXn     replace  "XXXn according[/FONT][/FONT][/FONT] to the output

one other to mention ,if  error code 16 is coming from the modem, may indicate wrong password , but try the setting on the tty ports first. then try wvdial from root ,sudo wvdial .if you got problem running not in root then you have permission problem with dialout and dip

also try to keep the modem connected  the same port , if you have a front plane , ie on a desk top ,use those

---

### Post by foresthill on 2010-05-25
I have been using Network Manager in 10.4 Lucid to connect with my USB broadband modem (Cricket A600) and having the same problem with getting disconnected and then not being able to reconnect unless I reboot or unplug the modem and plug it back in. Often unplugging the modem still won't work.

So I am having the same problem. What I did was install KPPP and have been using that to connect. No problems so far, but I have only been using it for a few hours.

I can hang up and reconnect, which is something I was not able to do before, since the connection would always die while trying to reconnect.

So you might try using KPPP and see what happens, but I'm at a loss as to why this seems to be happening, and I'm surprised that no one else has mentioned it.


I had all but switched back to 9.10, since this does not happen there. Good luck and keep us posted.

EDIT: Just had my connection drop off after about 3 hours online. KPPP froze, but I restarted another instance of the program and was able to reconnect. Not really the most elegant solution, but it beats rebooting.

---

### Post by hok00age on 2010-05-28
> **alexfish said:**
> looks like the wrong entry for the modem

to find the ports been used from the terminal

Code:

dmesg | grep -e "modem" -e "tty" 

then make an entry in the "wvdial.conf file"

like

[FONT=monospace][FONT=monospace]Modem = /dev/tty[FONT=Verdana]XXXn     replace  "XXXn according[/FONT][/FONT][/FONT] to the output

one other to mention ,if  error code 16 is coming from the modem, may indicate wrong password , but try the setting on the tty ports first. then try wvdial from root ,sudo wvdial .if you got problem running not in root then you have permission problem with dialout and dip

also try to keep the modem connected  the same port , if you have a front plane , ie on a desk top ,use those

I think it's not about wrong port in wvdial mate.
/dev/ttyUSB0 is the correct port on the FIRST execution of 'sudo wvdial' but when connection terminated and wvdial attempted to redial (I call this SECOND execution of wvdial) it said that /dev/ttyUSB0 does'nt exist. So, I must replug or reboot the machine to get wvdial works again with /dev/ttyUSB0.

---

### Post by hok00age on 2010-05-28
> **foresthill said:**
> I have been using Network Manager in 10.4 Lucid to connect with my USB broadband modem (Cricket A600) and having the same problem with getting disconnected and then not being able to reconnect unless I reboot or unplug the modem and plug it back in. Often unplugging the modem still won't work.

So I am having the same problem. What I did was install KPPP and have been using that to connect. No problems so far, but I have only been using it for a few hours.

I can hang up and reconnect, which is something I was not able to do before, since the connection would always die while trying to reconnect.

So you might try using KPPP and see what happens, but I'm at a loss as to why this seems to be happening, and I'm surprised that no one else has mentioned it.


I had all but switched back to 9.10, since this does not happen there. Good luck and keep us posted.

EDIT: Just had my connection drop off after about 3 hours online. KPPP froze, but I restarted another instance of the program and was able to reconnect. Not really the most elegant solution, but it beats rebooting.

KPPP is one of KDE apps, isn't it?

Is there any GNOME alternative to do what KPPP does?

I've been using pon, it's more 'stable' (I mean longer connection duration) than wvdial. Pon can hold my connection almost 4 hours but wvdial only 30 minutes. But 4 hours is not enough for me because I use my machine up to 20 hours per day, and it's quite annoying if I must reboot my machine several times a day in order to get my USB CDMA works.

---

### Post by alexfish on 2010-05-28
> **hok00age said:**
> I think it's not about wrong port in wvdial mate.
/dev/ttyUSB0 is the correct port on the FIRST execution of 'sudo wvdial' but when connection terminated and wvdial attempted to redial (I call this SECOND execution of wvdial) it said that /dev/ttyUSB0 does'nt exist. So, I must replug or reboot the machine to get wvdial works again with /dev/ttyUSB0.


Hi 

Ca you have a look at the ppp options


sudo egrep -v '#|^ *$' /etc/ppp/options

asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30 <============== try setting to 0
lcp-echo-failure 4 <================ try setting to 0
replacedefaultroute
noipx

To Change:

sudo gedit /etc/ppp/options

lcp-echo-failure 0
lcp-echo-interval 0
-vj <================ try uncommenting

also this error could be caused by:

    *  Bad hardware implementation of modem or USB controller, or
    * Bugs in device EEPROM, or
    * An unknown/undocumented AT command is required to prevent device from enterring its propretiary "power saving" mode.ref Sakis3g :{if the modem has two control ports there may be a way around this.}
  or find out the init code required , also which type of device is it
      

regards

alexfish

---

### Post by hok00age on 2010-05-28
I'll give it a try.

Thank's mate!

---

### Post by hok00age on 2010-05-29
> **alexfish said:**
> Hi 

Ca you have a look at the ppp options


sudo egrep -v '#|^ *$' /etc/ppp/options

asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30 <============== try setting to 0
lcp-echo-failure 4 <================ try setting to 0
replacedefaultroute
noipx

To Change:

sudo gedit /etc/ppp/options

lcp-echo-failure 0
lcp-echo-interval 0
-vj <================ try uncommenting

also this error could be caused by:

    *  Bad hardware implementation of modem or USB controller, or
    * Bugs in device EEPROM, or
    * An unknown/undocumented AT command is required to prevent device from enterring its propretiary "power saving" mode.ref Sakis3g :{if the modem has two control ports there may be a way around this.}
  or find out the init code required , also which type of device is it
      

regards

alexfish

I've tried, unfortunately it doesn't work, problem still occurs. No significant differences. :(

---

### Post by alexfish on 2010-05-29
hi

been back through your posts

 the problems with this device {from Techfaith seem to be generic } it is not the first post about this .I have tried to look up specific AT commands for their devices to no avail, if the device works in windows with no problem for more than the 3-4 Hrs then there has to be an AT command been sent to the device to keep it awake , or something in the ppp options to keep the connection live.

From what we see so far is wvdial and ppp give you the best results

try going through the ppp options one by one to see if they have any effect { read the details to see what they do , you may spot something which may be relevant} , first thing is reverse the changes I suggested , then start afresh , Then get in touch with techfaith or your ISP and see if they can provide a list of specific at commands for the device , technical departments are the people you need to talk to ,consumer help ,are in general terms.No Help.

for now You have achieved longer connection times than some post I have seen.

techfaith and qualcom have links , so i could suggest going back to the How to previously mentioned ,There is now a link to a pdf file for CDMA AT commands

in it are certain references to Qualcom secific At commands

regards

alexfish

---

### Post by hok00age on 2010-05-29
> **alexfish said:**
> hi

been back through your posts

 the problems with this device {from Techfaith seem to be generic } it is not the first post about this .I have tried to look up specific AT commands for their devices to no avail, if the device works in windows with no problem for more than the 3-4 Hrs then there has to be an AT command been sent to the device to keep it awake , or something in the ppp options to keep the connection live.

From what we see so far is wvdial and ppp give you the best results

try going through the ppp options one by one to see if they have any effect { read the details to see what they do , you may spot something which may be relevant} , first thing is reverse the changes I suggested , then start afresh , Then get in touch with techfaith or your ISP and see if they can provide a list of specific at commands for the device , technical departments are the people you need to talk to ,consumer help ,are in general terms.No Help.

for now You have achieved longer connection times than some post I have seen.

techfaith and qualcom have links , so i could suggest going back to the How to previously mentioned ,There is now a link to a pdf file for CDMA AT commands

in it are certain references to Qualcom secific At commands

regards

alexfish

Is there any "ndiswrapper" like apps that can be used for My USB CDMA?

As we all know, there is ndiswrapper to use Windows wireless card driver in Linux, I think that will be nice if we have same tools for CDMA modem.

---

