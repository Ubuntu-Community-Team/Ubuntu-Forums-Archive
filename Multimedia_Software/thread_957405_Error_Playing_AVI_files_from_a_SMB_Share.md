---
title: "Error Playing AVI files from a SMB Share"
date: 2008-10-24
forum: Multimedia Software
---

### Post by ASolano on 2008-10-24
I am very new to the world of Ubuntu, but I am happy so far with what I have found and hope to make the switch from Windows to Ubuntu.

That said i am having an issue playing files from an SMB share.  When I double click an AVI file from a SMB share (currently using VLC to open AVI files) I get the following message

******* Start Message *******

Errors

The following errors occurred. More details might be available in the message window.

Unable to open 'smb://<SERVER_NAME>/movies/<FILE_NAME>.avi'

******* End Message *******

After receiving the above message I copied the file to the workspace (to test opening the file locally).  Opening the file locally works fine.

When I open the file on the smb share within VLC (Within VLC > File > File open > Browse) the AVI file plays fine. My goal is to open folder from an Icon on the workspace and simply double click on the AVI file, not have to open VLC, got to a menu and select a file open option, browse for the share, then select the AVI file.

From the searches I have done this was an issue with past versions of Ubuntu, and i have not found any thing recent about the issue.

I'm hoping that the answer is out there and I just haven't searched properly, so I'm happy to accept that I'm a newbie, if someone can give me some instructions or point me in the direction of a how-to.

The following is my environment details

***** Server *****

- Windows Server 2003 with Service Pack 1
- Share's Security and Sharing Permission details
-- Security (Default security with the following change)
--- Guests - Read Only access (Guest account has been enabled)
-- Sharing
--- Administrators - Full Control
--- Everyone - Read
--- Guests - Read

***** Ubuntu Workstation *****

- Ubuntu
-- Release 8.04 (Hardy)
-- Kernal Linux 2.6.24-19-generic
-- GNOME 2.22.3

I setup the Ubuntu workstation in the following manner
1. Install Ubuntu
2. Using the Update Manager ensured that it was up to date
3. Using Applications > Add/Remove, Installed VLC
4. Mounted the SMB share (Places > Network > Windows Network > Workgroup > <SERVER_NAME> > In the location Bar typed the shared folder)

---

### Post by ASolano on 2008-11-05
The fact that this thread has been viewed over 40 time without response can I assume that this issue is just too hard?  Surely someone has come across this and can confirm that this is a problem, offer a solution or request more information.

---

