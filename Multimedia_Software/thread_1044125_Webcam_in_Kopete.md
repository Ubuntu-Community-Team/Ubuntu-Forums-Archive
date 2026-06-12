---
title: "Webcam in Kopete"
date: 2009-01-19
forum: Multimedia Software
---

### Post by itabhijitb on 2009-01-19
HI,

I am using Kopete with KDE 4.1 under ubuntu with both kubuntu and ubuntu desktop installed. libjasper-runtime is also installed. My webcam seems to work and can see my images under settings within kopete. But when I try to send or received a webcam request via yahoo protocol, nothing seems to happen. I seem to get a message similar to below

kopete(30056) KRichTextEditPart::readConfig: Text color:  "#000000"
Cannot register object at /kopete/MainWindow_2/actions because actions exports its own child objects
kopete(30056) KRichTextEditPart::readConfig: Text color:  "#000000"
Enchant dict for "en_US" 0xa85a750 
kopete(30056) Sonnet::Highlighter::slotRehighlight: Highlighter::slotRehighlight()
Transfer ACCEPTED by: WebcamTask
QObject: Do not delete object, 'unnamed', during its event handler!
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QColor::setNamedColor: Unknown color name 'fafafa'
QColor::setNamedColor: Unknown color name 'fafafa'
QColor::setNamedColor: Unknown color name 'fafafa'
QColor::setNamedColor: Unknown color name 'fafafa'
kopete(30056) KRichTextEditPart::readConfig: Text color:  "#000000"
Cannot register object at /kopete/MainWindow_2/actions because actions exports its own child objects
kopete(30056) KRichTextEditPart::readConfig: Text color:  "#000000"
Enchant dict for "en_US" 0xa85a750 
kopete(30056) Sonnet::Highlighter::slotRehighlight: Highlighter::slotRehighlight()
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished


Other Details:
abhijit@abhijit-laptop:~/Download/jasper-1.900.1/src/appl$ lsusb
Bus 005 Device 002: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
abhijit@abhijit-laptop:~/Download/jasper-1.900.1/src/appl$ 



abhijit@abhijit-laptop:~/Download/jasper-1.900.1/src/appl$ dpkg -l|grep v4l
ii  libpt-1.10.10-plugins-v4l                 1.10.10-2ubuntu3                            Portable Windows Library Video Plugin for Vi
ii  libpt-1.10.10-plugins-v4l2                1.10.10-2ubuntu3                            Portable Windows Library Video Plugin for Vi
ii  libv4l-0                                  0.5.6-1~intrepid1                           Collection of video4linux support libraries
ii  v4l-conf                                  3.95.dfsg.1-8ubuntu2                        tool to configure video4linux drivers
ii  xserver-xorg-video-v4l                    1:0.2.0-1ubuntu3                            X.Org X server -- Video 4 Linux display driv
abhijit@abhijit-laptop:~/Download/jasper-1.900.1/src/appl$ 



Please help.


Rgrds,
Abhijit

---

