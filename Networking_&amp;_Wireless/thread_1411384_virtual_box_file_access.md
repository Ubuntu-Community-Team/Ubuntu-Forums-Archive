---
title: "virtual box file access"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by Chet Hagerbaumer on 2010-02-19
I need help trying to setup a share folder between ubuntu 9.10 and windows xp running inside virtualbox.  I would like to be able to transfer files between the two different platforms.

Thanks

---

### Post by Jamie Jackson on 2010-02-19
It's pretty easy to do via VBox's shared folders. First thing to do is install the guest additions: Devices >> Install Guest Additions.

After a reboot of the guest, you'll be able to set up the shared folders using the little folder icon at the bottom right.

To access the shared folder from the guest, in windows explorer, browse to \\vboxsvr\<nameOfYourShare>. It tends to work best for me to map the shared folder to a drive letter rather than using the UNC (\\servername\share) syntax.

Jamie

---

### Post by bpalone on 2010-02-20
I think that you can only access from the Virtual Machine to the files and folders on the Host.  I don't think you can reverse the direction.  I could be wrong, I have been before.

The instructions given before should get you there.  Just keep in mind the direction limit.  I usually try to store all files on the host, so I can keep the Virtual Hard Drive as uncluttered as possible.

---

### Post by Jamie Jackson on 2010-02-20
> **bpalone said:**
> I think that you can only access from the Virtual Machine to the files and folders on the Host.  I don't think you can reverse the direction.  I could be wrong, I have been before.[quote]

Well, there's no *vbox* way to do the reverse, but of course you can set up a share on the windows guest, and access that share just as you would any windows share from any linux box.

[quote]
The instructions given before should get you there.  Just keep in mind the direction limit.  I usually try to store all files on the host, so I can keep the Virtual Hard Drive as uncluttered as possible.

Yup, that's what I do, too. I've got lots of VMs and I prefer not to balloon their virtual disks with files that will be shared, so I just keep those shared files in one place--on the host.

---

### Post by Jamie Jackson on 2010-02-20
Oh, and Chet, if you haven't looked at Dropbox yet, check it out. I've only got 2GB worth of space (free account), but I find myself using it more and more for smaller files that I need across machines.

---

### Post by Chet Hagerbaumer on 2010-02-21
Many thanks to all that have responded to my request.  I've got my usb external backup drive connected and it seems to be doing exactly what I need.  Drop box is also a good idea.  I think I'll give it a try for some other files.

Again many thanks to all.

Chet

---

