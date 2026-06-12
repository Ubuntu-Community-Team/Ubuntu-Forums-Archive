---
title: "Help! Video Prob!"
date: 2006-01-31
forum: Multimedia &amp; Video
---

### Post by linuxnovice on 2006-01-31
Hello People,
Its been two days since I REINSTALLED Ubuntu but this screen res is driving me nuts. Currently its 640x480 but my moniter & Video card, can support a max of 1074x768. Now I have an IBM E74 17 inch montier and an Intel 82845GL graphics card with 64 MB of video RAM. I have tried so many methods to resolve this problem but none have worked. 
The following site proposes to give me the driver for my graphics card to work in linux : [http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1764&DwnldID=8203&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1764&DwnldID=8203&strOSs=39&OSFullName=Linux*&lang=eng)
I do have a few questions though:
1) Will that really work?? or should I try something else (if so, please suggest!)
2) If that driver works, please give me instructions to download and install the driver.....as I have never as yet download any software off the net in this manner. (I have used apt-get, update manager, automatix).

I got this website from another thread. However the thread author had detailed that this drive is in .rpm format and cannot be uninstalled if installed. And the solution was to convert it to .deb format using alien. I dont get any of this....how do I do it?? 

Please give me detailed instrutions as I am new to linux.
THANKS IN ADVANCE!
Linuxnovice.

---

### Post by gingermark on 2006-01-31
I can't say whether it will help or not, but in regards to using alien:

Download the package, and save it somewhere sensible (maybe a directory called "alien" within your home directory).

Open up a terminal window, and navigate to the directory (so, in this example type 'cd alien/' or 'cd /home/your_username/alien'.

Then type 'alien -d packagename' (where packagename is the file you downloaded). A deb file should then be created.

To install it type 'sudo dpkg -i packagename.deb'.

---

### Post by linuxnovice on 2006-02-03
Well I installed it...but it really didnt solve my problem.
Linuxnovice.

---

