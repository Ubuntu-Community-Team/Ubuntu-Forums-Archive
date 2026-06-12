---
title: "Samba struggles in Dapper"
date: 2006-05-18
forum: Networking &amp; Wireless
---

### Post by hewhocutsdown on 2006-05-18
I spent this afternoon wading through

[http://www.howtoforge.com/samba_setup_ubuntu_5.10_p5](http://www.howtoforge.com/samba_setup_ubuntu_5.10_p5)
and 
[https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)

and have followed as much of the advice as possible. The only questionable areas are that in the System>Networking I've set the Domain as 'HOME' (which is the windows workgroup name)

In the below example my localhost is named 'gideon'.

```
$ smbclient -L localhost -U% 
Domain=[HOME] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          IPC       IPC Service (gideon server (Samba, Ubuntu))
        IPC$            IPC       IPC Service (gideon server (Samba, Ubuntu))
        allusers        Disk      All Users
        netlogon        Disk      Network Logon Service
Domain=[HOME] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------
        HOME                 gideon server (Samba, Ubuntu)

        Workgroup            Master
        ---------            -------
        HOME                 HOME

```

When I look at Places>Network Servers>Windows Networks nothing shows up...not certain where to go from here, or what do do...I'm not familiar with networking at all.

---

### Post by JNowka on 2006-05-18
Ok, one question, do you want to share a public drive, private drive, or both.

---

### Post by hewhocutsdown on 2006-05-18
I want my linux shared files to be available on windows, and vice versa, and all machines (windows and linux) to access the one printer (on a windows xp home box)

---

### Post by JNowka on 2006-05-18
You seem to have called both your Linux box and your workgroup home, making the comment for the Linux box gideon

I believe you can fix that by going to System->Administrator->Networking.

clicking on the General Tab

and Changing Hostname to gideon

and then editing the smb.conf from terminal so that "server string = gideon"

---

### Post by JNowka on 2006-05-19
Assuming you havent got a network shared folder yet...

Ok Im going to make this fast.  I will assume that you are using Gnome and that you have setup your network correctly to the point where you are able to see the Linux Box from your Windows computer and have set up a username and password with samba.  If you can't do this let me know and I will try to walk you through that first.

The first thing you are going to want to do is open a terminal and type:

"cd /etc/samba"

now you will need to type :

"gksudo gedit smb.conf"

enter the password and then scroll down until you find the line "security = user"

change it to "security = share"

This will make it where eventually you will be able to have the ability to access your linux box without a password.

continue to scroll down all the way to the bottom and make sure you start a new line.

now type the following

[Share_Name]
Path = /Path/To/Share/Folder
writeable = yes
public = yes

Where Share_Name is the short description you want the shares name to be.
You will see the folder called this on the network no matter what the folders original name is on linux.

now save this file.

exit the terminal

now hit CTRL + ALT + F1

you will come to a terminal like screen, dont worry its ok.

It will ask you to log in, enter your normal user name and password.

now type:

"sudo -i"

put in your password

type "startx -- :1"

another copy of gnome will open straight to the desktop.

You are now root.

Use the file browser to find the folder you want to share.  When you have found it right click on it and choose properties.

*Now for the fun part*

For access without a password
Click on the permissions tab and enable all the permissions for read write and execute for all users.  Any user can now use this folder.  

For yourself only with password
If you want it for just yourself make sure you change the owner of the folder to your login name and enable only yourself to read write and execute.

exit the file browser and goto System->Logout

This will take you back to ther terminal window

type "/etc/init.d/samba restart" and enter

type "exit" and enter

type "exit" again and enter

now hit CTRL + ALT + F7

You are done, you should now be able to use the folder from your windows computer

---

### Post by JNowka on 2006-05-19
Now for the printer.  Seeing that it is on your windows box it should be easy.

Get on the box that has the printer

Goto My Network Places

Click on Veiw Workgroup Computers

Choose the computer you are on

Now go into Printers and Faxes

Right click on the printer you wish to share, and choose sharing.

Make sure you are in the Sharing Tab, select Share this Printer, and beside Share Name, give it the name you wish it to have on the network.

To install it on the linux box you will want to go over to the linux box.

Goto System->Administrator->Printer

Select Network Printer

You will have to enter your password here

Now select the Windows computer with the Printer as the host.

give it a second to get the printer list from the windows computer and select the printer from the printer list.

click forward

choose the driver the linux computer is to use for the printer on the network and select apply.

Thats all you have to do to enable a network printer

---

