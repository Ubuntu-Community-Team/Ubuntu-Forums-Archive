---
title: "Printer Installation"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by cdawley4 on 2009-03-26
Hi,

I have a printer that is hooked up on my Windows PC via USB and shared so I can use it as a network printer.  Is it possible for me to set the printer up as a network printer in Ubuntu?  I tried to find my Windows Network, but when I search for my windows machine, it can't find it.  Both computers are hooked up to my wireless router.  I should be able to find the windows PC, as it also has a 160G HDD that I can use for saving files and backing up files to from the Ubuntu machine.

Thanks,

---

### Post by Dngrsone on 2009-03-26
It can be done!

First, you need to be sure that both your Windows and Ubuntu machines are on the same network-- in Win, go to Control Panel, System (System Properties) and see what Workgroup that computer is attached to (the default is WORKGROUP, go figure).

Then in Ubuntu, open up a terminal and type in the following:

```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
sudo gedit /etc/samba/smb.conf
```

You get a text-editor window.  If samba is installed (it should be) then you will see a whole bunch of stuff, but near the beginning of the config file there should be an entry like this:

>  workgroup = MSHOME

Change that workgroup to match the one in Win.  Save and quit the text editor, reboot Ubuntu.

Now, once again in Ubuntu, go to Places/Network and see if you get a Windows Network, double-click on that and your workgroup should show.  Double-click on that and you should see you Windows computer, and hitting that should show the printer and whatever else is being shared.  I believe you should be able to right-click and install the printer from there (my network is down at the moment or I would verify that).

If you don't have samba installed, then you can install that from synaptic, as I recall.

---

### Post by cdawley4 on 2009-03-26
IIRC, my WinXP machine is already set up to MSHOME as the workgroup.  I will verify those settings when I get home tonight.  Thanks.

---

