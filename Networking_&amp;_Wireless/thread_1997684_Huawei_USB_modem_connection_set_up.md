---
title: "Huawei USB modem connection set up"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by jacob lastman on 2012-06-05
greetings, Maverick 10.10 on an HP compaq mini Q.
I worked through this fine fellows words:

[URL="http://khansinfo.blogspot.com/2011/04/how-to-install-usb-modem-in-ubuntu.html"]

except that the editor was NANO it all went fine.
However my wireless /network icon still says firmware missing.

please help if you know? this is a Huawei web.digicelpanama.com E173 modem. My rules file is copied below

many thanks

ACTION!="add", GOTO="huawei_zerocd_end"
SUBSYSTEM=="usb", ATTR{bDeviceClass}!="ff"
,ENV{DEVTYPE}=="usb_device", GOTO="huawei_zerocd_disable" 
SUBSYSTEM=="scsi", ENV{DEVTYPE}=="scsi_device",
GOTO="huawei_zerocd_disable" 
GOTO="huawei_zerocd_end" 
LABEL="huawei_zerocd_disable" 
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1c0b", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd" 
LABEL="huawei_zerocd_end"

actually i dont even know if spaces and so on mess it up? how to check?

---

### Post by alexfish on 2012-06-05
not sure about the HP mini

but first try these links
[Draisberghof - Software - USB_ModeSwitch]("http://www.google.com/url?sa=t&rct=j&q=usb%20modeswitch&source=web&cd=1&ved=0CGYQFjAA&url=http%3A%2F%2Fwww.draisberghof.de%2Fusb_modeswitch%2F&ei=LnLOT8-8A8nR8gPp4IzJDA&usg=AFQjCNHXRDd_7g_A3ekgGQ2d_tARDOR6iA&cad=rja")  look at the forum they may advise

also usb modeswitch should be in the repos , "Synaptic package manager"
if the interface is qualcom gobi , the drivers are also in the repo,s 

This device has different modes of operation , you will note this by reading post at

the usb modeswitch  forum

if the hp mini is gobi free and need full use of the device as in MS Windows then can have
a look here
[Huawei Mobile Broadband Devices (Ubuntu 12.04)]("http://ubuntuforums.org/showthread.php?t=1974458")

although listed as 12.04 the same drivers should work in 10.04 

the whole package is Huawei's own ,

regards

alexfish

---

