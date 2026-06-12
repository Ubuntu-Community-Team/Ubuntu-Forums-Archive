---
title: "broadband problem"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by ankit.iitbhu@gmail.com on 2010-07-01
i have bsnl dsl broadband connection having wifi modem i.e modem with wifi but i could not connect to the internet by using my laptop having ubuntu 10.04 as operating sysyem pl help me out

---

### Post by dineshs on 2010-07-01
I dont know whether the DSL tab in NM will work for wireless.(I havent used wireless).So it is always better to configure your modem in PPPoE mode (if it is not already).This link can help 
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html) 
(click modem/CPE config)
But you must be first be able to access modem .
Can you ping your modem/router?what do you get for
```
ping 192.168.1.1 -c5
```
(Assuming that the modem IP is 192.168.1.1)
and 
```
ifconfig -a
```

---

### Post by d2r2 on 2010-07-01
Hi, I have joined this group and am a rookie linux user. I am using Ubuntu 10.04 LTS - the Lucid Lynx and **was also attempting to  configure BSNL 3G USB data card LW 272**. I got a procedure from one of the sites to configure the USB data card, however, during the execution of  the procedure,  i did not get any pop up box, wherein I could input the user details. Hence I am unable to  connect to the Internet. I ran the install thru the terminal window (signed in as root), however, am unable to figure out the error. The snapshot of the terminal window is below.
 
Desktop/PCL_COMNLG# sudo sh install.sh
..................start install.................
*** Check for root...[: 46: -ne: unexpected operator
ok...
[: 76: false: unexpected operator
Join_Air/
Join_Air/pppd/
Join_Air/driver/
Join_Air/res/
Join_Air/bin/
Join_Air/Data/
Join_Air/usr/
Join_Air/res/icons/
Join_Air/res/phonebook/
Join_Air/res/base/
Join_Air/res/loginMask/
Join_Air/res/sms/
Join_Air/res/component/
Join_Air/res/dataConnect/
Join_Air/res/messageBox/
Join_Air/res/buttons/
Join_Air/res/pics/
Join_Air/res/network/
Join_Air/Data/etc/
Join_Air/Data/help/
Join_Air/Data/sound/
Join_Air/usr/share/
Join_Air/usr/lib/
Join_Air/Data/etc/ppp/
Join_Air/Data/help/index_files/
Join_Air/usr/share/pixmaps/
Join_Air/usr/share/applications/
Join_Air/Data/etc/ppp/peers/
Join_Air/updaterc.xml
Join_Air/Join_Air
Join_Air/uninstall.sh
Join_Air/launch-gui.sh
Join_Air/pppd/ip-up.local
Join_Air/pppd/ip-down.local
Join_Air/pppd/get_route_info
Join_Air/driver/driver_install.run
Join_Air/driver/nm.pp
Join_Air/driver/disselfirefox.pp
Join_Air/driver/se
Join_Air/res/icon.jpg
Join_Air/res/minimize_butt.bmp
Join_Air/res/smsBar434x29.png
Join_Air/res/close_butt.bmp
Join_Air/res/smsBar434x29.bmp
Join_Air/res/smsBar434x29mask.png
Join_Air/res/startingWindow.jpg
Join_Air/bin/9-cdrom.rules
Join_Air/bin/Join_Air
Join_Air/Data/.version.txt
Join_Air/Data/version.txt
Join_Air/Data/ussdRecord.xml
Join_Air/Data/common-config.xml
Join_Air/Data/config
Join_Air/Data/aplay.sh
Join_Air/Data/run_evince.sh
Join_Air/Data/sms.xml
Join_Air/Data/apnmatchflag.conf
Join_Air/Data/contact.xml
Join_Air/Data/modem_types.xml
Join_Air/Data/networkrc.xml
Join_Air/Data/launchFirefox.sh
Join_Air/Data/historyRecord.xml
Join_Air/Data/defaultRecord.conf
Join_Air/Data/totalRecord.conf
Join_Air/res/icons/mobile_icon.bmp
Join_Air/res/icons/sms2.png
Join_Air/res/icons/help0.png
Join_Air/res/icons/sms3.png
Join_Air/res/icons/sms0.png
Join_Air/res/icons/help2.png
Join_Air/res/icons/help3.png
Join_Air/res/icons/homeicon3.png
Join_Air/res/icons/phonebook0.png
Join_Air/res/icons/AliceMobile2.png
Join_Air/res/icons/phonebook1.png
Join_Air/res/icons/homeicon1.png
Join_Air/res/icons/set3.png
Join_Air/res/icons/AliceMobile1.png
Join_Air/res/icons/phonebook2.png
Join_Air/res/icons/sms1.png
Join_Air/res/icons/stk3.png
Join_Air/res/icons/phonebook3.png
Join_Air/res/icons/homeicon0.png
Join_Air/res/icons/homeicon2.png
Join_Air/res/icons/stk1.png
Join_Air/res/icons/set0.png
Join_Air/res/icons/stk2.png
Join_Air/res/icons/set2.png
Join_Air/res/icons/AliceMobile3.png
Join_Air/res/icons/set1.png
Join_Air/res/icons/AliceMobile0.png
Join_Air/res/icons/stk0.png
Join_Air/res/icons/help1.png
Join_Air/res/phonebook/phonebookBarBackGround380x30.png
Join_Air/res/phonebook/phonebookBar425x30.png
Join_Air/res/phonebook/centralBG626x317.jpg
Join_Air/res/phonebook/ILIcon2.png
Join_Air/res/phonebook/ILIcon0.png
Join_Air/res/phonebook/ILIcon4.png
Join_Air/res/phonebook/ILIcon3.png
Join_Air/res/phonebook/PhoneBook11 copy.png
Join_Air/res/phonebook/phonebookBarBackGround380x30.png1
Join_Air/res/base/bottomBar.gif
Join_Air/res/base/bottom_copy.png
Join_Air/res/base/pixlabel.jpg
Join_Air/res/base/top_copy.png
Join_Air/res/base/widgetstack.jpg
Join_Air/res/base/baseBG.jpg
Join_Air/res/base/connectframe.JPG
Join_Air/res/base/configBackground.jpg
Join_Air/res/base/CentreBG.jpg
Join_Air/res/base/centralBG626x317.jpg
Join_Air/res/base/centre_copy.png
Join_Air/res/loginMask/close.bmp
Join_Air/res/loginMask/loginMaskButt52x22.bmp
Join_Air/res/loginMask/loginMask1.jpg
Join_Air/res/loginMask/loginMask2.jpg
Join_Air/res/loginMask/loginMaskBar259x25.jpg
Join_Air/res/loginMask/TopBar.jpg
Join_Air/res/loginMask/loginMaskcentre259x25.jpg
Join_Air/res/loginMask/loginMask0.jpg
Join_Air/res/sms/toplabel.png
Join_Air/res/sms/button2.png
Join_Air/res/sms/Contenbak.png
Join_Air/res/sms/BtLtoR.png
Join_Air/res/sms/search.png
Join_Air/res/sms/BtRtoL.png
Join_Air/res/component/data_disconnect.png
Join_Air/res/component/ImageList_NewSms2.png
Join_Air/res/component/data2.png
Join_Air/res/component/ILIcon6.png
Join_Air/res/component/ImageList_IncomingCall0.png
Join_Air/res/component/ImageList_TrayMain1.png
Join_Air/res/component/ImageList_TrayMain5.png
Join_Air/res/component/ImageList_MemFull1.png
Join_Air/res/component/ImImage_IncomingCall.png
Join_Air/res/component/ImageList_NewSms.gif
Join_Air/res/component/StateImageList0.png
Join_Air/res/component/ImageList_RSSILevel1.png
Join_Air/res/component/ImageList_TrayMain2.png
Join_Air/res/component/StateImageList2.png
Join_Air/res/component/sim_cancel.png
Join_Air/res/component/ImageList_Internet3.png
Join_Air/res/component/ILIcon1 .png
Join_Air/res/component/ImageList_RSSILevel5.png
Join_Air/res/component/ImageList_RSSILevel2.png
Join_Air/res/component/ImageList_TrayMain4.png
Join_Air/res/component/ImageList_power4.png
Join_Air/res/component/data0.png
Join_Air/res/component/ImageList_IncomingCall1.png
Join_Air/res/component/ImageList_Internet2.png
Join_Air/res/component/ImageList_NewSms0.png
Join_Air/res/component/ImageList_power1.png
Join_Air/res/component/data1.png
Join_Air/res/component/modem_on.png
Join_Air/res/component/modem_off.png
Join_Air/res/component/DataAniImageList0.png
Join_Air/res/component/ImageList_TrayMain9 .png
Join_Air/res/component/DataAniImageList4.png
Join_Air/res/component/DataStateImageList1.png
Join_Air/res/component/Call_IMbutton.png
Join_Air/res/component/sim_on.png
Join_Air/res/component/ImImage_Close.png
Join_Air/res/component/ImageList_power2.png
Join_Air/res/component/ImageList_IncomingCall2.png
Join_Air/res/component/ILIcon5.png
Join_Air/res/component/ImageList_MemFull2.png
Join_Air/res/component/ImageList_power0.png
Join_Air/res/component/ImageList_MemFull0.png
Join_Air/res/component/ImageList_power3.png
Join_Air/res/component/ILIcon2.png
Join_Air/res/component/ImageList_Internet1.png
Join_Air/res/component/ImageList_TrayMain8.png
Join_Air/res/component/ImageList_TrayMain0.png
Join_Air/res/component/ImageList_TrayMain3.png
Join_Air/res/component/nosimcard.jpg
Join_Air/res/component/datastate1.png
Join_Air/res/component/sim_off.png
Join_Air/res/component/ILIcon0.png
Join_Air/res/component/DataAniImageList2.png
Join_Air/res/component/ImageList_RSSILevel3.png
Join_Air/res/component/ImageList_IncomingCall3.png
Join_Air/res/component/iconBackground.jpg
Join_Air/res/component/ILIcon4.png
Join_Air/res/component/ILIcon3.png
Join_Air/res/component/DataStateImageList0.png
Join_Air/res/component/StateImageList1.png
Join_Air/res/component/ImageList_RSSILevel4.png
Join_Air/res/component/ImageList_TrayMain7.png
Join_Air/res/component/ImageList_Internet0.png
Join_Air/res/component/datastate0.png
Join_Air/res/component/SMS_IMbutton.png
Join_Air/res/component/ImageList_NewSms1.png
Join_Air/res/component/DataStateImage.png
Join_Air/res/component/StateImageList3.png
Join_Air/res/component/ImageList_TrayMain6.png
Join_Air/res/component/uninsert.jpg
Join_Air/res/component/ImImage_NewSms.png
Join_Air/res/component/DataAniImageList3.png
Join_Air/res/component/ImageList_NewSms3.png
Join_Air/res/component/DataAniImageList1.png
Join_Air/res/component/ImageList_RSSILevel0.png
Join_Air/res/component/Reject_IMbutton.png
Join_Air/res/dataConnect/bar608x29copy.png
Join_Air/res/messageBox/close.bmp
Join_Air/res/messageBox/MsgBoxImage.bmp
Join_Air/res/messageBox/msg_warning.png
Join_Air/res/messageBox/part5MessageBox.jpg
Join_Air/res/messageBox/part1MessageBOX234x121.bmp
Join_Air/res/messageBox/barMessageBOX238x23.bmp
Join_Air/res/messageBox/msg_query.png
Join_Air/res/messageBox/progress.gif
Join_Air/res/messageBox/messagebox_btn45x19.bmp
Join_Air/res/messageBox/MsgBoxBack.BMP
Join_Air/res/messageBox/NewMsgBackImage.bmp
Join_Air/res/messageBox/msg_information.png
Join_Air/res/buttons/buttons61x21.bmp
Join_Air/res/buttons/buttons8.png
Join_Air/res/buttons/buttons6.png
Join_Air/res/buttons/loginMaskButt52x22.bmp
Join_Air/res/buttons/buttons9mask.png
Join_Air/res/buttons/buttons10.png
Join_Air/res/buttons/buttons9.png
Join_Air/res/buttons/buttons10mask.png
Join_Air/res/buttons/buttons11mask.png
Join_Air/res/buttons/buttons6.jpg
Join_Air/res/buttons/buttons5.jpg
Join_Air/res/buttons/buttons7.png
Join_Air/res/buttons/buttons8.jpg
Join_Air/res/buttons/buttons57x23.bmp
Join_Air/res/buttons/buttons4.jpg
Join_Air/res/buttons/buttons7copy.png
Join_Air/res/buttons/buttons11.jpg
Join_Air/res/buttons/buttons14.jpg
Join_Air/res/buttons/buttons9.jpg
Join_Air/res/buttons/buttons12.jpg
Join_Air/res/buttons/buttons1.jpg
Join_Air/res/buttons/buttons13.jpg
Join_Air/res/buttons/buttons2.jpg
Join_Air/res/buttons/buttons5.MID.jpg
Join_Air/res/buttons/buttons6.MID.jpg
Join_Air/res/buttons/buttons50x23.bmp
Join_Air/res/buttons/buttons7mask.MID.png
Join_Air/res/buttons/buttons7.jpg
Join_Air/res/buttons/buttons6.MID.png
Join_Air/res/buttons/buttons14.png
Join_Air/res/buttons/buttons12mask.png
Join_Air/res/buttons/buttons4.MID.jpg
Join_Air/res/buttons/buttons3.MID.jpg
Join_Air/res/buttons/buttons159x37.bmp
Join_Air/res/buttons/buttons7mask.png
Join_Air/res/buttons/buttons0.jpg
Join_Air/res/buttons/buttons7.MID.png
Join_Air/res/buttons/buttons3.jpg
Join_Air/res/buttons/buttons10.jpg
Join_Air/res/buttons/buttons13.png
Join_Air/res/buttons/buttons12.png
Join_Air/res/buttons/buttons11.png
Join_Air/res/pics/Image3.png
Join_Air/res/pics/ILIcon2.png
Join_Air/res/pics/Button1.png
Join_Air/res/pics/Image2.png
Join_Air/res/pics/ILIcon0.png
Join_Air/res/pics/ILIcon4.png
Join_Air/res/pics/ILIcon3.png
Join_Air/res/pics/Image6.png
Join_Air/res/pics/test.png
Join_Air/res/network/search.gif
Join_Air/res/network/StateImageList0.png
Join_Air/res/network/StateImageList2.png
Join_Air/res/network/FindNetImage1.jpg
Join_Air/res/network/select.gif
Join_Air/res/network/StateImageList1.png
Join_Air/res/network/StateImageList3.png
Join_Air/Data/etc/wvdial.conf
Join_Air/Data/etc/resolv.conf
Join_Air/Data/help/help.html
Join_Air/Data/sound/connect.wav
Join_Air/Data/sound/sms.wav
Join_Air/Data/sound/chimes.wav
Join_Air/Data/sound/cat.wav
Join_Air/Data/sound/ringout.wav
Join_Air/Data/sound/stelephone.wav
Join_Air/Data/sound/ringin.wav
Join_Air/Data/sound/bird.wav
Join_Air/Data/sound/tada.wav
Join_Air/Data/sound/clock.wav
Join_Air/Data/sound/logout.wav
Join_Air/Data/sound/disconnect.wav
Join_Air/Data/sound/notify.wav
Join_Air/Data/etc/ppp/resolv.conf
Join_Air/Data/etc/ppp/options
Join_Air/Data/help/index_files/data_disconnect.png
Join_Air/Data/help/index_files/help0.png
Join_Air/Data/help/index_files/sms0.png
Join_Air/Data/help/index_files/data0.png
Join_Air/Data/help/index_files/modem_on.png
Join_Air/Data/help/index_files/phonebook0.png
Join_Air/Data/help/index_files/modem_off.png
Join_Air/Data/help/index_files/sim_on.png
Join_Air/Data/help/index_files/a_017_help
Join_Air/Data/help/index_files/sim_off.png
Join_Air/Data/help/index_files/homeicon0.png
Join_Air/Data/help/index_files/a_007_help
Join_Air/Data/help/index_files/a_004_help
Join_Air/Data/help/index_files/ImageList_NewSms1.png
Join_Air/Data/help/index_files/set0.png
Join_Air/Data/help/index_files/a_020_help
Join_Air/Data/help/index_files/AliceMobile0.png
Join_Air/Data/help/index_files/stk0.png
Join_Air/Data/help/index_files/a_024_help
Join_Air/usr/share/pixmaps/Join_Air.png
Join_Air/usr/share/applications/Join_Air.desktop
Join_Air/Data/etc/ppp/peers/wvdial
[: 223: false: unexpected operator
cp: cannot stat `*': No such file or directory
unrecognized command
udevadm is exist!
******Begin to /opt/Join_Air/driver
this is linux driver installtion
this  is customized kernel ,kernel version is: 2.6.32-22-generic
make -C /lib/modules/2.6.32-22-generic/build  M=/tmp/ONDA_driver_install_V2.8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /tmp/ONDA_driver_install_V2.8/onda.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/ONDA_driver_install_V2.8/onda.mod.o
  LD [M]  /tmp/ONDA_driver_install_V2.8/onda.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
enter customize_driver_install function
disselfirefox.pp driver_install.run nm.pp se End to /opt/Join_Air/driver
install completed!!!
....After setup, you will find the Join_Air in  "Applications->Internet->Join_Air". Click the Join_Air and the  application will run
read: 401: Illegal option -n
./Join_Air: error while loading shared libraries: libqt-mt.so.3: cannot  open shared object file: No such file or directory
install.sh: 404: Syntax error: "fi" unexpected
 
 
 **Could anybody help**
 
Regards

---

### Post by dineshs on 2010-07-01
d2r2,
pl start a new thread after reading this guide by alexfish.
[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)
You may need to post the output of
```
lsusb
```
```
dmesg | grep -e "modem" -e "tty"
```
So that alexfish, pdc ... can help
BTW did you try to configure the connection via the [COLOR="Blue"]Mobile broadband[/COLOR] tab in NM?

---

### Post by d2r2 on 2010-07-01
Dear dineshs

Thank u for the quick response. whilst I am trying to figure out the article and shall start a new thread, I just ran the codes given by u, albeit without the USB card inserted ( I shall do so in a while), and here are the results

$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04b3:310c IBM Corp. Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04b3:3025 IBM Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    0.277842] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.278277] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

Is this correct.

With regards to installation using the Network Manager, I donot think I used that since the procedure given was thru the terminal window. Anyways as time passes by I will figure out the jargons of using linux. 

Regards

---

