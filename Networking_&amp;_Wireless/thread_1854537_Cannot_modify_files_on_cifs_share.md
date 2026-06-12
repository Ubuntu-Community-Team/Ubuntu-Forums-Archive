---
title: "Cannot modify files on cifs share"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by midoh on 2011-10-04
I have an IOMEGA NAS drive connected to the network with a folder set up to hold the documents directory. On the Linux machine I mount the share via fstab. The entry is:

```
//192.168.2.201/Documents /home/office1/Documents cifs user,_netdev,nobrl,uid=1000,gid=office1,file_mode=0775,dir_mode=0775 0  0
```The directory mounts without any problems and I can see all the files and directories as well as create and delete files as expected. The problem comes in when attempting to edit and resave a file. When saving a modified file under gedit I get an error block at the top that reads
> Could not save the file /home/office1/Documents/gedit_test_file. Unexpected error: Error renaming temporary file: Input/output errorWhen I do the same thing with LibreOffice I get 2 message boxes that read > Error saving the document test_file: There is no space left on device /home/office1/Documents/test_file.odt. and then a message box the reads > Error saving the document test_file: General Error. General input/output error.About the only thing I have been able to figure out so far is that it seems to have something to do with the lock files and renaming.

FWIW, I tried the same thing on a windows pc and it works fine. Actually I used the windows pc to edit the text file I created with gedit with no issues. I have searched and searched and cannot seem to find the answer to this.

nfs is not an option as the iomega does not support nfs. I need this to work as this is set up in a small office so that several machines can access the same documents folder.

Any help would be greatly appreciated. Thanks.

---

