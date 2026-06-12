---
title: "Specify user on NFS share"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by KayakJim on 2009-11-10
I have a Synology DS209 NAS that I connect to via NFS share.

I have created a single user account on the NAS that I would like to use for all connections to avoid permission problems for any files and directories created on the shared drive.

How can I specify the shared account username when working on the shared drive?

---

### Post by renkinjutsu on 2009-11-10
NFS shares aren't user specific.. but what you could do is add all the client/users to the group of the one user on the NAS server.. i suppose that'll work

---

### Post by KayakJim on 2009-11-10
> **renkinjutsu said:**
> NFS shares aren't user specific.. but what you could do is add all the client/users to the group of the one user on the NAS server.. i suppose that'll work

For clarification, on the NAS create user accounts for all my users and then assign them to a single group or on my local systems assign all my users to the same shared group?

---

### Post by renkinjutsu on 2009-11-10
I think you'll need the user accounts on the server also, so you'll be able to add them to the group..

---

### Post by dmizer on 2009-11-10
NFS share permissions are handled in the file system of the server side of things. You'll need to add users to the NAS and then change the permissions of the share on the NAS to give your users the desired permissions.

You won't have to do anything on the client side of things.

---

### Post by KayakJim on 2009-11-11
I have been reading up on the different types of network connections I can make to my NAS.

It has the ability to have a Windows share, which I can use smb to connect to. All of the mount commands I have seen for this specify a username and password, which sounds more like what I want.

Does anyone have any experience with this? Is there any difference between doing it this way as opposed to NFS other than the method of connection?

---

### Post by dmizer on 2009-11-11
> **KayakJim said:**
> I have been reading up on the different types of network connections I can make to my NAS.

It has the ability to have a Windows share, which I can use smb to connect to. All of the mount commands I have seen for this specify a username and password, which sounds more like what I want.

Does anyone have any experience with this? Is there any difference between doing it this way as opposed to NFS other than the method of connection?

NFS is typically far easier to configure, offers faster transfer speeds and less network overhead than Samba. Samba offers cross platform compatibility, and has a few GUI tools.

---

### Post by KayakJim on 2009-11-11
> **dmizer said:**
> NFS is typically far easier to configure, offers faster transfer speeds and less network overhead than Samba. Samba offers cross platform compatibility, and has a few GUI tools.

Thank you, that was exactly the information I was looking for.

---

### Post by pablolie on 2009-11-13
I am also setting up the DS209.

Any pointers on how to mount a share on the NAS as a local drive on the Ubuntu machine?

---

### Post by pablolie on 2009-11-13
Since this topic shows for users with a Synology DS209, I just wanted to document how I set this up quite easily...

1. Start with the DS209 itself. Create the folder you want to share. The regular user definition will allow you to set up up for workgroup sharing. But **make *sure* to enable NFS access privilege for that folder**. Congratulations, your "server" side is set up.

The DS209 will even give you the mount point info on the NFS dialog, check the bottom line, where it will say something like
**Mount path:/volume1/pablosharex**
You also must know the IP address of the DS209 in your network, of course, let us say I have 
192.168.1.5

2. Now you have to set up the client, i.e. your Ubuntu machine. For that, Create a folder you will want to map the NFS share to map to, which I did in my user folder. It means I create a local folder called
**/home/pablo/Documents/ds209pabloshare**

3. Open a terminal window, and now you map the DS209 folder onto the local folder you created, which is done by saying

**sudo mount 192.168.1.5:/volume1/pablosharex /home/pablo/Documents/ds209pabloshare**

Now you can access that folder locally and it will look local. But it is remote. :-)

---

### Post by KayakJim on 2009-11-13
> **pablolie said:**
> I am also setting up the DS209.

Any pointers on how to mount a share on the NAS as a local drive on the Ubuntu machine?

In addition to the information provided by pablolie, I followed this wiki: [http://forum.synology.com/wiki/index.php/How_to_share_data_locally_using_the_Synology_server_as_a_File_Server]("http://forum.synology.com/wiki/index.php/How_to_share_data_locally_using_the_Synology_server_as_a_File_Server")

---

### Post by varanasi on 2009-12-16
Is there a way using nfs to automatically mount an individual's home share on the NAS when they login?  (We, too, have a Synology DS 209.)

I have [struggled with mount_pam]("http://ubuntuforums.org/showthread.php?p=8503810") but had no success.

---

