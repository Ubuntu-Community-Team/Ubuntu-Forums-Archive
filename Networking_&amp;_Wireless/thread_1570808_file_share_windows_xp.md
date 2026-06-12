---
title: "file share windows xp"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by zeus123 on 2010-09-08
Ive been trying for a week now to connect my ubuntu laptop to my windows xp desktop so that I can copy my pics on the desktop over to the laptop. Im using a crossover cable and ubuntu 10.04

I have tried too many things to bother explaining... including reinstalling ubuntu.

I have managed to get ubuntu to ping to xp. I had to set the ip address and netmask (?) manually. 

From here i cannot get to my shared file on the windows computer.

Ive tried using nautilus and clicking on network.... I get an icon called "Windows Network" but cant browse further. Ive also tried clicking "file", "connect to netowrk" and typing in the ip address with/out share name. Ive tried using the desktop's computer name etc. Ive enabled the Guest account on windows. I have run sudo apt-get install smbfs and installed samba from the software centre. There are lots of "sambas" in the software centre... i installed the one simply called "samba"

Please can someone explain to me what I have to do to move my pics from xp to ubuntu.

Ive googled for the entire week too and nothing works.

Any help? Please!!!!

---

### Post by mr clark25 on 2010-09-08
1.crossover cables are rarly supposted under ubuntu.

2.when you pinged the xp machine, it was probably over your network. (the ethernet cable)

3. you should be able to get the files to your computer by doing this:

create a file on your desktop. (name doesnt really matter)
right-click the file and select "sharing options". check the box named "share this folder". and then hit "creat share". if it needs to install something, let it. while your in the properties window, look under permissions, and let everyone do everything.
then (yes, i had to find a how-to, havent used widows forever...):
> 

[LIST=1]
[*]
[LIST]
[*]in Windows XP, click on the **Start **button and select **My Computer**.            In the *Other Places* section on the left-hand side of the window,            click on **My Network Places**. Under the *Network Tasks* section            on the left side of the window, click on **View workgroup computers**.
[/LIST]
     
[*]Double-click on the name of the computer the shared folder resides on.
[*]Double-click on the folder you have access to.
[*]In the window that appears, type in the username and password of the user        account you have been given in order to access that shared folder.
[*]Click **OK**.
[/LIST]
   The folder's contents will now be displayed in a window. What you are allowed      to do in this folder depends on the permissions its owner has given you.

now, copy/paste your stuff that you want to transfer here. it should now appear in the folder that you created on your ubuntu computer.

---

### Post by zeus123 on 2010-09-10
Thankyou for your suggestion. 

I have now managed to get the ubuntu laptop to show in the list of computers in the workgroup from windows but when I click on it I just get some error message... not even a username/password request.

From the ubuntu laptop.... if I click on network I get Windows Netowrk > Workgroup > Rik-Laptop. No desktop (ie my windows computer)

If I go to connect to network and enter the ip address of the windows desktop it opens up into Rik-Laptop, and not the windows desktop.

I am slowly getting there but its been something like 10 days now... very frustrating!

---

### Post by sydbat on 2010-09-10
Have you tried putting your pics onto a flash stick or USB drive and transfer them that way? Not a solution, I know, but it might save you headaches.

---

### Post by zeus123 on 2010-09-10
Ive got about 80gb of stuff in total and a 2gb flash drive... and my desktop is only USB1 :( 

Though I could have probably transferred it all by now!!!

Im gonna reinstall ubuntu and start with a clean slate.

---

### Post by Calash on 2010-09-10
I am going to assume that you are trying to map your Windows XP hard drive on your Ubuntu system.

First, make sure the Windows box has no firewall running.  Even the default will block incoming samba connections by default.

Second, make sure your account on Windows has a password.  Depending on the version of XP it may block you from using accounts with no password.

Make sure sharing is setup and working on the Windows box.  You will need to give your account both share and NTFS permissions to the folder in question.  If you are using the login account then this should be all set for you.

Now, on your Ubuntu system verify the connection one more time with a ping.  If it looks good open a Nautilus window, any will do.  From the Go menu select location and type the following in the Location: field:

```

smb://192.168.0.2/

```

Replace the IP with your Windows XP address.

You should get a window with a couple of admin shares, denoted by the $ after, and the share you setup.  Double click on that share and fill out any access information it asks for.

---

