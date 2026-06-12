---
title: "Help with scp"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by BramWillemsen on 2009-05-14
Hello,

I'm trying to copy files from a remote server to my own computer, but i am stuck. I did read the guides but it is not working in my case. The reason for this is that i cannot connect to the server directly. When i use ssh i connect to another server (server1) first and from there i use ssh again to connect to the server i need to get to (server2). I cannot connect to server2 directly.

Is there an option to send the files from server2 back to my computer using scp when i am logged in there with ssh? or do i really have to start scp from my own computer?

This is my first time using scp so i am probably overlooking something.

kind regards, Bram

---

### Post by jacobian64 on 2009-05-14
if you want to used scp then here is the command.
scp username_of_target_computer@ip_of_target_computer:/home/folder/file_to_be_copy ~

this ~ means that the file will be saved to your home folder.

---

### Post by Rubicon_82 on 2009-05-14
The scp program uses ssh for the actual data transfer.  As far as I know, this means that you won't be able to run copy files directly from server_2 to your box, unless you can create a direct ssh link between the two.  Your post suggests that sshd on server_2 won't accept connections from your local machine.  However, it may be possible to to the following:                                                                                                  

A)
Use scp to copy the files from server_2 to server_1, then copy the files from server_1 to your local machine.
On server_1 run:                                                                                             
```
                                                                                                       
$ scp user@server_2:file temp_location_on_server_1
```
Then, on your local machine:
```

$ scp user@server_1:temp_location_on_server_1 local_destination
```

B)
Use sshfs to mount the server_2 directory on server_1, then use scp to transfer the files to your local machine.
On server_1 run:
```

$ mkdir temp_mount_point
$ sshfs user@server_2:directory temp_mount_point
```
Then, on your local machine:
```

$ scp user@server_1:temp_mount_point/file local_destination
```

Use the command 'fusermount -u temp_mount_point' to unmount the directory on server_1 once you've copied the files.

C)
Start an instance of sshd on your local machine (ssh server), accepting incoming connections from server_2.  Use scp on server_2 to copy the files to your local machine.  However, first you should check this method with the admin of server_2.  Depending on their security policies they may not want you to connect from server_2 directly to your machine.

---

