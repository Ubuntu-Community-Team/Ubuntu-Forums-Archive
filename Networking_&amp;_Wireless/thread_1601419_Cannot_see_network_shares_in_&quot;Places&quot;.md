---
title: "Cannot see network shares in &quot;Places&quot;"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by vmajor on 2010-10-20
Hi,

Ubuntu 10.04 x64 desktop.

We have a NAS with several shared directories. They mount fine using manual "Connect to Server" using the SMB protocol.

I assigned "Bookmarks" on connection so that I can recall them more easily when needed. 

The shared drives appear under "Places" with the more user friendly Bookmarks for each share appearing after the line divider in File Manager.

This is all splendid.

However, when for example wanting to attach a file from a mapped shared drive when writing an email in Gmail (in either Firefox or Chromium), the "File Upload" window that opens DOES NOT show any mapped shared drives or Bookmarks making it impossible to attach anything from a shared drive.

Please let me know how to fix this rather bizarre behaviour since it is severely limiting the usefulness of centralizing our files on a NAS if I cannot attach shared files to emails.

Drag and drop also does not work. Firefox ignores them while Chromium says "This file is 0 bytes, so it will not be attached."

I just successfully attached the same files in Chrome running on a Windows 7 machine in Virtualbox. This is both amazing, and somewhat embarrassing. Please help me do this from within Ubuntu 10.04 so that I do not have to resort to running a Windows machine just so that I can attach shared files


V.

---

### Post by dwitkin on 2011-05-01
hello.  I'm having exactly the same issue... still looking for an answer.  Can some ubuntu guru help?

In my case, I've tried putting the following into the location box, but it doesn't seem to do anything...

smb://[SERVER NAME]/users/[ME]/Documents/XYZ%20Trading/Financial/Taxes

suggestions?  Thank you!


> **vmajor said:**
> Hi,

Ubuntu 10.04 x64 desktop.

We have a NAS with several shared directories. They mount fine using manual "Connect to Server" using the SMB protocol.

I assigned "Bookmarks" on connection so that I can recall them more easily when needed. 

The shared drives appear under "Places" with the more user friendly Bookmarks for each share appearing after the line divider in File Manager.

This is all splendid.

However, when for example wanting to attach a file from a mapped shared drive when writing an email in Gmail (in either Firefox or Chromium), the "File Upload" window that opens DOES NOT show any mapped shared drives or Bookmarks making it impossible to attach anything from a shared drive.

Please let me know how to fix this rather bizarre behaviour since it is severely limiting the usefulness of centralizing our files on a NAS if I cannot attach shared files to emails.

Drag and drop also does not work. Firefox ignores them while Chromium says "This file is 0 bytes, so it will not be attached."

I just successfully attached the same files in Chrome running on a Windows 7 machine in Virtualbox. This is both amazing, and somewhat embarrassing. Please help me do this from within Ubuntu 10.04 so that I do not have to resort to running a Windows machine just so that I can attach shared files


V.

---

### Post by vmajor on 2011-05-03
Hi.

fstab

That was the only way to get this to work, but now it is permanent and all shares are always visible to the entire OS. One important thing to keep in mind however is to make sure that you set up your NAS to make all new files and directories with "read & write" permissions. Windows does not care, but Ubuntu cares very much. I made a noob mistake and left this setting at the NAS end at "read only" and was thus unable to work properly with some of the newly created directories and files.

Now to the answer, here is my fstab file. Edit it with your own IP instead of xxx.xxx.xxx.xxx and user name instead of user.

```
//xxx.xxx.xxx.xxx/Multimedia /media/multimedia cifs credentials=/home/user/.smbcredentials,iocharset=utf8,file_mode=0777,dirmode=0777 0 0
//xxx.xxx.xxx.xxx/Photos /media/photos cifs credentials=/home/user/.smbcredentials,iocharset=utf8,file_mode=0777,dirmode=0777 0 0
//xxx.xxx.xxx.xxx/nas_c_root /media/nas_c_root cifs credentials=/home/user/.smbcredentials,iocharset=utf8,file_mode=0777,dirmode=0777 0 0

```

Also make sure you create the required local directories (mount locations) eg. /media/photos

You also need a /home/user/.smbcredentials file. Replace with your own information instead of xxxxxxxxxx and chown it to root:

username=xxxxxxxxxxxxxxx
password=xxxxxxxxxxxxxxx

Hope this helps.

V.

---

