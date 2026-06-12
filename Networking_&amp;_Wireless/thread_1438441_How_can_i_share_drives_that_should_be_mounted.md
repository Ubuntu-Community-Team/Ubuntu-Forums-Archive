---
title: "How can i share drives that should be mounted?"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by aviramof on 2010-03-25
most of the partitions on my computer are ntfs type and need to be mounted via ubuntu so how can i share the entire partition or folders from it and for it to mount automatily when remote computer reqest to enter one of those partitions?

thanks in advance.

---

### Post by johnson.d on 2010-03-25
For mounting and sharing an ntfs partition you use the following procedure:

1) Check whether NTFS driver is present in Ubuntu using the following command:

$ sudo apt-get install ntfs-3g

If it was not installed before it will prompt you to install. Type 'Y' and press enter to install.

2) After installation of ntfs-3g you can give the following command to mount the NTFS partition.

$ sudo mount -t ntfs /dev/< dev-file eg:sdb1,sdb2> /<mount-point>

3) Sharing the partition through Samba:

You need to install Samba for sharing the folder in which the ntfs partition is mounted.

You can install Samba using the following command:

$ sudo apt-get install samba

After installation you need to the edit /etc/samba/smb.conf file and add the following lines to it. 

[<share-name>]
path = /<mount-point>
browseable = yes
read only = no
guest ok = yes

Now restart the Samba service using the following command:

$ sudo /etc/init.d/samba restart

After restarting the service, you can access the folder from a Windows or Linux machine.

---

### Post by amit@nitttrchd.ac.in on 2010-03-25
> **johnson.d said:**
> For mounting and sharing an ntfs partition you use the following procedure:

1) Check whether NTFS driver is present in Ubuntu using the following command:

$ sudo apt-get install ntfs-3g

If it was not installed before it will prompt you to install. Type 'Y' and press enter to install.

2) After installation of ntfs-3g you can give the following command to mount the NTFS partition.

$ sudo mount -t ntfs /dev/< dev-file eg:sdb1,sdb2> /<mount-point>

3) Sharing the partition through Samba:

You need to install Samba for sharing the folder in which the ntfs partition is mounted.

You can install Samba using the following command:

$ sudo apt-get install samba

After installation you need to the edit /etc/samba/smb.conf file and add the following lines to it. 

[<share-name>]
path = /<mount-point>
browseable = yes
read only = no
guest ok = yes

Now restart the Samba service using the following command:

$ sudo /etc/init.d/samba restart

After restarting the service, you can access the folder from a Windows or Linux machine.


___________________________

For GUI sharing like windows one can install

$  sudo apt-get install nautilus-share

mount the folder as mentioned and thru above cmds , one can share by right click on tyhat folder

---

### Post by aviramof on 2010-03-25
Thank you very much johnson.d :):):)

---

