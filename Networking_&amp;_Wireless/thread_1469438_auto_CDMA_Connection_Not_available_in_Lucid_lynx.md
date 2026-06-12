---
title: "auto CDMA Connection Not available in Lucid lynx"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by dalfish on 2010-05-02
Dear ALL

                    I am a ubuntu user from Ubuntu8.10.Earlier versions of ubuntu Jauntyjacklope and prior to it had the Auto CDMA connection in the network manager applet. which was used to connect to the Huawei EC325 USBmodem. it works Flawlessly in Ubuntu 8.04,8.10 and 9.04. Since 9.10 this option is not present. I had put a thread regarding this while 9.10 was released. still this is not present in Lucid lynx How to get connected to the internet. The other options in the network manager applet are not working for me. My ISP is not listed in the network applet. So i am unable to connect to the internet Please help

---

### Post by alexfish on 2010-05-02
Hi dalfish

could you look at this thread, it may help

[http://ubuntuforums.org/showthread.php?t=1317056](http://ubuntuforums.org/showthread.php?t=1317056)

have details of your provider { Ask them if in doubt } as they may be different to those on the post

regards 

alexfish

---

### Post by dalfish on 2010-05-02
Hi Alexfish


                  I tried Gnomeppp and wvdial. Wvdial dials the connection but the permission to connect is denied by the root. i tried to give the permission for dialing but failed.So that method is also a failure.anyway I would like to comment. My favorite distro now is PCLOS as PCLOS is backward compatible. Ubuntu seems to going in a high end way ignoring the needs of mobile broadband users like me.i have put the same problem before in ubuntu forums before. They did not correct or rectify the problem in lucid. This means ubuntu lacks a direction. So i m sorry to say that ubuntu is not my favorite distro. Ignoring the needs of mobile broadband users like me is not a nice thing to do. i welcome other ubuntu users to solve my problem

---

### Post by alexfish on 2010-05-02
**[B]User Privileges- the dip and dialout groups**[/B]

 On some versions of Ubuntu you do not automatically have all the permissions to run gnome-ppp if you are the first (default) user created even with though you should have all the normal administration privileges - you need to be both in the **dip** and the **dialout** groups to run it. This apparent mistake was probably done for additional security but is a nuisance. If this is the case the log file which is available from the Log button will have a line complaining about permissions for the executable file /usr/sbin/pppd.
 The easiest way to get the required privileges is to do System -> Administration -> Users and Groups then unlock with your password and highlight your user name and click Properties and on the User Privileges Tab tick 'Connect to Internet using a Modem' which adds you to the **dip** group and 'Use Modems' which adds you to the **dialout** group. Neither act immediately and you need to restart or logout and back in as the same user.
 If this does not work or you prefer to use a terminal then the following two commands will add YOURUSERNAME to the dip and dialup groups

From the terminal

Code:

 sudo adduser YOURUSERNAME dip

sudo adduser YOURUSERNAME dialout

 You can check which groups you are in (and get some other useful information by:
Code:

 id
 
  If you still got permission problems try

 **[B]Permissions for /etc/ppp/pap-secrets and etc/ppp/chap-secrets**[/B]

 If you want to save the username and password in gnome-ppp they are saved in /etc/ppp/pap-secrets and etc/ppp/chap-secrets and you need to give read and write access to them from group dip - if you do not then you will get an warning message in the connection log. In most cases this does not matter as the username and password are not actually used or checked by most mobile internet providers - they know who you are from the SIM which is already registered before you can access data. Even so it is best to set these permissions. I use a root file browser which is started in a terminal by:

Use this with caution

Code:

 gksudo nautilus

 You then navigate to folder /etc/ppp and right click on pap-secrets -> Properties -> Permissions tab then select dip from the drop down menu for Group and and then select read and write under Access. Repeat for chap-secrets. The annoying warning messages should now disappear.
source

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

Hope this will help

You can use sudo wvdial ; but not recommended

regards


alexfish

---

### Post by alexfish on 2010-05-02
Hi again

Could you post the results of this command from the terminal

dmesg | grep -e "modem" -e "tty" 


thanks in advance a

alexfish

---

### Post by dalfish on 2010-05-03
Dear Alexfish


                       This is the output that you have requested

ubuntu@ubuntu-desktop:~$ dmesg | grep -e "modem" -e "tty" 
[    0.000000] console [tty0] enabled
[    0.299034] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.299340] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.179115] USB Serial support registered for GSM modem (1-port)
[   33.179962] option 2-7:1.0: GSM modem (1-port) converter detected
[   33.180416] usb 2-7: GSM modem (1-port) converter now attached to ttyUSB0
[   33.180432] option 2-7:1.1: GSM modem (1-port) converter detected
[   33.180558] usb 2-7: GSM modem (1-port) converter now attached to ttyUSB1
[   33.180579] option: v0.7.2:USB Driver for GSM modems
[   61.563742] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[   61.563872] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[   97.643446] option 2-7:1.0: GSM modem (1-port) converter detected
[   97.643574] usb 2-7: GSM modem (1-port) converter now attached to ttyUSB0
[   97.650046] option 2-7:1.1: GSM modem (1-port) converter detected
[   97.650152] usb 2-7: GSM modem (1-port) converter now attached to ttyUSB1
ubuntu@ubuntu-desktop:~$ 


Auto CDMA option in network applet in Jaunty and 8.10 was sucessful. This is not present in Lucid and karmic koala. I appreciate ur efforts for posting about Gnome ppp permissions. It is a laborious task. i will try it. if it does not work or system becomes unstable. i will go back to ubuntu 9.04 or PCLOS. meanwhile i welcome you and new methods to solve the problem

---

### Post by alexfish on 2010-05-03
hi
noting from the outputs shows the device as a GSM modem so possibly it is a enumeration problem with the modem manager I have seen a few post like this but the devices have connected


if you still got root problems with wvdial try using from root

code:
sudo wvdial

further

could post the contents of the wvdial.conf  

thanks in advance 

alexfish

---

### Post by alexfish on 2010-05-06
this may be a bug/ but can't find details in launchpad

By reason: look at the above : you say the modem is CDMA but  GSM is registering 

Extract from modem manager D-bus Interface Specification

                                  **Enumerated types:**

 **MM_MODEM_TYPE**

 MM_MODEM_TYPE_GSM = 1     A GSM device.
MM_MODEM_TYPE_CDMA = 2     A CDMA device.    

   reference :Modem Manager ;Look at entries on first site

possible work around below , but can't confirm 

1. wait  for official updates 
2. use git clone

As mentioned I can't confirm the above so use git at your own risk 
                                 

 [http://cgit.freedesktop.org/ModemManager/ModemManager/](http://cgit.freedesktop.org/ModemManager/ModemManager/)
 

 [http://sourceforge.net/apps/mediawiki/mbm/index.php?title=MBM](http://sourceforge.net/apps/mediawiki/mbm/index.php?title=MBM)
 

 [https://help.ubuntu.com/community/Git](https://help.ubuntu.com/community/Git)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

[URL="https://help.ubuntu.com/community/Git"]
[/URL]

---

