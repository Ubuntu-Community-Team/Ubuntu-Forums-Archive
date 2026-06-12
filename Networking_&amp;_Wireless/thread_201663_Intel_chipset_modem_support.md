---
title: "Intel chipset modem support"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by apolozanionut on 2006-06-22
Could anyone please help me find an Ubuntu compatible driver for my modem , which is Intel 537 V.92 Data Fax Modem ? Thank you.

---

### Post by pellgarlic on 2006-06-22
first of all, that modem is a dreaded "win-modem", meaning that the manufacturers of the modem relied quite heavily on windows code when they designed and built it, so they are often very difficult to get to work in linux. if you have an alternative modem, that isn't a "win-modem" you should use that instead. (non-"win-modems" are also called "hardware" modems - they are usually external usb modems, although some external modems are winmodems too - look here: [http://www.linmodems.org/](http://www.linmodems.org/) for more info). if the intel 537 is your only option, read on:

first, you should go to: [http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=8017&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=8017&strOSs=39&OSFullName=Linux*&lang=eng)
which is the download page for the driver you need. download it, and extract it anywhere on your computer. (your /home directory would be a good place :) )

next, you need to install a package that will be used to compile the driver (yes, this driver needs compiled manually :(). so, put your "dapper" install cd into the cd drive (wiht ubuntu running already). it should give you a message something like "ubuntu cd detected. you can start package manager now". click on the button that says "start package manager". synaptic will open. now search for "build-essential". select it for installation. click the "apply" button. now you are ready to install the driver.

to install this driver, you must follow the instructions that are included in the "readme.txt" file inside the .tgz file. (look for the "6 steps to install" section). it requires a bit of terminal command-line input, which isn't too complicated if you read carefully, and take your time. if you have any questions or worries, feel free to ask here.

if you are ok with following the instructions yourself, you may still find that it does not compile for ubuntu correctly - when i was installing my intel 536ep modem, i got errors telling me it hadn't compiled correctly (read the text that comes after each command you type). i had to make some changes to one of the files. 

if you get errors, read this thread: 
[http://ubuntuforums.org/showthread.php?t=122017&page=2](http://ubuntuforums.org/showthread.php?t=122017&page=2) 
(particularly my post - #19) 

and this thread: 
[http://ubuntuforums.org/showthread.php?t=169793&page=2](http://ubuntuforums.org/showthread.php?t=169793&page=2) 
(particularly my post #12, for the necessary edits to the "Intel536_inst" file - in your case, you would edit the "Intel537_inst" file in the same way).

---

