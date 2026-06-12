---
title: "Mount Folder on D-Link DNS-323 when Ubuntu Starts"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by geoff511 on 2009-05-22
Firstly many thanks to all who have shared information regarding the Mounting of Network drives, especially to dmizer in his thread
URL="http://ubuntuforums.org/showthread.php?t=288534". 
Please read this thread before attempting to use my information.

Am using Ubuntu 9.04 Jaunty and with a Dlink GW-510 wireless network card, connected via a Netgear Router to my DNS-323

1) Give the DNS-323 a static ip address.
Do this by using the help info supplied with the DNS-323 and your router/hub.
I have chosen  192.168.0.5
Folder to link to on the DNS-323 is /BT/Bits
(ignore the root folder Volume_1 that the DNS-323 creates)

2) Make folder in /media directory on Ubuntu for linked folder to be mounted in.
My folder is called DNS

sudo mkdir /media/DNS

3) Backup copy of /etc/fstab just in case, as this is where we will put the required mounting command

sudo cp /etc/fstab /etc/fstab_old

4) Test mounting code in a terminal window.
To mount the Folder /BT/Bits into the Ubuntu folder /media/DNS type following code -

sudo mount -t cifs //192.168.0.5/BT/Bits /media/DNS -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

Enter password if asked.

You should now have an icon on desktop linked (mounted) directly to your DNS-323 folder.
Open and check.

5) Right-click on desktop icon and unmount, so we can check the next step works also.

6) Edit fstab so mount will occur when Ubuntu starts.

sudo nano /etc/fstab

Insert line after last line of code in file -

//192.168.0.5/BT/Bits   /media/DNS    cifs  guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Ctrl + X  ,  Y  ,  enter
to save and exit

7) Test code in /fstab works

sudo mount -a

The icon should re-appear on desktop !

Mount should now occur when you re-start Ubuntu and folder should be avail via most programs.

If using 9.04 Jaunty - error when Shutting Down -
Edit PostSession/Default

sudo nano /etc/gdm/PostSession/Default

below line  #!/bin/sh   add line

/etc/init.d/unmountnfs.sh

Ctrl + X  ,  Y  ,  enter

-------------------------------------
** Don't forget to change your DNS-323 Ip address, folder names in above code to your settings. **
-------------------------------------
Once again many thanks to dmizer for his thread/info.

Regards,
Geoff

PS. in section 4) & 6) if not shown correctly, the code near end of line is
dir_mode=0777
In preview it shows a space in the middle of the 7's 
Beats me why ???

---

### Post by oyanax on 2009-07-04
Just to spare somebody else some frustration I went through when trying to use credentials:
On Jaunty I first had to install the smbfs package, otherwise only the variant of putting explicitly "username=xxx,password=yyy" in /etc/fstab would work. 

o.

---

### Post by ToreB on 2009-07-23
Hi there. Thank you for the good write-up, perfect for new users as myself.
I'm having some problems mounting my DNS-323 to xubuntu 8.04. I'm rather new to ubuntu, please excuse if my question is due to my lack of knowledge in this.
My DNS-323 works fine in connection to my Win PC (mapped as an external drive), have a static IP and is running 1.07 firmware.

I've installed smbfs successfully, ping to DNS-323 IP-address OK, created the /media/DNS folder as described, but when I try to manually mount the DNS-323: 
```
sudo mount -t cifs //192.168.1.4/iTunes_Tore/Music /media/DNS -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```This returns an an error:[I]
retrying with upper case share name
mount error 6 = No such device or address[/I]

Am I missing something here?

PS: There's a typo in the first post, the last "0777" contain a space character.


Thanks in advance,
Tore 
Oslo, Norway

---

### Post by ToreB on 2009-07-23
Ah, I found the solution myself, the string had to contain the root folder path in the DNS-323:

```
sudo mount -t cifs //192.168.1.4/Volume_1/iTunes_Tore/Music /media/DNS -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```

After doing this I now can browse the external files in the /media/DNS folder.
Regards,
Tore

---

