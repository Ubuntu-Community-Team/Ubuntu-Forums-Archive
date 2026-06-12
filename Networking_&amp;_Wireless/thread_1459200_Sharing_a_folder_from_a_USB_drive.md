---
title: "Sharing a folder from a USB drive"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by PaulClarke on 2010-04-21
Hello,

For many months I was using a Lacie NAS for all the shared files on our home LAN.  It broke last Friday and is being repaired under Warranty.  I got all the files off and put them on a USB drive and now want to share them via a Ubuntu 9.10 PC. 
I can share a folder in "home" but I cannot share a folder on the USB drive and get the following errors "Unable to mount location" and "Failed to mount Windows share"

I do exactly the same set for both.

any ideas?

Paul

---

### Post by Morbius1 on 2010-04-21
You didn't state how your usb drive is formatted or what method of file sharing your using - there are two.

It's likely that this isn't a samba problem but a linux file permissions problem. For example, if it's formatted in FAT32 or NTFS it's going to mount with you as owner and read / write permissions to you only.

You may have set up your share to allow guest access but no matter how hard samba tries to allow guests to access it nothing can override linux file permissions.

If you set up your share using Nautilus-share ( right click folder > sharing options ) then:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
force user = morbius
```[COLOR=Blue]*Change morbius to your local login user name*[/COLOR]

Save the file, exit gedit, and back in the Terminal type:

**sudo service samba restart**

If you used Classic-share ( where the share definition is in smb.conf itself ) then you need to add that line to share definition and not the global section.

---

### Post by PaulClarke on 2010-04-25
Thank you for your reply.

You are correct about the permissions issue. As this is only a temp issue till my NAS comes back from repair I will give the kids the USB drives with their files.

Thank you again

Paul

---

