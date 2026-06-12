---
title: "Accessing Windows Shared Documents and Printers"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by GTdenver on 2009-05-11
This is a simple manual method to bookmark your Windows Shares.  
Its not the ideal method, but after trying the configure Samba and other aspects of Ubuntu with no luck, this method worked for me.
I am new to Ubuntu, Linux and Programming.  Again this is a newbie quick fix that will at least allow you to transfer your images, music and documents to your Ubuntu Desktop via home networking.


Besides making sure Samba is running I used the following method to setup my Windows shared Printers and Documents in Ubuntu 9.04.

You'll need your Windows computer IP address and Shared Printer and Document Names.
[U][B]

TO GET WINDOWS[/B]** IP:**[/U]
START>RUN>CMD
Then type -  IPCONFIG /ALL

This will give you your Windows Computer IP address like 192.168.1.2
[U][B]
TO GET SHARED NAMES:[/B][/U]
START>RUN>CMD
Then type - NET SHARE

This will tell you the names of all your shared Printers and Folders.
Please note that names may be case-sensitive so capitalize only when needed.
[U][B]
SETTING UP UBUNTU TO ACCESS WINDOWS SHARED DOCUMENTS:[/B][/U]
In Ubuntu...
Click Places> Connect to Server
Change Service Type to "WINDOWS SHARE"
In SERVER type the Windows IP like 192.168.1.2
In FOLDER type SHAREDDOCS to access all shared folders.
Make sure you check the BOOKMARK BOX or you'll have to redo the shortcuts the next time you load.
[U][B]
SETTING UP UBUNTU TO ACCESS A WINDOWS SHARED PRINTER:[/B][/U]
In Ubuntu...
Click SYSTEM>ADMINISTRATION>PRINTING.
Click NEW>NETWORK>WINDOWS PRINTER VIA SAMBA.
Type Windows IP/Shared PrinterName in the SMB:// Box
Like 192.168.1.2/SamsungC


Well I think that's it. I'm just a newbie so I can't offer too much more tech support in this area.   Let me know if I need to clarify.

---

### Post by douglenn on 2009-05-21
> **GTdenver said:**
> This is a simple manual method to bookmark your Windows Shares.  
Its not the ideal method, but after trying the configure Samba and other aspects of Ubuntu with no luck, this method worked for me.
I am new to Ubuntu, Linux and Programming.  Again this is a newbie quick fix that will at least allow you to transfer your images, music and documents to your Ubuntu Desktop via home networking.


Besides making sure Samba is running I used the following method to setup my Windows shared Printers and Documents in Ubuntu 9.04.

You'll need your Windows computer IP address and Shared Printer and Document Names.
[U][B]

TO GET WINDOWS[/B]** IP:**[/U]
START>RUN>CMD
Then type -  IPCONFIG /ALL

This will give you your Windows Computer IP address like 192.168.1.2
[U][B]
TO GET SHARED NAMES:[/B][/U]
START>RUN>CMD
Then type - NET SHARE

This will tell you the names of all your shared Printers and Folders.
Please note that names may be case-sensitive so capitalize only when needed.
[U][B]
SETTING UP UBUNTU TO ACCESS WINDOWS SHARED DOCUMENTS:[/B][/U]
In Ubuntu...
Click Places> Connect to Server
Change Service Type to "WINDOWS SHARE"
In SERVER type the Windows IP like 192.168.1.2
In FOLDER type SHAREDDOCS to access all shared folders.
Make sure you check the BOOKMARK BOX or you'll have to redo the shortcuts the next time you load.
[U][B]
SETTING UP UBUNTU TO ACCESS A WINDOWS SHARED PRINTER:[/B][/U]
In Ubuntu...
Click SYSTEM>ADMINISTRATION>PRINTING.
Click NEW>NETWORK>WINDOWS PRINTER VIA SAMBA.
Type Windows IP/Shared PrinterName in the SMB:// Box
Like 192.168.1.2/SamsungC


Well I think that's it. I'm just a newbie so I can't offer too much more tech support in this area.   Let me know if I need to clarify.
I am also on Ubuntu 9.04 and really need to either share a windows printer or folder.  Unfortunately the Windows printer that I just purchased (Lexmark X4650) has no Linux driver support at all and I have tried using several existing Linux drivers for color inkjets and have not been able to print a test page.

I have basically given up on trying to share this particular windows printer with Linux and am now trying desperately to find a way to share a windows directory so that I can store Linux documents there and print them on the windows XP platform.

I have tried all of your suggestions for accessing windows documents after setting up 2 windows directories to be shared and writeable on the network. (verified with NET SHARE)  Unfortunately when I get back to Ubuntu 9.04 and "Connect to Server" with "WINDOWS SHARE" and Folder type SHAREDDOCS I immediately see a window with the message "Password required for share" with my username and Domain being set to the windows workgroup name.

I have tried lots of variations on my password and have even used the administrative password for my windows XP machine (which I just verified) and nothing works.  After cancelling out the password dialogue window I get another window popping up saying "cannot display location smb://192.168.0.12/shareddocs/"

Apparently I need to somehow setup a password in Linux for 'share' or for 'shareddocs'.  Any idea as to how I could do this?  If I cannot get this to work I will just have to try and use ftp to send doc files from Linux over to my windows XP session.

---

### Post by M1kevil on 2009-09-06
Hey Doug, the same is happening to me when I tried to access a shared folder from Ubuntu to a shared Windows XP machine in my network.
It would be great to know how to set up that passwd... :(

---

### Post by darell_m on 2009-09-09
Thanks for simple workaround as with jaunty 9.04 I failed to get network share to work but using server can now share  with XP and also printer work connect to XP computer. For a self proclaimed Noob you sure did good. Thanks again

---

### Post by country0129 on 2010-12-25
A different problem:
 
I got everything to work well, finally, Ubuntu 9.04 and Windows7 Pro, by deleting Windows Live Essentials.  Worked SEAMLESSLY over wireless from my Ubuntu laptop to my Win7 Desktop.
 
Guess what?  Wife thinks this is HER computer, and she insisted I reinstall WLE.  Well, everything worked but for the authentication on Ubuntu.  When I try to connect to the home network, it repeatedly asks for my log in name and password.  I know they're the right strings that I'm inputing in the dialog box.  I can access my Ubuntu box from windows perfectly.  The other system shows up on networking, but I cannot authenticate.
 
I uninstalled MSN Messenger and disabled Windows Live Log-in Assistant in the Windows Explorer "Add on" section of tools.  (Googled efforts suggested this).  No joy.  Does anyone have a workaround for this that will make it all work as it should?
 
 
 
 
Dean
 
> **douglenn said:**
> I am also on Ubuntu 9.04 and really need to either share a windows printer or folder. Unfortunately the Windows printer that I just purchased (Lexmark X4650) has no Linux driver support at all and I have tried using several existing Linux drivers for color inkjets and have not been able to print a test page.
 
I have basically given up on trying to share this particular windows printer with Linux and am now trying desperately to find a way to share a windows directory so that I can store Linux documents there and print them on the windows XP platform.
 
I have tried all of your suggestions for accessing windows documents after setting up 2 windows directories to be shared and writeable on the network. (verified with NET SHARE) Unfortunately when I get back to Ubuntu 9.04 and "Connect to Server" with "WINDOWS SHARE" and Folder type SHAREDDOCS I immediately see a window with the message "Password required for share" with my username and Domain being set to the windows workgroup name.
 
I have tried lots of variations on my password and have even used the administrative password for my windows XP machine (which I just verified) and nothing works. After cancelling out the password dialogue window I get another window popping up saying "cannot display location smb://192.168.0.12/shareddocs/"
 
Apparently I need to somehow setup a password in Linux for 'share' or for 'shareddocs'. Any idea as to how I could do this? If I cannot get this to work I will just have to try and use ftp to send doc files from Linux over to my windows XP session.

---

