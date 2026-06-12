---
title: "Simple file sharing using Samba"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by DavidS on 2011-02-01
I have a new computer running Ubuntu 10.10, and an old one running 9.10.

I'd like to set up file-sharing between them, using Samba - because I also have a hand-held computer running Windows XP Pro (yuk!) which it would be nice to bring into the system eventually.  All 3 computers connect via a router.

I have installed samba4 on the new machine, and samba4-clients on the old one.  When I click on Places-Network on the new machine I see "Juno" (which is the new machine) and "Windows Network".  Clicking on Juno just shows "print$".  (I can't even even share a folder on this machine, because right-clicking doesn't produce a sharing option.)  Clicking on Windows Network shows nothing.

On the old machine I do have a shared folder.  When I click on Places-Network I see "Windows Network", but when I click on that I get an error message "Failed to retrieve share list from server".

Finally, running 'ps -A' on the new machine shows 6 instances of samba, 4 of smbd and 1 gvfsd-smb-brows.  Running 'ps -A' on the old machine shows 2 instances of smbd.  I thought this probably meant I was running a samba server on both machines, so I killed the processes on the old machine and tried clicking on Windows Network again and got the same result as before.

Then I tried Places-Connect to Server... again.  I entered the server name 'juno' and got the message 'Cannot display location "smb://juno/" Failed to retrieve share list from server'.

Can someone tell me where to find out how to set this up so that it works?

David

---

### Post by Morbius1 on 2011-02-01
The description from Synaptic on the Samba4 package:
> These packages contain snapshot versions of Samba 4, the next-generation version of Samba. [COLOR=Blue]These should be considered _experimental_, and should not be used in production[/COLOR].Uninstall everything related to Samba4. Reboot the box just in case there's some wierd service started somewhere and when you login back to Ubuntu:

Open Nautilus
Right click on a folder in your home directory
Select "Sharing Options"
If you don't have samba installed it will automatically install samba and everything else you need to make samba work.

If you don't have "Sharing Options" available install the following package and try it again:
```
nautilus-share
```

---

### Post by bleutyler on 2011-02-01
I would advise that you start simple and ping each box from the other.  

Windows XP, Vista and up have "Network Settings" that let you pick between "Home Office" "Trusted Sites" or some list with similar options.  

If that part of XP is not configured properly, ping will not even work.

Just a heads up, this had me stuck for a while.

---

### Post by DavidS on 2011-02-01
Well, I've uninstalled samba4 etc. from both machines.

I then installed samba on the new machine, and then tried to share a file on the old one.  Sure enough, I was told that I needed to let Samba be installed, so I did.

Now I still can't see one machine from another, and I have smbd running on both machines - but surely, I should only have that on one machine, shouldn't I?

I don't appear to have a process called "samba" running on either machine, although I had before I uninstalled things!

Help!

David

---

### Post by pricetech on 2011-02-01
Try this:

[http://ubuntuforums.org/showthread.php?t=1644585](http://ubuntuforums.org/showthread.php?t=1644585)

Always works for me.

---

### Post by Morbius1 on 2011-02-01
Please post the output of the following commands:
```
testparm -s
``````
net usershare info --long
```[COLOR=Blue]EDIT[/COLOR]: You might as well post this one as well just in case something got borked with smbclient:
```
smbtree
```

---

