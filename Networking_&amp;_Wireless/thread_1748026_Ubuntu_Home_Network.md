---
title: "Ubuntu Home Network"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by Ashocka on 2011-05-03
I have two machines running ubuntu connected through a BiPAC 7401VGPR3 (Billion modem/router).  One is a new notebook running Ubuntu 11.04 and the other desktop computer is running 10.04 connected to the printer and external hdd.

I can't find the right documentation to network them so that I can share HDD, printers, devices, etc.  I can't get either computer to see each other via network searches.

Also may need to boot into Windows from time to time and access the network from there.

Sorry to bother with such a simple questions.

---

### Post by nothingspecial on 2011-05-03
> **Ashocka said:**
> I have two machines running ubuntu connected through a BiPAC 7401VGPR3 (Billion modem/router).  One is a new notebook running Ubuntu 11.04 and the other desktop computer is running 10.04 connected to the printer and external hdd.

I can't find the right documentation to network them so that I can share HDD, printers, devices, etc.  I can't get either computer to see each other via network searches.

Also may need to boot into Windows from time to time and access the network from there.

Sorry to bother with such a simple questions.

On the desktop, go system > administration > printing

Click server and check/tick the box that says "Publish shared printers connected to this system" (and anything else you might want).

On your notebook, click your username (top right) and click system settings, then printing. Click server on the top bar and check/tick Show printers shared by other systems.

That should sort the printing.

Now, back on your desktop type

```
sudo apt-get install openssh-server
```

When that's done go back to your laptop and click on the folder button on the left hand bar thingy. When it opens up, go to the top bar and click File > Connect to server.

In the Service type box, choose ssh from the dropdown menu. In the server box put user@ipaddress of the other computer  eg ashocka@192.168.1.2

(if you don't know the ipaddress of your desktop, right click on the network applet and choose connection information.

Check/tick the add bookmark box and give your desktop a name eg "pc"

Then click connect. You will have to enter the your users password on the desktop (not your one from the notebook). You can choose to remember that password.

Now all you need to do to have access to your desktops entire file system from your notebook is click "pc" (or whatever you called it) in your file manager.

To connect from windows you need samba but I don't use it and I don't know how. There's plenty of instruction though.

---

### Post by Ashocka on 2011-05-03
> **nothingspecial said:**
> On the desktop, go system > administration > printing

Click server and check/tick the box that says "Publish shared printers connected to this system" (and anything else you might want).

On your notebook, click your username (top right) and click system settings, then printing. Click server on the top bar and check/tick Show printers shared by other systems.

That should sort the printing.

Now, back on your desktop type

```
sudo apt-get install openssh-server
```

When that's done go back to your laptop and click on the folder button on the left hand bar thingy. When it opens up, go to the top bar and click File > Connect to server.

In the Service type box, choose ssh from the dropdown menu. In the server box put user@ipaddress of the other computer  eg ashocka@192.168.1.2

(if you don't know the ipaddress of your desktop, right click on the network applet and choose connection information.

Check/tick the add bookmark box and give your desktop a name eg "pc"

Then click connect. You will have to enter the your users password on the desktop (not your one from the notebook). You can choose to remember that password.

Now all you need to do to have access to your desktops entire file system from your notebook is click "pc" (or whatever you called it) in your file manager.

To connect from windows you need samba but I don't use it and I don't know how. There's plenty of instruction though.

Thanks.  Had done all the printer set up as you stated.  Will follow through on the other part tomorrow (my wife is using the notebook now):-)

Thanks again, I'll let you know how I go.  But I do want to be able to manage files; but I think I will be able to figure that out (hopefully):-)

---

### Post by nothingspecial on 2011-05-03
If you install openssh-server on the notebook, you can manage files and configs and do whatever you want on the notebook even when she's using it........

........ but that's for a different thread :wink:

---

### Post by Ashocka on 2011-05-04
> **nothingspecial said:**
> If you install openssh-server on the notebook, you can manage files and configs and do whatever you want on the notebook even when she's using it........

........ but that's for a different thread :wink:

Yeah, thanks I'll do that.

From your previous post everything seems to work well.  The only problem I am encountering is logging in as my wife from the notebook to her PC account.  It's not happening.  Does her account need to be open on the PC to do this?

Reading up on networking to try and get my DIY standards up a bit, but I'm in my mid fifties and a chronic neck and spinal injury is making the circuits in the old grey matter less vivid than before:confused:

Thanks a lot for taking the time to point out the bleedingly obvious.  It is really much appreciated.

---

### Post by nothingspecial on 2011-05-04
> **Ashocka said:**
> 

 The only problem I am encountering is logging in as my wife from the notebook to her PC account.  It's not happening.  Does her account need to be open on the PC to do this?



She shouldn't have to. What happens when you try?

---

### Post by gaellafond on 2011-05-26
I know this thread is already 3 weeks old, but I will try to help.

Ashocka, I think what you want to do is a file sharing, something similar to what Windows do. SSH will allow you to log to the other computer, but not to copy file from one computer to the other.

What you need is NFS (Network File System). This can allow you, for example, to see the file of your desktop computer into your wife notebook computer, in the file browser, like if they were on the notebook computer. If she save a new file in that folder, it will be save in the Desktop computer, saving disk space in the Notebook. This basically do the same as mounting a network drive in Windows.

If that's what you need, I can direct you for the installation.

Gael

NOTE: About your question for SSH-Server, if you installed the server in your wife's Notebook, you should be able to access your wife's Notebook using your desktop computer, when the Notebook is running. Your wife do not need to be logged on the Notebook. To log in the Notebook, you will have to type the following command on the desktop terminal:
ssh <wife login name>@<notebook IP>
You wife login name is the one she enter when she log in the computer. If the Notebook has been set to automatically log in, you should be able to see it in the top right corner of the screen. If you are not sure, you can open a terminal in the Notebook and type the command:
whoami
(in 1 word) That will tell you the login name. For the Notebook IP, you can go to the Internet Connection information on the Notebook, as suggested by nothingspecial on post #2.
After you typed the ssh command, it will ask you for a password. The password is the one of your wife's notebook. You will not see the password when you will type it, not even stars (*). This is normal, it's a security feature. Of course, you can NOT log in the Notebook using the Desktop login name (if that login name has not been set in the Notebook). That would be a huge security hole...

---

### Post by nothingspecial on 2011-05-27
> **gaellafond said:**
> SSH will allow you to log to the other computer, but not to copy file from one computer to the other.

What you need is NFS (Network File System). This can allow you, for example, to see the file of your desktop computer into your wife notebook computer, in the file browser, like if they were on the notebook computer.

You can do all that with ssh. I'm talking about nautilus-connect-server withh ssh. You can drag and drop files from one machine to another. Click on media files and they will play. It mounts the other computers file system in ~/.gvfs.

No need for the cli whatsoever

---

### Post by Ashocka on 2011-05-27
Hi guys (and girls),

Thanks for the comments.  Yes, basically I just want to share the mounted drives on the computers.  I want to be able to see the files on my desktop from the notebook and copy them and I want to be able to set up the backup facility on the notebook so that I can do regular automated backups to the external HDD attached via USB to the desktop computer.

I'll take the leads and encouragements you have headed me in and look into them over the next few days and report back.

Really appreciate your help.

Geoff

---

### Post by nothingspecial on 2011-05-27
I've done some screenshots if it helps.

This first one is where you click file > connect to server after opening the file browser.

[ATTACH]193352[/ATTACH]

Then this is how you fill it in. Obviously you have to change it to your details.

[ATTACH]193353[/ATTACH]

As soon as you click connect a new window will pop up that is the home folder of your other computer.

[ATTACH]193354[/ATTACH]

See how there is now a netbook bookmark in the left hand side pane. Whenever you want to connect you just click it.

You can copy files/folders between the windows. If you double click a file in the other computers window, it will open with the default app. So if you click a libre office document, it will open with libre office and you can edit it etc etc etc.

---

### Post by Ashocka on 2011-05-27
> **nothingspecial said:**
> I've done some screenshots if it helps.

This first one is where you click file > connect to server after opening the file browser.

[ATTACH]193352[/ATTACH]

Then this is how you fill it in. Obviously you have to change it to your details.

[ATTACH]193353[/ATTACH]

As soon as you click connect a new window will pop up that is the home folder of your other computer.

[ATTACH]193354[/ATTACH]

See how there is now a netbook bookmark in the left hand side pane. Whenever you want to connect you just click it.

You can copy files/folders between the windows. If you double click a file in the other computers window, it will open with the default app. So if you click a libre office document, it will open with libre office and you can edit it etc etc etc.

I have actually tried this before and I always get a msg

```
Could not display "sftp://lili@192.168.1.2/home Access was denied
```

---

### Post by nothingspecial on 2011-05-28
Try going to the other computer (lili@192.168.1.2) and doing

```
rm .ssh/known_hosts
```

Then try again.

---

### Post by Ashocka on 2011-05-28
I have actually got this working now, but for every directory I go into, or up and down a directory tree I get asked for a password.  I did tick some box somewhere to remember the password, but even when I do a new bookmark I get the same thing... always asking for the password... but at least I got to copy the files across.

---

### Post by Ashocka on 2011-05-28
Ok, funny thing... if I do it as you said from the notebook with Ubuntu 11.04 then it happens just as you stated without any problems.  But try the same thing from the desktop with ubuntu 10.04 then I get all continual password requests.

---

### Post by nothingspecial on 2011-05-29
On both computers type
```

rm .ssh/known_hosts
``` again, then
```

ssh-keygen
```

then
```

ssh-copy-id username@ipaddress
```

of the other computer, just enter through all the options. You will have to tpe the password once, but you shouldn't have to again.

---

### Post by Ashocka on 2011-05-29
> **nothingspecial said:**
> On both computers type
```

rm .ssh/known_hosts
``` again, then
```

ssh-keygen
```

then
```

ssh-copy-id username@ipaddress
```

of the other computer, just enter through all the options. You will have to tpe the password once, but you shouldn't have to again.

For the last one I get an error 
```
/usr/bin/ssh-copy-id: ERROR: No identities found
```

I'm confident I have correctly assigned username@ipaddress (if this is to be done on the host computer, not assigning the username@ipaddress of the target computer)

Funny thing is if I click "Cancel" on the password dialog box then I get into whichever directory I am targeting.

Note: notebook is in Windows at present as she has to fill in a PDF form and send it back and Linux PDF readers are not allowing all form fields to be filled and saved.

---

