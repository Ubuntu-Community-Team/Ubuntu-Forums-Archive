---
title: "Ubuntu to Windows XP on VirtualBox"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by jhouse59 on 2010-07-25
I'm using Ubuntu 10.04 LTS. How can I connect to a Windows machine? I'm trying to connect to a VirtualBox machine with Windows XP on it. I can connect from the VirtualBox to Ubuntu. But, can't find a way to do it from Ubuntu.

---

### Post by Goolie on 2010-07-25
> **jhouse59 said:**
> I'm using Ubuntu 10.04 LTS. How can I connect to a Windows machine? I'm trying to connect to a VirtualBox machine with Windows XP on it. I can connect from the VirtualBox to Ubuntu. But, can't find a way to do it from Ubuntu.

So you have Ubuntu running a Virtual Windows XP, and you can drag files from the WinXP OS to the outside Ubuntu machine but you can't transfer files from your main Ubuntu *into* winXP?

That's what I'm gathering, I dont' remember but check the file / edit , etc. menu and I think there's an option to allow the dragging and dropping of files into the virtualized OS.

---

### Post by jhouse59 on 2010-07-25
> **Goolie said:**
> So you have Ubuntu running a Virtual Windows XP, and you can drag files from the WinXP OS to the outside Ubuntu machine but you can't transfer files from your main Ubuntu *into* winXP?

That's what I'm gathering, I dont' remember but check the file / edit , etc. menu and I think there's an option to allow the dragging and dropping of files into the virtualized OS.

Well I've got a couple of folders I can put things in. And transfer it like that. But, I can't see the machine in Ubuntu.

---

### Post by Goolie on 2010-07-25
I'm really sorry, I don't *exactly* understand your situation.  Can you elaborate a bit more?  Maybe toss in some screenshots?

---

### Post by nakajimamituru on 2010-07-25
> **jhouse59 said:**
> Well I've got a couple of folders I can put things in. And transfer it like that. But, I can't see the machine in Ubuntu.

have you any shared folder on ubuntu?
if not, try to setup shared folder on your ubuntu.

  how:
    right click on some folder and select 'Properties'
    select 'Share' tab and check the 'Share this folder'
    if the dialog tells 'Sharing service is not installed', click 'Install service'

I'm sorry but I'm using ubuntu9.10 and i'm not testing in detail.
but i think you can see the ubuntu at My network on XP after avobe operation.

---

### Post by jhouse59 on 2010-07-25
> **Goolie said:**
> I'm really sorry, I don't *exactly* understand your situation.  Can you elaborate a bit more?  Maybe toss in some screenshots?

I'm just trying to figure out how to connect to Windows from Ubuntu. I don't see a icon or folder in Ubuntu.

---

### Post by Goolie on 2010-07-25
I don't have any Windows PC's on my network so I can't give you any first-hand experience knowledge.  But you can try:

[http://industriousone.com/blog/mounting-windows-shares-linux](http://industriousone.com/blog/mounting-windows-shares-linux)

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Looks like you need Samba?  I'm not really sure, so sorry. =\

Hope those can give you some direction though!

---

### Post by theozzlives on 2010-07-25
If you have SAMBA installed, you should see your XP machine. Make sure file and print sharing is enabled in XP.

---

### Post by nakajimamituru on 2010-07-25
> **nakajimamituru said:**
> 
but i think you can see the ubuntu at My network on XP after avobe operation.

sorry...i had a misconception...
it's how to connect to Ubuntu from XP...

installing samba may help you.

---

