---
title: "Unable to install silverlight on xp under virtualbox"
date: 2009-02-20
forum: Multimedia Software
---

### Post by graveland on 2009-02-20
Hello,

I have been reading up on ways to get netflix instant viewing to work on linux platforms.  I made the switch to Ubuntu a couple weeks ago and netflix is the only thing I truly miss about Windows.

I installed Virtualbox and setup a Windows XP image.  I also installed Firefox 3.0. 
The problem is that when downloading and installing silverlight it tells me that my operating system/browser configuration isn't supported. 

Has anyone ran into this issue with Windows XP under virtualbox?  I do not know much on how virtual machines work but I thought this would get pass the check.  It is a valid copy of XP that is activated.

I've tried searching google a bunch but can't seem to find anyone with this issue.  I can't wait for the new moonlight 2.0..

Any advice would appreciated.  Thanks in advance.

---

### Post by directhex on 2009-02-20
I believe there's a bug with Microsoft's Silverlight installer - it doesn't consider Firefox 3.0.6 a valid browser.

Downgrade to an older FF3 release, install SL, then update Firefox

---

### Post by graveland on 2009-02-20
I tried to downgrade to FF 3.0.5 then 3.0 but both failed the check.  Any other suggestions?

Thanks again for the help.

---

### Post by directhex on 2009-02-20
> **graveland said:**
> I tried to downgrade to FF 3.0.5 then 3.0 but both failed the check.  Any other suggestions?

Thanks again for the help.

No, can't think of anything else to suggest, sorry. I rarely use Windows

---

### Post by Anglagard on 2009-06-05
> **directhex said:**
> No, can't think of anything else to suggest, sorry. I rarely use Windows

It does not work with IE or Opera or Chrome or Safari under windows?
It **should** work with IE.

weird

How is the performance for virtualbox? I'm thinking of switching back to linux again...

---

### Post by b00kw0rm on 2009-07-09
I had no problems installing Netflix' version of Silverlight on XP under VirtualBox.  I am running VirtualBox 2.2.2 on Ubutu 8.0.4.  The guest OS is Windows XP Pro SP2, Firefox 3.0.1.  Host hardware:  2.66 GHz Pentium, 2.0 GB RAM

I find the video quality is directly linked to how much RAM I have allocated to Windows as the guest OS.  In my experience, anything under 1GB of RAM to the guest OS results in very choppy video that is out of sync with the audio.  At 1GB of RAM the video is still somewhat choppy unless I reduce the video resolution to 800 x 600.  Unfortunately, under VirtualBox this reduces the total size of the guest OS window and is too small to see the entire video image.   

I thought about adding more RAM to my PC to see if allocating still more RAM to guest OS improves the video performance, but I've already maxed out what the motherboard supports.

---

