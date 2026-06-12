---
title: "How-to: Install modem ZTE MF626 HSDPA in Jaunty"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by Unkuiri on 2009-05-03
1) Get the latest usb_modeswitch file from the page [http://www.draisberghof.de/usb_modeswitch/]("http://www.draisberghof.de/usb_modeswitch/") from the section "Downloads"

2) click with the right button of the mouse in the file and select extract here;

3) Open the Terminal, and go to the location of the decompressed file and execute: > sudo make install... it asks for the root password;

[IMG]http://i586.photobucket.com/albums/ss304/LB-MaN/1.jpg[/IMG]


4) Edit the "usb_modeswitch.conf" archive. To do that execute:
> sudo gedit /etc/usb_modeswitch.conf
 it will open the Gnome text editor.

5) Look for the modem name:"ZTE MF626" and erase the comments, the ( # ) and the ( ; ), Until it looks something like this:

ZTE MF628+ (tested version from Telia / Sweden)
ZTE MF626

Contributor: Joakim Wennergren

DefaultVendor= 0x19d2
DefaultProduct= 0x2000

TargetVendor= 0x19d2
TargetProduct= 0x0031

MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"

[IMG]http://i586.photobucket.com/albums/ss304/LB-MaN/2.jpg[/IMG]

6) Save and Quit.

7) Plug the modem, wait few seconds and execute "lsusb" in the terminal. Here one device must have the ID 19d2:2000.

[IMG]http://i586.photobucket.com/albums/ss304/LB-MaN/3.jpg[/IMG]

8) Execute this in Terminal: 
> sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf
With this we change the usb mode so the system recognize it as a modem. Do "lsusb" again, it has changed to ID 19d2:0031

[IMG]http://i586.photobucket.com/albums/ss304/LB-MaN/4.jpg[/IMG]

10) Now it should be recognized as a modem...and we can define an archive in order to make this device recognizable by Network Manager, for this we write in terminal:
> sudo gedit /usr/share/hal/fdi/information/20thirdparty/20-zte-mf626.fdi 
This will open a blank archive and in it we write:
> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device>
<!-- ZTE MF626 HSDPA USB Modem -->
<match key="@info.parent:usb.vendor_id" int="0x19d2">
<match key="@info.parent:usb.product_id" int="0x0031">
<match key="@info.parent:usb.interface.number" int="3">
<append key="modem.command_sets" type="strlist">GSM-07.07</append>
<append key="modem.command_sets" type="strlist">GSM-07.05</append>
<append key="info.capabilities" type="strlist">modem</append>
</match>
</match>
</match>
</device>
</deviceinfo>

Then Save and Quit

11) Now it should be seen in network connections as a new connection.

In the original page in spanish [http://www.taringa.net/posts/linux/2318037/Configurar-internet-en-Ubuntu-modem-ZTE-mf626.html]("http://www.taringa.net/posts/linux/2318037/Configurar-internet-en-Ubuntu-modem-ZTE-mf626.html") by MOZZart, it has other commands that for this ubuntu release I found unnecessary.

In my country and provider it's necessary to do some configuration in the network manager.
I have to do Edit Conections -> (in english could be something like) Mobile Broadband -> Add...and than select the mobile provider...

Reboot and than it will maybe (:P) work fine...
any corrections and suggestions are welcome...

P.S.:I still don't find a way to automatize all the process, anytime I want to enter the internet I have to do: "sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf"...anyone that knows a way I'll appreciate...:)

---

### Post by loell on 2009-05-03
And this is is in jaunty!? i'm only asking because, many have troubles using usb_modeswitch in jaunty.

---

### Post by Unkuiri on 2009-05-03
Yeah, it worked for me in Jaunty...I tried many tutorials but the only one that worked is this one...

P.S.::confused: I'm a newby in Ubuntu, maybe i'm making something wrong, if it happens please forgive me...

---

### Post by loell on 2009-05-03
ah great :), i was only asking because some have this error

[https://answers.launchpad.net/ubuntu/+source/linux/+question/65281](https://answers.launchpad.net/ubuntu/+source/linux/+question/65281)

but if it went just fine, then that's goog news :)

---

### Post by Unkuiri on 2009-05-03
I had that same error, as I know the usbserial module doesn't work on Jaunty and because of that I did a thing that a user said in other forum, I've edited the file "menu.lst" located in /boot/grub/ and added a line customized entry, copied the part that says:
> title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8a94291a-08f2-40dc-ac28-240589d74efc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8a94291a-08f2-40dc-ac28-240589d74efc ro locale=pt_PT quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
and altered the new one to look like this:
> title		Ubuntu 9.04, kernel 2.6.28-11-generic custom
uuid		8a94291a-08f2-40dc-ac28-240589d74efc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8a94291a-08f2-40dc-ac28-240589d74efc ro locale=pt_PT quiet splash usbserial.vendor=0x19d2 usbserial.product=0x0031
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
I've altered the first line adding "custom"(this is only to know what boot option is)
and added: "usbserial.vendor=0x19d2 usbserial.product=0x0031" (this is for my case, for the modem cited at the top)

and then I booted from that new option...but when I tried to plug the modem and make it work it didn't work and then I tried again to boot normally from the normal option (not custom) and voilá it's working...Thats the reason I didn't say it in the "How-to"...do you think it's important to say that?:P

---

### Post by loell on 2009-05-03
> **Unkuiri said:**
> Thats the reason I didn't say it in the "How-to"...do you think it's important to say that?:P

yeah.. but you already just said it, so it's fine. :)

---

### Post by GeorgeVita on 2009-05-04
> **Unkuiri said:**
> ...P.S.:I still don't find a way to automatize all the process, anytime I want to enter the internet I have to do: "sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf"...anyone that knows a way I'll appreciate...:)

Hi **Unkuiri**,
if above still exists, you can add a .rule file (as user **JimmyI** suggests with post #4 of [http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934)).

For your case you could create the file from terminal:
**sudo gedit /etc/udev/rules.d/90-zte.rules**

copy the following lines into gedit window:

```


ACTION!="add", GOTO="ZTE_End"

SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"

LABEL="ZTE_ZeroCD"
RUN+="/usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf"

LABEL="ZTE_End"

```

Save, Exit and reboot.

If all are OK, when you attach the modem (19d2:2000) the usb_modeswitch will run automatically changing to "modem state" (19d2:0031). As you are running the usbserial at boot, you don't need the "usbserial" part of above link.

Regards,
George

---

### Post by radolin on 2009-05-12
Hi guys,

I just want to ask those of you that have succeeded in getting the modem to work are you happy with it?

I read somewhere else that people are experiencing modem hangs after ~1hr of use, so do you get these too or it works reliably?

I am looking for a 3g modem to buy with Linux support #1 criteria on the list so this will be useful info.

Best regards,
Rado

---

### Post by Unkuiri on 2009-05-12
Hi, For me works fine the only problem that I'm experiencing sometimes is that I have to unplug and re-plug for it to work, but all the remaining things work fine and is faster than windows for example...:)...good luck for your search...

---

### Post by Unkuiri on 2009-05-12
Thanks GeorgeVita, What you said worked just fine...:)...now it's just plug and play...:P..

---

### Post by scr3wdriv3r on 2009-05-19
Thanks Unkuiri, you save me! Can i send you a postcard of my city in Brazil?

But i need one more thing: A way to the modem be detected in the boot, for use in remote gateways with ubuntu server and wvdial. If i leave the modem plugged in usb and shutdown, when i power-on the pc, the modem stills 19d2:2000, and the udev rules not works.

Any idea are welcome!

ps.: sorry for my poor english

---

### Post by Unkuiri on 2009-05-21
Hi scr3wdriv3r I'm a newbie, it wasn't me that have done such a great tutorial, I just traduced one from spanish to english, but if you want to send me a postcard anyway I'll appreciate and even send one to you from mine, want me to private you my adress?...:P
For your problem, as the little I know...I don't think that there is any solution that works all the times...:(...the modem isn't fully integrated in ubuntu and in my computer sometimes, it is difficult for it to work right away, I have to unplug and replug the modem for it to work...
The best I got is the tip from GeorgeVita that automates the process and when I plug it changes the usb mode automatically...

---

### Post by Unkuiri on 2009-05-21
I have an idea!!...:P...
Why don't you try to execute usbmodeswitch as a startup program?
Try to do this:
go to startup applications and add a new application with this command:
**sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf**
then you just need to type the password and it should work...with luck..:P
let me know if this worked...

---

### Post by scr3wdriv3r on 2009-05-27
Thanks, but i already tried your idea...  The modem hang in the boot process and the usb_modeswitch not works properly, giving me an error 110.

And yes, you can MP me to send your address!

Again, sorry my poor english

[]'s

scr3wdriv3r

---

### Post by websquare on 2009-06-02
Hi!

I tried to install my mf626 as you describe and everything seemed to work fine. Network Manager detected it and displayed the configuration dialog for a new connection.
However, when I try to connect it fails every time. It tries to connect but then displays that it is not connected.
Syslog shows the following:
```
May 28 20:07:55 ntb-stefan NetworkManager: <info>  Activation (ttyUSB4) starting connection 'Yesss' 
May 28 20:07:55 ntb-stefan NetworkManager: <info>  (ttyUSB4): device state change: 3 -> 4 
May 28 20:07:55 ntb-stefan NetworkManager: <info>  Activation (ttyUSB4) Stage 1 of 5 (Device Prepare) scheduled... 
May 28 20:07:55 ntb-stefan NetworkManager: <info>  Activation (ttyUSB4) Stage 1 of 5 (Device Prepare) started... 
May 28 20:07:55 ntb-stefan NetworkManager: <debug> [1243534075.629571] nm_serial_device_open(): (ttyUSB4) opening device... 
May 28 20:07:55 ntb-stefan NetworkManager: <info>  Activation (ttyUSB4) Stage 1 of 5 (Device Prepare) complete. 
May 28 20:07:55 ntb-stefan NetworkManager: <WARN>  init_done(): Trying alternate modem initialization (1) 
May 28 20:07:57 ntb-stefan NetworkManager: <WARN>  init_done(): Trying alternate modem initialization (2) 
May 28 20:07:58 ntb-stefan NetworkManager: <WARN>  init_done(): Trying alternate modem initialization (3) 
May 28 20:07:59 ntb-stefan NetworkManager: <WARN>  init_done(): Trying alternate modem initialization (4) 
May 28 20:08:00 ntb-stefan NetworkManager: <info>  (ttyUSB4): GSM pin secret required 
May 28 20:08:00 ntb-stefan NetworkManager: <info>  (ttyUSB4): device state change: 4 -> 6 
May 28 20:08:00 ntb-stefan NetworkManager: <info>  Activation (ttyUSB4) Stage 1 of 5 (Device Prepare) scheduled... 
May 28 20:08:00 ntb-stefan NetworkManager: <info>  Activation (ttyUSB4) Stage 1 of 5 (Device Prepare) started... 
May 28 20:08:00 ntb-stefan NetworkManager: <info>  (ttyUSB4): device state change: 6 -> 4 
May 28 20:08:00 ntb-stefan NetworkManager: <debug> [1243534080.049473] nm_serial_device_open(): (ttyUSB4) opening device... 
May 28 20:08:00 ntb-stefan NetworkManager: <info>  Activation (ttyUSB4) Stage 1 of 5 (Device Prepare) complete. 
May 28 20:08:00 ntb-stefan NetworkManager: <WARN>  init_done(): Trying alternate modem initialization (1) 
May 28 20:08:01 ntb-stefan NetworkManager: <WARN>  init_done(): Trying alternate modem initialization (2) 
May 28 20:08:02 ntb-stefan NetworkManager: <WARN>  init_done(): Trying alternate modem initialization (3) 
May 28 20:08:03 ntb-stefan NetworkManager: <WARN>  init_done(): Trying alternate modem initialization (4) 
May 28 20:08:04 ntb-stefan NetworkManager: <info>  (ttyUSB4): powering up... 
May 28 20:08:04 ntb-stefan NetworkManager: <info>  Searching for a network... 
May 28 20:08:14 ntb-stefan last message repeated 9 times
May 28 20:08:15 ntb-stefan NetworkManager: <info>  Registered on Home network 
May 28 20:08:15 ntb-stefan NetworkManager: <info>  Associated with network: +COPS: 0,0,"Orange Austria",2 
May 28 20:08:47 ntb-stefan NetworkManager: <WARN>  dial_done(): Dialing timed out 
May 28 20:08:47 ntb-stefan NetworkManager: <info>  (ttyUSB4): device state change: 4 -> 9 
May 28 20:08:47 ntb-stefan NetworkManager: <debug> [1243534127.011285] nm_serial_device_close(): Closing device 'ttyUSB4' 
May 28 20:08:47 ntb-stefan NetworkManager: <info>  Marking connection 'Yesss' invalid. 
May 28 20:08:47 ntb-stefan NetworkManager: <info>  Activation (ttyUSB4) failed. 
May 28 20:08:47 ntb-stefan NetworkManager: <info>  (ttyUSB4): device state change: 9 -> 3 
May 28 20:08:47 ntb-stefan NetworkManager: <info>  (ttyUSB4): deactivating device (reason: 0). 
May 28 20:08:47 ntb-stefan kernel: [ 6846.818917] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
May 28 20:08:47 ntb-stefan kernel: [ 6846.818949] option 1-3:1.0: device disconnected
May 28 20:08:47 ntb-stefan kernel: [ 6846.819292] option 1-3:1.1: device disconnected
May 28 20:08:47 ntb-stefan NetworkManager: <info>  Policy set 'GIULIANI' (wlan0) as default for routing and DNS. 
May 28 20:08:47 ntb-stefan kernel: [ 6846.819540] option1 ttyUSB5: GSM modem (1-port) converter now disconnected from ttyUSB5
May 28 20:08:47 ntb-stefan kernel: [ 6846.819591] option 1-3:1.3: device disconnected
May 28 20:08:47 ntb-stefan NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
May 28 20:08:47 ntb-stefan NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
May 28 20:08:47 ntb-stefan nm-system-settings:    SCPlugin-Ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/usb_device_19d2_31_noserial_if3_serial_usb_0)
May 28 20:08:47 ntb-stefan kernel: [ 6846.929147] usb 1-3: reset high speed USB device using ehci_hcd and address 22
May 28 20:09:02 ntb-stefan kernel: [ 6862.040158] usb 1-3: device descriptor read/64, error -110
```

Does anyone have an idea how to solve that problem?

Thanks,
Stefan

---

### Post by Unkuiri on 2009-06-02
> **scr3wdriv3r said:**
> Thanks, but i already tried your idea...  The modem hang in the boot process and the usb_modeswitch not works properly, giving me an error 110.

And yes, you can MP me to send your address!

Again, sorry my poor english

[]'s

scr3wdriv3r

I don't know what to say then..:(..All I can say is that, in all forums where I've seen information about this modem, it says that it is not fully supported in Ubuntu...I almost all times have to unplug and replug the modem for it to connect...but when it's connected it works relly fine...

Sorry that I can't help you more in this matter..:(

---

### Post by Unkuiri on 2009-06-02
websquare, Have you tryed to unplug an replug the modem, clicking with the left mouse button in the network icon and selecting the network you want to connect to?have you put the pin code in the options?

---

### Post by websquare on 2009-06-03
Yes, I tried to unplug and plug in again and when I tried to connect the first time it asked for the pin code.
Anyway, as the modem seems not to be supported very well I decided to return it and I am now looking for a Huawei E160. This should work better...
However, thank you for trying to help!

---

### Post by Azrael Nightwalker on 2009-06-20
My modem works great!
Even without creating /usr/share/hal/fdi/information/20thirdparty/20-zte-mf626.fdi 
I'm using Jaunty with latest updates.

---

### Post by stinger30au on 2009-07-02
thanks so much to poster #1 and #7

i had to do *EXACTLY* what was said in *BOTH* posts and now it works like a charm

i might also add as well to make the telstra pre paid wireless work in australia you need to add the connection that says 

Telstra (UTMS/HSDPA)

*BINGO*

thanks again

---

### Post by artmendez on 2009-07-07
Yours works without switching modes?
I've managed to make mine work once. It also appeared to mount and connect swiftly and transparently. But then, nothing... did the modeswitch and modeprobe... everything seems ok... it shows in network manager, but when it tries to connect, a "GSM Network - Disconnected" is shown in pop-up messaging (Ubuntu 9.04).

anyone knows if there's hope?

kind regards.

---

### Post by GeorgeVita on 2009-07-07
Hi **artmendez**,
as you have already connected once, try to repeat your steps. Delete every existing mobile broadband connection (from Network Manager icon), reboot without the modem, attach it, wait for the wizard and setup again.
Just to minimise conflicts turn off wireless and do not use ethernet.
Also search for any thread regarding your provider, in case they want a 'special' parameter (**APN**, user/password, IPv6 etc).

[COLOR="Blue"]EDIT: if more than one 'provider name' are shown on the Network Manager icon, try the last one to connect!
[/COLOR]
Regards,
George

---

### Post by philcart on 2009-07-20
Excuse the nooby-ness,

Everything goes fine until I get to the line,


 	 	 		 			 				> sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf 			 		

Where I get the message,
> sudo: unable to execute /usr/sbin/usb_modeswitch: No such file or directory

From what I can see, both files referenced in the command are there :confused::confused::confused:

Hope someone can help me get this working as I'd like to say goodbye to Vista and not be forced to upgrade to Win 7 to get some reasonable performance from my aging laptop.

Thanks
Phil

---

### Post by GeorgeVita on 2009-07-20
Hi **philcart**,
if your ubuntu version is 9.04 and you have an internet connection (other than your ZTE modem) to update it, you can try solution from:
post #1 [http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630)

Possibly will work without the use of usb-modeswitch.
> **jfernyhough said:**
> **Updated**
With Jaunty this is now not necessary and there is an easier way around. First, install udev-extras:

$ sudo aptitude install udev-extras

Now plug in your modem. It should mount as the ZeroCD device (1). Now right-click the icon on the desktop and eject. Wait a moment, and the light on the modem will go dark, then relight. It should now mount as a modem and be detected by Network Manager (2).

How easy was that?

A note should be made about udev-extras, though:YMMV.

1)lsusb:```
ID 19d2:2000 ONDA Communication S.p.A.
```
2)lsusb:```
ID 19d2:0031 ONDA Communication S.p.A.
```


Regards,
George

---

### Post by C-free on 2009-07-28
Thank you all for sharing your knowledge and insight!!! 

Running into little trouble, the issue is that the modem drops out after about an hour. Disappears. lsusb zombifies. Plug-unplug doesn't yield much result. 

Scenario A) Reboot, plugin, sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf - works

Up untill next time it hangs (about an hour) or reboot.

B) Tried George's solution:

sudo gedit /etc/udev/rules.d/90-zte.rules

copy the following lines into gedit window:

Code:

ACTION!="add", GOTO="ZTE_End"

SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"

LABEL="ZTE_ZeroCD"
RUN+="/usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf"

LABEL="ZTE_End"

This seems to majorly puzzle 4 processors, boot up takes 5-10 minutes. Had a message  

udevd [935]: GOTO 'ZTE_End has no matching label in: '/etc/udev/rules.d/90-zte.rules

Then cores are running @ 100% capacity for a while. 

Looking for an alternative solution to this situation if anyone came across. Thanks all!

---

### Post by GeorgeVita on 2009-07-28
Hi **C-free**, please try:```
lsusb
```after running usb_modeswitch mannually.

Also:```
cat /etc/udev/rules.d/90-zte.rules
```check it with the posted one and copy/paste it here.

> Looking for an alternative solution to this situation if anyone came across. Thanks all!With 9.04 an alternative could be the **updated** post#1 at:
[http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630)

Regards,
George

---

### Post by C-free on 2009-07-28
Usb Modeswitch – Manual

lsusb:

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 005: ID 19d2:0031  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 005 Device 003: ID 046d:c313 Logitech, Inc. 
Bus 005 Device 002: ID 046d:c040 Logitech, Inc. Corded Tilt-Whee 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

90-zte.rules cat command:

ACTION!="add", GOTO="ZTE_End" 

SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD" 

LABEL="ZTE_ZeroCD" 
RUN+="/usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf" 

Thank you.

---

### Post by GeorgeVita on 2009-07-28
> **C-free said:**
> ...
Bus 001 Device 005: ID **19d2:0031**
...

ACTION!="add", GOTO="ZTE_End" 

SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD" 

LABEL="ZTE_ZeroCD" 
RUN+="/usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf" 



From above, the last line is missing:

```
ACTION!="add", GOTO="ZTE_End"

SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"

LABEL="ZTE_ZeroCD"
RUN+="/usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf"

LABEL="ZTE_End"
```

USE COPY/PASTE from the above window to gedit window!

Above rule will just run the usb_modeswitch automatically. To connect successfully some other points needed but with 9.04 are complicated. Fix above and I am going to try my ZTE MF636 with 9.04 to follow up after some hours.

Regards,
George

---

### Post by C-free on 2009-07-28
George, thank you very much for pointing this out! Internet is ON. Back to modern society. Whoo-hoo!!

Few notes: 

- Time has increased threefold for BIOS to get to GRUB stage
- Device periodically kicks out. Which potentially might be due to local networks. After selection in Network Manager areas or plugin-out issue resolves.

---

### Post by GeorgeVita on 2009-07-28
Hi **C-free**,
ZTE 3G modems & Linux is still 'under construction' so we must be patient!
Many things are changing (udev, hal, network manager,...). You can have better and more stable connection with older methods as wvdial. Looking forward we test and try to report results hoping for a 'better' tomorrow!

Regards,
George

---

### Post by C-free on 2009-07-28
Thank you. On upside, Ubuntu still loads faster then XP and wireless broadband seems to work much faster then under Windowns.

*Thumbs up*

---

### Post by chepe263 on 2009-08-09
Tambien esta 
[http://ubuntuforums.org/showthread.php?t=1017630&highlight=zte+mf626](http://ubuntuforums.org/showthread.php?t=1017630&highlight=zte+mf626)

That is another way to do it

And

[http://ubuntuforums.org/showthread.php?t=1231021&highlight=zte+mf626](http://ubuntuforums.org/showthread.php?t=1231021&highlight=zte+mf626)
(Spanish only)

Just use the search!!

---

### Post by jamsh on 2009-08-11
I was recently given one of these T-Mobile dongles and have now got it to work after using the great stuff on this thread.
When I start up I have to delete T-Mobile from Network Manager, disable wireless network, plug in the dongle and use the wizard to set it up again and it works beautifully.
Must work out how to have it there on startup, but for now, a big thanks.
BTW, I got modeswitch  as a deb. [here]("http://packages.debian.org/search?keywords=usb-modeswitch").

---

### Post by imxuk on 2009-08-11
Hi,

I dont seem to be having much luck here, with a Orange UK 3G card - which is an MF636.

Following the details in the various threads to put it into modem mode, as opposed to storage, adding the hal/udev rules....im still not able to connect!

Its detected as USB4, ive modified the rules to take this into account - these all have id 3 set.  This is what the item is detected as in lsusb:

Bus 002 Device 016: ID 19d2:0033  

Using wvdial it appears to start to connect, but then just locks up.  Im unable to run another test without unplugging the device and reconnecting... This is what it just hangs on:

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internetvpn"
AT+CGDCONT=1,"IP","internetvpn"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Waiting for prompt.

Any ideas?!

Cheers,

iMxUK

---

### Post by GeorgeVita on 2009-08-11
Hi **imxuk**,
add an extra line to your /etc/wvdial.conf file:```
Stupid mode = Yes
```this will skip the 'waiting for prompt' message.

If you still cannot connect post ALL your /etc/wvdial.conf file to check.

Regards,
George

---

### Post by imxuk on 2009-08-12
Hi George,

Nice one, thank you for the reply - this certainly fixed my issue and i can now connect via wvdial.  Ive done the hacks posted in this forum, however it still wont show in NetworkManager....  Am running Jaunty.

Any ideas for NetworkManager?

Cheers,

Ed

---

### Post by imxuk on 2009-08-12
HAL doesnt seem to be notifying NetworkManager of the cards existence, have modified the HAL files to include the below:

usr/share/hal/fdi/information/10freedesktop/10-modem.fdi 

   <!-- ZTE MF636 HSDPA USB dongle -->
        <match key="@info.parent:usb.product_id" int="0x0033">
          <match key="@info.parent:usb.interface.number" int="4">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>

###

Bus 002 Device 003: ID 19d2:0033  

Device still doesnt show as a USB modem, or have any name..... ideas?

Thanks,

iMxUK

---

### Post by GeorgeVita on 2009-08-12
Hi again,
from 9.04 many changes affect 3G modems. I think that safer for now is to stay with **wvdial** or other terminal method.

If you still want to try, read:
[http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630) (updated post#1 **udev-extras)**

Regards,
George

---

### Post by imxuk on 2009-08-12
Hi George,

Thanks for the reply, however as previously noted ive already created my own HAL rules... including the installation of udev-extra.

Not using networkmanager is a pain for things like pidgin, openvpn etc etc.

Cheers,

Ed

---

### Post by imxuk on 2009-08-12
HAL see's it....NetworkManager just doesnt recognise it as a mobile broadband card.

Syslog below:

Aug 12 12:09:27 unknown-laptop kernel: [ 2023.108114] usb 2-1: new high speed USB device using ehci_hcd and address 10
Aug 12 12:09:27 unknown-laptop kernel: [ 2023.253828] usb 2-1: configuration #1 chosen from 1 choice
Aug 12 12:09:27 unknown-laptop kernel: [ 2023.257559] usbserial_generic 2-1:1.0: generic converter detected
Aug 12 12:09:27 unknown-laptop kernel: [ 2023.257681] usb 2-1: generic converter now attached to ttyUSB0
Aug 12 12:09:27 unknown-laptop kernel: [ 2023.488533] generic ttyUSB0: generic converter now disconnected from ttyUSB0
Aug 12 12:09:27 unknown-laptop kernel: [ 2023.488558] usbserial_generic 2-1:1.0: device disconnected
Aug 12 12:09:27 unknown-laptop kernel: [ 2023.597657] usb 2-1: USB disconnect, address 10
Aug 12 12:09:27 unknown-laptop usb_id[7425]: unable to access '/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/ttyUSB0/tty/ttyUSB0' 
Aug 12 12:09:33 unknown-laptop kernel: [ 2029.104141] usb 2-1: new high speed USB device using ehci_hcd and address 11
Aug 12 12:09:33 unknown-laptop kernel: [ 2029.251461] usb 2-1: configuration #1 chosen from 1 choice
Aug 12 12:09:33 unknown-laptop kernel: [ 2029.255273] usbserial_generic 2-1:1.0: generic converter detected
Aug 12 12:09:33 unknown-laptop kernel: [ 2029.255399] usb 2-1: generic converter now attached to ttyUSB0
Aug 12 12:09:33 unknown-laptop kernel: [ 2029.255589] usbserial_generic 2-1:1.1: generic converter detected
Aug 12 12:09:33 unknown-laptop kernel: [ 2029.255668] usb 2-1: generic converter now attached to ttyUSB1
Aug 12 12:09:33 unknown-laptop kernel: [ 2029.255842] usbserial_generic 2-1:1.2: generic converter detected
Aug 12 12:09:33 unknown-laptop kernel: [ 2029.255920] usb 2-1: generic converter now attached to ttyUSB2
Aug 12 12:09:33 unknown-laptop kernel: [ 2029.256097] usbserial_generic 2-1:1.3: generic converter detected
Aug 12 12:09:33 unknown-laptop kernel: [ 2029.256178] usb 2-1: generic converter now attached to ttyUSB3
Aug 12 12:09:33 unknown-laptop kernel: [ 2029.256347] usbserial_generic 2-1:1.4: generic converter detected
Aug 12 12:09:33 unknown-laptop kernel: [ 2029.256426] usb 2-1: generic converter now attached to ttyUSB4
Aug 12 12:09:33 unknown-laptop kernel: [ 2029.496607] generic ttyUSB0: generic converter now disconnected from ttyUSB0
Aug 12 12:09:33 unknown-laptop kernel: [ 2029.496665] usbserial_generic 2-1:1.0: device disconnected
Aug 12 12:09:33 unknown-laptop usb_id[7484]: unable to access '/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/ttyUSB0/tty/ttyUSB0' 
Aug 12 12:09:33 unknown-laptop NetworkManager: <info>  (ttyUSB1): ignoring due to lack of mobile broadband capabilties 
Aug 12 12:09:33 unknown-laptop NetworkManager: <info>  (ttyUSB3): ignoring due to lack of mobile broadband capabilties 
Aug 12 12:09:33 unknown-laptop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/usb_device_19d2_33_1234567890ABCDEF_if4_serial_usb_0_1, iface: (null)): iface not found
Aug 12 12:09:33 unknown-laptop NetworkManager: <info>  (ttyUSB4): found serial port (udev:  hal:GSM) 
Aug 12 12:09:33 unknown-laptop NetworkManager: <info>  (ttyUSB4): ignoring due to lack of probed mobile broadband capabilties 
Aug 12 12:09:33 unknown-laptop NetworkManager: <info>  (ttyUSB2): ignoring due to lack of mobile broadband capabilties

---

### Post by imxuk on 2009-08-12
For some reason...not quite sure why... but if i change the 'int' in the HAL rule to 2 (even though im using USB4 with wvdial) NetworkManager finds it fine...

        <!-- ZTE MF636 HSDPA USB dongle -->
        <match key="@info.parent:usb.product_id" int="0x0033">
          <match key="@info.parent:usb.interface.number" int="2">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>

##

You can debug any issues by querying the card as follows:

$ /lib/udev/nm-modem-probe --verbose --export /dev/ttyUSB#

i just ran through my USB devices from 1-4, until i found one that reported GSM as per the below:

/lib/udev/nm-modem-probe --verbose --export /dev/ttyUSB2
L: main(): (/dev/ttyUSB2): usb-vid 0x0000  usb-pid 0x0000  usb-intf 0  driver '(null)'
L: main(): probing /dev/ttyUSB2
L: modem_send_command(): Sending: 'AT+GCAP
'
L: modem_wait_reply(): Got: '
+ZDONR: "Not Found"

+ZPASR: "Limited Service"

+ZDONR: "Not Found"

+ZPASR: "Limited Service"

+ZDONR: "Orange",234,33,"CS_ONLY","ROAM_OFF"

+ZPASR: "GSM"

+ZDONR: "Orange",234,33,"CS_PS","ROAM_OFF"

+ZPASR: "GPRS"

+ZDONR: "Orange",234,33,"CS_PS","ROAM_OFF"

+ZPASR: "GPRS"

+ZDONR: "Orange",234,33,"CS_PS","ROAM_OFF"

+ZPASR: "UMTS"
'
L: modem_wait_reply(): Got: '
+ZDONR: "Not Found"

+ZPASR: "Limited Service"

+ZDONR: "Not Found"

+ZPASR: "Limited Service"

+ZDONR: "Orange",234,33,"CS_ONLY","ROAM_OFF"

+ZPASR: "GSM"

+ZDONR: "Orange",234,33,"CS_PS","ROAM_OFF"

+ZPASR: "GPRS"

+ZDONR: "Orange",234,33,"CS_PS","ROAM_OFF"

+ZPASR: "GPRS"

+ZDONR: "Orange",234,33,"CS_PS","ROAM_OFF"

+ZPASR: "UMTS"

+GCAP: +CGSM,+DS,+ES

OK
'
L: modem_probe_caps(): GCAP response: +GCAP: +CGSM,+DS,+ES
ID_NM_MODEM_GSM=1
ID_NM_MODEM_PROBED=1
L: main(): /dev/ttyUSB2: caps (0x19) GSM

---

### Post by GeorgeVita on 2009-08-12
This is fine now!
Can you describe in brief your actions, giving a h/w description also?

Ex. Uuntu 9.04, ZTE MF636 (or 636+) from provider Orange UK, initial lsusb = 19d2:2000, udev-extras installed, real modem = 19d2:0033 (!), changes to ...

... to become a one post solution for others with the same h/w!

Regards,
George

---

### Post by grozni on 2009-08-12
I have ZTE MF622. I've managed to get it working only when I plug it in before powering up Jaunty. I thought that I configured usb switch correctly, but in case I plug it in when Jaunty is running, and later trying usb switch here is what I receive


 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: /etc/usb_modeswitch.conf
DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0002
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint=0x04
MessageContent="55534243f8f993882000000080000a85010101180101010101000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 002
usb_os_find_busses: Found 007
usb_os_find_busses: Found 006
usb_os_find_busses: Found 005
usb_os_find_busses: Found 001
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 001 on 007
usb_os_find_devices: Found 005 on 006
usb_os_find_devices: Found 001 on 006
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 002 on 005
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 005
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 002 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 005 on bus 006 ...
Using endpoints 0x04 (out) and 0x84 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
USB error: could not get bound driver: No data available
 No driver found. Either detached before or never attached
USB error: error submitting URB: No such file or directory
 Could not send INQUIRY message (error -2)

Device description data (identification)
-------------------------
Manufacturer: Qualcomm, Incorporated
     Product: USB ZTE Storage
  Serial No.: not provided
-------------------------
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x04 ...
USB error: error submitting URB: No such file or directory
 Sending the message returned error -2. Trying to continue
USB error: could not clear/halt ep 4: No such file or directory
Device is gone, skipping further steps ...
-> Run lsusb to note any changes. Bye.



lsusb shows:


Bus 006 Device 005: ID 19d2:2000



Here is the output of .rules that I've created for MF622


ACTION!="add", GOTO="ZTE_End"

# Is this the ZeroCD device?
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000",
SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"

# Is this the actual modem?
SUBSYSTEM=="usb", SYSFS{idProduct}=="0001",
SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"

LABEL="ZTE_ZeroCD"
# This is the ZeroCD part of the card, remove
# the usb_storage kernel module so
# it does not get treated like a storage device
RUN+="/usr/src/usb_modeswitch-0.9.2/usb_modeswitch -d 1 -v 0x19d2 -p 0x2000 -V 0x19d2 -P 0x0001"

LABEL="ZTE_Modem"
# This is the Modem part of the card, let's
# load usbserial with the correct vendor
# and product ID's so we get our usb serial devices
RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0001",
# Make users belonging to the dialout group
# able to use the usb serial devices.
SUBSYSTEM=="usb", SYSFS{idProduct}=="0001", SYSFS{idVendor}=="19d2", MODE="660", GROUP="dialout"

LABEL="ZTE_End"



I just noticed that every line that containts +RUN is not good. I will change that part as soon as I figure out why usb switch is not working. 



I've attached usb switch config file. Help anyone?

---

### Post by grozni on 2009-08-12
I've managed to get this working. I've removed line that states MessageEndpoint, so config looks like this

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0002

;MessageEndpoint=0x04
MessageContent="55534243f8f993882000000080000a85010101180101010101000000000000"


Also I got this working under Network Manager, I just can't recall how I did it because I've tried many different combinations. I've attached .rules file

---

### Post by SuckerBlood on 2009-08-16
Hi!, I use Ubuntu Jaunty (eeebuntu 3 but is the same) in my Asus eeePC 901.

I bought an ZTE MF626 modem (with yoigo -Spain-) and it works correctly in Windows. In my netbook it works (I connect now) but I have some problems when i try to connect it.

My problem is when I plug the usb modem (with the above instructions) it detects, etc.. etc..

BUT, when I click in "yoigo" (the name of the modem network) the modem doesn't **usually** connected. I need try, try and try until it connects. Sometimes I should even replug the usb modem.

Somebody has the same problem? This has solution?


PS: Sorry for my English...

---

### Post by Carmen0669 on 2009-08-26
Please help!!! I am new in this, I am trying to install de ZTE modem, I tried the procedure you mentioned before but nothig happens. When I type sudo make install, the error " sudo: make: command not found"
 
I am using the version that came with Acer Spireone

---

### Post by GeorgeVita on 2009-08-27
Hi **SuckerBlood**, your problem could be caused by low/no 3G signal. Can you check if the status led color is 'blue' before trying to connect? Are you connecting via Network Manager?

Hi **Carmen0669**, please supply more technical info from some basic tests:
Boot without mode, **wait** for the system to load, attach it, **wait** 15 seconds, open a terminal window and try:```
dmesg
``````
lsusb
``` Copy/paste here the _last 15 lines_ of dmesg regarding modem/driver/ttyUSBx and the output of lsusb.

As this is a 'long' thread, which are the specific actions/tests you have done?

Regards,
George

---

### Post by SuckerBlood on 2009-09-12
GeorgeVita, I don't think that is problem of the 3G connection. I try the same in other laptop and it works correctly and 'correct' velocity (+- velocity when in Ubuntu it connects).

My problem is in the connection :( because i need to retry and retry and retry until it connects (sometimes the modem seems "busy" (at the 2-3 retry) and I should unplug and then plug to retry).


PS: I try to connect and other modem (with vodafone) but different model and it works totally correctly so... :?

---

### Post by GeorgeVita on 2009-09-12
Hi **SuckerBlood**, I tried just now and managed to reproduce the problem with another modem (E169) on Ubuntu 9.10 (now testing).

I do not have a 'clear' answer on this as many things are changing on 9.10 (version of network manager, way of 'driving' 3G modems etc.). Modem got working again after stop/start network manager and/or udev refresh-devices. I am not sure if can be used on 9.04, just for reference I am listing some commands:```
sudo /etc/init.d/networking restart
sudo /etc/init.d/NetworkManager stop
sudo modprobe -r option
sudo modprobe option
sudo /etc/init.d/udev refresh-devices
sudo /etc/init.d/NetworkManager start
```
As I remember refresh-devices causes multiple entries on network manager icon (with 9.04).

... so it is not a clear situation.

Regards,
George

---

### Post by Stefan Arsovski on 2009-09-14
Hi there

Some1 tried on ubuntu 8.04? I use caelinux 2009 & it works on 8.04.

Thanks in advance

---

### Post by tobik999 on 2009-09-22
Hi there and many thank for this tutorial.

I just have two problems:

1. I do not know what to type in at the Network Manger to set up a connection for Comcel Colombia. Can anyone help?

2. The modem just shows up for about 10-20 minutes at the Network Manager, after that I have disconnect and connect again. So many less than one hour.!?

---

### Post by tobik999 on 2009-09-22
I tried it now with wvdial as suggested on this page:
[http://www.slax.org/forum.php?action=view&parentID=44356](http://www.slax.org/forum.php?action=view&parentID=44356)
and get the following error:
```
tobias@Tobiasnotebook:~/wvdial-1.60$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Idle Seconds = 300, disabling automatic reconnect.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Sep 22 16:03:42 2009
--> Pid of pppd: 12754
--> Disconnecting at Tue Sep 22 16:03:42 2009
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

```

---

### Post by GeorgeVita on 2009-09-22
> **tobik999 said:**
> ...1. I do not know what to type in at the Network Manger to set up a connection for Comcel Colombia. Can anyone help?
From latest network manager data:

Comcel Colombia
Phone = *99#
APN = internet.comcel.com.co
username = COMCELWEB
password = COMCELWEB

That means if you are using **wvdial**, you must include at your **/etc/wvdial.conf** file the following lines:```
Init5 = AT+CGDCONT=1,"IP","internet.comcel.com.co"
Username = COMCELWEB
Password = COMCELWEB
Stupid Mode = yes
Phone = *99#

```

In any case of error post ALL your /etc/wvdial.conf file.
USE **sudo wvdial** to connect!

Regards,
George

---

### Post by tobik999 on 2009-09-22
Connecting form the Network Management did not work somehow. It told me it is connected but I could not ping google.com or anyting else. 

I will now try to find something in the log files and tomorrow I will reinstall wvdial and give it a try with the suggested configuration (Windows killed my GRUB :( and with this GPRS signal I can not download files larger than 100KB :( SHAME ON COMCEL) 

What ping times do you have using mobile internet? I am using Comcel and have #fantastic# repsonse times of 1500-4000ms (GPRS) and 400-1000ms (UMTS).

---

### Post by tobik999 on 2009-09-23
Many thanks to GeorgeVita!

My stick is now connecting with wvdial, but it is very slowly. The light on the stick is flashing in blue, so I am connected through GPRS, right?
What do I have to do to connect with UMTS?

My wvdial.conf looks as follows:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init5 = AT+CGDCONT=1,"IP","internet.comcel.com.co"
Stupid Mode = yes
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB2
ISDN = 0
 Phone = *99#
 Password = COMCELWEB
 Username = COMCELWEB

```

---

### Post by GeorgeVita on 2009-09-24
Hi **tobik999**,
the only change you can to is the baud rate: **Baud = 921600**
(this is not the maximum data rate but the speed of the command interface)

Usually blue led means 3G, green led is GPRS. Most times 'real' internet speed depends on provider so "Ask them to  check it".

Some pings from my provider, Wind Greece (local time 9:35 AM)
[www.otenet.gr](www.otenet.gr) 170mSec (local internet provider)
[www.ubuntuforums.org](www.ubuntuforums.org) 240mSec
[www.nasa.gov](www.nasa.gov) 245mSec
[www.lxde.org](www.lxde.org) 817mSec (taiwan)

Regards,
George

---

### Post by tobik999 on 2009-09-24
>  Usually blue led means 3G, green led is GPRS. Most times 'real' internet speed depends on provider so "Ask them to  check it".
With my stick it is right the other way, green is umts and blue is gprs. I do now have umts where it is available, I connected the stick to a windows pc changed the network settings from "GPRS only" to "Autmatically" and now it is working perfectly.

The above mentioned Ping times are from a windows pc, from Linux it is now a bit faster.
google.com (UMTS) about 300ms.
ubuntuformus.org primary 5 about 800ms and after that also about 300ms.

I think the reason for this bad ping times is that Comcel build a really ... network with a VPN from Colombia until USA and from there (sometimes central USA and sometimes East Coast) I get "really" into the www.

Many thanks GeorgeVita! I really felt in love with my Kubuntu now while everything is working :)

---

### Post by Kaizzer on 2009-09-28
Hey there .. i was going to the steps privided .. and crashed :( ... 

at this line .. sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf 

i get on my console.. :
```
Reading config file: /etc/usb_modeswitch.conf

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.0.5 (C) Josua Dietze 2009
 * Based on libusb 0.1.12

DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 005 on 002
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 002 on 001
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 005 on bus 002 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached
```...
and never coming back.. 
:( 
any ideas ?! :) 

(im on Ubuntu 8.04 ..btw) 
TIA.

---

### Post by GeorgeVita on 2009-09-29
Hi **Kaizzer**,
my opinion is that on Ubuntu 8.04 it is easier to try:
[http://ubuntuforums.org/showthread.php?p=6511814](http://ubuntuforums.org/showthread.php?p=6511814)

1. send '**AT+ZCDRUN=8**' from windows to modem
2. check actual productID using '**lsusb**' from Ubuntu
3. use '**sudo modprobe usbserial vendor=0x19d2 product=0xYYYY**' (YYYY from lsusb)
4. check if ports are created with '**ls /dev/ttyU***'
5. configure **wvdial** for your country/provider

Regards,
George

---

### Post by Kaizzer on 2009-09-29
> **GeorgeVita said:**
> Hi **Kaizzer**,
my opinion is that on Ubuntu 8.04 it is easier to try:
[http://ubuntuforums.org/showthread.php?p=6511814](http://ubuntuforums.org/showthread.php?p=6511814)

1. send '**AT+ZCDRUN=8**' from windows to modem
2. check actual productID using '**lsusb**' from Ubuntu
3. use '**sudo modprobe usbserial vendor=0x19d2 product=0xYYYY**' (YYYY from lsusb)
4. check if ports are created with '**ls /dev/ttyU***'
5. configure **wvdial** for your country/provider

Regards,
George

George. Frist of all, thanks for your response. 

i've read your post and as you say, it looks pretty simple to do.  the problem is that the modem is not for my personal use only. I have to share it with all my co-workers so the the step 1 is kind of anoying dont you think ? (im the only one working with linux here.. :( ) Besides, i would like a solution that doesnt depend on me having to deal with Windows...again .. 

Lets just say .. ive just made a step forward (windows -> ubuntu)  and i dont want to go back. i know you know what i mean.. 
Regards

---

### Post by GeorgeVita on 2009-09-29
Hi **Kaizzer**, below is your 2nd option that must be checked on Ubuntu **8.04** (I cannot):

When you attach the modem to the USB port, probably a CDROM is appeared. If yes, try to **eject it**. Usually after ejecting this CDROM the 'real modem' appears and can be checked via **lsusb** terminal command.

Read more at: [http://ubuntuforums.org/showpost.php?p=8014658&postcount=24](http://ubuntuforums.org/showpost.php?p=8014658&postcount=24)
and [http://ubuntuforums.org/showpost.php?p=8014658&postcount=26](http://ubuntuforums.org/showpost.php?p=8014658&postcount=26)

Above works with 'older' linux distributions and from the next Ubuntu 9.10


**[size=3][COLOR="DarkSlateBlue"]EDIT: [/COLOR][/size]** Just checked with a liveUSB running Ubuntu 8.04.2 and connected using a 'simple eject' switching to 'real modem' mode (**MF636**).
Actions done:
LiveUSB 'burned' using Ubuntu 9.04 'USB startup disk creator' and 8.04.2 .iso
Boot from 8.04.2 LiveUSB19d2:2000
From terminal window: sudo dmesg -c
modem attached, confirmed as **19d2:2000** (lsusb), CDROM found as **sr1** (dmesg), ejected and 'real modem' appeared as **19d2:0031** (lsusb), some (3) ports created  (sudo modprobe ...) using 0x19d2 and 0x0031 IDs (ports checked with ls /dev/ttyU*), connected using my pppd commaaaaaaand and finally I edited this post!

([size=1]8.10 and 9.04 do not have the 'eject facility', it comes back from 9.10[/size])

```
ubuntu@ubuntu:~$ lsusb | grep 19d2
Bus 005 Device 006: ID 19d2:2000  
ubuntu@ubuntu:~$ dmesg
[  168.187729] usb 5-2: new high speed USB device using ehci_hcd and address 6
[  168.334666] usb 5-2: configuration #1 chosen from 1 choice
[  168.397128] scsi4 : SCSI emulation for USB Mass Storage devices
[  168.398065] usb-storage: device found at 6
[  168.398075] usb-storage: waiting for device to settle before scanning
[  173.389776] usb-storage: device scan complete
[  173.391757] scsi 4:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[  173.423795] sr1: scsi-1 drive
[  173.424021] sr 4:0:0:0: Attached scsi CD-ROM sr1
[  173.424192] sr 4:0:0:0: Attached scsi generic sg2 type 5
[  176.090530] scsi 3:0:0:0: rejecting I/O to dead device
[  186.499850] ISO 9660 Extensions: Microsoft Joliet Level 1
[  186.502856] ISOFS: changing to secondary root
ubuntu@ubuntu:~$ sudo eject sr1
ubuntu@ubuntu:~$ lsusb | grep 19d2
Bus 005 Device 007: ID 19d2:0031  
ubuntu@ubuntu:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
ubuntu@ubuntu:~$ ls /dev/ttyU*
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2
ubuntu@ubuntu:~$ sudo pppd ttyUSB2 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','gint.b-online.gr'" OK "atdt*99***1#" CONNECT' user web password web
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB2
CHAP authentication succeeded
CHAP authentication succeeded
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address ...
```


Regards,
George

---

### Post by Kaizzer on 2009-09-30
Thanks GeorgeVita. i got to the eject part of your procedure and it worked..(ie .. i see the **19d2:0031 device)**  at the time i havent got the minute to follow the entire process, besides i have to find out the rest of the parameters.. ie ip, user and pass.. that i dont have...

i have another question and since im kind of new on linux, hope you wont mind me asking.

This procedure seems to me a bit complex to perform on a dayly basis . is there a way to automatizate all of this so i wont have to perform all this tasks each time i use this modem. 

its supposed to use (the modem) when im not at work .. ie .. at home or at a client's office... 

i know you get my point. 

Thank you again for your time. 
Regards.

---

### Post by GeorgeVita on 2009-10-01
> **Kaizzer said:**
> ...This procedure seems to me a bit complex to perform on a dayly basis . is there a way to automatizate all of this so i wont have to perform all this tasks each time i use this modem.

Most tasks above are for your tests only. Till now you have only 2 actions:
1. attach modem
2. eject CDROM from icon (can be automatically with a '[udev rule]("http://ubuntuforums.org/showpost.php?p=7624549&postcount=61")')

To create the 'auto eject rule': ```
gksudo gedit /etc/udev/rules.d/AutoEjectZTE.rules
``` and copy into that file: ```
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"
```

Your real problem is that you are using an older version (8.04) and when  you upgrade to 9.10 or 10.04 (LTS) the behavior of ZTE 3G modems is different.

Post provider/account type (prepaid?) to check latest network manager parameters.

Regards,
George

---

### Post by VH-BIL on 2009-10-03
For those that are having trouble getting the modem working and want a "REAL SIMPLE" way of connecting. Install the drivers into a [_VirtualBox_]("http://www.virtualbox.org/") with windows.

When you want to use the modem in Linux load the VirtualBox Windows and make sure it can see the modem. Then just close it. Simple :) Network Manager can now see the modem.

I know this solution is not as good, but it may help people that are newer to Linux. I mainly use a LAN connection but when I have to use the MF626 it access it this way and it works great every time!

---

### Post by Kaizzer on 2009-10-06
> **VH-BIL said:**
> For those that are having trouble getting the modem working and want a "REAL SIMPLE" way of connecting. Install the drivers into a [_VirtualBox_]("http://www.virtualbox.org/") with windows.

When you want to use the modem in Linux load the VirtualBox Windows and make sure it can see the modem. Then just close it. Simple :) Network Manager can now see the modem.

I know this solution is not as good, but it may help people that are newer to Linux. I mainly use a LAN connection but when I have to use the MF626 it access it this way and it works great every time!

Thank you VH-BIL.. it sure sounds like a nice workarround of this problem .. and im going to try it as soon i can. 

Still .. i will follow the above instrutions (GeorgeDeVita) becouse it seems im gonna learn more doing it .. :) although ..its gonna require more time ... 


Regards.

---

### Post by VH-BIL on 2009-10-06
> **Kaizzer said:**
> Thank you VH-BIL.. it sure sounds like a nice workarround of this problem .. and im going to try it as soon i can. 

Still .. i will follow the above instrutions (GeorgeDeVita) becouse it seems im gonna learn more doing it .. :) although ..its gonna require more time ... 


Regards.

No propblems Kaizzer, just make sure modem changes colour before you close down the windows VBox. I had to sudo VirtualBox to access my USB devices, but while I am typing this I am updating it and in the changelog was something about changing the way Linux Hosts access USB devices. Hopefully there will be no need to use sudo to get access to USB devices any more in VirtualBox.

---

### Post by Kaizzer on 2009-10-07
thanks for the tip again VH-BIL..!
regards

---

### Post by Kaizzer on 2009-10-08
> **GeorgeVita said:**
> 

Post provider/account type (prepaid?) to check latest network manager parameters.

Regards,
George

George.. i was about to re take this path of solution when i realized that i lack of the information that you ask .. ie ip, networks parameters, user and passwords.

i think this information should be in the modem somewhere.. because it was configured (on windows..not mine .. of course) when my company bout it .. am i right on this ?? if so .. is there a way to retrieve this information from the device somehow ? 

looking forward for your opinion.. 

im thinking to buy one of those modems from a local company in a shortime....
regards.

---

### Post by Abdullahnz on 2009-10-26
Gentlemen, I have a much simpler solution not requiring any terminal, udev rules or vbox.

It is possible (in fact very easy) to reconfigure the modem itself to not load as a CDROM first but straight into 'real modem' mode.

Under Karmic RC this makes the Modem plug n play. Haven't tried it with Jaunty, but I assume it would work the same.

I have written a guide here:
[http://ubuntuforums.org/showthread.php?t=1302235](http://ubuntuforums.org/showthread.php?t=1302235)

---

### Post by jamsh on 2009-10-29
I have just installed Ubuntu 9.10 and when I plugged in my T-Mobile USB modem, it just worked straight away!!

---

### Post by GeorgeVita on 2009-10-29
> **jamsh said:**
> I have just installed Ubuntu 9.10 and when I plugged in my T-Mobile USB modem, it just worked straight away!!

Hi **jamsh**,
can you please post the model of your modem and the output of **lsusb** command?

Regards,
George

---

### Post by VH-BIL on 2009-10-31
> **Abdullahnz said:**
> Gentlemen, I have a much simpler solution not requiring any terminal, udev rules or vbox.

It is possible (in fact very easy) to reconfigure the modem itself to not load as a CDROM first but straight into 'real modem' mode.

Under Karmic RC this makes the Modem plug n play. Haven't tried it with Jaunty, but I assume it would work the same.

I have written a guide here:
[http://ubuntuforums.org/showthread.php?t=1302235](http://ubuntuforums.org/showthread.php?t=1302235)

This worked great, thanks.

---

### Post by tibalt-99 on 2009-11-01
Sirs, please help

I can not plug MF 626 at my box
box: Dell ispiron mini 10, Ubuntu Ubuntu 8.04
                - the Hardy Heron - released in April 2008.
                
uname -a
Linux tibalt 2.6.24-24-lpia #1 SMP Wed May 6 17:43:36 UTC 2009 i686 GNU/Linux

pluging in modem:

> 

tibalt@tibalt:~$ lsusb
Bus 005 Device 019: ID 19d2:2000  
Bus 005 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 174f:1403  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1bcf:0007  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000




my .conf file

> 
sudo vim /etc/usb_modeswitch.conf

########################################################
#ZTE MF628+ (tested version from Telia / Sweden)
ZTE MF626
#ZTE MF633
#ZTE MF636 (aka "Telstra / BigPond 7.2 Mobile Card")

Contributor: Joakim Wennergren

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0031

# only for reference and 0.x versions
#MessageEndpoint=0x01

MessageContent="55534243123456782000000080000c85010101180101010101000000000000"

# if that command doesn't work, try the other ("eject")
#MessageContent="5553424312345678000000000000061b000000030000000000000000000000"





sudo vim /usr/share/hal/fdi/information/20thirdparty/20-zte-mf626.fdi


> 
<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device>
<!-- ZTE MF626 HSDPA USB Modem -->
<match key="@info.parent:usb.vendor_id" int="0x19d2">
<match key="@info.parent:usb.product_id" int="0x0031">
<match key="@info.parent:usb.interface.number" int="3">
<append key="modem.command_sets" type="strlist">GSM-07.07</append>
<append key="modem.command_sets" type="strlist">GSM-07.05</append>
<append key="info.capabilities" type="strlist">modem</append>
</match>
</match>
</match>
</device>
</deviceinfo>
~                



starting usb_modeswitch

> 

tibalt@tibalt:~$ sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf
Reading config file: /etc/usb_modeswitch.conf

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.0.5 (C) Josua Dietze 2009
 * Based on libusb 0.1.12

DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint= not set
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 021 on 005
usb_os_find_devices: Found 003 on 005
usb_os_find_devices: Found 002 on 005
skipping descriptor 0xB
skipped 1 class/vendor specific endpoint descriptors
skipped 6 class/vendor specific interface descriptors
skipping descriptor 0x25
skipped 1 class/vendor specific endpoint descriptors
skipped 12 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 005
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 002 on 002
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 001

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 021 on bus 005 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

Received inquiry data (detailed identification)
-------------------------
  Vendor String: ZTE     
   Model String: USB SCSI CD-ROM 
Revision String: 2.31
-------------------------

Device description data (identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE CDMA Technologies MSM
  Serial No.: P673M3BLNMassSto
-------------------------
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 OK, message successfully sent
-> Run lsusb to note any changes. Bye.



lsusb

> 


tibalt@tibalt:~$ lsusb 
Bus 005 Device 022: ID 19d2:0031  
Bus 005 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 174f:1403  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1bcf:0007  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000






it is seen that device ID haad been changed but I see nothing in my network manager

if I am trying to test modem through kppp I am getting: "Unable to open modem"

Please assist

Thank you

---

### Post by Piratini on 2009-11-04
Hello. I can't get usb_modeswitch working no matter what. It keeps telling me:
```
USB error: error submitting URB: Device or resource busy
```
I'm running on Karmic. When I was on Jaunty, I wasn't getting this message and everything worked just fine.

---

### Post by pdc on 2009-11-04
what would make you go back to jaunty, where everything worked fine?

---

### Post by Piratini on 2009-11-04
There are some new features in Karmic that I don't want to lose. All I want is to understand the reasons behind this error and fix it.

---

### Post by gfortes84 on 2009-11-04
Does anyone have any insight on getting this dmn moden to work with Karmic?

I got a weird problem that i wrote about here: [http://ubuntuforums.org/showthread.php?t=1314343](http://ubuntuforums.org/showthread.php?t=1314343)

Thanks in advance for any kind of help :)

[Solved]

**Abdullahnz** solution worked very well, had to use putty on Windows 7 instead o Hyperterminal. Thank you!

---

### Post by Piratini on 2009-11-05
Do I have to buy and install Windows just to make this modem work? :(

---

### Post by VH-BIL on 2009-11-05
> **Piratini said:**
> Do I have to buy and install Windows just to make this modem work? :(

lol, can't you just use someones computer that has windows installed?

---

### Post by artmendez on 2009-11-12
I switched to 9.10. Everything running smoothly.

Now the ZTE MF626 seems to "work"... no heavy acrobatics necessary.

I went into the Network connections manager, and added the connection... My service provider profile even appeared... **Make sure to select the connect automatically[B]**[/B] option (if your data plan allows this ;), this may save some clicks!)

I plugged in the modem, waited for the CD-ROM to be mounted (yes, this works now in 9.10), and without trying further, I unmounted the media unit from the Media Mounter applet I keep in a panel... and *voila!* This seems to have done the switching trick. It actually is described in some articles out there. Karmic Koala seems to handle this. After a few seconds... I'm connected full-throttle.

I'm actually using it right now to prove the concept.

(Drawback, last night after some time of trying it out, the connection was lost, and I could not make it work back... even after rebooting (??), but today, it worked... (maybe I spoofed something else by accident... but it was late to track it down)...)

Note: I tried this (only once) with the Live CD without success, but I would not say that you have to fully install 9.10... maybe you can testdrive 9.10 with the LiveCD, watch your ZTE usb modem works, and switch... ;)


saludos!

Good luck.

---

### Post by cataztrophe on 2009-11-13
thnx for your share bro!!
really need this!! :D

---

### Post by Cyberdragonfly on 2009-11-27
My MF626 shows up as ID 19d2:0072 after its switched. Any ideas why and what it is ?

---

### Post by IlPazzo on 2009-11-29
Hi all,

I've got some problem with that procedure. Basically, I went through it, but when I do "sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf" no device is found. This is what it says:

> stefano@stefano-laptop:~$ sudo gedit /etc/usb_modeswitch.conf
[sudo] password for stefano: 
stefano@stefano-laptop:~$ lsusb
Bus 005 Device 004: ID 046d:0896 Logitech, Inc. OrbiCam
Bus 005 Device 002: ID 19d2:0031  
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 093a:2510 Pixart Imaging, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
stefano@stefano-laptop:~$ sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf
Reading config file: /etc/usb_modeswitch.conf

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.0.5 (C) Josua Dietze 2009
 * Based on libusb 0.1.12

DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_busses: Found 003
usb_os_find_devices: Found 004 on 005
usb_os_find_devices: Found 002 on 005
usb_os_find_devices: Found 001 on 005
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 001 on 001
usb_os_find_devices: Found 004 on 003
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 003
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 No default device found. Is it connected? Bye.

---

### Post by IlPazzo on 2009-11-29
Some more details. Everything went fine with the procedure. Before point 10, the modem was also detected as default device ("Found default device (1)") as in the first post. In the end, as written, I restarted and then I typed:

sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf

And got:

> 
Reading config file: /etc/usb_modeswitch.conf

* usb_modeswitch: handle USB devices with multiple modes
* Version 1.0.5 (C) Josua Dietze 2009
* Based on libusb 0.1.12

DefaultVendor= 0x19d2
DefaultProduct= 0x2000
TargetVendor= 0x19d2
TargetProduct= 0x0031
TargetClass= not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c8501 0101180101010101000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_busses: Found 003
usb_os_find_devices: Found 004 on 005
usb_os_find_devices: Found 002 on 005
usb_os_find_devices: Found 001 on 005
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 001 on 001
usb_os_find_devices: Found 004 on 003
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 003
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
No devices in target mode or class found
Looking for default devices ...
No default device found. Is it connected? Bye.

The modem was correctly connected and the led was blue and always on. The USB Modem model is MF626 with T-Mobile in UK and Im on Jaunty.

Please, help :)

---

### Post by cirobr on 2009-12-19
Hello,

Just to inform this post on my Aiko 83D (Vivo Brazil) - same as ZTE MF626 - on Karmic with latest updates, providing the following:

usb-modeswitch is installed directly from Synaptic
/etc/usb_modeswitch.conf -> TargetProduct 0x0057
/usr/share/hal/fdi/information/20thirdparty/20-zte-mf626.fdi -> <match key="@info.parent:usb.product_id" int="0x0057">
Ethernet cables disconnected, WiFi switched off

Thanks to Unkuiri

---

### Post by Artemis3 on 2009-12-25
I just followed step 10, and the ZTE MF626 works fine with Ubuntu 9.10 in Network Manager. Usb modeswitch is not really needed, just unmount the usb storage device and it switches to modem.

---

### Post by Dark77 on 2009-12-30
Hi all. 
I've got T-Mobile USB modem ZTE MF626 (in Montenegro) and spent some time to make it work.

Yes, usb-modem will appear after you type "sudo eject sr1".
But I did following and it works for me with Network Manager when I connect it.

1. About system: ubuntu 9.10
cat /proc/version
Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8 ) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009
2. device
lsusb | grep 19d2
Bus 002 Device 029: ID 19d2:0031 ONDA Communication S.p.A. 

What I've done:
1. Install USB_ModeSwitch
sudo aptitude install usb-modeswitch
2. Edit udev rules
sudo vi /etc/udev/rules.d/usb_modeswitch.rules
2.1. I searched for "626" and found 
# ZTE MF628+ (tested version from Telia / Sweden)
# ZTE MF626
# ZTE MF636 (aka "Telstra / BigPond 7.2 Mobile Card")
2.2. Added next line
SUBSYSTEM=="usb", SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/sbin/usb_modeswitch --target-vendor 0x19d2 --target-product 0x0031 --default-vendor 0x19d2 --default-product 0x2000 --message-content 55534243123456782000000080000c85010101180101010101000000000000"

After that device appears in Network Manager and works as microSD adapter without problems.

---

### Post by PaulReaver on 2009-12-30
If you want an easier life install the modem driver/software in windows, and on the mf626 dashboard options, disable the onboard cdrom drive.  

the next time you connect it to your linux computer it should show up as a modem. easy.  no modeswithch nonsense is needed.

only thing is you'll need to re-enable the cd-drive again in windows before it'll install in another windows machine. 
and make sure not to un-install the mf626 dashboard while the cd-drive is disabled.

---

### Post by dawg on 2010-01-01
Will this technique working on all 3G CDMA modems?  I've got an mv100n modem that we use with Kalimat Telecomm here in Iraq and I was wondering if it would work.

---

### Post by cirobr on 2010-01-03
> **cirobr said:**
> Hello,

Just to inform this post on my Aiko 83D (Vivo Brazil) - same as ZTE MF626 - on Karmic with latest updates, providing the following:

usb-modeswitch is installed directly from Synaptic
/etc/usb_modeswitch.conf -> TargetProduct 0x0057
/usr/share/hal/fdi/information/20thirdparty/20-zte-mf626.fdi -> <match key="@info.parent:usb.product_id" int="0x0057">
Ethernet cables disconnected, WiFi switched off

Thanks to Unkuiri

Just an update on this. Although the solution has worked for me, I've found the connection through Network Manager extremely unstable, in the sense that:

- The modem is hardly recognized by the system at the first time when is plugged on to an USB port;
- Whenever modem is recognized, connection is made after countless trials through Network Manager.

To overcome that, I've dropped Network Manager once for all and adopted wvdial. Modem recognition is done smoothly and connection is almost immediate.

I've shared the HOW TO on the below link:

[http://ubuntuforums.org/showthread.php?p=8597766#post8597766]("http://ubuntuforums.org/showthread.php?p=8597766#post8597766")

---

### Post by ubumania on 2010-01-08
Does this work in Intrepid? The usb is being recognised but when I run
```

sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf
```

then run

```
lsusb
```

the device id isn't changing so I'm getting

```

Bus 007 Device 002: ID 19d2:2000  
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

And this is on an Ubuntu pre-loaded Dell Inspiron that becomes unusable on the Jaunty upgrade.

Any ideas?

---

### Post by cirobr on 2010-01-08
> **ubumania said:**
> Does this work in Intrepid? The usb is being recognised but when I run
```

sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf
```

then run

```
lsusb
```

the device id isn't changing so I'm getting

```

Bus 007 Device 002: ID 19d2:2000  
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

And this is on an Ubuntu pre-loaded Dell Inspiron that becomes unusable on the Jaunty upgrade.

Any ideas?

Don't know. I've tested on Karmic only.

---

### Post by pdc on 2010-01-08
if you go here

[http://www.draisberghof.de/usb_modeswitch/#trouble](http://www.draisberghof.de/usb_modeswitch/#trouble)

they suggest you edit the file 

> /usr/sbin/usb_modeswitch.tcl

so by editing that file, you should not affect anything else 

edit it by entering the command

> sudo gedit /usr/sbin/usb_modeswitch.tcl

and they say to change the line

> set logging 0

to 

> set logging 1

they say: this gives you a verbose output of the hotplug activity to /var/log/usb_modeswitch

and you would see that by the command

> tail -f /var/log/usb_modeswitch

these folks have a forum 

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

and also the version 1.05 of their software (which do you have?) comes as a debian package and is said to auto-configure

your usb_modeswitch.conf file presumably looks like

> # ZTE MF622 (aka "Onda MDC502HS")
# ZTE MF626
# ZTE MF628+ (tested version from Telia / Sweden)
# ZTE MF633
# ZTE MF636 (aka "Telstra / BigPond 7.2 Mobile Card")
# ZTE MF637
#
# Contributor: Joakim Wennergren and others

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0031

# only for reference and 0.x versions
MessageEndpoint=0x01

MessageContent="5553424312345678000000000000061b000000030000000000000000000000" 

I guess if you tell us that: did you edit the file yourself?

---

### Post by ubumania on 2010-01-09
Yes I edited the file myself but removed all of the comments in that section as per the instructions on this and every other how to I have looked at. I changed it so it was identical to the one above but it still won't switch. I have now upgraded to Jaunty and rolled back the drivers I needed to but I'm still not getting any further with the modeswitch.

When I run

```
sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf

```

regardless of /etc/modeswitch.conf config, I get the following

```

Reading config file: /etc/usb_modeswitch.conf

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.0.6 (C) Josua Dietze 2009
 * Based on libusb 0.1.12

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
GCTMode=0
MessageEndpoint= not set
MessageContent="5553424312345678000000000000061b000000030000000000000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 002
usb_os_find_busses: Found 007
usb_os_find_busses: Found 006
usb_os_find_busses: Found 005
usb_os_find_busses: Found 001
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_devices: Found 002 on 002
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 007
usb_os_find_devices: Found 001 on 006
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 001
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 002 on bus 002 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
USB error: could not get bound driver: No data available
 No driver found. Either detached before or never attached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: ZTE     
   Model String: USB SCSI CD-ROM 
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE CDMA Technologies MSM
  Serial No.: 1234567890ABCDEF
-------------------------
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 OK, message successfully sent
-> Run lsusb to note any changes. Bye.

```

Does that look right? There are a lot of 'not set' and one or two 'errors' but it looks similar to the output posted on page 1.

yet whenever I run 'lsusb' the device id remains

```
Bus 002 Device 002: ID 19d2:2000 
```

If I now upgrade to Karmic will this dongle just work or am I seriously going to have to put Windows on this machine I bought with Ubuntu on it? I love this OS and all that but if I can't get this thing connected I am going to have to do the unthinkable and give Bill Gates a bit more money. Total nightmare. Help.

PS I also tried 'sudo gedit /usr/sbin/usb_modeswitch.tcl' but the file doesn't exist so it opens up a blank document? There is a file '/usr/sbin/usb_modeswitch' but nothing with that extension.

---

### Post by alexfish on 2010-01-09
hi

seen a forum thread about this device here

[http://dreamlinuxforums.org/index.php?topic=5797.0](http://dreamlinuxforums.org/index.php?topic=5797.0)

also here

[http://blog.christophersmart.com/2009/05/21/telstra-nextg-working-with-mf626-usb-modem/](http://blog.christophersmart.com/2009/05/21/telstra-nextg-working-with-mf626-usb-modem/)

---

### Post by GeorgeVita on 2010-01-09
Updated info for using **ZTE MF636 on Ubuntu 8.10 with usb_modeswitch**.

[size=0]Other ways to use MF636 on Ubuntu 8.10:
8.10 & wvdial: [http://ubuntuforums.org/showthread.php?p=6511814](http://ubuntuforums.org/showthread.php?p=6511814)
8.10 & network manager: [http://ubuntuforums.org/showthread.php?p=6894586](http://ubuntuforums.org/showthread.php?p=6894586)[/size]

Initially ZTE MF636 is shown as **19d2:2000** at **lsusb**. After switching is **19d2:0031**
All tested on a Ubuntu 8.10 LiveUSB (created using USB disk start up creator on Ubuntu 9.04). Persistent disk area (380MBytes) used for installation space.

On an initial Ubuntu 8.10 when a ZTE MF636 3g modem is inserted, the usb-storage is ignored and then cannot be ejected (as it does not exists) to reveal 'real modem' state.

Below is my tested method using usb_modeswitch (very similar to that described by **Unkuiri** at 1st post!)

Downloaded 'debian version' of **usb_modeswitch** as it is not at 8.10 repositories 
(this is not 'typical' but worked) plus 2 extra packages needed: **tcl** and **tcl8.4**

>>> below are the packages for **i386**

1. [http://packages.ubuntu.com/intrepid/i386/tcl8.4/download](http://packages.ubuntu.com/intrepid/i386/tcl8.4/download)
2. [http://packages.ubuntu.com/intrepid/all/tcl/download](http://packages.ubuntu.com/intrepid/all/tcl/download)
3. [http://packages.debian.org/squeeze/i386/usb-modeswitch/download](http://packages.debian.org/squeeze/i386/usb-modeswitch/download)

To install copy to desktop and double click to install (or open with GDebi package installer). Then create udev rules file:
```
gksudo gedit /etc/udev/rules.d/90-zte.rules
```Place following contents into that file: ```
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf", OPTIONS+="last_rule"
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="0031", RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0031", OPTIONS+="last_rule"
``` and usb_modeswitch file: ```
gksudo gedit /etc/usb_modeswitch.conf
```Copy the following data (most taken from file **/etc/usb_modeswitch.d/19d2:2000:uPr=USB_ZTE**):
```
#############
# ZTE MF636

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0031

CheckSuccess=20

MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
```
Finally (!) edit the HAL info file as it does not cober 19d2:0031 as a modem:
```
gksudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
```
Search (**CRTL-F**) for **19d2**, move some lines below and edit line from '**usb.product_id" int="0x0015">**' to '**usb.product_id" int="0x0031">**'. Final edited section for vendorID=**19d2** of 10-modem.fdi file will be: ```
      <match key="@info.parent:usb.vendor_id" int="0x19d2">
        <!-- Qualcomm: Telstra/NextG CDMA -->
        <match key="@info.parent:usb.product_id" int="0x0001">
          <match key="@info.parent:usb.interface.number" int="0">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>
        <!-- ZTE MF628 HSDPA USB dongle -->
        <match key="@info.parent:usb.product_id" int="0x0015">
          <match key="@info.parent:usb.interface.number" int="3">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>
      </match>

```

Reboot to test it, click on network manager icon to create/use connection.

Notes:
- if a message asks 'password for default keyring' leave it blank > create > use unsafe storage
- if a window 'this medium contains software ...' appear click CANCEL

Extra note:
contents of file **/etc/usb_modeswitch.conf** determined running usb_modeswitch from terminal using various **/etc/usb_modeswitch.d/19d2...** configuration files. If your modem has other firmware and/or productID (here is 0x0031) you must check/adjust some data.

More info at: [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

Regards,
George

---

### Post by alexfish on 2010-01-09
hi GeorgeVita

do you have any tips on getting this device running at top speed

regards alexfish

---

### Post by GeorgeVita on 2010-01-09
Most times my provider controls the 'speed of my modem' (I can always test E169 vs MF636 with the same results). When firstly connected to +mobile -broadband I got a maximum of 4MBits/sec while today the maximum is 2.8Mbits/sec (same area) with a working average of 0.2-1.2Mbits/sec (Athens, Greece).

history: [http://ubuntuforums.org/showpost.php?p=7911123&postcount=33](http://ubuntuforums.org/showpost.php?p=7911123&postcount=33)

G

---

### Post by ubumania on 2010-01-09
Thanks to anyone trying to help out but it's too late now. For the second laptop on the trot, the Ubuntu upgrade process has fried my hard-drive. I now need to buy a replacement drive and, obviously, put a new OS on it. I'm not rich, saved up for this machine and all that crap, bought it just over a year ago with Ubuntu pre-loaded after being told-off on these forums for trying to run Ubuntu on a machine with 'incompatible hardware'; so, by the time I can afford a new hard drive my land-line connection will be cut off so I'm going to need to be able to plug this dongle in and have it instantly work. Can the Ubuntu that came pre-loaded on the Dell I paid a few-hundred quid for cope with such a simple task? NO, BIG BIG NO NO NO. Chances are, trying to get that (simple thing that just plugs and plays in that ever so crap Microsoft software) working on my pre-loaded Dell will break it.

Why oh why do they sell these machines in the shops as good to go when they clearly cannot compete? Pretending is no good, pretenders always get found out. It may well be no fault on the part of Canonical that they can't compete but why should users who buy hardware loaded with Ubuntu in good faith pay the ******* price? Like, what did I do to ubuntu to end up getting sold a machine that can't even deal with a device that connects to the internet without hard drives getting wiped out by an all to frequent, inadequate 6 monthly upgrade process?

Something has to give. I have used Win 7 and, with all of the God Modes enabled, it gives this Ubuntu a real run for its money on all fronts. 

Ubuntu: you let this user down in a big way, to the tune of a new hard drive after only 14 months of light use and the purchase of Windows. Last night my machine was working fine. The process of trying unsuccessfully to get Ubuntu to recognise a device for what it is in its entirety and thus connect to the internet has rendered this OS and the hard drive where it resides, inoperable. Is that good enough for paying customers who buy machines in good faith?
[I]
This is not meant to be a testimonial, I shall be posting one of those in the correct sub-forum in good time. This post is specific to this thread and therefore needs to stay as a warning to all other Dell Inspiron users who have had the misfortune of being told that these and other peripheral USB modem devices work on the Ubuntu pre-loaded machines they have purchased when clearly they do not.[/I]

Have any Ubuntu representatives got anything to say about the above experience? If this problem is specific to my machine: ie, other pre-loaded Dell Inspiron users have this device working in Ubuntu Intrepid or have upgraded beyond Intrepid without any problems and then got the OS to switch the device mode to a modem instead of a storage device (perhaps it would be better to concentrate on making these things work instead of trying to pump out release after release?) , then I apologise and humbly ask for help getting mine to do the same when I have replaced the hard drive the Ubuntu upgrade tool broke.

Only I honestly cannot believe that my story is unique.

Please prove me wrong. Give me a cast iron guarantee that this dongle will work on my Dell Inspiron 1525 if I put Ubuntu back on the new hard drive I get in a couple of weeks. Or at least be honest and say 'you will not be able to get that dongle working in Ubuntu on your machine without first having an internet connection, absolutely NO version of Ubuntu can plug and play those devices regardless of how much you paid for it, you will be better off purchasing Windows'.

Please, I can handle the truth, especially if it means having an internet connection that works.

If I put Ubuntu back on my new hard drive, how will I know if the new how 2s that have been posted above will work on this machine? How many files need editing to get this device to work? How many bits of software?

Paying customer.

Come on Ubuntu.

---

### Post by alexfish on 2010-01-09
Hi all

N.R.R
Ubuntu 9.04 (*Jaunty Jackalope*), released on 23 April 2009,[[54]]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#cite_note-JauntyReleased-53") was Canonical's tenth release of the distribution. It will be supported until October 2010
See below

Ubuntu 9.10

---

### Post by alexfish on 2010-01-09
> **ubumania said:**
> Thanks to anyone trying to help out but it's too late now. For the second laptop on the trot, the Ubuntu upgrade process has fried my hard-drive. I now need to buy a replacement drive and, obviously, put a new OS on it. I'm not rich, saved up for this machine and all that crap, bought it just over a year ago with Ubuntu pre-loaded after being told-off on these forums for trying to run Ubuntu on a machine with 'incompatible hardware'; so, by the time I can afford a new hard drive my land-line connection will be cut off so I'm going to need to be able to plug this dongle in and have it instantly work. Can the Ubuntu that came pre-loaded on the Dell I paid a few-hundred quid for cope with such a simple task? NO, BIG BIG NO NO NO. Chances are, trying to get that (simple thing that just plugs and plays in that ever so crap Microsoft software) working on my pre-loaded Dell will break it.

Why oh why do they sell these machines in the shops as good to go when they clearly cannot compete? Pretending is no good, pretenders always get found out. It may well be no fault on the part of Canonical that they can't compete but why should users who buy hardware loaded with Ubuntu in good faith pay the ******* price? Like, what did I do to ubuntu to end up getting sold a machine that can't even deal with a device that connects to the internet without hard drives getting wiped out by an all to frequent, inadequate 6 monthly upgrade process?

Something has to give. I have used Win 7 and, with all of the God Modes enabled, it gives this Ubuntu a real run for its money on all fronts. 

Ubuntu: you let this user down in a big way, to the tune of a new hard drive after only 14 months of light use and the purchase of Windows. Last night my machine was working fine. The process of trying unsuccessfully to get Ubuntu to recognise a device for what it is in its entirety and thus connect to the internet has rendered this OS and the hard drive where it resides, inoperable. Is that good enough for paying customers who buy machines in good faith?
[I]
This is not meant to be a testimonial, I shall be posting one of those in the correct sub-forum in good time. This post is specific to this thread and therefore needs to stay as a warning to all other Dell Inspiron users who have had the misfortune of being told that these and other peripheral USB modem devices work on the Ubuntu pre-loaded machines they have purchased when clearly they do not.[/I]

Have any Ubuntu representatives got anything to say about the above experience? If this problem is specific to my machine: ie, other pre-loaded Dell Inspiron users have this device working in Ubuntu Intrepid or have upgraded beyond Intrepid without any problems and then got the OS to switch the device mode to a modem instead of a storage device (perhaps it would be better to concentrate on making these things work instead of trying to pump out release after release?) , then I apologise and humbly ask for help getting mine to do the same when I have replaced the hard drive the Ubuntu upgrade tool broke.

Only I honestly cannot believe that my story is unique.

Please prove me wrong. Give me a cast iron guarantee that this dongle will work on my Dell Inspiron 1525 if I put Ubuntu back on the new hard drive I get in a couple of weeks. Or at least be honest and say 'you will not be able to get that dongle working in Ubuntu on your machine without first having an internet connection, absolutely NO version of Ubuntu can plug and play those devices regardless of how much you paid for it, you will be better off purchasing Windows'.

Please, I can handle the truth, especially if it means having an internet connection that works.

If I put Ubuntu back on my new hard drive, how will I know if the new how 2s that have been posted above will work on this machine? How many files need editing to get this device to work? How many bits of software?

Paying customer.

Come on Ubuntu.

This Knowledge is ""Free"" And so is ""OUR"" time

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

Forgot to add Win7 requires Special Drivers for Some types of Devices /  A CD IS SUPPLIED TO GET THEM GOING / WHO IS TO BLAME ;;;;

---

### Post by ubumania on 2010-01-09
> **alexfish said:**
> This Knowledge is ""Free"" And so is ""OUR"" time

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

Forgot to add Win7 requires Special Drivers for Some types of Devices /  A CD IS SUPPLIED TO GET THEM GOING / WHO IS TO BLAME ;;;;

Was I blaming anyone? I'm pretty sure I wrote that these issues may not be on the part of Ubuntu. I also understand the concept of 'free' as in open source software.

I wasn't having a go at anyone, I am just relating my real experiences. Would it honestly be better if I kept them to myself in what is an open source community?

Dell are, in my opinion, the most out of line in this particular case because they are selling these machines as quickly as they can get rid of them yet are obviously failing to provide the basic support customers like myself obviously need. But can Dell, or Canonical for that matter, force these hardware manufacturers to recognise this system and thus grant Ubuntu users the same access to new (or not so 'new' in this case) devices as their Mac/MS using counterparts?

Give me a break yeah (I mean the caps). I bought this laptop with Ubuntu pre-loaded in order to avoid the incompatibility issues I had with my last machine. If I hadn't paid for it (at the time, the price difference between this and an identical machine with Vista on was negligible) I would not have found sufficient cause within myself to lodge any complaint whatsoever on this forum. During the process of initially switching to Ubuntu around 5 years ago, I was told in no uncertain terms on these very boards that I should in future always try to purchase a machine with hardware known to be compatible with Ubuntu. I started saving up as soon as Dell announced they would ship machines with Ubuntu pre-loaded, I was that dedicated but simply didn't have/haven't got the time to be able to learn how to do all of the command line stuff, etc, like people such as yourself. Food on table and all that. I read a couple of paragraphs into the modeswitch blurb and I am totally lost:( There are two Deb files with obscure names like 'squeeze' that mean nothing to me, but apparently I am better off using one of them; which one? There is more than one package available for download on the modeswitch page this how to directed me to as well?

I have a new hard drive on the way (I'm using a live cd now). I really don't want to buy Windows so I will give the new methods that have been posted on this thread today a try before going through with that unspeakable shite.

Sorry if this is coming like some massive rant. Again, I am not digging anyone out here. Blamethrowers are such futile weapons, are they not? I'm just gutted because I have thoughts of purchasing Windows, an act that will go against against every ounce of will in my bones, contaminating my thought processes. I do feel let down by Ubuntu but I know damn well they haven't singled me out or anything and would provide the requisite software to get this device working if they could, but obviously they can't and I wouldn't expect them to go out of their way to help one person when there are much bigger pictures to paint.

Peace

---

### Post by pdc on 2010-01-09
thanks ubumania; we are sorry to hear of your hard drive problems and hope they can be resolved;

you did seem to get usb_modeswith installed; I find with the 2.6.31 kernel that one can also "flip" the modem just by the "eject" command; we hope you will be up and running well soon;

_________________________________________________

if I can go to back to post #96 where GeorgeVita kindly posted his experiences with downloading the latest version of usb_modeswitch from the debian sid site ???

was it version 1.0.5 ?

I have greatly appreciated reading your expertise on mobile broadband issues; many thanks. 

you reported your success and it sounded like it auto-configured?

you used the phrase

> with most data from file /etc/usb_modeswitch.d/19d2:2000:uPr=USB_ZTE

which came from 

> which switched using a modified /etc/usb_modeswitch.conf with most data from file /etc/usb_modeswitch.d/19d2:2000:uPr=USB_ZTE

so clarifying if you had to do the modifying; (as opposed to the programme recognising the MF636 ...........

and you kindly gave details of the /etc/udev/rules.d/90-zte.rules file

You said ..........

> Another /etc/udev/rules.d/90-zte.rules used:

........ again ...........

did you have to create that?

(I have personally stuck with just using the eject command before connecting to an MF636 that I have !!)

---

### Post by GeorgeVita on 2010-01-10
Hi **pdc**, I am also reading your posts (and other from alexfish) to raise my knowledge via your tests!

In fact I never used usb_modeswitch before post #96 of this thread. I tried for **ubumania** who has Ubuntu 8.10 and at this version the usb-storage (zeroCD) device is 'ignored' so it can not be 'ejected'.

usb_modeswitch appears from Ubuntu 9.10 repositories (a 'newcomer' cannot find it via Synaptic on 8.10 or 9.04) so I used 'debian' version as the closer to the 'older' 8.10/9.04. I firstly tried some .conf but did not worked till found the 19d2:2000:... files. Tried some of them and finally worked with the 'setup' mentioned on post #96. .rules file created automatically. Listed for reference and/or check as the 'debian' way is not standard and something may go wrong.

As you already know and use, for ZTE modems:
>>> The correct way is to 'sudo eject srX' (zeroCD) and then the modem appears
>>> a udev rule makes it automatically
>>> possibly wvdial or gnome-ppp makes the connection more stable, etc.

Alternative to usb_modeswitch for 9.04 is udev-extras and or modemswitch.
 
I just re-installed 9.04 on an SDHC and I can test any of the above if you need.

The problem for **ubumania** is that he needs to be 'typical' in his Dell laptop keeping the pre-install Ubuntu version. But the ZTE 3g modem operation is ALWAYS 'under construction' for Ubuntu...
Best way for 8.10 would be to 'trim' system for removing the 'automatic usb-storage ignorance' but I think this needs a kernel modification.

Regards,
George

**EDIT:** P.S. my edits on post #95 came as a conclusion after many terminal tests on running usb_modeswitch.
> **pdc said:**
> (I have personally stuck with just using the eject command before connecting to an MF636 that I have !!) Make it automatic with (taken from [here]("http://ubuntuforums.org/showpost.php?p=7624549&postcount=61")): **sudo gedit /etc/udev/rules.d/zte_eject.rules**
```
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"
```

---

### Post by pdc on 2010-01-11
thanks very much George; that worked very well for me, and I have now automated the "eject" function by following your instructions; many thanks; I am also using a Mandriva on an Eee and it worked fine there too; many thanks.

---

### Post by GeorgeVita on 2010-01-11
... after many tests on an Ubuntu 8.10 LiveUSB (running now connected via ZTE MF636), I updated post #96 of this thread. The result is very close to 1st post (!) but I had to share my results...

>>> Note that as usb_modeswitch uses some 'tricks' to be synchronised with the modem for switching, 'message content' may vary, so follow instructions from: [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

Regards,
George

---

### Post by ubumania on 2010-01-13
Thanks for your replies and time spent trying to help me with my problem George, PDC. I haven't run off to MS or anything, just waiting on the new drive and I'll be having another try with the new methods.

Thanks again.

---

### Post by ubumania on 2010-01-17
Many thanks. I got the new drive sorted and am using the dongle now. The procedure on #96 worked for me straight away on a clean 8.10 install on the new drive. The updates knocked it out, however, but I went through the procedure again and it was just a matter of editing /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi and making a similar change to the section I cut and pasted below, changing the 'int="0x0015" to 'int="0x0031" so it looks like...

```

<!-- ZTE MF628 HSDPA USB dongle -->
        <match key="@info.parent:usb.product_id" int="0x0031">
          <match key="@info.parent:usb.interface.number" int="3">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>

```

and network manager picked it up again.

better than forking out for windows.

Many thanks again for all the help.

Peace

---

### Post by pdc on 2010-01-17
congratulations; well done; you have scaled a few mountains on the way;

enjoy!

---

### Post by ikipeu on 2010-02-06
I have installed MF626 with mode_switch on Ubuntu 9.04. After upgrade to Ubuntu 9.10 my MF626 stop working? I check modem on the Windows and work.
Where is problem?

---

### Post by MichaelSM on 2010-02-14
Many thanks to UNKUIRI for his original thread-starter! Didn't have to go past Page 1.....

Worked like a TREAT in Karmic. (LM 8.)

Had to ditch WICD and re-install NM; that's all. 

Cheers.

Mike.

---

### Post by Unkuiri on 2010-02-23
Hi, I can't get it to work in karmic (MF626)..:(..
When I plug the modem it appears as a cd, I eject the cd and it detects a network but then when i try to connect (using network manager) the symbol spins one time and says: "Disconnected-network is now offline". The light never turn blue, always red. I noticed that, at the same time in "Computer" appears some kind of pen drive named: "ZTE MMC Storage" (I think it is the card reader). I tried to remove/eject this driver without results, it shows an error message saying that that can't be done. I've tried also usb-modeswitch as my initial tutorial without results. Can someone help with this?
(here are my [daemon.log]("http://paste.ubuntu.com/382355/") and my [dmesg]("http://paste.ubuntu.com/382359/") if that may be of any help)
Thanks in advance

---

### Post by GeorgeVita on 2010-02-23
> **Unkuiri said:**
> Hi, I can't get it to work in karmic (MF626)..:(..
When I plug the modem it appears as a cd, I eject the cd and it detects a network but then when i try to connect (using network manager) the symbol spins one time and says: "Disconnected-network is now offline". The light never turn blue, always red. I noticed that, at the same time in "Computer" appears some kind of pen drive named: "ZTE MMC Storage" (I think it is the card reader). I tried to remove/eject this driver without results, it shows an error message saying that that can't be done. I've tried also usb-modeswitch as my initial tutorial without results. Can someone help with this?
(here are my [daemon.log]("http://paste.ubuntu.com/382355/") and my [dmesg]("http://paste.ubuntu.com/382359/") if that may be of any help)
Thanks in advance
Hi **Unkuiri**, some ideas ('back to basics!'):
- update Ubuntu 9.10 using any other internet connection
- remove SIM PIN check (use other O.S. or a mobile-phone)
- right click on network-manager icon and check APN, username, password and also IPv4 settings for your provider ('Automatic PPP' works for me)
- DO NOT use usb-modeswitch but just the 'eject' of the CD-ROM (MMC doesn't bother)
- try to connect using network-manager icon
- reboot or remove-**wait**-attach again if you have done many 'not connected' tries

Post any progress...

Good Luck,
George

P.S. My ZTE MF636 works ONLY after 'nm stop', 'mm killall' via wvdial or pppd (more at [bug#408555]("https://bugs.launchpad.net/bugs/408555"))

---

### Post by Unkuiri on 2010-02-23
Thanks again GeorgeVita...The removal of the pin worked for me...:)...I never thought that it will be so simple..:P..

Thanks...

---

### Post by ghenus_rc on 2010-03-07
I've been using Modem ZTE MF 626 for 3 months. So far ok, but it's been 3 days, it can't work in HSDPA. 

Anyone knows and can solve the problem I have? Thx GBU!

---

### Post by anacrolix on 2010-06-14
This solved the problem for me:  [http://blog.christophersmart.com/2010/05/25/ubuntu-lucid-usb-3g-modem-issue-solved/](http://blog.christophersmart.com/2010/05/25/ubuntu-lucid-usb-3g-modem-issue-solved/),  see also my comment on that post.

---

### Post by linuxprob on 2010-06-24
Hi, I am having a major problem installing the telstra zte modem. I installed the software but the problem is that when click the software i get an error of the software. Anyone please help me A.S.A.P.

---

### Post by alexfish on 2010-06-24
> **linuxprob said:**
> Hi, I am having a major problem installing the telstra zte modem. I installed the software but the problem is that when click the software i get an error of the software. Anyone please help me A.S.A.P.

Hi

which versions of Ubuntu and Modeswitch are you using

Please note Some Versions of Ununtu do not require the Modeswitch for a ZTE 626 to work

---

### Post by The Pinny Parlour on 2010-06-30
Could some kind soul please post how I can get a Telstra ZTE MF626 to work in Ubuntu 10.04.

Thank you


P.S  I have no idea what mode micro switching thing is either.

---

### Post by MichaelSM on 2010-06-30
Pinny Parlour.

If you go back to the very first page of this thread, there is a tutorial on how to get the ZTE 626 working. Every letter, symbol and space is important to be done EXACTLTY as depicted. Copy/paste into terminal.

usb-modeswitch and usb-modeswitch-data should be in Synaptic Package Manager.

Don't forget to go into Network Manager. Right-click then enable wireless. Right-click then Edit Connections. Most of this is self-explanatory. You'll have to Add a connection in mobile broadband. The dialing number should already be there #99*. No passwords. Tick automatic connection.

Forget eg. Telstra's software package. Wine will try to install it, but it's so far unworkable. If you need stats on your usage you'll have to hit Telstra's site or use your ZTE 626 on a Windoze pc.

You just have to cross the t's and dot the i's. 

Best of luck! And when it works, it works GOOD!

Mike.

---

### Post by The Pinny Parlour on 2010-06-30
> **MichaelSM said:**
> Pinny Parlour.

If you go back to the very first page of this thread, there is a tutorial on how to get the ZTE 626 working. Every letter, symbol and space is important to be done EXACTLTY as depicted. Copy/paste into terminal.

usb-modeswitch and usb-modeswitch-data should be in Synaptic Package Manager.

Don't forget to go into Network Manager. Right-click then enable wireless. Right-click then Edit Connections. Most of this is self-explanatory. You'll have to Add a connection in mobile broadband. The dialing number should already be there #99*. No passwords. Tick automatic connection.

Forget eg. Telstra's software package. Wine will try to install it, but it's so far unworkable. If you need stats on your usage you'll have to hit Telstra's site or use your ZTE 626 on a Windoze pc.

You just have to cross the t's and dot the i's. 

Best of luck! And when it works, it works GOOD!

Mike.

Thank you for your help.  I wish it was as easy as you said.

```
xxxx@xxxxdesktop:~/usb-modeswitch-1.1.3$ sudo make install
gcc -o usb_modeswitch usb_modeswitch.c -Wall -l usb 
usb_modeswitch.c:56:17: error: usb.h: No such file or directory
usb_modeswitch.c: In function ‘main’:
usb_modeswitch.c:344: warning: implicit declaration of function ‘usb_init’
usb_modeswitch.c:347: warning: implicit declaration of function ‘usb_set_debug’
usb_modeswitch.c:349: warning: implicit declaration of function ‘usb_find_busses’
usb_modeswitch.c:350: warning: implicit declaration of function ‘usb_find_devices’
usb_modeswitch.c:393: error: dereferencing pointer to incomplete type
usb_modeswitch.c:394: error: dereferencing pointer to incomplete type
usb_modeswitch.c:396: warning: implicit declaration of function ‘usb_open’
usb_modeswitch.c:396: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c:403: error: dereferencing pointer to incomplete type
usb_modeswitch.c:405: error: dereferencing pointer to incomplete type
usb_modeswitch.c:407: error: dereferencing pointer to incomplete type
usb_modeswitch.c:555: warning: implicit declaration of function ‘usb_close’
usb_modeswitch.c: In function ‘deviceDescription’:
usb_modeswitch.c:569: error: dereferencing pointer to incomplete type
usb_modeswitch.c:570: warning: implicit declaration of function ‘usb_get_string_simple’
usb_modeswitch.c:570: error: dereferencing pointer to incomplete type
usb_modeswitch.c:579: error: dereferencing pointer to incomplete type
usb_modeswitch.c:580: error: dereferencing pointer to incomplete type
usb_modeswitch.c:589: error: dereferencing pointer to incomplete type
usb_modeswitch.c:590: error: dereferencing pointer to incomplete type
usb_modeswitch.c: In function ‘deviceInquire’:
usb_modeswitch.c:622: warning: implicit declaration of function ‘usb_claim_interface’
usb_modeswitch.c:627: warning: implicit declaration of function ‘usb_clear_halt’
usb_modeswitch.c:629: warning: implicit declaration of function ‘usb_bulk_write’
usb_modeswitch.c:635: warning: implicit declaration of function ‘usb_bulk_read’
usb_modeswitch.c:662: warning: implicit declaration of function ‘usb_release_interface’
usb_modeswitch.c: In function ‘resetUSB’:
usb_modeswitch.c:678: warning: implicit declaration of function ‘sleep’
usb_modeswitch.c:680: warning: implicit declaration of function ‘usb_reset’
usb_modeswitch.c: In function ‘switchSendMessage’:
usb_modeswitch.c:731: warning: implicit declaration of function ‘usleep’
usb_modeswitch.c: In function ‘switchConfiguration’:
usb_modeswitch.c:798: warning: implicit declaration of function ‘usb_set_configuration’
usb_modeswitch.c: In function ‘switchAltSetting’:
usb_modeswitch.c:814: warning: implicit declaration of function ‘usb_set_altinterface’
usb_modeswitch.c: In function ‘switchHuaweiMode’:
usb_modeswitch.c:831: warning: implicit declaration of function ‘usb_control_msg’
usb_modeswitch.c:831: error: ‘USB_TYPE_STANDARD’ undeclared (first use in this function)
usb_modeswitch.c:831: error: (Each undeclared identifier is reported only once
usb_modeswitch.c:831: error: for each function it appears in.)
usb_modeswitch.c:831: error: ‘USB_RECIP_DEVICE’ undeclared (first use in this function)
usb_modeswitch.c:831: error: ‘USB_REQ_SET_FEATURE’ undeclared (first use in this function)
usb_modeswitch.c: In function ‘switchSonyMode’:
usb_modeswitch.c:917: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c: In function ‘detachDriver’:
usb_modeswitch.c:951: warning: implicit declaration of function ‘usb_get_driver_np’
usb_modeswitch.c:967: warning: implicit declaration of function ‘usb_detach_kernel_driver_np’
usb_modeswitch.c: In function ‘checkSuccess’:
usb_modeswitch.c:1051: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c:1057: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1057: error: dereferencing pointer to incomplete type
usb_modeswitch.c: In function ‘search_devices’:
usb_modeswitch.c:1169: warning: implicit declaration of function ‘usb_get_busses’
usb_modeswitch.c:1169: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c:1169: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1171: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1171: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1173: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1173: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1174: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1195: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1202: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1202: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1204: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1214: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1223: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1225: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1228: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1229: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1255: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1255: error: dereferencing pointer to incomplete type
usb_modeswitch.c: In function ‘find_first_bulk_output_endpoint’:
usb_modeswitch.c:1277: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1280: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1281: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1282: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1282: error: ‘USB_ENDPOINT_TYPE_MASK’ undeclared (first use in this function)
usb_modeswitch.c:1282: error: ‘USB_ENDPOINT_TYPE_BULK’ undeclared (first use in this function)
usb_modeswitch.c:1283: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1283: error: ‘USB_ENDPOINT_DIR_MASK’ undeclared (first use in this function)
usb_modeswitch.c:1284: error: dereferencing pointer to incomplete type
usb_modeswitch.c: In function ‘find_first_bulk_input_endpoint’:
usb_modeswitch.c:1295: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1298: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1299: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1300: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1300: error: ‘USB_ENDPOINT_TYPE_MASK’ undeclared (first use in this function)
usb_modeswitch.c:1300: error: ‘USB_ENDPOINT_TYPE_BULK’ undeclared (first use in this function)
usb_modeswitch.c:1301: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1301: error: ‘USB_ENDPOINT_DIR_MASK’ undeclared (first use in this function)
usb_modeswitch.c:1302: error: dereferencing pointer to incomplete type
make: *** [usb_modeswitch] Error 1

```

---

### Post by The Pinny Parlour on 2010-06-30
Anyone know what the above means?

Thanks

---

### Post by The Pinny Parlour on 2010-06-30
I tried to get it working under WINE but it won't allow it.  (something about blocked executable bit).

So people really have this device running under Ubuntu?

---

### Post by The Pinny Parlour on 2010-06-30
In a last attempt before I 'throw in the towel', I used Synaptic PM to install the USB Switch modes that nearly every post regarding this issues mentions.

Don't know what to do next however.

---

### Post by The Pinny Parlour on 2010-06-30
Shows up a USB storage device icon in 'Computer' now, and the command:
```
dmesg | grep tty 
```

Results in:

```
ian@ian-desktop:~$ dmesg | grep tty 
[  827.593383] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB0
[  827.593517] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB1
[  827.595642] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB2
[ 1696.578042] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 1696.578220] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 1696.594912] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 1958.488757] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB0
[ 1958.488892] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB1
[ 1958.490773] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB2
[ 2240.420371] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 2240.420561] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 2240.433064] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 2385.506271] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB0
[ 2385.506412] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB1
[ 2385.506982] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB2
[ 2508.592462] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 2508.592651] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 2508.601538] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 5590.082166] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB0
[ 5590.082374] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB1
[ 5590.091244] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB2
ian@ian-desktop:~$ 

```

---

### Post by MichaelSM on 2010-07-01
Look, this is only a guess,, but it seems like the modem's working OK. It's trying to go on line, getting kicked off, then trying again etc. I could be WAY wrong but Right-click Network Manager, click Edit Connections, hit the Mobile Broadband tab, click on the one you've set up, hit Edit, put in your password, then go to PPP Settings. 

This is where the authentication bits are. Now, with my Telstra ZTE MF626, I ticked EVERY ONE and probably by luck, it worked. I have also an Optus Huawei modem, and that will ONLY authenticate with just PAP enabled !!

I don't think there's a manual on this stuff. Unfortunately I didn't keep any notes when I set my own system up last year. Basically I just plugged away until it worked. 

Oh, and one other thing. Sometimes - depending upon the weather (?) - I can plug in the ZTE ages after booting the pc, and it will connect. Or it won't. Or NM will say that it has when it hasn't. 

Don't worry you'll get there.

Mike. 

PS. here is the only evidence I have for my opening comment:

michael@michael-laptop-10:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[   20.004755] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[   20.004831] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[   20.004934] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2
michael@michael-laptop-10:~$

---

### Post by alexfish on 2010-07-01
[SIZE=1]Hi MichaelSM[/SIZE]
 [SIZE=1]
[/SIZE] 
   [SIZE=1]thanks for the unput about telstra . The Pinny Parlour has also been posting about the same problem here[/SIZE]
  [SIZE=1][B][URL="http://ubuntuforums.org/showthread.php?t=1477780&page=5"]
[/URL][/B][/SIZE]
[SIZE=1]**[http://ubuntuforums.org/showthread.php?t=1477780&page=5](http://ubuntuforums.org/showthread.php?t=1477780&page=5)**[/SIZE]
 [SIZE=1]
[/SIZE] 
 [SIZE=1]As regards your query &#8220; I can plug in the ZTE ages after booting the pc, and it will connect. Or it won't. Or NM will say that it has when it hasn't. &#8220;
 can you have a look here  [/SIZE]
 [SIZE=1]
[/SIZE] 
 [SIZE=1][How To : Mobile Broadband Connections [ Ubuntu 10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")[/SIZE]
 [SIZE=1]
[/SIZE] 
 [SIZE=1]look for the line[/SIZE]
 [SIZE=1]
[/SIZE] [FONT=Verdana][SIZE=1]Network Manager failing to return the [/SIZE][/FONT][FONT=Verdana][SIZE=1]**NS1**[/SIZE][/FONT][FONT=Verdana][SIZE=1]and [/SIZE][/FONT][FONT=Verdana][SIZE=1]**NS2**[/SIZE][/FONT][FONT=Verdana][SIZE=1]IE :the modem connects but the Browser and updates etc fail to connect[/SIZE][/FONT]  : Post #1
 
[SIZE=1]hope it helps[/SIZE]
[SIZE=1]
[/SIZE] [SIZE=1]regards[/SIZE]
 [SIZE=1]
[/SIZE] [SIZE=1]alexfish[/SIZE]

---

### Post by MichaelSM on 2010-07-01
Thank you Alexfish.

I wasn't too far off track.

Looks like PP has input incorrect data. 

The OS is fine, the modem is fine.

Hope he succeeds.

Going to: [http://ubuntuforums.org/showthread.p...hlight=Telstra](http://ubuntuforums.org/showthread.p...hlight=Telstra) 

should help. 

Choosing the wrong Telstra plan will blow it.

---

### Post by iluminameluna on 2010-09-01
> **radolin said:**
> Hi guys,

I read somewhere else that people are experiencing modem hangs after ~1hr of use, so do you get these too or it works reliably?

I am looking for a 3g modem to buy with Linux support #1 criteria on the list so this will be useful info.

Best regards,
Rado

I have a ZTE MF626 which was having hang problems. I pretty much leave it on continuously and it would hang all the time.

It still drops to null speed every few minutes but goes back to speed after less than a second. The solution turned out to be calling my ISP and having them ck my connection (there's a cell ph # associated w/ these modems). They then told me that it was mostly a prob w/ their system and reset my acct. It took several calls w/ several resets but it's now working like a charm for however long I leave it running.

Warning: if you're using the ZTE brand or it's the only one available from your provider, be aware that it comes configured ONLY for the Win OS's (XP, Vista, 7) according to the manufacturer's website through Alibaba gateway: [http://leadingtel.en.alibaba.com/](http://leadingtel.en.alibaba.com/) . However, it's VERY reasonably priced, considering it can double as a flash mem stick w/ the microSD dock it comes w/. The only question I have is about the max amount of mem it will handle. The website doesn't mention it and in the course of my surfing, it varies from 2Gs to 8Gs. I currently have a 512M chip in there but that's just me ..

---

### Post by archie888 on 2010-10-04
An alternative way to make the MF626 mode switched is to edit the modem via AT commands using hyperterminal. This eliminates the need for installing usb_modeswitch.   Use hyperterminal in an XP windows machine. Find the AT com port for the modem via device manager. Then create a terminal session using 115200 baud, 8 bit, 1 stop, none. Issue AT+ZCDRUN=8 and it will respond with a success value of 1.  If you ever want to restore the device just repeat this procedure using AT+ZCDRUN=9  When you plug the modem into ubuntu 9.04, configure the modem using connection manager. Untick all compression settings, limit authentication method to PAP only, and in IPV4 settings change to Automatic PPP. Use APN telstra.internet and dial up number *99#  This achieves the same result, but there still no gaurantee that will connect to it even if the modem connects to Telstra and gives you a solid blue light.   If anyone can provide more info or has success with this method please respond.

---

### Post by chino.rodriguez on 2010-10-13
Hi. I'm new to Ubuntu. Does this guide work on Maverick Meerkat, Ubuntu 10.10? Thank you.

---

### Post by lil_tud on 2012-04-18
Hi all

An update for anyone looking to get this working on 11.10

I am pretty reen with Ubuntu, and came here looking for a solution on getting my MF626 working

It turns out that the USB_Modeswitch is already installed and works automaticly with no configuration needed in 11.10

All you need to do is go into "network connections", and create a new Mobile boadband connection for your ISP, set it to connect automatically and it should work when you connect the boardband connection under "Network"

No need for any CLI to get this working any more

- note for newbies, "Network" and "Network Connections" are two different places, I didn't realise this, and when I wasn't able to create a new connection in "Network" I thought something must be wrong, but it turns out I was just looking in the wrong place.

Until you have set up the Mobile boadband under "Network Connections" the configure button will be greyed out in "Network" and it will not connect when you enable it.

This may seem obvious to some, but it too me a while to work it out, and would have saved me trawling through pages of advise that wasn't relevant any more, so thought I would add this post for any newbies like myself, hope it helps.

Thanks again to everyone who has posted in there, some good info

Cheers

---

### Post by lisati on 2012-04-19
May this old thread rest in peace.

---

